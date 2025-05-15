---
sidebar_position: 5
---

# PUT /users/:id

Update a user's information by their unique ID. Only the user or an admin can perform this action.

## Request
- **Method:** PUT
- **Endpoint:** `/users/:id`
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`
- **Body:**
  ```json
  {
    "email": "newemail@example.com",
    "username": "newusername",
    // ...other updatable fields
  }
  ```

## Response
- **Success:**
  ```json
  {
    "_id": "...",
    "email": "newemail@example.com",
    "username": "newusername",
    // ...other user fields
  }
  ```
- **Failure:**
  ```json
  {
    "message": "User not found or unauthorized."
  }
  ```

## Usage Example
```bash
curl -X PUT https://api.beamify.online/v1/users/USER_ID \
  -H "Authorization: Bearer <JWT_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"email": "newemail@example.com", "username": "newusername"}'
``` 