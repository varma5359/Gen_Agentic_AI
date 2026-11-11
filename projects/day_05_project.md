# Day 5 Project — AI Configuration and File Management Utility

**Phase:** 1 — Python and Software Development Foundations  
**Approved topic:** Python modules, packages, exceptions, JSON, file handling and logging.  
**Estimated duration:** 30–75 minutes (Day 10 may take longer)  
**Mode:** Independent self-learning

## 1. Problem statement and objective

Create a command-line utility that writes a JSON configuration, reads it back, validates required keys and logs operations.

## 2. Prerequisites

Modules, pathlib, JSON, exceptions, context managers and logging.

Complete the day's class notes first. Use only concepts already introduced in the pathway. No paid API key is required unless an optional extension explicitly adds one.

## 3. Functional requirements

- Solve the stated objective.
- Use readable names and small functions or classes with clear responsibilities.
- Validate input before processing.
- Provide useful behaviour for normal and invalid inputs.
- Keep credentials and sensitive values out of source code.

## 4. Step-by-step implementation plan

1. Create config_utils.py, validation.py and main.py.
2. Use Path, UTF-8 JSON and specific exception handling.
3. Create the data folder when required.

Do not skip steps. Run the program after each meaningful change. If an error occurs, fix it before adding another feature.

## 5. Suggested folder structure

~~~text
day_05_project/
├── config_utils.py
├── validation.py
├── main.py
└── data/
~~~

Create only files you actually use. Do not add empty modules merely to make the project look larger.

## 6. Sample data and expected behaviour

Start with two or three small records. Before running the program, write down the expected result for each record. Compare actual and expected behaviour and explain any difference.

## 7. Test cases and validation

Test valid config, missing file, malformed JSON, missing key and a path that cannot be written. Keep credentials out of files and logs.

Record each test as: input, expected result, actual result and PASS/FAIL. Do not mark a test passed until you have run it.

## 8. Common debugging method

1. Read the full error message.
2. Confirm the command, file path and active Python environment.
3. Inspect relevant inputs and variable values.
4. Reduce the problem to the smallest reproducible example.
5. Fix the cause and repeat the failing test.

## 9. Submission checklist

- [ ] Source files and folder structure are saved.
- [ ] Setup and run instructions are written.
- [ ] Example input and output are recorded.
- [ ] Normal and invalid cases have been tested.
- [ ] Known limitations are documented.
- [ ] No credentials, private data or unnecessary environment files are committed.
- [ ] I can explain the design and code I wrote.

## 10. Interview explanation

Prepare a 60–90 second explanation covering the problem, your design, the key concepts, one challenge, how you tested the result and one improvement you would make before production.

## 11. Optional extension

Add one small feature only after all required behaviour works. Keep it within concepts already taught; do not introduce an advanced framework early.
