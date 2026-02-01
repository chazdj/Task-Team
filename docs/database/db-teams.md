# Team Management Database Schema (MVP)

This document defines the database schema required to support team creation, membership, and ownership in TaskTeam.

---

## team Table

Stores team-level information.

| Column Name | Type      | Constraints | Description            |
| ----------- | --------- | ----------- | ---------------------- |
| id     | UUID      | PK          | Unique team identifier |
| team_name   | VARCHAR   | NOT NULL    | Team name              |
| created_at  | TIMESTAMP | NOT NULL    | Team creation time     |

---

## team_member Table

Associative table linking users and teams.

| Column Name    | Type      | Constraints                 | Description                        |
| -------------- | --------- | --------------------------- | ---------------------------------- |
| id | UUID      | PK                          | Unique membership record           |
| user_id        | UUID      | FK → user.user_id, NOT NULL | Member user                        |
| team_id        | UUID      | FK → team.team_id, NOT NULL | Associated team                    |
| role           | VARCHAR   | NOT NULL                    | Member role (owner, admin, member) |
| joined_at      | TIMESTAMP | NOT NULL                    | Date user joined the team          |

---

## Constraints & Rules

- A user may belong to many teams
- A team may have many users
- `(user_id, team_id)` must be unique to prevent duplicate membership
- Each team must have at least one `owner` stored in `team_member.role`
- Ownership is role-based, not stored directly on the team
- Owners cannot leave a team unless ownership is transferred

---

## Design Notes

- `team_members` resolves the many-to-many relationship between users and teams
- Ownership is inferred from `role = 'owner'`
- Role-based permissions will be expanded later (admin, viewer, etc.)
- Invite codes and permissions will be added in future iterations
---