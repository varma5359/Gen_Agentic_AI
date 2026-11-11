# Day 9 — FastAPI, routes, Pydantic models, request validation and response models.

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours  
**Level:** Intermediate

> **Self-learning instruction:** Read one section at a time. Type the code yourself, run it and compare the result. These notes are designed to teach without a trainer or video.

## 1. Understand the topic

FastAPI builds Python APIs and generates OpenAPI documentation. A route maps an HTTP method and path to a function. Path parameters identify resources; query parameters filter. Pydantic models define and validate JSON request bodies. response_model controls public output. An in-memory dictionary is a learning prototype because it resets on restart.

## 2. Why this matters in an AI application

A GenAI application is still software. It needs input handling, business logic, APIs, data, validation, security, tests and deployment. Today's concepts are building blocks for those responsibilities. A small example demonstrates one concept; it is not automatically production-ready.

## 3. Guided coding walkthrough

### Step 1 — Understand the task

Read the code and predict the output. Identify the input, the main operation and the value produced.

### Step 2 — Code

~~~python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel, Field
app = FastAPI()
class StudentCreate(BaseModel):
    name: str = Field(min_length=2)
    email: str
    age: int = Field(ge=16, le=100)
students = {}
next_id = 1
@app.post("/students", status_code=201)
def create_student(student: StudentCreate):
    global next_id
    saved = {"id": next_id, **student.model_dump()}
    students[next_id] = saved
    next_id += 1
    return saved
@app.get("/students/{student_id}")
def get_student(student_id: int):
    if student_id not in students:
        raise HTTPException(status_code=404, detail="Student not found")
    return students[student_id]
~~~

### Step 3 — Expected output

~~~text
POST /students with {"name":"Asha Rao","email":"asha@example.com","age":22} returns 201. GET /students/1 returns 200 when present.
~~~

### Step 4 — Explain the code line by line

- BaseModel defines input structure and validation.
- Field adds constraints.
- The route decorator registers method and path.
- FastAPI validates the request before calling the handler.
- HTTPException returns a deliberate 404.
- Run uvicorn main:app --reload and test /docs; 422 usually indicates invalid input.

### Step 5 — Interpret the result

Answer in your own words: What input did the program receive? What operation did it perform? What result did it produce? What would change if the input changed? What should be validated before using this in a larger application?

## 4. Common mistakes and troubleshooting

- Read the complete traceback and identify the exception type and line.
- Confirm the active Python interpreter, installed packages, current folder and filename.
- Check types, missing values, boundaries and external response formats.
- Reduce a complex failure to the smallest reproducible example.
- Fix the cause rather than hiding errors with broad exception handling.

## 5. Independent practice

1. Recreate the example from a blank file.
2. Change at least two inputs and predict the output before running.
3. Add one validation or failure case relevant to this topic.
4. Explain the changed output in your own words.
5. Save the code in a clearly named project folder.

## 6. Interview-ready summary

- Define the concept directly.
- Explain the problem it solves.
- Explain when to use it and when a simpler approach is better.
- Give one practical AI-application example.
- Mention one limitation or common failure mode.

## 7. Completion checklist

- [ ] I can explain the concept without copying the definition.
- [ ] I typed and ran the example.
- [ ] I understand the expected output.
- [ ] I completed the independent practice.
- [ ] I can identify and fix a common error.
- [ ] I am ready to attempt the approved project.
