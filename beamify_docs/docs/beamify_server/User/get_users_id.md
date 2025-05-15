---
sidebar_position: 3
---

# GET /users/:id

Retrieve a user by their unique ID.

## Request
- **Method:** GET
- **Endpoint:** `/users/:id`
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
    "message": "User not found."
  }
  ```

## Usage Example
```bash
curl -X GET https://api.beamify.online/v1/users/USER_ID \
  -H "Authorization: Bearer <JWT_TOKEN>"
``` 