# Day 01 — Introduction to AI Application Development, GenAI and Agentic AI Career Roles, Python Revision and Development Environment

**Pathway:** TechPhile.ai GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** AI Application Development Concept Explorer  
**Duration:** 2–3 hours  
**Audience:** College students, freshers and learners with 0–1 year of experience  
**Starting assumption:** You may be completely new to software development. No prior AI knowledge is required.

> Mentor's promise: we will not jump into complex AI frameworks today. First understand what an application is, what AI means, what a language model does, what an agent does and how to run a simple Python program.

## 1. What will you learn today?

By the end of this class, you should be able to:
1. Explain what software and an application are.
2. Explain input, processing and output.
3. Distinguish Artificial Intelligence, Machine Learning and Deep Learning.
4. Explain Generative AI using a simple example.
5. Explain what a Large Language Model is at a beginner level.
6. Explain the difference between a chatbot, workflow and AI agent.
7. Identify common entry-level GenAI and Agentic AI job roles.
8. Understand where Python fits into AI application development.
9. Check whether Python is installed.
10. Open VS Code, create a project folder and run a Python file.
11. Use variables, basic data types, input, output, conditions, loops and a simple function.
12. Explain the code you wrote instead of only copying it.

## 2. What is software?

Software is a set of instructions that tells a computer what work to perform.

Think about a college attendance application:
- A teacher opens the application.
- The teacher selects a class.
- The application displays student names.
- The teacher marks attendance.
- The application saves the result.
- A report can be displayed later.

The computer does not know what attendance means by itself. A developer writes instructions that make these steps happen.

### 2.1 Input, processing and output

Almost every beginner program can be understood using three words.

| Word | Simple meaning | Attendance example |
|---|---|---|
| Input | Information given to a program | Student ID |
| Processing | Work performed by the program | Find the student record |
| Output | Result produced | Student name and attendance |

A simple Python example:

```python
student_name = "Anu"
print(student_name)
```

Expected output:

```text
Anu
```

Line-by-line:
1. student_name is the variable name.
2. The equals sign assigns a value.
3. "Anu" is a string value because it is inside quotes.
4. print() displays the value.
5. The output is Anu.

Change the value to "Ravi" and run it again. The output changes because the stored value changed.

### 2.2 What is an application?

An application is software designed to help a user complete a task.

Examples:
- Banking application: view transactions and transfer money.
- Learning application: watch lessons and complete quizzes.
- Shopping application: browse products and place orders.
- Chat application: send and receive messages.
- AI assistant: ask a question and receive a generated response.

An application can have:
- A frontend: the screen that the user interacts with.
- A backend: the code that processes requests.
- A database: the place where structured information is stored.
- External services: APIs that provide additional capabilities.

Do not worry about implementing all these parts today. Learn the meaning first.

## 3. What is Artificial Intelligence?

Artificial Intelligence, usually shortened to AI, is a broad field of computer science focused on building systems that perform tasks associated with human intelligence.

Examples of tasks:
- Understanding language.
- Recognizing objects in images.
- Recommending a course.
- Detecting unusual transactions.
- Planning a route.
- Answering questions.

AI does not mean a computer has human feelings or human understanding. It means a system performs a task using algorithms, models, rules or learned patterns.

### 3.1 AI versus ordinary automation

Ordinary automation follows instructions written by a developer.

Example:

```python
marks = 75
if marks >= 40:
    print("Pass")
else:
    print("Fail")
```

Expected output:

```text
Pass
```

The developer wrote the rule: marks of 40 or more are a pass.

A machine-learning model is different. It learns patterns from examples. For example, a spam classifier can be trained using emails labelled spam or not spam.

Remember:
- A rule-based program follows explicitly written rules.
- A machine-learning model learns patterns from data.
- Both can be part of a larger AI application.

## 4. AI, Machine Learning and Deep Learning

These terms are related, but they do not mean exactly the same thing.

### 4.1 Artificial Intelligence

AI is the broad area.

Example: a system that helps a person choose a suitable route.

### 4.2 Machine Learning

Machine Learning (ML) is an approach where a model learns patterns from data.

Example: a model learns from historical student records to estimate whether a learner may need additional support. Such predictions must be evaluated carefully and should not be treated as unquestionable decisions.

### 4.3 Deep Learning

Deep Learning uses neural networks with multiple layers. It is useful for complex patterns in text, images, audio and other data.

### 4.4 Simple relationship

```text
Artificial Intelligence
    └── Machine Learning
            └── Deep Learning
```

This is a simplified learning diagram. It helps you remember the relationship; it is not a complete map of every AI technique.

### 4.5 Quick comparison

| Term | Beginner explanation | Example |
|---|---|---|
| AI | Broad field of intelligent computer systems | Route planning assistant |
| ML | Learns patterns from data | Spam classifier |
| Deep Learning | Uses multi-layer neural networks | Image recognition |

Interview answer:
"Artificial Intelligence is the broad field. Machine Learning is a way to build AI by learning patterns from data. Deep Learning is a type of machine learning that uses neural networks with multiple layers."

## 5. What is Generative AI?

Generative AI is a type of AI that can create new content.

It may generate:
- Text.
- Computer code.
- Images.
- Audio.
- Video.
- Summaries.
- Explanations.
- Draft documents.

Example: a student enters the prompt "Explain Python variables in simple words." A text-generating model can create an explanation.

A prompt is the instruction or input supplied to the model.

### 5.1 First prompt example — no API required

```python
prompt = "Explain Python variables in simple words."
print("Student question:")
print(prompt)
```

Expected output:

```text
Student question:
Explain Python variables in simple words.
```

This program only stores and displays a prompt. It does not call an AI model yet. That distinction is important.

### 5.2 What is an LLM?

LLM stands for Large Language Model.

A language model is trained to process and generate language. A developer can connect an LLM to an application using a provider's API.

A simplified application flow:

```text
Student enters a question
          |
          v
Python application receives it
          |
          v
Application sends a request to an LLM API
          |
          v
LLM generates a response
          |
          v
Python application displays the response
```

The model does not automatically know every current fact. It can generate incorrect information. Applications need validation, retrieval, testing and clear limitations.

## 6. What is Agentic AI?

Agentic AI refers to systems designed to pursue a goal through steps, decisions and tool use.

A simple chatbot may respond directly to a question.

An agent may:
1. Receive a goal.
2. Decide which step is needed.
3. Select an available tool.
4. Call the tool.
5. Observe the result.
6. Decide whether another step is needed.
7. Stop when the task is complete or a limit is reached.

Example: a college information assistant may search approved course notes, retrieve an academic calendar and prepare an answer with references.

### 6.1 Workflow versus agent

A workflow follows a predefined sequence.

An agent can choose between available actions based on the current task and observations.

A workflow is often easier to test and control. An agent may be useful when the next step depends on information discovered during execution.

Not every application needs an agent. Choose the simplest reliable approach.

### 6.2 Safety and human approval

An agent should not automatically perform every possible action.

For example:
- Searching public course information may be low risk.
- Sending an email needs permission.
- Deleting a student record is a sensitive action and needs strict authorization.
- Making a financial transaction needs strong controls and human approval.

The developer must define which tools the agent can use and what actions require approval.

## 7. GenAI Developer and Agentic AI Developer roles

A GenAI Developer builds applications that use language models and related services.

Typical responsibilities:
- Write Python application code.
- Connect to LLM APIs.
- Prepare prompts.
- Process documents.
- Build RAG applications.
- Validate model outputs.
- Develop backend APIs.
- Test and deploy applications.

An Agentic AI Developer additionally works on:
- Tool calling.
- Agent execution loops.
- Planning and task decomposition.
- State and memory.
- Workflow orchestration.
- Human approval.
- Multi-agent coordination.
- Monitoring and agent evaluation.

Possible entry-level role titles include:
- Junior GenAI Developer.
- Python GenAI Developer.
- LLM Application Developer.
- AI Application Developer.
- Junior AI Agent Developer.
- Junior Agentic AI Engineer.

These are possible target roles, not guaranteed placement outcomes. Employers may ask for different skills and experience.

## 8. Where does Python fit?

Python is the primary language in this pathway because it is widely used for application development, APIs, data processing and AI integrations.

You will use Python for:
- Variables and data structures.
- Functions and classes.
- File processing.
- API requests.
- Backend development with FastAPI.
- LLM API integration.
- Embeddings and RAG.
- Agent tools and workflows.
- Testing and automation.

Do not rush to LangChain or LangGraph before you understand Python functions, classes, API requests and error handling. Frameworks become easier when the underlying Python is clear.

## 9. Install and verify Python

First check whether Python is installed.

Windows terminal:

```powershell
py --version
```

You may also use:

```powershell
python --version
```

macOS or Linux terminal:

```bash
python3 --version
```

Expected output will look similar to:

```text
Python 3.x.x
```

The exact minor version depends on the installed release.

If the command is not found:
1. Confirm Python is installed.
2. Reopen the terminal after installation.
3. Try the platform-specific command.
4. Check that the interpreter is available on PATH.
5. In VS Code, select the installed Python interpreter.

## 10. Install and open VS Code

VS Code is a code editor. It helps you write and manage files.

Basic steps:
1. Install Visual Studio Code.
2. Open VS Code.
3. Open the Extensions view.
4. Search for the official Python extension.
5. Install it.
6. Open a folder for today's project.
7. Create a file named main.py.
8. Save the file.
9. Open the integrated terminal.
10. Run the program using the Python command available on your system.

The editor does not replace Python. VS Code helps you edit; the Python interpreter executes the code.

## 11. Your first Python program

Create a file named main.py.

```python
print("Hello, Python!")
print("Welcome to TechPhile.ai")
```

Expected output:

```text
Hello, Python!
Welcome to TechPhile.ai
```

Explanation:
- print is a built-in Python function.
- Parentheses contain the value to display.
- Text is written inside quotes.
- Each print call displays a line.

Run from the terminal:

```bash
python main.py
```

On systems where the command is python3:

```bash
python3 main.py
```

## 12. Variables

A variable is a name that refers to a value.

```python
student_name = "Anu"
course_name = "GenAI"
duration_days = 70

print(student_name)
print(course_name)
print(duration_days)
```

Expected output:

```text
Anu
GenAI
70
```

Walkthrough:
1. student_name is the variable name.
2. = assigns the value.
3. "Anu" is a string.
4. course_name stores another string.
5. duration_days stores an integer.
6. print displays each value.

Variable naming rules:
- Use letters, digits and underscores.
- Do not start a variable name with a digit.
- Do not use Python reserved keywords.
- Prefer meaningful names.
- Python variable names are case-sensitive.

Good names: student_name, total_marks, course_duration.

Poor names: a, x1, temp2 when the purpose is unclear.

## 13. Basic Python data types

### 13.1 String

A string stores text.

```python
name = "Anu"
print(type(name))
```

### 13.2 Integer

An integer stores a whole number.

```python
age = 20
print(type(age))
```

### 13.3 Float

A float stores a decimal number.

```python
percentage = 87.5
print(type(percentage))
```

### 13.4 Boolean

A Boolean stores True or False.

```python
is_enrolled = True
print(type(is_enrolled))
```

### 13.5 Check the type

```python
name = "Anu"
age = 20
percentage = 87.5
is_active = True

print(type(name).__name__)
print(type(age).__name__)
print(type(percentage).__name__)
print(type(is_active).__name__)
```

Expected output:

```text
str
int
float
bool
```

## 14. Taking input from the user

input() displays a prompt and waits for the user to type text.

```python
name = input("Enter your name: ")
print("Welcome", name)
```

Example interaction:

```text
Enter your name: Anu
Welcome Anu
```

Important: input() returns a string, even when the user types digits.

Convert numeric input:

```python
age_text = input("Enter your age: ")
age = int(age_text)
print(age + 1)
```

If the user enters 20, the output is 21.

If the user enters twenty, int() raises ValueError. You will learn to handle this safely in later lessons.

## 15. Operators

Operators perform operations on values.

| Operator | Meaning | Example |
|---|---|---|
| + | Addition | 10 + 5 |
| - | Subtraction | 10 - 5 |
| * | Multiplication | 10 * 5 |
| / | Division | 10 / 5 |
| // | Floor division | 11 // 2 |
| % | Remainder | 11 % 2 |
| ** | Power | 2 ** 3 |
| == | Equal comparison | 10 == 10 |
| != | Not equal | 10 != 5 |
| > | Greater than | 10 > 5 |
| < | Less than | 5 < 10 |

Try:

```python
first = 10
second = 5
print(first + second)
print(first - second)
print(first * second)
print(first / second)
```

Expected output:

```text
15
5
50
2.0
```

## 16. Conditions

Conditions allow the program to choose what to do.

```python
marks = 75

if marks >= 40:
    print("Pass")
else:
    print("Needs improvement")
```

Expected output:

```text
Pass
```

Line-by-line:
1. marks stores 75.
2. if begins a condition.
3. >= means greater than or equal to.
4. The condition 75 >= 40 is True.
5. The indented print statement runs.
6. else is skipped because the if condition was true.

Try marks = 30 and predict the output.

## 17. Loops

A loop repeats instructions.

```python
for day in range(1, 4):
    print("Practice day", day)
```

Expected output:

```text
Practice day 1
Practice day 2
Practice day 3
```

range(1, 4) produces 1, 2 and 3. The stop value 4 is not included.

## 18. Functions — first look

A function is a reusable block of code.

```python
def greet(name):
    return "Hello " + name

message = greet("Anu")
print(message)
```

Expected output:

```text
Hello Anu
```

Explanation:
- def starts the function definition.
- greet is the function name.
- name is a parameter.
- "Anu" is the argument supplied during the call.
- return sends the result back.
- message stores the returned string.

You will learn functions deeply on Day 3.

## 19. Python development environment: common problems

### Problem: Python command not found

Try the correct command for your operating system. Check installation and PATH.

### Problem: No module named package

The package may be installed in a different environment. Check the interpreter selected in VS Code and install the package using that interpreter.

### Problem: File not found

Check the current working directory and file name. Confirm that the file was saved.

### Problem: IndentationError

Python uses indentation to identify code blocks. Align statements correctly.

### Problem: SyntaxError

Check quotes, parentheses, colons and spelling.

### Problem: Program runs but shows no output

Check whether the function was called and whether print or another output operation was used.

## 20. Mini-project — AI Application Development Concept Explorer

### Project goal

Create a beginner console program that introduces a student to AI application development concepts.

### Version 1 — display a welcome message

```python
print("AI Application Development Concept Explorer")
print("Learn Python, GenAI and Agentic AI step by step.")
```

### Version 2 — collect learner details

```python
student_name = input("Enter your name: ")
course = input("Which course are you learning? ")

print("Welcome", student_name)
print("Your course is", course)
```

### Version 3 — show the learning pathway

```python
student_name = input("Enter your name: ")

topics = [
    "Python Foundations",
    "Generative AI",
    "LLM Applications",
    "RAG Engineering",
    "Agentic AI"
]

print("Welcome", student_name)
print("Your learning topics:")

for topic in topics:
    print("-", topic)
```

### Version 4 — add a simple function

```python
def show_welcome(name):
    return f"Welcome to TechPhile.ai, {name}"

student_name = input("Enter your name: ")
print(show_welcome(student_name))
```

### Expected learning result

The student should be able to explain:
- Why a list is used for topics.
- Why a for loop is used to display them.
- Why a function is useful for the welcome message.
- How input() receives a name.
- How print() displays the result.

## 21. Day 1 practice exercises

1. Print your name, college and department.
2. Create variables for course name and course duration.
3. Display the type of each variable.
4. Ask the user for their name.
5. Ask for two numbers and display their sum.
6. Check whether marks are greater than or equal to 40.
7. Use a for loop to display five learning topics.
8. Write a function that returns a welcome message.
9. Change one input and predict the output before running.
10. Explain the difference between AI, ML and Deep Learning.
11. Explain Generative AI with one example.
12. Explain the difference between a workflow and an agent.
13. Check the installed Python version.
14. Create and run main.py from VS Code.
15. Describe input, processing and output in your mini-project.

## 22. Day 1 interview questions with beginner answers

**Q1. What is Python?**  
Python is a high-level programming language used to build applications, automate tasks, process data and develop AI solutions.

**Q2. What is a variable?**  
A variable is a name that refers to a value stored or used by a program.

**Q3. What is a data type?**  
A data type describes the kind of value, such as text, an integer, a decimal number or True/False.

**Q4. What is the difference between AI and ML?**  
AI is the broad field. ML is an approach within AI where a model learns patterns from data.

**Q5. What is Generative AI?**  
Generative AI creates new content such as text, code, images or audio.

**Q6. What is an LLM?**  
An LLM is a Large Language Model designed to process and generate language.

**Q7. What is an AI agent?**  
An AI agent is a system that can use a model and tools to take steps toward a goal, within defined limits.

**Q8. Why is Python used in AI development?**  
Python has a large ecosystem for application development, data processing, machine learning and AI integrations.

**Q9. What does input() do?**  
It asks the user for input and returns the entered text as a string.

**Q10. What does print() do?**  
It displays information in the output.

**Q11. What is a function?**  
A function is a reusable block of code that performs a task.

**Q12. What is debugging?**  
Debugging is the process of finding and fixing the cause of a program problem.

## 23. Day 1 quiz

1. Which data type stores text?
2. What does input() return?
3. Which statement is used for a decision?
4. Which loop can process each item in a list?
5. What is the purpose of a function?
6. What does AI stand for?
7. What is the full form of LLM?
8. Does every chatbot need to be an agent?
9. Which tool executes Python code?
10. Why should API keys not be committed to a public repository?

## 24. Trainer assessment

| Assessment | Evidence |
|---|---|
| AI terminology | Student explains AI, ML, Deep Learning and GenAI |
| Agent understanding | Student explains workflow versus agent |
| Python basics | Student writes variables, conditions, loops and a function |
| Environment | Student runs main.py |
| Project | Student demonstrates the Concept Explorer |
| Interview | Student answers beginner questions in their own words |

## 25. Day 1 completion checklist

- [ ] I can explain what an application is.
- [ ] I can explain input, processing and output.
- [ ] I can distinguish AI, ML and Deep Learning.
- [ ] I can explain Generative AI and LLM.
- [ ] I can explain an AI agent at a beginner level.
- [ ] I know why Python is used in this pathway.
- [ ] I can check the Python version.
- [ ] I can create and run a Python file.
- [ ] I can use variables and basic data types.
- [ ] I can use input and print.
- [ ] I can write a simple condition and loop.
- [ ] I can define and call a function.
- [ ] I completed the mini-project.
- [ ] I can answer the interview questions.

**Day 1 is complete when you can explain and demonstrate the work yourself. Copying code without understanding it is not completion.**
