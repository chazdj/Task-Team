# Team Management Database Schema (MVP)

This document defines the database schema required to support team creation, membership, and ownership in TaskTeam.

---
## teams Table

Stores team-level information.

| Column Name | Type      | Constraints          | Description |
|-------------|-----------|----------------------|-------------|
| id          | UUID      | PK                   | Unique team identifier |
| name        | VARCHAR   | NOT NULL             | Team name |
| created_by  | UUID      | FK → users.id        | User who created the team |
| created_at  | TIMESTAMP | DEFAULT now()        | Team creation time |
---

## team_members Table

Associative table linking users and teams.

| Column Name | Type      | Constraints                   | Description |
|------------|-----------|-------------------------------|-------------|
| id         | UUID      | PK                            | Unique membership record |
| user_id   | UUID      | FK → users.id                 | Member user |
| team_id   | UUID      | FK → teams.id                 | Associated team |
| role      | VARCHAR   | NOT NULL                      | Member role (owner, member) |
| joined_at | TIMESTAMP | DEFAULT now()                 | Date user joined the team |

---

## Constraints & Rules

- A user may belong to many teams
- A team may have many users
- `(user_id, team_id)` must be unique to prevent duplicate membership
- Each team must have at least one `owner`
- Owners cannot leave a team unless ownership is transferred

---

## Design Notes

- `team_members` resolves the many-to-many relationship between users and teams
- Role-based access control will be expanded later
- Invite codes and permissions will be added in future iterations
---