---
sidebar_position: 4
---

# POST /auth/verify

Verify a user's email address using the verification token sent to their email during registration.

## Request
- **Method:** POST
- **Endpoint:** `/auth/verify`
- **Body:**
  ```json
  {
    "email": "user@example.com",
    "token": "<verification_token>"
  }
  ```

## Response
- **Success:**
  ```json
  {
    "message": "Email verified successfully."
  }
  ```
- **Failure:**
  ```json
  {
    "message": "Invalid or expired verification token."
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/verify \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com", "token": "<verification_token>"}'
``` 