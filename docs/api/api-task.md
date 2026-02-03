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

---

## Update Task Status

**Description**

Moves a task between workflow states (To Do, In Progress, Done).

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Task exists.
* User is a member of the project's team.

**System Behavior**
1. User selects a task.
2. User changes the task status.
3. System validates the new status.
4. System updates the task record.
5. System records the change in the activity log.
6. System updates the project board in real time.

**Database Interaction**
* UPDATE `task`
    * status
* INSERT INTO `activity`
    * project_id
    * user_id
    * action = "Updated task status"
    * created_at

**Success Response**
* Task status is updated and visible to all team members.