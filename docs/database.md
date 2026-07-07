# Database Design

## Overview

CodeMentor AI uses **PostgreSQL** as its primary relational database.

The database is designed incrementally alongside the application's development. Instead of creating every table upfront, the schema evolves as new features are introduced.

This approach keeps the design maintainable, reduces unnecessary complexity, and mirrors how production systems are typically developed.

---

# Design Goals

The database is designed with the following principles:

- Normalize data where appropriate
- Avoid premature optimization
- Use foreign keys to maintain integrity
- Prefer explicit relationships
- Design for readability first
- Optimize with indexes only when necessary
- Evolve schema through Alembic migrations

---

# Database Technology

| Technology | Purpose |
|------------|---------|
| PostgreSQL | Primary relational database |
| SQLAlchemy | ORM |
| Alembic | Database migrations |

---

# Schema Evolution

The database will evolve over multiple phases.

---

# Phase 1 — Authentication

## Tables

- User
- RefreshToken
- Role (optional, if role-based access is introduced early)

### User

Stores application users.

Planned fields:

- id
- username
- email
- password_hash
- created_at
- updated_at

---

### RefreshToken

Stores refresh tokens used for JWT authentication.

Planned fields:

- id
- user_id
- token
- expires_at
- revoked
- created_at

---

# Phase 2 — Coding Problems

## Tables

- Problem
- Tag
- Company
- ProblemTag
- ProblemCompany
- TestCase

### Problem

Stores coding interview questions.

Planned fields:

- id
- title
- slug
- description
- difficulty
- constraints
- examples
- created_at

---

### Tag

Examples:

- Array
- Graph
- DP
- Binary Search

---

### Company

Examples:

- Google
- Amazon
- Microsoft

---

### TestCase

Stores hidden and sample test cases.

---

# Phase 3 — Submissions

## Tables

- Submission

Stores every solution submitted by a user.

Planned information includes:

- programming language
- submitted code
- execution status
- runtime
- memory usage
- submission time

---

# Phase 4 — AI

## Tables

- AIReview
- AIHint
- MockInterview

These tables store AI-generated responses and interview sessions.

---

# Phase 5 — Analytics

## Tables

- UserStatistics
- DailyActivity

These support dashboards and progress tracking.

---

# Planned Relationships

```

User
│
├── RefreshToken

├── Submission

└── MockInterview

Problem
│
├── TestCase

├── Submission

├── ProblemTag

└── ProblemCompany

Tag
│
└── ProblemTag

Company
│
└── ProblemCompany

Submission
│
└── AIReview

```

---

# Naming Conventions

The project follows the following naming conventions.

## Tables

Singular nouns.

Examples:

- User
- Problem
- Submission

---

## Primary Keys

Every table uses:

id

as the primary key.

---

## Foreign Keys

Foreign keys follow the pattern:

<entity>_id

Examples:

user_id

problem_id

submission_id

---

## Timestamps

Whenever applicable:

created_at

updated_at

Future tables may also include:

deleted_at

for soft deletion.

---

# Migration Strategy

Database schema changes will never be performed manually.

Every structural change will be introduced through Alembic migrations.

Each migration should:

- be small
- have a descriptive name
- be committed with the corresponding feature

Example:

```
Add User table

Add Submission table

Create Problem relationships
```

---

# Future Considerations

The following optimizations are intentionally deferred until required.

- Database indexing
- Full-text search
- Materialized views
- Read replicas
- Partitioning
- Query optimization

The project prioritizes correctness and maintainability before optimization.

---

# Guiding Principles

- Keep the schema simple.
- Add tables only when features require them.
- Avoid premature optimization.
- Preserve data integrity.
- Evolve through migrations.
- Document every schema change.