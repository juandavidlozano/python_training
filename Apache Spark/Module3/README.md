
# Module 3: Spark DataFrames and SQL (Simplified)

In this module, we'll cover how to use Spark DataFrames and SQL. Think of DataFrames as tables (like in Excel or a database) where each row represents a record and each column represents a feature. DataFrames in Spark are powerful for handling large datasets efficiently.

---

## 3.1 Introduction to DataFrames

### What is a DataFrame?

A DataFrame in Spark is similar to a table. Each row is a record, and each column is a field. DataFrames are easy to work with and allow us to perform operations similar to SQL queries.

### Example

Let’s say we have data on employees and their departments:

```python
from pyspark.sql import SparkSession

# Start Spark session
spark = SparkSession.builder.appName("DataFrameExample").getOrCreate()

# Sample data
data = [("John", "HR", 3000), ("Jane", "IT", 4000), ("Bill", "Finance", 5000)]
columns = ["Name", "Department", "Salary"]

# Create DataFrame
df = spark.createDataFrame(data, columns)
df.show()
```

This will output:

```
+----+----------+------+
|Name|Department|Salary|
+----+----------+------+
|John|        HR|  3000|
|Jane|        IT|  4000|
|Bill|   Finance|  5000|
+----+----------+------+
```

### Why Use DataFrames?

DataFrames provide a structured way of organizing data and enable powerful querying and aggregating operations, which are both fast and intuitive.

---

## 3.2 Basic Operations on DataFrames

### 1. Selecting Columns

```python
# Selecting the 'Name' column
df.select("Name").show()
```

### 2. Filtering Rows

Filter employees in the "IT" department:

```python
df.filter(df.Department == "IT").show()
```

### 3. Adding a New Column

Add a 10% bonus to each employee’s salary:

```python
df = df.withColumn("Bonus", df.Salary * 0.1)
df.show()
```

### 4. Grouping and Aggregating Data

Calculate the average salary per department:

```python
df.groupBy("Department").avg("Salary").show()
```

These operations are simple but powerful, allowing you to perform data transformations directly on the DataFrame.

---

## 3.3 Using SQL Queries

With Spark SQL, you can write SQL-like queries on DataFrames.

### Example

Register the DataFrame as a SQL temporary view:

```python
df.createOrReplaceTempView("employees")

# Query using SQL
result = spark.sql("SELECT Department, avg(Salary) as Avg_Salary FROM employees GROUP BY Department")
result.show()
```

This outputs the average salary for each department, just like you would in a database.

---

## Real-World Scenarios for DataFrames and SQL

### 1. Analyzing Customer Purchases

If you’re analyzing millions of customer purchase records, you could use DataFrames to quickly filter for high-value customers and calculate metrics like total spending.

```python
# Assume 'purchases_df' is a DataFrame with purchase data
high_value_customers = purchases_df.filter(purchases_df["Amount"] > 5000)
total_spending = high_value_customers.groupBy("CustomerID").sum("Amount")
total_spending.show()
```

**Speed Advantage**: PySpark can process massive datasets in parallel, providing insights in minutes.

### 2. Aggregating Sales Data for Reports

For sales analysis, you might want to group sales by region and product, calculating the total revenue.

```python
# Assume 'sales_df' is a DataFrame with sales data
sales_df.groupBy("Region", "Product").sum("Revenue").show()
```

**Speed Advantage**: PySpark handles complex groupings on large datasets much faster than traditional methods.

### 3. Real-Time Monitoring of Web Traffic

Monitoring website visits can help identify popular pages and visitor demographics. Using Spark SQL on DataFrames, you can query specific user actions and summarize data in real-time.

```python
# Assume 'web_logs_df' is a DataFrame of web log data
popular_pages = spark.sql("SELECT PageURL, count(*) as Visits FROM web_logs_df GROUP BY PageURL ORDER BY Visits DESC")
popular_pages.show()
```

**Speed Advantage**: PySpark’s SQL engine can query and summarize logs in near real-time, making it ideal for fast-paced environments.

---

## Why Spark DataFrames are Fast

1. **Optimized Execution**: PySpark uses a Catalyst optimizer to make SQL queries and transformations run as efficiently as possible.
2. **In-Memory Computation**: DataFrames are processed in memory, so operations are quicker than traditional disk-based methods.
3. **Parallel Processing**: PySpark automatically distributes work across a cluster, enabling massive parallelism.

With Spark DataFrames and SQL, even complex data processing tasks become simple and fast, empowering users to get insights from large datasets.

---

Using PySpark with DataFrames and SQL makes it easy to process, transform, and analyze large data in a user-friendly way. Try experimenting with these examples to gain a solid understanding!
