---
sidebar_position: 3
---

# Gamify Profiles API

## Overview
The Gamify Profiles API allows clients to view and manage user gamification profiles, which include points, level, exp, crystals, achievements, quests, and badges. These endpoints are primarily for internal or admin use, but some may be exposed for user profile viewing.

## Endpoints
All endpoints are under `/api/gamify`.

### 1. List All Gamify Profiles
- **GET** `/api/gamify`
- **Description:** List all gamify profiles. (Typically internal/admin use)
- **Auth:** May require admin privileges or JWT depending on deployment
- **Example Request:**
  ```http
  GET /api/gamify
  ```
- **Example Response:**
  ```json
  [
    { "_id": "...", "user": "...", "points": 100, "level": 2, "exp": 50, "crystals": 5, ... },
    ...
  ]
  ```

### 2. Get Gamify Profile by ID
- **GET** `/api/gamify/:id`
- **Description:** Get a specific gamify profile by its ID.
- **Auth:** May require JWT or be public for profile viewing
- **Example Request:**
  ```http
  GET /api/gamify/60a7b2c4e1d2f8a1b2c3d4e5
  ```
- **Example Response:**
  ```json
  { "_id": "...", "user": "...", "points": 100, "level": 2, "exp": 50, "crystals": 5, ... }
  ```

### 3. Update Gamify Profile
- **PUT** `/api/gamify/:id`
- **Description:** Update a gamify profile by its ID. (Typically internal/admin use)
- **Auth:** JWT required (and may require admin privileges)
- **Example Request:**
  ```http
  PUT /api/gamify/60a7b2c4e1d2f8a1b2c3d4e5
  Authorization: Bearer <JWT>
  Content-Type: application/json

  {
    "points": 200,
    "level": 3
  }
  ```
- **Example Response:**
  ```json
  { "_id": "...", "user": "...", "points": 200, "level": 3, ... }
  ```

### 4. Delete Gamify Profile
- **DELETE** `/api/gamify/:id`
- **Description:** Delete a gamify profile by its ID. (Typically internal/admin use)
- **Auth:** JWT required (and may require admin privileges)
- **Example Request:**
  ```http
  DELETE /api/gamify/60a7b2c4e1d2f8a1b2c3d4e5
  Authorization: Bearer <JWT>
  ```
- **Example Response:**
  ```json
  { "message": "Gamify profile deleted" }
  ```

## Notes
- Most users will not interact with these endpoints directly; they are used by the system and admin tools.
- For user-facing gamification data, see Activities, Badges, and Rewards endpoints.
- For admin endpoints, see the Admin documentation. 
