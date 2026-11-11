# Day 10 Interview Guide — SQL, Git, Virtual Environments, pytest and Debugging

## Q1. What is a relational database?
It stores structured data in tables with rows and columns. Relationships use keys. A primary key uniquely identifies a row.

## Q2. Primary key versus foreign key?
A primary key identifies a row in its own table. A foreign key references a key in another table to represent a relationship and support referential integrity.

## Q3. Explain SELECT, INSERT, UPDATE and DELETE.
SELECT reads; INSERT adds; UPDATE changes; DELETE removes rows. Always inspect WHERE conditions before UPDATE and DELETE; without WHERE, all rows may be affected.

## Q4. What is SQL injection and how do you prevent it?
It occurs when untrusted input changes the meaning of dynamically constructed SQL. Use parameterized queries rather than concatenating user input. Validation complements but does not replace parameterization.

## Q5. Why use a virtual environment?
It isolates project dependencies. .venv should not be committed; recreate it from dependency instructions.

## Q6. Git versus GitHub?
Git tracks changes locally. GitHub hosts repositories and supports collaboration. A commit records local history; push sends commits to a remote.

## Q7. Explain add, commit and push.
add stages selected changes; commit records staged changes; push uploads local commits to a remote. Inspect git status before committing.

## Q8. What is pytest?
A Python test framework that discovers tests and checks assertions. Cover normal, boundary and invalid behaviour. Passing tests do not prove absence of all defects.

## Q9. Why use SQL placeholders?
They bind values separately from SQL syntax, reducing injection risk and handling quoting. Dynamic table/column identifiers need strict allow-list handling rather than ordinary value placeholders.

## Q10. Why is Day 10 API more durable than Day 9?
Day 9 used a Python dictionary that disappears on process restart. Day 10 uses SQLite, which persists records in a database file. SQLite is not automatically the best choice for every production workload.

## Practical task
Explain a POST request through FastAPI validation, parameterized SQL INSERT, transaction commit and JSON response. Describe how you would test it and track changes in Git.
