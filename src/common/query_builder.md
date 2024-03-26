# Query Builder

Queries are the most effective way of requesting a specific set of data. The query builder lends itself to a high degree of customisation.

Any query can use multiple lines & these lines can be grouped:
- Multi-line - A query may have multiple lines to specify a heightened set of criteria and display a more specific set of jobs.
- Group queries - Lines of a query can be grouped together so that their conditions are inextricably linked. Groups can exist within groups.

**Reporting**

The jobs which appear in the jobs page are those which adhere to the current query. This query can be seen by pressing the query button in the top right hand corner. To read more on queries in [Reporting]

**Tables**

Any table can be manually queried by clicking the edit button in a datastore. The query builder will appear above the table content.

The 'field' box relates to the columns which exist in either that table or any related table. Columns in related tables will be shown as: "TableName.ColumnName".

The query builder contains many different operators. They are as follows

| Operator | Description              | Example              |
|----------|--------------------------|----------------------|
| "="      | Equals to                | 5 = 5 returns TRUE
| "!="     | Not equals               | 5 != 6 returns TRUE  |
| "<>"     | Not equals               | 5 <> 4 returns TRUE  |
| ">"      | Greater than             | 4 > 5 returns FALSE  |
| "<"      | Less than                | 4 < 5 returns TRUE   |
| ">="     |Greater than or equal to | 4 >= 5 returns FALSE |
|"<=" |Less than or equal to |4 <= 5 returns TRUE |
|"<=" |Not less than |4 !< 5 returns FALSE |
|"!>" |Not greater than |4 !> 5 returns TRUE |
|"LIKE" |TRUE if the operand matches a pattern specially with wildcard.(%) | |
|"In" |TRUE if the operand is equal to one of a list of expressions. | |
|"Not in" |True if the operand is not equal to one of a list of expressions. | |

The 'value' field is where you insert what values to query for / against. Depending on which data type you have specified in the field box, the way you input the value will change. E.g A column type of 'date' will provide a data picker whereas 'string' will let you type text. The value field can have case sensitivity toggled on or off via the button on the right hand side.


**Tables Within Activities**

Tables can also be queried within many different table actions. The most common of which is 'get table data', which by default will return a table in its entirety. By using table queries you can make it return only the relevant data which can be utilised elsewhere in your automation. This is especially useful when dealing with big data.

By clicking the variable button in a field and choosing a datachip you could even begin to query using contextual data within your automation.

**Apps**

Queries can also be used within app components e.g Repeating layout. The option to do so will appear when you choose your datasource by clicking the variable button. The query can be edited by clicking the variable button again.

