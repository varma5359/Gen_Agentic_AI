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
