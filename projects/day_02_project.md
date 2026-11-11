# Day 2 Project — AI Conversation Data Manager

**Approved title:** AI Conversation Data Manager  
**Level:** Beginner | **Time:** 45–60 minutes  
**Prerequisite:** Day 2 class notes  
**External services:** None

## 1. Business problem

A chat application receives messages from a user and an assistant. It needs to preserve message order, identify who sent each message, display the conversation and count messages by role.

Build a small terminal program that manages conversation data in Python memory. It does not call an LLM and does not store data permanently.

## 2. Requirements

1. Store a conversation as an ordered list.
2. Represent each message as a dictionary with role and content.
3. Add user and assistant messages.
4. Display messages in order.
5. Count total messages and messages by role.
6. Extract unique words from message content using a set.
7. Handle an empty conversation without crashing.

## 3. Design before coding

~~~text
Create empty messages list
       |
       v
Add message dictionaries
       |
       v
Display conversation in order
       |
       v
Count messages by role
       |
       v
Collect unique words
       |
       v
Display summary
~~~

## 4. Create the project

~~~text
day_02_project/
└── conversation_manager.py
~~~

## 5. Build step by step

### Step 1 — Create an empty conversation

~~~python
conversation = []
print(conversation)
~~~

Output: []

An empty list is suitable because messages arrive in sequence and the collection will grow.

### Step 2 — Add message records

~~~python
conversation.append({
    "role": "user",
    "content": "What is Python?"
})

conversation.append({
    "role": "assistant",
    "content": "Python is a programming language."
})

print(conversation)
~~~

Each dictionary is one message record. The keys role and content describe its fields. append() adds each record to the end of the list.

### Step 3 — Display messages

~~~python
for message in conversation:
    print(f'{message["role"].upper()}: {message["content"]}')
~~~

Output:

~~~text
USER: What is Python?
ASSISTANT: Python is a programming language.
~~~

The loop visits each dictionary. The role is converted to uppercase for display; content is printed as stored.

### Step 4 — Count messages by role

~~~python
user_count = 0
assistant_count = 0

for message in conversation:
    if message["role"] == "user":
        user_count = user_count + 1
    elif message["role"] == "assistant":
        assistant_count = assistant_count + 1

print("User messages:", user_count)
print("Assistant messages:", assistant_count)
~~~

The counters start at zero. Each matching record increases the appropriate counter by one.

### Step 5 — Collect unique words

~~~python
unique_words = set()

for message in conversation:
    words = message["content"].lower().split()
    for word in words:
        unique_words.add(word.strip("?!.,:;"))

print("Unique words:", sorted(unique_words))
~~~

- set() creates an empty set.
- lower() normalises letter case.
- split() separates text on whitespace.
- add() stores a word only once.
- sorted() returns a sorted list for readable output.

This is a simple demonstration, not a full natural-language tokenizer. Punctuation and contractions require more careful handling in real text-processing systems.

## 6. Complete runnable program

~~~python
conversation = []

conversation.append({
    "role": "user",
    "content": "What is Python?"
})
conversation.append({
    "role": "assistant",
    "content": "Python is a programming language."
})
conversation.append({
    "role": "user",
    "content": "Where is Python used?"
})
conversation.append({
    "role": "assistant",
    "content": "Python is used in web development, data and AI."
})

print("===== CONVERSATION =====")
for message in conversation:
    print(f'{message["role"].upper()}: {message["content"]}')

user_count = 0
assistant_count = 0

for message in conversation:
    if message["role"] == "user":
        user_count += 1
    elif message["role"] == "assistant":
        assistant_count += 1

print()
print("===== SUMMARY =====")
print("Total messages:", len(conversation))
print("User messages:", user_count)
print("Assistant messages:", assistant_count)

unique_words = set()
for message in conversation:
    for word in message["content"].lower().split():
        unique_words.add(word.strip("?!.,:;"))

print("Unique words:", sorted(unique_words))
~~~

## 7. Sample output

~~~text
===== CONVERSATION =====
USER: What is Python?
ASSISTANT: Python is a programming language.
USER: Where is Python used?
ASSISTANT: Python is used in web development, data and AI.

===== SUMMARY =====
Total messages: 4
User messages: 2
Assistant messages: 2
Unique words: ['a', 'ai', 'and', 'data', 'development', 'in', 'is', 'language', 'programming', 'python', 'used', 'web', 'where', 'what']
~~~

The list retains the original message order. sorted() alphabetises only the unique-word output.

## 8. Test cases

| Test | Setup | Expected result |
|---|---|---|
| TC01 | Empty list | Total messages = 0 |
| TC02 | One user record | User count = 1 |
| TC03 | One assistant record | Assistant count = 1 |
| TC04 | Two user and two assistant records | Counts = 2 and 2 |
| TC05 | Same word appears twice | Set contains it once |
| TC06 | Same word appears in upper/lower case | Lowercase normalisation treats them alike |
| TC07 | Four messages added | Display order matches insertion order |

For TC01, temporarily leave conversation empty and run the summary. It should not crash.

## 9. Common mistakes

| Mistake | Why it fails | Correction |
|---|---|---|
| conversation["role"] | conversation is a list | Select a message first |
| message.role | Dictionary keys use key lookup | Use message["role"] |
| unique_words.append(word) | Sets do not have append() | Use add() |
| Counter starts at 1 | Off-by-one result | Start at 0 |
| Duplicate words remain | List allows duplicates | Use a set |
| Message order changes | Set does not represent a sequence | Use a list |

## 10. Independent tasks

1. Add a third role called system and count it separately.
2. Add a timestamp field to each message dictionary.
3. Display only user messages.
4. Check whether a particular word exists in the unique-word set.
5. Ask the user to type one new message and append it to the conversation.

## 11. Project README

Create README.md:

~~~markdown
# AI Conversation Data Manager

## Problem
A chat application needs to organise user and assistant messages.

## Features
- Stores messages in order.
- Represents each message with role and content.
- Counts messages by role.
- Displays unique words.

## Technology
Python 3 standard library.

## Run
Windows: py conversation_manager.py
macOS/Linux: python3 conversation_manager.py

## Limitations
This is an in-memory learning program. It does not call an LLM or persist data.
~~~

## 12. Submission checklist

- [ ] conversation_manager.py runs successfully.
- [ ] Message order is correct.
- [ ] User and assistant counts are correct.
- [ ] Unique words are collected.
- [ ] Empty conversation does not crash.
- [ ] Test results are recorded.
- [ ] README is complete.
- [ ] I can explain why a list of dictionaries is used.
- [ ] I can explain why a set is used for unique words.

**Completion standard:** Rebuild the program from a blank file, explain each collection and demonstrate the test cases.
