# Day 1 — Introduction to AI application development, GenAI and Agentic AI career roles, Python revision and development environment

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours | **Difficulty:** Beginner  
**Approved mini-project:** AI Application Development Concept Explorer  
**Prerequisites:** None. This lesson assumes you may never have written a Python program.

> **Study method:** Read one small section, type the example yourself, run it, compare the output and explain what happened. Do not copy the entire lesson into one file. The purpose is to learn how to think through code.

## 0. Today's learning plan

| Time | Activity | Evidence |
|---|---|---|
| 15 min | Understand software, AI, GenAI and Agentic AI | Explain the terms in your own words |
| 20 min | Understand what an AI application developer builds | Draw the request-to-response flow |
| 25 min | Prepare Python and your working folder | Python version shown in terminal |
| 40 min | Python basics: values, variables, input, output and types | Three small programs |
| 25 min | Conditions and simple validation | Menu choice checked correctly |
| 35 min | Build the approved project | Concept Explorer runs |
| 15 min | Quiz, interview practice and review | Answers and checklist |

If installation takes longer, do not rush. Finish setup and continue the coding in another session.

## 1. What are we learning, and why?

The goal of this 70-day pathway is not merely to send a question to an AI model. The goal is to build **software applications that use AI reliably**.

Imagine a company wants an assistant that answers employee questions using company policy documents. A working solution needs more than a model:

1. An employee enters a question.
2. The application receives and validates the question.
3. It may search approved company documents.
4. It sends suitable information to an AI model.
5. It displays the answer and, where required, its sources.
6. It protects private information.
7. It handles failures and is tested.
8. It is deployed so employees can use it.

Python is one of the tools used to build these application parts.

### 1.1 What is software?

**Software** is a set of instructions that tells a computer what to do.

Examples:
- A calculator receives numbers and performs calculations.
- A banking application checks a request and displays account information.
- A learning platform stores lessons, accepts quiz answers and calculates scores.
- An AI assistant receives a question and uses an AI model to generate a response.

A software application commonly has these parts:

| Part | Simple meaning | Learning-platform example |
|---|---|---|
| User interface | Where a person interacts | Web page with a question box |
| Input | Information supplied | Student's question |
| Program logic | Rules that decide what happens | Check whether the question is empty |
| Data storage | Where information is saved | Database containing user records |
| External service | Another system the app communicates with | LLM API |
| Output | What the application gives back | Answer shown on the page |

**Important:** An AI model is not the same as a complete application. The model performs an AI task. The application manages the user experience and surrounding software responsibilities.

### 1.2 What is an AI application?

An **AI application** is software that uses an AI capability as one component of its workflow.

Example: a support-ticket classifier.

- Input: "I cannot reset my password."
- AI task: predict the ticket category.
- Application logic: validate the ticket and check the model's result.
- Output: Account Access.
- Further action: route the ticket to the correct support team.

The AI prediction is only one step. The application still needs input validation, error handling, logging, permissions and tests.

### 1.3 AI, ML, Deep Learning, GenAI, LLM and Agentic AI

These terms are related, but they do not mean the same thing.

| Term | Beginner-friendly meaning | Example |
|---|---|---|
| Artificial Intelligence (AI) | Broad field of building systems that perform tasks associated with intelligence | System that helps decide which support queue receives a ticket |
| Machine Learning (ML) | Approach in which systems learn patterns from data | Model learns from old tickets and predicts a category |
| Deep Learning (DL) | Machine learning using neural networks with multiple layers | Neural network recognises objects in images |
| Generative AI (GenAI) | AI that generates content such as text, images, audio or code | Model drafts an answer |
| Large Language Model (LLM) | Model trained to process and generate language | Model summarises a document |
| Agentic AI | AI-based system designed to pursue a goal through controlled decisions and actions, often using tools | Assistant checks order status, prepares a report and requests approval before a refund |

Think of the relationship as a learning map:

~~~text
Artificial Intelligence (AI)
│
├── Machine Learning (ML)
│   └── Deep Learning (DL)
│
└── Other AI approaches

Generative AI: generates text, images, audio, code, etc.

Agentic AI application:
goal → choose next step → use an allowed tool
     → observe result → continue or stop
~~~

This is not a strict family tree. GenAI systems often use deep-learning models, and agentic applications may use LLMs, but not every AI system is generative or agentic.

**Check your understanding**
- A model predicts whether an email is spam. Is it necessarily GenAI? No. It may be a classification model.
- An application drafts an email from instructions. Is that a GenAI use case? Yes.
- An assistant checks a calendar and proposes meeting slots. It may be an agentic workflow if it selects and invokes tools as part of a goal-directed process. A fixed script that always calls the same API is automation, not automatically an AI agent.

### 1.4 What does a GenAI / Agentic AI developer actually build?

A developer builds the application around the model.

| Responsibility | What it means in a real project |
|---|---|
| Python programming | Write application logic |
| Prompt design | Give the model clear instructions and relevant context |
| API integration | Send requests to an external model service |
| Data preparation | Read, clean and organise documents or records |
| Retrieval | Find useful information for a question |
| Tool integration | Allow a model-driven workflow to use approved functions or APIs |
| Validation | Check inputs and outputs before trusting them |
| Testing | Verify expected behaviour and failure cases |
| Security | Protect secrets, user data and sensitive actions |
| Deployment | Make the application available to users |
| Monitoring | Observe errors, speed, usage and cost |

The pathway teaches these skills in sequence. We will not jump directly into LangChain, LangGraph or MCP today. First, become comfortable with Python and software development.

## 2. Understand the flow of a simple AI application

Consider a student asking: "Explain Python variables."

~~~text
Student
  │ enters a question
  ▼
User Interface
  │ sends the question
  ▼
Python Application
  │ validates input and applies rules
  ▼
AI Service / Model
  │ generates a response
  ▼
Python Application
  │ checks and formats the response
  ▼
User Interface
  │ displays the answer
  ▼
Student
~~~

Later we will add databases, document retrieval, APIs, agents and tools.

**Model vs API vs application**
- **Model:** the trained system that performs the AI task.
- **API:** a defined way for one software system to communicate with another.
- **Application:** the complete software that a user interacts with.
- **Python code:** can connect the application to an API, validate data and decide what to do next.

Do not say "I built an LLM" when you integrated an existing model into an application. Say: "I built a Python application that integrates an LLM through an API."

## 3. Prepare your development environment

### 3.1 Tools for today

| Tool | Why you need it |
|---|---|
| Python 3 | Runs Python programs |
| VS Code or another editor | Helps write and organise code |
| Terminal / Command Prompt / PowerShell | Runs commands |
| Project folder | Keeps your work organised |

Install Python 3 from the official Python website and install a code editor if needed. During Windows installation, enable the option to add Python to PATH if offered.

### 3.2 Open a terminal

- Windows: open PowerShell or Command Prompt.
- macOS: open Terminal.
- Linux: open your Terminal application.

A terminal is a text-based place to type commands. It is not the same as the Python editor.

### 3.3 Check Python installation

**Windows PowerShell / Command Prompt**

~~~powershell
py --version
~~~

If unavailable, try:

~~~powershell
python --version
~~~

**macOS / Linux**

~~~bash
python3 --version
~~~

Expected output looks similar to this; your version may differ:

~~~text
Python 3.12.4
~~~

If you see "command not found" or "not recognized":
1. Confirm Python installation completed.
2. Close and reopen the terminal.
3. On Windows, try py --version.
4. Check whether Python was added to PATH.
5. Do not install random packages to fix a missing Python command. Fix the interpreter installation or command path first.

### 3.4 Create your course folder

**Windows**

~~~powershell
mkdir techphile_genai
cd techphile_genai
mkdir day_01
cd day_01
~~~

**macOS / Linux**

~~~bash
mkdir -p techphile_genai/day_01
cd techphile_genai/day_01
~~~

- mkdir creates a folder.
- cd changes the current working directory.
- The current directory is where commands such as running a relative file path are interpreted.

Check the current folder:

~~~bash
pwd
~~~

### 3.5 Create and run your first Python file

In VS Code:

1. Open the day_01 folder.
2. Create a file named hello.py.
3. Type the code below.
4. Save the file.
5. Open the integrated terminal in that folder.
6. Run the command for your operating system.

~~~python
print("Hello, TechPhile!")
print("I am learning Python for AI application development.")
~~~

Run:
- Windows: py hello.py or python hello.py
- macOS/Linux: python3 hello.py

Expected output:

~~~text
Hello, TechPhile!
I am learning Python for AI application development.
~~~

**What does this prove?** Your file was saved, the Python interpreter found it, and the interpreter executed the instructions.

Common confusion:
- hello.py is a file name, not a terminal command by itself.
- print(...) is Python code; type it inside the file or Python interactive prompt, not as a PowerShell command.
- If you run from a different folder, Python may not find the file. Move to the correct folder or provide the correct path.

## 4. Python revision — start from zero

A Python program is a sequence of instructions. Python generally executes statements from top to bottom.

### 4.1 Display information with print()

print() displays information in the terminal.

~~~python
print("Welcome")
print(100)
print(10 + 5)
~~~

Expected output:

~~~text
Welcome
100
15
~~~

Line-by-line:
1. print("Welcome") displays the text Welcome.
2. print(100) displays the number 100.
3. print(10 + 5) calculates 10 + 5, then displays 15.

Text is placed inside quotes. Numbers used for arithmetic do not need quotes. Change 10 + 5 to 25 + 7 and predict the result before running it.

### 4.2 Comments explain code to humans

A comment begins with #. Python ignores the comment when executing the program.

~~~python
# Display the course name
print("GenAI and Agentic AI")
~~~

Use comments to explain why a non-obvious decision is made. Do not add a comment to every obvious line.

### 4.3 Variables store values

A **variable** is a name that refers to a value.

~~~python
student_name = "Asha"
course_name = "GenAI Developer"
days = 70

print(student_name)
print(course_name)
print(days)
~~~

Expected output:

~~~text
Asha
GenAI Developer
70
~~~

Understand the assignment statement student_name = "Asha":

- student_name is the variable name.
- = is the assignment operator. It assigns the value on the right to the name on the left.
- "Asha" is a string value.

It does not mean the two sides are mathematically equal. In Python, = assigns; == compares.

Good variable names describe the data:

| Avoid | Prefer | Reason |
|---|---|---|
| x | student_name | Meaning is clear |
| a1 | course_duration_days | Purpose is clear |
| data for everything | student_email, quiz_score | Specific names reduce confusion |

Python variable names are case-sensitive: student_name and Student_Name are different names.

### 4.4 Understand basic data types

A data type describes the kind of value.

| Type | Meaning | Example |
|---|---|---|
| str | Text | "Asha" |
| int | Whole number | 70 |
| float | Decimal number | 89.5 |
| bool | True or false | True, False |

Run:

~~~python
student_name = "Asha"
learning_days = 70
completion_percentage = 45.5
is_enrolled = True

print(type(student_name))
print(type(learning_days))
print(type(completion_percentage))
print(type(is_enrolled))
~~~

Expected output:

~~~text
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
~~~

The type() function helps inspect a value's type. It is useful when debugging unexpected data.

### 4.5 Receive information with input()

input() pauses the program and waits for the user to type something.

~~~python
student_name = input("Enter your name: ")
print("Welcome,", student_name)
~~~

Example run:

~~~text
Enter your name: Asha
Welcome, Asha
~~~

Line-by-line:
1. Python displays Enter your name:.
2. The program waits.
3. The user types Asha and presses Enter.
4. input() returns the typed value as text.
5. The returned text is assigned to student_name.
6. print() displays the greeting.

**Important beginner rule:** input() returns a string, even when the user types digits.

~~~python
age = input("Enter your age: ")
print(type(age))
~~~

If you type 21, the type is still str, not int.

### 4.6 Convert a value when you need a number

Suppose you ask for two marks and want to add them.

Incorrect approach:

~~~python
mark_one = input("Enter first mark: ")
mark_two = input("Enter second mark: ")
print(mark_one + mark_two)
~~~

If the user enters 10 and 20, output is:

~~~text
1020
~~~

Why? Both values are strings. For strings, + joins text together.

Correct approach:

~~~python
mark_one = int(input("Enter first mark: "))
mark_two = int(input("Enter second mark: "))

total = mark_one + mark_two
print("Total:", total)
~~~

Example output:

~~~text
Enter first mark: 10
Enter second mark: 20
Total: 30
~~~

- input() receives text.
- int(...) converts valid whole-number text into an integer.
- total stores the numeric sum.

Use float() when decimal values are allowed:

~~~python
price = float(input("Enter price: "))
print("Price:", price)
~~~

If a user types ten, int("ten") raises ValueError. Conversion only works when the text represents a valid number. We will learn structured exception handling later in Phase 1.

### 4.7 Basic operators

| Operator | Meaning | Example | Result |
|---|---|---|---|
| + | Addition | 10 + 3 | 13 |
| - | Subtraction | 10 - 3 | 7 |
| * | Multiplication | 10 * 3 | 30 |
| / | Division | 10 / 2 | 5.0 |
| // | Floor division | 11 // 2 | 5 |
| % | Remainder | 11 % 2 | 1 |
| == | Equal comparison | 10 == 10 | True |
| != | Not equal | 10 != 5 | True |
| > | Greater than | 10 > 5 | True |
| < | Less than | 3 < 5 | True |

Example:

~~~python
total_questions = 20
correct_answers = 15

score_percentage = (correct_answers / total_questions) * 100

print("Score:", score_percentage)
~~~

Expected output:

~~~text
Score: 75.0
~~~

The expression is evaluated using normal arithmetic order: divide first, then multiply.

### 4.8 Make a decision with if, elif and else

A condition lets the program choose what to do.

~~~python
score = 75

if score >= 50:
    print("Pass")
else:
    print("Try again")
~~~

Expected output: Pass.

Read it as:
- If score is greater than or equal to 50, display Pass.
- Otherwise, display Try again.

Notice the colon and indentation before print(). Indentation tells Python which statements belong inside the condition. Four spaces is the standard convention.

Add another condition:

~~~python
score = 85

if score >= 90:
    print("Excellent")
elif score >= 50:
    print("Pass")
else:
    print("Try again")
~~~

Expected output: Pass.

Python checks conditions from top to bottom. Since 85 is not at least 90, it checks the next condition. Since 85 is at least 50, it prints Pass and skips the remaining branch.

### 4.9 Validate a menu choice

Validation means checking whether input is acceptable before using it.

~~~python
choice = input("Choose 1, 2 or 3: ")

if choice == "1":
    print("You selected AI")
elif choice == "2":
    print("You selected Generative AI")
elif choice == "3":
    print("You selected Agentic AI")
else:
    print("Invalid choice. Please enter 1, 2 or 3.")
~~~

Why compare with strings such as "1"? Because input() returns text. Comparing text is simple here and avoids a conversion error.

Try entering 2, then hello, then leaving the input blank. The program should handle all three without crashing.

### 4.10 Combine the basics in one small program

Create student_intro.py:

~~~python
# Collect basic student information
student_name = input("Enter your name: ")
course_name = "GenAI and Agentic AI"
study_hours = float(input("How many hours will you study today? "))

# Display a simple summary
print()
print("----- STUDENT LEARNING PLAN -----")
print("Student:", student_name)
print("Course:", course_name)
print("Study hours:", study_hours)

# Check the planned study time
if study_hours >= 2:
    print("Plan: You have planned the recommended daily study time.")
else:
    print("Plan: Try to reserve at least 2 hours.")
~~~

Example run:

~~~text
Enter your name: Asha
How many hours will you study today? 2.5

----- STUDENT LEARNING PLAN -----
Student: Asha
Course: GenAI and Agentic AI
Study hours: 2.5
Plan: You have planned the recommended daily study time.
~~~

Trace the program:

| Step | Variable / action | Value |
|---:|---|---|
| 1 | student_name | "Asha" |
| 2 | course_name | "GenAI and Agentic AI" |
| 3 | study_hours | 2.5 as a float |
| 4 | print() | Displays a blank line |
| 5 | study_hours >= 2 | True |
| 6 | Selected branch | Prints the recommended-time message |

**Limitation:** This beginner example assumes the user types a valid decimal number. If they type words, float() raises ValueError. Later, learn to catch that error and show a friendly message.

## 5. Debugging: investigate instead of guessing

A bug is a problem that causes a program to behave incorrectly or stop.

| Error / symptom | Why it happens | What to check |
|---|---|---|
| SyntaxError | Python cannot understand the code structure | Missing quote, bracket, colon or invalid syntax |
| NameError | A name is used before it is defined or is misspelled | Variable spelling and order |
| TypeError | An operation is not supported for the supplied types | Mixing strings and numbers |
| ValueError | A value cannot be converted as requested | "ten" passed to int() |
| IndentationError | Code blocks are not indented consistently | Spaces under if, elif and else |
| File not found | Terminal is in a different folder or file name is wrong | Current folder and exact file name |

### 5.1 Debugging example: string plus integer

Problem:

~~~python
age = input("Enter your age: ")
next_year_age = age + 1
print(next_year_age)
~~~

If you enter 20, Python raises TypeError because age is text and 1 is an integer.

Fix:

~~~python
age = int(input("Enter your age: "))
next_year_age = age + 1
print("Next year you will be:", next_year_age)
~~~

The cause matters: input() returns a string, so convert valid numeric text before arithmetic.

### 5.2 A repeatable debugging method

1. Read the last line of the traceback to identify the exception type and message.
2. Find the file name and line number mentioned.
3. Inspect the values used on that line.
4. Check each value's type with type() if necessary.
5. Reproduce the issue with the smallest input that causes it.
6. Make one change at a time.
7. Run the same failing example again.
8. Add a test so the problem is less likely to return.

Avoid hiding every error with a broad except block. A program that silently ignores failures is difficult to trust.

## 6. Mini exercises — solve before viewing the answers

**Exercise 1 — Personal introduction:** Ask for a student's name and city, then print a greeting and city.

**Exercise 2 — Add two numbers:** Ask for two whole numbers, convert them to integers, add them and display the total. Test with 12 and 8.

**Exercise 3 — Pass or try again:** Ask for a quiz score. If it is 50 or above, print Pass; otherwise print Try again. Test 75 and 35.

**Exercise 4 — Predict before running:** What will this display?

~~~python
course = "Python"
days = 10
print(course)
print(days + 5)
print(type(course).__name__)
~~~

**Exercise 5 — Find the bug:** Why does this fail when the user types 18? Write the corrected version.

~~~python
age = input("Age: ")
print(age + 2)
~~~

<details>
<summary>Suggested answers — open only after attempting</summary>

**Exercise 1**

~~~python
student_name = input("Enter your name: ")
city = input("Enter your city: ")
print("Hello", student_name + "!")
print("You are learning from", city + ".")
~~~

**Exercise 2**

~~~python
first_number = int(input("First number: "))
second_number = int(input("Second number: "))
total = first_number + second_number
print("Total:", total)
~~~

For inputs 12 and 8, the total is 20.

**Exercise 3**

~~~python
score = int(input("Enter your score: "))
if score >= 50:
    print("Pass")
else:
    print("Try again")
~~~

**Exercise 4:** Python, 15, str.

**Exercise 5:** input() returns text. Convert it first: age = int(input("Age: ")). Then age + 2 is numeric addition.

</details>

## 7. Daily knowledge check — five MCQs

**Q1. Which statement best describes an AI application?**

A. It is always just a trained model.  
B. It is software that may use an AI model as one component.  
C. It never needs input validation.  
D. It cannot communicate with APIs.

**Correct answer: B.** An AI application includes surrounding software: input handling, program logic, integrations, output handling and safeguards.

**Q2. What does input() return?**

A. Always an integer  
B. Always a Boolean  
C. A string  
D. A list

**Correct answer: C.** Even if the user types digits, input() returns text. Convert with int() or float() when numeric operations are required.

**Q3. What is the output of the following?**

~~~python
number = 8
print(number + 2)
~~~

A. 82  
B. 10  
C. 8 + 2  
D. Error

**Correct answer: B.** Both values are integers, so + performs arithmetic addition.

**Q4. Which operator checks whether two values are equal?**

A. =  
B. +  
C. ==  
D. !=

**Correct answer: C.** A single = assigns a value. Double equals == compares two values.

**Q5. Which statement about Agentic AI is most accurate?**

A. Every Python script is an AI agent.  
B. An agentic system may use a model, state and tools to pursue a goal through bounded steps.  
C. An agent must run forever.  
D. An agent never needs permissions or stopping conditions.

**Correct answer: B.** Agentic systems need controlled tool access, observation and stopping conditions. Unbounded execution is unsafe and unreliable.

## 8. Day 1 project

The approved project is **AI Application Development Concept Explorer**. Follow the complete build-along guide at projects/day_01_project.md. It includes requirements, the implementation plan, complete runnable code, sample runs, test cases and submission checklist.

Do not skip the project. Apply variables, strings, input, output, conditions and basic validation to a small useful program.

## 9. Interview preparation

Use interview_questions/day_01_interview.md for fully explained answers and practical follow-ups.

Practise explaining:
1. How are AI, ML, Deep Learning, GenAI and Agentic AI different?
2. What does a GenAI application developer build besides connecting a model?
3. Why does input() return text, and when do you convert it?
4. What is the difference between assignment (=) and comparison (==)?
5. How would you investigate a Python error?

A strong answer uses this order: **meaning → how it works → example → limitation**.

## 10. Before Day 2

- [ ] Explain the difference between a model and an application.
- [ ] Explain AI, ML, Deep Learning, GenAI, LLM and Agentic AI in simple words.
- [ ] Describe the basic request-to-response flow of an AI application.
- [ ] Check your Python version from the terminal.
- [ ] Create a folder and a .py file.
- [ ] Run a Python file from the terminal.
- [ ] Use print(), comments and variables.
- [ ] Identify str, int, float and bool.
- [ ] Explain why input() returns a string.
- [ ] Convert valid numeric input using int() and float().
- [ ] Use arithmetic, comparison operators and if/elif/else.
- [ ] Read a basic error message and investigate its cause.
- [ ] Complete and test the AI Application Development Concept Explorer.
- [ ] Answer all five MCQs and explain the correct answers.

**Evidence to save:** hello.py, student_intro.py, project source file, one successful sample run and your own short explanation of the application flow.

**Next lesson:** Day 2 — Python data structures: strings, lists, tuples, sets and dictionaries. We will use these structures to organise conversation data.
