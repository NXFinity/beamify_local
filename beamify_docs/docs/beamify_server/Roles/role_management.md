# Role Management

This document explains how roles are managed and used in Beamify to control user access and permissions.

---

## What is a Role?
A role is a named collection of permissions. Assigning a role to a user grants them all the permissions associated with that role. Roles simplify access management by grouping related permissions together.

---

## Creating and Managing Roles
Roles are created and managed by administrators. Each role has:
- A unique name (e.g., `SYSTEM_ADMINISTRATOR`, `MEMBER`, `MODERATOR`)
- An optional description
- A set of permissions (by name)

**Example Role Definition**
```json
{
  "name": "MODERATOR",
  "description": "Moderator role",
  "permissions": ["MANAGE_USERS", "VIEW_AUDIT_LOGS"]
}
```

---

## Assigning Roles to Users
Users can have one or more roles. When a role is assigned to a user, they inherit all permissions from that role.

**Example**
- User A is assigned the `MEMBER` role (basic access)
- User B is assigned both `MEMBER` and `MODERATOR` roles (basic + moderation access)

---

## Role Hierarchies and Customization
Roles are flat (no built-in hierarchy), but you can create custom roles with any combination of permissions to fit your organization's needs.

**Best Practices:**
- Use descriptive names for roles
- Group permissions logically (e.g., all user management permissions in a `MODERATOR` role)
- Assign only the minimum roles necessary to each user (principle of least privilege)

---

## Example Built-in Roles
| Role Name            | Description                | Example Permissions                      |
|--------------------- |---------------------------|------------------------------------------|
| SYSTEM_ADMINISTRATOR | Full admin access         | MANAGE_USERS, MANAGE_ROLES, ...          |
| MEMBER               | Basic user access         | VIEW_SELF_PROFILE, EDIT_SELF_PROFILE     |
| MODERATOR            | Moderate user actions     | MANAGE_USERS, VIEW_AUDIT_LOGS            |

---

## Modifying Roles
Roles can be updated to add or remove permissions as your needs evolve. Removing a role from a user immediately revokes all permissions granted by that role.

---

## Direct Permissions vs. Roles
While permissions can be assigned directly to users for special cases, using roles is recommended for most scenarios. Roles make it easier to manage access for groups of users and maintain consistency.

---

## Audit Logging
All role assignments, updates, and removals are audit-logged for security and compliance.

---

For details on the API endpoints for managing roles, see the Admin API documentation. 