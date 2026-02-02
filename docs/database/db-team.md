# Team Management Database Schema (MVP)

This document defines the database schema required to support team creation, membership, and ownership in TaskTeam.

## team Table

Stores team-level information.

| Column Name | Type      | Constraints      | Description            |
| ----------- | --------- | ---------------- | ---------------------- |
| id          | UUID      | PK               | Unique team identifier |
| team_name   | VARCHAR   | NOT NULL         | Team name              |
| created_at  | TIMESTAMP | DEFAULT now()    | Team creation time     |

---

## team_member Table

Associative table linking users and teams.

| Column Name    | Type      | Constraints                 | Description                        |
| -------------- | --------- | --------------------------- | ---------------------------------- |
| id             | UUID      | PK                          | Unique membership record           |
| user_id        | UUID      | FK → user.id, NOT NULL      | Member user                        |
| team_id        | UUID      | FK → team.id, NOT NULL      | Associated team                    |
| role           | VARCHAR   | NOT NULL                    | Member role (owner, admin, member) |
| joined_at      | TIMESTAMP | DEFAULT now()               | Date user joined the team          |

---

## Relationships

* A **user** may belong to many teams → `team_member.user_id`.
* A **team** may have many users → `team_member.team_id`.
* Team ownership is inferred via `team_member.role = 'owner'`.

## Constraints & Rules

* `(user_id, team_id)` must be unique to prevent duplicate membership.
* Each team must have at least one `owner` stored in `team_member.role`.
* Ownership is role-based, not stored directly on the team.
* Owners cannot leave a team unless ownership is transferred.

## Design Notes

* `team_member` resolves the many-to-many relationship between users and teams.
* Role-based permissions will be expanded later (admin, viewer, etc.).
* Invite codes and permissions will be added in future iterations.