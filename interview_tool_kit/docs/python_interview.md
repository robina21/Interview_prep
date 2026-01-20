
# Python Interview Questions for Data Engineers

## 🧠 Basics

Data Types in Python:
Python offers numerous built-in data types that provide varying functionalities and utilities.

### Immutable Data Types

1. **int** – Whole numbers like `42`
2. **float** – Decimal numbers like `3.14`
3. **complex** – Real + imaginary parts, e.g., `3+4j`
4. **bool** – `True` or `False`
5. **str** – Unicode characters
6. **tuple** – Ordered, immutable collection
7. **frozenset** – Immutable set
8. **bytes** – Immutable byte sequence
9. **bytearray** – Mutable bytes
10. **NoneType** – Represents no value

---

### Mutable Data Types

1. **list** – Ordered, dynamic collection
2. **set** – Unique, unordered values
3. **dict** – Key–value pairs
4. **memoryview** – View memory buffers
5. **array** – Typed array
6. **deque** – Double‑ended queue
7. **object** – Root of all Python classes
8. **SimpleNamespace** – Flexible attribute storage
9. **ModuleType** – Module object
10. **FunctionType** – Function object


**Q2. What’s the difference between `is` and `==` in Python?**  
- `==` compares values, `is` checks identity (memory location).
is: Compares the memory address or identity of two objects.
==: Compares the content or value of two objects.


**Q4. What's the difference between a list and a tuple?**  
- Lists are mutable; tuples are immutable and faster.
Lists are ideal for collections that may change in size and content. They are the preferred choice for storing data elements.

Tuples, due to their immutability and enhanced performance, are a good choice for representing fixed sets of related data.


**Q5. What's the difference between append and extend ?**
-  Append adds object to the end of list = [1,2,3,[4,5]]
-  Extend adds individual objects to the list at the end

**What is the difference between Python Arrays and lists?**
Arrays in python can only contain elements of same data types i.e., data type of array should be homogeneous. It is a thin wrapper around C language arrays and consumes far less memory than lists.
Lists in python can contain elements of different data types i.e., data type of lists can be heterogeneous. It has the disadvantage of consuming large memory.

**kwargs and args**
In Python, *args and **kwargs are often used to pass a variable number of arguments to a function.

*args collects a variable number of positional arguments into a tuple, while **kwargs does the same for keyword arguments into a dictionary.

The name *args is a convention. The asterisk (*) tells Python to put any remaining positional arguments it receives into a tuple.

 The double asterisk (**) is used to capture keyword arguments and their values into a dictionary.

 args:
 def sum_all(*args):
    result = 0
    for num in args:
        result += num
    return result

print(sum_all(1, 2, 3, 4))  # Output: 10

 kwargs:
 def print_values(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

Keyword arguments are captured as a dictionary
print_values(name="John", age=30, city="New York")
---


## 🛠️ Advanced Topics for Data Engineering

**Q11. How to read a file line by line?**
```python
with open('file.txt') as f:
    for line in f:
        print(line)
```

**Q21. How do you read a large file without loading into memory?**

```python
with open('large.csv') as f:
    for line in f:
        process(line)
```

---