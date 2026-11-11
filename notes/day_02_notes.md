# Day 02 — Python Data Structures: Strings, Lists, Tuples, Sets and Dictionaries

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** AI Conversation Data Manager  
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

1. Explain strings using a simple example.
2. Explain lists using a simple example.
3. Explain tuples using a simple example.
4. Explain sets using a simple example.
5. Explain dictionaries using a simple example.
6. Explain choosing a data structure using a simple example.
7. Apply strings in the AI Conversation Data Manager.
8. Apply lists in the AI Conversation Data Manager.
9. Apply tuples in the AI Conversation Data Manager.
10. Apply sets in the AI Conversation Data Manager.
11. Apply dictionaries in the AI Conversation Data Manager.
12. Apply choosing a data structure in the AI Conversation Data Manager.

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

## 3. Strings

### Beginner explanation

A string stores text such as a student's question. Text is written inside quotes.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
message = "  Explain Python  "
print(message)
print(message.strip())
print(message.lower())
print(len(message))
```

**Expected output**

```text
  Explain Python  
Explain Python
  explain python  
18
```

### Walkthrough

strip() removes surrounding whitespace; lower() returns lowercase text; len() counts characters. Strings are immutable, so these methods return new values.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

upper(), title(), capitalize(), replace(old, new), split(separator), join(iterable), startswith(), endswith(), find() and count().

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

IndexError for an invalid position; confusing strip() with replace(); expecting a method to modify the original string.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Clean a question, count its characters, split it into words and explain the output.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define strings in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. Lists

### Beginner explanation

A list stores an ordered collection that can be changed. It is useful for messages, tasks or student names.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
messages = ["Hi", "Explain loops"]
messages.append("Give an example")
print(messages)
print(messages[0])
print(len(messages))
```

**Expected output**

```text
['Hi', 'Explain loops', 'Give an example']
Hi
3
```

### Walkthrough

append() adds one item. Index zero is the first item. len() returns the number of items.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

append(), extend(), insert(), remove(), pop(), clear(), index(), count(), sort(), reverse() and copy().

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

IndexError, ValueError from remove() when the value is absent, and modifying a list while iterating over it.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create a conversation list, add a message, replace one message and remove an unwanted message.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define lists in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Tuples

### Beginner explanation

A tuple is ordered like a list, but it cannot be changed after creation. It suits fixed records.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
student = ("Anu", 101, "CSE")
print(student[0])
print(student.count("CSE"))
print(student.index(101))
```

**Expected output**

```text
Anu
1
1
```

### Walkthrough

Indexing reads a value. count() counts occurrences. index() finds the first matching position.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

count(), index(), len(), tuple() and unpacking: name, roll, dept = student.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

TypeError when trying to assign to a tuple position; a one-item tuple needs a trailing comma.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Store a fixed student identity record and unpack it into three variables.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define tuples in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Sets

### Beginner explanation

A set stores unique values and is useful for removing duplicates or comparing groups.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
skills = {"Python", "SQL", "Python"}
skills.add("Git")
print(len(skills))
print("SQL" in skills)
```

**Expected output**

```text
3
True
```

### Walkthrough

The duplicate is stored once. add() inserts an item. in checks membership. Set display order is not guaranteed.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

add(), update(), discard(), remove(), union(), intersection(), difference(), issubset() and issuperset().

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not use numeric indexes with sets. remove() raises KeyError for a missing value; discard() does not.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Find unique skills and common skills between two students.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define sets in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Dictionaries

### Beginner explanation

A dictionary stores key-value pairs. A key is a label used to find its value.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
student = {"name": "Anu", "marks": 85}
print(student["name"])
print(student.get("age", "Not supplied"))
student["department"] = "CSE"
print(student)
```

**Expected output**

```text
Anu
Not supplied
{'name': 'Anu', 'marks': 85, 'department': 'CSE'}
```

### Walkthrough

Square brackets read a required key. get() safely reads an optional key. Assignment adds or updates a key.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

keys(), values(), items(), get(), update(), pop(), setdefault(), copy() and dictionary comprehensions.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

KeyError when a key is absent; using mutable objects as keys; confusing keys with values.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Represent one chat message with role, content and timestamp fields.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define dictionaries in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. Choosing a data structure

### Beginner explanation

Choose a structure based on what the data needs to do: preserve order, allow changes, prevent duplicates or map labels to values.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
question = "Explain Python"
tags = ["beginner", "python"]
fixed_id = (101, "Anu")
unique_tags = set(tags)
profile = {"name": "Anu", "level": "beginner"}
print(type(question).__name__, type(tags).__name__)
print(type(fixed_id).__name__, type(unique_tags).__name__)
print(profile["name"])
```

**Expected output**

```text
str list
tuple set
Anu
```

### Walkthrough

type() shows the object's type. Each structure has a different purpose; there is no single best collection for every problem.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Convert between list(), tuple(), set() and dict() only when the target structure makes sense. Consider ordering, mutability and uniqueness.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Converting a set to a list does not restore an original order. Converting a list to a set removes duplicates.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Choose a suitable structure for chat history, user profile, unique labels and fixed coordinates.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define choosing a data structure in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 9. Guided mini-project — AI Conversation Data Manager

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
day_02_project/
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

1. What is strings?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is lists?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is tuples?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is sets?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is dictionaries?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is choosing a data structure?
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

1. Explain strings to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain lists to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain tuples to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain sets to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain dictionaries to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain choosing a data structure to a beginner.
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

**Day 2 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.

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

## Guided classroom lab 4: Strings

### Step 1 — Say the idea in everyday language
Today's idea is "Strings". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Strings" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Strings" and explain why the output is correct.

---

## Guided classroom lab 5: Lists

### Step 1 — Say the idea in everyday language
Today's idea is "Lists". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Lists" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Lists" and explain why the output is correct.

---

## Guided classroom lab 6: Tuples

### Step 1 — Say the idea in everyday language
Today's idea is "Tuples". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Tuples" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Tuples" and explain why the output is correct.

---

## Guided classroom lab 7: Sets

### Step 1 — Say the idea in everyday language
Today's idea is "Sets". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Sets" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Sets" and explain why the output is correct.

---

## Guided classroom lab 8: Dictionaries

### Step 1 — Say the idea in everyday language
Today's idea is "Dictionaries". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Dictionaries" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Dictionaries" and explain why the output is correct.

---

## Guided classroom lab 9: Choosing a data structure

### Step 1 — Say the idea in everyday language
Today's idea is "Choosing a data structure". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Choosing a data structure" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Choosing a data structure" and explain why the output is correct.

---


---

# 15. Essential method-by-method workbook — do not skip

The earlier examples introduced the structures. This section teaches the operations individually. A method is called using the object, a dot, its name and parentheses: `messages.append("Hello")`.

## 15.1 List methods — all eleven

A list is ordered and changeable. Use it when you need to keep several items and may add, remove or update them.

Start with:

```python
messages = ["Hi", "Explain loops", "Give an example"]
```

| Method | What it does | Argument | Return value | Changes original list? |
|---|---|---|---|---|
| `append(x)` | Adds x as one item at the end | One item | `None` | Yes |
| `extend(items)` | Adds each item from an iterable | Iterable such as a list | `None` | Yes |
| `insert(i, x)` | Inserts x at position i | Index and item | `None` | Yes |
| `remove(x)` | Removes the first matching value | Value to remove | `None` | Yes |
| `pop(i)` | Removes and gives back item at index i; default is last | Optional index | Removed item | Yes |
| `clear()` | Removes every item | None | `None` | Yes |
| `index(x)` | Finds first position of x | Value to find | Integer index | No |
| `count(x)` | Counts occurrences of x | Value to count | Integer count | No |
| `sort()` | Sorts the list in place | Optional `key`, `reverse` | `None` | Yes |
| `reverse()` | Reverses item order in place | None | `None` | Yes |
| `copy()` | Makes a shallow copy | None | New list | No |

### A. append() — add one item

```python
messages = ["Hi", "How are you?"]
result = messages.append("Explain Python")

print(messages)
print(result)
```

Output:

```text
['Hi', 'How are you?', 'Explain Python']
None
```

**Understand it:** `append()` changes the existing list. It adds its argument as one single item. It does not return the updated list; its return value is `None`.

A frequent beginner mistake is writing `messages = messages.append("Hello")`. That makes `messages` become `None`. Correct approach: call `messages.append("Hello")` on its own line.

### B. extend() — add multiple items one by one

```python
messages = ["Hi"]
messages.extend(["Hello", "Good morning"])
print(messages)
```

Output:

```text
['Hi', 'Hello', 'Good morning']
```

### append() vs extend()

```python
a = ["Hi"]
a.append(["Hello", "Bye"])
print(a)

b = ["Hi"]
b.extend(["Hello", "Bye"])
print(b)
```

Output:

```text
['Hi', ['Hello', 'Bye']]
['Hi', 'Hello', 'Bye']
```

**Memory rule:**
- `append(one_thing)`: put that one thing at the end. If it is a list, the whole list becomes one nested item.
- `extend(iterable)`: take items out of the iterable and add them individually.

### C. insert() — add at a chosen position

```python
messages = ["Hi", "Bye"]
messages.insert(1, "Can you help?")
print(messages)
```

Output:

```text
['Hi', 'Can you help?', 'Bye']
```

The first argument `1` is the index. Python positions start at zero, so index 1 is the second position.

### D. remove() — remove by value

```python
messages = ["Hi", "Spam", "Hello", "Spam"]
messages.remove("Spam")
print(messages)
```

Output:

```text
['Hi', 'Hello', 'Spam']
```

It removes only the first matching value. If the value does not exist, Python raises `ValueError`.

Safer beginner version:

```python
if "Spam" in messages:
    messages.remove("Spam")
```

### E. pop() — remove by position and receive the removed item

```python
messages = ["Hi", "Hello", "Bye"]
removed_message = messages.pop(1)

print(removed_message)
print(messages)
```

Output:

```text
Hello
['Hi', 'Bye']
```

- `pop(1)` removes the item at index 1 and returns it.
- `pop()` with no argument removes and returns the last item.
- Popping from an empty list raises `IndexError`.

### F. clear() — empty the list

```python
messages = ["Hi", "Hello"]
result = messages.clear()

print(messages)
print(result)
```

Output:

```text
[]
None
```

The same list object is emptied. The method returns `None`.

### G. index() — find the first position

```python
messages = ["Hi", "Hello", "Hi"]
print(messages.index("Hello"))
print(messages.index("Hi"))
```

Output:

```text
1
0
```

It returns the first matching index. If the value is missing, it raises `ValueError`. Check membership first when the value may be absent:

```python
if "Welcome" in messages:
    print(messages.index("Welcome"))
else:
    print("Message not found")
```

### H. count() — count matching values

```python
messages = ["Hi", "Hello", "Hi", "Hi"]
print(messages.count("Hi"))
print(messages.count("Bye"))
```

Output:

```text
3
0
```

It does not change the list. It returns an integer.

### I. sort() — arrange values

```python
scores = [70, 95, 60, 85]
result = scores.sort()

print(scores)
print(result)
```

Output:

```text
[60, 70, 85, 95]
None
```

- `sort()` changes the original list.
- By default, numbers are sorted from smallest to largest.
- `sort(reverse=True)` sorts from largest to smallest.
- Values must be comparable with one another.

If you need a new sorted list while keeping the original unchanged, use the built-in `sorted(scores)` function:

```python
scores = [70, 95, 60]
new_scores = sorted(scores)

print(scores)
print(new_scores)
```

Output:

```text
[70, 95, 60]
[60, 70, 95]
```

### J. reverse() — reverse the current order

```python
messages = ["first", "second", "third"]
result = messages.reverse()

print(messages)
print(result)
```

Output:

```text
['third', 'second', 'first']
None
```

It reverses the existing order. It does not sort alphabetically.

### K. copy() — create a shallow copy

```python
original = ["Python", "SQL"]
backup = original.copy()

backup.append("Git")

print(original)
print(backup)
```

Output:

```text
['Python', 'SQL']
['Python', 'SQL', 'Git']
```

The new list is separate from the original at the outer list level. This is a **shallow copy**: if a list contains nested lists or other mutable objects, those inner objects are still shared. Deep copying is an advanced topic; do not assume `copy()` duplicates every nested object.

### Quick check — predict before running

```python
items = [3, 1, 2]
answer = items.append(4)
print(items)
print(answer)
items.sort()
print(items)
```

Expected output:

```text
[3, 1, 2, 4]
None
[1, 2, 3, 4]
```

## 15.2 String methods you must know

Strings store text and are immutable. A string method normally returns a new string; it does not edit the original string in place.

| Method / function | Purpose | Example | Result |
|---|---|---|---|
| `upper()` | Uppercase text | `"hello".upper()` | `"HELLO"` |
| `lower()` | Lowercase text | `"HELLO".lower()` | `"hello"` |
| `title()` | Capitalize each word | `"python basics".title()` | `"Python Basics"` |
| `capitalize()` | Capitalize first character | `"python".capitalize()` | `"Python"` |
| `strip()` | Remove surrounding whitespace | `" hi ".strip()` | `"hi"` |
| `replace(old, new)` | Replace matching text | `"AI bot".replace("bot", "app")` | `"AI app"` |
| `split(sep)` | Split text into a list | `"a,b".split(",")` | `["a", "b"]` |
| `startswith(x)` | Check beginning | `"Python".startswith("Py")` | `True` |
| `endswith(x)` | Check ending | `"notes.txt".endswith(".txt")` | `True` |
| `find(x)` | Find first position; -1 if absent | `"hello".find("e")` | `1` |
| `count(x)` | Count occurrences | `"banana".count("a")` | `3` |
| `len(text)` | Count characters (built-in function) | `len("AI")` | `2` |
| `" ".join(words)` | Join strings with a separator | `" ".join(["Hello", "Anu"])` | `"Hello Anu"` |

**Important:** `split()` returns a list. `join()` is called on the separator string and expects an iterable of strings. If an item is not a string, join raises `TypeError`.

## 15.3 Tuple operations

A tuple is ordered but cannot be changed after it is created.

| Operation | Example | Result / meaning |
|---|---|---|
| Read by index | `student[0]` | Reads first value |
| Count | `student.count("CSE")` | Number of matches |
| Find index | `student.index(101)` | First matching position |
| Unpack | `name, roll = ("Anu", 101)` | Assigns values to variables |
| One-item tuple | `("Python",)` | Comma makes it a tuple |

Tuple methods `count()` and `index()` do not change the tuple. Attempting `student[0] = "Ravi"` raises `TypeError`.

## 15.4 Set operations

A set stores unique hashable values and does not support numeric indexing. Its display order is not guaranteed.

| Method / operator | Purpose | Example |
|---|---|---|
| `add(x)` | Add one item | `skills.add("Git")` |
| `update(items)` | Add items from an iterable | `skills.update(["SQL", "Docker"])` |
| `discard(x)` | Remove if present; no error if absent | `skills.discard("Java")` |
| `remove(x)` | Remove; raises `KeyError` if absent | `skills.remove("SQL")` |
| `union(other)` / `|` | All unique items from both | `a | b` |
| `intersection(other)` / `&` | Items in both | `a & b` |
| `difference(other)` / `-` | Items in first but not second | `a - b` |
| `issubset(other)` | Check whether all items are in other | `a.issubset(b)` |
| `issuperset(other)` | Check whether set contains all items of other | `a.issuperset(b)` |

Example:

```python
python_students = {"Anu", "Ravi", "Meena"}
sql_students = {"Ravi", "Meena", "John"}

print(python_students & sql_students)
print(python_students - sql_students)
print(python_students | sql_students)
```

The three results represent common students, Python-only students and everyone in either group. Set order may vary, so do not rely on printed order.

## 15.5 Dictionary operations

A dictionary maps keys to values. Keys are unique and must be hashable.

| Method / operation | Purpose | Example |
|---|---|---|
| `data[key]` | Read required key | `student["name"]` |
| `get(key, default)` | Read safely with a default | `student.get("age", 0)` |
| `keys()` | View keys | `student.keys()` |
| `values()` | View values | `student.values()` |
| `items()` | View key-value pairs | `student.items()` |
| `update(other)` | Add or replace values | `student.update({"age": 20})` |
| `pop(key)` | Remove key and return its value | `student.pop("age")` |
| `setdefault(key, default)` | Return existing value or insert default | `student.setdefault("city", "Unknown")` |
| `copy()` | Make a shallow copy | `backup = student.copy()` |
| `key in data` | Check key membership | `"name" in student` |

Example:

```python
message = {"role": "user", "content": "Explain lists"}
print(message.get("role"))
print(message.get("timestamp", "not supplied"))
message["content"] = "Explain Python lists"
print(message)
```

Output:

```text
user
not supplied
{'role': 'user', 'content': 'Explain Python lists'}
```

## 15.6 Choose the right structure

| Need | Use | Why |
|---|---|---|
| Store a question or answer | String | Text data |
| Keep ordered chat messages and update them | List | Ordered and mutable |
| Store a fixed pair or record | Tuple | Ordered and immutable |
| Keep unique tags | Set | Removes duplicates |
| Store role, content and timestamp by name | Dictionary | Key-value lookup |

A real chat record can combine structures: a **list** holds the conversation, and each **dictionary** holds one message.

## 16. Fully guided mini-project — AI Conversation Data Manager

### What you will build

A terminal program that stores chat messages, adds new messages, displays conversation history, counts messages by role, and lists unique words used in the conversation.

### Step 1 — create the folder

```text
day_02_project/
└── main.py
```

### Step 2 — type this complete program

```python
def create_message(role, content):
    return {
        "role": role,
        "content": content.strip()
    }


def display_messages(conversation):
    print("\nConversation history:")

    for number, message in enumerate(conversation, start=1):
        print(number, "-", message["role"], ":", message["content"])


def count_user_messages(conversation):
    total = 0

    for message in conversation:
        if message["role"] == "user":
            total += 1

    return total


def collect_unique_words(conversation):
    words = set()

    for message in conversation:
        cleaned_text = message["content"].lower()
        for word in cleaned_text.split():
            words.add(word.strip(".,!?"))

    return words


def main():
    conversation = [
        create_message("user", "Explain Python lists."),
        create_message("assistant", "A list stores ordered items."),
        create_message("user", "Show a simple list example.")
    ]

    display_messages(conversation)

    new_text = input("\nEnter another user message: ").strip()

    if new_text:
        conversation.append(create_message("user", new_text))
    else:
        print("Empty message was not added.")

    display_messages(conversation)

    print("\nUser message count:", count_user_messages(conversation))
    print("Unique words:", sorted(collect_unique_words(conversation)))


if __name__ == "__main__":
    main()
```

### Step 3 — run it

From the `day_02_project` folder:

**Windows**
```bash
py main.py
```

**macOS / Linux**
```bash
python3 main.py
```

### Step 4 — sample run

If the user enters `What is a tuple?`, the beginning and end of the output will look like this:

```text
Conversation history:
1 - user : Explain Python lists.
2 - assistant : A list stores ordered items.
3 - user : Show a simple list example.

Enter another user message: What is a tuple?

Conversation history:
1 - user : Explain Python lists.
2 - assistant : A list stores ordered items.
3 - user : Show a simple list example.
4 - user : What is a tuple?

User message count: 3
Unique words: [...]
```

The exact unique-word order is sorted alphabetically by the `sorted()` function. The complete list depends on the messages typed.

### Step 5 — understand the program

1. `create_message(role, content)` returns a dictionary. The dictionary labels each piece of data with a key.
2. `conversation` is a list. It stores multiple message dictionaries in order.
3. `display_messages()` uses a `for` loop to visit each dictionary.
4. `enumerate(..., start=1)` supplies a display number beginning at 1. Python list indexes still begin at 0.
5. `count_user_messages()` uses a counter. It increases only when the role equals `"user"`.
6. `collect_unique_words()` uses a set so duplicate words are kept only once.
7. `lower()` normalizes uppercase/lowercase differences.
8. `split()` separates the text into words.
9. `strip(".,!?")` removes those punctuation characters from the ends of each word.
10. `sorted()` returns a sorted list for display; it does not change the set.
11. `if __name__ == "__main__":` runs `main()` when this file is executed directly. You will learn this pattern more deeply later.

### Step 6 — test the project

| Test | Input | Expected behaviour |
|---|---|---|
| Normal message | `Can you explain dictionaries?` | Message is added |
| Empty message | Press Enter without text | Message is not added |
| Uppercase | `PYTHON IS USEFUL` | Unique-word collection uses lowercase |
| Repeated word | `Python Python Python` | Word appears once in unique-word set |
| No extra input | Press Enter | Original three messages remain |

### Step 7 — common errors

| Error | Cause | Fix |
|---|---|---|
| `KeyError: 'role'` | A message dictionary has no role key | Create every message using `create_message()` or check the key |
| `AttributeError` on `strip` | Content is not a string | Check input type before calling string methods |
| `IndentationError` | Code block indentation is inconsistent | Use four spaces per block level |
| File not found | Terminal is not in the project folder | Change directory or open the correct folder |
| Unexpected word count | Punctuation or capitalization differs | Inspect the normalized text and splitting logic |

### Step 8 — extend the project independently

1. Add an assistant message using `create_message()`.
2. Add a function that counts assistant messages.
3. Add a function that returns the latest message using `pop()` only on a copy, so the original history stays unchanged.
4. Add a dictionary for the learner profile with name and course.
5. Explain why a list of dictionaries is suitable for conversation history.

### Project completion criteria

- [ ] I can explain why the conversation is a list.
- [ ] I can explain why each message is a dictionary.
- [ ] I can explain why unique words are stored in a set.
- [ ] I can explain what every function returns.
- [ ] I can run all five test cases.
- [ ] I can add one feature without copying the solution.

## 17. Day 2 independent challenge

Create a second program from a blank file. It must:
1. Ask for three skills from the user.
2. Store them in a list.
3. Display the first and last skill.
4. Remove duplicates using a set.
5. Store the learner name and unique skills in a dictionary.
6. Display a clean report.

**Hints:** use `input()`, `split(",")`, `strip()`, `set()` and a dictionary. Do not look at the project solution until you have tried for at least 15 minutes.

**Sample solution**

```python
name = input("Enter learner name: ").strip()
skills_text = input("Enter three skills separated by commas: ")

skills = [skill.strip() for skill in skills_text.split(",") if skill.strip()]
unique_skills = sorted(set(skills))

profile = {
    "name": name,
    "skills": unique_skills
}

print("\nLearner:", profile["name"])
print("First entered skill:", skills[0] if skills else "Not supplied")
print("Last entered skill:", skills[-1] if skills else "Not supplied")
print("Unique skills:", profile["skills"])
```

This solution uses a list comprehension. If you have not studied comprehensions yet, replace that line with a normal `for` loop. Day 3 will explain comprehensions in detail.

## 18. Day 2 final readiness gate

Move to Day 3 only if you can answer yes to these:

- [ ] Can I explain the difference between string, list, tuple, set and dictionary?
- [ ] Can I explain all eleven list methods and predict their return values?
- [ ] Can I distinguish `append()` from `extend()` with code?
- [ ] Can I explain which list methods mutate the list?
- [ ] Can I explain why `append()`, `sort()` and `reverse()` return `None`?
- [ ] Can I build a list of dictionaries to represent chat history?
- [ ] Can I run and modify the Conversation Data Manager?
- [ ] Can I identify and fix one missing-key or invalid-input problem?

If any answer is no, repeat that section and its code exercise. Understanding these structures is essential before learning functions, APIs and LLM conversation messages.
