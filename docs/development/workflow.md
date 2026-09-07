# Development Workflow

This document describes the development workflow used in the Event-Driven Payment Processing Platform.

The project is both a software project and a learning laboratory. The goal is not only to implement features, but to understand the technical concepts, architectural decisions, trade-offs and failure scenarios behind them.

The development process therefore combines traditional engineering practices with AI-assisted development.

---

## Development Principles

### 1. Learn before implementing

Before introducing a new technology, pattern or architectural component, understand the problem it is intended to solve.

The default question is:

> What problem are we trying to solve?

and only then:

> Which solution is appropriate?

Technologies should not be added simply because they are popular or because they appear in the project's target job descriptions.

---

### 2. Start simple and evolve

The architecture should grow as the requirements grow.

Avoid introducing distributed-system complexity before there is a reason to do so.

For example:

```text
Initial

Payment Service
      ↓
 PostgreSQL
```

may later evolve into:

```text
Payment Service
      ↓
    Kafka
   ┌──┼──┐
   ↓  ↓  ↓
 Fraud Ledger Notification
```

The reason for each architectural change should be documented.

---

### 3. Optimize for learning, not only speed

AI and automation can make implementation faster, but completing a task is not the only objective.

I should be able to explain:

* what was implemented;
* why it was implemented;
* how it works;
* what could go wrong;
* what trade-offs exist;
* how it could be improved.

---

# Task Lifecycle

Each meaningful task should follow this general workflow:

```text
Kanban Task
    ↓
Learn
    ↓
Design
    ↓
Implement
    ↓
Test
    ↓
Break
    ↓
Review
    ↓
Document
    ↓
Done
```

Not every small task requires every step in the same depth, but important technical features should follow the full cycle.

---

## 1. Define the Task

Before coding, make sure the task has a clear objective.

A good task should describe:

* Goal
* Context
* Why it is needed
* Learning objectives
* Relevant constraints
* Definition of Done

Example:

```md
## Goal

Implement idempotent payment creation.

## Why

Repeated client requests must not create duplicate payments.

## Learning goals

- Understand idempotency.
- Understand race conditions.
- Understand Redis atomic operations.

## Definition of Done

- Idempotency key supported.
- Duplicate requests return the original result.
- Concurrent requests are handled safely.
- Tests cover duplicate and concurrent requests.
```

---

# 2. Learn

Before implementing an unfamiliar concept, study the minimum knowledge required.

The preferred order is:

```text
Problem
  ↓
Concept
  ↓
Possible solutions
  ↓
Trade-offs
```

Use documentation, books, articles, experiments and AI to build an initial mental model.

The objective is not to understand every detail before starting.

The objective is to understand enough to make an informed first design.

---

# 3. Design

Before writing significant amounts of code, describe the proposed solution.

For non-trivial tasks, consider:

* components involved;
* data flow;
* synchronous vs asynchronous communication;
* data ownership;
* consistency requirements;
* failure scenarios;
* concurrency;
* scalability;
* security;
* operational implications.

When relevant, create a small diagram.

Example:

```text
Client
  ↓
Payment Service
  ↓
Redis
  ↓
PostgreSQL
```

The design can be revised during implementation.

The objective is to make architectural reasoning explicit rather than designing everything implicitly through code.

---

# 4. Implement

Implement incrementally.

Prefer small changes that can be understood, tested and reviewed independently.

Avoid generating an entire feature or service at once.

A typical implementation sequence is:

```text
Domain model
    ↓
Application logic
    ↓
Persistence
    ↓
Infrastructure integration
    ↓
API / interface
    ↓
Tests
```

The exact order may vary depending on the task.

---

# 5. Test

Testing is part of implementation, not a final step.

Depending on the feature, consider:

### Unit tests

For isolated business logic.

### Integration tests

For interactions with components such as:

* PostgreSQL
* Redis
* Kafka

### End-to-end tests

For important user-facing flows.

### Concurrency tests

When behavior depends on simultaneous requests or consumers.

### Failure tests

When behavior depends on infrastructure failures or retries.

The type of test should reflect the kind of risk being introduced.

---

# 6. Break the System

A distributed system should not only be tested when everything is working.

For important infrastructure and architectural features, intentionally introduce failures.

Examples:

```text
Kafka unavailable
Redis unavailable
Database unavailable
Consumer crashes
Consumer becomes slow
Duplicate event
Network timeout
Message processing fails
Retry repeatedly fails
```

Ask:

> What happens to the payment?

Then determine:

* whether the behavior is acceptable;
* whether data can be lost;
* whether duplicate processing can occur;
* whether the system can recover;
* whether manual intervention is required.

Failure experiments should be documented when they produce meaningful learning.

---

# 7. Review

After implementation, review the feature from multiple perspectives.

### Correctness

Does it behave as intended?

### Maintainability

Is the design unnecessarily complex?

### Concurrency

Could race conditions occur?

### Reliability

What happens when dependencies fail?

### Performance

Could this become a bottleneck?

### Security

Are there sensitive data or authorization concerns?

### Architecture

Does the implementation fit the overall system?

AI can be used as a code and architecture reviewer during this step.

The goal is not to blindly accept AI suggestions, but to evaluate them.

---

# 8. Document

Important technical discoveries and decisions should be recorded.

Depending on the situation, use:

### Architecture Decision Record

When a meaningful architectural decision was made.

```text
docs/architecture/decisions/
```

### Experiment

When a behavior was investigated experimentally.

```text
docs/learning/experiments/
```

### Learning note

When the main outcome was understanding a concept.

```text
docs/learning/notes/
```

### Architecture documentation

When the implementation changes the system structure.

```text
docs/architecture/
```

Documentation should capture the reasoning, not only the final result.

---

# AI-Assisted Development Workflow

AI is intentionally part of the development process.

The objective is to use AI to increase productivity while maintaining technical ownership and understanding.

AI can act as:

* Teacher
* Pair programmer
* Design reviewer
* Code reviewer
* Debugging partner
* Adversarial tester
* System Design interviewer
* Documentation assistant

---

## Before Coding — Teacher

Use AI to understand unfamiliar concepts.

Prefer questions such as:

> Explain the problem before showing me the solution.

> What concepts do I need to understand before implementing this?

> What are the common approaches and their trade-offs?

Avoid immediately asking AI to generate the complete implementation.

---

## During Design — Design Reviewer

Present my proposed solution to AI.

Ask it to identify:

* missing assumptions;
* race conditions;
* failure scenarios;
* scalability concerns;
* consistency problems;
* unnecessary complexity;
* alternative approaches.

Prefer questions that challenge the design instead of asking AI to redesign everything immediately.

---

## During Implementation — Pair Programmer

Use AI for:

* explaining APIs and libraries;
* small implementation questions;
* debugging;
* test generation;
* boilerplate when appropriate;
* refactoring suggestions.

Implementation should remain incremental.

For unfamiliar concepts, use progressive assistance:

```text
Level 1 → Hint
Level 2 → Concept explanation
Level 3 → Pseudocode
Level 4 → Example implementation
```

Start with the lowest level that is useful.

---

## After Implementation — Code Reviewer

Ask AI to review the implementation with emphasis on:

* correctness;
* edge cases;
* concurrency;
* error handling;
* security;
* performance;
* reliability;
* maintainability.

Prefer review and feedback before requesting a complete rewrite.

---

## Failure Analysis — Adversarial Tester

Use AI to think beyond the happy path.

Ask:

> Assume this system is running in production. What could realistically fail?

Then select scenarios and reproduce them locally.

This step is particularly important for:

* Kafka;
* Redis;
* asynchronous processing;
* distributed transactions;
* retries;
* database interactions.

---

## Learning Validation — Teach Back

After implementing an important concept, explain it in my own words.

Ask AI to evaluate the explanation as a technical interviewer.

Example:

> Explain what is wrong or incomplete in my understanding of Kafka consumer groups. Do not rewrite my explanation immediately.

The goal is to verify actual understanding instead of relying on implementation success.

---

# Git Workflow

Each task should normally be developed in its own branch.

Example:

```bash
git checkout -b feature/payment-creation
```

Commits should be small and meaningful.

Examples:

```text
feat: add payment domain model
feat: add payment creation endpoint
test: add payment creation integration test
```

Avoid mixing unrelated changes in the same commit.

Pull Requests may be used even for solo development when doing so helps simulate a professional review process.

---

# Definition of Done

A task is considered complete when applicable:

* The intended behavior is implemented.
* Tests cover the relevant behavior.
* Error cases are handled.
* The implementation follows project conventions.
* Important failure scenarios have been considered.
* Relevant documentation has been updated.
* Architectural decisions have been recorded when necessary.
* The task is reflected accurately in `current-state.md`.

For larger features, the feature should also be explainable from a System Design perspective.

I should be able to answer:

> Why was this approach chosen?

> What alternatives were considered?

> What can go wrong?

> How does it scale?

> What happens when a dependency fails?

---

# Learning Log

For meaningful milestones, record:

```text
What I learned
What surprised me
What I broke
How I fixed it
What trade-off I discovered
How I would explain it in an interview
```

The purpose of the learning log is to turn implementation experience into reusable engineering knowledge.

---

# Overall Philosophy

The goal of this workflow is not to become dependent on AI or to avoid using AI.

The goal is to learn how to use AI effectively while becoming a stronger engineer.

The preferred relationship is:

```text
Human
  ↓
Problem understanding
  ↓
Architectural reasoning
  ↓
AI-assisted exploration
  ↓
Implementation
  ↓
Human review and understanding
```

AI should make the development loop faster, broader and more analytical — while I remain responsible for the decisions and understanding behind the system.
