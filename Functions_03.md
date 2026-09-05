SQL Functions ⭐⭐⭐⭐⭐
===================

Using the same `employees` table:

| id | name | department | salary | joining_date |
| --- | --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 | 2024-01-15 |
| 2 | Rahul | Dev | 60000 | 2023-06-10 |
| 3 | Amit | QA | 40000 | 2025-03-20 |

* * * * *

Aggregate Functions ⭐⭐⭐⭐⭐
-------------------------

Aggregate functions perform calculations on multiple rows.

### `COUNT()` → Count records

```
SELECT COUNT(*) FROM employees;
```

👉 Returns total number of employees.

* * * * *

### `SUM()` → Total value

```
SELECT SUM(salary) FROM employees;
```

👉 Returns the total salary.

* * * * *

### `AVG()` → Average value

```
SELECT AVG(salary) FROM employees;
```

👉 Returns the average salary.

* * * * *

### `MIN()` → Smallest value

```
SELECT MIN(salary) FROM employees;
```

👉 Returns the lowest salary.

* * * * *

### `MAX()` → Largest value

```
SELECT MAX(salary) FROM employees;
```

👉 Returns the highest salary.

### 🧠 Easy Memory

> `COUNT` = How many\
> `SUM` = Total\
> `AVG` = Average\
> `MIN` = Smallest\
> `MAX` = Largest

* * * * *

String Functions ⭐⭐⭐
====================

Function names can slightly differ depending on the database, but these basics are enough.

### `UPPER()` → Convert to uppercase

```
SELECT UPPER(name) FROM employees;
```

`Aniket` → `ANIKET`

* * * * *

### `LOWER()` → Convert to lowercase

```
SELECT LOWER(name) FROM employees;
```

`Aniket` → `aniket`

* * * * *

### `LENGTH()` → Count characters

```
SELECT LENGTH(name) FROM employees;
```

`Aniket` → `6`

* * * * *

### `CONCAT()` → Join text

```
SELECT CONCAT(name, ' - ', department)
FROM employees;
```

Result:

> Aniket - QA

* * * * *

Date Functions ⭐⭐⭐
==================

Date function syntax varies between databases, so understand the concept.

### Current Date

```
SELECT CURRENT_DATE;
```

👉 Returns today's date.
