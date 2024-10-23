# Python Functions Cheat Sheet

## 1. Defining Functions
In Python, functions are defined using the `def` keyword, followed by the function name and parentheses `()`.

```python
def function_name(parameters):
    # Function body
    return some_value  # Optional
```

### Example: Simple Function
```python
def greet():
    print("Hello, World!")

greet()  # Output: Hello, World!
```

---

## 2. Function Arguments and Parameters

### Positional Arguments
Arguments are passed in the same order as defined in the function signature.
```python
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")  # Output: Hello, Alice!
```

### Default Parameters
You can define default values for parameters. If no argument is passed, the default is used.
```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()  # Output: Hello, Guest!
greet("Alice")  # Output: Hello, Alice!
```

### Keyword Arguments
You can pass arguments by explicitly specifying the parameter name.
```python
def greet(first_name, last_name):
    print(f"Hello, {first_name} {last_name}!")

greet(first_name="Alice", last_name="Smith")  # Output: Hello, Alice Smith!
```

### Variable-Length Arguments (`*args`)
`*args` allows you to pass a variable number of arguments to a function. These arguments are passed as a tuple.
```python
def sum_numbers(*args):
    total = sum(args)
    print(total)

sum_numbers(1, 2, 3)  # Output: 6
```

### Keyword Variable-Length Arguments (`**kwargs`)
`**kwargs` allows you to pass a variable number of keyword arguments, which are passed as a dictionary.
```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=30, city="New York")
# Output:
# name: Alice
# age: 30
# city: New York
```

---

## 3. Returning Values
Functions can return values using the `return` keyword. If no `return` statement is specified, the function returns `None`.

```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # Output: 8
```

You can also return multiple values by separating them with commas. They are returned as a tuple.
```python
def operations(a, b):
    return a + b, a - b

sum_val, diff_val = operations(5, 3)
print(sum_val, diff_val)  # Output: 8 2
```

---

## 4. Scope of Variables

### Local Scope
Variables defined within a function are **local** to that function.
```python
def foo():
    x = 10  # Local variable
    print(x)

foo()  # Output: 10
# print(x)  # Raises NameError because x is not defined outside the function.
```

### Global Scope
Variables defined outside of functions are **global** and can be accessed inside functions, but you cannot modify them inside functions without using the `global` keyword.
```python
x = 10  # Global variable

def foo():
    print(x)  # Accessing global variable

foo()  # Output: 10
```

To modify a global variable:
```python
x = 10

def foo():
    global x
    x = 20  # Modifying global variable

foo()
print(x)  # Output: 20
```

---

## 5. Lambda Functions (Anonymous Functions)
Lambda functions are small, unnamed functions defined using the `lambda` keyword. They are used for simple operations.

### Syntax
```python
lambda arguments: expression
```

### Example:
```python
double = lambda x: x * 2
print(double(5))  # Output: 10
```

### Using Lambda Functions with `map()`, `filter()`, and `sorted()`
```python
numbers = [1, 2, 3, 4, 5]

# Using lambda with map()
squared_numbers = list(map(lambda x: x ** 2, numbers))
print(squared_numbers)  # Output: [1, 4, 9, 16, 25]

# Using lambda with filter()
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # Output: [2, 4]

# Using lambda with sorted()
names = ['Alice', 'Bob', 'Charlie']
sorted_names = sorted(names, key=lambda name: len(name))
print(sorted_names)  # Output: ['Bob', 'Alice', 'Charlie']
```

---

## 6. Recursion
Recursion occurs when a function calls itself. It’s commonly used in problems like tree traversal, factorial calculation, etc.

### Base Case and Recursive Case
A recursive function must have a **base case** to stop recursion, and a **recursive case** to continue calling the function.

### Example: Factorial Calculation
```python
def factorial(n):
    # Base case
    if n == 1:
        return 1
    # Recursive case
    return n * factorial(n - 1)

print(factorial(5))  # Output: 120
```

### Example: Fibonacci Sequence
```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(6))  # Output: 8
```

### Stack Limitations
Recursion can lead to **stack overflow** if the recursion is too deep (exceeds the Python recursion limit). You can check and set the recursion limit using the `sys` module.

```python
import sys
print(sys.getrecursionlimit())  # Output: 1000 (default limit)

# To change recursion limit
sys.setrecursionlimit(1500)
```

---

## 7. Nested Functions
You can define functions inside other functions. The inner function can access the variables of the outer function.

```python
def outer_function():
    x = "Hello"

    def inner_function():
        print(x)

    inner_function()

outer_function()  # Output: Hello
```

---

## 8. Functions as First-Class Citizens
In Python, functions are first-class objects, meaning you can pass functions as arguments, return them from other functions, and assign them to variables.

### Passing Functions as Arguments
```python
def apply_function(func, value):
    return func(value)

def double(x):
    return x * 2

print(apply_function(double, 5))  # Output: 10
```

### Returning Functions
```python
def outer_function():
    def inner_function():
        return "Hello from inner function"
    return inner_function

func = outer_function()
print(func())  # Output: Hello from inner function
```

---

## 9. Higher-Order Functions
A **higher-order function** is a function that takes one or more functions as arguments or returns a function as a result.

### Example: `map()`, `filter()`, and `reduce()`
```python
from functools import reduce

# map() example
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # Output: [1, 4, 9, 16]

# filter() example
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # Output: [2, 4]

# reduce() example
sum_numbers = reduce(lambda x, y: x + y, numbers)
print(sum_numbers)  # Output: 10
```

---

## 10. Function Decorators
A **decorator** is a function that takes another function and extends its behavior without explicitly modifying it. It’s often used for logging, authentication, or timing functions.

### Defining a Decorator
```python
def decorator_function(func):
    def wrapper():
        print("Before the function call")
        func()
        print("After the function call")
    return wrapper

@decorator_function
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before the function call
# Hello!
# After the function call
```

---

## 11. Generators and `yield`
Generators are a way to **iterate lazily**. Instead of returning a value and ending, a generator **yields** values one at a time, pausing execution in between.

### Example:
```python
def my_generator():
    yield 1
    yield 2
    yield 3

gen = my_generator()
print(next(gen))  # Output: 1
print(next(gen))  # Output: 2
```

### Example: Fibonacci Sequence with `yield`
```python
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

fib = fibonacci()
print(next(fib))  # Output: 0
print(next(fib))  # Output: 1
print(next(fib))  # Output: 1
print(next(fib))  # Output: 2
```

---

## 12. Memoization and `lru_cache`
**Memoization** is an optimization technique used to speed up recursive functions by caching previously computed results.

### Example: Fibonacci with Memoization
```python
from functools import lru_cache

@lru_cache(maxsize=None)  # Cache results of previous calls
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(10))  # Output: 55
```

---

## 13. Function Annotations (Type Hints)
Type hints (`-> int`, `arg: str`) are important to indicate what types your function takes and returns. These are useful for improving readability and helping with type checking.

### Example with Type Hints
```python
def add_numbers(a: int, b: int) -> int:
    return a + b

def greet(name: str) -> str:
    return f"Hello, {name}!"
```

---

## Exercises for Practice

1. **Pass by Reference vs Value**: Write a function that modifies a list and an integer, and observe the behavior.
2. **Higher-Order Function**: Write a function that takes another function and applies it twice to an input.
3. **Closure**: Write a closure function that retains state and counts how many times it's been called.
4. **Memoization**: Implement a recursive Fibonacci function and optimize it using memoization with `lru_cache`.
5. **Generator**: Write a generator function that yields prime numbers up to a given number.


