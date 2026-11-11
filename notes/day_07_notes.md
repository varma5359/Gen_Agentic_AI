# Day 7 — Asynchronous Python: async, await, asyncio, HTTP fundamentals and concurrent API requests

**Phase 1 | 2–3 hours | Project: Asynchronous API Data Fetcher**

## Learning objectives
Explain synchronous and asynchronous execution, define coroutine/event loop, use async/await and gather, understand HTTP requests/responses, make asynchronous HTTP requests and bound concurrent work.

## 1. Why async?
Programs often wait for network responses. In synchronous code, the next operation waits until the current call returns. Asynchronous code can pause a task during I/O so other tasks can make progress. It is useful for I/O-bound work, not automatically faster for CPU-heavy calculations.

~~~python
import time
def task(name):
    print("Start", name)
    time.sleep(2)
    print("End", name)
task("A")
task("B")
~~~

These tasks run one after another, taking roughly four seconds.

## 2. async and await
~~~python
import asyncio

async def task(name):
    print("Start", name)
    await asyncio.sleep(2)
    print("End", name)

async def main():
    await asyncio.gather(task("A"), task("B"))

asyncio.run(main())
~~~

Both tasks start before either finishes. Approximate duration is around two seconds plus overhead.
- async def defines a coroutine function.
- Calling it creates a coroutine object.
- await pauses the current coroutine until the awaited operation completes.
- gather schedules multiple awaitables and collects results.
- asyncio.run starts an event loop for this script.

Do not call asyncio.run inside an already-running event loop, as in some notebook environments.

## 3. Concurrency versus parallelism
Concurrency means tasks make progress during overlapping periods. Parallelism means simultaneous execution, often on multiple CPU cores. Asyncio provides cooperative concurrency, especially useful while waiting for I/O. CPU-heavy tasks need a different approach.

## 4. HTTP request and response
HTTP is a request-response protocol.

| Request/response part | Meaning |
|---|---|
| Method | GET, POST, PUT, PATCH, DELETE |
| URL | Resource location |
| Headers | Metadata such as content type or authorization |
| Body | Optional data sent to server |
| Status | Outcome code |
| Response body | Returned content |

Common statuses: 200 success, 201 created, 400 bad request, 401 unauthenticated, 403 forbidden, 404 missing, 429 rate limited, 500 server error.

## 5. Async HTTP using httpx
Install httpx in your virtual environment. Then:

~~~python
import asyncio
import httpx

async def fetch_post(client, post_id):
    url = f"https://jsonplaceholder.typicode.com/posts/{post_id}"
    response = await client.get(url, timeout=10.0)
    response.raise_for_status()
    return response.json()

async def main():
    async with httpx.AsyncClient() as client:
        results = await asyncio.gather(
            fetch_post(client, 1),
            fetch_post(client, 2),
            fetch_post(client, 3)
        )
    for post in results:
        print(post["id"], post["title"])

asyncio.run(main())
~~~

AsyncClient manages reusable connections. await client.get performs the network operation asynchronously. timeout bounds waiting. raise_for_status raises for unsuccessful HTTP status. response.json parses JSON. async with closes the client.

## 6. Errors and bounded concurrency
Network calls may fail due to timeout, DNS, server errors or rate limits. A semaphore limits simultaneous operations.

~~~python
limit = asyncio.Semaphore(3)

async def limited_fetch(client, post_id):
    async with limit:
        return await fetch_post(client, post_id)
~~~

Catch specific exceptions such as httpx.TimeoutException, httpx.HTTPStatusError and httpx.RequestError. Retries must be limited and delayed; never retry forever. A timeout does not prove the server did not process a request.

## 7. Industry scenario
An AI backend may retrieve several independent records before constructing context for a model. Async HTTP can overlap network waits. It improves orchestration around I/O; it does not guarantee the model itself generates faster.

## 8. Common mistakes
| Mistake | Fix |
|---|---|
| Forget await | Await the coroutine operation |
| Use time.sleep in async function | Use asyncio.sleep |
| Forget to close client | Use async with |
| No timeout | Set explicit timeout |
| Gather huge request list without limit | Use semaphore or bounded workers |
| Assume async speeds CPU calculations | Use appropriate CPU parallelism |

## 9. Exercises
1. Run two asyncio.sleep tasks concurrently.
2. Compare sequential and concurrent durations.
3. Fetch three public test posts with httpx.
4. Add timeout and HTTP error handling.
5. Limit concurrency to two.
6. Explain I/O-bound versus CPU-bound.

## 10. Five-question quiz
1. async def defines: A coroutine function B thread C database D class. **Answer A.**
2. await: A pauses coroutine for awaitable B ends program C encrypts D starts OS. **Answer A.**
3. Which blocks event loop? A asyncio.sleep B time.sleep C gather D async with. **Answer B.**
4. HTTP 404 means: A Created B Not Found C Unauthorized D Rate limited. **Answer B.**
5. Semaphore is used to: A limit concurrent tasks B parse JSON C define route D close file. **Answer A.**

## Completion
- [ ] Explain sync/async, coroutine and event loop.
- [ ] Use await and gather.
- [ ] Explain HTTP request/response.
- [ ] Make async HTTP requests.
- [ ] Add timeout and concurrency limit.
- [ ] Complete the project.

**Next:** Day 8 — REST APIs, HTTP methods, status codes, headers, requests and responses.
