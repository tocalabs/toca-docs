# Tables


// Overview

## Data Types

Every column in a table has a predefined type, this helps to make sure that your data is always in the right format.
As the data types of each column are always known, it also allows you to build safer Apps and Automation by making sure your data is always in the correct format.
The following formats are available:

| Type | Description |
|---   | --- |
| String | Used to store any text based data, this is stored as a `longtext` type behind the scenes. |
| Number | Used to store any numerical data, can handle decimal points |
| Boolean | Stores `true` or `false` |
| Time | A fixed 24-hour time in the format of `HH:MM:SS` e.g. `20:52:22` |
| Date | A date and 24-hour time in the format of `dd/mm/YYYY` e.g. `05/09/2018` represents the 5th September 2018 |
| DateTime | A fixed date in the format of `dd/mm/YYYY HH:MM:SS` e.g. `05/09/2018 09:00:00` represents 9am on the 5th September 2018 |
| JSON | Stores valid `JSON`, this is useful for storing complex objects e.g. `{ "name": "Toca.io" }` |
| UUID | Stores a `UUIDv4`, this allows you to generate unique values. e.g. `72f6eae6-c795-40f2-898a-8f02c202082d` |
| File | Stores any sort of file, this is useful for when you want to associate a file with a record of data |
| Image | Stores any image format, this can be particularly useful when powering a repeating layout in an App and wanting to display an image per record, e.g. a list of employees |
| Table Relation | Allows you to specify either a 1:1 or 1:many relationship with another table in the datastore |

You can "cast" columns from one type to another by changing the column type, however there can be some incompatibilities between types.
For example, if you cast a timestamp to a date, you will lose all the time information that was previously saved.


## Default Values

Default values can be provided for most column types, which allows you to insert a value into a column even when an explicit value is not provided.
You can set a "hardcoded" default value which will always be used if a value is not provided.
Alternatively, some types (e.g. a `DateTime` or `UUID` type) give you the option to auto generate a value when:
- the row is created
- the row is updated

## Table Relationships

Tables can be joined together using foreign keys. This is named "relational data" as the data is forming a relationship.
This helps us to model our data in the most accurate way possible as more often than not, data in the real world is related.

You can have two different kind of relationships between tables:
1. _One to One_

A 1:1 relationship means 1 row of data in Table A can relate to 1 row of data in Table B.
For example, you might have a table of _employees_ and a table of _addresses_ and each employee only has one address.

2. _One to Many_

A 1:many relationship means 1 row of data in Table A can relate to many rows of data in Table B.
For example, you might have a table of _managers_ and a table of _employees_ and each manager might oversee many employees.

**Benefits of Relational Data**

Creating relationships between your data has many benefits such as:

- Referential Integrity

_Because a table **must** have valid references to it's related data at all times, it automatically prevents you from deleting a row of data that is relied upon by other tables.. This also allows you to make sure your data is accurate._

- Better Ergonomics

_Because the relationships between tables are predefined, Apps and Automation actions understand the structure of data and allow you to access related data without having to make separate queries to the related tables._

- Less Redundancy

_By allowing you to create relationships between your data, it will naturally lead to less replicated and redundant data in your tables. This is because instead of duplicating the same data when it is required by many tables, you can just have them all relate to the data they need._

**Examples of Relational Data**

- You might have built a table that contains a list of movies.
- Each movie must relate to a category
- Each movie contains several actors

Your table relationships for the above scenario might look like:
- Movies 1:1 Categories
- Movies 1:Many Actors


## Row level permissions

There are 
