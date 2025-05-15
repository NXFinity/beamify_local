---
sidebar_position: 2
---

# Structure

## Overview

Beamify Server is a modular Node.js/Express backend for the Beamify platform. It is organized for scalability, security, and extensibility, with clear separation of concerns across its directories. The structure supports a wide range of features, including user management, social networking, media streaming, e-commerce, gamification, messaging, notifications, and third-party integrations.

---

## Directory Structure

```
beamify_server/
├── beamify_server.js         # Main Express server setup
├── package.json              # Project metadata and dependencies
├── .env.development          # Environment variables for development
├── README.md                 # Project overview and setup
├── src/                      # Main source code
│   ├── api/                  # API endpoints, grouped by feature
│   │   ├── user/             # User management APIs
│   │   ├── social/           # Social features (posts, likes, etc.)
│   │   ├── media/            # Media streaming/handling APIs
│   │   ├── store/            # Store/payment APIs
│   │   ├── apps/             # Third-party integrations (Twitch, Discord, etc.)
│   │   ├── gamify/           # Gamification APIs
│   │   ├── tools/            # Platform tools (chat, events, commands, alerts)
│   │   ├── payment/          # Payment gateway and related endpoints
│   │   └── ...               # Other feature groups
│   ├── services/             # Business logic and integrations
│   │   ├── media/            # Media-related services
│   │   ├── email/            # Email sending services and templates
│   │   ├── messages/         # Messaging services
│   │   └── notifications/    # Notification services
│   ├── admin/                # Admin-specific logic and endpoints
│   ├── security/             # Authentication, authorization, validation (passport, pkce, etc.)
│   │   └── validation/       # Validation utilities (passport.js, pkce.js, etc.)
│   ├── db/                   # Database models, migrations, and logic (MongoDB/Mongoose)
│   │   ├── models/           # All data models, grouped by domain
│   │   │   ├── user/         # User and developer models
│   │   │   ├── social/       # Social models (post, comment, like, reply)
│   │   │   ├── gamify/       # Gamification models (quest, badge, achievement, gamify)
│   │   │   ├── store/        # Store models (vendor, product, etc.)
│   │   │   ├── media/        # Media models
│   │   │   ├── apps/         # Third-party app connection models
│   │   │   ├── admin/        # Role and permission models
│   │   │   ├── logs/         # Logging models
│   │   │   ├── notifications/# Notification models
│   │   │   └── messages/     # Messaging models
│   │   └── migrations/       # Database migration scripts
│   ├── utils/                # Utility functions (e.g., Stripe integration)
│   ├── logs/                 # Logging utilities
│   └── swagger/              # API documentation (Swagger/OpenAPI)
├── scripts/                  # Utility scripts
├── www/                      # Static files and views (EJS templates)
├── bin/                      # Server startup scripts
└── ...                       # Other config and support files
```

---

## Key Files

- **beamify_server.js**: Sets up the Express server, middleware, and error handling.
- **package.json**: Lists dependencies and scripts.
- **.env.development**: Stores environment variables (DB URIs, API keys, secrets, etc.).
- **README.md**: High-level project description and setup instructions.

---

## Notes
- API endpoints are grouped by feature in `src/api/` for modularity and scalability.
- Business logic and integrations are in `src/services/` (media, email, messages, notifications, etc.).
- Security and authentication are handled in `src/security/` (including validation utilities).
- Database models are in `src/db/models/`, organized by domain (user, social, gamify, store, media, apps, admin, logs, notifications, messages).
- Database migrations are in `src/db/migrations/`.
- Real-time and media features are supported via WebSockets and media services.
- Third-party integrations (Stripe, Discord, Twitch, etc.) are configured via environment variables and implemented in relevant `api/`, `services/`, or `utils/` subfolders.
- Messaging and notification systems are first-class features, with dedicated models and services.
- Tools and platform utilities (chat, events, commands, alerts) are modularized under `src/api/tools/`.

---

For more details on each module or integration, see the corresponding documentation sections.
