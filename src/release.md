# 8.0 - Release Notes

The theme of this release is all around view ports and tables! The release brings in a lot of new functionality that enhances existing features within the platform, making it easier and faster to build things!

## What's New

Tables have been given a massive production boost!
We have taken your feedback and enhanced the customizations available for use in a user friendly, yet powerful way.

---

### Table Columns

#### Database Data Types
Datatype customizations have been added for `String` columns. You are now able to specify the database data type you wish to use per column.
You can find these data types in the `Update Column` modal in the Datastore edit screen.

![data_type](/src/assets/database_datatype.png)

Read up more on :docs-link[Database Data Types]{id="projects/automation/datastores/tables/database_data_types"}.

#### Delete Operations
To help prevent orphaned data in certain situations there is the ability to include delete operations for `One-To-One` and `One-To-Many` table relationships.
![delete_operation](/src/assets/delete_operation.png)

Read up more on :docs-link[Delete Operations]{id="projects/automation/datastores/tables/delete_operation"}.

#### Auto Increment
The ability to add auto-incrementing `Number` columns has been added.
![Auto Increment](/src/assets/auto_increment.gif)

Read up more on :docs-link[Columns]{id="projects/automation/datastores/tables/column"}.

---

### Table Indexes
![Add Index Example](/src/assets/add_index.gif)

Indexes improve query performance by allowing the database engine to find data more efficiently, much like an index in a book. Instead of scanning an entire table, the database can quickly locate relevant rows.

You can observe and interact with indexes via the new `Index` tab in the table editor.

Read up more on :docs-link[Indexes]{id="projects/automation/datastores/tables/index"}.

---

### Apps

### Automation

### General

## Bug Fixes

A number of bug fixes were included in this release across the platform.

> Contact <support@toca.io> for a full list of bug fixes included within this release.

## Deprecated

Nothing has been deprecated in this release.

## Previous Releases

- :docs-link[7.10]{id="releases/7_10"}
- :docs-link[7.9]{id="releases/7_9"}
- :docs-link[7.8]{id="releases/7_8"}
- :docs-link[7.7]{id="releases/7_7"}
- :docs-link[7.6]{id="releases/7_6"}
- :docs-link[7.5]{id="releases/7_5"}
