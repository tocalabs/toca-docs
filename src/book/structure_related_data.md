# Using Tables to Structure Related Data

A table is a data structure that allows you to organize and manage information within your application. Think of it as a spreadsheet within your app, where data is arranged in rows and columns. Each row represents a record, and each column represents a specific attribute or field.

Imagine you want to store some data about your users, we want to store:
- Their name
- Email address
- Profile picture
- Date of Birth
-

| Id | Name | Email address | Profile picture | Date of birth |
|:-- | :-- | :-- | :-- | :-- |
| 1 | Alan Turing | alan@computers.inc | 💻 | `1912-06-12` |
| 2 | Tim Berners-Lee | tim@worldwideweb.com | 🌐 | `1955-06-08` |
| 3 | Linus Torvalds | linus@linux.net | 🐧 | `1969-12-28` |

All tables in Toca contain an `Id` column of type `UUID`, this means that there will always be a column containing unique values.
