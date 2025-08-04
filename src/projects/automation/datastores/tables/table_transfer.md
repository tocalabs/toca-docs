# Transfer Table Tool

This tool allows you to migrate data from one table to another, regardless of whether or not they are in the same datastore. This tool not only allows you to transfer the data but also allows you to migrate changes to the tables structure such as changes to the columns.

There are 3 steps to the tool:
1. Select Tables: Choosing your source Datastore and Table and your target Datastore and Table
2. Transfer Options: Define how and what you want to transfer, this is where you select the options to transfer the schema, clear the original table before transferring the data etc.
3. Verify Schema Changes: Check the schema migrations that are about to be performed are valid, this helps identify issues such as changing a column to an incompatible type
4. Summary: A summary of the changes that the tool is about to make before

> **Tip** ✨
>
> You can also use this tool to clear all data from a table. To do this, set the source and target table  to the same table and then make sure you have selected the option to "Transfer data" and "Clear Target Table before transfer" and then click through the tool. Once completed, your target table will now contain no rows of data.
