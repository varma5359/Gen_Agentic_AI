# Day 8 Interview Guide — REST APIs and HTTP

## Q1. What is an API?
A defined interface that lets software systems communicate. A web API commonly receives HTTP requests and returns HTTP responses. Not every API is REST.

## Q2. Explain GET, POST, PUT, PATCH and DELETE.
GET retrieves; POST commonly creates/submits; PUT commonly replaces; PATCH partially updates; DELETE requests removal. The API contract determines exact behaviour.

## Q3. What are HTTP headers?
They carry request/response metadata such as Content-Type, Accept, caching instructions and authorization. Never log authorization tokens.

## Q4. Path versus query parameter?
A path parameter identifies a resource, e.g. /posts/12. A query parameter filters or modifies a request, e.g. /posts?userId=3. Query parameters are often used for pagination.

## Q5. Explain common status codes.
200 success, 201 created, 204 no content, 400 bad request, 401 unauthenticated, 403 forbidden, 404 missing, 409 conflict, 422 validation issue, 429 rate limited, 500 server error. 401 and 403 are not the same.

## Q6. Why set a timeout?
It bounds waiting and protects resources. A client timeout does not prove the server did not process a POST.

## Q7. Why call raise_for_status()?
It raises for unsuccessful status codes so error responses are not mistaken for normal success. Not every error should be retried.

## Q8. How validate an API response?
Check status, content type, JSON parsing, expected top-level type, required keys and business constraints. Valid JSON alone does not guarantee valid business data.

## Practical task
Write a GET client with query parameters and timeout, parse JSON, validate the structure and handle HTTP/network errors.
