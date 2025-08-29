# Views

A View is a virtual table based on the result of a table query. It is essentially a stored query that you can treat like a regular table. Instead of storing data itself, a view stores the definition of the query. When you fetch data from a view, the underlying query is executed and the results are returned as if it was a real table.

## Creating a View

At its heart, a View is a reflection of your data query. When building a view, you select the base table, the columns you want to include from that table and the query so that your data is filtered by specific criteria. Imagine you had a table of `Orders`, you want to create a view that only shows orders for books. You would set a filter on the `Category` column to achieve this. The resulting view, which we might call `BookOrders`, would always show the most up-to-date information for that category without you having to manually filter the data each time with a new query.

:video{src="/src/assets/book/create_view.webm"}

## Joins

### Connecting Tables

Real-world data is rarely confined to a single table. You might have customer information in one table, sales orders in another and product details in a third. The `Join` feature in views allows you to combine data from multiple tables, creating a unified and comprehensive dataset.

To create a join you first define your base table for the view, as we did in the section above. Now in the Joins section, press Add and select the next table you want to pull data from in your view. Once you have done this, you pick a common key or matching column between the base table and this new table (e.g. `orderId` in both the `Users` table and `orders` table), Toca will then link the rows together based on the values in the column. This allows you to pull data from both tables as if they were one.

When you join a table into the view, you will need to specify the type of join. These are:
- **An (inner) join**: Only includes rows where the key exists in both tables
- **Left join**: Includes all rows from the base table as well as matching rows from the joining table, when there are no matches the columns containing data from the joining table will be empty
- **Right join**: The same as a left join but it includes all rows from the joining table and matching rows from the base table

For example,  to see the users's name and address alongside each sales order, you would Join the `Orders` table onto the `Users` table on the `Id` column, you would then join the `Addresses` table onto the `Users` table on the address `Id` column.

For more information about joins, the :docs-link[views documentation]{id="projects/automation/datastores/views"} covers this in more detail.

:video{src="/src/assets/book/view_with_join.webm"}

## Column Alias

After joining multiple tables together in a view, one thing that can become confusing is the column names. This is because you might have columns with the same name in the tables you are joining. Luckily, with Views, you can change how the names of a view appear through the aliases. This means that if you had a `Name` column in both your `Users` and `Order` table, you can rename the column that comes from the `Orders` table to `Product_Name` and the one from the `Users` table can be renamed to `Username`. This helps to avoid confusion and makes it much clearer what each column in your view represents.

:view{src="/src/assets/book/view_with_column_alias.webm"}

## Functions

Views also give you access to SQL functions which you can apply to the columns returned by your view. This means that instead of running the data in your view through some transformation pipeline that you might have built inside an activity, your View can actually perform the data transformation directly on the data. The functions are split into the following categories:
- **String functions**: performs text manipulation such as `TRIM()`, `LOWER()`, `SUBSTRING()` etc.
- **Numeric functions**: lets you perform basic mathematical functions such as `+`, `-`, `*`, `/` as well as more advanced functions such as `LOG()`, `SIN()`, `COS()` and `TAN()`
- **Datetime functions**: lets you manipulate and generate date times, particularly useful for getting dates to appear in exactly the format you want. Functions include `NOW()`, `ADDTIME()` and `DATE_FORMAT()`
- **Advanced functions**: These functions cover more advanced use cases which don't necessarily fall into any of the above categories. This includes functions such as `IF()`, `GROUP_CONCAT()` and `ISNULL()`

For more detailed information about any of the functions you have available to you, you can either ask Tocabot (`ctrl+k`) or you can search the web for "MariaDB {insert function name}".

:video{src="/src/assets/book/view_with_sql_function.webm"}

## Group By

### Aggregating Data

Often, you don't need to see every single row of data. Instead, you're interested in summaries — the total sales per region, the average product rating, or the count of orders for each customer. This is where the Group By feature shines.

Group By aggregates rows that have the same value in a specified column. For example, if you group by `category`, all order records for "Electronics" are combined into a single group. Once you've grouped your data, you can apply aggregate functions to get meaningful insights. Below are some of the most common aggregate functions:
- `SUM()`: Calculates the total value of a column (e.g. `SUM(amount)`).
- `AVG()`: Finds the average value.
- `COUNT()`: Counts the number of rows in each group.
- `MAX()`: Finds the highest value.
- `MIN()`: Finds the lowest value.

Continuing with our `Orders` example, to see the total sales for each category, you would Group By the `Category` and use the `SUM()` function on the `amount` column. The result is a concise View showing `Category` and `TotalSales`, eliminating the need to look at every individual sale.

:video{src="/src/assets/book/view_group_by.webm"}

## Having

### Filterting aggregated results

While the Group By statement lets you aggregate data, the Having statement takes it a step further by allowing you to filter those aggregated results. This is a crucial distinction: `WHERE` filters individual rows before they are grouped, while `HAVING` filters the groups after they have been created.

Having statements are used in conjunction with Group By. You can apply a condition to the results of your aggregate functions.

Finishing up our example, you want to see which categories had total sales of over £100. You would add a Having statement to your View: `Having SUM(amount) > 100`. This would filter out all products with sales less than or equal to £100, giving you a clean list of your top performers.

:video{src="/src/assets/book/view_group_by_having.webm"}
