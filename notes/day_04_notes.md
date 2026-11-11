# Day 4 — Object-oriented programming: classes, objects, inheritance, encapsulation and composition.

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours  
**Level:** Beginner to Intermediate

> **Self-learning instruction:** Read one section at a time. Type the code yourself, run it and compare the result. These notes are designed to teach without a trainer or video.

## 1. Understand the topic

A class is a blueprint; an object is an instance. __init__ initializes an object. self refers to the current instance. Attributes store state; methods define behaviour. Encapsulation groups data and controlled operations. Inheritance models an is-a relationship. Composition models a has-a relationship and is often better for replaceable components.

## 2. Why this matters in an AI application

A GenAI application is still software. It needs input handling, business logic, APIs, data, validation, security, tests and deployment. Today's concepts are building blocks for those responsibilities. A small example demonstrates one concept; it is not automatically production-ready.

## 3. Guided coding walkthrough

### Step 1 — Understand the task

Read the code and predict the output. Identify the input, the main operation and the value produced.

### Step 2 — Code

~~~python
class PromptBuilder:
    def __init__(self, name):
        self.name = name
    def build(self, question):
        return f"{self.name}: {question}"

class AIApplication:
    def __init__(self, builder):
        self.builder = builder
    def prepare(self, question):
        return self.builder.build(question)

app = AIApplication(PromptBuilder("TechPhile Assistant"))
print(app.prepare("What is RAG?"))
~~~

### Step 3 — Expected output

~~~text
TechPhile Assistant: What is RAG?
~~~

### Step 4 — Explain the code line by line

- PromptBuilder owns prompt creation.
- __init__ initializes an object.
- self refers to the current instance.
- AIApplication receives a builder object and delegates work; this is composition.
- AttributeError often means an attribute was not initialized or was misspelled.

### Step 5 — Interpret the result

Answer in your own words: What input did the program receive? What operation did it perform? What result did it produce? What would change if the input changed? What should be validated before using this in a larger application?

## 4. Common mistakes and troubleshooting

- Read the complete traceback and identify the exception type and line.
- Confirm the active Python interpreter, installed packages, current folder and filename.
- Check types, missing values, boundaries and external response formats.
- Reduce a complex failure to the smallest reproducible example.
- Fix the cause rather than hiding errors with broad exception handling.

## 5. Independent practice

1. Recreate the example from a blank file.
2. Change at least two inputs and predict the output before running.
3. Add one validation or failure case relevant to this topic.
4. Explain the changed output in your own words.
5. Save the code in a clearly named project folder.

## 6. Interview-ready summary

- Define the concept directly.
- Explain the problem it solves.
- Explain when to use it and when a simpler approach is better.
- Give one practical AI-application example.
- Mention one limitation or common failure mode.

## 7. Completion checklist

- [ ] I can explain the concept without copying the definition.
- [ ] I typed and ran the example.
- [ ] I understand the expected output.
- [ ] I completed the independent practice.
- [ ] I can identify and fix a common error.
- [ ] I am ready to attempt the approved project.
