# Day 7 — Asynchronous Python: async, await, asyncio, HTTP fundamentals and concurrent API requests.

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours  
**Level:** Intermediate

> **Self-learning instruction:** Read one section at a time. Type the code yourself, run it and compare the result. These notes are designed to teach without a trainer or video.

## 1. Understand the topic

Synchronous code waits before continuing. Async code can pause at await so an event loop can run other tasks during I/O waits. async def defines a coroutine function; await suspends a coroutine. asyncio.run manages a top-level loop. asyncio.gather runs independent awaitables concurrently. Async is useful for I/O-bound work, not automatically faster for CPU-heavy work.

## 2. Why this matters in an AI application

A GenAI application is still software. It needs input handling, business logic, APIs, data, validation, security, tests and deployment. Today's concepts are building blocks for those responsibilities. A small example demonstrates one concept; it is not automatically production-ready.

## 3. Guided coding walkthrough

### Step 1 — Understand the task

Read the code and predict the output. Identify the input, the main operation and the value produced.

### Step 2 — Code

~~~python
import asyncio
async def fetch_record(record_id):
    print("Starting", record_id)
    await asyncio.sleep(1)  # Simulates network waiting
    return {"id": record_id, "status": "ok"}
async def main():
    results = await asyncio.gather(fetch_record(101), fetch_record(102), fetch_record(103))
    print(results)
asyncio.run(main())
~~~

### Step 3 — Expected output

~~~text
Starting 101
Starting 102
Starting 103
[{'id': 101, 'status': 'ok'}, {'id': 102, 'status': 'ok'}, {'id': 103, 'status': 'ok'}]
~~~

### Step 4 — Explain the code line by line

- asyncio.sleep simulates non-blocking waiting; it is not a real HTTP request.
- gather runs independent coroutines concurrently and returns results in input order.
- Use HTTPX AsyncClient for real async HTTP and set timeouts.
- In notebooks use await main() rather than nesting asyncio.run().

### Step 5 — Interpret the result

Answer in your own words: What input did the program receive? What operation did it perform? What result did it produce? What would change if the input changed? What should be validated before using this in a larger application?

## 4. Common mistakes and troubleshooting

- Read the complete traceback and identify the exception type and line.
- Confirm the active Python interpreter, installed packages, current folder and filename.
- Check types, missing values, boundaries and external response formats.
- Reduce a complex failure to the smallest reproducible example.
- Fix the cause rather than hiding errors with broad exception handling.

## 5. Independent practice

1. Recreate the example from a blank file.
2. Change at least two inputs and predict the output before running.
3. Add one validation or failure case relevant to this topic.
4. Explain the changed output in your own words.
5. Save the code in a clearly named project folder.

## 6. Interview-ready summary

- Define the concept directly.
- Explain the problem it solves.
- Explain when to use it and when a simpler approach is better.
- Give one practical AI-application example.
- Mention one limitation or common failure mode.

## 7. Completion checklist

- [ ] I can explain the concept without copying the definition.
- [ ] I typed and ran the example.
- [ ] I understand the expected output.
- [ ] I completed the independent practice.
- [ ] I can identify and fix a common error.
- [ ] I am ready to attempt the approved project.
