# Admin Gamification Management

## Overview
Admins can manage all aspects of the gamification system, including:
- Creating, editing, viewing, and deleting badges and rewards
- Adjusting user points, levels, and crystals
- Viewing and updating gamify profiles
- All actions are protected by the `SYSTEM_ADMINISTRATOR` role and are fully audit-logged

## Required Role
- All endpoints require the `SYSTEM_ADMINISTRATOR` role and a valid JWT

## Endpoints
All endpoints are under `/admin` (see Swagger for full details).

### Badges
- `POST   /admin/badges` — Create a badge
- `GET    /admin/badges` — List all badges
- `GET    /admin/badges/:id` — Get badge by ID
- `PUT    /admin/badges/:id` — Update badge
- `DELETE /admin/badges/:id` — Delete badge

### Rewards
- `POST   /admin/rewards` — Create a reward
- `GET    /admin/rewards` — List all rewards
- `GET    /admin/rewards/:id` — Get reward by ID
- `PUT    /admin/rewards/:id` — Update reward
- `DELETE /admin/rewards/:id` — Delete reward

### Gamify Profiles
- `GET    /admin/gamify` — List all gamify profiles
- `GET    /admin/gamify/:id` — Get gamify profile by ID
- `PUT    /admin/gamify/:id` — Update gamify profile

### Points, Levels, Exp, Crystals
- `POST /admin/gamify/:id/add-points` — Add points
- `POST /admin/gamify/:id/remove-points` — Remove points
- `POST /admin/gamify/:id/add-level` — Add level(s)
- `POST /admin/gamify/:id/remove-level` — Remove level(s)
- `POST /admin/gamify/:id/add-exp` — Add experience
- `POST /admin/gamify/:id/remove-exp` — Remove experience
- `POST /admin/gamify/:id/add-crystals` — Add crystals
- `POST /admin/gamify/:id/remove-crystals` — Remove crystals

## Example: Add Points
```http
POST /admin/gamify/123456/add-points
Authorization: Bearer <JWT>
Content-Type: application/json

{
  "amount": 100
}
```
**Response:**
```json
{
  "_id": "...",
  "user": "...",
  "points": 200,
  ...
}
```

## Security & Audit Logging
- All admin actions are logged for auditing (user, action, target, details, IP)
- Only users with the `SYSTEM_ADMINISTRATOR` role can access these endpoints

## See Also
- [Gamification System Introduction](../Gamification/introduction.md)
- [API Reference (Swagger)](../../Swagger/adminSwagger.md) 