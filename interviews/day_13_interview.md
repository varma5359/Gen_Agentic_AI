# Day 13 — Interview Questions and Answers

## Generation Parameters and Hallucinations

1. **What is temperature?**  
   Temperature controls how sharply or broadly the model's next-token probability distribution is used during sampling.

2. **What is the effect of low temperature?**  
   It generally makes sampling more concentrated around high-probability tokens, often producing more predictable wording.

3. **Does high temperature make a model more intelligent?**  
   No. It changes output variation, not the model's knowledge or intelligence.

4. **What is top-p sampling?**  
   It retains a set of likely tokens whose cumulative probability reaches a configured threshold, then samples from that set.

5. **What is the difference between temperature and top-p?**  
   Both influence sampling, but temperature reshapes the distribution while top-p limits the candidate set by cumulative probability.

6. **What is max output tokens?**  
   It is a limit on the number of tokens generated in the response. API parameter names and behaviour vary.

7. **Is max output tokens the same as context length?**  
   No. One limits generated output; the other describes the model's supported context capacity.

8. **What is an LLM hallucination?**  
   It is unsupported, fabricated or incorrect content presented as if it were true.

9. **Why do hallucinations occur?**  
   A model generates likely continuations from learned patterns and available context; it is not automatically verifying every claim against authoritative evidence.

10. **Can low temperature prevent hallucinations?**  
    No. It may make output more predictable but does not guarantee factual correctness.

11. **How can hallucination risk be reduced?**  
    Ground answers in trusted sources, retrieve relevant evidence, validate important claims and use human review for high-impact tasks.

12. **Why run a controlled parameter experiment?**  
    It helps identify the effect of one setting while keeping the prompt and model constant.

13. **Why record the model name and exact prompt?**  
    So results can be reproduced and compared fairly.

14. **Should temperature and top-p both be changed in one experiment?**  
    Not when isolating their individual effects. Change one variable at a time.

15. **Can a model's answer be fluent but wrong?**  
    Yes. Fluency is not proof of factual accuracy.
