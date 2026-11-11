# Day 2 — Python data structures: strings, lists, tuples, sets and dictionaries

**Phase:** 1 — Python and Software Development Foundations  
**Duration:** 2–3 hours | **Difficulty:** Beginner  
**Approved mini-project:** AI Conversation Data Manager  
**Prerequisite:** Day 1 — variables, data types, input/output and conditions.

## 1. Learning objectives

By the end of this lesson, you can:
- Explain why programs need collections of values.
- Create and inspect strings, lists, tuples, sets and dictionaries.
- Read, update, add and remove collection items.
- Choose a suitable structure for a small application.
- Use common methods and built-in functions.
- Represent a simple conversation as Python data.

## 2. Why do data structures matter?

Imagine a chat application. A student sends three messages. You could create three separate variables, but what happens when the student sends 100 messages? A data structure organises multiple values so the program can work with them as a group.

| Structure | Stores | Mutable? | Typical application use |
|---|---|---|---|
| String | Text | No | A message's content |
| List | Ordered collection | Yes | Conversation messages |
| Tuple | Ordered collection | No | Fixed configuration values |
| Set | Unique values | Yes | Unique tags or permissions |
| Dictionary | Key-value pairs | Yes | User profile or message record |

These Python objects normally live in memory. A Python list is not a database: it does not automatically preserve information after the program stops.

## 3. Strings — working with text

A string is a sequence of characters.

~~~python
message = "Explain Python in simple words"
print(message)
print(len(message))
print(message.upper())
print(message.lower())
~~~

Expected output:

~~~text
Explain Python in simple words
31
EXPLAIN PYTHON IN SIMPLE WORDS
explain python in simple words
~~~

Explanation:
- The variable message refers to the text.
- len() counts characters, including spaces.
- upper() returns an uppercase version.
- lower() returns a lowercase version.
- These methods return new strings; they do not change the original string.

### 3.1 Indexing

Python uses zero-based indexing: the first character is at position 0.

~~~python
word = "AGENT"
print(word[0])
print(word[1])
print(word[-1])
~~~

Output:

~~~text
A
G
T
~~~

Positive indexes count from the beginning. Negative indexes count from the end. An index outside the valid range raises IndexError.

### 3.2 Slicing

A slice uses start:stop. The start position is included; the stop position is excluded.

~~~python
topic = "GenerativeAI"
print(topic[0:10])
print(topic[10:])
print(topic[:5])
~~~

Output:

~~~text
Generative
AI
Gener
~~~

### 3.3 Useful string methods

| Method | Purpose | Example result |
|---|---|---|
| strip() | Remove whitespace at both ends | "  hi  " becomes "hi" |
| replace(old, new) | Replace matching text | "AI app" becomes "AI tool" |
| split() | Split text into a list | "a b" becomes ["a", "b"] |
| join(items) | Join strings with a separator | ["a","b"] becomes "a, b" |
| startswith(prefix) | Check the beginning | "Hello" starts with "He" |
| find(text) | Find a substring position | "hello" finds "ll" at 2 |

Example:

~~~python
raw_question = "   Explain embeddings   "
clean_question = raw_question.strip()
print(clean_question)
print(clean_question.startswith("Explain"))
~~~

Output:

~~~text
Explain embeddings
True
~~~

### 3.4 Strings are immutable

You cannot replace a character by assigning to its index.

~~~python
name = "Ravi"
# name[0] = "K"  # This raises TypeError
name = "K" + name[1:]
print(name)
~~~

Output: Kavi

The expression creates a new string and assigns it to name.

### 3.5 f-strings

Use an f-string to insert values into readable text.

~~~python
student = "Asha"
score = 86
summary = f"{student} scored {score}%"
print(summary)
~~~

Output: Asha scored 86%

An f-string begins with f and expressions go inside curly braces.

## 4. Lists — ordered collections you can change

A list stores multiple values in order.

~~~python
messages = [
    "What is Python?",
    "Explain variables",
    "Show an example"
]

print(messages)
print(messages[0])
print(len(messages))
~~~

Output:

~~~text
['What is Python?', 'Explain variables', 'Show an example']
What is Python?
3
~~~

### 4.1 Add items

~~~python
messages.append("Explain lists")
messages.insert(1, "What is a program?")
print(messages)
~~~

- append(value) adds one item to the end.
- insert(index, value) inserts at a chosen position. Existing items shift right.

### 4.2 Update and remove

~~~python
messages[0] = "What is an AI application?"
messages.remove("Explain variables")
last_message = messages.pop()
print(messages)
print("Removed:", last_message)
~~~

- Assignment to messages[0] replaces the first item.
- remove(value) removes the first matching value; it raises ValueError if absent.
- pop() removes and returns the last item. pop(index) removes a chosen position.

### 4.3 Sort and reverse

~~~python
scores = [72, 95, 64, 88]
scores.sort()
print(scores)
scores.reverse()
print(scores)
~~~

Output:

~~~text
[64, 72, 88, 95]
[95, 88, 72, 64]
~~~

sort() changes the list itself. sorted(scores) returns a new sorted list.

### 4.4 Loop through a list

~~~python
messages = ["Hello", "Need help", "Thank you"]

for message in messages:
    print("User:", message)
~~~

Output:

~~~text
User: Hello
User: Need help
User: Thank you
~~~

A for loop takes each item in sequence and assigns it to message. The indented statement runs once per item.

## 5. Tuples — ordered collections that should not change

A tuple is ordered and immutable.

~~~python
model_settings = ("model-a", 0.2, 500)
print(model_settings[0])
print(model_settings[1])
print(len(model_settings))
~~~

Output:

~~~text
model-a
0.2
3
~~~

Use a tuple for a small fixed group of values that should not be modified accidentally. You cannot append to a tuple or assign to one of its positions.

A one-item tuple needs a trailing comma:

~~~python
single_value = ("production",)
~~~

Parentheses without a comma do not create a one-item tuple.

## 6. Sets — unique values

A set stores unique values. It does not provide list-style positional indexing.

~~~python
skills = {"Python", "RAG", "Python", "FastAPI"}
print(len(skills))
~~~

The set contains three unique values; its display order may vary.

### 6.1 Add and remove

~~~python
skills.add("LangGraph")
skills.discard("RAG")
print(skills)
~~~

- add(value) inserts a value.
- discard(value) removes it if present and does not fail if absent.
- remove(value) raises KeyError if the value is absent.

### 6.2 Set operations

~~~python
python_group = {"Python", "SQL", "Git"}
ai_group = {"Python", "RAG", "LangGraph"}

print(python_group & ai_group)
print(python_group | ai_group)
print(python_group - ai_group)
~~~

- & gives the intersection: values in both sets.
- | gives the union: values in either set.
- - gives the difference: values in the left set but not the right.

Use sets for uniqueness or membership checks. Do not use them for ordered conversation history.

## 7. Dictionaries — key-value data

A dictionary stores values under named keys.

~~~python
student = {
    "name": "Asha",
    "course": "GenAI",
    "score": 86,
    "active": True
}

print(student["name"])
print(student["score"])
~~~

Output:

~~~text
Asha
86
~~~

The key "name" maps to the value "Asha".

### 7.1 Read safely with get()

~~~python
print(student.get("course"))
print(student.get("city", "Not provided"))
~~~

Output:

~~~text
GenAI
Not provided
~~~

Accessing student["city"] would raise KeyError if the key is missing. get() returns None by default or the fallback you supply.

### 7.2 Add, update and remove

~~~python
student["city"] = "Hyderabad"
student["score"] = 90
removed_score = student.pop("score")
print("Removed:", removed_score)
print(student.keys())
print(student.values())
print(student.items())
~~~

A new key is added; an existing key is updated. pop(key) removes the key and returns its value. keys(), values() and items() let you inspect the dictionary.

~~~python
for key, value in student.items():
    print(key, "=", value)
~~~

### 7.3 Nested dictionaries and lists

Real application data is often nested:

~~~python
conversation = {
    "conversation_id": "C101",
    "user": {"name": "Asha", "role": "student"},
    "messages": [
        {"role": "user", "content": "What is Python?"},
        {"role": "assistant", "content": "Python is a programming language."}
    ]
}

print(conversation["user"]["name"])
print(conversation["messages"][0]["content"])
~~~

Output:

~~~text
Asha
What is Python?
~~~

Read the access path step by step:
1. Get the user dictionary from the conversation.
2. Get name from that dictionary.
3. Get the messages list.
4. Select its first item using index 0.
5. Get content from that message dictionary.

This pattern is common when processing API JSON responses.

## 8. JSON — common format for application data

JSON is a text format commonly used by APIs. Python dictionaries and lists can represent JSON objects and arrays.

~~~python
import json

message = {
    "role": "user",
    "content": "Explain Python",
    "tags": ["beginner", "python"]
}

json_text = json.dumps(message, indent=2)
print(json_text)
~~~

Example output:

~~~json
{
  "role": "user",
  "content": "Explain Python",
  "tags": [
    "beginner",
    "python"
  ]
}
~~~

- import json loads Python's standard JSON module.
- json.dumps() converts a Python object into JSON text.
- indent=2 makes the output readable.

Convert JSON text back into Python:

~~~python
restored_message = json.loads(json_text)
print(restored_message["content"])
~~~

Output: Explain Python

Remember:
- dumps(): Python object → JSON string.
- loads(): JSON string → Python object.
- dump() and load() work with file objects; file handling is covered on Day 5.

## 9. Industry scenario — conversation history

An AI chat backend needs to preserve message order and distinguish user messages from assistant messages.

~~~python
conversation = [
    {"role": "user", "content": "What is an embedding?"},
    {"role": "assistant", "content": "An embedding is a numeric vector representing data."}
]

for message in conversation:
    print(f'{message["role"]}: {message["content"]}')
~~~

Expected output:

~~~text
user: What is an embedding?
assistant: An embedding is a numeric vector representing data.
~~~

Why a list of dictionaries?
- The list preserves message order.
- Each dictionary names the message fields.
- A new message can be appended.
- The program can inspect role and content separately.

This is only an in-memory teaching representation. A production service also needs identity, timestamps, validation, access control, persistence and retention rules.

## 10. Common errors

| Error / symptom | Cause | Fix |
|---|---|---|
| IndexError | Index outside valid range | Check len() and indexes |
| KeyError | Dictionary key absent | Check keys or use get() |
| TypeError | Trying to modify tuple or combine incompatible types | Inspect type and operation |
| ValueError | Removing missing list item with remove() | Check membership first |
| Duplicate values remain | List used where uniqueness is needed | Consider a set |
| Ordering is lost | Set used for sequence data | Use a list |

Debug by inspecting one level at a time:

~~~python
print(type(conversation))
print(len(conversation))
print(conversation)
~~~

## 11. Practice exercises

1. Create a string containing a question. Print its length, uppercase version and first five characters.
2. Create a list of four AI topics. Add one, replace one and remove one.
3. Create a tuple containing a model name and temperature. Try to change the temperature and observe the error.
4. Create a set from ["Python", "RAG", "Python", "SQL"]. How many unique values remain?
5. Create a student dictionary with name, city and completed_days. Add an email field.
6. Create a list of two message dictionaries and print each role and content.
7. Convert a dictionary to JSON text and back.

### Suggested answers

~~~python
# 1
question = "Explain embeddings"
print(len(question))
print(question.upper())
print(question[:5])

# 2
topics = ["Python", "LLM", "RAG", "Agents"]
topics.append("MCP")
topics[1] = "GenAI"
topics.remove("RAG")
print(topics)

# 3
settings = ("model-a", 0.3)
print(settings[1])
# settings[1] = 0.5  # TypeError

# 4
unique_skills = set(["Python", "RAG", "Python", "SQL"])
print(len(unique_skills))  # 3

# 5
student = {"name": "Asha", "city": "Hyderabad", "completed_days": 2}
student["email"] = "asha@example.test"
print(student)

# 6
messages = [
    {"role": "user", "content": "Hello"},
    {"role": "assistant", "content": "How can I help?"}
]
for message in messages:
    print(message["role"], message["content"])

# 7
import json
payload = {"role": "user", "content": "Hi"}
encoded = json.dumps(payload)
decoded = json.loads(encoded)
print(decoded["content"])
~~~

## 12. Daily quiz

**Q1. Which structure preserves order and can grow as new conversation messages arrive?**  
A. Set B. List C. Integer D. Boolean  
**Answer: B.** A list preserves insertion order and supports append().

**Q2. What happens when profile.get("city", "Unknown") is used and city is missing?**  
A. KeyError B. Deletes profile C. Returns Unknown D. Returns a list  
**Answer: C.** get() returns the supplied fallback for a missing key.

**Q3. Which statement about strings is correct?**  
A. Mutable B. Immutable C. Numbers only D. Cannot be sliced  
**Answer: B.** String methods return new strings rather than changing the original.

**Q4. Which structure is suitable for unique permission names?**  
A. Set B. Float C. String D. Integer  
**Answer: A.** A set stores unique values.

**Q5. What does json.loads(json_text) do when the JSON text represents an object?**  
A. Returns a Python dictionary B. Returns a function C. Creates a file D. Returns a set  
**Answer: A.** loads() parses JSON text into Python objects such as dictionaries and lists.

## 13. Day completion checklist

- [ ] Explain the difference between list, tuple, set and dictionary.
- [ ] Use string indexing, slicing and methods.
- [ ] Add, update and remove list items.
- [ ] Explain tuple immutability.
- [ ] Remove duplicates using a set.
- [ ] Read, add and update dictionary fields.
- [ ] Traverse a list and dictionary.
- [ ] Explain nested data access.
- [ ] Convert Python objects to JSON and back.
- [ ] Complete and test AI Conversation Data Manager.

**Evidence:** Save your practice file, project file, test results and sample conversation output.

**Next lesson:** Day 3 — Functions, parameters, arguments, return values, scope and comprehensions.
