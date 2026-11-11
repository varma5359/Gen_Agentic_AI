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


---

# 14. Learn classes and objects by running each example

Create a file called `practice_oop.py`. Type and run each section separately.

## 14.1 Class vs object

A class describes what a kind of object can store and do. An object is one actual instance of that class.

```python
class Student:
    pass

student_one = Student()
student_two = Student()

print(type(student_one).__name__)
print(student_one is student_two)
```

Output:

```text
Student
False
```

Explanation:
- `class Student:` defines a new class.
- `pass` means "there is no code here yet"; it is used as a temporary empty body.
- `Student()` creates an object.
- `type(student_one)` tells us the object's class.
- `. __name__` is the class name attribute (without the space after the dot; write `.__name__`).
- `is` checks whether two names refer to the exact same object. These are two different objects, so the result is False.

A class is not itself a student record. Each object is a separate instance.

## 14.2 __init__ and self

`__init__` is an initializer method. Python calls it after creating a new instance. `self` is the conventional name for the current instance.

```python
class Student:
    def __init__(self, name, course):
        self.name = name
        self.course = course

student_one = Student("Anu", "Python")
student_two = Student("Ravi", "GenAI")

print(student_one.name)
print(student_two.name)
print(student_one.course)
```

Output:

```text
Anu
Ravi
Python
```

Understand `self.name = name`:
- The right-side `name` is the argument received by the initializer.
- The left-side `self.name` is an attribute stored on this particular object.
- `student_one.name` reads the attribute from student_one.
- `student_two.name` reads the separate attribute from student_two.

Do not write `self = name`; that would only reassign the local parameter name and would not create the intended attribute.

## 14.3 Attributes and instance methods

An attribute stores information. A method is a function defined inside a class.

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.completed_days = 0

    def complete_day(self):
        self.completed_days += 1

    def show_progress(self):
        return f"{self.name} completed {self.completed_days} days"

student = Student("Meena")
student.complete_day()
student.complete_day()
print(student.show_progress())
```

Output:

```text
Meena completed 2 days
```

- `complete_day()` changes this student's progress.
- `+= 1` means add one to the current value and store the result.
- `show_progress()` returns a string; it does not print by itself.
- `student.show_progress()` calls the method on this object.

When you call `student.complete_day()`, Python passes the student object as `self) automatically. You do not pass self yourself.

## 14.4 Instance attribute vs class attribute

```python
class Course:
    platform = "TechPhile"

    def __init__(self, title):
        self.title = title

python_course = Course("Python")
genai_course = Course("GenAI")

print(python_course.title)
print(genai_course.title)
print(python_course.platform)
print(genai_course.platform)
```

Output:

```text
Python
GenAI
TechPhile
TechPhile
```

- `title` is an instance attribute; each course has its own value.
- `platform` is a class attribute shared through the class.
- Be careful with mutable class attributes such as lists: all instances may share the same list. Put per-object lists inside `__init__`.

## 14.5 Encapsulation and validation

Encapsulation means grouping the data and the operations that manage it. Python uses naming conventions; a leading underscore means "internal use", not secure privacy.

```python
class Wallet:
    def __init__(self, opening_balance=0):
        if opening_balance < 0:
            raise ValueError("Opening balance cannot be negative")
        self._balance = opening_balance

    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("Deposit must be greater than zero")
        self._balance += amount

    def get_balance(self):
        return self._balance


wallet = Wallet(100)
wallet.deposit(50)
print(wallet.get_balance())
```

Output:

```text
150
```

- `raise ValueError(...)` deliberately reports invalid input.
- `self._balance` is an internal attribute by convention.
- `deposit()` checks the amount before changing the balance.
- The public method controls how the value changes.

### Use a property

A property lets code access a method using attribute-like syntax.

```python
class Student:
    def __init__(self, name):
        self._name = name

    @property
    def name(self):
        return self._name

    @name.setter
    def name(self, new_name):
        cleaned = new_name.strip()
        if not cleaned:
            raise ValueError("Name cannot be empty")
        self._name = cleaned


student = Student("Anu")
student.name = "  Ravi  "
print(student.name)
```

Output:

```text
Ravi
```

- `@property` makes `name()` available as `student.name`.
- `@name.setter` runs when assigning `student.name = ...`.
- The setter strips outside spaces and rejects an empty value.
- A leading underscore is not a security boundary. Never store passwords or API keys in an object and assume the underscore protects them.

## 14.6 Inheritance and method overriding

Inheritance models an "is-a" relationship. A child class can reuse and specialize a parent class.

```python
class Notification:
    def send(self, message):
        return f"Notification: {message}"


class EmailNotification(Notification):
    def send(self, message):
        return f"Email sent: {message}"


class ConsoleNotification(Notification):
    pass


email = EmailNotification()
console = ConsoleNotification()

print(email.send("Welcome"))
print(console.send("Course starts today"))
```

Output:

```text
Email sent: Welcome
Notification: Course starts today
```

- Both child classes inherit from `Notification`.
- `EmailNotification` overrides `send()` with its own behavior.
- `ConsoleNotification` does not override it, so it uses the parent's method.

### What does super() do?

`super()` gives access to the next class in the method resolution order, commonly used to call a parent implementation.

```python
class Tool:
    def __init__(self, name):
        self.name = name


class SearchTool(Tool):
    def __init__(self, name, max_results):
        super().__init__(name)
        self.max_results = max_results


tool = SearchTool("Course Search", 5)
print(tool.name)
print(tool.max_results)
```

Output:

```text
Course Search
5
```

The child initializer reuses the parent's initialization for `name`, then stores its own `max_results`.

## 14.7 Composition and dependency injection

Composition means an object uses another object as a component. Dependency injection means the component is supplied from outside instead of being secretly created inside the class.

```python
class MessageStore:
    def __init__(self):
        self.messages = []

    def add(self, message):
        self.messages.append(message)

    def get_all(self):
        return self.messages


class Assistant:
    def __init__(self, store):
        self.store = store

    def receive(self, message):
        self.store.add(message)

    def history(self):
        return self.store.get_all()


store = MessageStore()
assistant = Assistant(store)
assistant.receive("Explain classes")
assistant.receive("Show a project")
print(assistant.history())
```

Output:

```text
['Explain classes', 'Show a project']
```

The `Assistant` has a `MessageStore`. The store is passed into the assistant through its initializer. Later, we can replace it with a different store (for example, one that saves to a database) without rewriting the assistant's main behavior.

## 14.8 When should you use a class?

| Situation | Good starting choice | Reason |
|---|---|---|
| Convert Celsius to Fahrenheit once | Function | No stored object state needed |
| Store one student's name and progress | Class | Related data and behavior belong together |
| Keep a sequence of messages | List | Ordered collection |
| Represent one message with role and content | Dictionary or small class | Named fields |
| Use a replaceable message store in an assistant | Composition | Components can be substituted |
| Share a common interface for email and SMS notifications | Inheritance or a protocol-like design | Same operation, different implementation |

Do not turn every function into a class. Choose the simplest design that makes the code easier to understand.

---

# 15. Complete guided mini-project — AI Application Component Manager

## Project goal

Build a small plain-Python program that represents components in a future AI application:
- A `Prompt` stores the instruction sent to an AI system.
- A `MessageStore` stores conversation messages.
- A `TextAssistant` uses both components.
- A `SafeTextAssistant` specializes the assistant with input validation.

This project does **not** call an AI model or an external API. It teaches object-oriented design before we connect real AI services in later phases.

## Step 1 — create the folder

```text
day_04_project/
└── main.py
```

## Step 2 — type this complete code

```python
class Prompt:
    def __init__(self, instruction):
        cleaned = instruction.strip()
        if not cleaned:
            raise ValueError("Prompt instruction cannot be empty")
        self.instruction = cleaned

    def build(self, question):
        return f"{self.instruction}\nUser question: {question.strip()}"


class MessageStore:
    def __init__(self):
        self._messages = []

    def add(self, role, content):
        message = {
            "role": role,
            "content": content
        }
        self._messages.append(message)

    def get_all(self):
        return self._messages.copy()

    def count(self):
        return len(self._messages)


class TextAssistant:
    def __init__(self, prompt, store):
        self.prompt = prompt
        self.store = store

    def receive_question(self, question):
        prepared_prompt = self.prompt.build(question)
        self.store.add("user", question)
        return prepared_prompt

    def history(self):
        return self.store.get_all()


class SafeTextAssistant(TextAssistant):
    def receive_question(self, question):
        if not question.strip():
            raise ValueError("Question cannot be empty")
        return super().receive_question(question)


def main():
    prompt = Prompt("You are a patient Python tutor. Explain in simple steps.")
    store = MessageStore()
    assistant = SafeTextAssistant(prompt, store)

    prepared = assistant.receive_question("What is a Python class?")

    print("--- PROMPT PREPARED FOR A FUTURE AI MODEL ---")
    print(prepared)

    print("\n--- CONVERSATION HISTORY ---")
    for message in assistant.history():
        print(message["role"], ":", message["content"])

    print("\nTotal stored messages:", store.count())


if __name__ == "__main__":
    main()
```

## Step 3 — run the project

Open a terminal inside the `day_04_project` folder.

Windows:

```bash
py main.py
```

macOS / Linux:

```bash
python3 main.py
```

No package installation, API key, database or internet connection is needed.

## Step 4 — expected output

```text
--- PROMPT PREPARED FOR A FUTURE AI MODEL ---
You are a patient Python tutor. Explain in simple steps.
User question: What is a Python class?

--- CONVERSATION HISTORY ---
user : What is a Python class?

Total stored messages: 1
```

## Step 5 — understand every component

| Component | Responsibility | OOP idea |
|---|---|---|
| `Prompt` | Stores and builds an instruction | Class, attributes, methods, validation |
| `MessageStore` | Keeps message dictionaries | Encapsulation, list attribute |
| `TextAssistant` | Coordinates prompt and store | Composition, dependency injection |
| `SafeTextAssistant` | Rejects blank questions | Inheritance, overriding, super() |
| `main()` | Creates and connects the objects | Application entry point |

### Follow one question through the program

```text
User types question
       |
       v
SafeTextAssistant.receive_question()
       |
       +---- Is the question blank?
       |          |
       |          +---- Yes -> raise ValueError
       |          |
       |          +---- No
       v
TextAssistant.receive_question()
       |
       +---- Prompt.build(question)
       |
       +---- MessageStore.add("user", question)
       |
       v
Return prepared prompt
       |
       v
Display prompt and stored history
```

### Important code details

- `instruction.strip()` removes whitespace at the start and end of the instruction.
- `if not cleaned` checks whether the resulting string is empty.
- `raise ValueError(...)` stops the operation with a clear input error.
- `self.instruction` stores data on the Prompt object.
- `self._messages = []` creates a separate list for each MessageStore object.
- `append()` adds one message dictionary to that list.
- `copy()` returns a shallow copy of the message list so a caller cannot add/remove entries in the store's outer list by modifying the returned list. The dictionaries inside are still shared; this is a shallow copy.
- `super().receive_question(question)` calls the inherited implementation after the child class validates the question.
- The assistant receives prompt and store objects from outside. This is dependency injection.

## Step 6 — test the project

Try each test by changing the question in main().

| Test | Input | Expected behaviour |
|---|---|---|
| Normal question | `What is a class?` | Prompt prepared and message stored |
| Empty question | `""` | ValueError with clear message |
| Spaces only | `"   "` | ValueError with clear message |
| Different prompt | Change Prompt instruction | Prepared prompt uses new instruction |
| Two questions | Call receive_question twice | Store count becomes 2 |

To see the empty-question error, temporarily replace the call with:

```python
prepared = assistant.receive_question("   ")
```

Expected error:

```text
ValueError: Question cannot be empty
```

This is intentional input validation, not a Python installation problem.

## Step 7 — common mistakes

| Error | Cause | Fix |
|---|---|---|
| `TypeError: ... missing 1 required positional argument` | An initializer or method argument was not supplied | Check the constructor call and method parameters |
| `AttributeError` | The object does not have the attribute/method being used | Check spelling and whether the object is the expected class |
| `NameError` | Class name is misspelled or referenced before definition | Check spelling and definition order |
| `IndentationError` | Method body is not nested correctly inside the class | Use consistent four-space indentation |
| Prompt is blank | Empty instruction was supplied | Give a non-empty instruction |
| Store count does not increase | The assistant did not call store.add() | Trace receive_question() step by step |

## Step 8 — independent project extensions

Complete in order:

1. Add an `assistant` role message to the store after preparing the prompt. Explain that it is a placeholder, not a real model response.
2. Add a `clear()` method to MessageStore.
3. Add a `last_message()` method that returns the latest message or None if the store is empty.
4. Create a second MessageStore and a second assistant. Prove that their histories are independent.
5. Create another child class called `ShortQuestionAssistant` that rejects questions shorter than five characters.
6. Explain why composition is used for Prompt and MessageStore, while inheritance is used for SafeTextAssistant.

## Step 9 — project submission checklist

- [ ] I created and ran main.py.
- [ ] I can explain class vs object.
- [ ] I can explain `self` and `__init__`.
- [ ] I can identify instance attributes and methods.
- [ ] I can explain why the message list is internal.
- [ ] I can explain the child class and `super()`.
- [ ] I can explain how the assistant receives its components.
- [ ] I tested blank and normal questions.
- [ ] I understand that this project prepares a prompt but does not call an LLM.
- [ ] I can add one feature without copying a finished answer.

---

# 16. Day 4 knowledge check — answers included

Try to answer each question before reading the answer.

1. **What is a class?** A definition describing the attributes and behavior that its objects can have.
2. **What is an object?** A particular instance created from a class.
3. **What does `__init__` do?** It initializes a newly created object.
4. **What is `self`?** The conventional parameter referring to the current instance.
5. **What is an instance attribute?** Data stored on one particular object.
6. **What is an instance method?** A function defined in a class that works with an instance.
7. **What is encapsulation?** Keeping related data and behavior together and controlling changes through methods or properties.
8. **Does an underscore make an attribute private and secure?** No. It is a convention that signals internal use.
9. **What is inheritance?** A child class reuses or specializes behavior from a parent.
10. **What is overriding?** A child class supplies its own implementation of an inherited method.
11. **What does `super()` do?** It provides access to the next implementation in the method resolution order, often the parent implementation.
12. **What is composition?** One object contains or uses another object.
13. **What is dependency injection?** Supplying a dependency from outside an object rather than creating it internally.
14. **Should every function become a class?** No. Use a function when there is no useful object state or behavior to group.

## Day 4 readiness gate

Do not move to Day 5 until you can:
- Create a class and two independent objects.
- Explain `__init__`, `self`, attributes and instance methods.
- Explain instance vs class attributes.
- Add a property setter that validates a value.
- Explain inheritance, overriding and `super()`.
- Explain composition and dependency injection with the project.
- Run the AI Application Component Manager.
- Test invalid input and explain the resulting error.
- Explain why the project does not yet call an AI model.
