---
sidebar_position: 6
---

# POST /auth/reset

Reset a user's password using the reset token sent to their email address.

## Request
- **Method:** POST
- **Endpoint:** `/auth/reset`
- **Body:**
  ```json
  {
    "email": "user@example.com",
    "token": "<reset_token>",
    "newPassword": "yourNewPassword"
  }
  ```

## Response
- **Success:**
  ```json
  {
    "message": "Password has been reset successfully."
  }
  ```
- **Failure:**
  ```json
  {
    "message": "Invalid or expired reset token."
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/reset \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "token": "<reset_token>", "newPassword": "yourNewPassword"}'
``` 