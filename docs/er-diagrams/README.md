# TaskTeam ER Diagrams

This folder contains **all Entity-Relationship (ER) diagrams** for the TaskTeam application, documenting the system’s data design as it evolves from high-level concepts to database-ready structures.

## 1. Conceptual ER Diagram
The **conceptual ER diagram** provides a **high-level overview** of the TaskTeam system. It highlights the main entities and their relationships without showing attributes or keys.  

- Focuses on **core entities** like Users, Teams, Chats, Projects, Tasks, Discussions, Replies, Activity, and Notifications.  
- Shows how **Users join Teams** and how Teams organize **Projects**, which in turn manage Tasks and Discussions.  
- Includes **cardinality** (e.g., 1..*, 0..*) to clarify relationship constraints.  
- **Abstracted from implementation details**, ideal for understanding overall system structure.  


![Conceptual ER Diagram](01-conceptional-ERD.svg)

## 2. Logical ER Diagram
The **logical ER diagram** expands the conceptual model by including **entity attributes, primary keys (PK), and foreign keys (FK)**. It resolves many-to-many relationships using associative entities such as `TeamMember`.  

- Adds **attributes** for each entity (e.g., `name`, `description`, `status`).  
- Shows **primary keys** (`id`) and **foreign keys** (`user_id`, `team_id`, `project_id`) for relational structure.  
- Defines **ownership and membership relationships** clearly.  
- Prepares the model for the **physical database schema**.  

![Logical ER Diagram](02-logical-ERD.svg)

## 3. Physical ER Diagram
The **physical ER diagram** converts the logical model into a **database-ready schema**, showing **tables, data types, constraints, and relationships** for SQL implementation.  

- Includes **column types** (e.g., `VARCHAR`, `INT`, `DATETIME`) and **constraints** (e.g., `NOT NULL`, `UNIQUE`).  
- Maps **foreign keys and indexes** explicitly to ensure data integrity.  
- Represents the final structure used to **create and manage persistent data** in TaskTeam.  


![Physical ER Diagram](03-physical-ERD.svg)