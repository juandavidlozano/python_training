# Python Data Structures Cheat Sheet

## 1. Lists
Lists are ordered, mutable collections of items.

### Creating Lists
```python
my_list = [1, 2, 3, 4, 5]  # List of integers
empty_list = []  # Empty list
```

### Accessing List Elements
```python
print(my_list[0])  # Output: 1
print(my_list[-1])  # Output: 5 (last element)
```

### Common List Methods
- `append()`: Adds an element to the end of the list.
- `extend()`: Adds multiple elements to the end of the list.
- `insert()`: Inserts an element at a specific position.
- `remove()`: Removes the first occurrence of a value.
- `pop()`: Removes and returns the last element (or an element at a specific index).
- `sort()`: Sorts the list in ascending order.
- `reverse()`: Reverses the list.

```python
my_list.append(6)  # [1, 2, 3, 4, 5, 6]
my_list.extend([7, 8])  # [1, 2, 3, 4, 5, 6, 7, 8]
my_list.insert(2, 2.5)  # [1, 2, 2.5, 3, 4, 5, 6, 7, 8]
my_list.remove(2.5)  # [1, 2, 3, 4, 5, 6, 7, 8]
my_list.pop()  # Removes 8, [1, 2, 3, 4, 5, 6, 7]
my_list.sort()  # [1, 2, 3, 4, 5, 6, 7]
my_list.reverse()  # [7, 6, 5, 4, 3, 2, 1]
```

### List Comprehensions
List comprehensions provide a concise way to create lists.
```python
# Example: Create a list of squares
squares = [x ** 2 for x in range(1, 6)]  # [1, 4, 9, 16, 25]
```

---

## 2. Dictionaries
Dictionaries are unordered collections of key-value pairs.

### Creating Dictionaries
```python
my_dict = {'name': 'Alice', 'age': 25, 'city': 'New York'}
empty_dict = {}  # Empty dictionary
```

### Accessing and Modifying Dictionary Elements
```python
print(my_dict['name'])  # Output: 'Alice'
my_dict['age'] = 30  # Change value
my_dict['country'] = 'USA'  # Add new key-value pair
```

### Looping Over a Dictionary
```python
# Looping through keys and values
for key, value in my_dict.items():
    print(f"{key}: {value}")

# Output:
# name: Alice
# age: 30
# city: New York
# country: USA
```

### Common Dictionary Methods
- `get()`: Returns the value for a specified key.
- `keys()`: Returns all keys in the dictionary.
- `values()`: Returns all values in the dictionary.
- `items()`: Returns all key-value pairs as tuples.
- `update()`: Updates the dictionary with key-value pairs from another dictionary.

```python
print(my_dict.get('name', 'Not Found'))  # Output: 'Alice'
print(my_dict.keys())  # Output: dict_keys(['name', 'age', 'city', 'country'])
print(my_dict.values())  # Output: dict_values(['Alice', 30, 'New York', 'USA'])
print(my_dict.items())  # Output: dict_items([('name', 'Alice'), ('age', 30), ('city', 'New York'), ('country', 'USA')])

# Update multiple values
my_dict.update({'name': 'Bob', 'age': 40})
```

### Example: Counting Word Frequencies in a String
```python
text = "hello world hello everyone"
word_counts = {}

for word in text.split():
    word_counts[word] = word_counts.get(word, 0) + 1

print(word_counts)  # Output: {'hello': 2, 'world': 1, 'everyone': 1}
```

---

## 3. Sets
Sets are unordered collections of unique elements.

### Creating Sets
```python
my_set = {1, 2, 3, 4, 5}
empty_set = set()  # Empty set
```

### Common Set Operations
- `add()`: Adds an element to the set.
- `remove()`: Removes an element from the set.
- `union()`: Returns the union of two sets.
- `intersection()`: Returns the intersection of two sets.
- `difference()`: Returns the difference between two sets.

```python
my_set.add(6)  # {1, 2, 3, 4, 5, 6}
my_set.remove(3)  # {1, 2, 4, 5, 6}

set_a = {1, 2, 3}
set_b = {3, 4, 5}
union_set = set_a.union(set_b)  # {1, 2, 3, 4, 5}
intersection_set = set_a.intersection(set_b)  # {3}
difference_set = set_a.difference(set_b)  # {1, 2}
```

---

## 4. Tuples
Tuples are ordered, immutable collections of items.

### Creating Tuples
```python
my_tuple = (1, 2, 3)
single_element_tuple = (1,)  # Comma is needed for single-element tuples
```

### Accessing Tuple Elements
```python
print(my_tuple[0])  # Output: 1
print(my_tuple[-1])  # Output: 3
```

### Tuple Packing and Unpacking
```python
# Tuple packing
my_tuple = 1, 2, 3

# Tuple unpacking
a, b, c = my_tuple
print(a, b, c)  # Output: 1 2 3
```

---

## 5. Stacks, Queues, and Heaps

Python’s `collections` module provides an efficient way to implement stacks and queues.

### Stacks (LIFO - Last In, First Out)
You can use a list or `collections.deque` to implement a stack.

```python
stack = [1, 2, 3]
stack.append(4)  # Push element onto the stack
print(stack.pop())  # Pop element, output: 4
```

### Queues (FIFO - First In, First Out)
You can use `collections.deque` to implement a queue.

```python
from collections import deque

queue = deque([1, 2, 3])
queue.append(4)  # Add element to the queue
print(queue.popleft())  # Remove the first element, output: 1
```

### Heaps (Priority Queue)
Use Python's `heapq` module to implement a heap (min-heap by default).

```python
import heapq

heap = [5, 7, 9, 1, 3]
heapq.heapify(heap)  # Convert list into a heap
heapq.heappush(heap, 4)  # Push an element onto the heap
print(heapq.heappop(heap))  # Pop the smallest element, output: 1
```

---

## Looping Over Different Data Structures

### 1. Looping Over Lists
```python
my_list = [10, 20, 30, 40]

# Basic for loop
for item in my_list:
    print(item)
```

#### Loop with Indexes using `enumerate()`
```python
for index, item in enumerate(my_list):
    print(f"Index {index} has value {item}")
```

#### Using `len()` to Loop by Index
```python
for i in range(len(my_list)):
    print(my_list[i])
```

---

### 2. Looping Over Dictionaries
#### Looping Over Keys
```python
my_dict = {'a': 1, 'b': 2, 'c': 3}

for key in my_dict:
    print(key)
```

#### Looping Over Values
```python
for value in my_dict.values():
    print(value)
```

#### Looping Over Keys and Values
```python
for key, value in my_dict.items():
    print(f"{key}: {value}")
```

---

### 3. Looping Over Sets
Sets are unordered, so you can loop over them using a `for` loop, but there are no indexes.
```python
my_set = {1, 2, 3, 4}

for item in my_set:
    print(item)
```

---

### 4. Looping Over Tuples
Tuples are immutable, so you loop over them like lists but cannot change their contents.
```python
my_tuple = (1, 2, 3)

for item in my_tuple:
    print(item)
```

---

### 5. Using `in` for Membership Testing
#### Check if an Element Exists in a List
```python
my_list = [1, 2, 3, 4, 5]

if 3 in my_list:
    print("3 is in the list")
```

#### Check if a Key Exists in a Dictionary
```python
my_dict = {'a': 1, 'b': 2, 'c': 3}

if 'b' in my_dict:
    print("Key 'b' exists in the dictionary")
```

#### Check if an Element Exists in a Set
```python
my_set = {1, 2, 3, 4, 5}

if 2 in my_set:
    print("2 is in the set")
```

---

### 6. Using `zip()` to Loop Over Multiple Structures
`zip()` allows you to loop over multiple structures at once, pairing elements from each one.

```python
names = ["Alice", "Bob", "Charlie"]
scores = [85, 90, 78]

for name, score in zip(names, scores):
    print(f"{name}: {score}")
```

---

### 7. Looping with `range()`
`range()` generates a sequence of numbers and is often used to loop over a sequence by index.

```python
for i in range(5):  # Loops from 0 to 4
    print(i)
```

---

### General Tips for Looping
1. **Use `in`**: Use `in` to check membership (whether an element is in a list, set, or dictionary).
2. **Use `enumerate()`**: If you need both the index and value from a list, use `enumerate()` for a cleaner solution than using `len()`.
3. **Use `.items()` for Dictionaries**: If you need both the keys and values from a dictionary, iterate using `.items()`.
4. **Use List Comprehensions**: For simple loops that involve generating new lists, consider using **list comprehensions** for cleaner code.
    ```python
    squares = [x ** 2 for x in range(5)]  # [0, 1, 4, 9, 16]
    ```
5. **`zip()` for Parallel Iteration**: Use `zip()` when you need to loop through multiple iterables simultaneously.
