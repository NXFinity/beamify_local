---
sidebar_position: 1
---

# Introduction

The Beamify Permission System is the foundation of access control throughout the platform. Permissions define the specific actions a user can perform on particular resources (such as 'manage users', 'view audit logs', or 'edit profile').

Permissions are the building blocks of roles: each role is a named collection of permissions. By assigning permissions to roles, and roles to users, Beamify enables fine-grained, scalable, and secure access management.

## What is a Permission?
A permission grants the ability to perform a specific action (like 'manage', 'view', or 'edit') on a resource (like 'users', 'roles', or 'profile').

## Why Use Permissions?
- **Granular Control:** Define exactly what actions are allowed on each resource.
- **Flexibility:** Combine permissions into roles to fit your organization's needs.
- **Security:** Enforce the principle of least privilege by granting only the permissions required for each role or user.

## How Permissions Work in Beamify
- Permissions are created and managed by administrators.
- Each permission has a unique name, an optional description, a resource, and an action.
- Permissions are typically assigned to roles, but can also be assigned directly to users for special cases.

## Example Permissions
- **MANAGE_USERS:** Can create, update, delete, ban, timeout, and suspend users.
- **VIEW_AUDIT_LOGS:** Can view audit logs.
- **EDIT_SELF_PROFILE:** Can edit own profile.

See the following documentation for details on managing permissions, assigning permissions to roles and users, and best practices.
