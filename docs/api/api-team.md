# Team Management API (MVP)

This document defines the operations related to team creation, membership, and management within TaskTeam.

## Create Team

**Description**

Allows a logged-in user to create a new team workspace.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.

**System Behavior**
1. User submits a team name.
2. System creates a new team record.
3. System creates a team_member record:
  * user_id = creator
  * role = owner
4. User becomes the team owner.

**Database Interaction**
* INSERT into `team`
* INSERT into `team_member`

**Success Response**
* Team is created successfully.
* User is assigned as team owner.

---

## Join Team

**Description**

Allows a user to join an existing team.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Team exists.

**System Behavior**
1. User requests to join a team.
2. System verifies the team exists.
3. System checks that user is not already a member of the team.
4. System creates a new `team_member` record.
5. User is added to the team with role = `member`.

**Database Interaction**
* SELECT team by `team_id`
* INSERT into `team_member`

**Success Response**
* User is successfully added to the team.

---

## Leave Team

**Description**

Allows a user to leave a team they are a member of.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* User is a member of the team.
* User is not the team owner.

**System Behavior**
1. User requests to leave a team.
2. System verifies the user is a member of the team.
3. System checks that the user is not the team owner.
4. System removes the user's `team_member` record.
5. User is no longer associated with the team.

**Database Interaction**
* SELECT from `team_member`
* DELETE from `team_member`

**Failure Conditions**
* If the user is the team owner, the system prevents leaving unless ownership is transferred.

**Success Response**
* User successfully leaves the team.

---

## View My Teams

**Description**

Returns all teams the authenticated user is a member of.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.

**System Behavior**
1. User requests their team list.
2. System retrieves all `team_member` records for the user.
3. System joins team data for display.
4. System returns the list of teams.

**Database Interaction**
* SELECT from `team_member`
* JOIN with `team`

**Success Response**
* List of teams with basic metadata (id, name, role)