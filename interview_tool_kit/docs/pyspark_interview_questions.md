# PySpark Interview Questions & Answers (With Definitions)

This page is formatted for **MkDocs** and can be saved as:
```
docs/pyspark-interview.md
```

---

## 1) What is PySpark and how does it differ from regular Spark?

**Definition:**  
Apache Spark is a distributed computing engine for large-scale data processing. **PySpark** is the Python API for Apache Spark that allows you to write Spark applications using Python while Spark executes them on a distributed JVM-based engine.

**How it differs from regular (Scala) Spark:**
- Spark core is written in **Scala/Java** and runs on the JVM.
- PySpark provides a **Python interface**, but computations are still executed by the Spark engine.
- PySpark is easier for Python users, but may introduce slight serialization overhead compared to native Scala.
- Performance is generally comparable when using DataFrames (because of Catalyst optimization).

---

## 2) How do you set up a PySpark environment?

**Definition:**  
A PySpark environment is a runtime setup where Python can communicate with a Spark cluster to execute distributed computations.

**Common ways to set it up:**

**Local machine:**
```bash
pip install pyspark
```
```python
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("test").getOrCreate()
```

**Cloud/Production options:**
- **AWS Glue** – Managed Spark environment for ETL.
- **Databricks** – Managed notebooks + clusters.
- **AWS EMR** – You create and manage a Spark cluster.

---

## 3) Explain the architecture of Apache Spark.

**Definition:**  
Spark uses a distributed master–worker architecture to process data in parallel across a cluster.

**Components:**
- **Driver:** Controls the application, creates the DAG, and schedules tasks.
- **Cluster Manager:** (YARN, Mesos, or Standalone) allocates resources.
- **Executors:** Run tasks on worker nodes and store cached data.
- **Tasks:** Smallest unit of work executed on partitions.

**Execution flow:**
```
Driver → Logical Plan → Optimized Plan → DAG → Stages → Tasks → Executors
```

---

## 4) What are RDDs (Resilient Distributed Datasets)?

**Definition:**  
An RDD is Spark’s original distributed data structure representing an immutable, partitioned collection of elements that can be processed in parallel.

**Key properties:**
- Distributed across nodes
- Immutable
- Fault-tolerant via lineage
- Lazy evaluated
- Partitioned for parallelism

**Example:**
```python
rdd = spark.sparkContext.parallelize([1,2,3,4])
```

---

## 5) How do DataFrames and Datasets differ in PySpark?

**Definition:**
- A **DataFrame** is a distributed table with named columns and a schema.
- A **Dataset** is a strongly typed distributed collection (mainly used in Scala/Java).

| Feature | DataFrame | Dataset |
|--------|-----------|---------|
| Schema | Yes | Yes |
| Type safety | No (Python) | Yes (Scala/Java) |
| Performance | Optimized | Optimized |
| Common in PySpark | Yes | Rare |

**In practice:** Most PySpark work uses **DataFrames**.

---

## 6) How do you read and write data using PySpark?

**Definition:**  
PySpark provides a unified data source API to read/write structured data from files, databases, and cloud storage.

**Read CSV:**
```python
df = spark.read.csv("s3://bucket/file.csv", header=True, inferSchema=True)
```

**Write Parquet:**
```python
df.write.mode("overwrite").parquet("s3://bucket/output/")
```

**Read Parquet:**
```python
df = spark.read.parquet("s3://bucket/output/")
```

---

## 7) What are common transformations and actions?

**Definition:**  
- **Transformations** create a new DataFrame/RDD but do not execute immediately (lazy).
- **Actions** trigger execution of the Spark job.

**Common transformations:**
- `select()`, `filter()`, `withColumn()`, `groupBy()`, `join()`

**Common actions:**
- `show()`, `count()`, `collect()`, `write()`

---

## 8) How do you handle missing or null values?

**Definition:**  
Missing values (nulls) must be cleaned before analytics to avoid incorrect results.

```python
df.dropna() drop duplicates
df.fillna(0) fill with value
df.fillna({"age": 30, "salary": 0})
```

---

## 9) Explain lazy evaluation in PySpark.

**Definition:**  
Lazy evaluation means Spark **does not execute transformations immediately**. Instead, it builds a logical plan (DAG) and waits for an action before running.

**Why this matters:**
- Allows Spark to optimize the full pipeline.
- Reduces unnecessary computation.

---

## 10) How do you perform joins in PySpark?

```python
df1.join(df2, on="id", how="inner")
```

**Join types:**
- `inner`, `left`, `right`, `full`, `left_semi`, `left_anti`

---

## 11) What is the role of SparkSession?

**Definition:**  
SparkSession is the single entry point to programming Spark in PySpark.

```python
spark = SparkSession.builder.appName("app").getOrCreate()
```

It replaces older objects like SQLContext and HiveContext.

---

## 12) How do you optimize PySpark jobs?

**Definition:**  
Optimization means improving speed, reducing memory usage, and minimizing data shuffles.

Key techniques:
- Use **Parquet instead of CSV** (columnar + compressed).
- Tune partitions: `df.repartition(200)`.
- Avoid `collect()` on large data (prevents driver OOM errors).
- Use **broadcast joins** for small tables.
- Cache reused DataFrames: `df.cache()`.
- Select only needed columns.

---

## 13) Differences between RDD, DataFrame, Dataset

| Structure | Schema | Performance | Ease of use |
|-----------|--------|-------------|-------------|
| RDD | No | Lower | Hard |
| DataFrame | Yes | High | Easy |
| Dataset | Yes | High | Medium |

---

## 14) How do lazy evaluation and DAG work together?

**Definition:**  
Spark builds a **Directed Acyclic Graph (DAG)** representing transformations before execution.

Process:
1. User defines transformations.
2. Spark builds a logical DAG.
3. Optimizer refines the plan.
4. DAG is split into stages.
5. Tasks run in parallel on executors.

---

## 15) More performance optimization tips
- Use Parquet + ZSTD compression.
- Avoid data skew.
- Use predicate pushdown.
- Increase executor memory if needed.

---

## 16) How do you handle data skew?

**Definition:**  
Data skew happens when some keys have far more records than others, causing slow tasks.

Solutions:
- Key salting
- Broadcast small tables
- Repartition on different keys
- Use `skewHint` in Spark 3+

---

## 17) What are broadcast variables?

**Definition:**  
Broadcast variables efficiently share a small, read-only dataset with all executors.

**Why use them:**
- Reduce network shuffle
- Speed up joins with small tables

```python
from pyspark.sql.functions import broadcast
fact_df.join(broadcast(dim_df), "customer_id")
```

---

## 18) Custom UDF in PySpark

**Definition:**  
A UDF allows you to apply custom Python logic to Spark DataFrames.

```python
from pyspark.sql.functions import udf
from pyspark.sql.types import IntegerType

def square(x): return x*x
square_udf = udf(square, IntegerType())
df = df.withColumn("squared", square_udf(df["value"]))
```

**Note:** Prefer built-in Spark functions when possible.

---

## 19) How do you monitor and debug PySpark?

**Definition:**  
Monitoring helps detect slow jobs, skew, memory issues, and failures.

Tools:
- Spark UI: http://localhost:4040
- AWS Glue CloudWatch logs
- Databricks UI
- YARN Resource Manager
- `spark.sparkContext.setLogLevel("INFO")`

---

### Add this to MkDocs
```yaml
nav:
  - Home: index.md
  - Python Interviews: python-interview.md
  - Projects: projects.md
  - PySpark Q&A: pyspark-interview.md
```

