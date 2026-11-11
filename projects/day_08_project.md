# Day 8 Project — External API Integration Client

## Objective
Create a Python client that reads and creates sample posts using a public test API. Practise GET, POST, query parameters, JSON, status checks and errors.

## Setup
Create and activate a virtual environment, then install requests:
Windows: py -m venv .venv; .venv\Scripts\Activate.ps1; python -m pip install requests  
macOS/Linux: python3 -m venv .venv; source .venv/bin/activate; python -m pip install requests

## Create api_client.py
~~~python
import requests

BASE_URL = "https://jsonplaceholder.typicode.com"

def get_posts(user_id):
    response = requests.get(
        f"{BASE_URL}/posts",
        params={"userId": user_id},
        timeout=10
    )
    response.raise_for_status()
    data = response.json()
    if not isinstance(data, list):
        raise ValueError("Expected a list of posts")
    return data

def create_post(title, body, user_id):
    payload = {"title": title, "body": body, "userId": user_id}
    response = requests.post(
        f"{BASE_URL}/posts",
        json=payload,
        timeout=10
    )
    response.raise_for_status()
    return response.json()

if __name__ == "__main__":
    try:
        posts = get_posts(1)
        print("Posts returned:", len(posts))
        if posts:
            print("First title:", posts[0]["title"])
        created = create_post("Learning REST APIs", "Sample request", 1)
        print("Created response:", created)
    except requests.Timeout:
        print("The API request timed out.")
    except requests.HTTPError as error:
        print("HTTP request failed:", error)
    except requests.RequestException as error:
        print("Network request failed:", error)
    except ValueError as error:
        print("Response validation failed:", error)
~~~

## Explanation
BASE_URL avoids repeating the host. params sends a query parameter. json sends a JSON body. timeout bounds waiting. raise_for_status checks unsuccessful status codes. isinstance validates the top-level response. Specific exception handlers separate timeout, HTTP and network failures. A test API may simulate creation rather than persist data.

## Run
Windows: py api_client.py  
macOS/Linux: python3 api_client.py

Network access is required. Record errors honestly if the test endpoint is unreachable.

## Test cases
| Test | Expected |
|---|---|
| GET userId 1 | List of posts |
| GET another userId | Filtered list |
| POST valid payload | JSON response with submitted fields |
| Network disabled | Request exception handled |
| Timeout | Timeout handled |
| Unexpected response type | ValueError |

## Extensions
1. Add get_post(post_id).
2. Add DELETE and inspect its status.
3. Add Accept header.
4. Read base URL from environment configuration.
5. Validate required response fields.

## Submission
Submit source, setup instructions, sample responses and tests. Never commit credentials.
