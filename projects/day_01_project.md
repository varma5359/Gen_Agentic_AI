# Day 1 Project — AI Application Development Concept Explorer

**Phase:** 1 — Python and Software Development Foundations  
**Approved topic:** Introduction to AI application development, GenAI and Agentic AI career roles, Python revision and development environment.  
**Approved project title:** AI Application Development Concept Explorer  
**Difficulty:** Beginner | **Time:** 35–50 minutes after class notes  
**External services / API keys:** Not required

> **What you will build:** A terminal application that lets a learner choose an AI topic and read a beginner-friendly explanation. You will practise variables, strings, dictionaries, input, output, conditions and validation. This is a learning project, not an AI chatbot or production application.

## 1. Business problem

A beginner hears terms such as AI, Machine Learning, Deep Learning, Generative AI, LLM and Agentic AI. The terms sound similar, and the learner may confuse them.

Build a small menu-driven program that displays a simple explanation for each term.

## 2. Learning outcomes

After completing the project, you should be able to:
- Translate a small requirement into program steps.
- Store related information in a Python dictionary.
- Display a menu using print().
- Receive a selection using input().
- Use if/elif/else to select a response.
- Validate an invalid selection without crashing.
- Explain the code and test expected behaviour.

## 3. Requirements

1. Display the application title.
2. Display a numbered menu of topics.
3. Accept the user's selection.
4. Display an explanation for a valid selection.
5. Display a friendly message for an invalid selection.
6. Allow the user to exit.
7. Keep the program simple and readable.

| Choice | Topic |
|---:|---|
| 1 | Artificial Intelligence |
| 2 | Machine Learning |
| 3 | Deep Learning |
| 4 | Generative AI |
| 5 | Large Language Model |
| 6 | Agentic AI |
| 0 | Exit |

## 4. Plan before coding

~~~text
START
  │
  ▼
Display application title
  │
  ▼
Display topic menu
  │
  ▼
Ask the user for a choice
  │
  ▼
Is the choice "0"?
  ├── Yes → Display goodbye message → END
  │
  └── No
       │
       ▼
Is the choice a known topic?
  ├── Yes → Display its explanation
  │
  └── No  → Display "Invalid choice"
       │
       ▼
END
~~~

For Day 1, this first version runs once and then ends. A repeating menu is an optional extension after the required version works.

## 5. Create the project folder

Create this structure:

~~~text
day_01_project/
└── concept_explorer.py
~~~

Open the folder in your editor. Create a file named exactly concept_explorer.py.

## 6. Build the project step by step

### Step 1 — Display the title and menu

~~~python
print("===================================")
print(" AI APPLICATION CONCEPT EXPLORER")
print("===================================")
print("1. Artificial Intelligence")
print("2. Machine Learning")
print("3. Deep Learning")
print("4. Generative AI")
print("5. Large Language Model")
print("6. Agentic AI")
print("0. Exit")
~~~

Run the file.

Expected output:

~~~text
===================================
 AI APPLICATION CONCEPT EXPLORER
===================================
1. Artificial Intelligence
2. Machine Learning
3. Deep Learning
4. Generative AI
5. Large Language Model
6. Agentic AI
0. Exit
~~~

**What you learned:** print() displays one line at a time. Text is written inside quotes.

### Step 2 — Receive the user's choice

Add this line at the bottom:

~~~python
choice = input("Enter your choice: ")
~~~

Run the program and enter 4. Nothing else happens after you enter the choice yet. That is expected: we have collected input but have not written the decision logic.

**Important:** choice is a string. Compare it with "4", not the integer 4.

### Step 3 — Display an explanation for a selection

Add:

~~~python
if choice == "4":
    print("Generative AI creates new content such as text, images, audio or code.")
~~~

Run the program and enter 4.

Expected final line:

~~~text
Generative AI creates new content such as text, images, audio or code.
~~~

Line-by-line:
- if starts a conditional decision.
- choice == "4" checks whether the entered text is exactly "4".
- The colon starts the indented block.
- The indented print() runs only when the condition is true.

### Step 4 — Add all topic choices

Replace the single if block with:

~~~python
if choice == "1":
    print("AI is the broad field of building systems that perform tasks associated with intelligence.")

elif choice == "2":
    print("Machine Learning uses data to learn patterns and make predictions or decisions.")

elif choice == "3":
    print("Deep Learning is a type of Machine Learning that uses neural networks with multiple layers.")

elif choice == "4":
    print("Generative AI creates new content such as text, images, audio or code.")

elif choice == "5":
    print("An LLM is a model trained to process and generate language.")

elif choice == "6":
    print("Agentic AI systems work toward a goal through controlled steps and may use tools.")

elif choice == "0":
    print("Thank you for learning. Goodbye!")

else:
    print("Invalid choice. Please enter a number from 0 to 6.")
~~~

**Why use elif?** It means "otherwise, if". Python checks the conditions in order. When one is true, its block runs and the remaining branches are skipped.

**Why use else?** It handles choices that did not match any valid condition.

### Step 5 — Complete runnable version

Your complete file should now look like this:

~~~python
print("===================================")
print(" AI APPLICATION CONCEPT EXPLORER")
print("===================================")
print("1. Artificial Intelligence")
print("2. Machine Learning")
print("3. Deep Learning")
print("4. Generative AI")
print("5. Large Language Model")
print("6. Agentic AI")
print("0. Exit")

choice = input("Enter your choice: ")

if choice == "1":
    print("AI is the broad field of building systems that perform tasks associated with intelligence.")

elif choice == "2":
    print("Machine Learning uses data to learn patterns and make predictions or decisions.")

elif choice == "3":
    print("Deep Learning is a type of Machine Learning that uses neural networks with multiple layers.")

elif choice == "4":
    print("Generative AI creates new content such as text, images, audio or code.")

elif choice == "5":
    print("An LLM is a model trained to process and generate language.")

elif choice == "6":
    print("Agentic AI systems work toward a goal through controlled steps and may use tools.")

elif choice == "0":
    print("Thank you for learning. Goodbye!")

else:
    print("Invalid choice. Please enter a number from 0 to 6.")
~~~

### Step 6 — Run the project

Open the terminal in the project folder.

- Windows: py concept_explorer.py or python concept_explorer.py
- macOS/Linux: python3 concept_explorer.py

**Sample run — valid choice**

~~~text
===================================
 AI APPLICATION CONCEPT EXPLORER
===================================
1. Artificial Intelligence
2. Machine Learning
3. Deep Learning
4. Generative AI
5. Large Language Model
6. Agentic AI
0. Exit
Enter your choice: 6
Agentic AI systems work toward a goal through controlled steps and may use tools.
~~~

**Sample run — invalid choice**

~~~text
Enter your choice: 9
Invalid choice. Please enter a number from 0 to 6.
~~~

**Sample run — exit**

~~~text
Enter your choice: 0
Thank you for learning. Goodbye!
~~~

## 7. Understand the limitations

This is intentionally a small first-day program.

- It displays only one topic per execution.
- Explanations are stored directly in the Python source code.
- It does not use a database or an LLM.
- It does not remember previous selections.
- It does not repeat the menu after a selection.
- It does not yet have automated tests.

These are not mistakes. We are learning one concept at a time. Do not add databases, APIs or AI frameworks today.

## 8. Test the application

Run the program separately for each test.

| Test | Input | Expected result |
|---|---|---|
| TC01 | 1 | AI explanation displayed |
| TC02 | 2 | Machine Learning explanation displayed |
| TC03 | 3 | Deep Learning explanation displayed |
| TC04 | 4 | Generative AI explanation displayed |
| TC05 | 5 | LLM explanation displayed |
| TC06 | 6 | Agentic AI explanation displayed |
| TC07 | 0 | Goodbye message displayed |
| TC08 | 9 | Invalid-choice message displayed |
| TC09 | hello | Invalid-choice message displayed |
| TC10 | blank input | Invalid-choice message displayed |

Record your actual result:

| Test ID | Expected result | Actual result | PASS / FAIL |
|---|---|---|---|
| TC01 | AI explanation |  |  |
| TC04 | Generative AI explanation |  |  |
| TC07 | Goodbye message |  |  |
| TC08 | Invalid-choice message |  |  |
| TC09 | Invalid-choice message |  |  |

A test is not PASS merely because you read the expected output. Run it and compare the result.

## 9. Common mistakes and fixes

| Mistake | What happens | Fix |
|---|---|---|
| Compare choice == 4 | Input is text, so comparison does not match | Use choice == "4" |
| Forget the colon | Syntax error | Add : after the condition |
| No indentation | Indentation error or wrong block | Indent consistently |
| Use = inside the condition | Assignment is not a comparison | Use == |
| Run from wrong folder | Python cannot find the file | Change to project directory |
| Misspell file name | File-not-found error | Check spelling and .py extension |

## 10. Independent tasks

Complete without copying the full solution:

1. Change the title to include your name or batch.
2. Rewrite the Machine Learning explanation in your own words without changing its meaning.
3. Add one more menu option: Python. Explain that Python is a programming language used to build application logic and integrations.
4. Test the new option and an invalid option.
5. Explain why the program compares menu input to strings.

## 11. Optional extension

A repeating menu would require a while loop. Loops are formally covered later in the pathway, so do not feel you must learn them prematurely. First complete and understand the required version.

## 12. Project README template

Create a README.md in the project folder and fill it in:

~~~markdown
# AI Application Development Concept Explorer

## Problem
Beginners often confuse AI, ML, Deep Learning, GenAI, LLM and Agentic AI.

## Features
- Displays a topic menu.
- Shows an explanation for a selected topic.
- Handles invalid choices.
- Provides an exit option.

## Technology
- Python 3
- Python built-in functions only

## How to run
Windows:
py concept_explorer.py

macOS / Linux:
python3 concept_explorer.py

## Sample input
4

## Expected output
Generative AI creates new content such as text, images, audio or code.

## Limitations
This is a beginner terminal program. It does not call an AI model or save user data.
~~~

## 13. Explain the project in an interview

A sample structure:

"I built a beginner-friendly terminal application called AI Application Development Concept Explorer. It helps learners distinguish AI, Machine Learning, Deep Learning, Generative AI, LLMs and Agentic AI. I used Python input and output to create a menu, conditional statements to select a topic, and an else branch to handle invalid choices. I tested valid selections, exit and invalid input. This is a basic educational program; it does not connect to an LLM or database."

Do not claim that this project is an AI agent. It is a Python learning application about AI concepts.

## 14. Submission checklist

- [ ] concept_explorer.py exists and runs.
- [ ] All six topic choices work.
- [ ] Exit choice works.
- [ ] Invalid text and invalid numbers are handled.
- [ ] I tested the required test cases.
- [ ] I wrote the project README.
- [ ] I can explain input(), print(), if, elif and else.
- [ ] I can explain why this is not itself an LLM or AI agent.
- [ ] No API key, password or private information is included.

**Completion standard:** You can build the program again from a blank file and explain each line without copying this guide.
