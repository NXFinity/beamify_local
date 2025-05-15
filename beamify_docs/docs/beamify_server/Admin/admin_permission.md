# Admin Permission Management

All endpoints require authentication and the `SYSTEM_ADMINISTRATOR` role.

---

## Create Permission
**POST** `/v1/admin/permissions`

Creates a new permission.

| Field        | Type     | Required | Description                                 |
|--------------|----------|----------|---------------------------------------------|
| name         | string   | Yes      | Permission name (unique, uppercase)         |
| description  | string   | No       | Description of the permission               |
| resource     | string   | Yes      | Resource this permission applies to         |
| action       | string   | Yes      | Action this permission allows (e.g. manage) |

**Request Example**
```json
{
  "name": "MANAGE_USERS",
  "description": "Can manage users",
  "resource": "users",
  "action": "manage"
}
```

**Response Example**
```json
{
  "_id": "permissionId",
  "name": "MANAGE_USERS",
  "description": "Can manage users",
  "resource": "users",
  "action": "manage"
}
```

**Errors**
- 400: Validation error (missing/duplicate fields)
- 403: Forbidden (not SYSTEM_ADMINISTRATOR)

---

## Get All Permissions
**GET** `/v1/admin/permissions`

Returns all permissions.

**Response Example**
```json
[
  { "_id": "permissionId", "name": "MANAGE_USERS", ... },
  { "_id": "permissionId", "name": "VIEW_AUDIT_LOGS", ... }
]
```

---

## Get Permission by ID
**GET** `/v1/admin/permissions/{id}`

| Parameter | Type   | In   | Required | Description     |
|-----------|--------|------|----------|-----------------|
| id        | string | path | Yes      | Permission ID   |

**Response Example**
```json
{
  "_id": "permissionId",
  "name": "MANAGE_USERS",
  "description": "Can manage users",
  "resource": "users",
  "action": "manage"
}
```

---

## Update Permission
**PUT** `/v1/admin/permissions/{id}`

Updates a permission.

| Parameter | Type   | In   | Required | Description     |
|-----------|--------|------|----------|-----------------|
| id        | string | path | Yes      | Permission ID   |

**Request Example**
```json
{
  "description": "Updated description",
  "resource": "users",
  "action": "manage"
}
```

**Response Example**
```json
{
  "_id": "permissionId",
  "name": "MANAGE_USERS",
  "description": "Updated description",
  "resource": "users",
  "action": "manage"
}
```

**Errors**
- 400: Validation error
- 403: Forbidden (not SYSTEM_ADMINISTRATOR)
- 404: Permission not found

---

## Delete Permission
**DELETE** `/v1/admin/permissions/{id}`

Deletes a permission.

| Parameter | Type   | In   | Required | Description     |
|-----------|--------|------|----------|-----------------|
| id        | string | path | Yes      | Permission ID   |

**Response Example**
```json
{ "message": "Permission deleted" }
```

**Errors**
- 403: Forbidden (not SYSTEM_ADMINISTRATOR)
- 404: Permission not found

---

## Assign Permission to User
**POST** `/v1/admin/users/{id}/permissions`

Assigns a permission directly to a user.

| Parameter | Type   | In   | Required | Description   |
|-----------|--------|------|----------|---------------|
| id        | string | path | Yes      | User ID       |

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

**Errors**
- 400: Validation error (missing/invalid permission)
- 403: Forbidden (not SYSTEM_ADMINISTRATOR)
- 404: User or permission not found

---

## Remove Permission from User
**DELETE** `/v1/admin/users/{id}/permissions`

Removes a permission from a user.

| Parameter | Type   | In   | Required | Description   |
|-----------|--------|------|----------|---------------|
| id        | string | path | Yes      | User ID       |

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

**Errors**
- 400: Validation error (missing/invalid permission)
- 403: Forbidden (not SYSTEM_ADMINISTRATOR)
- 404: User or permission not found

---
**All actions are audit-logged.** 