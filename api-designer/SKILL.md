---
name: api-designer
description: >
  Design clean REST APIs, define endpoints, request/response schemas, error handling, authentication.
  Use when user says "design an API", "what endpoints do I need", "API structure for X",
  "REST API for my app", "review my API design", "how should I structure this endpoint".
---
# API Designer

## URL Structure
GET    /resources       - list
POST   /resources       - create
GET    /resources/:id   - get one
PUT    /resources/:id   - replace
PATCH  /resources/:id   - update fields
DELETE /resources/:id   - delete

## Naming Rules
- Plural nouns: /users not /user
- Lowercase hyphens: /user-profiles
- No verbs: /users/123/activate not /activateUser

## Response Format
Success: { "data": {...}, "meta": {"page":1,"total":100} }
Error: { "error": {"code":"VALIDATION_ERROR","message":"...","field":"..."} }

## Status Codes
200 OK / 201 Created / 204 No Content
400 Bad Request / 401 Unauthorized / 403 Forbidden / 404 Not Found / 409 Conflict / 500 Error

## Auth
JWT: Authorization: Bearer <token>
API Key: X-API-Key: <key>
Always HTTPS

## Versioning
URL: /v1/users (recommended)
