# Day 10 Project — Version-Controlled Database-Connected Python API

## Objective
Build a small Python API backed by SQLite, test its data-access logic, isolate dependencies and track code with Git. Production systems need stronger authentication, migrations and deployment controls.

## Folder structure
~~~text
student_api/
    app.py
    database.py
    test_database.py
    requirements.txt
    .gitignore
    README.md
~~~

## Step 1 — Environment
Windows:
~~~powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install fastapi uvicorn pytest
~~~
macOS/Linux:
~~~bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install fastapi uvicorn pytest
~~~

## Step 2 — database.py
~~~python
import sqlite3
from pathlib import Path

DB_PATH = Path(__file__).resolve().parent / "students.db"

def get_connection():
    connection = sqlite3.connect(DB_PATH)
    connection.row_factory = sqlite3.Row
    return connection

def initialize_database():
    with get_connection() as connection:
        connection.execute("""
            CREATE TABLE IF NOT EXISTS students (
                id INTEGER PRIMARY KEY AUTOINCREMENT,
                name TEXT NOT NULL,
                course TEXT NOT NULL
            )
        """)

def create_student(name, course):
    with get_connection() as connection:
        cursor = connection.execute(
            "INSERT INTO students (name, course) VALUES (?, ?)",
            (name, course)
        )
        return cursor.lastrowid

def get_student(student_id):
    with get_connection() as connection:
        row = connection.execute(
            "SELECT id, name, course FROM students WHERE id = ?",
            (student_id,)
        ).fetchone()
        return dict(row) if row else None

def list_students():
    with get_connection() as connection:
        rows = connection.execute(
            "SELECT id, name, course FROM students ORDER BY id"
        ).fetchall()
        return [dict(row) for row in rows]
~~~

The placeholders bind values separately from SQL syntax. row_factory enables column-name access. The connection context manager manages transaction completion; production code should make transaction and cleanup policy explicit.

## Step 3 — app.py
~~~python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel, Field
from database import initialize_database, create_student, get_student, list_students

app = FastAPI(title="Database Connected Student API")
initialize_database()

class StudentCreate(BaseModel):
    name: str = Field(min_length=2, max_length=60)
    course: str = Field(min_length=2, max_length=80)

@app.post("/students", status_code=201)
def add_student(student: StudentCreate):
    student_id = create_student(student.name, student.course)
    return get_student(student_id)

@app.get("/students")
def read_students():
    return list_students()

@app.get("/students/{student_id}")
def read_student(student_id: int):
    student = get_student(student_id)
    if student is None:
        raise HTTPException(status_code=404, detail="Student not found")
    return student
~~~

Run: uvicorn app:app --reload. Open /docs.

POST body:
~~~json
{"name": "Asha", "course": "GenAI"}
~~~

Expected: 201 with a generated ID. GET /students lists records; GET /students/1 returns one record. Unlike Day 9's dictionary, SQLite data persists after restart.

## Step 4 — test_database.py
~~~python
from database import create_student, get_student, list_students

def test_create_and_get_student():
    student_id = create_student("Test Learner", "Python")
    student = get_student(student_id)
    assert student is not None
    assert student["name"] == "Test Learner"
    assert student["course"] == "Python"

def test_list_students_returns_list():
    result = list_students()
    assert isinstance(result, list)
~~~

Run pytest -q. This starter uses a local database for simplicity. A professional suite should isolate tests with a temporary database so runs do not depend on prior local records.

## Step 5 — requirements.txt
~~~text
fastapi
uvicorn
pytest
~~~
Pin tested versions for reproducible deployment.

## Step 6 — .gitignore
~~~text
.venv/
__pycache__/
.pytest_cache/
*.pyc
students.db
.env
~~~

Exclude local database files because they may contain learner data. Never commit credentials or personal information.

## Step 7 — Git workflow
~~~bash
git init
git status
git add app.py database.py test_database.py requirements.txt .gitignore README.md
git status
git commit -m "Build database-connected student API"
~~~

Create an empty GitHub repository, then use its actual remote URL:
~~~bash
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git branch -M main
git push -u origin main
~~~

Replace placeholders. Review staged files before committing.

## Test plan
| Test | Action | Expected |
|---|---|---|
| TC01 | Start API | Server starts |
| TC02 | POST valid student | 201 and ID |
| TC03 | GET list | Created record appears |
| TC04 | GET existing ID | Details returned |
| TC05 | GET unknown ID | 404 |
| TC06 | POST too-short name | Validation error |
| TC07 | Restart and GET record | Record still exists |
| TC08 | Run pytest | Tests pass |
| TC09 | Inspect Git status | No .venv, .env or database staged |

## Production gaps
No authentication, authorisation, pagination, migrations, structured logging, pooling or isolated test database is included. Do not deploy this demo with real personal records as-is.

## Submission
Submit source, requirements, .gitignore, test output, API examples and GitHub URL. Explain how SQLite persistence differs from Day 9 in-memory storage.
