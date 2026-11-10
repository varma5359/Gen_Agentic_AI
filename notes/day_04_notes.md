# Day 04 — Object-Oriented Programming: Classes, Objects, Inheritance, Encapsulation and Composition

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Approved mini-project:** AI Application Component Manager  
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

1. Explain classes and objects using a simple example.
2. Explain __init__ and self using a simple example.
3. Explain instance methods and attributes using a simple example.
4. Explain encapsulation and properties using a simple example.
5. Explain inheritance and overriding using a simple example.
6. Explain composition and dependency injection using a simple example.
7. Explain choosing class design using a simple example.
8. Apply classes and objects in the AI Application Component Manager.
9. Apply __init__ and self in the AI Application Component Manager.
10. Apply instance methods and attributes in the AI Application Component Manager.
11. Apply encapsulation and properties in the AI Application Component Manager.
12. Apply inheritance and overriding in the AI Application Component Manager.
13. Apply composition and dependency injection in the AI Application Component Manager.
14. Apply choosing class design in the AI Application Component Manager.

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

## 3. Classes and objects

### Beginner explanation

A class is a blueprint for a kind of object. An object is one instance created from that blueprint.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
class Student:
    pass
student_one = Student()
student_two = Student()
print(type(student_one).__name__)
print(student_one is student_two)
```

**Expected output**

```text
Student
False
```

### Walkthrough

class defines a new type. Student() creates an instance. is checks whether two names refer to the same object.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Class naming, instance creation, attributes and object identity.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A class definition does not create a particular student record. Each call creates a new instance.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create Book and Course classes and make two objects of each.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define classes and objects in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 4. __init__ and self

### Beginner explanation

__init__ initializes a newly created object. self refers to the current instance.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
class Student:
    def __init__(self, name, roll_no):
        self.name = name
        self.roll_no = roll_no
student = Student("Anu", 101)
print(student.name, student.roll_no)
```

**Expected output**

```text
Anu 101
```

### Walkthrough

Python supplies the new instance as self when an instance method is called. The assignments create instance attributes.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Default attribute values, validation in initialization and readable repr methods.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Forgetting self or supplying too few constructor arguments causes errors. __init__ should initialize, not perform long network calls.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create two Student objects and show that their names are independent.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define __init__ and self in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 5. Instance methods and attributes

### Beginner explanation

A method is a function defined inside a class. An instance method can read or update the current object's attributes.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
class Student:
    def __init__(self, name):
        self.name = name
    def introduce(self):
        return f"I am {self.name}"
print(Student("Anu").introduce())
```

**Expected output**

```text
I am Anu
```

### Walkthrough

introduce() uses self.name from the object. The instance is passed automatically when called through the object.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Methods such as add_skill(), rename() and display_details(); class methods and static methods as later extensions.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Calling an instance method without an instance can cause a missing self argument error.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create a Conversation class with add_message() and message_count().

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define instance methods and attributes in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 6. Encapsulation and properties

### Beginner explanation

Encapsulation groups data and behavior. A public method can validate a change before updating internal state.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
class Wallet:
    def __init__(self, balance=0):
        self._balance = balance
    def deposit(self, amount):
        if amount > 0:
            self._balance += amount
    def get_balance(self):
        return self._balance
wallet = Wallet(100)
wallet.deposit(50)
print(wallet.get_balance())
```

**Expected output**

```text
150
```

### Walkthrough

_balance is marked internal by convention. deposit() checks that the amount is positive before changing it.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Properties with @property and setters; validation; data hiding conventions; immutable public interfaces.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

A leading underscore is a convention, not strong security. Never rely on it to protect passwords or API keys.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Add a withdraw() method that rejects a withdrawal greater than the balance.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define encapsulation and properties in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 7. Inheritance and overriding

### Beginner explanation

Inheritance lets a child class reuse behavior from a parent class. A child can add or specialize behavior.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
class Tool:
    def run(self):
        print("Running tool")
class SearchTool(Tool):
    def search(self):
        print("Searching")
item = SearchTool()
item.run()
item.search()
```

**Expected output**

```text
Running tool
Searching
```

### Walkthrough

SearchTool inherits run() and adds search(). The child is a specialized kind of Tool.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Method overriding, super(), abstract base classes and substitutability as intermediate topics.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not create deep inheritance trees just to share a few lines. Prefer clear relationships.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create Notification and EmailNotification classes.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define inheritance and overriding in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 8. Composition and dependency injection

### Beginner explanation

Composition means one object contains or uses another object. It models a has-a relationship.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
class Prompt:
    def __init__(self, text):
        self.text = text
class Assistant:
    def __init__(self, prompt):
        self.prompt = prompt
helper = Assistant(Prompt("Explain simply"))
print(helper.prompt.text)
```

**Expected output**

```text
Explain simply
```

### Walkthrough

Assistant has a Prompt object. Passing the prompt in is a simple form of dependency injection.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Pass database clients, repositories or tools into a service instead of creating all dependencies inside it.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Tightly coupling a class to a concrete external service makes testing and replacement harder.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Create an Assistant that receives a MessageStore component.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define composition and dependency injection in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---

## 9. Choosing class design

### Beginner explanation

Use a class when data and related behavior belong together. Use a simple function when no object state is needed.

**Remember:** first understand the purpose. Syntax becomes easier after you know what problem the feature solves.

### Example 1 — start here

```python
class Message:
    def __init__(self, role, content):
        self.role = role
        self.content = content
    def preview(self):
        return self.content[:20]
msg = Message("user", "Please explain Python methods")
print(msg.role)
print(msg.preview())
```

**Expected output**

```text
user
Please explain Pyth
```

### Walkthrough

The object stores a role and content. preview() returns the first twenty characters.

Read each line aloud. Identify the variable, function, method, operator or statement responsible for the result. Then change one value and predict the new output before running the program again.

### Important methods and syntax

Use dataclasses for simple data containers; keep business logic in suitable services; test behavior independently.

For each method, remember this pattern: object, dot, method name, parentheses and any required arguments. A function may instead be called directly by its name. Read the documentation when you are unsure about arguments or return values.

### Common mistakes

Do not turn every small function into a class. Avoid classes with unclear responsibilities.

When you see an error, read the exception type and the line number. Check the actual value and type. Fix one problem at a time instead of rewriting the whole program.

### Practice task

Design Message, Conversation and Prompt components for a tiny chatbot.

1. Write the smallest working version.
2. Run it with the sample value.
3. Change the input.
4. Try an empty or unexpected input.
5. Explain why the output changed.

### Interview check

1. Define choosing class design in simple language.
2. Explain how the example works.
3. Name one important method or syntax feature.
4. Explain one common mistake.
5. Give one real application use case.

### Beginner-to-intermediate bridge

After the beginner example works, improve it by adding meaningful names, a small function, input validation and a test. Do not add a framework before you understand the Python behavior.

---


# 10. Guided mini-project — AI Application Component Manager

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
day_04_project/
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

1. What is classes and objects?
1.1 Why would a Python developer use it?
1.2 What mistake should a beginner avoid?

2. What is __init__ and self?
2.1 Why would a Python developer use it?
2.2 What mistake should a beginner avoid?

3. What is instance methods and attributes?
3.1 Why would a Python developer use it?
3.2 What mistake should a beginner avoid?

4. What is encapsulation and properties?
4.1 Why would a Python developer use it?
4.2 What mistake should a beginner avoid?

5. What is inheritance and overriding?
5.1 Why would a Python developer use it?
5.2 What mistake should a beginner avoid?

6. What is composition and dependency injection?
6.1 Why would a Python developer use it?
6.2 What mistake should a beginner avoid?

7. What is choosing class design?
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

1. Explain classes and objects to a beginner.
1.1 Give a practical example.
1.2 What is one limitation or common error?

2. Explain __init__ and self to a beginner.
2.1 Give a practical example.
2.2 What is one limitation or common error?

3. Explain instance methods and attributes to a beginner.
3.1 Give a practical example.
3.2 What is one limitation or common error?

4. Explain encapsulation and properties to a beginner.
4.1 Give a practical example.
4.2 What is one limitation or common error?

5. Explain inheritance and overriding to a beginner.
5.1 Give a practical example.
5.2 What is one limitation or common error?

6. Explain composition and dependency injection to a beginner.
6.1 Give a practical example.
6.2 What is one limitation or common error?

7. Explain choosing class design to a beginner.
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

**Day 4 completion:** mark complete only when you can explain the concepts, run the examples and demonstrate your mini-project.

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

## Guided classroom lab 4: Classes and objects

### Step 1 — Say the idea in everyday language
Today's idea is "Classes and objects". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Classes and objects" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Classes and objects" and explain why the output is correct.

---

## Guided classroom lab 5: __init__ and self

### Step 1 — Say the idea in everyday language
Today's idea is "__init__ and self". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "__init__ and self" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "__init__ and self" and explain why the output is correct.

---

## Guided classroom lab 6: Instance methods and attributes

### Step 1 — Say the idea in everyday language
Today's idea is "Instance methods and attributes". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Instance methods and attributes" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Instance methods and attributes" and explain why the output is correct.

---

## Guided classroom lab 7: Encapsulation and properties

### Step 1 — Say the idea in everyday language
Today's idea is "Encapsulation and properties". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Encapsulation and properties" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Encapsulation and properties" and explain why the output is correct.

---

## Guided classroom lab 8: Inheritance and overriding

### Step 1 — Say the idea in everyday language
Today's idea is "Inheritance and overriding". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Inheritance and overriding" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Inheritance and overriding" and explain why the output is correct.

---

## Guided classroom lab 9: Composition and dependency injection

### Step 1 — Say the idea in everyday language
Today's idea is "Composition and dependency injection". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Composition and dependency injection" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Composition and dependency injection" and explain why the output is correct.

---

## Guided classroom lab 10: Choosing class design

### Step 1 — Say the idea in everyday language
Today's idea is "Choosing class design". Before typing code, explain what problem this feature solves. Use an example from a college, student portal, chat application or simple business process.

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
Build a tiny program that demonstrates "Choosing class design" without using a framework.
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

**Mastery evidence:** the student can independently demonstrate "Choosing class design" and explain why the output is correct.

---
