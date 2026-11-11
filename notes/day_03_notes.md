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

# Deep teaching workbook — guided labs and mentor walkthroughs

This workbook is part of the class lesson. Complete each lab with your trainer; do not treat it as optional filler.

## Guided classroom lab 1: Learning objectives

### Step 1 — Say the idea in everyday language
Today's idea is "Learning objectives". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Learning objectives" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Learning objectives" and explain why the output is correct.

---

## Guided classroom lab 2: Important vocabulary

### Step 1 — Say the idea in everyday language
Today's idea is "Important vocabulary". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Important vocabulary" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Important vocabulary" and explain why the output is correct.

---

## Guided classroom lab 3: Class plan

### Step 1 — Say the idea in everyday language
Today's idea is "Class plan". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Class plan" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Class plan" and explain why the output is correct.

---

## Guided classroom lab 4: Defining and calling functions

### Step 1 — Say the idea in everyday language
Today's idea is "Defining and calling functions". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Defining and calling functions" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Defining and calling functions" and explain why the output is correct.

---

## Guided classroom lab 5: Parameters and arguments

### Step 1 — Say the idea in everyday language
Today's idea is "Parameters and arguments". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Parameters and arguments" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Parameters and arguments" and explain why the output is correct.

---

## Guided classroom lab 6: Return values

### Step 1 — Say the idea in everyday language
Today's idea is "Return values". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Return values" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Return values" and explain why the output is correct.

---

## Guided classroom lab 7: Variable scope

### Step 1 — Say the idea in everyday language
Today's idea is "Variable scope". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Variable scope" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Variable scope" and explain why the output is correct.

---

## Guided classroom lab 8: Default arguments and keyword arguments

### Step 1 — Say the idea in everyday language
Today's idea is "Default arguments and keyword arguments". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Default arguments and keyword arguments" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Default arguments and keyword arguments" and explain why the output is correct.

---

## Guided classroom lab 9: Comprehensions

### Step 1 — Say the idea in everyday language
Today's idea is "Comprehensions". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Comprehensions" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Comprehensions" and explain why the output is correct.

---

## Guided classroom lab 10: Small reusable toolkit

### Step 1 — Say the idea in everyday language
Today's idea is "Small reusable toolkit". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

Ask yourself:
- What information do I start with?
- What action does the program perform?
- What result should I see?
- What should happen if the input is missing?
- What should happen if the input is the wrong type?

### Step 2 — Read the smallest example
Open the first code example in this lesson. Read it from top to bottom.
Do not run it immediately.
Underline the variable names.
Circle the function or method name.
Mark the input values.
Mark the line that produces the result.
Write a one-sentence explanation beside every important line.

### Step 3 — Predict before execution
Write down what you expect the program to display.
Run the program once.
Compare the actual result with your prediction.
If the result differs, do not randomly change the code.
Check the value, type, order of operations and indentation.
Run the smallest part that reproduces the difference.

### Step 4 — Change one thing at a time
Change one input value.
Predict the new result.
Run the program again.
Restore the original value.
Change a second value.
Predict again.
Run again.
Explain the difference between the two results.

### Step 5 — Trace the program
Use a notebook to make a trace table.

| Step | Variable or operation | Value before | Action | Value after |
|---:|---|---|---|---|
| 1 | First input | Empty | Supply sample input | Sample input |
| 2 | First operation | Sample input | Apply the lesson concept | Intermediate result |
| 3 | Second operation | Intermediate result | Continue processing | Final result |
| 4 | Output | Final result | Display or return | Visible result |

Fill the table with the actual values from your program.
Do not copy the words 'sample input' into every cell; write the real values.

### Step 6 — Beginner coding challenge
Build a tiny program that demonstrates "Small reusable toolkit" without using a framework.
Use no more than three variables at first.
Use one small function if the concept requires a function.
Use sample values that a college student can understand.
Print the result with a clear label.
Run the program.
Change one input.
Run it again.
Explain the change.

### Step 7 — Make the program safer
Ask what could go wrong if the user supplies an empty value.
Ask what could go wrong if the user supplies a different data type.
Ask what could go wrong if the collection has no items.
Ask what could go wrong if a requested key or index does not exist.
Choose a suitable validation or exception-handling approach.
Do not catch every possible exception without understanding it.
Show the user a helpful message when an expected problem occurs.

### Step 8 — Improve readability
Use names that describe the meaning of each value.
Keep one operation per line while learning.
Add a short comment only when it explains a reason that is not obvious.
Remove code that is no longer used.
Keep the example small enough to explain aloud.
Do not compress beginner code into a clever one-liner.

### Step 9 — Explain the concept to another person
Start with a one-sentence definition.
Describe why a developer needs it.
Walk through the example.
Explain the expected output.
Describe one common error.
Give one practical application.
Ask the other person to change an input and predict the result.

### Step 10 — Trainer observation
The trainer should ask the student to close the notes.
The student should recreate the smallest example.
The student should explain each important line.
The student should modify one input without help.
The student should identify one limitation.
The trainer should correct misunderstandings before moving forward.

### Independent practice record
- [ ] I explained the concept in simple words.
- [ ] I typed the example myself.
- [ ] I predicted the output.
- [ ] I ran the code successfully.
- [ ] I changed an input and explained the result.
- [ ] I tested one unusual input.
- [ ] I completed the challenge.
- [ ] I explained the code aloud.

**Mastery evidence:** the student can independently demonstrate "Small reusable toolkit" and explain why the output is correct.

---


---

# 14. Learn every function concept by running it

This section is the detailed classroom walkthrough. Type each example into a new file called `practice_functions.py`. Run one example at a time.

## 14.1 Defining a function vs calling a function

A function is a named, reusable group of Python statements.

```python
def say_hello():
    print("Hello, learner!")

print("Before calling")
say_hello()
print("After calling")
```

Output:

```text
Before calling
Hello, learner!
After calling
```

Read it in this order:
1. `def` tells Python that a function is being defined.
2. `say_hello` is the function's name.
3. `()` holds parameters. This function has none.
4. The colon `:` starts the function body.
5. The indented `print()` belongs to the function.
6. The line `say_hello()` calls it. That is when its body runs.

**Important:** defining a function does not execute its body. Calling it does.

Common mistakes:
- `def say_hello()` without the colon causes a syntax error.
- Missing indentation causes an indentation error.
- Writing `say_hello` without parentheses refers to the function; it does not call it.
- Defining a function but never calling it means its body does not run.

## 14.2 Parameters and arguments

A parameter is a variable name in the function definition. An argument is the actual value passed to the function call.

```python
def greet_student(name):
    print("Welcome,", name)

greet_student("Anu")
greet_student("Ravi")
```

Output:

```text
Welcome, Anu
Welcome, Ravi
```

Here, `name` is the parameter. `"Anu"` and `"Ravi"` are arguments. Each call supplies a different value.

### Two parameters

```python
def calculate_total(price, quantity):
    total = price * quantity
    print("Total:", total)

calculate_total(100, 3)
```

Output:

```text
Total: 300
```

The first argument goes to `price`; the second goes to `quantity`. This is positional argument matching.

### Keyword arguments

```python
def student_card(name, course):
    print(name, "is learning", course)

student_card(course="GenAI", name="Meena")
```

Output:

```text
Meena is learning GenAI
```

Keyword arguments use parameter names, so the order can change. Use the exact parameter name. Do not put a positional argument after a keyword argument in the same call.

### Default arguments

```python
def send_welcome(name, course="Python"):
    print(f"Welcome {name}. Your course is {course}.")

send_welcome("Anu")
send_welcome("Ravi", "GenAI")
```

Output:

```text
Welcome Anu. Your course is Python.
Welcome Ravi. Your course is GenAI.
```

The default `"Python"` is used only when the caller does not provide `course`.

A default parameter must come after required parameters:

```python
def create_user(name, role="student"):
    print(name, role)
```

Do not write `def create_user(role="student", name):`; Python rejects a required parameter after a default parameter.

### Variable number of positional arguments: *args

Use `*args` when a function should accept any number of extra positional arguments. Inside the function, `args` is a tuple.

```python
def calculate_sum(*numbers):
    print(numbers)
    return sum(numbers)

print(calculate_sum(10, 20))
print(calculate_sum(10, 20, 30, 40))
```

Output:

```text
(10, 20)
30
(10, 20, 30, 40)
100
```

- The asterisk collects extra positional arguments into a tuple.
- `sum()` is a built-in function that adds numeric items and returns the total.
- Use `*args` only when the number of values genuinely varies.

### Variable number of keyword arguments: **kwargs

Use `**kwargs` when a function should accept extra named arguments. Inside the function, `kwargs` is a dictionary.

```python
def show_profile(**details):
    for key, value in details.items():
        print(key, ":", value)

show_profile(name="Anu", course="Python", city="Hyderabad")
```

Output:

```text
name : Anu
course : Python
city : Hyderabad
```

- `**` collects extra keyword arguments.
- `.items()` provides key-value pairs from the dictionary.
- The names `args` and `kwargs` are conventions; the asterisks perform the collection.

## 14.3 print() vs return — one of the most important differences

`print()` displays something on the screen. `return` sends a result back to the code that called the function.

```python
def show_total(a, b):
    print(a + b)

def get_total(a, b):
    return a + b

first_result = show_total(5, 3)
second_result = get_total(5, 3)

print("First result:", first_result)
print("Second result:", second_result)
```

Output:

```text
8
First result: None
Second result: 8
```

Why?
- `show_total()` displays 8 but has no explicit return statement. Python therefore returns `None`.
- `get_total()` returns 8. The caller stores it in `second_result`.

Use `print()` when the goal is to show a message to a person. Use `return` when another part of the program must use the calculated result.

### Return different data types

```python
def get_course():
    return "Python"

def get_score():
    return 95

def get_skills():
    return ["Python", "SQL"]

def get_student():
    return {"name": "Anu", "score": 95}

print(get_course())
print(get_score())
print(get_skills())
print(get_student())
```

Output:

```text
Python
95
['Python', 'SQL']
{'name': 'Anu', 'score': 95}
```

A function can return a string, number, list, dictionary or another object.

### Returning more than one value

```python
def get_name_and_score():
    return "Anu", 95

name, score = get_name_and_score()
print(name)
print(score)
```

Output:

```text
Anu
95
```

Python packages these returned values into a tuple. The assignment unpacks the tuple into two variables.

### Early return

```python
def get_average(marks):
    if len(marks) == 0:
        return None

    return sum(marks) / len(marks)

print(get_average([80, 90, 100]))
print(get_average([]))
```

Output:

```text
90.0
None
```

The first return exits the function immediately when there are no marks. This avoids dividing by zero.

## 14.4 Variable scope — where can a name be used?

```python
course = "GenAI"

def show_topic():
    topic = "Python functions"
    print(course)
    print(topic)

show_topic()
print(course)
```

Output:

```text
GenAI
Python functions
GenAI
```

- `course` is defined outside the function. It is a module-level (global) name.
- `topic` is created inside the function. It is local to that function.
- The function can read the global name, but code outside cannot directly read the function's local variable.

This fails:

```python
def create_topic():
    topic = "Functions"

create_topic()
print(topic)  # NameError: topic is not defined here
```

### Prefer parameters and return values

Instead of changing a global variable, pass data in and return the result:

```python
def add_tax(price, tax_rate):
    return price + (price * tax_rate)

final_price = add_tax(100, 0.18)
print(final_price)
```

Output:

```text
118.0
```

This function is easier to test because its inputs and output are visible. Avoid using `global` in beginner projects unless you have a clear reason.

## 14.5 Comprehensions — first understand the loop

A comprehension is a compact way to create a new collection. It does not magically make every program faster or easier to read.

### List comprehension

First, write the ordinary loop:

```python
scores = [40, 75, 90]
passed = []

for score in scores:
    if score >= 50:
        passed.append(score)

print(passed)
```

Output:

```text
[75, 90]
```

Now the equivalent list comprehension:

```python
scores = [40, 75, 90]
passed = [score for score in scores if score >= 50]
print(passed)
```

Output:

```text
[75, 90]
```

Read it as: create a list of `score` values, for each `score` in `scores`, only if the score is at least 50.

### Transform values

```python
names = ["anu", "ravi", "meena"]
capital_names = [name.upper() for name in names]
print(capital_names)
```

Output:

```text
['ANU', 'RAVI', 'MEENA']
```

`upper()` is a string method. It returns an uppercase string; it does not modify the original string.

### Set comprehension

```python
words = ["ai", "python", "ai", "rag"]
unique_lengths = {len(word) for word in words}
print(unique_lengths)
```

Output contains the unique lengths 2, 3 and 6. Set display order is not guaranteed.

### Dictionary comprehension

```python
names = ["Anu", "Ravi"]
lengths = {name: len(name) for name in names}
print(lengths)
```

Output:

```text
{'Anu': 3, 'Ravi': 4}
```

### When should you NOT use a comprehension?

Use a normal loop when:
- There are several steps inside the loop.
- You need detailed error handling.
- The comprehension becomes difficult to read.
- You need to print progress or perform several side effects.

Readable code is more important than short code.

---

# 15. Complete guided project — Reusable Text Processing Toolkit

## What you are building

A small command-line utility that receives text and reports:
- cleaned text,
- number of characters,
- number of words,
- unique words,
- words longer than a chosen length.

This is a foundation for later tasks such as cleaning user prompts, preparing documents for search and processing text before sending it to an LLM. It is not yet an LLM application; it uses plain Python only.

## Step 1 — create the project

Create this folder and file:

```text
day_03_project/
└── main.py
```

## Step 2 — type the complete code

```python
def clean_text(text):
    """Remove spaces from the beginning and end of text."""
    return text.strip()


def count_characters(text):
    """Return the number of characters, including spaces."""
    return len(text)


def count_words(text):
    """Return the number of words separated by whitespace."""
    cleaned = clean_text(text)

    if cleaned == "":
        return 0

    return len(cleaned.split())


def get_unique_words(text):
    """Return unique lowercase words without common punctuation."""
    cleaned = clean_text(text).lower()
    words = cleaned.split()

    cleaned_words = []
    for word in words:
        word = word.strip(".,!?;:")
        if word:
            cleaned_words.append(word)

    return sorted(set(cleaned_words))


def get_long_words(text, minimum_length=5):
    """Return words whose character count is at least minimum_length."""
    cleaned = clean_text(text).lower()
    words = cleaned.split()

    result = []
    for word in words:
        word = word.strip(".,!?;:")
        if len(word) >= minimum_length:
            result.append(word)

    return result


def analyze_text(text):
    """Return all text analysis results in one dictionary."""
    cleaned = clean_text(text)

    return {
        "cleaned_text": cleaned,
        "characters": count_characters(cleaned),
        "words": count_words(cleaned),
        "unique_words": get_unique_words(cleaned),
        "long_words": get_long_words(cleaned)
    }


def main():
    print("TECHPHILE TEXT TOOLKIT")
    user_text = input("Enter a sentence: ")

    if not user_text.strip():
        print("Please enter some text. Empty input cannot be analyzed.")
        return

    report = analyze_text(user_text)

    print("\n--- TEXT REPORT ---")
    print("Cleaned text:", report["cleaned_text"])
    print("Characters:", report["characters"])
    print("Words:", report["words"])
    print("Unique words:", report["unique_words"])
    print("Long words:", report["long_words"])


if __name__ == "__main__":
    main()
```

## Step 3 — run the program

Open a terminal in the `day_03_project` folder.

Windows:

```bash
py main.py
```

macOS / Linux:

```bash
python3 main.py
```

No external package or API key is required. This project uses Python's built-in functions and string methods.

## Step 4 — expected output

Input:

```text
  Python helps students learn AI. Python is useful!
```

Output:

```text
TECHPHILE TEXT TOOLKIT
Enter a sentence:   Python helps students learn AI. Python is useful!

--- TEXT REPORT ---
Cleaned text: Python helps students learn AI. Python is useful!
Characters: 49
Words: 8
Unique words: ['ai', 'helps', 'is', 'learn', 'python', 'students', 'useful']
Long words: ['python', 'helps', 'students', 'learn', 'python', 'useful']
```

## Step 5 — understand every function

| Function | Input | What it does | Return value |
|---|---|---|---|
| `clean_text(text)` | One string | Removes surrounding whitespace | New string |
| `count_characters(text)` | One string | Counts characters | Integer |
| `count_words(text)` | One string | Splits text and counts words | Integer |
| `get_unique_words(text)` | One string | Normalizes and removes duplicates | Sorted list |
| `get_long_words(text, minimum_length=5)` | String and optional integer | Selects words meeting length threshold | List |
| `analyze_text(text)` | One string | Calls the smaller functions | Dictionary |
| `main()` | No parameters | Handles input and displays report | No explicit return; returns None |

### Understand the Python features used

- `def`: starts a function definition.
- `return`: sends a result to the caller.
- `strip()`: returns a string without surrounding whitespace.
- `lower()`: returns a lowercase version of a string.
- `split()`: returns a list of words.
- `len()`: returns the number of characters or items.
- `for`: visits each item in a sequence.
- `append()`: adds one item to a list and returns None.
- `if`: runs a block only when its condition is true.
- `set()`: creates a collection of unique values.
- `sorted()`: returns a new sorted list.
- `dict`: stores named results as key-value pairs.
- `input()`: reads text typed by the user.
- `__name__ == "__main__"`: calls main when this file is run directly.

## Step 6 — test it with these inputs

| Test | Input | What should happen |
|---|---|---|
| Normal text | `Python is useful` | Report shows 3 words |
| Leading/trailing spaces | `  Learn Python  ` | Cleaned text has no outside spaces |
| Empty input | Press Enter | Friendly message; no report |
| Repeated word | `AI AI Python` | Unique words contains AI once (lowercase) |
| Punctuation | `Hello, world!` | Unique words are hello and world |
| One word | `Python` | Word count is 1 |

## Step 7 — common errors and how to fix them

| Error / symptom | Why it happens | Fix |
|---|---|---|
| `IndentationError` | Function or loop body is not indented consistently | Use four spaces for each block |
| `NameError` | Function name is misspelled or not defined before use | Check spelling and definition |
| `TypeError` in `len()` or `strip()` | A non-string value was passed | Convert or validate the value before using string methods |
| Program shows no report | `main()` was not called | Keep the final `if __name__...` block |
| File not found | Terminal is in a different folder | Change directory to `day_03_project` |
| Word count surprises you | Punctuation is attached to a word or multiple spaces exist | Inspect `split()` output; whitespace splitting handles repeated spaces |

## Step 8 — improve the project

Try these in order. Do not skip to the last task.

1. Add `count_sentences(text)`. Start by counting periods, question marks and exclamation marks. State the limitation: abbreviations such as "Dr." also contain periods.
2. Add an optional `minimum_length` argument to `get_long_words()`. Call it with 4 and then 7.
3. Add a function that returns the most frequent word. Hint: use a dictionary as a counter.
4. Add a menu so the user can analyze more than one sentence without restarting the program.
5. Add automated tests after learning the testing topic later in the course.

## Step 9 — project submission checklist

- [ ] I created the folder and typed the code into `main.py`.
- [ ] I can run it using the correct command for my operating system.
- [ ] I understand the input and output of each function.
- [ ] I can explain why the smaller functions return values.
- [ ] I tested normal, empty and repeated-word inputs.
- [ ] I can add one new feature without copying a finished answer.
- [ ] I can explain how text cleaning helps prepare data for a future AI application.

---

# 16. Day 3 self-assessment — answer before reading the guide

1. What is the difference between defining and calling a function?
2. In `def greet(name):`, what is `name`?
3. In `greet("Anu")`, what is `"Anu"`?
4. What is the difference between `print()` and `return`?
5. What does a function return if it reaches the end without a return statement?
6. What is a local variable?
7. Why should a mutable list not normally be used as a default argument?
8. What do `*args` and `**kwargs` collect?
9. What does a list comprehension create?
10. When is a normal for loop clearer than a comprehension?

## Answer guide

1. Defining creates the function; calling executes its body.
2. It is a parameter.
3. It is an argument.
4. print displays output; return sends a value back to the caller.
5. `None`.
6. A variable created inside a function and normally available only there.
7. The same list object can be reused across calls, causing unexpected shared changes.
8. `*args` collects extra positional arguments into a tuple; `**kwargs` collects extra keyword arguments into a dictionary.
9. A new list built by iterating over values, optionally transforming or filtering them.
10. When the logic has several steps, side effects or complex error handling.

## Day 3 readiness gate

Do not move on until you can:
- Define and call a function without looking at notes.
- Pass positional, keyword and default arguments.
- Explain `*args` and `**kwargs` with a small example.
- Predict the result of a function that prints versus one that returns.
- Explain local and global scope.
- Convert a simple for loop into a readable list comprehension.
- Run the Text Processing Toolkit and explain each function.
- Add one small feature and test it yourself.
