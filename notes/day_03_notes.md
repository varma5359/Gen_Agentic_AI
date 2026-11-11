# Day 3 — Functions, parameters, arguments, return values, scope and comprehensions

**Phase 1 | 2–3 hours | Beginner | Project: Reusable Text Processing Toolkit**

## Learning objectives
You will define and call functions, distinguish parameters from arguments, return reusable results, use default and keyword arguments, understand local scope, and write simple list and dictionary comprehensions.

## 1. Why functions?
A function is a named block of reusable code. Imagine cleaning a question in five parts of an application. Copying the same code five times means fixing five places later. A function gives that operation one name and one implementation.

~~~python
def greet():
    print("Welcome to TechPhile")

greet()
greet()
~~~

Output:
~~~text
Welcome to TechPhile
Welcome to TechPhile
~~~

The keyword def defines a function. The name greet identifies it. Parentheses hold optional parameters. The colon begins the indented function body. Defining the function does not run it; greet() calls it.

## 2. Parameters and arguments
A parameter is the name in a function definition. An argument is the actual value supplied by the caller.

~~~python
def greet_student(student_name):
    print(f"Hello, {student_name}")

greet_student("Asha")
greet_student("Ravi")
~~~

student_name is the parameter. Asha and Ravi are arguments. Each call supplies a different value.

## 3. Return versus print
print displays a value. return sends a result back to the caller so it can be reused.

~~~python
def clean_text(text):
    cleaned = text.strip().lower()
    return cleaned

question = clean_text("  Explain RAG  ")
print(question)
~~~

Output: explain rag

The function receives text, trims whitespace, lowercases it and returns the new string. The caller stores the result in question.

~~~python
def show_total(a, b):
    print(a + b)

def calculate_total(a, b):
    return a + b

answer = calculate_total(10, 20)
print(answer)
~~~

The first function only displays the result. The second returns it, allowing another part of the program to use it. A function with no explicit return returns None.

## 4. Positional, keyword and default arguments

~~~python
def make_summary(topic, level="beginner"):
    return f"{topic} ({level})"

print(make_summary("Embeddings"))
print(make_summary("RAG", "intermediate"))
print(make_summary(level="advanced", topic="Agents"))
~~~

Output:
~~~text
Embeddings (beginner)
RAG (intermediate)
Agents (advanced)
~~~

Positional arguments match by order. Keyword arguments name the parameter. A default is used when the caller omits that argument. Required parameters should come before defaulted parameters.

## 5. Returning multiple values

~~~python
def calculate_scores(scores):
    if not scores:
        return 0, 0
    total = sum(scores)
    average = total / len(scores)
    return total, average

total_score, average_score = calculate_scores([80, 90, 70])
print(total_score, average_score)
~~~

Output: 240 80.0

Python returns the two values as a tuple. The caller unpacks them into two variables. Empty input is explicitly handled to avoid division by zero.

## 6. Scope
Scope determines where a variable name can be accessed.

~~~python
course_name = "GenAI"

def show_course():
    lesson_name = "Python functions"
    print(course_name)
    print(lesson_name)

show_course()
~~~

lesson_name is local to the function. course_name is defined at module level. Prefer passing values into functions and returning results instead of changing global variables. Explicit inputs and outputs make code easier to test.

## 7. Comprehensions
First understand the normal loop:

~~~python
topics = ["python", "rag", "agents"]
uppercase_topics = []
for topic in topics:
    uppercase_topics.append(topic.upper())
print(uppercase_topics)
~~~

The compact equivalent:

~~~python
uppercase_topics = [topic.upper() for topic in topics]
print(uppercase_topics)
~~~

Output: ['PYTHON', 'RAG', 'AGENTS']

A comprehension creates a collection from an iterable. Filtering example:

~~~python
scores = [35, 82, 49, 91]
passed_scores = [score for score in scores if score >= 50]
print(passed_scores)
~~~

Output: [82, 91]

Dictionary comprehension:

~~~python
words = ["python", "rag"]
lengths = {word: len(word) for word in words}
print(lengths)
~~~

Output: {'python': 6, 'rag': 3}

Use comprehensions for simple transformations. Use a regular loop if the expression becomes difficult to read.

## 8. Industry scenario
A question-answering application may receive inconsistent text. A reusable normalisation function can trim whitespace and standardise case before later processing.

~~~python
def normalize_question(question):
    if not question.strip():
        return ""
    return question.strip().lower()

questions = ["  HOW do I use Python?  ", "Explain RAG"]
cleaned = [normalize_question(item) for item in questions]
print(cleaned)
~~~

Output: ['how do i use python?', 'explain rag']

This is basic text normalisation, not a complete language-processing pipeline. Case may matter in passwords, identifiers and source code, so do not lowercase every kind of data indiscriminately.

## 9. Common mistakes
| Mistake | Cause | Fix |
|---|---|---|
| Function never runs | Defined but not called | Call it with parentheses |
| Missing argument | Required input not supplied | Pass the required value |
| print used instead of return | Result cannot be reused | Return computed data |
| Code after return | Function already exited | Move required work before return |
| Local name used outside | Scope misunderstanding | Return it or pass it onward |
| Complex comprehension | Compact syntax hides logic | Use a normal loop |

## 10. Practice
1. Write welcome(name) that returns a greeting.
2. Write word_count(text) that returns the number of whitespace-separated words.
3. Write calculate_average(scores); return zero for an empty list.
4. Clean a list of questions using a loop, then a comprehension.
5. Build a dictionary mapping each word to its length.
6. Explain why return is different from print.

## 11. Five-question quiz
1. What does calling a function do? A Deletes it B Executes its body C Saves it D Converts it to a class. **Answer B:** defining and calling are separate.
2. In def double(number), what is number? A Argument B Parameter C Return D Module. **Answer B:** it is the input name in the definition.
3. Which statement sends a value back? A print B input C return D import. **Answer C:** return supplies a result to the caller.
4. What does a function without return produce? A 0 B False C None D Empty string. **Answer C:** Python returns None implicitly.
5. When is a comprehension suitable? A Complex nested workflow B Simple transformation C Replacing all functions D File encryption. **Answer B:** use it when the transformation remains readable.

## 12. Completion checklist
- [ ] Define and call functions.
- [ ] Explain parameters and arguments.
- [ ] Use positional, keyword and default arguments.
- [ ] Explain print versus return.
- [ ] Return multiple values and unpack them.
- [ ] Explain local and module scope.
- [ ] Write list and dictionary comprehensions.
- [ ] Complete the project and test empty input.

**Next:** Day 4 — Object-oriented programming: classes, objects, inheritance, encapsulation and composition.
