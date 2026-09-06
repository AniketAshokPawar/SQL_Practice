Subqueries ⭐⭐⭐⭐
===============

A **subquery = query inside another query**.

Think of it as: **First find something → then use that result in the main query.**

Example `employees` table:

| id | name | department | salary |
| --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 |
| 2 | Rahul | Dev | 60000 |
| 3 | Amit | QA | 70000 |
| 4 | Priya | HR | 45000 |

* * * * *

1\. Simple Subquery
-------------------

**Question:** Find employees whose salary is greater than the average salary.

First, we need average salary:

```
SELECT AVG(salary)
FROM employees;
```

Instead of manually putting that value, use it as a subquery:

```
SELECT name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

### How it works

```
Subquery → finds average salary
              ↓
Main query → finds employees above that average
```

This is the most basic idea of a subquery.

* * * * *

2\. `IN` with Subquery
----------------------

`IN` is useful when the subquery returns **multiple values**.

Suppose we have:

### departments

| department_id | department_name |
| --- | --- |
| 101 | QA |
| 102 | Dev |
| 103 | HR |

### employees

| id | name | department_id |
| --- | --- | --- |
| 1 | Aniket | 101 |
| 2 | Rahul | 102 |
| 3 | Amit | 101 |

**Question:** Find employees who belong to departments whose name is `QA` or `Dev`.

```
SELECT name
FROM employees
WHERE department_id IN (
    SELECT department_id
    FROM departments
    WHERE department_name IN ('QA', 'Dev')
);
```

### Think of it like:

```
Subquery → 101, 102
              ↓
IN (101, 102)
              ↓
Main query → Aniket, Rahul
```

### Interview point

`IN` with a subquery is useful when the inner query can return **multiple rows**.
