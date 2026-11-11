# Day 6 — Advanced Python: iterators, generators, decorators, context managers and type hints

**Phase 1 | 2–3 hours | Project: Reusable Python Logging and Timing Utility**

## Learning objectives
Explain iterable and iterator; use iter() and next(); create generators with yield; explain decorators; use context managers; add type hints to functions.

## 1. Iterable and iterator
An iterable can produce an iterator. Lists, tuples and strings are iterable.

~~~python
topics = ["Python", "RAG", "Agents"]
iterator = iter(topics)
print(next(iterator))
print(next(iterator))
print(next(iterator))
~~~

Output: Python, RAG, Agents.

iter() obtains an iterator. next() asks for its next item. After the last item, next() raises StopIteration. A for loop handles this stopping signal automatically.

## 2. Build a simple iterator
~~~python
class NumberRange:
    def __init__(self, stop):
        self.current = 0
        self.stop = stop

    def __iter__(self):
        return self

    def __next__(self):
        if self.current >= self.stop:
            raise StopIteration
        value = self.current
        self.current += 1
        return value

for number in NumberRange(3):
    print(number)
~~~

Output: 0, 1, 2. __iter__ returns the iterator. __next__ returns a value or signals completion. Most everyday code uses built-in iterables or generators rather than custom iterator classes.

## 3. Generators and yield
A generator produces values lazily, one at a time.

~~~python
def read_questions(lines):
    for line in lines:
        cleaned = line.strip()
        if cleaned:
            yield cleaned

for question in read_questions([" What is RAG? ", "", "Explain embeddings"]):
    print(question)
~~~

yield produces one value and pauses execution. The next iteration resumes from that point. Generators can save memory when processing large files or streams. An exhausted generator does not restart; call the generator function again to obtain a new one.

## 4. Decorators
A decorator wraps a function to add behaviour without rewriting the function's main logic.

~~~python
from functools import wraps

def announce_call(function):
    @wraps(function)
    def wrapper(*args, **kwargs):
        print("Starting operation")
        result = function(*args, **kwargs)
        print("Operation finished")
        return result
    return wrapper

@announce_call
def clean_question(question):
    return question.strip().lower()

print(clean_question("  Explain RAG  "))
~~~

The decorator syntax is equivalent to assigning clean_question = announce_call(clean_question). wrapper accepts positional and keyword arguments. wraps preserves useful metadata. This simple wrapper prints "Operation finished" only when the function returns normally; use try/finally if cleanup or timing must occur even after an exception.

## 5. Context managers
A context manager controls setup and cleanup around a block. You have already used one with files.

~~~python
with open("sample.txt", "w", encoding="utf-8") as file:
    file.write("Hello")
~~~

The file is closed when the block exits. The context manager protocol uses __enter__ and __exit__. Prefer with for resources that need cleanup.

## 6. Type hints
Type hints describe expected input and output types. Python does not automatically enforce them at runtime.

~~~python
def word_count(text: str) -> int:
    return len(text.split())

count: int = word_count("Learn Python today")
print(count)
~~~

text: str documents the expected input. -> int documents the expected return type. Editors and static type checkers can use hints to detect mistakes.

For collections:
~~~python
def normalize_all(items: list[str]) -> list[str]:
    return [item.strip().lower() for item in items]
~~~

## 7. Industry scenario
A document ingestion pipeline may process a large source one record at a time. A generator avoids loading every record into memory. A decorator can measure duration. A context manager closes files. Type hints make reusable utility contracts clearer.

## 8. Common mistakes
| Mistake | Fix |
|---|---|
| next() after exhaustion | Use for loops or handle StopIteration |
| Expect generator to replay | Create a new generator |
| Decorator forgets return | Return the wrapped function's result |
| Wrapper hides metadata | Use functools.wraps |
| Assume hints validate input | Add explicit runtime validation |
| Forget resource cleanup | Use a context manager |

## 9. Exercises
1. Create an iterator from a list and call next() three times.
2. Write a generator that yields even numbers below a limit.
3. Write a decorator that prints a function name.
4. Add type hints to a function accepting a list of strings.
5. Use with to write and read a text file.
6. Explain one benefit of lazy generation.

## 10. Five-question quiz
1. iter() returns: A iterator B list always C string D class. **Answer A:** it obtains an iterator.
2. yield: A ends program B produces a value and suspends generator C writes a file D imports module. **Answer B.**
3. Iterator exhaustion raises: A KeyError B StopIteration C ValueError D SyntaxError. **Answer B.**
4. functools.wraps preserves: A database B function metadata C API keys D memory. **Answer B.**
5. Are type hints enforced automatically at runtime? A always B no C strings only D classes only. **Answer B.**

## Completion checklist
- [ ] Explain iterable versus iterator.
- [ ] Use iter() and next().
- [ ] Explain StopIteration.
- [ ] Write a generator.
- [ ] Explain and write a decorator.
- [ ] Explain context-manager cleanup.
- [ ] Add type hints.
- [ ] Complete the project.

**Next:** Day 7 — Asynchronous Python: async, await, asyncio, HTTP fundamentals and concurrent API requests.
