# Day 17 — Interview Preparation: Structured Outputs, JSON and Pydantic

## Beginner questions

**1. What is JSON?**  
JSON is a text format for representing structured data using objects, arrays, strings, numbers, booleans and null.

**2. Why do LLM applications use structured output?**  
It makes model responses easier for programs to validate, store, display and pass to other components.

**3. What is the difference between a Python dictionary and JSON?**  
A dictionary is a Python object. JSON is a text format. They can represent similar data, but they are not the same type.

**4. What does json.dumps() do?**  
It serializes Python data into a JSON string.

**5. What does json.loads() do?**  
It parses a JSON string into Python data.

## Pydantic questions

**6. What is Pydantic?**  
A Python library for defining data models and validating data against declared types and constraints.

**7. What is BaseModel?**  
The base class used to define Pydantic models.

**8. What does name: str mean?**  
It declares a field named name that is expected to contain a string.

**9. What does list[str] mean?**  
A list whose items are strings.

**10. What does Field(min_length=1, max_length=4000) do?**  
It adds length constraints to a field so invalid values can be rejected during validation.

**11. What does model_dump() return?**  
A Python dictionary containing the model's data.

**12. What is a required field?**  
A field that must be provided when creating a model instance.

**13. How can a field be optional?**  
Use a nullable type and a suitable default, such as email: str | None = None.

## LLM structured output

**14. Does structured output guarantee that model facts are correct?**  
No. It helps control response format. Information still needs to be checked against a trusted source.

**15. Explain parsing, validation and verification.**  
Parsing converts text into data. Validation checks the data against a schema. Verification checks whether claims are supported by the original source.

**16. Why is a Pydantic schema useful for resume extraction?**  
It defines expected fields such as name, skills and years of experience, and validates their types.

**17. What should the application do when a resume does not contain an email address?**  
Represent email as missing or None according to the schema instead of inventing an address.

## Scenario-based questions

**18. JSON parsing succeeds, but extracted experience is incorrect. Why?**  
Correct JSON syntax does not prove factual correctness. Compare the result with the resume.

**19. The model returns a string where your schema expects an integer. What happens?**  
Pydantic validates the value and may reject it if it cannot be converted according to its rules. A ValidationError is raised.

**20. Why check structured-output model compatibility?**  
Not every model or SDK version supports the same structured-output features and schemas.

**21. How would you handle invalid structured output?**  
Catch the validation/parsing error, record a safe diagnostic, and either request a controlled correction or report that extraction could not be completed. Do not silently invent missing fields.

## Quick revision

| Term | Meaning |
|---|---|
| JSON | Structured data text format |
| dumps() | Python data to JSON string |
| loads() | JSON string to Python data |
| Pydantic | Data validation library |
| BaseModel | Base class for schemas |
| Field() | Field constraints and metadata |
| model_dump() | Model to Python dictionary |
| Parsing | Convert representation |
| Validation | Check schema |
| Verification | Check facts against source |
