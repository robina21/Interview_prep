>what did you do in informatica ?
“In Informatica, I worked on  maintaining ETL mappings and workflows. I used it to perform source-to-target data mapping, apply transformations like filtering, joins, lookups, aggregations, and data cleansing, and load data into target tables while ensuring data quality and consistency.”

“I analyzed source data, designed mappings based on source-to-target documents, implemented transformations, handled slowly changing dimensions, and scheduled workflows to automate daily and incremental loads.”

> What is the difference between Source Qualifier and Filter transformation?
SQL is used to filter rows at the source level before they enter the mapping, reducing the volume of data processed, whereas a Filter transformation filters data later in the pipeline.

> What is Target Load Order and when is it used?
It defines the order in which data is loaded into targets, particularly crucial when targets have primary-foreign key constraints. It is configured in the Session Properties.

>What are the different types of targets in Informatica?
Relational tables (databases), Flat files (CSV, fixed-width), XML, and other applications.

🔹 How Do You Do a Filter in Informatica?
Primary way: Filter Transformation

“I use a Filter transformation to filter records based on a condition.”

Example:

Condition:

salary > 50000 AND status = 'ACTIVE'

Only records meeting the condition pass through.

🔹 Other Ways to Filter in Informatica (Important)
1️⃣ Source Qualifier Filter (Best for performance)

“I apply filters in the Source Qualifier whenever possible to push filtering to the source database.”

Example:

WHERE created_date >= SYSDATE - 1

✔ Reduces data volume early
✔ Improves performance

2️⃣ Expression Transformation

“I use Expression transformation with conditional logic and route records using ports.”

Example logic:

IF(status = 'ACTIVE', 1, 0)

Then connect only valid records.

3️⃣ Router Transformation

“Router transformation is used when I need multiple filtering conditions in one place.”

Example:

Group 1: status = 'ACTIVE'

Group 2: status = 'INACTIVE'