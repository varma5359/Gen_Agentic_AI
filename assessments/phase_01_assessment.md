# Phase 1 Assessment — Python and Software Development Foundations

**Approved phase:** Days 1–10  
**Assessment project:** Python AI Application Backend  
**Suggested duration:** 3–4 hours

## 1. Business scenario

A training company needs a student-record service. Staff should add student records, retrieve a record and list records. The service must validate input, store records persistently and return useful errors.

## 2. Requirements

- Build a Python application separating API routes, business logic and database access.
- Use FastAPI and Pydantic for HTTP input validation.
- Use SQLite for persistence.
- Use parameterized SQL for every query.
- Add pytest tests for core operations.
- Use logging without recording private data.
- Use Git and include a README.
- Keep credentials, virtual environments and unnecessary local artifacts out of version control.

## 3. Expected endpoints

| Method | Endpoint | Behaviour |
|---|---|---|
| POST | /students | Validate and create; return 201 |
| GET | /students/{student_id} | Return one record; return 404 if missing |
| GET | /students | Return all records |

Suggested fields: name, email and age. Define suitable validation constraints and a unique email rule.

## 4. Ordered implementation tasks

1. Create and activate a virtual environment.
2. Install FastAPI, Uvicorn and pytest.
3. Create a students table with a primary key and constraints.
4. Implement repository functions for create, retrieve and list.
5. Define request and response Pydantic models.
6. Implement API routes and deliberate HTTP error responses.
7. Add safe logging.
8. Write tests using a temporary database.
9. Run tests and inspect the interactive API documentation.
10. Document setup, commands, endpoint examples, tests and limitations.

## 5. Required evidence

- Project structure and README.
- Successful POST and GET responses.
- Example validation failure and 404 response.
- Pytest output.
- Git status and commit history.
- Short explanation of architecture and design decisions.

## 6. Evaluation rubric

| Dimension | Weight |
|---|---:|
| Conceptual understanding | 20% |
| Practical correctness | 30% |
| Problem-solving and reasoning | 20% |
| Quality and maintainability | 15% |
| Testing and validation | 10% |
| Communication and evidence | 5% |
| **Total** | **100%** |

## 7. Common mistakes

- Concatenating user input into SQL.
- Returning unvalidated request data.
- Mixing database logic into every route.
- Tests sharing persistent state and depending on execution order.
- Missing or misleading HTTP status codes.
- Committing secrets or .venv.
- Omitting setup instructions.
- Calling a prototype production-ready without authentication, authorization, migrations and deployment hardening.

## 8. Phase interview questions

1. How did you separate API routes from database operations?
2. Why did you use Pydantic models?
3. How do parameterized queries help prevent SQL injection?
4. Explain 400, 401, 403, 404 and 500.
5. How would you test an endpoint without modifying a real database?
6. What would you add before exposing the application to real users?

## 9. Completion standard

The phase is complete when the application runs, required tests pass, evidence is documented and the learner can explain the design decisions without merely reading the code. Record incomplete requirements honestly and fix them before moving to Phase 2.
