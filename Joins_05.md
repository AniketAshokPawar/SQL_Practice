SQL JOINs ⭐⭐⭐⭐⭐ VVIP
====================

**JOIN = Combine data from two or more tables using a related column.**

Let's use:

### `employees`

| id | name | department_id |
| --- | --- | --- |
| 1 | Aniket | 101 |
| 2 | Rahul | 102 |
| 3 | Amit | 103 |
| 4 | Priya | 999 |

### `departments`

| department_id | department_name |
| --- | --- |
| 101 | QA |
| 102 | Development |
| 103 | HR |
| 104 | Finance |

Here `employees.department_id` is related to `departments.department_id`.

* * * * *

1\. INNER JOIN ⭐⭐⭐⭐⭐
--------------------

Returns **only matching records from both tables**.

```
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d
ON e.department_id = d.department_id;
```

Result:

| name | department_name |
| --- | --- |
| Aniket | QA |
| Rahul | Development |
| Amit | HR |

👉 Priya is excluded because `999` doesn't exist in departments.\
👉 Finance is excluded because nobody in employees has `104`.

**Memory:**

> INNER = **Only matching**

* * * * *

2\. LEFT JOIN ⭐⭐⭐⭐⭐
-------------------

Returns **ALL records from the left table**, plus matching records from the right table.

```
SELECT e.name, d.department_name
FROM employees e
LEFT JOIN departments d
ON e.department_id = d.department_id;
```

Result:

| name | department_name |
| --- | --- |
| Aniket | QA |
| Rahul | Development |
| Amit | HR |
| Priya | NULL |

👉 All employees are returned.\
👉 If no matching department exists → `NULL`.

**Memory:**

> LEFT = **Everything from left + matching from right**

* * * * *

3\. RIGHT JOIN ⭐⭐⭐
------------------

Opposite of LEFT JOIN.

Returns **ALL records from the right table**, plus matching records from the left.

```
SELECT e.name, d.department_name
FROM employees e
RIGHT JOIN departments d
ON e.department_id = d.department_id;
```

Result includes:

| name | department_name |
| --- | --- |
| Aniket | QA |
| Rahul | Development |
| Amit | HR |
| NULL | Finance |

👉 Finance is included even though it has no employee.

**Memory:**

> RIGHT = **Everything from right + matching from left**

* * * * *

4\. FULL OUTER JOIN ⭐⭐⭐
-----------------------

Returns **everything from both tables**.

```
SELECT e.name, d.department_name
FROM employees e
FULL OUTER JOIN departments d
ON e.department_id = d.department_id;
```

Result includes:

-   Matching employees/departments
-   Priya with `NULL` department
-   Finance with `NULL` employee

**Memory:**

> FULL = **Everything from both tables**

⚠️ Some databases, such as MySQL, don't directly support `FULL OUTER JOIN`, so syntax can vary by database.

* * * * *

5\. SELF JOIN ⭐⭐⭐
=================

A table is **joined with itself**.

Useful when records in the same table have relationships with each other.

### Example: Employees and their managers

| id | name | manager_id |
| --- | --- | --- |
| 1 | Aniket | NULL |
| 2 | Rahul | 1 |
| 3 | Amit | 1 |

Query:

```
SELECT e.name AS employee,
       m.name AS manager
FROM employees e
JOIN employees m
ON e.manager_id = m.id;
```

Result:

| employee | manager |
| --- | --- |
| Rahul | Aniket |
| Amit | Aniket |

👉 `employees` is used **twice**: once as employee (`e`) and once as manager (`m`).

* * * * *

🔥 JOINs --- Quick Revision
=========================

| JOIN | What it returns |
| --- | --- |
| **INNER JOIN** | Only matching records |
| **LEFT JOIN** | All left + matching right |
| **RIGHT JOIN** | All right + matching left |
| **FULL OUTER JOIN** | Everything from both |
| **SELF JOIN** | Table joined with itself |
