---
sidebar_position: 8
---

# POST /auth/logout

Logs out the current user. For JWT-based authentication, this is typically handled client-side by deleting the token, but you may implement server-side token blacklisting if needed.

## Request
- **Method:** POST
- **Endpoint:** `/auth/logout`
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`

## Response
- **Success:**
  ```json
  {
    "message": "User logged out successfully."
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/logout \
  -H "Authorization: Bearer <JWT_TOKEN>"
``` 