# Indexes

An `Index` is a database object that improves the speed of data retrieval operations by allowing the database engine to find rows more quickly. Indexes work like a table of contents, making searches faster, especially for large datasets.

![Add Index Example](/src/assets/add_index.gif)

## How Indexes Improve Performance
- Faster `SELECT` queries: The database doesn't need to scan the entire table.
- Efficient filtering and sorting: Indexes optimize `WHERE`, `ORDER BY`, and `JOIN` operations.
- Reduced disk I/O: Less data needs to be read from storage.

## Considerations When Using Indexes
- Indexes take up additional storage.
- Frequent updates (`INSERT`/`UPDATE`/`DELETE`) can slow down performance since indexes must be maintained.
- Not all queries benefit from indexes, especially small tables where a full table scan is just as fast.

## Index Types

### Hash
Hash indexes can only be used for equality comparisons, so those using the `=` or `<=>` operators. They cannot be used for ordering, and provide no information to the optimizer on how many rows exist between two values.

 Hash indexes do not permit leftmost prefixing - only the whole index can be used.

### B-Tree
B-tree indexes are used for column comparisons using the `>`, `<=`, `=`, `>=`, `<` or `BETWEEN` operators, as well as for `LIKE` comparisons that begin with a constant. B-tree indexes also permit leftmost prefixing for searching of rows.

 If the number or rows doesn't change, hash indexes occupy a fixed amount of memory, which is lower than the memory occupied by `BTREE` indexes.

### FullText
A full-text index in our database architecture is an index of type `FULLTEXT`, and it allows more options when searching for portions of text
from a field.

### Composite
Composite indexes, which involve multiple columns, can be extremely powerful when used correctly.
- Order Matters: In a composite index, the order of the columns matters. Place the most selective column (the one that filters out the most rows) first.
- Covering Indexes: A composite index that includes all the columns needed by a query is known as a covering index. Using a covering index can eliminate the need for the database to access the table data at all, further speeding up queries.

## Unique
A unique index ensures that the value in the column(s) selected for each row is unique and cannot be present more than once.

If a column has duplicate values, this create operation will fail.

When using a `Composite` index, the hash of the combined values will form a key and prevent that exact combination from being duplicated.
