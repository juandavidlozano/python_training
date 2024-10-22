
# Python Control Flow Cheat Sheet

## 1. Conditionals

Conditionals allow you to execute certain blocks of code based on specific conditions.

### `if` Statements
```python
x = 10
if x > 5:
    print("x is greater than 5")
```

### `if-else` Statements
```python
x = 10
if x > 5:
    print("x is greater than 5")
else:
    print("x is not greater than 5")
```

### `if-elif-else` Statements
```python
x = 10
if x > 10:
    print("x is greater than 10")
elif x == 10:
    print("x is equal to 10")
else:
    print("x is less than 10")
```

### Nested `if` Statements
```python
x = 10
if x > 5:
    if x < 15:
        print("x is between 5 and 15")
```

---

## 2. Loops

Loops allow you to repeat a block of code multiple times.

### `for` Loop
```python
# Looping over a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Looping over a range of numbers
for i in range(5):
    print(i)  # Prints numbers from 0 to 4
```

### `while` Loop
```python
x = 0
while x < 5:
    print(x)
    x += 1  # Increment x by 1
```

### Nested Loops
```python
for i in range(3):
    for j in range(2):
        print(f"i = {i}, j = {j}")
```

---

## 3. Loop Control

You can control the flow of loops using `break`, `continue`, and `pass`.

### `break` Statement
Exits the loop when a certain condition is met.
```python
for i in range(5):
    if i == 3:
        break
    print(i)  # Output: 0, 1, 2
```

### `continue` Statement
Skips the rest of the loop iteration and moves to the next iteration.
```python
for i in range(5):
    if i == 3:
        continue
    print(i)  # Output: 0, 1, 2, 4
```

### `pass` Statement
Does nothing. Useful as a placeholder.
```python
for i in range(5):
    if i == 3:
        pass  # Placeholder for future code
    print(i)  # Output: 0, 1, 2, 3, 4
```

---

## 4. List Comprehensions

List comprehensions provide a concise way to create lists.

### Basic List Comprehension
```python
squares = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]
```

### List Comprehension with Conditional
```python
even_numbers = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]
```

---

## 5. Generator Expressions

Generator expressions work like list comprehensions, but they return a generator, which is more memory efficient.

### Basic Generator Expression
```python
gen = (x**2 for x in range(5))
print(next(gen))  # Output: 0
print(next(gen))  # Output: 1
```

### Generator Expression with Conditional
```python
even_gen = (x for x in range(10) if x % 2 == 0)
for num in even_gen:
    print(num)  # Output: 0, 2, 4, 6, 8
```

---
