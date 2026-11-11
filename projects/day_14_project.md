# Day 14 Project — Business Text Classification Prompt Application

**Duration:** 45–75 minutes. Start with prompt design and a test set, not a model API.

## Objective
Build an application that creates zero-shot and few-shot prompts for routing support messages to business teams.

## Starting label taxonomy
- Billing: charges, invoices, refunds and payment issues.
- Technical: software defects, crashes and malfunctioning features.
- Account: sign-in, password, profile and access issues.
- Other: requests outside the first three categories.

A real company must agree and refine its own taxonomy.

## Requirements
1. Accept a support message.
2. Build a zero-shot prompt.
3. Build a few-shot prompt with at least three labelled examples.
4. Display the prompt for inspection.
5. Keep a labelled test dataset.
6. If no API is available, allow manual recording of actual output; do not invent results.
7. Validate output against the four allowed labels.
8. Compare actual and expected labels and report correct/incorrect counts.

## Suggested structure
~~~text
day14_ticket_classifier/
    main.py
    prompts.py
    test_cases.json
    README.md
~~~

## Starter test data
| Message | Expected label |
|---|---|
| I was charged twice this month | Billing |
| The app crashes when I upload a PDF | Technical |
| I cannot reset my password | Account |
| Please tell me your office address | Other |
| The invoice amount is incorrect | Billing |
| The login page shows a server error | Define a documented rule |

For the last row, decide whether the dominant issue is a technical failure or account access. Document the decision instead of hiding ambiguity.

## Implementation tasks
1. Define label descriptions and decision rules.
2. Write zero-shot prompt template.
3. Add few-shot examples.
4. Separate prompt construction from model invocation.
5. Create a test dataset.
6. Validate returned labels.
7. Compare actual versus expected results.
8. Document limitations.

## Test plan
| Test | Expected |
|---|---|
| Billing message | Prompt includes all labels |
| Technical message | Few-shot example includes technical case |
| Blank input | Rejected or handled clearly |
| Unknown model output | Marked invalid |
| Allowed label | Accepted |
| Ambiguous message | Business rule documented |
| No API key | Offline prompt-building still works |

## Privacy and safety
Use synthetic messages. Do not send real customer personal data to an unapproved external model. Never let a classification prompt grant access or execute account actions.

## Submission
Submit prompts, taxonomy, test cases, evaluation results and README. Clearly distinguish offline work from genuine API execution.

## Optional extension
Add an uncertainty/manual-review label. Do not assume a model's self-reported confidence is calibrated probability.
