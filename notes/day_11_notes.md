# Day 11 — AI, Machine Learning, Deep Learning, Generative AI, LLM Architecture and Transformer Fundamentals

**Phase:** 2 — Generative AI and LLM Foundations  
**Approved syllabus topic:** Artificial Intelligence, Machine Learning, Deep Learning and Generative AI; LLM architecture overview and transformer fundamentals.  
**Approved project:** Generative AI Concept Explorer  
**Audience:** Absolute beginners and learners with 0–1 year of experience.  
**Study time:** 2–3 hours for the core lesson, followed by independent practice.

> **Lesson promise:** You will learn the concepts from the beginning, understand the high-level flow of a language model, distinguish a model from a complete application, and build a small Python program. You do not need to memorise mathematical equations today.

---

## How to study this lesson

1. Study one section at a time.
2. Type every code example into your editor.
3. Predict the output before running the code.
4. Run the code and compare the result with your prediction.
5. If the result differs, trace the code line by line.
6. Complete each exercise before reading its suggested answer.
7. Build the project yourself before looking at the complete example.
8. Explain the concepts aloud in your own words.
9. Do not move forward just because you have finished reading.
10. Move forward when you can explain and demonstrate the learning outcomes.

## Lesson map

| Section | Learning focus |
|---|---|
| 1 | Why GenAI developers need these foundations |
| 2 | Software, programs, models and applications |
| 3 | Artificial Intelligence |
| 4 | Machine Learning |
| 5 | Deep Learning |
| 6 | Generative AI |
| 7 | Large Language Models |
| 8 | Transformer architecture |
| 9 | Tokenization, token IDs and embeddings |
| 10 | Attention and next-token generation |
| 11 | Model versus application architecture |
| 12 | Industry use cases and risks |
| 13 | Python foundations required for the project |
| 14 | Build the concept explorer step by step |
| 15 | Testing and debugging |
| 16 | Exercises and explained answers |
| 17 | MCQs |
| 18 | Interview preparation |
| 19 | Glossary and completion checklist |

---

# 1. Why are we learning this?

Imagine TechPhile.ai wants to add a learning assistant. A student can type:

- Explain Python dictionaries.
- Give me five SQL interview questions.
- Summarise this lesson.
- Create a seven-day study plan.
- Explain why my Python code produces an error.

A normal website can display content written in advance. It can search a database and return a stored record. A generative model can create a response for a particular request.

That does not mean the model is the whole application.

A real product also needs software to receive the request, check the user, prepare instructions, call the model, handle failures, validate the result and display it.

## 1.1 A simple user journey

~~~text
Student types a question
        |
        v
Website receives the question
        |
        v
Python backend validates the request
        |
        v
Application prepares instructions and context
        |
        v
Language model generates a response
        |
        v
Backend checks and formats the response
        |
        v
Website displays the answer
~~~

Read the flow from top to bottom. Each box has a responsibility.

## 1.2 What the developer builds

A GenAI developer may work on:

- The user interface.
- Backend routes and request validation.
- Authentication and authorisation.
- Prompt construction.
- Model-provider integration.
- Conversation storage.
- Retrieval of approved documents.
- Response validation.
- Error handling and retries.
- Logging and monitoring.
- Automated tests.
- Deployment and configuration.

The model is one component in this system.

## 1.3 Learning outcomes

After completing Day 11, you should be able to:

1. Explain what software and an AI application are.
2. Distinguish rule-based software from machine learning.
3. Explain the relationship between AI, ML and deep learning.
4. Define generative AI and give examples.
5. Explain what an LLM does at a high level.
6. Describe the main stages of a transformer-based language model.
7. Explain the purpose of tokenization, embeddings and attention.
8. Describe how next-token generation works.
9. Distinguish a model from a complete AI application.
10. Build and test the Generative AI Concept Explorer.

---

# 2. Software, programs, models and applications

## 2.1 What is software?

Software is a collection of instructions that tells a computer what operations to perform.

Examples:

| Software | What it does |
|---|---|
| Calculator | Performs arithmetic |
| Banking application | Displays account information and records transactions |
| Learning platform | Stores courses and tracks student progress |
| Search application | Finds records matching a query |
| AI assistant | Uses a model to generate or transform content |

## 2.2 Input, processing and output

Most beginner programs can be understood through three stages:

~~~text
INPUT  --->  PROCESSING  --->  OUTPUT
~~~

Example: calculator.

- Input: two numbers.
- Processing: add the numbers.
- Output: display the sum.

Example: support-ticket classifier.

- Input: a customer's message.
- Processing: determine its category.
- Output: Billing, Technical, Account or Other.

The processing may use fixed rules, a trained model, or a combination.

## 2.3 A rule-based program

~~~python
message = "I was charged twice"

if "charged" in message:
    category = "Billing"
else:
    category = "Other"

print(category)
~~~

Expected output:

~~~text
Billing
~~~

Line-by-line explanation:

1. The first line creates a variable named message.
2. The value is a string because it is enclosed in quotation marks.
3. The if keyword begins a conditional decision.
4. The expression checks whether the text charged occurs inside message.
5. The in operator performs a membership check.
6. If the condition is true, the indented statement executes.
7. The assignment stores Billing in category.
8. The else branch is used when the condition is false.
9. The final print statement displays the selected value.

This is a rule-based program because the developer wrote the decision rule.

## 2.4 Why simple rules can fail

Customers may write:

- You took payment twice.
- There are two charges on my card.
- My account was debited two times.
- I see a duplicate transaction.
- Why was I billed again?

A rule that searches only for the exact word charged will not recognise every variation.

A developer could add more rules. A machine-learning model or LLM may help with varied wording, but it introduces different risks and must be evaluated.

## 2.5 Rule-based versus machine learning

| Question | Rule-based program | Machine-learning model |
|---|---|---|
| Where does behaviour come from? | Explicit instructions written by a developer | Patterns learned during training |
| Who writes the decision logic? | Developer writes conditions and rules | Developer chooses data, objective and learning method |
| Can it handle unseen wording? | Only if rules cover it | May generalise, but can still fail |
| Is it always correct? | No | No |
| Can it be tested? | Yes | Yes |
| Does it always need training data? | No | Usually yes |

**Check yourself:** Is a password rule that locks an account after five failed attempts machine learning?

**Answer:** No. It is a fixed rule unless a learning model is actually involved.

---

# 3. Artificial Intelligence

Artificial Intelligence (AI) is a broad field concerned with building systems that perform tasks commonly associated with intelligent behaviour.

Examples include:

- Recognising objects in an image.
- Processing spoken language.
- Recommending products.
- Predicting whether a transaction may be fraudulent.
- Planning a route.
- Detecting unusual activity.
- Generating text.
- Supporting decisions using data.

AI does not mean a computer has human consciousness.

## 3.1 Examples around you

| Feature | AI-related task |
|---|---|
| Email spam filter | Classifies messages |
| Route planner | Searches for a useful route |
| Shopping recommendation | Predicts items a user may prefer |
| Photo grouping | Finds visual similarity |
| Voice assistant | Processes spoken requests |
| Text-generation assistant | Generates language |
| Fraud alert | Detects suspicious patterns |

These features may use different techniques. Do not assume every AI feature uses an LLM.

## 3.2 AI is broader than machine learning

A useful beginner map is:

~~~text
Artificial Intelligence
|
|-- Rule-based systems
|
|-- Search and planning
|
|-- Machine Learning
      |
      |-- Traditional Machine Learning
      |
      |-- Deep Learning
             |
             |-- Many modern Generative AI models
                    |
                    |-- Large Language Models
~~~

This is a learning map, not a perfect mathematical taxonomy. Research areas overlap. Generative AI also includes image, audio and video generation.

## 3.3 Does every AI system learn?

No.

A rule-based system can perform a task associated with intelligent behaviour without learning from examples.

Examples:

- If temperature is above a threshold, switch on a fan.
- If a password is wrong five times, temporarily lock the account.
- If stock is below a configured level, show a warning.

These rules do not learn automatically.

## 3.4 Common misunderstandings

**Misunderstanding:** Every AI system learns automatically.

**Correction:** Some AI systems use fixed rules. A trained model learns patterns during training, but it does not necessarily update itself whenever a user interacts with it.

**Misunderstanding:** AI always gives the correct answer.

**Correction:** AI systems can make mistakes, use incomplete information or fail on unfamiliar inputs.

**Misunderstanding:** AI and ChatGPT are the same thing.

**Correction:** AI is a broad field. ChatGPT is a product that uses AI models and application infrastructure.

**Misunderstanding:** An AI model is a complete AI application.

**Correction:** The model is one component. The application includes software around it.

---

# 4. Machine Learning

Machine Learning (ML) is an area of AI in which a system learns patterns from data and uses those patterns to make predictions or decisions.

In a rule-based program, a developer writes the decision conditions directly.

In a machine-learning workflow, developers provide training data and select a learning method. The training algorithm adjusts model parameters to reduce an error measure.

## 4.1 Example: house-price prediction

Suppose a dataset contains:

| House size (square feet) | Bedrooms | Sale price |
|---:|---:|---:|
| 800 | 2 | 40 lakh |
| 1,000 | 2 | 50 lakh |
| 1,200 | 3 | 62 lakh |
| 1,500 | 3 | 75 lakh |
| 1,800 | 4 | 92 lakh |

A model can learn relationships between the input features and target price.

- Features: house size and number of bedrooms.
- Target: sale price.
- Training data: examples used to fit the model.
- Prediction: estimated price for a new house.

The developer does not need to write a separate exact price rule for every possible house.

## 4.2 Basic ML workflow

~~~text
Collect data
    |
    v
Understand and clean data
    |
    v
Choose useful features
    |
    v
Prepare training and evaluation data
    |
    v
Train a model
    |
    v
Evaluate predictions
    |
    v
Improve or select the model
    |
    v
Use the model for predictions
    |
    v
Monitor performance
~~~

This is a simplified workflow. Real projects also need to consider data leakage, fairness, validation, deployment and monitoring.

## 4.3 What does learning mean?

A model contains parameters: numerical values adjusted during training.

A simplified training cycle:

1. The model receives examples.
2. It produces predictions.
3. The predictions are compared with target values or a training objective.
4. A loss value measures the error.
5. An optimiser updates model parameters.
6. The process repeats across examples.

The parameters change during training. They are not normally changed just because a user writes a prompt.

## 4.4 Types of machine learning

| Type | Learning signal | Example |
|---|---|---|
| Supervised learning | Examples include target labels or values | Spam classification |
| Unsupervised learning | Finds structure without supplied target labels | Customer clustering |
| Reinforcement learning | Learns from rewards or penalties | Game-playing agent |

### Supervised learning

Training examples contain the expected answer.

| Email text | Label |
|---|---|
| Claim your free prize | Spam |
| Meeting at 10 AM | Not spam |
| Verify your account now | Spam |

The model learns patterns that may help classify new emails.

### Unsupervised learning

The data does not contain a target label for every row. An algorithm may group similar records.

Example: a retailer groups customers by purchase behaviour to explore customer segments.

### Reinforcement learning

An agent takes actions in an environment and receives feedback as rewards or penalties.

Example: a simulated robot tries movements and receives a reward for reaching a target.

## 4.5 Industry examples

- Banking: fraud-risk prediction.
- Retail: demand forecasting.
- Healthcare: assisting image analysis under clinical oversight.
- Manufacturing: predictive maintenance.
- Telecom: churn-risk prediction.
- Logistics: delivery-time estimation.
- Education: identifying topics where learners need support.

The output must be interpreted according to the model's limitations and the risk of the decision.

---

# 5. Deep Learning

Deep Learning is a subfield of machine learning that uses neural networks with multiple processing layers.

A neural network is a mathematical model made of connected computational units. During training, its parameters are adjusted so that it can learn useful representations from examples.

## 5.1 Why is it called deep?

The word deep refers to multiple layers of computation between input and output.

~~~text
Input data
   |
   v
Input representation
   |
   v
Hidden layer 1
   |
   v
Hidden layer 2
   |
   v
Hidden layer 3
   |
   v
Output
~~~

This is simplified. Real networks may contain many more layers and different structures.

## 5.2 Example: recognising a cat

A deep-learning image model may learn useful visual patterns.

At a high level:

1. The input image is represented numerically.
2. Early layers can learn simple visual patterns.
3. Deeper layers can combine patterns into more complex representations.
4. The output layer produces scores for possible classes.
5. A prediction method reports a class or score.

A developer does not normally write a separate rule for every possible pose, lighting condition and background.

## 5.3 Neural-network vocabulary

| Term | Beginner explanation |
|---|---|
| Neuron or unit | A computation that receives values and produces a value |
| Layer | A stage of computations |
| Weight | A learned parameter controlling a connection's contribution |
| Bias | A learned parameter added to a computation |
| Activation function | A function that introduces non-linearity |
| Loss | A measure of model error for a training objective |
| Optimiser | A method used to update model parameters |
| Epoch | One pass through a training dataset |
| Batch | A subset of training examples processed together |

## 5.4 Traditional ML and deep learning

| Aspect | Many traditional ML workflows | Deep-learning workflows |
|---|---|---|
| Feature preparation | Often requires substantial manual feature engineering | Can learn representations from raw or lightly processed data |
| Data needs | Can work well with smaller structured datasets for some tasks | Often benefits from large datasets |
| Compute | Can be relatively modest | Can require substantial compute |
| Interpretability | Depends on the model | Often more difficult to interpret |
| Examples | Decision trees, linear models, gradient boosting | CNNs, transformers and other neural networks |

These are tendencies, not universal rules.

---

# 6. Generative AI

Generative AI refers to AI systems that generate new content based on patterns learned during training and the context supplied at use time.

Generated content may include:

- Text.
- Source code.
- Images.
- Audio.
- Music.
- Video.
- Structured data.
- Three-dimensional content.

## 6.1 Classification and generation

A classification task often predicts a label or category.

A generation task produces content.

| Request | Task |
|---|---|
| Is this email spam? | Classification |
| Write a reply to this email | Generation |
| Which category is this ticket? | Classification |
| Summarise this report | Generation |
| Is this transaction suspicious? | Classification or risk scoring |
| Create three practice questions | Generation |

A model may support more than one task. The distinction is about the task, not merely the model brand.

## 6.2 Business example

Customer message:

~~~text
I paid for the subscription, but my account still says unpaid.
Please help me.
~~~

A classification system may return:

~~~text
Billing
~~~

A generative system may draft:

~~~text
Thank you for contacting us. I understand that your payment
was completed but your account still shows an unpaid status.
Please share the transaction reference through our secure
support channel so the team can investigate.
~~~

This is only a draft. The application must not claim that a payment was verified unless a trusted payment system confirms it.

## 6.3 Generative AI is not automatically factual

A model may produce fluent but incorrect content.

For example, a student asks for a Python method that does not exist. The model may produce a plausible-looking method name.

Risk-reduction techniques include:

- Supplying trusted documentation.
- Asking for evidence or source references.
- Validating structured outputs.
- Running generated code in a safe test environment.
- Using deterministic calculations for arithmetic.
- Requiring human review for sensitive decisions.
- Monitoring failures and collecting evaluation examples.

No single prompt or setting guarantees that a model will never make a mistake.

---

# 7. Large Language Models

A Large Language Model (LLM) is a neural network trained to process and generate language. Modern LLMs commonly use transformer-based architectures.

A common training objective is to predict the next token based on preceding context.

Example:

~~~text
Context:
"The capital of France is"

Possible next token:
"Paris"
~~~

The model calculates scores for possible next tokens. A decoding procedure selects a token. The selected token is added to the context, and generation continues.

This is a simplified explanation. Actual models may use more complex training objectives, message formats, tools and multimodal inputs.

## 7.1 What does large mean?

The word large can refer to aspects such as:

- A large number of learned parameters.
- Large training datasets.
- Significant training compute.
- Broad learned language patterns.

There is no single universal parameter count that defines every LLM.

## 7.2 What can an LLM do?

Depending on the model and application, an LLM can:

- Explain concepts.
- Draft text.
- Summarise documents.
- Translate text.
- Extract information.
- Classify messages.
- Generate code.
- Answer questions using supplied context.
- Convert information into a requested structure.
- Help plan multi-step work.

These are capabilities, not guarantees. Quality varies with task, model, prompt, context and evaluation.

## 7.3 What should you not assume?

Do not assume an LLM:

- Knows every current fact.
- Has internet access.
- Can see a user's database.
- Remembers every past conversation.
- Executes code simply because it generated code.
- Has permission to call an external API.
- Verifies every source it mentions.
- Knows a company's private policy.
- Always follows every instruction.
- Produces identical output every time.

The application must explicitly provide permitted data, tools and permissions.

## 7.4 Model knowledge versus application data

Suppose TechPhile.ai has a private course database.

A base model does not automatically know:

- Which course a student purchased.
- Which lesson a student completed.
- The latest private exam questions.
- The student's account status.
- The institute's internal refund policy.

The application must retrieve permitted data and supply relevant context or use authorised tools.

This leads to later lessons on APIs, embeddings, vector databases and RAG.

---

# 8. Transformer fundamentals

The transformer is a neural-network architecture that became central to modern language models.

You do not need to implement a transformer from scratch today. You need to understand the main components and their responsibilities.

## 8.1 High-level flow

~~~text
Text input
   |
   v
Tokenization
   |
   v
Token IDs
   |
   v
Token embeddings
   |
   v
Position information
   |
   v
Transformer blocks
   |
   +--> Attention
   |
   +--> Feed-forward network
   |
   v
Output scores for possible next tokens
   |
   v
Decoding and token selection
   |
   v
Generated token sequence
~~~

This is a teaching diagram. Implementations differ in details, and modern architectures may use variations.

## 8.2 Step 1 — Text input

A user types:

~~~text
Explain machine learning in simple words.
~~~

The application sends the text in a request format supported by the model provider.

The model does not simply process the visible characters exactly as a human sees them. Text is converted into token IDs.

## 8.3 Step 2 — Tokenization

Tokenization divides text into units defined by a tokenizer.

A token might represent:

- A complete common word.
- A word fragment.
- Punctuation.
- Whitespace or a text boundary.
- Another unit defined by the tokenizer.

A token is not necessarily one word.

Day 12 studies tokenization and token counting in detail.

## 8.4 Step 3 — Token IDs

A tokenizer maps token pieces to integer identifiers.

Illustrative example only:

| Token piece | Example ID |
|---|---:|
| Explain | 1201 |
| machine | 845 |
| learning | 2207 |
| . | 13 |

These IDs are invented for teaching. They are not actual IDs from a production tokenizer.

The model uses numerical IDs as part of its input representation.

## 8.5 Step 4 — Embeddings

An embedding layer maps token IDs to vectors: lists of numbers.

Illustrative example:

~~~text
Token ID: 1201

Embedding:
[0.12, -0.08, 0.44, 0.31, ...]
~~~

Real vectors may have many dimensions. These small values are only an illustration.

An embedding gives the neural network a numerical representation it can process.

**Two uses of the word embedding:**

1. Token embeddings inside a language model are part of the model's input representation.
2. Sentence or document embeddings used in semantic search represent larger text units for similarity retrieval.

Day 21 studies application embeddings in detail.

## 8.6 Step 5 — Position information

Word order matters.

Compare:

- The dog chased the cat.
- The cat chased the dog.

The same words appear, but their order changes the meaning.

A transformer needs information about token positions or sequence order. Implementations use different positional approaches.

Remember:

- Token identity alone is not enough.
- Position information helps represent order.
- The model uses relationships among tokens in context.

## 8.7 Step 6 — Attention

Attention allows a token representation to incorporate information from other token positions.

Consider:

~~~text
The student placed the book on the table because it was heavy.
~~~

A reader uses context to infer what it refers to. Attention mechanisms provide a way for token representations to use information from other positions.

This is an intuition. Actual attention computes numerical relationships between vectors.

### Query, key and value

Attention is commonly described using three projections:

- Query: what information this position is looking for.
- Key: what information a position offers for matching.
- Value: information that can be combined.

Simplified operation:

1. Token representations are transformed into query, key and value vectors.
2. A query is compared with keys from available positions.
3. Comparisons produce attention scores.
4. Scores are normalised into weights.
5. Values are combined using those weights.
6. The resulting representation contains contextual information.

Do not interpret query, key and value as literal English questions or database keys. They are mathematical vectors.

### Self-attention

It is called self-attention because the operation relates positions within the same input sequence or representation stream.

### Multi-head attention

A transformer can use multiple attention heads.

At a high level:

- Different heads can learn different attention patterns.
- Their outputs are combined.
- The model can represent several kinds of relationships.
- The exact interpretation of a head is not always simple or human-readable.

### Causal masking

Many decoder-only language models use a causal attention mask so a position cannot attend to future tokens during next-token prediction.

When predicting token 3, the model can use earlier available positions, but not token 4 that has not yet been generated.

This supports left-to-right generation.

## 8.8 Step 7 — Feed-forward network

Transformer blocks also contain feed-forward computations.

At a high level:

- Attention mixes information across positions.
- The feed-forward network transforms the representation at each position.
- Residual connections and normalisation are commonly used.
- Multiple blocks are stacked to build deeper representations.

This is an overview, not a complete architecture specification.

## 8.9 Step 8 — Output scores

After processing the context, a language model produces scores over possible next tokens.

These scores are often called logits before conversion into probabilities.

Illustrative values:

| Candidate token | Illustrative probability |
|---|---:|
| AI | 0.52 |
| machine | 0.25 |
| software | 0.13 |
| data | 0.10 |

These values are invented only to explain the idea.

The model does not necessarily select the highest-probability token every time. Decoding and generation settings influence selection.

## 8.10 Step 9 — Generate the next token

The decoding procedure selects a token according to the configured strategy.

The selected token is appended to the context.

The model predicts another token.

This repeats until a stopping condition is reached, such as:

- An end-of-sequence token.
- A provider-defined stop sequence.
- An output-token limit.
- A request cancellation.
- Another API or runtime condition.

## 8.11 Step 10 — Convert tokens into text

The tokenizer maps generated token IDs back into text pieces.

The application receives the response in the provider's format and displays or processes it.

## 8.12 Generation trace

~~~text
Prompt:
"Python is a"

Possible generated sequence:
" programming language"

Updated context:
"Python is a programming language"

Possible next sequence:
" used for"

Updated context:
"Python is a programming language used for"

Possible next sequence:
" data analysis"

Illustrative final response:
"Python is a programming language used for data analysis."
~~~

This trace is illustrative. Actual generation may differ, and token boundaries may split displayed words.

---

# 9. Model versus AI application architecture

A real GenAI product is a software system.

## 9.1 Basic architecture

~~~text
+---------------------+
| Web or Mobile UI    |
+----------+----------+
           |
           v
+---------------------+
| Python Backend      |
| Authentication      |
| Validation          |
| Business rules      |
+----------+----------+
           |
           v
+---------------------+
| Prompt Builder      |
| Instructions        |
| User request        |
| Permitted context   |
+----------+----------+
           |
           v
+---------------------+
| LLM Provider API    |
+----------+----------+
           |
           v
+---------------------+
| Response Validation |
| Format checks       |
| Error handling      |
+----------+----------+
           |
           v
+---------------------+
| UI / Client         |
+---------------------+
~~~

## 9.2 Responsibility by layer

| Layer | Responsibility | Possible failure |
|---|---|---|
| UI | Collect and show information | Empty question |
| Backend | Validate and coordinate | Server exception |
| Prompt builder | Construct model input | Missing context |
| Provider integration | Communicate with model | Timeout or rate limit |
| Model | Generate output | Unsupported claim |
| Validator | Check response shape | Missing required field |
| Database | Store permitted data | Connection failure |
| Monitoring | Observe behaviour | Failure not detected |

## 9.3 Why this matters

The model may return a valid paragraph while the user is not authenticated. The backend must still enforce access control.

The model may return invalid JSON. The application must detect it instead of assuming it is safe.

The provider may be unavailable. The application should return a useful error or designed fallback rather than exposing a raw stack trace.

Treat model output as untrusted input before using it for important operations.

---

# 10. Industry applications

## 10.1 Education

Possible features:

- Explain a lesson at different difficulty levels.
- Generate practice questions.
- Summarise course material.
- Provide hints for coding exercises.
- Help interpret an error message.

Risks:

- Incorrect explanations.
- Invented references.
- Giving away an answer when the goal is practice.
- Exposing another student's private information.

Controls:

- Use approved course material as context.
- Evaluate explanations against reference answers.
- Separate hints from full solutions.
- Enforce student access checks in backend code.

## 10.2 Customer support

Possible features:

- Draft replies.
- Summarise a conversation.
- Classify a ticket.
- Retrieve relevant policy passages.

Risks:

- Inventing refund promises.
- Misclassifying urgent cases.
- Exposing another customer's data.
- Sending an unreviewed response.

Controls:

- Retrieve current approved policy.
- Validate ticket permissions.
- Require human approval for sensitive actions.
- Keep an audit trail.

## 10.3 Software development

Possible features:

- Explain code.
- Draft tests.
- Suggest refactoring.
- Summarise logs.
- Generate documentation.

Risks:

- Invented APIs.
- Insecure code.
- Incorrect assumptions about a project.
- Tests that do not check the actual requirement.

Controls:

- Run tests.
- Review dependencies.
- Inspect generated changes.
- Use static analysis and code review.
- Never execute arbitrary generated code in a privileged environment.

## 10.4 Business operations

Possible features:

- Extract fields from documents.
- Summarise reports.
- Draft meeting notes.
- Convert natural-language requests into structured data.

Risks:

- Incorrect extracted values.
- Omitted caveats.
- Unsupported claims.
- Misuse of confidential data.

Controls:

- Schema validation.
- Source references.
- Human review for consequential records.
- Data minimisation.

---

# 11. Python foundations for the project

The mini-project is a normal Python program. It does not call an LLM. It teaches the programming concepts needed to build later AI applications.

## 11.1 What is Python?

Python is a general-purpose programming language used for scripting, backend development, data work, automation and AI applications.

Python files commonly use the .py extension.

Example filename: main.py

## 11.2 Check the Python installation

Open a terminal in your project folder.

~~~bash
python --version
~~~

If Windows uses the Python launcher:

~~~bash
py --version
~~~

On some Linux systems:

~~~bash
python3 --version
~~~

If the command is not found, check the installation and PATH configuration. Do not assume the program itself is wrong.

## 11.3 Create and run a file

Create a file named main.py.

Write:

~~~python
print("Welcome to GenAI learning")
~~~

Run:

~~~bash
python main.py
~~~

Or, where required:

~~~bash
python3 main.py
~~~

Expected output:

~~~text
Welcome to GenAI learning
~~~

## 11.4 print()

print() displays values in the terminal.

~~~python
print("Hello")
print(25)
print(10 + 5)
~~~

Output:

~~~text
Hello
25
15
~~~

Explanation:

- print is a built-in Python function.
- Parentheses contain the value or expression to display.
- Quotation marks indicate a string literal.
- 10 + 5 is an arithmetic expression.
- Python evaluates the expression before displaying the result.

## 11.5 Comments

Comments explain code to people. Python ignores comments during normal execution.

~~~python
# Display the course title
print("TechPhile GenAI")
~~~

A comment begins with #.

A useful comment explains why a non-obvious decision exists. Avoid comments that merely repeat the next line.

## 11.6 Variables

A variable is a name that refers to a value.

~~~python
course_name = "Generative AI"
duration_days = 5
is_beginner_course = True
~~~

Explanation:

- course_name is a variable name.
- The equals sign assigns a value.
- The text in quotation marks is a string.
- duration_days refers to an integer.
- is_beginner_course refers to a Boolean.
- Python determines the type at runtime.

Use descriptive names.

Good:

~~~python
student_question = "What is an LLM?"
~~~

Less clear:

~~~python
x = "What is an LLM?"
~~~

## 11.7 Basic data types

| Type | Example | Meaning |
|---|---|---|
| str | "Python" | Text |
| int | 10 | Whole number |
| float | 3.14 | Decimal number |
| bool | True | True or false |
| NoneType | None | Absence of a value |

Check a value's type:

~~~python
course_name = "GenAI"
print(type(course_name))
~~~

Expected output:

~~~text
<class 'str'>
~~~

type() returns the type of a value. print() displays it.

## 11.8 User input

~~~python
student_name = input("Enter your name: ")
print("Welcome", student_name)
~~~

Possible interaction:

~~~text
Enter your name: Anu
Welcome Anu
~~~

input() pauses and waits for text. It returns a string.

Even if the user types 25, the returned value is initially the text "25".

Convert numeric input when calculation is required:

~~~python
age_text = input("Enter your age: ")
age = int(age_text)
print(age + 1)
~~~

If the user enters 20, output is 21.

If the user enters twenty, int() raises ValueError. Later we will handle this safely.

## 11.9 Conditional statements

A condition allows the program to choose a path.

~~~python
choice = 1

if choice == 1:
    print("Artificial Intelligence")
else:
    print("Unknown choice")
~~~

Output:

~~~text
Artificial Intelligence
~~~

Explanation:

- if begins a conditional block.
- choice == 1 compares two values.
- == means equality comparison.
- A single equals sign assigns a value.
- The indented line runs when the condition is true.
- else runs when the condition is false.

Use elif for additional choices:

~~~python
choice = 3

if choice == 1:
    print("AI")
elif choice == 2:
    print("Machine Learning")
elif choice == 3:
    print("Deep Learning")
else:
    print("Unknown choice")
~~~

Output:

~~~text
Deep Learning
~~~

## 11.10 Lists

A list stores an ordered collection of values.

~~~python
topics = ["AI", "Machine Learning", "Deep Learning"]
print(topics[0])
print(topics[1])
print(len(topics))
~~~

Output:

~~~text
AI
Machine Learning
3
~~~

Important:

- Square brackets create a list.
- Items are separated by commas.
- Indexing starts at zero.
- topics[0] accesses the first item.
- len() returns the number of items.

## 11.11 Dictionaries

A dictionary stores key-value pairs.

~~~python
concept = {
    "name": "Generative AI",
    "example": "Drafting a response",
    "type": "AI field"
}

print(concept["name"])
print(concept["example"])
~~~

Output:

~~~text
Generative AI
Drafting a response
~~~

A dictionary is useful when values have named meanings. We do not need to remember that index zero means name and index one means example.

## 11.12 Functions

A function groups reusable instructions.

~~~python
def greet_student():
    print("Welcome to TechPhile")

greet_student()
~~~

Output:

~~~text
Welcome to TechPhile
~~~

Explanation:

- def begins a function definition.
- greet_student is the function name.
- Parentheses contain optional parameters.
- The indented block is the function body.
- Defining a function does not execute it.
- Calling greet_student() executes it.

## 11.13 Loops

A for loop repeats instructions for each item.

~~~python
for topic in ["AI", "ML", "GenAI"]:
    print(topic)
~~~

Output:

~~~text
AI
ML
GenAI
~~~

A while loop repeats while a condition remains true.

~~~python
count = 1

while count <= 3:
    print(count)
    count = count + 1
~~~

Output:

~~~text
1
2
3
~~~

The update is important. Without it, the condition may remain true forever.

## 11.14 Exceptions

An exception is an event that interrupts normal program execution.

~~~python
try:
    number = int("hello")
except ValueError:
    print("Please provide a valid whole number.")
~~~

Output:

~~~text
Please provide a valid whole number.
~~~

The try block contains code that may fail. The except block handles the specified error.

Catch errors you understand. Do not use a broad exception handler to hide every programming mistake.

---

# 12. Guided project — Generative AI Concept Explorer

## 12.1 What are we building?

Create a command-line program that teaches five concepts:

1. Artificial Intelligence.
2. Machine Learning.
3. Deep Learning.
4. Generative AI.
5. Large Language Models.

The learner chooses a number. The program displays the concept name, a simple definition, a practical example and its relationship to AI.

The menu repeats until the learner chooses Exit.

## 12.2 What this project is not

This project is not an LLM.

- It does not generate new answers.
- It does not train a model.
- It does not call an API.
- It displays information written by the developer.

That is intentional. Learn normal application logic before connecting a model.

## 12.3 Project requirements

- Display a welcome heading.
- Display a numbered menu.
- Accept a choice.
- Show the selected concept.
- Repeat the menu.
- Exit cleanly.
- Handle invalid numbers.
- Handle non-numeric input.
- Keep the code readable.
- Separate menu display and concept display into functions.

## 12.4 Project folder

~~~text
day11_concept_explorer/
    main.py
    README.md
~~~

main.py contains the Python program. README.md explains what the project does and how to run it.

## 12.5 Step 1 — Store concept information

~~~python
concepts = {
    1: {
        "name": "Artificial Intelligence",
        "meaning": "The broad field of building systems that perform tasks associated with intelligent behaviour.",
        "example": "A route-planning system.",
        "relationship": "AI is the broad field."
    },
    2: {
        "name": "Machine Learning",
        "meaning": "A way to learn patterns from data and use them to make predictions or decisions.",
        "example": "Predicting whether a transaction may be fraudulent.",
        "relationship": "Machine Learning is one area within AI."
    },
    3: {
        "name": "Deep Learning",
        "meaning": "Machine Learning that uses neural networks with multiple processing layers.",
        "example": "Recognising objects in images.",
        "relationship": "Deep Learning is a subfield of Machine Learning."
    },
    4: {
        "name": "Generative AI",
        "meaning": "AI systems that generate content such as text, images, audio or code.",
        "example": "Drafting a customer support response.",
        "relationship": "Generative AI is an area of AI; many modern systems use deep learning."
    },
    5: {
        "name": "Large Language Model",
        "meaning": "A neural network trained to process and generate language.",
        "example": "Explaining a Python concept in natural language.",
        "relationship": "An LLM is a type of language model used in many GenAI applications."
    }
}
~~~

### Understand the nested dictionary

- concepts is a variable.
- The outer braces create a dictionary.
- 1, 2, 3, 4 and 5 are keys.
- Each key maps to another dictionary.
- The inner dictionaries store named information.
- name is a key in the inner dictionary.
- Artificial Intelligence is its value.
- A comma separates dictionary entries.
- Strings are enclosed in matching quotation marks.
- Indentation makes the nested structure easier to read.

Why use a dictionary of dictionaries?

The outer dictionary finds a concept using its menu number. The inner dictionary retrieves a field by its name.

~~~python
print(concepts[4]["name"])
~~~

Output:

~~~text
Generative AI
~~~

Read the lookup from left to right:

1. concepts refers to the outer dictionary.
2. [4] selects the entry whose key is 4.
3. ["name"] selects the name field.
4. print() displays the resulting string.

## 12.6 Step 2 — Create the menu function

~~~python
def show_menu():
    print()
    print("=" * 40)
    print("GENAI CONCEPT EXPLORER")
    print("=" * 40)
    print("1. Artificial Intelligence")
    print("2. Machine Learning")
    print("3. Deep Learning")
    print("4. Generative AI")
    print("5. Large Language Model")
    print("0. Exit")
~~~

Explanation:

- def defines a function.
- show_menu is a descriptive function name.
- Empty parentheses mean no argument is required.
- The colon begins the function body.
- The indented statements belong to the function.
- print() with no argument prints a blank line.
- The multiplication operator repeats the equals sign 40 times.
- The labels tell the user which choices are available.
- Defining the function does not display the menu.
- The function must be called later.

Call the function:

~~~python
show_menu()
~~~

Expected output:

~~~text
========================================
GENAI CONCEPT EXPLORER
========================================
1. Artificial Intelligence
2. Machine Learning
3. Deep Learning
4. Generative AI
5. Large Language Model
0. Exit
~~~

## 12.7 Step 3 — Create the concept display function

~~~python
def show_concept(concept):
    print()
    print("-" * 40)
    print(concept["name"])
    print("-" * 40)
    print("Meaning:", concept["meaning"])
    print("Example:", concept["example"])
    print("Relationship:", concept["relationship"])
~~~

The function receives one dictionary through the parameter named concept.

When it is called with concepts[4], the parameter refers to the Generative AI dictionary.

- concept["name"] retrieves the name.
- concept["meaning"] retrieves the definition.
- concept["example"] retrieves the example.
- concept["relationship"] retrieves the relationship.

The function does not need to know which menu number was selected. It only needs the dictionary it receives.

## 12.8 Step 4 — Build the main loop

~~~python
while True:
    show_menu()
    choice_text = input("Choose a concept: ")
~~~

Explanation:

- while starts a loop.
- True is a Boolean value.
- while True repeats until the program exits or breaks out.
- show_menu() displays the menu on each iteration.
- input() waits for the user's response.
- choice_text stores the response as text.

At this point choice_text is a string. It may contain "4", "0" or "hello".

## 12.9 Step 5 — Convert the choice safely

~~~python
    try:
        choice = int(choice_text)
    except ValueError:
        print("Please enter a number from 0 to 5.")
        continue
~~~

Explanation:

- try begins a block that may raise an exception.
- int() attempts to convert the text into an integer.
- "4" can become 4.
- "hello" cannot become an integer.
- ValueError is raised for an unsuitable value.
- except ValueError handles that specific error.
- continue skips the remaining statements in the current iteration.
- The loop starts again and displays the menu.

This is better than allowing an expected typing mistake to crash the application.

## 12.10 Step 6 — Handle the exit choice

~~~python
    if choice == 0:
        print("Thank you for learning GenAI concepts!")
        break
~~~

- if checks a condition.
- choice == 0 compares the value with zero.
- == means equality comparison.
- print() displays the exit message.
- break exits the nearest loop.

## 12.11 Step 7 — Find and display the concept

~~~python
    concept = concepts.get(choice)

    if concept is None:
        print("Invalid choice. Please select a number from 0 to 5.")
        continue

    show_concept(concept)
~~~

Explanation:

- get(choice) searches the dictionary for the supplied key.
- If the key exists, get() returns its value.
- If the key does not exist, get() returns None by default.
- is None checks for the special None value.
- Invalid selections display a friendly message.
- continue returns to the start of the loop.
- A valid dictionary is passed to show_concept().

Using get() avoids a KeyError for a missing key.

## 12.12 Complete working program

~~~python
concepts = {
    1: {
        "name": "Artificial Intelligence",
        "meaning": "The broad field of building systems that perform tasks associated with intelligent behaviour.",
        "example": "A route-planning system.",
        "relationship": "AI is the broad field."
    },
    2: {
        "name": "Machine Learning",
        "meaning": "A way to learn patterns from data and use them to make predictions or decisions.",
        "example": "Predicting whether a transaction may be fraudulent.",
        "relationship": "Machine Learning is one area within AI."
    },
    3: {
        "name": "Deep Learning",
        "meaning": "Machine Learning that uses neural networks with multiple processing layers.",
        "example": "Recognising objects in images.",
        "relationship": "Deep Learning is a subfield of Machine Learning."
    },
    4: {
        "name": "Generative AI",
        "meaning": "AI systems that generate content such as text, images, audio or code.",
        "example": "Drafting a customer support response.",
        "relationship": "Generative AI is an area of AI; many modern systems use deep learning."
    },
    5: {
        "name": "Large Language Model",
        "meaning": "A neural network trained to process and generate language.",
        "example": "Explaining a Python concept in natural language.",
        "relationship": "An LLM is a type of language model used in many GenAI applications."
    }
}


def show_menu():
    print()
    print("=" * 40)
    print("GENAI CONCEPT EXPLORER")
    print("=" * 40)
    print("1. Artificial Intelligence")
    print("2. Machine Learning")
    print("3. Deep Learning")
    print("4. Generative AI")
    print("5. Large Language Model")
    print("0. Exit")


def show_concept(concept):
    print()
    print("-" * 40)
    print(concept["name"])
    print("-" * 40)
    print("Meaning:", concept["meaning"])
    print("Example:", concept["example"])
    print("Relationship:", concept["relationship"])


while True:
    show_menu()
    choice_text = input("Choose a concept: ")

    try:
        choice = int(choice_text)
    except ValueError:
        print("Please enter a number from 0 to 5.")
        continue

    if choice == 0:
        print("Thank you for learning GenAI concepts!")
        break

    concept = concepts.get(choice)

    if concept is None:
        print("Invalid choice. Please select a number from 0 to 5.")
        continue

    show_concept(concept)
~~~

## 12.13 Sample execution

~~~text
========================================
GENAI CONCEPT EXPLORER
========================================
1. Artificial Intelligence
2. Machine Learning
3. Deep Learning
4. Generative AI
5. Large Language Model
0. Exit
Choose a concept: 4

----------------------------------------
Generative AI
----------------------------------------
Meaning: AI systems that generate content such as text, images, audio or code.
Example: Drafting a customer support response.
Relationship: Generative AI is an area of AI; many modern systems use deep learning.
~~~

The menu appears again after the concept is displayed.

If the learner enters 0, the program exits.

## 12.14 Invalid input behaviour

Input:

~~~text
Choose a concept: hello
~~~

Expected behaviour:

~~~text
Please enter a number from 0 to 5.
~~~

Input:

~~~text
Choose a concept: 9
~~~

Expected behaviour:

~~~text
Invalid choice. Please select a number from 0 to 5.
~~~

The program should not show a traceback for these expected user mistakes.

---

# 13. Testing and debugging

Testing checks whether the program behaves according to its requirements. Do not test only the successful path.

## 13.1 Test cases

| Test ID | Input | Expected result | Reason |
|---|---|---|---|
| TC01 | 1 | AI details appear | First valid option |
| TC02 | 2 | ML details appear | Second valid option |
| TC03 | 3 | Deep Learning details appear | Middle option |
| TC04 | 4 | GenAI details appear | GenAI option |
| TC05 | 5 | LLM details appear | Last valid option |
| TC06 | 0 | Friendly exit | Loop termination |
| TC07 | 9 | Invalid-choice message | Unknown number |
| TC08 | hello | Friendly input error | Non-numeric value |
| TC09 | blank input | Friendly input error | Empty value |
| TC10 | 4 then 2 | Both details appear | Menu repeats |

## 13.2 Common errors

### ValueError during integer conversion

Problem:

~~~python
choice = int("hello")
~~~

Cause: int() expects text that can be interpreted as an integer.

Solution:

~~~python
try:
    choice = int(choice_text)
except ValueError:
    print("Please enter a valid number.")
~~~

### KeyError

Problem:

~~~python
print(concepts[9])
~~~

Cause: key 9 does not exist.

Solution:

~~~python
concept = concepts.get(9)
~~~

Then check whether concept is None.

### IndentationError

Cause: a statement inside a function or loop is not indented consistently.

Fix:

- Check the indentation level.
- Use the same indentation style throughout the file.
- Most Python projects use four spaces per indentation level.
- Avoid mixing tabs and spaces.

### Infinite loop

Cause: the loop never reaches an exit condition and has no effective break.

Fix:

- Identify how the loop should stop.
- Confirm that the exit choice is checked.
- Confirm that break is reachable.
- Test the exit option.

### Function defined but never called

Problem:

~~~python
def show_menu():
    print("Menu")
~~~

The function is defined, but no call is made.

Solution:

~~~python
show_menu()
~~~

A function definition and a function call are different operations.

## 13.3 Debugging method

1. Read the last line of the traceback first.
2. Identify the exception type.
3. Identify the file and line number.
4. Inspect the values used on that line.
5. Check the data types.
6. Check spelling and indentation.
7. Reproduce the issue with the smallest input.
8. Fix one cause at a time.
9. Re-run the test that previously failed.
10. Run the other tests to check for regressions.

Do not randomly change several lines at once. That makes the original cause harder to identify.

---

# 14. Exercises with explained solutions

## Exercise 1 — Explain the hierarchy

Write one or two sentences explaining AI, ML, Deep Learning, Generative AI and LLMs.

**Hint:** Start with AI as the broad field. Explain which terms describe learning approaches and which describe content generation.

**Suggested answer:** AI is the broad field of building systems that perform tasks associated with intelligent behaviour. ML is one area within AI, and Deep Learning is a form of ML based on multi-layer neural networks. Generative AI describes systems that generate content. LLMs are language models used for language tasks and many text-generation applications.

## Exercise 2 — Classification or generation?

Identify the task.

1. Is this transaction fraudulent?
2. Write a polite reply to this customer.
3. Classify this ticket as Billing or Technical.
4. Summarise this report.
5. Generate three practice questions.

**Suggested answers:**

| Number | Task | Reason |
|---:|---|---|
| 1 | Classification or risk prediction | Produces a class or score |
| 2 | Generation | Produces new text |
| 3 | Classification | Selects a category |
| 4 | Generation | Produces a shorter text |
| 5 | Generation | Creates new questions |

## Exercise 3 — Identify application components

A student types a question into a website. A Python server sends it to a model provider and returns the response.

Identify the frontend, backend, model, prompt and API.

**Suggested answer:**

- Frontend: the website interface.
- Backend: the Python server.
- Model: the language model selected from the provider.
- Prompt: instructions and user content sent to the model.
- API: the communication interface used by the backend to call the provider.

## Exercise 4 — Read the Python code

~~~python
topics = ["AI", "ML", "GenAI"]

for topic in topics:
    print(topic)
~~~

Questions:

1. What type of value is topics?
2. What does the for loop do?
3. How many times does print() run?
4. What is the output?

**Suggested answer:**

1. topics is a list.
2. The loop processes each list item in order.
3. print() runs three times.
4. AI, ML and GenAI appear on separate lines.

## Exercise 5 — Fix the bug

~~~python
choice_text = input("Choose: ")
choice = int(choice_text)

if choice = 1:
    print("AI")
~~~

**Problem:** The condition uses assignment syntax instead of equality comparison.

Corrected version:

~~~python
choice_text = input("Choose: ")
choice = int(choice_text)

if choice == 1:
    print("AI")
~~~

A complete user-facing program should also handle non-numeric input with try and except.

## Exercise 6 — Add another concept

Add Natural Language Processing as a sixth concept.

Your entry must contain a name, meaning, example and relationship to AI.

Suggested entry:

~~~python
6: {
    "name": "Natural Language Processing",
    "meaning": "A field concerned with enabling computers to process human language.",
    "example": "Extracting important details from an email.",
    "relationship": "NLP is an area of AI; LLMs are used for many NLP tasks."
}
~~~

Update the menu and the valid-choice message too.

## Exercise 7 — Why is this project not an LLM?

**Suggested answer:** The program retrieves fixed information from a Python dictionary. It does not use a trained language model, token generation or a model API. It is a normal application that presents educational information.

## Exercise 8 — Identify the limitation

A model generates a confident answer about a company's refund policy, but the answer is not in the approved policy document.

What should the developer do?

**Suggested answer:** Do not trust the confident wording. Retrieve the current approved policy, require the answer to be grounded in it, validate citations or evidence, and send uncertain or high-impact cases for human review. The backend must enforce permissions independently of the prompt.

---

# 15. Knowledge check — five MCQs

Answer before reading the explanation.

## Question 1

Which statement best describes Machine Learning?

A. Every program written in Python.  
B. A field in which systems learn patterns from data.  
C. A database that stores customer records.  
D. A user interface for a chatbot.

**Correct answer: B.**

Explanation: Machine Learning uses data and learning algorithms to fit models that make predictions or decisions. Python, databases and interfaces may be used in an ML application, but they are not the definition of ML.

## Question 2

Which statement best describes Deep Learning?

A. A form of Machine Learning using multi-layer neural networks.  
B. A method of writing longer Python comments.  
C. A type of relational database.  
D. A prompt that contains many examples.

**Correct answer: A.**

Explanation: Deep Learning is based on neural networks with multiple processing layers. It is not defined by code length, database type or prompt length.

## Question 3

Which task is an example of Generative AI?

A. Returning a fixed HTTP status code.  
B. Checking whether a number is greater than zero.  
C. Drafting a new customer-support reply.  
D. Sorting a list alphabetically.

**Correct answer: C.**

Explanation: Drafting a new reply generates content. The other tasks can be handled by ordinary deterministic software.

## Question 4

What is the purpose of attention in a transformer?

A. To store a user's password.  
B. To let token representations use information from other positions.  
C. To guarantee that every answer is factual.  
D. To convert Python code into a database.

**Correct answer: B.**

Explanation: Attention computes relationships between representations at different positions and combines information. It does not guarantee truth or provide application security.

## Question 5

Which statement about an LLM-powered application is correct?

A. The model automatically handles user authentication.  
B. The model automatically knows a company's private database.  
C. The application must handle validation, security and failures around the model.  
D. A prompt guarantees that the response is correct.

**Correct answer: C.**

Explanation: The application developer remains responsible for authentication, permissions, input validation, provider errors, response validation and monitoring.

---

# 16. Interview preparation

## Question 1 — What is the difference between AI, ML and Deep Learning?

**Answer:** AI is the broad field of building systems that perform tasks associated with intelligent behaviour. ML is one approach within AI where models learn patterns from data. Deep Learning is a type of ML that uses neural networks with multiple layers.

**Example:** A rule-based route planner is an AI-related system. A model that predicts delivery time from historical data uses ML. A neural network that recognises objects in images uses Deep Learning.

**What the interviewer checks:** Whether you understand the relationship, can give examples and avoid treating the terms as synonyms.

## Question 2 — What is Generative AI?

**Answer:** Generative AI refers to AI systems that create new content such as text, images, audio, video or code. A text-generation model can draft an email or summarise a document. Its output can be useful but must be checked because generated content can be incorrect or unsupported.

**Follow-up:** Is every ML model generative?

No. Many ML models predict labels, scores or numerical values rather than generating new content.

## Question 3 — What is an LLM?

**Answer:** An LLM is a neural network trained to process and generate language. Many modern LLMs use transformer architectures. A common training objective is next-token prediction. At inference time, the model uses supplied context to generate a sequence of tokens. It does not automatically verify every factual statement.

## Question 4 — Explain a transformer at a high level.

**Answer:** Text is tokenised into token IDs. The model maps token IDs into vector representations and includes information about token positions. Transformer blocks use attention and feed-forward computations to build contextual representations. The model then produces scores for possible next tokens. A decoding method selects a token and generation continues until a stopping condition is reached.

Do not claim every transformer implementation has exactly the same layers, positional method or decoding behaviour.

## Question 5 — What is attention?

**Answer:** Attention is a mechanism that lets a representation at one token position use information from other positions. It computes scores between queries and keys, converts those scores into weights and combines value vectors. This helps the model represent relationships among tokens in context.

## Question 6 — Does an LLM know facts like a human?

**Answer:** An LLM learns statistical and structural patterns from training data and processes the context supplied to it. It can produce useful language and solve many tasks, but fluent output does not prove that it has verified a fact or understood it in the same way a person does. Developers should evaluate outputs and supply trusted information where required.

## Question 7 — What is the difference between a model and an AI application?

**Answer:** A model is the trained component that performs a task such as generating text. An AI application includes the model plus the user interface, backend, prompts, authentication, data retrieval, validation, error handling, monitoring and business rules.

## Question 8 — Can an LLM access a company's database automatically?

**Answer:** No. The application must provide an authorised mechanism, such as a backend database query or permitted tool. The application must check the user's permissions and limit which data can be accessed. A prompt alone is not an access-control system.

## Question 9 — What is a hallucination?

**Answer:** A hallucination is generated content that sounds plausible but is false, unsupported or fabricated. It can be reduced through trusted context, retrieval, validation, evaluation and human review, but no single prompt or temperature setting guarantees it will never happen.

## Question 10 — Why do developers need Python if they already have an LLM?

**Answer:** Python lets developers build the application around the model. It can validate user input, construct prompts, call APIs, retrieve data, enforce permissions, handle errors, test outputs and connect the model to a user interface.

## Practice task

Draw this flow from memory and explain every box:

~~~text
User
 |
 v
Frontend
 |
 v
Python backend
 |
 v
Input validation
 |
 v
Prompt and context
 |
 v
LLM provider API
 |
 v
Response validation
 |
 v
Frontend response
~~~

For each stage, name one possible failure and one way to handle it.

---

# 17. Independent speaking and writing practice

Record or write a short explanation in your own words for each prompt:

1. Explain AI to a person who has never written code.
2. Explain ML using a house-price prediction example.
3. Explain Deep Learning using image recognition.
4. Explain why generating a reply differs from classifying a ticket.
5. Explain what an LLM does.
6. Explain tokenization without saying one word equals one token.
7. Explain embeddings as numerical representations.
8. Explain attention using a sentence with a pronoun.
9. Explain why a model is not a complete application.
10. Explain one way an AI application can fail even when the model is working.

A strong explanation contains a definition, a practical example and one limitation.

---

# 18. Glossary

| Term | Meaning |
|---|---|
| Artificial Intelligence | Broad field of systems performing tasks associated with intelligent behaviour |
| Machine Learning | Learning patterns from data to make predictions or decisions |
| Deep Learning | ML using neural networks with multiple processing layers |
| Generative AI | AI systems that generate content |
| LLM | Large Language Model |
| Neural network | Parameterised mathematical model made of connected computational units |
| Parameter | Learned numerical value in a model |
| Training | Process of fitting model parameters using data and an objective |
| Inference | Using a trained model to produce an output |
| Transformer | Neural-network architecture built around attention and other transformations |
| Token | Unit produced by a tokenizer |
| Tokenizer | Component that converts text to token IDs and back |
| Token ID | Integer identifier for a token |
| Embedding | Vector representation |
| Attention | Mechanism for combining information across positions |
| Query | One vector projection used in attention |
| Key | One vector projection used in attention |
| Value | One vector projection used in attention |
| Logit | Unnormalised score before a probability transformation |
| Decoding | Method used to select generated tokens |
| Prompt | Instructions and context supplied to a model |
| Inference API | Interface used by an application to request model output |
| Hallucination | Plausible-sounding but false or unsupported generated content |
| Backend | Server-side application logic |
| Frontend | User-facing application interface |
| Validation | Checking that data or output meets requirements |
| Monitoring | Observing application behaviour and failures over time |

---

# 19. Day 11 completion checklist

Mark an item only when you can demonstrate it without copying the lesson.

## Concept understanding

- [ ] I can define software and explain input, processing and output.
- [ ] I can distinguish a rule-based program from a learned model.
- [ ] I can explain AI, ML and Deep Learning.
- [ ] I can explain Generative AI.
- [ ] I can define an LLM.
- [ ] I can explain the high-level transformer flow.
- [ ] I can describe attention without claiming it guarantees truth.
- [ ] I can distinguish token embeddings from document embeddings at a high level.
- [ ] I can explain model versus application.

## Python skills

- [ ] I can create and run a Python file.
- [ ] I can use print().
- [ ] I can create variables.
- [ ] I can identify strings, integers and Booleans.
- [ ] I can accept input using input().
- [ ] I can use if, elif and else.
- [ ] I can use lists and dictionaries.
- [ ] I can define and call a function.
- [ ] I can use a while loop.
- [ ] I can catch a ValueError.

## Project skills

- [ ] I created the project folder.
- [ ] I implemented the concept dictionary.
- [ ] I wrote the menu function.
- [ ] I wrote the concept display function.
- [ ] I implemented the repeated menu.
- [ ] I handled non-numeric input.
- [ ] I handled an invalid numeric choice.
- [ ] I tested the exit option.
- [ ] I wrote a README.
- [ ] I can explain every important line of the code.

## Evidence to submit

1. main.py.
2. README.md.
3. Terminal output for a valid selection.
4. Terminal output for invalid input.
5. Terminal output for exit.
6. A short explanation of why the project is not an LLM.
7. Answers to the five MCQs.
8. Your own explanation of the transformer flow.

---

# 20. What comes next — Day 12

Day 11 introduced tokens as the units processed by language models. Day 12 examines them carefully.

You will learn:

- Why a token is not always a word.
- How tokenization converts text into token IDs.
- How to inspect tokens using a supported tokenizer.
- What a context window means.
- How instructions, history, user input and retrieved context consume capacity.
- Why output allowance must be planned.
- How to estimate and reduce token usage responsibly.

Do not skip Day 12 because you already understand the word token. In an LLM application, token budgeting affects whether a request fits, how much context can be supplied and how much a request may cost.

**End of Day 11.**
