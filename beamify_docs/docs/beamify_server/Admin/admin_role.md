# Admin Role Management

All endpoints require authentication and the `SYSTEM_ADMINISTRATOR` role.

---

## Create Role
**POST** `/v1/admin/roles`

Creates a new role.

| Field        | Type     | Required | Description                       |
|--------------|----------|----------|-----------------------------------|
| name         | string   | Yes      | Role name (unique, uppercase)     |
| description  | string   | No       | Description of the role           |
| permissions  | string[] | No       | Array of permission names         |

**Request Example**
```json
{
  "name": "MODERATOR",
  "description": "Moderator role",
  "permissions": ["MANAGE_USERS"]
}
```

**Response Example**
```json
{
  "_id": "roleId",
  "name": "MODERATOR",
  "description": "Moderator role",
  "permissions": ["MANAGE_USERS"]
}
```

**Errors**
- 400: Validation error
- 403: Forbidden (not SYSTEM_ADMINISTRATOR)

---

## Get All Roles
**GET** `/v1/admin/roles`

Returns all roles.

**Response Example**
```json
[
  { "_id": "roleId", "name": "SYSTEM_ADMINISTRATOR", ... },
  { "_id": "roleId", "name": "MEMBER", ... }
]
```

---

## Get Role by ID
**GET** `/v1/admin/roles/{id}`

| Parameter | Type   | In   | Required | Description |
|-----------|--------|------|----------|-------------|
| id        | string | path | Yes      | Role ID     |

**Response Example**
```json
{
  "_id": "roleId",
  "name": "MODERATOR",
  ...
}
```

---

## Update Role
**PUT** `/v1/admin/roles/{id}`

Updates a role.

| Parameter | Type   | In   | Required | Description |
|-----------|--------|------|----------|-------------|
| id        | string | path | Yes      | Role ID     |

**Request Example**
```json
{
  "description": "Updated description",
  "permissions": ["MANAGE_USERS", "VIEW_AUDIT_LOGS"]
}
```

**Response Example**
```json
{
  "_id": "roleId",
  "name": "MODERATOR",
  "description": "Updated description",
  "permissions": ["MANAGE_USERS", "VIEW_AUDIT_LOGS"]
}
```

---

## Delete Role
**DELETE** `/v1/admin/roles/{id}`

Deletes a role.

| Parameter | Type   | In   | Required | Description |
|-----------|--------|------|----------|-------------|
| id        | string | path | Yes      | Role ID     |

**Response Example**
```json
{ "message": "Role deleted" }
```

---
**All actions are audit-logged.** 