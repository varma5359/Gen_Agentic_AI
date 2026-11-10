# Day 07 — Asynchronous Python: async, await, asyncio, HTTP Fundamentals and Concurrent API Requests

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** Asynchronous API Data Fetcher  
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

1. Explain synchronous execution using a simple example.
2. Explain coroutines: async and await using a simple example.
3. Explain concurrent tasks using a simple example.
4. Explain http request-response basics using a simple example.
5. Explain async http with httpx using a simple example.
6. Explain concurrency limits and safe design using a simple example.
7. Apply synchronous execution in the Asynchronous API Data Fetcher.
8. Apply coroutines: async and await in the Asynchronous API Data Fetcher.
9. Apply concurrent tasks in the Asynchronous API Data Fetcher.
10. Apply http request-response basics in the Asynchronous API Data Fetcher.
11. Apply async http with httpx in the Asynchronous API Data Fetcher.
12. Apply concurrency limits and safe design in the Asynchronous API Data Fetcher.

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

## 3. Synchronous execution

### Beginner explanation

Synchronous code waits for one operation to finish before starting the next operation.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
import time
def task(name):
    print("Start", name)
    time.sleep(1)
    print("End", name)
task("A")
task("B")
```

**Expected output**

```text
Start A
End A
Start B
End B
```

### Walkthrough

task B starts after task A completes. sleep() blocks the current thread.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Use synchronous code for simple scripts and libraries that do not need concurrency.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not assume async makes CPU-heavy calculations faster. Blocking calls can stall an event loop.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Predict the order of two synchronous tasks.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define synchronous execution in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. Coroutines: async and await

### Beginner explanation

async def defines a coroutine function. await pauses that coroutine while an awaitable operation completes.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
import asyncio
async def greet():
    print("Hello")
    await asyncio.sleep(1)
    print("Welcome back")
asyncio.run(greet())
```

**Expected output**

```text
Hello
Welcome back
```

### Walkthrough

Calling greet() creates a coroutine. asyncio.run() starts an event loop and runs it to completion.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

async def, await, asyncio.run(), asyncio.sleep() and coroutine objects.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Calling a coroutine without awaiting or scheduling it means it may never execute and can cause a warning. Do not use time.sleep in async code.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write an async function that waits and then prints a completion message.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define coroutines: async and await in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Concurrent tasks

### Beginner explanation

asyncio.gather() runs multiple awaitables concurrently. During waits, the event loop can run another task.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
import asyncio
async def fetch(name):
    print("Starting", name)
    await asyncio.sleep(1)
    print("Finished", name)
async def main():
    await asyncio.gather(fetch("A"), fetch("B"))
asyncio.run(main())
```

**Expected output**

```text
Starting A
Starting B
Finished A
Finished B
```

### Walkthrough

Both tasks begin before the one-second waits finish. The event loop switches at await points.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

create_task(), gather(), TaskGroup, cancellation and timeouts.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Concurrency is not identical to parallel CPU execution. Blocking code prevents other coroutines from progressing.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Run two independent simulated API calls concurrently and compare with sequential calls.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define concurrent tasks in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. HTTP request-response basics

### Beginner explanation

HTTP is a protocol used by clients and servers to exchange requests and responses.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
method = "GET"
path = "/students/101"
headers = {"Accept": "application/json"}
print(method, path)
print(headers["Accept"])
```

**Expected output**

```text
GET /students/101
application/json
```

### Walkthrough

The method expresses the operation. The path identifies a resource. Headers carry metadata.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

URL, method, path, query parameters, headers, body, status code and response body.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A network request can fail because of DNS, timeout, authentication or server errors. A connection alone does not guarantee application success.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Describe a GET request to retrieve student 101.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define http request-response basics in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Async HTTP with httpx

### Beginner explanation

An asynchronous HTTP client allows network waits without blocking the event loop. The library must support async operations.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
# Install: python -m pip install httpx
import asyncio
import httpx
async def main():
    async with httpx.AsyncClient(timeout=10) as client:
        response = await client.get("https://httpbin.org/get")
        response.raise_for_status()
        print(response.status_code)
        print(response.json()["url"])
asyncio.run(main())
```

**Expected output**

```text
200
https://httpbin.org/get
```

### Walkthrough

AsyncClient manages the session. await waits for the response. raise_for_status() raises for HTTP error statuses. json() parses JSON.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Timeouts, connection reuse, query parameters, headers, JSON request bodies and exception handling.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A 404 response is still an HTTP response. Check status codes and do not assume every response body is JSON.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write an async function that fetches a safe test endpoint and prints the status.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define async http with httpx in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. Concurrency limits and safe design

### Beginner explanation

A large number of simultaneous requests can overload your application or a remote service. Limit concurrency and set timeouts.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
import asyncio
semaphore = asyncio.Semaphore(2)
async def bounded_task(number):
    async with semaphore:
        print("Working", number)
        await asyncio.sleep(0.2)
async def main():
    await asyncio.gather(*(bounded_task(i) for i in range(5)))
asyncio.run(main())
```

**Expected output**

```text
Working messages appear in groups of at most two active tasks.
```

### Walkthrough

Semaphore(2) allows up to two tasks inside the protected section at once. async with releases the permit safely.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Use semaphores, timeouts, retries with backoff and cancellation. Respect provider rate limits.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Unbounded concurrency can exhaust sockets, memory or API quotas. Retrying immediately can worsen an outage.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Fetch a small list of URLs with a concurrency limit and record failures.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define concurrency limits and safe design in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 9. Guided mini-project — Asynchronous API Data Fetcher

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
day_07_project/
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

1. What is synchronous execution?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is coroutines: async and await?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is concurrent tasks?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is http request-response basics?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is async http with httpx?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is concurrency limits and safe design?
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

1. Explain synchronous execution to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain coroutines: async and await to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain concurrent tasks to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain http request-response basics to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain async http with httpx to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain concurrency limits and safe design to a beginner.
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

**Day 7 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.
