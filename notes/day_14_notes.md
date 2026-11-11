# Day 14 — Prompt engineering: system prompts, user prompts, zero-shot and few-shot prompting

**Phase 2 | Beginner | 2–3 hours | Project: Business Text Classification Prompt Application**

## Learning outcomes
Explain prompt engineering; distinguish system and user messages; design clear task instructions; create zero-shot and few-shot prompts; define labels and edge cases; and evaluate outputs against a labelled test set.

## 1. What is a prompt?
A prompt is the input supplied to a model. It may include instructions, context, examples and a user request. Prompt engineering structures that input to make the task clear. It reduces ambiguity but does not guarantee correctness.

## 2. Message roles
- System message: commonly contains high-level application behaviour and constraints.
- User message: contains the end user's current request or data.
- Assistant message: the model's response.
- Some APIs also use developer and tool messages. Exact roles and precedence depend on the provider/API; check its current documentation.

Example:
~~~text
SYSTEM:
You classify support tickets.
Choose exactly one label: Billing, Technical, Account, Other.
Return the label only.

USER:
I was charged twice for my subscription.
~~~
Expected label: Billing.

The system message defines the task and constraints. The user message provides the ticket.

## 3. Zero-shot prompting
Zero-shot asks the model to perform a task without task examples.

~~~text
Classify this message as Billing, Technical, Account or Other.
Return one label only.

Message: I cannot reset my password.
~~~
Expected label: Account.

Zero-shot can work when the task and labels are clear. It may struggle with company-specific rules and overlapping categories.

## 4. Few-shot prompting
Few-shot includes examples demonstrating the desired mapping.

~~~text
Classify each message as Billing, Technical, Account or Other.
Return one label only.

Example:
Message: My invoice includes an unexpected fee.
Label: Billing

Example:
Message: The application crashes when I upload a file.
Label: Technical

Example:
Message: I cannot sign in after changing my password.
Label: Account

Now classify:
Message: I was charged twice this month.
Label:
~~~
Expected label: Billing.

Examples should be representative, correct and consistent. Conflicting examples can teach the wrong pattern.

## 5. Build a clear prompt
A useful prompt includes:
1. Task: what should be done?
2. Context: what business situation matters?
3. Input: what content is being processed?
4. Rules: allowed labels and decision boundaries.
5. Output format: what exactly should be returned?
6. Fallback: what to do when no label fits.

Example:
~~~text
Task: Classify a support ticket.
Allowed labels: Billing, Technical, Account, Other.
Rule: Choose one best label. Do not invent a label.
If none fits, choose Other.
Output: label only.

Ticket:
{ticket_text}
~~~

## 6. Ambiguity matters
“I cannot access my invoice” could be Billing (invoice content) or Account (access problem). Define a business rule: if the problem is sign-in or permission, choose Account; if the amount or charge is wrong, choose Billing. The taxonomy must be agreed with the business.

## 7. Prompt testing
Create labelled tests:
- clear examples;
- overlapping categories;
- empty/short messages;
- multiple issues;
- out-of-scope requests.

Compare actual output with expected labels. One successful example does not prove reliability.

## 8. Python: build a prompt template (no model call)
~~~python
def build_classification_prompt(ticket_text):
    prompt = """
Task: Classify the support ticket.
Allowed labels: Billing, Technical, Account, Other.
Return one label only.

Ticket:
""" + ticket_text
    return prompt.strip()

ticket = "I was charged twice."
print(build_classification_prompt(ticket))
~~~
The function receives a message, inserts it into a fixed instruction and returns text. It does not call an LLM. Day 16 introduces provider API integration.

## 9. Industry scenario
A business routes thousands of support tickets. The classifier needs a business-approved label taxonomy, edge-case tests, output validation and a human correction path. Incorrect routing can delay support.

## 10. Common mistakes
| Mistake | Better approach |
|---|---|
| “Classify this” only | Define labels and boundaries |
| No output format | Specify exactly what to return |
| Contradictory examples | Review and balance examples |
| No edge-case rule | Define fallback |
| Judge from one sample | Use labelled tests |
| Assume prompt enforces permissions | Enforce access in backend code |
| Send unnecessary personal data | Minimise and protect data |

## 11. Practice
1. Write a zero-shot sentiment prompt.
2. Convert it to few-shot with three examples.
3. Define four ticket labels and boundaries.
4. Create five ambiguous tests and expected labels.
5. Build a Python prompt template.
6. Explain why prompts cannot replace access control.

## 12. Quiz
1. Zero-shot means: A no task examples B no input C no model D no output. **A.**
2. Few-shot includes: A labelled examples B backup C no instructions D compiler. **A.**
3. System message commonly gives: A application instructions B invoice only C SQL rows D cookies. **A.**
4. Classification prompt should define: A labels and output B “do it” only C no task D hidden rules. **A.**
5. Does a prompt enforce real permissions? A yes B no. **B:** application code must enforce access.

## 13. Interview questions
- Define prompt engineering.
- System versus user message?
- Zero-shot versus few-shot?
- How do you define and test ambiguous labels?
- Why are validation and security still required?

**Completion check:** Design a classification prompt and labelled test set. Next: reusable prompt templates and regression tests.
