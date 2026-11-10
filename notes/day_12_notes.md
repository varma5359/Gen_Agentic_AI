# Day 12 — Tokens, Tokenization and Context Windows

**Phase:** 2 — Generative AI and LLM Foundations  
**Approved topic:** Tokens, tokenization, context windows, model inputs and outputs  
**Mini-project:** LLM Token and Context Window Analyzer  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
- Explain what a token is and why models use tokens.
- Distinguish characters, words and tokens.
- Explain token IDs and the tokenizer's role.
- Describe a context window and why it matters.
- Run a token-counting experiment and interpret its limits.

## 2. What is a token?

A token is a unit of text processed by a language model. Depending on the tokenizer, a token may represent:
- A whole word.
- Part of a word.
- Punctuation.
- Whitespace combined with text.
- A special control token.

A token is **not always one word** and is **not always one character**.

Example (illustrative only; exact splits depend on the model tokenizer):
```text
Text: "Generative AI is useful!"
Possible pieces: ["Gener", "ative", " AI", " is", " useful", "!"]
```

The exact token boundaries and count vary by tokenizer and model. Never use a guessed word-to-token ratio for precise billing or context calculations.

| Unit | Meaning |
|---|---|
| Character | A letter, digit, space or punctuation mark |
| Word | A human-readable language unit |
| Token | A unit defined by a model's tokenizer |
| Token ID | Integer identifier for a token in a vocabulary |

## 3. What is tokenization?

Tokenization is the process of converting input text into tokens and then into numeric token IDs that the model can process.

```text
"Hello, students!"
       ↓ tokenizer
["Hello", ",", " students", "!"]  (illustrative)
       ↓ vocabulary lookup
[15496, 11, 1051, 0]              (illustrative IDs only)
       ↓
Model processes numeric representations
```

The IDs above are examples, not guaranteed IDs for a real model. Different tokenizers use different vocabularies and IDs.

### Why tokens are used
- Neural networks process numbers, not raw text characters.
- A subword vocabulary can represent common words efficiently and still handle unfamiliar words.
- Token counts are used for context limits and often for API pricing.
- Tokenization can behave differently across languages, code, symbols and long identifiers.

## 4. What is a context window?

The context window is the maximum amount of tokenized information a model can consider in one request or conversation step. The exact limit depends on the model and provider.

It may include:
- System instructions.
- Developer instructions.
- User messages.
- Conversation history.
- Tool descriptions and tool results.
- The requested output budget (provider/model dependent).

```text
Context capacity (illustrative: 8,000 tokens)
┌──────────────────────────────────────┐
│ Instructions + conversation + input │
│                                      │
│ Used context                         │
├──────────────────────────────────────┤
│ Space reserved for generated output  │
└──────────────────────────────────────┘
Total must fit the model's applicable limit.
```

**Important:** A larger context window does not guarantee that the model will use every detail perfectly. Long prompts can increase cost and latency, and relevant details may be harder to use consistently.

## 5. Model input and output

| Item | Example |
|---|---|
| Input | “Summarize this paragraph in three bullets.” |
| Input tokens | Tokens representing instructions and paragraph |
| Output | Three generated bullets |
| Output tokens | Tokens generated for the answer |
| Context | Input and other included context, plus generation constraints |

A provider may report separate input, output, cached or reasoning token categories. Check the provider's usage response and current model documentation before estimating costs.

## 6. Count tokens with a real tokenizer

For a local demonstration, install OpenAI's `tiktoken` package. This lesson uses the `cl100k_base` encoding as an example. It is **not** the tokenizer for every model.

**Run in terminal**
```bash
python -m pip install tiktoken
```

**Python program**
```python
import tiktoken

text = "Generative AI helps students learn."

encoding = tiktoken.get_encoding("cl100k_base")
token_ids = encoding.encode(text)

print("Text:", text)
print("Token IDs:", token_ids)
print("Token count:", len(token_ids))
print("Decoded text:", encoding.decode(token_ids))
```

**What each line does**
- `import tiktoken`: makes the installed tokenizer library available.
- `get_encoding("cl100k_base")`: loads a named tokenizer encoding.
- `encode(text)`: converts text into a list of token IDs.
- `len(token_ids)`: returns the number of IDs in the list.
- `decode(token_ids)`: converts token IDs back into text.

**Expected output:** The exact token IDs and count are produced by the installed library. The decoded text should match the original text. Do not copy a token count from another tokenizer and assume it will match.

### What if the package is unavailable?
The program will raise `ModuleNotFoundError`. Install it in the same Python environment used to run the script. Do not replace token counting with `len(text.split())`: that counts whitespace-separated pieces, not model tokens.

## 7. Mini-project — LLM Token and Context Window Analyzer

Create `token_analyzer.py`.

```python
import tiktoken

MODEL_ENCODING = "cl100k_base"
CONTEXT_LIMIT = 8000  # Practice value only, not a claim about a real model.

encoding = tiktoken.get_encoding(MODEL_ENCODING)

text = input("Paste text to analyze: ")
token_ids = encoding.encode(text)

token_count = len(token_ids)
remaining = CONTEXT_LIMIT - token_count

print("\n--- Token Analysis ---")
print("Characters:", len(text))
print("Whitespace-separated words:", len(text.split()))
print("Tokens:", token_count)
print("Practice context limit:", CONTEXT_LIMIT)
print("Remaining practice tokens:", remaining)

if remaining < 0:
    print("Warning: text is above the practice limit.")
else:
    print("Text is within the practice limit.")
```

**Sample input**
```text
Paste text to analyze: AI can help summarize documents.
```

**Output format**
```text
--- Token Analysis ---
Characters: [calculated value]
Whitespace-separated words: [calculated value]
Tokens: [calculated by tiktoken]
Practice context limit: 8000
Remaining practice tokens: [calculated value]
Text is within the practice limit.
```

The bracketed values are intentionally calculated at runtime because tokenizer output depends on the exact input and encoding.

### Project improvement tasks
1. Let the user choose a practice context limit.
2. Warn when 80% of the practice limit is used.
3. Print the first ten token IDs.
4. Explain why word count and token count differ.
5. Add a note that real model limits and API usage must be checked for the selected model.

## 8. Common mistakes
- Treating one word as one token.
- Treating a token count from one tokenizer as universal.
- Using Python's `split()` as an exact token counter.
- Assuming the context window contains only the user's latest message.
- Assuming the full context window should be filled for every request.
- Forgetting that generated output also consumes a token budget.

## 9. Practice with answers
1. Is punctuation sometimes a token? **Yes.**
2. Are token IDs words? **No. They are integer vocabulary identifiers.**
3. Does every model use `cl100k_base`? **No.**
4. Why should a long document sometimes be split? **To fit context limits, focus retrieval and control cost.**
5. If text has 100 words, can we say it has exactly 100 tokens? **No.**

## 10. Lesson checkpoint
Students should be able to run the analyzer, explain why its count is tokenizer-specific, and describe what contributes to a model's context. Day 13 uses these foundations to study generation controls.
