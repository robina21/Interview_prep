
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

---

## 🧱 Data Structures & Algorithms

**Q5. How do you implement a queue in Python?**
```python
from collections import deque
queue = deque()
queue.append('a')
queue.popleft()
```

**Q6. How to find duplicates in a list?**
```python
seen = set()
dupes = [x for x in lst if x in seen or seen.add(x)]
```

**Q7. What is a dictionary and how is it used?**  
- Key-value mapping. Fast lookups using hash tables.

**Q8. How do you sort a dictionary by values?**
```python
sorted_dict = dict(sorted(my_dict.items(), key=lambda item: item[1]))
```

---

## 🔄 Loops & Comprehensions

**Q9. What is a list comprehension?**
```python
[x for x in range(10) if x % 2 == 0]
```

**Q10. What is a generator?**
```python
def gen():
    for i in range(5):
        yield i
```

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

## 🧪 Testing & Functions

**Q16. What are *args and **kwargs in Python?**
```python
def func(*args, **kwargs):
    pass
```

**Q17. What is a lambda function?**
```python
square = lambda x: x*x
```

---

## 🧱 Object-Oriented Programming

**Q18. What is inheritance?**
```python
class A: pass
class B(A): pass
```

**Q19. What is a class method vs static method?**
```python
@classmethod def cls_method(cls): pass  
@staticmethod def static_method(): pass
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
