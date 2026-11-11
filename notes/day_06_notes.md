# Day 6 — Advanced Python: iterators, generators, decorators, context managers and type hints.

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours  
**Level:** Beginner to Intermediate

> **Self-learning instruction:** Read one section at a time. Type the code yourself, run it and compare the result. These notes are designed to teach without a trainer or video.

## 1. Understand the topic

An iterable can provide an iterator. An iterator produces the next value and remembers its position. A generator uses yield to produce values lazily. A decorator wraps a callable to add behaviour. functools.wraps preserves metadata. A context manager manages setup and cleanup around with. Type hints document expectations but do not enforce runtime types.

## 2. Why this matters in an AI application

A GenAI application is still software. It needs input handling, business logic, APIs, data, validation, security, tests and deployment. Today's concepts are building blocks for those responsibilities. A small example demonstrates one concept; it is not automatically production-ready.

## 3. Guided coding walkthrough

### Step 1 — Understand the task

Read the code and predict the output. Identify the input, the main operation and the value produced.

### Step 2 — Code

~~~python
from functools import wraps
from time import perf_counter
from typing import Iterator

def timed(function):
    @wraps(function)
    def wrapper(*args, **kwargs):
        start = perf_counter()
        result = function(*args, **kwargs)
        print(f"Elapsed: {perf_counter() - start:.4f}s")
        return result
    return wrapper

def ids(total: int) -> Iterator[int]:
    for value in range(1, total + 1):
        yield value

@timed
def total_ids(total: int) -> int:
    return sum(ids(total))

print(total_ids(5))
~~~

### Step 3 — Expected output

~~~text
Elapsed: 0.0000s
15
(Timing varies.)
~~~

### Step 4 — Explain the code line by line

- yield produces values one at a time.
- The decorator receives a function and returns a wrapper.
- wraps preserves original function metadata.
- sum consumes the generator.
- Generators are usually exhausted after one pass; type hints are not runtime validation.

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
