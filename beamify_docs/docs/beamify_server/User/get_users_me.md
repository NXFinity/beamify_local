---
sidebar_position: 4
---

# GET /users/me

Retrieve the profile of the currently authenticated user.

## Request
- **Method:** GET
- **Endpoint:** `/users/me`
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
curl -X GET https://api.beamify.online/v1/users/me \
  -H "Authorization: Bearer <JWT_TOKEN>"
``` 