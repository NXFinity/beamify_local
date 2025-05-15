---
sidebar_position: 3
---

# POST /auth/register

Register a new user account. Requires email verification. Automatically creates all associated user models (developer, gamify, media, etc.).

## Request
- **Method:** POST
- **Endpoint:** `/auth/register`
- **Body:**
  ```json
  {
    "email": "user@example.com",
    "username": "user123",
    "password": "yourPassword"
  }
  ```

## Response
- **Success:**
  ```json
  {
    "message": "Registration successful. Please check your email to verify your account."
  }
  ```
- **Failure:**
  ```json
  {
    "message": "Email already in use"
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/register \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "username": "user123", "password": "yourPassword"}'
``` 