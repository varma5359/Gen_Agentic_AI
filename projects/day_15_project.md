# Day 15 Project — Reusable Business Prompt Library

**Duration:** 45–75 minutes. Build the prompt library before calling a model.

## Objective
Create reusable templates for product summaries, customer email drafts and meeting summaries. Store metadata, collect variable inputs, validate required fields and test prompt versions.

## Requirements
- At least three prompt templates.
- Each template has task, audience/context, rules, input placeholders and output format.
- Role included only when it adds value.
- Unique prompt ID and version.
- List and select templates.
- Collect and validate required variables.
- Render and display completed prompt.
- Test normal, missing, conflicting and unsupported input.
- Compare at least two versions using the same test set.
- No API key required; model execution is an optional extension.

## Suggested structure
~~~text
day15_prompt_library/
    main.py
    prompts.py
    prompt_tests.json
    README.md
~~~

## Suggested prompt metadata
- prompt_id
- version
- purpose
- required_variables
- template_text
- output_format
- change_notes

## Implementation tasks
1. Define three prompt templates.
2. Write a function to list templates.
3. Validate required variables.
4. Render a selected template.
5. Add test cases for normal, missing, conflicting and unsupported information.
6. Define an evaluation rubric.
7. Compare v1 and v2 on identical tests.
8. Document limitations.

## Sample product data
Product: Wireless Keyboard  
Facts: Compact layout; USB-C charging; black finish.  
Audience: First-time buyers.

Rendered prompt must include the supplied product name and facts, audience, no-invention rule and requested output structure.

## Test plan
| Test | Expected |
|---|---|
| Valid product input | Prompt renders |
| Missing details | Validation or explicit missing-data handling |
| Missing audience | Clear error |
| Unknown prompt ID | Friendly not-found message |
| v1/v2 | Version and change notes visible |
| Unsupported feature | No-invention rule present |
| Input says “ignore all rules” | Treat as untrusted data; do not claim full injection prevention |

## Evaluation
Score 1–5 for clarity, factual grounding, completeness, output format and consistency. If no model was called, evaluate prompt structure only and mark output quality as not tested.

## Submission
Submit source, three templates, version history, test cases, results and README. Never include customer confidential information or API keys.

## Optional extension
Add JSON export or a simple Streamlit interface after the CLI works.
