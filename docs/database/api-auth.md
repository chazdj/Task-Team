<!--
## POST /auth/

Registers a new user account.

### Request Body
```json
{
 
}
```
---

### Success Response
```json
{
  
}
```
---

### Error Responses
- 
-->
# Authentication API (MVP)

This document defines the authentication-related API endpoints for the TaskTeam MVP.

## POST /auth/register

Registers a new user account.

### Request Body
```json
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```
---

### Success Response (201 Created)
```json
{
  "id": "uuid",
  "email": "user@example.com"
}
```
---

### Error Responses
- 400 Bad Request - invalid email or password.
- 409 Conflict - email already registered.

## POST /auth/login

Authenticates an existing user.

### Request Body
```json
{
  "email": "user@example.com",
  "password": "securePassword123"
}
```
---

### Success Response (200 OK)
```json
{
  "token": "jwt-token-string",
  "user": {
    "id": "uuid",
    "email": "user@example.com"
  }
}
```
---

### Error Responses
- 401 Unauthorized - invalid credentials


## POST /auth/logout

Logs out the currently authenticated user.

### Headers
```makefile
Authorization: Bearer <token>
```
---

### Success Response (200 OK)
```json
{
  "message": "Logged out successfully"
}
```
---

## Authentication Notes
- Authentication uses JWT-based sessions
- Passwords are hashed and never stored in plain text
- Protected routes require a valid JWT

