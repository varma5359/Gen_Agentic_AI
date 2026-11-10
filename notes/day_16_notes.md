# Day 16 — OpenAI and Gemini API Integration

**Phase:** 3 — LLM Application Development  
**Approved topic:** OpenAI and Gemini API integration, SDK usage, API keys, model selection and secure configuration  
**Mini-project:** Python LLM API Integration Application  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
By the end of this lesson, students can:
- Explain how a Python program communicates with an LLM.
- Understand API, SDK, API key, model, request and response.
- Create a virtual environment and install an SDK.
- Store an API key outside Python source code.
- Send a basic request to OpenAI or Gemini.
- Read the response and diagnose common setup errors.

## 2. What is an API?
An API is a defined way for two software systems to communicate.

Example: your Python program needs an AI answer. It sends a request to the provider's server instead of installing a large model locally.

~~~text
Python application
      |
      | HTTPS request + prompt + API key
      v
AI provider (OpenAI / Google)
      |
      | model processes the prompt
      v
Generated response
      |
      v
Python application displays the answer
~~~

| Word | Simple meaning |
|---|---|
| API | Communication interface between programs |
| API provider | Company that makes the model available |
| SDK | Package that makes API calls easier |
| API key | Secret credential used to authorize API access |
| Model | AI system that generates the response |
| Request | Information your program sends |
| Response | Information the provider returns |

An API key is not the model. It is a credential that allows an application to access an API.

## 3. OpenAI and Gemini
- OpenAI and Google provide language models through APIs.
- Both can be called from Python.
- Their SDKs, method names, model names and response structures differ.
- Code for one provider cannot automatically be copied unchanged to the other.

## 4. Prepare a Python project

~~~text
llm_api_app/
├── .venv/
├── .env
├── .gitignore
├── main.py
└── requirements.txt
~~~

Run these commands in the terminal inside the project folder.

~~~bash
python -m venv .venv
~~~

Activate the environment:

| Operating system | Command |
|---|---|
| Windows PowerShell | .venv\Scripts\Activate.ps1 |
| Windows Command Prompt | .venv\Scripts\activate.bat |
| macOS / Linux | source .venv/bin/activate |

Check installation:

~~~bash
python --version
python -m pip --version
~~~

A virtual environment is an isolated place for this project's packages. It helps prevent one project's package changes from affecting another project.

## 5. Install SDK packages

OpenAI example:

~~~bash
python -m pip install openai python-dotenv
~~~

Gemini example:

~~~bash
python -m pip install google-genai python-dotenv
~~~

Save installed dependencies:

~~~bash
python -m pip freeze > requirements.txt
~~~

| Command | Meaning |
|---|---|
| python -m pip install package | Installs a package in the active environment |
| python -m pip freeze | Lists installed packages and versions |
| > requirements.txt | Writes command output to a file |

## 6. API key security

Create a local file named .env:

~~~text
OPENAI_API_KEY=put_your_real_key_here
GEMINI_API_KEY=put_your_real_key_here
~~~

These are variable names; obtain real keys from the providers' official developer consoles.

Create .gitignore:

~~~text
.env
.venv/
__pycache__/
*.pyc
~~~

**Never:**
- Put a real API key directly in a Python file.
- Commit .env to GitHub.
- Share a key in screenshots or public messages.
- Put a server API key in browser-side JavaScript.
- Print the full key while debugging.

If a key is exposed, revoke it with the provider and create a replacement.

## 7. OpenAI — first API request

Create main.py:

~~~python
import os
from dotenv import load_dotenv
from openai import OpenAI

load_dotenv()

api_key = os.getenv("OPENAI_API_KEY")

if not api_key:
    raise ValueError("OPENAI_API_KEY is missing. Check your .env file.")

client = OpenAI(api_key=api_key)

response = client.responses.create(
    model="gpt-4.1-mini",
    input="Explain an API in two simple sentences for a college student."
)

print(response.output_text)
~~~

Run:

~~~bash
python main.py
~~~

**Expected result:** A short explanation appears in the terminal. Exact wording varies because model responses are generated dynamically.

### Understand every important line

| Code | Explanation |
|---|---|
| import os | Loads Python operating-system utilities |
| load_dotenv() | Reads local .env values into environment variables |
| os.getenv("OPENAI_API_KEY") | Reads the variable; returns a string or None |
| if not api_key | Checks whether the value is missing or empty |
| raise ValueError(...) | Stops the program with a clear configuration error |
| OpenAI(api_key=api_key) | Creates a configured provider client |
| client.responses.create(...) | Sends input to the selected model |
| response.output_text | Reads generated text from the response |

**What is a client object?** It is a configured helper object that knows how to communicate with the provider. Create it once and use it to make requests.

**What does responses.create() return?** A response object containing information about the model output and request. output_text is a convenient property for generated text.

## 8. Gemini — first API request

Create gemini_app.py:

~~~python
import os
from dotenv import load_dotenv
from google import genai

load_dotenv()

api_key = os.getenv("GEMINI_API_KEY")

if not api_key:
    raise ValueError("GEMINI_API_KEY is missing. Check your .env file.")

client = genai.Client(api_key=api_key)

response = client.models.generate_content(
    model="gemini-2.5-flash",
    contents="Explain an API in two simple sentences for a college student."
)

print(response.text)
~~~

Run:

~~~bash
python gemini_app.py
~~~

**Expected result:** A short AI-generated explanation appears. Exact wording may vary.

### Compare provider SDKs

| Task | OpenAI example | Gemini example |
|---|---|---|
| Import | from openai import OpenAI | from google import genai |
| Client | OpenAI(api_key=...) | genai.Client(api_key=...) |
| Request | client.responses.create(...) | client.models.generate_content(...) |
| Read text | response.output_text | response.text |

Check current provider documentation for supported model names and SDK changes before starting a new project.

## 9. Choosing a model

Do not choose a model only because its name sounds powerful.

| Factor | Question |
|---|---|
| Quality | Is the answer accurate enough for this task? |
| Speed | Does the application need a quick response? |
| Cost | What will input and output usage cost? |
| Context | Can the model handle the required amount of information? |
| Features | Does it support the required output format or modality? |
| Availability | Can this account access the model? |

Start with a small, cost-effective model for learning. Measure quality and cost before production use.

## 10. Common errors

| Error or symptom | Possible cause | First check |
|---|---|---|
| Missing API key | .env not loaded or variable misspelled | Check filename and variable name |
| 401 authentication error | Invalid, expired or revoked key | Check or replace provider key |
| 403 permission error | Account/key lacks access | Check project permissions |
| Model not found | Wrong or unavailable model name | Check provider model list |
| 429 rate limit | Too many requests or quota issue | Check usage and retry guidance |
| Timeout / connection error | Network or temporary service issue | Check network and provider status |
| ModuleNotFoundError | Package installed in another environment | Activate .venv and install again |

Do not solve every error by changing the model name. Identify whether it is a key, permission, model, quota or network problem.

## 11. Mini-project — Python LLM API Integration Application

**Goal:** Build a command-line application that sends a question to one provider and displays the answer.

Requirements:
1. Read the key from .env.
2. Keep .env out of Git.
3. Ask the user to enter a question.
4. Send the question to the selected provider.
5. Print the response.
6. Show a useful message if the key is missing.
7. Never print the secret key.

Beginner input example:

~~~python
question = input("Ask the AI: ").strip()

if not question:
    print("Please enter a question.")
else:
    print("Your question:", question)
~~~

| Python feature | Meaning |
|---|---|
| input() | Displays a prompt and reads text typed by the user |
| strip() | Returns a new string without whitespace at the beginning/end |
| if not question | Checks whether the user entered an empty string |

**Completion checklist**
- [ ] Virtual environment created and activated.
- [ ] SDK installed in that environment.
- [ ] .env contains the key locally.
- [ ] .gitignore excludes .env.
- [ ] One successful request completed.
- [ ] Missing-key case tested.
- [ ] No secret committed to Git.

## 12. Practice questions with answers

1. **What is an API?** A defined interface that lets software systems communicate.
2. **What is an SDK?** A package that provides convenient code for using a service.
3. **Is an API key the AI model?** No. It is a credential used to authorize API access.
4. **Why use .env?** To keep configuration and secrets outside source code.
5. **What does os.getenv() return when a variable is missing?** None, unless a default is supplied.
6. **Why activate .venv?** To use the packages installed for this project.
7. **Are OpenAI and Gemini SDK calls identical?** No. Their clients and request methods differ.
8. **What does a 401 error commonly indicate?** An authentication problem.
9. **Why check model availability?** Model names and account access can change.
10. **Should a key be committed to GitHub?** Never.

## 13. Day 16 recap

~~~text
Python project
    |
    v
Load environment variables
    |
    v
Read API key safely
    |
    v
Create provider client
    |
    v
Send prompt to model
    |
    v
Read response text
    |
    v
Display result
~~~

**Next day:** Day 17 — Structured outputs, JSON responses, Pydantic schemas, output validation and parsing.
