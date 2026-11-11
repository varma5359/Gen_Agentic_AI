# Day 15 — Prompt templates, role prompting, prompt structure, reusable prompts and prompt testing

**Phase 2 | Beginner | 2–3 hours | Project: Reusable Business Prompt Library**

## Learning outcomes
Explain reusable prompt templates; design a consistent prompt structure; use role prompting appropriately; create parameterised templates; version prompts; build test cases; and compare prompt versions.

## 1. Why reusable prompts?
A one-off prompt may work once but produce inconsistent results across an application. A reusable template keeps the instruction structure stable and inserts changing data through named variables.

Example: a business needs product summaries with a short overview, benefits and neutral tone. One template can be reused for every product.

## 2. A practical prompt structure
1. Role/perspective (optional).
2. Task.
3. Context and audience.
4. Input data.
5. Rules and constraints.
6. Output format.
7. Uncertainty/fallback instruction.

~~~text
ROLE:
You are a business writing assistant.

TASK:
Summarise the supplied product information.

AUDIENCE:
A first-time customer.

RULES:
Use only supplied facts. Do not invent specifications.
Use plain language and neutral tone.

OUTPUT:
Summary:
Key benefits:
Information not provided:

INPUT:
{product_information}
~~~

Each section has a purpose. Avoid unnecessary role statements. “You are the world's best expert” does not create expertise or guarantee accuracy.

## 3. Role prompting
Role prompting asks the model to adopt a perspective, such as “technical documentation editor”. It can guide tone, vocabulary and focus. It does not grant credentials, authority or access to private data.

Weak: “You are the world's best expert. Give a perfect answer.”
Better: “Review this beginner Python explanation for correctness. Identify inaccurate claims, explain why, and suggest a clearer version. Use only the supplied text and flag missing evidence.”

The second prompt describes an observable task.

## 4. Parameterised prompt templates
~~~python
def build_product_prompt(product_name, product_details, audience):
    template = """
Task: Write a product summary.
Audience: {audience}
Rules:
- Use only supplied details.
- Do not invent specifications.
- If a detail is missing, say it was not provided.
Product: {product_name}
Details:
{product_details}
"""
    return template.format(
        audience=audience,
        product_name=product_name,
        product_details=product_details
    ).strip()

prompt = build_product_prompt(
    "Wireless Keyboard",
    "Compact layout; USB-C charging; black finish.",
    "first-time buyers"
)
print(prompt)
~~~
The function separates fixed instructions from changing data. format substitutes named placeholders. In production, validate input and treat user-provided text as untrusted. Delimiters improve readability but are not a complete prompt-injection defence.

## 5. Store prompts as data
A small project can store prompt strings in Python or text files. A larger prompt library should record:
- prompt ID and version;
- purpose and owner;
- model compatibility notes;
- required variables;
- expected output format;
- test dataset and results;
- date and change reason.

Never put API secrets in prompt files.

## 6. Prompt testing
Do not evaluate a prompt by trying it once and liking the answer. Build tests for:
- normal input;
- missing input;
- long input;
- conflicting facts;
- unsupported request;
- malicious instructions embedded in data;
- output-format violations.

Evaluate correctness against supplied facts, instruction following, completeness, format validity, consistency and safety. Use human review where quality is subjective.

## 7. Versioning and iteration
~~~text
Prompt v1
   |
Run fixed test set
   |
Record failures
   |
Change one meaningful instruction
   |
Prompt v2
   |
Run the same test set
   |
Compare and document results
~~~
Keep old versions for rollback. If prompt and test set change together, it becomes difficult to identify the cause of a result change.

## 8. Templates are not security boundaries
A variable such as customer_message may contain “ignore previous instructions”. Treat inserted content as untrusted. Restrict tools and permissions, validate outputs and avoid exposing secrets. Delimiters may help the model interpret sections but do not guarantee isolation.

## 9. Industry scenario
A marketing team creates hundreds of product summaries. A prompt library standardises sections and tone. A fixed test set checks that the model does not invent features. A reviewer approves content before publication.

## 10. Common mistakes
| Mistake | Better approach |
|---|---|
| Long role, unclear task | State observable task |
| Hardcode every prompt | Use named variables |
| Allow invented product details | Ground output in supplied facts |
| Change prompt and tests together | Keep tests fixed during comparison |
| No prompt version | Record ID, version and reason |
| Assume delimiters block injection | Enforce application security |
| Store keys in prompt files | Use secure secret configuration |

## 11. Practice
1. Turn a one-off email prompt into a template.
2. Add role, task, context, rules and output sections.
3. Add audience and source-text placeholders.
4. Create six tests including missing and conflicting facts.
5. Compare two versions on the same tests.
6. Explain role prompting limitations.
7. Explain how untrusted input can try to alter instructions.

## 12. Quiz
1. Templates improve: A consistency/reuse B model training C password storage D testing removal. **A.**
2. Role prompting guarantees expertise: A true B false. **B.**
3. Version record should include: A purpose/change B API secret C password D nothing. **A.**
4. Best evaluation: A one favourite output B fixed test set and rubric C prompt length D role title. **B.**
5. Delimiters fully prevent injection: A yes B no. **B.**

## 13. Interview questions
- What is a prompt template and why use one?
- What sections make a prompt clear?
- What can role prompting do and not do?
- How do you test before production?
- How do you version prompts and compare changes?
- Why are placeholders not a security boundary?

**Phase 2 outcome:** You understand LLM fundamentals, tokens, generation controls and prompt engineering. Phase 3 will connect real provider APIs and build LLM-powered applications.
