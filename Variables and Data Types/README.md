# Python Basics Cheat Sheet

## 1. Variables and Data Types

### Primitive Data Types:
- **Integer**: Whole numbers, e.g., `x = 10`
- **Float**: Decimal numbers, e.g., `y = 3.14`
- **String**: Text enclosed in single, double, or triple quotes, e.g., `name = "John"`
- **Boolean**: `True` or `False`, e.g., `is_active = True`

### Common Operations:
```python
# Integer
a = 10
b = 5
print(a + b)   # 15

# Float
pi = 3.14
radius = 2
area = pi * radius ** 2  # 12.56

# String
greeting = "Hello"
name = "Alice"
full_greeting = greeting + " " + name  # "Hello Alice"

# Boolean
is_even = (a % 2 == 0)  # True
```

### Type Conversion:
```python
# Converting data types
x = int(3.6)         # 3
y = float(5)         # 5.0
z = str(10)          # '10'
```

### String Formatting:
```python
name = "John"
age = 30
# f-string formatting
print(f"My name is {name} and I am {age} years old.")
```

## 2. Input and Output (I/O)

### User Input:
```python
name = input("Enter your name: ")
print(f"Hello, {name}!")
```

### Reading and Printing:
```python
print("Hello, World!")
```

## 3. String Operations

### Common String Methods:
```python
string = "Hello, Python!"

# String slicing
print(string[0:5])  # 'Hello'

# String methods
print(string.lower())    # 'hello, python!'
print(string.upper())    # 'HELLO, PYTHON!'
print(string.replace("Python", "World"))  # 'Hello, World!'
print(string.find("Python"))   # 7
```

## 4. List Operations

### Creating and Accessing Lists:
```python
fruits = ["apple", "banana", "cherry"]

# Access elements
print(fruits[0])   # 'apple'
print(fruits[-1])  # 'cherry'

# Modify list
fruits.append("orange")      # ['apple', 'banana', 'cherry', 'orange']
fruits.remove("banana")      # ['apple', 'cherry', 'orange']
```

### List Methods:
```python
numbers = [5, 3, 9, 1]
numbers.sort()   # [1, 3, 5, 9]
numbers.reverse()  # [9, 5, 3, 1]
```

## 5. Tuples

### Creating Tuples:
```python
my_tuple = (1, 2, 3)
print(my_tuple[0])  # 1
```

### Immutability:
```python
# Tuples are immutable; you cannot change elements
```

## 6. Dictionaries

### Creating and Accessing Dictionaries:
```python
person = {"name": "Alice", "age": 25}

# Access elements
print(person["name"])  # 'Alice'

# Add/update elements
person["age"] = 30
person["city"] = "New York"  # {'name': 'Alice', 'age': 30, 'city': 'New York'}
```

### Common Dictionary Methods:
```python
print(person.keys())   # dict_keys(['name', 'age', 'city'])
print(person.values()) # dict_values(['Alice', 30, 'New York'])
```

## 7. Type Conversion Functions
```python
int("10")      # Converts string to integer
float("10.5")  # Converts string to float
str(100)       # Converts integer to string
list("abc")    # Converts string to list ['a', 'b', 'c']
```

## 8. Type Checking
```python
type(10)         # <class 'int'>
type(10.5)       # <class 'float'>
type([1, 2, 3])  # <class 'list'>
type({"key": 1}) # <class 'dict'>
```

## 9. Arithmetic Operators
```python
# Addition, subtraction, multiplication, division, and modulus
x = 10
y = 3

print(x + y)  # 13
print(x - y)  # 7
print(x * y)  # 30
print(x / y)  # 3.3333333333333335
print(x % y)  # 1 (remainder)
print(x ** y) # 1000 (exponentiation)
```

## 10. Comparison and Logical Operators

### Comparison Operators:
```python
a = 10
b = 20

print(a == b)  # False
print(a != b)  # True
print(a < b)   # True
print(a > b)   # False
print(a <= b)  # True
print(a >= b)  # False
```

### Logical Operators:
```python
x = True
y = False

print(x and y)  # False
print(x or y)   # True
print(not x)    # False
```

## 11. Python Ranges
```python
range(5)         # Creates range from 0 to 4
list(range(5))   # [0, 1, 2, 3, 4]

# Using start, stop, and step
list(range(1, 10, 2))  # [1, 3, 5, 7, 9]
```

## Exercises for Practice

1. **Variable Assignment and Type Checking:**
   Write a Python program that assigns values to variables, prints their types, and performs basic arithmetic operations.
   
   ```python
   x = 10
   y = 3.14
   print(type(x), type(y))
   print(x + y)
   ```

2. **String Manipulation:**
   Write a program to:
   - Convert a string to uppercase.
   - Replace a word in the string.
   - Slice and print a substring.
   
   ```python
   text = "hello world"
   print(text.upper())
   print(text.replace("world", "Python"))
   print(text[0:5])  # 'hello'
   ```

3. **List Operations:**
   - Create a list of numbers, sort it in ascending order, and reverse it.
   - Add and remove items from the list.
   
   ```python
   numbers = [5, 3, 8, 1]
   numbers.sort()
   print(numbers)
   numbers.reverse()
   print(numbers)
   ```

4. **Dictionary Exercise:**
   Create a dictionary for a person, add/update keys, and access dictionary values.
   
   ```python
   person = {"name": "John", "age": 25}
   person["city"] = "New York"
   print(person["city"])
   ```

5. **Input and Output:**
   Write a Python program that takes input from the user, processes it, and prints the result.
   
   ```python
   name = input("Enter your name: ")
   print(f"Hello, {name}!")
   ```

## Tips for Python Basics Interviews

- **Understand Data Types**: Know how to differentiate between strings, integers, lists, and dictionaries and how to use them efficiently.
- **Practice String and List Manipulations**: Be comfortable with common string and list operations.
- **Variable Scope**: Understand how variable scopes work (local vs global).
- **Pythonic Code**: Learn to write clean and efficient code using Python idioms like list comprehensions and dictionary comprehensions.
- **Avoid Over-complicating**: When solving problems, first aim for clarity and simplicity.

