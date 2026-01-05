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

```sql
CREATE VIEW category_sales_summary AS
SELECT
    p.category,
    COUNT(o.order_id) AS total_orders,
    SUM(o.order_total) AS total_sales
FROM orders o
JOIN products p ON o.product_id = p.product_id
GROUP BY p.category;
