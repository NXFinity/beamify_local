---
sidebar_position: 10
---

# GET /auth/me

Get the profile of the currently authenticated user.

## Request
- **Method:** GET
- **Endpoint:** `/auth/me`
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`

## Response
- **Success:**
  ```json
  {
    "_id": "...",
    "email": "user@example.com",
    "username": "user123",
    // ...other user fields
  }
  ```
- **Failure:**
  ```json
  {
    "message": "Not authenticated."
  }
  ```

## Usage Example
```bash
curl -X GET https://api.beamify.online/v1/auth/me \
  -H "Authorization: Bearer <JWT_TOKEN>"
``` 