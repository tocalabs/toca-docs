# Table Relationships

Tables can be joined together using foreign keys. This is named "relational data" as the data is forming a relationship.
This helps us to model our data in the most accurate way possible as more often than not, data in the real world is related.

![Related Tables Diagram](/src/assets/related_data.png)


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