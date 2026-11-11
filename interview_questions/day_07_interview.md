# Day 7 Interview Guide — Asynchronous Python and HTTP

## Q1. What is asynchronous programming?
It lets a coroutine pause during I/O so the event loop can run other ready tasks. It is useful for network or database waits, not automatically CPU-heavy calculations. Follow-up: Give an I/O-bound example.

## Q2. What is a coroutine?
A coroutine is an awaitable computation typically defined with async def. Calling it creates a coroutine object; an event loop runs it. Calling alone does not guarantee completion.

## Q3. What does await do?
It suspends the current coroutine until the awaited operation completes, allowing other tasks to progress. The object must be awaitable.

## Q4. gather versus sequential awaits?
Sequential awaits wait for each operation in order. asyncio.gather schedules multiple awaitables so independent I/O can overlap. Bound concurrency to avoid overwhelming resources or triggering limits.

## Q5. Concurrency versus parallelism?
Concurrency is overlapping progress; parallelism is simultaneous execution. Asyncio typically provides cooperative I/O concurrency. CPU-heavy work may need a process pool or other parallel strategy.

## Q6. What is an HTTP status code?
It communicates request outcome. Examples: 200 success, 201 created, 400 bad request, 401 unauthenticated, 403 forbidden, 404 missing, 429 rate limited and 500 server error. Not every error should be retried.

## Q7. Why use timeouts?
They bound waiting and protect resources. A client timeout does not prove the server did not process a request.

## Q8. What does a semaphore do?
It limits tasks that can enter a protected section concurrently. It is not the same as a rate limiter, which controls operations over time.

## Practical task
Explain one async GET request from URL construction through JSON parsing and error handling.
