---
sidebar_position: 2
---

# POST /auth/login

Authenticate a user with their email/username and password. Returns a JWT token if credentials are valid.

## Request
- **Method:** POST
- **Endpoint:** `/auth/login`
- **Body:**
  ```json
  {
    "email": "user@example.com", // or "username": "user123"
    "password": "yourPassword"
  }
  ```

## Response
- **Success:**
  ```json
  {
    "token": "<JWT_TOKEN>",
    "user": {
      "_id": "...",
      "email": "user@example.com",
      "username": "user123",
      // ...other user fields
    }
  }
  ```
- **Failure:**
  ```json
  {
    "message": "Invalid credentials"
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "password": "yourPassword"}'
``` 