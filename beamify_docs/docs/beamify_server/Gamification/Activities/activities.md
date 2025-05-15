# Activities API

## Overview
The Activities API allows users and clients to view user activity logs. Activities are actions performed by users (e.g., posting, logging in) and are viewable both publicly (by username or ID) and privately (for the current user).

## Endpoints
All endpoints are under `/api/gamify/activities`.

### 1. List Activities by Username (Public)
- **GET** `/api/gamify/activities/user/:username`
- **Description:** List all activities for a given username. No sensitive user data is returned.
- **Auth:** None (public)
- **Example Request:**
  ```http
  GET /api/gamify/activities/user/johndoe
  ```
- **Example Response:**
  ```json
  [
    { "type": "post_created", "meta": { "postId": "abc123" }, "createdAt": "2024-06-01T12:00:00Z" },
    ...
  ]
  ```

### 2. Get Activity by ID (Public)
- **GET** `/api/gamify/activities/:id`
- **Description:** View a specific activity by its ID. No sensitive user data is returned.
- **Auth:** None (public)
- **Example Request:**
  ```http
  GET /api/gamify/activities/60a7b2c4e1d2f8a1b2c3d4e5
  ```
- **Example Response:**
  ```json
  { "type": "post_created", "meta": { "postId": "abc123" }, "createdAt": "2024-06-01T12:00:00Z" }
  ```

### 3. List My Activities (Private)
- **GET** `/api/gamify/activities/me`
- **Description:** List all activities for the current authenticated user. Returns full activity data.
- **Auth:** JWT required (Bearer token)
- **Example Request:**
  ```http
  GET /api/gamify/activities/me
  Authorization: Bearer <JWT>
  ```
- **Example Response:**
  ```json
  [
    { "_id": "...", "type": "post_created", "meta": { "postId": "abc123" }, "createdAt": "2024-06-01T12:00:00Z" },
    ...
  ]
  ```

## Notes
- Public endpoints never expose sensitive user data.
- Activities are sorted by most recent first.
- For real-time activity notifications, see [Gateway](../gateway.md). 