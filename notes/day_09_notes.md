# Day 09 — FastAPI, Routes, Pydantic Models, Request Validation and Response Models

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** Student Information REST API  
**Duration:** 2–3 hours  
**Audience:** College students and freshers  
**Level:** Beginner first, intermediate only after the basics

## How to use these notes

These notes assume that you may be learning the topic for the first time. You do not need to understand everything in one sitting.

1. Read the beginner explanation.
2. Type the code yourself. Do not only copy and paste.
3. Predict the output before running the code.
4. Run it and compare your prediction.
5. Change one value and run it again.
6. Explain the code in your own words.
7. Complete the practice task without looking at a solution.
8. Practise the interview question aloud.

**Teaching rule:** never introduce a complicated framework example before the student understands the plain Python operation underneath it.

## 1. Learning objectives

1. Explain fastapi application using a simple example.
2. Explain path parameters using a simple example.
3. Explain query parameters using a simple example.
4. Explain pydantic request models using a simple example.
5. Explain response models using a simple example.
6. Explain api structure and dependency basics using a simple example.
7. Apply fastapi application in the Student Information REST API.
8. Apply path parameters in the Student Information REST API.
9. Apply query parameters in the Student Information REST API.
10. Apply pydantic request models in the Student Information REST API.
11. Apply response models in the Student Information REST API.
12. Apply api structure and dependency basics in the Student Information REST API.

## 2. Important vocabulary

| Term | Beginner meaning |
|---|---|
| Syntax | Rules for writing valid Python |
| Variable | A name referring to a value |
| Function | Reusable code that performs a task |
| Method | A function associated with an object |
| Argument | A value passed when calling a function |
| Return value | A result sent back to the caller |
| Exception | An event that interrupts normal execution |
| Debugging | Finding and fixing the cause of a problem |
| Input | Information supplied to a program |
| Output | Information produced by a program |

## 3. Class plan

| Activity | Time |
|---|---:|
| Concept explanation | 30–40 minutes |
| Trainer demonstration | 35–45 minutes |
| Student coding practice | 45–60 minutes |
| Mini-project | 30–40 minutes |
| Quiz and interview practice | 15–20 minutes |

## 3. FastAPI application

### Beginner explanation

FastAPI is a Python framework for building web APIs. A route connects an HTTP request to a Python function.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

FastAPI() creates the application. @app.get registers a route. The function runs for a matching request.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Run with: uvicorn main:app --reload. Visit /docs to inspect interactive API documentation.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

The command main:app means file main.py and variable app. Check the current folder and active environment if import fails.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create /health and return a simple status object.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define fastapi application in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. Path parameters

### Beginner explanation

A path parameter is part of the URL and identifies a particular resource.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

FastAPI extracts 101 from the URL and converts it to int using the annotation.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Use path parameters for identifiers such as /students/101 or /orders/500.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Invalid integer text fails validation. The route path parameter name must match the function parameter.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create /courses/{course_id} and test a valid and invalid value.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define path parameters in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Query parameters

### Beginner explanation

Query parameters follow ? in a URL and are useful for optional filtering and pagination.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

FastAPI maps query-string values to function parameters and converts their types.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Defaults, optional values, limit/offset pagination and validation constraints.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not accept unlimited page sizes. Validate user-controlled values and set safe defaults.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Call the route with and without query parameters and explain the defaults.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define query parameters in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Pydantic request models

### Beginner explanation

Pydantic models describe and validate structured data. FastAPI uses them to validate JSON request bodies.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

BaseModel declares the schema. FastAPI parses JSON and validates it before calling the endpoint.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Field constraints, optional fields, nested models and separate create/update schemas.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Missing or invalid fields produce validation errors. Validation does not automatically save data to a database.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Send a valid JSON body, then omit age and inspect the validation response.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define pydantic request models in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Response models

### Beginner explanation

A response model defines the shape of the data returned by an endpoint.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

response_model documents and validates the response shape and helps avoid returning undeclared fields.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Separate database models, request schemas and public response schemas. Configure serialization intentionally.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A response that cannot satisfy the schema causes a response validation error. Do not expose secrets in public models.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Add a private field to returned data and verify it is not included in the response.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define response models in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. API structure and dependency basics

### Beginner explanation

A small API can begin in one file. As it grows, separate routes, schemas and services. Dependencies provide reusable components.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

Depends() tells FastAPI to obtain the value from get_version(). The route receives the result as value.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Routers, dependency injection, configuration, service layers and database sessions.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not put all business logic inside route functions as the application grows. Keep dependencies testable.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Move student routes into an APIRouter and include it in the main application.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define api structure and dependency basics in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 9. Guided mini-project — Student Information REST API

## Business situation

A beginner AI application developer must be able to organize information, process it and explain what the program does. In this project, build a small working program using only concepts covered in today's lesson.

## Requirements

- Create a project folder and a Python file.
- Define small sample data.
- Apply at least three concepts from this lesson.
- Display a clear result.
- Handle one invalid or missing value where appropriate.
- Use meaningful variable names.
- Explain the program line by line.

## Suggested folder structure

```text
day_09_project/
    main.py
    README.md
    sample_data/
```

## Build in small steps

1. Create main.py.
2. Add two or three sample records.
3. Write one small operation.
4. Run the program and inspect the output.
5. Add the next operation only after the first works.
6. Test an unusual input.
7. Explain input, processing and output to your trainer.

## Student submission checklist

- [ ] Program runs without syntax errors.
- [ ] I can explain every line I wrote.
- [ ] I used meaningful names.
- [ ] I tested a normal input.
- [ ] I tested an unusual input.
- [ ] I can explain one limitation.
- [ ] I saved the project in the correct folder.

# 10. Daily revision questions

1. What is fastapi application?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is path parameters?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is query parameters?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is pydantic request models?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is response models?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is api structure and dependency basics?
6.1 Why would a Python developer use it?
6.2 What mistake should a beginner avoid?

# 11. Daily quiz

1. Which concept from today's lesson would you use for the sample problem?
2. What does the main method or function in one example do?
3. What happens if the input is missing or invalid?
4. Why should code be divided into small understandable steps?
5. Give one use of today's concepts in an AI application.

**Answer method:** answer in your own words, then prove your understanding with a small code example.

# 12. Interview practice

1. Explain fastapi application to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain path parameters to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain query parameters to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain pydantic request models to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain response models to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain api structure and dependency basics to a beginner.
6.1 Give a practical example.
6.2 What is one limitation or common error?

## How to structure an interview answer

1. Give a direct definition.
2. Explain how it works in two or three steps.
3. Give a small example.
4. Mention one real use.
5. Mention one limitation or error case.

# 13. Trainer assessment rubric

| Area | Evidence |
|---|---|
| Concept understanding | Student explains without reading |
| Code reading | Student describes important lines |
| Practical execution | Student runs and modifies code |
| Debugging | Student locates a simple error |
| Project | Student applies the day's concepts |
| Interview communication | Student gives a clear structured answer |

# 14. What you should remember

- Understand why a feature is used before memorizing syntax.
- Type and run each example yourself.
- Know the difference between a function, method, argument and return value.
- Read error messages instead of guessing.
- Build the project in small steps.
- Be ready to teach the concept to another beginner.

**Day 9 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.
