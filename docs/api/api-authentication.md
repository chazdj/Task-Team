# Authentication API (MVP)

This document defines the backend operations required to support user authentication in TaskTeam.

## Register User

**Description**

Creates a new user account using an email and password.

**Actor**

Unauthenticated user

**Preconditions**
* User is not logged in.
* Email address is not already registered.

**Request Data**
* email
* password
* name (optional)

**System Behavior**
1. Validate email format and password strength.
2. Check if the email already exists in the `user` table.
3. Hash the password securely.
4. Create a new record in the `user` table.
5. Generate an authentication session or token.

**Database Interaction**
* INSERT INTO `user`

**Success Response**
* User account is created.
* Authentication token/session is returned.

**Failure Cases**
* Email already exists.
* Invalid email or password format.

---

## Log In User

**Description**

Authenticates an existing user using email and password.

**Actor**

Unauthenticated user

**Preconditions**
* User has an existing account.

**Request Data**
* email
* password

**System Behavior**
1. Validate email and password are provided.
2. Look up the user by email in the `user` table.
3. Compare the provided password with the stored password hash.
4. If valid, create an authentication session or token.

**Database Interaction**
* SELECT FROM `user`

**Success Response**
* Authentication token/session returned.
* User is considered logged in.

**Failure Cases**
* Email not found.
* Incorrect password

---

## Log Out User

**Description**

Ends the user's authenticated session.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.

**System Behavior**
1. Invalidate the user's authentication token or session.
2. Remove access to protected resources.

**Database Interaction**
* None (or session store if applicable).

**Success Reponse**
* User is logged out successfully.