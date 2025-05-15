# Rewards API

## Overview
The Rewards API allows users and clients to view rewards (achievements) earned by users. Rewards are granted for special actions or milestones and are viewable both publicly (by username or ID) and privately (for the current user).

## Endpoints
All endpoints are under `/api/gamify/rewards`.

### 1. List Rewards by Username (Public)
- **GET** `/api/gamify/rewards/user/:username`
- **Description:** List all rewards for a given username. No sensitive user data is returned.
- **Auth:** None (public)
- **Example Request:**
  ```http
  GET /api/gamify/rewards/user/johndoe
  ```
- **Example Response:**
  ```json
  [
    { "title": "First Login", "description": "You logged in for the first time!", "icon": "first-login.png", "dateAchieved": "2024-06-01T12:00:00Z" },
    ...
  ]
  ```

### 2. Get Reward by ID (Public)
- **GET** `/api/gamify/rewards/:id`
- **Description:** View a specific reward by its ID. No sensitive user data is returned.
- **Auth:** None (public)
- **Example Request:**
  ```http
  GET /api/gamify/rewards/60a7b2c4e1d2f8a1b2c3d4e5
  ```
- **Example Response:**
  ```json
  { "title": "First Login", "description": "You logged in for the first time!", "icon": "first-login.png", "dateAchieved": "2024-06-01T12:00:00Z" }
  ```

### 3. List My Rewards (Private)
- **GET** `/api/gamify/rewards/me`
- **Description:** List all rewards for the current authenticated user. Returns full reward data.
- **Auth:** JWT required (Bearer token)
- **Example Request:**
  ```http
  GET /api/gamify/rewards/me
  Authorization: Bearer <JWT>
  ```
- **Example Response:**
  ```json
  [
    { "_id": "...", "title": "First Login", "description": "You logged in for the first time!", "icon": "first-login.png", "dateAchieved": "2024-06-01T12:00:00Z" },
    ...
  ]
  ```

## Notes
- Public endpoints never expose sensitive user data.
- Rewards are sorted by most recent first.
- For real-time reward notifications, see [Gateway](../gateway.md). 