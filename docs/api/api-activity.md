# Activity Feed API

## View Project Activity Feed

**Description**

Allows a user to view a read-only activity feed that tracks actions within a project.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* User is a member of the project's team.
* Project exists.

**System Behavior**
1. User navigates to the project dashboard.
2. User opens the activity feed.
3. System retrieves recent activity records for the project.
4. System orders actiivity entries chronologically.
5. System displays a read-only list of activities.

**Database Interaction**
* SELECT FROM `activity`
* WHERE `project_id = ?`

**Success Response**
* User can view a chronological list of project activities.

---

## View Activity Actor and Timestamp

**Description**

Allows a user to see who performed each action and when it occurred.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Activity records exist for the project.

**System Behavior**
1. User views an activity entry.
2. System displays the user associated with the activity.
3. System displays the timestamp of the activity.

**Database Interaction**
* SELECT FROM `activity`
* JOIN with `user`

**Success Response**
* Each activity clearly shows the actor and time of action.