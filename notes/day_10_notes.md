# Day 10 — SQL fundamentals, relational database concepts, Git, GitHub, virtual environments, pytest and debugging

**Phase 1 | 2–3 hours | Project: Version-Controlled Database-Connected Python API**

## Learning objectives
Explain relational tables and keys; write basic SQL; connect Python to SQLite with parameterized queries; create virtual environments; use Git status/add/commit/push; write pytest tests; debug systematically.

## 1. Why databases?
Day 9 stored students in a Python dictionary. Restart the server and those records disappear. A database stores data persistently and provides querying, constraints and transaction support.

A relational database stores tables. A row is a record; a column is a field. A primary key uniquely identifies a row. A foreign key refers to a key in another table.

## 2. SQL basics
~~~sql
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    course TEXT NOT NULL
);

INSERT INTO students (id, name, course)
VALUES (1, 'Asha', 'GenAI');

SELECT id, name, course FROM students;

UPDATE students
SET course = 'Agentic AI'
WHERE id = 1;

DELETE FROM students
WHERE id = 1;
~~~

CREATE TABLE defines structure. INSERT adds a row. SELECT reads rows. UPDATE changes matching rows. DELETE removes matching rows. Always inspect WHERE conditions before UPDATE or DELETE; without WHERE, every row may be affected.

## 3. Filtering, sorting and aggregation
~~~sql
SELECT name, course
FROM students
WHERE course = 'GenAI'
ORDER BY name ASC;

SELECT COUNT(*) AS student_count FROM students;
~~~

WHERE filters rows. ORDER BY sorts results. COUNT counts rows. Other aggregates include SUM, AVG, MIN and MAX.

## 4. SQLite from Python
SQLite is a lightweight relational database included in Python's standard library. It is suitable for learning and some local applications. PostgreSQL/MySQL may be better for larger deployed systems.

~~~python
import sqlite3

connection = sqlite3.connect("students.db")
cursor = connection.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS students (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    course TEXT NOT NULL
)
""")

cursor.execute(
    "INSERT INTO students (name, course) VALUES (?, ?)",
    ("Asha", "GenAI")
)
connection.commit()

cursor.execute("SELECT id, name, course FROM students")
for row in cursor.fetchall():
    print(row)

connection.close()
~~~

Question-mark placeholders bind values safely. Never build SQL by concatenating user input; that creates SQL injection risk. commit saves changes. close releases the connection. Production code should use clear transaction and cleanup patterns.

## 5. Virtual environments
A virtual environment isolates dependencies for one project.

~~~bash
python -m venv .venv
~~~

Activation:
- Windows PowerShell: .venv\Scripts\Activate.ps1
- Windows Command Prompt: .venv\Scripts\activate.bat
- macOS/Linux: source .venv/bin/activate

Install packages with python -m pip install package-name. Inspect with python -m pip list. Leave using deactivate. Do not commit .venv; recreate it from dependency instructions.

## 6. Git and GitHub
Git tracks file changes locally. GitHub hosts Git repositories and supports collaboration.

~~~bash
git init
git status
git add .
git commit -m "Add student API"
~~~

init creates a repository. status shows changes. add stages files for the next commit. commit records staged changes in local history.

Connect a remote after creating the repository:
~~~bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git branch -M main
git push -u origin main
~~~

Replace placeholders with your actual repository URL. A commit does not automatically upload; push sends commits to the remote. Review staged files before committing.

Add sensitive/generated paths to .gitignore:
~~~text
.venv/
__pycache__/
.pytest_cache/
*.pyc
.env
*.db
~~~

Never commit credentials, private data or local database files containing real user records.

## 7. pytest
pytest discovers test functions named test_* in test files.

Install:
~~~bash
python -m pip install pytest
~~~

Create test_math.py:
~~~python
def add(a, b):
    return a + b

def test_add_two_numbers():
    assert add(2, 3) == 5

def test_add_negative_number():
    assert add(-2, 2) == 0
~~~

Run pytest -q. assert checks actual versus expected behaviour. Include normal, boundary and invalid cases. Passing tests do not prove there are no bugs; they provide evidence for the behaviours covered.

## 8. Debugging workflow
1. Reproduce the failure.
2. Read the complete traceback.
3. Identify the failing line and exception.
4. Inspect inputs and types.
5. Reduce to a small example.
6. Fix one cause at a time.
7. Run the failing test again.
8. Run the full test suite.
9. Record cause and prevention.

## 9. Industry scenario
A student API needs persistent records. SQL stores them; Python handles logic; tests verify rules; Git tracks changes; a virtual environment isolates dependencies. This is a small version of a professional workflow.

## 10. Common mistakes
| Mistake | Impact | Prevention |
|---|---|---|
| UPDATE/DELETE without WHERE | All rows may change | Inspect query on sample data |
| SQL concatenation with user input | Injection risk | Parameterized queries |
| Forget commit | Changes may not persist | Commit successful writes |
| Install packages globally | Dependency conflicts | Use venv |
| Commit .venv or secrets | Leak or repository bloat | .gitignore and review status |
| Test only happy path | Defects remain | Add boundary and invalid tests |
| Treat passing tests as proof | False confidence | Combine tests, review and monitoring |

## 11. Exercises
1. Create students table and insert two rows.
2. Select with WHERE and ORDER BY.
3. Update one row with WHERE.
4. Delete one sample row.
5. Write a function and two pytest tests.
6. Create a venv and install pytest.
7. Initialise Git, inspect status, stage and commit.
8. Explain parameterized SQL.

## 12. Five-question quiz
1. What uniquely identifies a row? A Primary key B Table name C Variable D HTTP header. **Answer A.**
2. SELECT: A deletes B reads C updates D creates user. **Answer B.**
3. SQL placeholders provide: A safe value binding B encryption C routing D deployment. **Answer A.**
4. git commit: A uploads automatically B records staged changes C installs Python D runs tests. **Answer B.**
5. pytest discovers: A every text file B test functions in test files C only notebooks D database tables. **Answer B.**

## 13. Phase 1 completion checklist
- [ ] Explain tables, rows, columns, primary and foreign keys.
- [ ] Write CREATE, INSERT, SELECT, UPDATE and DELETE.
- [ ] Use WHERE, ORDER BY and COUNT.
- [ ] Connect Python to SQLite with placeholders.
- [ ] Create and activate a virtual environment.
- [ ] Use Git status, add and commit.
- [ ] Explain Git versus GitHub.
- [ ] Write and run pytest tests.
- [ ] Debug a failing test systematically.
- [ ] Complete the database-connected API project.

**Phase 1 outcome:** You can organise Python code, call APIs, create a FastAPI backend, store structured records, version code and test expected behaviour.
