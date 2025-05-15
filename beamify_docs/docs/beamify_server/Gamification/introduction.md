---
sidebar_position: 1
---

# Introduction

## What is Beamify Gamification?
Beamify's gamification system is a robust, extensible framework for rewarding and engaging users across the platform. It provides:
- **Points, Levels, Crystals:** Track user progress, achievements, and special currency.
- **Activities:** Log and display user actions (e.g., posting, logging in).
- **Badges & Rewards:** Visual and milestone-based achievements for user engagement.
- **Real-time Notifications:** Users receive instant updates for gamification events via a dedicated gateway.

## Core Concepts
- **Points:** Numeric value for user actions (e.g., posting, completing quests).
- **Levels:** User progression, based on points/exp.
- **Crystals:** Special currency for advanced rewards.
- **Activities:** Log of user actions, viewable by username or user (private).
- **Badges:** Visual achievements for milestones.
- **Rewards:** Achievements for special actions (e.g., first login).
- **Real-time Gateway:** Socket.IO-based, user ID–scoped, JWT-authenticated, delivers all gamification events instantly to the frontend.

For details on endpoints and usage, see the CRUD documentation in this folder:
- [Activities](./Activities/activities.md)
- [Badges](./Badges/badges.md)
- [Rewards](./Rewards/rewards.md)
- [Gateway](./gateway.md)
