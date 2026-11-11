# Day 7 Project — Asynchronous API Data Fetcher

**Phase:** 1 — Python and Software Development Foundations  
**Approved topic:** Asynchronous Python: async, await, asyncio, HTTP fundamentals and concurrent API requests.  
**Estimated duration:** 30–75 minutes (Day 10 may take longer)  
**Mode:** Independent self-learning

## 1. Problem statement and objective

Build an asynchronous fetcher that runs independent I/O tasks concurrently. Begin with simulated waits; optionally replace them with HTTPX async requests.

## 2. Prerequisites

Coroutines, await, asyncio.run, asyncio.gather, timeouts and error handling.

Complete the day's class notes first. Use only concepts already introduced in the pathway. No paid API key is required unless an optional extension explicitly adds one.

## 3. Functional requirements

- Solve the stated objective.
- Use readable names and small functions or classes with clear responsibilities.
- Validate input before processing.
- Provide useful behaviour for normal and invalid inputs.
- Keep credentials and sensitive values out of source code.

## 4. Step-by-step implementation plan

1. Create one coroutine per data source.
2. Use gather for a small fixed set.
3. Add a timeout or simulated failure path.
4. Optional: use HTTPX AsyncClient with request timeouts.

Do not skip steps. Run the program after each meaningful change. If an error occurs, fix it before adding another feature.

## 5. Suggested folder structure

~~~text
day_07_project/
└── async_fetcher.py
~~~

Create only files you actually use. Do not add empty modules merely to make the project look larger.

## 6. Sample data and expected behaviour

Start with two or three small records. Before running the program, write down the expected result for each record. Compare actual and expected behaviour and explain any difference.

## 7. Test cases and validation

Test success, delayed task, timeout and one task failing. Explain whether tasks are independent. Do not use blocking time.sleep inside a coroutine.

Record each test as: input, expected result, actual result and PASS/FAIL. Do not mark a test passed until you have run it.

## 8. Common debugging method

1. Read the full error message.
2. Confirm the command, file path and active Python environment.
3. Inspect relevant inputs and variable values.
4. Reduce the problem to the smallest reproducible example.
5. Fix the cause and repeat the failing test.

## 9. Submission checklist

- [ ] Source files and folder structure are saved.
- [ ] Setup and run instructions are written.
- [ ] Example input and output are recorded.
- [ ] Normal and invalid cases have been tested.
- [ ] Known limitations are documented.
- [ ] No credentials, private data or unnecessary environment files are committed.
- [ ] I can explain the design and code I wrote.

## 10. Interview explanation

Prepare a 60–90 second explanation covering the problem, your design, the key concepts, one challenge, how you tested the result and one improvement you would make before production.

## 11. Optional extension

Add one small feature only after all required behaviour works. Keep it within concepts already taught; do not introduce an advanced framework early.
