# Day 9 Interview Guide — FastAPI and Pydantic

## Q1. What is FastAPI?
A Python framework for HTTP APIs. It maps requests to path-operation functions, supports type-based validation and generates OpenAPI documentation. Uvicorn commonly runs it as an ASGI server.

## Q2. What is a route?
A URL path and HTTP method mapped to a function. GET /students retrieves; POST /students creates. The same path can support multiple methods.

## Q3. Path versus query parameter?
A path parameter is part of the route, such as /students/10. A query parameter follows ?, such as /students?course=Python. Query parameters are useful for filters and pagination.

## Q4. What is Pydantic?
A validation library used by FastAPI to parse request data against declared models and constraints. Invalid input produces a validation error response.

## Q5. Request model versus response model?
A request model describes accepted input. A response model describes and validates the output shape. Separate models help avoid exposing internal fields.

## Q6. Why use HTTPException?
It allows a route to return an intentional status and detail, such as 404 when a student does not exist. Missing data should not normally be returned as a successful 200.

## Q7. What is the limitation of in-memory storage?
It is lost when the process restarts and is not reliably shared between multiple workers. A production service uses a database and appropriate transaction/concurrency handling.

## Q8. What does Uvicorn do?
It is an ASGI server that runs the FastAPI application. --reload is a development convenience, not a normal production setting.

## Practical task
Design a POST endpoint with a Pydantic model, validate a numeric range and return 201. Explain what happens for invalid input.
