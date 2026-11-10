# Day 03 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** Functions, Parameters, Arguments, Return Values, Scope and Comprehensions  
**Mini-project:** Reusable Text Processing Toolkit  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain defining and calling functions.

**Beginner answer:** A function is a named set of instructions that can be reused. Defining it does not run it; calling it does.

**Example code**

```python
def greet():
    print("Welcome to Python")

greet()
greet()
```

**Expected output**

```text
Welcome to Python
Welcome to Python
```

**How it works:** def begins a definition. The indented body belongs to the function. greet() calls it.

**Important methods or syntax:** Function names, docstrings, return statements, positional calls and keyword calls.

**Common mistake:** Forgetting parentheses, incorrect indentation or defining a function but never calling it.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain parameters and arguments.

**Beginner answer:** Parameters are names in the function definition. Arguments are actual values supplied during a call.

**Example code**

```python
def greet(name, course):
    print(f"Hello {name}, welcome to {course}")
greet("Anu", "Python")
greet(course="GenAI", name="Ravi")
```

**Expected output**

```text
Hello Anu, welcome to Python
Hello Ravi, welcome to GenAI
```

**How it works:** name and course are parameters. The strings supplied are arguments. Keyword arguments identify parameters by name.

**Important methods or syntax:** Positional, keyword, default and variable-length arguments (*args and **kwargs) after the basic form is clear.

**Common mistake:** Missing required arguments cause TypeError. Positional arguments must not follow keyword arguments in a call.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain return values.

**Beginner answer:** return sends a result back to the caller. print() displays information but does not return that displayed text.

**Example code**

```python
def add(first, second):
    total = first + second
    return total
answer = add(10, 5)
print(answer)
```

**Expected output**

```text
15
```

**How it works:** The function calculates total. return sends 15 back. answer stores it.

**Important methods or syntax:** Returning strings, numbers, lists and dictionaries; early returns; returning multiple values as a tuple.

**Common mistake:** A function without return gives None. Code after return in the same path is not executed.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain variable scope.

**Beginner answer:** Scope describes where a variable name can be accessed. A local variable is created inside a function.

**Example code**

```python
course = "Python"
def show_course():
    topic = "Functions"
    print(course, topic)
show_course()
```

**Expected output**

```text
Python Functions
```

**How it works:** topic is local. course is global to this module and can be read inside the function.

**Important methods or syntax:** LEGB name lookup: Local, Enclosing, Global, Built-in. Prefer parameters and return values over global mutation.

**Common mistake:** Reading a local variable outside its function causes NameError. Assignment can make a name local unexpectedly.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain default arguments and keyword arguments.

**Beginner answer:** A default argument is used when the caller does not supply a value. Keyword arguments make a call easier to understand.

**Example code**

```python
def make_label(name, level="beginner"):
    return f"{name} - {level}"
print(make_label("Anu"))
print(make_label(name="Ravi", level="intermediate"))
```

**Expected output**

```text
Anu - beginner
Ravi - intermediate
```

**How it works:** level has a default. The second call passes both values by parameter name.

**Important methods or syntax:** Use immutable defaults. For optional lists, use None and create a new list inside the function.

**Common mistake:** A required parameter cannot follow a default parameter in the definition. Avoid [] as a mutable default.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain comprehensions.

**Beginner answer:** A comprehension builds a new collection from an iterable. Learn the ordinary loop first, then use a comprehension when it remains readable.

**Example code**

```python
names = ["anu", "ravi", "sara"]
upper_names = []
for name in names:
    upper_names.append(name.upper())
print(upper_names)
short_names = [name for name in names if len(name) <= 4]
print(short_names)
```

**Expected output**

```text
['ANU', 'RAVI', 'SARA']
['anu', 'ravi']
```

**How it works:** The loop creates the first result. The list comprehension selects names with four or fewer characters.

**Important methods or syntax:** List, set and dictionary comprehensions; conditional expressions; nested comprehensions only when clear.

**Common mistake:** Dense nested comprehensions are hard to debug. Do not use one merely to shorten code.

**Follow-up:** Where would you use this in a Python AI application?


### Q7. Explain small reusable toolkit.

**Beginner answer:** A toolkit combines small functions, each responsible for one step. This makes the code easier to test and reuse.

**Example code**

```python
def clean_text(text):
    return text.strip()
def word_count(text):
    return len(text.split())
def summarize(text):
    cleaned = clean_text(text)
    return {"text": cleaned, "words": word_count(cleaned)}
print(summarize("  Learn Python today  "))
```

**Expected output**

```text
{'text': 'Learn Python today', 'words': 3}
```

**How it works:** summarize() calls two smaller functions and combines their results in a dictionary.

**Important methods or syntax:** Add type hints, docstrings, input validation and unit tests when comfortable.

**Common mistake:** A function should not silently do unrelated tasks. Validate None and unexpected input types when the function is public.

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

### Exercise 1 — Defining and calling functions

**Task:** Write welcome(), clean_question() and display_result() as separate functions.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — Parameters and arguments

**Task:** Create a function that accepts a student's name and today's topic.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Return values

**Task:** Write calculate_average(marks) that returns a number.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Variable scope

**Task:** Create two functions and demonstrate that one function's local variable is not available globally.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Default arguments and keyword arguments

**Task:** Write a function with a default language parameter.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Comprehensions

**Task:** Convert names to title case and filter short names.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 7 — Small reusable toolkit

**Task:** Extend the toolkit with character_count() and test empty input.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — Reusable Text Processing Toolkit

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
