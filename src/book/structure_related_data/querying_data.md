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
`FETCH ALL Data WHERE Amount (GBP) < 5.00` which would return the following data:

| Id |  Product | Category | Amount (GBP) | Associated User |
|:-- | :-- | :-- | :-- | :-- |
| 321 | Guide to Microsoft Windows | Books | 0.99 | 3 |
| 322 | Guide to MacOS | Books | 1.99 | 3 |

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

![Query Interface](/src/assets/book/query_interface.png)

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

Filtering a Number field is straightforward, you can find rows where a number is the same, not the same, greater than or less than a number.

In the below video clip we can see that we can apply a query to a number column, including specifying the decimal places.

:video{src="/src/assets/book/querying_number_column.webm"}

#### String Columns

There are fewer filtering options for strings as you cannot use the comparison operators (e.g. Greater than, less than) but you can use the `LIKE` operator to come up with wildcard searches, so if you want to search for a word that starts with, contains or ends with, you can do so!

If I wanted to search for any "Category" beginning with "Bo" then my query value would be `Bo%` and it will match on anything that starts with "Bo"!

:video{src="/src/assets/book/querying_string_column.webm"}

Maybe you need to return data for a certain list of categories? Well, in that case you can use the `IN` operator and define a comma separated list of values for it to filter on.

:video{src="/src/assets/book/querying_with_like.webm"}


> **Tip ✨**
>
> When using the `LIKE` operator, you can use as many instances of a wildcard (e.g. `%`) as you like. There is also another wildcard character which represents a single wildcard character: `_`. So if you wanted to search for `L%on` then that would match "London", "Leon" and "Lisbon" but if you did `L___on`, that would only match "Lisbon" and "London" and if you did `L_on` that would only return "Leon".

#### Boolean Columns

When querying Boolean columns you really only have two options, either `=` or `!=`. The Query Interface is also context aware so will give you a checkbox to define your value, this is to avoid confusion as there are many ways of representing `true` or `false` such as 1 or 0 or "True" and "False".

:video{src="/src/assets/book/querying_bool_column.webm"}

#### Table Relationship Columns



> **Note 📝**
>
> You cannot filter on File or Image columns.


### Defining a Condition

## Combining Conditions

### AND

### OR

### Groups
