---
sidebar_position: 2
---

# GET /users

Retrieve a list of all users. This is a public endpoint, but only non-sensitive, public user data is returned. Sensitive information such as email, roles, or internal IDs is not included in the response.

## Request
- **Method:** GET
- **Endpoint:** `/users`

## Response
- **Success:**
  ```json
  [
    {
      "username": "user123",
      "profile": {
        "displayName": "User 123",
        "avatar": "https://example.com/avatar.png"
      }
      // ...other public fields
    },
    // ...more users
  ]
  ```

## Usage Example
```bash
curl -X GET https://api.beamify.online/v1/users
``` 