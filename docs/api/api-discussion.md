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
* INSERT INTO `discussion`
* INSERT INTO `activity`

**Success Response**
* Discussion post is visible in the project discussion board.

---
## Reply to Discussion Post

**Description**

Allows a user to reply to an existing discussion post.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Discussion post exists.
* User is a member of the project's team.

**System Behavior**
1. User opens a discussion post.
2. User writes a reply.
3. User submits the reply.
4. System validates the content.
5. System creates a reply record.
6. System logs the action in the activity feed.
7. System notifies the discussion author.

**Database Interactions**
* INSERT INTO `reply`
* INSERT INTO `activity`
* INSERT INTO `notification`

**Success Response**
* Reply appears under the discussion post.

---

## Edit Discussion Post

**Description**

Allows a user to edit their own discussion post.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Discussion post exists.
* User is the author of the discussion post.
* User is the member of the project's team.

**System Behavior**
1. User opens their discussion post.
2. User selects the "Edit" option.
3. User updates the discussion content and/or type.
4. System validates the updated input.
5. System updates the discussion record.
6. System logs the action in the activity feed.

**Database Interaction**
* UPDATE `discussion`
* INSERT INTO `activity`

**Success Response**
* Updated discussion content is displayed in the discussion board.

---

## Delete Discussion Post

**Description**

Allows a user to delete their own discussion post.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Discussion post exists.
* User is the author of the discussion post or has appropriate permissions.
* User is a member of the project's team.

**System Behavior**
1. User selects the discussion post.
2. User chooses the "Delete" option.
3. System requests confirmation.
4. User confirms deletion.
5. System removes the discussion post.
6. System logs the action in the activity feed.

**Database Interaction**
* DELETE FROM `discussion`
* INSERT INTO `activity`

**Success Response**
* Discussion post is removed from the discussion board.

---

## Pin Discussion Post

**Description**

Allows a user with appropriate permissions to pin a discussion post.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* Discussion posts exist.
* User has permission to manage discussions.
* User is a member of the project's team.

**System Behavior**
1. User selects a discussion post.
2. User chooses the "Pin" option.
3. System marks the discussion post as pinned.
4. System updates the discussion board ordering.
5. System logs the action in the activity feed.

**Database Interaction**
* UPDATE `discussion`
* INSERT INTO `activity`

**Success Response**
* Discussion post appears pinned at the top of the discussion board.

---

## Search Discussion Post

**Description**

Allows a user to search for discussion posts within a project.

**Actor**

Authenticated user

**Preconditions**
* User is logged in.
* User is a member of the project's team.
* Discussion posts exist.

**System Behavior**
1. User enters a search query.
2. System searches discussion posts by content, title, or type.
3. System retrieves matching discussion posts.
4. System displays search results.

**Database Interaction**
* SELECT FROM `discussion`

**Success Response**
* Matching discussion posts are displayed to the user.