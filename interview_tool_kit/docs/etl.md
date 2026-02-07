How do you optimize ETL performance? 

> Parallel processing
breaking down ETL tasks into smaller units that can be executed concurrently across multiple threads, processors, or nodes

> Data partitioning
By dividing large datasets into smaller, manageable partitions based on predefined criteria

> Optimizing SQL queries 
The SQL queries used in ETL processes can be optimized to improve performance by reducing execution time and resource consumption. 

Incremental loading and CDC (change data capture)

Incremental loading involves updating only the changed or new data since the last ETL run rather than processing the entire dataset.

Describe the use of Lookup Transformation in ETL.

> How do you write efficient SQL queries for ETL?
Indexing
Ensure that primary and foreign key columns are indexed to speed up joins and lookups.

Optimizing joins is another strategy

Pitfalls to avoid
There are also common pitfalls that hamper the performance of SQL queries. These include:

SELECT *: Do not select all columns when necessary. It is better to specify the required columns to reduce the amount of data processed and transferred.
Performing many functions in WHERE clauses: It’s better to calculate values outside the query or use indexed computed columns.
Not using batch processing: Break down large operations into smaller batches to avoid long-running transactions and reduce lock contention.
Inappropriate data types: Choose the most efficient data types for your columns to save storage and improve performance.

> How to optimise a sql query ?
avoid using select * statements, 
Use the right WHERE clause (filter early)
Write efficient JOINs
“Indexes help the optimizer avoid full table scans.”
Use INNER JOIN instead of LEFT JOIN if possible
    > WHY it helps

    LEFT JOIN keeps unmatched rows → more data processed

    INNER JOIN filters earlier

    Fewer rows → faster join
Use EXISTS instead of IN (for large datasets)

First, I analyze the query to understand which part is slow. I avoid using SELECT * and fetch only required columns to reduce data scanning.

I check joins and prefer INNER JOINs instead of LEFT JOINs wherever possible, because inner joins reduce the number of rows processed.

I make sure indexes exist on columns used in WHERE clauses and JOIN conditions, and I avoid applying functions on indexed columns so the index can be used effectively.

I also check the execution plan to see if there are any full table scans and optimize accordingly.”

> why should you not index all columns 
We don’t index all columns because indexes take additional storage and every insert, update, or delete operation also needs to update the index. Too many indexes slow down write performance and increase maintenance overhead. So we only index columns that are frequently used in joins, filters, and sorting.”

> what are the different transformations have you done ?
Trimming spaces, converting text to upper/lower case

Handling missing values using defaults or conditional logic

Filtering out invalid or rejected records

> Data type conversions
String to ---> date / timestamp conversions
“I used CAST, CONVERT, CASE, and TRY_CAST to avoid runtime failures.”
“I first check the format of the incoming string to ensure it matches the expected date format. For example, DD-MM-YYYY or YYYY-MM-DD.”

TO_DATE(source_date, 'DD-MM-YYYY')
in python/pandas
df['target_date'] = pd.to_datetime(df['source_date'], format='%d-%m-%Y', errors='coerce')


********** ANSWER THE BELOW ***********
“If the source column is decimal but Athena expects an integer, I first check if it’s possible to safely cast or convert the type. If yes, I perform the conversion in Pandas or PySpark before loading, ensuring no data is lost. If casting isn’t feasible and the business allows, I load it as a string to avoid load errors. Throughout, I validate the data to make sure the transformation aligns with business requirements.”

> joins & lookups
I performed lookups and joins across multiple source systems

>>>>>Current project

I bring the data from s3 for example
and do a virus scan [affected files)]
since I work with healt care data we use a aws service called macie which will check for PHI/PII information and flag it
then we get the data dict and get the data types and create tables and then load to redshift 

then we do some dq checks 
like checking for null vs empty
consistency checks
