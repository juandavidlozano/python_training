
# PySpark Data Loading Cheat Sheet

## 1. Loading a CSV File into PySpark DataFrame

### Basic Load with Header
```python
from pyspark.sql import SparkSession

# Initialize Spark session
spark = SparkSession.builder.appName("DataLoadingExample").getOrCreate()

# Load CSV file with header
df = spark.read.format("csv").option("header", "true").load("path/to/yourfile.csv")
df.show(5)
```

### Load CSV with Schema Inference
```python
df = spark.read.format("csv").option("header", "true").option("inferSchema", "true").load("path/to/yourfile.csv")
df.printSchema()
```

### Load CSV with Custom Schema
```python
from pyspark.sql.types import StructType, StructField, IntegerType, StringType, DoubleType

# Define schema
schema = StructType([
    StructField("column1", IntegerType(), True),
    StructField("column2", StringType(), True),
    StructField("column3", DoubleType(), True)
])

# Load CSV with custom schema
df = spark.read.format("csv").option("header", "true").schema(schema).load("path/to/yourfile.csv")
df.printSchema()
```

---

## 2. Creating a PySpark DataFrame from a Dictionary

### Basic DataFrame Creation from List of Dictionaries
```python
# Sample data as a list of dictionaries
data = [
    {"name": "Alice", "age": 29, "city": "New York"},
    {"name": "Bob", "age": 34, "city": "Los Angeles"}
]

# Create DataFrame from data
df = spark.createDataFrame(data)
df.show()
```

### Specifying Schema for Dictionary-Based DataFrame
```python
# Define schema
schema = StructType([
    StructField("name", StringType(), True),
    StructField("age", IntegerType(), True),
    StructField("city", StringType(), True)
])

# Create DataFrame with schema
df = spark.createDataFrame(data, schema=schema)
df.show()
```

---

## 3. Infer Schema from Data

### Automatically Inferring Schema
- PySpark can infer the schema automatically from CSV files or JSON files if `inferSchema` is set to `true`.

```python
# Infer schema from CSV file
df = spark.read.format("csv").option("header", "true").option("inferSchema", "true").load("path/to/yourfile.csv")
df.printSchema()
```

---

## 4. Specifying Data Types Directly in Code

### Converting Columns After Loading
- You can change data types after loading the DataFrame by using the `cast()` function.

```python
from pyspark.sql import functions as F

# Example of casting columns
df = df.withColumn("age", F.col("age").cast(IntegerType()))
df.printSchema()
```

---

## 5. Saving Data to CSV

### Save DataFrame as CSV File
```python
# Save DataFrame to CSV with header
df.write.format("csv").option("header", "true").save("path/to/output_directory")
```

