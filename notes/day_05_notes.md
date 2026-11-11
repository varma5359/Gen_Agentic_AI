# Day 5 — Python modules, packages, exceptions, JSON, file handling and logging.

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours  
**Level:** Beginner to Intermediate

> **Self-learning instruction:** Read one section at a time. Type the code yourself, run it and compare the result. These notes are designed to teach without a trainer or video.

## 1. Understand the topic

A module is a Python file; a package groups modules. pathlib.Path represents paths. Use with when opening files so resources close reliably. JSON is a text format: dumps/loads convert Python data and JSON strings; dump/load work with file objects. Catch specific expected exceptions. Logging records events; never log secrets.

## 2. Why this matters in an AI application

A GenAI application is still software. It needs input handling, business logic, APIs, data, validation, security, tests and deployment. Today's concepts are building blocks for those responsibilities. A small example demonstrates one concept; it is not automatically production-ready.

## 3. Guided coding walkthrough

### Step 1 — Understand the task

Read the code and predict the output. Identify the input, the main operation and the value produced.

### Step 2 — Code

~~~python
import json
import logging
from pathlib import Path
logging.basicConfig(level=logging.INFO)
path = Path("config.json")
config = {"app_name": "TechPhile", "max_results": 5}
try:
    path.write_text(json.dumps(config, indent=2), encoding="utf-8")
    loaded = json.loads(path.read_text(encoding="utf-8"))
except (OSError, json.JSONDecodeError):
    logging.exception("Configuration operation failed")
else:
    print(loaded["app_name"])
~~~

### Step 3 — Expected output

~~~text
TechPhile
~~~

### Step 4 — Explain the code line by line

- Path writes and reads UTF-8 text.
- dumps serializes a dictionary; loads parses it.
- except handles expected file/JSON failures; else runs after success.
- Avoid naming local files json.py or logging.py.
- Never write credentials or private data to logs.

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
