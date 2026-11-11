# Day 1 Interview Guide — AI Application Development, GenAI and Agentic AI Foundations

**Phase:** 1 — Python and Software Development Foundations  
**Level:** Beginner / Fresher  
**Approved topic:** Introduction to AI application development, GenAI and Agentic AI career roles, Python revision and development environment.

> **Practice rule:** Answer aloud before reading the suggested answer. Do not memorise sentences word for word. Learn the idea and explain it naturally.

## 1. Core concept questions

### Q1. What is the difference between AI, Machine Learning, Deep Learning and Generative AI?

**Suggested answer:** Artificial Intelligence is the broad field of building systems that perform tasks associated with intelligence. Machine Learning is an approach in which systems learn patterns from data. Deep Learning is a type of machine learning that uses neural networks with multiple layers. Generative AI focuses on generating content such as text, images, audio or code.

**Example:** A model that predicts whether a transaction is suspicious may be a classification system. A model that drafts a customer response is a Generative AI use case.

**Follow-up: Is every AI system Generative AI?** No. Classification, recommendation and forecasting systems may use AI without generating new content.

### Q2. What is an LLM?

**Suggested answer:** A Large Language Model is a model trained to process and generate language. An application can send it instructions and input, and receive generated text or structured output. The model does not automatically know private company data or have permission to access company systems. Those capabilities must be provided safely by the application.

**Follow-up: Does an LLM always give a correct answer?** No. It can produce incorrect or unsupported output. Applications need suitable context, validation, evaluation and user-facing limitations.

### Q3. What is the difference between an AI model and an AI application?

**Suggested answer:** A model performs a particular learned task, such as generating text or classifying an input. An application is the complete software that users operate. It handles the interface, input validation, business rules, model/API communication, data, error handling, security and output.

**Example:** A company FAQ assistant is an application. The LLM is one component; Python code handles the question, retrieves information, calls the model and displays the answer.

### Q4. What does a GenAI developer do?

**Suggested answer:** A GenAI developer builds software that uses generative models to solve a business problem. Responsibilities can include Python development, prompt design, API integration, document processing, retrieval, structured-output validation, testing, security, deployment and monitoring.

**Important:** Integrating an existing model into an application is not the same as training a foundation model from scratch. Describe your work accurately.

### Q5. What is Agentic AI?

**Suggested answer:** Agentic AI describes systems designed to work toward a goal through a sequence of decisions and actions. An agentic workflow may use an LLM, state or memory, tools, observations and rules that determine what happens next. It needs boundaries such as allowed tools, permissions, step limits and stopping conditions.

**Example:** An assistant checks order status through an approved read-only tool, summarises the result and asks a human before issuing a refund.

**Follow-up: Is every automated workflow an AI agent?** No. A fixed script can automate steps without model-driven selection or adaptation. The exact boundary depends on the system design.

### Q6. Why is Python important for GenAI development?

**Suggested answer:** Python is used to write application logic, process data, call APIs, validate responses, connect databases and build backend services. Understanding Python helps a developer debug and customise an application instead of depending entirely on a framework.

### Q7. What is the difference between a programming language, an editor and an interpreter?

**Suggested answer:** A programming language defines how instructions are written. A code editor helps a developer create and organise source files. The Python interpreter executes Python code. A terminal is where we run commands such as checking the Python version or executing a script.

### Q8. What is a variable?

**Suggested answer:** A variable is a name that refers to a value so the program can use it later.

~~~python
student_name = "Asha"
~~~

Here, student_name refers to the string value "Asha".

### Q9. What is the difference between = and == in Python?

**Suggested answer:** A single equals sign assigns a value to a variable. Double equals compares two values and produces a Boolean result.

~~~python
score = 75
print(score == 75)
~~~

Output: True.

### Q10. What does input() return? Why does it matter?

**Suggested answer:** input() returns a string. If the user types 25, the value is text until converted. For arithmetic, convert valid input with int() or float().

~~~python
age = int(input("Enter age: "))
print(age + 1)
~~~

If the user types non-numeric text, conversion raises ValueError. A robust application should handle that case.

## 2. Practical code-reading questions

### Q11. What is the output, and why?

~~~python
name = "Ravi"
days = 10
print("Hello", name)
print(days + 5)
print(type(name).__name__)
~~~

**Answer**

~~~text
Hello Ravi
15
str
~~~

The first line displays text and the value of name. The second performs integer addition. The third displays the type name of name, which is str.

### Q12. Why does this code produce an error?

~~~python
marks = input("Enter marks: ")
print(marks + 5)
~~~

**Answer:** input() returns a string, but the code attempts to add an integer. Convert valid input first:

~~~python
marks = int(input("Enter marks: "))
print(marks + 5)
~~~

For production-quality input handling, also handle invalid text and validate the allowed score range.

### Q13. What does this condition do?

~~~python
score = 65

if score >= 50:
    print("Pass")
else:
    print("Try again")
~~~

**Answer:** Python checks whether 65 is greater than or equal to 50. The condition is true, so it prints Pass. The else block is skipped.

### Q14. What is the difference between a syntax error and a logic error?

**Suggested answer:** A syntax error means Python cannot parse the code, for example a missing closing bracket. A logic error means the code runs but produces an incorrect result, for example using addition when multiplication was intended. A program can have logic errors without displaying an exception.

## 3. Scenario-based questions

### Q15. A user enters "twenty" when your program expects an age. What should happen?

**Suggested answer:** The application should not crash with an unexplained traceback. It should detect that the input cannot be converted to a number and show a useful message asking for a valid age. It should also validate sensible boundaries, such as rejecting a negative age. In Python, this can later be implemented using try/except ValueError.

### Q16. Your Python file works in VS Code but not in the terminal. How do you investigate?

**Suggested answer:**
1. Confirm the file was saved.
2. Confirm the terminal is in the folder containing the file.
3. Check the exact file name and extension.
4. Check which Python interpreter is active.
5. Run the file using the correct command: py, python or python3, depending on the system.
6. Read the full error message and reproduce the issue.

### Q17. A business asks you to build an AI assistant that answers questions from internal policy documents. What components might you need?

**Suggested answer:** I would clarify the business requirements and data permissions first. The application may need a user interface, Python backend, document ingestion, a retrieval system, an LLM integration, source references, authentication, input validation, logging, tests and deployment. The exact design depends on document formats, access rules, expected traffic and answer-quality requirements.

### Q18. Why should an agent not be allowed to perform every action without restrictions?

**Suggested answer:** An agent can choose an incorrect action, misinterpret tool output or encounter malicious instructions in untrusted content. Tool permissions should follow least privilege. Sensitive or irreversible actions should require explicit human approval. The workflow also needs timeouts, step limits, logging and a clear stop condition.

## 4. Difference-based revision

| Compare | Main difference |
|---|---|
| Model vs application | A model performs an AI task; an application delivers the complete user-facing workflow |
| Editor vs interpreter | Editor writes code; interpreter executes code |
| Terminal vs Python file | Terminal runs commands; Python file contains program instructions |
| = vs == | Assignment vs comparison |
| str vs int | Text vs whole number |
| Fixed automation vs agentic workflow | Predetermined steps vs goal-directed steps that may select actions based on state and observations |

## 5. Practical interview task

Without opening the class notes, create a file that:
1. Asks for a person's name.
2. Asks for a quiz score.
3. Converts the score into an integer.
4. Prints a greeting.
5. Prints Pass for a score of 50 or higher; otherwise prints Try again.

Then explain each line. Mention one input that could cause an error and how you would handle it.

## 6. How to give a strong fresher answer

Use this structure:

1. **Definition:** What is it?
2. **Purpose:** Why is it needed?
3. **Working:** What happens step by step?
4. **Example:** Where would you use it?
5. **Limitation:** What can go wrong?

Avoid weak answers:
- "AI means ChatGPT." This is too narrow.
- "Agentic AI means an AI that does everything automatically." This is unsafe and inaccurate.
- "Python is easy." This does not explain why it is useful.
- "The model knows all company information." Private information must be made available through authorised application design.
- "My project is production-ready" when it has not been secured, tested, deployed and monitored.

## 7. Self-evaluation rubric

| Skill | 0 — Not yet | 1 — With notes | 2 — Independently |
|---|---|---|---|
| Explain AI / GenAI / Agentic AI | Cannot explain | Explains with prompts | Gives clear examples and distinctions |
| Explain application architecture | Confuses model and app | Names some components | Explains request-to-response flow |
| Read Python basics | Cannot trace code | Traces with help | Predicts output correctly |
| Explain input and types | Does not know return type | Remembers conversion | Explains why conversion is needed |
| Debug a simple issue | Guesses | Uses error message with help | Reproduces, isolates and verifies a fix |

**Target:** At least 7 out of 10, with no zero in Python basics. If you score lower, repeat the relevant class-note sections and rebuild the small examples.
