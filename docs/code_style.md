# Code Style Guide

## Overview

This document defines the coding standards and engineering conventions followed throughout CodeMentor AI.

The objective is not to enforce personal preferences, but to create a codebase that is:

- Consistent
- Readable
- Maintainable
- Easy to review
- Easy to extend

Whenever there is uncertainty, prioritize **clarity over cleverness**.

---

# General Principles

Every line of code should answer two questions:

1. Is this easy to understand?
2. Will another developer understand this six months from now?

Good code is not measured by how little is written, but by how easily it can be maintained.

---

# Engineering Principles

The project follows these principles:

- SOLID Principles
- Separation of Concerns
- DRY (Don't Repeat Yourself)
- KISS (Keep It Simple, Stupid)
- YAGNI (You Aren't Gonna Need It)
- Composition over Inheritance
- Explicit over Implicit

---

# Project Structure

Every folder should have a single responsibility.

Example:

```
backend/

app/

api/

services/

repositories/

models/

schemas/

middleware/

utils/
```

Avoid placing unrelated files together.

---

# Naming Conventions

## Variables

Use descriptive names.

Good

```python
user_count
problem_id
submission_result
```

Bad

```python
x
data
temp
obj
```

---

## Functions

Functions should describe an action.

Good

```python
create_user()

calculate_score()

get_problem_by_id()
```

Avoid

```python
user()

process()

run()
```

---

## Classes

Use PascalCase.

```python
UserService

ProblemRepository

SubmissionSchema
```

---

## Constants

Use UPPER_SNAKE_CASE.

```python
MAX_RETRIES

DEFAULT_TIMEOUT

JWT_EXPIRATION_MINUTES
```

---

## Files

Use lowercase with underscores.

```
user_service.py

problem_repository.py

auth_router.py
```

Avoid

```
UserService.py

ProblemRepository.py
```

---

# Backend Guidelines

## Layer Responsibilities

### Router

Responsible for:

- receiving requests
- validating input
- calling services
- returning responses

Never place business logic inside routes.

---

### Service

Responsible for:

- business rules
- validation
- orchestration
- AI interaction

Most application logic belongs here.

---

### Repository

Responsible only for:

- database queries
- CRUD operations
- persistence

Repositories should never contain business logic.

---

### Models

Represent database tables only.

---

### Schemas

Represent request and response validation.

---

# Function Design

Functions should ideally perform one task.

Good

```python
create_user()
```

Avoid

```python
create_user_and_send_email_and_generate_report()
```

Split responsibilities whenever possible.

---

# Function Length

Prefer functions under **40 lines**.

If a function becomes difficult to scan, consider extracting helper functions.

---

# Class Size

Classes should have a single responsibility.

If a class grows beyond one clear purpose, consider splitting it.

---

# Comments

Write comments that explain **why**, not **what**.

Good

```python
# Cache results to reduce repeated database queries.
```

Avoid

```python
# Increment i
i += 1
```

The code should explain *what*.

Comments should explain *why*.

---

# Error Handling

Never silently ignore exceptions.

Good

```python
try:
    ...
except Exception:
    logger.exception(...)
    raise
```

Avoid

```python
except:
    pass
```

---

# Logging

Use structured logging.

Good

```python
logger.info("User created", extra={"user_id": user.id})
```

Avoid

```python
print("User created")
```

Production code should never rely on print statements for debugging.

---

# Configuration

Never hardcode:

- passwords
- API keys
- secrets
- database URLs

Use environment variables.

---

# Database Guidelines

- Use migrations.
- Avoid raw SQL unless necessary.
- Use foreign keys.
- Add indexes only when justified.
- Keep transactions small.

---

# API Design

Endpoints should use nouns instead of verbs.

Good

```
GET /problems

POST /submissions
```

Avoid

```
/getProblems

/createSubmission
```

---

# Response Format

Responses should remain consistent throughout the application.

Example

```json
{
    "success": true,
    "message": "Problem created successfully.",
    "data": {}
}
```

---

# Frontend Guidelines

## Components

Components should be:

- reusable
- small
- focused

Avoid creating components that handle multiple unrelated responsibilities.

---

## Hooks

Move reusable logic into custom hooks.

Avoid duplicating state management.

---

## Services

API requests belong inside the service layer.

Avoid making HTTP requests directly inside components.

---

## State

Keep state as local as possible.

Only promote state when it truly needs to be shared.

---

# Imports

Group imports consistently.

Example

```python
# Standard library

# Third-party packages

# Local project imports
```

Avoid random import ordering.

---

# Formatting

Follow the project's formatter and linter configuration.

Do not manually fight the formatter.

Formatting should be automated whenever possible.

---

# Git Guidelines

Prefer small commits.

Good

```
feat: implement user registration

fix: validate duplicate emails

docs: update authentication flow
```

Avoid combining unrelated changes into one commit.

---

# Documentation

Every significant architectural decision should update the relevant documentation.

Keep documentation synchronized with the implementation.

---

# Testing Philosophy

Test behavior, not implementation details.

Good tests should:

- be deterministic
- be isolated
- be readable
- be repeatable

---

# Performance

Do not optimize prematurely.

Follow this order:

1. Correctness
2. Readability
3. Maintainability
4. Performance

Measure performance before optimizing.

---

# Security

Always assume user input is untrusted.

Validate:

- request bodies
- query parameters
- path parameters

Never expose internal implementation details in API responses.

---

# Refactoring

Refactor continuously.

Small refactors performed regularly are preferable to large rewrites.

When refactoring:

- preserve behavior
- improve readability
- reduce duplication
- simplify complexity

---

# Definition of Done

A feature is considered complete only when:

- Implementation is complete.
- Code follows project conventions.
- Documentation is updated.
- Tests pass.
- No obvious technical debt has been introduced.
- The application builds successfully.

---

# Final Principle

Future you is another developer.

Write code that future you will appreciate reading.