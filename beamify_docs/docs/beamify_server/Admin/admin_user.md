# Admin User Management

All endpoints require authentication and the `SYSTEM_ADMINISTRATOR` role.

---

## Create User
**POST** `/v1/admin/users`

Creates a new user.

| Field      | Type   | Required | Description         |
|------------|--------|----------|---------------------|
| email      | string | Yes      | User's email        |
| username   | string | Yes      | User's username     |
| password   | string | Yes      | User's password     |
| ...        | ...    | ...      | Other user fields   |

**Request Example**
```json
{
  "email": "newuser@example.com",
  "username": "newuser",
  "password": "securePassword123"
}
```

**Response Example**
```json
{
  "_id": "userId",
  "email": "newuser@example.com",
  "username": "newuser",
  "roles": ["MEMBER"],
  ...
}
```

**Errors**
- 400: Validation error
- 403: Forbidden (not SYSTEM_ADMINISTRATOR)

---

## Update User
**PUT** `/v1/admin/users/{id}`

Updates an existing user.

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Request Example**
```json
{
  "username": "updateduser"
}
```

**Response Example**
```json
{
  "_id": "userId",
  "username": "updateduser",
  ...
}
```

---

## Delete User
**DELETE** `/v1/admin/users/{id}`

Deletes a user.

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Response Example**
```json
{ "message": "User deleted" }
```

---

## Ban User
**POST** `/v1/admin/users/{id}/ban`

Bans a user (sets `status.isBanned: true`).

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Response Example**
```json
{
  "_id": "userId",
  "status": { "isBanned": true }
}
```

---

## Timeout User
**POST** `/v1/admin/users/{id}/timeout`

Times out a user until a specified date/time.

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Request Example**
```json
{ "timeoutUntil": "2024-12-31T23:59:59Z" }
```

**Response Example**
```json
{
  "_id": "userId",
  "timeoutUntil": "2024-12-31T23:59:59Z"
}
```

---

## Suspend User
**POST** `/v1/admin/users/{id}/suspend`

Suspends a user (sets `status.isActive: false`).

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Response Example**
```json
{
  "_id": "userId",
  "status": { "isActive": false }
}
```

---

## Assign Role to User
**POST** `/v1/admin/users/{id}/roles`

Assigns a role to a user.

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Request Example**
```json
{ "role": "MODERATOR" }
```

**Response Example**
```json
{
  "_id": "userId",
  "roles": ["MEMBER", "MODERATOR"]
}
```

---

## Remove Role from User
**DELETE** `/v1/admin/users/{id}/roles`

Removes a role from a user.

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Request Example**
```json
{ "role": "MODERATOR" }
```

**Response Example**
```json
{
  "_id": "userId",
  "roles": ["MEMBER"]
}
```

---

## Assign Permission to User
**POST** `/v1/admin/users/{id}/permissions`

Assigns a permission directly to a user.

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Request Example**
```json
{ "permission": "MANAGE_USERS" }
```

**Response Example**
```json
{
  "_id": "userId",
  "permissions": ["MANAGE_USERS"]
}
```

---

## Remove Permission from User
**DELETE** `/v1/admin/users/{id}/permissions`

Removes a permission from a user.

| Parameter | Type   | In   | Required | Description      |
|-----------|--------|------|----------|------------------|
| id        | string | path | Yes      | User ID          |

**Request Example**
```json
{ "permission": "MANAGE_USERS" }
```

**Response Example**
```json
{
  "_id": "userId",
  "permissions": []
}
```

---
**All actions are audit-logged.** 