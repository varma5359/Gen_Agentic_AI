# Day 6 Interview Guide — Advanced Python

## Q1. Iterable versus iterator?
An iterable can produce an iterator; an iterator produces values one at a time with next(). A list is iterable; iter(list) returns an iterator. After exhaustion, next() raises StopIteration.

## Q2. What is a generator?
A generator is an iterator commonly written as a function using yield. It produces values lazily and pauses between them, which can reduce memory use for large sequences. An exhausted generator must be recreated to iterate again.

## Q3. yield versus return?
return exits a function and supplies its final result. yield produces a value while suspending a generator so iteration can resume later.

## Q4. What is a decorator?
A decorator takes a callable and returns a callable, often wrapping the original with extra behaviour such as logging, timing or access checks. functools.wraps preserves useful metadata.

## Q5. What is a context manager?
It manages setup and cleanup around a with block. Files are a common example. The protocol uses __enter__ and __exit__.

## Q6. What are type hints?
They document expected types and support editors and static analysis. Python generally does not enforce them automatically at runtime; validate untrusted input explicitly.

## Q7. Why use perf_counter?
It is designed for high-resolution elapsed-time measurement and is monotonic. Wall-clock time can change due to clock adjustments.

## Practical task
Write a decorator that logs a function name and elapsed time, preserves metadata and returns the original result. Explain try/finally.
