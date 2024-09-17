---
layout: post
title: "Solve Complex Real World Problems Using SQL"
date: 2024-09-01
categories: blog
author: Nawaraj Paudel, PhD
---

## Introduction

Structured Query Language (SQL) is a powerful language for relational databases. It enables users to efficiently manage and manipulate data stored in relational database management systems (RDBMS). SQL is a must learn for Data Analyst, Data Scientist, Data Engineer and Machine Learning Engineer. We will provide `PostgreSQL`- specific commands when they differ from `MySQL`, while prioritizing the use of MySQL commands that are compatible with both databases whenever possible.

## Why Learn SQL?

- **Data Management**: SQL is essential for managing and manipulating data in relational databases.
- **Career Opportunities**: Proficiency in SQL is highly valued in many industries, including tech, finance, and healthcare.
- **Data Analysis**: SQL is a fundamental skill for data analysts and data scientists.

 ## Platforms to Learn SQL

1. **LeetCode**: Offers a comprehensive SQL study plan with 50 essential SQL questions for free.
   - [LeetCode SQL Study Plan](https://leetcode.com/studyplan/top-sql-50/)

2. **HackerRank**: Provides a variety of SQL challenges ranging from basic to advanced levels.
   - [HackerRank SQL Challenges](https://www.hackerrank.com/domains/sql)

3. **Codecademy**: Offers an interactive SQL course that covers the basics and more advanced topics.
   - [Codecademy SQL Course](https://www.codecademy.com/learn/learn-sql)

4. **Khan Academy**: Provides a free SQL course with video tutorials and interactive exercises.
   - [Khan Academy SQL Course](https://www.khanacademy.org/computer-programming/new/sql)

5. **W3Schools**: A comprehensive resource for learning SQL with examples and exercises.
   - [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)

8. **SQLZoo**: An interactive SQL tutorial with practice problems.
   - [SQLZoo](https://sqlzoo.net/wiki/SQL_Tutorial)

6. **Coursera**: Features SQL courses from top universities and institutions.
   - [Coursera SQL Courses](https://www.coursera.org/)

7. **Udemy**: Offers a variety of SQL courses for different skill levels.
   - [Udemy SQL Courses](https://www.udemy.com/)

## Relational Databases

There are many ways of storing data on a computer (text files, JSON files, CSV files, spreadsheets, etc.). A relational database is a data storage system with the following properties:

1. **Data is stored in tables**.
2. **Each table has a set of columns**. Each column is used to store a specific type of data.
3. **Data is stored as rows** (also called records) within database tables.
4. **Tables support CRUD operations on rows**: Create, Read, Update, and Delete.
5. **Tables can be connected to other tables** using relationship constraints.
6. **Information can be retrieved from the databases using SQL** (Structured Query Language).
7. **Databases can be hosted locally** (on your computer) or on the cloud for distributed access.

## Relational Database Software

- MySQL
- PostgreSQL
- SQLite
- Microsoft SQL Server
- MariaDB
- Oracle
- IBM DB2

## SQL Statements and Syntax

### Data Definition Language (DDL)
- Modifies the actual structure of a database rather than its content.
- Used for creating, altering, and deleting database objects.

  Commands:
  - `CREATE`
  - `DROP`
  - `DELETE`
  - `RENAME`
  - `COMMENT`

### Data Manipulation Language (DML)
- Allows you to manipulate the database's content.
- Used for searching, inserting, updating, and deleting data.

  Commands:
  - `SELECT`
  - `INSERT`
  - `UPDATE`
  - `DELETE`

### Data Control Language (DCL)
- Manages user access rights to the database.

  Commands:
  - `GRANT`
  - `REVOKE`
  - `LOCK`

### Transaction Control Language (TCL)
- Helps manage the changes made by DML commands.

  Commands:
  - `COMMIT`
  - `ROLLBACK`
  - `SAVEPOINT`
  - `CALL`
  - `EXPLAIN`

## SQL Data Types

### Numeric Data Types
- **INT**: INT, INTEGER, BIGINT, SMALLINT
- **DECIMAL**: DECIMAL(P, S) where P is the precision and S is the scale.
- **FLOAT**: FLOAT, REAL, DOUBLE PRECISION
- **NUMERIC**: NUMERIC(P, S) - similar to DECIMAL, it stores exact numeric values.
- **TINYINT**, **SMALLINT**, **INT**, **BIGINT**
- **DECIMAL**, **NUMERIC**, **FLOAT**

### Date and Time Data Types
- **DATE**
- **TIME**
- **DATETIME**
- **TIMESTAMP**
- **YEAR**

### String Data Types
- **CHAR**
- **VARCHAR**
- **VARCHAR(MAX)**
- **TEXT**
- **UNICODE CHARACTER/STRING**: NCHAR, NVARCHAR

### Binary Data Types
- **BINARY**
- **VARBINARY**

### Miscellaneous Data Types
- **BOOLEAN**

## Data Manipulation Language (DML)

We will primarily focus on Data Manipulation Language (DML) as it is the key area for SQL and most of the learning. This focus is particularly important because data scientists, machine learning engineers, and data analysts frequently use DML in their day-to-day work.

## SELECT
The `SELECT` statement is used to query data from a table. This is the most important command we will use in DML.
```sql
SELECT * FROM table_name; -- '*' means all columns (all table content)

SELECT 2; -- It prints out 2 in the console
```

### INSERT
The `INSERT` statement is used to add new rows to a table and we cab add multiple rows at once.

```sql
INSERT INTO table_name (col1, col2, col3)
VALUES 
        (value1, value2, value3)
        (value1, value2, value3);
```

### UPDATE
The `UPDATE` statement is used to modify existing rows in a table. You can use **CASE** for conditional updates. The syntax goes like `UPDATE`, `SET`, conditionals such as `WHERE`, `CASE`, `IF` as shown in example below:

```sql
UPDATE table_name 
SET col1 = val1, col2 = val2
WHERE condition;

UPDATE table_name
SET col1 = CASE 
    WHEN condition1 THEN value1
    WHEN condition2 THEN value2
    ELSE value3
END
WHERE condition;
```

### DELETE
The DELETE statement is used to remove existing rows from a table.

```sql
DELETE FROM table_name 
WHERE condition;
```

## SQL Query Structure Flow

**`SELECT -> DISTINCT -> FROM -> JOIN -> WHERE -> GROUP BY -> HAVING -> ORDER BY -> LIMIT -> OFFSET`**

When you write a SQL query, this is the order you follow. FROM and JOIN have same order of precedence.

## SQL Order of Operation Flow

The order in which SQL performs the query is different from the query structure. The SQL query order of operation follows:

**`FROM -> JOIN -> WHERE -> GROUP BY -> HAVING -> SELECT -> DISTINCT -> ORDER BY -> LIMIT -> OFFSET`**

<span style="color:green;">***The way we write SQL queries is quite different from how SQL query operations are executed. It’s crucial to understand and remember the SQL query structure and the order of operation flow, as this knowledge is essential when writing SQL queries later on.***</span>

I will discuss the syntax of the most commonly used data manipulation commands, data types, and other essential SQL concepts.

## Topic 1: String Manipulation

## Common Functions (PostgreSQL and MySQL)

### Concatenation
- `CONCAT()` or `||`
  - Example:
    ```sql
    SELECT 'Raj' || ' ' || 'Paudel' AS full_name;
    SELECT CONCAT('Raj', ' Paudel') AS full_name;
    ```
  - `CONCAT()` is more versatile and powerful than `||`, introduced in PostgreSQL 9.1 and above.
  - Example:
    ```sql
    SELECT CONCAT('Raj', NULL); -- 'Raj'
    SELECT 'Raj' || NULL; -- NULL
    ```

### Replace
- `REPLACE(source, from_text, to_text)`
  - `source`: Input string you want to replace.
  - `from_text`: Substring you want to search and replace. If `from_text` appears multiple times in `source`, it will replace all occurrences.
  - `to_text`: New substring that you want to replace the `from_text`.
  - Example:
    ```sql
    UPDATE post
    SET url = REPLACE(url, 'http', 'https');
    ```

### Regular Expressions
- `REGEXP_REPLACE(source, pattern, replacement_string [, flags])`
  - `pattern`: POSIX regular expression.
  - Example:
    ```sql
    SELECT REGEXP_REPLACE('abc', 'a.c', 'xyz'); -- 'xyz'
    ```

### Pattern Matching
- `LIKE` vs `ILIKE` (case insensitive)
  - `%`: Matches any sequence of characters.
  - `_`: Matches any single character.
  - Example:
    ```sql
    SELECT * FROM products WHERE code ILIKE 'A%';
    ```

### Substring Extraction
In SQL, indexing starts from 1, unlike in Python, which starts from 0. `SUBSTRING('PostgreSQL', 2, 4)` means starting from index 2, retrieve 4 characters.

- `SUBSTRING()`, `LEFT()`, `RIGHT()`
  - Example:
    ```sql
    SELECT SUBSTRING('PostgreSQL', 2, 4); -- 'ostg'
    SELECT LEFT('PostgreSQL', 4); -- 'Post'
    SELECT RIGHT('PostgreSQL', 4); -- 'eSQL'
    ```

### Length of a String
- `LENGTH()`: Counts spaces as well. If you want to remove spaces from a string and then measure its length, you can replace the spaces with an empty string and use the LENGTH() function in SQL.
  - Example:
    ```sql
    SELECT LENGTH('PostgreSQL is cool'); -- 18
    SELECT CHARACTER_LENGTH('PostgreSQL is cool'); -- 18
    ```

### Stripping White Spaces or Specified Characters
- `TRIM()`, `RTRIM()`, `LTRIM()`, `BTRIM()`
  - Syntax: `TRIM([LEADING | TRAILING | BOTH] [characters] FROM string)`
  - Example:
    ```sql
    SELECT BTRIM('  PostgreSQL  '); -- 'PostgreSQL'
    ```

### Upper and Lower Case
- `UPPER()`, `LOWER()`
  - Example:
    ```sql
    SELECT UPPER('Raj'); -- 'RAJ'
    SELECT LOWER('Raj'); -- 'raj'
    SELECT INITCAP('raj'); -- 'Raj'
    ```

### Reverse
- `REVERSE()`
  - Example:
    ```sql
    SELECT REVERSE('Raj'); -- 'jaR'
    ```

## PostgreSQL Specific Functions

### Split Part
- `SPLIT_PART(string, delimiter, field_index)`
  - Example:
    ```sql
    SELECT SPLIT_PART('newking@gmail.com', '@', 1); -- 'newking'
    ```
### Title (First letter is upper case and rest are lower case)
- `INITCAP(string)`
- Example:
    ```sql
    SELECT INITCAP('raj'); -- 'Raj'
    ```

### String Aggregation
- `STRING_AGG(column, delimiter [ORDER BY column])`
  - Used to concatenate strings in `GROUP BY`.
  - Example:
    ```sql
    SELECT STRING_AGG(name, ', ') AS names 
    FROM employees
    GROUP BY department;
    ```

## MySQL Specific Functions

### Split Part
- `SUBSTRING_INDEX(string, delimiter, number)`
  - Example:
    ```sql
    SELECT SUBSTRING_INDEX('newking@gmail.com', '@', 1); -- 'newking'
    ```

### String Aggregation
- `GROUP_CONCAT(column, delimiter [ORDER BY column])`
  - Used to concatenate strings in `GROUP BY`.
  - Example:
    ```sql
    SELECT GROUP_CONCAT(name, ', ') AS names 
    FROM employees
    GROUP BY department;
    ```

### Title (First letter is upper case and rest are lower case)
MySQL doesn’t have an `INITCAP()` function like PostgreSQL databases. Instead, you can achieve the same result by combining `LOWER()` and `UPPER()` functions along with `SUBSTRING()`. Here’s how you can do it:
- Example:
    ```sql
    SELECT CONCAT(UPPER(SUBSTRING('rAj', 1, 1)), LOWER(SUBSTRING('rAj', 2))); -- 'Raj'
    ```


## Topic 2: Date and Time Functions

## Common Functions (PostgreSQL and MySQL)

### Current Date and Time
- `NOW()` - Returns the current date and time.
- `CURRENT_DATE` - Returns the current date in `YYYY-MM-DD` (`%Y-%m-%d`) format.
- `CURRENT_TIME` - Returns the current time.
- `CURRENT_TIMESTAMP` - Returns the current date and time.

### Extracting Parts of a Date/Time
`EXTRACT(field FROM source)` - Extracts a part of the date/time given date/time is in `'%Y/%m/%d` (separator could be `-` as well) format and it is a `DATETIME` object not a string, if string returns `NULL`. For example, `SELECT EXTRACT(MONTH FROM '2018-02-28')` returns `NULL`.
  - Example: `SELECT EXTRACT(DAY FROM NOW());`

### Using Intervals
Both MySQL and PostgreSQL support interval arithmetic, but there is a slight difference in syntax. In PostgreSQL, the unit of the interval is enclosed in quotes.

- `INTERVAL quantity unit` - Adds or subtracts intervals. Please note there is no quotation marks after `INTERVAL` for `quantity unit` in `MySQL` unlike `PostgreSQL`.
  - Example: `SELECT NOW() + INTERVAL 1 DAY;`
  - Example: `SELECT NOW() - INTERVAL 1 DAY;`


## MySQL Specific Functions

### Truncating Dates
- `DATE_FORMAT(date, format)` - Formats the date to a specified precision.
  - Example: 
    - `SELECT DATE_FORMAT(NOW(), '%Y-%m-01');` (Truncates to the first day of the month)
    - `SELECT DATE_FORMAT(NOW(), '%Y-%m');` (Removes day part from the date)

### Extracting Date Parts
MySQL is much flexible in that it automatically recognizes str date as datetime object if the date is in the format `%Y-%m-%d` format. 

- Extract the month
    ```sql
    SELECT MONTH('2023-09-05') AS month;
    ```

- Extract the hour
    ```sql
    SELECT HOUR('2023-09-05 14:30:00') AS hour;
    ```

- Extract the minute
    ```sql
    SELECT MINUTE('2023-09-05 14:30:00') AS minute;
    ```
- Extract the day
    ```sql
    SELECT DAY('2023-09-05') AS day;
    ```

- Extract the year
    ```sql
    SELECT YEAR('2023-09-05') AS year;
    ```

- Extract the day of the week (1 = Sunday, 2 = Monday, ..., 7 = Saturday)
    ```sql
    SELECT DAYOFWEEK('2023-09-05') AS day_of_week;
    ```

- Extract the name of the month
    ```sql
    SELECT MONTHNAME('2023-09-05') AS month_name;
    ```

- Extract the week of the year
    ```sql
    SELECT WEEKOFYEAR('2023-09-05') AS week_of_year;
    ```

- Extract the weekday (0 = Monday, 1 = Tuesday, ..., 6 = Sunday)
    ```sql
    SELECT WEEKDAY('2023-09-05') AS weekday;
    ```

- Extract the microseconds
    ```sql
    SELECT MICROSECOND('2023-09-05 14:30:00.123456') AS microseconds;
    ```

### Casting to Timestamp
- `STR_TO_DATE(time_text, format)` - Converts text to date.
  - Example: `SELECT STR_TO_DATE('2023-09-01 12:34:56', '%Y-%m-%d %H:%i:%s');`


### Calculating Date Differences
- `TIMESTAMPDIFF(unit, datetime_expr1, datetime_expr2)` - Calculates the difference between two dates. This is equivalent to `EXTRACT(EPOCH FROM datetime_expr1 - datetime_expr2)` and converting the `EPOCH in seconds` to desired unit. Make sure datetime_expr1 and datetime_expr2
are explicit date time object in PostgreSQL.

  - Example: `SELECT TIMESTAMPDIFF(YEAR, '1992-06-25 05:15:37', NOW());`
- We can also use `DATE_ADD()` and `DATE_SUB()` with `INTERVAL quantity unit`. Note the syntax difference: PostgreSQL is flexible using `INTERVAL '10 DAYS'` or `INTERVAL '10 DAY'`.

  - Example: `SELECT DATE_ADD('2024-08-01', INTERVAL 10 DAY) AS new_date;`
  - Example: `SELECT DATE_SUB('2024-08-01', INTERVAL 10 DAY) AS new_date;`
    
## PostgreSQL Specific Functions

### Casting to Timestamp
- `TO_TIMESTAMP(time_text, format)` - Converts text to timestamp.
  - Example: `SELECT TO_TIMESTAMP('2023-09-01 12:34:56', 'YYYY-MM-DD HH24:MI:SS');`
- Explicit Type Casting
  - Example: `SELECT '2023-09-01 12:34:56'::TIMESTAMP;`

### Truncating Dates
- `DATE_TRUNC(field, source)` - Truncates a timestamp or interval to a specified precision.
  - Example: `SELECT DATE_TRUNC('month', NOW());`

### Calculating Date Differences
**Note**: Please always use `AGE()` function which calculates the difference by considering the actual calendar months and days. Direct Subtraction assumes 30 days per month.

- `AGE(timestamp, timestamp)` - Calculates the difference between two timestamps.
  - Example: `SELECT AGE('1992-06-25 05:15:37'::TIMESTAMP, NOW());`
  - Example: `SELECT NOW() - '1992-06-25 05:15:37'::TIMESTAMP;`

- Convert date difference in desired units
    - Example: `SELECT EXTRACT(EPOCH FROM ('2024-09-01 12:00:00'::timestamp - '2024-08-01 12:00:00'::timestamp)) AS seconds_diff;` -- Assumes 30 days in a month
    - Example: `SELECT EXTRACT(EPOCH FROM AGE('2024-09-01 12:00:00'::timestamp, '2024-08-01 12:00:00'::timestamp)) AS seconds_diff;` -- Uses ISO calendar
    - Example: `SELECT DATE_PART('DAY', '2024-09-01'::timestamp - '2024-08-01'::timestamp) AS days_diff;`
    - Example: `SELECT DATE_PART('YEAR', AGE('2036-09-01'::timestamp,'2024-08-01'::timestamp)) AS years_diff;`

### Using Intervals
- `INTERVAL 'quantity unit'` - Adds or subtracts intervals. Make sure the `quantity unit` is inside quotation marks like `INTERVAL 2 MONTH`, this is what is different from MySQL.
  - Example: `SELECT NOW() + INTERVAL '1 DAY';`

### Generating Series
- `GENERATE_SERIES(start, stop, step)` - Generates a series of values. Note it must be `6 DAYS` noy `6 DAY` in the following example.
  - Example: `SELECT GENERATE_SERIES(NOW(), NOW() + INTERVAL '6 DAYS', '1 DAY');`

## Example Queries

### Selecting Last Day's Logs
```sql
SELECT log_date, log_message 
FROM logs 
WHERE log_date >= NOW() - INTERVAL 1 DAY;
```

## Topic 3: JOINS

## Common Functions (PostgreSQL and MySQL)

### INNER JOIN
Only rows matching `customer_id` values in both tables will be returned.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
INNER JOIN customers
ON orders.customer_id = customers.customer_id;
```

### LEFT JOIN or LEFT OUTER JOIN
Returns all rows from the left table and matching rows from the right table. If there is no match, NULL values are returned for columns from the right table.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
LEFT JOIN customers
ON orders.customer_id = customers.customer_id;
```

### RIGHT JOIN or RIGHT OUTER JOIN
Returns all rows from the right table and matching rows from the left table. If there is no match, NULL values are returned for columns from the left table.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
RIGHT JOIN customers
ON orders.customer_id = customers.customer_id;
```

### CROSS JOIN
It’s like a Cartesian product and returns all possible combinations of rows. No need to use `ON`.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
CROSS JOIN customers;
```

### SELF JOIN
Join a table to itself when you need to compare rows within the same table to establish hierarchical relationships within the data. We can use `self join` in lieu of window functions as well.
```sql
SELECT a.employee_id, a.name AS employee_name, b.name AS manager_name
FROM employees a
JOIN employees b -- give different name for same table
ON a.manager_id = b.employee_id;
```

### ON Clause
When column names are different, or you want to keep both.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
INNER JOIN customers
ON orders.customer_id = customers.customer_id;
```
Using additional conditions like `AND` directly in the `JOIN` clause can sometimes be more efficient because it reduces the number of rows that need to be processed than using `WHERE` clause after `JOIN`. Here’s an example:
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
INNER JOIN customers
ON orders.customer_id = customers.customer_id
AND customers.status = 'active';
--************versus*************************--
SELECT orders.order_id, customers.customer_name
FROM orders
INNER JOIN customers
ON orders.customer_id = customers.customer_id
WHERE customers.status = 'active';
```

### USING Clause
When the column names are the same, keeps only one column in the result. I do not recommend this approach, however its good to know it exists.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
INNER JOIN customers USING (customer_id);
```
If you want to use additional filtering condition like `AND` along with `USING`, that is not allowed. We must use `WHERE` clause after `USING` to filter the data.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
INNER JOIN customers USING (customer_id)
WHERE customers.status = 'active';
```

### UNION
If tables have the same structure (same number of columns, same names and same orderof columns) and you want to stack their rows on top of each other (removing duplicates by default), you can use `UNION`.
```sql
SELECT employee_id, name, department
FROM employees
UNION
SELECT employee_id, name, department
FROM contractors;
```

### UNION ALL
If you want to keep duplicates (rows) as well.
```sql
SELECT employee_id, name, department
FROM employees
UNION ALL
SELECT employee_id, name, department
FROM contractors;
```

## MySQL Specific Functions

MySQL **does not support FULL JOIN or FULL OUTER JOIN** directly. You can achieve similar results using a combination of `LEFT JOIN` and `RIGHT JOIN` with `UNION`.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
LEFT JOIN customers
ON orders.customer_id = customers.customer_id
UNION
SELECT orders.order_id, customers.customer_name
FROM orders
RIGHT JOIN customers
ON orders.customer_id = customers.customer_id;
```


## PostgreSQL Specific Functions

### INTERSECT
Selects rows common to both queries.
```sql
SELECT employee_id, name, department
FROM employees
INTERSECT
SELECT employee_id, name, department
FROM contractors;
```
### EXCEPT
Selects rows from the first query that are not in the second query. Its like A - B in set (Keep all elements from A after deleting common elements from B).
```sql
SELECT employee_id, name, department
FROM employees
EXCEPT
SELECT employee_id, name, department
FROM contractors;
```

### FULL JOIN or FULL OUTER JOIN
Returns all rows when there is a match in either the left or right table. If there is no match, NULL values are returned for columns from the opposite table.
```sql
SELECT orders.order_id, customers.customer_name
FROM orders
FULL JOIN customers
ON orders.customer_id = customers.customer_id;
```

Let’s understand how joins work. Let’s say we have `Table A` and `Table B` with a common column user_id

### Table A
| user_id | first_name |
|---------|------------|
| 1       | Alice      |
| 1       | Bob        |
| 0       | Charlie    |
| 1       | David      |
| 2       | Eve        |

### Table B
| user_id | last_name  |
|---------|------------|
| 1       | Smith      |
| 0       | Johnson    |
| 1       | Williams   |
| NULL    | Brown      |
| 3       | Davis      |

Lets do different types of `JOIN` on `user_id` and report how the output looks like.

#### Step-by-Step Matching for INNER JOIN
```sql
SELECT a.user_id, a.first_name, b.last_name
FROM table_a a
INNER JOIN table_b b
ON a.user_id = b.user_id;
```
Start with the first row in Table A:
user_id = 1 (Alice)

Find all rows in Table B where user_id = 1: Smith, Williams
Combine Alice with each matching row in Table B.
Result:
| user_id | first_name | last_name |
|---------|------------|-----------|
| 1       | Alice      | Smith     |
| 1       | Alice      | Williams  |

Move to the next row in Table A:
user_id = 1 (Bob)

Find all rows in Table B where user_id = 1: Smith, Williams
Combine Bob with each matching row in Table B.
Result:
| user_id | first_name | last_name |
|---------|------------|-----------|
| 1       | Bob        | Smith     |
| 1       | Bob        | Williams  |

Move to the next row in Table A:
user_id = 0 (Charlie)

Find the row in Table B where user_id = 0: Johnson
Combine Charlie with the matching row in Table B.
Result:
| user_id | first_name | last_name |
|---------|------------|-----------|
| 0       | Charlie    | Johnson   |

Move to the next row in Table A:
user_id = 1 (David)

Find all rows in Table B where user_id = 1: Smith, Williams
Combine David with each matching row in Table B.
Result:
| user_id | first_name | last_name |
|---------|------------|-----------|
| 1       | David      | Smith     |
| 1       | David      | Williams  |

Move to the next row in Table A:
user_id = 2 (Eve)

There are no rows in Table B where user_id = 2.
No matches for Eve.
Combine all results:
| user_id | first_name | last_name |
|---------|------------|-----------|
| 1       | Alice      | Smith     |
| 1       | Alice      | Williams  |
| 1       | Bob        | Smith     |
| 1       | Bob        | Williams  |
| 0       | Charlie    | Johnson   |
| 1       | David      | Smith     |
| 1       | David      | Williams  |

This step-by-step explanation should help you understand how an INNER JOIN works by matching each row in Table A with rows in Table B based on the user_id. 

#### Step-by-Step Matching for LEFT JOIN
```sql
SELECT a.user_id, a.first_name, b.last_name
FROM table_a a
LEFT JOIN table_b b
ON a.user_id = b.user_id;
```

A `LEFT JOIN` is essentially an `INNER JOIN` plus the remaining unmatched rows from the left table (table_a in above query). In our example, the unmatched user_id from Table A is 2. The result of `LEFT JOIN` is just user_id = 2 row added at the bottom of `INNER JOIN` result.

| user_id | first_name | last_name |
|---------|------------|-----------|
| 1       | Alice      | Smith     |
| 1       | Alice      | Williams  |
| 1       | Bob        | Smith     |
| 1       | Bob        | Williams  |
| 0       | Charlie    | Johnson   |
| 1       | David      | Smith     |
| 1       | David      | Williams  |
| 2       | Eve        | NULL      |

#### Step-by-Step Matching for RIGHT JOIN
```sql
SELECT a.user_id, a.first_name, b.last_name
FROM table_a a
RIGHT JOIN table_b b
ON a.user_id = b.user_id;
```
A `RIGHT JOIN` is essentially an `INNER JOIN` plus the remaining unmatched rows from the right table (table_b in above query). In our example, the unmatched user_id from Table B are NULL and 3. The result of `RIGHT JOIN` is just user_id = NULL and user_id = 3 row added at the bottom of `INNER JOIN` result.

| user_id | first_name | last_name |
|---------|------------|-----------|
| 1       | Alice      | Smith     |
| 1       | Bob        | Smith     |
| 1       | David      | Smith     |
| 0       | Charlie    | Johnson   |
| 1       | Alice      | Williams  |
| 1       | Bob        | Williams  |
| 1       | David      | Williams  |
| NULL    | NULL       | Brown     |
| 3       | NULL       | Davis     |

#### Step-by-Step Matching for OUTER JOIN
An `OUTER JOIN` is essentially an `INNER JOIN` with unmatched rows from both tablles appended at the bottom. Alternatively, it can be viewed as a `UNION` of `RIGHT JOIN` and `LEFT JOIN`. We append rows corresponding to user_id = 2 from table A and user_id = 3 and user_id = NULL to the result of `INNER JOIN`.

```sql
SELECT a.user_id, a.first_name, b.last_name
FROM table_a a
OUTER JOIN table_b b -- for PostgreSQL only
ON a.user_id = b.user_id;
```

| user_id | first_name | last_name |
|---------|------------|-----------|
| 1       | Alice      | Smith     |
| 1       | Bob        | Smith     |
| 1       | David      | Smith     |
| 0       | Charlie    | Johnson   |
| 1       | Alice      | Williams  |
| 1       | Bob        | Williams  |
| 1       | David      | Williams  |
| NULL    | NULL       | Brown     |
| 3       | NULL       | Davis     |
| 2       | Eve        | NULL      |

### JOIN Takeaways:

 - <span style = "color:green; font-weight:bold; font-size:20px;"> You never have to use `RIGHT JOIN` if you prefer. The rule of thumb is to use `LEFT JOIN` where the larger table based on [common] column to join on, the table for which you want all information from, is on the left and the smaller table, the table for which we want only information common with larger table, is on the right. This makes the query more intuitive and easier to read.</span>
 - <span style = "color:green; font-weight:bold; font-size:20px;"> When you use a `LEFT JOIN`, you return all rows from the left table, and if the right table does not have matching rows, it returns `NULL`. When you want `NULL` values from the right table if the rows do not match based on join column (usually the smaller table in terms of the column you join on), you should use `LEFT JOIN`. If you want `NULL` values from both tables, use a `FULL OUTER JOIN`.</span>
- <span style = "color:green; font-weight:bold; font-size:20px;">  Use `INNER JOIN` when you want to return only the rows that have matching values in both tables. This is useful when you need to find records that exist in both tables.</span>

**Topic 3: AGGREGATIONS AND GROUPING**

When you need to calculate aggregates for a group, use `GROUP BY` clause. The `GROUP BY` clause must be accompanied by an `aggregate function`. **This is a crucial concept in Data Science. Please ensure you thoroughly understand each concept below before tackling real-world problems.**

- **GROUP BY**: Aggregating data into groups.
- **HAVING**: Filtering groups after aggregation.
- **Aggregate functions**: `SUM()`, `COUNT()`, `AVG()`, `MIN()`, `MAX()`, `STDEV()`, `STDEVP()`, `STRING_AGG() or GROUP_AGG()`

**Order of Operations:**
1. `FROM` + `JOIN` -- Join tables if you have `JOIN`
2. `WHERE` -- filtering rows before aggregation
3. `GROUP BY` -- Aggregating data into groups
4. `HAVING` -- Filtering groups after aggregation
5. `SELECT` -- Select data/ Window functions happen here
6. `DISTINCT` -- Select only distinct/unique values
7. `ORDER BY`  -- Order the result by column(s), default ASC
8. `LIMIT` -- How many rows we want to retrieve
9. `OFFSET` -- Which row should we start retrieving data from

For the following sales data, calculate the total sales for each Location.

**Table Sales**
| Location    | Product | Price  |
|-------------|---------|--------|
| New York    | Laptop  | 1200.00|
| New York    | Tablet  | 300.00 |
| New York    | Laptop  | 1300.00|
| Los Angeles | Laptop  | 1100.00|
| Los Angeles | Tablet  | 350.00 |
| Los Angeles | Laptop  | 1200.00|
| Chicago     | Laptop  | 1150.00|
| Chicago     | Tablet  | 320.00 |
| Chicago     | Laptop  | 1250.00|

Lets put together `Price` of products for each `Location` which is called grouping. The table after `GROUP BY` Location looks like this:
| Location    | Price  |
|-------------|--------|
| Chicago     | 1150.00|
|             | 320.00 |
|             | 1200.00|
| Los Angeles | 1100.00|
|             | 350.00 |
|             | 1150.00|
| New York    | 1200.00|
|             | 300.00 |
|             | 1300.00|

Now we can do aggregation for each Location like total sales, average sales, max sales, min sales etc. The table below shows table for total sales for each location.

| Location    | Total Sales |
|-------------|-------------|
| Chicago     | 2670.00     |
| Los Angeles | 2600.00     |
| New York    | 2800.00     |

The `SQL` query to achieve above result looks like
```sql
SELECT Location, SUM(Price) AS 'Total Sales'
FROM Sales
GROUP BY Location;
```
What if we only want Location where the `Total Sales` is greater than 2620? Use `HAVING` after `GROUP BY` because want to filter group results.
```sql
SELECT Location, SUM(Price) AS 'Total Sales'
FROM Sales
GROUP BY Location
HAVING SUM(Price) > 2610;
```
I will leave it up to you to figure out why I used `SUM(Price) > 2610` instead of `'Total Sales' > 2610` after `HAVING`. The answer lies in understanding the order of operations. The result of above query is shown below:

| Location    | Total Sales |
|-------------|-------------|
| Chicago     | 2670.00     |
| New York    | 2800.00     |

If we want `Product` column in `GROUP BY` result can we do the following?
```sql
-- Wrong Query
SELECT Location, Product, SUM(Price) AS 'Total Sales'
FROM Sales
GROUP BY Location;
```
The answer is absolutely **NO**. We can select only the column(s) that we have in the GROUP BY clause. In the above case, we need to include Product in the GROUP BY clause as well.

```sql
-- Correct Query:
SELECT Location, Product, SUM(Price) AS 'Total Sales'
FROM Sales
GROUP BY Location, Product;
```
The result of above query looks like:

| Location    | Product | Total Sales |
|-------------|---------|-------------|
| Chicago     | Laptop  | 2350.00     |
|             | Tablet  | 320.00      |
| Los Angeles | Laptop  | 2250.00     |
|             | Tablet  | 350.00      |
| New York    | Laptop  | 2500.00     |
|             | Tablet  | 300.00      |


## GROUP BY Takeaways:
- The `GROUP BY` clause is used to aggregate data into groups based on **one or more columns**.
- It **must be accompanied by an aggregate function** such as SUM(), COUNT(), AVG(), MIN(), MAX() or GROUP_CONCAT().
- We can only `select columns` that are in `GROUP BY` clause.
- Use `WHERE` clause to filter data before `GROUP BY` and `HAVING` to filter groups based on aggregate result after `GROUP BY`.

 
## Topic 5: SUBQUERIES & NESTED QUERIES

A basic subquery is enclosed within parentheses and typically placed within a `WHERE`, `FROM`, or `SELECT` clause of the main query.

### Example 1: Subquery in `SELECT` Clause
Assume two tables: orders and customers. Let’s count orders per customer.
```sql
SELECT customer_id, customer_name,
    (SELECT COUNT(*)
     FROM orders
     WHERE orders.customer_id = customers.customer_id) AS order_count
FROM customers;
```
**Note**: `COUNT(*)` counts `NULL` values as well but `COUNT(col_name)` counts only `NON NULL` values in the column.

### Example 2: Subquery in `WHERE` Clause
Assume we have two tables: `customers` (with columns `customer_id`, `customer_name`) and `orders` (with columns `order_id`, `customer_id`, `order_amount`). We want to find customers who have placed orders greater than $1000.

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (
    SELECT customer_id
    FROM orders
    WHERE order_amount > 1000
);
```

### Example 2: Subquery in `FROM` Clause (Derived Tables)
Assume you have two tables: customers (with columns customer_id, customer_name) and orders (with columns order_id, customer_id, order_amount). You want to find customers whose individual order amounts are above the average order amount across all customers.
```sql
SELECT c.customer_id, c.customer_name, o.avg_order_amount
FROM customers c
JOIN (
    SELECT customer_id, AVG(order_amount) AS avg_order_amount
    FROM orders
    GROUP BY customer_id
) AS o
ON c.customer_id = o.customer_id
WHERE o.avg_order_amount > (
    SELECT AVG(order_amount)
    FROM orders
);
```
### Example 4: Correlated Subqueries
Finding employees with salaries above their department average. Assume a table employees.
```sql
SELECT employee_id, employee_name, salary
FROM employees e
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
    WHERE department_id = e.department_id
);
```
Note in `WHERE` clause, the column from inner query (or subquery) table `employees` is on left side and outer query table `employees e` column is on the right side. The setup `WHERE department_id = e.department_id` ensures that the subquery is executed for each row in the outer query, using the value of e.department_id from the current row of the outer query. This creates a correlation between the outer and inner queries, making the subquery dependent on the outer query.

### Example 5: Using Subqueries with EXISTS and NOT EXISTS
`EXISTS` and `NOT EXISTS` are SQL keywords used to check for the existence of rows returned by a subquery. They are often used in `WHERE` clauses to conditionally filter rows based on whether the subquery returns any result.

Assume tables customers and invoices. We want to find customers who have unpaid invoices.
```sql
SELECT customer_id, customer_name
FROM customers c
WHERE EXISTS (
    SELECT 1 -- we just want to know if it exists i.e., at least one value is True, not return query result as rows
    FROM invoices i
    WHERE i.customer_id = c.customer_id
    AND i.paid = false
);
```

## TOPIC 6: COMMON TABLE EXPRESSIONS (CTEs)

CTEs are used for readability, code reusability, recursive queries, data transformation, aggregation, and window functions. We can define as many CTEs as needed and use results from one CTE in another. **There must be a query with a SELECT statement after the CTE is defined.**

### Example: Average Order Amount per Customer
Assume two tables: `customers` (with column names `customer_id`, `customer_name`) and `orders` (with columns `order_id`, `customer_id`, and `order_amount`). 

```sql
WITH AvgOrderAmountPerCustomer AS (
    SELECT
        customer_id,
        AVG(order_amount) AS avg_order_amount
    FROM orders
    GROUP BY customer_id
)
SELECT
    c.customer_id,
    c.customer_name,
    a.avg_order_amount
FROM customers c
JOIN AvgOrderAmountPerCustomer a
ON c.customer_id = a.customer_id;
```
This example demonstrates how to use a CTE to calculate the average order amount per customer and then join it with the `customers` table to display the customer details along with their average order amount.

**Note**: 
We had to use a CTE because we wanted `customer_name` in the final result as well. If you look at the CTE `AvgOrderAmountPerCustomer`, we have grouped by the column `customer_id`, and we can only select the column which is in the `GROUP BY` clause: `customer_id`. However, we wanted `customer_name` in the result as well, which is why we had to store the grouped result in a CTE and then join it with the original table to get the desired result.**


# TOPIC 7: WINDOW FUNCTIONS

Window functions are different from aggregate functions like `SUM()` or `AVG()` in that they do not collapse the rows into a single output row for each group.

## Syntax
```sql
WINDOW_FUNCTION(column) OVER (
    [PARTITION BY partition_expression]
    [ORDER BY sort_expression [ASC | DESC]]
    [ROWS | RANGE clause]
)
```
**Note: Not all window functions require a column as an argument, for example, RANK().**

## Window Functions That Don't Require Ordering (Except for Running Aggregates)
All aggregate functions require an argument column that has the appropriate data type. For example, SUM(), AVG() etc. must have numeric column as its argument.

- SUM(column) OVER(ORDER BY sort_exp)-- Returns running total.
- AVG(column) OVER(ORDER BY sort_exp)-- Returns running average.
- MIN(column) OVER(ORDER BY sort_exp)-- Returns running min.
- MAX(column) OVER(ORDER BY sort_exp)-- Returns running max.
- COUNT(column) OVER(ORDER BY sort_exp)-- Returns running count.

Please remember that `SUM(column) OVER()` calculates the total sum of the column and returns this total sum for every row in the result set. This does not provide a running total. To calculate a running total, you must use `SUM(column) OVER(ORDER BY sort_expression)`, the key is `ORDER BY` in `OVER()`.

Standard aggregate functions in SQL are designed to handle `NULL` values. For example, `SUM()` ignores `NULL` values when calculating the total. This means you don't need to worry about `NULL` values affecting the results of your standard aggregate functions.


## Window Functions thhat MUST to be sorted (Rank Functions)
- ROW_NUMBER() -- Gives unique serial number from 1 to length of table
- RANK() -- Gap in rank if tie, use same rank for tie and the next rank will skip the number of tied rows
- DENSE_RANK() -- No gap in rank if tie, gives same rank
- PERCENT_RANK() -- Relative standing of a value within a dataset, expressed as a percentage
- CUME_DIST() -- cumulative distribution of value that lies between (0, 1]
- NTILE(n) - n (number of partitions), n = 1 means top bucket
- LEAD(column, offset, default) -- get [offset] next row
- LAG(column, offset, default) -- get [offset] previous row
- FIRST_VALUE(column) -- get first value of a column
- LAST_VALUE(column) -- get last value of a column
- NTH_VALUE(column, n) -- get nth value of a column


For LEAD() and LAG(), the default `offset` is 1 (get next row value for `LEAD` and get previous row value for `LAG`) and `default` is `NULL` if the next or previous row does not exists. We can specify value for `default` like keep the current row value as `LEAD(column, 1, column)`. 

### Frame Clauses
Operates on physical row positions.

- **ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW**: Includes all rows from the start of the partition to the current row. This is default if you do not specify frame clause in `OVER()`.

- **ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING**: Includes the current row and all following rows.

- **ROWS BETWEEN n PRECEDING AND CURRENT ROW**:  Includes a specified number of rows `n` before the current row and the current row.

- **ROWS BETWEEN CURRENT ROW AND 3 FOLLOWING**: ncludes the current row and a specified number of rows after the current row.

 Operates on logical values (e.g., dates, numeric ranges).

 - **RANGE BETWEEN INTERVAL '3' DAYS PRECEDING AND CURRENT ROW**
 - **RANGE BETWEEN CURRENT ROW AND INTERVAL '3' DAYS FOLLOWING**

For PostgreSQL, use `'3 DAYS'` instead of `'3' DAYS`. 

```sql
SELECT department_name, headcount,
       CUME_DIST() OVER (ORDER BY headcount) AS cume_dist_val
FROM department_headcounts;
```

Calculate monthly sales decrease:

```sql
SELECT 
    month,
    sales,
    LAG(sales) OVER (ORDER BY month) AS previous_month_sales,
    sales - LAG(sales) OVER (ORDER BY month) AS sales_decrease
FROM 
    monthly_sales;
```

To find the employee with the second highest salary in each department, you can use the NTH_VALUE() function:

```sql
SELECT 
    employee_name, 
    department, 
    salary,
    NTH_VALUE(salary, 2) OVER (
        PARTITION BY department 
        ORDER BY salary DESC 
    ) AS second_highest_salary
FROM 
    employees;
```

We can achieve the same result as NTH_VALUE() illustrated above using DENSE_RANK() + CTE.

```sql
WITH RankedSalaries AS (
    SELECT 
        employee_name, 
        department, 
        salary,
        DENSE_RANK() OVER (
            PARTITION BY department 
            ORDER BY salary DESC
        ) AS salary_rank
    FROM 
        employees
)
SELECT 
    employee_name, 
    department, 
    salary
FROM 
    RankedSalaries
WHERE 
    salary_rank = 2;
```

7 day movinge average sales given sales_date is unique:

```sql
SELECT 
    sales_date, 
    sales_amount,
    AVG(sales_amount) OVER (
        ORDER BY sales_date 
        ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
    ) AS moving_avg_7_day
FROM 
    sales_data;
```

Assume you have a table employees with columns employee_name and salary. Here’s how you can use NTILE() to find the top 10 percentile earners:

```sql
WITH SalaryBuckets AS (
    SELECT 
        employee_name, 
        salary,
        NTILE(10) OVER (ORDER BY salary DESC) AS salary_bucket
    FROM 
        employees
)
SELECT 
    employee_name, 
    salary
FROM 
    SalaryBuckets
WHERE 
    salary_bucket = 1;
```

## Topic 10: CONDITIONAL STATEMENTS

Create a new column (or modify an existing column) based on conditions applied to an existing column or columns.
```sql
CASE
    WHEN (condition) THEN <value>
    WHEN (condition) THEN <value>
    ...
    ELSE <value>
END;
```

We can also create multiple columns from a given condition using CASE (like pivoting a table):

```sql
CASE WHEN (condition) THEN <value> END AS col_1
CASE WHEN (condition) THEN <value> END AS col_2
.....................
CASE WHEN (condition) THEN <value> END AS col_m
;
```

If using `CASE` with `GROUP BY`, do not forget to use aggregate function. Let’s say you have a table sales with columns salesperson, region, and sales_amount. You want to categorize the sales amounts into ‘High’, ‘Medium’, and ‘Low’ categories and then calculate the total sales for each category.

### Nested CASE

```sql
SELECT 
    customerid,
    purchase_amount,
    CASE 
        WHEN customer_type = 'Regular' THEN
            CASE 
                WHEN purchase_amount < 100 THEN purchase_amount * 0.05
                ELSE purchase_amount * 0.10
            END
        WHEN customer_type = 'Premium' THEN
            CASE 
                WHEN purchase_amount < 100 THEN purchase_amount * 0.10
                ELSE purchase_amount * 0.15
            END
        ELSE 0
    END AS discount
FROM 
    purchases;
```

```sql
IF(condition, value_if_true, value_if_false)
```

The following says `IF` id % 2 = 0 (even) then do id - 1 else id + 1 and if maximum id is odd keep it as it is. Its a exchange seat problem.

```sql
SELECT 
    IF(id % 2 = 1 AND id + 1 <= (SELECT MAX(id) FROM Seat), id + 1, 
       IF(id % 2 = 0, id - 1, id)) AS id,
    student
FROM 
    Seat
ORDER BY 
    id;
```

Here’s how you can use nested IF functions:

```sql
SELECT 
    name,
    salary,
    IF(salary > 2000, 'High', IF(salary BETWEEN 1000 AND 2000, 'Medium', 'Low')) AS salary_category
FROM 
    Employees;
```


## Topic 11: Handling NULL Values

### IS NULL/ IS NOT NULL
- **Description**: Checks if a value is NULL.

```sql
  SELECT * FROM orders
  WHERE Paid IS NULL;
```

### COALESCE(column, value)

**Description**: Replaces `NULL` values in a column with a specified value. It is equivalent to `fillna(value)` in pandas. Unlike in pandas, COALESCE() should be applied to columns individually.

```sql
SELECT
    COALESCE(category, 'unknown') AS category,
    ROUND(AVG(order_amount), 2) AS avg_order_per_category
FROM
    orders
WHERE
    COALESCE(category, 'unknown') = 'unknown'
GROUP BY
    COALESCE(category, 'unknown');
```
### IFNULL(expression1, expression2) works only for MySQL like COALESCE() 

**Description**: Returns `NULL` if the two expressions are equal; otherwise, returns the either of `expression1 or expression2` whichever is not `NULL`. If both values are not `NULL`, returns first value.

```sql
SELECT id, name, IFNULL(bonus, 0) AS bonus
FROM employees;
```

### NULLIF(expression1, expression2)

**Description**: Returns `NULL` if the two expressions are equal; otherwise, returns the `first expression`.

```sql
SELECT some_value / NULLIF(another_value, 0) AS result
FROM some_table;
```
If the `another_value is zero`, it returns `NULL` else returns `another_value`.

## Topic 12: DISTINCT CLAUSE

### Use DISTINCT When
1. Need to remove duplicate rows, select unique values, or count unique entries.
2. Optimize your use of DISTINCT to ensure efficient queries and accurate results.

## Avoid DISTINCT When
1. It is unnecessary, could impact performance negatively, or when the data is already unique.

## DON'T Dos
<span style="color:red">** SELECT column1, DISTINCT column2 FROM table;**</span>

## Slecting unique combination of two columns
Let’s say you have a table `employees` with columns `department` and `job_title`. You want to `find unique combinations of departments and job titles`.

```sql
SELECT DISTINCT department, job_title
FROM employees;
```


## Examples
###  Count Distinct Values
```sql
SELECT COUNT(DISTINCT product) AS unique_products
FROM sales;
```

Note that aggregate functions `MIN()`, `MAX()` return multiple values if there are multiple minimum, maximum and if we want unique value then we should use `DISTINCT` with `MIN()` and `MAX()`.

```sql
SELECT 
    product,
    MAX(DISTINCT sales_amount) AS max_sales_amount,
    MIN(DISTINCT sales_amount) AS min_sales_amount
FROM 
    sales
GROUP BY 
    product;
```

## Topic 13: SQL Logical Operators

- **AND**
  - **Description**: Returns TRUE if all the conditions separated by AND are TRUE.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE department = 'Sales' AND salary > 50000;
    ```

- **OR**
  - **Description**: Returns TRUE if any of the conditions separated by OR are TRUE.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE department = 'Sales' OR department = 'Marketing';
    ```

- **NOT**
  - **Description**: Reverses the value of any other Boolean operator. Returns TRUE if the condition is FALSE.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE NOT (department = 'Sales');
    ```

- **IN**
  - **Description**: Returns TRUE if the operand is equal to one of a list of expressions.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE department IN ('Sales', 'Marketing', 'HR');
    ```

- **BETWEEN**
  - **Description**: Returns TRUE if the operand is within a range of comparisons.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE salary BETWEEN 40000 AND 60000;
    ```

- **LIKE**
  - **Description**: Returns TRUE if the operand matches a pattern.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE employee_name LIKE 'J%';
    ```

- **EXISTS**
  - **Description**: Returns TRUE if the subquery returns one or more records.
  - **Example**:
    ```sql
    SELECT * FROM departments
    WHERE EXISTS (SELECT * FROM employees WHERE employees.department_id = departments.id);
    ```

### These are only for PostgreSQL.

- **ALL**
  - **Description**: Returns TRUE if all of a set of comparisons are TRUE.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE salary > ALL (SELECT salary FROM employees WHERE department = 'HR');
    ```

- **ANY**
  - **Description**: Returns TRUE if any one of a set of comparisons are TRUE.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE salary > ANY (SELECT salary FROM employees WHERE department = 'HR');
    ```

- **SOME**
  - **Description**: Returns TRUE if some of a set of comparisons are TRUE. It is synonymous with ANY.
  - **Example**:
    ```sql
    SELECT * FROM employees
    WHERE salary > SOME (SELECT salary FROM employees WHERE department = 'HR');
    ```


## Additional Notes for PostgreSQL

## FILTER() Clause

- **FILTER** is always used with aggregate functions (with or without `GROUP BY`).
- **Syntax**:
```sql
AGGREGATE_FUNCTION(expression) FILTER (WHERE condition)
```
```sql
SELECT
    AVG(CASE WHEN product = 'Widget' THEN 1 ELSE 0 END) AS widget_fraction
FROM 
    sales;
```

## Calculate Aggregate on Some Other Column Based on Category Column [Calculates conditional aggregates]

```sql
SELECT
    SUM(amount) AS total_amount,
    SUM(amount) FILTER (WHERE product = 'Widget') AS widget_amount
FROM 
    sales;
```

After reviewing the SQL concepts, we are now ready to tackle real-world problems with confidence and skill. Lets solve some problems in Leetcode. 

- **Take 30 Seconds to Read the Question** : Carefully read the problem statement to understand what is being asked. Pay attention to the details and any specific requirements.

- **Examine the Desired Output**: Look at the example output provided. This will give you a clear idea of what your query needs to achieve. I always find it helpful to look at the exaplanation of the example output provided.

- **Write a Thought Process using pseudo code**: Based on the question and the desired output, plan your approach. Think about which SQL clauses and functions you’ll need to use.

- **Try Running Each Step**: If the problem is complex, break it into smaller parts and run each part to see if it gives you the intended result.

**Please note that SQL is case insensitive and no indentation is needed. I prefer to use all capital letters for SQL keywords to keep the code neat and more readable**.

# Easy Questions

[1757. Recyclable and Low Fat Products](https://leetcode.com/problems/recyclable-and-low-fat-products/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to `select` product for only rows `where` low_fats is 'Y' (Yes) and recylable is 'Y' (Yes).

```sql
SELECT product_id
FROM products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```

[595. Big Countries](https://leetcode.com/problems/big-countries/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to `seelct` the columns `name`, `population` and `area` and only rows `where` a country has an area of at least three million (i.e., 3000000 km2), or a population of at least twenty-five million (i.e., 25000000).

```sql
SELECT name, population, area
FROM world
WHERE area >= 3000000 OR population >= 25000000;
```

[1148. Article Views](https://leetcode.com/problems/article-views-i/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Since author_id and viewer_id indicate the same person, we can simply `seelct` rows `where` viewer_id = author_id. Since an author may have viewed their own article more than once, we want to return only `distinct` author_id. Notice the output table has column name `id`, we should `select` author_id values as `id` and order the result by `id` in ascending order.

```sql
SELECT DISTINCT author_id AS id
FROM views
WHERE author_id = viewer_id
ORDER BY author_id; -- ASC is default, try `ORDER BY id` and ask yourself why it works
```

[1683. Invalid Tweets](https://leetcode.com/problems/invalid-tweets/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to `select` only rows for tweet_id `where` the length of characters is greater than 15.

```sql
SELECT tweet_id
FROM Tweets
WHERE CHARACTER_LENGTH(content) > 15; -- count white spaces as well
```

[584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to `select` only rows for column name `where` referee_id is not 2. Note if referee_id is `NULL`, we need to explicitly check them for `NULL`. To check if it is `NULL`, we use `IS NULL` and `IS NOT NULL`.

```sql
SELECT name
FROM customer
WHERE referee_id != 2 OR referee_id IS NULL;
```

[175. Combine Two Tables](https://leetcode.com/problems/combine-two-tables/description/?envType=problem-list-v2&envId=e55d9ob1)

Thought Process: We do `LEFT JOIN` since we want all data from `Person` table.

```sql
SELECT 
firstName,
lastName, 
city,
state
FROM Person p LEFT JOIN Address a
ON p.personId = a.personId;
```

[182. Duplicate Emails](https://leetcode.com/problems/duplicate-emails/description/?envType=problem-list-v2&envId=e55d9ob1)

Thought Process: If emails are duplicated, we can `GROUP BY` email and count the size of each group then filter only groups whose size is greater than 1 (means email are duplicated).

```sql
SELECT Email
FROM Person
GROUP BY email
HAVING COUNT(*) > 1;
```

[1378. Replace Employee ID with the Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Since we want column `unique_id` from table `EmployeeUNI` and column `name` from table `Employees`. That means we have to `JOIN` these two tables. What kind of `JOIN`?. One hint is the output table contains `NULL` unique_id after `JOIN`, that does not happen in `INNER JOIN` and we want all `name` in `Employees` table in the output. As a rule of thumb, we always do `LEFT JOIN` using bigger table (set) on the left side (`Employees`) and smaller table (subset) on the right side (`EmployeeUNI`). From the combined table, we only seelct `unique_id` and `name` columns.

```sql
SELECT unique_id,
name
FROM employees e LEFT JOIN employeeuni eu -- short names for table moving forward
ON e.id = eu.id; -- we used short names for table so we dont have to type long name
```


[1068. Product Sales Analysis I](https://leetcode.com/problems/product-sales-analysis-i/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Since we only want products that are sold (not all products in product table might have been sold). That means we want common product_id in both tables meaning we perform `INNER JOIN` using column `product_id`. Please remember, when we JOIN using `ON` it keeps `product_id` from both tables. 

**Note**: The notation like `p.product_name` must be used **if** both the table contain same column `product_name` and we want to specify which table the column `product` comes from. Otherwise, it **results a Runtime Error** saying `Column 'product_name' in field list is ambiguous`. In our problem below, `p.product_name` is optional as `product_name` is only in `Product` table.

```sql
SELECT p.product_name, s.year, s.price FROM Sales s
JOIN Product p WHERE p.product_id = s.product_id;
```

[1581. Customer Who Visited but Did Not Make Any Transactions](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: To find the number of visits without transactions for each customer `(GROUP BY customer_id)`, we use a `LEFT JOIN` to combine the `visits` and `transactions` tables on `visit_id`, ensuring all visits are included: Same idea, bigger table on left and smaller on right and we are looking for `NULL` transaction values for `no transactions` during a visit. We then filter for rows where transaction_id is `NULL`, indicating no transactions occurred. Finally, we `group` the results by `customer_id` and `count` the number of such visits for each customer. We can only `select` column thats in group by clause and we must use aggregate, count here, whenever we use group by.

```sql
SELECT customer_id, COUNT(*) AS count_no_trans FROM visits
LEFT JOIN transactions
ON visits.visit_id = transactions.visit_id
WHERE transaction_id IS NULL
GROUP BY customer_id;
```

[1587. Bank Account Summary II](https://leetcode.com/problems/bank-account-summary-ii/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: Please explain your thought process on why the following code works.

```sql
SELECT name,
SUM(amount) AS balance
FROM users JOIN transactions USING (account)
GROUP BY account
HAVING SUM(amount) > 10000;
```

[1965. Employees With Missing Information](https://leetcode.com/problems/employees-with-missing-information/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: We have two tables, each containing an `employee_id` column and one unique column. By examining the output example, we see that the goal is to identify `employee_id`s present in one table but not the other, and then use the `UNION` operator to combine these results for the final output.

Question: Can you explain what happens when we replace `NOT EXISIS` with `EXISTS` and 
`s.employee_id = e.employee_id` to `s.employee_id != e.employee_id` in second query? This will help you understand how `EXISTS` and `NOT EXISTS` work.

```sql
SELECT employee_id FROM
Employees 
WHERE employee_id NOT IN (SELECT employee_id FROM
Salaries)
UNION
SELECT employee_id FROM
Salaries 
WHERE employee_id NOT IN (SELECT employee_id FROM
Employees)
ORDER BY employee_id;
---------------------------------------OR------------------------------------------
SELECT employee_id 
FROM Employees e
WHERE NOT EXISTS (
    SELECT 1 
    FROM Salaries s 
    WHERE s.employee_id = e.employee_id -- each s.employee_id is compared to current e.employee_id until we return True or exhaust the s.employee_id values
)
UNION
SELECT employee_id 
FROM Salaries s
WHERE NOT EXISTS (
    SELECT 1 
    FROM Employees e
    WHERE e.employee_id = s.employee_id
)
ORDER BY employee_id;
---------------------------------------OR------------------------------------------
-- This gives employeed id where info are missing on left join
SELECT employee_id
FROM employees e
LEFT JOIN salaries s
USING(employee_id) -- removes the employee id from salaries
WHERE e.name IS NULL OR s.salary IS NULL
-- This gives employee id where info are missing on right join
UNION
SELECT employee_id
FROM employees e
RIGHT JOIN salaries s
USING(employee_id) -- removes employee id from employees
WHERE e.name IS NULL OR s.salary IS NULL
ORDER BY employee_id;
```

[197. Rising Temperature](https://leetcode.com/problems/rising-temperature/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please remember **if you want to combine information from two different rows of the same table into a single row with different columns, you can use a self join**. For this problem, simply check if a row exists where today's temperature is greater than yesterday's temperature, which can be done by using record date condition. Its always a better idea to use date function whenever dealing with date time data type: if there are missing records for certain dates, the query might fail to find a match. For example, **if there is no record for yesterday.recorddate + 1, the subquery will not return any rows, and the EXISTS condition will fail**.

```sql
SELECT today.id FROM weather today
WHERE EXISTS (
    SELECT 1 FROM weather yesterday
    WHERE DATE_ADD(yesterday.recorddate, INTERVAL 1  DAY) = today.recorddate -- aligns today and yesterday in same row
    AND yesterday.temperature < today.temperature -- make a direct comparison
);
-------------------------*****OR****-------------------------
SELECT today.id 
FROM weather AS today
JOIN weather AS yesterday
ON today.recordDate = yesterday.recordDate + INTERVAL 1 DAY
WHERE today.temperature > yesterday.temperature;
```

[1661. Average Time of Process per Machine](https://leetcode.com/problems/average-time-of-process-per-machine/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Like in problem 197 above, to combine values from two different rows into a single row with different columns, you can use a self join. For example, we want to display the `activity_type start` in one column and `end` in another column for each `machine_id` and `process_id`, we can achieve this with a self join. Remember, we can JOIN tables `USING(col_name)` if the column names on which we join tables are same, its an alternative to using `ON`.

```sql
SELECT machine_id, ROUND(AVG(a2.timestamp - a1.timestamp), 3) AS processing_time
FROM activity a1 JOIN activity a2 USING(machine_id, process_id)
-- You cannot use AND clause with USING(), use WHERE instead
WHERE a1.activity_type = 'start' AND a2.activity_type = 'end'
GROUP BY machine_id;
```

[577. Employee Bonus](https://leetcode.com/problems/employee-bonus/?envType=study-plan-v2&envId=top-sql-50)


Thought Process: We want to `select` columns `name` and `bonus` of employees from the employee table, including those who may not have a corresponding entry in the bonus table. To achieve this, a `LEFT JOIN `is used on the `empid column`, ensuring all employees are included in the result set, even if they don’t have a bonus. The `WHERE` clause filters the results to include only those employees whose bonus is less than 1000 or who do not have a bonus entry at all (NULL). This ensures that we capture employees with low bonuses or no bonuses in the final output.
```sql
SELECT name, bonus
FROM employee LEFT JOIN bonus
USING(empid)
WHERE (bonus < 1000) OR (bonus IS NULL);
```

[1280. Students and Examinations](https://leetcode.com/problems/students-and-examinations/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Since we want all subjects and all students combinations, whether they are in the `examination` table or not, first we need to generate all possible combinations of `students and subjects` using `CROSS JOIN`. This gives a table with students and three subjects each for all students to take an exam for. After that, we want all students and all subjects with how many times the exams were taken. That means we need to `LEFT JOIN` these two tables using `student_id` and `subject_name`, where we `COUNT()` the non-NULL `student_id` in the `examination` table but group by `student_id` in the `students` table and such.

```sql
SELECT s.student_id, s.student_name, sub.subject_name, 
COALESCE(COUNT(e.student_id), 0) AS attended_exams
FROM students s CROSS JOIN subjects sub
LEFT JOIN examinations e ON s.student_id = e.student_id AND sub.subject_name = e.subject_name
GROUP BY s.student_id, s.student_name, sub.subject_name
ORDER BY s.student_id, sub.subject_name;
```

[1251. Average Selling Price](https://leetcode.com/problems/average-selling-price/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process:

- **LEFT JOIN** two tables to ensure that if an item is in the prices table but not in the units sold table, the average price will be zero.
- Select only products where the purchase date is between the start and end price.
- Make sure to sum the multiplication of price and unit, then divide by the sum of units.

```sql
SELECT p.product_id, COALESCE(ROUND(SUM(price * units) * 1.0/SUM(units), 2), 0) AS average_price FROM
prices p LEFT JOIN unitssold u USING(product_id)
WHERE (purchase_date BETWEEN start_date AND end_date) OR (purchase_date IS NULL)
GROUP BY p.product_id;
```

[1075. Project Employees I](https://leetcode.com/problems/project-employees-i/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT project_id, ROUND(AVG(experience_years), 2) AS average_years
FROM project JOIN employee USING(employee_id)
GROUP BY project_id;
```

[1633. Percentage of Users Attended a Contest](https://leetcode.com/problems/percentage-of-users-attended-a-contest/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT contest_id, ROUND(COUNT(*) * 100.0/(SELECT COUNT(user_id) FROM users), 2) AS percentage
FROM register
GROUP BY contest_id
ORDER BY percentage DESC, contest_id ASC;
```

[1211. Queries Quality and Percentage](https://leetcode.com/problems/queries-quality-and-percentage/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT query_name, 
       ROUND(AVG(rating * 1.0 / position), 2) AS quality,
       ROUND(AVG(CASE WHEN rating < 3 THEN 1 ELSE 0 END) * 100.0, 2) AS poor_query_percentage
FROM queries
WHERE query_name IS NOT NULL
GROUP BY query_name;
```

[2356. Number of Unique Subjects Taught by Each Teacher](https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT teacher_id, COUNT(DISTINCT subject_id) AS cnt
FROM teacher
GROUP BY teacher_id;
```

[1141. User Activity for the Past 30 Days I](https://leetcode.com/problems/user-activity-for-the-past-30-days-i/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT activity_date AS day , COUNT(DISTINCT user_id) AS active_users FROM
activity
WHERE activity_date BETWEEN '2019-07-27' - INTERVAL '29 DAYS' AND
'2019-07-27' AND activity_type IS NOT NULL
GROUP BY activity_date;
```

[596. Classes More Than 5 Students](https://leetcode.com/problems/classes-more-than-5-students/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT class
FROM courses
GROUP BY class
HAVING COUNT(*) >= 5;
```

[1729. Find Followers Count](https://leetcode.com/problems/find-followers-count/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.

```sql
SELECT user_id,
COUNT(*) AS followers_count
FROM followers
GROUP BY user_id
ORDER BY user_id;
```

[619. Biggest Single Number](https://leetcode.com/problems/biggest-single-number/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT MAX(num) AS num FROM (
SELECT num FROM
mynumbers 
GROUP BY(num)
HAVING COUNT(*) = 1
) AS temp_table; -- MySQL must have a derived table name unlike in PostgreSQL
----------------------------------OR--------------------------------
WITH unique_num AS (
    SELECT num
    FROM mynumbers
    GROUP BY num
    HAVING COUNT(num) = 1
)
SELECT MAX(num) AS num
FROM unique_num;
```

[1731. The Number of Employees Which Report to Each Employee](https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.

**Note:  Make sure the order is employee_id = e.reports_to not e.reports_to = employee_id which violates sql subquery correlation**.

```sql
SELECT e.reports_to AS employee_id,
(SELECT name FROM employees WHERE employee_id = e.reports_to),
COUNT(*) AS reports_count,
ROUND(AVG(e.age)) AS average_age
FROM employees e
WHERE e.reports_to IS NOT NULL
GROUP BY e.reports_to
ORDER BY e.reports_to;
```

[1789. Primary Department for Each Employee](https://leetcode.com/problems/primary-department-for-each-employee/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We can simply find employees with only one department and `UNION` that with the employees with more than one department where 'Y' means primary department. If an employee has more than two departments and all have primary_flag 'N', they are omitted.

```sql
SELECT employee_id, department_id
FROM employee
WHERE employee_id IN (SELECT employee_id
                      FROM Employee e1
                      GROUP BY employee_id
                      HAVING COUNT(employee_id) = 1)
   OR primary_flag = 'Y'
-----------------------------OR--------------------------
SELECT employee_id, MIN(department_id) AS department_id
FROM employee
GROUP BY employee_id
HAVING COUNT(*) = 1
UNION
SELECT employee_id, department_id FROM employee WHERE primary_flag = 'Y';
```

[610. Triangle Judgement](https://leetcode.com/problems/triangle-judgement/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: For a valid triangle, the sum of two sides must greater than the third side.

```sql
SELECT x, y, z,
CASE WHEN (x + y) > z AND (y + z) > x AND (z + x) > y THEN 'Yes' ELSE 'No' END AS triangle
FROM triangle;
```

[1978. Employees Whose Manager Left the Company](https://leetcode.com/problems/employees-whose-manager-left-the-company/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT employee_id FROM employees
WHERE salary < 30000
AND
manager_id NOT IN
(SELECT employee_id FROM employees)
ORDER BY employee_id;
```

[1667. Fix Names in a Table](https://leetcode.com/problems/fix-names-in-a-table/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.

Note: For PostgreSQL, you can just use `INITCAP()`.

```sql
SELECT user_id,
CONCAT(UPPER(LEFT(name, 1)), LOWER(SUBSTR(name, 2))) AS name
FROM Users
ORDER BY user_id;
```

[1527. Patients With a Condition](https://leetcode.com/problems/patients-with-a-condition/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT * FROM patients
WHERE conditions LIKE '% DIAB1%' OR conditions LIKE 'DIAB1%';
```

[196. Delete Duplicate Emails](https://leetcode.com/problems/delete-duplicate-emails/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.
```sql
DELETE p2 
FROM person p1
JOIN person p2 
ON p1.email = p2.email 
AND p1.id < p2.id;
```

[1484. Group Sold Products By The Date](https://leetcode.com/problems/group-sold-products-by-the-date/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Replace the `STRING_AGG()` function used in PostgreSQL with the `GROUP_CONCAT()` function in MySQL. Its like other aggregate functions but for strings. The default separator is comma.

```sql
SELECT sell_date,
COUNT(DISTINCT product) AS num_sold,
GROUP_CONCAT(DISTINCT product ORDER BY product SEPARATOR ',') AS products
FROM activities
GROUP BY sell_date
ORDER BY sell_date;
```

[1327. List the Products Ordered in a Period](https://leetcode.com/problems/list-the-products-ordered-in-a-period/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Please explain your thought process on why the following code works.

```sql
WITH filtered_order AS (
    SELECT * FROM orders
    WHERE order_date BETWEEN '2020-02-01' AND '2020-02-29'
)

SELECT p.product_name, SUM(o.unit) AS unit
FROM filtered_order o JOIN products p USING(product_id)
GROUP BY p.product_name
HAVING SUM(o.unit) >= 100;
```

[1517. Find Users With Valid E-Mails](https://leetcode.com/problems/find-users-with-valid-e-mails/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: The mail column is checked against a regular expression pattern using the REGEXP keyword. In PostgreSQL, replace REGEX by `~` and double backslash (`\\`) by single backslash (`\`).
- ^[a-zA-Z]+: Ensures the email starts (^) with one or more alphabetic characters.
- [a-zA-Z0-9_.-]*: Allows for any combination of alphanumeric characters, underscores, dots, and hyphens.
- @leetcode\\.com$: Ensures the email ends ($) with @leetcode.com. The backslash (\\) is used to escape the dot (.) character.

```sql
SELECT * FROM Users
WHERE mail REGEXP '^[a-zA-Z]+[a-zA-Z0-9_.-]*@leetcode\\.com$';
```

[586. Customer Placing the Largest Number of Orders](https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: Please explain your thought process on why the following code works.
```sql
SELECT customer_number
FROM Orders
GROUP BY customer_number
ORDER BY COUNT(customer_number) DESC
LIMIT 1;
```

[607. Sales Person](https://leetcode.com/problems/sales-person/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: It is simply asking find all sales person who did not
make any order to company 'RED'. There might be sales person who
might not have made any orders, it makes sense to use left(right) join
to get all sales person who either made no order or made orders from some other company than the 'RED'. Just join all these tables and find names of sales person where company is not 'RED'

```sql
SELECT s.name
FROM SalesPerson s
WHERE s.name NOT IN
(SELECT s.name
    FROM SalesPerson s
        LEFT JOIN Orders o ON s.sales_id = o.sales_id
        LEFT JOIN Company c ON o.com_id = c.com_id
WHERE c.name = 'Red')
```

[1741. Find Total Time Spent by Each Employee](https://leetcode.com/problems/find-total-time-spent-by-each-employee/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: We want to find total time in minutes spent by each employee on each day at the office. In SQL language, its saying please `GROUP BY` event_day, emp_id and sum the total time (out_time - in_time).

```sql
SELECT event_day AS day,
emp_id,
SUM(out_time - in_time) AS total_time
FROM Employees
GROUP BY emp_id, event_day;
```

[1873. Calculate Special Bonus](https://leetcode.com/problems/calculate-special-bonus/description/?envType=problem-list-v2&envId=e97a9e5m)

Tips: Notice how we can replace `[NOT] LIKE` with `[NOT] REGEXP` with regular expression to filter out rows. In PostgreSQL, just replace `REGEXP` by `~`.

```sql
SELECT employee_id,
    CASE 
    WHEN employee_id % 2 = 1 AND name NOT REGEXP '^M' THEN salary ELSE 0
    END AS  bonus
FROM Employees
ORDER BY employee_id
;
```

[1050. Actors and Directors Who Cooperated At Least Three Times](https://leetcode.com/problems/actors-and-directors-who-cooperated-at-least-three-times/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: Please explain your thought process on why the following code works.

```sql
SELECT actor_id, director_id
FROM actordirector
GROUP BY actor_id, director_id
HAVING count(*)  >= 3;
```





# Medium Questions

[570. Managers with at least 5 Direct Reporters](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to identify managers who have at least 5 direct reports. To achieve this, we first create a Common Table Expression (CTE) named `report_counts` that selects `managerid` and counts the number of employees (`n_reporters`) reporting to each manager. We filter out rows where `managerid` is `NULL` and group the results by `managerid`. The `HAVING` clause ensures that only managers with 5 or more direct reports are included.

Next, we select the `name` of employees from the `employee` table who are managers with at least 5 direct reports. This is done by performing an `INNER JOIN` between the `employee` table and the `report_counts` CTE on the `id` column of the `employee` table and the `managerid` column of the `report_counts` CTE.

```sql
WITH report_counts AS (
    SELECT managerid, COUNT(managerid) as n_reporters
    FROM employee
    WHERE managerid IS NOT NULL
    GROUP BY managerid
    HAVING COUNT(managerid) >= 5
)

SELECT e.name
FROM employee e
INNER JOIN report_counts rc 
ON e.id = rc.managerid;  
```

[1934. Confirmation Rate](https://leetcode.com/problems/confirmation-rate/?envType=study-plan-v2&envId=top-sql-50)


**Thought Process**: Let’s break down the thought process into smaller, more detailed steps. This will help in solving similar problems in the future. Since we want to calculate the confirmation rate for each user, we need to follow these steps:

1. **Join Tables**: We start by joining the `signups` table with the `confirmations` table using a `LEFT JOIN` on `user_id`. This ensures that we include all users from the `signups` table, even if they don't have any corresponding records in the `confirmations` table.

    ```sql
    FROM signups s 
    LEFT JOIN confirmations c
    ON s.user_id = c.user_id
    ```

2. **Calculate Confirmation Rate**: We need to calculate the confirmation rate for each user. This is done by using the `AVG` function on a `CASE` statement that checks if the `action` is 'confirmed'. If it is, we return 1; otherwise, we return 0. This counts the number of 'confirmed' actions and divides by the total number of actions for each user.

    ```sql
    ROUND(AVG(CASE WHEN action = 'confirmed' THEN 1 ELSE 0 END), 2) AS confirmation_rate
    ```

3. **Group By User ID**: Finally, we group the results by `user_id` to calculate the confirmation rate for each user individually.

    ```sql
    GROUP BY user_id
    ```

Putting it all together, the complete query looks like this:

```sql
SELECT s.user_id, 
ROUND(AVG(CASE WHEN action = 'confirmed' THEN 1 ELSE 0 END), 2) AS confirmation_rate
FROM signups s 
LEFT JOIN confirmations c
ON s.user_id = c.user_id
GROUP BY user_id;
```

[1193. Monthly Transactions I](https://leetcode.com/problems/monthly-transactions-i/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to aggregate transaction data by month and country. To achieve this, we use the `DATE_FORMAT` function to format the transaction date into a year-month format (%Y-%m). We then utilize the `COALESCE` function to handle any null values, ensuring that counts and sums default to zero when no data is present. The COUNT and SUM functions, combined with conditional logic, allow us to differentiate between all transactions and those specifically approved. The `GROUP BY` clause organizes the results by month and country, providing a detailed breakdown of transaction metrics over time and across different regions.

```sql
SELECT 
    DATE_FORMAT(trans_date, '%Y-%m') AS month, -- %m means two digits month
    country,
    COALESCE(COUNT(state), 0) AS trans_count,
    COALESCE(COUNT(CASE WHEN state = 'approved' THEN 1 END), 0) AS approved_count,
    COALESCE(SUM(amount), 0) AS trans_total_amount,
    COALESCE(SUM(CASE WHEN state = 'approved' THEN amount END), 0) AS approved_total_amount
FROM 
    transactions
GROUP BY 
    MONTH(trans_date), 
    country;
```

[1174. Immediate Food Delivery II](https://leetcode.com/problems/immediate-food-delivery-ii/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to calculate the percentage of deliveries made on the customer’s preferred delivery date for their first order. To achieve this, we first create a `Common Table Expression (CTE) named first_order` that selects the customer_id and the earliest order_date (i.e., the first order date) for each customer. This is done using the `MIN` function and grouping by customer_id.

Next, we calculate the percentage of deliveries that match the customer’s preferred delivery date. We perform an `INNER JOIN` between the delivery table and the `first_order CTE` on both the order_date and customer_id columns. The `CASE` statement checks if the order_date matches the customer_pref_delivery_date, assigning a value of 1 if true and 0 otherwise. We then use the `AVG` function to compute the average of these values, multiply by 100 to get a percentage, and round the result to two decimal places.

```sql
WITH first_order AS (
    SELECT customer_id, min(order_date) as first_order_date
    FROM delivery
    GROUP BY customer_id
)
SELECT
ROUND(AVG(CASE WHEN d.order_date = d.customer_pref_delivery_date THEN 1 ELSE 0 END) * 100, 2) AS immediate_percentage
FROM delivery d
INNER JOIN first_order f ON d.order_date = f.first_order_date AND d.customer_id = f.customer_id;
```

[550. Game Play Analysis IV](https://leetcode.com/problems/game-play-analysis-iv/?envType=study-plan-v2&envId=top-sql-50)

Thought Process:  We want to calculate the fraction of players who return exactly one day after their first recorded activity. To achieve this, we first create a `Common Table Expression (CTE)` named `delta_log` that calculates the difference in days (delta_date) between each event_date and the first event_date for each player. This is done using the `DATEDIFF` function and the `FIRST_VALUE` window function, partitioned by player_id and ordered by event_date.

Next, we calculate the fraction of players who return exactly one day after their first activity. We do this by counting the number of records in delta_log where delta_date equals 1 and dividing it by the total number of distinct players in the activity table. The result is then rounded to two decimal places using the `ROUND` function. 

```sql
WITH delta_log AS (
    SELECT player_id,
           DATEDIFF(event_date, FIRST_VALUE(event_date) OVER (PARTITION BY player_id ORDER BY event_date)) AS delta_date
    FROM activity
)
SELECT ROUND(
    (SELECT COUNT(*) FROM delta_log WHERE delta_date = 1) * 1.0 / (SELECT COUNT(DISTINCT player_id) FROM activity), 2
) AS fraction;
```

[1070. Product Sales Analysis III](https://leetcode.com/problems/product-sales-analysis-iii/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We aim to retrieve product details along with the first year of sales, quantity sold, and price for each product. To achieve this, we perform a `LEFT JOIN` between the `product` table (`p`) and the `sales` table (`s`) on the `product_id` column. This ensures that all products are included, even if they have no sales records.

We use a subquery to find the earliest year (`MIN(year)`) for each product in the `sales` table, grouping by `product_id`. The `WHERE` clause ensures that only the records corresponding to the first year of sales for each product are included.

The `COALESCE` function is used to handle any null values, defaulting to zero for the `year`, `quantity`, and `price` columns. This ensures that products without sales records still appear in the result set with default values. 

```sql
SELECT p.product_id,
	COALESCE(year, 0) AS first_year,
	COALESCE(quantity, 0) AS quantity,
    COALESCE(price, 0) AS price
FROM product p LEFT JOIN sales s 
ON p.product_id = s.product_id
WHERE (s.product_id, s.year) IN
(SELECT product_id, MIN(year)
FROM sales GROUP BY product_id);
```

[1045. Customers Who Bought all Products](https://leetcode.com/problems/customers-who-bought-all-products/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to identify customers who have purchased every product available. To achieve this, we group the `customer` table by `customer_id` to aggregate data for each customer. The `HAVING` clause is used to filter the grouped results, ensuring that only customers who have purchased a distinct count of products equal to the total number of products in the `product` table are included.

The subquery `(SELECT COUNT(*) FROM product)` calculates the total number of distinct products available. The `COUNT(DISTINCT product_key)` function within the `HAVING` clause counts the number of unique products each customer has purchased. By comparing these two values, we ensure that only customers who have purchased every product are selected. The final query returns the `customer_id` of these customers.

```sql
SELECT customer_id
FROM customer 
GROUP BY customer_id
HAVING COUNT(DISTINCT product_key) = (SELECT COUNT(*) FROM product);
```

[180. Consecutive Numbers](https://leetcode.com/problems/consecutive-numbers/description/?envType=study-plan-v2&envId=top-sql-50)

First, please try running this. It should give you an idea about how self-jopin allows you to get different rows data from original table into same row but different columns.

```sql
SELECT l1.id as l1_id, l2.id as l2_id, l3.id as l3_id, 
l1.num as l1_num, l2.num as l2_num, l3.num as l3_num
FROM logs l1
JOIN logs l2
ON l1.id = l2.id + 1
JOIN logs l3
ON l1.id = l3.id + 2;
```

**Thought Process:** We want to identify sequences of three consecutive rows in the `logs` table where the `num` values are the same. To achieve this, we use self-joins to compare different rows within the same table.

1. **Self-Join Setup:** We perform two self-joins on the `logs` table:
   - The first join (`l1` to `l2`) matches rows where the `id` of `l1` is one greater than the `id` of `l2` (`l1.id = l2.id + 1`).
   - The second join (`l1` to `l3`) matches rows where the `id` of `l1` is two greater than the `id` of `l3` (`l1.id = l3.id + 2`).

2. **Filtering for Consecutive Numbers:** The `WHERE` clause ensures that the `num` values in the joined rows are the same (`l1.num = l2.num AND l2.num = l3.num`). This condition filters the results to only include sequences where three consecutive rows have the same `num` value.

3. **Selecting Distinct Values:** The `SELECT DISTINCT` statement ensures that each sequence of three consecutive rows with the same `num` value is included only once in the result set.

```sql
SELECT DISTINCT l1.num AS ConsecutiveNums
FROM logs l1
JOIN logs l2
ON l1.id = l2.id + 1
JOIN logs l3
ON l1.id = l3.id + 2
WHERE l1.num = l2.num AND l2.num = l3.num;
----------------OR---------------------------------
WITH consecutive_logs AS (
    SELECT 
        num,
        LAG(num, 1) OVER (ORDER BY id) AS prev_num1,
        LAG(num, 2) OVER (ORDER BY id) AS prev_num2
    FROM logs
)
SELECT DISTINCT num AS ConsecutiveNums
FROM consecutive_logs
WHERE num = prev_num1 AND num = prev_num2;
```

[1164. Product Price at a given Date](https://leetcode.com/problems/product-price-at-a-given-date/?envType=study-plan-v2&envId=top-sql-50)

**Thought Process:** We want to keep only the latest price of each product as of a specific date (`2019-08-16`). If a product has no price change recorded before this date, we assign a `default price of 10`. To achieve this, we use a `Common Table Expression (CTE)` and a combination of `INNER JOIN` and `UNION` operations.

1. **Store result in  a CTE:** We create a CTE named `priced_changed_before` that selects the `product_id` and the latest `change_date` (i.e., the maximum `change_date`) for each product where the `change_date` is on or before `2019-08-16`. This is done using the `MAX` function and grouping by `product_id`.

2. **Joining for Latest Prices:** We perform an `INNER JOIN` between the `priced_changed_before` CTE and the `products` table (`ps`) on both the `product_id` and `change_date` columns. This ensures that we retrieve the latest price (`new_price`) for each product as of `2019-08-16`.

3. **Handling Products Without Price Changes:** We use a `UNION` operation to include products that have no price change recorded before `2019-08-16`. The second part of the `UNION` selects `product_id` and assigns a default price of 10 for products not present in the `priced_changed_before` CTE. This is achieved using a `NOT IN` subquery.


```sql
WITH priced_changed_before AS (
	SELECT product_id, MAX(change_date) AS dates
	FROM products
	WHERE change_date <= '2019-08-16'
	GROUP BY product_id
)

SELECT pcb.product_id, ps.new_price AS price
FROM priced_changed_before pcb INNER JOIN products ps
ON pcb.product_id = ps.product_id AND pcb.dates = ps.change_date
UNION
SELECT product_id, 10 AS price FROM products
WHERE product_id NOT IN (SELECT product_id FROM priced_changed_before);
```

[1204. Last Person to Fit in the Bus](https://leetcode.com/problems/last-person-to-fit-in-the-bus/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to identify the last person who can board the bus without exceeding the weight limit of 1000 kilograms. To achieve this, we will calculate the running sum of weights ordered by the `turn` column and then find the last person whose cumulative weight does not exceed the limit.

1. **Calculate Running Sum:** We create a Common Table Expression (CTE) named `running_totals` that calculates the running sum of weights for each person using the `SUM` function with the `OVER` clause. The `ORDER BY turn` ensures the weights are summed in the order people board the bus.

2. **Filter by Weight Limit:** We filter the results to include only those rows where the running sum is less than or equal to 1000 kilograms.

3. **Select Last Person:** We order the filtered results by `turn` in descending order and use `LIMIT 1` to select the person with the highest `turn` value. This ensures we get the last person who can board the bus without exceeding the weight limit.

```sql
WITH running_totals AS (
    SELECT 
        person_name,
        turn,
        SUM(weight) OVER (ORDER BY turn) AS running_sum
    FROM queue
)

SELECT person_name
FROM running_totals
WHERE running_sum <= 1000
ORDER BY turn DESC
LIMIT 1;
```

[1907. Count Salary Categories](https://leetcode.com/problems/count-salary-categories/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to categorize accounts based on their income into predefined salary categories and count the number of accounts in each category. To ensure that all categories are represented in the final result, `even if some categories are not present in input table`, we use a combination of Common Table Expressions (CTEs) and a `LEFT JOIN`. We need to use `UNION` to count categoroies of each salary to get the result in the desired output format.

1. **Create Salary Categories CTE:** We create a CTE named `salary_categories` that lists all possible salary categories (`Low Salary`, `Average Salary`, and `High Salary`). This will help us ensure that all categories are included in the final result, even if there are no accounts in some categories.

2. **Create Category Counts CTE:** We create another CTE named `category_counts` that counts the number of accounts in each salary category. This is done using `UNION ALL` to combine the results of three separate queries:
   - The first query counts accounts with an income less than 20000 and labels them as `Low Salary`.
   - The second query counts accounts with an income between 20000 and 50000 and labels them as `Average Salary`.
   - The third query counts accounts with an income greater than 50000 and labels them as `High Salary`.

3. **Left Join for Final Result:** We perform a `LEFT JOIN` between the `salary_categories` CTE and the `category_counts` CTE on the `category` column. This ensures that all salary categories are included in the final result, even if some categories have no accounts. The `COALESCE` function is used to replace any null counts with zero, ensuring that categories with no accounts are represented with a count of zero.

```sql
-- Create a CTE with all salary categories
WITH salary_categories AS (
    SELECT 'Low Salary' AS category
    UNION ALL -- UNION works as well
    SELECT 'Average Salary' AS category
    UNION ALL -- UNION works as well
    SELECT 'High Salary' AS category
),

-- Create a CTE with salary category and their counts
category_counts AS (
    SELECT 'Low Salary' AS category,
    COUNT(*) AS accounts_count
    FROM accounts
    WHERE income < 20000
    UNION ALL -- UNION works as well
    SELECT 'Average Salary' AS category,
    COUNT(*) AS accounts_count
    FROM accounts
    WHERE income BETWEEN 20000 AND 50000
    UNION ALL -- UNION works as well
    SELECT 'High Salary' AS category,
    COUNT(*) AS accounts_count
    FROM accounts
    WHERE income > 50000
)

-- Left JOIN these two tables on category for final result
SELECT sc.category, COALESCE(cc.accounts_count, 0) AS accounts_count
FROM salary_categories sc LEFT JOIN category_counts cc
ON sc.category = cc.category;
```

[626. Exchange Seats](https://leetcode.com/problems/exchange-seats/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: Switch id or student and make sure the results are orderd by id.

**Please remember that the `IF` function follows the format `IF(condition, value_if_true, value_if_false)`. For nested `IF` statements, you can place another `IF` function in the `value_if_false` position as many times as needed. For example: `IF(condition1, value_if_true1, IF(condition2, value_if_true2, value_if_false2))`**.
```sql
SELECT 
    IF(id % 2 = 0, id - 1, 
    IF(id % 2 = 1 AND id = (SELECT MAX(id) FROM seat), id, id + 1)) AS id,
    student
FROM seat
ORDER BY id;
---------------------------------OR------------------------------------------------
SELECT 
    CASE 
        WHEN id % 2 = 0 THEN id - 1
        WHEN id % 2 = 1 AND id = (SELECT MAX(id) FROM seat) THEN id
        ELSE id + 1
    END AS id,
    student
FROM seat
ORDER BY id;
---------------------------------OR------------------------------------------------
SELECT
id,
CASE
    WHEN id % 2 = 0 THEN LAG(student, 1) OVER(ORDER BY id)
    -- When LEAD(sudent, 1) results NULL then LAG(student, 1, student)
    -- replaces by student (the case for last student when id is odd)
    WHEN id % 2 = 1 THEN LEAD(student, 1, student) OVER(ORDER BY id)
END AS student
FROM seat;
```

[627. Swap Salary](https://leetcode.com/problems/swap-salary/description/?envType=problem-list-v2&envId=e97a9e5m)

Hint: Swapping values in a table typically requires an `UPDATE` statement since it involves modifying existing data

```sql
UPDATE Salary
SET sex = CASE 
            WHEN sex = 'm' THEN 'f'
            WHEN sex = 'f' THEN 'm'
          END;
```

[1890. The Latest Login in 2020](https://leetcode.com/problems/the-latest-login-in-2020/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: Please explain your thought process on why the following code works.

```sql
SELECT user_id,
MAX(time_stamp) AS last_stamp
FROM logins
WHERE YEAR(time_stamp) = '2020'
GROUP BY user_id;
```

[1341. Movie Rating](https://leetcode.com/problems/movie-rating/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to find the user who has rated the greatest number of movies and the movie with the highest average rating. To achieve this, we will perform the following steps:

1. **Join Users and MovieRating Tables:** First, we join the `Users` and `MovieRating` tables using the `user_id` column. This allows us to access both user names and their corresponding movie ratings.

2. **Group and Order by User Ratings:** We group the results by `name` and order them by the count of ratings in descending order. This helps us identify the user who has rated the most movies. In case of a tie, we order by `name` to get the lexicographically smaller name.

3. **Select Top User:** We select the first row from the grouped and ordered results to get the user with the highest number of ratings.

4. **Group and Order by Movie Ratings:** Similarly, we group the results by `title` and order them by the average rating in descending order. This helps us identify the movie with the highest average rating. In case of a tie, we order by `title` to get the lexicographically smaller title.

5. **Select Top Movie:** We select the first row from the grouped and ordered results to get the movie with the highest average rating.

6. **Union the Results:** Finally, we use a `UNION` operation to combine the results of the top user and the top movie into a single result set.

```sql
(SELECT name AS results FROM 
users JOIN movierating USING(user_id)
GROUP BY name
ORDER BY COUNT(*) DESC, name ASC
LIMIT 1)
UNION ALL
(SELECT title AS results FROM 
movies JOIN movierating USING(movie_id)
WHERE TO_CHAR(created_at, 'YYYY-MM') = '2020-02'
GROUP BY title
ORDER BY AVG(rating) DESC, title ASC
LIMIT 1)
;
```

[1321. Restaurant Growth](https://leetcode.com/problems/restaurant-growth/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: We want to calculate a seven-day moving average of the `amount` column, ensuring that the `visited_on` dates are unique. Additionally, since MySQL does not support the `OFFSET` clause alone, we use a large number in the `LIMIT` clause to retrieve all results from the original table. In reality, we do not have `7 day` moving average of `amount` before the seventh day (**MySQL calculates the sum for the available days rather than returning `NULL` values for days before the 7th day**), so we only retrieve data starting from the seventh day.

1. **Ensure Unique Dates:** We first ensure that the `visited_on` dates are unique by grouping the data by `visited_on` and summing the `amount` for each date. This is done in a subquery, which we name `unique_visited_on`.

2. **Calculate Running Sum and Average:** We use `window functions` to calculate the running sum and the seven-day moving average of the `amount` column. The `SUM` and `AVG` functions, combined with the `OVER` clause, allow us to calculate these values over a window of the current row and the six preceding rows (`ROWS BETWEEN 6 PRECEDING AND CURRENT ROW`). Note if the days were not consecutive, we would have to use `RANGE BETWEEN INTERVAL '6 DAYS' PRECEDING AND CURRENT ROW`.

3. **Handle Non-Supported OFFSET:** Since MySQL does not support the `OFFSET` clause alone, we use a large number in the `LIMIT` clause to ensure we retrieve all results. We use `LIMIT 10000 OFFSET 6` to skip the first six rows, ensuring that we only retrieve data starting from the seventh day.

Here is the SQL query implementing this thought process:

```sql
SELECT 
	visited_on,
    SUM(amount) OVER (ORDER BY visited_on ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS amount,
    ROUND(AVG(amount) OVER (ORDER BY visited_on ROWS BETWEEN 6 PRECEDING AND CURRENT ROW), 2) AS average_amount
FROM 
    (SELECT visited_on, SUM(amount) AS amount
	FROM customer
	GROUP BY visited_on) AS unique_visited_on -- MySQL must have derived table name
ORDER BY unique_visited_on.visited_on
LIMIT 10000 OFFSET 6; --MySQL does not support OFFSET only unlike in PostgreSQL
-----------------------------------------------OR----------------------------------------
SELECT
    c1.visited_on,
    (
        SELECT SUM(c2.amount)
        FROM customer c2
        WHERE c2.visited_on BETWEEN c1.visited_on - INTERVAL 6 DAY AND c1.visited_on
    ) AS amount,
    ROUND(
        (
            SELECT SUM(c2.amount)/7.0
            FROM customer c2
            WHERE c2.visited_on BETWEEN c1.visited_on - INTERVAL 6 DAY AND c1.visited_on
        ),
        2
    ) AS average_amount
FROM customer c1
WHERE c1.visited_on >= (
        SELECT DATE_ADD(MIN(visited_on), INTERVAL 6 DAY)
        FROM customer
    )
GROUP BY c1.visited_on
ORDER BY c1.visited_on;
```

[602. Friend Requests II: Who Has the Most Friends](https://leetcode.com/problems/friend-requests-ii-who-has-the-most-friends/description/?envType=study-plan-v2&envId=top-sql-50)

**Thought Process:** We want to find the user with the highest number of friends, considering both scenarios: when the user sends a friend request and it gets accepted, and when the user receives a friend request and accepts it. To achieve this, we use a combination of `COUNT` functions and a `UNION ALL` (`UNION` might not work correctly when the number of requests a user accepts is equal to the number of requests they receive and get accepted) operation.

1. **Count Requests Sent and Accepted:** 
   - We first count the number of friend requests sent by each user that have been accepted. This is done by selecting the `requester_id` and counting the `accepter_id` using `COUNT(accepter_id)`. This ensures that only accepted requests are counted, only `NOT NULL accepted_id` are counted.

   - We then count the number of friend requests received and accepted by each user. This is done by selecting the `accepter_id` and counting all rows using `COUNT(*)`. This counts all accepted requests, regardless of whether the `accepter_id` is null or not.

2. **Combine Results with UNION ALL:** 
   - We use `UNION ALL` to combine the results of the two counts. This ensures that we include both the counts of requests sent and accepted, and the counts of requests received and accepted.

3. **Aggregate Total Counts:** 
   - We create a Common Table Expression (CTE) named `friends` that combines the results of the two counts. We then select the `id` and sum the counts (`num`) for each user using `SUM(num)`.

   - We group the results by `id` to aggregate the total number of accepted friend requests for each user.

4. **Order and Limit Results:** 
   - We order the results by the total number of accepted friend requests in descending order using `ORDER BY SUM(num) DESC`.

   - We use `LIMIT 1` to select the user with the highest number of accepted friend requests.

```sql
WITH friends AS (
    (SELECT requester_id AS id, COUNT(accepter_id) AS num -- COUNT(*) works as well for this problem
     FROM RequestAccepted
     GROUP BY requester_id)
    UNION ALL
    (SELECT accepter_id AS id, COUNT(*) AS num
     FROM RequestAccepted
     GROUP BY accepter_id)
)

SELECT id, SUM(num) AS num
FROM friends
GROUP BY id
ORDER BY SUM(num) DESC
LIMIT 1;
```

[585. Investment in 2016](https://leetcode.com/problems/investments-in-2016/?envType=study-plan-v2&envId=top-sql-50)

**Thought Process:** We want to calculate the sum of all total investment values in 2016 (`tiv_2016`) for policyholders who meet two specific criteria:
1. They have the same `tiv_2015` value as one or more other policyholders.
2. They are not located in the same city as any other policyholder (i.e., the `(lat, lon)` attribute pairs must be unique).

To achieve this, we follow these steps:

1. **Group Policyholders with Same `tiv_2015`:**
   - We use a subquery to select `tiv_2015` values that appear more than once in the `insurance` table. This is done by grouping the data by `tiv_2015` and using the `HAVING COUNT(*) > 1` clause to filter for non-unique values.

2. **Get (lat, lon) that appear only once:**
   - We use another subquery to select `(lat, lon)` pairs that are unique in the `insurance` table. This is done by grouping the data by `lat` and `lon` and using the `HAVING COUNT(*) = 1` clause to filter for unique locations.

3. **Filter and Sum `tiv_2016`:**
   - We combine the results of the two subqueries in the main query's `WHERE` clause to filter for policyholders who meet both criteria.
   - We then calculate the sum of `tiv_2016` for these filtered policyholders.
   - The `ROUND` function is used to round the sum to two decimal places.

```sql
SELECT ROUND(SUM(tiv_2016), 2) AS tiv_2016
FROM insurance
WHERE
tiv_2015 IN -- For each tiv_2015 check if there are other equal tiv_2015 value
(SELECT tiv_2015
 FROM insurance
 GROUP BY tiv_2015
 HAVING COUNT(*) > 1)
AND       -- For the tiv_2015 row we are at now, check if its (lat, lon) is unique
(lat, lon) IN
(SELECT lat, lon
 FROM insurance
 GROUP BY lat, lon
 HAVING COUNT(*) = 1);
```


[176. Second Highest Salary](https://leetcode.com/problems/second-highest-salary/description/?envType=study-plan-v2&envId=top-sql-50)

Thought Process:

**Initial Approach**

1. **Finding the Second Highest Salary**:
   - To find the second highest salary, we can exclude the highest salary and then find the maximum salary from the remaining records.
   - This approach works well for finding the second highest salary but becomes cumbersome for finding the nth highest salary.
   - It requires nested subqueries and is not efficient for larger datasets.

2. **Using `DENSE_RANK()`**

    a. **Generalizing for nth Highest Salary**:
   - To generalize the approach for any `n`, we can use the `DENSE_RANK()` window function.
   - `DENSE_RANK()` assigns a rank to each row (within the partition of a result set), with no gaps in ranking values.

    b. **Handling Multiple Maximum Salaries**:
   - If there are multiple maximum salaries, `DENSE_RANK()` will assign the same rank to all of them.
   - This means the query will return all rows with the nth highest salary.
   - If a single row is desired, we can use `DISTINCT` to ensure only unique salaries are returned.
   - If there is no `NTH` largest salary, return `NULL` which can be done by checking `IF NTH salary rank EXISTS`.

```sql
SELECT MAX(salary) AS SecondHighestSalary FROM employee
WHERE salary != (SELECT MAX(salary) FROM employee);
----------------------------------------OR-------------------------------------------
WITH RankedSalaries AS (
         SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_salary_rank
         FROM employee
     )

SELECT 
    CASE 
        WHEN EXISTS (SELECT 1 FROM RankedSalaries WHERE dense_salary_rank = 2) 
        THEN (SELECT DISTINCT salary FROM RankedSalaries WHERE dense_salary_rank = 2)
        ELSE NULL 
    END AS SecondHighestSalary;
```

[608. Tree Node](https://leetcode.com/problems/tree-node/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process:
- When `p_id` is `NULL`, it is a root node.
- When `id` is in `p_id`, it means they are parents to some node, so they are `Inner`.
- The remaining nodes are `Leaf`.

**How the Code Captures This Notion ?**

- The `CASE` statement is used to evaluate each node and assign the appropriate classification.
- **Root Node**: 
  - `WHEN p_id IS NULL THEN 'Root'`
  - This condition checks if `p_id` is `NULL` for a given `id`, indicating that the node is a root node.
- **Inner Node**: 
  - `WHEN id IN (SELECT p_id FROM tree) THEN 'Inner'`
  - This condition checks if the `id` of the node appears in the list of `p_id` values from the `tree` table, indicating that the node is a parent to some other node.
- **Leaf Node**: 
  - `ELSE 'Leaf'`
  - If the node is neither a root nor an inner node, it is classified as a leaf node.


```sql
SELECT id, -- this is the current id (row)
    CASE  -- now we ask questions for current id (row)
    WHEN p_id IS NULL THEN 'Root' -- for the current id, is p_id NULL?
    WHEN id IN (SELECT p_id FROM tree) THEN 'Inner' -- If p_id is NOT NULL, then does current id belong in p_id
    ELSE 'Leaf' -- If both of the above conditions are not satisfied, it must be a leaf
    END AS type
FROM tree;
```

[1393. Capital Gain/Loss](https://leetcode.com/problems/capital-gainloss/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: Only idea to focus here is how do we get sell - buy. That is we should make all buys negative and just `SUM`. Group by each stock name and `SUM` using conditional where if it is a buy its negative.

```sql
SELECT 
    stock_name,
    COALESCE(SUM(
        CASE WHEN operation = 'Buy' THEN -price ELSE price END), 0) AS capital_gain_loss
FROM stocks
GROUP BY stock_name;
-------------------------------------OR---------------------------------------------------
SELECT 
    stock_name,
    SUM(
        COALESCE(CASE WHEN operation = 'Buy' THEN -price ELSE 0 END, 0) +   --creates a column for buy
        COALESCE(CASE WHEN operation = 'Sell' THEN price ELSE 0 END, 0) -- creates a column for sell
    ) AS capital_gain_loss
FROM stocks
GROUP BY stock_name;
```

[181. Employees Earning More Than Their Managers](https://leetcode.com/problems/employees-earning-more-than-their-managers/description/)

Hint: Use `SELF JOIN` using employee `id` and `managerID` so we have employee and manager salaries on the same row but different columns. In the following, the columns on the left (e1) will be for managers and on the right (e2) for employees.

```sql
SELECT e2.name AS Employee
FROM Employee e1
JOIN Employee e2
ON e1.id = e2.managerid AND e1.salary < e2.salary;
```

[183. Customers Who Never Order](https://leetcode.com/problems/customers-who-never-order/description/)

```sql
SELECT name AS customers FROM
customers
WHERE id NOT IN(  -- this query is efficient for small data sets
    SELECT customerID
    FROM Orders
);
--------------------------------OR---------------------------
SELECT name AS Customers FROM
Customers c
WHERE NOT EXISTS( --this query is efficient for large data sets
    SELECT 1
    FROM Orders o
    WHERE o.customerID = c.id
);
------------------------------OR--------------------------------
SELECT c.name AS Customers FROM
Customers c
LEFT JOIN Orders o
ON c.id = o.customerID
WHERE o.customerId IS NULL;
```
In 3rd query using `LEFT JOIN`, can we join on  `c.id = o.customerID AND o.customerId IS NULL` to get the desired result? If not, why?

[184. Department Highest Salary](https://leetcode.com/problems/department-highest-salary/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: The idea is to simply `JOIN` the Employee and Department tables and filter only the rows where the employee's department ID and salary match the maximum salary for that department. This is achieved by joining the `Employee` and `Department` tables, using a subquery to find the maximum salary per department, and filtering the results with an `IN` clause to include only the highest paid employees in each department.

```sql
SELECT 
d.name AS Department,
e.name AS Employee,
e.salary AS Salary
FROM Employee e JOIN Department d
ON e.departmentId = d.id
WHERE (e.departmentId, e.salary)
IN (
    SELECT  departmentId, MAX(salary)
    FROM Employee
    GROUP BY departmentId
);
```

[178. Rank Scores](https://leetcode.com/problems/rank-scores/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: This is a standard implementation of `DENSE_RANK()`.

```sql
SELECT
score,
DENSE_RANK() OVER(ORDER BY score DESC) AS rank
FROM scores
ORDER BY score DESC;
```

[1084. Sales Analysis III](https://leetcode.com/problems/sales-analysis-iii/description/?envType=problem-list-v2&envId=e55d9ob1)

Hint: We want to select `product_id` and `product_name` only for those products where the `product_id` from Product is in the Sales table as well where its sold in between '2019-01-01' AND '2019-03-31' and not sold after '2019-03-31'.

```sql
SELECT p.product_id, p.product_name
FROM Product p
JOIN
(SELECT
product_id FROM
Sales s
GROUP BY product_id
HAVING MIN(sale_date) >= '2019-01-01' 
AND MAX(sale_date) <= '2019-03-31')  AS t
ON t.product_id = p.product_id;
```


[1407. Top Travellers](https://leetcode.com/problems/top-travellers/description/?envType=problem-list-v2&envId=e55d9ob1)

Hint: We want LEFT JOIN because want all users from `Users` table even if they have not shared a ride yet, that is, some user from `Users` might not be in `Rides` table. In that case, the travelled_distance is 0.

```sql
SELECT name, COALESCE(SUM(distance), 0) AS travelled_distance FROM
Users u LEFT JOIN Rides r
ON u.id = r.user_id
GROUP BY r.user_id
ORDER BY travelled_distance DESC, u.name ASC;
```

[1795. Rearrange Products Table](https://leetcode.com/problems/rearrange-products-table/description/?envType=problem-list-v2&envId=e55d9ob1)

Hint: Select product_id and each store named store1, store2 and store3 at a time. Introduce new column `store` by giving a constant value of `store?(? = 1, 2, 3)` at a time. Pivot the individually and stack (union) them.

```sql
SELECT product_id, 
'store1' AS store, -- introduce new column 'store' with value 'store1'
store1 AS price
FROM Products
WHERE store1 IS NOT NULL -- We want store1 values are NOT NULL
UNION -- copy and paste above steps for 'store2' and 'store3'
SELECT product_id, 
'store2' AS store, 
store2 AS price
FROM Products
WHERE store2 IS NOT NULL
UNION
SELECT product_id, 
'store3' AS store, 
store3 AS price
FROM Products
WHERE store3 IS NOT NULL; 
```

[1693. Daily Leads and Partners](https://leetcode.com/problems/daily-leads-and-partners/description/?envType=problem-list-v2&envId=e55d9ob1)

Hint: Please read the question, you should be able to translate what is asked into SQL query.

```sql
SELECT date_id,
make_name,
COUNT(DISTINCT lead_id) AS unique_leads,
COUNT(DISTINCT partner_id) AS unique_partners
FROM DailySales
GROUP BY date_id, make_name;
```

# Hard Questions

[185. Department Top three Salaries](https://leetcode.com/problems/department-top-three-salaries/?envType=study-plan-v2&envId=top-sql-50)

Thought Process: [2nd query] The simple approach is to just join the two tables using `departmentid` and `id`. The main problem is selecting the top 3 salaries for each department. For that, we can use a `correlated subquery` where we ask for each row of salary (and same department), is that salary greater than 2 other salaries? If yes, keep that row.

```sql
WITH ranked_salary AS(
SELECT 
	name,
	departmentid, 
	salary,
	DENSE_RANK() OVER(PARTITION BY departmentID ORDER BY salary DESC) AS salary_rank
	FROM employee)

SELECT d.name AS department, rs.name AS employee, salary
FROM ranked_salary rs JOIN department d ON rs.departmentid = d.id
WHERE salary_rank <= 3
ORDER BY salary DESC;
--------------OR-------------------------------------------
SELECT d.name AS Department, e.name AS Employee, e.salary AS Salary
FROM employee e JOIN department d
ON e.departmentid = d.id
WHERE (  -- this is where we use correlated subquery to ask that question
    SELECT COUNT(DISTINCT e1.salary)
    FROM employee e1
    -- subquery values on left and outer query values on the right
    -- thats how correlated subqueries work
    WHERE e1.departmentid = e.departmentid AND e1.salary >= e.salary
) <= 3;
```

[601. Human Traffic of Stadium](https://leetcode.com/problems/human-traffic-of-stadium/)

Thought Process: This is a very interesting problem. We would like to find if the rows are consecutive or not. Since IDs are consecutive but after filtering where only people with IDs greater than 100 are selected, the consecutiveness of IDs might be broken. Now we ask, what are the at least 3 consecutive IDs? 

We can create a `row_number()` field and subtract that from the `id` field. If IDs are consecutive, the difference between `row_number()` and `id` is the same, let's call this `delta_group`. It might be 0, 1, 2, 3, and so on. We group by the `delta_group` and select only those groups of size >= 3. 

**Please sketch the row_number, id and their deltas on a notebook and see for yourself**.

```sql
WITH delta_row_id AS (
    SELECT 
    id,
    visit_date,
    people,
    id - ROW_NUMBER() OVER(ORDER BY id) AS delta_group -- ORDER BY is optional
FROM stadium
WHERE people >= 100)

SELECT id, visit_date, people
FROM delta_row_id
WHERE delta_group IN
(SELECT delta_group FROM delta_row_id -- select those groups
GROUP BY delta_group -- it goes in select
HAVING COUNT(*) >= 3); -- having at least 3 consecutive ids
```

[262. Trips and Users](https://leetcode.com/problems/trips-and-users/description/?envType=problem-list-v2&envId=e97a9e5m)

Thought Process: This problem is much simpler than it looks. Since `user_id` in `Users` corresponds to `driver_id` and `client_id` in `Trips`, we can remove rows from `Trips` where either `client_id` or `driver_id` equals `user_id` in `Users` and they are banned. After filtering those rows, use `NOT EXISTS` which is faster than `NOT IN`.

```sql
SELECT t.request_at AS "Day",
ROUND(AVG(CASE WHEN LOWER(status) LIKE "%cancelled%" THEN 1 ELSE 0 END), 2) AS "Cancellation Rate" 
FROM trips t
WHERE NOT EXISTS(-- either client_id or driver_id matches with users_id
-- and that id is banned
    SELECT 1 FROM users u
    WHERE (u.users_id = t.driver_id OR u.users_id = t.client_id) AND banned = 'Yes'
) AND request_at BETWEEN '2013-10-01' AND '2013-10-03'
GROUP BY request_at;
```
