# Day 14 — Prompt Engineering Fundamentals

**Phase:** 2 — Generative AI and LLM Foundations  
**Approved topic:** Prompt engineering: system prompts, user prompts, zero-shot and few-shot prompting  
**Mini-project:** Business Text Classification Prompt Application  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
- Define a prompt and explain why its structure matters.
- Distinguish system-level instructions from a user request.
- Write a clear zero-shot prompt.
- Use examples in a few-shot prompt.
- Compare prompt outputs against a simple expected result.

## 2. What is a prompt?

A prompt is the input given to a model. It can contain instructions, a question, examples, reference text, formatting requirements and other context.

Weak prompt:
```text
Classify this.
```

Improved prompt:
```text
Classify the customer message as exactly one of:
Billing, Technical, Account, or Other.

Message: "I was charged twice for my subscription."

Return only the category.
```

The improved version defines:
- The task.
- The permitted labels.
- The input to classify.
- The required output format.

## 3. System prompt and user prompt

In chat-based model APIs, messages can have roles.

| Role | Typical purpose |
|---|---|
| System | High-level behaviour and constraints for the assistant |
| Developer | Application-level instructions set by the application builder, where supported |
| User | The request or information supplied by the end user |
| Assistant | Model response |
| Tool | Result returned by a tool |

Some APIs use different role names or message formats. Do not assume every provider exposes identical roles.

**Example**
```text
SYSTEM:
You are a support-ticket classifier.
Choose exactly one label: Billing, Technical, Account, Other.
Do not add explanations.

USER:
Message: "I cannot reset my password."
```

Expected classification: `Account`

A role label is not a security boundary by itself. Applications must still validate inputs and outputs.

## 4. Zero-shot prompting

**Meaning:** Ask the model to perform a task without providing task examples.

```text
Classify the message into Billing, Technical, Account or Other.
Return only the label.

Message: "My invoice includes an extra charge."
```

Expected label: Billing

Use zero-shot when:
- The task is clear.
- Labels or output rules can be explained directly.
- A quick baseline is useful.

Possible weakness: the model may interpret ambiguous labels differently from your team.

## 5. Few-shot prompting

**Meaning:** Include a small number of input/output examples so the model can follow the demonstrated pattern.

```text
Classify each message as Billing, Technical, Account or Other.
Return only one label.

Examples:
Message: "I was charged twice." → Billing
Message: "The app crashes when I open it." → Technical
Message: "I cannot sign in." → Account

Now classify:
Message: "My payment receipt is missing."
```

Expected label: Billing

Examples should be:
- Correct and representative.
- Consistent in format.
- Relevant to the real cases.
- Balanced enough not to suggest an unintended bias.

Few-shot examples guide the model; they do not retrain the model's weights.

## 6. A repeatable prompt structure

Use this checklist when writing a prompt:

| Part | Question |
|---|---|
| Role/context | What job should the assistant perform? |
| Task | What exact action is required? |
| Input | What text or data should it process? |
| Constraints | What must it do or avoid? |
| Output format | What should the response look like? |
| Examples | Would examples clarify the expected pattern? |

## 7. Mini-project — Business Text Classification Prompt Application

**Goal:** Classify simple support messages using a transparent Python baseline first, then design prompts to perform the same task with an LLM later.

This first version does not call an LLM. It teaches the input/output contract and gives students test cases without API cost.

```python
def classify_message(message):
    text = message.lower()

    if "charged" in text or "invoice" in text or "payment" in text:
        return "Billing"
    elif "crash" in text or "error" in text or "not loading" in text:
        return "Technical"
    elif "password" in text or "sign in" in text or "login" in text:
        return "Account"
    else:
        return "Other"


messages = [
    "I was charged twice.",
    "The app is not loading.",
    "I forgot my password.",
    "I want to know your office address."
]

for message in messages:
    print(message, "->", classify_message(message))
```

**Expected output**
```text
I was charged twice. -> Billing
The app is not loading. -> Technical
I forgot my password. -> Account
I want to know your office address. -> Other
```

**Code explanation**
- `def`: starts a function definition.
- `message`: function parameter; receives the text to classify.
- `lower()`: returns a lowercase copy so matching is case-insensitive.
- `if / elif / else`: selects the first matching rule.
- `return`: sends the category back to the caller.
- `for`: processes each message in the list.

This rule-based classifier is deliberately simple. It can fail on synonyms, negation and ambiguous messages. An LLM may generalize better, but it can also make mistakes and must be evaluated.

### Prompt version for the same task
```text
SYSTEM:
You classify customer support messages.
Allowed labels: Billing, Technical, Account, Other.
Choose exactly one label.
If the message does not clearly fit the first three labels, choose Other.
Return only valid JSON in this format:
{"category": "Billing"}

USER:
Classify this message:
"I was charged twice."
```

Expected shape:
```json
{"category": "Billing"}
```

The example shows the requested format, not a guarantee that every model will return valid JSON. In production, parse and validate the response.

## 8. Test cases and evaluation

| Message | Expected label |
|---|---|
| “My card was charged twice.” | Billing |
| “The application freezes.” | Technical |
| “I cannot reset my password.” | Account |
| “Where is your office?” | Other |

Measure:
- Correct predictions.
- Incorrect predictions.
- Cases where the message is ambiguous.
- Whether output follows the requested format.

Do not test only easy examples. Add realistic edge cases such as “I was not charged” and “I cannot log in after payment”.

## 9. Common mistakes
- Writing “be good” instead of a specific task.
- Forgetting to list permitted categories.
- Mixing instructions and input without clear boundaries.
- Giving examples that contradict one another.
- Assuming few-shot examples guarantee correctness.
- Trusting model output without validation.

## 10. Practice with answers
1. What is a prompt? **The input and instructions provided to a model.**
2. What is zero-shot? **Performing a task without supplied examples.**
3. What is few-shot? **Providing a small number of examples in the prompt.**
4. Does a system prompt replace application security? **No.**
5. Why define output labels? **To make the task bounded and results easier to validate.**

## 11. Lesson checkpoint
Students should write one zero-shot and one few-shot classifier prompt and explain the difference. Day 15 turns these prompts into reusable templates and a small testable library.
