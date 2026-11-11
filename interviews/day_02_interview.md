# Day 02 — Interview Preparation

**Pathway:** GenAI & Agentic AI Developer  
**Phase:** 1 — Python and Software Development Foundations  
**Topic:** Python Data Structures: Strings, Lists, Tuples, Sets and Dictionaries  
**Mini-project:** AI Conversation Data Manager  
**Audience:** College students and freshers

## How to practise

Read a question, close the notes and answer aloud. Do not memorize word for word. For coding questions, type and run the example yourself.

## 1. Core concept questions

### Q1. Explain strings.

**Beginner answer:** A string stores text such as a student's question. Text is written inside quotes.

**Example code**

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

**How it works:** strip() removes surrounding whitespace; lower() returns lowercase text; len() counts characters. Strings are immutable, so these methods return new values.

**Important methods or syntax:** upper(), title(), capitalize(), replace(old, new), split(separator), join(iterable), startswith(), endswith(), find() and count().

**Common mistake:** IndexError for an invalid position; confusing strip() with replace(); expecting a method to modify the original string.

**Follow-up:** Where would you use this in a Python AI application?


### Q2. Explain lists.

**Beginner answer:** A list stores an ordered collection that can be changed. It is useful for messages, tasks or student names.

**Example code**

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

**How it works:** append() adds one item. Index zero is the first item. len() returns the number of items.

**Important methods or syntax:** append(), extend(), insert(), remove(), pop(), clear(), index(), count(), sort(), reverse() and copy().

**Common mistake:** IndexError, ValueError from remove() when the value is absent, and modifying a list while iterating over it.

**Follow-up:** Where would you use this in a Python AI application?


### Q3. Explain tuples.

**Beginner answer:** A tuple is ordered like a list, but it cannot be changed after creation. It suits fixed records.

**Example code**

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

**How it works:** Indexing reads a value. count() counts occurrences. index() finds the first matching position.

**Important methods or syntax:** count(), index(), len(), tuple() and unpacking: name, roll, dept = student.

**Common mistake:** TypeError when trying to assign to a tuple position; a one-item tuple needs a trailing comma.

**Follow-up:** Where would you use this in a Python AI application?


### Q4. Explain sets.

**Beginner answer:** A set stores unique values and is useful for removing duplicates or comparing groups.

**Example code**

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

**How it works:** The duplicate is stored once. add() inserts an item. in checks membership. Set display order is not guaranteed.

**Important methods or syntax:** add(), update(), discard(), remove(), union(), intersection(), difference(), issubset() and issuperset().

**Common mistake:** Do not use numeric indexes with sets. remove() raises KeyError for a missing value; discard() does not.

**Follow-up:** Where would you use this in a Python AI application?


### Q5. Explain dictionaries.

**Beginner answer:** A dictionary stores key-value pairs. A key is a label used to find its value.

**Example code**

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

**How it works:** Square brackets read a required key. get() safely reads an optional key. Assignment adds or updates a key.

**Important methods or syntax:** keys(), values(), items(), get(), update(), pop(), setdefault(), copy() and dictionary comprehensions.

**Common mistake:** KeyError when a key is absent; using mutable objects as keys; confusing keys with values.

**Follow-up:** Where would you use this in a Python AI application?


### Q6. Explain choosing a data structure.

**Beginner answer:** Choose a structure based on what the data needs to do: preserve order, allow changes, prevent duplicates or map labels to values.

**Example code**

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

**How it works:** type() shows the object's type. Each structure has a different purpose; there is no single best collection for every problem.

**Important methods or syntax:** Convert between list(), tuple(), set() and dict() only when the target structure makes sense. Consider ordering, mutability and uniqueness.

**Common mistake:** Converting a set to a list does not restore an original order. Converting a list to a set removes duplicates.

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

### Exercise 1 — Strings

**Task:** Clean a question, count its characters, split it into words and explain the output.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 2 — Lists

**Task:** Create a conversation list, add a message, replace one message and remove an unwanted message.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 3 — Tuples

**Task:** Store a fixed student identity record and unpack it into three variables.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 4 — Sets

**Task:** Find unique skills and common skills between two students.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 5 — Dictionaries

**Task:** Represent one chat message with role, content and timestamp fields.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.


### Exercise 6 — Choosing a data structure

**Task:** Choose a suitable structure for chat history, user profile, unique labels and fixed coordinates.

**Starter area**

```python
# Write your solution here.
# Use meaningful names.
# Print or return the result.
# Test one unusual input.
```

**Interviewer checks:** understanding, choice of Python feature, correctness, readability, output explanation and error handling.



## 4. Mini-project discussion — AI Conversation Data Manager

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

## 8. List-method interview questions — know the exact behaviour

### Q7. What is the difference between append() and extend()?

`append(x)` adds x as one item. `extend(items)` adds each item from an iterable separately.

```python
a = ["Hi"]
a.append(["Hello", "Bye"])

b = ["Hi"]
b.extend(["Hello", "Bye"])

print(a)
print(b)
```

Output:

```text
['Hi', ['Hello', 'Bye']]
['Hi', 'Hello', 'Bye']
```

### Q8. Does append() return the updated list?

No. It changes the existing list and returns `None`.

```python
names = ["Anu"]
result = names.append("Ravi")
print(names)
print(result)
```

Output:

```text
['Anu', 'Ravi']
None
```

### Q9. What is the difference between remove() and pop()?

- `remove(value)` removes the first matching value.
- `pop(index)` removes the item at an index and returns that item. Without an index, it removes the last item.

### Q10. What is the difference between sort() and sorted()?

- `list.sort()` changes the original list and returns `None`.
- `sorted(list)` returns a new sorted list and leaves the original unchanged.

### Q11. What is the difference between reverse() and sort(reverse=True)?

- `reverse()` reverses the current order.
- `sort(reverse=True)` arranges values in descending sorted order.

### Q12. What does copy() do?

It creates a shallow copy of a list. The outer list is new, but nested mutable objects may still be shared.

### Q13. Which list methods change the original list?

`append()`, `extend()`, `insert()`, `remove()`, `pop()`, `clear()`, `sort()` and `reverse()` change the list. `index()` and `count()` only return information. `copy()` creates another list.

## 9. Code-output interview drills

Predict the output before reading the answer.

### Drill 1

```python
items = [1, 2]
items.append([3, 4])
print(len(items))
```

**Answer:** `3`. The nested list is one item.

### Drill 2

```python
items = [1, 2]
items.extend([3, 4])
print(len(items))
```

**Answer:** `4`. Two items were added separately.

### Drill 3

```python
items = ["a", "b", "a"]
print(items.count("a"))
print(items.index("a"))
```

**Answer:** `2`, then `0`.

### Drill 4

```python
scores = [30, 10, 20]
result = scores.sort()
print(scores)
print(result)
```

**Answer:** `[10, 20, 30]`, then `None`.

### Drill 5

```python
items = ["first", "second", "third"]
removed = items.pop()
print(removed)
print(items)
```

**Answer:** `third`, then `['first', 'second']`.

### Drill 6

```python
message = "  HELLO Python  "
print(message.strip().lower())
```

**Answer:** `hello python`. strip() removes surrounding spaces; lower() returns lowercase text.

## 10. Mini-project interview answers

### Q14. Why did you represent conversation history as a list?

Because a conversation is an ordered sequence of messages. A list preserves the order and allows new messages to be appended.

### Q15. Why is each message a dictionary?

Each message has named fields such as role and content. A dictionary lets the program access them by meaningful keys rather than remembering numeric positions.

### Q16. Why did you use a set for unique words?

A set keeps only unique values, so repeated words are stored once. Sets do not guarantee a display order, so the project uses `sorted()` when it needs predictable display.

### Q17. Why did you write separate functions?

Each function performs one focused task: create a message, display history, count user messages or collect unique words. This makes code easier to read, test and reuse.

### Q18. What tests did you perform?

I tested a normal message, an empty message, uppercase text and repeated words. I checked that empty input is not added and duplicate words appear only once in the unique-word result.

### Q19. What would you improve before production?

I would validate allowed roles, limit message length, persist the conversation in a database, add automated tests and avoid storing sensitive information unnecessarily.

## 11. Practical coding interview challenge

**Task:** Write a function that receives a list of message dictionaries and returns only the user messages.

Starter data:

```python
conversation = [
    {"role": "user", "content": "Hi"},
    {"role": "assistant", "content": "Hello"},
    {"role": "user", "content": "Explain lists"}
]
```

**One possible solution:**

```python
def get_user_messages(conversation):
    user_messages = []

    for message in conversation:
        if message["role"] == "user":
            user_messages.append(message["content"])

    return user_messages


print(get_user_messages(conversation))
```

Output:

```text
['Hi', 'Explain lists']
```

**Explain your solution:** the function receives a list, creates an empty result list, checks each dictionary's role, appends matching content and returns the result. The original conversation is not changed.

## 12. Final interview readiness checklist

- [ ] I can define all five data structures with a practical example.
- [ ] I can explain append vs extend without hesitation.
- [ ] I know which list methods mutate and which return a value.
- [ ] I can explain the return value of append, sort and reverse.
- [ ] I can distinguish remove from pop.
- [ ] I can explain shallow copy at a beginner level.
- [ ] I can explain list-of-dictionaries conversation history.
- [ ] I can write and explain the practical coding challenge.
- [ ] I can discuss the mini-project honestly, including its limitations.
