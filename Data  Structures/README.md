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




# Cheat Sheet: List Looping with `enumerate` and Combining Lists

## List Looping with `enumerate`

`enumerate` is used when you need both the **index** and the **value** of elements in a list while looping.

### Basic Syntax
```python
for index, value in enumerate(your_list):
    # Use index and value as needed
```

### Example Usage
```python
my_list = ['a', 'b', 'c']

for index, value in enumerate(my_list):
    print("Index:", index, "Value:", value)
```
**Output:**
```
Index: 0 Value: a
Index: 1 Value: b
Index: 2 Value: c
```

### Start `enumerate` from a Custom Index
```python
for index, value in enumerate(my_list, start=1):
    print("Index:", index, "Value:", value)
```
**Output:**
```
Index: 1 Value: a
Index: 2 Value: b
Index: 3 Value: c
```

### Using `enumerate` with Conditional Logic
```python
for index, value in enumerate(my_list):
    if index % 2 == 0:
        print("Even Index:", index, "Value:", value)
```

---

## Combining or Appending Lists

### 1. Using `+` Operator to Concatenate Lists
The `+` operator creates a new list by joining two or more lists.
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined_list = list1 + list2
print(combined_list)  # Output: [1, 2, 3, 4, 5, 6]
```

### 2. Using `extend()` to Add Elements of One List to Another
The `extend()` method adds elements from another list to the end of the current list, modifying it in place.
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list1.extend(list2)
print(list1)  # Output: [1, 2, 3, 4, 5, 6]
```

### 3. Using `append()` to Add a List as a Single Element
The `append()` method can be used to add one list as a single element at the end of another list.
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list1.append(list2)
print(list1)  # Output: [1, 2, 3, [4, 5, 6]]
```

### 4. Using `*` (Unpacking) for Combining Lists
You can use the `*` operator to unpack lists and combine them.
```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined_list = [*list1, *list2]
print(combined_list)  # Output: [1, 2, 3, 4, 5, 6]
```

### 5. Using `sum()` to Combine a List of Lists
If you have a list of lists, you can use `sum()` to concatenate them into a single list.
```python
list_of_lists = [[1, 2], [3, 4], [5, 6]]
combined_list = sum(list_of_lists, [])
print(combined_list)  # Output: [1, 2, 3, 4, 5, 6]
```
**Note**: The `sum()` method with lists can be slower for large data.

---

## Summary Table

| Task                               | Syntax / Method                       | Example Output                           |
|------------------------------------|---------------------------------------|------------------------------------------|
| Basic `enumerate` loop             | `for index, value in enumerate(lst)`  | `Index: 0, Value: a`                     |
| Start `enumerate` at custom index  | `enumerate(lst, start=1)`             | `Index: 1, Value: a`                     |
| Concatenate lists with `+`         | `combined = list1 + list2`            | `[1, 2, 3, 4, 5, 6]`                    |
| Add all items with `extend()`      | `list1.extend(list2)`                 | `[1, 2, 3, 4, 5, 6]`                    |
| Add list as single element         | `list1.append(list2)`                 | `[1, 2, 3, [4, 5, 6]]`                  |
| Unpack and combine lists           | `combined = [*list1, *list2]`         | `[1, 2, 3, 4, 5, 6]`                    |
| Concatenate list of lists          | `combined = sum(list_of_lists, [])`   | `[1, 2, 3, 4, 5, 6]`                    |

This cheat sheet covers using `enumerate` for indexed looping and different ways to combine or append lists in Python!


---

## Looping Through a List Backwards

To loop through a list in reverse order, you can use several methods:

### 1. Using `reversed()`
The `reversed()` function allows you to loop through a list backwards without changing the list itself.

```python
my_list = [1, 2, 3, 4, 5]

for item in reversed(my_list):
    print(item)
```
**Output:**
```
5
4
3
2
1
```

### 2. Using Negative Stepping with Slicing (`[::-1]`)
You can create a reversed view of the list using slicing with a step of `-1`.

```python
my_list = [1, 2, 3, 4, 5]

for item in my_list[::-1]:
    print(item)
```
**Output:**
```
5
4
3
2
1
```

### 3. Using a `for` Loop with a Range in Reverse
You can loop through the indices in reverse using `range()`.

```python
my_list = [1, 2, 3, 4, 5]

for i in range(len(my_list) - 1, -1, -1):
    print(my_list[i])
```
**Output:**
```
5
4
3
2
1
```

---

## Summary Table (Updated)

| Task                               | Syntax / Method                       | Example Output                           |
|------------------------------------|---------------------------------------|------------------------------------------|
| Loop backwards with `reversed()`   | `for item in reversed(lst)`           | `5, 4, 3, 2, 1`                         |
| Loop backwards with slicing        | `for item in lst[::-1]`               | `5, 4, 3, 2, 1`                         |
| Loop backwards with `range()`      | `for i in range(len(lst) - 1, -1, -1)` | `5, 4, 3, 2, 1`                         |




# Python Dictionary Cheat Sheet

## 1. Basic Dictionary Operations

### Creating a Dictionary
```python
my_dict = {1: "apple", 2: "banana", 3: "cherry"}
```

### Adding or Updating a Key-Value Pair
```python
my_dict[4] = "date"  # Adds a new key 4 with value "date"
my_dict[2] = "blueberry"  # Updates the value of key 2 to "blueberry"
```

### Accessing a Value by Key
```python
value = my_dict[1]  # Returns "apple"
```

### Removing a Key-Value Pair
```python
del my_dict[3]  # Removes the key 3 and its associated value
```

---

## 2. Checking for Existence of Keys

### Check if a Key is in the Dictionary
- `key in dict` checks if a key exists in the dictionary.
```python
if 1 in my_dict:
    print("Key 1 is in the dictionary")
```

### Check if a Key is NOT in the Dictionary
- `key not in dict` checks if a key does **not** exist in the dictionary.
```python
if 4 not in my_dict:
    print("Key 4 is not in the dictionary")
```

> **Note**: `in` and `not in` only check keys, not values.

---

## 3. Checking for Values in a Dictionary

### Check if a Value is in the Dictionary
- Use `value in dict.values()` to check if a value exists.
```python
if "banana" in my_dict.values():
    print("Value 'banana' is in the dictionary")
```

### Check if a Value is NOT in the Dictionary
- Use `value not in dict.values()` to check if a value does **not** exist.
```python
if "fig" not in my_dict.values():
    print("Value 'fig' is not in the dictionary")
```

---

## 4. Counting Appearances of Items in a List

### Using a Dictionary to Count Items in a List
```python
nums = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
count_dict = {}

for num in nums:
    if num not in count_dict:
        count_dict[num] = 1
    else:
        count_dict[num] += 1

print(count_dict)  # Output: {0: 2, 1: 3, 2: 2, 3: 2, 4: 1}
```

---

## 5. Dictionary Methods

### `dict.keys()`
- Returns a view of all keys in the dictionary.
```python
keys = my_dict.keys()
print(keys)  # Output: dict_keys([1, 2, 4])
```

### `dict.values()`
- Returns a view of all values in the dictionary.
```python
values = my_dict.values()
print(values)  # Output: dict_values(['apple', 'blueberry', 'date'])
```

### `dict.items()`
- Returns a view of all key-value pairs as tuples.
```python
items = my_dict.items()
print(items)  # Output: dict_items([(1, 'apple'), (2, 'blueberry'), (4, 'date')])
```

---

## 6. Dictionary Comprehension

### Creating a Dictionary from a List
```python
squares = {x: x*x for x in range(5)}
print(squares)  # Output: {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

---

## 7. Using `collections.Counter` for Counting

If you’re only counting items in a list, you can use `Counter` from the `collections` module for a more concise solution.

```python
from collections import Counter

nums = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
count_dict = Counter(nums)
print(count_dict)  # Output: Counter({1: 3, 0: 2, 2: 2, 3: 2, 4: 1})
```

---

## 8. Dictionary Clear and Copy Methods

### `dict.clear()`
- Removes all items from the dictionary.
```python
my_dict.clear()
print(my_dict)  # Output: {}
```

### `dict.copy()`
- Returns a shallow copy of the dictionary.
```python
new_dict = my_dict.copy()
```

---

## 9. Dictionary Default Value with `get`

- Use `dict.get(key, default)` to safely retrieve a value. If the key is not found, it returns the `default` value.

```python
value = my_dict.get(5, "not found")  # Returns "not found" if key 5 doesn't exist
```

---

## 10. Removing and Retrieving with `pop`

- Use `dict.pop(key, default)` to remove a key and return its value. If the key is not found, it returns `default`.

```python
removed_value = my_dict.pop(2, "not found")
print(removed_value)  # If key 2 exists, returns its value; otherwise, "not found"
```

---

This cheat sheet provides a quick reference to core dictionary concepts and operations, covering everything from basic usage to counting techniques and checking for keys and values.

