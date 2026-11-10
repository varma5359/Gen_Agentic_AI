# Day 08 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** REST APIs, HTTP Methods, Status Codes, Headers, Requests and Responses  
**Mini-project:** External API Integration Client  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain api and client-server model.

**Beginner answer:** An API is a documented way for software components to communicate. A web API commonly uses HTTP.

**Example code**

```python
client = "Student Portal"
server = "College API"
request = {"method": "GET", "resource": "/students"}
print(client, "asks", server)
print(request)
```

**Expected output**

```text
Student Portal asks College API
{'method': 'GET', 'resource': '/students'}
```

**How it works:** The client sends a request. The server processes it and returns a response. This sample only represents the idea.

**Important methods or syntax:** Endpoint, resource, client, server, request body, response body and API documentation.

**Common mistake:** An API is not necessarily a web page. Many APIs return JSON for another program to consume.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain http methods.

**Beginner answer:** HTTP methods describe what a client wants to do with a resource.

**Example code**

```python
methods = ["GET", "POST", "PUT", "PATCH", "DELETE"]
for method in methods:
    print(method)
```

**Expected output**

```text
GET
POST
PUT
PATCH
DELETE
```

**How it works:** GET commonly reads; POST commonly creates or submits; PUT commonly replaces; PATCH partially updates; DELETE requests removal.

**Important methods or syntax:** Safe and idempotent method concepts, method semantics and API-specific contracts.

**Common mistake:** Do not assume all APIs implement methods identically. Read the API documentation. Never put secrets in URL query strings.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain status code families.

**Beginner answer:** Status codes tell a client the broad result of a request.

**Example code**

```python
codes = {200:"OK", 201:"Created", 400:"Bad Request", 401:"Unauthorized", 403:"Forbidden", 404:"Not Found", 500:"Server Error"}
for code, label in codes.items():
    print(code, label)
```

**Expected output**

```text
200 OK
201 Created
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
500 Server Error
```

**How it works:** 2xx indicates success; 3xx redirection; 4xx client/request issue; 5xx server issue.

**Important methods or syntax:** Know 200, 201, 204, 400, 401, 403, 404, 409, 422, 429 and 500.

**Common mistake:** 401 usually concerns authentication; 403 means access is refused. 429 often signals rate limiting. Follow the API contract.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain headers and json bodies.

**Beginner answer:** Headers carry metadata. A JSON body carries structured data sent with a request or response.

**Example code**

```python
headers = {"Accept":"application/json", "Content-Type":"application/json"}
payload = {"name":"Anu", "department":"CSE"}
print(headers["Content-Type"])
print(payload["name"])
```

**Expected output**

```text
application/json
Anu
```

**How it works:** Accept describes a response format the client can process. Content-Type describes the body format being sent.

**Important methods or syntax:** Authorization headers, caching headers, content negotiation and correlation IDs.

**Common mistake:** Keep API keys out of source code. Use HTTPS and the authentication scheme required by the service.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain calling apis with requests.

**Beginner answer:** requests is a synchronous HTTP client. Check status and parse response data carefully.

**Example code**

```python
# Install: python -m pip install requests
import requests
response = requests.get("https://httpbin.org/get", timeout=10)
print(response.status_code)
response.raise_for_status()
data = response.json()
print(data["url"])
```

**Expected output**

```text
200
https://httpbin.org/get
```

**How it works:** get() sends the request. timeout limits waiting. raise_for_status() raises for unsuccessful HTTP status. json() parses the body.

**Important methods or syntax:** params= for query values, json= for JSON bodies, headers= for headers, Session() for connection reuse.

**Common mistake:** A response may not contain JSON. Catch RequestException and JSON decoding errors when appropriate.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain api reliability and security.

**Beginner answer:** A robust API client handles expected failures and protects credentials.

**Example code**

```python
import os
api_key = os.getenv("DEMO_API_KEY")
if not api_key:
    print("API key is not configured")
else:
    print("API key is available")
```

**Expected output**

```text
API key is not configured (when the environment variable is absent)
```

**How it works:** getenv() reads an environment variable. The example does not print the secret itself.

**Important methods or syntax:** Timeouts, bounded retries, exponential backoff, status validation, safe logs and environment configuration.

**Common mistake:** Never print or commit API keys. Do not retry every error blindly; distinguish transient failures from invalid requests.

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

### Exercise 1 — API and client-server model

**Task:** Draw the request-response flow for a mobile app retrieving a student profile.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — HTTP methods

**Task:** Choose a method for listing, creating, replacing, partially updating and deleting a student.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Status code families

**Task:** Match common API situations to suitable status code families.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Headers and JSON bodies

**Task:** Describe a POST request with a JSON body and appropriate headers.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Calling APIs with requests

**Task:** Write a function that calls a public test endpoint and returns one selected field.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — API reliability and security

**Task:** Add timeout and error handling to your API client. Test missing configuration.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — External API Integration Client

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
