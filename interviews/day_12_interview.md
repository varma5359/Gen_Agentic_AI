# Day 12 — Interview Questions and Answers

## Tokens, Tokenization and Context Windows

1. **What is a token?**  
   A token is a unit of text defined by a model's tokenizer. It may be a whole word, part of a word, punctuation or whitespace-associated text.

2. **Is one token always one word?**  
   No. A word can be split into multiple tokens, and some tokens can contain spaces or punctuation.

3. **What is tokenization?**  
   Tokenization converts text into tokens and maps them to numeric token IDs.

4. **Why do language models use token IDs?**  
   Neural networks operate on numerical representations, so text is converted into IDs and then vectors.

5. **What is a tokenizer vocabulary?**  
   It is the collection of token units known to a tokenizer, each associated with an ID.

6. **Do all LLMs use the same tokenizer?**  
   No. Tokenizers and vocabularies can differ between model families.

7. **What is a context window?**  
   It is the model's supported limit for the tokenized information considered during a request or generation step.

8. **What can consume context?**  
   Instructions, user input, conversation history, tool descriptions/results and other supplied context. Output generation also has a token budget and model-specific constraints.

9. **Why does token count matter?**  
   It can affect context limits, latency and API cost.

10. **Is Python's `len(text.split())` an exact token count?**  
    No. It counts whitespace-separated pieces, not model tokens.

11. **What is tiktoken?**  
    It is a Python library that provides tokenization encodings. A chosen encoding is suitable only for models that use or are compatible with it.

12. **Why can two tokenizers count the same text differently?**  
    They can have different vocabularies and token-splitting rules.

13. **Does a larger context window guarantee better answers?**  
    No. It permits more context, but relevance, retrieval quality and model behaviour still matter.

14. **Why chunk a long document?**  
    Chunking helps fit content into limits and makes it easier to retrieve relevant passages.

15. **How should an application estimate token costs?**  
    Use the correct model/provider tokenizer or usage reporting and the provider's current pricing rules. Do not rely on a universal word-to-token ratio.
