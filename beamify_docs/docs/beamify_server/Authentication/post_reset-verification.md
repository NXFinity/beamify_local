---
sidebar_position: 11
---

# POST /auth/reset-verification

Generate and send a new email verification token if the previous one has expired or was lost.

## Request
- **Method:** POST
- **Endpoint:** `/auth/reset-verification`
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
    "message": "New verification token sent to your email."
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
curl -X POST https://api.beamify.online/v1/auth/reset-verification \
  -H "Content-Type: application/json" \
  -d '{"email": "user@example.com"}'
``` 