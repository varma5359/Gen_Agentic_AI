# Day 5 — Python modules, packages, exceptions, JSON, file handling and logging

**Phase 1 | 2–3 hours | Beginner | Project: AI Configuration and File Management Utility**

## 1. Why these concepts matter
A useful application splits code into maintainable files, reads and writes data, handles failures and records what happened. A program that only works when every operation succeeds is not robust.

## 2. Modules and imports
A module is a Python file that can be imported.

Create text_utils.py:
~~~python
def clean_text(text):
    return " ".join(text.strip().split())
~~~

Create app.py:
~~~python
from text_utils import clean_text

question = "  Explain   JSON  "
print(clean_text(question))
~~~

Run from the folder containing both files. Output: Explain JSON. The import makes the function available in app.py.

## 3. Packages
A package groups related modules. Example:

~~~text
ai_utility/
    app.py
    config/
        __init__.py
        settings.py
    services/
        __init__.py
        text_utils.py
~~~

__init__.py marks a regular package and can contain initialization code. Modern Python also supports namespace packages; this course uses explicit package markers for clarity. Run imports from the project root so Python can resolve package paths.

## 4. Exceptions
An exception is raised when an operation cannot complete normally.

~~~python
try:
    age = int(input("Enter age: "))
    print("Next year:", age + 1)
except ValueError:
    print("Please enter a whole number.")
~~~

try contains the operation that may fail. except ValueError handles invalid numeric text. Catch the exception you expect; do not silently suppress every error.

### else and finally
~~~python
try:
    number = int("25")
except ValueError:
    print("Invalid number")
else:
    print("Converted:", number)
finally:
    print("Conversion attempt finished")
~~~

else runs only if try succeeds. finally runs as control leaves the structure and is useful for cleanup.

### Raise a meaningful error
~~~python
def validate_temperature(value):
    if value < 0 or value > 1:
        raise ValueError("Temperature must be between 0 and 1")
    return value
~~~

raise signals that a function's input violates its contract.

## 5. Text file handling
Use with so the file is closed automatically.

~~~python
with open("question.txt", "w", encoding="utf-8") as file:
    file.write("What is an embedding?\\n")
    file.write("Explain in simple words.\\n")

with open("question.txt", "r", encoding="utf-8") as file:
    content = file.read()

print(content)
~~~

Modes:
- r reads an existing file.
- w creates or overwrites a file.
- a appends to the end.
- x creates a new file and fails if it exists.

w can destroy previous contents. Choose carefully. For large files, iterate line by line rather than reading everything into memory.

## 6. JSON files
JSON is a text format commonly used by APIs and configuration files.

~~~python
import json

settings = {
    "application": "TechPhile Utility",
    "provider": "demo",
    "temperature": 0.2
}

with open("config.json", "w", encoding="utf-8") as file:
    json.dump(settings, file, indent=2)

with open("config.json", "r", encoding="utf-8") as file:
    loaded = json.load(file)

print(loaded["application"])
~~~

dump writes a Python object to a file. load reads JSON from a file. dumps converts an object to a JSON string; loads parses a JSON string. JSON supports objects, arrays, strings, numbers, booleans and null. Python sets and custom objects need conversion before serialization.

## 7. Logging
Logging records application events with severity and timestamps.

~~~python
import logging

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s %(levelname)s %(message)s"
)

logging.debug("Detailed diagnostic")
logging.info("Application started")
logging.warning("Optional configuration missing")
logging.error("Could not read required file")
~~~

Levels: DEBUG, INFO, WARNING, ERROR and CRITICAL. The configured INFO level normally suppresses DEBUG messages. Never log API keys, passwords, access tokens or private user content. Log safe summaries and identifiers.

## 8. Industry scenario
An AI backend may load provider name, model choice and safe generation settings from configuration. Real credentials belong in environment variables or a secrets manager, not committed JSON files. Configuration validation should happen before the application starts serving requests.

## 9. Common errors
| Error | Cause | Fix |
|---|---|---|
| ModuleNotFoundError | Wrong working directory or import path | Run from project root |
| FileNotFoundError | Missing path | Check path and current directory |
| JSONDecodeError | Invalid JSON | Check commas, quotes and structure |
| Previous content lost | File opened with w | Use append or back up |
| Hidden failure | Broad silent except | Catch specific exceptions |
| Secret in log | Sensitive value logged | Redact and log safe metadata |

## 10. Exercises
1. Create and import a reusable module.
2. Write a text file and read it.
3. Append a line without deleting earlier content.
4. Save a dictionary to JSON and reload it.
5. Catch ValueError from int("hello").
6. Configure INFO and WARNING logs.
7. Explain why with open is preferred.

## 11. Five-question quiz
1. A module is: A Python file importable by another file B database table C loop D AI model. **Answer A:** modules organise reusable code.
2. Which mode overwrites a file? A r B a C w D x. **Answer C:** w truncates existing content.
3. Invalid JSON raises: A IndexError B JSONDecodeError C KeyError D StopIteration. **Answer B:** the JSON parser raises it.
4. Benefit of with for files? A closes file reliably B encrypts C converts to JSON D prevents all errors. **Answer A:** context management handles cleanup.
5. What must never be logged? A safe event name B duration C API secret D status code. **Answer C:** credentials must be protected.

## 12. Completion checklist
- [ ] Create/import a module and explain package layout.
- [ ] Handle ValueError.
- [ ] Read, write and append text.
- [ ] Read/write JSON.
- [ ] Configure logging and explain levels.
- [ ] Explain safe secret handling.
- [ ] Complete the project and test failure cases.

**Next:** Day 6 — Advanced Python: iterators, generators, decorators, context managers and type hints.
