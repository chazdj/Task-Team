# Task API

This document defines task-related actions for the TaskTeam application.

## Create Task

**Description**

Creates a new task within a project.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Project exists.
* User is a member of the project's team.

**System Behavior**
1. User naviagates to the project's dashboard.
2. User selects "Create Task".
3. User enters task title and optional details.
4. System validates required fields.
5. System creates a new task linked to the project.
6. System sets the task status to `todo`.
7. System displays the task on the project board.

**Database Interaction**
* INSERT into `task`
    * project_id
    * title
    * description (optional)
    * status = 'todo'
    * created_at

**Success Response**
* Task is created and visible in the project.
