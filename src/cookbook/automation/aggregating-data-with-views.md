# Aggregating Data With Views
Views are useful when you want to aggregate or summarise data without modifying the original tables.  
They allow you to encapsulate logic once and reuse it across reports, apps, or dashboards.

## Scenario: Sales Summary by Product Category

Imagine you are building a sales dashboard for an online store.  
You want to display total sales and order counts per product category.

You already have two tables with live data:

## Source Tables

### 1. `orders` table (30+ rows)

Stores individual customer orders.

| column_name   | description                     |
|---------------|---------------------------------|
| order_id      | Unique order identifier         |
| product_id    | Product being purchased         |
| quantity      | Number of items ordered         |
| order_date    | Date of the order               |
| order_total   | Total price for the order       |

Example rows (out of 30+):

| order_id | product_id | quantity | order_date | order_total |
|--------|------------|----------|------------|-------------|
| 101    | 1          | 2        | 2024-01-05 | 40.00       |
| 102    | 3          | 1        | 2024-01-06 | 25.00       |
| 103    | 2          | 4        | 2024-01-07 | 80.00       |

---

### 2. `products` table (30+ rows)

Stores product details.

| column_name | description               |
|-------------|---------------------------|
| product_id  | Unique product identifier |
| product_name| Name of the product       |
| category    | Product category          |
| price       | Unit price                |

Example rows (out of 30+):

| product_id | product_name | category     | price |
|-----------|--------------|--------------|-------|
| 1         | T-Shirt      | Clothing     | 20.00 |
| 2         | Jeans        | Clothing     | 20.00 |
| 3         | Mug          | Accessories  | 25.00 |

---

## Goal

You want to see:
- Total sales per category  
- Number of orders per category  

Instead of recalculating this every time, you create a **view**.

---

## Creating the Aggregation View

![Fig 1. View Creation Modal](/src/assets/cookbook/aggregating_views/fig_1.png)
**Fig 1. View Creation Modal**

To create a view, we first go to our datastore where our source tables are, and we click the '+' button on the top right and select **Table View**. You will be presented with a modal (Fig 1.) where we can now define our view.

```sql
CREATE VIEW category_sales_summary AS
SELECT
    p.category,
    COUNT(o.order_id) AS total_orders,
    SUM(o.order_total) AS total_revenue
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.category;
```
**Fig 2. SQL Representation of View**

Before we go setup the view lets first design what our view will look like. For this we will mimic the view that would be created by the SQL command in Fig 2.

**category_sales_summary**
| Column Name   | Description                           |
|---------------|---------------------------------------|
| category      | Product category                      |
| total_orders  | The number of orders for that category|
| total_revenue | The total revenue for that category   |

To make this table we will make use of the two source tables `orders` and `products` where orders is the base table and products is JOINed on.

### Joining
Sometimes, you might need to grab data from multiple different tables, such as in our case, we need to grab the product category from the `products` table and the order totals from the order total from `orders` table. In this case, we would make use of a **JOIN** where we would match the product_id column of the `orders` table to the product_id column of the `products` table.

| JOIN Type     | Description                                                                   |
|-------------- |-------------------------------------------------------------------------------|
| JOIN (Inner)  | This type ensures requires that the matching value is present in both tables. |
| Left JOIN     | This type ensures that all records in the left table are present.             |
| Right JOIN    | This type ensures that all records in the right table are present.            |

As we will be using the `orders` table as our base table (see Fig 2.), that becomes our LEFT table, and the `products` table is our RIGHT table.

In this instance, we will make use of the inner JOIN which then requires a mapping to exist between each order and product.

Now that we understand how the table needs to look, lets start building it.

![Fig 3. Adding the source tables](/src/assets/cookbook/aggregating_views/fig_3.png)<br>
**Fig 3. Adding the source tables**

In the table field, we can select `orders` as our base table.

Next, we can click the '+ Add' button under joins section to add a join. By default "JOIN" is already selected, so we can simply select the table, and in the LEFT and RIGHT property fields, simply select the columns to match on.

> **Note:** You cannot join the same table on more than once.

### Queries
![Fig 4. Adding a query](/src/assets/cookbook/aggregating_views/fig_4.png)<br>
**Fig 4. Adding a query**

In our views, we can also set up queries to filter the records. This works similarly to how queries work in other parts of Toca. The only addition here is that now we can filter by the columns across all joined tables.

### Columns
With the joins now sorted, you should see that your view already has a bunch of columns added. By default, when you select a base table, or join a table, the columns of that table are automatically inserted into your view. As we already have our design for the view, we can remove all these columns and start inserting our own.

![Fig 5. Adding a column](/src/assets/cookbook/aggregating_views/fig_5.png)<br>
**Fig 5. Adding a column**

When inserting a columns, there are 4 fields to be aware of:

| Field | Description|
|-------|------------|
| Functions | A function is an instruction which tells the view to treat the value of a cell in certain way. There are many different types of functions such as arithmetic (SUM), text manipulation (CONCAT), conditions (IF) and many more. |
| Value | The value field represents the data that the function will be manipulating. When you click on it, you will see a list of options presented. These are all columns from your base and joined tables. |
| Column name | This is the name that will be given to your column, and is used to reference the column. <br> **Note: If this is changed after being used in automation, your references may be out of date.** |
| Column label | This is the value that is presented as the column header when looking in a datastore.
 |

Let's walk through how we set up each of our columns.

#### category
This column is quite simple. For this, the data doesn't require any manipulation, so we can simple click on the value field, and select the `category` column from the `products` table.

#### total_orders
For this column, we require some manipulation. Here, we want to grab all the orders of the same category, and then add them together. For this, we can make use of a **function**. If we click the function field and search for **SUM**, we can see that a function allows us to do exactly this. We can then select `order_id` from `orders`.

#### total_revenue
Similar to `total_orders`, for this column, we want to fetch the order totals of all orders of a matching category. So, again, we can use the **SUM** function and instead of `order_id`, this time we will pick `order_total` from the `orders` table this time.

### Group By
![Fig 6. Group By](/src/assets/cookbook/aggregating_views/fig_grouping.png)<br>
**Fig 6. Group By**

Now you're columns are aggregating data, we want to make sure that its aggregating correctly. This is where group by comes in. This lets you group data by matching values. So, if we add a grouping for category, the view will accumulate the data from all matching categories to a single row. This allows our **SUM** functions from earlier to also behave correctly, as it now know which values it can sum together.

### Havings
The last piece of table views to look at is havings. Havings is a concept that allows you to further filter down the data but using aggregate functions which isn't possible with a standard query. 

![Fig 7. Havings](/src/assets/cookbook/aggregating_views/fig_having.png)<br>
**Fig 7. Havings**

You will have noticed both in the value field for havings and also the value field when adding a column, there is an icon button on the right hand side (**∑**). This button allows you to add a function to the value field. This allows you to nest functions inside others and create equations like the following:

![Fig 8. Nesting Functions](/src/assets/cookbook/aggregating_views/fig_nested_functions.png)<br>
**Fig 8. Nesting Functions**

This lets you work out the average price across all orders. This is just an example but using this functionality can allow for many complex aggregations to be built.

Finally, now that we have our source tables added, columns have been set up and groupings have been applied, we can finally hit save, and see the final view.

![Fig 9. Final View](/src/assets/cookbook/aggregating_views/fig_final_view_result.png)