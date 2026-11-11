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
