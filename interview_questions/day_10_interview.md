# Day 10 Interview Questions — Day 10 — SQL fundamentals, relational database concepts, Git, GitHub, virtual environments, pytest and debugging

**Phase:** 1 — Python and Software Development Foundations

## How to use this guide

Answer each question aloud before reading the suggested answer. Use your own words. A strong fresher answer defines the concept, explains its purpose and gives a relevant example.

## Section 1 — Core interview questions

### Q1. Primary key versus foreign key?

**Answer:** A primary key uniquely identifies a row; a foreign key references a key in another table.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q2. DELETE versus UPDATE?

**Answer:** DELETE removes matching rows; UPDATE changes values in matching rows. Both require a carefully checked WHERE clause.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q3. What is SQL injection?

**Answer:** An attack where untrusted input changes SQL meaning. Parameterized queries keep input as data.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q4. Git versus GitHub?

**Answer:** Git is version control; GitHub hosts repositories and collaboration workflows.

**Practical follow-up:** Give an example from today's approved project and explain one limitation.

### Q5. How debug a failing test?

**Answer:** Read the traceback and assertion, reproduce the smallest case, compare expected and actual values, fix the cause and add a regression test.

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
