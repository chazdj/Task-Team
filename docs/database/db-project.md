# Projects Database Schema (MVP)

This document defines the database schema required to support **projects** in the TaskTeam application. Projects serve as the primary organizational unit within a team and act as the parent entity for tasks, discussions, activity logs, and notifications.

## project Table

Stores project-level information created within a team.

| Column Name  | Type         | Constraints                 | Description                             |
| ------------ | ------------ | --------------------------- | --------------------------------------- |
| id           | UUID         | PK                          | Unique project identifier               |
| team_id      | UUID         | FK → team.id, NOT NULL      | Team that owns the project              |
| project_name | VARCHAR(150) | NOT NULL                    | Name of the project                     |
| status       | VARCHAR(30)  | NOT NULL                    | Project status (e.g., Active, Archived) |
| created_at   | TIMESTAMP    | DEFAULT now()               | Project creation timestamp              |

---

## Relationships

* A **team** can have many projects.
* A **project** belongs to exactly one team.
* A **project** can have many:

  * tasks → `task.project_id`.
  * discussions → `discussion.project_id`
  * activity records → `activity.project_id`
  * notifications → `notification.project_id`

Foreign key relationship:

* `project.team_id` -> `team.id`

## Constraints & Rules

* Each project must belong to a valid team.
* Project names are not required to be globally unique, only unique within a team (enforced at the application layer).
* Deleting a team should either:

  * cascade-delete associated projects, or
  * restrict deletion if projects exist (implementation decision)

## Design Notes

* Projects are **team-scoped**, not user-scoped.
* Status is stored as a string to allow flexibility (e.g., Active, Archived, Completed).
* Ownership and permissions are inherited from team membership.
* Additional metadata (descriptions, deadlines, visibility) may be added in future iterations.