# Task Management Database Schema (MVP)

This document defines the database schema required to support task creation, assignment, and tracking in TaskTeam.

## task Table

Stores individual tasks within projects.

| Column Name      | Type      | Constraints                       | Description                                       |
| ---------------- | --------- | --------------------------------- | ------------------------------------------------- |
| id               | UUID      | PK                                | Unique task identifier                            |
| project_id       | UUID      | FK → project.id, NOT NULL         | Project this task belongs to                      |
| assigned_user_id | UUID      | FK → user.id                      | User assigned to the task (optional)              |
| title            | VARCHAR   | NOT NULL                          | Task title                                        |
| description      | TEXT      |                                   | Task details                                      |
| status           | VARCHAR   | NOT NULL                          | Task status (e.g., “todo”, “in progress”, “done”) |
| priority         | VARCHAR   |                                   | Task priority (optional)                          |
| due_date         | DATE      |                                   | Task due date                                     |
| created_at       | TIMESTAMP | DEFAULT now()                     | Task creation timestamp                           |

---

## Relationships

* A **project** can have many tasks → `task.project_id`.
* A **task** belongs to exactly one project → `task.project_id`.
* A **user** can be assigned to many tasks → `task.assigned_user_id`.

## Constraints & Rules

* Each task must belong to one project.
* `assigned_user_id` is optional, allowing unassigned tasks.
* Status is mandatory to track progress.
* Tasks can only be assigned to users who are members of the project’s team.

## Design Notes

* `task` are tied to `project` via a foreign key for project-level organization.
* Priority and due dates are optional fields to allow flexibility in task planning.
* Assignments are optional at creation but can be updated later.