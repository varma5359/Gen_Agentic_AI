# Day 18 — Streaming Responses and Multi-Turn Conversations

**Phase:** 3 — LLM Application Development
**Approved project:** Streaming Conversational Chatbot
**Study time:** 2–3 hours
**Level:** Beginner-first

## Learning outcomes
- Explain the difference between a normal response and a streamed response.
- Understand chunks, deltas, completion events, interruption and cancellation.
- Represent a conversation as ordered role-based messages.
- Maintain bounded conversation history across turns.
- Explain context-window and token-budget constraints.
- Design a provider adapter that emits normalized stream events.
- Build a safe user experience for partial, completed and interrupted answers.
- Test message ordering, ownership, streaming assembly and failure cases.
- Explain privacy and retention responsibilities for chat history.

## Offline streaming simulation

```python
def fake_stream():
    chunks = ["Hello", " ", "from", " ", "the", " ", "assistant."]
    for chunk in chunks:
        yield chunk

assembled = ""
for piece in fake_stream():
    print(piece, end="", flush=True)
    assembled += piece
print()
print("Complete:", assembled)
```

- A generator function uses `yield` to provide values one at a time.
- The loop consumes each chunk in order.
- The accumulator stores the complete answer.
- This is a local simulation, not a real provider stream.
- A real SDK stream must be consumed according to its current documentation.

## Conversation data model

```python
from dataclasses import dataclass
from datetime import datetime, timezone

@dataclass
class Message:
    role: str
    content: str
    created_at: datetime

history = [
    Message("user", "What is an embedding?", datetime.now(timezone.utc)),
    Message("assistant", "An embedding is a numeric representation.", datetime.now(timezone.utc)),
]
```

- A dataclass groups related values.
- Role identifies the speaker; content stores text.
- UTC timestamps avoid timezone ambiguity.
- Production history needs persistence and authenticated ownership checks.

## Provider event contract

```python
from dataclasses import dataclass

@dataclass
class StreamEvent:
    event_type: str
    text: str = ""
    detail: str | None = None
```

- Normalize provider-specific events into an internal event shape.
- Distinguish text deltas, completion, refusal, usage and errors.
- Do not leak provider SDK objects into the UI.
- Verify exact stream iteration and event fields in the installed SDK documentation.

## Approved project milestones
1. Build offline chunk assembly and message validation.
2. Integrate one provider's current streaming interface.
3. Add bounded, ordered multi-turn history.
4. Display generating, completed and interrupted states.
5. Add fake-stream tests for normal completion, failure and cancellation.
6. Document ownership, privacy, retention and limitations.

### Additional deep-dive 1: SSE event framing

Server-Sent Events (SSE) is a text-based event stream format commonly used for one-way server-to-browser updates.

**Implementation detail:** An SSE message may include fields such as `event`, `data` and `id`.

**Engineering consequence:** The server uses the SSE content type and separates events using the protocol's required line endings.

**Failure mode:** The browser's EventSource API is one possible client, but it is not the only streaming approach.

**Test design:** SSE is generally server-to-client; it is not a replacement for a normal POST request that starts generation.

**Project application:** A backend can accept a POST, then expose a separate streaming response depending on its architecture.

**Review prompt:** Parse the event framing according to the protocol rather than splitting arbitrary chunks on a guessed delimiter.

**Operational note:** Test UTF-8 characters that may be split across transport reads.

**Takeaway:** Do not confuse provider-specific event JSON with the outer SSE framing.

### Additional deep-dive 2: Transport chunks versus model tokens

A network read chunk is not guaranteed to equal one model token.

**Implementation detail:** The operating system, HTTP client and proxy may combine or split bytes independently of model generation.

**Engineering consequence:** One visible word can arrive across multiple events.

**Failure mode:** A single event can contain several words or metadata.

**Test design:** Do not animate a token counter by counting network chunks.

**Project application:** If the provider reports token usage, use that metadata rather than guessing from chunk count.

**Review prompt:** UTF-8 characters may require multiple bytes, so decode according to the HTTP client's supported streaming behavior.

**Operational note:** Test non-ASCII text such as accented letters and Indic scripts.

**Takeaway:** The application should treat text as Unicode, not assume ASCII.

### Additional deep-dive 3: Async iteration

Some SDKs expose streams as asynchronous iterators.

**Implementation detail:** An async iterator is consumed with `async for` inside an `async def` function.

**Engineering consequence:** Each `async for` iteration waits for the next available event without blocking the event loop in the same way as synchronous waiting.

**Failure mode:** Do not call `async for` from a normal synchronous function without an async runtime.

**Test design:** Do not call `asyncio.run` inside an already-running event loop such as many async web frameworks.

**Project application:** Keep sync and async adapter contracts distinct or provide an explicit bridge.

**Review prompt:** Close async streams using the SDK's documented cleanup mechanism.

**Operational note:** Catch cancellation and provider errors at the correct async boundary.

**Takeaway:** Test with a fake async generator before integrating the provider.

### Additional deep-dive 4: Backpressure

Backpressure occurs when a producer creates data faster than the consumer can handle it.

**Implementation detail:** A slow browser or downstream processor can cause buffers to grow.

**Engineering consequence:** An application should avoid accumulating an unbounded stream in memory.

**Failure mode:** Use bounded queues when producer and consumer work independently.

**Test design:** If the consumer is too slow, apply a documented pause, drop or cancellation policy.

**Project application:** Do not drop text deltas silently if the final answer must be complete.

**Review prompt:** Monitor buffer size and stream duration in production.

**Operational note:** Test a deliberately slow consumer.

**Takeaway:** Backpressure is a reliability concern, not just a performance optimization.

### Additional deep-dive 5: Heartbeat and idle timeout

A long-running stream may be quiet while the model is thinking or the network is idle.

**Implementation detail:** A heartbeat can indicate that the connection is still alive, depending on the protocol.

**Engineering consequence:** An idle timeout should distinguish expected model delay from a dead connection.

**Failure mode:** Choose timeouts based on observed provider behavior and product expectations.

**Test design:** Do not display a heartbeat as answer text.

**Project application:** A proxy may close idle connections even when the provider is still working.

**Review prompt:** Configure proxy and application timeout policies consistently.

**Operational note:** Test long pauses and dropped connections.

**Takeaway:** Tell the user when the stream has stalled beyond the supported threshold.

### Additional deep-dive 6: Browser disconnect

A browser tab may close while the backend continues a provider request.

**Implementation detail:** The backend should detect disconnects where the framework supports it.

**Engineering consequence:** Propagate cancellation to the provider stream when safe and supported.

**Failure mode:** A disconnected client should not leave unlimited background work running.

**Test design:** Some provider calls may still complete or incur usage after cancellation.

**Project application:** Decide whether to persist partial output, discard it or mark it interrupted.

**Review prompt:** Release database cursors, response iterators and worker resources.

**Operational note:** Log disconnect as a distinct outcome.

**Takeaway:** Test disconnect before the first chunk and mid-response.

### Additional deep-dive 7: Conversation identifiers

A conversation identifier is a lookup key for stored state.

**Implementation detail:** Use unpredictable identifiers where appropriate, but never rely on unpredictability as the only access control.

**Engineering consequence:** Verify the authenticated user owns the conversation on every operation.

**Failure mode:** Do not accept a user ID from the request body as proof of identity.

**Test design:** Create a new conversation when the user explicitly starts one.

**Project application:** Return a not-found or forbidden response according to the application's information-disclosure policy.

**Review prompt:** Avoid putting personal information into identifiers.

**Operational note:** Test guessed, copied and cross-account identifiers.

**Takeaway:** Authorization belongs on the server.

### Additional deep-dive 8: Message ordering

Message order determines conversational meaning.

**Implementation detail:** A sequence number is often clearer than relying on timestamps with equal precision.

**Engineering consequence:** Create sequence numbers atomically when multiple requests may append messages.

**Failure mode:** Sort history consistently before constructing the provider payload.

**Test design:** Do not assume database row order without an explicit `ORDER BY`.

**Project application:** Handle assistant turns that fail before completion according to a documented policy.

**Review prompt:** Use transaction boundaries to avoid orphaned user messages where appropriate.

**Operational note:** Test two requests arriving close together.

**Takeaway:** The conversation service should own ordering rules.

### Additional deep-dive 9: Idempotency

Idempotency helps prevent duplicate processing when a client retries a request.

**Implementation detail:** A client can send a request ID or idempotency key for one intended operation.

**Engineering consequence:** The server records the key and outcome within a defined scope and retention period.

**Failure mode:** Do not reuse an idempotency key for a different prompt.

**Test design:** A duplicate request should return or reference the original outcome where appropriate.

**Project application:** Streaming makes replay more complex because the client may have received some events already.

**Review prompt:** Define whether a reconnect resumes, replays or starts a new generation.

**Operational note:** Provider-side idempotency support varies and must be verified.

**Takeaway:** Test duplicate submission after a simulated network timeout.

### Additional deep-dive 10: Assistant turn lifecycle

A turn can move through states such as queued, generating, completed, interrupted, failed and cancelled.

**Implementation detail:** Define allowed state transitions in the service layer.

**Engineering consequence:** Do not move a failed turn to completed merely because some text exists.

**Failure mode:** Store timestamps for start and finish when useful for operations.

**Test design:** A user message may be saved even if its assistant response fails; document that behavior.

**Project application:** A retry can create a new attempt linked to the original turn.

**Review prompt:** The UI should reflect the authoritative server-side state.

**Operational note:** Use tests to prevent invalid state transitions.

**Takeaway:** A lifecycle model makes support and debugging easier.

### Additional deep-dive 11: History trimming policy

A trimming policy chooses which messages are sent when history is too large.

**Implementation detail:** A simple policy keeps the most recent complete turns.

**Engineering consequence:** Do not split a user-assistant pair if the application relies on both for meaning.

**Failure mode:** Preserve system or application instructions separately from user history.

**Test design:** A summary may replace older turns only when its quality is acceptable.

**Project application:** Keep the current user message even when trimming older history.

**Review prompt:** Reserve output tokens before calculating the available input budget.

**Operational note:** Record when trimming or summarization occurred for debugging.

**Takeaway:** Test the policy with histories of different sizes.

### Additional deep-dive 12: Token budget arithmetic

A request budget includes instruction tokens, history tokens, current input and expected output.

**Implementation detail:** The model context limit is not the same as the output token limit.

**Engineering consequence:** Leave a safety margin for provider formatting and tokenizer differences.

**Failure mode:** Use the provider's token counting method when available.

**Test design:** If exact token counting is unavailable, use a conservative estimate and label it approximate.

**Project application:** Reject or summarize an input that exceeds the application budget.

**Review prompt:** Do not truncate text in the middle of a critical instruction or identifier.

**Operational note:** Test a request just below and just above the configured threshold.

**Takeaway:** Budgeting prevents predictable context errors but cannot guarantee provider acceptance.

### Additional deep-dive 13: Context relevance

More history is not always better.

**Implementation detail:** Old messages can distract the model from the current task.

**Engineering consequence:** Include prior turns that are necessary to resolve references such as 'that example'.

**Failure mode:** Exclude unrelated earlier topics when the user starts a distinct task.

**Test design:** A conversation boundary is a product decision, not merely a database record.

**Project application:** Let users start a fresh chat when context should not carry over.

**Review prompt:** Test follow-up resolution and topic switching.

**Operational note:** Do not claim persistent memory when the application only sends recent messages.

**Takeaway:** Explain what history is included in each request where transparency matters.

### Additional deep-dive 14: System instruction placement

Application instructions should be constructed by trusted server code.

**Implementation detail:** Do not allow the browser to send arbitrary privileged instruction messages.

**Engineering consequence:** Keep user content in user-role data or a clearly separated document field.

**Failure mode:** Provider role structures differ; the adapter maps the internal policy to supported fields.

**Test design:** Do not assume a system role makes instructions impossible to override.

**Project application:** Keep authorization rules in code and database permissions.

**Review prompt:** Test user attempts to submit a fake system role.

**Operational note:** Avoid placing API keys or private configuration in instruction text.

**Takeaway:** Prompt hierarchy is a model behavior aid, not an access-control system.

### Additional deep-dive 15: History integrity

Stored assistant messages may be used as future context.

**Implementation detail:** If a user can modify stored history, they may alter the context the model receives.

**Engineering consequence:** Define whether users can edit or delete their own messages.

**Failure mode:** Preserve audit information when an edit changes downstream meaning.

**Test design:** Do not trust a client-supplied transcript when the server has an authoritative history store.

**Project application:** Validate message ownership and conversation relationship.

**Review prompt:** Protect database updates with transactions and authorization checks.

**Operational note:** Test tampered history payloads.

**Takeaway:** History integrity affects both correctness and security.

### Additional deep-dive 16: Message attachments

A conversation may eventually contain files, images or other content blocks.

**Implementation detail:** Attachments require their own type, size and content validation.

**Engineering consequence:** A filename is not a safe storage path.

**Failure mode:** Scan or validate uploads according to the application's threat model.

**Test design:** Do not assume text extraction from a PDF is accurate for scanned pages.

**Project application:** Store attachment references separately from message text.

**Review prompt:** Apply access control to both the conversation and each referenced file.

**Operational note:** Avoid logging full attachment contents.

**Takeaway:** This day's core project can use text-only messages; multimodal support is an extension.

### Additional deep-dive 17: Markdown rendering

Model output may contain Markdown syntax.

**Implementation detail:** Render Markdown using a safe renderer and a documented allowed feature set.

**Engineering consequence:** Do not interpret raw model output as trusted HTML.

**Failure mode:** Sanitize HTML if the renderer permits raw HTML.

**Test design:** Escape content when displaying plain text.

**Project application:** Links from model output should be treated as untrusted destinations.

**Review prompt:** Do not automatically fetch arbitrary URLs found in an answer.

**Operational note:** Test script-like text, HTML tags and malformed Markdown.

**Takeaway:** Presentation safety is separate from prompt safety.

### Additional deep-dive 18: Scroll management

A streaming chat often needs to keep the newest text visible.

**Implementation detail:** Automatically scrolling can prevent users from reading earlier content.

**Engineering consequence:** Track whether the user is already near the bottom before forcing a scroll.

**Failure mode:** Offer a jump-to-latest control when the user scrolls upward.

**Test design:** Avoid re-rendering the entire conversation on every tiny event if it causes performance problems.

**Project application:** Batch UI updates carefully without making output feel frozen.

**Review prompt:** Keep focus and keyboard behavior predictable.

**Operational note:** Test long responses and narrow screens.

**Takeaway:** A usable stream interface is part of the project acceptance criteria.

### Additional deep-dive 19: Accessibility of streaming

Screen readers may announce every tiny delta and become unusable.

**Implementation detail:** Use a status region with deliberate announcement behavior.

**Engineering consequence:** Do not repeatedly announce the entire growing response.

**Failure mode:** Expose generating, complete and interrupted states as text, not color alone.

**Test design:** Keep keyboard focus stable while new chunks arrive.

**Project application:** Provide a clear cancel or stop control when supported.

**Review prompt:** Test with keyboard navigation and assistive technology where possible.

**Operational note:** Avoid rapid animations that distract from content.

**Takeaway:** Accessibility must be considered while designing the stream, not added at the end.

### Additional deep-dive 20: Rate limits during streams

A stream still consumes provider capacity and may be limited by request or token throughput.

**Implementation detail:** Concurrent streams can exhaust a project's quota.

**Engineering consequence:** Track active streams per user and across the service.

**Failure mode:** Apply queueing or admission control before creating excessive provider requests.

**Test design:** A provider may return an error before the stream begins or during it.

**Project application:** A retry should use bounded backoff and respect retry-after guidance when supplied.

**Review prompt:** Do not start a second stream just because the first one is slow.

**Operational note:** Display a clear busy or rate-limited message.

**Takeaway:** Test concurrency with fake provider limits.

### Additional deep-dive 21: Streaming observability

Record request start, first-event time, completion time and outcome.

**Implementation detail:** Time to first token is different from total generation time.

**Engineering consequence:** Record provider, model, stream status and a correlation ID.

**Failure mode:** Avoid recording raw message text unless a reviewed policy explicitly permits it.

**Test design:** Track interrupted streams and client disconnects.

**Project application:** Measure event count and bytes only when useful.

**Review prompt:** Do not infer model token count from transport event count.

**Operational note:** Use structured logs and redact secrets.

**Takeaway:** Observability should help diagnose failures without exposing conversation content.

### Additional deep-dive 22: Latency metrics

Time to first token measures how long the user waits before seeing output.

**Implementation detail:** Total duration measures the full request lifecycle.

**Engineering consequence:** Streaming can improve perceived latency while total generation time remains unchanged.

**Failure mode:** Network distance, provider queueing, prompt length and model choice all affect latency.

**Test design:** Measure several representative requests, not one run.

**Project application:** Report median and tail percentiles when sample size supports it.

**Review prompt:** Separate client, backend and provider timing where possible.

**Operational note:** Avoid promising a fixed response time.

**Takeaway:** Use measurements to guide model and UX decisions.

### Additional deep-dive 23: Cost accounting

Input and output usage can be reported at different points in a streaming lifecycle.

**Implementation detail:** Some SDKs provide usage only in a final event or separate response metadata.

**Engineering consequence:** If usage is unavailable, mark it unknown rather than estimating as exact.

**Failure mode:** A cancelled stream may still have billable usage.

**Test design:** Store cost estimates with model and pricing date if you calculate them.

**Project application:** Do not hardcode a price table without a refresh process.

**Review prompt:** Set per-user or per-project limits where supported.

**Operational note:** Test that failed requests do not create fabricated zero-cost records.

**Takeaway:** Cost reporting must be transparent about estimates and missing data.

### Additional deep-dive 24: Provider-managed conversations

Some providers expose conversation or thread resources that retain context remotely.

**Implementation detail:** Using such a feature changes where state is stored and how deletion works.

**Engineering consequence:** Read the provider's current documentation for retention, access and lifecycle behavior.

**Failure mode:** Do not mix local transcript state with provider-managed state without a clear source of truth.

**Test design:** A provider conversation ID is still not your application's authorization token.

**Project application:** Map provider conversation IDs to the authenticated application owner.

**Review prompt:** Handle provider-side deletion or expiration.

**Operational note:** Test behavior after a provider conversation is unavailable.

**Takeaway:** Choose managed state only when its trade-offs fit the product.

### Additional deep-dive 25: Local versus remote history

Local application history gives the product control over storage and access policies.

**Implementation detail:** Provider-managed history may simplify some request construction but can reduce control.

**Engineering consequence:** A hybrid design needs clear ownership of canonical history.

**Failure mode:** Do not store the same transcript in several places without a retention reason.

**Test design:** Define synchronization and deletion behavior.

**Project application:** Consider data residency and contractual requirements.

**Review prompt:** Ensure a user's delete action reaches every storage location under your control.

**Operational note:** Document the design in the architecture diagram.

**Takeaway:** The right choice depends on product and compliance requirements.

### Additional deep-dive 26: Summarization evaluation

A summary should preserve facts needed for likely follow-up questions.

**Implementation detail:** Create test conversations with known dates, names, preferences and corrections.

**Engineering consequence:** Ask follow-up questions whose answers depend on older turns.

**Failure mode:** Score whether the summary preserves key facts and uncertainty.

**Test design:** Check whether negations and corrections survive compression.

**Project application:** Do not allow the summary to turn an uncertain statement into a fact.

**Review prompt:** Keep source references for important summarized claims where feasible.

**Operational note:** Re-evaluate when model or prompt versions change.

**Takeaway:** A shorter summary is not automatically a better summary.

### Additional deep-dive 27: Tool events in chat history

Some agent APIs include tool calls and tool results as distinct message types.

**Implementation detail:** A text-only chat model may not use the same message structure.

**Engineering consequence:** Do not flatten tool calls into ordinary assistant prose if the provider expects structured tool events.

**Failure mode:** Validate tool names and arguments in the backend.

**Test design:** Treat tool results as untrusted content.

**Project application:** Keep tool execution permissions outside the chat transcript.

**Review prompt:** This project can defer actual agent tools to later approved phases.

**Operational note:** If tool events are added, version the message schema.

**Takeaway:** Do not pretend a text mention of a tool is an executed tool call.

### Additional deep-dive 28: Refusal handling

A provider may return a refusal or safety-related outcome.

**Implementation detail:** Do not treat refusal text as a JSON or ordinary answer if the provider marks it separately.

**Engineering consequence:** Show a respectful, concise refusal state when appropriate.

**Failure mode:** Do not retry the same prohibited request through another provider to bypass a safety restriction.

**Test design:** Record only the safe category needed for metrics.

**Project application:** Test refusal handling with controlled fixtures.

**Review prompt:** Keep safety outcomes distinct from transport failures.

**Operational note:** A refusal is not necessarily a system defect.

**Takeaway:** The application must respect provider and product safety boundaries.

### Additional deep-dive 29: Output truncation

A response can stop because an output limit was reached.

**Implementation detail:** The provider may report a finish reason or equivalent metadata.

**Engineering consequence:** A syntactically incomplete final sentence should not be presented as complete.

**Failure mode:** Explain when the response may have been truncated.

**Test design:** A continuation request should include enough context and avoid repeating the prior text.

**Project application:** Continuation can add cost and may introduce inconsistency.

**Review prompt:** Do not continue indefinitely; set a maximum number of continuation attempts.

**Operational note:** Test truncation using a deliberately low output limit.

**Takeaway:** The UI should distinguish truncation from network interruption.

### Additional deep-dive 30: Conversation export

A user may want to export or download their chat.

**Implementation detail:** Export must include only conversations the user is authorized to access.

**Engineering consequence:** Choose a documented format such as JSON or plain text.

**Failure mode:** Escape or serialize content correctly.

**Test design:** Avoid exporting internal prompts, API keys or hidden metadata.

**Project application:** Apply the same retention and deletion rules to exports.

**Review prompt:** Warn users that exported files may contain sensitive information.

**Operational note:** Test export with Unicode and long messages.

**Takeaway:** Export is an optional extension, not required for the Day 18 core.

### Additional deep-dive 31: Conversation deletion

Deleting a conversation should remove or deactivate its messages according to the retention design.

**Implementation detail:** Deletion must verify ownership before changing records.

**Engineering consequence:** If backups or provider-managed copies exist, document their deletion schedule and limitations.

**Failure mode:** Avoid leaving attachment files orphaned after message deletion.

**Test design:** Use transactions or a controlled deletion job for multi-table records.

**Project application:** Do not promise immediate physical erasure if the storage system uses backups.

**Review prompt:** Record deletion outcomes without retaining the deleted content in logs.

**Operational note:** Test deletion and subsequent access.

**Takeaway:** Deletion behavior should be clear to the user.

### Additional deep-dive 32: Conversation title generation

A title can help users find a conversation later.

**Implementation detail:** A title may be generated from the first user message or assigned by the user.

**Engineering consequence:** Do not send extra model calls solely for a title unless the feature justifies the cost.

**Failure mode:** Do not include sensitive details in a title unnecessarily.

**Test design:** Limit title length and sanitize display content.

**Project application:** Allow users to rename a title if the product supports it.

**Review prompt:** Test blank and very long first messages.

**Operational note:** Treat a generated title as untrusted display text.

**Takeaway:** This is optional and should not distract from streaming fundamentals.

### Additional deep-dive 33: Conversation isolation

Each user's conversations must remain isolated.

**Implementation detail:** Never use a single global history list in a multi-user server.

**Engineering consequence:** Pass the authenticated principal into service methods.

**Failure mode:** Filter database queries by owner or an explicit access-control relationship.

**Test design:** Check authorization again when accessing referenced attachments.

**Project application:** Do not rely on hidden UI controls to prevent cross-user access.

**Review prompt:** Test two users with overlapping conversation IDs in separate test fixtures.

**Operational note:** Review cache keys to ensure they include the appropriate user scope.

**Takeaway:** Isolation is a core acceptance criterion, not an advanced feature.

### Additional deep-dive 34: Caching chat responses

Caching may reduce repeated provider calls for identical safe requests.

**Implementation detail:** A cache key must include all inputs that affect the output, including model and relevant prompt version.

**Engineering consequence:** Do not share cached personal responses across users unless the product explicitly supports that behavior and privacy review approves it.

**Failure mode:** Conversation context usually makes a response user- and history-specific.

**Test design:** Define expiration and invalidation behavior.

**Project application:** Do not cache sensitive prompts by default.

**Review prompt:** Record cache hits without logging the full prompt.

**Operational note:** Test that changing a system prompt or model invalidates the relevant cache.

**Takeaway:** Caching is an optional optimization, not a correctness substitute.

### Additional deep-dive 35: Testing asynchronous streams

Use an async fake generator that yields known events.

**Implementation detail:** Test normal completion, exception and cancellation.

**Engineering consequence:** Use deterministic delays only where a timing behavior is under test.

**Failure mode:** Avoid flaky tests that depend on real network speed.

**Test design:** Assert the order of events and final accumulated text.

**Project application:** Test that resources are closed after cancellation.

**Review prompt:** Use framework test clients appropriate to the application's async stack.

**Operational note:** Keep live provider tests separate from continuous integration.

**Takeaway:** A reliable fake stream makes edge cases repeatable.

### Additional deep-dive 36: Mocking provider SDKs

Mock the adapter boundary rather than every internal SDK method in business tests.

**Implementation detail:** A fake adapter should implement the same contract as the real adapter.

**Engineering consequence:** Configure fake sequences for deltas, usage, refusal and errors.

**Failure mode:** Assert that the service sends only the intended history.

**Test design:** Avoid tests that duplicate the implementation's exact internal steps without checking outcomes.

**Project application:** Use a small number of adapter-specific tests for SDK mapping.

**Review prompt:** Keep fixtures sanitized and stable.

**Operational note:** Run tests without credentials.

**Takeaway:** Mocking validates your code path, not provider uptime.

### Additional deep-dive 37: Integration test design

An integration test checks that several application layers work together.

**Implementation detail:** Use a fake provider with the real conversation service and storage layer.

**Engineering consequence:** Verify message order, persistence and status transitions.

**Failure mode:** Test authorization with more than one user.

**Test design:** Test a stream failure after partial output.

**Project application:** Use a temporary test database or isolated test schema.

**Review prompt:** Clean up fixtures after each test.

**Operational note:** Avoid calling a paid API in every CI run.

**Takeaway:** Document which test requires external credentials.

### Additional deep-dive 38: Load and soak tests

A load test checks behavior under expected concurrent usage.

**Implementation detail:** A soak test runs for longer to reveal resource leaks or gradual degradation.

**Engineering consequence:** Do not begin with high traffic against a paid provider account.

**Failure mode:** Use a local fake provider to test backend concurrency and memory behavior.

**Test design:** Measure active connections, queue length, worker use and response latency.

**Project application:** Apply realistic user think time and message sizes.

**Review prompt:** Set a safe test ceiling and stop conditions.

**Operational note:** Review provider rate limits before any live load test.

**Takeaway:** Report test environment and limitations.

### Additional deep-dive 39: Failure injection

Failure injection deliberately simulates conditions such as timeout or disconnect.

**Implementation detail:** It helps prove that cleanup and state transitions work.

**Engineering consequence:** Inject errors before the first chunk and after several chunks.

**Failure mode:** Simulate a provider returning a refusal event.

**Test design:** Simulate a database write failure after generation.

**Project application:** Check whether partial output is retained or marked interrupted according to policy.

**Review prompt:** Verify no worker or connection remains stuck.

**Operational note:** Use controlled fakes rather than intentionally breaking production services.

**Takeaway:** Record each scenario and expected result.

### Additional deep-dive 40: User feedback on responses

A feedback control can capture whether an answer was useful or incorrect.

**Implementation detail:** Store feedback with a conversation and turn reference, not only as an unlinked number.

**Engineering consequence:** Avoid treating one user's rating as proof of general model quality.

**Failure mode:** Do not expose feedback from one user to another.

**Test design:** Provide an optional text reason with length limits and privacy notice.

**Project application:** Use feedback to prioritize evaluation cases and product fixes.

**Review prompt:** Do not automatically train on user feedback without an approved data process.

**Operational note:** Test authorization and deletion behavior for feedback records.

**Takeaway:** Feedback is an optional product feature beyond the minimum streaming scope.

### Additional deep-dive 41: Conversation analytics

Useful aggregate metrics include turn count, completion rate and interruption rate.

**Implementation detail:** Avoid collecting message content for basic operational analytics.

**Engineering consequence:** Aggregate by provider and model only when sample sizes and privacy policy permit.

**Failure mode:** Separate user behavior metrics from model quality metrics.

**Test design:** Do not use analytics to infer sensitive user traits.

**Project application:** Set retention limits and access permissions.

**Review prompt:** Document event names and metric definitions.

**Operational note:** Test that metrics do not contain secrets or prompt text.

**Takeaway:** Use metrics to identify product problems, not to surveil users.

### Additional deep-dive 42: Operational runbook

A runbook explains how to respond when the chatbot fails in production.

**Implementation detail:** Include symptoms, diagnostic checks, safe mitigations and escalation owner.

**Engineering consequence:** Never put secrets in the runbook.

**Failure mode:** Document how to disable a provider or pause new streams safely.

**Test design:** Document how to inspect request IDs and safe error categories.

**Project application:** Include steps for rate-limit and outage handling.

**Review prompt:** Test the runbook in a simulated incident.

**Operational note:** Keep the instructions current when SDKs or deployment settings change.

**Takeaway:** A production-ready feature needs an operational handoff.

### Additional deep-dive 43: Release checklist

Pin tested dependency versions before a release.

**Implementation detail:** Run offline unit and integration tests.

**Engineering consequence:** Run a small live smoke test in a controlled environment.

**Failure mode:** Verify secret configuration and log redaction.

**Test design:** Verify authorization for conversation reads and writes.

**Project application:** Verify stream behavior through the production proxy.

**Review prompt:** Verify cancellation and disconnect cleanup.

**Operational note:** Review privacy, retention and deletion behavior.

**Takeaway:** Document model identifier and prompt version.

### Additional deep-dive 44: Student explanation practice

Explain streaming to a nontechnical teammate using a typing indicator analogy.

**Implementation detail:** Then explain why network chunks are not necessarily model tokens.

**Engineering consequence:** Draw the message lifecycle from user input to stored assistant result.

**Failure mode:** Describe what the application does if the stream fails halfway.

**Test design:** Explain how the app decides which prior turns to send.

**Project application:** Explain why conversation IDs need ownership checks.

**Review prompt:** Describe one test that runs without a provider key.

**Operational note:** Explain one privacy risk of storing chat transcripts.

**Takeaway:** Identify one feature you intentionally left out of the first version.

### Additional deep-dive 45: Project scope control

Build text-only streaming before adding attachments or voice.

**Implementation detail:** Implement one provider adapter before supporting several providers.

**Engineering consequence:** Use an in-memory fake history for the first offline exercise, then persistence if the course environment supports it.

**Failure mode:** Do not add agent tools in this project; those are later syllabus topics.

**Test design:** Do not add long-term memory and imply it is covered by simple chat history.

**Project application:** Keep the core requirements visible in the README.

**Review prompt:** Label optional extensions separately.

**Operational note:** Finish tests before polishing animations.

**Takeaway:** A smaller complete system is better than a large unfinished demo.

### Additional deep-dive 46: Architecture review

Identify the frontend, backend route, conversation service, storage layer and provider adapter.

**Implementation detail:** Show where authentication is checked.

**Engineering consequence:** Show where history is trimmed.

**Failure mode:** Show where streaming events are normalized.

**Test design:** Show where partial results are marked interrupted.

**Project application:** Show where secrets are loaded.

**Review prompt:** Show how a fake provider enters during tests.

**Operational note:** Show which components own cleanup and cancellation.

**Takeaway:** Explain what changes if the provider is replaced.

### Additional deep-dive 47: Data model migration

Conversation features evolve as the product adds status, sequence and model metadata.

**Implementation detail:** Use migrations to change database schemas safely.

**Engineering consequence:** Do not edit production tables manually as a routine deployment practice.

**Failure mode:** Add nullable fields or backfill steps carefully when old rows exist.

**Test design:** Test migration from a previous schema snapshot.

**Project application:** Keep application code compatible during a staged rollout when needed.

**Review prompt:** Do not store SDK objects in database columns.

**Operational note:** Persist stable normalized fields and JSON only for deliberate flexible metadata.

**Takeaway:** Document migration and rollback considerations.

### Additional deep-dive 48: Error messages

A user-facing error should say what happened and what they can do next.

**Implementation detail:** Do not show raw exception traces or provider internals in the UI.

**Engineering consequence:** A rate-limit message can suggest waiting before retrying.

**Failure mode:** A timeout message can explain that the response did not finish.

**Test design:** An authorization error should not reveal another user's conversation exists.

**Project application:** A configuration error should be visible to the operator, not expose a key.

**Review prompt:** Keep internal error codes for support and metrics.

**Operational note:** Use consistent wording across CLI and web interfaces.

**Takeaway:** Test that messages remain useful without sensitive detail.

### Additional deep-dive 49: Retry policy

Retry only failures that are plausibly transient.

**Implementation detail:** Do not retry invalid input or invalid credentials automatically.

**Engineering consequence:** Use a bounded attempt count and exponential backoff with jitter where appropriate.

**Failure mode:** Respect provider retry-after information when available.

**Test design:** A stream retry may restart generation and produce a different answer.

**Project application:** Do not append a restarted answer to partial output without clear semantics.

**Review prompt:** Use an idempotency strategy where supported.

**Operational note:** Record attempt count and final outcome.

**Takeaway:** Test retry exhaustion using a fake provider.

### Additional deep-dive 50: Model and prompt reproducibility

Record model identifier and prompt version for each generation where useful.

**Implementation detail:** Provider aliases may point to updated model revisions.

**Engineering consequence:** A prompt edit can change output even if the model remains the same.

**Failure mode:** Keep a small regression dataset for follow-up behavior.

**Test design:** Do not store raw sensitive content merely to reproduce a test.

**Project application:** Use synthetic inputs and expected behavior descriptions.

**Review prompt:** Compare quality before and after changing model or prompt.

**Operational note:** Document when a test result was produced.

**Takeaway:** Reproducibility helps explain changes and regressions.

### Additional deep-dive 51: Internationalization

Users may send text in multiple languages and scripts.

**Implementation detail:** Do not assume one character equals one token or byte.

**Engineering consequence:** Store and transmit Unicode correctly.

**Failure mode:** Use UTF-8 consistently across application boundaries.

**Test design:** Test emoji, accented characters and Indic-language content.

**Project application:** Do not normalize Unicode without understanding whether it changes identifiers or meaning.

**Review prompt:** The model may respond in a different language unless the application sets an appropriate instruction.

**Operational note:** Measure quality across the languages the product claims to support.

**Takeaway:** Do not claim multilingual reliability from one short example.

### Additional deep-dive 52: Clock and timestamp handling

Store timestamps in UTC where practical.

**Implementation detail:** Convert to the user's local timezone for display.

**Engineering consequence:** Do not compare naive and timezone-aware datetimes without an explicit conversion.

**Failure mode:** Use server-side timestamps for authoritative ordering when appropriate.

**Test design:** Client clocks may be wrong or manipulated.

**Project application:** A sequence number can complement timestamps for strict ordering.

**Review prompt:** Test daylight-saving transitions if users operate across such regions.

**Operational note:** Document timestamp format in exports and APIs.

**Takeaway:** Consistent time handling simplifies audit and debugging.

### Additional deep-dive 53: Multi-device synchronization

A user may open the same conversation on two devices.

**Implementation detail:** Define how new messages appear across active sessions.

**Engineering consequence:** Use polling, server-sent events or another documented update mechanism if synchronization is required.

**Failure mode:** Avoid two devices starting conflicting generations without a policy.

**Test design:** Use server-side ordering and state as the source of truth.

**Project application:** Handle reconnect by fetching authoritative recent history.

**Review prompt:** Do not trust a stale browser transcript as canonical.

**Operational note:** Test a message added from a second session.

**Takeaway:** Multi-device sync is an extension, not required for a single-session demo.

### Additional deep-dive 54: Conversation search

Search may operate over titles, message text or metadata.

**Implementation detail:** Searching personal conversations requires the same ownership checks as reading them.

**Engineering consequence:** Avoid indexing sensitive content without a retention and deletion policy.

**Failure mode:** Use database indexes or a search system appropriate to the scale.

**Test design:** Highlight matches without rendering untrusted HTML.

**Project application:** Do not leak whether another user has a matching conversation.

**Review prompt:** Test deletion and search-index cleanup.

**Operational note:** Keep search optional for this day's core objective.

**Takeaway:** A feature should not be added without its privacy design.

### Additional deep-dive 55: Data export and portability

A user may want their conversation history in a portable format.

**Implementation detail:** Define a stable export schema and include timestamps and roles.

**Engineering consequence:** Do not export hidden instructions or credentials.

**Failure mode:** Escape content safely and preserve Unicode.

**Test design:** Verify export ownership and scope.

**Project application:** Warn that downloaded content may be sensitive.

**Review prompt:** Support deletion and retention rules for generated exports.

**Operational note:** Test round-trip parsing if importing is supported.

**Takeaway:** Do not confuse a provider's raw event log with a user-friendly transcript.

### Additional deep-dive 56: Incident response for leaked transcript

A transcript leak is a privacy incident, not just a UI bug.

**Implementation detail:** Restrict access to the affected storage and logs.

**Engineering consequence:** Preserve only the operational evidence required by the incident process.

**Failure mode:** Identify affected conversations and users using authorized audit data.

**Test design:** Follow organizational notification and legal processes.

**Project application:** Fix the access-control root cause and add regression tests.

**Review prompt:** Rotate credentials if provider secrets were also exposed.

**Operational note:** Review backups and exports according to policy.

**Takeaway:** Do not conceal the incident or speculate beyond verified facts.

### Additional deep-dive 57: Final architecture walkthrough

Start at the browser input and trace the request to the backend.

**Implementation detail:** Show authentication and conversation ownership checks.

**Engineering consequence:** Show validation and history selection.

**Failure mode:** Show the provider adapter and stream event mapping.

**Test design:** Show the client event handling and text assembly.

**Project application:** Show persistence and completion state transitions.

**Review prompt:** Show error and cancellation paths.

**Operational note:** Show tests that replace the provider with a fake.

**Takeaway:** Explain privacy and resource controls.


## Troubleshooting and test checklist
- [ ] Chunks assemble in order.
- [ ] Metadata is not rendered as answer text.
- [ ] Failure after partial output marks the turn interrupted.
- [ ] Unsupported roles and blank messages are rejected.
- [ ] History is ordered and bounded.
- [ ] Conversation ownership is checked on every read and write.
- [ ] A fake provider is used for offline tests.
- [ ] Cancellation closes supported resources.
- [ ] Secrets and transcript content are absent from logs.

## Daily MCQs
1. A stream chunk is one event or piece delivered during generation, not necessarily a full sentence.
2. A partial answer after a network failure must be marked incomplete.
3. Stateless chat requests need relevant history included by the application.
4. History limits control context size, cost and relevance.
5. A conversation ID is not authorization; server-side ownership checks are required.

## Interview preparation
**Q: What is the benefit of streaming?** It progressively displays generated content, reducing perceived wait time. It requires ordered event assembly, completion detection and partial-failure handling.

**Q: How is multi-turn context maintained?** Store ordered messages under an authenticated owner, load relevant history, apply a context budget and send the selected messages with the current turn.

**Q: What is a delta?** Newly generated content. It differs from a cumulative snapshot; appending snapshots as deltas duplicates text.

**Q: How should interruption be handled?** Mark the result incomplete, release resources, log a safe error category and retry only under a bounded safe policy.

**Q: How is chat history protected?** Authenticate users, check ownership on every operation, minimize stored content, apply retention and deletion rules and redact logs.

## Completion gate
Day 18 is complete when a learner can explain stream events, assemble them safely, preserve authorized ordered context, control history size and represent partial failures honestly.
