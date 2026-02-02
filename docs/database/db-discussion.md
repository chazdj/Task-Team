# Discussions & Replies Database Schema (MVP)

This document defines the database schema required to support project discussions and threaded replies in TaskTeam.

## discussion Table

Stores discussion threads associated with a project.

| Column Name     | Type      | Constraints            | Description                                      |
|-----------------|-----------|------------------------|--------------------------------------------------|
| id              | UUID      | PK                     | Unique discussion identifier                     |
| project_id      | UUID      | FK → project.id        | Associated project                               |
| created_by      | UUID      | FK → user.id           | User who created the discussion                  |
| type            | VARCHAR   |                        | Discussion type (announcement, question, update) |
| content         | TEXT      | NOT NULL               | Discussion body                                  |
| created_at      | TIMESTAMP | DEFAULT now()          | Time discussion was created                      |

---

## reply Table

Stores replies to a discussion thread.

| Column Name     | Type      | Constraints                  | Description               |
|-----------------|-----------|------------------------------|---------------------------|
| id              | UUID      | PK                           | Unique reply identifier   |
| discussion_id   | UUID      | FK → discussion.id          | Parent discussion         |
| created_by      | UUID      | FK → user.id                | User who posted the reply |
| content         | TEXT      | NOT NULL                     | Reply body                |
| created_at      | TIMESTAMP | DEFAULT now()                | Time reply was created    |

---

## Relationships

* A **project** can have many discussions → `discussion.project_id`.
* A **discussion** belongs to exactly one project → `discussion.project_id`.
* A **discussion** may have many replies → `reply.discussion_id`.
* Replies cannot exist without a parent discussion.
* Only project members may create discussions or replies.

## Design Notes

* Discussions are intentionally lightweight for MVP.
* Replies are flat (no nested threading) to reduce complexity.
* `type` allows UI differentiation without separate tables.
* Editing and reactions may be added in later iterations.