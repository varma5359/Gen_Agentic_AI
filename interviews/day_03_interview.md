# Day 03 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** Functions, Parameters, Arguments, Return Values, Scope and Comprehensions  
**Mini-project:** Reusable Text Processing Toolkit  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain defining and calling functions.

**Beginner answer:** A function is a named set of instructions that can be reused. Defining it does not run it; calling it does.

**Example code**

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

**How it works:** def begins a definition. The indented body belongs to the function. greet() calls it.

**Important methods or syntax:** Function names, docstrings, return statements, positional calls and keyword calls.

**Common mistake:** Forgetting parentheses, incorrect indentation or defining a function but never calling it.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain parameters and arguments.

**Beginner answer:** Parameters are names in the function definition. Arguments are actual values supplied during a call.

**Example code**

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

**How it works:** name and course are parameters. The strings supplied are arguments. Keyword arguments identify parameters by name.

**Important methods or syntax:** Positional, keyword, default and variable-length arguments (*args and **kwargs) after the basic form is clear.

**Common mistake:** Missing required arguments cause TypeError. Positional arguments must not follow keyword arguments in a call.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain return values.

**Beginner answer:** return sends a result back to the caller. print() displays information but does not return that displayed text.

**Example code**

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

**How it works:** The function calculates total. return sends 15 back. answer stores it.

**Important methods or syntax:** Returning strings, numbers, lists and dictionaries; early returns; returning multiple values as a tuple.

**Common mistake:** A function without return gives None. Code after return in the same path is not executed.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain variable scope.

**Beginner answer:** Scope describes where a variable name can be accessed. A local variable is created inside a function.

**Example code**

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

**How it works:** topic is local. course is global to this module and can be read inside the function.

**Important methods or syntax:** LEGB name lookup: Local, Enclosing, Global, Built-in. Prefer parameters and return values over global mutation.

**Common mistake:** Reading a local variable outside its function causes NameError. Assignment can make a name local unexpectedly.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain default arguments and keyword arguments.

**Beginner answer:** A default argument is used when the caller does not supply a value. Keyword arguments make a call easier to understand.

**Example code**

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

**How it works:** level has a default. The second call passes both values by parameter name.

**Important methods or syntax:** Use immutable defaults. For optional lists, use None and create a new list inside the function.

**Common mistake:** A required parameter cannot follow a default parameter in the definition. Avoid [] as a mutable default.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain comprehensions.

**Beginner answer:** A comprehension builds a new collection from an iterable. Learn the ordinary loop first, then use a comprehension when it remains readable.

**Example code**

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

**How it works:** The loop creates the first result. The list comprehension selects names with four or fewer characters.

**Important methods or syntax:** List, set and dictionary comprehensions; conditional expressions; nested comprehensions only when clear.

**Common mistake:** Dense nested comprehensions are hard to debug. Do not use one merely to shorten code.

**Follow-up:** Where would you use this in a Python AI application?


### Q7. Explain small reusable toolkit.

**Beginner answer:** A toolkit combines small functions, each responsible for one step. This makes the code easier to test and reuse.

**Example code**

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

**How it works:** summarize() calls two smaller functions and combines their results in a dictionary.

**Important methods or syntax:** Add type hints, docstrings, input validation and unit tests when comfortable.

**Common mistake:** A function should not silently do unrelated tasks. Validate None and unexpected input types when the function is public.

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

### Exercise 1 — Defining and calling functions

**Task:** Write welcome(), clean_question() and display_result() as separate functions.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — Parameters and arguments

**Task:** Create a function that accepts a student's name and today's topic.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Return values

**Task:** Write calculate_average(marks) that returns a number.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Variable scope

**Task:** Create two functions and demonstrate that one function's local variable is not available globally.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Default arguments and keyword arguments

**Task:** Write a function with a default language parameter.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Comprehensions

**Task:** Convert names to title case and filter short names.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 7 — Small reusable toolkit

**Task:** Extend the toolkit with character_count() and test empty input.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — Reusable Text Processing Toolkit

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

## 6. Function coding interview — complete answers

### Q8. What is the difference between print() and return?

`print()` displays output for a person. `return` sends a value to the caller so the program can use it.

```python
def show_total():
    print(10 + 5)

def calculate_total():
    return 10 + 5

first = show_total()
second = calculate_total()
print(first)
print(second)
```

Output:

```text
15
None
15
```

The first function prints 15 and implicitly returns None. The second function returns 15.

### Q9. What is variable scope?

Scope is where a variable name can be accessed. A local variable is defined inside a function. A module-level variable is defined outside functions.

Prefer passing values through parameters and receiving results through return values. This makes functions easier to test and understand.

### Q10. What are default arguments?

A default argument is used when the caller does not supply a value for that parameter.

```python
def greet(name, course="Python"):
    return f"Hello {name}, welcome to {course}"

print(greet("Anu"))
print(greet("Ravi", "GenAI"))
```

Output:

```text
Hello Anu, welcome to Python
Hello Ravi, welcome to GenAI
```

Avoid mutable defaults such as `items=[]`. The same list can be reused across calls. Use `None` and create a new list inside the function instead.

### Q11. What are *args and **kwargs?

- `*args` collects extra positional arguments into a tuple.
- `**kwargs` collects extra keyword arguments into a dictionary.

Use them when a function genuinely needs a variable number of arguments, not automatically in every function.

### Q12. What is a comprehension?

A comprehension creates a new collection from an iterable, optionally transforming or filtering its values.

```python
scores = [40, 75, 90]
passed = [score for score in scores if score >= 50]
print(passed)
```

Output:

```text
[75, 90]
```

A normal loop may be clearer when the logic has several steps.

## 7. Code-output interview drills

### Drill 1 — no explicit return

```python
def greet():
    print("Hi")

result = greet()
print(result)
```

**Answer:**

```text
Hi
None
```

### Drill 2 — parameter and argument

```python
def multiply(number, factor):
    return number * factor

print(multiply(4, 3))
```

**Answer:** `12`.

### Drill 3 — keyword arguments

```python
def profile(name, course):
    return name + " - " + course

print(profile(course="Python", name="Anu"))
```

**Answer:** `Anu - Python`.

### Drill 4 — default value

```python
def welcome(name, course="Python"):
    return f"{name}: {course}"

print(welcome("Ravi"))
```

**Answer:** `Ravi: Python`.

### Drill 5 — comprehension

```python
values = [1, 2, 3, 4]
squares = [value * value for value in values if value % 2 == 0]
print(squares)
```

**Answer:** `[4, 16]`. Only even values are selected and squared.

## 8. Practical coding interview challenge

**Task:** Write a function that accepts a list of text messages and returns the number of non-empty messages.

Starter data:

```python
messages = ["Hello", "", "Explain Python", "   ", "Thanks"]
```

**One possible solution:**

```python
def count_non_empty_messages(messages):
    count = 0

    for message in messages:
        if message.strip():
            count += 1

    return count


print(count_non_empty_messages(messages))
```

Output:

```text
3
```

Explanation:
- The function receives a list parameter.
- The for loop visits each message.
- `strip()` removes surrounding whitespace and returns a new string.
- An empty string is false in a condition.
- The counter increases for each non-empty message.
- `return` sends the final integer to the caller.
- The original list is not modified.

## 9. Project discussion — Reusable Text Processing Toolkit

Be ready to explain:

1. **What problem does it solve?** It accepts a text input and reports cleaned text, character count, word count, unique words and long words.
2. **Why did you create separate functions?** Each function has one responsibility and can be checked independently.
3. **Why does clean_text() return a string?** Other functions need to use the cleaned value.
4. **Why does analyze_text() return a dictionary?** Each result has a meaningful name such as `words` or `unique_words`.
5. **Why is set() used?** It removes duplicate words.
6. **Why is sorted() used after set()?** It gives predictable alphabetical display order.
7. **How does the program handle empty input?** main() checks whether the stripped input is empty and displays a helpful message.
8. **Does it use an AI model?** No. It is a plain Python text-processing foundation, not an LLM application.
9. **What are its limitations?** Simple whitespace splitting does not fully handle every punctuation mark, abbreviation or language. It does not identify sentence meaning.
10. **What would you add next?** Automated tests, stronger text normalization and a reusable module.

## 10. Final interview readiness checklist

- [ ] I can define and call a function.
- [ ] I can explain parameters and arguments.
- [ ] I can explain positional, keyword and default arguments.
- [ ] I can explain `*args` and `**kwargs`.
- [ ] I can explain print versus return.
- [ ] I can explain local and global scope.
- [ ] I can read and write a simple list comprehension.
- [ ] I can explain every function in the Text Processing Toolkit.
- [ ] I can solve the non-empty message challenge.
- [ ] I can explain one project limitation honestly.
