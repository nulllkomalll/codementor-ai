# Contributing to CodeMentor AI

First off, thank you for taking the time to contribute to **CodeMentor AI**.

Although this project is currently maintained by a single developer, it is developed using engineering practices commonly followed in professional software teams. This document defines the development workflow, coding standards, Git conventions, and review process to ensure consistency throughout the project's lifecycle.

As the project grows, this guide will evolve alongside it.

---

# Table of Contents

- Project Philosophy
- Development Workflow
- Getting Started
- Repository Structure
- Branch Naming Convention
- Commit Message Convention
- Coding Guidelines
- Documentation Requirements
- Testing Expectations
- Pull Request Guidelines
- Code Review Checklist
- Reporting Issues
- Future Contributions

---

# Project Philosophy

CodeMentor AI is built with the following engineering principles:

- Simplicity over cleverness
- Readability over brevity
- Incremental development
- Small, focused commits
- Documentation-first mindset
- Production-oriented architecture
- Continuous refactoring
- Maintainability over premature optimization

Every contribution should move the project toward these goals.

---

# Development Workflow

Development follows an incremental approach.

Each feature should progress through the following stages:

1. Understand the problem.
2. Design the solution.
3. Update documentation if required.
4. Implement the feature.
5. Test the implementation.
6. Review the code.
7. Commit with a meaningful message.
8. Push changes.

Large features should be broken into multiple smaller commits whenever practical.

---

# Getting Started

## Clone the Repository

```bash
git clone <repository-url>
cd codementor-ai
```

## Environment Setup

Detailed setup instructions will be added as infrastructure is completed.

Eventually, local development will require:

- Docker
- Docker Compose
- Python
- Node.js
- PostgreSQL
- Redis

The recommended development workflow will be:

```bash
docker compose up --build
```

---

# Repository Structure

```
codementor-ai/

├── frontend/
├── backend/
├── shared/
├── docker/
├── docs/
├── README.md
└── CONTRIBUTING.md
```

Each directory has a clearly defined responsibility.

Contributors should avoid placing files outside their intended location.

---

# Branch Naming Convention

Use descriptive branch names.

## Features

```
feature/authentication

feature/problem-service

feature/code-execution

feature/dashboard

feature/ai-review
```

## Bug Fixes

```
fix/login-validation

fix/docker-build

fix/api-pagination
```

## Documentation

```
docs/readme-update

docs/api-documentation
```

## Refactoring

```
refactor/repository-layer

refactor/project-structure
```

## Testing

```
test/auth-service

test/problem-api
```

Avoid generic branch names such as:

```
new

temp

work

changes

update
```

---

# Commit Message Convention

The project follows the Conventional Commits specification.

## Feature

```
feat: implement JWT authentication
```

## Bug Fix

```
fix: resolve duplicate email validation
```

## Documentation

```
docs: update architecture documentation
```

## Refactoring

```
refactor: simplify repository layer
```

## Testing

```
test: add authentication service tests
```

## Chore

```
chore: update development dependencies
```

## Style

```
style: format backend code
```

Commit messages should:

- be concise
- use the imperative mood
- describe a single logical change

---

# Coding Guidelines

The project follows the coding standards documented in:

```
docs/code_style.md
```

General expectations include:

- Write readable code.
- Prefer explicit code over implicit behavior.
- Keep functions focused.
- Avoid unnecessary complexity.
- Remove dead code.
- Minimize duplication.

---

# Documentation Requirements

Documentation should evolve alongside the code.

Whenever a significant architectural change is introduced, update the relevant documentation.

Possible files include:

```
docs/architecture.md

docs/database.md

docs/api.md

docs/roadmap.md

docs/decisions.md
```

Documentation should explain **why** a decision was made rather than simply describing what the code does.

---

# Testing Expectations

Every completed feature should be tested before merging.

Testing strategy includes:

- Unit Tests
- Integration Tests
- API Tests

As the project grows, automated tests will become part of the CI pipeline.

Before committing:

- Ensure the application starts successfully.
- Verify affected functionality manually.
- Run the available test suite.

---

# Pull Request Guidelines

Although this project is currently maintained by a single developer, all features should be developed as though they will be reviewed by another engineer.

A pull request should:

- solve one problem
- remain reasonably small
- include meaningful commit history
- update documentation if needed
- avoid unrelated changes

Large pull requests should be split into multiple smaller ones whenever possible.

---

# Code Review Checklist

Before merging a feature, verify the following:

## Architecture

- Does the implementation follow the project's architecture?
- Is business logic placed in the service layer?
- Are repositories responsible only for database operations?

## Readability

- Are names meaningful?
- Are functions reasonably short?
- Is the code easy to understand?

## Maintainability

- Is duplication minimized?
- Can future developers understand the implementation?
- Are abstractions justified?

## Documentation

- Has documentation been updated?
- Are new decisions recorded if necessary?

## Testing

- Has the feature been tested?
- Do existing tests still pass?

---

# Reporting Issues

When reporting an issue, include:

- Expected behavior
- Actual behavior
- Steps to reproduce
- Relevant logs
- Environment information

Clear issue reports significantly reduce debugging time.

---

# Future Contributions

At present, CodeMentor AI is primarily a personal engineering and learning project.

External contributions may be considered in the future.

Until then, this document primarily serves as the project's internal development guide and engineering workflow.

---

# Acknowledgements

Thank you for taking the time to read these guidelines.

Following consistent engineering practices helps keep the project maintainable, scalable, and enjoyable to work on as it evolves.