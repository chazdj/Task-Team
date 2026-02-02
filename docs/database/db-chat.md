# Chat Database Schema (MVP)

This document defines the database schema required to support team chat in TaskTeam.

## chat Table

Stores chat sessions for a team.

| Column Name | Type      | Constraints        | Description            |
|-------------|-----------|--------------------|------------------------|
| id          | UUID      | PK                 | Unique chat identifier |
| team_id     | UUID      | FK → team.id       | Associated team        |
| created_at  | TIMESTAMP | DEFAULT now()      | Time chat was created  |

---

## chat_message Table

Stores individual messages within a chat session.

| Column Name       | Type      | Constraints        | Description               |
|-------------------|-----------|--------------------|---------------------------|
| id                | UUID      | PK                 | Unique message identifier |
| chat_id           | UUID      | FK → chat.id       | Parent chat session       |
| user_id           | UUID      | FK → user.id       | User who sent the message |
| content           | TEXT      | NOT NULL           | Message content           |
| created_at        | TIMESTAMP | DEFAULT now()      | Time message was sent     |

---

## Relationships

* A **team** can have one chat session → `chat.team_id`.
* A chat session belongs to exactly one team → `chat.team_id`.
* A chat session can have many messages → `chat_message.chat_id`.
* Each message belongs to exactly one chat → `chat_message.chat_id`.
* Each message is sent by a user → `chat_message.user_id`.

## Constraints & Rules

* Only team members can send messages in a team chat.

## Design Notes

* Separating chats and messages allows for multiple chat threads per team.
* Ordering messages by `created_at` enables chronological display.
* Future improvements: read receipts, message edits, and reactions.