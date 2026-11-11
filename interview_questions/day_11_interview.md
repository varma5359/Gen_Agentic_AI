# Day 11 Interview Guide — AI, Generative AI, LLMs and Transformers

## 1. What is Artificial Intelligence?
AI is the broad field of building systems that perform tasks associated with intelligent behaviour, such as perception, prediction, planning or language processing. It includes rule-based and learning-based approaches.

## 2. Differentiate AI, ML and deep learning.
AI is the broad field. ML learns patterns from data. Deep learning is ML based on multi-layer neural networks. A fraud classifier using a deep neural network may be described as AI, ML and DL.

## 3. What is Generative AI?
Generative AI refers to models that create new content such as text, images, audio or code. A classifier that only assigns a label is not necessarily generative.

## 4. What is an LLM?
A large language model is a neural network trained on language data to process and generate text. A common training objective is predicting the next token from prior context. This does not guarantee factual correctness.

## 5. What is a transformer?
A neural network architecture built around attention and feed-forward transformations. Transformers process token representations through stacked blocks and are widely used in modern language models.

## 6. Explain self-attention simply.
Self-attention allows a token representation to use information from other token positions. It helps model context and relationships instead of treating each token independently.

## 7. What are token embeddings?
Learned vectors associated with token IDs. The model uses these numerical representations internally. They are distinct from sentence/document embeddings used later for semantic search.

## 8. What is next-token generation?
The model calculates scores for possible next tokens based on context. A decoding method selects a token, appends it to context and repeats until a stopping condition.

## 9. Is an LLM the same as an AI application?
No. An application includes input handling, prompt construction, provider calls, validation, error handling, user interface, security and monitoring.

## 10. Why do LLMs hallucinate?
They generate plausible sequences based on learned patterns and context; they do not automatically verify every claim against a trusted source. Missing context and limitations can produce unsupported statements.

## 11. Does a prompt train the model?
No. Prompting supplies context at inference time. Training changes model parameters through a training process.

## 12. Practical interview task
Draw user input → application → prompt/context → model → generated output → validation → user. Explain one possible failure at every stage.
