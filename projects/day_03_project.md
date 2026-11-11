# Day 3 Project — Reusable Text Processing Toolkit

## Objective
Build reusable functions to clean text, count words, extract non-empty lines and summarise multiple questions. This is a Python utility, not an LLM.

## Requirements
- Accept text as function input.
- Return results rather than only printing inside utility functions.
- Count words safely, including empty input.
- Extract non-empty lines.
- Summarise a list of questions.
- Demonstrate a comprehension.

## Create text_toolkit.py

~~~python
def clean_text(text):
    return " ".join(text.strip().split())


def count_words(text):
    cleaned = clean_text(text)
    if not cleaned:
        return 0
    return len(cleaned.split())


def extract_lines(text):
    return [line.strip() for line in text.splitlines() if line.strip()]


def summarize_questions(questions):
    summaries = []
    for question in questions:
        cleaned = clean_text(question)
        summaries.append({
            "question": cleaned,
            "word_count": count_words(cleaned)
        })
    return summaries


if __name__ == "__main__":
    samples = ["  What is Python?  ", "Explain embeddings", "   "]
    print("Clean:", clean_text("  Learn   Python  "))
    print("Word count:", count_words("Build AI applications with Python"))
    print("Lines:", extract_lines("First question\n\nSecond question"))
    print("Summary:", summarize_questions(samples))
~~~

## Explain the code
- clean_text trims the ends, splits on whitespace and rejoins using one space.
- count_words handles blank input before dividing or counting.
- splitlines separates a multiline string.
- The list comprehension keeps only non-empty trimmed lines.
- summarize_questions reuses the other functions instead of duplicating their logic.
- The main guard runs the demonstration only when this file is executed directly. When imported, its function definitions are available without running the demo.

## Run
Windows: py text_toolkit.py  
macOS/Linux: python3 text_toolkit.py

Expected key results: Clean text is Learn Python; word count is 5; extracted lines are First question and Second question; the blank question has word_count 0.

## Test cases
| Input | Expected |
|---|---|
| Empty string | Word count 0 |
| Spaces only | Clean result empty; count 0 |
| Learn with three spaces then Python | Clean result has one space |
| A, blank line, B | Two extracted lines |
| Two normal questions and one blank | Three summary records |

## Extensions
1. Add character_count(text).
2. Add longest_word(text), including empty-input behaviour.
3. Add a second file that imports clean_text().
4. Explain one situation where lowercasing could be unsafe.

## Submission
Submit the Python file, sample output, test results and a short explanation of why utility functions return values instead of printing them.
**Completion standard:** Rebuild one new text utility from a blank file and explain its inputs, output and empty-input behaviour.
