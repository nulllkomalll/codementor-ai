# API Design

## Overview

CodeMentor AI exposes a RESTful API that serves the frontend application and future third-party integrations.

The API is designed to be:

- Consistent
- Predictable
- Versioned
- Well documented
- Easy to extend

All endpoints will follow common naming conventions and standardized response formats.

---

# Base URL

During development:

```
http://localhost:8000
```

API Version:

```
/api/v1
```

Example:

```
GET /api/v1/health
```

Future API versions may be introduced without breaking existing clients.

---

# API Principles

The API follows these principles:

- RESTful design
- Stateless requests
- JSON request and response bodies
- Consistent HTTP status codes
- Predictable error responses
- Versioned endpoints
- Thin controllers (business logic belongs in services)

---

# Content Type

Requests:

```
Content-Type: application/json
```

Responses:

```
application/json
```

---

# HTTP Methods

| Method | Purpose |
|---------|----------|
| GET | Retrieve resources |
| POST | Create resources |
| PUT | Replace a resource |
| PATCH | Partially update a resource |
| DELETE | Remove a resource |

---

# URL Naming Convention

Use plural nouns.

Good:

```
/users

/problems

/submissions
```

Avoid:

```
/getUsers

/createProblem

/deleteSubmission
```

Resources should represent nouns rather than actions.

---

# API Versioning

Every endpoint begins with:

```
/api/v1/
```

Example:

```
GET /api/v1/problems

POST /api/v1/auth/login

GET /api/v1/users/me
```

Future versions:

```
/api/v2/...
```

---

# Planned Endpoints

## Health

```
GET /health
```

Returns application health status.

---

## Authentication

```
POST /auth/register

POST /auth/login

POST /auth/refresh

POST /auth/logout
```

---

## Users

```
GET /users/me

PATCH /users/me
```

---

## Problems

```
GET /problems

GET /problems/{id}

POST /problems

PATCH /problems/{id}

DELETE /problems/{id}
```

---

## Submissions

```
POST /submissions

GET /submissions

GET /submissions/{id}
```

---

## Dashboard

```
GET /dashboard
```

---

## AI

```
POST /ai/review

POST /ai/hint

POST /ai/complexity
```

---

# Response Format

Successful responses follow a consistent structure.

Example:

```json
{
  "success": true,
  "message": "Request completed successfully.",
  "data": {}
}
```

---

# Error Response Format

Errors use the following format.

```json
{
  "success": false,
  "message": "Validation failed.",
  "errors": [
    {
      "field": "email",
      "message": "Invalid email address."
    }
  ]
}
```

Using a consistent structure simplifies frontend error handling.

---

# HTTP Status Codes

| Status Code | Meaning |
|-------------|----------|
| 200 | Success |
| 201 | Resource Created |
| 204 | No Content |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Resource Not Found |
| 409 | Conflict |
| 422 | Validation Error |
| 500 | Internal Server Error |

---

# Authentication

Protected endpoints require a JWT access token.

Example:

```
Authorization: Bearer <access_token>
```

Authentication will be implemented in a later development phase.

---

# Pagination

Collection endpoints will support pagination.

Example:

```
GET /problems?page=1&limit=20
```

Response:

```json
{
  "success": true,
  "data": {
    "items": [],
    "page": 1,
    "limit": 20,
    "total": 125
  }
}
```

---

# Filtering

Example:

```
GET /problems?difficulty=easy

GET /problems?tag=array

GET /problems?company=google
```

Filters may be combined.

---

# Sorting

Example:

```
GET /problems?sort=created_at

GET /problems?sort=-created_at
```

Prefixing a field with `-` indicates descending order.

---

# API Documentation

The backend will automatically expose OpenAPI documentation.

FastAPI provides:

```
/docs
```

Swagger UI

and

```
/redoc
```

ReDoc documentation.

These are available only in development unless explicitly enabled in production.

---

# Rate Limiting

Rate limiting is planned for future releases to protect API resources and prevent abuse.

Likely implementation:

- Redis
- Token Bucket algorithm

---

# Future Improvements

Potential future enhancements include:

- API Keys
- WebSockets
- Streaming responses
- GraphQL exploration
- Request tracing
- API metrics

These features are intentionally deferred until the core REST API is stable.

---

# Guiding Principles

Every API endpoint should be:

- Easy to understand
- Predictable
- Well documented
- Backward compatible
- Consistent with existing conventions

New endpoints should follow the same design patterns established in this document.