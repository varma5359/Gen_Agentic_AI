# Day 09 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** FastAPI, Routes, Pydantic Models, Request Validation and Response Models  
**Mini-project:** Student Information REST API  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain fastapi application.

**Beginner answer:** FastAPI is a Python framework for building web APIs. A route connects an HTTP request to a Python function.

**Example code**

```python
# Install: python -m pip install fastapi uvicorn
from fastapi import FastAPI
app = FastAPI()
@app.get("/")
def home():
    return {"message": "Welcome"}
```

**Expected output**

```text
GET / returns JSON: {"message":"Welcome"}
```

**How it works:** FastAPI() creates the application. @app.get registers a route. The function runs for a matching request.

**Important methods or syntax:** Run with: uvicorn main:app --reload. Visit /docs to inspect interactive API documentation.

**Common mistake:** The command main:app means file main.py and variable app. Check the current folder and active environment if import fails.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain path parameters.

**Beginner answer:** A path parameter is part of the URL and identifies a particular resource.

**Example code**

```python
from fastapi import FastAPI
app = FastAPI()
@app.get("/students/{student_id}")
def get_student(student_id: int):
    return {"student_id": student_id}
```

**Expected output**

```text
GET /students/101 returns {"student_id":101}
```

**How it works:** FastAPI extracts 101 from the URL and converts it to int using the annotation.

**Important methods or syntax:** Use path parameters for identifiers such as /students/101 or /orders/500.

**Common mistake:** Invalid integer text fails validation. The route path parameter name must match the function parameter.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain query parameters.

**Beginner answer:** Query parameters follow ? in a URL and are useful for optional filtering and pagination.

**Example code**

```python
from fastapi import FastAPI
app = FastAPI()
@app.get("/students")
def list_students(department: str = "CSE", limit: int = 10):
    return {"department": department, "limit": limit}
```

**Expected output**

```text
/students?department=ECE&limit=5 returns {"department":"ECE","limit":5}
```

**How it works:** FastAPI maps query-string values to function parameters and converts their types.

**Important methods or syntax:** Defaults, optional values, limit/offset pagination and validation constraints.

**Common mistake:** Do not accept unlimited page sizes. Validate user-controlled values and set safe defaults.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain pydantic request models.

**Beginner answer:** Pydantic models describe and validate structured data. FastAPI uses them to validate JSON request bodies.

**Example code**

```python
from fastapi import FastAPI
from pydantic import BaseModel
app = FastAPI()
class StudentCreate(BaseModel):
    name: str
    age: int
@app.post("/students")
def create_student(student: StudentCreate):
    return {"name": student.name, "age": student.age}
```

**Expected output**

```text
POST body {"name":"Anu","age":20} returns validated fields.
```

**How it works:** BaseModel declares the schema. FastAPI parses JSON and validates it before calling the endpoint.

**Important methods or syntax:** Field constraints, optional fields, nested models and separate create/update schemas.

**Common mistake:** Missing or invalid fields produce validation errors. Validation does not automatically save data to a database.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain response models.

**Beginner answer:** A response model defines the shape of the data returned by an endpoint.

**Example code**

```python
from fastapi import FastAPI
from pydantic import BaseModel
app = FastAPI()
class StudentOut(BaseModel):
    id: int
    name: str
@app.get("/student", response_model=StudentOut)
def student():
    return {"id": 1, "name": "Anu", "internal_note": "private"}
```

**Expected output**

```text
Response contains id and name; the undeclared internal_note is excluded by response filtering.
```

**How it works:** response_model documents and validates the response shape and helps avoid returning undeclared fields.

**Important methods or syntax:** Separate database models, request schemas and public response schemas. Configure serialization intentionally.

**Common mistake:** A response that cannot satisfy the schema causes a response validation error. Do not expose secrets in public models.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain api structure and dependency basics.

**Beginner answer:** A small API can begin in one file. As it grows, separate routes, schemas and services. Dependencies provide reusable components.

**Example code**

```python
from fastapi import FastAPI, Depends
app = FastAPI()
def get_version():
    return "1.0"
@app.get("/version")
def version(value: str = Depends(get_version)):
    return {"version": value}
```

**Expected output**

```text
{"version":"1.0"}
```

**How it works:** Depends() tells FastAPI to obtain the value from get_version(). The route receives the result as value.

**Important methods or syntax:** Routers, dependency injection, configuration, service layers and database sessions.

**Common mistake:** Do not put all business logic inside route functions as the application grows. Keep dependencies testable.

**Follow-up:** Where would you use this in a Python AI application?



## 2. Understanding questions

1. Explain today's topic to a person who has never programmed.
2. Why is this concept useful in a real application?
3. What happens when the input is empty or invalid?
4. How would you make the example easier to read?
5. How would you test that the code works?
6. Which line would you change if the requirement changed?
7. What is one limitation of the beginner example?
8. How could this concept be used in a GenAI application?

## 3. Practical coding tasks

### Exercise 1 — FastAPI application

**Task:** Create /health and return a simple status object.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — Path parameters

**Task:** Create /courses/{course_id} and test a valid and invalid value.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Query parameters

**Task:** Call the route with and without query parameters and explain the defaults.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Pydantic request models

**Task:** Send a valid JSON body, then omit age and inspect the validation response.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Response models

**Task:** Add a private field to returned data and verify it is not included in the response.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — API structure and dependency basics

**Task:** Move student routes into an APIRouter and include it in the main application.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — Student Information REST API

Be ready to explain:

1. What problem does the project solve?
2. Who would use it?
3. What input does it accept?
4. What processing does it perform?
5. What output does it produce?
6. Which Python concepts did you apply?
7. What error cases did you consider?
8. How did you test the project?
9. What would you improve next?
10. How could it become one component of a larger AI application?

## 5. Mock interview

**Interviewer:** Explain the main topic you learned today.

**Student:** Give a definition, describe the steps and show a small example.

**Interviewer:** Why did you choose this Python feature?

**Student:** Explain the problem it solves and why it is suitable.

**Interviewer:** What happens if the input is incorrect?

**Student:** Explain the likely error and how you would validate or handle the input.

**Interviewer:** How did you verify your program?

**Student:** Explain the test input, expected output, actual output and correction.

## 6. Communication checklist

- [ ] I answer the question directly.
- [ ] I explain technical words simply.
- [ ] I give a relevant example.
- [ ] I can read my code line by line.
- [ ] I can explain one error case.
- [ ] I can describe my mini-project honestly.

## 7. Self-assessment

| Skill | Rating |
|---|---:|
| Explain the concepts | /5 |
| Read the code | /5 |
| Write a small example | /5 |
| Debug an error | /5 |
| Explain the mini-project | /5 |
| Answer interview follow-ups | /5 |

**Trainer note:** A student is ready to move forward when they can explain the concept, modify a working example and solve a small task without copying the complete solution.
