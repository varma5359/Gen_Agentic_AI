# Day 13 Project — LLM Generation Parameter Experiment

**Duration:** 45–60 minutes. This is an experiment, not a search for a magic setting.

## Objective
Compare temperature, top-p and output-token limits using a fixed prompt and input. If provider access is unavailable, submit an experiment plan and label it clearly as not executed. Never invent model outputs.

## Requirements
1. Select one model/API if access is available.
2. Record model identifier/version and test date.
3. Write one fixed prompt and fixed input.
4. Record a baseline.
5. Change only temperature and record output.
6. Restore baseline, change only top-p if supported.
7. Restore baseline, change output-token limit and observe completeness.
8. Repeat stochastic runs where practical.
9. Evaluate correctness, completeness, instruction following and variation.
10. Draw conclusions only from observed evidence.

## Fixed prompt
“Explain the difference between a Python list and tuple to a beginner. Give one example of each. Do not invent features.”

Use exactly the same prompt in each run.

## Experiment record
| Run | Model | Temperature | Top-p | Max output tokens | Output / observation |
|---|---|---:|---:|---:|---|
| Baseline | Record | Record | Record | Record | Paste actual output |
| Temperature test | Same | Change only this | Same | Same | Paste actual output |
| Top-p test | Same | Same | Change only this | Same | Paste actual output |
| Output-limit test | Same | Same | Same | Change only this | Paste actual output |

Provider support and parameter ranges vary. Read the selected API documentation first.

## Evaluation rubric
Score each 1–5: correctness, completeness, instruction following, clarity and variation across repeated runs. A higher variation score is not automatically better.

## No API access?
Submit the experiment design, hypotheses and blank result table. Clearly label it planned, not executed. Do not fabricate results.

## Reflection
1. Did temperature change wording?
2. Did correctness change?
3. Did a small output limit truncate the answer?
4. Was top-p supported?
5. What evidence supports your conclusion?
6. What cannot be concluded from this small test?

## Submission
Submit prompt, model/date, settings, genuine outputs (if run), scores and evidence. Remove secrets and personal data.
