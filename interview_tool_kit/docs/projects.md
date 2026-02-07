# Data Engineering Projects




## **Health Care Triangle Projects [ROCHE]**
- Developed Roche billing and cost optimization dashboards in Tableau for client reporting and decision-making.
- Extracted and modeled data from Amazon Redshift to support analytics and visualization.
- Designed and optimized SQL queries for accurate billing insights and trend analysis.
- Automated recurring billing reports from Redshift and delivered them to clients via scheduled emails.
- Improved reporting efficiency and reduced manual effort through automation.

---
## **Deloitte Projects**
### **Project 1 — Oracle → Azure Data Factory → Snowflake (Care First)**

### Objective  
Migrate historical data from **Oracle to Snowflake** using **Azure Data Factory (ADF)** with a SQL Server control layer for orchestration and tracking.

### What I built and implemented

- Designed an **end‑to‑end migration framework** for table‑by‑table loading.
- Created and maintained **SQL Server stored procedures** to control and track loads.
- Built **metadata tables** in SQL Server to manage:
  - Source table list
  - Load status
  - Start/complete timestamps
  - Error tracking
- Automated a **table‑driven loop** that:
  1. Reads the next table from metadata
  2. Updates status to **"STARTED"** in SQL Server
  3. Triggers Azure Data Factory pipeline
  4. Loads data into Snowflake
  5. Updates status to **"COMPLETED"** in SQL Server
  6. Moves to the next table
- Implemented restartability so failed tables could be rerun without reloading everything.

### Tech stack
- Oracle
- Azure Data Factory
- Snowflake
- SQL Server (control/metadata layer)

---

### Project 2 — Oracle → AWS (Centene)

### Objective
Build an automated ingestion framework to move data from **Oracle to AWS Redshift** using AWS Glue and S3.

### What I built and implemented

- Developed **AWS Glue jobs** to:
  - Create target tables in Redshift
  - Load data from S3 into Redshift
- Designed a **control file in S3** to drive loads (table name, file name, target, etc.).
- Built parameterized **SQL templates** for loading and validation.
- Updated **DynamoDB configuration tables** with metadata such as:
  - File name
  - Target table/location
  - File size
  - Load status
  - Timestamps
- Implemented automated pipeline flow:
  1. Oracle extract → S3 landing
  2. Metadata written to DynamoDB
  3. Glue job reads config and loads Redshift
  4. Status updated on success/failure
- Performed **Source‑to‑Target (S→T) data mapping**.
- Analyzed existing data flows in **Informatica** to align mappings with AWS implementation.

### Tech stack
- Oracle
- AWS S3
- AWS Glue
- Amazon Redshift
- DynamoDB
- Informatica (analysis)

---

### Project 3 — Discovery & Data Mapping (Exploratory Project)

### Objective
Analyze source systems and define a clean, duplicate‑free loading strategy.

### What I did

- Performed deep **data profiling and exploratory analysis**.
- Created detailed **source‑to‑target mappings**.
- Wrote complex **SQL queries** to:
  - Identify correct join paths across multiple tables
  - Remove duplicates
  - Apply necessary business filters
  - Define primary keys and uniqueness rules
- Documented transformation logic for downstream ingestion.

### Key skills demonstrated
- SQL joins (inner, left, multi‑table)
- Deduplication strategies
- Data quality validation
- Requirements gathering from raw data

---


### **Genentech Projects**

- Designed and orchestrated end-to-end ETL workflows using AWS Step Functions to manage multi-step data pipelines.
- Developed and deployed Talend-based ETL pipelines for AWS cloud environments.
- Built and managed AWS Glue ETL jobs for data ingestion, transformation, and quality validation.
- Implemented custom data quality checks and schema evolution in AWS Glue to ensure reliable analytics.
- Designed automated sensitive data detection workflows using AWS Macie for data governance and compliance.
- Loaded and optimized datasets in Amazon Redshift Serverless for reporting and analytics.
- Developed complex Spark SQL and PySpark transformations for large-scale data processing.
- Migrated data from on-prem FTP servers to PostgreSQL as part of cloud modernization.
- Established reusable data quality frameworks for enterprise ETL pipelines.