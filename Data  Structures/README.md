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
print(my_list[0])  # Access the first element (output: 1)
print(my_list[-1])  # Access the last element (output: 5)
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
my_list.insert(1, 1.5)  # [1, 1.5, 2, 3, 4, 5, 6, 7, 8]
my_list.remove(1.5)  # [1, 2, 3, 4, 5, 6, 7, 8]
my_list.pop()  # Removes the last element, output: 8
my_list.sort()  # [1, 2, 3, 4, 5, 6, 7]
my_list.reverse()  # [7, 6, 5, 4, 3, 2, 1]
```

### List Slicing
```python
sub_list = my_list[1:4]  # Get a slice of the list, output: [6, 5, 4]
reversed_list = my_list[::-1]  # Reverse the list using slicing, output: [1, 2, 3, 4, 5, 6, 7]
```

---

## 2. Dictionaries

Dictionaries are collections of key-value pairs.

### Creating Dictionaries
```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
empty_dict = {}  # Empty dictionary
```

### Accessing and Modifying Dictionary Elements
```python
print(my_dict["name"])  # Access value by key, output: 'Alice'
my_dict["age"] = 30  # Modify value
my_dict["country"] = "USA"  # Add new key-value pair
```

### Common Dictionary Methods
- `get()`: Returns the value for a specified key (or a default value if the key is not found).
- `keys()`: Returns all keys in the dictionary.
- `values()`: Returns all values in the dictionary.
- `items()`: Returns all key-value pairs as tuples.
- `pop()`: Removes the key-value pair for the specified key.
- `update()`: Updates the dictionary with key-value pairs from another dictionary or iterable.

```python
print(my_dict.get("name", "Not Found"))  # 'Alice'
print(my_dict.keys())  # dict_keys(['name', 'age', 'city', 'country'])
print(my_dict.values())  # dict_values(['Alice', 30, 'New York', 'USA'])
print(my_dict.items())  # dict_items([('name', 'Alice'), ('age', 30), ('city', 'New York'), ('country', 'USA')])
my_dict.pop("city")  # Removes 'city' key, output: 'New York'
my_dict.update({"profession": "Engineer"})  # Adds a new key-value pair
```

---

## 3. Sets

Sets are unordered collections of unique elements.

### Creating Sets
```python
my_set = {1, 2, 3, 4, 5}
empty_set = set()  # Create an empty set
```

### Common Set Operations
- `add()`: Adds an element to the set.
- `remove()`: Removes an element from the set.
- `union()`: Returns a set that is the union of two sets.
- `intersection()`: Returns a set that is the intersection of two sets.
- `difference()`: Returns the difference between two sets.

```python
my_set.add(6)  # Adds 6 to the set
my_set.remove(1)  # Removes 1 from the set
another_set = {4, 5, 6, 7}
union_set = my_set.union(another_set)  # {2, 3, 4, 5, 6, 7}
intersection_set = my_set.intersection(another_set)  # {4, 5, 6}
difference_set = my_set.difference(another_set)  # {2, 3}
```

---

## 4. Tuples

Tuples are ordered, immutable collections of items.

### Creating Tuples
```python
my_tuple = (1, 2, 3)
single_element_tuple = (1,)  # Comma is needed for single-element tuples
```

### Tuple Packing and Unpacking
```python
a, b, c = my_tuple  # Tuple unpacking
print(a, b, c)  # 1, 2, 3
```

### Immutability
Tuples cannot be changed after creation. You cannot modify, append, or remove items from a tuple.

```python
# This will raise an error:
# my_tuple[0] = 5  # TypeError: 'tuple' object does not support item assignment
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
