# Day 4 — Object-oriented programming: classes, objects, inheritance, encapsulation and composition

**Phase 1 | 2–3 hours | Beginner | Project: AI Application Component Manager**

## 1. Why OOP?
As applications grow, related data and behaviour should be organised. A message has a role and content; a retriever has a name and a search operation. Object-oriented programming groups related state and behaviour into objects. OOP is useful for some systems, but simple functions and dictionaries are often clearer for small tasks.

## 2. Class and object
A class is a blueprint. An object is an instance created from it.

~~~python
class Student:
    def __init__(self, name, course):
        self.name = name
        self.course = course

    def introduce(self):
        return f"{self.name} is learning {self.course}"

student_one = Student("Asha", "GenAI")
print(student_one.introduce())
~~~

Output: Asha is learning GenAI

- class defines a new type.
- __init__ is the initializer called during object creation.
- self refers to the current instance.
- self.name and self.course are instance attributes.
- introduce is an instance method.
- Student(...) creates an instance.
Python supplies the instance as self when the method is called through the object.

## 3. Each object has its own state

~~~python
first = Student("Asha", "GenAI")
second = Student("Ravi", "Python")
print(first.name)
print(second.name)
~~~

Each object has its own name and course. Changing one instance's attribute does not automatically change the other.

## 4. Encapsulation and validation
Encapsulation groups data with the operations that manage it. Python uses conventions rather than strict private access in ordinary classes.

~~~python
class QuizResult:
    def __init__(self, score):
        self.set_score(score)

    def set_score(self, score):
        if not 0 <= score <= 100:
            raise ValueError("Score must be between 0 and 100")
        self._score = score

    def get_score(self):
        return self._score

result = QuizResult(85)
print(result.get_score())
~~~

The setter checks the allowed range before storing the score. A leading underscore communicates that _score is intended for internal use; it is not a security boundary.

## 5. Inheritance
Inheritance represents an "is-a" relationship and allows a subclass to reuse or specialise a base class.

~~~python
class AIComponent:
    def __init__(self, name):
        self.name = name

    def describe(self):
        return f"Component: {self.name}"

class Retriever(AIComponent):
    def retrieve(self):
        return "Searching the knowledge store"

retriever = Retriever("Document Retriever")
print(retriever.describe())
print(retriever.retrieve())
~~~

Retriever is an AIComponent, so it inherits describe and adds retrieve. Use inheritance for a genuine subtype, not merely to avoid writing a few lines.

## 6. Composition
Composition represents a "has-a" relationship: one object contains or uses another.

~~~python
class PromptBuilder:
    def build(self, question):
        return f"Answer clearly: {question}"

class Assistant:
    def __init__(self, prompt_builder):
        self.prompt_builder = prompt_builder

    def prepare_prompt(self, question):
        return self.prompt_builder.build(question)

assistant = Assistant(PromptBuilder())
print(assistant.prepare_prompt("What is RAG?"))
~~~

Output: Answer clearly: What is RAG?

Assistant has a PromptBuilder. It does not need to inherit from it. Composition makes components easier to replace and test.

## 7. Class attributes and instance attributes

~~~python
class Course:
    platform = "TechPhile"

    def __init__(self, title):
        self.title = title

a = Course("GenAI")
b = Course("Python")
print(a.platform, a.title)
print(b.platform, b.title)
~~~

platform is a class attribute shared through the class. title is an instance attribute. Avoid mutable class-level lists for per-object state because instances may accidentally share them.

## 8. Industry scenario
A knowledge assistant may use a PromptBuilder, Retriever and ResponseFormatter. The Assistant coordinates those components. A retriever can be replaced with a test double during testing. This is a practical reason to use composition.

## 9. Common mistakes
| Mistake | Correction |
|---|---|
| Forget self in an instance method | Add self as first parameter |
| Confuse class and instance attributes | Shared class state versus per-object state |
| Use inheritance for every relationship | Use composition for has-a |
| Treat underscore as secure private | It is a naming convention |
| Store per-user mutable data on class | Initialise it on each instance |

## 10. Exercises
1. Create Message with role and content.
2. Add a method returning a formatted message.
3. Create Document and PDFDocument using inheritance.
4. Create SearchService that contains a DocumentStore using composition.
5. Validate a score range.

## 11. Five-question quiz
1. A class is: A instance B blueprint C loop D database. **Answer B:** class defines the structure and behaviour of instances.
2. self refers to: A current instance B parent always C module D global. **Answer A.**
3. Composition models: A is-a B has-a C equality D import. **Answer B.**
4. Inheritance allows: A reuse/specialisation B database storage C encryption D concurrency. **Answer A.**
5. Is a leading underscore secure privacy? A yes B no, convention C encryption D abstract class. **Answer B.**

## 12. Completion checklist
- [ ] Define a class and create objects.
- [ ] Explain self and __init__.
- [ ] Create attributes and methods.
- [ ] Validate object state.
- [ ] Demonstrate inheritance and composition.
- [ ] Distinguish class and instance attributes.
- [ ] Complete the project.

**Next:** Day 5 — Python modules, packages, exceptions, JSON, file handling and logging.
