Work In progress 

Roche:
Worked on Roche billing dashboards, cost optimisation, cost allocation etc 
Brought data from Redshift into Tableau and built dashboards on it to present to clients
Automated Billing reports from redshift and sent via an email. 
Built queries to visualise data 

Deloitte:
Worked on Data migration projects Brining data from oracle to snowflake 

# Data Engineering Projects

This page is written in clean **MkDocs‑friendly Markdown** so you can paste it directly into your site (for example: `docs/projects.md`).

---

## **Project 1 — Oracle → Azure Data Factory → Snowflake (Care First)**

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

## **Project 2 — Oracle → AWS (Centene)**

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

## **Project 3 — Discovery & Data Mapping (Exploratory Project)**

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

### How to add this to MkDocs

1. Save this file as:
```
docs/projects.md
```

2. Update `mkdocs.yml`:
```yaml
nav:
  - Home: index.md
  - Python Interviews: python-interview.md
  - Projects: projects.md
```

