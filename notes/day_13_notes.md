# Day 13 — Temperature, top-p, max tokens, model limitations and hallucinations

**Phase 2 | Beginner | 2–3 hours | Project: LLM Generation Parameter Experiment**

## Learning outcomes
Explain temperature, top-p and output-token limits; distinguish generation settings from training; design a controlled experiment; identify hallucinations and model limitations; and report conclusions based on evidence.

## 1. Why generation settings exist
A language model calculates scores for possible next tokens. Decoding settings influence how a token is selected and how long the response can continue. Settings influence behaviour; they do not guarantee truth.

## 2. Temperature
Temperature changes the sharpness of the probability distribution used during sampling.
- Lower temperature generally concentrates selection around high-probability tokens.
- Higher temperature generally allows more varied selections.
- Exact behaviour depends on the provider and decoding implementation.

Use a lower setting when consistency is important; explore higher settings when varied wording is useful. Neither guarantees correctness.

## 3. Top-p
Top-p, also called nucleus sampling, restricts selection to a set of likely tokens whose cumulative probability reaches a configured threshold.
- Smaller top-p narrows the candidate pool.
- Larger top-p permits a broader pool.
- It is not a response-length setting.

Some providers advise changing temperature or top-p, not both simultaneously, during comparisons. Follow the chosen API documentation.

## 4. Maximum output tokens
This limits how many tokens may be generated in the response. It is not the same as the complete context window. A limit that is too small may cut off a response. A limit that is unnecessarily large may permit overly long responses and higher cost.

## 5. Compare controls
| Setting | Controls | Does not guarantee |
|---|---|---|
| Temperature | Sampling distribution | Factual accuracy |
| Top-p | Candidate probability mass | Relevance |
| Max output tokens | Generated response allowance | Complete answer |
| Model selection | Underlying model behaviour/capability | Zero hallucinations |

Supported settings and valid ranges vary by provider and model.

## 6. Hallucinations
A hallucination is plausible-sounding generated content that is false, unsupported or fabricated. Examples:
- invented citations or URLs;
- a made-up API parameter;
- incorrect policy details stated confidently;
- a summary that adds claims absent from the source.

Fluent language is not evidence.

## 7. Why they happen
Models generate likely sequences from learned patterns and supplied context. They do not automatically verify every claim against an authoritative source. Missing context, ambiguity, contradictory sources, weak reasoning and unsupported questions can lead to fabricated details.

## 8. Reduce risk in the application
1. Supply relevant, trusted context where available.
2. Ask the model to identify missing evidence.
3. Validate references against the actual source.
4. Check critical facts against authoritative systems.
5. Validate structured output with schemas.
6. Use deterministic code for calculations and business rules.
7. Evaluate representative cases.
8. Require human review for high-impact decisions.

“Never hallucinate” in a prompt cannot guarantee accuracy.

## 9. Design a fair experiment
Keep model, prompt and input fixed. Change one setting at a time. Record exact values and raw outputs. Repeat runs when sampling is stochastic. Evaluate correctness, completeness, instruction following and variation. One attractive response is not proof.

## 10. Industry scenario
A customer-support assistant explains refund policy. A varied answer is not necessarily better. Supply approved policy text, test the response against policy facts, avoid unsupported claims and route uncertain cases to staff.

## 11. Common mistakes
| Mistake | Correction |
|---|---|
| High temperature means more intelligence | It changes sampling |
| Low temperature guarantees truth | False claims remain possible |
| Top-p controls response length | It controls candidate probability mass |
| Max tokens means context size | It caps generated output |
| One output proves best setting | Run controlled repeated tests |
| “Do not hallucinate” solves factuality | Verify claims against evidence |
| Use LLM for critical arithmetic | Calculate in deterministic code |

## 12. Practice
1. Explain temperature to a beginner.
2. Explain top-p without calling it a creativity slider.
3. Predict the effect of a tiny output limit.
4. Identify three hallucination examples.
5. Design a test changing only temperature.
6. Propose safeguards for policy answers.

## 13. Quiz
1. Temperature influences: A sampling B database C network D tokenizer. **A.**
2. Top-p is: A nucleus sampling B SQL join C authentication D file upload. **A.**
3. Max output tokens limits: A generated output B training data C bandwidth D users. **A.**
4. Does low temperature guarantee truth? A yes B no. **B.**
5. Fair comparison: A change everything B change one variable and record runs C guess D select favourite. **B.**

## 14. Interview questions
- Explain temperature and top-p.
- Max output tokens versus context window?
- What is a hallucination?
- How would you evaluate a generation setting?
- What should an application do when evidence is missing?

**Completion check:** You can explain controls and design a controlled test. Next: system/user messages and zero-shot/few-shot prompting.


# 18. Extended controlled-experiment workbook

The following experiments are designed to teach you how to evaluate generation settings and model limitations. They are not claims that one setting guarantees a particular answer. Provider behaviour varies by model and endpoint.

## Experiment 1 — Factual definition

**Scenario:** Ask for a stable definition and compare outputs under lower and higher temperature settings.

**Experiment design:** Check correctness against a trusted reference; fluent wording is not evidence.

**Evaluation:** Record whether wording changes and whether any factual claim changes.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 2 — Creative slogan

**Scenario:** Ask for five original slogans for a fictional learning app.

**Experiment design:** Higher variation may help explore alternatives, but review relevance and appropriateness.

**Evaluation:** Compare diversity and usefulness rather than choosing the longest response.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 3 — Fixed-format label

**Scenario:** Ask the model to return exactly one of Billing, Technical, Account or Other.

**Experiment design:** Use a clear schema and evaluate exact-label compliance across repeated trials.

**Evaluation:** Count invalid labels and category mistakes.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 4 — Short summary

**Scenario:** Request a three-sentence summary of a supplied paragraph.

**Experiment design:** Set a suitable output allowance and check that the core meaning is preserved.

**Evaluation:** Measure sentence count and factual coverage.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 5 — Long report

**Scenario:** Request a structured report with headings and recommendations.

**Experiment design:** A low output allowance may stop the report early; plan response length.

**Evaluation:** Check whether all required sections are present.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 6 — JSON extraction

**Scenario:** Extract name, date and amount from a supplied synthetic invoice.

**Experiment design:** Validate JSON syntax and field types after generation.

**Evaluation:** Test missing fields and malformed JSON.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 7 — Math calculation

**Scenario:** Ask the model to calculate a multi-step arithmetic result.

**Experiment design:** Do not assume temperature makes arithmetic reliable; use deterministic code for critical calculations.

**Evaluation:** Compare the answer with Python's result.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 8 — Code generation

**Scenario:** Ask for a Python function that validates an email-like string.

**Experiment design:** Run tests and inspect edge cases; generation settings do not prove code correctness.

**Evaluation:** Record test pass rate, not just whether code looks plausible.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 9 — Policy question with evidence

**Scenario:** Supply a short fictional policy and ask a question answered by it.

**Experiment design:** Check whether the response stays within the supplied policy.

**Evaluation:** Mark unsupported additions as failures.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 10 — Question without evidence

**Scenario:** Ask a question whose answer is absent from the supplied material.

**Experiment design:** The prompt should instruct the model to say the evidence is missing.

**Evaluation:** Check whether the model admits uncertainty.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 11 — Ambiguous request

**Scenario:** Ask “make it better” without supplying a target or criteria.

**Experiment design:** Improve the prompt by defining audience, goal and success criteria.

**Evaluation:** Compare the number of unsupported assumptions.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 12 — Conflicting instructions

**Scenario:** Provide two incompatible formatting requirements.

**Experiment design:** Resolve the conflict in the prompt design rather than hoping a setting will fix it.

**Evaluation:** Check whether the chosen priority is followed.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 13 — Very small output limit

**Scenario:** Request a five-part explanation with a tiny maximum output allowance.

**Experiment design:** Expect possible incompleteness; do not treat a cut-off answer as complete.

**Evaluation:** Check the ending and required-section count.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 14 — Large output limit

**Scenario:** Request a one-line answer with a very large output allowance.

**Experiment design:** A large ceiling does not require a long response, but avoid unnecessary allowances.

**Evaluation:** Measure actual output length and usage.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 15 — Repeated identical prompt

**Scenario:** Run the same prompt multiple times with the same settings.

**Experiment design:** Compare variation; hosted models may still have implementation-specific behaviour.

**Evaluation:** Save outputs and note the date, model and settings.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 16 — Prompt with examples

**Scenario:** Provide three labelled examples before a new classification item.

**Experiment design:** Examples may guide the task; incorrect examples can mislead.

**Evaluation:** Measure accuracy against a labelled test set.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 17 — Unbalanced examples

**Scenario:** Provide many Billing examples but only one Technical example.

**Experiment design:** Example distribution may bias model responses.

**Evaluation:** Create balanced examples and compare results.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 18 — Rare category

**Scenario:** Include an uncommon but valid label in the classification task.

**Experiment design:** Check whether the model overuses common categories.

**Evaluation:** Report per-class precision and recall where appropriate.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 19 — Sarcasm

**Scenario:** Use a support message with sarcastic wording.

**Experiment design:** Ambiguity can cause misclassification regardless of temperature.

**Evaluation:** Include human-labelled edge cases in the evaluation set.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 20 — Negation

**Scenario:** Use “I do not want to cancel my subscription”.

**Experiment design:** Ensure the model distinguishes negation and intent.

**Evaluation:** Test paired positive and negative examples.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 21 — Multiple intents

**Scenario:** Use a message containing both billing and technical problems.

**Experiment design:** Define whether multiple labels are allowed or which priority rule applies.

**Evaluation:** Compare output with the defined policy.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 22 — Sensitive decision

**Scenario:** Ask the model to make a high-impact eligibility decision.

**Experiment design:** Do not rely on generation settings as a safety control; use validated rules and human oversight.

**Evaluation:** Document what must be reviewed by a person.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 23 — Medical-style uncertainty

**Scenario:** Ask for an interpretation of a fictional health-related note.

**Experiment design:** Use appropriate boundaries and qualified human review; do not treat model confidence as diagnosis.

**Evaluation:** Check whether limitations and escalation are present.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 24 — Legal-style uncertainty

**Scenario:** Ask for a definitive legal conclusion from incomplete facts.

**Experiment design:** Do not present generated output as a verified legal determination.

**Evaluation:** Check whether missing facts and professional review are identified.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 25 — Current information

**Scenario:** Ask for a current price or policy without supplying a current source.

**Experiment design:** The model may not have current information; retrieve an authoritative source when required.

**Evaluation:** Record whether the answer cites supplied evidence.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 26 — Invented citation test

**Scenario:** Ask for references when no sources are supplied.

**Experiment design:** A model may fabricate references; validate every citation against a real source.

**Evaluation:** Count citations that cannot be verified.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 27 — API parameter test

**Scenario:** Ask for a parameter name for a library version not provided.

**Experiment design:** The model may invent plausible API details.

**Evaluation:** Check the official versioned documentation.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 28 — Version mismatch

**Scenario:** Ask for code using a library version different from the model's learned examples.

**Experiment design:** Supply the exact version and test the code.

**Evaluation:** Record compatibility errors.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 29 — Prompt injection in source

**Scenario:** Supply a document that contains irrelevant instructions to the model.

**Experiment design:** Treat document text as untrusted data and keep task instructions separate.

**Evaluation:** Check that embedded instructions do not override the task.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 30 — Long context distraction

**Scenario:** Place the answer in one paragraph among many irrelevant passages.

**Experiment design:** Retrieval quality and context construction matter; more text is not automatically better.

**Evaluation:** Check whether the answer uses the relevant passage.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 31 — Contradictory source passages

**Scenario:** Supply two passages with different dates and conflicting values.

**Experiment design:** Expose source dates and define precedence rules.

**Evaluation:** Check whether the answer reports the conflict.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 32 — Missing source passage

**Scenario:** Ask a question not answered by the provided material.

**Experiment design:** Require the model to say that the supplied evidence is insufficient.

**Evaluation:** Check for unsupported guesses.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 33 — Tone transformation

**Scenario:** Ask for a neutral paragraph to be rewritten in a friendly tone.

**Experiment design:** Evaluate whether facts remain unchanged while tone changes.

**Evaluation:** Compare factual claims before and after.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 34 — Translation

**Scenario:** Translate a short paragraph and compare settings.

**Experiment design:** Evaluate meaning preservation, not only fluency.

**Evaluation:** Use a bilingual reviewer or trusted reference.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 35 — Language mixing

**Scenario:** Ask for an explanation in a specified mix of English and Hindi.

**Experiment design:** Specify the language ratio or vocabulary requirements clearly.

**Evaluation:** Check that technical terms remain understandable.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 36 — Repeated list items

**Scenario:** Ask for ten distinct examples.

**Experiment design:** A response can repeat ideas even when the output is long.

**Evaluation:** Check semantic duplicates.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 37 — Strict word limit

**Scenario:** Ask for a response under 50 words.

**Experiment design:** Token limits and word limits are different constraints.

**Evaluation:** Count words after generation and validate.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 38 — Strict sentence count

**Scenario:** Ask for exactly four sentences.

**Experiment design:** Check sentence segmentation and punctuation after generation.

**Evaluation:** Reject outputs that do not meet the format.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 39 — Markdown table

**Scenario:** Ask for a table with five specified columns.

**Experiment design:** Validate headers and row structure.

**Evaluation:** Check missing or extra columns.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 40 — Refusal behaviour

**Scenario:** Ask for a harmless request and an out-of-scope request.

**Experiment design:** Evaluate the application's policy behaviour independently of sampling settings.

**Evaluation:** Record false refusals and missed refusals.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 41 — Hallucination bait

**Scenario:** Ask about a fictional product feature that was never supplied.

**Experiment design:** A reliable response should state that the feature is not in evidence.

**Evaluation:** Count invented details.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 42 — Confidence wording

**Scenario:** Ask the model to state confidence in a factual answer.

**Experiment design:** Self-reported confidence is not calibrated probability by default.

**Evaluation:** Do not use the wording as a substitute for evaluation.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 43 — Output continuation

**Scenario:** Ask for a multi-section response and set a low output ceiling.

**Experiment design:** Check provider finish reason or equivalent metadata where available.

**Evaluation:** Detect incomplete output and decide whether a safe continuation is possible.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 44 — Retry after timeout

**Scenario:** Simulate a provider timeout in a test double.

**Experiment design:** Retries need limits, backoff and idempotency where relevant.

**Evaluation:** Confirm that one user action does not create uncontrolled duplicate work.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 45 — Rate limit

**Scenario:** Simulate a rate-limit response.

**Experiment design:** Respect provider retry guidance and avoid immediate retry loops.

**Evaluation:** Test bounded retry behaviour.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 46 — Model comparison

**Scenario:** Run the same evaluation set against two supported models.

**Experiment design:** Compare quality, latency, cost and reliability rather than one impressive example.

**Evaluation:** Record model versions and settings.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 47 — Parameter interaction

**Scenario:** Change temperature and top-p together in one experiment.

**Experiment design:** You cannot attribute the observed change to one setting.

**Evaluation:** Repeat while changing one variable at a time.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 48 — Regression test

**Scenario:** Change a prompt template and rerun the same test cases.

**Experiment design:** Prompt edits can improve one case and break another.

**Evaluation:** Compare old and new pass rates.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.


## Experiment 49 — Human review threshold

**Scenario:** Route uncertain or sensitive outputs to a reviewer.

**Experiment design:** A generation setting is not a substitute for an approval workflow.

**Evaluation:** Define what triggers review and who can approve.

**Record these fields:**
- Model and model version:
- Date and time:
- Prompt version:
- Temperature setting:
- Top-p setting:
- Maximum output setting:
- Input category:
- Output observed:
- Factual or format errors:
- Human review decision:
- Conclusion supported by evidence:

**Interpretation rule:** Change one parameter at a time when studying its effect. Keep the prompt, input, model version and other settings fixed as far as the provider allows.



# 19. How to write an experiment report

Every experiment must include:

1. Objective.
2. Hypothesis.
3. Model name and version.
4. Provider and endpoint.
5. Exact prompt.
6. Input sample.
7. Temperature value, if supported.
8. Top-p value, if supported.
9. Maximum output setting, if supported.
10. Other relevant settings.
11. Number of repeated runs.
12. Raw outputs.
13. Evaluation criteria.
14. Observed errors.
15. Limitations.
16. Conclusion.
17. Next experiment.

Never invent a provider setting or assume every model exposes the same controls. Use the selected provider's current documentation.

# 20. Practical evaluation rubric

| Criterion | What a strong submission demonstrates |
|---|---|
| Controlled variables | Only the intended setting changes |
| Reproducibility | Prompt, model and settings are recorded |
| Evidence | Outputs are saved rather than remembered |
| Factual evaluation | Claims are checked against a trusted reference |
| Format evaluation | Output is parsed or checked against explicit requirements |
| Safety | Sensitive decisions have appropriate human oversight |
| Interpretation | Conclusions are limited to what the test supports |
| Documentation | Limitations and unexpected results are recorded |

# 21. Worked comparison: temperature experiment

**Task:** Generate a short explanation of a Python list for a beginner.

**Fixed prompt:**

~~~text
Explain a Python list to a student who has never programmed.
Use one short example and explain what the square brackets mean.
Do not discuss tuples or dictionaries.
~~~

**Controlled method:**

1. Select one model.
2. Record its exact model identifier.
3. Keep the prompt unchanged.
4. Keep top-p unchanged or use the provider's recommended default.
5. Run a lower temperature supported by the model.
6. Save the response.
7. Run a higher temperature supported by the model.
8. Save the response.
9. Compare factual correctness.
10. Compare wording diversity.
11. Compare whether the required example appears.
12. Repeat if the experiment requires more than one sample.
13. Do not conclude that one setting is universally best from one output.

**What to inspect:**

- Is the definition correct?
- Is the example valid Python?
- Does it explain square brackets?
- Does it accidentally discuss unrelated structures?
- Is the response readable for a beginner?
- Does the output stay within the requested length?

# 22. Worked comparison: output-token allowance

**Task:** Request a structured lesson summary with five sections.

Test a small output allowance and a larger allowance while keeping the rest of the request fixed.

Inspect:

- Whether the answer finishes.
- Whether all five sections appear.
- Whether a code block is closed.
- Whether the provider reports a length-related finish condition.
- Whether the larger allowance causes unnecessary verbosity.

The correct allowance depends on the expected task output. A larger maximum does not guarantee a better answer.

# 23. Hallucination verification workflow

When a model makes a factual claim:

1. Identify the claim.
2. Determine whether the prompt supplied evidence for it.
3. Find the authoritative source needed to verify it.
4. Check the source's date and version.
5. Compare the claim with the source.
6. Mark the claim as supported, contradicted or unverified.
7. Do not accept invented citations.
8. If the source is missing, ask for evidence or state uncertainty.
9. Record the error as an evaluation example.
10. Add a regression test if the issue is important.

## Claim verification table

| Generated claim | Evidence available? | Verification outcome | Action |
|---|---|---|---|
| Claim appears in supplied source | Yes | Supported after checking | May use with source |
| Claim contradicts supplied source | Yes | Contradicted | Reject or correct |
| Claim has no supplied evidence | No | Unverified | Do not present as established fact |
| Citation URL is invented | No valid source | Failed | Remove and investigate |
| Claim depends on current data | Old or missing source | Not current | Retrieve current authoritative data |

# 24. Production guardrails

Generation settings are not security controls. A production application also needs:

- Authentication.
- Authorisation.
- Input validation.
- Output validation.
- Prompt-injection resistance.
- Data minimisation.
- Provider timeout handling.
- Bounded retries.
- Rate-limit handling.
- Logging with privacy protections.
- Evaluation datasets.
- Human approval for sensitive actions.
- Monitoring and incident handling.

Temperature does not make a model safe. Top-p does not verify a citation. Maximum output tokens do not validate JSON.

# 25. Day 13 practical assessment

Complete all tasks:

1. Explain temperature in your own words.
2. Explain top-p in your own words.
3. Explain maximum output tokens.
4. Distinguish output allowance from context capacity.
5. Explain hallucination with a business example.
6. Create a controlled comparison plan.
7. Change only one generation setting in the first experiment.
8. Save the exact prompt and outputs.
9. Evaluate outputs using explicit criteria.
10. Verify one factual claim against a trusted source.
11. Demonstrate a response that is cut off by a small output allowance.
12. Explain how the application should detect incomplete output.
13. Describe one case requiring human review.
14. Explain why temperature cannot guarantee correctness.
15. Submit an experiment report.

**Assessment standard:** The learner must distinguish settings accurately, control experiment variables, evaluate outputs against criteria and avoid unsupported conclusions.
