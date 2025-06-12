
# Python Interview Questions for Data Engineers

## 🧠 Basics

**Q1. What are Python's key features?**  
- Interpreted, dynamically typed, object-oriented, open-source, and has extensive libraries.


**Q2. What’s the difference between `is` and `==` in Python?**  
- `==` compares values, `is` checks identity (memory location).

**Q3. How do you swap two variables without a temporary variable?**
```python
a, b = b, a
```

**Q4. What's the difference between a list and a tuple?**  
- Lists are mutable; tuples are immutable and faster.


**Q5. What's the difference between append and extend ?**
-  Append adds object to the end of list = [1,2,3,[4,5]]
-  Extend adds individual objects to the list at the end
---



## 🗃️ File Handling & Error Handling

**Q11. How to read a file line by line?**
```python
with open('file.txt') as f:
    for line in f:
        print(line)
```

**Q12. How does Python handle exceptions?**
```python
try:
    1/0
except ZeroDivisionError:
    print("Cannot divide by zero")
```

---

## 📊 Data Analysis (Pandas / NumPy)

**Q13. How do you handle missing data in pandas?**
```python
df.dropna(), df.fillna(0)
```

**Q14. How to group data in pandas?**
```python
df.groupby('column').agg({'sales': 'sum'})
```

**Q15. How to filter rows in a DataFrame?**
```python
df[df['value'] > 100]
```

---


## 🛠️ Advanced Topics for Data Engineering

**Q20. What is a Python decorator?**
```python
def decorator(func):
    def wrapper():
        print("Before")
        func()
        print("After")
    return wrapper
```

**Q21. How do you read a large file without loading into memory?**
```python
with open('large.csv') as f:
    for line in f:
        process(line)
```

**Q22. What is the GIL in Python?**  
- Global Interpreter Lock prevents multiple native threads from executing Python bytecodes at once.

---

## ✅ Tips for Interviews

- Focus on writing clean and readable code
- Know common libraries: `pandas`, `numpy`, `collections`, `itertools`
- Be able to explain your reasoning out loud
