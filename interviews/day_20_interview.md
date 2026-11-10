# Day 20 — Interview Preparation: FastAPI and LLM Integration

## Beginner questions

**1. What is FastAPI?**  
A Python framework used to build HTTP APIs.

**2. What is Uvicorn?**  
An ASGI server that runs an ASGI application such as FastAPI.

**3. What is an API endpoint?**  
A URL path and HTTP method that allow a client to perform an operation.

**4. What is the difference between GET and POST?**  
GET is commonly used to retrieve information. POST is commonly used to submit data for processing or creation.

**5. What is Pydantic?**  
A Python library used to define and validate structured data.

## FastAPI questions

**6. What does app = FastAPI() do?**  
It creates the FastAPI application object.

**7. What does @app.get("/") do?**  
It registers a function to handle GET requests to the root path.

**8. What does @app.post("/ask") do?**  
It registers a function to handle POST requests to /ask.

**9. What is a request model?**  
A Pydantic model describing the expected incoming request data.

**10. What is a response model?**  
A model describing the expected response data returned by an endpoint.

**11. What does Field(min_length=1, max_length=4000) do?**  
It sets constraints on a field's accepted string length.

**12. What is HTTPException used for?**  
To return an HTTP error with a status code and detail message.

**13. What does HTTP 422 mean in FastAPI?**  
The request data failed validation, for example because a required field is missing or a value violates a constraint.

**14. What is /docs?**  
FastAPI's automatically generated interactive Swagger UI documentation.

**15. What is /openapi.json?**  
The machine-readable OpenAPI description of the API.

## Architecture questions

**16. Why should the frontend call FastAPI instead of calling the LLM directly with a private key?**  
The backend can keep the key secret, validate inputs, apply access controls and handle provider errors.

**17. Why separate route code from LLM service code?**  
It separates HTTP concerns from provider integration, making the application easier to test, maintain and reuse.

**18. What does app.main:app mean in the Uvicorn command?**  
Import the app package's main module and run the variable named app inside it.

**19. Why set a timeout on the provider client?**  
So the backend does not wait indefinitely for a slow provider response.

**20. Why should the API return a structured response?**  
A predictable response shape makes it easier for frontend applications and other services to consume the result.

## Scenario-based questions

**21. The API returns 422 before calling the LLM. What should you inspect?**  
The request body and Pydantic constraints. FastAPI may reject invalid input before the route function runs.

**22. The frontend developer asks you to put the API key in JavaScript. What do you say?**  
A private key must remain on the backend. The frontend should call the backend endpoint, which then calls the LLM provider.

**23. Your uvicorn app.main:app --reload command cannot import the module. What should you check?**  
Confirm current working directory, package structure, __init__.py files where needed, installed dependencies and module path.

**24. Why should an API not return HTTP 200 when the provider call failed?**  
The status should accurately represent the result. A success status with a fabricated answer misleads the client.

**25. What would you add before production deployment?**  
Authentication and authorization, input limits, rate limiting, comprehensive provider error handling, logging without secrets, tests, monitoring, secure secret management and deployment configuration.

## Quick revision

| Topic | Key point |
|---|---|
| FastAPI | Python API framework |
| Uvicorn | ASGI server |
| Route | HTTP method + path |
| Pydantic | Data validation |
| Request model | Expected input shape |
| Response model | Expected output shape |
| HTTPException | Return an HTTP error |
| 422 | Request validation failure |
| /docs | Interactive API documentation |
| Backend key storage | Keeps private credentials away from browsers |
