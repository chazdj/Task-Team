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
* INSERT INTO `project`
* Validate membership via `team_member`

**Success Response**
* Project ID
* Project name
* Team ID
* Status

---

## View Active Projects

**Description**

Returns all active projects for a team.

**Actor**

Authenticated team member

**Preconditions**
* User is logged in.
* User is a member of the team.

**System Behavior**
1. User requests projects for a team.
2. System verifies team membership.
3. System retrieves projects with status = `Active`.
4. System returns the list of projects.

**Database Interaction**
* SELECT FROM `project`
* WHERE tead_id = ?
* AND status = `Active`

**Success Response**
* List of active projects.

---

## View Archived Projects

**Description**

Returns archived projects for a team.

**Actor**

Authenticated team member

**Preconditions**
* User is logged in.
* Archived projects exist.

**System Behavior**
1. User navigates to archived projects.
2. System retrieves projects with status = `Archived`.
4. System returns archived project list.

**Database Interaction**
* SELECT FROM `project`
* WHERE tead_id = ?
* AND status = `Archived`

**Success Response**
* List of archived projects.

---

## Archive Project

**Description**

Marks a project as archived so it no longer appears in active project lists.

**Actor**

Authenticated user with project permissions

**Preconditions**
* User is logged in.
* Project exists.
* User is a member of the project's team.

**System Behavior**
1. User selects a project.
2. User chooses the archive option.
3. System verifies user permissions.
4. System update the project status to `Archived`.
5. System removes the project from active views.

**Database Interaction**
* UPDATE `project`
* SET status = `Archived`
* WHERE id = ?

**Success Response**
* Project is archived successfully.