# Day 03 — Functions, Parameters, Arguments, Return Values, Scope and Comprehensions

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** Reusable Text Processing Toolkit  
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

1. Explain defining and calling functions using a simple example.
2. Explain parameters and arguments using a simple example.
3. Explain return values using a simple example.
4. Explain variable scope using a simple example.
5. Explain default arguments and keyword arguments using a simple example.
6. Explain comprehensions using a simple example.
7. Explain small reusable toolkit using a simple example.
8. Apply defining and calling functions in the Reusable Text Processing Toolkit.
9. Apply parameters and arguments in the Reusable Text Processing Toolkit.
10. Apply return values in the Reusable Text Processing Toolkit.
11. Apply variable scope in the Reusable Text Processing Toolkit.
12. Apply default arguments and keyword arguments in the Reusable Text Processing Toolkit.
13. Apply comprehensions in the Reusable Text Processing Toolkit.
14. Apply small reusable toolkit in the Reusable Text Processing Toolkit.

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

## 3. Defining and calling functions

### Beginner explanation

A function is a named set of instructions that can be reused. Defining it does not run it; calling it does.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

def begins a definition. The indented body belongs to the function. greet() calls it.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Function names, docstrings, return statements, positional calls and keyword calls.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Forgetting parentheses, incorrect indentation or defining a function but never calling it.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write welcome(), clean_question() and display_result() as separate functions.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define defining and calling functions in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. Parameters and arguments

### Beginner explanation

Parameters are names in the function definition. Arguments are actual values supplied during a call.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

name and course are parameters. The strings supplied are arguments. Keyword arguments identify parameters by name.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Positional, keyword, default and variable-length arguments (*args and **kwargs) after the basic form is clear.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Missing required arguments cause TypeError. Positional arguments must not follow keyword arguments in a call.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create a function that accepts a student's name and today's topic.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define parameters and arguments in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Return values

### Beginner explanation

return sends a result back to the caller. print() displays information but does not return that displayed text.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

The function calculates total. return sends 15 back. answer stores it.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Returning strings, numbers, lists and dictionaries; early returns; returning multiple values as a tuple.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A function without return gives None. Code after return in the same path is not executed.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write calculate_average(marks) that returns a number.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define return values in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Variable scope

### Beginner explanation

Scope describes where a variable name can be accessed. A local variable is created inside a function.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

topic is local. course is global to this module and can be read inside the function.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

LEGB name lookup: Local, Enclosing, Global, Built-in. Prefer parameters and return values over global mutation.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Reading a local variable outside its function causes NameError. Assignment can make a name local unexpectedly.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create two functions and demonstrate that one function's local variable is not available globally.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define variable scope in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Default arguments and keyword arguments

### Beginner explanation

A default argument is used when the caller does not supply a value. Keyword arguments make a call easier to understand.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

level has a default. The second call passes both values by parameter name.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Use immutable defaults. For optional lists, use None and create a new list inside the function.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A required parameter cannot follow a default parameter in the definition. Avoid [] as a mutable default.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Write a function with a default language parameter.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define default arguments and keyword arguments in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. Comprehensions

### Beginner explanation

A comprehension builds a new collection from an iterable. Learn the ordinary loop first, then use a comprehension when it remains readable.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

The loop creates the first result. The list comprehension selects names with four or fewer characters.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

List, set and dictionary comprehensions; conditional expressions; nested comprehensions only when clear.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Dense nested comprehensions are hard to debug. Do not use one merely to shorten code.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Convert names to title case and filter short names.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define comprehensions in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 9. Small reusable toolkit

### Beginner explanation

A toolkit combines small functions, each responsible for one step. This makes the code easier to test and reuse.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

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

### Walkthrough

summarize() calls two smaller functions and combines their results in a dictionary.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Add type hints, docstrings, input validation and unit tests when comfortable.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A function should not silently do unrelated tasks. Validate None and unexpected input types when the function is public.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Extend the toolkit with character_count() and test empty input.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define small reusable toolkit in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 10. Guided mini-project — Reusable Text Processing Toolkit

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
day_03_project/
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

# 11. Daily revision questions

1. What is defining and calling functions?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is parameters and arguments?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is return values?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is variable scope?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is default arguments and keyword arguments?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is comprehensions?
6.1 Why would a Python developer use it?
6.2 What mistake should a beginner avoid?

7. What is small reusable toolkit?
7.1 Why would a Python developer use it?
7.2 What mistake should a beginner avoid?

# 12. Daily quiz

1. Which concept from today's lesson would you use for the sample problem?
2. What does the main method or function in one example do?
3. What happens if the input is missing or invalid?
4. Why should code be divided into small understandable steps?
5. Give one use of today's concepts in an AI application.

**Answer method:** answer in your own words, then prove your understanding with a small code example.

# 13. Interview practice

1. Explain defining and calling functions to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain parameters and arguments to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain return values to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain variable scope to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain default arguments and keyword arguments to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain comprehensions to a beginner.
6.1 Give a practical example.
6.2 What is one limitation or common error?

7. Explain small reusable toolkit to a beginner.
7.1 Give a practical example.
7.2 What is one limitation or common error?

## How to structure an interview answer

1. Give a direct definition.
2. Explain how it works in two or three steps.
3. Give a small example.
4. Mention one real use.
5. Mention one limitation or error case.

# 14. Trainer assessment rubric

| Area | Evidence |
|---|---|
| Concept understanding | Student explains without reading |
| Code reading | Student describes important lines |
| Practical execution | Student runs and modifies code |
| Debugging | Student locates a simple error |
| Project | Student applies the day's concepts |
| Interview communication | Student gives a clear structured answer |

# 15. What you should remember

- Understand why a feature is used before memorizing syntax.
- Type and run each example yourself.
- Know the difference between a function, method, argument and return value.
- Read error messages instead of guessing.
- Build the project in small steps.
- Be ready to teach the concept to another beginner.

**Day 3 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.
