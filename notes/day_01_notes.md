# Day 01 — Start Building Software: Python, AI Applications and Your Development Setup

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** AI Application Development Concept Explorer  
**Time:** 2–3 hours  
**Level:** Absolute beginner  
**Prerequisites:** None. Start here even if you have never written code.

> **How to study:** Keep this file open beside VS Code. Type every code example yourself. Before running it, predict what it will display. Then run it, compare the output and explain the result aloud. Do not skip the practice tasks.

---

## 1. Your finish line for today

By the end of this lesson, you will be able to:

- Explain what software, an application, AI, Generative AI, an LLM and an AI agent mean.
- Describe how input becomes processing and then output.
- Explain where Python is used when building an AI application.
- Check whether Python is installed and run a `.py` file in VS Code.
- Create variables and use strings, integers, floats and Boolean values.
- Read user input and convert text into a number.
- Use `print()`, `input()`, `type()` and `int()`.
- Write a simple `if/else` decision, a `for` loop and a function.
- Build and run the approved mini-project without copying a finished answer blindly.

## 2. First understand what you are building toward

### 2.1 What is software?

Software is a set of instructions that tells a computer how to perform a task.

Example: a college attendance application lets a teacher choose a class, mark students present or absent, save the records and display a report. A developer writes the instructions that make those actions happen.

### 2.2 The three parts of a simple program

| Part | Meaning | College attendance example |
|---|---|---|
| Input | Information given to the program | Student name |
| Processing | Work the program performs | Check the attendance record |
| Output | Result shown by the program | Present / Absent |

**Flow**

```text
User enters information
        |
        v
Python program processes it
        |
        v
Program displays a result
```

Try this first program:

```python
student_name = "Anu"
print(student_name)
```

Expected output:

```text
Anu
```

Explanation:

1. `student_name` is the variable name.
2. `=` assigns the value on its right to the variable on its left.
3. `"Anu"` is text. In Python, text is called a string.
4. `print()` displays a value in the terminal.
5. The output is `Anu`.

Change `"Anu"` to your own name and run the program again.

### 2.3 What is an application?

An application is software created to help a user complete a task.

| Application | Task it helps with |
|---|---|
| Banking app | View balance and transactions |
| Learning app | Study lessons and take quizzes |
| Shopping app | Search products and place orders |
| Chat app | Send and receive messages |
| AI assistant | Ask a question and receive a generated response |

A typical application may contain a **frontend** (the screen), a **backend** (the code that handles work), a **database** (where information is stored) and external services (other systems accessed through APIs). You will learn how these parts connect later in this course.

## 3. AI and Generative AI — the beginner explanation

### 3.1 Artificial Intelligence (AI)

AI is a field of computing focused on making computer systems perform tasks that normally require abilities such as recognising patterns, understanding language or making predictions.

Examples:
- An email system identifying likely spam.
- A map suggesting a route.
- A photo app recognising objects.
- An assistant responding to a question.

AI is not magic and does not guarantee a correct answer. It is software built using rules, data, models and algorithms.

### 3.2 AI, Machine Learning and Deep Learning

| Term | Beginner meaning | Example |
|---|---|---|
| Artificial Intelligence | Broad field of building systems that perform intelligent tasks | A route-planning system |
| Machine Learning (ML) | A system learns patterns from examples/data | Spam detection trained on labelled emails |
| Deep Learning (DL) | Machine learning using neural networks with multiple layers | Recognising objects in images |

A useful way to remember the relationship:

```text
Artificial Intelligence
└── Machine Learning
    └── Deep Learning
```

This is a simplified relationship: deep learning is a type of machine learning, and machine learning is one approach within AI.

### 3.3 What is Generative AI?

Generative AI is AI that can create new content based on patterns learned during training.

It can generate:
- Text — explanations, summaries and emails.
- Code — example programs and code suggestions.
- Images — illustrations and designs.
- Audio — speech and music.
- Other structured content — for example, a JSON response.

Example: you provide the instruction, "Explain Python variables to a beginner." A text-generation model can produce an explanation.

### 3.4 What is an LLM?

LLM means **Large Language Model**. It is a model trained on large amounts of text so it can process and generate language.

Beginner example:

- You send: "Explain a Python list."
- The model processes the prompt.
- The model generates a response.
- Your application displays the response.

The instruction you send is called a **prompt**. The generated response is called the **output**.

Important: an LLM can produce incorrect or invented information. Developers must test outputs and design safeguards. Never assume that every generated answer is true.

### 3.5 Chatbot, workflow and AI agent are not identical

| Type | How it works | Example |
|---|---|---|
| Basic chatbot | Responds to a user's messages | Answers a course FAQ |
| Workflow | Follows a sequence designed by a developer | Receive a question → search FAQs → format an answer |
| AI agent | Uses a model to choose from permitted actions, observes results and continues toward a goal | Checks an order status using an approved order lookup tool |

Simple flow:

```text
Chatbot: User message -> Response

Workflow: Step 1 -> Step 2 -> Step 3 -> Result

Agent: Goal -> Choose permitted action -> Observe result
                    ^                         |
                    |------ continue ----------|
```

An agent must have boundaries: allowed tools, permissions, limits and a way to stop. An agent should not be allowed to perform every action without control.

## 4. Where Python fits into an AI application

Python is a programming language. Developers use it to write the instructions that connect application parts.

A simplified AI application flow:

```text
Student types a question
          |
          v
Frontend collects the question
          |
          v
Python backend receives it
          |
          v
Python sends a request to an LLM API
          |
          v
LLM returns a response
          |
          v
Python sends the response to the frontend
          |
          v
Student sees the answer
```

You do not need to build all these parts today. First learn the Python building blocks. Later phases will connect them.

## 5. Prepare your computer

### 5.1 What you need

| Tool | Why you need it |
|---|---|
| Python 3 | Runs Python programs |
| Visual Studio Code (VS Code) | Editor where you write code |
| Python extension for VS Code | Adds Python language support and run/debug features |
| Terminal | Where you run commands and see program output |

Install Python 3 from the official Python website and VS Code from the official Visual Studio Code website. In VS Code, open **Extensions**, search for **Python** by Microsoft and install it.

### 5.2 Check whether Python is installed

Open a terminal:

- **Windows:** open PowerShell or the VS Code terminal.
- **macOS/Linux:** open Terminal or the VS Code terminal.

Try the command for your operating system:

```bash
python --version
```

If Windows does not recognise `python`, try:

```bash
py --version
```

On macOS/Linux, try:

```bash
python3 --version
```

A successful result looks similar to:

```text
Python 3.x.x
```

The exact minor version may differ. If every command says Python was not found, install Python 3 and reopen the terminal. On Windows, during installation, select the option to add Python to PATH if the installer offers it.

### 5.3 Create your first project folder

Create a folder named:

```text
techphile_day01
```

Open VS Code → **File** → **Open Folder** → select `techphile_day01`.

Inside VS Code:

1. Select **New File**.
2. Name it `hello.py`.
3. Type the code below.
4. Save the file.

```python
print("Hello, TechPhile!")
print("I am learning Python.")
```

Run it from the VS Code terminal:

**Windows**
```bash
py hello.py
```

If `py` is not available but `python` works:
```bash
python hello.py
```

**macOS/Linux**
```bash
python3 hello.py
```

Expected output:

```text
Hello, TechPhile!
I am learning Python.
```

**What just happened?** You created a file containing Python instructions. The Python interpreter read the file and executed the instructions from top to bottom.

### 5.4 Understand the file extension

- `.py` means a Python source file.
- `.md` means a Markdown notes file.
- `.json` means a JSON data file.

For now, save Python code in files ending with `.py`.

## 6. Python building blocks — learn them one at a time

### 6.1 `print()` — display information

| Item | Explanation |
|---|---|
| Meaning | Displays information in the output/terminal |
| Why use it? | To show a message or inspect a value while learning/debugging |
| Syntax | `print(value)` |
| Argument | The value you want to display |
| Return value | `None`; it displays text rather than returning the displayed text |
| Changes original data? | No |

Example:

```python
print("Welcome")
print(25)
print(10 + 5)
```

Output:

```text
Welcome
25
15
```

You can pass more than one value:

```python
name = "Anu"
course = "Python"
print("Student:", name, "| Course:", course)
```

Output:

```text
Student: Anu | Course: Python
```

Common mistake: writing `Print("Hello")`. Python is case-sensitive; use lowercase `print`.

### 6.2 Variables — give a value a name

A variable is a name that refers to a value.

```python
student_name = "Ravi"
age = 20
course_fee = 4999.50
is_enrolled = True

print(student_name)
print(age)
print(course_fee)
print(is_enrolled)
```

Output:

```text
Ravi
20
4999.5
True
```

Variable naming rules:

- Use meaningful names: `student_name` is clearer than `x`.
- A name may contain letters, numbers and underscores.
- A name cannot begin with a number.
- Do not use spaces: write `student_name`, not `student name`.
- Python distinguishes uppercase and lowercase: `age` and `Age` are different names.

### 6.3 Basic data types

A data type tells Python what kind of value is stored.

| Type | Meaning | Example |
|---|---|---|
| `str` | Text | `"Python"` |
| `int` | Whole number | `25` |
| `float` | Decimal number | `75.5` |
| `bool` | True or False | `True` |

Check a value's type with `type()`.

| Item | Explanation |
|---|---|
| Meaning | Returns the type/class of a value |
| Syntax | `type(value)` |
| Argument | The value to inspect |
| Return value | A type object, such as `<class 'int'>` |
| Changes original data? | No |

Example:

```python
student_name = "Ravi"
marks = 85
percentage = 85.5
is_passed = True

print(type(student_name))
print(type(marks))
print(type(percentage))
print(type(is_passed))
```

Output:

```text
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
```

### 6.4 `input()` — receive information from a user

| Item | Explanation |
|---|---|
| Meaning | Waits for the user to type something |
| Syntax | `input(prompt)` |
| Argument | Optional message shown before the user types |
| Return value | Always a string (`str`) |
| Changes original data? | No; it returns the entered text |

Example:

```python
name = input("Enter your name: ")
print("Welcome,", name)
```

Sample run:

```text
Enter your name: Anu
Welcome, Anu
```

**Important beginner rule:** even if the user types `20`, `input()` returns the text `"20"`, not the integer `20`.

### 6.5 Convert input using `int()` and `float()`

Use `int()` to convert suitable text into a whole number. Use `float()` to convert suitable text into a decimal number.

| Function | Purpose | Example |
|---|---|---|
| `int(value)` | Convert to integer | `int("20")` → `20` |
| `float(value)` | Convert to decimal number | `float("20.5")` → `20.5` |
| `str(value)` | Convert to text | `str(20)` → `"20"` |

Example:

```python
age_text = input("Enter your age: ")
age = int(age_text)

print("Next year you will be", age + 1)
```

Sample run:

```text
Enter your age: 20
Next year you will be 21
```

Why convert? Without conversion, `"20"` is text. Python cannot use it as a number in every calculation.

Common error:

```python
age = int(input("Enter age: "))
```

If the user types `twenty`, Python raises `ValueError` because that text cannot be converted into an integer. You will learn safe error handling on Day 5. For today, enter a valid whole number.

### 6.6 Basic operators

| Operator | Meaning | Example | Result |
|---|---|---|---:|
| `+` | Add | `10 + 5` | 15 |
| `-` | Subtract | `10 - 5` | 5 |
| `*` | Multiply | `10 * 5` | 50 |
| `/` | Divide | `10 / 5` | 2.0 |
| `%` | Remainder | `10 % 3` | 1 |
| `==` | Equal comparison | `10 == 10` | True |
| `>=` | Greater than or equal | `10 >= 5` | True |

Do not confuse `=` and `==`:

- `=` assigns a value: `marks = 80`.
- `==` compares two values: `marks == 80`.

### 6.7 Conditions — let the program make a simple decision

A condition chooses which code should run.

```python
marks = 72

if marks >= 40:
    print("Pass")
else:
    print("Fail")
```

Output:

```text
Pass
```

Line-by-line:

1. `marks = 72` stores the number 72.
2. `if marks >= 40:` checks whether marks are at least 40.
3. The indented line runs when the condition is True.
4. `else:` means "otherwise".
5. The indented line under `else` runs when the condition is False.

Python uses indentation (spaces at the start of a line) to identify a code block. Keep the indentation consistent.

Try changing `marks` to `25`. The output becomes `Fail`.

### 6.8 Loops — repeat instructions

A `for` loop repeats a block for each item in a sequence.

```python
topics = ["Python", "APIs", "LLMs"]

for topic in topics:
    print(topic)
```

Output:

```text
Python
APIs
LLMs
```

Understand the parts:

- `topics` is a list of three text values. You will study lists properly on Day 2.
- `for` starts the loop.
- `topic` receives one item at a time.
- `in topics` tells Python which collection to visit.
- The indented `print(topic)` runs once for each item.

A loop is useful when you need to process many messages, documents or records without writing the same instruction repeatedly.

### 6.9 Functions — create reusable instructions

A function is a named block of code that performs a task. You define it once and call it when you need it.

```python
def welcome_student(name):
    message = "Welcome, " + name
    return message

result = welcome_student("Anu")
print(result)
```

Output:

```text
Welcome, Anu
```

| Code part | Meaning |
|---|---|
| `def` | Starts a function definition |
| `welcome_student` | Function name |
| `name` | Parameter — a named input placeholder |
| `"Anu"` | Argument — the actual value passed in the call |
| `return message` | Sends a result back to the caller |
| `result = ...` | Stores the returned value |

**Return vs print:**

```python
def add(a, b):
    return a + b

answer = add(3, 4)
print(answer)
```

Output: `7`.

- `return` sends a value back so the program can use it.
- `print()` only displays a value.
- A function that reaches its end without a `return` statement returns `None`.

You will study functions in depth on Day 3. Today, understand the basic idea.

## 7. Guided mini-project — AI Application Development Concept Explorer

### 7.1 What are we building?

A small terminal program that welcomes a learner, displays the main concepts in this career pathway and checks whether the learner is ready to continue.

**What the program will do**

1. Ask for the learner's name.
2. Display a welcome message.
3. Show a list of concepts.
4. Ask the learner to enter their current Python experience level.
5. Display a suitable message.

### 7.2 Create the project file

Inside your `techphile_day01` folder, create:

```text
techphile_day01/
└── concept_explorer.py
```

### 7.3 Type the complete code

```python
def show_learning_topics():
    topics = [
        "Python programming",
        "Generative AI",
        "Large Language Models",
        "Prompt Engineering",
        "AI Agents"
    ]

    print("\nTopics in this career pathway:")

    for topic in topics:
        print("-", topic)


def recommend_next_step(level):
    if level == "beginner":
        return "Start with Python basics. You are in the right place!"
    elif level == "some":
        return "Revise Python basics and practise every example."
    else:
        return "Enter beginner or some."


def main():
    print("================================")
    print("TECHPHILE AI CONCEPT EXPLORER")
    print("================================")

    student_name = input("Enter your name: ").strip()

    if student_name == "":
        student_name = "Learner"

    print("\nWelcome,", student_name)

    show_learning_topics()

    print("\nChoose your Python experience:")
    print("1. beginner")
    print("2. some")

    level = input("Enter beginner or some: ").strip().lower()
    advice = recommend_next_step(level)

    print("\nYour learning guidance:")
    print(advice)
    print("\nKeep practising. Type every example yourself!")


main()
```

### 7.4 Run the project

Open the terminal inside the project folder.

**Windows**
```bash
py concept_explorer.py
```

**macOS/Linux**
```bash
python3 concept_explorer.py
```

### 7.5 Sample run

```text
================================
TECHPHILE AI CONCEPT EXPLORER
================================
Enter your name: Anu

Welcome, Anu

Topics in this career pathway:
- Python programming
- Generative AI
- Large Language Models
- Prompt Engineering
- AI Agents

Choose your Python experience:
1. beginner
2. some
Enter beginner or some: beginner

Your learning guidance:
Start with Python basics. You are in the right place!

Keep practising. Type every example yourself!
```

### 7.6 Understand the project — line by line by component

**Function 1: `show_learning_topics()`**

- `def` defines the function.
- `topics` is a list of strings.
- `print()` displays the heading.
- The `for` loop visits each topic.
- `topic` contains the current item during each loop.
- The function has no explicit `return`; it returns `None` after displaying the topics.

**Function 2: `recommend_next_step(level)`**

- `level` is a parameter.
- `if` checks whether the value is `"beginner"`.
- `elif` checks another possible value if the first condition is false.
- `else` handles every other value.
- Each branch returns a text message.
- The function does not print the message; it returns it to the caller.

**Function 3: `main()`**

- Holds the main sequence of the application.
- `input()` collects the learner's name.
- `.strip()` removes spaces from the beginning and end of the entered text.
- The condition checks whether the name is empty.
- `show_learning_topics()` calls the first function.
- `.lower()` converts the entered level to lowercase.
- `recommend_next_step(level)` returns advice.
- `print(advice)` displays the returned message.

**Last line: `main()`**

Defining a function does not automatically run it. The final line calls `main()`, so the program starts.

### 7.7 Important methods used in this project

| Method | Meaning | Example | Result |
|---|---|---|---|
| `strip()` | Removes whitespace at the start and end of a string | `" Anu ".strip()` | `"Anu"` |
| `lower()` | Returns a lowercase copy of a string | `"BEGINNER".lower()` | `"beginner"` |

Both methods return a new string. Strings are immutable: these methods do not change the original string in place.

### 7.8 Test the project with these inputs

| Test | Name | Experience | Expected behaviour |
|---|---|---|---|
| 1 | Anu | beginner | Shows the beginner guidance |
| 2 | Ravi | some | Shows the revision guidance |
| 3 | Leave name empty | beginner | Uses the name Learner |
| 4 | Priya | advanced | Explains the accepted choices |

For Test 4, the program displays `Enter beginner or some.` This is intentional for today's basic version. You will improve input validation in a later exercise.

### 7.9 Common problems and fixes

| Problem | Why it happens | Fix |
|---|---|---|
| `python` is not recognised | Python is not installed or is not on PATH | Try `py` on Windows or `python3` on macOS/Linux; install Python if needed |
| `can't open file` | Terminal is in a different folder or filename is wrong | Open the correct folder and check the filename |
| `IndentationError` | Lines inside a function, loop or condition are not indented correctly | Use four spaces for each indentation level |
| `NameError` | A variable/function name is misspelled or used before it is defined | Compare spelling and capitalisation |
| Program shows nothing | The function was defined but never called | Check that the final line calls `main()` |
| Output differs | Input differs or code was changed | Compare your code and input with the sample run |

**Debugging habit:** read the final line of the error message first, note the file and line number, inspect that line and the few lines above it, then fix one issue and run again.

## 8. Independent practice — try before viewing the solutions

### Task 1 — personal introduction

Write a program that stores your name, city and course in variables and prints all three.

### Task 2 — age calculator

Ask the user for their age and display their age next year. Convert the input to an integer first.

### Task 3 — pass or fail

Ask for marks. Display `Pass` if marks are at least 40; otherwise display `Fail`.

### Task 4 — display course topics

Create a list containing three topics and use a `for` loop to display each topic.

### Task 5 — reusable greeting

Write a function named `make_greeting(name)` that returns `"Hello, "` followed by the name. Call it and print the returned value.

### Task 6 — explain the difference

In your own words, explain the difference between `print()` and `return`.

### Practice solutions

**Task 1**

```python
name = "Anu"
city = "Hyderabad"
course = "GenAI"

print("Name:", name)
print("City:", city)
print("Course:", course)
```

**Task 2**

```python
age = int(input("Enter your age: "))
print("Next year:", age + 1)
```

**Task 3**

```python
marks = int(input("Enter marks: "))

if marks >= 40:
    print("Pass")
else:
    print("Fail")
```

**Task 4**

```python
topics = ["Python", "APIs", "LLMs"]

for topic in topics:
    print(topic)
```

**Task 5**

```python
def make_greeting(name):
    return "Hello, " + name

message = make_greeting("Anu")
print(message)
```

**Task 6 — sample answer**

`print()` displays information on the screen. `return` sends a value from a function back to the code that called it, so the program can store or use that value.

## 9. Knowledge check

Try answering without looking back. Answers follow each question so you can check your understanding.

1. What are input, processing and output?
2. What is the difference between software and an application?
3. What does AI stand for?
4. How are AI, ML and DL related?
5. What does Generative AI create?
6. What is an LLM?
7. What is a prompt?
8. Is every chatbot an AI agent? Explain.
9. Why is Python useful in AI applications?
10. What does `print()` do?
11. What is a variable?
12. Name four basic Python data types.
13. What does `input()` return?
14. Why do we use `int()`?
15. What is the difference between `=` and `==`?
16. What does an `if/else` statement do?
17. Why do we use a loop?
18. What is a function?
19. What is the difference between a parameter and an argument?
20. What is the difference between `print` and `return`?

### Answers

1. Input is supplied information, processing is the work, and output is the result.
2. Software is a set of instructions; an application is software designed for a user task.
3. Artificial Intelligence.
4. ML is one approach within AI; DL is a type of ML using multi-layer neural networks.
5. New content such as text, code, images or audio.
6. Large Language Model, a model that processes and generates language.
7. The instruction or input sent to a model.
8. No. A chatbot may only respond; an agent can choose from permitted actions and use tools.
9. Python is used to write application logic, process data and connect APIs and AI services.
10. It displays information.
11. A name that refers to a value.
12. `str`, `int`, `float`, `bool`.
13. A string.
14. To convert suitable input text into an integer for numeric work.
15. `=` assigns; `==` compares.
16. It chooses which code block runs based on a condition.
17. To repeat work without writing the same instruction many times.
18. A named reusable block of code.
19. A parameter is the named placeholder in the definition; an argument is the actual value passed in a call.
20. `print` displays; `return` sends a value back from a function.

## 10. Day 01 completion checklist

Do not mark this day complete until you can do these tasks yourself:

- [ ] Explain software, applications, AI, Generative AI, LLMs and agents in simple words.
- [ ] Check your Python version.
- [ ] Create and run `hello.py` from the terminal.
- [ ] Explain strings, integers, floats and Booleans.
- [ ] Use `print()`, `input()`, `type()` and `int()`.
- [ ] Write an `if/else` statement.
- [ ] Write a `for` loop.
- [ ] Define and call a function.
- [ ] Build and run `concept_explorer.py`.
- [ ] Complete at least four independent practice tasks.
- [ ] Explain your mini-project without reading the code line by line.

**Self-assessment:** If you can run the project but cannot explain how it works, repeat the guided project. The goal is understanding, not merely getting the output.

## 11. What comes next?

On Day 2, you will learn how Python stores and organises multiple values using strings, lists, tuples, sets and dictionaries. You will use those structures to manage AI conversation data. You already saw a list in today's project; on Day 2 you will learn how to create, read, update and use it correctly.
