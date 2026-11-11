# Day 9 Project — Student Information REST API

## Objective
Build a FastAPI service to create and retrieve student records with request validation and response schemas. The first version uses in-memory storage, not a production database.

## Setup
Create and activate a virtual environment:
~~~bash
python -m venv .venv
~~~
Install:
~~~bash
python -m pip install fastapi uvicorn
~~~

## Create main.py
~~~python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel, Field

app = FastAPI(title="TechPhile Student Information API")
students = {}
next_id = 1

class StudentCreate(BaseModel):
    name: str = Field(min_length=2, max_length=60)
    email: str
    course: str = Field(min_length=2, max_length=80)
    score: float = Field(ge=0, le=100)

class StudentResponse(BaseModel):
    id: int
    name: str
    email: str
    course: str
    score: float

@app.get("/health")
def health():
    return {"status": "ok"}

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

@app.get("/students")
def list_students():
    return list(students.values())
~~~

## Run
~~~bash
uvicorn main:app --reload
~~~
Open /docs on the local server and use Try it out.

POST body:
~~~json
{
  "name": "Asha",
  "email": "asha@example.test",
  "course": "GenAI",
  "score": 88
}
~~~
Expected: 201 with an id and validated fields.

## Test cases
| Test | Request | Expected |
|---|---|---|
| TC01 | GET /health | 200 and status ok |
| TC02 | POST valid student | 201 |
| TC03 | GET /students/1 after create | 200 |
| TC04 | GET /students/999 | 404 |
| TC05 | POST score 120 | Validation error |
| TC06 | POST one-character name | Validation error |
| TC07 | GET /students | List of records |

## Important limitations
- Dictionary data disappears when server restarts.
- Global integer ID is only a single-process teaching example.
- Email is a string here; production validation should verify format and ownership.
- There is no authentication or authorisation. Do not expose this demo with real student data.

## Extensions
1. Add PATCH to update a field.
2. Add DELETE.
3. Add response model for list.
4. Add pytest tests after Day 10.
5. Draw request → validation → route → response.

## Submission
Submit main.py, API request/response evidence, test table and a paragraph describing in-memory storage limitations.
