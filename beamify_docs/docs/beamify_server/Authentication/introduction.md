---
sidebar_position: 1
---

# Introduction

Beamify Server's authentication system is designed to provide secure, modern, and user-friendly access control for the Beamify platform. It supports a full suite of authentication and account management features, including:

- **User Registration** with email verification
- **Login** with JWT-based authentication
- **Email Verification** and token management
- **Password Reset** and **Forgot Password** flows
- **Resend and Reset Verification** for expired or lost tokens
- **Logout** and **Change Password**
- **Current User Check** (get authenticated user's profile)

The system is built using Passport.js (JWT strategy), secure password hashing, and robust email workflows. All endpoints are RESTful and follow a clear naming convention for easy integration.

Each endpoint is documented in detail in this section, including request/response formats and usage examples.
