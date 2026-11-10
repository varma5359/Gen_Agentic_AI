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
