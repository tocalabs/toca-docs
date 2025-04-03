# 8.0 - Release Notes

The theme of this release is all around productivity! The release brings in a lot of new functionality that enhances existing features within the platform, making it easier and faster to build things!

## What's New

Tables have been given a massive production boost!
We have taken your feedback and enhanced the customizations available for use in a user friendly, yet powerful way.

### Table Columns

#### Database Data Types
Datatype customizations have been added for `String` columns. You are now able to specify the database data type you wish to use per column.
You can find these data types in the `Update Column` modal in the Datastore edit screen.

![data_type](/src/assets/database_datatype.png)

##### VARCHAR(n)
Variable-length string with a maximum length of n (1 to 65,535 characters, depending on row size and storage).
Stores only the actual length of the string, plus 1-2 bytes for length metadata.
More efficient for short, frequently updated text fields.

##### CHAR(n)
Fixed-length string of n characters (1 to 255).
Always occupies n bytes, padded with spaces if the string is shorter.
Best for fixed-size values like codes or abbreviations.

##### TEXT Types (Used for large text storage, cannot have default values)
**TEXT** – Up to 65,535 characters (2-byte length indicator).
**LONGTEXT** – Up to 4,294,967,295 characters (4-byte length indicator).

### Table Indexes
![Add Index Example](/src/assets/add_index.gif)

Indexes improve query performance by allowing the database engine to find data more efficiently, much like an index in a book. Instead of scanning an entire table, the database can quickly locate relevant rows.

You can observe and interact with indexes via the new `Index` tab in the table editor.

Read up more on :docs-link[Indexes]{id="projects/automation/datastores/tables/index"}.

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
