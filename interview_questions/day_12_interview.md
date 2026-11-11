# Day 12 Interview Guide — Tokens and Context Windows

## 1. What is a token?
A unit produced by a model tokenizer. It may be a whole word, word fragment, punctuation or another text unit. It is not necessarily one word.

## 2. What is tokenization?
Converting text into token pieces and token IDs that a model can process. The exact tokenisation depends on the tokenizer associated with the model.

## 3. Why do token counts matter?
They affect context capacity, input/output limits, latency and cost. Developers should inspect actual usage and current provider rules.

## 4. What is a context window?
The amount of tokenised information a model can consider in an interaction. Instructions, conversation history, user input, retrieved context and generated output may need to be budgeted according to the API's rules.

## 5. What happens if context capacity is exceeded?
The request may be rejected or require content reduction. Strategies include selecting relevant history, summarising older turns, retrieving fewer passages or reducing output allowance.

## 6. How would you reduce token usage?
Remove irrelevant context, avoid repeated instructions, retrieve relevant passages, summarise old history carefully and set an appropriate output limit. Do not remove safety or essential task context blindly.

## 7. Does tiktoken count tokens for every LLM?
No. It provides encodings for supported model families. Other models may use different tokenizers. Use provider guidance or usage reports.

## 8. Input tokens versus output tokens?
Input tokens are sent to the model; output tokens are generated. Pricing can distinguish cached input and other categories, so inspect current provider definitions.

## 9. Context window versus long-term memory?
Context is information available to a particular model interaction. Long-term memory requires separate storage and retrieval; it is not guaranteed by a large context window.

## 10. Practical interview task
Given 900 instruction tokens, 1,200 history, 500 user input, 2,400 retrieved context and 1,000 output allowance, calculate the total and explain what you would do if capacity were 5,000.
