# Day 5 Interview Guide — Modules, Exceptions, Files, JSON and Logging

## Q1. What is a Python module?
A module is a Python source file that can be imported. It separates reusable code from application entry points. Follow-up: What is a package? A package groups related modules in a directory structure.

## Q2. Why use exception handling?
It lets an application respond to expected runtime failures rather than terminating unexpectedly. Catch specific exceptions, provide a useful message and preserve diagnostics. Follow-up: Why avoid except Exception: pass? It hides defects and makes debugging difficult.

## Q3. Explain try, except, else and finally.
try contains risky operations; except handles a matching exception; else runs if try succeeds; finally runs as control leaves the structure and is useful for cleanup. Follow-up: Does finally normally run after an exception? Yes, as control exits the try structure.

## Q4. Compare file modes r, w and a.
r reads an existing file; w creates or truncates a file; a appends or creates. Follow-up: Which mode can destroy existing content? w.

## Q5. Why use with open?
It uses a context manager to close the file when the block exits, including when an exception occurs. It does not prevent missing-path or permission errors.

## Q6. dumps versus dump?
json.dumps returns JSON text from a Python object. json.dump writes JSON to a file-like object. loads parses text; load reads from a file. Malformed JSON raises JSONDecodeError.

## Q7. Why use logging instead of print?
Logging supports severity levels, timestamps and configurable destinations. print is useful for simple learning output, but not a full diagnostics strategy. Never log passwords, API keys, tokens or sensitive user content.

## Q8. How should application secrets be stored?
Use environment variables or a managed secrets service, restrict access and never commit secrets. A private repository is not a safe secrets vault.

## Practical task
Write a program that loads JSON configuration, validates a required key and gives friendly messages for a missing file or malformed JSON. Explain each exception branch.
