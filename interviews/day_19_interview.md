# Day 19 — Interview Preparation: Reliable LLM API Clients

## Beginner questions

**1. Why is error handling important in an LLM application?**  
Network services can fail. Error handling lets the application respond safely instead of crashing or misleading the user.

**2. What is a timeout?**  
A maximum wait duration for an operation. If the operation takes longer, the client treats it as timed out.

**3. What is a rate limit?**  
A provider restriction on how many requests or tokens can be used during a period.

**4. What is a retry?**  
A new attempt after an operation fails.

**5. What is a fallback?**  
A safe alternative response or action when the preferred operation cannot complete.

## HTTP and API questions

**6. What does HTTP 400 mean?**  
The request is invalid or malformed.

**7. What does HTTP 401 mean?**  
Authentication failed.

**8. What does HTTP 403 mean?**  
The caller is not permitted to access the resource.

**9. What does HTTP 429 mean?**  
A rate limit or quota-related response.

**10. What do HTTP 500–599 responses usually indicate?**  
A server-side failure. Some may be temporary.

## Python and retry questions

**11. What is an exception?**  
An event that interrupts normal execution and can be handled using try and except.

**12. What does finally do?**  
It runs whether or not the try block raised an exception.

**13. What is exponential backoff?**  
A retry strategy that increases the wait after each failure, such as 1, 2 and 4 seconds.

**14. Why limit retry attempts?**  
To avoid endless loops, unnecessary provider load and extra costs.

**15. Why should permanent errors not be retried unchanged?**  
An invalid key or malformed request will not normally become valid simply by sending it again.

**16. What is jitter?**  
A small random variation added to retry waits so many clients do not retry at exactly the same time.

**17. What does time.sleep(2) do?**  
It pauses the current thread for approximately two seconds.

## Scenario-based questions

**18. Your application receives a 429 response. What do you do?**  
Check whether it is a rate limit or quota issue, inspect provider guidance and usage, respect retry timing and retry only when appropriate.

**19. The API key is invalid. Should the application retry three times?**  
No. This is a configuration/authentication issue. Fix the key rather than repeatedly retrying it.

**20. The request times out. Does that prove the provider did not process it?**  
No. The provider may have processed the request even though the client did not receive the response. Consider this when retrying costly or state-changing operations.

**21. Why is except: pass dangerous?**  
It hides errors and makes failures difficult to diagnose.

**22. What should application logs avoid?**  
API keys, passwords, unnecessary personal data and full sensitive prompts.

**23. How would you test retry logic without using an LLM API?**  
Pass a test function that raises a simulated TimeoutError a known number of times and then succeeds.

## Quick revision

| Term | Meaning |
|---|---|
| Timeout | Maximum wait duration |
| Rate limit | Usage/request restriction |
| Retry | Try again after failure |
| Backoff | Wait longer between retries |
| Jitter | Random variation in retry wait |
| Fallback | Safe alternative |
| 401 | Authentication failure |
| 429 | Rate limit or quota response |
| 5xx | Server-side error |
