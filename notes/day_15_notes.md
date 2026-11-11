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

# 18. Extended reusable prompt engineering workshop

Use these cases to practise turning one-off instructions into maintained application components. A prompt template is not production-ready merely because it produces one good answer.

## Reusable-prompt case 1 — Product summary

**Scenario:** A shop needs consistent summaries for many products.

**Design response:** Use a template with named product and audience variables; never invent missing specifications.

**Practice task:** Test with two products and one missing specification.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 2 — Customer reply

**Scenario:** Support agents draft replies using different wording each time.

**Design response:** Create a reusable structure for acknowledgement, evidence, next step and sign-off.

**Practice task:** Check that it does not promise an action that has not occurred.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 3 — Lesson explanation

**Scenario:** A learning platform explains the same concept to different learner levels.

**Design response:** Make audience level a validated variable.

**Practice task:** Test beginner and intermediate settings.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 4 — Meeting summary

**Scenario:** A business needs a consistent summary format.

**Design response:** Define decisions, actions, owners and due dates as separate fields.

**Practice task:** Test a meeting note with no due dates.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 5 — Resume extraction

**Scenario:** Recruiters need a structured record from resume text.

**Design response:** Define required fields, types and missing-value behaviour.

**Practice task:** Test a resume that omits a graduation date.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 6 — Invoice extraction

**Scenario:** Finance staff need invoice fields.

**Design response:** Define field names, currency and date formats; validate values in code.

**Practice task:** Test a synthetic invoice with a missing total.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 7 — Email classification

**Scenario:** A mail system classifies incoming messages.

**Design response:** Keep the label set and boundary definitions in the template.

**Practice task:** Test an ambiguous message.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 8 — SQL explanation

**Scenario:** A learning tool explains a SQL query.

**Design response:** Provide the query, database dialect and learner level as inputs.

**Practice task:** Test a query with dialect-specific syntax.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 9 — Code review

**Scenario:** A developer wants a consistent code review.

**Design response:** Specify correctness, security, readability and testability criteria.

**Practice task:** Test a deliberately buggy code sample.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 10 — Bug report

**Scenario:** Support converts an error report into structured fields.

**Design response:** Define summary, steps, expected result, actual result and environment.

**Practice task:** Test an incomplete report.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 11 — Translation template

**Scenario:** A product translates support content.

**Design response:** Define source language, target language, audience and terminology rules.

**Practice task:** Test a phrase with a product name that must not be translated.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 12 — Tone rewriting

**Scenario:** Marketing rewrites content for a specified audience.

**Design response:** Separate facts from tone instructions and preserve factual claims.

**Practice task:** Compare source and rewritten factual statements.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 13 — FAQ generation

**Scenario:** A team creates FAQs from an approved policy.

**Design response:** Require each answer to be supported by supplied text.

**Practice task:** Test a question not answered by the policy.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 14 — Study questions

**Scenario:** An education platform generates quiz questions.

**Design response:** Specify topic, difficulty, number, answer format and source boundaries.

**Practice task:** Check answer correctness against lesson material.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 15 — Prompt variables

**Scenario:** A template accepts arbitrary user strings.

**Design response:** Define variable names, required status, types and validation.

**Practice task:** Test empty and very long values.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 16 — Missing variable

**Scenario:** A required field is not supplied.

**Design response:** Validate required variables before rendering the template.

**Practice task:** Test a missing audience value.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 17 — Unsafe variable content

**Scenario:** A user-provided variable contains instructions to ignore the task.

**Design response:** Treat variable content as untrusted data and use structured message boundaries.

**Practice task:** Test a harmless injected phrase.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 18 — Template escaping

**Scenario:** A variable contains braces or formatting characters.

**Design response:** Use a safe rendering approach and test special characters.

**Practice task:** Test text containing braces and percent signs.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 19 — Version identifier

**Scenario:** The team cannot tell which prompt produced a response.

**Design response:** Assign a stable prompt name and version and store it with evaluation records.

**Practice task:** Compare two versions in a test report.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 20 — Change log

**Scenario:** A prompt changes but no reason is recorded.

**Design response:** Record what changed, why, expected impact and test evidence.

**Practice task:** Write a change entry for a label-definition update.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 21 — Regression test

**Scenario:** A prompt edit breaks an older example.

**Design response:** Rerun the same labelled dataset after every change.

**Practice task:** Add the broken example to regression tests.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 22 — A/B comparison

**Scenario:** Two prompt versions are compared informally.

**Design response:** Use the same inputs, model and settings, and define metrics before testing.

**Practice task:** Build a fair comparison table.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 23 — Prompt ownership

**Scenario:** Nobody knows who maintains a production prompt.

**Design response:** Record owner, purpose, contact and review date.

**Practice task:** Add ownership metadata to a template record.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 24 — Deprecation

**Scenario:** An old prompt is still used by one API route.

**Design response:** Mark it deprecated, identify callers and migrate deliberately.

**Practice task:** Write a migration checklist.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 25 — Provider-specific role

**Scenario:** A template assumes identical role behaviour across APIs.

**Design response:** Keep provider-specific message assembly separate from reusable task content.

**Practice task:** Document one adaptation point.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 26 — Output schema

**Scenario:** A template expects a JSON response.

**Design response:** Define schema and validate the actual response in application code.

**Practice task:** Test invalid JSON and wrong types.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 27 — Structured extraction

**Scenario:** The model returns a date in several formats.

**Design response:** Specify the desired format and parse/validate it after generation.

**Practice task:** Test impossible dates and ambiguous formats.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 28 — Uncertainty field

**Scenario:** The model is forced to fill every field.

**Design response:** Define null or unknown behaviour for missing evidence.

**Practice task:** Test a source with an absent field.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 29 — Source citation

**Scenario:** A summary must cite supplied passages.

**Design response:** Preserve source identifiers and require claims to map to evidence.

**Practice task:** Check every cited ID exists.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 30 — No-source case

**Scenario:** The template asks for citations when none are supplied.

**Design response:** Define a response for missing sources instead of fabricating citations.

**Practice task:** Test an empty source list.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 31 — Prompt injection

**Scenario:** A document includes instructions to reveal system text.

**Design response:** Treat document content as untrusted and preserve the application task boundary.

**Practice task:** Run a harmless injection regression test.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 32 — Privacy

**Scenario:** A prompt template logs raw personal data during debugging.

**Design response:** Avoid logging secrets and minimise personal data.

**Practice task:** Replace sample records with synthetic values.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 33 — Long input

**Scenario:** A template receives a very long report.

**Design response:** Define size limits and a preprocessing or sectioning strategy.

**Practice task:** Test near the configured input limit.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 34 — Token budget

**Scenario:** A reusable prompt grows after examples are added.

**Design response:** Estimate prompt size and monitor provider usage.

**Practice task:** Compare version token usage.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 35 — Output length

**Scenario:** The template requests a detailed report without an output budget.

**Design response:** Define expected structure and a suitable output allowance.

**Practice task:** Check whether all sections complete.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 36 — Locale

**Scenario:** A template formats dates for different regions.

**Design response:** Make locale an explicit validated variable.

**Practice task:** Test two date formats.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 37 — Currency

**Scenario:** A product prompt mixes currency symbols and amounts.

**Design response:** Pass currency explicitly and avoid inventing exchange rates.

**Practice task:** Test a product with no currency supplied.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 38 — Audience variable

**Scenario:** Audience values are free text and inconsistent.

**Design response:** Use a controlled set of supported audience levels where possible.

**Practice task:** Reject an unsupported level.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 39 — Tone variable

**Scenario:** Tone values produce unpredictable output.

**Design response:** Define supported tone options with short descriptions.

**Practice task:** Test neutral, friendly and formal.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 40 — Template composition

**Scenario:** A large prompt repeats common instructions across templates.

**Design response:** Reuse shared components carefully while keeping task-specific rules explicit.

**Practice task:** Compare rendered prompt versions.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 41 — Template testing

**Scenario:** The team tests only the rendered prompt manually.

**Design response:** Add unit tests for variable substitution and expected sections.

**Practice task:** Test every required placeholder.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 42 — Prompt injection through examples

**Scenario:** A few-shot example contains untrusted commands.

**Design response:** Review examples as carefully as instructions and data.

**Practice task:** Add a test that checks task boundaries.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 43 — Prompt portability

**Scenario:** A template is copied into a different product.

**Design response:** Check audience, terminology, policy and output contract before reuse.

**Practice task:** Create a portability checklist.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 44 — Evaluation drift

**Scenario:** The business task changes but the test set does not.

**Design response:** Review test coverage when requirements or policies change.

**Practice task:** Add examples for the new requirement.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 45 — Model upgrade

**Scenario:** A provider changes the model version.

**Design response:** Rerun prompt evaluations and monitor changes in output quality.

**Practice task:** Compare results before rollout.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 46 — Fallback prompt

**Scenario:** The main prompt fails validation.

**Design response:** Define a safe fallback or human escalation path.

**Practice task:** Simulate invalid output.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 47 — Human approval

**Scenario:** The prompt drafts a high-impact customer message.

**Design response:** Require an authorised person to review before sending.

**Practice task:** Test that the system cannot bypass approval.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 48 — Documentation

**Scenario:** A prompt is stored without usage instructions.

**Design response:** Document purpose, variables, examples, limitations and tests.

**Practice task:** Ask another developer to maintain it.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


## Reusable-prompt case 49 — Production monitoring

**Scenario:** Prompt failures are not measured.

**Design response:** Track version, validation failures, latency and token usage with privacy safeguards.

**Practice task:** Define an alert for an abnormal failure rate.

**Review questions:**
- Is the task stable across uses?
- Which parts should be variables?
- Are variable types and required values defined?
- Is the output format testable?
- What should happen when evidence or input is missing?
- Is the prompt version recorded?
- What regression test protects this behaviour?

**Expected standard:** A reusable prompt is a maintained application asset. It needs a clear owner, purpose, version, input contract, output contract, tests and documented limitations.


# 19. Anatomy of a reusable prompt

| Component | Purpose | Example |
|---|---|---|
| Identifier | Names the prompt | support_reply_draft |
| Version | Tracks changes | 1.0.0 |
| Purpose | Explains the task | Draft a support reply |
| Role or perspective | Sets a useful viewpoint | Customer-support writing assistant |
| Task | States the required operation | Draft a reply from the supplied ticket |
| Context | Provides business rules | Approved support policy excerpt |
| Audience | Defines who reads the output | Customer |
| Input variables | Supplies changing data | ticket_text, policy_text |
| Constraints | Defines boundaries | Do not invent account status |
| Output contract | Defines expected structure | subject, body, escalation_required |
| Uncertainty rule | Handles missing evidence | Mark missing information |
| Tests | Checks behaviour | Representative ticket dataset |

# 20. A prompt template specification

Before writing a reusable template, answer:
1. What business task does it perform?
2. Who uses the result?
3. Which model or provider will receive it?
4. What information must be supplied?
5. Which inputs are optional?
6. What data types are expected?
7. What should happen when an input is missing?
8. What information must never be invented?
9. What output format is required?
10. How will output be validated?
11. What failure cases are expected?
12. Who owns the template?
13. How is it versioned?
14. Which regression tests must pass?
15. How will production performance be monitored?

# 21. Python template example

~~~python
def build_product_prompt(product_name, product_details, audience):
    template = """
TASK:
Write a product summary.

AUDIENCE:
{audience}

RULES:
- Use only supplied details.
- Do not invent specifications.
- If a detail is missing, say it was not provided.

PRODUCT:
{product_name}

DETAILS:
{product_details}

OUTPUT:
Summary:
Key benefits:
Information not provided:
"""

    return template.format(
        audience=audience,
        product_name=product_name,
        product_details=product_details
    ).strip()


prompt = build_product_prompt(
    product_name="Sample Laptop",
    product_details="16 GB memory; 512 GB storage",
    audience="A first-time buyer"
)

print(prompt)
~~~

## Line-by-line explanation
1. The function receives three values: product name, details and audience.
2. The template is a multi-line string.
3. Each placeholder names a value that changes between calls.
4. The task remains stable for every product.
5. The audience variable changes the explanation style.
6. The rules restrict the model to supplied information.
7. The missing-information rule discourages invented specifications.
8. The product name is inserted in its designated place.
9. Product details are inserted in a separate section.
10. The output headings make the requested structure explicit.
11. format() substitutes the named placeholders.
12. strip() removes outer whitespace.
13. return sends the completed prompt to the caller.
14. The example call supplies synthetic product information.
15. print() displays the final prompt for inspection.

**Important:** This example teaches string templates. Production systems should validate input, use structured provider messages and protect untrusted variable content. Do not treat a prompt as an access-control mechanism.

# 22. Prompt versioning policy

Use a simple version policy that the team can maintain:
- Major version: changes the task contract or output structure.
- Minor version: adds compatible behaviour or a new optional field.
- Patch version: corrects wording without changing the intended contract.

Record for every change:
- Old version.
- New version.
- Date.
- Author or owner.
- Reason for change.
- Expected effect.
- Test cases run.
- Test results.
- Known risks.
- Rollback plan.

# 23. Regression testing

After a prompt change:
1. Load the fixed evaluation dataset.
2. Render the old prompt version.
3. Render the new prompt version.
4. Run both against the same inputs where possible.
5. Keep the model and settings fixed for the comparison.
6. Validate output format.
7. Compare factual correctness.
8. Compare missing-information behaviour.
9. Compare safety and privacy behaviour.
10. Compare token usage and latency.
11. Review failures manually.
12. Approve or reject the change.
13. Record the decision.

# 24. Prompt library directory example

~~~text
prompt_library/
    README.md
    support/
        ticket_classifier_v1.txt
        ticket_classifier_v2.txt
        reply_drafter_v1.txt
    education/
        lesson_explainer_v1.txt
        quiz_generator_v1.txt
    extraction/
        resume_extractor_v1.txt
        invoice_extractor_v1.txt
    tests/
        test_ticket_classifier.json
        test_lesson_explainer.json
    CHANGELOG.md
~~~

This is one possible organisation. A project may use Python modules, configuration files or a prompt-management service. Choose an approach that supports review, versioning and automated tests.

# 25. Day 15 practical assessment
1. Create at least three reusable business prompt templates.
2. Give each template a clear identifier and version.
3. Define required and optional variables.
4. Define the output contract.
5. Include a missing-information rule.
6. Add representative examples where useful.
7. Create at least five test cases per template.
8. Include one invalid-input test per template.
9. Include one prompt-injection boundary test.
10. Validate outputs in application code or a test harness.
11. Record a prompt change in a changelog.
12. Run regression tests after the change.
13. Compare token usage where measurable.
14. Document provider-specific assumptions.
15. Submit templates, tests, README and evaluation results.

**Assessment standard:** A strong submission is reusable, documented, versioned, testable and explicit about missing information and limitations.