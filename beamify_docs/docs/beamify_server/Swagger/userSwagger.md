---
sidebar_position: 2
---

# userSwagger.json

The `userSwagger.json` file documents all User API endpoints for Beamify Server. It defines the OpenAPI paths, request/response schemas, and descriptions for user-related operations.

**Endpoints covered:**
- `GET /users` — List all users (public, non-sensitive data)
- `GET /users/{id}` — Get user by ID
- `PUT /users/{id}` — Update user by ID
- `DELETE /users/{id}` — Delete user by ID
- `GET /users/me` — Get current authenticated user's profile

**How to extend:**
- Add new user-related endpoints to the `paths` object in this file.
- Update schemas and descriptions as the API evolves.

**Integration:**
- This file is loaded and merged into the main Swagger UI at `/v1/docs`.
- Changes here are reflected automatically in the interactive documentation. 