SQL Basics ⭐⭐⭐⭐⭐
================

Let's use one example table throughout:

### `employees`

| id | name | department | salary |
| --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 |
| 2 | Rahul | Dev | 60000 |
| 3 | Amit | QA | 50000 |

* * * * *

Database
--------

A **Database** is a collection of related data.

Example:

> Company Database → Employees, Departments, Projects tables.

* * * * *

Table
-----

A **Table** stores related data in rows and columns.

Example:

> `employees` table stores employee information.

* * * * *

Row
---

A **Row** represents one complete record.

Example:

| id | name | department | salary |
| --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 |

👉 One employee = **one row**

* * * * *

Column
------

A **Column** represents one type of information.

Examples:

`id`, `name`, `department`, `salary`

👉 `name` column stores employee names.

* * * * *

Primary Key ⭐⭐⭐⭐
================

A **Primary Key uniquely identifies each row**.

Example:

`id`

```
id = 1 → Aniket
id = 2 → Rahul
```

Primary Key should be:

-   Unique
-   Not NULL

* * * * *

Foreign Key ⭐⭐⭐⭐
================

A **Foreign Key connects one table with another table**.

Example:

### employees

| id | name | department_id |
| --- | --- | --- |
| 1 | Aniket | 101 |
| 2 | Rahul | 102 |

### departments

| department_id | department |
| --- | --- |
| 101 | QA |
| 102 | Development |

Here:

`employees.department_id` → **Foreign Key**

It connects to:

`departments.department_id`

* * * * *

NULL ⭐⭐⭐⭐
=========

`NULL` means **value is missing or unknown**.

Example:

| name | phone |
| --- | --- |
| Aniket | NULL |

👉 Phone information is not available.

⚠️ `NULL` is **not the same as**:

-   `0`
-   Empty string `''`

* * * * *

SELECT ⭐⭐⭐⭐⭐
============

Used to **retrieve data from a table**.

### Get all columns:

```
SELECT * FROM employees;
```

### Get specific columns:

```
SELECT name, salary FROM employees;
```

* * * * *

WHERE ⭐⭐⭐⭐⭐
===========

Used to **filter records based on a condition**.

### Example:

Get QA employees:

```
SELECT *
FROM employees
WHERE department = 'QA';
```

Result:

| id | name | department | salary |
| --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 |
| 3 | Amit | QA | 50000 |

* * * * *

DISTINCT ⭐⭐⭐⭐
=============

Used to remove duplicate values.

### Example:

```
SELECT DISTINCT department
FROM employees;
```

Result:

```
QA
Dev
```

👉 Even though QA appears twice, it is shown only once.

* * * * *

ORDER BY ⭐⭐⭐⭐
=============

Used to **sort the result**.

### Ascending (default):

```
SELECT *
FROM employees
ORDER BY salary ASC;
```

### Descending:

```
SELECT *
FROM employees
ORDER BY salary DESC;
```

👉 `ASC` = Low → High\
👉 `DESC` = High → Low

* * * * *

🧠 Quick Revision
=================

| Concept | Remember |
| --- | --- |
| Database | Collection of data |
| Table | Data in rows and columns |
| Row | One complete record |
| Column | One type of data |
| Primary Key | Unique identifier |
| Foreign Key | Connects tables |
| NULL | Missing/unknown value |
| SELECT | Get data |
| WHERE | Filter data |
| DISTINCT | Remove duplicates |
| ORDER BY | Sort data |

### ⭐ Most important to practice:

```
SELECT * FROM employees;

SELECT name FROM employees;

SELECT * FROM employees WHERE department = 'QA';

SELECT DISTINCT department FROM employees;

SELECT * FROM employees ORDER BY salary DESC;
```
