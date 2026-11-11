# Day 4 Project — AI Application Component Manager

## Objective
Model components of a small AI application using classes and objects. Build a retriever, prompt builder and assistant coordinator. No external model is called.

## Requirements
- Base component with name and describe method.
- Retriever inherits from the base.
- Prompt builder formats a prompt.
- Assistant uses retriever and prompt builder through composition.
- Validate required text.
- Demonstrate object instances and tests.

## Create component_manager.py

~~~python
class AIComponent:
    def __init__(self, name):
        if not name.strip():
            raise ValueError("Component name cannot be empty")
        self.name = name

    def describe(self):
        return f"Component: {self.name}"


class DocumentRetriever(AIComponent):
    def retrieve(self, query):
        if not query.strip():
            raise ValueError("Query cannot be empty")
        return f"Sample context for: {query}"


class PromptBuilder:
    def build(self, question, context):
        return (
            "Use the context to answer.\\n"
            f"Context: {context}\\n"
            f"Question: {question}"
        )


class Assistant:
    def __init__(self, retriever, prompt_builder):
        self.retriever = retriever
        self.prompt_builder = prompt_builder

    def prepare_request(self, question):
        context = self.retriever.retrieve(question)
        return self.prompt_builder.build(question, context)


if __name__ == "__main__":
    retriever = DocumentRetriever("Policy Retriever")
    builder = PromptBuilder()
    assistant = Assistant(retriever, builder)
    print(retriever.describe())
    print(assistant.prepare_request("What is the leave policy?"))
~~~

## Code walkthrough
- AIComponent stores common identity and exposes describe().
- DocumentRetriever is a kind of AIComponent, so inheritance is appropriate.
- PromptBuilder has a separate responsibility.
- Assistant contains a retriever and builder; this is composition.
- prepare_request coordinates components. It does not perform real search or call an LLM.

## Run
Windows: py component_manager.py  
macOS/Linux: python3 component_manager.py

Expected output includes the component name and a prompt containing the sample context and leave-policy question.

## Test cases
| Test | Expected |
|---|---|
| Create retriever with a name | Object created |
| Call describe | Component name returned |
| Retrieve non-empty query | Sample context returned |
| Retrieve blank query | ValueError |
| Prepare assistant request | Prompt includes context and question |
| Create component with blank name | ValueError |

## Independent extensions
1. Add a VectorStore class with search().
2. Add a ChatMessage class with role validation.
3. Create two retrievers and show their instance names differ.
4. Draw inheritance and composition relationships.
5. Replace the retriever with a fake object that returns fixed test context.

## Submission
Submit the Python file, sample output, test table and explanation of why Assistant uses composition.
