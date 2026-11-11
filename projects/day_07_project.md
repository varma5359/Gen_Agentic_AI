# Day 7 Project — Asynchronous API Data Fetcher

## Objective
Fetch independent sample posts concurrently from a public test API. Practise async HTTP, timeouts, status codes and bounded concurrency.

## Setup
Windows: py -m venv .venv; .venv\Scripts\Activate.ps1; python -m pip install httpx  
macOS/Linux: python3 -m venv .venv; source .venv/bin/activate; python -m pip install httpx

## Create async_fetcher.py
~~~python
import asyncio
import httpx

BASE_URL = "https://jsonplaceholder.typicode.com/posts"

async def fetch_post(client, post_id, semaphore):
    async with semaphore:
        try:
            response = await client.get(f"{BASE_URL}/{post_id}", timeout=8.0)
            response.raise_for_status()
            data = response.json()
            return {"id": data["id"], "title": data["title"], "status": "success"}
        except httpx.TimeoutException:
            return {"id": post_id, "status": "timeout"}
        except httpx.HTTPStatusError as error:
            return {"id": post_id, "status": f"http_error_{error.response.status_code}"}
        except httpx.RequestError:
            return {"id": post_id, "status": "connection_error"}

async def main():
    semaphore = asyncio.Semaphore(2)
    async with httpx.AsyncClient() as client:
        tasks = [fetch_post(client, item, semaphore) for item in [1, 2, 3, 4, 5]]
        results = await asyncio.gather(*tasks)
    for result in results:
        print(result)

if __name__ == "__main__":
    asyncio.run(main())
~~~

## Walkthrough
The list comprehension creates five coroutine objects. gather schedules them. Semaphore(2) permits at most two fetch operations inside its protected block at a time. AsyncClient reuses connections and async with closes it. The timeout prevents indefinite waiting. Specific exceptions return a status record. A real service should log safe diagnostics and retry only selected transient failures with a strict limit.

## Run
Windows: py async_fetcher.py  
macOS/Linux: python3 async_fetcher.py

Network access is required. A connection error is a valid observed outcome if the test API is unreachable.

## Tests
| Test | Expected |
|---|---|
| Fetch IDs 1–5 | Five result records |
| Invalid ID | API-specific error/not-found response |
| Network unavailable | Connection error |
| Slow server | Timeout result |
| Semaphore value 2 | At most two protected calls simultaneously |

## Extensions
1. Accept IDs from input.
2. Measure sequential and concurrent duration.
3. Add bounded retry for transient failures.
4. Save results as JSON using Day 5 knowledge.

## Submission
Submit source, setup instructions, sample output and test observations. Do not claim the endpoint is always available.
