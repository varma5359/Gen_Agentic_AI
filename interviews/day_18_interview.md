# Day 18 — Interview Preparation: Streaming and Conversations

## Beginner questions

**1. What is response streaming?**  
Streaming delivers generated output in smaller pieces as the model produces it instead of waiting for the complete response.

**2. What is the difference between normal output and streaming?**  
A normal request generally returns the completed response. A streaming request lets the application display output progressively.

**3. Does streaming make the model generate faster?**  
Not necessarily. It mainly improves perceived responsiveness by showing the first output earlier.

**4. What are message roles?**  
Roles identify who or what supplied a message, such as system, user and assistant.

**5. What is conversation history?**  
A sequence of earlier messages that an application can include with a new question so the model has context.

## Python questions

**6. How can Python store conversation history?**  
A list of dictionaries, with each dictionary containing fields such as role and content.

**7. What does list.append(item) do?**  
It adds one item to the end of a list and modifies the original list.

**8. What does append() return?**  
None. It does not return the updated list.

**9. What does return answer do?**  
It sends the value of answer back to the code that called the function.

**10. What does end="" do in print()?**  
It prevents print() from adding its usual newline after the output.

**11. Why use flush=True when printing streamed chunks?**  
It asks Python to flush buffered output so text is shown promptly.

## Conversation design

**12. Does an LLM automatically remember every earlier API call?**  
No. The application normally needs to send relevant conversation history or use a provider feature that manages conversation state.

**13. Why save the assistant response in history?**  
So the next request can include both the user's question and the assistant's previous answer.

**14. Why should each user have separate conversation history?**  
To prevent private messages from one user being exposed to another user.

**15. What is a context window?**  
The amount of input and conversation context a model can process for a request. Capacity is limited.

**16. What can an application do when history becomes too long?**  
Keep recent relevant messages, summarize older messages, or remove irrelevant content while preserving necessary context.

## Scenario-based questions

**17. A chatbot answers the first question but forgets it on the second turn. What should you inspect?**  
Check whether the application saved earlier messages and included them in the second API request.

**18. The streamed response appears one word per line. What might be wrong?**  
The code may be using print()'s default newline. Use end="" for consecutive chunks.

**19. Two users see the same conversation. What is the likely design problem?**  
The application may use shared global conversation history instead of session-specific storage.

**20. Why should a chatbot limit its conversation history?**  
To control context-window usage, cost, latency and unnecessary retention of user data.

## Quick revision

| Topic | Key point |
|---|---|
| Streaming | Receive output progressively |
| Message role | Identifies message source/type |
| History | Earlier messages sent for context |
| append() | Adds item; returns None |
| end="" | Avoids newline after each chunk |
| Context window | Limited model context capacity |
| Session isolation | Keeps each user's history separate |
