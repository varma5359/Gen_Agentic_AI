# Day 15 — Interview Questions and Answers

## Prompt Templates, Reuse and Testing

1. **What is a prompt template?**  
   A reusable prompt structure with placeholders for changing values.

2. **Why use prompt templates?**  
   They reduce copy-paste, improve consistency and make prompts easier to maintain and test.

3. **What is role prompting?**  
   Asking a model to respond from a specified role or perspective, such as a support assistant or business analyst.

4. **Does role prompting make the model a real expert?**  
   No. It guides style and task focus but does not grant credentials or guarantee accuracy.

5. **What is prompt structure?**  
   A clear arrangement of role, task, context, constraints, input and expected output.

6. **What does Python's `str.format()` do?**  
   It returns a new string with named placeholders replaced by supplied values.

7. **Does `format()` call an LLM?**  
   No. It performs local string formatting.

8. **What happens if a named placeholder is missing?**  
   `str.format()` raises a `KeyError`.

9. **What does `**kwargs` mean in a Python function?**  
   It collects additional keyword arguments into a dictionary.

10. **Why should prompt templates be tested?**  
    To detect missing placeholders, unclear instructions, format failures and poor behaviour on edge cases.

11. **What is a prompt test case?**  
    A defined input with an expected behaviour or output property used to evaluate a prompt.

12. **Name useful prompt test categories.**  
    Normal input, empty input, long input, ambiguous input, conflicting/untrusted text and output-format checks.

13. **Why separate instructions from untrusted content?**  
    It makes the prompt clearer and helps the application treat user-provided text as data rather than trusted instructions. Additional safeguards are still needed.

14. **Should API keys be stored inside prompt templates or committed to Git?**  
    No. Credentials belong in secure configuration such as environment variables or a secrets manager.

15. **What is the difference between a prompt template and a prompt response?**  
    A template is the reusable instruction structure; the response is the model output after the filled prompt is submitted.
