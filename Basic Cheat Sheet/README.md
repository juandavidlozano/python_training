
# Python Basics Cheat Sheet

## 1. Variables and Data Types

### Primitive Data Types
- **Integer (`int`)**: Whole numbers, e.g., `x = 10`
- **Float (`float`)**: Decimal numbers, e.g., `y = 3.14`
- **String (`str`)**: Text, e.g., `name = "John"`
- **Boolean (`bool`)**: True/False values, e.g., `is_valid = True`

### Lists (`list`)
A mutable, ordered collection of items.
```python
my_list = [1, 2, 3, 4]  # List of integers
print(my_list[0])  # Access the first element (output: 1)
```

### Tuples (`tuple`)
An immutable, ordered collection of items.
```python
my_tuple = (1, 2, 3)
print(my_tuple[0])  # Access the first element (output: 1)
```

### Dictionaries (`dict`)
An unordered collection of key-value pairs.
```python
my_dict = {"name": "Alice", "age": 25}
print(my_dict["name"])  # Access value by key (output: "Alice")
```

### Sets (`set`)
An unordered collection of unique items.
```python
my_set = {1, 2, 3, 3}  # Duplicates are automatically removed
print(my_set)  # Output: {1, 2, 3}
```

---

## 2. Type Conversion

### Converting Between Types
- `int()`: Converts a value to an integer.
- `float()`: Converts a value to a float.
- `str()`: Converts a value to a string.
- `bool()`: Converts a value to a boolean.

```python
x = "123"
y = int(x)  # Converts string "123" to integer 123
z = float(y)  # Converts integer 123 to float 123.0
s = str(z)  # Converts float 123.0 to string "123.0"
```

### Example:
```python
a = int("10")  # 10
b = float("3.14")  # 3.14
c = str(100)  # "100"
d = bool(1)  # True
```

---

## 3. String Operations

### String Indexing and Slicing
- Access individual characters using indexing.
- Use slicing to get a substring.
```python
s = "Python"
print(s[0])  # 'P' (first character)
print(s[-1])  # 'n' (last character)
print(s[1:4])  # 'yth' (substring from index 1 to 3)
```

### Common String Methods
- `len()`: Returns the length of the string.
- `replace()`: Replaces parts of a string.
- `upper()`: Converts the string to uppercase.
- `lower()`: Converts the string to lowercase.
- `find()`: Finds the first occurrence of a substring.
- `strip()`: Removes leading and trailing spaces.

```python
s = "  hello world  "
print(len(s))  # 15 (includes spaces)
print(s.strip())  # 'hello world' (removes spaces)
print(s.replace("hello", "hi"))  # '  hi world  '
print(s.upper())  # '  HELLO WORLD  '
```

---

## 4. Input and Output (I/O)

### User Input
- Use `input()` to get input from the user.
```python
name = input("Enter your name: ")
print(f"Hello, {name}!")  # Prints a formatted greeting
```

### Print Function
- Use `print()` to output text.
```python
print("Hello, World!")  # Prints: Hello, World!
```

---

## 5. Working with Lists

### Creating and Accessing Lists
```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])  # Access the first element (output: 'apple')
print(fruits[-1])  # Access the last element (output: 'cherry')
```

### Common List Methods
- `append()`: Adds an element to the end of the list.
- `remove()`: Removes the first occurrence of the element.
- `sort()`: Sorts the list in ascending order.
- `reverse()`: Reverses the list in place.
- `len()`: Returns the number of elements in the list.

```python
fruits.append("orange")  # Adds 'orange' to the list
fruits.remove("banana")  # Removes 'banana' from the list
fruits.sort()  # Sorts the list alphabetically
fruits.reverse()  # Reverses the list order
print(len(fruits))  # Prints the number of elements in the list
```

---

## 6. Tuples

### Creating Tuples
```python
my_tuple = (1, 2, 3)
print(my_tuple[0])  # Accessing the first element (output: 1)
```

### Tuple Unpacking
```python
a, b, c = my_tuple
print(a)  # 1
print(b)  # 2
print(c)  # 3
```

---

## 7. Dictionaries

### Creating and Accessing Dictionaries
```python
person = {"name": "Alice", "age": 25}
print(person["name"])  # Access value by key (output: "Alice")
```

### Adding and Modifying Dictionary Entries
```python
person["city"] = "New York"  # Adding a new key-value pair
person["age"] = 30  # Modifying the value for an existing key
```

### Dictionary Methods
- `keys()`: Returns all the keys in the dictionary.
- `values()`: Returns all the values in the dictionary.
- `items()`: Returns all key-value pairs as tuples.

```python
print(person.keys())  # dict_keys(['name', 'age', 'city'])
print(person.values())  # dict_values(['Alice', 30, 'New York'])
print(person.items())  # dict_items([('name', 'Alice'), ('age', 30), ('city', 'New York')])
```

---

## 8. Sets

### Creating and Accessing Sets
```python
my_set = {1, 2, 3, 3}  # Duplicate values are automatically removed
print(my_set)  # Output: {1, 2, 3}
```

### Common Set Methods
- `add()`: Adds an element to the set.
- `remove()`: Removes an element from the set.
- `union()`: Returns the union of two sets (all unique elements).
- `intersection()`: Returns the intersection of two sets (common elements).

```python
my_set.add(4)  # Adds 4 to the set
my_set.remove(1)  # Removes 1 from the set
another_set = {3, 4, 5}
print(my_set.union(another_set))  # {2, 3, 4, 5}
print(my_set.intersection(another_set))  # {3, 4}
```

---

## Conclusion

This cheat sheet covers all the basics needed to solve common Python exercises involving variables, data types, type conversion, string operations, input/output, lists, tuples, dictionaries, and sets. Make sure to practice these concepts with the exercises provided to solidify your understanding!

