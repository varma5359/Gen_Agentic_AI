# Day 4 Interview Guide — Object-Oriented Programming

## Q1. What is a class and an object?
A class defines structure and behaviour; an object is an instance. A Message class can define role and content, while individual objects represent particular messages. Follow-up: Can one class create many objects? Yes, each has its own instance state.

## Q2. What is self?
self is the conventional first parameter of an instance method and refers to the current object. Python supplies the instance when the method is called through that object. Follow-up: Is self a reserved keyword? No, but the convention should be followed.

## Q3. What is __init__?
It is an initializer called when an instance is created. It commonly assigns attributes and validates initial values. Follow-up: Does __init__ create the object itself? Object creation occurs before initialization.

## Q4. Explain encapsulation.
Encapsulation groups data and operations and encourages controlled access through methods. A leading underscore signals an internal attribute by convention; it does not make data securely private. Follow-up: How can a method protect state? Validate before updating attributes.

## Q5. Explain inheritance.
Inheritance models an is-a relationship and lets a subclass reuse or specialise a base class. PDFDocument may be a kind of Document. Follow-up: When should it be avoided? When the relationship is has-a or the hierarchy creates unnecessary coupling.

## Q6. What is composition?
Composition builds an object using other objects as components. Assistant can contain Retriever and PromptBuilder. Follow-up: How does this help testing? Supply a fake dependency with predictable behaviour.

## Q7. Class attribute versus instance attribute?
A class attribute is associated with the class and shared unless shadowed; an instance attribute belongs to one object. Follow-up: Why are mutable class attributes risky? Instances may unintentionally share one list.

## Q8. Should every function be placed inside a class?
No. Classes help model stateful components; simple stateless transformations are often clearer as functions. Follow-up: Give an example of each.

## Practical task
Create two Message objects and a Conversation object that contains them. Explain why Conversation has a list of Message objects (composition).
