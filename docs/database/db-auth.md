# Authentication Database Schema (MVP)

This document defines the database schema required to support authentication in TaskTeam.

---
## users Table

Stores user account information.

| Column Name   | Type        | Constraints                  | Description |
|---------------|-------------|------------------------------|-------------|
| id            | UUID        | PK                           | Unique user identifier |
| email         | VARCHAR     | UNIQUE, NOT NULL             | User email address |
| password_hash | VARCHAR     | NOT NULL                     | Hashed password |
| created_at    | TIMESTAMP   | DEFAULT now()                | Account creation time |
---
## Design Notes

- `UUID` is used for user IDs to ensure global uniqueness
- Passwords are stored as hashed values only
- Email must be unique across all users
- Additional profile fields will be added in later iterations
---