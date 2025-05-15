---
sidebar_position: 1
---

# Introduction

Beamify Server uses Swagger (OpenAPI) to provide interactive, up-to-date API documentation for all public and internal endpoints. Swagger makes it easy for developers and integrators to explore, test, and understand the API, with clear request/response schemas and live examples.

**Key features:**
- Interactive API explorer at `/v1/docs`
- Documentation for all user, authentication, and future endpoints
- Modular structure: each API group (users, auth, etc.) has its own Swagger JSON file
- Automatically updated as the API evolves

To access the Swagger UI, start the server and visit:

```
http://localhost:3021/v1/docs
```

This section describes how Swagger is set up, how to extend it, and best practices for documenting new endpoints.
