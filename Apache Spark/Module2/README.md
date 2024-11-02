# Module 2: Spark Core Concepts and RDDs

## 2.1 Resilient Distributed Datasets (RDDs)
Resilient Distributed Datasets (RDDs) are the fundamental data structure in Spark. They are fault-tolerant collections of elements that can be processed in parallel. 

### Understanding RDDs, Transformations, and Actions
- **Transformations**: Operations that define a new RDD based on the current one (e.g., `map`, `filter`). Transformations are **lazy**, meaning they are only computed when an action requires them.
- **Actions**: Operations that trigger computation on RDDs and return a result to the driver program or write to external storage (e.g., `count`, `collect`).

### Lazy Evaluation and DAG (Directed Acyclic Graph)
- Spark uses **lazy evaluation** to optimize the execution plan, constructing a **Directed Acyclic Graph (DAG)** that represents the series of transformations and actions.
- The DAG ensures that Spark only recomputes lost data and avoids unnecessary recalculations.

### Persistence and Caching RDDs
- RDDs can be **cached** in memory to speed up operations that are repeatedly used.
- Use `.persist()` to persist data in memory or `.cache()` to cache the data with default storage level (MEMORY_ONLY).

#### Code Example:
```python
from pyspark import SparkContext

# Initialize Spark Context
sc = SparkContext("local", "RDDExample")

# Create an RDD
data = [1, 2, 3, 4, 5]
rdd = sc.parallelize(data)

# Transformation (Lazy Evaluation)
rdd_transformed = rdd.map(lambda x: x * 2)

# Action
print("Transformed RDD:", rdd_transformed.collect())  # Triggers computation

# Caching RDD
rdd_transformed.cache()
```

---

## 2.2 Data Partitioning and Shuffling
Efficient data partitioning and reducing shuffle operations are crucial for optimizing Spark applications.

### Data Partitioning Strategies in Spark
- By default, Spark creates a number of partitions based on the size of the input data and the available resources.
- Use `repartition` to increase or decrease the number of partitions. For example, `rdd.repartition(4)`.

### Shuffling Operations and Optimization Techniques
- **Shuffling** occurs when Spark needs to redistribute data across partitions, like with `groupByKey`, `reduceByKey`.
- Minimize shuffling by using transformations that combine data within partitions, such as `reduceByKey` over `groupByKey`.

### Key-Value Pair RDD Operations
Key-value RDDs enable operations that leverage partitioning for performance gains.

#### Code Example:
```python
# Key-Value Pair RDD
kv_rdd = sc.parallelize([("key1", 1), ("key2", 2), ("key1", 3)])

# Reduce by key (shuffling minimized)
reduced_rdd = kv_rdd.reduceByKey(lambda x, y: x + y)
print("Reduced RDD:", reduced_rdd.collect())

# Repartition RDD
repartitioned_rdd = kv_rdd.repartition(4)
print("Repartitioned RDD partition count:", repartitioned_rdd.getNumPartitions())
```

---

## 2.3 RDD Operations
Spark RDDs support various operations, both transformations and actions.

### Basic RDD Transformations
- **map**: Apply a function to each element in the RDD.
- **filter**: Select elements that meet a specific condition.
- **flatMap**: Similar to `map`, but each element can produce zero or more output elements.

#### Code Example:
```python
# Basic RDD Transformations
mapped_rdd = rdd.map(lambda x: x * 2)
filtered_rdd = rdd.filter(lambda x: x > 2)
flatmapped_rdd = rdd.flatMap(lambda x: (x, x * 2))

print("Mapped RDD:", mapped_rdd.collect())
print("Filtered RDD:", filtered_rdd.collect())
print("FlatMapped RDD:", flatmapped_rdd.collect())
```

### Aggregation Operations
- **reduce**: Aggregate elements of the RDD using an associative function.
- **fold**: Similar to `reduce` but with a zero value for initialization.
- **aggregate**: More complex aggregation that allows combining results within and across partitions.

#### Code Example:
```python
# Aggregation Operations
sum_rdd = rdd.reduce(lambda x, y: x + y)
product_rdd = rdd.fold(1, lambda x, y: x * y)

print("Sum of RDD:", sum_rdd)
print("Product of RDD:", product_rdd)
```

### Key-Value Operations
- **groupByKey**: Group values with the same key (can be costly due to shuffling).
- **reduceByKey**: Aggregate values with the same key, more efficient than `groupByKey`.
- **join**: Perform an inner join on two key-value RDDs.

#### Code Example:
```python
# Key-Value Operations
grouped_rdd = kv_rdd.groupByKey().mapValues(list)
reduced_by_key_rdd = kv_rdd.reduceByKey(lambda x, y: x + y)

print("Grouped RDD:", grouped_rdd.collect())
print("Reduced by Key RDD:", reduced_by_key_rdd.collect())
```
