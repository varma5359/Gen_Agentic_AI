# Day 10 — SQL Fundamentals, Relational Database Concepts, Git, GitHub, Virtual Environments, pytest and Debugging

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** Version-Controlled Database-Connected Python API  
**Duration:** 2–3 hours  
**Audience:** College students and freshers  
**Level:** Beginner first, intermediate only after the basics

## How to use these notes

These notes assume that you may be learning the topic for the first time. You do not need to understand everything in one sitting.

1. Read the beginner explanation.
2. Type the code yourself. Do not only copy and paste.
3. Predict the output before running the code.
4. Run it and compare your prediction.
5. Change one value and run it again.
6. Explain the code in your own words.
7. Complete the practice task without looking at a solution.
8. Practise the interview question aloud.

**Teaching rule:** never introduce a complicated framework example before the student understands the plain Python operation underneath it.

## 1. Learning objectives

1. Explain relational databases and tables using a simple example.
2. Explain select and where using a simple example.
3. Explain insert, update and delete using a simple example.
4. Explain keys and relationships using a simple example.
5. Explain git fundamentals using a simple example.
6. Explain virtual environments and pip using a simple example.
7. Explain pytest and debugging using a simple example.
8. Apply relational databases and tables in the Version-Controlled Database-Connected Python API.
9. Apply select and where in the Version-Controlled Database-Connected Python API.
10. Apply insert, update and delete in the Version-Controlled Database-Connected Python API.
11. Apply keys and relationships in the Version-Controlled Database-Connected Python API.
12. Apply git fundamentals in the Version-Controlled Database-Connected Python API.
13. Apply virtual environments and pip in the Version-Controlled Database-Connected Python API.
14. Apply pytest and debugging in the Version-Controlled Database-Connected Python API.

## 2. Important vocabulary

| Term | Beginner meaning |
|---|---|
| Syntax | Rules for writing valid Python |
| Variable | A name referring to a value |
| Function | Reusable code that performs a task |
| Method | A function associated with an object |
| Argument | A value passed when calling a function |
| Return value | A result sent back to the caller |
| Exception | An event that interrupts normal execution |
| Debugging | Finding and fixing the cause of a problem |
| Input | Information supplied to a program |
| Output | Information produced by a program |

## 3. Class plan

| Activity | Time |
|---|---:|
| Concept explanation | 30–40 minutes |
| Trainer demonstration | 35–45 minutes |
| Student coding practice | 45–60 minutes |
| Mini-project | 30–40 minutes |
| Quiz and interview practice | 15–20 minutes |

## 3. Relational databases and tables

### Beginner explanation

A relational database stores structured information in tables. Rows represent records and columns represent fields.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
# students table
# id | name | department
# 1  | Anu  | CSE
# 2  | Ravi | ECE
print("A row represents one student")
print("A column represents one field")
```

**Expected output**

```text
A row represents one student
A column represents one field
```

### Walkthrough

The comments show a conceptual table. Each row is one student record.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Database, table, row, column, primary key, foreign key, schema and constraints.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A database is more than a spreadsheet. It supports concurrent access, constraints and structured queries.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Design a students table with id, name, email and department.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define relational databases and tables in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. SELECT and WHERE

### Beginner explanation

SELECT reads data from a table. WHERE filters which rows are returned.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
SELECT name, department
FROM students
WHERE department = 'CSE';
```

**Expected output**

```text
Returns names and departments for rows whose department is CSE.
```

### Walkthrough

SELECT columns, WHERE conditions, ORDER BY, LIMIT and DISTINCT.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Text values need quotes. Use parameters rather than string concatenation when passing user input from Python.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Write a query to list students in ECE ordered by name.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

undefined

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define select and where in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. INSERT, UPDATE and DELETE

### Beginner explanation

These SQL statements change records. UPDATE and DELETE need careful filtering.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
INSERT INTO students (id, name, department)
VALUES (3, 'Sara', 'CSE');
UPDATE students
SET department = 'IT'
WHERE id = 3;
```

**Expected output**

```text
The example inserts Sara and then changes her department to IT.
```

### Walkthrough

INSERT, UPDATE, DELETE, transactions, COMMIT and ROLLBACK.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

UPDATE or DELETE without a suitable WHERE clause can affect every row. Never practise destructive queries on production data.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Insert one sample student and update that student's department.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

undefined

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define insert, update and delete in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Keys and relationships

### Beginner explanation

A primary key uniquely identifies a row. A foreign key links a record to another table.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
-- students(id, name)
-- courses(id, title)
-- enrollments(student_id, course_id)
-- enrollments.student_id references students.id
-- enrollments.course_id references courses.id
SELECT 'Keys connect related records';
```

**Expected output**

```text
Keys connect related records
```

### Walkthrough

The comments describe a many-to-many relationship through an enrollment table.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

One-to-one, one-to-many, many-to-many, primary key, foreign key and referential integrity.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not store a comma-separated list of course IDs in one student column when a relationship table is appropriate.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Draw students, courses and enrollments and explain the foreign keys.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define keys and relationships in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Git fundamentals

### Beginner explanation

Git tracks changes to files over time. GitHub hosts repositories and collaboration tools; Git is the version-control system.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
git init
git status
git add .
git commit -m "Initial project"
```

**Expected output**

```text
Commands initialize a repository, show changes, stage files and create a commit.
```

### Walkthrough

status, add, commit, log, diff, branch, switch, pull, push and .gitignore.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

A file must be staged before it is included in a commit. Never commit .env files, passwords or API keys.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Create a repository for your student API and commit a working version.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

undefined

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define git fundamentals in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. Virtual environments and pip

### Beginner explanation

A virtual environment isolates project dependencies so packages for one project do not interfere with another.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
python -m venv .venv
# Windows PowerShell:
.venv\\Scripts\\Activate.ps1
# macOS/Linux:
source .venv/bin/activate
python -m pip install fastapi uvicorn
```

**Expected output**

```text
The commands create and activate an environment and install packages into it.
```

### Walkthrough

python -m pip, pip list, pip show, pip freeze and requirements.txt. Select the correct interpreter in VS Code.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

If VS Code uses another interpreter, imports may appear missing. Activate the environment and select its Python interpreter.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Create .venv, install a package and verify the interpreter path.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

undefined

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define virtual environments and pip in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 9. pytest and debugging

### Beginner explanation

pytest runs test functions and checks assertions. Debugging finds the cause of unexpected behavior.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
# test_math.py
def add(a, b):
    return a + b
def test_add():
    assert add(2, 3) == 5
# Run: pytest -q
```

**Expected output**

```text
1 passed
```

### Walkthrough

assert checks a condition. pytest discovers test functions beginning with test_ and reports failures.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Fixtures, parametrized tests, mocks, integration tests and coverage as later topics.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Printing a value is not the same as asserting expected behavior. Test normal, boundary and invalid inputs.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write tests for a function that accepts marks only from 0 to 100.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define pytest and debugging in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 10. Guided mini-project — Version-Controlled Database-Connected Python API

## Business situation

A beginner AI application developer must be able to organize information, process it and explain what the program does. In this project, build a small working program using only concepts covered in today's lesson.

## Requirements

- Create a project folder and a Python file.
- Define small sample data.
- Apply at least three concepts from this lesson.
- Display a clear result.
- Handle one invalid or missing value where appropriate.
- Use meaningful variable names.
- Explain the program line by line.

## Suggested folder structure

```text
day_10_project/
    main.py
    README.md
    sample_data/
```

## Build in small steps

1. Create main.py.
2. Add two or three sample records.
3. Write one small operation.
4. Run the program and inspect the output.
5. Add the next operation only after the first works.
6. Test an unusual input.
7. Explain input, processing and output to your trainer.

## Student submission checklist

- [ ] Program runs without syntax errors.
- [ ] I can explain every line I wrote.
- [ ] I used meaningful names.
- [ ] I tested a normal input.
- [ ] I tested an unusual input.
- [ ] I can explain one limitation.
- [ ] I saved the project in the correct folder.

# 11. Daily revision questions

1. What is relational databases and tables?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is select and where?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is insert, update and delete?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is keys and relationships?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is git fundamentals?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is virtual environments and pip?
6.1 Why would a Python developer use it?
6.2 What mistake should a beginner avoid?

7. What is pytest and debugging?
7.1 Why would a Python developer use it?
7.2 What mistake should a beginner avoid?

# 12. Daily quiz

1. Which concept from today's lesson would you use for the sample problem?
2. What does the main method or function in one example do?
3. What happens if the input is missing or invalid?
4. Why should code be divided into small understandable steps?
5. Give one use of today's concepts in an AI application.

**Answer method:** answer in your own words, then prove your understanding with a small code example.

# 13. Interview practice

1. Explain relational databases and tables to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain select and where to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain insert, update and delete to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain keys and relationships to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain git fundamentals to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain virtual environments and pip to a beginner.
6.1 Give a practical example.
6.2 What is one limitation or common error?

7. Explain pytest and debugging to a beginner.
7.1 Give a practical example.
7.2 What is one limitation or common error?

## How to structure an interview answer

1. Give a direct definition.
2. Explain how it works in two or three steps.
3. Give a small example.
4. Mention one real use.
5. Mention one limitation or error case.

# 14. Trainer assessment rubric

| Area | Evidence |
|---|---|
| Concept understanding | Student explains without reading |
| Code reading | Student describes important lines |
| Practical execution | Student runs and modifies code |
| Debugging | Student locates a simple error |
| Project | Student applies the day's concepts |
| Interview communication | Student gives a clear structured answer |

# 15. What you should remember

- Understand why a feature is used before memorizing syntax.
- Type and run each example yourself.
- Know the difference between a function, method, argument and return value.
- Read error messages instead of guessing.
- Build the project in small steps.
- Be ready to teach the concept to another beginner.

**Day 10 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.
