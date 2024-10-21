
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

## 3. Common Python Functions

### `len()`
Returns the length (number of items) of an object.
```python
s = "Python"
print(len(s))  # 6
```

### `max()` and `min()`
Returns the largest and smallest item, respectively.
```python
numbers = [1, 2, 3, 4]
print(max(numbers))  # 4
print(min(numbers))  # 1
```

### `sum()`
Returns the sum of all items in an iterable (like a list).
```python
numbers = [1, 2, 3, 4]
print(sum(numbers))  # 10
```

### `sorted()`
Returns a sorted version of the iterable.
```python
numbers = [4, 1, 3, 2]
print(sorted(numbers))  # [1, 2, 3, 4]
```

### `type()`
Returns the type of an object.
```python
x = 5
print(type(x))  # <class 'int'>
```

## 4. String Operations

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

## 5. List Operations

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

## 6. Tuples

### Creating Tuples:
```python
my_tuple = (1, 2, 3)
print(my_tuple[0])  # 1
```

### Immutability:
```python
# Tuples are immutable; you cannot change elements
```

### Swapping Variables using Tuple Unpacking:
```python
a = 5
b = 10

# Swapping variables
a, b = b, a

print(a)  # 10
print(b)  # 5
```

## 7. Dictionaries

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

## 8. Type Conversion Functions
```python
int("10")      # Converts string to integer
float("10.5")  # Converts string to float
str(100)       # Converts integer to string
list("abc")    # Converts string to list ['a', 'b', 'c']
```

## 9. Type Checking
```python
type(10)         # <class 'int'>
type(10.5)       # <class 'float'>
type([1, 2, 3])  # <class 'list'>
type({"key": 1}) # <class 'dict'>
```

## 10. Arithmetic Operators
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

## 11. Comparison and Logical Operators

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

## 12. Python Ranges
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

## Best Practices for Python Code

### 1. Variable Scope

**Scope** refers to the region in a program where a variable is accessible. Understanding scope is crucial to avoid unexpected behavior, especially in larger programs.

#### **Local Variables:**
Local variables are defined inside a function and can only be used within that function.

```python
def my_function():
    x = 10  # Local variable
    print(x)

my_function()
print(x)  # This will cause an error since x is not accessible outside the function.
```

#### **Global Variables:**
Global variables are defined outside of functions and are accessible throughout the entire program.

```python
x = 10  # Global variable

def my_function():
    print(x)  # Accessing global variable inside a function

my_function()
print(x)  # Global variable can be accessed outside the function too.
```

#### **Modifying Global Variables Inside Functions:**
To modify a global variable inside a function, you must explicitly declare it using the `global` keyword.

```python
x = 10

def modify_global():
    global x
    x = 20

modify_global()
print(x)  # 20, because the global variable was modified inside the function.
```

#### **Nonlocal Variables (In Nested Functions):**
If you want to modify a variable in a nested (enclosing) function, use the `nonlocal` keyword.

```python
def outer_function():
    x = 10

    def inner_function():
        nonlocal x  # Modifies the variable from the outer function
        x = 20

    inner_function()
    print(x)  # 20

outer_function()
```

---

### 2. Pythonic Code

Python encourages writing code that is **clear**, **concise**, and **efficient**. Below are some techniques that make code more Pythonic:

#### **List Comprehensions:**
Instead of using loops to build lists, you can use list comprehensions for a more readable and concise solution.

##### Example (Using a Loop):
```python
squares = []
for i in range(5):
    squares.append(i ** 2)
print(squares)  # [0, 1, 4, 9, 16]
```

##### Pythonic Way (Using List Comprehension):
```python
squares = [i ** 2 for i in range(5)]
print(squares)  # [0, 1, 4, 9, 16]
```

#### **Dictionary Comprehensions:**
Similar to list comprehensions, Python allows comprehensions for dictionaries too.

##### Example (Using a Loop):
```python
numbers = [1, 2, 3]
squares = {}
for n in numbers:
    squares[n] = n ** 2
print(squares)  # {1: 1, 2: 4, 3: 9}
```

##### Pythonic Way (Using Dictionary Comprehension):
```python
numbers = [1, 2, 3]
squares = {n: n ** 2 for n in numbers}
print(squares)  # {1: 1, 2: 4, 3: 9}
```

#### **Using Generators:**
Generators are memory-efficient and produce items one at a time, only as needed. They are written using `()` instead of `[]` for list comprehensions.

##### Example (Using a List):
```python
numbers = [i for i in range(1000000)]  # Creates a list of one million elements (takes a lot of memory)
```

##### Pythonic Way (Using a Generator):
```python
numbers = (i for i in range(1000000))  # Generator that produces one element at a time (more memory efficient)
```

#### **Ternary Operators:**
In Python, you can write conditional statements in a single line using a ternary operator.

##### Example (Standard Conditional):
```python
x = 10
if x > 5:
    result = "Greater"
else:
    result = "Smaller"
```

##### Pythonic Way (Using Ternary Operator):
```python
x = 10
result = "Greater" if x > 5 else "Smaller"
```

---

### 3. Avoiding Redundancies

Python has built-in functions like `any()`, `all()`, and `zip()` that help you avoid writing redundant loops.

#### **Using `any()` and `all()` for Conditions:**
Instead of checking conditions with multiple loops or if-statements, `any()` returns `True` if **any** of the elements are `True`, while `all()` returns `True` if **all** elements are `True`.

##### Example (Using a Loop):
```python
numbers = [1, 2, 3, 0]
for n in numbers:
    if n == 0:
        print(True)
        break
```

##### Pythonic Way (Using `any()`):
```python
numbers = [1, 2, 3, 0]
print(any(n == 0 for n in numbers))  # True
```

#### **Using `zip()` to Loop Over Two Lists Simultaneously:**
When you need to loop over two or more lists at the same time, `zip()` can help.

```python
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]

for name, age in zip(names, ages):
    print(f"{name} is {age} years old.")
```

---

These techniques help write concise and more efficient code. Becoming comfortable with these will make your Python code more "Pythonic" and improve readability.
