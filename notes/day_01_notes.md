# Day 01 — Introduction to AI Application Development, GenAI and Agentic AI Career Roles, Python Revision and Development Environment

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved day topic:** Introduction to AI application development, GenAI and Agentic AI career roles, Python revision and development environment  
**Approved mini-project:** AI Application Development Concept Explorer  
**Duration:** 2–3 hours  
**Level:** Beginner  
**Primary language:** Python

---

## How to use these notes

These notes are written for a student who may be opening Python for the first time or may remember only a little Python from college.

Do not rush through the lesson.

Read one small section, run its code, compare your output, and explain the result in your own words.

When a word is new, read its meaning before continuing.

Do not copy a complete program without understanding each line.

The aim is not to memorize code. The aim is to understand what the computer is doing and why.

### Learning agreement

- Start with the beginner example.
- Type the code yourself instead of only copying it.
- Run the code after each small change.
- Read error messages calmly.
- Change one value and observe what happens.
- Explain the result aloud as if teaching a friend.
- Try the practice task before looking at any suggested solution.
- Ask why a line is required, not only what it does.

---

# 1. What will we learn today?

By the end of Day 1, you should be able to:

1. Explain what an AI application is.
2. Explain the difference between traditional software, AI, Generative AI and Agentic AI at a beginner level.
3. Identify the responsibilities of a junior GenAI or Agentic AI developer.
4. Explain where Python is used in an AI application.
5. Open a project folder in Visual Studio Code.
6. Check whether Python is installed.
7. Create and run a simple Python file.
8. Understand basic Python statements, variables, data types, input and output.
9. Read a simple conditional statement and a simple loop.
10. Describe the input-process-output pattern.
11. Explain the small project created today.

You are not expected to build a complete chatbot today. We will first understand the building blocks.

# 2. What is software?

## 2.1 Beginner explanation

Software is a set of instructions that tells a computer what to do.

Think about a calculator.

You enter two numbers.

You select addition.

The calculator follows instructions and displays the answer.

A calculator application is software.

A college attendance application is also software.

A shopping application is software.

A banking application is software.

A Python program is also software, even if it contains only two lines.

## 2.2 Real-life example

Imagine a college wants to calculate the total marks of a student.

The student has marks in three subjects:

- Python: 80
- Mathematics: 75
- English: 90

A simple program can add the marks and show the total.

The computer does not decide the addition rule by itself.

A developer writes instructions that tell the computer to add the values.

## 2.3 What problem does software solve?

Software helps people perform tasks in a repeatable way.

Examples:

- A banking application calculates account balances.
- A hospital application stores appointment details.
- An e-commerce application records orders.
- A college application stores student marks.
- A delivery application tracks orders.
- An AI application answers questions or assists with tasks.

## 2.4 Important words

| Word | Beginner meaning |
|---|---|
| Computer | An electronic machine that follows instructions |
| Program | Instructions written for a computer |
| Software | A program or collection of programs |
| Developer | A person who builds and maintains software |
| Application | Software created for a particular user task |
| Input | Information given to a program |
| Process | Work performed using the input |
| Output | Result produced by a program |
| Bug | A problem or mistake in a program |
| Debugging | Finding and fixing a problem |

## 2.5 Interview understanding

If an interviewer asks, "What is software?", do not give a complicated answer.

A fresher can say:

"Software is a set of instructions that helps a computer perform a task. For example, a student management application stores student details and helps a college manage records."

That answer is clear and includes an example.

# 3. What is an AI application?

## 3.1 Start with a normal application

A normal student information application may ask for:

- Student name
- Roll number
- Department
- Year

The application stores the information and displays it when requested.

The developer writes the rules for what the application should do.

## 3.2 Now imagine an AI feature

Suppose a student types:

"I am struggling to understand Python loops. Can you explain with a simple example?"

An AI-powered learning application can send the question to an AI model and show a generated explanation.

The application is still software.

It also uses an AI model as one of its components.

This is an AI application.

## 3.3 Simple definition

An AI application is a software application that uses an artificial intelligence model or technique to perform tasks such as understanding text, classifying information, making predictions, searching content or generating responses.

## 3.4 AI application examples

| Application | What the AI feature does |
|---|---|
| Learning assistant | Explains a topic or answers a student's question |
| Resume helper | Extracts skills and summarizes experience |
| Customer support assistant | Suggests answers to customer questions |
| Document assistant | Finds information in uploaded documents |
| Product recommendation system | Suggests products based on available information |
| Email assistant | Drafts or classifies messages |
| Business report assistant | Summarizes supplied business information |

## 3.5 Is every application an AI application?

No.

A basic calculator that follows fixed addition and subtraction rules does not need an AI model.

A calculator that accepts a natural-language question such as "Explain why my monthly expenses increased" may use AI to interpret and explain information.

The important difference is whether an AI capability is part of the application.

## 3.6 The developer's responsibility

An AI developer does more than send a question to a model.

The developer must think about:

- What information the user enters.
- Whether the input is valid.
- Which model or service is appropriate.
- How the application sends the request.
- How the response is received.
- Whether the response has the expected format.
- What happens if the model service is unavailable.
- Whether sensitive information is protected.
- How the result is shown to the user.
- How the application is tested.

A model response is not automatically correct just because it sounds confident.

# 4. What is Artificial Intelligence?

## 4.1 Beginner meaning

Artificial Intelligence, usually called AI, is a field of computer science that develops systems capable of performing tasks that normally require some form of human intelligence.

Examples of such tasks include:

- Understanding language.
- Recognizing objects in images.
- Identifying patterns.
- Making predictions.
- Recommending items.
- Generating text or images.
- Planning steps toward a goal.

This is a broad definition. Different AI systems work in different ways.

## 4.2 A simple example

A traditional rule-based application may check whether a student's mark is greater than or equal to 40.

If yes, it displays "Pass".

Otherwise, it displays "Fail".

The developer has written the exact rule.

An AI system may instead examine many examples of student performance and estimate which students may need additional support.

That is a prediction task.

The two systems solve different problems.

## 4.3 AI is a broad field

Artificial Intelligence is the broad area.

Machine Learning is one approach within AI.

Deep Learning is one approach within Machine Learning.

Generative AI uses models that can generate new content.

These terms are related, but they do not mean exactly the same thing.

## 4.4 Simple relationship diagram

`Artificial Intelligence → Machine Learning → Deep Learning`

Generative AI is a group of techniques and models that can generate content. Many modern Generative AI systems use deep learning.

Do not assume that every AI system is a chatbot.

# 5. What is Generative AI?

## 5.1 Beginner explanation

Generative AI is a type of AI that can create new content based on patterns learned from data and the instructions it receives.

The generated content may include:

- Text.
- Code.
- Images.
- Audio.
- Video.
- Structured data.

For example, a student asks:

"Explain Python variables using a college example."

A text-generation model may produce a new explanation.

The model is generating a response based on its learned patterns and the current request.

## 5.2 What does the word generate mean?

Generate means create or produce.

If a system creates a paragraph, it generates text.

If a system creates a picture, it generates an image.

If a system produces a Python code example, it generates code.

## 5.3 What is an LLM?

LLM means Large Language Model.

A language model is a model designed to work with language.

A Large Language Model is trained using a very large amount of text and other suitable data, depending on the model.

It can perform tasks such as:

- Answering questions.
- Summarizing text.
- Rewriting sentences.
- Explaining code.
- Generating code.
- Extracting information.
- Classifying text.

We will study LLMs in detail in Phase 2. Today, remember that an LLM is one important technology used in many Generative AI applications.

## 5.4 Simple request-and-response example

A user enters:

`Explain Python in one sentence.`

The application sends the request to an LLM service.

The model generates a response.

The application displays the response.

The simplified flow is:

`User question → Python application → LLM service → Generated response → User`

This is a simplified view. A real application also needs configuration, network communication, error handling, security and response validation.

## 5.5 Does Generative AI always give correct answers?

No.

A model can produce an incorrect answer.

It can misunderstand a question.

It can provide information that sounds convincing but is unsupported.

This behavior is commonly discussed under the term hallucination.

We will study hallucinations and model limitations on Day 13.

For now, remember:

**Generated output must be checked according to the risk and purpose of the application.**

## 5.6 Where is Generative AI used?

- Drafting business emails.
- Summarizing long documents.
- Explaining technical topics.
- Helping developers understand code.
- Extracting fields from resumes.
- Answering questions about company documents.
- Creating first drafts of reports.
- Supporting customer service teams.

## 5.7 Interview answer

"Generative AI is a branch of AI that creates new content such as text, code, images or audio based on a user request and patterns learned during training. For example, a learning assistant can use an LLM to generate a beginner-friendly explanation of a Python concept."

# 6. What is Agentic AI?

## 6.1 First understand a normal chatbot

A simple chatbot receives a message and returns a response.

Example:

User: "What is the capital of India?"

Chatbot: "New Delhi."

The chatbot may answer the question, but it may not perform additional actions.

## 6.2 Now imagine a task that needs multiple steps

A user asks:

"Find the total sales from this file and prepare a short summary."

A system designed as an agentic workflow may need to:

1. Understand the user's goal.
2. Identify that a file must be read.
3. Use an approved file-reading tool.
4. Calculate the total.
5. Prepare a summary.
6. Return the result.

The system is doing more than generating one direct answer.

It is coordinating steps and using tools.

## 6.3 Beginner definition

Agentic AI refers to AI systems designed to work toward a goal by selecting actions, using tools, observing results and continuing through a controlled workflow.

The exact level of autonomy depends on the system design.

## 6.4 What is an agent?

An AI agent is a software system that uses an AI model and a set of defined capabilities to work toward a task.

An agent may have:

- A goal.
- An input.
- Instructions.
- Access to approved tools.
- A way to observe tool results.
- A state or memory mechanism.
- Rules for when to stop.
- Permission boundaries.

Not every chatbot is an agent.

Not every agent needs unrestricted access to external systems.

## 6.5 Example: student study assistant

A student asks:

"Help me prepare for tomorrow's Python test. Make a revision plan from these topics."

A simple chatbot can generate a plan from the text supplied by the student.

A more capable agentic application may:

- Read an uploaded topic list.
- Identify the topics.
- Arrange them into a schedule.
- Check whether the requested time is realistic.
- Ask the student to approve the plan.
- Save the approved plan if the application has permission.

The tools and permissions must be deliberately designed.

## 6.6 Important safety point

An agent should not be allowed to perform every action it can technically access.

For example:

- Reading a document may be low risk.
- Sending an email is an external action.
- Deleting a database record can be destructive.
- Making a payment is a sensitive action.

Sensitive actions should use appropriate authorization and human approval.

## 6.7 Interview answer

"Agentic AI describes AI systems that can work toward a goal through multiple steps, use approved tools, observe results and decide what to do next within defined limits. For example, an agent may read a supplied sales file, calculate totals using a Python tool and prepare a report. Important actions should have permission checks and approval controls."

# 7. Traditional Software vs AI Application vs Generative AI vs Agentic AI

| Type | Beginner explanation | Example |
|---|---|---|
| Traditional software | Follows explicitly programmed rules | Marks calculator |
| AI application | Uses an AI model or technique for a task | Spam classifier |
| Generative AI application | Uses a generative model to create content | Email drafting assistant |
| Agentic AI application | Uses an AI-driven workflow to select actions and use tools toward a goal | Report assistant that reads a file, calculates results and prepares a report |

## 7.1 Do not confuse these categories

A Generative AI application may simply generate a response.

An Agentic AI application may use a model as part of a multi-step process.

An agent may use a Generative AI model, but the terms are not interchangeable.

## 7.2 Example comparison

Task: "Tell me the total sales in this CSV file."

- Traditional software: A developer writes a fixed program that reads a known CSV structure and calculates the total.
- AI application: A model may classify or interpret the supplied information.
- Generative AI application: An LLM may explain the calculated result in natural language.
- Agentic AI application: A controlled agent workflow may identify the file-reading tool, execute the calculation, inspect the result and prepare a summary.

The correct design depends on the task. Do not use an AI agent when a simple, reliable Python function is enough.

# 8. What does a GenAI Developer do?

A GenAI Developer builds software applications that use Generative AI models.

Typical responsibilities include:

1. Understanding a business requirement.
2. Preparing application inputs.
3. Connecting an application to an LLM provider.
4. Designing prompts.
5. Handling model responses.
6. Validating structured outputs.
7. Connecting the model to documents or databases when required.
8. Building APIs and user interfaces.
9. Testing application behavior.
10. Handling errors and service failures.
11. Protecting secrets and user data.
12. Monitoring quality, speed and cost.
13. Documenting the application.

## 8.1 Example workday

A junior developer may receive a task:

"Build an API that accepts a paragraph and returns a short summary."

The developer may:

- Read the requirement.
- Understand the expected input and output.
- Create a Python project.
- Build an API endpoint.
- Connect an approved LLM provider.
- Send the paragraph to the model.
- Receive the generated summary.
- Handle an API failure.
- Test the endpoint.
- Document how to run the project.

This pathway gradually teaches the required skills.

# 9. What does an Agentic AI Developer do?

An Agentic AI Developer builds systems where AI models can coordinate steps and use tools under defined rules.

Typical responsibilities include:

- Understanding the task the agent should perform.
- Defining the agent's responsibilities.
- Choosing which tools are available.
- Describing tool inputs and outputs.
- Validating tool arguments.
- Managing state and memory.
- Controlling loops and stopping conditions.
- Handling failures and retries.
- Adding human approval for sensitive operations.
- Testing whether the agent completes tasks correctly.
- Recording execution traces.
- Protecting the application from unsafe actions.

## 9.1 Example

A company wants an assistant to prepare a weekly sales report.

A controlled workflow might:

1. Receive a report request.
2. Check the user's permission.
3. Read the approved sales data.
4. Calculate totals using deterministic Python code.
5. Ask an LLM to explain the verified figures.
6. Create a draft report.
7. Ask a manager to approve it.
8. Publish the report only after approval.

Notice that ordinary Python code performs the calculation. The LLM helps with language tasks. The workflow controls the steps.

# 10. Why is Python used in this pathway?

Python is a programming language.

It is popular in AI and data-related development because it has readable syntax and a large ecosystem of libraries.

A library is reusable code created by other developers that we can use in our own projects.

Python is used for:

- Writing application logic.
- Processing text and files.
- Calling web APIs.
- Building backend services.
- Working with databases.
- Integrating AI models.
- Building RAG pipelines.
- Creating agent tools.
- Writing automated tests.

## 10.1 Why begin with Python?

We need a programming language to connect the different parts of an AI application.

For example, a Python application can:

- Accept a question.
- Validate the question.
- Send it to an AI service.
- Receive the response.
- Check the response.
- Return the result.

Without understanding the programming language, students may copy AI code without knowing how it works.

## 10.2 Python is not the AI model

Python and an LLM are different things.

Python is a programming language.

An LLM is a trained model.

Python code can communicate with an LLM service, but Python itself is not the LLM.

This difference is important in interviews.

# 11. Development environment — what does it mean?

A development environment is the collection of software and tools used to write, run and test code.

For this pathway, the beginner setup includes:

- A computer.
- Python.
- Visual Studio Code.
- The Python extension for Visual Studio Code.
- A project folder.
- A terminal.
- A Python file.

## 11.1 What is Python installation?

Installing Python makes the Python interpreter available on your computer.

The Python interpreter is the program that reads and executes Python code.

A Python file commonly ends with:

`.py`

Example:

`hello.py`

## 11.2 What is Visual Studio Code?

Visual Studio Code, often called VS Code, is a code editor.

A code editor helps us:

- Write code.
- Organize files.
- View project folders.
- Use a terminal.
- Read errors.
- Run programs with extensions and commands.

VS Code is not the Python language.

It is a tool used to write and manage code.

## 11.3 What is a terminal?

A terminal is a text-based interface where we enter commands.

For example, we can ask Python to display its version.

We can also run a Python file from the terminal.

Do not confuse the terminal with the Python editor.

The editor is where you write code.

The terminal is where you run commands.

## 11.4 Windows beginner setup

1. Install a supported Python 3 version from the official Python website.
2. During installation, enable the option that adds Python to PATH if the installer offers it.
3. Install Visual Studio Code.
4. Open VS Code.
5. Open the Extensions view.
6. Search for the Microsoft Python extension.
7. Install the extension.
8. Create a folder named `genai_learning`.
9. Open that folder in VS Code.
10. Create a file named `day01_hello.py`.

Use the official installation instructions for your operating system. Installation screens can change between versions.

## 11.5 Check Python from the terminal

Open a terminal in VS Code.

Run:

```bash
python --version
```

On some Windows computers, this command may be:

```bash
py --version
```

On some Linux or macOS systems, use:

```bash
python3 --version
```

Expected output will look similar to:

```text
Python 3.x.x
```

The exact minor version may be different.

## 11.6 What does the version command do?

- `python` asks the terminal to run the Python command.
- `--version` asks Python to display its version.
- The version helps us confirm which Python installation is being used.

If the command is not recognized, Python may not be installed or may not be available through PATH.

Do not immediately reinstall everything. First check the installation and command suggested for your operating system.

## 11.7 Create your first Python file

Create a file named:

`day01_hello.py`

Write:

```python
print("Hello, Python!")
```

Run the file.

Expected output:

```text
Hello, Python!
```

## 11.8 Explain every part

- `print` is a built-in Python function.
- A function is a reusable operation.
- Parentheses `()` contain the information given to the function.
- The text is placed inside quotation marks.
- Python displays the text in the output.
- The line is a Python statement.

A statement is an instruction that Python can execute.

## 11.9 What is a string?

A string is text data.

Examples:

```python
"Hello"
"Python"
"GenAI Developer"
"Student 101"
```

A string is usually written inside single or double quotation marks.

Both examples below are valid:

```python
print("Hello")
print('Hello')
```

Use a consistent style in a project.

## 11.10 Common beginner errors

Incorrect:

```python
print(Hello)
```

Why it fails:

Python treats `Hello` as a name, not as text, because it is not inside quotation marks.

Correct:

```python
print("Hello")
```

Incorrect:

```python
Print("Hello")
```

Why it fails:

Python names are case-sensitive.

`print` and `Print` are not the same name.

Correct:

```python
print("Hello")
```

# 12. Python basics revision — one idea at a time

The next examples are a revision of basic Python. We will not introduce advanced functions, classes or complex structures today.

## 12.1 The input-process-output pattern

Most beginner programs can be understood using three stages.

**Input:** Information enters the program.

**Process:** The program performs an operation.

**Output:** The program displays or returns a result.

Example:

`Student marks → Add the marks → Display total`

This pattern will appear throughout the pathway.

## 12.2 Example 1 — display a message

Task:

Display a welcome message for a student.

Code:

```python
print("Welcome to TechPhile.ai")
```

Expected output:

```text
Welcome to TechPhile.ai
```

Explanation:

- The program contains one instruction.
- The instruction calls `print()`.
- The text is the value passed to `print()`.
- Python displays the text.

What did we learn?

We learned how to display a message.

## 12.3 Example 2 — display multiple messages

Task:

Display the course name and the learning topic.

Code:

```python
print("Course: GenAI and Agentic AI")
print("Topic: Python Basics")
```

Expected output:

```text
Course: GenAI and Agentic AI
Topic: Python Basics
```

Explanation:

- The first statement runs first.
- The second statement runs next.
- Each `print()` displays its value on a new line by default.
- Python normally executes statements from top to bottom.

## 12.4 What is a variable?

A variable is a name that refers to a value.

Think of a labelled box.

The label is the variable name.

The value is the information associated with it.

Example:

```python
student_name = "Anu"
```

Here:

- `student_name` is the variable name.
- `=` is the assignment operator.
- `"Anu"` is the string value.

The assignment operator stores or binds the value to the variable name.

It does not mean "equal to" in the mathematical comparison sense.

## 12.5 Example 3 — create and display a variable

Task:

Store a student's name and display it.

Code:

```python
student_name = "Anu"
print(student_name)
```

Expected output:

```text
Anu
```

Line-by-line explanation:

1. Python evaluates the text `"Anu"`.
2. Python assigns that value to the name `student_name`.
3. The next statement calls `print()`.
4. Python looks up the value associated with `student_name`.
5. Python displays the value.

## 12.6 Example 4 — store multiple student details

Code:

```python
student_name = "Anu"
course_name = "Python"
learning_day = 1

print(student_name)
print(course_name)
print(learning_day)
```

Expected output:

```text
Anu
Python
1
```

Explanation:

- `student_name` refers to text.
- `course_name` refers to text.
- `learning_day` refers to an integer.
- An integer is a whole number without a decimal part.

## 12.7 Variable naming rules

Good variable names describe the value.

Good examples:

```python
student_name = "Anu"
total_marks = 245
course_duration = 70
```

Poor examples:

```python
x = "Anu"
a = 245
z = 70
```

Single-letter names can be suitable in limited situations, but descriptive names help beginners and teams understand code.

Python variable names:

- Can contain letters.
- Can contain numbers after the first character.
- Can contain underscores.
- Cannot begin with a number.
- Are case-sensitive.
- Cannot be Python keywords.

## 12.8 Common variable mistakes

Incorrect:

```python
2student = "Anu"
```

Reason:

A variable name cannot begin with a number.

Correct:

```python
student2 = "Anu"
```

Incorrect:

```python
student-name = "Anu"
```

Reason:

A hyphen is interpreted as a minus operator.

Correct:

```python
student_name = "Anu"
```

## 12.9 What is a data type?

A data type describes the kind of value a variable refers to.

Common beginner Python types:

| Type | Meaning | Example |
|---|---|---|
| str | Text | `"Anu"` |
| int | Whole number | `25` |
| float | Decimal number | `85.5` |
| bool | True or false value | `True` |

## 12.10 Example 5 — use different data types

Code:

```python
student_name = "Anu"
student_age = 20
student_percentage = 86.5
is_enrolled = True

print(student_name)
print(student_age)
print(student_percentage)
print(is_enrolled)
```

Expected output:

```text
Anu
20
86.5
True
```

Explanation:

- The name is text, so it is a string.
- The age is a whole number, so it is an integer.
- The percentage includes a decimal, so it is a float.
- Enrollment is either true or false, so it is a Boolean.

## 12.11 Check a value's type using type()

Python provides the built-in `type()` function.

It tells us the type of a value.

Example:

```python
student_age = 20
print(type(student_age))
```

Expected output:

```text
<class 'int'>
```

Explanation:

- `type` is the function name.
- `student_age` is the value we want to inspect.
- Parentheses tell Python which value to inspect.
- The output indicates that the value is an integer.

Another example:

```python
student_name = "Anu"
print(type(student_name))
```

Expected output:

```text
<class 'str'>
```

## 12.12 What is input()?

The `input()` function accepts text entered by a user through the terminal.

Example:

```python
student_name = input("Enter your name: ")
print(student_name)
```

Possible terminal interaction:

```text
Enter your name: Anu
Anu
```

Explanation:

- `input()` displays the prompt.
- The user types a value.
- Python reads the entered value.
- The entered value is returned as a string.
- The returned string is assigned to `student_name`.
- `print()` displays the stored value.

Important:

Even if a user enters digits, `input()` returns text.

## 12.13 Example 6 — accept a student's name

Code:

```python
student_name = input("Enter student name: ")
print("Student name:", student_name)
```

Example interaction:

```text
Enter student name: Anu
Student name: Anu
```

The comma in `print()` allows us to display multiple values separated by a space by default.

## 12.14 Example 7 — accept a number and convert it

Task:

Ask the student for their age and display the age next year.

Code:

```python
age_text = input("Enter your age: ")
age = int(age_text)
next_year_age = age + 1

print("Next year age:", next_year_age)
```

Example interaction:

```text
Enter your age: 20
Next year age: 21
```

Line-by-line explanation:

1. `input()` reads the entered value as text.
2. The text is stored in `age_text`.
3. `int(age_text)` converts valid whole-number text into an integer.
4. The integer is stored in `age`.
5. Python adds one to the age.
6. The result is stored in `next_year_age`.
7. `print()` displays the result.

## 12.15 Why do we need int()?

The `int()` function converts a suitable value into an integer.

Without conversion, Python would be working with text.

For example, text values are not added in the same way as numbers.

Try this:

```python
first_value = "10"
second_value = "20"

print(first_value + second_value)
```

Expected output:

```text
1020
```

Why?

Both values are strings.

The plus operator joins the strings.

Now try:

```python
first_value = int("10")
second_value = int("20")

print(first_value + second_value)
```

Expected output:

```text
30
```

Why?

Both values are now integers, so the plus operator performs numeric addition.

## 12.16 What is float()?

The `float()` function converts a suitable value into a decimal number.

Example:

```python
percentage_text = "86.5"
percentage = float(percentage_text)

print(percentage)
print(type(percentage))
```

Expected output:

```text
86.5
<class 'float'>
```

Use `float()` when the value may contain a decimal part.

## 12.17 Common input conversion error

If the user enters:

`twenty`

then this code cannot convert it to an integer:

```python
age = int(input("Enter age: "))
```

Python raises a `ValueError`.

A ValueError means the value has the correct general type of input for the operation, but its content is not acceptable for that conversion.

We will study exception handling on Day 5.

For today, remember to enter a valid whole number when the program asks for an age.

# 13. Basic operators

An operator is a symbol or keyword that performs an operation on values.

## 13.1 Arithmetic operators

| Operator | Meaning | Example | Result |
|---|---|---|---:|
| + | Addition | 10 + 5 | 15 |
| - | Subtraction | 10 - 5 | 5 |
| * | Multiplication | 10 * 5 | 50 |
| / | Division | 10 / 5 | 2.0 |
| // | Floor division | 11 // 5 | 2 |
| % | Remainder | 11 % 5 | 1 |
| ** | Power | 2 ** 3 | 8 |

## 13.2 Example 8 — calculate total marks

Task:

Calculate the total of three subject marks.

Code:

```python
python_marks = 80
math_marks = 75
english_marks = 90

total_marks = python_marks + math_marks + english_marks

print("Total marks:", total_marks)
```

Expected output:

```text
Total marks: 245
```

Explanation:

- Each subject mark is stored separately.
- The plus operator adds the three values.
- The result is assigned to `total_marks`.
- The result is displayed.

## 13.3 Example 9 — calculate average marks

Code:

```python
total_marks = 245
number_of_subjects = 3

average_marks = total_marks / number_of_subjects

print("Average marks:", average_marks)
```

Expected output:

```text
Average marks: 81.66666666666667
```

Explanation:

- The slash operator performs division.
- Python returns a floating-point result for this division.
- We will learn formatting later in the pathway.

## 13.4 Comparison operators

Comparison operators compare values and produce a Boolean result.

| Operator | Meaning |
|---|---|
| == | Equal to |
| != | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |

Important:

A single `=` assigns a value.

Two equal signs `==` compare values.

## 13.5 Example 10 — compare a mark

Code:

```python
student_mark = 75
pass_mark = 40

print(student_mark >= pass_mark)
```

Expected output:

```text
True
```

Explanation:

- Python compares 75 with 40.
- 75 is greater than or equal to 40.
- The comparison result is `True`.
- Boolean values are written as `True` and `False` with capital first letters.

# 14. Basic decision-making with if and else

## 14.1 Why do we need decisions?

A program sometimes needs to choose what to do based on a condition.

Example:

If a student's mark is 40 or higher, display "Pass".

Otherwise, display "Fail".

The program needs a decision.

## 14.2 Understand the condition

A condition is an expression that evaluates to true or false.

Example:

`student_mark >= 40`

If the mark is 75, the condition is true.

If the mark is 25, the condition is false.

## 14.3 Example 11 — pass or fail

Code:

```python
student_mark = 75

if student_mark >= 40:
    print("Pass")
else:
    print("Fail")
```

Expected output:

```text
Pass
```

Line-by-line explanation:

1. The student's mark is stored in a variable.
2. Python checks the condition after `if`.
3. If the condition is true, Python executes the indented block below `if`.
4. If the condition is false, Python executes the indented block below `else`.
5. Only one of these two blocks runs in this example.

## 14.4 Why indentation matters

Python uses indentation to identify a block of code.

Correct:

```python
if student_mark >= 40:
    print("Pass")
```

Incorrect:

```python
if student_mark >= 40:
print("Pass")
```

The second example has no indentation for the statement inside the if block.

Python will report an indentation-related error.

Use consistent indentation. Four spaces are the common convention.

## 14.5 Example 12 — take marks from the user

Code:

```python
mark_text = input("Enter your mark: ")
mark = int(mark_text)

if mark >= 40:
    print("You passed")
else:
    print("You did not pass")
```

Example interaction:

```text
Enter your mark: 75
You passed
```

Try entering 25.

Expected output:

```text
You did not pass
```

## 14.6 What is elif?

`elif` means "else if".

It allows us to check another condition when the earlier condition is false.

Example:

```python
mark = 85

if mark >= 90:
    print("Grade A")
elif mark >= 75:
    print("Grade B")
elif mark >= 40:
    print("Pass")
else:
    print("Fail")
```

Expected output:

```text
Grade B
```

Python checks the conditions from top to bottom.

When it finds the first true condition, it executes that block and skips the remaining branches.

# 15. Basic repetition with loops

## 15.1 Why do we need a loop?

Imagine you need to display the word "Study" five times.

You could write five print statements.

That would work, but it repeats the same instruction.

A loop allows a program to repeat an instruction.

## 15.2 What is a for loop?

A `for` loop repeats a block of code for each item in a sequence or iterable.

For today's beginner example, we will use `range()`.

## 15.3 Example 13 — repeat a message

Code:

```python
for number in range(5):
    print("Study Python")
```

Expected output:

```text
Study Python
Study Python
Study Python
Study Python
Study Python
```

Explanation:

- `for` begins the loop.
- `number` is the loop variable.
- `range(5)` produces five values: 0, 1, 2, 3 and 4.
- The indented print statement runs once for each value.
- The message is displayed five times.

The variable `number` is not used in the output, but it receives each value during the loop.

## 15.4 Example 14 — display numbers

Code:

```python
for number in range(1, 6):
    print(number)
```

Expected output:

```text
1
2
3
4
5
```

Why does 6 not appear?

The ending value supplied to `range()` is excluded.

So `range(1, 6)` produces 1 through 5.

## 15.5 What is a while loop?

A `while` loop repeats a block while its condition remains true.

Example:

```python
count = 1

while count <= 3:
    print(count)
    count = count + 1
```

Expected output:

```text
1
2
3
```

Explanation:

1. The variable starts at 1.
2. Python checks whether count is less than or equal to 3.
3. The value is displayed.
4. One is added to count.
5. Python checks the condition again.
6. When count becomes 4, the condition is false.
7. The loop stops.

## 15.6 What is an infinite loop?

An infinite loop is a loop that does not reach its stopping condition.

For example, if the value of `count` is never increased in the previous while loop, the condition may remain true forever.

Always understand what changes the loop condition.

# 16. How Python fits into an AI application

A simple AI application may contain several parts.

1. A user interface accepts the user's question.
2. Python receives the input.
3. Python validates the input.
4. Python prepares the request.
5. Python communicates with an AI model service.
6. Python receives the response.
7. Python checks or formats the response.
8. The application displays the result.

Today we only practise the early programming foundations.

We will connect to model APIs later, after learning the required concepts.

## 16.1 Simple architecture diagram

`User → Application interface → Python backend → AI model service → Python backend → User`

## 16.2 Why not write everything in one file forever?

A tiny beginner program can fit in one file.

As an application grows, putting every feature in one large file becomes difficult to understand and maintain.

Developers gradually separate responsibilities into modules and packages.

We will learn modules and packages on Day 5.

Today, use one file so that you can focus on the basic Python statements.

# 17. Python methods and functions — what should a beginner know today?

The syllabus introduces functions in detail on Day 3.

Today, we only need to understand the functions used in our beginner examples.

## 17.1 What is a function?

A function is a reusable block of code that performs a task.

Python provides built-in functions.

Examples used today:

- `print()`: displays information.
- `input()`: reads text entered by the user.
- `type()`: tells us the type of a value.
- `int()`: converts a suitable value to an integer.
- `float()`: converts a suitable value to a floating-point number.
- `range()`: produces a sequence of numbers commonly used in loops.

## 17.2 Function call anatomy

Example:

```python
print("Welcome")
```

- `print` is the function name.
- Parentheses indicate a function call.
- `"Welcome"` is the argument supplied to the function.
- The function performs its task.

An argument is a value supplied when calling a function.

A parameter is a named input in a function definition. We will study parameters properly on Day 3.

## 17.3 print() beginner guide

Purpose:

Display values.

Example:

```python
print("Hello")
print(100)
print(True)
```

Output:

```text
Hello
100
True
```

The function can display strings, numbers and Boolean values.

## 17.4 input() beginner guide

Purpose:

Read text from the user.

Example:

```python
city = input("Enter your city: ")
print("Your city is", city)
```

The returned value is a string.

Convert the value when a numeric calculation is required.

## 17.5 type() beginner guide

Purpose:

Inspect the type of a value.

Example:

```python
value = 25
print(type(value))
```

Output:

```text
<class 'int'>
```

This is useful when debugging unexpected values.

## 17.6 int() beginner guide

Purpose:

Convert a suitable value into an integer.

Example:

```python
number = int("25")
print(number + 5)
```

Output:

```text
30
```

If the text is not a valid integer representation, Python raises an error.

## 17.7 float() beginner guide

Purpose:

Convert a suitable value into a decimal number.

Example:

```python
price = float("99.50")
print(price)
```

Output:

```text
99.5
```

## 17.8 range() beginner guide

Purpose:

Produce a sequence of integers.

Example:

```python
for day in range(1, 4):
    print(day)
```

Output:

```text
1
2
3
```

The stop value 4 is excluded.

## 17.9 Important difference: function vs method

A function can be called by its name.

A method is a function associated with an object or type.

Example of a built-in function:

```python
print("hello")
```

Example of a string method:

```python
course_name = "python"
print(course_name.upper())
```

Output:

```text
PYTHON
```

Here, `upper()` is a string method.

We will study string methods and other data-structure methods on Day 2.

Do not try to memorize every Python method today.

Learn each method when the relevant topic is taught, with its purpose, syntax, input, output and limitations.

# 18. Mini-project — AI Application Development Concept Explorer

**Approved project title:** AI Application Development Concept Explorer

## 18.1 Project objective

Create a small Python program that displays basic information about the GenAI and Agentic AI development pathway.

This project is intentionally simple.

It checks whether you can:

- Store text in variables.
- Display information using `print()`.
- Accept a simple user choice.
- Use a condition.
- Display a relevant explanation.

Do not connect to an LLM API today.

## 18.2 Problem statement

A college student is exploring AI application development.

The student wants a small terminal program that explains the difference between a GenAI application and an Agentic AI application.

Build a menu-based concept explorer.

## 18.3 Functional requirements

The program should:

1. Display a welcome message.
2. Display two choices.
3. Ask the student to select a choice.
4. Display an explanation for the selected choice.
5. Display a helpful message for an invalid choice.

## 18.4 Beginner implementation — build one step at a time

### Step 1 — display the title

Code:

```python
print("AI Application Development Concept Explorer")
```

Expected output:

```text
AI Application Development Concept Explorer
```

Explanation:

This is the title of the program.

### Step 2 — display the choices

Code:

```python
print("1. Generative AI")
print("2. Agentic AI")
```

Expected output:

```text
1. Generative AI
2. Agentic AI
```

Explanation:

The user can now see the available choices.

### Step 3 — accept the user's choice

Code:

```python
choice = input("Enter your choice (1 or 2): ")
```

Explanation:

- `input()` asks the user to enter a value.
- The entered value is stored in `choice`.
- The value is text, even when the user enters 1 or 2.

### Step 4 — check the choice

Code:

```python
if choice == "1":
    print("Generative AI creates content such as text or code.")
elif choice == "2":
    print("Agentic AI can use tools and follow steps toward a goal.")
else:
    print("Please enter 1 or 2.")
```

Explanation:

- `if` checks whether the choice is the text "1".
- `elif` checks whether the choice is the text "2" if the first condition is false.
- `else` handles every other value.
- The comparison uses `==`.
- The values are written as strings because `input()` returns text.

### Step 5 — combine the steps

Complete beginner version:

```python
print("AI Application Development Concept Explorer")
print("---------------------------------------------")

print("1. Generative AI")
print("2. Agentic AI")

choice = input("Enter your choice (1 or 2): ")

if choice == "1":
    print("Generative AI creates content such as text or code.")
elif choice == "2":
    print("Agentic AI can use tools and follow steps toward a goal.")
else:
    print("Please enter 1 or 2.")
```

## 18.5 Example run — choice 1

```text
AI Application Development Concept Explorer
---------------------------------------------
1. Generative AI
2. Agentic AI
Enter your choice (1 or 2): 1
Generative AI creates content such as text or code.
```

## 18.6 Example run — choice 2

```text
AI Application Development Concept Explorer
---------------------------------------------
1. Generative AI
2. Agentic AI
Enter your choice (1 or 2): 2
Agentic AI can use tools and follow steps toward a goal.
```

## 18.7 Example run — invalid choice

```text
AI Application Development Concept Explorer
---------------------------------------------
1. Generative AI
2. Agentic AI
Enter your choice (1 or 2): 5
Please enter 1 or 2.
```

## 18.8 Understand the complete program

| Code part | Responsibility |
|---|---|
| First print | Displays the program title |
| Choice print statements | Shows available options |
| input() | Reads the user's selection |
| if | Checks the first choice |
| elif | Checks the second choice |
| else | Handles an unsupported choice |
| print inside each branch | Displays the matching explanation |

## 18.9 Test cases

| Test | Input | Expected behavior |
|---|---|---|
| 1 | 1 | Displays the Generative AI explanation |
| 2 | 2 | Displays the Agentic AI explanation |
| 3 | 5 | Displays the invalid-choice message |
| 4 | hello | Displays the invalid-choice message |
| 5 | Empty input | Displays the invalid-choice message |

## 18.10 Common mistakes

**Mistake 1: Using `=` instead of `==` in a condition**

Incorrect:

```python
if choice = "1":
    print("Generative AI")
```

Correct:

```python
if choice == "1":
    print("Generative AI")
```

Reason:

`=` assigns a value.

`==` compares two values.

**Mistake 2: Forgetting quotation marks**

Incorrect:

```python
if choice == 1:
    print("Generative AI")
```

This compares a string with an integer. It will not match the string "1".

Correct:

```python
if choice == "1":
    print("Generative AI")
```

**Mistake 3: Incorrect indentation**

Incorrect:

```python
if choice == "1":
print("Generative AI")
```

Correct:

```python
if choice == "1":
    print("Generative AI")
```

**Mistake 4: Wrong spelling of a variable**

If you create `choice` but later write `choices`, Python treats them as different names.

Use the same variable name consistently.

## 18.11 Independent improvements

Try these changes yourself:

1. Add a third option called "Traditional Software".
2. Add an explanation for the third option.
3. Change the welcome message.
4. Add your own name to the welcome message.
5. Test the program with an invalid value.
6. Explain why the program uses string values for choices.

Do not add API calls or agent frameworks. Those topics belong to later days.

# 19. Development environment troubleshooting

## 19.1 Problem: python command is not recognized

Possible reasons:

- Python is not installed.
- Python was installed but not added to PATH.
- The terminal was open before installation and needs to be reopened.
- The system uses `py` or `python3` instead of `python`.

What to check:

1. Confirm Python installation.
2. Close and reopen the terminal.
3. Try the operating-system-appropriate version command.
4. Check the official installation instructions.
5. Ask the trainer for help if the command still fails.

## 19.2 Problem: VS Code does not show Python as the selected interpreter

Possible reasons:

- The Python extension is missing.
- Python is not installed.
- VS Code has not detected the installation.
- The wrong project environment is selected.

What to do:

1. Install or enable the Python extension.
2. Open the project folder.
3. Open the Command Palette.
4. Search for the Python interpreter selection command.
5. Select the intended Python installation.

## 19.3 Problem: file does not run

Check:

- Did you save the file?
- Is the file extension `.py`?
- Are you running the correct file?
- Is the terminal in the correct project folder?
- Does the code contain a syntax error?
- Did you select the correct Python interpreter?

## 19.4 Problem: output is different from expected

Do not immediately rewrite the complete program.

Check one thing at a time:

1. Check the input.
2. Check the variable values.
3. Check the condition.
4. Check the spelling.
5. Check the indentation.
6. Read the complete error message.
7. Run the smallest example that reproduces the problem.

This is a beginner debugging habit.

# 20. Industry thinking — choosing a simple solution first

Imagine a business wants to add the total of five invoice amounts.

A normal Python calculation may be the best solution.

There is no need to ask an LLM to perform simple arithmetic if deterministic code can do it accurately and transparently.

Now imagine the business wants to summarize the descriptions of hundreds of customer complaints.

An LLM may be useful for language understanding and summarization, with suitable validation.

The lesson:

**Use the simplest reliable tool that solves the problem.**

AI is useful when its capabilities are needed. It is not a replacement for every normal programming operation.

# 21. Interview preparation inside the class notes

## 21.1 How should a fresher explain an AI application?

Suggested answer:

"An AI application is a software application that uses an AI model or technique to perform a task such as classification, prediction, language understanding or content generation. For example, a document assistant can use an AI model to answer questions about supplied documents."

## 21.2 How should a fresher explain Generative AI?

Suggested answer:

"Generative AI creates new content such as text, code, images or audio based on learned patterns and the user's instructions. A chatbot that generates an explanation is one example."

## 21.3 How should a fresher explain Agentic AI?

Suggested answer:

"Agentic AI systems can work toward a goal through multiple steps. They may use approved tools, observe results and continue a controlled workflow. For example, an agent can read a supplied report, calculate information using Python and prepare a summary."

## 21.4 How should a fresher explain Python's role?

Suggested answer:

"Python is the programming language used to build the application logic. It can accept user input, validate data, call AI services, process responses, connect to databases and expose APIs."

## 21.5 Interview speaking method

When answering a technical question, use this sequence:

1. Give a direct definition.
2. Explain why it is useful.
3. Give one simple example.
4. Mention one limitation or practical consideration.
5. Stop and allow the interviewer to ask a follow-up.

Avoid giving a memorized paragraph that you do not understand.

# 22. Day 1 revision sheet

- Software is a set of instructions used to perform tasks.
- An application is software designed for a user need.
- An AI application includes an AI capability.
- AI is a broad field.
- Machine Learning is one approach within AI.
- Deep Learning is one approach within Machine Learning.
- Generative AI creates content.
- An LLM is a Large Language Model.
- Agentic AI systems can work through controlled steps and use tools.
- A chatbot and an agent are not automatically the same thing.
- Python is a programming language.
- Python is not itself an LLM.
- VS Code is a code editor.
- The terminal accepts commands.
- The Python interpreter executes Python code.
- A `.py` file contains Python source code.
- `print()` displays information.
- `input()` reads text from the user.
- `type()` checks a value's type.
- `int()` converts a suitable value to an integer.
- `float()` converts a suitable value to a decimal number.
- A variable is a name associated with a value.
- A string stores text.
- An integer stores a whole number.
- A float stores a decimal number.
- A Boolean stores `True` or `False`.
- `=` assigns a value.
- `==` compares values.
- `if`, `elif` and `else` support decisions.
- A loop repeats a block of code.
- Indentation is meaningful in Python.
- Debugging means finding and fixing problems.
- A good developer chooses a simple and reliable solution.

# 23. Student self-check

Before marking Day 1 complete, answer these questions without looking at the notes:

1. What is software?
2. What makes an application an AI application?
3. What is Generative AI?
4. What does LLM stand for?
5. What is Agentic AI?
6. How is an agent different from a simple question-answer chatbot?
7. What is Python?
8. What is the purpose of VS Code?
9. What is the purpose of a terminal?
10. What does `print()` do?
11. What does `input()` return?
12. Why do we use `int()`?
13. What is the difference between `=` and `==`?
14. Why is indentation important?
15. When should we avoid using an AI model?

If you cannot answer a question, return to that section and run its example again.

# 24. Day 1 completion checklist

- [ ] I can explain software and an AI application.
- [ ] I can distinguish Generative AI from Agentic AI.
- [ ] I can explain the role of Python in an AI application.
- [ ] I installed or verified Python.
- [ ] I opened the project folder in VS Code.
- [ ] I created and ran a Python file.
- [ ] I used `print()` and `input()`.
- [ ] I created variables.
- [ ] I identified common data types.
- [ ] I used `int()` and `float()`.
- [ ] I used a comparison operator.
- [ ] I wrote a simple `if/else` statement.
- [ ] I read a simple `for` loop.
- [ ] I completed the Concept Explorer mini-project.
- [ ] I tested valid and invalid inputs.
- [ ] I can explain my project line by line.

**Day 1 is complete when you can run the mini-project and explain why each part is present.**

---

## Trainer note

Students may have different levels of previous Python exposure. Do not assume that a college student remembers syntax simply because Python was part of a previous subject.

Ask the learner to predict the output before running each example.

If the learner cannot explain a line, reduce the example to fewer lines and rebuild it.

Do not introduce API keys, paid model APIs, LangChain, LangGraph, vector databases or MCP on Day 1. These are later syllabus topics.

Preserve the approved Day 1 topic and project title.
