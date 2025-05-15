---
sidebar_position: 9
---

# POST /auth/change-password

Change the password for the current authenticated user. Requires the current password and the new password.

## Request
- **Method:** POST
- **Endpoint:** `/auth/change-password`
- **Headers:**
  - `Authorization: Bearer <JWT_TOKEN>`
- **Body:**
  ```json
  {
    "currentPassword": "oldPassword",
    "newPassword": "newPassword"
  }
  ```

## Response
- **Success:**
  ```json
  {
    "message": "Password changed successfully."
  }
  ```
- **Failure:**
  ```json
  {
    "message": "Current password is incorrect."
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/change-password \
  -H "Authorization: Bearer <JWT_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"currentPassword": "oldPassword", "newPassword": "newPassword"}'
``` 