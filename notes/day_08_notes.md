# Day 08 — REST APIs, HTTP Methods, Status Codes, Headers, Requests and Responses

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** External API Integration Client  
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

1. Explain api and client-server model using a simple example.
2. Explain http methods using a simple example.
3. Explain status code families using a simple example.
4. Explain headers and json bodies using a simple example.
5. Explain calling apis with requests using a simple example.
6. Explain api reliability and security using a simple example.
7. Apply api and client-server model in the External API Integration Client.
8. Apply http methods in the External API Integration Client.
9. Apply status code families in the External API Integration Client.
10. Apply headers and json bodies in the External API Integration Client.
11. Apply calling apis with requests in the External API Integration Client.
12. Apply api reliability and security in the External API Integration Client.

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

## 3. API and client-server model

### Beginner explanation

An API is a documented way for software components to communicate. A web API commonly uses HTTP.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

The client sends a request. The server processes it and returns a response. This sample only represents the idea.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Endpoint, resource, client, server, request body, response body and API documentation.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

An API is not necessarily a web page. Many APIs return JSON for another program to consume.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Draw the request-response flow for a mobile app retrieving a student profile.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define api and client-server model in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. HTTP methods

### Beginner explanation

HTTP methods describe what a client wants to do with a resource.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

GET commonly reads; POST commonly creates or submits; PUT commonly replaces; PATCH partially updates; DELETE requests removal.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Safe and idempotent method concepts, method semantics and API-specific contracts.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not assume all APIs implement methods identically. Read the API documentation. Never put secrets in URL query strings.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Choose a method for listing, creating, replacing, partially updating and deleting a student.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define http methods in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Status code families

### Beginner explanation

Status codes tell a client the broad result of a request.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

2xx indicates success; 3xx redirection; 4xx client/request issue; 5xx server issue.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Know 200, 201, 204, 400, 401, 403, 404, 409, 422, 429 and 500.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

401 usually concerns authentication; 403 means access is refused. 429 often signals rate limiting. Follow the API contract.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Match common API situations to suitable status code families.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define status code families in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Headers and JSON bodies

### Beginner explanation

Headers carry metadata. A JSON body carries structured data sent with a request or response.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

Accept describes a response format the client can process. Content-Type describes the body format being sent.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Authorization headers, caching headers, content negotiation and correlation IDs.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Keep API keys out of source code. Use HTTPS and the authentication scheme required by the service.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Describe a POST request with a JSON body and appropriate headers.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define headers and json bodies in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Calling APIs with requests

### Beginner explanation

requests is a synchronous HTTP client. Check status and parse response data carefully.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

get() sends the request. timeout limits waiting. raise_for_status() raises for unsuccessful HTTP status. json() parses the body.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

params= for query values, json= for JSON bodies, headers= for headers, Session() for connection reuse.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A response may not contain JSON. Catch RequestException and JSON decoding errors when appropriate.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write a function that calls a public test endpoint and returns one selected field.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define calling apis with requests in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. API reliability and security

### Beginner explanation

A robust API client handles expected failures and protects credentials.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

getenv() reads an environment variable. The example does not print the secret itself.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Timeouts, bounded retries, exponential backoff, status validation, safe logs and environment configuration.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Never print or commit API keys. Do not retry every error blindly; distinguish transient failures from invalid requests.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Add timeout and error handling to your API client. Test missing configuration.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define api reliability and security in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 9. Guided mini-project — External API Integration Client

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
day_08_project/
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

1. What is api and client-server model?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is http methods?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is status code families?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is headers and json bodies?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is calling apis with requests?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is api reliability and security?
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

1. Explain api and client-server model to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain http methods to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain status code families to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain headers and json bodies to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain calling apis with requests to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain api reliability and security to a beginner.
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

**Day 8 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.
