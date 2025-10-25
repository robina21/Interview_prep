# Slowly Changing Dimensions (SCDs)

## What is an SCD?

A **Slowly Changing Dimension** tracks how dimension data changes over time.  
For example, when a customer moves to a new city, do we overwrite it or keep history?

---

## Types of SCDs

### 🟩 Type 1 – Overwrite
Old data is replaced by new data.

| customer_key | name  | city  |
|---------------|-------|-------|
| 501 | Alice | Seattle |

➡ Alice moves to Denver  
→ Updated record (no history)

| customer_key | name  | city  |
|---------------|-------|-------|
| 501 | Alice | Denver |

✅ Simple  
❌ No history

---

### 🟦 Type 2 – Add New Record
Old record is retained; new record is added with a new surrogate key.

| customer_key | name  | city | start_date | end_date |
|---------------|-------|------|-------------|-----------|
| 501 | Alice | Seattle | 2022-01-01 | 2023-04-01 |
| 502 | Alice | Denver | 2023-04-02 | NULL |

✅ Keeps history  
❌ Grows table size  

---

### 🟨 Type 3 – Add New Column
Store both old and new values in same record.

| customer_key | name | old_city | current_city |
|---------------|------|-----------|---------------|
| 501 | Alice | Seattle | Denver |

✅ Simple and compact  
❌ Only one level of history  

---

## Summary Table

| Type | Description | History Preserved? |
|------|--------------|--------------------|
| Type 1 | Overwrite old data | ❌ |
| Type 2 | Add new record | ✅ |
| Type 3 | Add new column | ⚠️ Partial |

---

## Which Type to Use?

- **Type 1** → When changes are unimportant (e.g., typo fix)
- **Type 2** → When tracking history is critical (e.g., address, department)
- **Type 3** → When limited history is acceptable (e.g., current vs previous)

Why are SCDs important?:

Historical tracking: They allow you to track changes over time, which helps with accurate reporting and analysis. 
For example, you can analyze a store's sales by its region before and after a reorganization.

Data integrity: They ensure that historical data remains accurate, preventing metrics from becoming unreliable as dimensions change.

Business insights: By capturing historical context, businesses can connect performance changes to the specific attribute versions that were in effect at the time. 