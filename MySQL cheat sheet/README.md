# MySQL Cheat Sheet

## 1. Aggregate Functions:
These are used to perform calculations on multiple rows of a table.

- **`COUNT()`**: Counts the number of rows.
    ```sql
    SELECT COUNT(*) FROM Orders;
    ```

- **`SUM()`**: Returns the total sum of a numeric column.
    ```sql
    SELECT SUM(total_amount) FROM Orders;
    ```

- **`AVG()`**: Returns the average value of a numeric column.
    ```sql
    SELECT AVG(total_amount) FROM Orders;
    ```

- **`MAX()`**: Returns the maximum value in a column.
    ```sql
    SELECT MAX(total_amount) FROM Orders;
    ```

- **`MIN()`**: Returns the minimum value in a column.
    ```sql
    SELECT MIN(total_amount) FROM Orders;
    ```

## 2. String Manipulation:
Functions for manipulating and querying string values.

- **`CONCAT()`**: Concatenates two or more strings.
    ```sql
    SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM Customers;
    ```

- **`LENGTH()`**: Returns the length of a string.
    ```sql
    SELECT LENGTH(first_name) FROM Customers;
    ```

- **`LOWER()`**: Converts a string to lowercase.
    ```sql
    SELECT LOWER(first_name) FROM Customers;
    ```

- **`UPPER()`**: Converts a string to uppercase.
    ```sql
    SELECT UPPER(first_name) FROM Customers;
    ```

- **`SUBSTRING()`**: Extracts a substring from a string.
    ```sql
    SELECT SUBSTRING(first_name, 1, 3) FROM Customers; -- Extract first 3 characters
    ```

- **`REPLACE()`**: Replaces all occurrences of a substring with another substring.
    ```sql
    SELECT REPLACE(first_name, 'J', 'K') FROM Customers; -- Replace 'J' with 'K'
    ```

- **`TRIM()`**: Removes leading and trailing whitespace.
    ```sql
    SELECT TRIM(first_name) FROM Customers;
    ```

## 3. Date Manipulation:
Functions to handle dates and times in MySQL.

- **`CURDATE()`**: Returns the current date.
    ```sql
    SELECT CURDATE();
    ```

- **`NOW()`**: Returns the current date and time.
    ```sql
    SELECT NOW();
    ```

- **`DATE()`**: Extracts the date part of a datetime expression.
    ```sql
    SELECT DATE(NOW());
    ```

- **`DATEDIFF()`**: Returns the difference between two dates.
    ```sql
    SELECT DATEDIFF('2024-12-25', '2024-12-01') AS diff_days; -- Difference in days
    ```

- **`DATE_ADD()`**: Adds a time interval to a date.
    ```sql
    SELECT DATE_ADD('2024-12-01', INTERVAL 7 DAY);
    ```

- **`DATE_SUB()`**: Subtracts a time interval from a date.
    ```sql
    SELECT DATE_SUB('2024-12-01', INTERVAL 7 DAY);
    ```

- **`YEAR()`, `MONTH()`, `DAY()`**: Extracts the year, month, or day from a date.
    ```sql
    SELECT YEAR(order_date), MONTH(order_date), DAY(order_date) FROM Orders;
    ```

- **`TIMESTAMPDIFF()`**: Returns the difference between two dates or times.
    ```sql
    SELECT TIMESTAMPDIFF(HOUR, '2024-01-01 12:00:00', '2024-01-01 18:00:00') AS diff_hours;
    ```

## 4. Conditional Functions:
These functions allow you to perform conditional logic in SQL queries.

- **`IF()`**: Simple if-then-else statement.
    ```sql
    SELECT first_name, IF(city = 'New York', 'NY Resident', 'Other') AS residence FROM Customers;
    ```

- **`CASE`**: More complex if-then-else structure.
    ```sql
    SELECT first_name,
      CASE 
        WHEN city = 'New York' THEN 'East Coast'
        WHEN city = 'Chicago' THEN 'Midwest'
        ELSE 'Other' 
      END AS region
    FROM Customers;
    ```

- **`COALESCE()`**: Returns the first non-null value in a list.
    ```sql
    SELECT COALESCE(city, 'Unknown') FROM Customers;
    ```

## 5. Mathematical Functions:
Useful for numerical calculations in SQL.

- **`ROUND()`**: Rounds a number to a specified number of decimal places.
    ```sql
    SELECT ROUND(total_amount, 2) FROM Orders;
    ```

- **`FLOOR()`**: Rounds down to the nearest integer.
    ```sql
    SELECT FLOOR(total_amount) FROM Orders;
    ```

- **`CEIL()`**: Rounds up to the nearest integer.
    ```sql
    SELECT CEIL(total_amount) FROM Orders;
    ```

- **`ABS()`**: Returns the absolute value of a number.
    ```sql
    SELECT ABS(-100) AS positive_number;
    ```

## 6. Joins:
Joins are used to combine rows from two or more tables.

- **`INNER JOIN`**: Returns rows with matching values in both tables.
    ```sql
    SELECT Customers.first_name, Orders.order_id
    FROM Customers
    INNER JOIN Orders ON Customers.customer_id = Orders.customer_id;
    ```

- **`LEFT JOIN`**: Returns all rows from the left table, and matched rows from the right table. Unmatched rows result in `NULL` values.
    ```sql
    SELECT Customers.first_name, Orders.order_id
    FROM Customers
    LEFT JOIN Orders ON Customers.customer_id = Orders.customer_id;
    ```

- **`RIGHT JOIN`**: Returns all rows from the right table, and matched rows from the left table. Unmatched rows result in `NULL` values.
    ```sql
    SELECT Customers.first_name, Orders.order_id
    FROM Customers
    RIGHT JOIN Orders ON Customers.customer_id = Orders.customer_id;
    ```

- **`CROSS JOIN`**: Returns the Cartesian product of two tables.
    ```sql
    SELECT Customers.first_name, Orders.order_id
    FROM Customers
    CROSS JOIN Orders;
    ```

## 7. Subqueries and CTEs:
Used to write complex queries.

- **Subquery (used in `SELECT`)**:
    ```sql
    SELECT first_name, 
      (SELECT COUNT(*) FROM Orders WHERE Orders.customer_id = Customers.customer_id) AS order_count
    FROM Customers;
    ```

- **Subquery (used in `WHERE`)**:
    ```sql
    SELECT first_name FROM Customers
    WHERE customer_id IN (SELECT customer_id FROM Orders WHERE total_amount > 200);
    ```

- **Common Table Expression (CTE)**:
    ```sql
    WITH OrderTotals AS (
      SELECT customer_id, SUM(total_amount) AS total_spent
      FROM Orders
      GROUP BY customer_id
    )
    SELECT Customers.first_name, OrderTotals.total_spent
    FROM Customers
    JOIN OrderTotals ON Customers.customer_id = OrderTotals.customer_id;
    ```

## 8. Window Functions:
For ranking, cumulative sums, etc.

- **`ROW_NUMBER()`**: Assigns a unique row number for each row.
    ```sql
    SELECT customer_id, total_amount, ROW_NUMBER() OVER (ORDER BY total_amount DESC) AS row_num
    FROM Orders;
    ```

- **`RANK()`**: Assigns a rank to rows with ties.
    ```sql
    SELECT customer_id, total_amount, RANK() OVER (ORDER BY total_amount DESC) AS rank
    FROM Orders;
    ```

- **`LEAD()` and `LAG()`**: Returns the next or previous value in the result set.
    ```sql
    SELECT customer_id, total_amount,
      LAG(total_amount, 1) OVER (ORDER BY order_date) AS previous_order
    FROM Orders;
    ```

- **`SUM()` (as a window function)**: Cumulative sum.
    ```sql
    SELECT customer_id, total_amount,
      SUM(total_amount) OVER (ORDER BY order_date) AS cumulative_sum
    FROM Orders;
    ```

This cheat sheet covers many of the most common SQL functions and operations used in technical interviews and day-to-day work. Use it as a quick reference for writing efficient and clear SQL queries.

