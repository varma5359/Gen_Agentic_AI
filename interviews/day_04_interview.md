# Day 04 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** Object-Oriented Programming: Classes, Objects, Inheritance, Encapsulation and Composition  
**Mini-project:** AI Application Component Manager  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain classes and objects.

**Beginner answer:** A class is a blueprint for a kind of object. An object is one instance created from that blueprint.

**Example code**

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

**How it works:** class defines a new type. Student() creates an instance. is checks whether two names refer to the same object.

**Important methods or syntax:** Class naming, instance creation, attributes and object identity.

**Common mistake:** A class definition does not create a particular student record. Each call creates a new instance.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain __init__ and self.

**Beginner answer:** __init__ initializes a newly created object. self refers to the current instance.

**Example code**

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

**How it works:** Python supplies the new instance as self when an instance method is called. The assignments create instance attributes.

**Important methods or syntax:** Default attribute values, validation in initialization and readable repr methods.

**Common mistake:** Forgetting self or supplying too few constructor arguments causes errors. __init__ should initialize, not perform long network calls.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain instance methods and attributes.

**Beginner answer:** A method is a function defined inside a class. An instance method can read or update the current object's attributes.

**Example code**

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

**How it works:** introduce() uses self.name from the object. The instance is passed automatically when called through the object.

**Important methods or syntax:** Methods such as add_skill(), rename() and display_details(); class methods and static methods as later extensions.

**Common mistake:** Calling an instance method without an instance can cause a missing self argument error.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain encapsulation and properties.

**Beginner answer:** Encapsulation groups data and behavior. A public method can validate a change before updating internal state.

**Example code**

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

**How it works:** _balance is marked internal by convention. deposit() checks that the amount is positive before changing it.

**Important methods or syntax:** Properties with @property and setters; validation; data hiding conventions; immutable public interfaces.

**Common mistake:** A leading underscore is a convention, not strong security. Never rely on it to protect passwords or API keys.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain inheritance and overriding.

**Beginner answer:** Inheritance lets a child class reuse behavior from a parent class. A child can add or specialize behavior.

**Example code**

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

**How it works:** SearchTool inherits run() and adds search(). The child is a specialized kind of Tool.

**Important methods or syntax:** Method overriding, super(), abstract base classes and substitutability as intermediate topics.

**Common mistake:** Do not create deep inheritance trees just to share a few lines. Prefer clear relationships.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain composition and dependency injection.

**Beginner answer:** Composition means one object contains or uses another object. It models a has-a relationship.

**Example code**

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

**How it works:** Assistant has a Prompt object. Passing the prompt in is a simple form of dependency injection.

**Important methods or syntax:** Pass database clients, repositories or tools into a service instead of creating all dependencies inside it.

**Common mistake:** Tightly coupling a class to a concrete external service makes testing and replacement harder.

**Follow-up:** Where would you use this in a Python AI application?


### Q7. Explain choosing class design.

**Beginner answer:** Use a class when data and related behavior belong together. Use a simple function when no object state is needed.

**Example code**

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

**How it works:** The object stores a role and content. preview() returns the first twenty characters.

**Important methods or syntax:** Use dataclasses for simple data containers; keep business logic in suitable services; test behavior independently.

**Common mistake:** Do not turn every small function into a class. Avoid classes with unclear responsibilities.

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

### Exercise 1 — Classes and objects

**Task:** Create Book and Course classes and make two objects of each.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — __init__ and self

**Task:** Create two Student objects and show that their names are independent.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Instance methods and attributes

**Task:** Create a Conversation class with add_message() and message_count().

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Encapsulation and properties

**Task:** Add a withdraw() method that rejects a withdrawal greater than the balance.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Inheritance and overriding

**Task:** Create Notification and EmailNotification classes.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Composition and dependency injection

**Task:** Create an Assistant that receives a MessageStore component.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 7 — Choosing class design

**Task:** Design Message, Conversation and Prompt components for a tiny chatbot.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — AI Application Component Manager

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


---

## 6. OOP interview questions with clear answers

### Q8. What is the difference between a class and an object?

A class defines a type and describes its possible data and behavior. An object is one instance created from that class. One class can create many separate objects.

### Q9. What are __init__ and self?

`__init__` initializes the new object. `self` refers to the current instance and is used to read or update its attributes. Python supplies the instance automatically when an instance method is called through an object.

### Q10. What is the difference between an attribute and a method?

An attribute stores data on an object. A method is a function defined in a class that performs an operation, often using that object's data.

### Q11. What is the difference between instance and class attributes?

An instance attribute belongs to one object and can have a different value on each object. A class attribute is defined on the class and is shared unless an instance overrides it with its own attribute.

### Q12. What is encapsulation?

Encapsulation groups data and related operations together. A class can validate a value through a method or property before updating its internal state. In Python, a leading underscore is a convention for internal use, not strong security.

### Q13. What is a property?

A property allows a method to be accessed with attribute-like syntax. A setter can validate values when someone assigns to the attribute.

### Q14. What is inheritance?

Inheritance lets a child class reuse and specialize behavior from a parent class. Use it when the child is genuinely a more specific kind of the parent.

### Q15. What is method overriding?

Overriding occurs when a child class defines a method with the same name as an inherited method, providing specialized behavior.

### Q16. What does super() do?

`super()` provides access to the next implementation in the method resolution order. It is commonly used by a child initializer to reuse the parent's initialization.

### Q17. What is composition?

Composition means one object contains or uses another object. For example, an Assistant can have a Prompt and a MessageStore.

### Q18. What is dependency injection?

Dependency injection means an object receives the components it needs from outside. This makes it easier to replace a real database with a test version or change a component without rewriting the class.

### Q19. When should you use a function instead of a class?

Use a function for a focused operation that does not need to retain object state. Use a class when related data and behavior belong together. Do not create classes just to make every piece of code look object-oriented.

## 7. Code-output interview drills

### Drill 1 — separate objects

```python
class Student:
    def __init__(self, name):
        self.name = name

a = Student("Anu")
b = Student("Ravi")
print(a.name)
print(b.name)
```

Answer:

```text
Anu
Ravi
```

Each object stores its own name.

### Drill 2 — instance method

```python
class Counter:
    def __init__(self):
        self.value = 0

    def increase(self):
        self.value += 1

counter = Counter()
counter.increase()
counter.increase()
print(counter.value)
```

Answer: `2`.

### Drill 3 — overriding

```python
class Tool:
    def run(self):
        return "Base"

class SearchTool(Tool):
    def run(self):
        return "Search"

print(SearchTool().run())
```

Answer: `Search`. The child implementation overrides the inherited method.

### Drill 4 — class attribute

```python
class Course:
    platform = "TechPhile"

one = Course()
two = Course()
print(one.platform, two.platform)
```

Answer: `TechPhile TechPhile`.

### Drill 5 — composition

```python
class Engine:
    def start(self):
        return "Started"

class Car:
    def __init__(self, engine):
        self.engine = engine

car = Car(Engine())
print(car.engine.start())
```

Answer: `Started`. Car has an Engine object.

## 8. Practical coding interview challenge

**Task:** Create a `CourseProgress` class that stores a learner's name and completed lesson count. Add a method that completes one lesson and another method that returns a readable progress message.

**One possible solution:**

```python
class CourseProgress:
    def __init__(self, learner_name):
        self.learner_name = learner_name
        self.completed_lessons = 0

    def complete_lesson(self):
        self.completed_lessons += 1

    def report(self):
        return f"{self.learner_name}: {self.completed_lessons} lessons completed"


learner = CourseProgress("Anu")
learner.complete_lesson()
learner.complete_lesson()
print(learner.report())
```

Output:

```text
Anu: 2 lessons completed
```

Explain:
- The class defines the learner progress object.
- `__init__` initializes two instance attributes.
- Each call to `complete_lesson()` increases the count.
- `report()` returns a string.
- The caller prints the returned string.

## 9. Project discussion — AI Application Component Manager

Be ready to explain:

1. **What does the project do?** It prepares a prompt, stores user messages and connects reusable components.
2. **Does it call an LLM?** No. It is a plain-Python OOP exercise. It does not make a network request or require an API key.
3. **Why is Prompt a class?** It stores an instruction and provides a method to build a prepared prompt.
4. **Why is MessageStore a class?** It owns the message list and exposes methods to add and retrieve messages.
5. **Why does Assistant receive Prompt and MessageStore?** This is composition and dependency injection. The components can be replaced independently.
6. **Why does SafeTextAssistant inherit from TextAssistant?** It is a specialized assistant that adds a blank-input check.
7. **Why call super()?** To reuse the parent's receive_question() implementation after validation.
8. **How is invalid input handled?** The program raises a ValueError with a clear message.
9. **What would you improve?** Add automated tests, persistent storage, role validation and an actual model client in a later lesson.
10. **What is one limitation?** The prompt is prepared but no AI response is generated.

## 10. Final interview readiness checklist

- [ ] I can explain class vs object.
- [ ] I can explain `__init__` and `self`.
- [ ] I can identify attributes and methods.
- [ ] I can explain class vs instance attributes.
- [ ] I can explain encapsulation and properties.
- [ ] I can explain inheritance and overriding.
- [ ] I can explain `super()`.
- [ ] I can explain composition and dependency injection.
- [ ] I can complete the CourseProgress coding challenge.
- [ ] I can explain the AI Application Component Manager and its limitations.
