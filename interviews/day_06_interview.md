# Day 06 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** Advanced Python: Iterators, Generators, Decorators, Context Managers and Type Hints  
**Mini-project:** Reusable Python Logging and Timing Utility  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain iterable and iterator.

**Beginner answer:** An iterable can provide values one by one. An iterator remembers its current position and produces the next value.

**Example code**

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

**How it works:** iter() obtains an iterator. next() asks it for the next value. A for loop handles StopIteration automatically.

**Important methods or syntax:** iter(), next(), __iter__(), __next__(), enumerate() and zip().

**Common mistake:** Calling next() after the final item raises StopIteration. An iterator is generally consumed as it is used.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain generators and yield.

**Beginner answer:** A generator produces values lazily. yield pauses a function and remembers where execution should continue.

**Example code**

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

**How it works:** Calling a generator function returns a generator object. Each iteration continues until the next yield.

**Important methods or syntax:** yield, yield from, generator expressions and lazy processing of large files or streams.

**Common mistake:** Generators are usually single-pass. A generator object is not the same as a list; create a new generator to iterate again.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain decorators.

**Beginner answer:** A decorator wraps a function to add behavior without rewriting its original body.

**Example code**

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

**How it works:** @announce is shorthand for greet = announce(greet). wrapper() runs the added behavior and calls the original function.

**Important methods or syntax:** *args, **kwargs, functools.wraps, timing decorators, logging decorators and authorization checks.

**Common mistake:** A wrapper that accepts no arguments cannot wrap a function requiring arguments. Use wraps to preserve metadata.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain context managers.

**Beginner answer:** A context manager performs setup before a block and cleanup after it. with uses this protocol.

**Example code**

```python
with open("sample.txt", "w", encoding="utf-8") as file:
    file.write("Saved safely")
print("File block completed")
```

**Expected output**

```text
File block completed
```

**How it works:** The file is opened before the block and closed when the block exits, including when an exception occurs.

**Important methods or syntax:** __enter__, __exit__, contextlib.contextmanager and ExitStack as later topics.

**Common mistake:** Forgetting cleanup can leak resources. Prefer with when the library supports context managers.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain type hints.

**Beginner answer:** Type hints describe expected types and intended return values. They improve readability and editor assistance.

**Example code**

```python
def add_marks(first: int, second: int) -> int:
    return first + second
print(add_marks(70, 20))
```

**Expected output**

```text
90
```

**How it works:** The parameters are annotated as int and the return type is annotated as int. Python does not enforce annotations automatically at runtime.

**Important methods or syntax:** list[str], dict[str, int], union types, Optional, Protocol and typed return objects.

**Common mistake:** A type hint is not runtime validation. Validate external input separately, especially API request data.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain combining decorators, timing and logs.

**Beginner answer:** Small reusable wrappers can add cross-cutting behavior such as timing or logging around functions.

**Example code**

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

**How it works:** perf_counter() measures elapsed time. wraps preserves metadata. wrapper forwards positional and keyword arguments and returns the original result.

**Important methods or syntax:** Use logging instead of print in production; consider exceptions and async functions separately.

**Common mistake:** A decorator for synchronous functions does not automatically handle coroutine functions correctly. Do not hide exceptions.

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

### Exercise 1 — Iterable and iterator

**Task:** Create an iterator over a list of user questions.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — Generators and yield

**Task:** Write a generator that yields one conversation message at a time.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Decorators

**Task:** Build a decorator that reports the execution time of a simple function.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Context managers

**Task:** Use with to read a file and explain automatic cleanup.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Type hints

**Task:** Add type hints to a function that receives a list of marks and returns a total.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Combining decorators, timing and logs

**Task:** Add a timing decorator to one safe function and explain each wrapper step.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — Reusable Python Logging and Timing Utility

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
