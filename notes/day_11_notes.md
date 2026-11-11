# Day 11 — AI, ML, Deep Learning, Generative AI, LLM architecture and transformer fundamentals

**Phase 2 | Beginner | 2–3 hours | Project: Generative AI Concept Explorer**

## Learning outcomes
You will distinguish AI, ML, deep learning, GenAI and LLMs; explain a basic transformer flow; identify tokenization, embeddings, attention and generation; and draw the architecture of an LLM-powered application.

## 1. Start with a business problem
A learning platform receives hundreds of questions: explain Python lists, create SQL practice questions, summarise lessons and draft emails. A rule-based program can return answers written in advance, but maintaining a rule for every possible question becomes difficult. A generative model can create a response based on learned patterns and the supplied input. It can also be wrong, so the application must validate and evaluate the result.

**Remember:** An AI model is not a complete product. The product also needs input handling, prompt construction, API integration, validation, security, user interface and monitoring.

## 2. AI, ML, deep learning, GenAI and LLM

| Concept | Meaning | Example |
|---|---|---|
| Artificial Intelligence | Broad field of systems performing tasks associated with intelligent behaviour | Route planning |
| Machine Learning | Methods that learn patterns from data | Fraud prediction |
| Deep Learning | ML using multi-layer neural networks | Image recognition |
| Generative AI | Models that generate new content | Drafting an email |
| Large Language Model | Model trained to process and generate language | Answering a question |

A useful learning map is AI → ML → Deep Learning → many modern GenAI systems → language generation models. This is a simplified map, not a claim that every AI system belongs to one strict nested category. GenAI also includes image, audio and video generation.

**Classification versus generation:** A spam detector chooses a label. A generative system drafts a new reply. Some models can perform both depending on the task.

## 3. What is an LLM?
A Large Language Model is a neural network trained on large amounts of language data. A common training objective is to predict the next token from preceding context.

Example input: “The capital of France is”
The model calculates scores for possible next tokens. Paris may receive a high score. The model is not necessarily looking up a verified fact; it is generating based on learned patterns and supplied context.

A token is not always a complete word. Day 12 explains this.

## 4. Model versus application

| Model does | Application developer does |
|---|---|
| Processes token representations | Collects user input |
| Generates likely output | Builds instructions and context |
| Uses learned parameters | Selects provider/model/settings |
| Returns generated content | Validates, formats, logs and displays |

## 5. Transformer overview
A transformer uses attention mechanisms to let token representations use contextual information from other positions.

~~~text
Text input
   |
Tokenizer
   |
Token IDs
   |
Token embeddings + position information
   |
Transformer blocks
   |-- self-attention
   |-- feed-forward transformations
   |-- normalization and residual pathways
   |
Output scores (logits)
   |
Decoding selects next token
   |
Append token and repeat until stopping
~~~

### Tokenization
The tokenizer converts text into token pieces and integer IDs. A token may be a word, part of a word, punctuation or another unit.

### Embeddings
Token IDs are mapped to learned numerical vectors. These are internal token representations. Do not confuse them with sentence/document embeddings used later for semantic search.

### Position information
The model needs information about token order. Transformer designs include positional information so sequence order can influence processing.

### Self-attention
Self-attention allows each token representation to combine information from other relevant token positions. Query, key and value vectors are used to calculate attention weights. At this stage, understand the purpose rather than memorising matrix equations.

### Feed-forward layers and stacked blocks
Feed-forward transformations process token representations. Multiple blocks build contextual representations.

### Generation
The model produces scores for possible next tokens. A decoding method selects a token, appends it to context and repeats until a stop condition or output limit is reached.

## 6. Training versus prompting
Training adjusts model parameters using data and optimisation. Prompting supplies instructions and context at request time; it does not normally update model weights. Application developers commonly select a model, construct prompts, call an API and validate outputs rather than train a foundation model.

## 7. LLM application flow
~~~text
Student question
   |
Python backend
   |-- system/developer instructions
   |-- conversation context
   |
LLM provider API
   |
Model generates response
   |
Application validates and formats
   |
Student sees answer
~~~

## 8. Python exercise: fixed lookup is not GenAI
~~~python
concepts = {
    "AI": "The broad field of intelligent computer systems.",
    "ML": "Methods that learn patterns from data.",
    "DL": "Machine learning using multi-layer neural networks.",
    "GenAI": "Models that generate new content."
}

for name, meaning in concepts.items():
    print(f"{name}: {meaning}")
~~~
The dictionary stores fixed text. The loop visits each key-value pair. The f-string inserts both values into the output. This program retrieves predefined definitions; it does not generate a new answer using an LLM.

## 9. Industry scenario
A support assistant needs to answer customer questions. The developer builds the request flow, supplies approved policy context, handles API failures, checks output and displays the answer. Later lessons add real model integration, retrieval and security.

## 10. Common misunderstandings
| Mistake | Correction |
|---|---|
| AI and GenAI are identical | GenAI is one area of AI |
| Every AI system is an LLM | AI includes many non-language systems |
| Every LLM answer is verified | Fluent output can be false |
| Token means word | Tokens can be word pieces |
| Prompting retrains the model | Prompting changes request context |
| Transformer means chatbot | Transformer is a neural-network architecture |

## 11. Practice
1. Classify a spam detector and explain why multiple labels may apply.
2. Give one classification example and one generation example.
3. Draw the model/application boundary.
4. Explain tokenizer, embedding and attention in your own words.
5. Why must an LLM response be checked?
6. Explain training versus prompting.

## 12. Five-question quiz
1. Broadest term: A LLM B AI C token D prompt. **Answer B:** AI is the broad field.
2. Generative task: A label spam B sort numbers C draft email D count rows. **Answer C:** it creates content.
3. Text-to-token-ID component: A tokenizer B database C router D compiler. **Answer A.**
4. Self-attention helps: A store passwords B combine contextual information C deploy servers D create tables. **Answer B.**
5. Does prompting normally update model weights? A yes B no. **Answer B:** it changes supplied context.

## 13. Interview questions
- Differentiate AI, ML, deep learning and GenAI with examples.
- What is an LLM and what is next-token prediction?
- Explain the transformer flow from text to generated output.
- Why can an LLM sound confident and still be wrong?
- What responsibilities belong to the application rather than the model?

**Completion check:** Draw and explain the architecture without copying the diagram. Next: tokenisation and context budgeting.
