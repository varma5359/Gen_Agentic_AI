# Day 19 — API Errors, Retries, Timeouts and Reliability

**Phase:** 3 — LLM Application Development
**Approved project:** Resilient LLM API Client
**Study time:** 2–3 hours
**Level:** Beginner-first

## Learning outcomes
- Classify configuration, validation, authentication, authorization, rate-limit, quota, network, timeout and provider errors.
- Use Python exceptions deliberately.
- Configure connection and read timeouts using the installed SDK's documented interface.
- Apply bounded retry rules, exponential backoff and jitter.
- Explain idempotency, duplicate work and retry cost.
- Implement provider-neutral error categories.
- Understand fallback, circuit breakers and concurrency controls.
- Add safe structured logs and reliability metrics.
- Test failure behavior without a live API or real waiting.

## Reliability flow
```text
Validate input and configuration
             |
             v
Set overall deadline
             |
             v
Call provider with timeout
             |
       +-----+-----+
       |           |
     Success     Failure
       |           |
       v           v
Normalize       Classify error
response           |
       |       +---+----------------+
       |       |                    |
       |   Permanent             Retryable
       |       |                    |
       |   Return safe       Check retry budget
       |   error                    |
       |                       Wait bounded
       |                       backoff
       |                           |
       |                       Retry / fallback
       |                           |
       +------------+--------------+
                    v
          Record outcome safely
```

## Python exception refresher
```python
try:
    result = 10 / 2
except ZeroDivisionError:
    print("The denominator cannot be zero")
else:
    print("Result:", result)
finally:
    print("Cleanup can happen here")
```
- `try` contains operations that may fail.
- `except` catches a specific failure type.
- `else` runs when the `try` block succeeds.
- `finally` runs whether the operation succeeds or fails.
- Catch the narrowest useful exception and avoid silently hiding errors.

## A simple retry policy model
```python
from dataclasses import dataclass

@dataclass
class RetryPolicy:
    max_attempts: int = 3
    base_delay_seconds: float = 0.5
    max_delay_seconds: float = 4.0

def is_retryable(error_category: str) -> bool:
    return error_category in {"network", "timeout", "rate_limit", "server_error"}
```
- `max_attempts` includes the initial attempt in this example; document this convention.
- `base_delay_seconds` is the first backoff basis.
- `max_delay_seconds` caps the delay.
- The retryable set is an application policy, not a universal provider rule.
- Invalid input and authentication failures are intentionally excluded.

## Backoff calculation
```python
def backoff_seconds(attempt: int, policy: RetryPolicy) -> float:
    if attempt < 1:
        raise ValueError("attempt must be at least 1")
    delay = policy.base_delay_seconds * (2 ** (attempt - 1))
    return min(delay, policy.max_delay_seconds)
```
- Attempt one waits the base delay.
- Attempt two doubles it.
- Attempt three doubles it again.
- `min` applies the configured cap.
- Production code should add jitter and respect provider retry-after guidance.
- Tests should inject or control randomness and time rather than wait in real time.

## Why not retry every exception?
- A wrong API key remains wrong when repeated.
- A malformed JSON request remains malformed when repeated.
- A user permission error requires authorization changes.
- Quota exhaustion may require billing or quota action.
- A network reset may be temporary and can be retryable.
- A rate limit may require waiting for a reset window.
- A timeout may be ambiguous because the provider may have processed the request.
- A retry can create duplicate cost or duplicate side effects.

## Project implementation milestones
1. Define stable internal error categories.
2. Create a fake provider that can return success or raise controlled failures.
3. Validate input before provider traffic.
4. Add provider-specific exception translation.
5. Add timeout configuration using the current SDK's documented setting.
6. Add bounded retries for eligible failures only.
7. Add backoff, jitter and retry-after handling.
8. Add total request deadline and cancellation behavior.
9. Add fallback only where policy allows and quality is evaluated.
10. Add logs, metrics, tests and a troubleshooting README.

## Core implementation rules
- Keep retry logic outside UI and route handlers.
- Do not sleep for long periods inside a synchronous web worker; queue work when appropriate.
- Do not block an async event loop with synchronous sleep.
- Preserve the total deadline across attempts.
- Close failed responses and streams before retrying.
- Do not append a restarted stream to partial output without a documented policy.
- Log attempt count and safe error category.
- Never log API keys, authorization headers or private prompts by default.
- Make retry count a server-controlled setting.
- Return a stable application error when recovery is exhausted.

## Failure test matrix
| Scenario | Expected behavior |
|---|---|
| Invalid prompt | Reject before provider call |
| Missing key | Configuration error; no retry |
| Invalid key | Authentication error; no automatic retry |
| No model permission | Authorization error; no automatic retry |
| Rate limit | Respect retry guidance and bounded policy |
| Network reset | Retry only within attempt and deadline budget |
| Timeout | Return timeout or retry according to safe policy |
| Provider server error | Bounded retry if classified transient |
| Quota exhausted | Operator guidance; no rapid retry loop |
| Primary unavailable | Approved fallback or safe unavailable result |
| All attempts fail | Predictable terminal error |
| Cancellation | Stop further attempts and release resources |

## Exercises with answers
**Exercise 1:** Should a missing API key be retried three times?
**Answer:** No. It is a configuration problem; repeating the same request does not fix it.

**Exercise 2:** A request times out after the provider may have received it. What risk exists?
**Answer:** The provider may have completed work, so retrying can duplicate cost or side effects. The application needs a documented retry and idempotency policy.

**Exercise 3:** Why add jitter to exponential backoff?
**Answer:** It spreads retries across time so many clients do not retry simultaneously after a shared outage or rate-limit window.

**Exercise 4:** Is a circuit breaker the same as a retry?
**Answer:** No. A retry repeats an eligible failed operation after a delay. A circuit breaker temporarily rejects or limits calls after repeated failures to protect the application and dependency.

**Exercise 5:** What should be logged?
**Answer:** Correlation ID, provider, model, duration, attempt count, safe error category and outcome. Do not log keys or full private prompts by default.

## Daily MCQs
1. Which failure should normally not be retried unchanged? **Answer: Invalid API key.** The credential must be corrected or rotated.
2. What is exponential backoff? **Answer: Increasing the delay between retry attempts.** It reduces pressure during transient failures.
3. What does a timeout prove? **Answer: Only that the client stopped waiting within its configured time.** It does not prove the provider did no work.
4. What does a circuit breaker do? **Answer: Temporarily limits calls after repeated failures.** It protects resources from a failing dependency.
5. Why use a fake provider in tests? **Answer: To reproduce success and failure deterministically without cost or network dependence.**

## Interview questions
**Q1. How do you design retries for an LLM API?**
**Answer:** Classify errors, retry only transient categories, use bounded attempts, exponential backoff with jitter, respect retry-after metadata, preserve an overall deadline and record each attempt. Avoid retries for invalid credentials, permissions and malformed input.

**Q2. What is the difference between a timeout and a rate limit?**
**Answer:** A timeout means the client stopped waiting within a configured duration. A rate limit means the provider restricted request or token throughput. They require different diagnostics and recovery policies.

**Q3. What is a circuit breaker?**
**Answer:** A circuit breaker tracks repeated dependency failures and temporarily stops sending calls when a threshold is reached. It can later allow a limited probe to determine whether the dependency recovered.

**Q4. How do you prevent retry storms?**
**Answer:** Use bounded retries, exponential backoff, jitter, retry-after guidance, concurrency limits and service-wide retry budgets. A queue or circuit breaker may be appropriate for sustained overload.

**Q5. What should happen when the primary provider fails?**
**Answer:** First classify the failure. Use an alternate provider only for approved failure categories and only if data policy permits. Validate fallback output using the same contract, record which provider served the request and return a clear unavailable state if fallback also fails.

## Project — Resilient LLM API Client
### Acceptance criteria
- [ ] Input validation occurs before provider traffic.
- [ ] Internal error categories are documented.
- [ ] Timeouts are configured using the installed SDK's documented API.
- [ ] Retry eligibility is explicit.
- [ ] Retry attempts are bounded.
- [ ] Backoff is capped and includes jitter in the live implementation.
- [ ] Total deadline is preserved across retries.
- [ ] Authentication and validation errors are not blindly retried.
- [ ] Fallback behavior is explicit and tested if implemented.
- [ ] Logs do not contain credentials or full prompts.
- [ ] Tests use a fake provider and deterministic delays.
- [ ] README contains a troubleshooting runbook.

## Completion gate
Day 19 is complete when the student can explain each failure category, demonstrate bounded recovery with a fake provider, show that permanent errors are not retried, and explain the cost and duplicate-work risks of a timeout. A loop that retries forever is not resilience.

## Deep-dive 1: Why reliability matters

A model API call depends on a network, provider service, account, model and request format.

**Practical behavior:** Any one of these dependencies can fail independently.

**Decision rule:** A reliable client expects failures and converts them into predictable application outcomes.

**Failure risk:** A successful retry does not erase the need to record the original failure.

**Implementation note:** The goal is controlled recovery, not hiding every error.

**Test case:** Users need a clear outcome and a safe next action.

**Project connection:** Operators need enough diagnostic information to investigate without seeing secrets.

**Operational concern:** Tests should prove behavior under failure, not only on the happy path.

**Remember:** Reliability is a product feature because users depend on predictable behavior.

## Deep-dive 2: Failure taxonomy

Configuration failures include missing keys and invalid timeout settings.

**Practical behavior:** Authentication failures include invalid or revoked credentials.

**Decision rule:** Authorization failures include a key without access to a model or project.

**Failure risk:** Validation failures mean the application request does not satisfy the contract.

**Implementation note:** Rate-limit failures mean usage exceeded a provider limit.

**Test case:** Quota failures may require billing or account changes.

**Project connection:** Network failures include DNS, connection and TLS problems.

**Operational concern:** Timeouts mean the client stopped waiting within a configured period.

**Remember:** Provider server errors may be temporary or persistent.

## Deep-dive 3: Exceptions in Python

An exception represents an error or unusual condition during execution.

**Practical behavior:** `try` marks code that may raise an exception.

**Decision rule:** `except` handles a matching exception type.

**Failure risk:** Catch the narrowest useful exception rather than every exception by default.

**Implementation note:** `finally` is useful for cleanup that must run on success or failure.

**Test case:** `raise` signals an error to a caller.

**Project connection:** Exception chaining with `raise ... from exc` preserves diagnostic cause.

**Operational concern:** Do not use exceptions for ordinary branching when a simple condition is clearer.

**Remember:** Never silently swallow an exception without recording a safe outcome.

## Deep-dive 4: Timeout types

A connect timeout limits the time to establish a connection.

**Practical behavior:** A read timeout limits waiting for response data, depending on the client library.

**Decision rule:** A total deadline limits the overall operation duration.

**Failure risk:** SDKs may expose different timeout configuration shapes.

**Implementation note:** A single timeout number may not mean the same thing across libraries.

**Test case:** Set values based on observed task duration and user expectations.

**Project connection:** Long generation tasks may need a different policy from short classification calls.

**Operational concern:** A timeout does not prove the provider did not process the request.

**Remember:** Test timeout behavior using a fake client or controlled local server.

## Deep-dive 5: Retry eligibility

Retry only errors that are plausibly transient.

**Practical behavior:** Network resets, selected server errors and rate limits may be retryable.

**Decision rule:** Invalid credentials are not fixed by repeating the same request.

**Failure risk:** Malformed input is not fixed by repeating the same request.

**Implementation note:** Permission errors require configuration or account changes.

**Test case:** Quota exhaustion may require billing action rather than retry.

**Project connection:** A timeout may be ambiguous about whether the provider completed work.

**Operational concern:** Use provider guidance and status metadata to decide eligibility.

**Remember:** Document the retryable categories in code.

## Deep-dive 6: Exponential backoff

Backoff waits before trying again after a retryable failure.

**Practical behavior:** Exponential backoff increases the delay after each failed attempt.

**Decision rule:** A common conceptual schedule is base delay multiplied by powers of two.

**Failure risk:** A maximum delay prevents unbounded waiting.

**Implementation note:** Jitter adds randomness so many clients do not retry simultaneously.

**Test case:** Use a small maximum attempt count.

**Project connection:** Honor provider retry-after guidance when supplied.

**Operational concern:** Do not sleep inside a request handler for excessive periods; use queues for longer waits.

**Remember:** Test the schedule with an injected clock or sleep function.

## Deep-dive 7: Retry budgets

A retry budget limits extra attempts across a request or service.

**Practical behavior:** Per-request limits prevent one user operation from looping forever.

**Decision rule:** Service-wide limits prevent retries from amplifying an outage.

**Failure risk:** A retry consumes time and may consume provider quota or money.

**Implementation note:** Do not retry a streaming request after visible partial output without an explicit restart policy.

**Test case:** Track attempts and the final outcome.

**Project connection:** Use a circuit breaker or queue when a provider is persistently unhealthy.

**Operational concern:** Define when a human operator should intervene.

**Remember:** A bounded retry policy is part of the API contract.

## Deep-dive 8: Idempotency and duplicate work

A retry can repeat a request that the provider already processed.

**Practical behavior:** Idempotency means repeating the same operation does not create an unintended duplicate effect.

**Decision rule:** Generation calls may still incur repeated cost even if no external state changes.

**Failure risk:** Use provider-supported idempotency keys only when documented for the endpoint.

**Implementation note:** An application request ID helps correlate attempts but does not automatically make a provider call idempotent.

**Test case:** For actions with side effects, require stronger idempotency design in application code.

**Project connection:** Do not assume a timed-out request failed before reaching the provider.

**Operational concern:** Test ambiguous timeout scenarios with a fake provider.

**Remember:** Explain duplicate-cost risk to operators.

## Deep-dive 9: Rate limit response

A rate limit is a capacity or usage restriction, not necessarily an application bug.

**Practical behavior:** The provider may return a specific status code or structured error type.

**Decision rule:** Some responses include retry-after or reset metadata.

**Failure risk:** Read the current provider documentation for exact semantics.

**Implementation note:** Do not parse a human-readable error string if a stable code is available.

**Test case:** Reduce concurrency or queue requests when traffic exceeds sustainable capacity.

**Project connection:** A burst limit and a sustained throughput limit need different controls.

**Operational concern:** Do not make all users retry immediately.

**Remember:** Record safe rate-limit metrics.

## Deep-dive 10: Quota and billing

Quota exhaustion may differ from short-term rate limiting.

**Practical behavior:** A retry loop cannot create more account quota.

**Decision rule:** The account may need billing setup, a quota increase or a different accessible model.

**Failure risk:** Do not switch accounts or credentials without authorization.

**Implementation note:** Return a clear operator-facing configuration message.

**Test case:** Keep user-facing errors concise and avoid account secrets.

**Project connection:** Track usage and budget alerts before production traffic.

**Operational concern:** Pricing and quota policies change; check current provider documentation.

**Remember:** Test quota errors as a distinct case.

## Deep-dive 11: Connection errors

A connection error can occur before the provider receives a request.

**Practical behavior:** DNS lookup, TLS negotiation, proxy configuration and network routing can all be involved.

**Decision rule:** Check whether the issue affects all endpoints or only one provider.

**Failure risk:** Do not disable TLS certificate verification as a workaround.

**Implementation note:** Use a supported HTTP client and current certificate store.

**Test case:** Retry transient connection resets with bounded backoff.

**Project connection:** Do not retry permanent DNS or configuration failures endlessly.

**Operational concern:** Log endpoint host and safe error category, not authorization headers.

**Remember:** Test with a fake transport for deterministic behavior.

## Deep-dive 12: Provider server errors

A server error means the provider failed to complete the request successfully at its service boundary.

**Practical behavior:** Some server errors are transient; others indicate unsupported operations or internal failures.

**Decision rule:** Use status code and provider error metadata where available.

**Failure risk:** Retry only when the error category and operation make it safe.

**Implementation note:** Use a maximum attempt count and overall deadline.

**Test case:** If the provider remains unhealthy, return a safe unavailable response.

**Project connection:** Do not tell the user the provider is down unless the evidence supports that claim.

**Operational concern:** Capture request IDs for provider support when available.

**Remember:** Test repeated server errors and recovery.

## Deep-dive 13: Authentication versus authorization

Authentication asks whether the credential is valid.

**Practical behavior:** Authorization asks whether that credential can access the requested resource or action.

**Decision rule:** An invalid key should not be retried unchanged.

**Failure risk:** A valid key may still lack access to a particular model or project.

**Implementation note:** Keep credential loading and provider selection separate.

**Test case:** Never display the key in an error message.

**Project connection:** Rotate a key if exposure is suspected.

**Operational concern:** Use least-privilege credentials where the provider supports them.

**Remember:** Test both categories independently.

## Deep-dive 14: Circuit breaker

A circuit breaker temporarily stops calls to a dependency after repeated failures.

**Practical behavior:** It can prevent a failing provider from consuming all application workers.

**Decision rule:** Typical states are closed, open and half-open.

**Failure risk:** Closed allows requests; open rejects or routes them elsewhere; half-open permits a limited probe.

**Implementation note:** Thresholds and reset windows should be based on measured behavior.

**Test case:** A circuit breaker is not a replacement for timeouts or retries.

**Project connection:** Do not let every user trigger a probe at once.

**Operational concern:** Expose a safe degraded state to the UI.

**Remember:** Test state transitions with a fake clock and provider.

## Deep-dive 15: Fallback provider

Fallback selects an alternate provider when a defined failure occurs.

**Practical behavior:** Only fallback on eligible failures such as a provider outage or supported capacity issue.

**Decision rule:** Do not fallback for invalid input or a user permission failure.

**Failure risk:** Different providers may produce different quality, format, safety behavior and cost.

**Implementation note:** Validate fallback output using the same application contract.

**Test case:** Record which provider served the request.

**Project connection:** Do not silently change provider when policy or data residency constraints prohibit it.

**Operational concern:** Test primary success, primary failure with fallback success and both failing.

**Remember:** Fallback is a product policy, not a catch-all exception handler.

## Deep-dive 16: Deadline propagation

A request deadline is the latest time by which the application should stop work.

**Practical behavior:** Pass the remaining time budget to each downstream operation where supported.

**Decision rule:** A retry should not reset the overall deadline.

**Failure risk:** A provider call that starts after the deadline is already exceeded should not be sent.

**Implementation note:** Use monotonic time for elapsed duration calculations.

**Test case:** Do not confuse wall-clock timestamps with elapsed-time measurement.

**Project connection:** Propagate cancellation when the caller disconnects.

**Operational concern:** Return a predictable deadline-exceeded outcome.

**Remember:** Test that retries fit inside the total budget.

## Deep-dive 17: Concurrency limits

Many simultaneous model calls can exhaust provider limits and application workers.

**Practical behavior:** A semaphore or queue can cap concurrent operations in one process.

**Decision rule:** A per-process limit is not a global limit across multiple server instances.

**Failure risk:** Use shared coordination when a global cap is required.

**Implementation note:** Set limits based on provider quotas and application capacity.

**Test case:** Avoid holding locks while doing unrelated work.

**Project connection:** Queue length should also be bounded.

**Operational concern:** Return a busy response or enqueue work according to product design.

**Remember:** Load-test with a fake provider before live traffic.

## Deep-dive 18: Bulkhead isolation

Bulkheads isolate one dependency or workload so its failure does not consume every resource.

**Practical behavior:** Separate provider pools or concurrency budgets can prevent one model from blocking unrelated work.

**Decision rule:** A fallback provider should not share all the same exhausted resources if independence is required.

**Failure risk:** Do not overcomplicate a single-user command-line demo.

**Implementation note:** For a production service, identify critical resource pools and their limits.

**Test case:** Monitor queue saturation and rejection counts.

**Project connection:** Test one slow provider while another remains responsive.

**Operational concern:** A bulkhead reduces blast radius; it does not make a dependency reliable.

**Remember:** Document the isolation boundary.

## Deep-dive 19: Async retry pitfalls

An async retry loop must await the delay without blocking the event loop.

**Practical behavior:** Use async-compatible sleep inside async functions.

**Decision rule:** Do not call blocking `time.sleep` in an asynchronous web request handler.

**Failure risk:** Ensure cancellation interrupts the retry wait when appropriate.

**Implementation note:** Preserve the same overall deadline across attempts.

**Test case:** Close any failed response or stream before retrying.

**Project connection:** Do not run concurrent retries for the same request unintentionally.

**Operational concern:** Test cancellation during backoff.

**Remember:** Keep synchronous and asynchronous retry helpers separate unless a clear abstraction supports both.

## Deep-dive 20: Error translation

Provider SDK exceptions should not leak directly into every layer of the application.

**Practical behavior:** Translate them into stable internal exceptions or result categories.

**Decision rule:** Preserve a safe cause for logs and diagnostics.

**Failure risk:** Do not expose provider stack traces to end users.

**Implementation note:** Use distinct categories for authentication, rate limit, timeout, unavailable and invalid request.

**Test case:** Do not classify every unknown error as retryable.

**Project connection:** Keep provider request IDs when available.

**Operational concern:** Test each mapping with fake SDK exceptions.

**Remember:** A stable error contract allows the UI and API to remain provider-neutral.

## Deep-dive 21: Safe user messaging

A user-facing message should explain what happened at the level they need.

**Practical behavior:** Do not reveal API keys, internal endpoints or raw stack traces.

**Decision rule:** A temporary service issue can suggest trying later if the policy permits.

**Failure risk:** A validation error should explain what input needs correction.

**Implementation note:** A configuration issue should be routed to an operator rather than blaming the user.

**Test case:** A partial response must be labeled incomplete.

**Project connection:** Avoid claiming that data was not processed if a timeout makes that uncertain.

**Operational concern:** Keep messages consistent across CLI and web clients.

**Remember:** Test that secret-like strings never appear in error output.

## Deep-dive 22: Structured logs

Structured logs store fields such as timestamp, severity, request ID and error category.

**Practical behavior:** They are easier to query than unstructured paragraphs.

**Decision rule:** Use a correlation ID to connect an incoming request with provider attempts.

**Failure risk:** Log provider name and model identifier where appropriate.

**Implementation note:** Record attempt count, duration and outcome.

**Test case:** Do not log API keys, authorization headers or full private prompts by default.

**Project connection:** Redact personal data before logging if content logging is explicitly approved.

**Operational concern:** Keep exception stack traces in restricted operational logs only.

**Remember:** Test log capture for secret leakage.

## Deep-dive 23: Metrics

Metrics summarize behavior over time.

**Practical behavior:** Useful reliability metrics include request success rate, timeout rate, rate-limit count and retry count.

**Decision rule:** Latency metrics should include percentiles, not only averages.

**Failure risk:** Separate primary-provider and fallback-provider traffic.

**Implementation note:** Track circuit-breaker state and queue depth if those mechanisms exist.

**Test case:** Do not put user prompts or secrets into metric labels.

**Project connection:** Use bounded label values to avoid unbounded cardinality.

**Operational concern:** Set alerts based on service objectives and operational impact.

**Remember:** Metrics help identify trends but do not explain every individual failure.

## Deep-dive 24: Tracing

A trace connects related operations across application components.

**Practical behavior:** A single user request may include validation, provider call, retry and fallback spans.

**Decision rule:** Use a correlation or trace ID across layers.

**Failure risk:** Do not include sensitive prompt content in trace attributes by default.

**Implementation note:** Record timing and safe error categories.

**Test case:** Keep trace sampling and retention under control.

**Project connection:** Provider SDKs may expose request IDs that can be attached to the trace.

**Operational concern:** A trace is useful only when the instrumentation is consistent.

**Remember:** Test that failures still produce a trace ending with an error status.

## Deep-dive 25: Health checks

A liveness check asks whether the application process is running.

**Practical behavior:** A readiness check asks whether the application can accept work.

**Decision rule:** A provider dependency check may be separate from application liveness.

**Failure risk:** Do not make every liveness probe call a paid LLM endpoint.

**Implementation note:** A temporary provider outage should not necessarily cause the application process to restart continuously.

**Test case:** Use cached or lightweight dependency status where appropriate.

**Project connection:** Keep health endpoints free of secret configuration details.

**Operational concern:** Document what each health endpoint means.

**Remember:** Test behavior when the provider is unavailable.

## Deep-dive 26: Graceful degradation

Graceful degradation means providing a reduced but honest service during dependency failure.

**Practical behavior:** The application may show a temporary unavailable state or queue work.

**Decision rule:** Do not return fabricated model answers as a fallback.

**Failure risk:** A cached response is safe only when the request and cache policy make it appropriate.

**Implementation note:** Explain when an alternate provider is used.

**Test case:** Keep user permissions and privacy controls unchanged in degraded mode.

**Project connection:** Provide a clear route to retry or contact support.

**Operational concern:** Measure how often degraded behavior occurs.

**Remember:** Test primary and fallback failure together.

## Deep-dive 27: Retry-after handling

A provider may tell the client how long to wait before retrying.

**Practical behavior:** Use the documented header or SDK metadata rather than guessing.

**Decision rule:** Validate the parsed delay and cap it to the request deadline.

**Failure risk:** If the delay exceeds the user's wait budget, return a rate-limited result or queue the task.

**Implementation note:** Do not ignore retry-after and hammer the service.

**Test case:** Jitter may still be appropriate when multiple clients share the same reset time.

**Project connection:** Record the delay decision in safe logs.

**Operational concern:** Test missing, malformed and very large retry-after values.

**Remember:** Retry-after is guidance, not permission for unlimited retries.

## Deep-dive 28: Partial completion

A request can produce partial content before an error or cancellation.

**Practical behavior:** Represent partial content separately from a completed answer.

**Decision rule:** Do not silently store partial content as a final assistant response.

**Failure risk:** If the user retries, decide whether to start over or continue using a documented provider capability.

**Implementation note:** Avoid duplicating already visible text.

**Test case:** Record the attempt and final status.

**Project connection:** Do not claim that a timed-out response was not processed by the provider.

**Operational concern:** Test failures at the start, middle and end of generation.

**Remember:** Partial outcomes deserve first-class handling.

## Deep-dive 29: Input validation and retries

Invalid inputs should fail before provider traffic begins.

**Practical behavior:** A retry cannot repair an empty prompt or unsupported application option.

**Decision rule:** Validate lengths, types and allowed settings at the application boundary.

**Failure risk:** Validate provider model and parameter compatibility before sending when possible.

**Implementation note:** Return field-specific errors to the caller.

**Test case:** Do not let invalid input consume retry budget.

**Project connection:** Add unit tests for each validation rule.

**Operational concern:** Keep validation errors separate from provider errors.

**Remember:** A clean boundary reduces cost and simplifies troubleshooting.

## Deep-dive 30: Request size errors

A request can exceed a model's context or endpoint payload limits.

**Practical behavior:** Measure or estimate input tokens before sending where possible.

**Decision rule:** Account for system instructions, history, current prompt and output reserve.

**Failure risk:** A character limit alone is not a reliable token limit.

**Implementation note:** Return a clear input-too-large error or use an approved summarization policy.

**Test case:** Do not silently drop important content.

**Project connection:** Use provider token counting where available.

**Operational concern:** Test just below and above the configured boundary.

**Remember:** Large-request handling should be predictable.

## Deep-dive 31: Model availability

A model may be retired, renamed, region-restricted or unavailable to an account.

**Practical behavior:** Do not assume a model name from an old tutorial remains valid.

**Decision rule:** Keep model identifiers configurable.

**Failure risk:** Check current provider documentation and account access.

**Implementation note:** A model-not-found error is usually not fixed by rapid retries.

**Test case:** A fallback model must be explicitly approved and tested.

**Project connection:** Record the model identifier that served each request.

**Operational concern:** Test unavailable-model behavior with a fake adapter.

**Remember:** Document the last verified model configuration.

## Deep-dive 32: SDK version mismatch

An SDK upgrade can change methods, exception classes or response structures.

**Practical behavior:** Pin tested versions for reproducible deployments.

**Decision rule:** Read release notes before upgrading major versions.

**Failure risk:** Run adapter contract tests after an upgrade.

**Implementation note:** Do not patch production code based on an unverified tutorial snippet.

**Test case:** Keep provider code isolated so version changes are localized.

**Project connection:** Use a clean environment to reproduce installation.

**Operational concern:** Record tested package versions in README or lock file.

**Remember:** A package update is a code change and needs regression tests.

## Deep-dive 33: Provider maintenance

A provider may schedule maintenance or have a temporary incident.

**Practical behavior:** Check official status information when investigating a suspected outage.

**Decision rule:** Do not infer a global outage from one failed request.

**Failure risk:** Distinguish local network issues from provider-wide issues.

**Implementation note:** Use bounded retries and fallback only according to policy.

**Test case:** Communicate uncertainty in status messages.

**Project connection:** Record incident time and request IDs for support.

**Operational concern:** Review status after recovery and rerun a smoke test.

**Remember:** A status page is useful evidence but not a guarantee of your account's exact state.

## Deep-dive 34: Secrets and credential rotation

Rotate credentials when they are exposed or when policy requires periodic rotation.

**Practical behavior:** Update the secret store without committing a new key to source code.

**Decision rule:** Avoid printing old and new values during deployment.

**Failure risk:** Plan a safe overlap or coordinated restart if the service requires it.

**Implementation note:** Revoke the old key after confirming the new key works.

**Test case:** Review logs for suspicious usage when a leak is suspected.

**Project connection:** Restrict who can read or change production secrets.

**Operational concern:** Test startup with a missing or invalid credential in a non-production environment.

**Remember:** Credential rotation should be documented and auditable.

## Deep-dive 35: Provider error payloads

Error payloads may contain a code, message, request ID and documentation hint.

**Practical behavior:** Prefer stable codes over parsing free-form text.

**Decision rule:** Sanitize messages before exposing them to users.

**Failure risk:** Do not echo request payloads or authorization headers from the error object.

**Implementation note:** SDKs may wrap an HTTP response inside an exception.

**Test case:** Inspect the installed SDK's documented exception attributes.

**Project connection:** Avoid depending on undocumented private attributes.

**Operational concern:** Write adapter tests for the fields your code actually uses.

**Remember:** Keep provider-specific parsing inside the adapter.

## Deep-dive 36: Circuit breaker testing

Test the closed state with successful calls.

**Practical behavior:** Inject enough failures to cross the configured threshold.

**Decision rule:** Confirm that open state rejects calls without contacting the provider.

**Failure risk:** Advance a fake clock past the reset interval.

**Implementation note:** Confirm that half-open permits only the configured probe count.

**Test case:** Verify a successful probe closes the breaker.

**Project connection:** Verify a failed probe reopens it.

**Operational concern:** Ensure concurrent requests do not trigger a probe storm.

**Remember:** Test that metrics and logs show the state transition.

## Deep-dive 37: Fallback evaluation

Create one fixed evaluation set for both providers.

**Practical behavior:** Compare task success, structured validity and domain-specific quality.

**Decision rule:** Measure latency and usage under the same conditions.

**Failure risk:** Check whether fallback output follows the same safety and privacy policy.

**Implementation note:** Do not assume the second provider supports identical features.

**Test case:** Document model identifiers and test date.

**Project connection:** Set an acceptable minimum quality threshold before enabling automatic fallback.

**Operational concern:** Send low-quality or ambiguous results to human review.

**Remember:** Fallback quality must be measured, not guessed.

## Deep-dive 38: Cost of retries

Each retry may consume another input and output allocation.

**Practical behavior:** A request that times out may still be billable.

**Decision rule:** Backoff reduces pressure but does not remove cost.

**Failure risk:** Set a maximum retry count and an overall request budget.

**Implementation note:** Track attempts per successful user operation.

**Test case:** Alert on unusual retry amplification.

**Project connection:** Avoid retrying expensive long-context requests for permanent errors.

**Operational concern:** Include cost impact in incident review.

**Remember:** A reliable client is also cost-aware.

## Deep-dive 39: Queue-based recovery

A queue can hold work when immediate provider capacity is unavailable.

**Practical behavior:** Queueing is appropriate when the user can wait for an asynchronous result.

**Decision rule:** A queue needs bounded size, expiration and failure handling.

**Failure risk:** Store a job ID and status rather than keeping an HTTP request open indefinitely.

**Implementation note:** Workers should use the same timeout and retry policies.

**Test case:** Make jobs idempotent or detect duplicate submissions.

**Project connection:** Secure queue payloads because they may contain user content.

**Operational concern:** Provide status polling or notifications with authorization.

**Remember:** Queueing is an architectural extension beyond a simple synchronous client.

## Deep-dive 40: Human escalation

Some failures require an operator or user decision.

**Practical behavior:** Repeated permission errors need account configuration, not retries.

**Decision rule:** Ambiguous data should be reviewed rather than guessed.

**Failure risk:** A provider outage may require a service status message.

**Implementation note:** Define when an error moves from automated recovery to human escalation.

**Test case:** Capture a request ID and safe diagnostic summary.

**Project connection:** Do not include credentials in support tickets.

**Operational concern:** Document escalation ownership and expected response path.

**Remember:** A human escalation path prevents endless automated loops.

## Deep-dive 41: Security of retry metadata

Retry metadata may contain provider request IDs or internal details.

**Practical behavior:** Expose only what is safe and useful to the user.

**Decision rule:** Do not let a client choose an arbitrary retry count or backoff duration.

**Failure risk:** Keep policy limits on the server.

**Implementation note:** Validate any idempotency key format and scope.

**Test case:** Avoid logging sensitive request bodies during retry diagnostics.

**Project connection:** Protect job and attempt records with authorization.

**Operational concern:** Test tampered retry parameters.

**Remember:** Operational controls must not be user-overridable by default.

## Deep-dive 42: Testing deterministic delays

Inject a sleep function or clock into retry logic for unit tests.

**Practical behavior:** A test can record requested delays instead of actually waiting.

**Decision rule:** Assert the backoff sequence and maximum delay.

**Failure risk:** Assert that retry-after overrides or bounds the calculated delay according to policy.

**Implementation note:** Assert that permanent errors cause no retry.

**Test case:** Assert that cancellation stops further attempts.

**Project connection:** Avoid tests that depend on random jitter values unless the random source is injected.

**Operational concern:** Seed or fake randomness for deterministic tests.

**Remember:** Fast deterministic tests improve confidence.

## Deep-dive 43: Error budget

An error budget is the acceptable amount of failure within a service objective period.

**Practical behavior:** It helps teams balance reliability work and feature changes.

**Decision rule:** Define the objective before calculating the budget.

**Failure risk:** A classroom project can track success rate without claiming a formal production SLO.

**Implementation note:** Count user-visible failed operations, not only provider HTTP errors.

**Test case:** Separate expected user validation errors from dependency failures.

**Project connection:** Review trends and major incidents.

**Operational concern:** Do not use a metric without a clear numerator and denominator.

**Remember:** Error budgets are a production operations concept, not a promise of zero failure.

## Deep-dive 44: Runbook design

A runbook tells an operator what to check and what action is safe.

**Practical behavior:** Start with the symptom and impact.

**Decision rule:** List checks in a safe order from configuration to provider status.

**Failure risk:** Include request IDs, model and time window when investigating.

**Implementation note:** Never include secret values in commands or documentation.

**Test case:** Explain how to disable a provider or lower concurrency safely.

**Project connection:** Document rollback and escalation steps.

**Operational concern:** Test the runbook with a simulated failure.

**Remember:** Keep the owner and last-reviewed date visible.

## Deep-dive 45: Incident postmortem

A postmortem explains what happened, impact, contributing causes and corrective actions.

**Practical behavior:** Focus on system conditions rather than blaming an individual.

**Decision rule:** Build a timeline from logs and traces.

**Failure risk:** Distinguish confirmed facts from hypotheses.

**Implementation note:** Identify detection gaps and recovery delays.

**Test case:** Assign actions with owners and due dates.

**Project connection:** Add regression tests for the failure mode.

**Operational concern:** Avoid publishing personal data or secrets in the report.

**Remember:** Review whether retry or fallback amplified the incident.

## Deep-dive 46: Reliability review

List external dependencies and their failure modes.

**Practical behavior:** Check timeouts and total deadlines.

**Decision rule:** Check retry eligibility and maximum attempts.

**Failure risk:** Check rate-limit and quota behavior.

**Implementation note:** Check fallback quality and policy restrictions.

**Test case:** Check error translation and user messages.

**Project connection:** Check log redaction, metrics and trace correlation.

**Operational concern:** Check concurrency limits and resource cleanup.

**Remember:** Check offline failure tests.

## Deep-dive 47: Project milestones

Milestone one defines internal error categories and a fake provider.

**Practical behavior:** Milestone two implements input validation and configuration checks.

**Decision rule:** Milestone three adds timeout and error translation.

**Failure risk:** Milestone four adds bounded retry with backoff and jitter.

**Implementation note:** Milestone five adds rate-limit handling and a total deadline.

**Test case:** Milestone six adds a primary/fallback adapter policy where appropriate.

**Project connection:** Milestone seven adds structured logs and metrics without private prompts.

**Operational concern:** Milestone eight adds deterministic failure tests and a runbook.

**Remember:** Do not build a circuit breaker before basic timeouts and retries work.

## Deep-dive 48: Interview explanation

Explain why network requests fail even when Python code is correct.

**Practical behavior:** Differentiate authentication, authorization, rate limit, quota and timeout.

**Decision rule:** Explain why retrying every exception is dangerous.

**Failure risk:** Describe exponential backoff and jitter.

**Implementation note:** Explain how a circuit breaker differs from a retry.

**Test case:** Describe a safe provider fallback policy.

**Project connection:** Explain why a timeout can still result in provider-side work.

**Operational concern:** Describe how to test retries without sleeping or calling a live provider.

**Remember:** Explain which fields belong in structured logs.
