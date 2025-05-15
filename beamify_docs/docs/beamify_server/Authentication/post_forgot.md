---
sidebar_position: 5
---

# POST /auth/forgot

Initiate the password reset process by sending a reset token to the user's email address.

## Request
- **Method:** POST
- **Endpoint:** `/auth/forgot`
- **Body:**
  ```json
  {
    "email": "user@example.com"
  }
  ```

## Response
- **Success:**
  ```json
  {
    "message": "Password reset instructions sent to your email."
  }
  ```
- **Failure:**
  ```json
  {
    "message": "Email not found."
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/forgot \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com"}'
``` 