# Day 2 Interview Questions — Day 2 — Python data structures: strings, lists, tuples, sets and dictionaries

**Phase:** 1 — Python and Software Development Foundations

## How to use this guide

Answer each question aloud before reading the suggested answer. Use your own words. A strong fresher answer defines the concept, explains its purpose and gives a relevant example.

## Section 1 — Core interview questions

### Q1. When use a list instead of a tuple?

**Answer:** Use a list for ordered data that changes, such as conversation messages. Use a tuple for a fixed ordered grouping.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q2. List versus set?

**Answer:** A list preserves order and duplicates. A set stores unique hashable values and is useful for membership checks.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q3. What is a dictionary?

**Answer:** A mapping of keys to values. It is useful for named records such as a message with role and content.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q4. What does mutable mean?

**Answer:** A mutable object can change after creation. Lists and dictionaries are mutable; strings and tuples are immutable.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q5. How handle a missing dictionary key?

**Answer:** Use square brackets when the key must exist. Use get() with a meaningful default when it is optional.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

## Section 2 — Difference-based questions

Compare the related concepts from today's notes. Explain their meaning, practical difference and when you would choose each one. Use the comparison table in the class notes as a revision starting point; add an example from your own code.

## Section 3 — Practical implementation questions

1. Explain how you would recreate today's guided example from an empty project.
2. Which inputs should be validated before the main operation starts?
3. What should the program return or display on success and failure?
4. What tests would you write for a normal case, an edge case and an invalid case?
5. What would you change before using the example in a production application?

## Section 4 — Scenario-based questions

### Scenario A — Your code works for one input but fails for another

**Expected approach**
1. Reproduce the failure using the exact input.
2. Read the complete traceback or response details.
3. Inspect assumptions about types, missing values and boundaries.
4. Fix the underlying cause instead of hiding the error.
5. Add a regression test and rerun the relevant tests.

### Scenario B — A prototype must become part of a business application

**Expected approach**
1. Confirm the business requirement and expected behaviour.
2. Separate input validation, business logic and external dependencies.
3. Define clear data structures and interfaces.
4. Add persistence, security and observability appropriate to the use case.
5. Add tests, documentation and deployment controls.

## Section 5 — Troubleshooting questions

- What exact error or status code do you see?
- Can you reproduce the issue with a smaller input?
- Which line or request boundary first shows incorrect behaviour?
- What changed immediately before the failure?
- How will you verify the fix and prevent regression?

## Section 6 — Strong points to remember

- Define the concept directly before giving an example.
- Explain why the approach fits the requirement.
- Mention one limitation and how you would handle it.
- Do not claim a demonstration is production-ready without the persistence, security, testing and operational controls it needs.
- Explain your own contribution honestly.
