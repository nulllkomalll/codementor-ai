# System Architecture

## Overview

CodeMentor AI is a production-oriented, AI-powered coding interview preparation platform designed using a layered architecture. The project emphasizes maintainability, scalability, and separation of concerns while remaining simple enough for continuous feature development.

The architecture follows a monorepo approach where the frontend, backend, infrastructure, shared resources, and documentation are maintained in a single repository.

---

# High-Level Architecture

```
                     +----------------------+
                     |      React SPA       |
                     |  (Frontend Client)   |
                     +----------+-----------+
                                |
                           HTTP / HTTPS
                                |
                                ▼
                     +----------------------+
                     |     FastAPI API      |
                     |      (Backend)       |
                     +----------+-----------+
                                |
        +-----------------------+-----------------------+
        |                       |                       |
        ▼                       ▼                       ▼
+---------------+      +----------------+      +----------------+
| PostgreSQL    |      | Redis          |      | Celery Workers |
| Persistent DB |      | Cache / Queue  |      | Background Jobs|
+---------------+      +----------------+      +----------------+
                                |
                                ▼
                      +----------------------+
                      |    AI Providers      |
                      | OpenAI / Gemini APIs |
                      +----------------------+
```

---

# Architectural Goals

The project is designed around the following engineering goals:

- Maintainable codebase
- Clear separation of responsibilities
- Easy feature expansion
- Production-ready folder structure
- Modular backend architecture
- Scalable infrastructure
- Incremental development

---

# Repository Structure

```
codementor-ai/

├── frontend/
├── backend/
├── shared/
├── docker/
├── docs/
```

Each directory has a single responsibility.

| Folder | Responsibility |
|----------|---------------|
| frontend | React application |
| backend | FastAPI server |
| shared | Resources shared across services |
| docker | Container configuration |
| docs | Engineering documentation |

---

# Backend Architecture

The backend follows a layered architecture.

```
HTTP Request
      │
      ▼
Router (API Layer)
      │
      ▼
Service Layer
      │
      ▼
Repository Layer
      │
      ▼
Database
```

## Router Layer

Responsible for:

- Request validation
- Calling services
- Returning responses

Routes should remain thin and contain little or no business logic.

---

## Service Layer

Responsible for:

- Business logic
- Validation beyond request schemas
- Coordination between repositories
- Calling AI services
- Background task orchestration

The majority of application logic belongs here.

---

## Repository Layer

Responsible for:

- Database operations
- CRUD functionality
- Query optimization
- Data access abstraction

Repositories isolate the rest of the application from the database implementation.

---

## Database Layer

Persistent application data is stored in PostgreSQL using SQLAlchemy ORM.

Database schema evolution is managed using Alembic migrations.

---

# Frontend Architecture

The frontend follows a component-driven architecture.

```
Pages
   │
   ▼
Components
   │
   ▼
Hooks
   │
   ▼
Services
   │
   ▼
Backend API
```

Responsibilities:

- UI rendering
- Routing
- State management
- API communication
- User interactions

Business logic should remain minimal on the client whenever possible.

---

# Infrastructure

## PostgreSQL

Primary relational database.

Stores:

- Users
- Problems
- Submissions
- Analytics
- Interviews

---

## Redis

Redis will be introduced early to support:

- Caching
- Rate limiting
- Session storage
- Celery broker
- Temporary application state

---

## Celery

Used for asynchronous background tasks.

Examples include:

- AI code reviews
- Email notifications
- Report generation
- Analytics processing

Moving these operations outside the request-response cycle improves application responsiveness.

---

# AI Architecture (Planned)

Initially, AI features will communicate directly with external LLM providers.

```
Submission

↓

Prompt Builder

↓

LLM API

↓

Structured Response

↓

Backend

↓

Frontend
```

Future improvements may include:

- Prompt templates
- Retrieval-Augmented Generation (RAG)
- Embedding-based semantic search
- Conversation memory

---

# Security Principles

The project will prioritize secure development practices.

Planned measures include:

- JWT Authentication
- Password hashing
- Input validation
- Environment-based configuration
- SQL injection prevention through ORM
- CORS configuration
- Secure secret management

---

# Scalability Considerations

Although this project targets educational and portfolio purposes, it is designed with production concepts in mind.

Examples include:

- Layered architecture
- API versioning
- Background workers
- Redis caching
- Stateless backend services
- Containerized deployment

These decisions simplify future scaling and maintenance.

---

# Development Philosophy

The project is intentionally developed incrementally.

Each milestone focuses on one area of the system before introducing additional complexity.

This approach encourages:

- Smaller commits
- Easier debugging
- Better documentation
- Incremental learning
- Sustainable project growth

---

# Future Architecture Improvements

Potential future enhancements include:

- API Gateway
- Distributed caching
- Load balancing
- WebSocket support
- Monitoring with Prometheus
- Grafana dashboards
- OpenTelemetry tracing
- Kubernetes deployment

These improvements are intentionally deferred until the core platform is stable.

---

# Guiding Principles

Throughout development, the project follows these engineering principles:

- Simplicity before complexity
- Readability over cleverness
- Separation of concerns
- Single responsibility
- Incremental delivery
- Production-oriented design
- Continuous documentation

These principles guide architectural decisions as the platform evolves.