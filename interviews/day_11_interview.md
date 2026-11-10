# Day 11 — Interview Questions and Answers

## AI, ML, Deep Learning, GenAI and LLM Fundamentals

1. **What is Artificial Intelligence?**  
   AI is the broad field of building computer systems that perform tasks associated with intelligent behaviour, such as recognizing patterns or understanding language.

2. **What is Machine Learning?**  
   ML is an approach in which a system learns patterns from data instead of relying only on manually written rules.

3. **What is deep learning?**  
   Deep learning is a type of machine learning that uses neural networks with multiple layers.

4. **What is Generative AI?**  
   Generative AI refers to models and systems that create content such as text, images, audio or video.

5. **What is an LLM?**  
   A Large Language Model is a model trained on large amounts of language data to process and generate text.

6. **Is every AI system a generative AI system?**  
   No. A rule-based fraud detector or a classifier can be an AI/ML system without generating new content.

7. **What is a token?**  
   A token is a unit of text processed by a model. It may be a word, part of a word, punctuation or another text unit.

8. **What is an embedding?**  
   An embedding is a numerical vector representation learned for an item such as a token or text. It allows neural networks to process information numerically.

9. **What is attention in a transformer?**  
   Attention allows a position in a sequence to combine information from other positions, helping the model represent relationships between tokens.

10. **What are queries, keys and values?**  
    They are learned vector representations used by attention. Query-key compatibility determines how information from value vectors is combined.

11. **What is the high-level flow of an LLM response?**  
    Text is tokenized, token IDs are converted into representations, transformer layers process context, and the model produces scores used to select output tokens.

12. **Does an LLM retrieve every answer from a database?**  
    No. A basic LLM generates output using learned model parameters and the provided context. Applications can add retrieval systems when external information is needed.

## Practical questions

13. **Why should a developer understand the LLM request flow?**  
    It helps debug token limits, input formatting, latency, output quality and cost.

14. **Can a generative model perform classification?**  
    Yes. It can be prompted to return a category, although output must be evaluated and validated.

15. **What is one misconception about attention?**  
    Attention is not a web search engine; it is a neural-network mechanism for combining information across positions.
