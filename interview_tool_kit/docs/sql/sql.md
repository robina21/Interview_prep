
# SQL Interview Questions for Data Engineers

## 🧾 Basic Queries

**Q1. What is the difference between `WHERE` and `HAVING`?**  
- `WHERE` filters rows before grouping; `HAVING` filters groups after aggregation.

**Q2. How do you fetch only unique values from a column?**  
```sql
SELECT DISTINCT column_name FROM table_name;
```

**Q3. How to get the second highest salary from an employee table?**  
```sql
SELECT MAX(salary) FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**Q4. How do you rename a column in the result set?**  
```sql
SELECT column_name AS new_name FROM table_name;
```

---

## 🧮 Aggregations & Grouping

**Q5. How to count the number of employees per department?**  
```sql
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

**Q6. How to calculate average salary by job role?**  
```sql
SELECT job_role, AVG(salary) FROM employees GROUP BY job_role;
```

**Q7. How to filter groups with more than 10 employees?**  
```sql
SELECT department, COUNT(*) FROM employees
GROUP BY department
HAVING COUNT(*) > 10;
```

---

## 🔗 Joins

**Q8. What’s the difference between INNER JOIN and LEFT JOIN?**  
- `INNER JOIN` returns matching rows; `LEFT JOIN` returns all from left + matches.

**Q9. How to get employees and their department names?**  
```sql
SELECT e.name, d.name
FROM employees e
JOIN departments d ON e.dept_id = d.id;
```

**Q10. How to find employees without a manager (using LEFT JOIN)?**  
```sql
SELECT e.name FROM employees e
LEFT JOIN employees m ON e.manager_id = m.id
WHERE m.id IS NULL;
```

---

## 📐 Subqueries & CTEs

**Q11. What is a CTE and when would you use it?**  
- A Common Table Expression makes complex queries more readable and reusable.

**Q12. Write a query using a CTE to get top 5 salaries.**  
```sql
WITH ranked AS (
  SELECT name, salary,
         DENSE_RANK() OVER (ORDER BY salary DESC) AS rank
  FROM employees
)
SELECT * FROM ranked WHERE rank <= 5;
```

**Q13. How to use a correlated subquery?**  
```sql
SELECT name FROM employees e
WHERE salary > (SELECT AVG(salary) FROM employees WHERE department = e.department);
```

---

## 🪟 Window Functions

**Q14. How to calculate running total of salaries?**  
```sql
SELECT name, salary,
       SUM(salary) OVER (ORDER BY name) AS running_total
FROM employees;
```

**Q15. How to get each employee’s rank based on salary within department?**  
```sql
SELECT name, department,
       RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS dept_rank
FROM employees;
```

---

## 📋 Miscellaneous

**Q16. What’s the difference between `UNION` and `UNION ALL`?**  
- `UNION` removes duplicates, `UNION ALL` includes all.

**Q17. How to get rows between two dates?**  
```sql
SELECT * FROM orders
WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31';
```

**Q18. How to delete duplicate records but keep one?**  
```sql
DELETE FROM employees
WHERE id NOT IN (
  SELECT MIN(id)
  FROM employees
  GROUP BY name, department
);
```

**Q19. What are indexes and why are they used?**  
- Indexes speed up read queries by allowing faster lookup but slow down inserts/updates.

**Q20. How to find null values in a column?**  
```sql
SELECT * FROM employees WHERE manager_id IS NULL;
```
