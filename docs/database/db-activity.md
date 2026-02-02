# Activity Log Database Schema (MVP)

This document defines the database schema required to support project-level activity tracking in TaskTeam.

## activity Table

Stores a chronological log of important actions within a project.

| Column Name | Type      | Constraints            | Description                   |
|-------------|-----------|------------------------|-------------------------------|
| id          | UUID      | PK                     | Unique activity identifier    |
| project_id  | UUID      | FK → project.id        | Associated project            |
| user_id     | UUID      | FK → user.id           | User who performed the action |
| action      | TEXT      | NOT NULL               | Description of the action     |
| created_at  | TIMESTAMP | DEFAULT now()          | Time the activity occurred    |

---

## Relationships

* A **project** can have many activities → `activity.project_id`.
* An **activity** belongs to exactly one project → `activity.project_id`.
* An **activity** belongs to exactly one user → `activity.user_id`.

## Constraints & Rules

* Activity records are immutable once created.
* Activities are ordered chronologically by `created_at`.

## Design Notes

* Activity logs provide transparency and accountability.
* Actions are stored as text for flexibility in MVP.
* Filtering by project enables per-project timelines.
* This table supports dashboards and audit-style views.