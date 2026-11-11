# Day 01 — Interview Preparation and Code Understanding

**Topic:** Introduction to AI application development, GenAI and Agentic AI career roles, Python basics and development environment  
**Mini-project:** AI Application Development Concept Explorer  
**Level:** Beginner

> Use this file after completing the Day 01 class notes and coding tasks. First answer aloud without reading. Then compare your answer with the sample. Interview answers should be clear and correct, not memorised word for word.

## 1. Concept questions

### Q1. What is software?
Software is a set of instructions that tells a computer how to perform tasks.

### Q2. What is an application?
An application is software designed to help a user complete a task, such as learning, shopping or communication.

### Q3. Explain input, processing and output.
Input is the information supplied to a program. Processing is the work the program performs. Output is the result it produces.

### Q4. What is Artificial Intelligence?
AI is the field of building computer systems that perform tasks such as recognising patterns, understanding language or making predictions.

### Q5. What is Machine Learning?
Machine Learning is an approach in which a model learns patterns from data or examples.

### Q6. What is Deep Learning?
Deep Learning is a type of machine learning that uses neural networks with multiple layers.

### Q7. What is Generative AI?
Generative AI creates new content, such as text, code, images or audio, based on patterns learned during training.

### Q8. What is an LLM?
LLM means Large Language Model. It is a model designed to process and generate language.

### Q9. What is a prompt?
A prompt is the instruction or input supplied to a model.

### Q10. Does an LLM always give correct answers?
No. It can produce incorrect or unsupported information. Developers should test outputs and use suitable safeguards.

### Q11. What is the difference between a chatbot and an AI agent?
A chatbot may simply respond to messages. An AI agent can select from permitted actions, use tools and observe results while working toward a goal.

### Q12. What is the difference between a workflow and an agent?
A workflow follows a sequence defined by a developer. An agent can choose actions based on the goal and observations, within defined boundaries.

### Q13. Why is Python used in AI application development?
Python is used to write application logic, process data, call APIs and connect AI models with user-facing applications.

## 2. Python fundamentals

### Q14. What is a variable?
A variable is a name that refers to a value.

### Q15. What is a data type?
A data type describes the kind of value, such as text, an integer, a decimal number or True/False.

### Q16. Name four basic Python data types.
- `str`: text, for example `"Python"`.
- `int`: whole number, for example `25`.
- `float`: decimal number, for example `75.5`.
- `bool`: Boolean value, either `True` or `False`.

### Q17. What does `print()` do?
It displays information in the terminal. It returns `None`.

### Q18. What does `input()` do?
It waits for the user to type something and returns the entered value as a string.

### Q19. Why do we use `int()`?
It converts suitable values, such as the text `"20"`, into an integer `20`.

### Q20. What is the difference between `=` and `==`?
`=` assigns a value to a variable. `==` compares two values and produces True or False.

### Q21. What is a condition?
A condition is a test that helps a program choose which block of code should run.

### Q22. What is a loop?
A loop repeats instructions. A `for` loop can process each item in a collection.

### Q23. What is a function?
A function is a named, reusable block of code that performs a task.

### Q24. What is a parameter?
A parameter is a named placeholder in a function definition.

### Q25. What is an argument?
An argument is the actual value passed to a function when it is called.

### Q26. What is the difference between `print()` and `return`?
`print()` displays information. `return` sends a value from a function back to the code that called it.

### Q27. What is debugging?
Debugging is finding and fixing the cause of a problem in a program.

### Q28. What is an interpreter?
A Python interpreter runs Python code.

## 3. Code-reading questions

### Q29. What is the output?

```python
name = "Anu"
print("Hello", name)
```

**Answer**
```text
Hello Anu
```

### Q30. What is the type of `marks`?

```python
marks = 85
print(type(marks))
```

**Answer:** `<class 'int'>`.

### Q31. What does this program display?

```python
age = input("Enter age: ")
print(type(age))
```

**Answer:** `<class 'str'>`, because `input()` returns text.

### Q32. What is the output?

```python
age = int("20")
print(age + 1)
```

**Answer:** `21`.

### Q33. What is the output?

```python
marks = 35

if marks >= 40:
    print("Pass")
else:
    print("Fail")
```

**Answer:** `Fail`.

### Q34. How many times does this loop run?

```python
for number in range(1, 4):
    print(number)
```

**Answer:** Three times. It displays 1, 2 and 3.

### Q35. What does this function return?

```python
def add(a, b):
    return a + b

result = add(2, 3)
print(result)
```

**Answer:** It returns `5`, which is stored in `result` and then displayed.

### Q36. What happens here?

```python
def say_hello():
    print("Hello")

result = say_hello()
print(result)
```

**Answer**
```text
Hello
None
```

The function prints Hello but has no explicit return value, so Python returns `None`.

## 4. Mini-project discussion — AI Application Development Concept Explorer

Be ready to explain the project in your own words.

1. **What problem does it solve?**  
   It gives a beginner a simple introduction to the topics in the GenAI and Agentic AI pathway and displays a suggested next step.

2. **Why did you create functions?**  
   To separate tasks into reusable, understandable blocks.

3. **Why did you use a list?**  
   To store several learning topics together and process them using a loop.

4. **Why did you use a loop?**  
   To display every topic without writing a separate print statement for each one.

5. **Why did you use `strip()`?**  
   To remove spaces at the beginning and end of user-entered text.

6. **Why did you use `lower()`?**  
   To make the level comparison work even if the user types uppercase letters.

7. **What does `recommend_next_step()` return?**  
   A text message based on the experience level supplied to it.

8. **Why is `main()` called at the bottom?**  
   Defining a function does not run it. Calling `main()` starts the main program sequence.

9. **What happens if the learner enters an empty name?**  
   The program uses the default name `Learner`.

10. **What would you improve next?**  
    I would keep asking for the experience level until the user enters one of the accepted choices. I could also add a quiz and save progress.

## 5. Practical coding tasks

Try these without looking at the solutions in the class notes:

1. Ask for a learner's name and display a welcome message.
2. Ask for two whole numbers and display their sum.
3. Check whether a mark is pass or fail.
4. Display five course topics using a loop.
5. Write a function that returns a welcome message.
6. Explain why `input()` needs conversion before numeric addition.
7. Run a Python file from the terminal and describe each step.
8. Intentionally misspell a variable name, observe the error and fix it.

## 6. Mock interview

**Interviewer:** You are new to GenAI development. What are you learning first?

**Student:** I am learning Python and software development fundamentals first. I need to understand variables, data structures, functions, APIs and error handling before I build applications that connect to language models.

**Interviewer:** What is an LLM-powered application?

**Student:** It is a software application that sends input to a large language model, receives the generated output and presents or uses that output as part of a user task.

**Interviewer:** Can you trust every response from an LLM?

**Student:** No. A model can generate incorrect information. An application should validate inputs and outputs, test its behaviour and provide suitable safeguards.

**Interviewer:** What did you build today?

**Student:** I built a Python terminal application called AI Application Development Concept Explorer. It collects a learner's name and experience level, displays the pathway topics and gives a suggested next step. I used variables, input, conditions, loops, lists and functions.

## 7. Self-check before the next lesson

You are ready to move on when you can do these without copying:

- [ ] Explain AI, Generative AI, LLM, chatbot, workflow and agent.
- [ ] Explain the purpose of variables and the four basic data types.
- [ ] Explain why `input()` returns a string.
- [ ] Write a condition and a loop.
- [ ] Define a function with a parameter and return a value.
- [ ] Explain the difference between printing and returning.
- [ ] Run your mini-project and explain its main functions.

If you cannot explain one answer, revisit that section in the Day 01 class notes and repeat its small code example.
