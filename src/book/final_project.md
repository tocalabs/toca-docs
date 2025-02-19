# Building a Tasklist Application

Now that you’re familiar with the core concepts of Toca, let’s dive into creating a functional **Tasklist Application**. This will demonstrate how to manage data with tables, build workflows for task logic, and create an app interface for users.

Our task application will allow users to:
- Register and log in.
- Create, view, edit, and delete tasks.
- Mark tasks as complete.
- Attach files to tasks.
- View tasks in a list and sort them by priority.

## Automation

This project will use both an **Automation Project** and an **App Project**. Automations will handle task creation, updates, and status management, while the App will provide the user interface.

---

## Setting Up the Data Structure

### Creating Tables
Navigate to the **Data** section in your project and create the following tables:

### 1. `user_profile` Table
Stores information about users.
- **Fields:**
  - `id` (UUID)
  - `created` (DateTime)
  - `updated` (DateTime)
  - `appUserId` (String)
  - `first_name` (String)
  - `first_name` (String)
  - `email` (String)
  - `profile-pic` (File)

### 2. `tasks` Table
Holds all the task details.
- **Fields:**
  - `id` (UUID)
  - `created` (DateTime)
  - `updated` (DateTime)
  - `task_title` (String)
  - `task_description` (String)
  - `task_due_date` (DateTime)
  - `task_priority` (String)
  - `task_file` (File)
  - `task_complete` (Boolean)
  - `task_appUserId` (Foreign Key to our application users, as well as the `user_profile` table using the `appUserId`)

---

## Automation

### Automation Goals
1. Handle task creation and updates.
2. Toggle the `task_completion` boolean to complete a task.

### Automating Task Creation
1. Create a new **Automation Project** and name it appropriately.
   - e.g. **Automation | Tasklist App**
2. Create a new **Activity** called **Create a New Task** and assign it to be **Stateless**.
3. Open your new activity, and add **Inputs** to the activity for all the task information you want to store.
   - _e.g. `task_title`, `task_description`, `task_due_date`, `task_priority`, and `task_file`._
4. Use the following Actions:
   - **`Add Row to Table`**: Add a new task to the `tasks` table.
   - Populate each of your variables  inputs for `task_title`, `task_description`, `task_due_date`, `task_priority`, and (_optionally_) `task_file`.

### Automating updating a Task
1. In the same **Automation Project** Create a new **Activity** called **Update a Task** and assign it to be **Stateless**.
2. Open your new activity, and add **Inputs** to the activity for all the task information you may want to update, as well as a unique identifier for the task row you want to update.
   - e.g. `task_id`, `task_title`, `task_description`, `task_due_date`, `task_priority` and `task_file`.
3. Use the following Actions:
   - **`Update Row in Table`**: Update a task in the `tasks` table with the updated values from your inputs, using `task_id` to specify the row to update.

### Automating Marking a Task Completed (_Optional_)
_You could handle this using the previous activity, or create a bespoke one as follows if you would prefer._
1. In the same **Automation Project** Create a new **Activity** called **Mark Task as Completed** and assign it to be **Stateless**.
2. Open your new activity, and add an **Input** that is a unique identifier for the task row you want to mark as completed.
   - e.g. `task_id`.
3. Use the following Actions:
   - **`Update Row in Table`**: Update a task in the `tasks` table by setting `task_completion` boolean to true, using `task_id` to specify the row to update.

### Automating Deleting a Task
1. In the same **Automation Project** Create a new **Activity** called **Delete a Task** and assign it to be **Stateless**.
2. Open your new activity, and add an **Input** that is a unique identifier for the task row you want to delete.
   - e.g. `task_id`.
3. Use the following Actions:
   - **`Delete Row from Table`**: Delete a task from the `tasks` table where id = `task_id` as your query.

---

## ___UNFINISHED FROM HERE ONWARDS___

## Building the App Interface

### App Goals
1. Display tasks in a list view.
2. Allow users to create, edit, delete, and mark tasks as complete.
3. Provide a dropdown for sorting tasks by priority.

### Creating the App


---
