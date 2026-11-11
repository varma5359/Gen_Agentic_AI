# Day 15 Interview Guide — Prompt Templates, Role Prompting and Testing

## 1. What is a prompt template?
A reusable prompt structure with fixed instructions and named placeholders for changing data. It improves consistency and maintainability.

## 2. What makes a good prompt structure?
A clear task, relevant context, input data, constraints, output format and uncertainty behaviour. Include a role only when it adds useful perspective.

## 3. What is role prompting?
Giving the model a perspective or communication role, such as “technical editor”. It can influence style and focus but does not grant credentials or guarantee correctness.

## 4. Why version prompts?
To reproduce behaviour, track changes, compare results and roll back regressions. Record ID, version, purpose, change reason and test outcomes.

## 5. How do you test prompts?
Use a fixed representative dataset containing normal, edge, missing, conflicting and unsupported inputs. Evaluate correctness, completeness, instruction following, format and safety.

## 6. Why keep test data fixed when comparing versions?
It isolates the effect of the prompt change. If prompt and test cases both change, it is difficult to explain why scores changed.

## 7. How do placeholders work?
They insert variable data into a stable template. Validate required values and clearly separate instructions from untrusted user content.

## 8. Do delimiters prevent prompt injection?
No. They may help communicate structure, but are not a security boundary. Enforce tool permissions, access controls, data minimisation and output validation.

## 9. What is a prompt regression?
A change that improves one case but causes earlier working cases to fail. Re-run the full regression test set after edits.

## 10. Practical interview task
Design a versioned meeting-summary prompt. Name its variables, output sections, test cases and evaluation criteria.
