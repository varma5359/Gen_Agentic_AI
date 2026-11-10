# Day 16 — Interview Preparation: OpenAI and Gemini API Integration

## Beginner questions

**1. What is an API?**  
An API is an interface that allows one software application to communicate with another.

**2. What is an LLM API?**  
It lets an application send input to a language model and receive generated output through a network request.

**3. What is an SDK?**  
A software development kit is a package that provides helper classes and methods for using a service. The OpenAI Python SDK and Google Gen AI SDK simplify provider API calls.

**4. What is an API key?**  
A secret credential used to authenticate an application with an API provider. It must be protected.

**5. Is the API key the same as the model?**  
No. The key authorizes access; the model processes input and generates output.

**6. Why use a virtual environment?**  
It isolates project dependencies so package versions in one project do not unnecessarily affect another.

**7. What is a .env file?**  
A local configuration file commonly used to store environment variables during development. It must not be committed when it contains secrets.

## Technical questions

**8. What does os.getenv("OPENAI_API_KEY") do?**  
It reads an environment variable and returns its string value, or None if the variable is missing and no default is provided.

**9. Why call load_dotenv()?**  
It loads values from a local .env file into the process environment so code can read them using os.getenv().

**10. What does OpenAI(api_key=api_key) create?**  
A configured SDK client used to make requests to the OpenAI API.

**11. What is the purpose of client.responses.create()?**  
It sends input to a selected model through the Responses API and returns a response object.

**12. How do you read generated text in the Day 16 example?**  
Use response.output_text.

**13. How does the Gemini example differ?**  
It creates a genai.Client and calls client.models.generate_content(...); generated text is read from response.text.

**14. Can the same SDK code be used for OpenAI and Gemini?**  
No. Providers have different SDKs, method names, request formats and model availability.

**15. What should you consider when choosing a model?**  
Quality, speed, cost, context capacity, required features and account availability.

## Security and troubleshooting

**16. Why should an API key never be hardcoded?**  
Source code may be shared, logged or committed. An exposed key can be misused and create unauthorized usage or charges.

**17. What should .gitignore contain for this project?**  
At minimum .env, .venv/, __pycache__/ and compiled Python files such as *.pyc.

**18. What does HTTP 401 usually indicate?**  
An authentication failure, often caused by a missing, invalid or revoked key.

**19. What does HTTP 429 usually indicate?**  
A rate limit or quota-related issue. Check usage and provider guidance.

**20. What should you do if the SDK import fails?**  
Confirm the virtual environment is active and install the required package using that environment's Python executable.

**21. Why can a model name fail?**  
It may be misspelled, unavailable, retired or inaccessible to the account.

**22. What happens if the API key is missing in the example?**  
The program raises a clear ValueError before attempting the API request.

## Scenario-based questions

**23. A key was accidentally pushed to a public repository. What do you do?**  
Revoke the exposed key immediately, create a replacement, update the deployment secret, inspect usage and remove the secret from repository history where appropriate. Deleting the visible line alone does not make an exposed key safe.

**24. The code works on one computer but says ModuleNotFoundError on another. Why?**  
The package may not be installed in the active environment. Activate the correct virtual environment and install dependencies from requirements.txt.

**25. Your application needs to support two LLM providers. How would you organize it?**  
Keep provider-specific SDK calls in separate service modules and expose a common application-level function or interface. Keep credentials separate and test each provider.

## Quick revision

| Topic | Key point |
|---|---|
| API | Software communication interface |
| SDK | Helper package for an API |
| API key | Secret credential |
| .env | Local environment configuration |
| os.getenv() | Reads an environment variable |
| OpenAI client | OpenAI(api_key=...) |
| Gemini client | genai.Client(api_key=...) |
| Authentication error | Often HTTP 401 |
| Rate limit / quota | Often HTTP 429 |
