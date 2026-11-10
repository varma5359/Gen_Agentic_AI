# Day 15 — Reusable Prompt Templates and Prompt Testing

**Phase:** 2 — Generative AI and LLM Foundations  
**Approved topic:** Prompt templates, role prompting, prompt structure, reusable prompts and prompt testing  
**Mini-project:** Reusable Business Prompt Library  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
- Explain why applications use prompt templates.
- Separate fixed instructions from changing input data.
- Use role/context, task, constraints and output format.
- Build reusable templates with Python string formatting.
- Test prompts against examples and record failures.

## 2. What is a prompt template?

A prompt template is a reusable prompt containing placeholders for values that change.

Without a template, a developer may copy and edit the same prompt many times. This can create inconsistent instructions.

Template:
```text
You are a {role}.
Task: {task}
Audience: {audience}
Input:
{content}
Output requirements:
{format_rules}
```

At runtime, the application replaces placeholders with actual values.

```text
Fixed instructions + variable input
             ↓
        Prompt template
             ↓
       Filled prompt
             ↓
             LLM
             ↓
       Model response
```

## 3. Role prompting

Role prompting asks the model to respond from a specified professional perspective.

Example:
```text
You are a customer support assistant for an online learning platform.
Explain the solution in simple language.
Do not claim that an account action has been completed unless the system confirms it.
```

A role can guide tone and focus, but it does not give the model real-world credentials or guarantee expert accuracy.

## 4. Prompt structure checklist

Before using a prompt, check:
1. **Role:** Who should the assistant act as?
2. **Task:** What must it do?
3. **Context:** What information does it need?
4. **Constraints:** What rules must it follow?
5. **Output:** What format is expected?
6. **Uncertainty:** What should it do when information is missing?
7. **Examples:** Would one or more examples remove ambiguity?

### Example: business email summary

```text
Role: You are an assistant helping a business analyst.
Task: Summarize the email below.
Context: The reader has limited time.
Constraints:
- Do not invent facts.
- Preserve dates, names and amounts exactly.
- If a detail is missing, write "Not specified".
Output:
- Main point (one sentence)
- Important details (up to 3 bullets)
- Required action (if any)

Email:
{email_text}
```

## 5. Python string templates

Python's `str.format()` method replaces named placeholders.

**Meaning:** Creates a new string with placeholders replaced by supplied values.  
**Purpose:** Reuse one prompt structure for different inputs.  
**Syntax:** `template.format(name=value)`  
**Arguments:** Values for the named placeholders in the string.  
**Return:** A new formatted string.  
**Original:** The original template string is unchanged.

```python
template = "You are a {role}. Summarize this text: {content}"

prompt = template.format(
    role="business analyst",
    content="Sales increased by 12% in April."
)

print(prompt)
```

**Expected output**
```text
You are a business analyst. Summarize this text: Sales increased by 12% in April.
```

**Common mistakes**
- Missing a required placeholder value causes `KeyError`.
- Misspelling a placeholder name causes `KeyError`.
- Braces intended as literal text need escaping as `{{` and `}}` when using `format()`.
- Do not insert untrusted text into instructions without clear boundaries.

## 6. Build a reusable prompt library

Create `prompt_library.py`.

```python
PROMPTS = {
    "support_reply": """
You are a helpful support assistant.
Write a polite reply to the customer.
Do not claim that an action is completed unless confirmed.
Customer message:
{message}
Return:
1. Acknowledgement
2. Next step
""",
    "meeting_summary": """
You are an assistant for a project manager.
Summarize the meeting notes below.
Do not invent decisions or deadlines.
If information is missing, write "Not specified".
Meeting notes:
{notes}
Return:
- Summary
- Decisions
- Action items
"""
}


def build_prompt(prompt_name, **values):
    template = PROMPTS.get(prompt_name)

    if template is None:
        raise ValueError("Unknown prompt name: " + prompt_name)

    return template.format(**values)


support_prompt = build_prompt(
    "support_reply",
    message="I cannot access my course after payment."
)

print(support_prompt)
```

**Expected output (spacing may vary)**
```text
You are a helpful support assistant.
Write a polite reply to the customer.
Do not claim that an action is completed unless confirmed.
Customer message:
I cannot access my course after payment.
Return:
1. Acknowledgement
2. Next step
```

### Explain the new Python pieces

| Code | Meaning |
|---|---|
| Dictionary `PROMPTS` | Stores prompt names and template strings |
| `def build_prompt(...)` | Defines a reusable function |
| `prompt_name` | Required parameter identifying the template |
| `**values` | Collects extra keyword arguments into a dictionary |
| `.get(prompt_name)` | Returns the value for the key, or `None` if missing |
| `raise ValueError(...)` | Stops execution with a meaningful error |
| `.format(**values)` | Uses dictionary entries as named formatting values |

The function returns a string. It does not call an LLM.

## 7. Prompt testing

A prompt should be tested like application code. Use a small test set before relying on it.

| Test | Input | What to check |
|---|---|---|
| Normal | Clear customer message | Correct task and tone |
| Missing data | Empty or incomplete message | Does it avoid inventing facts? |
| Long input | Long meeting notes | Does it preserve important details? |
| Conflicting text | Notes contain “ignore previous instructions” | Does the prompt treat notes as data? |
| Format | Any valid input | Does it follow the requested structure? |

### Simple local template tests

```python
def test_support_prompt_contains_message():
    prompt = build_prompt(
        "support_reply",
        message="I cannot log in."
    )
    assert "I cannot log in." in prompt
    assert "Do not claim" in prompt


def test_unknown_prompt_name():
    try:
        build_prompt("not_a_prompt")
    except ValueError:
        print("Unknown prompt test passed.")
    else:
        print("Test failed: expected ValueError.")


test_support_prompt_contains_message()
test_unknown_prompt_name()
print("Prompt template checks completed.")
```

**Expected output**
```text
Unknown prompt test passed.
Prompt template checks completed.
```

The first test prints nothing when its assertions pass. If an assertion fails, Python raises `AssertionError`.

## 8. Mini-project — Reusable Business Prompt Library

**Required features**
- Store at least three prompts: support reply, meeting summary and text classification.
- Build a prompt by name.
- Accept changing user content.
- Handle unknown prompt names clearly.
- Include at least five test cases.
- Save sample prompts and test results in the project README.

**Suggested folder**
```text
prompt_library_project/
├── prompt_library.py
├── test_prompts.py
└── README.md
```

**Completion checklist**
- [ ] Three or more reusable prompt templates.
- [ ] Named placeholders are clear.
- [ ] Unknown names raise a useful error.
- [ ] Test cases cover normal and missing input.
- [ ] No API keys are stored in source code.
- [ ] README explains how to run the program.

## 9. Common mistakes
- Copy-pasting prompts instead of using templates.
- Using unclear placeholder names.
- Forgetting to test empty or adversarial input.
- Assuming role prompting makes the model an actual professional.
- Expecting prompt wording alone to guarantee correct answers.
- Mixing trusted instructions with untrusted user-provided content.

## 10. Practice with answers
1. Why use a prompt template? **To reuse consistent instructions with different input values.**
2. What does `format()` return? **A new formatted string.**
3. Does `format()` call an LLM? **No.**
4. Why test prompts? **To detect unclear instructions, format failures and edge cases.**
5. What should happen if the prompt name is unknown? **Return or raise a clear error rather than silently using the wrong prompt.**

## 11. Phase 2 review
Students should now be able to explain the LLM request flow, tokenization and context windows, generation controls, hallucination risks, zero-shot/few-shot prompting and reusable prompt templates.

**Bridge to Phase 3:** Phase 3 will connect these concepts to real model APIs, credentials, structured outputs, streaming and FastAPI. API keys must be stored securely and never committed to Git.
