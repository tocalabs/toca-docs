# Using Tables to Structure Related Data

A table is a data structure that allows you to organize and manage information within your application. Think of it as a spreadsheet within your app, where data is arranged in rows and columns. Each row represents a record, and each column represents a specific attribute or field.

Imagine you want to store some data about your users, we want to store:
- Their name
- Email address
- Profile picture
- Date of Birth

We need to create a table with a column for each of these properties and we can leverage proper data types for each one.
So for a name and email address we can use the `Text` type in those columns, then for storing the profile picture we'll use an `Image` type and lastly for the date of birth, we can leverage the `Date` type. This allows us to store our data for each user in it's most usable form and means we don't have to go and convert any data to store it in the table.

So, our table will then look like the following:

| Id | Name | Email address | Profile picture | Date of birth |
|:-- | :-- | :-- | :-- | :-- |
| 1 | Alan Turing | alan@computers.inc | 💻 | `1912-06-12` |
| 2 | Tim Berners-Lee | tim@worldwideweb.com | 🌐 | `1955-06-08` |
| 3 | Linus Torvalds | linus@linux.net | 🐧 | `1969-12-28` |

> **Note** 📝
> All tables in Toca contain an `Id` column of type `UUID`, this means that there will always be a column containing unique values.

This is great, but in a real world application, the different data we store tends to be related. Think of our table of users, we might also want to store their address, their contact information and their previous orders.

We _could_ create one table that contains all of this data, but that could end up being an incredibly big table which becomes very difficult to manage and maintain over time. Also, how would we represent many previous orders against a single user if it all lived in one table? It would result in an unwiedly table.

It would be _much_ better if we could store the data about our users, their addresses, their previous orders and their contact information in separate tables and then just link them to each other.
