# Day 14 — Interview Questions and Answers

## Prompt Engineering Fundamentals

1. **What is prompt engineering?**  
   It is the practice of designing and testing inputs and instructions so a model can perform a task more reliably.

2. **What is a prompt?**  
   A prompt is the information and instructions supplied to a model.

3. **What is a system prompt?**  
   It is a high-level instruction message used by many chat APIs to guide assistant behaviour.

4. **What is a user prompt?**  
   It is the request or information provided by the end user.

5. **What is a developer message?**  
   In APIs that support it, it contains application-level instructions from the developer.

6. **What is zero-shot prompting?**  
   Asking the model to perform a task without giving examples of the desired task output.

7. **What is few-shot prompting?**  
   Providing a small number of examples in the prompt to demonstrate the expected input/output pattern.

8. **Do few-shot examples train the model?**  
   No. They guide the model's response in the current context; they do not update model weights.

9. **What should a good classification prompt include?**  
   The task, allowed labels, input boundaries and required output format.

10. **Why specify allowed labels?**  
    It constrains the expected answer and makes validation easier.

11. **Does a system prompt provide security by itself?**  
    No. Applications still need authentication, authorization, validation and safe handling of untrusted input.

12. **Why include examples?**  
    Examples can clarify ambiguous categories and demonstrate the required format.

13. **What is a weakness of few-shot prompting?**  
    Poor or unrepresentative examples can guide the model toward incorrect or biased outputs.

14. **How do you evaluate a classifier prompt?**  
    Test it on representative examples with known expected labels and measure correct/incorrect outputs and format compliance.

15. **Why compare a rule-based classifier with an LLM classifier?**  
    It highlights the trade-off between predictable explicit rules and flexible language understanding, while showing that both need testing.
