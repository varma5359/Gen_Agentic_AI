# Day 10 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** SQL Fundamentals, Relational Database Concepts, Git, GitHub, Virtual Environments, pytest and Debugging  
**Mini-project:** Version-Controlled Database-Connected Python API  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain relational databases and tables.

**Beginner answer:** A relational database stores structured information in tables. Rows represent records and columns represent fields.

**Example code**

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

**How it works:** The comments show a conceptual table. Each row is one student record.

**Important methods or syntax:** Database, table, row, column, primary key, foreign key, schema and constraints.

**Common mistake:** A database is more than a spreadsheet. It supports concurrent access, constraints and structured queries.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain select and where.

**Beginner answer:** SELECT reads data from a table. WHERE filters which rows are returned.

**Example code**

```python
SELECT name, department
FROM students
WHERE department = 'CSE';
```

**Expected output**

```text
Returns names and departments for rows whose department is CSE.
```

**How it works:** SELECT columns, WHERE conditions, ORDER BY, LIMIT and DISTINCT.

**Important methods or syntax:** Text values need quotes. Use parameters rather than string concatenation when passing user input from Python.

**Common mistake:** Write a query to list students in ECE ordered by name.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain insert, update and delete.

**Beginner answer:** These SQL statements change records. UPDATE and DELETE need careful filtering.

**Example code**

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

**How it works:** INSERT, UPDATE, DELETE, transactions, COMMIT and ROLLBACK.

**Important methods or syntax:** UPDATE or DELETE without a suitable WHERE clause can affect every row. Never practise destructive queries on production data.

**Common mistake:** Insert one sample student and update that student's department.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain keys and relationships.

**Beginner answer:** A primary key uniquely identifies a row. A foreign key links a record to another table.

**Example code**

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

**How it works:** The comments describe a many-to-many relationship through an enrollment table.

**Important methods or syntax:** One-to-one, one-to-many, many-to-many, primary key, foreign key and referential integrity.

**Common mistake:** Do not store a comma-separated list of course IDs in one student column when a relationship table is appropriate.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain git fundamentals.

**Beginner answer:** Git tracks changes to files over time. GitHub hosts repositories and collaboration tools; Git is the version-control system.

**Example code**

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

**How it works:** status, add, commit, log, diff, branch, switch, pull, push and .gitignore.

**Important methods or syntax:** A file must be staged before it is included in a commit. Never commit .env files, passwords or API keys.

**Common mistake:** Create a repository for your student API and commit a working version.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain virtual environments and pip.

**Beginner answer:** A virtual environment isolates project dependencies so packages for one project do not interfere with another.

**Example code**

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

**How it works:** python -m pip, pip list, pip show, pip freeze and requirements.txt. Select the correct interpreter in VS Code.

**Important methods or syntax:** If VS Code uses another interpreter, imports may appear missing. Activate the environment and select its Python interpreter.

**Common mistake:** Create .venv, install a package and verify the interpreter path.

**Follow-up:** Where would you use this in a Python AI application?


### Q7. Explain pytest and debugging.

**Beginner answer:** pytest runs test functions and checks assertions. Debugging finds the cause of unexpected behavior.

**Example code**

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

**How it works:** assert checks a condition. pytest discovers test functions beginning with test_ and reports failures.

**Important methods or syntax:** Fixtures, parametrized tests, mocks, integration tests and coverage as later topics.

**Common mistake:** Printing a value is not the same as asserting expected behavior. Test normal, boundary and invalid inputs.

**Follow-up:** Where would you use this in a Python AI application?



## 2. Understanding questions

1. Explain today's topic to a person who has never programmed.
2. Why is this concept useful in a real application?
3. What happens when the input is empty or invalid?
4. How would you make the example easier to read?
5. How would you test that the code works?
6. Which line would you change if the requirement changed?
7. What is one limitation of the beginner example?
8. How could this concept be used in a GenAI application?

## 3. Practical coding tasks

### Exercise 1 — Relational databases and tables

**Task:** Design a students table with id, name, email and department.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — SELECT and WHERE

**Task:** undefined

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — INSERT, UPDATE and DELETE

**Task:** undefined

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Keys and relationships

**Task:** Draw students, courses and enrollments and explain the foreign keys.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Git fundamentals

**Task:** undefined

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Virtual environments and pip

**Task:** undefined

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 7 — pytest and debugging

**Task:** Write tests for a function that accepts marks only from 0 to 100.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — Version-Controlled Database-Connected Python API

Be ready to explain:

1. What problem does the project solve?
2. Who would use it?
3. What input does it accept?
4. What processing does it perform?
5. What output does it produce?
6. Which Python concepts did you apply?
7. What error cases did you consider?
8. How did you test the project?
9. What would you improve next?
10. How could it become one component of a larger AI application?

## 5. Mock interview

**Interviewer:** Explain the main topic you learned today.

**Student:** Give a definition, describe the steps and show a small example.

**Interviewer:** Why did you choose this Python feature?

**Student:** Explain the problem it solves and why it is suitable.

**Interviewer:** What happens if the input is incorrect?

**Student:** Explain the likely error and how you would validate or handle the input.

**Interviewer:** How did you verify your program?

**Student:** Explain the test input, expected output, actual output and correction.

## 6. Communication checklist

- [ ] I answer the question directly.
- [ ] I explain technical words simply.
- [ ] I give a relevant example.
- [ ] I can read my code line by line.
- [ ] I can explain one error case.
- [ ] I can describe my mini-project honestly.

## 7. Self-assessment

| Skill | Rating |
|---|---:|
| Explain the concepts | /5 |
| Read the code | /5 |
| Write a small example | /5 |
| Debug an error | /5 |
| Explain the mini-project | /5 |
| Answer interview follow-ups | /5 |

**Trainer note:** A student is ready to move forward when they can explain the concept, modify a working example and solve a small task without copying the complete solution.


## Additional mentor-led interview drills

### How to answer a question when you are a beginner
1. Listen to the complete question.
2. Identify the exact Python feature being asked about.
3. Give a simple definition.
4. Explain the purpose before describing syntax.
5. Write the smallest example that demonstrates the feature.
6. Predict and explain its output.
7. Mention one limitation or common error.
8. Connect it to the day's mini-project.

### Interviewer follow-up ladder
- What problem does this feature solve?
- Can you explain it without using a technical definition?
- What is the smallest working example?
- What happens when the input changes?
- Does the operation change the original value or return a new value?
- What happens for empty or invalid input?
- How would you test this behavior?
- Where would you use it in a real application?
- What would you improve before production use?

### Practical communication drill
Ask the student to explain one code example in this order: input, variable, operation, output, error case and practical use. The student must not read the answer word for word. The trainer should ask one follow-up after each explanation.

### Code review drill
- Are names meaningful?
- Is each function focused on one task?
- Is the output predictable?
- Are invalid inputs considered?
- Are secrets kept outside source code?
- Can another beginner run the project using the README?
- Is there at least one test for normal behavior and one test for an edge case?

### Student reflection
Write down the question that was hardest to answer. Revisit the matching class-note section, create a smaller example and explain it again the next day.
