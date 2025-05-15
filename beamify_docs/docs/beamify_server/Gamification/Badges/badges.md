# Badges API

## Overview
The Badges API allows users and clients to view badges earned by users. Badges are visual achievements for milestones and are viewable both publicly (by username or ID) and privately (for the current user).

## Endpoints
All endpoints are under `/api/gamify/badges`.

### 1. List Badges by Username (Public)
- **GET** `/api/gamify/badges/user/:username`
- **Description:** List all badges for a given username. No sensitive user data is returned.
- **Auth:** None (public)
- **Example Request:**
  ```http
  GET /api/gamify/badges/user/johndoe
  ```
- **Example Response:**
  ```json
  [
    { "name": "First Post", "description": "You made your first post!", "icon": "first-post.png", "createdAt": "2024-06-01T12:00:00Z" },
    ...
  ]
  ```

### 2. Get Badge by ID (Public)
- **GET** `/api/gamify/badges/:id`
- **Description:** View a specific badge by its ID. No sensitive user data is returned.
- **Auth:** None (public)
- **Example Request:**
  ```http
  GET /api/gamify/badges/60a7b2c4e1d2f8a1b2c3d4e5
  ```
- **Example Response:**
  ```json
  { "name": "First Post", "description": "You made your first post!", "icon": "first-post.png", "createdAt": "2024-06-01T12:00:00Z" }
  ```

### 3. List My Badges (Private)
- **GET** `/api/gamify/badges/me`
- **Description:** List all badges for the current authenticated user. Returns full badge data.
- **Auth:** JWT required (Bearer token)
- **Example Request:**
  ```http
  GET /api/gamify/badges/me
  Authorization: Bearer <JWT>
  ```
- **Example Response:**
  ```json
  [
    { "_id": "...", "name": "First Post", "description": "You made your first post!", "icon": "first-post.png", "createdAt": "2024-06-01T12:00:00Z" },
    ...
  ]
  ```

## Notes
- Public endpoints never expose sensitive user data.
- Badges are sorted by most recent first.
- For real-time badge notifications, see [Gateway](../gateway.md). 