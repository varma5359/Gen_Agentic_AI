# Day 05 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** Python Modules, Packages, Exceptions, JSON, File Handling and Logging  
**Mini-project:** AI Configuration and File Management Utility  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain modules and imports.

**Beginner answer:** A module is a Python file containing reusable names. import lets another file use those names.

**Example code**

```python
import math
print(math.sqrt(25))
from pathlib import Path
print(Path("notes.txt").suffix)
```

**Expected output**

```text
5.0
.txt
```

**How it works:** math.sqrt() calculates a square root. Path.suffix returns the filename extension.

**Important methods or syntax:** import module, from module import name, aliases and __name__ == "__main__".

**Common mistake:** Naming your file json.py or random.py can shadow a standard-library module. Check the working directory if imports fail.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain packages and project layout.

**Beginner answer:** A package groups related modules in folders. It helps organize a growing application.

**Example code**

```python
# project/
#   app/
#     __init__.py
#     text_tools.py
#   main.py
# main.py:
from app.text_tools import clean_text
print(clean_text("  Hello  "))
```

**Expected output**

```text
Hello
```

**How it works:** Python finds the app package and imports clean_text from text_tools.py.

**Important methods or syntax:** Organize by responsibility: routes, services, schemas, database, config and utilities. Use absolute imports for clarity in many applications.

**Common mistake:** ModuleNotFoundError can result from wrong paths, misspelled names or running from the wrong working directory.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain exceptions and try/except.

**Beginner answer:** An exception signals that something went wrong during execution. try/except lets you handle expected failures.

**Example code**

```python
try:
    age = int("twenty")
except ValueError:
    print("Enter a whole number")
else:
    print(age)
finally:
    print("Input check finished")
```

**Expected output**

```text
Enter a whole number
Input check finished
```

**How it works:** int() raises ValueError. except handles it. finally runs whether or not an exception occurred.

**Important methods or syntax:** Catch specific exception types, raise meaningful errors, chain exceptions and use custom exceptions when appropriate.

**Common mistake:** Bare except can hide programming errors. Do not silently ignore an exception. Preserve useful diagnostic information.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain reading and writing files.

**Beginner answer:** Files let programs store information beyond one run. with manages the file resource and closes it automatically.

**Example code**

```python
with open("message.txt", "w", encoding="utf-8") as file:
    file.write("Hello learner")
with open("message.txt", "r", encoding="utf-8") as file:
    content = file.read()
print(content)
```

**Expected output**

```text
Hello learner
```

**How it works:** w writes and replaces existing content. r reads. read() returns the file contents as a string.

**Important methods or syntax:** read(), readline(), readlines(), write(), append mode, pathlib.Path.read_text() and write_text().

**Common mistake:** Wrong paths raise FileNotFoundError. w can overwrite a file. Use a to append and validate file locations.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain json serialization.

**Beginner answer:** JSON is a text format for exchanging structured data. Python's json module converts dictionaries and lists to and from JSON.

**Example code**

```python
import json
student = {"name": "Anu", "marks": 85}
json_text = json.dumps(student, indent=2)
print(json_text)
restored = json.loads(json_text)
print(restored["name"])
```

**Expected output**

```text
{
  "name": "Anu",
  "marks": 85
}
Anu
```

**How it works:** dumps() creates JSON text. loads() parses JSON text. dump() and load() work directly with file objects.

**Important methods or syntax:** JSON supports objects, arrays, strings, numbers, booleans and null. Python None maps to JSON null. Use ensure_ascii and indent when needed.

**Common mistake:** Invalid JSON raises JSONDecodeError. JSON object keys are strings. Avoid serializing arbitrary Python objects without a clear schema.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain logging.

**Beginner answer:** Logging records events and errors with severity levels. It is more configurable than print statements.

**Example code**

```python
import logging
logging.basicConfig(level=logging.INFO, format="%(levelname)s:%(message)s")
logging.info("Application started")
logging.warning("No question supplied")
```

**Expected output**

```text
INFO:Application started
WARNING:No question supplied
```

**How it works:** basicConfig configures the root logger. info() and warning() record messages at different levels.

**Important methods or syntax:** DEBUG, INFO, WARNING, ERROR and CRITICAL; module-level loggers; file handlers; structured logs and exception logging.

**Common mistake:** Never log passwords, API keys or unnecessary personal information. Avoid swallowing errors after logging.

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

### Exercise 1 — Modules and imports

**Task:** Create helper.py and import one function from it into main.py.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — Packages and project layout

**Task:** Design a package with separate modules for prompt formatting and text cleaning.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Exceptions and try/except

**Task:** Ask for marks and handle non-numeric input.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Reading and writing files

**Task:** Save a student's question and read it back.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — JSON serialization

**Task:** Save application settings in settings.json and load them safely.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Logging

**Task:** Add logs to a file-reading utility and record successful reads and failures.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — AI Configuration and File Management Utility

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


---

## 6. Detailed interview answers

### Q7. What is the difference between a module and a package?

A module is a Python file that contains reusable code. A package organizes related modules in a directory. A regular package commonly contains an `__init__.py` file. A package helps keep a larger application organized.

### Q8. What is the difference between import and from ... import?

`import math` makes the module name available, so we call `math.sqrt(25)`.  
`from math import sqrt` imports the selected name, so we call `sqrt(25)`.

Avoid importing everything with `from module import *` in normal application code because it can make names unclear.

### Q9. What is an exception?

An exception is a Python object that represents an error or unusual condition during execution. Examples include `ValueError`, `TypeError`, `FileNotFoundError` and `JSONDecodeError`.

### Q10. Why should we catch specific exceptions?

Specific exceptions let us handle problems we understand. A broad `except Exception` can hide programming mistakes and make debugging harder. Catch the narrowest useful exception and show a helpful message.

### Q11. What is the purpose of finally?

A `finally` block runs whether the try block succeeds or raises an exception. It is useful for cleanup. When using `with open(...)`, Python already handles closing the file, so a separate finally block is usually unnecessary.

### Q12. What is JSON serialization?

Serialization converts a Python value such as a dictionary or list into JSON text so it can be stored or sent. Deserialization parses JSON text back into Python values.

### Q13. Explain load(), loads(), dump() and dumps().

- `json.load(file)`: reads JSON from an open file.
- `json.loads(text)`: parses JSON from a string.
- `json.dump(data, file)`: writes Python data as JSON to an open file.
- `json.dumps(data)`: returns JSON text as a string.

### Q14. Why use pathlib?

`pathlib.Path` represents filesystem paths using an object-oriented interface. It helps build paths across operating systems and makes operations such as checking existence and creating directories clearer.

### Q15. What is logging and why is it better than print() for application diagnostics?

Logging records events with levels, timestamps and configurable destinations. Print is useful for simple interactive output, but logging can write to files and distinguish informational events, warnings and errors. Do not log passwords, API keys or sensitive personal data.

### Q16. What are common logging levels?

- DEBUG: detailed diagnostic information.
- INFO: normal application events.
- WARNING: something unexpected that did not stop the program.
- ERROR: an operation failed.
- CRITICAL: a serious failure that may prevent the application from continuing.

### Q17. What does the main guard do?

`if __name__ == "__main__":` runs code only when the file is executed directly. If another module imports the file, the guarded code does not automatically run.

## 7. Code-output interview drills

### Drill 1 — import a function

```python
# maths_tools.py
def double(number):
    return number * 2

# main.py
from maths_tools import double
print(double(6))
```

**Answer:** `12`. The function is imported from the module and called with 6.

### Drill 2 — exception handling

```python
try:
    number = int("abc")
except ValueError:
    print("Invalid number")
```

**Answer:** `Invalid number`. int() cannot convert the text "abc" into an integer, so ValueError is handled.

### Drill 3 — JSON serialization

```python
import json
student = {"name": "Anu", "score": 90}
text = json.dumps(student)
print(type(text).__name__)
```

**Answer:** `str`. dumps() returns JSON text.

### Drill 4 — JSON deserialization

```python
import json
student = json.loads('{"name": "Anu"}')
print(student["name"])
```

**Answer:** `Anu`. loads() parses the JSON string into a Python dictionary.

### Drill 5 — file context manager

```python
with open("notes.txt", "w", encoding="utf-8") as file:
    file.write("Python")
print("Finished")
```

**Answer:** `Finished`. The file is closed when execution leaves the with block.

## 8. Practical coding interview challenge

**Task:** Write a function that saves a list of student dictionaries to a JSON file and another function that reads the file back.

**One possible solution:**

```python
import json


def save_students(students, file_path):
    with open(file_path, "w", encoding="utf-8") as file:
        json.dump(students, file, indent=4)


def read_students(file_path):
    with open(file_path, "r", encoding="utf-8") as file:
        return json.load(file)


records = [
    {"name": "Anu", "course": "Python"},
    {"name": "Ravi", "course": "GenAI"}
]

save_students(records, "students.json")
loaded_records = read_students("students.json")
print(loaded_records)
```

Output:

```text
[{'name': 'Anu', 'course': 'Python'}, {'name': 'Ravi', 'course': 'GenAI'}]
```

Explanation:
- The first function opens a file in write mode and serializes the list as JSON.
- The second opens the file in read mode and parses JSON into Python objects.
- Both use `with` so the file is closed automatically.
- In a real application, add handling for missing files, invalid JSON and permission errors.

## 9. Project discussion — Student Records application

Be prepared to explain:

1. **What does the application do?** It adds and lists student/course records and keeps them in a JSON file between runs.
2. **Why are there multiple Python files?** Each module has one responsibility, making code easier to understand and maintain.
3. **Why does students.py contain create_student()?** It validates the input and creates a consistent dictionary.
4. **Why does storage.py import json?** It converts Python dictionaries/lists to JSON text and back.
5. **Why use pathlib?** It builds file paths based on the location of the Python file, not only the terminal's current directory.
6. **Why use with?** It ensures the file is closed after reading or writing.
7. **Why catch ValueError?** It handles invalid student data and invalid JSON structure reported by the storage layer.
8. **Why catch OSError?** It handles filesystem problems such as permission or disk errors.
9. **Why use logging?** It records important events and diagnostic information in a log file.
10. **Why is the main guard useful?** Importing a module should not unexpectedly start the interactive menu.
11. **Does the project use a database?** No. It uses a JSON file for simple local persistence.
12. **What are its limitations?** It has no multi-user access control, database transactions, duplicate prevention by default or web interface.
13. **What would you improve?** Add unique IDs, duplicate checks, automated tests, a database and a web API in later lessons.

## 10. Final interview readiness checklist

- [ ] I can explain module vs package.
- [ ] I can write and use import statements.
- [ ] I can explain try, except, else and finally.
- [ ] I can choose a specific exception to catch.
- [ ] I can explain JSON serialization and deserialization.
- [ ] I know load, loads, dump and dumps.
- [ ] I can read and write a text file using with.
- [ ] I can build paths using pathlib.
- [ ] I can explain logging levels and avoid logging secrets.
- [ ] I can explain the main guard.
- [ ] I can describe each file in the Student Records project.
- [ ] I can discuss the project's limitations honestly.
