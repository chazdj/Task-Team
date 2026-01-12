# Architecture Overview

This document describes the high-level architecture and system design for TaskTeam.

## Overview
TaskTeam follows a client-server architecture with real-time capabilities.

## Planned Architecture
- **Client:** Next.js frontend
- **Backend & Database:** Supabase (PostgreSQL)
- **Authentication:** Supabase Auth
- **Realtime Features:** Supabase Realtime (chat, discussions, notifications)
- **Hosting:** Vercel

## Key Concepts
- Projects belong to teams
- Tasks and discussions belong to projects
- Team chat is scoped at the team level
- Activity feed is system-generated and read-only
- Notifications are user-specific and actionable

Detailed database schemas and data flow diagrams will be added during implementation.