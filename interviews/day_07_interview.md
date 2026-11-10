# Day 07 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** Asynchronous Python: async, await, asyncio, HTTP Fundamentals and Concurrent API Requests  
**Mini-project:** Asynchronous API Data Fetcher  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain synchronous execution.

**Beginner answer:** Synchronous code waits for one operation to finish before starting the next operation.

**Example code**

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

**How it works:** task B starts after task A completes. sleep() blocks the current thread.

**Important methods or syntax:** Use synchronous code for simple scripts and libraries that do not need concurrency.

**Common mistake:** Do not assume async makes CPU-heavy calculations faster. Blocking calls can stall an event loop.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain coroutines: async and await.

**Beginner answer:** async def defines a coroutine function. await pauses that coroutine while an awaitable operation completes.

**Example code**

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

**How it works:** Calling greet() creates a coroutine. asyncio.run() starts an event loop and runs it to completion.

**Important methods or syntax:** async def, await, asyncio.run(), asyncio.sleep() and coroutine objects.

**Common mistake:** Calling a coroutine without awaiting or scheduling it means it may never execute and can cause a warning. Do not use time.sleep in async code.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain concurrent tasks.

**Beginner answer:** asyncio.gather() runs multiple awaitables concurrently. During waits, the event loop can run another task.

**Example code**

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

**How it works:** Both tasks begin before the one-second waits finish. The event loop switches at await points.

**Important methods or syntax:** create_task(), gather(), TaskGroup, cancellation and timeouts.

**Common mistake:** Concurrency is not identical to parallel CPU execution. Blocking code prevents other coroutines from progressing.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain http request-response basics.

**Beginner answer:** HTTP is a protocol used by clients and servers to exchange requests and responses.

**Example code**

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

**How it works:** The method expresses the operation. The path identifies a resource. Headers carry metadata.

**Important methods or syntax:** URL, method, path, query parameters, headers, body, status code and response body.

**Common mistake:** A network request can fail because of DNS, timeout, authentication or server errors. A connection alone does not guarantee application success.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain async http with httpx.

**Beginner answer:** An asynchronous HTTP client allows network waits without blocking the event loop. The library must support async operations.

**Example code**

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

**How it works:** AsyncClient manages the session. await waits for the response. raise_for_status() raises for HTTP error statuses. json() parses JSON.

**Important methods or syntax:** Timeouts, connection reuse, query parameters, headers, JSON request bodies and exception handling.

**Common mistake:** A 404 response is still an HTTP response. Check status codes and do not assume every response body is JSON.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain concurrency limits and safe design.

**Beginner answer:** A large number of simultaneous requests can overload your application or a remote service. Limit concurrency and set timeouts.

**Example code**

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

**How it works:** Semaphore(2) allows up to two tasks inside the protected section at once. async with releases the permit safely.

**Important methods or syntax:** Use semaphores, timeouts, retries with backoff and cancellation. Respect provider rate limits.

**Common mistake:** Unbounded concurrency can exhaust sockets, memory or API quotas. Retrying immediately can worsen an outage.

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

### Exercise 1 — Synchronous execution

**Task:** Predict the order of two synchronous tasks.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — Coroutines: async and await

**Task:** Write an async function that waits and then prints a completion message.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Concurrent tasks

**Task:** Run two independent simulated API calls concurrently and compare with sequential calls.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — HTTP request-response basics

**Task:** Describe a GET request to retrieve student 101.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Async HTTP with httpx

**Task:** Write an async function that fetches a safe test endpoint and prints the status.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Concurrency limits and safe design

**Task:** Fetch a small list of URLs with a concurrency limit and record failures.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — Asynchronous API Data Fetcher

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


## Additional mentor-led interview drills

### How to answer a question when you are a beginner
1. Listen to the complete question.
2. Identify the exact Python feature being asked about.
3. Give a simple definition.
4. Explain the purpose before describing syntax.
5. Write the smallest example that demonstrates the feature.
6. Predict and explain its output.
7. Mention one limitation or common error.
8. Connect it to the day's mini-project.

### Interviewer follow-up ladder
- What problem does this feature solve?
- Can you explain it without using a technical definition?
- What is the smallest working example?
- What happens when the input changes?
- Does the operation change the original value or return a new value?
- What happens for empty or invalid input?
- How would you test this behavior?
- Where would you use it in a real application?
- What would you improve before production use?

### Practical communication drill
Ask the student to explain one code example in this order: input, variable, operation, output, error case and practical use. The student must not read the answer word for word. The trainer should ask one follow-up after each explanation.

### Code review drill
- Are names meaningful?
- Is each function focused on one task?
- Is the output predictable?
- Are invalid inputs considered?
- Are secrets kept outside source code?
- Can another beginner run the project using the README?
- Is there at least one test for normal behavior and one test for an edge case?

### Student reflection
Write down the question that was hardest to answer. Revisit the matching class-note section, create a smaller example and explain it again the next day.
