# Day 05 — Python Modules, Packages, Exceptions, JSON, File Handling and Logging

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** AI Configuration and File Management Utility  
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

1. Explain modules and imports using a simple example.
2. Explain packages and project layout using a simple example.
3. Explain exceptions and try/except using a simple example.
4. Explain reading and writing files using a simple example.
5. Explain json serialization using a simple example.
6. Explain logging using a simple example.
7. Apply modules and imports in the AI Configuration and File Management Utility.
8. Apply packages and project layout in the AI Configuration and File Management Utility.
9. Apply exceptions and try/except in the AI Configuration and File Management Utility.
10. Apply reading and writing files in the AI Configuration and File Management Utility.
11. Apply json serialization in the AI Configuration and File Management Utility.
12. Apply logging in the AI Configuration and File Management Utility.

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

## 3. Modules and imports

### Beginner explanation

A module is a Python file containing reusable names. import lets another file use those names.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

math.sqrt() calculates a square root. Path.suffix returns the filename extension.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

import module, from module import name, aliases and __name__ == "__main__".

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Naming your file json.py or random.py can shadow a standard-library module. Check the working directory if imports fail.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create helper.py and import one function from it into main.py.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define modules and imports in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. Packages and project layout

### Beginner explanation

A package groups related modules in folders. It helps organize a growing application.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

Python finds the app package and imports clean_text from text_tools.py.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Organize by responsibility: routes, services, schemas, database, config and utilities. Use absolute imports for clarity in many applications.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

ModuleNotFoundError can result from wrong paths, misspelled names or running from the wrong working directory.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Design a package with separate modules for prompt formatting and text cleaning.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define packages and project layout in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Exceptions and try/except

### Beginner explanation

An exception signals that something went wrong during execution. try/except lets you handle expected failures.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

int() raises ValueError. except handles it. finally runs whether or not an exception occurred.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Catch specific exception types, raise meaningful errors, chain exceptions and use custom exceptions when appropriate.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Bare except can hide programming errors. Do not silently ignore an exception. Preserve useful diagnostic information.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Ask for marks and handle non-numeric input.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define exceptions and try/except in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Reading and writing files

### Beginner explanation

Files let programs store information beyond one run. with manages the file resource and closes it automatically.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

w writes and replaces existing content. r reads. read() returns the file contents as a string.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

read(), readline(), readlines(), write(), append mode, pathlib.Path.read_text() and write_text().

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Wrong paths raise FileNotFoundError. w can overwrite a file. Use a to append and validate file locations.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Save a student's question and read it back.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define reading and writing files in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. JSON serialization

### Beginner explanation

JSON is a text format for exchanging structured data. Python's json module converts dictionaries and lists to and from JSON.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

dumps() creates JSON text. loads() parses JSON text. dump() and load() work directly with file objects.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

JSON supports objects, arrays, strings, numbers, booleans and null. Python None maps to JSON null. Use ensure_ascii and indent when needed.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Invalid JSON raises JSONDecodeError. JSON object keys are strings. Avoid serializing arbitrary Python objects without a clear schema.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Save application settings in settings.json and load them safely.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define json serialization in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. Logging

### Beginner explanation

Logging records events and errors with severity levels. It is more configurable than print statements.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

basicConfig configures the root logger. info() and warning() record messages at different levels.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

DEBUG, INFO, WARNING, ERROR and CRITICAL; module-level loggers; file handlers; structured logs and exception logging.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Never log passwords, API keys or unnecessary personal information. Avoid swallowing errors after logging.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Add logs to a file-reading utility and record successful reads and failures.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define logging in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 9. Guided mini-project — AI Configuration and File Management Utility

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
day_05_project/
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

# 10. Daily revision questions

1. What is modules and imports?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is packages and project layout?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is exceptions and try/except?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is reading and writing files?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is json serialization?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is logging?
6.1 Why would a Python developer use it?
6.2 What mistake should a beginner avoid?

# 11. Daily quiz

1. Which concept from today's lesson would you use for the sample problem?
2. What does the main method or function in one example do?
3. What happens if the input is missing or invalid?
4. Why should code be divided into small understandable steps?
5. Give one use of today's concepts in an AI application.

**Answer method:** answer in your own words, then prove your understanding with a small code example.

# 12. Interview practice

1. Explain modules and imports to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain packages and project layout to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain exceptions and try/except to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain reading and writing files to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain json serialization to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain logging to a beginner.
6.1 Give a practical example.
6.2 What is one limitation or common error?

## How to structure an interview answer

1. Give a direct definition.
2. Explain how it works in two or three steps.
3. Give a small example.
4. Mention one real use.
5. Mention one limitation or error case.

# 13. Trainer assessment rubric

| Area | Evidence |
|---|---|
| Concept understanding | Student explains without reading |
| Code reading | Student describes important lines |
| Practical execution | Student runs and modifies code |
| Debugging | Student locates a simple error |
| Project | Student applies the day's concepts |
| Interview communication | Student gives a clear structured answer |

# 14. What you should remember

- Understand why a feature is used before memorizing syntax.
- Type and run each example yourself.
- Know the difference between a function, method, argument and return value.
- Read error messages instead of guessing.
- Build the project in small steps.
- Be ready to teach the concept to another beginner.

**Day 5 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.
