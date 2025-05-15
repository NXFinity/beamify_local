# Permission Management

This document explains how permissions are managed and used in Beamify to control user access and actions.

---

## What is a Permission?
A permission is a rule that grants the ability to perform a specific action on a resource. Permissions are the most granular unit of access control in Beamify.

---

## Creating and Managing Permissions
Permissions are created and managed by administrators. Each permission has:
- A unique name (e.g., `MANAGE_USERS`, `VIEW_AUDIT_LOGS`)
- An optional description
- A resource (e.g., `users`, `profile`, `audit_logs`)
- An action (e.g., `manage`, `view`, `edit`)

**Example Permission Definition**
```json
{
  "name": "MANAGE_USERS",
  "description": "Can manage users",
  "resource": "users",
  "action": "manage"
}
```

---

## Assigning Permissions
Permissions are typically assigned to roles, which are then assigned to users. This allows for scalable and maintainable access control. In special cases, permissions can also be assigned directly to users.

**Example**
- The `MODERATOR` role might have the `MANAGE_USERS` and `VIEW_AUDIT_LOGS` permissions.
- A user can be given the `EDIT_SELF_PROFILE` permission directly if needed.

---

## Permission Structure
| Field       | Type   | Description                                 |
|-------------|--------|---------------------------------------------|
| name        | string | Unique name (UPPERCASE, e.g., MANAGE_USERS) |
| description | string | Optional description                        |
| resource    | string | Resource the permission applies to          |
| action      | string | Action allowed (e.g., manage, view, edit)   |

---

## Best Practices
- Use clear, descriptive names for permissions.
- Group permissions logically by resource and action.
- Assign permissions to roles rather than directly to users whenever possible.
- Grant only the permissions required for each role or user (principle of least privilege).

---

## Example Built-in Permissions
| Name               | Resource     | Action  | Description                                      |
|--------------------|-------------|---------|--------------------------------------------------|
| MANAGE_USERS       | users       | manage  | Can create, update, delete, ban, timeout users    |
| MANAGE_ROLES       | roles       | manage  | Can create, update, and delete roles              |
| MANAGE_PERMISSIONS | permissions | manage  | Can create, update, and delete permissions        |
| VIEW_AUDIT_LOGS    | audit_logs  | view    | Can view audit logs                              |
| VIEW_SELF_PROFILE  | profile     | view    | Can view own profile                             |
| EDIT_SELF_PROFILE  | profile     | edit    | Can edit own profile                             |

---

## Modifying Permissions
Permissions can be updated to change their description, resource, or action. Deleting a permission will remove it from all roles and users.

---

## Audit Logging
All permission assignments, updates, and removals are audit-logged for security and compliance.

---

For details on the API endpoints for managing permissions, see the Admin API documentation. 