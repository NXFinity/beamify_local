---
sidebar_position: 2
---

# Structure

## Overview

Beamify Server is a modular Node.js/Express backend for the Beamify platform. It is organized for scalability, security, and extensibility, with clear separation of concerns across its directories.

---

## Directory Structure

```
beamify_server/
├── beamify_server.js                # Main Express beamify_server setup
├── package.json          # Project metadata and dependencies
├── .env.development      # Environment variables for development
├── README.md             # Project overview and setup
├── src/                  # Main source code
│   ├── api/              # API endpoints, grouped by feature
│   │   ├── user/         # User management APIs
│   │   ├── social/       # Social features (posts, likes, etc.)
│   │   ├── media/        # Media streaming/handling APIs
│   │   ├── store/        # Store/payment APIs
│   │   ├── apps/         # Third-party beamify_server integrations (Twitch, Discord, etc.)
│   │   ├── gamify/       # Gamification APIs
│   │   └── ...           # Other feature groups
│   ├── services/         # Business logic and integrations
│   │   ├── media/        # Media-related services
│   │   └── email/        # Email sending services
│   ├── admin/            # Admin-specific logic and endpoints
│   ├── security/         # Authentication, authorization, and security logic
│   ├── db/               # Database models and logic (MongoDB/Mongoose)
│   ├── utils/            # Utility functions
│   ├── logs/             # Logging utilities
│   └── swagger/          # API documentation (Swagger/OpenAPI)
├── scripts/              # Utility scripts
├── www/                  # Static files and views (EJS templates)
├── bin/                  # Server startup scripts
└── ...                   # Other config and support files
```

---

## Key Files

- **beamify_server.js**: Sets up the Express beamify_server, middleware, and error handling.
- **package.json**: Lists dependencies and scripts.
- **.env.development**: Stores environment variables (DB URIs, API keys, secrets, etc.).
- **README.md**: High-level project description and setup instructions.

---

## Notes
- API endpoints are grouped by feature in `src/api/` for modularity.
- Business logic and integrations are in `src/services/`.
- Security and authentication are handled in `src/security/`.
- Database models are in `src/db/` (uses MongoDB/Mongoose).
- Real-time and media features are supported via WebSockets and media services.
- Third-party integrations (Stripe, Discord, Twitch, etc.) are configured via environment variables and implemented in relevant `api/` or `services/` subfolders.

---

For more details on each module or integration, see the corresponding documentation sections.
