# Day 19 — Building a Resilient LLM API Client

**Phase:** 3 — LLM Application Development  
**Approved topic:** API errors, retries, timeouts, rate limits, fallback handling and exception management  
**Mini-project:** Resilient LLM API Client  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
Students will learn to:
- Identify common API failure types.
- Understand timeouts and rate limits.
- Handle errors with Python exceptions.
- Retry temporary failures safely.
- Avoid unlimited retry loops.
- Provide useful fallback messages.
- Protect secrets and avoid logging sensitive information.

## 2. Why does an application need error handling?

An API call that works today can fail tomorrow because:
- The internet connection is unavailable.
- The provider is temporarily down.
- The API key is invalid.
- The account has exceeded a quota.
- Too many requests were sent too quickly.
- The server took too long to respond.

A resilient application expects failures and handles them clearly.

~~~text
Send request
    |
    v
Did request succeed?
    |
  +---+---+
  |       |
 Yes      No
  |       |
Show      Identify error
answer       |
          +-- Temporary? --> Retry a limited number of times
          |
          +-- Permanent? --> Show useful error
          |
          +-- Still failing --> Safe fallback
~~~

## 3. Common API errors

| Status / symptom | Meaning | What to do |
|---|---|---|
| 400 | Request is invalid | Check request body and parameters |
| 401 | Authentication failed | Check API key |
| 403 | Access is forbidden | Check account/project permissions |
| 404 | Resource or model not found | Check endpoint and model availability |
| 408 / timeout | Request took too long | Check network and timeout |
| 429 | Rate limit or quota issue | Respect retry guidance; check usage |
| 500–599 | Server-side failure | May be temporary; retry carefully |
| Connection error | Could not connect | Check network and provider availability |

Exact error types can vary by SDK/provider. Read the error details rather than relying only on the status number.

## 4. Python exceptions refresher

An exception is an error event that interrupts normal program flow.

~~~python
try:
    number = int("hello")
    print(number)
except ValueError:
    print("Please provide a valid number.")
~~~

**Expected output**
~~~text
Please provide a valid number.
~~~

| Keyword | Meaning |
|---|---|
| try | Run code that may raise an exception |
| except | Handle a matching exception |
| else | Run when try had no exception |
| finally | Run whether an exception happened or not |
| raise | Raise an exception intentionally |

Do not catch every error and silently ignore it. Handle known errors and preserve enough information to debug safely.

## 5. What is a timeout?

A timeout is the maximum time your application waits for an operation before treating it as failed.

~~~text
Request sent
    |
    v
Wait for response
    |
    +---- response arrives in time --> Continue
    |
    +---- time limit exceeded ------> Timeout error
~~~

OpenAI SDK example:

~~~python
from openai import OpenAI

client = OpenAI(
    api_key="read this from an environment variable",
    timeout=20.0
)
~~~

The number is in seconds. In a real project, do not place a real key in the source file; load it from the environment as shown on Day 16.

A timeout does not always mean the provider did not process the request. Be careful when retrying operations that may create charges or perform actions.

## 6. What is a rate limit?

A rate limit controls how many requests can be made within a period.

~~~text
Request 1 -> accepted
Request 2 -> accepted
Request 3 -> accepted
Request 4 -> rate limited (429)
                  |
                  v
          Wait, then retry if allowed
~~~

Limits differ by provider, model, account tier and usage. Check provider documentation and account dashboard.

## 7. Retry strategy

A retry means trying a failed request again.

Good retry rules:
- Retry only failures that may be temporary.
- Limit the number of attempts.
- Wait between attempts.
- Respect provider retry guidance such as Retry-After when available.
- Do not repeatedly retry invalid keys or invalid requests.
- Do not retry indefinitely.

**Exponential backoff:** Increase the wait after each failed attempt.

| Attempt | Wait before retry |
|---:|---:|
| 1st failure | 1 second |
| 2nd failure | 2 seconds |
| 3rd failure | 4 seconds |

In production, add random jitter to reduce many clients retrying simultaneously.

## 8. Understand a simple retry function

~~~python
import time

def run_with_retry(operation, max_attempts=3):
    for attempt in range(max_attempts):
        try:
            return operation()
        except TimeoutError:
            if attempt == max_attempts - 1:
                raise

            wait_seconds = 2 ** attempt
            print(f"Temporary timeout. Waiting {wait_seconds} seconds.")
            time.sleep(wait_seconds)
~~~

| Code | Meaning |
|---|---|
| def run_with_retry(...) | Defines a reusable function |
| operation | A function passed into this function |
| max_attempts=3 | Default maximum number of attempts |
| range(max_attempts) | Produces attempt numbers 0, 1 and 2 |
| try | Runs the operation |
| return operation() | Calls the function and returns its successful result |
| except TimeoutError | Handles timeout exceptions |
| attempt == max_attempts - 1 | Checks whether this was the last attempt |
| raise | Re-raises the last timeout |
| 2 ** attempt | Calculates 1, then 2, then 4 |
| time.sleep(...) | Pauses the current program |

**Important:** This teaching example retries only TimeoutError. A real LLM client should handle the provider SDK's documented timeout, connection, rate-limit and server-error exceptions separately.

## 9. Test retry logic without API credits

~~~python
attempt_count = 0

def sample_operation():
    global attempt_count
    attempt_count += 1

    if attempt_count < 3:
        raise TimeoutError("Temporary problem")

    return "Success"

result = run_with_retry(sample_operation)
print(result)
~~~

**Expected output**
~~~text
Temporary timeout. Waiting 1 seconds.
Temporary timeout. Waiting 2 seconds.
Success
~~~

global allows a function to update a variable defined outside it. In larger applications, a class or explicit state container is often easier to test than global variables.

## 10. Fallback handling

A fallback is a safe alternative when the preferred operation cannot complete.

Example:
- Main action: call the AI model.
- Fallback: tell the user the answer is temporarily unavailable and invite them to retry.

~~~python
def show_answer(answer):
    if answer:
        return answer

    return "The AI service is temporarily unavailable. Please try again."
~~~

A fallback must not pretend that the model produced an answer.

## 11. Safer API-call structure

This example uses documented OpenAI SDK exception types. Confirm names against the installed SDK version.

~~~python
import os
from dotenv import load_dotenv
from openai import OpenAI, APITimeoutError, RateLimitError, APIConnectionError

load_dotenv()

api_key = os.getenv("OPENAI_API_KEY")
if not api_key:
    raise ValueError("OPENAI_API_KEY is missing.")

client = OpenAI(api_key=api_key, timeout=20.0, max_retries=0)

def ask_model(question):
    try:
        response = client.responses.create(
            model="gpt-4.1-mini",
            input=question
        )
        return response.output_text

    except APITimeoutError:
        return "The request timed out. Please try again."

    except RateLimitError:
        return "The service is busy or the usage limit was reached."

    except APIConnectionError:
        return "Could not connect to the AI service. Check your network."

answer = ask_model("Explain a Python function simply.")
print(answer)
~~~

This example disables automatic SDK retries so the lesson's error handling is visible. SDK defaults and exception classes may change; consult the installed SDK documentation before production use.

For production, also consider:
- Provider server errors.
- Invalid request and authentication errors.
- Logging a request ID when available.
- A bounded retry policy with jitter.
- User-friendly messages that do not expose internals.
- Monitoring repeated failures.

## 12. Mini-project — Resilient LLM API Client

**Goal:** Create a Python client that handles common API failures gracefully.

Requirements:
1. Read the key from .env.
2. Set a finite request timeout.
3. Make an LLM request.
4. Handle timeout, connection and rate-limit errors.
5. Retry temporary errors a limited number of times.
6. Show a safe fallback message after final failure.
7. Never display or log the API key.

~~~text
User question
    |
    v
Validate question
    |
    v
Send API request with timeout
    |
    v
Success? ---- yes ---> Return answer
    |
    no
    |
Identify error
    |
Temporary? ---- yes ---> Limited retry + backoff
    |
    no
    |
Show safe message
~~~

Suggested files:

~~~text
resilient_llm_client/
├── client.py
├── retry.py
├── main.py
├── .env
├── .gitignore
└── requirements.txt
~~~

Test cases:
- Successful request.
- Missing API key.
- Invalid key using a deliberately invalid test value.
- Empty question.
- Simulated timeout.
- Simulated rate limit.
- Repeated temporary failure until attempts are exhausted.

## 13. Common mistakes
- Retrying an invalid API key repeatedly.
- Using an unlimited while loop.
- Retrying immediately without waiting.
- Ignoring Retry-After guidance.
- Treating every 429 as the same quota problem.
- Hiding errors with a generic except/pass.
- Printing API keys or sensitive prompts in logs.
- Assuming a timeout proves that no request was processed.

## 14. Practice with answers
1. **What is a timeout?** A limit on how long the program waits for an operation.
2. **What is a rate limit?** A restriction on request or token usage over time.
3. **What does HTTP 401 commonly mean?** Authentication failed.
4. **What does HTTP 429 commonly mean?** Rate limit or quota-related response.
5. **What is a retry?** Another attempt after a failure.
6. **What is exponential backoff?** Increasing the wait between repeated attempts.
7. **Why limit retries?** To prevent endless loops, extra cost and unnecessary load.
8. **Which errors should not normally be retried unchanged?** Permanent configuration or request errors.
9. **What is a fallback?** A safe alternative when the main operation fails.
10. **Should logs contain API keys?** No.

## 15. Day 19 recap

~~~text
Request
  |
  v
Timeout + error handling
  |
  v
Success? --------------------> Return answer
  |
  no
  |
Temporary failure?
  |
  +---- yes ----> Bounded retry + backoff
  |
  +---- no -----> Safe error/fallback
~~~

**Next day:** Day 20 — FastAPI and LLM integration, backend architecture, modular code and API documentation.
