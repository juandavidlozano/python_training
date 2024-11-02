
# Module 2: Spark Core Concepts and RDDs (Simplified)

Welcome! This document explains the basics of Spark Core Concepts and RDDs (Resilient Distributed Datasets) in an easy-to-understand way with lots of examples.

---

## 2.1 Resilient Distributed Datasets (RDDs)

### What are RDDs?

Think of an RDD as a collection of data items that are **distributed** across many computers, but can be used like one single dataset. RDDs are like magical lists that let Spark work with massive amounts of data without running out of memory.

### Key Ideas

1. **Transformations**: These are instructions to modify or create new RDDs from existing ones (like a recipe for a dish but not cooking it yet).
2. **Actions**: These actually execute the transformations and produce results (like actually cooking the dish from the recipe).
3. **Lazy Evaluation**: Spark waits until it knows exactly what you want before it does any work, creating an efficient plan.

### Example

Imagine you have a list of numbers, and you want to get the squares of each number:

```python
# Create an RDD from a list of numbers
numbers = spark.parallelize([1, 2, 3, 4])

# Transformation (instructions only, no work done yet)
squares = numbers.map(lambda x: x * x)

# Action (now Spark actually computes the squares)
print(squares.collect())  # Output: [1, 4, 9, 16]
```

In this example, `map` is a transformation, and `collect` is an action that makes Spark compute the result.

---

## 2.2 Data Partitioning and Shuffling

### Why Data Partitioning Matters

Spark splits data across computers (partitions) so it can work faster. However, sometimes it needs to move data around (shuffle) to complete certain tasks.

### Example

Imagine each partition contains students in a different city, and we want to find the average age of students in each city. If the data is already grouped by city, we can work within each partition easily. But if not, Spark has to "shuffle" data across computers.

```python
students = spark.parallelize([("NY", 15), ("CA", 14), ("NY", 18), ("CA", 16)])

# Transformation: Group by state
grouped_by_state = students.groupByKey()

# Action: Compute average age for each state
average_age = grouped_by_state.mapValues(lambda ages: sum(ages) / len(ages))
print(average_age.collect())  # Output: [('NY', 16.5), ('CA', 15.0)]
```

Shuffling can be slow, so reducing it often makes programs faster.

---

## 2.3 RDD Operations

### Basic Transformations

1. **map** - Apply a function to each item
   ```python
   numbers = spark.parallelize([1, 2, 3])
   doubled = numbers.map(lambda x: x * 2)
   print(doubled.collect())  # Output: [2, 4, 6]
   ```

2. **filter** - Keep only items that match a condition
   ```python
   numbers = spark.parallelize([1, 2, 3, 4])
   evens = numbers.filter(lambda x: x % 2 == 0)
   print(evens.collect())  # Output: [2, 4]
   ```

### Aggregation Operations

1. **reduce** - Combine items
   ```python
   numbers = spark.parallelize([1, 2, 3, 4])
   sum_total = numbers.reduce(lambda x, y: x + y)
   print(sum_total)  # Output: 10
   ```

2. **fold** - Similar to reduce but with an initial value
   ```python
   numbers = spark.parallelize([1, 2, 3])
   sum_with_initial = numbers.fold(10, lambda x, y: x + y)
   print(sum_with_initial)  # Output: 16
   ```

### Key-Value Operations

1. **groupByKey** - Group values by key
   ```python
   pairs = spark.parallelize([("a", 1), ("b", 2), ("a", 3)])
   grouped = pairs.groupByKey()
   print([(k, list(v)) for k, v in grouped.collect()])  # Output: [('a', [1, 3]), ('b', [2])]
   ```

2. **reduceByKey** - Reduce values by key
   ```python
   pairs = spark.parallelize([("a", 1), ("a", 2), ("b", 3)])
   sums = pairs.reduceByKey(lambda x, y: x + y)
   print(sums.collect())  # Output: [('a', 3), ('b', 3)]
   ```

---

This guide covers the essentials of RDDs in a simple and approachable way. Try these examples yourself to get a feel for how Spark works!
```
