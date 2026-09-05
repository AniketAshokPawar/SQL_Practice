GROUP BY & HAVING ⭐⭐⭐⭐⭐
=======================

Let's use this table:

### `employees`

| id | name | department | salary |
| --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 |
| 2 | Rahul | Dev | 60000 |
| 3 | Amit | QA | 40000 |
| 4 | Priya | Dev | 55000 |
| 5 | Neha | QA | 45000 |

* * * * *

`GROUP BY`
----------

Used to **group rows with the same value**, usually with aggregate functions like `COUNT()`, `SUM()`, or `AVG()`.

### Example: Count employees in each department

```
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

### Result:

| department | COUNT |
| --- | --- |
| QA | 3 |
| Dev | 2 |

👉 `GROUP BY department` creates groups: **QA group** and **Dev group**.

* * * * *

### Another example: Average salary by department

```
SELECT department, AVG(salary)
FROM employees
GROUP BY department;
```

👉 Calculates the average salary separately for each department.

* * * * *

`HAVING`
========

`HAVING` is used to **filter grouped results**.

### Example:

Show departments having more than 2 employees:

```
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 2;
```

### Result:

| department | COUNT |
| --- | --- |
| QA | 3 |

👉 First, SQL groups employees by department.\
👉 Then `HAVING` filters those groups.

* * * * *

⭐ WHERE vs HAVING ⭐⭐⭐⭐⭐ VVIP
============================

| WHERE | HAVING |
| --- | --- |
| Filters **rows** | Filters **groups** |
| Used before `GROUP BY` | Used after `GROUP BY` |
| Cannot normally filter aggregate results | Used with aggregate results |
| Example: `WHERE salary > 40000` | Example: `HAVING COUNT(*) > 2` |

* * * * *

### Example using both together

```
SELECT department, COUNT(*)
FROM employees
WHERE salary > 40000
GROUP BY department
HAVING COUNT(*) > 1;
```

### What happens?

1.  `WHERE salary > 40000` → Filters individual employees.
2.  `GROUP BY department` → Groups remaining employees.
3.  `HAVING COUNT(*) > 1` → Filters the groups.

### 🧠 Easy Memory

> **WHERE = Filter rows before grouping**\
> **HAVING = Filter groups after grouping**

### ⭐ Very common interview question

**Q: Can we use `WHERE` and `HAVING` together?**

**Yes.** `WHERE` filters rows first, and `HAVING` filters the grouped result afterward.

* * * * *

🔥 SQL Query Order to Remember
------------------------------

```
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
```
`ORDER BY` with GROUP BY & HAVING ⭐⭐⭐⭐
--------------------------------------

`ORDER BY` is used to **sort the final result**.

### Example: Count employees department-wise and sort by count

```
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
ORDER BY employee_count DESC;
```

👉 First groups employees by department → then sorts the result by employee count.

* * * * *

### Using `WHERE + GROUP BY + HAVING + ORDER BY`

```
SELECT department, COUNT(*) AS employee_count
FROM employees
WHERE salary > 40000
GROUP BY department
HAVING COUNT(*) > 1
ORDER BY employee_count DESC;
```

### Easy flow:

```
WHERE     → Filter rows
GROUP BY  → Create groups
HAVING    → Filter groups
ORDER BY  → Sort final result
```
