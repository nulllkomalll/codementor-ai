# CodeMentor AI

> A production-grade AI-powered coding interview preparation platform built with modern full-stack technologies.

CodeMentor AI is an end-to-end platform designed to help developers prepare for technical interviews through coding practice, AI-assisted feedback, and progress analytics.

Unlike traditional coding platforms, CodeMentor AI aims to combine an online coding environment with intelligent AI features such as code reviews, hint generation, complexity analysis, mock interviews, and personalized learning insights.

This project is being built incrementally following production-grade software engineering practices with a strong emphasis on clean architecture, scalability, maintainability, and developer experience.

---

## 🎯 Project Goals

The objective of this project is not simply to build another coding platform, but to design and implement a system that demonstrates real-world backend engineering concepts including:

- Clean Architecture
- Scalable API Design
- Authentication & Authorization
- Distributed Caching
- Background Job Processing
- AI Integration
- Database Design
- Docker-based Development
- CI/CD
- Production-ready Software Engineering Practices

This project is intended to simulate how modern SaaS applications are developed in industry.

---

# Planned Features

## User Features

- User Registration & Login
- Secure JWT Authentication
- User Profiles
- Coding Problem Library
- Online Code Editor
- Code Submission
- Submission History
- Progress Tracking
- Personalized Dashboard

---

## AI Features

- AI Code Review
- AI Hint Generation
- Time & Space Complexity Analysis
- AI Explanation of Incorrect Solutions
- AI Mock Interviews
- Personalized Learning Recommendations

---

## Admin Features

- Problem Management
- Company & Tag Management
- Test Case Management
- User Management
- Analytics Dashboard

---

## Platform Features

- Dockerized Development
- PostgreSQL Database
- Redis Caching
- Background Workers (Celery)
- REST API
- Responsive Frontend
- Automated Testing
- CI/CD Pipeline

---

# Tech Stack

## Frontend

- React
- TypeScript
- Vite
- Tailwind CSS
- React Router
- React Query
- Axios

## Backend

- FastAPI
- SQLAlchemy
- Alembic
- PostgreSQL
- Redis
- Celery

## AI

- OpenAI / Gemini API
- Prompt Engineering
- Retrieval-Augmented Generation (RAG)
- Sentence Embeddings *(planned)*

## DevOps

- Docker
- Docker Compose
- GitHub Actions *(planned)*

---

# Project Structure

```
codementor-ai/

├── frontend/          # React application
├── backend/           # FastAPI backend
├── shared/            # Shared resources
├── docker/            # Docker configuration
├── docs/              # Project documentation
├── .env.example
├── .gitignore
└── README.md
```

---

# High-Level Architecture

```
                React Frontend
                       │
                       ▼
                FastAPI Backend
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
 PostgreSQL         Redis         Celery
        │                             │
        └──────────────┬──────────────┘
                       ▼
                  AI Services
```

---

# Development Roadmap

The project is being developed incrementally.

## Phase 0

- Project Planning
- Repository Setup
- Folder Structure
- Docker Scaffolding
- Documentation

## Phase 1

- Backend Infrastructure
- FastAPI
- Database Connection
- Redis Setup
- Health Checks

## Phase 2

- Authentication
- JWT
- Refresh Tokens
- User Management

## Phase 3

- Coding Problems
- CRUD APIs
- Tags
- Companies
- Test Cases

## Phase 4

- Online Code Execution
- Docker Sandbox
- Secure Execution Environment

## Phase 5

- Submission Management
- Submission History
- Statistics

## Phase 6

- AI Integration
- Code Review
- Hint Generation
- Complexity Analysis

## Phase 7

- Dashboard
- Analytics
- Progress Tracking

## Phase 8

- Mock Interviews

## Phase 9

- Notifications
- Background Jobs

## Phase 10

- Deployment
- CI/CD
- Monitoring
- Production Improvements

---

# Current Status

🚧 **Project is currently under active development.**

Current milestone:

- [x] Repository Initialization
- [x] Project Structure
- [ ] Backend Infrastructure
- [ ] Frontend Infrastructure
- [ ] Authentication
- [ ] Coding Problems
- [ ] Code Execution
- [ ] AI Features
- [ ] Dashboard
- [ ] Deployment

---

# Local Development

This section will be updated as development progresses.

Eventually the project will support:

```bash
git clone <repository>

docker compose up --build
```

---

# Documentation

Project documentation is maintained inside the `docs/` directory.

| Document | Description |
|----------|-------------|
| architecture.md | System architecture and design decisions |
| roadmap.md | Development roadmap |
| database.md | Database schema and ER diagrams |
| api.md | API documentation |
| decisions.md | Important engineering decisions |

---

# Engineering Principles

The project follows several software engineering principles throughout development.

- Clean Architecture
- SOLID Principles
- Separation of Concerns
- Layered Backend Architecture
- API Versioning
- Reusable Components
- Production-first Development
- Incremental Feature Delivery

---

# Learning Objectives

This project is also intended as a learning exercise in:

- Backend Engineering
- Full Stack Development
- AI Integration
- Distributed Systems
- Database Design
- Docker
- Software Architecture
- Production Engineering

---

# License

This project is currently being developed for educational and portfolio purposes.
