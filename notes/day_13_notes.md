# Day 13 — LLM Generation Parameters and Hallucinations

**Phase:** 2 — Generative AI and LLM Foundations  
**Approved topic:** Temperature, top-p, max tokens, model limitations and hallucinations  
**Mini-project:** LLM Generation Parameter Experiment  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
- Explain temperature, top-p and maximum output tokens.
- Understand that generation settings influence output, not factual correctness.
- Describe hallucinations and common model limitations.
- Compare outputs using a controlled experiment.
- Record observations without claiming one setting is best for every task.

## 2. How does a model choose the next token?

After processing the input, a language model produces scores (logits) for possible next tokens. A decoding strategy turns those scores into a selection.

```text
Prompt → model scores possible next tokens
       → decoding settings influence selection
       → selected token is added to context
       → repeat until a stop condition
```

A model's output can change when sampling settings change. The same settings do not guarantee identical output in every provider or serving setup.

## 3. Temperature

**Meaning:** Temperature adjusts how sharply or broadly the model uses its next-token probability distribution during sampling.

- Lower temperature: choices are more concentrated around high-probability tokens; output is often more predictable.
- Higher temperature: probability is spread more broadly; output may be more varied.
- Temperature does not add knowledge or verify facts.
- Some models or endpoints may restrict, ignore or interpret this parameter differently. Check the selected model's API documentation.

| Setting (illustrative) | Typical effect |
|---:|---|
| 0.0 / very low | More predictable selection where supported |
| 0.3 | Often restrained variation |
| 0.7 | More variation |
| 1.0 or above | More exploratory variation, if supported |

Do not promise that temperature 0 always gives identical outputs across all systems.

## 4. Top-p (nucleus sampling)

**Meaning:** Top-p limits sampling to a set of likely next tokens whose cumulative probability reaches the configured threshold.

Example with a simplified probability list:

| Candidate | Probability | Cumulative |
|---|---:|---:|
| A | 0.50 | 0.50 |
| B | 0.25 | 0.75 |
| C | 0.15 | 0.90 |
| D | 0.10 | 1.00 |

If top-p is 0.80, candidates A and B form the smallest set reaching at least 0.80. The model samples within the retained set after renormalization. Real distributions have many candidates.

- Lower top-p generally narrows the candidate set.
- Higher top-p generally permits more candidates.
- Temperature and top-p both affect sampling. Avoid changing both at once during a beginner experiment.
- Provider support and defaults vary.

## 5. Maximum output tokens

This setting limits how many tokens the model may generate in its response (the parameter name varies by API).

It is not the same as the context-window size.

Example:
- Prompt and history use 1,200 tokens.
- The application requests a maximum of 200 output tokens.
- The answer may stop at the output limit even if the response is incomplete.

A response can also end because the model/provider returns a stop condition or reaches another limit.

## 6. Model limitations

LLMs can:
- Generate false statements confidently (hallucinations).
- Miss details in long or unclear prompts.
- Reflect limitations or biases in training data.
- Produce outdated information if not connected to current sources.
- Miscalculate or make reasoning errors.
- Follow malicious instructions embedded in untrusted text if the application is not designed defensively.
- Produce different answers to similar prompts.

### What is a hallucination?
A hallucination is generated content that is unsupported, fabricated or incorrect while being presented as if it were true.

Example:
- User: “Give me the official 2026 policy number for Company X.”
- Model: invents a plausible-looking policy number.
- Risk: the user may trust the confident wording.

**Safer application behaviour**
1. Ask for source material when the answer must be grounded.
2. Retrieve trusted documents where appropriate.
3. Ask the model to say when evidence is missing.
4. Validate critical facts against authoritative sources.
5. Show sources or evidence to users.
6. Require human review for high-impact decisions.

A prompt alone cannot guarantee zero hallucinations.

## 7. Parameter experiment without an API

This Python exercise demonstrates a controlled experiment using a fixed set of fictional candidate probabilities. It does **not** reproduce a real LLM's sampler.

```python
candidates = [
    ("A", 0.50),
    ("B", 0.25),
    ("C", 0.15),
    ("D", 0.10)
]

top_p = 0.80
cumulative = 0.0

print("Candidates retained for top-p =", top_p)

for token, probability in candidates:
    cumulative += probability
    print(token, "cumulative probability:", round(cumulative, 2))

    if cumulative >= top_p:
        break
```

**Expected output**
```text
Candidates retained for top-p = 0.8
A cumulative probability: 0.5
B cumulative probability: 0.75
C cumulative probability: 0.9
```

The threshold is crossed at C, so A, B and C are retained in this simple illustration. This uses the first candidates in descending probability order.

## 8. Mini-project — LLM Generation Parameter Experiment

**Goal:** Compare how settings affect one task, then document observations.

Choose a provider/model that supports the settings. Keep the prompt and model fixed. Change only one setting per experiment.

**Prompt**
```text
Write a product description for a reusable stainless-steel water bottle.
Audience: college students.
Length: 3 sentences.
Do not invent certifications or performance claims.
```

**Experiment sheet**

| Run | Temperature | Top-p | Max output tokens | What to record |
|---|---:|---:|---:|---|
| A | 0.2 | Keep provider default | 120 | Wording and consistency |
| B | 0.8 | Keep provider default | 120 | Wording and variation |
| C | Keep default | 0.5 (if supported) | 120 | Candidate diversity |
| D | Keep default | Keep default | 30 | Whether answer is cut short |

These values are classroom experiment settings, not universal recommendations. Follow provider constraints.

**Record for each run**
- Model and provider name.
- Date and settings.
- Exact prompt.
- Output.
- Input/output token usage if available.
- Was the answer complete?
- Did it invent an unsupported claim?
- Which output best followed the task, and why?

**No API key?** Perform the experiment as a paper exercise using outputs supplied by the trainer. Do not paste secret keys into source code or commit them to Git.

## 9. Common mistakes
- Believing higher temperature means higher intelligence.
- Assuming lower temperature guarantees truth.
- Changing temperature and top-p simultaneously, then not knowing which caused the change.
- Confusing output-token limit with context-window size.
- Treating a fluent answer as verified evidence.
- Comparing outputs without recording the model and exact prompt.

## 10. Practice with answers
1. What does temperature influence? **The sampling distribution used to select tokens.**
2. Does top-p mean “top p words”? **No. It is a cumulative probability threshold.**
3. Can max output tokens cause an incomplete answer? **Yes.**
4. Is hallucination always intentional? **No. It is a model output failure, not proof of intent.**
5. How do you reduce risk? **Ground answers in reliable sources, validate claims and use review for important decisions.**

## 11. Lesson checkpoint
Students should be able to explain the three controls, run the top-p illustration, and write a fair experiment report. Day 14 moves from model settings to the instructions supplied to a model.
