# Day 13 Interview Guide — Generation Parameters and Hallucinations

## 1. What is temperature?
A setting that adjusts the sharpness of the probability distribution used during sampling. Lower values generally concentrate selection on likely tokens; higher values generally allow more variation. Provider behaviour can differ.

## 2. What is top-p?
Nucleus sampling: sample from a set of likely tokens whose cumulative probability reaches the configured threshold. It is not a response-length setting.

## 3. Temperature versus top-p?
Both influence token selection but use different controls. Temperature reshapes probabilities; top-p limits the candidate pool by cumulative probability. Change one at a time during an experiment.

## 4. What is max output tokens?
A cap on generated response tokens. It differs from context capacity and may truncate a response.

## 5. Does lower temperature remove hallucinations?
No. It may make output more consistent but does not verify facts. Use trusted context, evidence checks, deterministic calculations and evaluation.

## 6. Define hallucination.
Plausible-sounding but false, unsupported or fabricated model output. Examples include invented references, APIs or policy details.

## 7. How would you test generation settings?
Keep model, prompt and input constant, vary one setting, record raw outputs, repeat runs where needed and score correctness, completeness and instruction following.

## 8. What is a model limitation?
A boundary in knowledge, context, reasoning, modality, tool access or reliability. Test realistic cases and design safe fallbacks.

## 9. Why is “never hallucinate” not enough?
A prompt cannot guarantee factual correctness. Applications need evidence, validation, monitoring and human review for sensitive cases.

## 10. Practical interview task
Design a controlled experiment comparing two temperature values. Explain what remains fixed, what changes, how you record runs and how you judge quality.
