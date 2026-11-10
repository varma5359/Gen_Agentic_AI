# Day 01 — Interview Questions

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved topic:** Introduction to AI application development, GenAI and Agentic AI career roles, Python revision and development environment

These questions are written for college students, freshers and junior developer candidates. Understand the answer and practise explaining it in your own words.

---

# Section 1 — Core interview questions

## 1. What is software?

**Answer:**
- Software is a set of instructions that tells a computer how to perform tasks.
- A student management application, calculator and banking application are examples.
- Developers create, test and maintain software.

**Example:** A marks application accepts subject marks, calculates the total and displays the result.

**Follow-up:** What is the difference between software and hardware?

Hardware refers to the physical components of a computer. Software contains the instructions that run on the hardware.

## 2. What is an AI application?

**Answer:**
- An AI application is software that uses an AI model or technique to perform a task.
- It may classify information, make predictions, understand language or generate content.
- The application still needs normal software components such as input validation, APIs, error handling and a user interface.

**Example:** A document assistant that answers questions about uploaded documents.

**Follow-up:** Is every application an AI application?

No. A basic calculator can use fixed arithmetic rules without an AI model.

## 3. What is Artificial Intelligence?

**Answer:**
- Artificial Intelligence is a field of computer science focused on systems that perform tasks associated with human intelligence.
- Examples include language understanding, image recognition, pattern identification and decision support.
- AI is a broad field that includes multiple approaches.

**Follow-up:** Is Machine Learning the same as AI?

No. Machine Learning is one approach within the broader field of AI.

## 4. What is Generative AI?

**Answer:**
- Generative AI creates new content based on patterns learned from data and the instructions it receives.
- It can generate text, code, images, audio and other content.
- A text assistant that drafts an email is one example.

**Follow-up:** Does Generative AI always produce correct information?

No. Its output can be incorrect or unsupported, so applications need suitable validation and evaluation.

## 5. What is an LLM?

**Answer:**
- LLM stands for Large Language Model.
- It is a model designed to process and generate language.
- LLMs can support tasks such as question answering, summarization, rewriting and code generation.

**Example:** An application uses an LLM to explain a Python error in simple language.

**Follow-up:** Is Python an LLM?

No. Python is a programming language. An LLM is a trained model. Python code can communicate with an LLM service.

## 6. What is Agentic AI?

**Answer:**
- Agentic AI describes AI systems designed to work toward a goal through multiple steps.
- Such systems may select and use approved tools.
- They can observe tool results and continue a controlled workflow.
- Their permissions and stopping conditions must be designed carefully.

**Example:** A system reads a supplied sales file, calculates totals using Python and prepares a report draft.

**Follow-up:** Should an agent have unrestricted access to all company systems?

No. It should receive only the permissions needed for its task. Sensitive actions should require suitable approval.

## 7. What is the difference between Generative AI and Agentic AI?

**Answer:**
- Generative AI focuses on creating content.
- Agentic AI focuses on working toward a goal through actions and steps.
- An agentic system may use a Generative AI model as one component.
- The terms are related but not interchangeable.

**Example:** A chatbot generating an answer is a Generative AI use case. A workflow that reads a file, calls a calculation tool and prepares a report is an agentic use case.

**Follow-up:** Can an agent use an LLM?

Yes. An LLM can help an agent interpret requests, choose among permitted tools or generate a response.

## 8. What is Python?

**Answer:**
- Python is a general-purpose programming language.
- It has readable syntax and a large ecosystem of libraries.
- It is used in backend development, automation, data processing and AI applications.

**Follow-up:** Why is Python useful in GenAI development?

Python can handle application logic, API calls, input validation, document processing, database access and integration with AI libraries.

## 9. What is a development environment?

**Answer:**
- A development environment is the set of tools used to write, run and test software.
- In this pathway, the basic setup includes Python, VS Code, the Python extension, a project folder and a terminal.

**Follow-up:** Is VS Code the Python interpreter?

No. VS Code is a code editor. The Python interpreter executes Python code.

## 10. What is debugging?

**Answer:**
- Debugging is the process of finding and fixing problems in a program.
- A developer checks the input, variable values, conditions, code path and error messages.
- A good developer tries to isolate the smallest example that reproduces the issue.

**Follow-up:** What should you do when a program produces an unexpected output?

Check the input and intermediate values, read the error message, inspect the relevant condition and reproduce the problem with a small example.

---

# Section 2 — Difference-based questions

## 11. Difference between traditional software and an AI application

| Traditional software | AI application |
|---|---|
| Often follows explicitly programmed rules | Uses an AI model or technique for at least one task |
| May produce predictable results for the same input and state | Model outputs may vary depending on the model and settings |
| Example: fixed marks calculator | Example: learning assistant that generates explanations |

**Interview point:** AI applications still need normal software engineering.

## 12. Difference between Generative AI and Machine Learning

| Generative AI | Machine Learning |
|---|---|
| Focuses on generating new content | Focuses on learning patterns from data to perform tasks |
| Can generate text, images or code | Can classify, predict, cluster or generate content depending on the method |
| Often uses deep learning models | Includes multiple approaches, including non-deep-learning methods |

**Important:** Generative AI commonly uses Machine Learning and Deep Learning techniques. These terms are not competing categories.

## 13. Difference between a chatbot and an AI agent

| Chatbot | AI agent |
|---|---|
| Often responds to user messages | Works toward a defined goal |
| May only generate responses | May use tools and perform multiple steps |
| Can be stateless or maintain conversation history | Often uses state or execution context |
| Example: FAQ bot | Example: controlled workflow that reads data and prepares a report |

A chatbot can include agent capabilities. The labels depend on the actual system behavior.

## 14. Difference between Python and an LLM

| Python | LLM |
|---|---|
| Programming language | Trained machine learning model |
| Executes application instructions | Processes and generates language |
| Used to build application logic | Used as an AI capability inside an application |
| Example: validates a user's input | Example: generates a summary |

## 15. Difference between a code editor and a terminal

| Code editor | Terminal |
|---|---|
| Used to write and edit source code | Used to enter commands |
| Shows project files and code | Runs commands and programs |
| Example: VS Code editor | Example: integrated VS Code terminal |

---

# Section 3 — Practical implementation questions

## 16. How do you display a message in Python?

**Answer:**

Use the built-in `print()` function.

```python
print("Hello, Python!")
```

**Output:**

```text
Hello, Python!
```

**Explanation:**
- `print` is the function name.
- The text is passed as an argument.
- Python displays the text.

**Follow-up:** Is `Print()` the same as `print()`?

No. Python is case-sensitive.

## 17. How do you store a student's name in Python?

**Answer:**

```python
student_name = "Anu"
print(student_name)
```

**Output:**

```text
Anu
```

**Explanation:**
- `student_name` is the variable name.
- `=` assigns the value.
- The value is a string.

**Follow-up:** Can a variable name begin with a number?

No. A Python variable name cannot begin with a number.

## 18. How do you accept input from a user?

**Answer:**

```python
student_name = input("Enter your name: ")
print("Hello", student_name)
```

**Explanation:**
- `input()` displays a prompt and reads user input.
- The returned value is a string.
- `print()` displays the result.

**Follow-up:** What happens if the user enters 25?

The value is still returned as text, not as an integer.

## 19. How do you convert user input into an integer?

**Answer:**

```python
age_text = input("Enter age: ")
age = int(age_text)
print(age + 1)
```

**Explanation:**
- `input()` returns a string.
- `int()` converts valid whole-number text into an integer.
- The program adds one and displays the result.

**Follow-up:** What happens if the user enters "twenty"?

Python raises a ValueError because that text cannot be converted into an integer.

## 20. How do you check a value's data type?

**Answer:**

```python
mark = 85
print(type(mark))
```

**Output:**

```text
<class 'int'>
```

**Follow-up:** Name four common Python data types.

String, integer, float and Boolean.

## 21. How do you write a condition in Python?

**Answer:**

```python
mark = 75

if mark >= 40:
    print("Pass")
else:
    print("Fail")
```

**Explanation:**
- Python checks the condition.
- If it is true, the if block runs.
- Otherwise, the else block runs.
- Indentation identifies the blocks.

**Follow-up:** What is the difference between `=` and `==`?

`=` assigns a value. `==` compares two values.

## 22. How do you repeat a statement five times?

**Answer:**

```python
for number in range(5):
    print("Practice Python")
```

**Explanation:**
- `range(5)` produces five values.
- The loop body runs once for each value.
- The message is displayed five times.

**Follow-up:** Which values are produced by `range(1, 4)`?

1, 2 and 3. The stop value 4 is excluded.

## 23. How would you calculate a student's total marks?

**Answer:**

```python
python_marks = 80
math_marks = 75
english_marks = 90

total_marks = python_marks + math_marks + english_marks

print(total_marks)
```

**Output:**

```text
245
```

**Explanation:** Each mark is stored in a variable. The plus operator adds the values. The result is stored and displayed.

**Follow-up:** How would you calculate the average?

Divide the total by the number of subjects.

## 24. How do you run a Python file from the terminal?

**Answer:**
1. Open the project folder in the terminal.
2. Confirm the file name.
3. Run the appropriate command.

Example on many systems:

```bash
python day01_hello.py
```

Some systems use `python3` or `py`.

**Follow-up:** What should you check if the command is not recognized?

Check whether Python is installed, whether the correct command is used and whether Python is available through PATH.

---

# Section 4 — Scenario-based interview questions

## 25. Scenario: A college wants a student marks calculator. Should you use an LLM?

**Problem:** The college needs to add marks and calculate averages.

**Expected answer:**
- I would first understand the calculation rules.
- I would use normal Python arithmetic for the calculation.
- I would validate that the marks are within the permitted range.
- I would test boundary values such as 0 and the maximum mark.
- I would display the result clearly.

**Reasoning:** Addition and average calculations are deterministic tasks. An LLM is unnecessary for this core calculation.

**Practical considerations:** Validate input, handle invalid values and test the calculation.

## 26. Scenario: Students want to ask questions about Python concepts in natural language. What would you build?

**Expected answer:**
- I would build a learning assistant.
- The application would accept a student's question.
- A Python backend would validate the input.
- The backend would call an approved LLM service.
- The application would receive and display the response.
- I would explain that generated answers may need verification.
- I would protect API credentials and handle service errors.

**Reasoning:** Natural-language explanation is a suitable use case for a Generative AI model.

**Practical considerations:** User privacy, response quality, cost, latency and failure handling.

## 27. Scenario: A user asks an AI agent to delete old customer records. What controls are needed?

**Expected answer:**
- First verify the user's identity and permissions.
- Define exactly which records are in scope.
- Do not allow the model to execute arbitrary database commands.
- Use a narrowly defined tool with validated arguments.
- Show the proposed action to an authorized human.
- Require approval before deletion.
- Record the action and its result.
- Provide a recovery strategy where possible.

**Reasoning:** Deleting customer records is a sensitive and potentially destructive action.

**Practical considerations:** Authorization, audit logging, data retention rules, backups and human approval.

## 28. Scenario: Your Python program shows an unexpected result. How do you debug it?

**Expected answer:**
1. Reproduce the issue.
2. Check the input.
3. Inspect variable values.
4. Check data types.
5. Review conditions and loops.
6. Read the full error message.
7. Reduce the program to a small example.
8. Make one change at a time.
9. Run the test again.
10. Confirm that the fix does not break other cases.

**Reasoning:** A systematic approach is more reliable than changing many lines at once.

## 29. Scenario: Python works in one terminal but not in VS Code. What do you check?

**Expected answer:**
- Check the Python interpreter selected in VS Code.
- Check the terminal command.
- Check whether multiple Python installations exist.
- Check the project environment if one is configured.
- Reopen the terminal after changing environment settings.
- Run the version command in both terminals and compare.

**Reasoning:** VS Code and the external terminal may be using different Python installations.

---

# Section 5 — Troubleshooting questions

## 30. Why does `print(Hello)` fail?

**Answer:** Python treats Hello as a variable or name because it is not quoted. If the intention is to display text, use `print("Hello")`.

## 31. Why does `input()` return text even when a number is entered?

**Answer:** The `input()` function returns a string. Convert it with `int()` or `float()` when a numeric operation is required.

## 32. Why does `"10" + "20"` produce `"1020"`?

**Answer:** Both values are strings. The plus operator joins strings. Convert them to integers to perform numeric addition.

## 33. Why does Python report an indentation error?

**Answer:** Python uses indentation to identify code blocks. Check that statements inside conditions and loops are indented consistently.

## 34. Why does `if mark = 40` fail?

**Answer:** A condition needs a comparison expression. Use `==` to compare values. A single `=` is used for assignment.

## 35. Why is `Print()` different from `print()`?

**Answer:** Python is case-sensitive. The built-in function is named `print` using lowercase letters.

## 36. Why might `python --version` fail?

**Answer:** Python may not be installed, may not be available through PATH, or the operating system may use another command such as `py` or `python3`.

---

# Section 6 — Follow-up questions

Use these to practise extending your first answer.

1. Can an AI application work without an LLM?
2. Can a Generative AI application be built without an agent?
3. Why should an agent have limited permissions?
4. Why is input validation important?
5. What is the difference between a Python interpreter and a code editor?
6. Why does Python use indentation?
7. What is the difference between a string and an integer?
8. Why should a developer not use an LLM for every calculation?
9. What should an application do when an AI provider is unavailable?
10. How would you explain your Day 1 mini-project to an interviewer?

### Suggested way to answer follow-ups

- Listen to the complete question.
- Answer the exact point first.
- Give a short example.
- Mention a limitation if it matters.
- Do not pretend to know something you have not studied.
- It is acceptable to say, "I have not implemented that yet, but my understanding is..."

---

# Section 7 — Strong points to remember

- Software is a set of instructions used to perform tasks.
- AI is a broad field.
- Machine Learning is one approach within AI.
- Generative AI creates content.
- LLM means Large Language Model.
- Agentic AI systems work toward goals through controlled steps and may use tools.
- A chatbot is not automatically an agent.
- Python is a programming language, not an AI model.
- VS Code is a code editor.
- A terminal is used to enter commands.
- `print()` displays information.
- `input()` returns text.
- `type()` checks a value's type.
- `int()` and `float()` convert suitable values.
- `=` assigns; `==` compares.
- `if`, `elif` and `else` make decisions.
- Loops repeat code.
- Indentation defines Python code blocks.
- Debugging should be systematic.
- Use deterministic code for deterministic calculations.
- Give agents only the permissions they need.
- Validate and test AI-generated output.

---

# Short mock interview practice

**Interviewer:** Tell me about the project you completed today.

**Candidate:** "I created a small Python terminal application called AI Application Development Concept Explorer. It displays two choices, Generative AI and Agentic AI. It accepts the user's choice using input(), checks the value using if and elif conditions, and displays the corresponding explanation. I also tested invalid input using the else block."

**Interviewer:** Why did you compare the choice with quotation marks?

**Candidate:** "Because input() returns a string. Therefore, I compare the entered value with the string values '1' and '2'."

**Interviewer:** What would you improve later?

**Candidate:** "I could separate the explanation data from the menu logic, add more concepts and write automated tests. I would make those changes when the relevant topics have been taught."

**Interviewer:** Would you connect an LLM to this small application?

**Candidate:** "Not for the current requirement. The explanations are fixed and simple, so normal Python code is enough. An LLM may be useful in a later version if students need open-ended explanations."

---

**End of Day 1 interview preparation.**
