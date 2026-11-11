# Day 8 — REST APIs, HTTP methods, status codes, headers, requests and responses

**Phase 1 | 2–3 hours | Project: External API Integration Client**

## Learning objectives
Explain API and REST-style resource concepts; describe request/response components; use HTTP methods; understand status families; send query parameters and JSON; handle errors and timeouts.

## 1. What is an API?
An API is a defined interface through which one software system requests data or capabilities from another. A REST-style web API commonly exposes resources through URLs and uses HTTP methods to describe operations.

## 2. Request-response flow
~~~text
Python client
  | HTTP request: method + URL + headers + optional body
  v
API server
  | HTTP response: status + headers + body
  v
Python client parses and handles result
~~~

Request components:
- Method: GET, POST, PUT, PATCH or DELETE.
- URL: target resource.
- Headers: metadata such as content type and authorization.
- Query parameters: filters or pagination.
- Body: optional data, often JSON.

Response components: status code, headers and body.

## 3. HTTP methods
| Method | Common intent | Example |
|---|---|---|
| GET | Read resource | Retrieve student |
| POST | Create/submit | Create student |
| PUT | Replace resource | Replace profile |
| PATCH | Partially update | Change one field |
| DELETE | Request removal | Delete record |

Actual behaviour depends on the API's documented contract.

## 4. Status code families
| Range | Meaning |
|---|---|
| 2xx | Success |
| 3xx | Redirection |
| 4xx | Client request/authentication issue |
| 5xx | Server-side failure |

Common examples: 200 OK, 201 Created, 204 No Content, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 422 validation issue, 429 rate limited, 500 Internal Server Error.

HTTP success does not prove business data is correct. Validate response shape and meaning.

## 5. Headers and content types
Content-Type describes the body format, commonly application/json. Accept indicates response formats the client accepts. Authorization carries credentials where required. Never paste a real token into source code or logs.

## 6. Query and path parameters
A path parameter identifies a resource, such as /posts/12. A query parameter filters a collection, such as /posts?userId=3.

~~~python
import requests

response = requests.get(
    "https://jsonplaceholder.typicode.com/posts",
    params={"userId": 1},
    timeout=10
)
response.raise_for_status()
posts = response.json()
print(len(posts))
~~~

params encodes query values. timeout bounds waiting. raise_for_status raises for unsuccessful HTTP status. json parses the response.

## 7. POST JSON
~~~python
payload = {"title": "Learn APIs", "body": "Practice requests", "userId": 1}
response = requests.post(
    "https://jsonplaceholder.typicode.com/posts",
    json=payload,
    timeout=10
)
response.raise_for_status()
print(response.json())
~~~

json serializes the Python object and sets the appropriate content type. The public test service may simulate creation rather than persist data permanently.

## 8. PUT, PATCH and DELETE
PUT commonly replaces a resource; PATCH partially updates; DELETE requests removal. Inspect API documentation and status codes. Do not assume every API implements all methods.

## 9. Robust client checklist
1. Set base URL.
2. Set timeout.
3. Send documented method and parameters.
4. Check status.
5. Parse response.
6. Validate expected fields.
7. Handle timeout, connection and HTTP errors.
8. Protect credentials.

## 10. Common errors
| Problem | Likely cause | Action |
|---|---|---|
| 401 | Missing/invalid authentication | Check credential setup |
| 403 | Insufficient permission | Check access rights |
| 404 | Wrong path or ID | Verify endpoint |
| 429 | Rate limit | Respect retry guidance |
| 5xx | Server-side failure | Log safe details; bounded retry if appropriate |
| JSONDecodeError | Invalid/non-JSON body | Check response content type |
| Timeout | Slow server/network | Handle timeout |

## 11. Exercises
1. GET from a public test API.
2. Filter using query parameters.
3. Submit JSON using POST.
4. Print status and content type.
5. Handle timeout and HTTP errors.
6. Explain path versus query parameters.
7. Explain why status 200 alone does not prove business correctness.

## 12. Five-question quiz
1. Read a resource: A GET B POST C DELETE D PATCH. **Answer A.**
2. Not Found: A 200 B 401 C 404 D 500. **Answer C.**
3. Filtering values commonly go in: A query string B comment C file name D status. **Answer A.**
4. Content-Type describes: A body format B user role C host D method. **Answer A.**
5. 429 means: A Created B Rate limited C Missing D Redirect. **Answer B.**

## Completion checklist
- [ ] Explain API and REST-style resources.
- [ ] Identify request and response parts.
- [ ] Explain GET/POST/PUT/PATCH/DELETE.
- [ ] Read status code families.
- [ ] Use headers and query parameters.
- [ ] Send JSON and parse responses.
- [ ] Handle timeouts and errors.
- [ ] Complete External API Integration Client.

**Next:** Day 9 — FastAPI, routes, Pydantic models, request validation and response models.
