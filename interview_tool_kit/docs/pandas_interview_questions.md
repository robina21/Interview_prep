
# Pandas Interview Questions for Data Engineers (with Explanations)

## 📥 Data Loading & Exploration

**Q1. How do you read a large CSV file in chunks using Pandas?**  
Use `chunksize` to load the file in smaller parts to save memory.
```python
chunks = pd.read_csv('data.csv', chunksize=10000)
for chunk in chunks:
    process(chunk)
```

**Q2. How do you get a quick summary of a DataFrame?**  
Use `info()`, `describe()`, and `head()` to get structure, statistics, and sample data.
```python
df.info()
df.describe()
df.head()
```

**Q3. How do you detect missing values?**  
Use `isnull().sum()` to count nulls per column.
```python
df.isnull().sum()
```

---

## 🧹 Data Cleaning

**Q4. How to drop rows with any null values?**  
`dropna()` removes all rows with at least one NaN.
```python
df.dropna()
```

**Q5. How to fill missing values with the median of a column?**  
`fillna()` can fill NaNs with median, mean, or custom values.
```python
df['column'].fillna(df['column'].median(), inplace=True)
```

**Q6. How to convert a column to datetime?**  
Use `pd.to_datetime()` to ensure proper datetime parsing.
```python
df['date'] = pd.to_datetime(df['date'])
```

**Q7. How to remove duplicates from a DataFrame?**  
`drop_duplicates()` keeps the first instance and drops repeated rows.
```python
df.drop_duplicates(inplace=True)
```

---

## 🔍 Filtering, Sorting & Mapping

**Q8. How to filter rows where salary > 100K and department = 'IT'?**  
Use boolean conditions with `&` for AND logic.
```python
df[(df['salary'] > 100000) & (df['department'] == 'IT')]
```

**Q9. How to apply a function to a column?**  
Use `apply()` to perform row-wise or column-wise transformations.
```python
df['salary_bracket'] = df['salary'].apply(lambda x: 'High' if x > 100000 else 'Low')
```

**Q10. How to sort data by two columns?**  
Use `sort_values()` with `ascending` flags.
```python
df.sort_values(by=['department', 'salary'], ascending=[True, False])
```

---

## 🔁 GroupBy & Aggregation

**Q11. How to group by department and calculate average salary?**  
`groupby()` with aggregation helps summarize data.
```python
df.groupby('department')['salary'].mean()
```

**Q12. How to get count and sum in one groupby operation?**  
`agg()` allows multiple aggregations on grouped data.
```python
df.groupby('department').agg({'salary': ['count', 'sum']})
```

---

## 🔗 Joins & Merges

**Q13. How to perform an inner join on two DataFrames?**  
`pd.merge()` works like SQL JOINs.
```python
pd.merge(df1, df2, on='id', how='inner')
```

**Q14. How to do a left join using different column names?**  
You can specify different key names using `left_on` and `right_on`.
```python
pd.merge(df1, df2, left_on='emp_id', right_on='id', how='left')
```

---

## 📏 Reshaping Data

**Q15. How to pivot a table to summarize data?**  
Use `pivot_table()` to create cross-tabulations.
```python
df.pivot_table(index='department', columns='gender', values='salary', aggfunc='mean')
```

**Q16. How to melt a wide table into a long format?**  
`melt()` is useful for unpivoting columns into rows.
```python
pd.melt(df, id_vars=['id'], var_name='attribute', value_name='value')
```

---

## 🧠 Optimization & Performance

**Q17. How do you handle memory issues with large data sets?**  
Use `dtype`, `usecols`, and `chunksize` to control memory usage.

**Q18. How to optimize string columns?**  
Convert strings to category dtype for better performance.
```python
df['category_column'] = df['category_column'].astype('category')
```

---

## 📆 Date & Time Operations

**Q19. How to extract year and month from a datetime column?**  
Use `dt` accessor to break down datetime parts.
```python
df['year'] = df['date'].dt.year
df['month'] = df['date'].dt.month
```

**Q20. How to calculate the number of days between two dates?**  
Subtract datetime columns and use `.dt.days`.
```python
df['days'] = (df['end_date'] - df['start_date']).dt.days
```

---

## 🧪 Real-World Case

**Q21. You get a daily CSV dump with millions of rows. How do you deduplicate and load only new records into a database?**  
Use chunking, hash comparison, and staging tables to identify new data before loading.

**Q22. How to check for data consistency between two large DataFrames (e.g., source vs target)?**  
Compare with `.equals()` or find differences using `concat()` and `drop_duplicates()`.
```python
df1.equals(df2)
pd.concat([df1, df2]).drop_duplicates(keep=False)
```

---

## ✅ Interview Tips

- Practice real-world data cleanup and profiling.
- Be fluent in joins, groupby, filtering, and performance tuning.
- Know how to work with large files and time-based operations.
