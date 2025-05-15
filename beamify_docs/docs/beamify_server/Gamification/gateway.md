---
sidebar_position: 2
---

# Gamification Gateway

## Overview
The Gamification Gateway provides real-time updates to users for all gamification events (points, levels, crystals, badges, rewards, activities, messages, notifications) using Socket.IO. Each user receives events scoped to their User ID.

## Connection
- **Protocol:** Socket.IO (WebSocket)
- **Port:** 4001 (default, configurable)
- **Authentication:** JWT required on connection
- **Room:** Each socket joins a room named after the User ID

### Example Client Connection
```js
const socket = io('http://localhost:4001', {
  auth: { token: 'JWT_TOKEN_HERE' }
});
socket.on('gamify:points', (data) => { /* handle points update */ });
socket.on('gamify:level', (data) => { /* handle level update */ });
socket.on('gamify:crystals', (data) => { /* handle crystals update */ });
socket.on('gamify:badge', (data) => { /* handle badge awarded */ });
socket.on('gamify:reward', (data) => { /* handle reward granted */ });
socket.on('gamify:activity', (data) => { /* handle activity */ });
socket.on('gamify:message', (data) => { /* handle message */ });
socket.on('gamify:notification', (data) => { /* handle notification */ });
```

## Event Types
- `gamify:points` — Points update
- `gamify:level` — Level update
- `gamify:crystals` — Crystals update
- `gamify:badge` — Badge awarded
- `gamify:reward` — Reward granted
- `gamify:activity` — Activity logged
- `gamify:message` — System/gamification message
- `gamify:notification` — Generic notification (e.g., "You received 100 points!")

## Security
- JWT is required for all connections. The server verifies the token and associates the socket with the User ID.
- Only the authenticated user receives their own events.

## Usage Notes
- The gateway is designed to be used from any page in the app, not just the gamification page.
- Other backend modules and gateways can emit events to users via the exported API in `gamifyGateway.js`. 
