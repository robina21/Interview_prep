Primary Key:
Unique column in a table
No null values are allowed
a table can have only 1 primary key

> diff between delete, drop, truncate:
“DELETE removes rows from a table and can be used with or without a WHERE clause. It is a DML operation and can be rolled back before commit.

TRUNCATE removes all data from the table but keeps the table structure. It is faster than DELETE, does not support WHERE clause, and cannot be rolled back.

DROP removes the entire table including its structure and data, and it cannot be rolled back.”

> How would you find and remove duplicate records from a table in SQL?
“I use ROW_NUMBER with PARTITION BY to identify duplicates and remove rows where row_number is greater than 1.”

the below will help ony; to select dupliactes not delete.
SELECT customer_id, order_date, COUNT(*)
FROM orders
GROUP BY customer_id, order_date
HAVING COUNT(*) > 1;

“In ETL pipelines, I usually remove duplicates using SQL before loading or by using a Sorter + Aggregator transformation.”

>What is the difference between WHERE and HAVING clauses?
“WHERE clause is used to filter rows before aggregation, whereas HAVING clause is used to filter aggregated results after GROUP BY.”

WHERE → filters rows before aggregation

HAVING → filters groups after aggregation

> What is a CTE and why do we use it?
“A CTE, or Common Table Expression, is a temporary named result set that you can reference within a larger query. It helps simplify complex queries, improves readability, and avoids repeating the same subquery multiple times. Essentially, it makes SQL easier to write and maintain.”

> What is a window function, and when would you use it instead of GROUP BY?
“A window function performs calculations across a set of rows related to the current row, without collapsing the rows like GROUP BY does. It’s useful when you need aggregates along with detailed row-level data, such as running totals, ranks, or moving averages.”

>You have a table orders with millions of rows. You need to load only the new records daily into your data warehouse.
👉 How would you handle this using SQL?
“I would use incremental loading by identifying new or changed records using a timestamp column like last_updated or a unique ID. In SQL, I would filter source data where last_updated > last ETL run date and load only those rows. This reduces the volume of data processed and improves ETL performance.”

