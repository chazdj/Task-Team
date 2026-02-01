# Authentication Database Schema (MVP)

This document defines the database schema required to support **authentication** in TaskTeam.

---
## users Table

Stores user account and identity information.

| Column Name   | Type         | Constraints      | Description                |
| ------------- | ------------ | ---------------- | -------------------------- |
| id       | UUID         | PK               | Unique user identifier     |
| email         | VARCHAR(255) | UNIQUE, NOT NULL | User email address         |
| password_hash | TEXT         | NOT NULL         | Securely hashed password   |
| name          | VARCHAR(100) |                  | Display name for the user  |
| created_at    | TIMESTAMP    | NOT NULL         | Account creation timestamp |
---
## Design Notes

* `UUID` is used for user identifiers to ensure global uniqueness
* Passwords are stored as hashed values only; no plaintext passwords are persisted
* Email addresses must be unique across all users
* The `name` field is optional and intended for display purposes
* Authentication-related tables are intentionally minimal for MVP scope
* Additional profile and security fields (e.g., password reset tokens, MFA) may be added in later iterations
---