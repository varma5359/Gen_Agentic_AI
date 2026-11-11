# Day 16 — OpenAI and Gemini API Integration

**Phase:** 3 — LLM Application Development
**Approved project:** Python LLM API Integration Application
**Study time:** 2–3 hours
**Level:** Absolute beginner to entry-level application developer

## How to use this lesson

- Read one numbered section at a time; do not copy code before understanding the inputs and outputs.
- Type the examples yourself in a virtual environment. Typing helps you notice punctuation, indentation and naming.
- Run the offline exercises before configuring a paid API account.
- Keep API keys private. Never paste a real key into a screenshot, GitHub issue, notebook or chat.
- The provider SDK changes over time. Follow the current official documentation for installation, supported model names and exact method signatures.
- This lesson teaches a maintainable integration pattern. It does not promise that one model name or SDK method will remain valid forever.

## Learning outcomes

By the end, you should be able to:
- Explain what an LLM API does and how a Python application communicates with it.
- Distinguish a provider, model, SDK, API key, request and response.
- Create and activate a Python virtual environment.
- Load local development settings without committing secrets.
- Explain why secrets belong on a server and not in browser JavaScript.
- Organize a small integration into configuration, provider, service and CLI modules.
- Make a minimal provider call using the official SDK documentation for the installed version.
- Inspect response content and usage metadata safely.
- Handle missing configuration, invalid input, network failure and provider errors.
- Mock provider behavior so automated tests do not spend money.
- Compare OpenAI and Gemini using the same evaluation task.
- Submit a documented, tested Python LLM API Integration Application.

## Prerequisites and setup

### What you should already know
- A Python variable stores a value under a name.
- A function groups instructions and can accept arguments.
- An `if` statement chooses a path based on a condition.
- A dictionary stores key-value pairs.
- An import makes code from a module available.
- A terminal runs commands in the current working directory.
- Git records project history; `.gitignore` excludes local files from normal commits.

### Create the project folder
```bash
mkdir day16_llm_api
cd day16_llm_api
python -m venv .venv
```

**What each command does**
- `mkdir day16_llm_api` creates a folder for this day's work.
- `cd day16_llm_api` moves the terminal into that folder.
- `python -m venv .venv` creates an isolated Python environment named `.venv`.
- If `python` is not available on your computer, try `python3` or the Python launcher appropriate to your operating system.

### Activate the environment
```bash
# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS / Linux
source .venv/bin/activate
```

- The activation command changes which Python and pip are found first in the terminal.
- Your prompt may show `(.venv)` after activation.
- If PowerShell blocks script activation, follow your organization's device policy; do not disable security controls blindly.
- Confirm the interpreter with `python --version` and `python -m pip --version`.

### Suggested folder structure
```text
day16_llm_api/
├── .env                 # local secrets; never commit
├── .env.example         # safe placeholder settings
├── .gitignore
├── requirements.txt
├── README.md
├── main.py              # command-line entry point
└── llm_app/
    ├── __init__.py
    ├── config.py        # read and validate configuration
    ├── models.py        # internal request/result data
    ├── providers.py     # provider adapters
    └── service.py       # application use case
```

### Install dependencies
Use the current official installation instructions for the SDK you intend to test. A common development setup is:
```bash
python -m pip install --upgrade pip
python -m pip install python-dotenv
python -m pip install openai
python -m pip install google-genai
python -m pip install pytest
python -m pip freeze > requirements.txt
```

- `python-dotenv` loads a local `.env` file during development.
- `openai` is the commonly used OpenAI Python package distribution.
- `google-genai` is the commonly used Google Gen AI Python package distribution.
- `pytest` runs automated tests.
- Verify current package names and supported SDK versions against official provider documentation before teaching or deploying.
- Do not install both SDKs if your exercise only uses one provider; the second provider is optional for comparison.

### Environment files
Create `.env.example` with placeholders:
```dotenv
LLM_PROVIDER=openai
OPENAI_API_KEY=replace_with_your_local_key
GEMINI_API_KEY=replace_with_your_local_key
OPENAI_MODEL=replace_with_a_current_supported_model
GEMINI_MODEL=replace_with_a_current_supported_model
REQUEST_TIMEOUT_SECONDS=30
```

Create `.env` locally and replace placeholders with your own credentials. Never paste the real values into the course submission.

Create `.gitignore`:
```gitignore
.env
.venv/
__pycache__/
.pytest_cache/
.coverage
*.pyc
```

**Important:** `.gitignore` prevents many accidental additions, but it cannot erase a secret already committed. If a key is exposed, revoke it at the provider and create a new one.

## Core concepts, taught from zero

### 1. What an API does

An API is a contract that lets one program request a capability from another program.

**How it works in practice:** Your Python application sends a request; the provider authenticates it, processes it and returns a response.

**Design rule:** Treat the provider as an external dependency, not as a Python function that is guaranteed to succeed.

**Request and response detail:** The request usually contains a model identifier, messages or input, generation settings and optional metadata.

**What to inspect:** The response commonly contains generated content, usage information and provider-specific identifiers.

**Common beginner mistake:** Never assume every provider returns the same JSON shape; normalize provider responses at your application boundary.

**Project connection:** In the project, isolate provider calls in a service module so the CLI or web layer does not know SDK details.

**Test idea:** Test the boundary with a fake provider response before making a paid network request.

**Remember:** A successful HTTP response does not prove that the generated answer is factually correct.

### 2. OpenAI and Gemini as providers

OpenAI and Google Gemini both expose hosted models through authenticated APIs and supported SDKs.

**How it works in practice:** The provider supplies model inference; your application owns validation, business rules, user experience and data handling.

**Design rule:** A provider account, an enabled API product and a valid key are separate prerequisites.

**Request and response detail:** Model names are identifiers that can change as providers release, retire or alias models.

**What to inspect:** Do not copy a model name from an old tutorial without checking the provider's current model catalogue.

**Common beginner mistake:** Keep provider-specific request construction behind a small adapter interface.

**Project connection:** Compare providers using the same task, input, output schema, latency measurement and evaluation rubric.

**Test idea:** A model that is cheaper for one task may be less suitable for another task.

**Remember:** Document the tested model identifier and date in your project README.

### 3. SDK versus raw HTTP

An SDK is a library that wraps HTTP requests, authentication and response parsing.

**How it works in practice:** Raw HTTP gives more control but requires you to manage headers, serialization, status codes and response parsing.

**Design rule:** For a beginner project, use the official SDK unless a specific requirement needs raw HTTP.

**Request and response detail:** An SDK does not remove the need to understand HTTP, errors, timeouts or network behavior.

**What to inspect:** Pin compatible package versions in a requirements file or lock file.

**Common beginner mistake:** Read the installed SDK version's documentation; method names can differ between major versions.

**Project connection:** Do not mix examples from different SDK generations in one codebase.

**Test idea:** Keep SDK imports inside the provider adapter when practical.

**Remember:** A small adapter makes later migration or provider comparison easier.

### 4. Creating a provider account

Create an account only through the provider's official developer console.

**How it works in practice:** Review billing, quotas, regional availability and data handling before creating credentials.

**Design rule:** A free trial or promotional credit is not a guarantee of unlimited API use.

**Request and response detail:** Set a spending limit or budget alert where the provider supports it.

**What to inspect:** Use a dedicated development key rather than a shared personal key for a team project.

**Common beginner mistake:** Do not ask students to paste keys into notebooks, screenshots, issue trackers or chat messages.

**Project connection:** If a key is exposed, revoke it and issue a replacement immediately.

**Test idea:** Record account setup steps without recording the secret value.

**Remember:** For classroom work, explain that students may incur usage charges depending on their account.

### 5. API key anatomy

An API key is a bearer credential: possession may grant the permissions associated with it.

**How it works in practice:** The key is sent through the SDK's supported authentication mechanism, commonly an authorization header.

**Design rule:** A key is not a model name, project ID, organization ID or endpoint URL.

**Request and response detail:** Never print the complete key to logs, terminal output or exception messages.

**What to inspect:** Mask secrets in diagnostics; showing only a short suffix is rarely necessary for beginners.

**Common beginner mistake:** Do not commit keys in Python source, `.env` files, notebooks or sample configuration files.

**Project connection:** A `.gitignore` entry reduces accidental commits but does not protect a key already committed.

**Test idea:** Environment variables keep configuration outside source code but are not a complete secrets-management system.

**Remember:** Production deployments should use the platform's secret store or workload identity where supported.

### 6. Environment variables

An environment variable is a name-value setting supplied to a running process.

**How it works in practice:** Python can read environment variables with `os.environ` or `os.getenv`.

**Design rule:** `os.getenv('OPENAI_API_KEY')` returns `None` when the variable is absent unless a default is supplied.

**Request and response detail:** Validate required configuration during application startup rather than failing much later during a request.

**What to inspect:** Do not place a real secret as the default value in source code.

**Common beginner mistake:** Use distinct variable names such as `OPENAI_API_KEY` and `GEMINI_API_KEY`.

**Project connection:** A variable set in one terminal session may not exist in another terminal or service process.

**Test idea:** Restart the process after changing environment configuration when required by the operating system or service manager.

**Remember:** Provide `.env.example` with placeholder values, never real credentials.

### 7. Loading a .env file

A `.env` file is a local convenience for development configuration.

**How it works in practice:** A library such as `python-dotenv` can load the file into process environment variables.

**Design rule:** Install the dependency in the active virtual environment, not a different system Python.

**Request and response detail:** Call the loader early in the application's startup path, before reading settings.

**What to inspect:** The file should contain simple `KEY=value` entries and should not be committed when it contains secrets.

**Common beginner mistake:** Quote values when special characters or spaces require it according to the loader's syntax.

**Project connection:** Do not assume `.env` is automatically loaded by Python; loading must be explicit or handled by the runtime.

**Test idea:** Deployment platforms often provide environment variables directly, so a `.env` file may not be needed in production.

**Remember:** If a key is missing, check the filename, working directory, variable spelling and process environment.

### 8. Configuration module

A configuration module centralizes settings so they are not scattered through the codebase.

**How it works in practice:** Read configuration once and expose a clear settings object or validated constants.

**Design rule:** Separate secret settings from non-secret settings such as timeout seconds or default output length.

**Request and response detail:** Fail fast with a clear message when a required key is absent.

**What to inspect:** Do not include secret values in `repr`, debug dumps or application startup logs.

**Common beginner mistake:** Allow the model identifier to be configured so experiments do not require code edits.

**Project connection:** Validate numeric settings such as timeout and retry count before using them.

**Test idea:** Use different settings for development, testing and production without changing application logic.

**Remember:** Write unit tests for missing and malformed configuration.

### 9. Virtual environments

A virtual environment isolates the project's Python packages from other projects.

**How it works in practice:** Create one environment per project to avoid dependency conflicts.

**Design rule:** Activate the environment before installing SDKs or running the application.

**Request and response detail:** Check `python --version` and `python -m pip --version` to confirm which interpreter and package installer are active.

**What to inspect:** Use `python -m pip install ...` to bind installation to the selected interpreter.

**Common beginner mistake:** A package installed globally may not be visible inside the virtual environment.

**Project connection:** Recreate environments from declared dependencies instead of copying environment folders between machines.

**Test idea:** Do not commit `.venv` to Git.

**Remember:** When an import fails, first confirm the active interpreter and installed package list.

### 10. Installing official SDKs

Install the official package using the provider's current installation instructions.

**How it works in practice:** For OpenAI Python examples, the package is commonly installed as `openai`; verify the current SDK docs before pinning a version.

**Design rule:** For Google Gemini API examples, the current unified Python SDK is commonly distributed as `google-genai`; verify the current docs before pinning a version.

**Request and response detail:** Do not confuse a package distribution name with its Python import name.

**What to inspect:** Install only the provider SDKs you intend to use in the current exercise.

**Common beginner mistake:** Record exact tested dependency versions in the project dependency file.

**Project connection:** Run a small import check after installation.

**Test idea:** If pip reports a dependency conflict, inspect the full resolver message instead of randomly upgrading everything.

**Remember:** Avoid installing similarly named unofficial packages from untrusted publishers.

### 11. First API call

The first API call should be a minimal smoke test, not a large application.

**How it works in practice:** Use a short harmless prompt that does not contain personal or confidential information.

**Design rule:** Set a small output limit to control cost and response size.

**Request and response detail:** Print only the returned text and non-sensitive usage metadata needed for the exercise.

**What to inspect:** Check that the response contains usable content before treating the call as successful.

**Common beginner mistake:** Handle the possibility of an empty response or a blocked response.

**Project connection:** Keep the smoke-test script separate from the production service module.

**Test idea:** Run it manually after configuring credentials and before debugging the larger project.

**Remember:** Document the expected success shape without hardcoding a live response.

### 12. Messages and roles

A chat request commonly represents input as a sequence of messages or content blocks.

**How it works in practice:** A system or instruction message establishes application-level behavior where supported by the model interface.

**Design rule:** A user message contains the task or question from the person using the application.

**Request and response detail:** An assistant message represents prior model output when conversation history is included.

**What to inspect:** Some APIs use different naming or input formats; map your internal roles to provider-specific formats.

**Common beginner mistake:** Never assume a provider's role semantics are identical across all model families.

**Project connection:** Keep application policy outside user-controlled message content.

**Test idea:** Validate role names before constructing a request.

**Remember:** Do not let a user impersonate an application instruction by concatenating raw text into a privileged message.

### 13. Model selection

Choose a model based on task quality, latency, availability, context requirements and cost.

**How it works in practice:** A reasoning-heavy task may need a different model from short classification or extraction.

**Design rule:** A larger model is not automatically the best choice for every production task.

**Request and response detail:** Test candidate models against a representative evaluation set rather than one impressive example.

**What to inspect:** Record model identifier, prompt version and evaluation result together.

**Common beginner mistake:** Check provider documentation for supported features such as structured output or streaming.

**Project connection:** Do not silently change model identifiers in production without regression testing.

**Test idea:** Provide a configuration switch for development experiments.

**Remember:** Explain the trade-off in the project report.

### 14. Generation parameters

Generation parameters influence response length, randomness or other model behavior.

**How it works in practice:** Only send parameters supported by the selected model and endpoint.

**Design rule:** A parameter accepted by one provider may have a different name or meaning at another provider.

**Request and response detail:** Keep default settings conservative for deterministic extraction tasks.

**What to inspect:** Separate application constraints from model sampling settings.

**Common beginner mistake:** Validate numeric parameter ranges before sending requests.

**Project connection:** Do not treat parameter tuning as a replacement for clear instructions and evaluation.

**Test idea:** Record the settings used in experiments so results can be reproduced.

**Remember:** If the provider rejects a parameter, inspect the error and model capability documentation.

### 15. Request construction

Build the request from validated application data rather than raw untrusted dictionaries.

**How it works in practice:** Keep model name, messages, timeout and output constraints explicit.

**Design rule:** Do not include internal secrets or unrelated user data in the prompt.

**Request and response detail:** Serialize structured input using a JSON serializer instead of manual string concatenation when appropriate.

**What to inspect:** Check required fields before sending the request.

**Common beginner mistake:** Avoid sending enormous histories or documents without a deliberate context strategy.

**Project connection:** Use a stable internal request object so provider adapters can translate it.

**Test idea:** Log a request correlation ID, not the entire private prompt by default.

**Remember:** Unit-test request construction independently from network execution.

### 16. Response inspection

Inspect the response object according to the installed SDK's documented schema.

**How it works in practice:** Distinguish generated content from metadata such as model, finish reason and token usage.

**Design rule:** Some responses may contain multiple content blocks or candidates.

**Request and response detail:** A refusal, safety block or empty output is not the same as a transport failure.

**What to inspect:** Check finish reason or truncation metadata when the SDK exposes it.

**Common beginner mistake:** Do not assume the first content field is always a plain string.

**Project connection:** Normalize the provider response into an internal result object.

**Test idea:** Keep raw provider metadata available for debugging while avoiding secret or personal-data leakage.

**Remember:** Write tests for normal, empty, blocked and unexpected response shapes.

### 17. Usage and cost awareness

Many provider responses expose input and output token usage or equivalent metering data.

**How it works in practice:** Usage values help estimate cost and identify unexpectedly large requests.

**Design rule:** Pricing depends on model, region, modality, cached input and provider policy; never hardcode an old price as timeless truth.

**Request and response detail:** Keep a usage record with timestamp, provider, model and request ID when appropriate.

**What to inspect:** Avoid storing user content merely to calculate cost.

**Common beginner mistake:** Use budgets, quotas and alerts where available.

**Project connection:** A retry can incur another charge if the provider processed the original request.

**Test idea:** Estimate cost before batch processing a large dataset.

**Remember:** Display estimates as estimates, not guaranteed invoices.

### 18. Timeouts

A timeout is a limit on how long the application waits for a network operation.

**How it works in practice:** Without timeouts, a request may occupy a worker for too long when the provider or network is unhealthy.

**Design rule:** Choose connect and read timeout values based on the task's expected duration.

**Request and response detail:** A timeout does not prove the provider did not process the request.

**What to inspect:** Retrying a timed-out non-idempotent operation can create duplicate work or charges.

**Common beginner mistake:** Return a clear application-level timeout error to the caller.

**Project connection:** Measure actual latency before tuning timeout values.

**Test idea:** Use separate timeout settings for short classification and longer generation tasks when needed.

**Remember:** Test timeout behavior with a mock rather than waiting for a real provider outage.

### 19. Rate limits

A rate limit restricts request volume, token throughput or another usage dimension.

**How it works in practice:** Limits may be scoped by project, organization, model or account tier.

**Design rule:** A burst of concurrent requests can exceed a limit even when average traffic seems low.

**Request and response detail:** Read response headers or structured error metadata when the provider exposes rate-limit information.

**What to inspect:** Use bounded backoff rather than an immediate tight retry loop.

**Common beginner mistake:** Queue or throttle work when the application has sustained traffic.

**Project connection:** A rate limit is different from an invalid API key or insufficient quota.

**Test idea:** Do not ask every end user to retry independently without controlling aggregate traffic.

**Remember:** Test the application's behavior when a provider returns a rate-limit response.

### 20. Provider adapter design

A provider adapter translates your application's internal request into a provider-specific SDK call.

**How it works in practice:** The adapter also converts provider-specific responses into a stable internal result.

**Design rule:** Keep provider selection out of route handlers and business logic.

**Request and response detail:** Use a small interface such as `generate(request) -> result` for the first version.

**What to inspect:** Do not build a complex plugin framework for a two-provider beginner exercise.

**Common beginner mistake:** Make unsupported features explicit rather than silently ignoring them.

**Project connection:** Inject the adapter into services to make tests easy.

**Test idea:** A fake adapter can return deterministic output without network access.

**Remember:** A clean adapter boundary reduces the cost of adding another provider later.

### 21. Provider fallback

Fallback means switching to another supported path when the preferred provider cannot serve the request.

**How it works in practice:** Fallback should be based on defined failure categories, not every exception.

**Design rule:** Do not fall back after an application validation error; fix the invalid input instead.

**Request and response detail:** A provider fallback may produce different output quality, format or safety behavior.

**What to inspect:** Validate fallback output using the same application-level schema and rules.

**Common beginner mistake:** Avoid retrying the same provider indefinitely before trying a fallback.

**Project connection:** Record which provider served the request for observability.

**Test idea:** Disclose degraded behavior where it affects user expectations.

**Remember:** Test primary success, primary failure plus fallback success, and all providers failing.

### 22. Privacy and data minimization

Send only the data needed to complete the user's task.

**How it works in practice:** Remove unnecessary identifiers, secrets and unrelated document sections before calling a model.

**Design rule:** Review provider retention and data-processing terms for the account and product being used.

**Request and response detail:** Do not send regulated or confidential data unless the organization has approved that use.

**What to inspect:** Explain to users when their content is sent to an external AI provider.

**Common beginner mistake:** Keep access to API credentials restricted to the server process that needs them.

**Project connection:** Do not expose provider keys in browser JavaScript or mobile app bundles.

**Test idea:** Define log retention and redact prompts when logs could contain personal data.

**Remember:** Privacy requirements are part of system design, not a final checkbox.

### 23. Prompt injection boundary

A prompt is not a security boundary or authorization mechanism.

**How it works in practice:** A user can submit text that attempts to override application instructions.

**Design rule:** Do not let model-generated text directly authorize payments, account changes or privileged actions.

**Request and response detail:** Enforce permissions in ordinary application code before a sensitive operation.

**What to inspect:** Treat retrieved documents and user-provided content as untrusted data.

**Common beginner mistake:** Keep secrets out of prompts because models may repeat or transform supplied text.

**Project connection:** For this API integration day, focus on safe request composition and do not claim prompts alone prevent attacks.

**Test idea:** Add security controls and human approval in later agent phases.

**Remember:** Test adversarial inputs as part of application validation.

### 24. Error categories

Configuration errors happen before or during request construction, such as a missing key.

**How it works in practice:** Authentication errors indicate that credentials are missing, invalid, revoked or unauthorized.

**Design rule:** Permission errors can indicate that the account cannot access a model or feature.

**Request and response detail:** Validation errors mean the request does not satisfy the endpoint's contract.

**What to inspect:** Rate-limit errors mean the application must slow down or queue work.

**Common beginner mistake:** Quota or billing errors may require account action rather than a retry.

**Project connection:** Network errors include DNS, connection reset and transport failures.

**Test idea:** Timeout errors mean the application stopped waiting within its configured limit.

**Remember:** Server errors may be transient but still need bounded recovery behavior.

### 25. Testing without a live API

Unit tests should not depend on a paid provider call.

**How it works in practice:** Mock the adapter or inject a fake implementation into the service.

**Design rule:** Use deterministic fixtures for success, empty response and failure cases.

**Request and response detail:** Assert that the service passes the correct model and messages to the adapter.

**What to inspect:** Assert that provider exceptions are translated to safe application errors.

**Common beginner mistake:** Keep one optional manual smoke test for a real key and real network.

**Project connection:** Do not make CI depend on personal API credentials.

**Test idea:** Never use real customer data in test fixtures.

**Remember:** A passing mock test proves application logic, not provider availability or model quality.

### 26. Logging

Log operational facts such as request ID, provider, model, duration and outcome.

**How it works in practice:** Do not log API keys, authorization headers or full secret configuration.

**Design rule:** Avoid logging complete prompts and responses by default because they may contain personal information.

**Request and response detail:** Use structured fields so logs can be searched and aggregated.

**What to inspect:** Record error category and retry count without exposing raw internal stack traces to end users.

**Common beginner mistake:** Use a correlation ID to connect a web request with the provider call.

**Project connection:** Keep log levels meaningful: DEBUG for local detail, INFO for normal events, WARNING for recoverable issues and ERROR for failed operations.

**Test idea:** Rotate and retain logs according to the application's policy.

**Remember:** Test redaction by intentionally passing a fake secret and checking captured logs.

### 27. CLI application structure

A command-line interface is a simple way to test an LLM integration before building a web UI.

**How it works in practice:** Keep `main.py` responsible for reading user input and printing the result.

**Design rule:** Keep configuration loading in a settings module.

**Request and response detail:** Keep provider-specific calls in a provider module.

**What to inspect:** Keep business behavior in a service module.

**Common beginner mistake:** Keep input validation in a separate function or schema.

**Project connection:** Avoid putting all code in one large script as the project grows.

**Test idea:** Use `if __name__ == '__main__':` to control direct script execution.

**Remember:** A modular CLI can later be reused by FastAPI or Streamlit.

### 28. Input validation

Validate that a prompt is a string and is not empty after trimming whitespace.

**How it works in practice:** Apply a reasonable maximum length before sending data to a provider.

**Design rule:** Reject unsupported values with a clear message rather than letting an SDK fail obscurely.

**Request and response detail:** Do not silently truncate user content unless the product explicitly communicates that behavior.

**What to inspect:** Normalize line endings and whitespace only when doing so preserves meaning.

**Common beginner mistake:** Check that the selected provider is one of the supported choices.

**Project connection:** Validate model identifiers against configuration or a maintained allowlist when appropriate.

**Test idea:** Keep validation deterministic and testable without network access.

**Remember:** Never treat input validation as a substitute for prompt-injection defenses.

### 29. Output limits

Set output limits to protect cost, latency and application expectations.

**How it works in practice:** The exact parameter name and supported range vary by provider and model.

**Design rule:** A response may stop because it reached an output limit rather than because the task is complete.

**Request and response detail:** Inspect finish metadata when available and handle truncated output explicitly.

**What to inspect:** Do not ask the model to produce unlimited content.

**Common beginner mistake:** Choose a limit appropriate to the task: a title needs far less output than a report.

**Project connection:** If output is truncated, decide whether to ask for a continuation or return a clear partial result.

**Test idea:** Avoid blindly concatenating continuations because they may repeat or contradict earlier text.

**Remember:** Test a deliberately small output limit to understand truncation behavior.

### 30. Responsible model use

A language model generates likely outputs; it is not a database of guaranteed facts.

**How it works in practice:** Model output can be incomplete, outdated, biased or fabricated.

**Design rule:** For high-impact decisions, require human review and authoritative verification.

**Request and response detail:** Do not present generated legal, medical or financial content as professional advice.

**What to inspect:** Tell users when output is AI-generated where appropriate.

**Common beginner mistake:** Avoid using a model to infer sensitive attributes from unrelated data.

**Project connection:** Use evaluation examples that represent the real user population and task.

**Test idea:** Measure errors, not only impressive demonstrations.

**Remember:** Define what the application should do when confidence or evidence is insufficient.

## Python building blocks for this application

### 1. Reading environment variables
```python
import os

api_key = os.getenv("OPENAI_API_KEY")
if not api_key:
    raise RuntimeError("OPENAI_API_KEY is not configured")
```

- `import os` imports Python's operating-system interface.
- `os.getenv(...)` reads a variable from the process environment.
- The result is a string when present and `None` when absent.
- `if not api_key` catches both a missing value and an empty string.
- The exception stops startup with a clear configuration message.
- Never print `api_key` to confirm that it exists.

### 2. Loading local development configuration
```python
from dotenv import load_dotenv
load_dotenv()
```

- Import `load_dotenv` from the installed `python-dotenv` package.
- Call it before reading environment variables.
- By default it searches for a `.env` file using the package's discovery behavior.
- Production environments should normally inject secrets through the deployment platform.
- The application should work when variables are supplied by the operating system even if no `.env` file exists.

### 3. Validating user input
```python
def validate_prompt(prompt: str) -> str:
    if not isinstance(prompt, str):
        raise TypeError("Prompt must be text")
    cleaned = prompt.strip()
    if not cleaned:
        raise ValueError("Prompt cannot be empty")
    if len(cleaned) > 8000:
        raise ValueError("Prompt is too long for this demo")
    return cleaned
```

- `prompt: str` is a type hint: it communicates the expected input type.
- `-> str` communicates that the function returns text.
- `isinstance` checks the runtime type.
- `strip` removes whitespace from the beginning and end.
- `len` counts characters, not tokens.
- The character limit is an application rule for this exercise, not a provider context-window guarantee.
- Returning `cleaned` means later code receives normalized input.

### 4. A provider-neutral request model
```python
from dataclasses import dataclass

@dataclass
class LLMRequest:
    prompt: str
    system_instruction: str
    max_output_tokens: int = 300
```

- A dataclass is a convenient way to define a class mainly used to hold data.
- `@dataclass` asks Python to generate common methods such as an initializer.
- `prompt` stores the user's task.
- `system_instruction` stores the application's behavior guidance.
- `max_output_tokens` has a default value when the caller does not supply one.
- This is an internal application model; each provider adapter may translate it differently.

### 5. A provider-neutral result model
```python
from dataclasses import dataclass

@dataclass
class LLMResult:
    text: str
    provider: str
    model: str
    request_id: str | None = None
    input_tokens: int | None = None
    output_tokens: int | None = None
```

- `text` is the normalized generated content.
- `provider` identifies which adapter served the request.
- `model` records the model identifier used.
- `str | None` means the value may be a string or `None` in supported Python versions.
- Token usage can be absent, so optional fields should not be assumed to exist.
- Never fabricate usage values when the provider does not return them.

## Provider integration pattern

### Architecture
```text
User enters a task
       |
       v
CLI validates the input
       |
       v
Application service
       |
       v
Provider adapter selected from configuration
       |
       v
Official provider SDK
       |
       v
External LLM API
       |
       v
Provider response
       |
       v
Adapter normalizes the response
       |
       v
Service returns an internal result
       |
       v
CLI displays safe output and usage metadata
```

### Why separate these layers?
- The CLI should not know the provider's response object structure.
- The service should not read terminal input directly.
- The provider adapter should not decide how the result is displayed.
- Configuration should not be duplicated in several files.
- Tests should be able to replace a real provider with a fake one.
- A later FastAPI route can call the same service without copying SDK code.

### Example configuration module
```python
# llm_app/config.py
import os
from dotenv import load_dotenv

load_dotenv()

def required_setting(name: str) -> str:
    value = os.getenv(name)
    if value is None or not value.strip():
        raise RuntimeError(f"Required setting is missing: {name}")
    return value.strip()

def optional_setting(name: str, default: str = "") -> str:
    value = os.getenv(name, default)
    return value.strip()
```

**Walkthrough**
- `load_dotenv()` runs when the module is imported.
- `required_setting` is used for values without which a provider cannot be initialized.
- The error message contains the setting name but not its secret value.
- `optional_setting` allows a safe non-secret default.
- Avoid reading every setting at import time if that makes unit testing difficult; a settings object or explicit loader can be better as the application grows.

### Provider adapter contract
Define a small protocol or base class only when it makes the design clearer. For a beginner exercise, a documented function contract is enough:
```python
def generate(request: LLMRequest) -> LLMResult:
    """Send one validated request and return normalized text."""
    raise NotImplementedError
```

- The function accepts one internal request object.
- The function returns one internal result object.
- Provider-specific SDK objects should not leak into the rest of the application.
- The contract must define how failures are reported.
- The first implementation can support one provider; add the second after the first is tested.

## Making a real provider call safely

SDK APIs and model names evolve. Use the current official provider quickstart to confirm the exact call syntax for the installed SDK version. The following patterns are intentionally marked as version-sensitive teaching examples: adapt only the SDK call block to the current official reference, while preserving validation, configuration, normalization and tests.

### OpenAI SDK call pattern
```python
from openai import OpenAI

client = OpenAI()  # reads the supported environment configuration
response = client.responses.create(
    model="YOUR_CURRENT_SUPPORTED_MODEL",
    input="Explain what an API is in two beginner-friendly sentences.",
)
print(response.output_text)
```

- `OpenAI()` creates an SDK client; the SDK reads the configured credential according to its documented convention.
- `responses.create` sends an input to the Responses API in SDK versions that support this interface.
- Replace the placeholder with a model currently available to your account and supported by this endpoint.
- `input` contains the task text in this minimal example.
- `output_text` is a convenience accessor in SDK versions that expose it; inspect the installed SDK documentation.
- Do not assume this minimal call covers streaming, structured outputs or every model capability.

### Gemini SDK call pattern
```python
from google import genai

client = genai.Client()  # reads the supported environment configuration
response = client.models.generate_content(
    model="YOUR_CURRENT_SUPPORTED_MODEL",
    contents="Explain what an API is in two beginner-friendly sentences.",
)
print(response.text)
```

- `from google import genai` imports the client library namespace used by the current unified SDK.
- `genai.Client()` creates a client using the supported credential configuration.
- `models.generate_content` sends content to the selected model in SDK versions that expose this method.
- `contents` contains the prompt for this simple example.
- `response.text` is a convenient text accessor when the response contains text.
- Some responses may have no text or may include other parts; inspect the response schema and handle those cases.

### Do not combine provider-specific examples
- OpenAI's request and response types are not Gemini request and response types.
- Do not pass an OpenAI response object into Gemini parsing code.
- Do not assume that a parameter name or role format is portable.
- Keep a separate adapter for each provider.
- Normalize only the fields your application needs.
- Add explicit tests for each adapter.

## Suggested implementation for the project

### Milestone 1 — offline skeleton
- Create the folder structure.
- Create `.gitignore` and `.env.example`.
- Create `LLMRequest` and `LLMResult`.
- Implement `validate_prompt`.
- Write tests for empty input, non-text input and oversized input.
- Do not configure a provider key yet.

### Milestone 2 — one provider
- Choose one provider for the first working integration.
- Read its current official Python quickstart.
- Install its SDK in the active virtual environment.
- Create one adapter function.
- Make one harmless smoke-test call.
- Normalize the result into `LLMResult`.
- Handle missing key and provider exceptions without exposing credentials.

### Milestone 3 — second provider
- Add the second SDK only after the first adapter works.
- Implement the same internal contract.
- Keep each provider's model name in configuration.
- Compare outputs using the same input set.
- Record latency and usage when available.
- Do not claim one provider is universally better based on one prompt.

### Milestone 4 — CLI
- Read a prompt from the terminal.
- Validate it before making a network request.
- Ask the user to choose a configured provider.
- Call the application service.
- Print generated text.
- Print provider, model and available usage metadata.
- Print a safe error message if the request fails.

### Milestone 5 — documentation and handoff
- Explain setup from a clean computer.
- Document environment variables by name only.
- Explain how to run offline tests.
- Explain how to run the optional live smoke test.
- Include sample output clearly labelled as illustrative.
- Include a cost and privacy warning.

## Common failures and troubleshooting

| Symptom | Likely cause | What to check | Safe next action |
|---|---|---|---|
| `ModuleNotFoundError` | SDK installed into another interpreter | `python -m pip show package` and active Python path | Activate the project's virtual environment and install with its Python |
| Missing-key error | Environment variable absent | Variable spelling, `.env` location, loader order | Add the key locally; never paste it into source code |
| Authentication failure | Key invalid, revoked or wrong account | Provider console and environment variable source | Revoke exposed key and create a replacement |
| Permission or model access error | Model unavailable to account or endpoint | Current model catalogue and account access | Select an accessible supported model |
| Bad request | Unsupported parameter or malformed input | Provider error details with secrets redacted | Reduce request to a minimal documented example |
| Rate limit | Request volume or token throughput exceeded | Response status and provider limit metadata | Back off, queue work and bound retries |
| Timeout | Network or model response took too long | Timeout configuration and measured latency | Return a safe timeout result; do not retry forever |
| Empty output | Blocked, incomplete or unexpected response | Finish metadata and response content blocks | Handle empty output as a distinct outcome |
| Unexpected attribute error | SDK response shape differs from tutorial | Installed SDK version and object schema | Inspect the documented response type and update adapter tests |
| Unexpected bill | Large prompt, output or repeated calls | Usage metadata and request count | Add output limits, budgets and usage tracking |

### Debugging sequence
1. Confirm the terminal is inside the project folder.
2. Confirm the virtual environment is active.
3. Confirm the Python interpreter and pip belong to that environment.
4. Confirm the SDK package is installed.
5. Confirm configuration loading happens before the key is read.
6. Confirm the key exists without printing its value.
7. Confirm the model identifier is currently supported for the endpoint.
8. Reduce the request to one short prompt and one supported parameter.
9. Inspect the provider's status code and safe error category.
10. Test the same application service with a fake provider to separate code defects from network defects.

## Exercises with solutions

### Exercise 1 — explain the request path
**Task:** Write the eight steps from terminal input to displayed response.

**Solution:**
1. CLI reads input.
2. Validation checks type, whitespace and length.
3. Service builds an internal request.
4. Configuration selects a provider and model.
5. Adapter calls the official SDK.
6. Provider processes the request and returns a response.
7. Adapter extracts text and available metadata into an internal result.
8. CLI displays the result and handles failures safely.

### Exercise 2 — detect missing configuration
**Task:** What should happen if `OPENAI_API_KEY` is missing?

**Solution:**
- Configuration validation should fail before the first paid request.
- The error should name the missing setting but never print a key value.
- The user should receive a short setup instruction.
- The application should not silently use a hardcoded credential.

### Exercise 3 — choose a testing boundary
**Task:** You need to test that a blank prompt is rejected. Should the test call a real LLM?

**Solution:**
- No. Prompt validation is deterministic local Python logic.
- Pass an empty string to `validate_prompt`.
- Assert that it raises `ValueError`.
- This test should run offline and cost nothing.

### Exercise 4 — provider comparison
**Task:** Design a fair comparison between two providers.

**Solution:**
- Prepare a fixed set of representative tasks.
- Use equivalent instructions and comparable output limits.
- Run each task under documented model identifiers.
- Record correctness against a rubric, latency and usage.
- Repeat where variability matters.
- Report the date and account/model availability constraints.

### Exercise 5 — secret exposure
**Task:** A student committed `.env` containing a real key, then deleted the file in a later commit. Is the key safe?

**Solution:**
- No. Git history may still contain the secret.
- Revoke the exposed key immediately.
- Remove the secret from repository history using an approved process if required.
- Create a new key and store it outside source control.
- Review logs and access for possible misuse.

## Guided practical checklist

- [ ] Create a dedicated project directory.
- [ ] Create and activate `.venv`.
- [ ] Verify the interpreter and pip.
- [ ] Install only the required packages.
- [ ] Create `.gitignore`.
- [ ] Create `.env.example` with placeholders.
- [ ] Create a local `.env` without committing it.
- [ ] Implement prompt validation.
- [ ] Implement configuration validation.
- [ ] Define internal request and result structures.
- [ ] Implement one provider adapter.
- [ ] Run an optional real API smoke test.
- [ ] Normalize the provider response.
- [ ] Handle missing, empty and failed responses.
- [ ] Add a fake provider for tests.
- [ ] Add unit tests that run offline.
- [ ] Add a second provider adapter if account access permits.
- [ ] Compare providers with a repeatable evaluation set.
- [ ] Document setup, cost, privacy and troubleshooting.
- [ ] Confirm no secret appears in Git status or committed files.

## Daily assessment — five MCQs

**1. What is the safest place for a server-side API key?**
- A. In browser JavaScript
- B. In a public GitHub repository
- C. In server-side environment configuration or a secret manager
- D. Inside a prompt
**Answer: C.** A key must remain in a trusted server-side environment and be restricted to the process that needs it.

**2. Why create a provider adapter?**
- A. To make model output always correct
- B. To isolate provider-specific request and response handling
- C. To remove the need for tests
- D. To bypass authentication
**Answer: B.** The adapter provides a stable internal boundary while SDK details remain provider-specific.

**3. Which test should run without a live API?**
- A. Validate that an empty prompt is rejected
- B. Measure a provider's current uptime
- C. Verify today's live model availability
- D. Confirm a real invoice amount
**Answer: A.** Input validation is local deterministic logic and should be tested offline.

**4. What does a timeout mean?**
- A. The provider definitely did not process the request
- B. The application stopped waiting within its configured time
- C. The API key is always invalid
- D. The model has been deleted
**Answer: B.** The provider may still have processed the request; blind retries can duplicate work or cost.

**5. How should two providers be compared?**
- A. One random prompt each
- B. By logo and popularity
- C. Using the same task set, rubric and recorded conditions
- D. By selecting whichever gives the longest answer
**Answer: C.** A repeatable evaluation is more informative than a single anecdotal output.

## Interview preparation

**Q1. What happens when a Python application calls an LLM API?**

**Answer:** The application validates its input, constructs a provider-specific request, authenticates through a protected credential, sends the request over HTTPS, waits for the provider response, checks the response status and content, and converts the result into an application-friendly form. The application must also handle timeouts, rate limits, invalid credentials and empty or blocked outputs.

**Follow-up:** Why should the API call not be placed directly in every route or UI component?

**Answer:** Duplicated calls create inconsistent error handling and make testing difficult. A service and provider adapter centralize behavior and can be reused by a CLI, FastAPI route or frontend.

**Q2. What is the difference between an SDK and an API?**

**Answer:** The API is the remote contract exposed by the provider. The SDK is a client library that helps application code call that API by handling common details such as authentication, serialization and response parsing. The SDK does not eliminate the need to understand HTTP, errors and provider-specific behavior.

**Follow-up:** When might raw HTTP be useful?

**Answer:** When an SDK does not expose a required feature, when debugging a protocol issue or when working in an environment where the SDK cannot be used. It also means the developer must implement request and response handling carefully.

**Q3. How do you protect API keys?**

**Answer:** Keep keys out of source code, Git, browser bundles, screenshots and logs. Use environment configuration for local development and a secret manager or deployment platform secret store in production. Restrict access, rotate exposed keys and monitor usage.

**Follow-up:** Is `.gitignore` enough?

**Answer:** No. It helps prevent accidental additions but does not remove a secret already committed or protect a compromised machine.

**Q4. Why normalize provider responses?**

**Answer:** Providers may return different response objects, metadata and error types. Normalization gives the rest of the application a stable result model, which reduces provider coupling and makes tests and future migrations easier.

**Q5. How do you test an LLM integration without spending money?**

**Answer:** Separate deterministic application logic from the network boundary. Inject a fake provider that returns fixed responses or raises controlled exceptions. Test validation, request construction, response normalization and error mapping offline. Keep a small optional smoke test for the real provider.

## Project specification — Python LLM API Integration Application

### Business scenario
A small internal learning team wants a command-line tool that sends a question to a selected LLM provider and displays the answer. The team wants to compare providers without rewriting the user interface or exposing credentials.

### Required features
1. Read provider and model configuration from environment settings.
2. Support at least one provider for the first milestone.
3. Provide a second provider adapter as an extension when credentials are available.
4. Validate user input before making a request.
5. Keep provider-specific SDK code in adapter functions or modules.
6. Normalize results into one internal result structure.
7. Display provider, model, response text and available usage information.
8. Handle missing credentials, invalid input, provider errors, timeouts and empty output.
9. Include offline automated tests using a fake provider.
10. Include a README with setup, execution, cost, privacy and troubleshooting instructions.

### Acceptance criteria
- A beginner can create the environment using only the README.
- The application does not start a provider request for blank input.
- No real credential exists in tracked files.
- The provider can be replaced in tests without a network call.
- The response is displayed without depending on a provider-specific object outside the adapter.
- Errors are understandable and do not expose keys.
- The tests pass without provider credentials.
- The README distinguishes a mocked test from a live smoke test.

### Suggested test cases
| Test | Input or setup | Expected behavior |
|---|---|---|
| Empty prompt | `"   "` | Reject before API call |
| Non-string prompt | `None` | Raise input type error |
| Prompt within limit | Short sentence | Accept |
| Prompt too long | More than configured limit | Reject with clear message |
| Missing API key | No key configured | Fail during configuration validation |
| Valid fake response | Fake adapter returns text | Display normalized text |
| Empty fake response | Adapter returns empty content | Report empty response safely |
| Authentication failure | Fake adapter raises auth error | Show safe credential guidance |
| Rate limit | Fake adapter raises rate-limit error | Show throttling guidance; no tight loop |
| Timeout | Fake adapter raises timeout | Return bounded timeout error |
| Provider switch | Select second fake adapter | Correct adapter is called |
| Secret redaction | Inject a fake secret into config | Captured logs do not contain secret |

### Suggested repository submission
```text
day16_llm_api/
├── .gitignore
├── .env.example
├── requirements.txt
├── README.md
├── main.py
├── llm_app/
│   ├── __init__.py
│   ├── config.py
│   ├── models.py
│   ├── providers.py
│   └── service.py
└── tests/
    ├── test_validation.py
    ├── test_service.py
    └── test_provider_errors.py
```

### Student evidence
- Screenshot of the folder structure with no secrets visible.
- Terminal output showing the offline test suite passing.
- Sanitized sample output from one live smoke test, if the student has provider access.
- A short explanation of the adapter boundary.
- A comparison table if both providers were tested.

## Revision sheet

- API: contract for software-to-software communication.
- SDK: client library that wraps common API operations.
- API key: secret bearer credential; protect it.
- Model: provider-hosted inference target identified by a model name.
- Environment variable: process configuration supplied outside source code.
- Adapter: provider-specific implementation behind an internal contract.
- Service: application use case that coordinates validation and provider calls.
- Normalization: conversion into a stable internal result structure.
- Timeout: maximum wait configured by the client; not proof the provider did no work.
- Rate limit: provider usage constraint requiring bounded backoff or queueing.
- Mock: deterministic replacement used to test code without a real external service.
- Usage metadata: provider-reported token or metering details, when available.

## Completion gate

Do not mark Day 16 complete merely because one prompt returned an answer.

To pass this day, demonstrate all of the following:
- You can explain the complete request lifecycle without reading the code.
- You can configure a provider key without committing or printing it.
- You can identify the active Python environment and installed SDK.
- You can validate input before the network call.
- You can explain where provider-specific code lives.
- You can handle at least three distinct failure categories.
- You can run tests without a live API key.
- You can explain the cost and privacy implications of sending data to an external model.
- You can reproduce setup from the README on a clean environment.
- You can describe one limitation of your implementation and a sensible next improvement.

**Day 16 is complete when the application is understandable, reproducible, tested and safe—not merely when the model answers once.**
