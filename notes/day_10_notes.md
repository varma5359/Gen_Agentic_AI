# Day 10 — SQL fundamentals, relational database concepts, Git, GitHub, virtual environments, pytest and debugging.

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours  
**Level:** Intermediate

> **Self-learning instruction:** Read one section at a time. Type the code yourself, run it and compare the result. These notes are designed to teach without a trainer or video.

## 1. Understand the topic

A relational database stores records in tables. A row is a record; a column is an attribute. A primary key uniquely identifies a row; a foreign key references another table. SELECT reads, INSERT adds, UPDATE changes and DELETE removes. Use parameterized queries. Git tracks changes; GitHub hosts repositories. A virtual environment isolates dependencies; pytest runs tests.

## 2. Why this matters in an AI application

A GenAI application is still software. It needs input handling, business logic, APIs, data, validation, security, tests and deployment. Today's concepts are building blocks for those responsibilities. A small example demonstrates one concept; it is not automatically production-ready.

## 3. Guided coding walkthrough

### Step 1 — Understand the task

Read the code and predict the output. Identify the input, the main operation and the value produced.

### Step 2 — Code

~~~python
import sqlite3
connection = sqlite3.connect("students.db")
cursor = connection.cursor()
cursor.execute("CREATE TABLE IF NOT EXISTS students (id INTEGER PRIMARY KEY, name TEXT NOT NULL, email TEXT UNIQUE NOT NULL)")
cursor.execute("INSERT INTO students (id, name, email) VALUES (?, ?, ?)", (1, "Asha Rao", "asha@example.com"))
connection.commit()
cursor.execute("SELECT id, name, email FROM students WHERE email = ?", ("asha@example.com",))
print(cursor.fetchone())
connection.close()
~~~

### Step 3 — Expected output

~~~text
(1, 'Asha Rao', 'asha@example.com')
~~~

### Step 4 — Explain the code line by line

- ? placeholders separate SQL structure from values and help prevent injection.
- commit saves the write; fetchone returns one row.
- Git workflow: git status, git add, git commit, git push.
- pytest discovers test_*.py and test_ functions.
- Read tracebacks, reproduce the smallest failure, fix the cause and add a regression test.

### Step 5 — Interpret the result

Answer in your own words: What input did the program receive? What operation did it perform? What result did it produce? What would change if the input changed? What should be validated before using this in a larger application?

## 4. Common mistakes and troubleshooting

- Read the complete traceback and identify the exception type and line.
- Confirm the active Python interpreter, installed packages, current folder and filename.
- Check types, missing values, boundaries and external response formats.
- Reduce a complex failure to the smallest reproducible example.
- Fix the cause rather than hiding errors with broad exception handling.

## 5. Independent practice

1. Recreate the example from a blank file.
2. Change at least two inputs and predict the output before running.
3. Add one validation or failure case relevant to this topic.
4. Explain the changed output in your own words.
5. Save the code in a clearly named project folder.

## 6. Interview-ready summary

- Define the concept directly.
- Explain the problem it solves.
- Explain when to use it and when a simpler approach is better.
- Give one practical AI-application example.
- Mention one limitation or common failure mode.

## 7. Completion checklist

- [ ] I can explain the concept without copying the definition.
- [ ] I typed and ran the example.
- [ ] I understand the expected output.
- [ ] I completed the independent practice.
- [ ] I can identify and fix a common error.
- [ ] I am ready to attempt the approved project.
