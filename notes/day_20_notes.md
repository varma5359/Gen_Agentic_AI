# Day 20 — Build an LLM-Powered REST API with FastAPI

**Phase:** 3 — LLM Application Development  
**Approved topic:** FastAPI and LLM integration, backend architecture, modular code and API documentation  
**Mini-project:** LLM-Powered REST API  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
Students will learn to:
- Explain how a backend connects a frontend to an LLM.
- Create a FastAPI application.
- Define a request model using Pydantic.
- Create a POST endpoint that accepts a question.
- Call an LLM from the endpoint.
- Return a structured JSON response.
- Organize code into separate files.
- Use FastAPI interactive API documentation.

## 2. Understand the application architecture

A user interface should not contain a private server API key. Instead, it sends the question to your backend. The backend securely calls the LLM provider.

~~~text
Browser / Streamlit / Mobile app
              |
              | POST /ask
              v
        FastAPI backend
              |
              | validate request
              v
        LLM service module
              |
              | API key from environment
              v
        OpenAI / Gemini API
              |
              | generated answer
              v
        FastAPI JSON response
              |
              v
          User interface
~~~

**Why this architecture?**
- The API key stays on the server.
- Input can be validated before spending API credits.
- Error handling can be centralized.
- The frontend does not need provider-specific SDK code.
- Other applications can reuse the backend endpoint.

## 3. Install packages

Inside your active project virtual environment:

~~~bash
python -m pip install fastapi uvicorn openai python-dotenv
~~~

| Package | Purpose |
|---|---|
| fastapi | Builds the HTTP API |
| uvicorn | Runs the ASGI application server |
| openai | Communicates with OpenAI API |
| python-dotenv | Loads local .env configuration |

## 4. Create the project structure

~~~text
llm_fastapi_app/
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── schemas.py
│   └── services/
│       ├── __init__.py
│       └── llm_service.py
├── .env
├── .gitignore
└── requirements.txt
~~~

- main.py: application and API routes.
- schemas.py: request and response data rules.
- llm_service.py: code that calls the model.
- .env: local secret configuration.
- .gitignore: files Git should not track.

## 5. Define request and response schemas

Create app/schemas.py:

~~~python
from pydantic import BaseModel, Field

class AskRequest(BaseModel):
    question: str = Field(min_length=1, max_length=4000)

class AskResponse(BaseModel):
    answer: str
    model: str
~~~

| Code | Meaning |
|---|---|
| BaseModel | Pydantic class used to define validated data |
| Field(...) | Adds constraints and metadata to a field |
| min_length=1 | Rejects an empty string |
| max_length=4000 | Rejects text longer than 4,000 characters |
| AskRequest | Describes the data expected from caller |
| AskResponse | Describes the data returned by endpoint |

The schema checks shape and length. It does not decide whether a question is safe for every business use.

## 6. Create the LLM service

Create app/services/llm_service.py:

~~~python
import os
from dotenv import load_dotenv
from openai import OpenAI

load_dotenv()

MODEL_NAME = "gpt-4.1-mini"
api_key = os.getenv("OPENAI_API_KEY")

if not api_key:
    raise RuntimeError("OPENAI_API_KEY is not configured.")

client = OpenAI(api_key=api_key, timeout=20.0)

def generate_answer(question: str) -> str:
    response = client.responses.create(
        model=MODEL_NAME,
        input=question
    )
    return response.output_text
~~~

| Code | Meaning |
|---|---|
| question: str | Type hint: function expects text |
| -> str | Type hint: function is expected to return text |
| MODEL_NAME | Constant holding the selected model name |
| generate_answer() | Reusable function that sends question to model |
| timeout=20.0 | Sets a finite request timeout |
| return response.output_text | Returns generated text to caller |

This function does not know about HTTP routes. Keeping it separate makes it easier to test and reuse.

## 7. Create the FastAPI application

Create app/main.py:

~~~python
from fastapi import FastAPI, HTTPException
from openai import APIConnectionError, APITimeoutError, RateLimitError
from app.schemas import AskRequest, AskResponse
from app.services.llm_service import generate_answer, MODEL_NAME

app = FastAPI(
    title="LLM Question API",
    description="A beginner-friendly API that sends questions to an LLM.",
    version="1.0.0"
)

@app.get("/")
def home():
    return {"message": "LLM API is running"}

@app.post("/ask", response_model=AskResponse)
def ask_question(request: AskRequest):
    try:
        answer = generate_answer(request.question)
        return AskResponse(
            answer=answer,
            model=MODEL_NAME
        )

    except APITimeoutError:
        raise HTTPException(
            status_code=504,
            detail="The AI provider took too long to respond."
        )

    except APIConnectionError:
        raise HTTPException(
            status_code=503,
            detail="Could not connect to the AI provider."
        )

    except RateLimitError:
        raise HTTPException(
            status_code=429,
            detail="The AI provider rate limit or quota was reached."
        )
~~~

### Understand the FastAPI parts

| Code | Meaning |
|---|---|
| FastAPI(...) | Creates the application object |
| @app.get("/") | Registers a GET route at root path |
| @app.post("/ask") | Registers a POST route at /ask |
| request: AskRequest | Validates incoming JSON using Pydantic |
| response_model=AskResponse | Declares expected response structure |
| HTTPException | Produces an HTTP error response |
| status_code=504 | Uses HTTP 504 for gateway timeout |
| status_code=503 | Uses HTTP 503 for unavailable service |
| status_code=429 | Uses HTTP 429 for rate-limit response |

A route is a URL path plus an HTTP method that tells the backend which function to run.

**Note:** This starter example handles three common provider errors. Add handling for authentication, invalid requests and server errors before production. Do not expose internal stack traces or secrets to API users.

## 8. Configure environment variables

Create .env in the project root:

~~~text
OPENAI_API_KEY=your_real_key_here
~~~

Create .gitignore:

~~~text
.env
.venv/
__pycache__/
*.pyc
~~~

Never commit .env. The backend reads the key; the browser should never receive it.

## 9. Run the API

From the project root:

~~~bash
uvicorn app.main:app --reload
~~~

Meaning:
- uvicorn: start the ASGI server.
- app.main: import main.py module inside the app package.
- :app: use the variable named app inside that module.
- --reload: restart the development server when code changes.

The terminal should show that the server is running, usually at http://127.0.0.1:8000.

## 10. Test using interactive API documentation

Open these local URLs:

| URL | Purpose |
|---|---|
| http://127.0.0.1:8000/ | Test the home route |
| http://127.0.0.1:8000/docs | Interactive Swagger UI documentation |
| http://127.0.0.1:8000/openapi.json | Machine-readable OpenAPI schema |

In /docs:
1. Find POST /ask.
2. Select Try it out.
3. Enter this request body:

~~~json
{
  "question": "Explain Python variables in two simple sentences."
}
~~~

4. Select Execute.

**Expected response shape (answer wording varies):**

~~~json
{
  "answer": "A variable is a name used to store a value. For example, age = 20 stores the number 20 in age.",
  "model": "gpt-4.1-mini"
}
~~~

If the key is missing or invalid, the request will fail. Confirm environment and provider access.

## 11. Understand HTTP request and response

~~~text
POST /ask
Content-Type: application/json

{"question": "Explain Python variables."}
                  |
                  v
             FastAPI route
                  |
                  v
             Pydantic validation
                  |
                  v
             LLM service
                  |
                  v
             Provider response
                  |
                  v
HTTP 200 + JSON response
~~~

| Status | Meaning in this application |
|---:|---|
| 200 | Request completed successfully |
| 422 | Request body failed FastAPI/Pydantic validation |
| 429 | Provider rate limit or quota response |
| 503 | Provider connection unavailable |
| 504 | Provider request timed out |

A 422 response can happen before the LLM is called, such as when question is missing or too long.

## 12. Test validation without calling the model

Try sending an empty question:

~~~json
{
  "question": ""
}
~~~

**Expected:** FastAPI returns a 422 validation response because the minimum length is one.

Try a normal question:

~~~json
{
  "question": "What is an API?"
}
~~~

**Expected:** The backend calls the model and returns an answer if configuration and provider access are valid.

## 13. Mini-project — LLM-Powered REST API

**Goal:** Build a backend service that accepts a question and returns an AI answer.

Required features:
- GET / health route.
- POST /ask question route.
- Pydantic request and response schemas.
- LLM call in a separate service module.
- API key loaded from environment.
- Finite timeout.
- Clear handling for provider connection, timeout and rate-limit errors.
- Interactive documentation at /docs.
- .env excluded from Git.

Suggested architecture:

~~~text
app/
├── main.py             # HTTP routes
├── schemas.py          # Pydantic request/response models
└── services/
    └── llm_service.py  # Provider SDK integration
~~~

**Completion checklist**
- [ ] Server starts successfully.
- [ ] GET / returns a message.
- [ ] POST /ask accepts valid JSON.
- [ ] Empty question is rejected.
- [ ] Valid question returns an answer.
- [ ] Provider failures return useful HTTP errors.
- [ ] /docs displays endpoint documentation.
- [ ] API key is not committed to Git.

## 14. Common mistakes
- Putting API key in frontend JavaScript.
- Putting all code in one large file.
- Forgetting to activate the correct virtual environment.
- Running Uvicorn from the wrong directory.
- Confusing app.main:app with a URL.
- Forgetting that POST request data must be JSON in this example.
- Returning a raw provider object instead of the response schema.
- Catching an error but returning HTTP 200 with a fake answer.
- Assuming a local development server is ready for public production traffic.

## 15. Practice questions with answers
1. **What is FastAPI?** A Python framework for building APIs.
2. **What is Uvicorn?** An ASGI server that runs the FastAPI application.
3. **What does @app.post("/ask") do?** Registers a POST endpoint at /ask.
4. **Why use Pydantic?** To define and validate request and response data.
5. **What is a request model?** A schema describing data an endpoint expects.
6. **What is a response model?** A schema describing data an endpoint returns.
7. **Why keep LLM code in a service module?** To separate provider logic from HTTP routing.
8. **What is /docs?** FastAPI's interactive API documentation page.
9. **Why keep API key on the backend?** To prevent exposing the secret to browser users.
10. **What does HTTP 422 commonly indicate in FastAPI?** Request data failed validation.

## 16. Phase 3 recap

~~~text
Day 16: Python -> Provider API -> Model response
Day 17: Model response -> JSON -> Pydantic validation
Day 18: Message history -> Streaming -> Chat experience
Day 19: Errors -> Timeout -> Retry -> Fallback
Day 20: FastAPI -> LLM service -> REST API
~~~

## Phase 3 outcome
After completing this phase, students should be able to:
- Make a basic LLM API call from Python.
- Keep API keys outside source code.
- Request and validate structured data.
- Maintain conversation history and stream output.
- Handle common API failures.
- Build a basic FastAPI endpoint that calls an LLM.

**Next phase:** Phase 4 — Embeddings and Vector Databases (Days 21–25).
