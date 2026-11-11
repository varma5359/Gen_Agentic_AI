# Day 3 Interview Guide — Python Functions

## Q1. Why use functions?
Functions package a task into a reusable unit. They reduce repeated code, give operations meaningful names and make testing easier. Example: clean_text() can be reused for many incoming questions. Follow-up: Does defining a function execute it? No; it must be called.

## Q2. Parameter versus argument?
A parameter is a name in the function definition; an argument is the value supplied by the caller. In def greet(name), name is the parameter. In greet("Asha"), Asha is the argument. Follow-up: What if a required argument is missing? Python raises TypeError.

## Q3. Explain print versus return.
print displays a value. return sends a value to the caller so it can be stored, tested or passed to another function. A function without explicit return produces None. Follow-up: Can a function return multiple values? Yes; Python packages comma-separated results in a tuple, which can be unpacked.

## Q4. What are default and keyword arguments?
A default value is used when the caller omits that parameter. A keyword argument supplies a value by parameter name, making calls clearer. Follow-up: Where do default parameters appear? After required parameters.

## Q5. Explain variable scope.
Scope determines where a name can be accessed. A variable created inside a function is local. Module-level names are defined outside functions. Prefer explicit inputs and outputs instead of changing globals. Follow-up: Why? It makes dependencies visible and testing easier.

## Q6. What is a list comprehension?
A concise way to build a list by applying an expression to each item, optionally filtering. Example: [word.upper() for word in words]. Follow-up: When avoid it? When it becomes complex; use a normal loop.

## Q7. What does the main guard do?
It runs a block when the file is executed directly, but skips that block when imported. Top-level statements outside the guard still execute during import. Follow-up: Is it a security feature? No, it controls program entry behaviour.

## Q8. Trace the output.
~~~python
def add(a, b=2):
    return a + b
print(add(5))
print(add(5, 4))
~~~
Answer: 7 then 9. The first call uses the default; the second supplies b=4.

## Practical task
Write a function that receives questions and returns dictionaries containing each trimmed question and its word count. Explain empty-input handling and why the function returns data rather than printing it.
