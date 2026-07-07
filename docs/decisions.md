# Architecture Decision Log

## Overview

This document records significant architectural and engineering decisions made throughout the development of CodeMentor AI.

Rather than documenting *what* was built, this document explains **why** specific technologies, patterns, and approaches were chosen.

Keeping a history of decisions helps maintain consistency as the project evolves and provides context for future contributors.

---

# Decision Record Format

Every architectural decision follows the same structure.

## Decision

A short description of the decision.

## Context

What problem needed to be solved?

## Options Considered

What alternatives were evaluated?

## Decision

Which option was chosen?

## Rationale

Why was this option selected?

## Consequences

What benefits and trade-offs result from this decision?

---

---

# ADR-001

## Title

Use a Monorepo Architecture

## Status

Accepted

## Date

July 2026

### Context

The project consists of multiple parts:

- Frontend
- Backend
- Infrastructure
- Documentation
- Shared resources

Managing these components across multiple repositories would increase complexity during development.

### Options Considered

1. Monorepo
2. Multiple repositories

### Decision

Use a monorepo.

### Rationale

A monorepo simplifies:

- local development
- dependency management
- documentation
- onboarding
- version control

Since this is a single product developed by one team, the advantages outweigh the drawbacks.

### Consequences

Pros

- Easier development
- Simpler project structure
- Single source of truth

Cons

- Larger repository over time

---

# ADR-002

## Title

Choose FastAPI for the Backend

## Status

Accepted

## Date

July 2026

### Context

The backend requires:

- REST APIs
- asynchronous support
- automatic documentation
- strong typing
- good developer experience

### Options Considered

- FastAPI
- Flask
- Django

### Decision

Use FastAPI.

### Rationale

FastAPI provides:

- excellent performance
- automatic OpenAPI generation
- modern Python typing
- dependency injection
- asynchronous programming support

These features align well with the project's goals.

### Consequences

Pros

- Fast development
- Type safety
- Built-in API documentation

Cons

- Smaller ecosystem than Django

---

# ADR-003

## Title

Choose PostgreSQL as the Primary Database

## Status

Accepted

## Date

July 2026

### Context

The platform contains relational data such as:

- users
- submissions
- problems
- interviews

These entities have well-defined relationships.

### Options Considered

- PostgreSQL
- MongoDB

### Decision

Use PostgreSQL.

### Rationale

Relational databases provide:

- ACID transactions
- foreign keys
- data integrity
- mature tooling

The application's data model is strongly relational.

### Consequences

Pros

- Reliable
- Mature
- Excellent SQL support

Cons

- Schema migrations require planning

---

# ADR-004

## Title

Adopt Layered Backend Architecture

## Status

Accepted

## Date

July 2026

### Context

Business logic should remain independent from HTTP routing and database access.

### Options Considered

1. Layered Architecture
2. Fat Controllers
3. MVC

### Decision

Use a layered architecture.

### Structure

```
Request

↓

Router

↓

Service

↓

Repository

↓

Database
```

### Rationale

Separating responsibilities improves:

- maintainability
- testing
- readability
- scalability

### Consequences

Pros

- Clear separation of concerns
- Easier testing
- Better maintainability

Cons

- Slightly more boilerplate

---

# ADR-005

## Title

Use Docker for Local Development

## Status

Accepted

## Date

July 2026

### Context

Developers should be able to run the project with minimal manual setup.

### Options Considered

- Native installations
- Docker

### Decision

Use Docker Compose.

### Rationale

Docker provides:

- consistent environments
- easier onboarding
- reproducible development setup

### Consequences

Pros

- Works consistently across environments
- Simplifies dependency management

Cons

- Slight learning curve
- Additional resource usage

---

# Future Decision Records

The following architectural decisions will be documented as they arise:

- Authentication strategy
- JWT implementation
- Refresh token storage
- Redis caching
- Code execution sandbox
- AI provider selection
- Background job processing
- Rate limiting strategy
- Deployment architecture
- Monitoring and observability
- Logging strategy
- API versioning changes

---

# Guiding Principles

Architectural decisions should be:

- intentional
- documented
- reviewed when necessary
- easy to understand

If a major design choice is made, it should be recorded here before implementation whenever practical.

This document serves as the project's architectural history and should evolve alongside the codebase.