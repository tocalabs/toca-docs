# Querying Data

The ability to query table data to bring back exactly the rows you want is very powerful. It allows you to do things like return only the rows where the value is greater than {x}, or only return the data where the title is equal to "Mr". You can query tables and views using a powerful query editor that allows you to combine queries so that you can return only the data you are interested in.

Imagine you have a table that looks something like the following:
| Id |  Product | Category | Amount (GBP) | Associated User |
|:-- | :-- | :-- | :-- | :-- |
| 987 | Engima Cracking Kit | Electronics | 99.99 | 1 |
| 988 | Turing Machine Parts | Electronics | 25.50 | 1 |
| 546 | Guide to the Internet | Books | 74.99 | 2 |
| 547 | How to build your first website | Books | 24.99 | 2 |
| 548 | Server for website | Computing Hardware | 24.99 | 2 |
| 321 | Guide to Microsoft Windows | Books | 0.99 | 3 |
| 322 | Guide to MacOS | Books | 1.99 | 3 |
| 322 | How to build an Operating System | Books | 5.99 | 3 |

If we wanted to find all products that were below £5, we would then write a Query that would represent the following:
`FETCH ALL Data WHERE Amount (GBP) > 5.00`.

Let's take a deeper look into how we would do this.

## Creating a Query

### Where you can use a query

There are five main places you can use a query to filter the data you return:
- Actions in Activities
- Datastore Interface
- Dynamic Pages in Apps
- App Components
- App IPL Actions

All of these places share the same Query interface and give you the same options for filtering a Table or View. The Query interface gives you an option of the `Field` which defines _where_ you are filtering, the `Operator` which represents _how_ you are filtering and a `Value` which represents _what_ you are filtering by.

Different types of columns in your Table / View can use different operators. For example, if you are filtering on a `Number` column, then you can use:
- **=** - _Is equal to_
- **!=** / **<>** - _Is not equal to_
- **<** - _Is less than_
- **>** - _Is greater than_
- **<=** - _Is less than or equal to_
- **>=** - _Is greater than or equal to_
- **IN** - _Is in the following list of values (comma separated)_
- **NOT IN** - _Is not in the following list of values (comma separated)_

If you are filtering on a `String` column, then the `>`, `<`, `>=` and `<=` operators do not make sense, as how can one piece of text be less than another piece of text? However, you can use the following other operators on String types:
- **LIKE** - _Allows you to search for part of some text, using a `%` character to denote where non search text could be_
- **REGEXP** - _Allows you to use [Regular expression](https://en.wikipedia.org/wiki/Regular_expression) to search for a pattern of characters in your text_

Let's look at some examples:

#### Number Columns

#### String Columns

#### Boolean Columns


#### Table Relationship Columns



> **Note 📝**
>
> You cannot filter on File or Image columns.


### Defining a Condition

## Combining Conditions

### AND

### OR

### Groups
