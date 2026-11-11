# Day 2 Interview Guide — Python Data Structures

## Q1. What is a data structure, and why do applications need one?

**Answer:** A data structure organises data so a program can store, access and modify it. A chat application may use a list to preserve message order and dictionaries to represent each message's fields.

**Example:** A list containing message dictionaries: [{"role": "user", "content": "Hi"}].

**Follow-up:** Is a Python list a database? No. A list is an in-memory object; a database provides persistent storage and query capabilities.

## Q2. Compare a list and a tuple.

**Answer:** Both are ordered collections and support indexing. A list is mutable, so items can be added, removed or replaced. A tuple is immutable, so its positions cannot be reassigned after creation.

**Example:** Use a list for growing conversation history and a tuple for fixed configuration values.

**Follow-up:** Does an immutable tuple guarantee every object nested inside it is immutable? No. A tuple may contain a mutable object such as a list.

## Q3. When would you use a set?

**Answer:** Use a set when uniqueness and membership are important. Adding the same value more than once does not create duplicate entries.

**Example:** Store unique skill tags or permission names.

**Follow-up:** Should a set be used for ordered chat messages? No. Use a list when sequence matters.

## Q4. Why are dictionaries useful in API applications?

**Answer:** Dictionaries represent named key-value fields. JSON objects commonly map naturally to Python dictionaries, making it easy to read fields such as role, content, id and status.

**Follow-up:** What happens when you access a missing key with square brackets? Python raises KeyError; get() can provide a fallback.

## Q5. Explain string immutability.

**Answer:** A string cannot be modified in place. Operations such as replace() return a new string. Assigning that result to a variable makes the variable refer to the new string.

**Follow-up:** Does upper() modify the original string? No. It returns a new uppercase string.

## Q6. What is the difference between append() and extend()?

**Answer:** append() adds one object as a single item. extend() iterates over another iterable and adds its elements individually.

~~~python
items = [1, 2]
items.append([3, 4])
print(items)  # [1, 2, [3, 4]]

items = [1, 2]
items.extend([3, 4])
print(items)  # [1, 2, 3, 4]
~~~

## Q7. Explain indexing and slicing.

**Answer:** Indexing selects one item by position. Slicing selects a range using start:stop, including the start and excluding the stop.

~~~python
word = "PYTHON"
print(word[0])    # P
print(word[1:4])  # YTH
print(word[-1])   # N
~~~

## Q8. How do you convert a Python dictionary to JSON?

**Answer:** Use json.dumps() to convert a Python object into JSON text, and json.loads() to parse JSON text back into Python objects. Use json.dump() and json.load() with file objects when reading or writing JSON files.

## Q9. A conversation has 1,000 messages. Which structure would you use and why?

**Answer:** For a simple in-memory representation, use a list of dictionaries so messages stay ordered and each message has named fields. For a real service, persist the conversation in a database and load the relevant history with limits and access checks. The Python list alone is not durable storage.

## Q10. Read this code and explain its output.

~~~python
tags = ["rag", "python", "rag"]
unique_tags = set(tags)
print(len(tags))
print(len(unique_tags))
~~~

**Answer:** It prints 3 and then 2. The list contains three items, including a duplicate. The set contains only two unique values.

## Practical interview task

Create a dictionary for a student, add a list of completed topics, then print each topic. Explain why the student record is a dictionary and the completed topics are a list.

## How to structure your answer

Explain the requirement first, choose the structure, justify the choice, show a small example and mention one limitation. Avoid saying one data structure is universally best.
