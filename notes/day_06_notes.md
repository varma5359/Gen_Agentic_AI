# Day 06 — Advanced Python: Iterators, Generators, Decorators, Context Managers and Type Hints

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** Reusable Python Logging and Timing Utility  
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

1. Explain iterable and iterator using a simple example.
2. Explain generators and yield using a simple example.
3. Explain decorators using a simple example.
4. Explain context managers using a simple example.
5. Explain type hints using a simple example.
6. Explain combining decorators, timing and logs using a simple example.
7. Apply iterable and iterator in the Reusable Python Logging and Timing Utility.
8. Apply generators and yield in the Reusable Python Logging and Timing Utility.
9. Apply decorators in the Reusable Python Logging and Timing Utility.
10. Apply context managers in the Reusable Python Logging and Timing Utility.
11. Apply type hints in the Reusable Python Logging and Timing Utility.
12. Apply combining decorators, timing and logs in the Reusable Python Logging and Timing Utility.

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

## 3. Iterable and iterator

### Beginner explanation

An iterable can provide values one by one. An iterator remembers its current position and produces the next value.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
numbers = [10, 20, 30]
iterator = iter(numbers)
print(next(iterator))
print(next(iterator))
print(next(iterator))
```

**Expected output**

```text
10
20
30
```

### Walkthrough

iter() obtains an iterator. next() asks it for the next value. A for loop handles StopIteration automatically.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

iter(), next(), __iter__(), __next__(), enumerate() and zip().

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Calling next() after the final item raises StopIteration. An iterator is generally consumed as it is used.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create an iterator over a list of user questions.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define iterable and iterator in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. Generators and yield

### Beginner explanation

A generator produces values lazily. yield pauses a function and remembers where execution should continue.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
def count_up_to(limit):
    number = 1
    while number <= limit:
        yield number
        number += 1
for value in count_up_to(3):
    print(value)
```

**Expected output**

```text
1
2
3
```

### Walkthrough

Calling a generator function returns a generator object. Each iteration continues until the next yield.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

yield, yield from, generator expressions and lazy processing of large files or streams.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Generators are usually single-pass. A generator object is not the same as a list; create a new generator to iterate again.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write a generator that yields one conversation message at a time.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define generators and yield in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Decorators

### Beginner explanation

A decorator wraps a function to add behavior without rewriting its original body.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
def announce(func):
    def wrapper():
        print("Starting")
        func()
        print("Finished")
    return wrapper
@announce
def greet():
    print("Hello")
greet()
```

**Expected output**

```text
Starting
Hello
Finished
```

### Walkthrough

@announce is shorthand for greet = announce(greet). wrapper() runs the added behavior and calls the original function.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

*args, **kwargs, functools.wraps, timing decorators, logging decorators and authorization checks.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A wrapper that accepts no arguments cannot wrap a function requiring arguments. Use wraps to preserve metadata.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Build a decorator that reports the execution time of a simple function.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define decorators in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Context managers

### Beginner explanation

A context manager performs setup before a block and cleanup after it. with uses this protocol.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
with open("sample.txt", "w", encoding="utf-8") as file:
    file.write("Saved safely")
print("File block completed")
```

**Expected output**

```text
File block completed
```

### Walkthrough

The file is opened before the block and closed when the block exits, including when an exception occurs.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

__enter__, __exit__, contextlib.contextmanager and ExitStack as later topics.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Forgetting cleanup can leak resources. Prefer with when the library supports context managers.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Use with to read a file and explain automatic cleanup.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define context managers in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Type hints

### Beginner explanation

Type hints describe expected types and intended return values. They improve readability and editor assistance.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
def add_marks(first: int, second: int) -> int:
    return first + second
print(add_marks(70, 20))
```

**Expected output**

```text
90
```

### Walkthrough

The parameters are annotated as int and the return type is annotated as int. Python does not enforce annotations automatically at runtime.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

list[str], dict[str, int], union types, Optional, Protocol and typed return objects.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A type hint is not runtime validation. Validate external input separately, especially API request data.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Add type hints to a function that receives a list of marks and returns a total.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define type hints in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. Combining decorators, timing and logs

### Beginner explanation

Small reusable wrappers can add cross-cutting behavior such as timing or logging around functions.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
from functools import wraps
from time import perf_counter

def timed(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = perf_counter()
        result = func(*args, **kwargs)
        print(f"Elapsed: {perf_counter() - start:.6f}s")
        return result
    return wrapper
@timed
def add(a, b):
    return a + b
print(add(2, 3))
```

**Expected output**

```text
Elapsed: (small measured duration)
5
```

### Walkthrough

perf_counter() measures elapsed time. wraps preserves metadata. wrapper forwards positional and keyword arguments and returns the original result.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Use logging instead of print in production; consider exceptions and async functions separately.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A decorator for synchronous functions does not automatically handle coroutine functions correctly. Do not hide exceptions.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Add a timing decorator to one safe function and explain each wrapper step.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define combining decorators, timing and logs in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 9. Guided mini-project — Reusable Python Logging and Timing Utility

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
day_06_project/
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

1. What is iterable and iterator?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is generators and yield?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is decorators?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is context managers?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is type hints?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is combining decorators, timing and logs?
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

1. Explain iterable and iterator to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain generators and yield to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain decorators to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain context managers to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain type hints to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain combining decorators, timing and logs to a beginner.
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

**Day 6 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.
