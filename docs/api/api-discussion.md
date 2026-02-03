# Discussion API

## Create Discussion Post

**Description**

Allows a user to create a discussion post within a project.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* User is a member of the project's team.
* Project exists.

**System Behavior**
1. User navigates to the project discussion board.
2. User selects "Create Post."
3. User enters content and selects a discussion type.
4. System validates input.
5. System creates a new discussion record.
6. System logs the action in the activity feed.
7. System notifies relevant project members if applicable.

**Database Interaction**
* INSERT into `discussion`
* INSERT into `activity`

**Success Response**
* Discussion post is visible in the project discussion board.