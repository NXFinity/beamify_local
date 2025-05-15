---
sidebar_position: 3
---

# authSwagger.json

The `authSwagger.json` file documents all Authentication API endpoints for Beamify Server. It defines the OpenAPI paths, request/response schemas, and descriptions for authentication-related operations.

**Endpoints covered:**
- `POST /auth/login` — User login
- `POST /auth/register` — User registration
- `POST /auth/verify` — Email verification
- `POST /auth/forgot` — Forgot password
- `POST /auth/reset` — Reset password
- `POST /auth/resend` — Resend verification email
- `POST /auth/logout` — Logout
- `POST /auth/change-password` — Change password
- `GET /auth/me` — Get current user profile
- `POST /auth/reset-verification` — Reset verification token

**How to extend:**
- Add new authentication-related endpoints to the `paths` object in this file.
- Update schemas and descriptions as the API evolves.

**Integration:**
- This file is loaded and merged into the main Swagger UI at `/v1/docs`.
- Changes here are reflected automatically in the interactive documentation. 