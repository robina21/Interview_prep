# Star Schema

## What is a Star Schema?

A star schema is a type of data modeling technique used in data warehousing to represent data in a structured and intuitive way. In a star schema, data is organized into a central fact table that contains the measures of interest, surrounded by dimension tables that describe the attributes of the measures.

Fact Table:
The fact table in a star schema contains the measures or metrics that are of interest to the user or organization. 

Dimension Table:
    > The dimension tables in a star schema contain the descriptive attributes of the measures in the fact table.
    > Each dimension table is joined to the fact table through a foreign key relationship.
This allows users to query the data in the fact table using attributes from the dimension tables.

This schema is widely used to develop or build a data warehouse and dimensional data marts. 
It includes one or more fact tables indexing any number of dimensional tables. 
The star schema is a necessary cause of the snowflake schema. 
It is also efficient for handling basic queries. 

Denormalized structure: A star schema is denormalized, which means that redundancy is allowed in the schema design to improve query performance. This is because it is easier and faster to join a small number of tables than a large number of tables.

It is designed for fast query performance. This is because the schema is denormalized and data is pre-aggregated, making queries faster and more efficient.
