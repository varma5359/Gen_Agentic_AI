# Day 11 — Generative AI Concept Explorer

**Phase:** 2 — Generative AI and LLM Foundations  
**Approved topic:** Artificial Intelligence, Machine Learning, Deep Learning and Generative AI; LLM architecture overview and transformer fundamentals  
**Mini-project:** Generative AI Concept Explorer  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
By the end of this lesson, you can:
- Explain AI, ML, deep learning, generative AI and an LLM in simple language.
- Show how these terms relate to one another.
- Describe the high-level flow from text input to generated text.
- Identify the main jobs of tokens, embeddings, attention and transformer layers.
- Run a small Python concept explorer.

## 2. The big picture

Artificial Intelligence (AI) is the broad field of building computer systems that perform tasks associated with intelligent behaviour.

```text
Artificial Intelligence (AI)
└── Machine Learning (ML)
    └── Deep Learning (DL)
        └── Generative AI (GenAI) — an application area that can use deep learning
            └── Large Language Models (LLMs) — models trained to work with language
```

This diagram is a learning aid, not a strict taxonomy. Generative AI is broader than language models: it can generate text, images, audio, video and other content. Not every AI system is generative, and not every generative model is an LLM.

| Term | Simple meaning | Example |
|---|---|---|
| AI | Computer system performs an intelligent task | A route planner |
| ML | System learns patterns from examples | Predicting house prices |
| Deep learning | ML using multi-layer neural networks | Image recognition |
| Generative AI | Model creates new content | Drafting an email |
| LLM | Large model trained to process and generate language | Answering a question in a chatbot |

### Traditional prediction vs generation
- Prediction/classification: choose or estimate an answer from learned patterns.
- Generation: produce a sequence of new content, such as a paragraph or code.
- A generative model can still perform classification when instructed to choose a label.

**Check your understanding:** Is a spam detector necessarily a generative AI system? No. It may simply classify an email as spam or not spam.

## 3. What is an LLM?

A Large Language Model is a neural network trained on large collections of text (and, for some models, other data) to learn patterns in language. A common training objective is to predict the next token.

Example:
- Given: `The capital of France is`
- A model estimates likely next tokens such as `Paris`.
- It selects a next token according to its decoding method, adds it to the context, and repeats.

It does not mean the model searches a perfect database of facts. Its output is generated from learned patterns and the current input.

## 4. LLM request flow

```text
User text
   ↓
Tokenizer: text → token IDs
   ↓
Embedding layer: token IDs → vectors
   ↓
Transformer blocks: process context and relationships
   ↓
Output layer: scores for possible next tokens
   ↓
Decoding: choose the next token
   ↓
Repeat until stop condition
   ↓
Tokenizer: token IDs → readable text
```

### Important building blocks

| Component | What it does |
|---|---|
| Tokenizer | Splits text into tokens and maps them to numeric IDs |
| Token ID | Integer representing a token in a model vocabulary |
| Embedding | Learned vector representation of a token |
| Positional information | Helps represent token order |
| Attention | Lets a token's representation use information from other positions |
| Transformer block | Repeated neural-network layer containing attention and feed-forward processing |
| Output logits | Scores assigned to possible next tokens before probability conversion |
| Decoding | Selects the next token from the model's scores |

### Transformer fundamentals: attention in plain English

Consider: “Ravi put the book on the table because it was heavy.”

To interpret “it”, a language model needs information from other words. Attention is a mechanism that lets each position combine information from other positions. It does not simply look at the nearest word.

A simplified attention block uses **queries, keys and values**:
- Query: what information is this position looking for?
- Key: what information does another position advertise?
- Value: what information can that position contribute?
- Similarity between queries and keys determines how strongly values contribute.

The real calculation uses learned matrices and vector operations. Students do not need to implement transformer mathematics today; understand the purpose first.

### Why transformers matter
- They process relationships between tokens using attention.
- They can be trained on large datasets.
- The architecture can be scaled and adapted for many language tasks.
- Decoder-style transformer models are commonly used for next-token text generation.

Do not assume every modern AI model is a plain text-only decoder transformer. Model architectures vary.

## 5. A small Python concept explorer

No AI API or paid account is required for this exercise.

```python
concepts = {
    "AI": "The broad field of intelligent computer systems.",
    "ML": "A way for systems to learn patterns from data.",
    "Deep Learning": "Machine learning using multi-layer neural networks.",
    "Generative AI": "AI that creates content such as text, images or audio.",
    "LLM": "A large model trained to process and generate language."
}

for name, meaning in concepts.items():
    print(name + ": " + meaning)
```

**Expected output**
```text
AI: The broad field of intelligent computer systems.
ML: A way for systems to learn patterns from data.
Deep Learning: Machine learning using multi-layer neural networks.
Generative AI: AI that creates content such as text, images or audio.
LLM: A large model trained to process and generate language.
```

**Code explanation**
- `concepts = {...}`: creates a dictionary. Each key is a term and each value is its explanation.
- `.items()`: returns key-value pairs so the loop can read both.
- `for name, meaning in ...`: assigns the current key to `name` and value to `meaning`.
- `print()`: displays text in the terminal.
- `+`: joins the strings. Both sides are strings here.

## 6. Mini-project — Generative AI Concept Explorer

**Requirements**
1. Store at least six AI terms in a dictionary.
2. Display all terms and meanings.
3. Ask the learner to enter one term.
4. Display its meaning, or a friendly “term not found” message.
5. Allow the learner to try more than once.

**Starter solution**
```python
concepts = {
    "AI": "The broad field of intelligent computer systems.",
    "ML": "Systems learn patterns from data.",
    "Deep Learning": "Machine learning based on neural networks.",
    "Generative AI": "AI that creates new content.",
    "LLM": "A model trained to process and generate language.",
    "Transformer": "A neural-network architecture built around attention."
}

while True:
    term = input("Enter a term (or type exit): ").strip()

    if term.lower() == "exit":
        print("Goodbye!")
        break

    meaning = concepts.get(term)
    if meaning is None:
        print("Term not found. Check the spelling.")
    else:
        print(term + ": " + meaning)
```

**Expected interaction**
```text
Enter a term (or type exit): LLM
LLM: A model trained to process and generate language.
Enter a term (or type exit): exit
Goodbye!
```

New methods used:
- `strip()`: removes whitespace at the beginning and end of a string; returns a new string.
- `lower()`: returns a lowercase copy of a string; it does not change the original string.
- `get(key)`: dictionary method. Returns the value for a key, or `None` if the key is missing and no default is supplied.

## 7. Common misconceptions
- **“AI and GenAI mean the same thing.”** GenAI is one area within the wider AI field.
- **“An LLM knows every fact.”** It can produce incorrect or outdated statements.
- **“The model thinks exactly like a human.”** A language model computes outputs from learned numerical patterns; human-like wording is not proof of human understanding.
- **“Attention is a search engine.”** Attention is a neural-network operation over representations in the model's context.
- **“Every AI chatbot uses the same architecture.”** Providers and models can differ.

## 8. Practice
1. Put AI, ML, deep learning and GenAI in a sensible relationship.
2. Explain tokenization to a classmate in one sentence.
3. Name the job of an embedding layer.
4. Why does a model generate one token and then repeat?
5. Give one example of prediction and one of generation.

**Suggested answers**
1. AI is the broad field; ML is one approach within AI; deep learning is a type of ML; GenAI is a content-generating area that often uses deep learning.
2. Tokenization converts text into smaller units called tokens and maps them to IDs.
3. It maps token IDs to learned numerical vectors.
4. Autoregressive generation uses the tokens generated so far as context for predicting the next token.
5. Prediction: classify a support ticket as billing/technical. Generation: draft a reply to the ticket.

## 9. Lesson checkpoint
A learner is ready to move on when they can draw the request flow, explain each block without memorizing jargon, and run the concept explorer. The next lesson explains why text is counted as tokens rather than simply as words.
