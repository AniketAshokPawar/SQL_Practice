1\. Find second-highest salary ⭐⭐⭐⭐⭐
================================

```
SELECT MAX(salary) AS second_highest
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**Interview answer:** Find the maximum salary that is less than the overall maximum salary.

* * * * *

2\. Find duplicate records ⭐⭐⭐⭐⭐
================================

```
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

**Interview answer:** Group by the column that should be unique and use `HAVING COUNT(*) > 1`.

* * * * *

3\. Find employees who don't have a department ⭐⭐⭐⭐⭐
====================================================

If `department_id` is `NULL`:

```
SELECT *
FROM employees
WHERE department_id IS NULL;
```

If employees have a department ID but that department doesn't exist in the department table:

```
SELECT e.*
FROM employees e
LEFT JOIN departments d
    ON e.department_id = d.department_id
WHERE d.department_id IS NULL;
```

**Interview point:** `LEFT JOIN` is useful for finding unmatched records.

* * * * *

4\. Find records present in Table A but not Table B ⭐⭐⭐⭐⭐
=========================================================

```
SELECT a.*
FROM table_a a
LEFT JOIN table_b b
    ON a.id = b.id
WHERE b.id IS NULL;
```

**Meaning:** Get everything from A where no matching record exists in B.

* * * * *

5\. Count employees in each department ⭐⭐⭐⭐⭐
============================================

```
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department;
```

Example result:

| department | employee_count |
| --- | --- |
| QA | 5 |
| Dev | 8 |
| HR | 3 |

* * * * *

6\. Find departments having more than 5 employees ⭐⭐⭐⭐⭐
=======================================================

```
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

**Remember:** `HAVING` because we're filtering an aggregate result.

* * * * *

7\. Find the highest salary in each department ⭐⭐⭐⭐⭐
====================================================

```
SELECT department, MAX(salary) AS highest_salary
FROM employees
GROUP BY department;
```

Example:

| department | highest_salary |
| --- | --- |
| QA | 70000 |
| Dev | 90000 |
| HR | 60000 |

* * * * *

8\. Fetch records between two dates ⭐⭐⭐⭐
========================================

```
SELECT *
FROM employees
WHERE joining_date BETWEEN '2026-01-01' AND '2026-03-31';
```

`BETWEEN` is **inclusive** of the boundary values.

* * * * *

9\. Find employees whose name starts with `A` ⭐⭐⭐⭐
==================================================

```
SELECT *
FROM employees
WHERE name LIKE 'A%';
```

`%` means **zero or more characters**.

So this can find:

```
Aniket
Amit
Akash
```

* * * * *

10\. Difference between `WHERE` and `HAVING` ⭐⭐⭐⭐⭐
==================================================

| WHERE | HAVING |
| --- | --- |
| Filters individual rows | Filters groups |
| Used before `GROUP BY` | Used after `GROUP BY` |
| Normally used for normal conditions | Commonly used with aggregate functions |

Example:

```
-- WHERE
SELECT *
FROM employees
WHERE salary > 50000;
```

```
-- HAVING
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

### Interview answer:

> `WHERE` filters rows before grouping, while `HAVING` filters groups after `GROUP BY`.

* * * * *

11\. `INNER JOIN` vs `LEFT JOIN` ⭐⭐⭐⭐⭐
======================================

| INNER JOIN | LEFT JOIN |
| --- | --- |
| Returns only matching records | Returns all records from left table |
| Unmatched records are excluded | Unmatched right-side values become `NULL` |

```
-- INNER JOIN
SELECT *
FROM employees e
INNER JOIN departments d
ON e.department_id = d.department_id;
```

Only employees having a matching department.

```
-- LEFT JOIN
SELECT *
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.department_id;
```

All employees are returned, even if their department doesn't exist.

### Interview answer:

> `INNER JOIN` returns only matching records from both tables, while `LEFT JOIN` returns all records from the left table and matching records from the right table.

* * * * *

12\. `UNION` vs `UNION ALL` ⭐⭐⭐⭐
================================

| UNION | UNION ALL |
| --- | --- |
| Removes duplicates | Keeps duplicates |
| Generally slower | Generally faster |
| Performs duplicate checking | No duplicate checking |

```
SELECT name FROM employees_2024
UNION
SELECT name FROM employees_2025;
```

```
SELECT name FROM employees_2024
UNION ALL
SELECT name FROM employees_2025;
```

### Easy memory:

> **UNION = remove duplicates**\
> **UNION ALL = keep duplicates**

* * * * *

13\. Primary Key vs Foreign Key ⭐⭐⭐⭐⭐
=====================================

| Primary Key | Foreign Key |
| --- | --- |
| Uniquely identifies a record | Creates relationship between tables |
| Cannot be `NULL` | Can be `NULL` depending on design |
| Must be unique | Can contain duplicate values |
| Usually one primary key constraint per table | A table can have multiple foreign keys |

Example:

```
departments
department_id ← Primary Key

employees
department_id ← Foreign Key
```

### Interview answer:

> Primary Key uniquely identifies a record, whereas Foreign Key is used to establish a relationship between two tables.

* * * * *

14\. `DELETE` vs `TRUNCATE` vs `DROP` ⭐⭐⭐⭐⭐
===========================================

| DELETE | TRUNCATE | DROP |
| --- | --- | --- |
| Deletes rows | Removes all rows | Removes entire table |
| Can use `WHERE` | No `WHERE` | Table structure also removed |
| Table remains | Table remains | Table no longer exists |
| DML | Commonly classified as DDL in many DBMSs | DDL |

### Examples:

```
DELETE FROM employees
WHERE id = 5;
```

Deletes specific records.

```
TRUNCATE TABLE employees;
```

Removes all records but keeps the table.

```
DROP TABLE employees;
```

Removes the table itself.

### 🧠 Easy memory

> **DELETE → remove selected rows**\
> **TRUNCATE → remove all rows**\
> **DROP → remove table**

* * * * *

15\. How do you validate UI data against DB? ⭐⭐⭐⭐⭐
==================================================

This is **very important for a QA interview**.

Example:

User registers through UI:

```
Name: Aniket
Email: aniket@test.com
```

First perform registration through UI.

Then query the DB:

```
SELECT *
FROM users
WHERE email = 'aniket@test.com';
```

Then compare:

```
UI Data
   ↓
Database Query
   ↓
Compare values
   ↓
Pass / Fail
```

You can validate:

-   Record was created
-   Name/email are correct
-   Status is correct
-   IDs are generated correctly
-   Updated data is reflected
-   Deleted data is removed
-   No duplicate record is created

### ⭐ Best interview answer

> **After performing an action through the UI or API, I query the database using SQL and compare the expected UI/API data with the actual database values. I verify that records are correctly inserted, updated, retrieved, or deleted according to the requirement.**
