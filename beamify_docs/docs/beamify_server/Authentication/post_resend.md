---
sidebar_position: 7
---

# POST /auth/resend

Resend the email verification token to a user who has not yet verified their account.

## Request
- **Method:** POST
- **Endpoint:** `/auth/resend`
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
    "message": "Verification email resent."
  }
  ```
- **Failure:**
  ```json
  {
    "message": "User already verified or email not found."
  }
  ```

## Usage Example
```bash
curl -X POST https://api.beamify.online/v1/auth/resend \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com"}'
``` 