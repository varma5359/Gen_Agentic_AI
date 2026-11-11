# Day 14 Interview Guide — Prompt Engineering

## 1. What is prompt engineering?
Designing instructions, context, examples and output constraints supplied to a model to improve task performance. It must be tested; a well-written prompt is not a guarantee.

## 2. What is a system prompt?
An application-supplied instruction message that commonly defines the assistant's role, task and constraints. Exact message roles and precedence depend on the provider/API.

## 3. What is a user prompt?
The end user's task or content for the current interaction. It is distinct from application-level instructions.

## 4. Zero-shot versus few-shot?
Zero-shot asks the model to perform a task without task examples. Few-shot includes labelled examples to demonstrate the expected pattern or format.

## 5. When would you use few-shot?
When label boundaries, output style or business-specific patterns are easier to demonstrate than explain. Examples must be representative and consistent.

## 6. How do you design a classification prompt?
Define task, context, allowed labels, label definitions, decision rules, input, output format and fallback for ambiguous content. Validate output in code.

## 7. Why test ambiguous examples?
Real messages overlap categories. An explicit taxonomy and edge-case tests make routing consistent and reveal unclear business rules.

## 8. Can a system prompt enforce security?
No. It can instruct the model, but access control and permissions must be enforced by backend code. Treat user input and model output as untrusted.

## 9. What is prompt injection?
An attempt to manipulate model behaviour through untrusted content or instructions. Role prompts alone do not prevent it; apply data boundaries, tool permissions and validation.

## 10. Practical interview task
Write a zero-shot and few-shot prompt for four support-ticket labels. Explain an ambiguous ticket decision and how to measure correctness.
