# Authentication Database Schema (MVP)

This document defines the database schema required to support authentication in TaskTeam.

## user Table

Stores user account and identity information.

| Column Name   | Type         | Constraints      | Description                |
| ------------- | ------------ | ---------------- | -------------------------- |
| id            | UUID         | PK               | Unique user identifier     |
| email         | VARCHAR(255) | UNIQUE, NOT NULL | User email address         |
| password_hash | TEXT         | NOT NULL         | Securely hashed password   |
| name          | VARCHAR(100) |                  | Display name for the user  |
| created_at    | TIMESTAMP    | DEFAULT now()    | Account creation timestamp |

---

## Relationships

* Users can belong to many teams → `team_member.user_id`.
* Users can be assigned to many tasks → `task.assigned_user_id`.
* Users can create discussions and replies → `discussion.created_by`, `reply.created_by`.
* Users can have many activity records → `activity.user_id`.
* Users can have many notifications → `notification.user_id`.
* Users can send chat messages → `chat_message.user_id`.

## Constraints & Rules

* Email addresses must be unique across all users.
* Passwords are stored as hashed values only; no plaintext passwords are persisted.

## Design Notes

* `UUID` is used for user identifiers to ensure global uniqueness.
* The `name` field is optional and intended for display purposes.
* Authentication-related tables are intentionally minimal for MVP scope.
* Additional profile and security fields (e.g., password reset tokens, MFA) may be added in later iterations.