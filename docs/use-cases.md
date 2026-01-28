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

## UC-4: Create Team 

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.

**Main Flow:**
1. User selects the option to create a new team.
2. User enters a team name (and optional description).
3. User submits the form.
4. System validates the input.
5. System creates a new team.
6. System assigns the user as a member of the team.
7. System sets the user as the team owner.
8. System displays the newly created team.

**Alternate Flows:**
- 4a. Invalid or missing team name -> system displays an error message.

**Postconditions:**
- A new team exists.
- User is a member and owner of the team. 

## UC-5: Join Team 

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- Team exists.

**Main Flow:**
1. User selects the option to join a team.
2. User enters a team invite code.
3. System validates the team information.
4. System adds the user to the team.
5. System displays the team dashboard.

**Alternate Flows:**
- 3a. Invalid invite code -> system displays an error message.
- 4a. User is already a member -> system prevents deuplicate membership.

**Postconditions:**
- User is a member of the team.

## UC-6: View My Teams 

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in. 

**Main Flow:**
1. User navigates to the dashboard.
2. System retrieves all teams the user belongs to.
3. System displays the list of teams.
4. User selects a team to view its workspace.

**Postconditions:**
- User can view and access their teams.

## UC-7: Leave Team

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- User is a member of the team.

**Main Flow:**
1. User selects the option to leave a team.
2. System asks for confirmation.
3. User confirms the action.
4. System removes the user from the team.
5. System updates the user's team list.

**Alternate Flows:**
- 4a. User is the only owner -> system prevents leaving or requires ownership transfer.

**Postconditions:**
- User is no longer a member of the team.

## UC-8: Send Chat Message

**Primary Actor:** Authenticated User

**Preconditions:**.
- User is logged in
- User is a member of the team.

**Main Flow:**
1. User opens the team chat.
2. User types a message.
3. User sends the message.
4. System saves the message.
5. System broadcasts the message to other team members in real time.

**Postconditions:**
- Message appears in the team chat for all members.

## UC-9: View Real-Time Chat Messages 

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in
- User is a member of the team.

**Main Flow:**
1. User opens the team chat.
2. System retrieves recent messages.
3. System displays incoming messages in real time.

**Postconditions:**
- User can view live chat updates.

## UC-10: View Message Sender and Timestamp

**Primary Actor:** Authenticated User

**Preconditions:**
- Messages exist in the chat.

**Main Flow:**
1. User views messages in the team chat/
2. System displays the sender's name and timestamp with each message.

**Postconditions:**
- Chat messages are clear and attributable.

## UC-11: View Chat History

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- User is a member of the team.

**Main Flow:**
1. User scrolls up in the team chat.
2. System loads older messages.
3. System displays chat history.

**Postconditions:**
- User can view previous conversations.

## UC-12: Edit or Delete Chat Message

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- User is the author of the message.

**Main Flow:**
1. User selects one of their own messages.
2. User chooses to edit or delete the message.
3. System updates or removes the message.
4. System updates the chat view.

**Alternate Flows:**
- 2a. User attempts to edit another user's message -> system denies action.

**Postconditions:**
- Message is edited or removed successfully.

## UC-13: Create Project

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- User is a member of the team.

**Main Flow:**
1. User navigates to a team workspace.
2. User selects the option to create a new project.
3. User enters project details (name, optional description).
4. User submits the form.
5. System validates the input.
6. System creates the project under the selected team.
7. System displays the new project dashboard.

**Alternate Flows:**
- 5a. Invalid or missing project name → system displays an error.

**Postconditions:**
- A new project exists within the team.

## UC-14: View Active Projects

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- User is a member of the team.

**Main Flow:**
1. User opens the team workspace.
2. System retrieves all active projects for the team.
3. System displays the list of active projects.

**Postconditions:**
- User can see all ongoing projects.

## UC-15: View Archived Projects

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- Archived projects exist.

**Main Flow:**
1. User navigates to the archived projects section.
2. System retrieves archived projects for the team.
3. System displays the archived projects list. 

**Postconditions:**
- User can reference completed or paused projects.

## UC-16: Archive Project

**Primary Actor:** Authenticated User

**Preconditions:**
- User is logged in.
- User has permission to manage the project.

**Main Flow:**
1. User selects a project.
2. User chooses the option to archive the project.
3. System asks for confirmation.
4. User confirms the action.
5. System marks the project as archived.
6. System removes the project from the active projects list.

**Alternate Flows:**
- 2a. User lacks permission → system denies the action.

**Postconditions:**
- Project is archived and no longer active.