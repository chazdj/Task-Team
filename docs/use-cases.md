# Use Cases

## UC-1: Register Account

**Primary Actor:** User

**Preconditions:**
- User is not logged in
- User has a valid email

**Main Flow:**
1. User navigates to the Sign Up page.
2. User enters an email and password.
3. User submits the registration form.
4. System validates the email format and password requirements.
5. System checks that the email is not already registered.
6. System creates a new user account.
7. System logs the user in.
8. System redirects the user to the dashboard.

**Alternate Flow:**
- 5a. Email already exists -> system displays an error message.
- 4a. Invalid input -> system displays validation errors.

**Postconditions:**
- A new user account exists.
- User is authenticated.

## UC-2: Log In

**Primary Actor:** Returning User

**Preconditions:**
- User has an existing account.
- User is logged out.

**Main Flow:**
1. User navigates to the Login page.
2. User enters email and password.
3. User submits the login form.
4. System validates credentials.
5. System authenticates the user.
6. System redirects the user to their dashboard.

**Alternate Flow:**
- 4a. Invalid credentials -> system displays an error message.

**Postconditions:**
- User is authenticated.
- User can access teams, projects, and tasks.

## UC-3: Log Out

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.

**Main Flow:**
1. User selects "Log Out".
2. System invalidates the user session.
3. System redirects the user to the login page.

**Postconditions:**
- User session is terminated.
- User is logged out of the system.