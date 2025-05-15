---
sidebar_position: 1
---

# Introduction

The Beamify Admin API provides a secure, robust interface for managing all critical aspects of the Beamify platform. It is designed for use by users with the `SYSTEM_ADMINISTRATOR` role and enforces strict access control on all endpoints.

## Key Features
- **User Management:** Create, update, delete, ban, timeout, suspend users; assign and remove roles and permissions.
- **Role Management:** Create, update, delete roles; assign permissions to roles.
- **Permission Management:** Create, update, delete permissions; assign permissions directly to users if needed.
- **Audit Logging:** All admin actions and errors are logged for traceability and compliance.
- **Security:** All endpoints require authentication and the `SYSTEM_ADMINISTRATOR` role. Fine-grained permission checks are supported.

## Access Control
- Only users with the `SYSTEM_ADMINISTRATOR` role can access admin endpoints.
- Permission-based middleware is available for even more granular control.

## API Structure
- All admin endpoints are prefixed with `/v1/admin/`.
- Endpoints are grouped by resource: users, roles, permissions, and logs.

## Documentation
- Each admin resource is documented in its own file (e.g., `admin_user.md`, `admin_role.md`, `admin_permission.md`).
- See those files for detailed endpoint usage, request/response formats, and examples.
