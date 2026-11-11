# Day 9 — FastAPI, routes, Pydantic models, request validation and response models

**Phase 1 | 2–3 hours | Project: Student Information REST API**

## Learning objectives
Install and run FastAPI; create routes; use path and query parameters; define Pydantic request/response models; validate inputs; return appropriate status codes and errors.

## 1. What is FastAPI?
FastAPI is a Python framework for building HTTP APIs. It maps HTTP requests to Python functions, validates request data using type annotations and Pydantic, and generates interactive API documentation.

A route is a URL path plus an HTTP method. A path operation function runs when a matching request arrives.

## 2. Install and run
Create/activate a virtual environment first. Install:
~~~bash
python -m pip install fastapi uvicorn
~~~
Create main.py, then run:
~~~bash
uvicorn main:app --reload
~~~
main is the module/file name, app is the FastAPI object. --reload is for development. Open the local /docs route for interactive API documentation.

## 3. First API
~~~python
from fastapi import FastAPI

app = FastAPI(title="TechPhile Student API")

@app.get("/")
def home():
    return {"message": "Student API is running"}
~~~

FastAPI() creates the application. @app.get registers a GET route. home runs when that route is requested. Returning a dictionary produces JSON.

## 4. Path and query parameters
~~~python
@app.get("/students/{student_id}")
def get_student(student_id: int):
    return {"student_id": student_id}

@app.get("/search")
def search_students(course: str = "Python"):
    return {"course": course}
~~~

student_id is in the URL path and is validated as an integer. course is a query parameter because it is not in the path. Try /students/12 and /search?course=GenAI. Invalid integer input produces a validation response.

## 5. Pydantic request model
A request body often contains multiple fields. A Pydantic model describes and validates the expected data.

~~~python
from pydantic import BaseModel, Field

class StudentCreate(BaseModel):
    name: str = Field(min_length=2, max_length=60)
    email: str
    course: str
    score: float = Field(ge=0, le=100)
~~~

BaseModel defines the schema. Field adds constraints. Pydantic parses JSON into a model and reports invalid values. Email is a string in this beginner example; a production service should use format validation and a verification workflow.

## 6. Complete API example
~~~python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel, Field

app = FastAPI(title="TechPhile Student API")
students = {}
next_id = 1

class StudentCreate(BaseModel):
    name: str = Field(min_length=2, max_length=60)
    email: str
    course: str
    score: float = Field(ge=0, le=100)

class StudentResponse(BaseModel):
    id: int
    name: str
    email: str
    course: str
    score: float

@app.post("/students", response_model=StudentResponse, status_code=201)
def create_student(student: StudentCreate):
    global next_id
    student_id = next_id
    next_id += 1
    record = {"id": student_id, **student.model_dump()}
    students[student_id] = record
    return record

@app.get("/students/{student_id}", response_model=StudentResponse)
def get_student(student_id: int):
    if student_id not in students:
        raise HTTPException(status_code=404, detail="Student not found")
    return students[student_id]
~~~

StudentCreate defines accepted input. StudentResponse defines the output shape. POST creates a record and returns 201. GET retrieves one record. HTTPException returns a deliberate 404 when the record is absent.

Important limitation: students is an in-memory dictionary. It resets when the server restarts and is not safe persistent storage for multiple workers. Day 10 introduces SQL.

## 7. Request and response
POST /students body:
~~~json
{
  "name": "Asha",
  "email": "asha@example.test",
  "course": "GenAI",
  "score": 88
}
~~~
A successful response contains an id and the validated fields. Score 120 fails because the permitted range is 0–100.

## 8. Industry scenario
A student portal exposes endpoints to create and retrieve profiles. A future AI service may call these backend APIs, but must respect authentication and authorisation. Today we focus on routes, schemas and validation.

## 9. Common mistakes
| Mistake | Fix |
|---|---|
| Wrong Uvicorn module path | Run from folder containing main.py |
| Forget route decorator | Add @app.get or @app.post |
| Treat path ID as trusted | Validate type and existence |
| No request schema | Define Pydantic model |
| Return 200 for missing record | Raise HTTPException 404 |
| Claim dictionary data is persistent | Explain reset on restart |
| Use global state in production | Use database and concurrency-safe design |

## 10. Exercises
1. Add GET /health.
2. Add GET /students returning all current records.
3. Add minimum length to course.
4. Submit invalid score and inspect validation.
5. Request unknown ID and verify 404.
6. Explain request model versus response model.

## 11. Five-question quiz
1. A route is: A path and method mapping B database C model D variable. **Answer A.**
2. @app.post registers: A GET B POST path operation C class D table. **Answer B.**
3. Pydantic is used for: A request validation B DNS C image generation D SQL engine. **Answer A.**
4. Newly created resource commonly returns: A 200 only B 201 C 404 D 500. **Answer B.**
5. What happens to dictionary storage on restart? A persists B clears C uploads D encrypts. **Answer B.**

## Completion checklist
- [ ] Install FastAPI and Uvicorn in a virtual environment.
- [ ] Run local API and open /docs.
- [ ] Create GET and POST routes.
- [ ] Use path and query parameters.
- [ ] Define Pydantic request and response models.
- [ ] Validate input and return 404 errors.
- [ ] Complete Student Information REST API.

**Next:** Day 10 — SQL fundamentals, relational database concepts, Git, GitHub, virtual environments, pytest and debugging.
