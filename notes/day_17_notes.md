# Day 17 — Structured Outputs, JSON and Pydantic Validation

**Phase:** 3 — LLM Application Development  
**Approved topic:** Structured outputs, JSON responses, Pydantic schemas, output validation and parsing  
**Mini-project:** Resume Information Extraction Application  
**Duration:** 2–3 hours | **Difficulty:** Beginner

## 1. Learning objectives
Students will learn to:
- Explain normal text versus structured data.
- Understand JSON objects, keys and values.
- Create a Pydantic model for expected data.
- Validate data and understand validation errors.
- Ask an LLM for a predictable structure.
- Convert a model response into Python data safely.

## 2. Why do applications need structured output?

Imagine asking an LLM to extract details from a resume.

Normal text:
~~~text
The candidate is Asha. She knows Python and SQL and has two years of experience.
~~~

A program must search this sentence to find each value. That is difficult and unreliable.

Structured data:
~~~json
{
  "name": "Asha",
  "skills": ["Python", "SQL"],
  "experience_years": 2
}
~~~

~~~text
Resume text
    |
    v
LLM extraction request
    |
    v
Structured JSON response
    |
    v
Validate required fields and types
    |
    +---- valid ----> Use in application
    |
    +---- invalid --> Handle validation error
~~~

Structured output is easier to store, display, search and pass to another program. It does not prove the extracted facts are true; compare them with the source document.

## 3. JSON basics

JSON means JavaScript Object Notation. It is a text format used to exchange structured data.

~~~json
{
  "name": "Asha",
  "age": 22,
  "is_student": true,
  "skills": ["Python", "SQL", "Excel"],
  "location": null
}
~~~

| JSON value | Example | Meaning |
|---|---|---|
| String | "Asha" | Text in double quotes |
| Number | 22 | Integer or decimal |
| Boolean | true | True or false |
| Array | ["Python", "SQL"] | Ordered collection |
| Object | {"name": "Asha"} | Key-value collection |
| Null | null | No value |

JSON uses true, false and null. Python uses True, False and None.

## 4. Python dictionaries and JSON strings

A Python dictionary is a Python data structure. JSON is a text representation used to exchange data.

~~~python
import json

student = {
    "name": "Asha",
    "age": 22,
    "skills": ["Python", "SQL"]
}

json_text = json.dumps(student, indent=2)
print(json_text)
~~~

**Expected output**
~~~json
{
  "name": "Asha",
  "age": 22,
  "skills": [
    "Python",
    "SQL"
  ]
}
~~~

| Method | Purpose | Input | Return |
|---|---|---|---|
| json.dumps(data) | Convert Python data to JSON text | Python dictionary/list | String |
| json.loads(text) | Convert JSON text to Python data | JSON string | Python data |

Both return a result; they do not modify the original dictionary or string.

~~~python
received_text = '{"name": "Asha", "age": 22}'
received_data = json.loads(received_text)

print(received_data["name"])
print(received_data["age"])
~~~

Output:
~~~text
Asha
22
~~~

Common mistake: json.loads() expects valid JSON text. Passing a Python dictionary directly is incorrect.

## 5. Why use Pydantic?

Pydantic helps describe and validate the shape of data.

Think of a form:
- Name must be text.
- Skills must be a list of text values.
- Experience must be an integer.

Install if needed:

~~~bash
python -m pip install pydantic
~~~

Create schema_demo.py:

~~~python
from pydantic import BaseModel

class Resume(BaseModel):
    name: str
    skills: list[str]
    experience_years: int

resume = Resume(
    name="Asha",
    skills=["Python", "SQL"],
    experience_years=2
)

print(resume.name)
print(resume.skills)
print(resume.model_dump())
~~~

**Expected output**
~~~text
Asha
['Python', 'SQL']
{'name': 'Asha', 'skills': ['Python', 'SQL'], 'experience_years': 2}
~~~

| Code | Meaning |
|---|---|
| class Resume | Defines a class named Resume |
| BaseModel | Pydantic base class that provides validation |
| name: str | Field name should contain a string |
| skills: list[str] | Field should be a list of strings |
| experience_years: int | Field should be an integer |
| Resume(...) | Creates and validates a model instance |
| resume.name | Reads the name field |
| model_dump() | Returns model data as a Python dictionary |

model_dump() returns a new dictionary. It does not change the model.

## 6. Required and optional fields

A field without a default is required.

~~~python
from pydantic import BaseModel

class Candidate(BaseModel):
    name: str
    email: str | None = None
    experience_years: int = 0

candidate = Candidate(name="Asha")
print(candidate.model_dump())
~~~

**Expected output**
~~~text
{'name': 'Asha', 'email': None, 'experience_years': 0}
~~~

| Field declaration | Meaning |
|---|---|
| name: str | Required string |
| email: str \| None = None | Optional string; default None |
| experience_years: int = 0 | Integer; default zero |

The vertical bar type syntax means either listed type is accepted (Python 3.10+).

## 7. Validation errors

~~~python
from pydantic import BaseModel, ValidationError

class Candidate(BaseModel):
    name: str
    experience_years: int

try:
    candidate = Candidate(name="Asha", experience_years="many")
except ValidationError as error:
    print("Input data is invalid.")
    print(error)
~~~

**Expected result:** Pydantic reports that "many" cannot be accepted as an integer. Exact error detail depends on the Pydantic version.

| Term | Meaning |
|---|---|
| Validation | Checking data against rules |
| ValidationError | Exception raised when model data fails validation |
| try | Runs code that may fail |
| except | Handles a matching exception |

Validation checks structure and types. It cannot prove that a resume claim is true.

## 8. Ask an LLM for structured resume data

For a provider that supports structured output, define a schema and ask the SDK to return data matching it. The exact SDK method depends on provider and model.

OpenAI example using a Pydantic schema:

~~~python
import os
from dotenv import load_dotenv
from pydantic import BaseModel
from openai import OpenAI

class ResumeDetails(BaseModel):
    name: str
    skills: list[str]
    experience_years: int

load_dotenv()
client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

resume_text = """
Asha Kumar
Skills: Python, SQL, Excel
Experience: 2 years as a data analyst.
"""

response = client.responses.parse(
    model="gpt-4.1-mini",
    input=[
        {
            "role": "system",
            "content": (
                "Extract resume information. Use only facts present "
                "in the resume. Do not invent missing values."
            )
        },
        {
            "role": "user",
            "content": resume_text
        }
    ],
    text_format=ResumeDetails
)

details = response.output_parsed
print(details.model_dump())
~~~

**Expected output (illustrative)**
~~~text
{'name': 'Asha Kumar', 'skills': ['Python', 'SQL', 'Excel'], 'experience_years': 2}
~~~

Exact support depends on selected model and SDK version. Check current provider documentation if the call is not supported.

**Important:** Structured output constrains response format. It does not independently verify the resume, prove the candidate's skills or guarantee perfect extraction. Keep the original resume available for review.

## 9. Parsing, validation and verification

| Step | Question answered |
|---|---|
| Parsing | Can the text be converted into data? |
| Validation | Does the data match the expected schema? |
| Verification | Is the information supported by the source? |

JSON can parse correctly and pass the schema while still containing an invented experience value. Verification requires comparison with the source resume.

## 10. Mini-project — Resume Information Extraction Application

**Goal:** Extract candidate name, skills and experience from resume text.

Required fields:
- name: string
- skills: list of strings
- experience_years: integer or optional when not specified

~~~text
Resume text
   |
   v
Send extraction instructions to LLM
   |
   v
Receive structured result
   |
   v
Validate with Pydantic
   |
   v
Display extracted fields
   |
   v
Human checks source resume
~~~

Requirements:
1. Use a Pydantic model.
2. Provide a sample resume.
3. Ask the LLM to extract only source-supported information.
4. Validate the result.
5. Handle API and validation errors.
6. Display extracted fields clearly.
7. Never invent missing information.

Suggested structure:

~~~text
resume_extractor/
├── main.py
├── schemas.py
├── .env
├── .gitignore
└── requirements.txt
~~~

## 11. Common mistakes
- Confusing a Python dictionary with a JSON string.
- Passing a dictionary directly to json.loads().
- Forgetting required fields.
- Assuming validation proves factual correctness.
- Treating missing information as zero when it should be unknown.
- Assuming every model supports every structured-output feature.
- Trusting extracted information without checking the source.

## 12. Practice with answers
1. **What is JSON?** A text format for exchanging structured data.
2. **What does json.dumps() do?** Converts Python data into a JSON string.
3. **What does json.loads() do?** Converts JSON text into Python data.
4. **What is Pydantic used for?** Defining data models and validating data.
5. **What does name: str mean?** The field is expected to contain a string.
6. **What does model_dump() return?** A Python dictionary containing model data.
7. **Does valid JSON mean the information is true?** No.
8. **What is a required field?** A field that must be provided when creating the model.
9. **Why use structured output?** It makes results easier to validate and process.
10. **What should happen when information is missing?** Represent it as missing according to the schema; do not invent it.

## 13. Day 17 recap

~~~text
LLM result -> Structured data -> Pydantic schema -> Validation
                                              |
                               +--------------+--------------+
                               |                             |
                            Valid                         Invalid
                               |                             |
                          Application                  Error handling
~~~

**Next day:** Day 18 — Streaming responses, conversation history, message roles and multi-turn conversations.
