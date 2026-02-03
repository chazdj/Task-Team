# Team Management API

This document defines the operations related to team creation, membership, and management within TaskTeam.

## Create Project

**Description**

Creates a new project within a team.

**Actor**

Authenticated team member

**Preconditions**
* User is logged in.
* User is a member of the team.

**System Behavior**
1. User submits a project name and team ID.
2. System verifies user membership in the team.
3. System creates a new project with status `Active`.
4. System returns the newly created peoject.

**Database Interaction**
* INSERT into `project`.
* Validate membership via `team_member`.

**Success Response**
* Project ID
* Project name
* Team ID
* Status