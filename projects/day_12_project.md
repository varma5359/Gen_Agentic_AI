# Day 12 Project — LLM Token and Context Window Analyzer

**Duration:** 45–60 minutes. Build the analyser yourself before using hints.

## Objective
Create a Python CLI utility that reports character/word counts, token count using a selected tokenizer when available, and a configurable context budget.

## Requirements
1. Accept text from the user.
2. Display character count and whitespace-separated word count.
3. If tiktoken is installed, display token count and token pieces using a chosen encoding.
4. Display the encoding name; do not claim it applies to every model.
5. Accept context capacity and instruction/history/user/retrieval/output allocations.
6. Calculate planned total and remaining headroom.
7. Warn if the planned total exceeds capacity.
8. Handle blank text and invalid or negative numbers.

## Setup
~~~bash
python -m venv .venv
python -m pip install tiktoken
~~~
Activate the virtual environment using the commands taught in Phase 1. If installation is unavailable, complete the count and budget features first.

## Suggested structure
~~~text
day12_token_analyzer/
    main.py
    README.md
~~~

## Build plan
1. Write a function for character and word counts.
2. Write a separate tokenizer function.
3. Write a function that adds the budget categories.
4. Validate integer inputs; reject negatives.
5. Compare planned total with capacity.
6. Test normal, blank, invalid and over-capacity inputs.

## Sample budget
Capacity 8,000; instructions 700; history 1,800; user 300; retrieved context 3,000; output allowance 1,000. Planned total = 6,800; remaining headroom = 1,200. These are illustrative values, not a real model specification.

## Test plan
| Test | Expected |
|---|---|
| Empty text | Friendly validation |
| Normal sentence | Character and word counts |
| Tokenizer installed | Token IDs/pieces and count |
| Tokenizer unavailable | Helpful installation guidance; rest still works |
| Valid budget | Correct sum and headroom |
| Over capacity | Clear warning |
| Negative/text budget | Reject and reprompt/report |

## Hints
- len(text) counts characters.
- len(text.split()) counts whitespace-separated pieces.
- encoding.encode(text) returns token IDs.
- sum() adds budget components.
- Keep the selected encoding visible.

## Reflection
Explain why word count differs from token count, why tokenizer choice matters and why output allowance must be budgeted.

## Submission
Submit code, README, sample output and test evidence. Never claim a tokenizer matches every provider model.

## Optional extension
Add an early warning when 80% of the capacity is used.
