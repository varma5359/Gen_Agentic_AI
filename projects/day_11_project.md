# Day 11 Project — Generative AI Concept Explorer

**Duration:** 30–45 minutes. Build it yourself before using hints.

## Objective
Create a Python command-line explorer that helps a beginner understand AI, ML, deep learning, GenAI and LLMs.

## Requirements
1. Show a numbered menu for the five concepts.
2. Accept a selection and display its definition, practical example and relationship to AI.
3. Allow multiple selections until the learner exits.
4. Handle invalid numeric and non-numeric input without crashing.
5. Keep the program understandable to a beginner.

## Suggested structure
~~~text
day11_concept_explorer/
    main.py
    README.md
~~~

## Build tasks
1. Create a dictionary. For each concept store name, meaning, example and relationship.
2. Write a function to display the menu.
3. Write a function to display one concept.
4. Add a loop to repeat the menu.
5. Convert input safely using try/except.
6. Add an exit option and friendly messages.

## Example interaction
~~~text
GENAI CONCEPT EXPLORER
1. Artificial Intelligence
2. Machine Learning
3. Deep Learning
4. Generative AI
5. Large Language Model
0. Exit
Choose a concept: 4

Generative AI
Meaning: Models that generate new content.
Example: Drafting a customer support reply.
Remember: Generative AI is an area of AI.
~~~

## Test cases
| Test | Input | Expected |
|---|---|---|
| TC01 | 1 | AI details shown |
| TC02 | 5 | LLM details shown |
| TC03 | 0 | Program exits |
| TC04 | 9 | Invalid choice message |
| TC05 | abc | No traceback; friendly error |
| TC06 | 2 then 4 | Menu repeats |

## Hints
- Use a dictionary of dictionaries to group concept details.
- items() is useful for displaying menu options.
- Use while for a repeated menu.
- Use get() to safely look up an option.
- Keep menu and display functions separate.

## Reflection
1. Why is this a fixed lookup program rather than GenAI?
2. What does a dictionary do that an LLM does differently?
3. Which concepts were hardest to distinguish?
4. Draw the transformer overview.

## Submission
Submit main.py, README, test observations and terminal evidence. No API key or paid model is required.

## Optional extension
Add a compare-two-concepts option. Explain the comparison logic.
