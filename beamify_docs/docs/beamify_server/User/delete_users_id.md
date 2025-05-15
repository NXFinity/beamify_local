---
sidebar_position: 6
---

# DELETE /users/:id

Delete a user by their unique ID. Only the user or an admin can perform this action.

## Request
- **Method:** DELETE
- **Endpoint:** `/users/:id`
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`

## Response
- **Success:**
  ```json
  {
    "message": "User deleted."
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
curl -X DELETE https://api.beamify.online/v1/users/USER_ID \
  -H "Authorization: Bearer <JWT_TOKEN>"
``` 