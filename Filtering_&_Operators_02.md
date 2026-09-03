Filtering & Operators ⭐⭐⭐⭐⭐
===========================

Using the same `employees` table:

| id | name | department | salary |
| --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 |
| 2 | Rahul | Dev | 60000 |
| 3 | Amit | QA | 40000 |
| 4 | Priya | HR | NULL |

* * * * *

AND
---

Both conditions must be true.

```
SELECT *
FROM employees
WHERE department = 'QA' AND salary > 45000;
```

👉 Returns QA employees **with salary greater than 45,000**.

* * * * *

OR
--

At least one condition must be true.

```
SELECT *
FROM employees
WHERE department = 'QA' OR department = 'Dev';
```

👉 Returns employees from **QA or Dev**.

* * * * *

NOT
---

Excludes records matching a condition.

```
SELECT *
FROM employees
WHERE NOT department = 'QA';
```

👉 Returns everyone **except QA employees**.

* * * * *

IN ⭐⭐⭐⭐
-------

Used when checking multiple values.

```
SELECT *
FROM employees
WHERE department IN ('QA', 'Dev', 'HR');
```

👉 Same as writing multiple `OR` conditions.

```
WHERE department = 'QA'
   OR department = 'Dev'
   OR department = 'HR';
```

### Easy memory:

> `IN` = Multiple possible values

* * * * *

BETWEEN ⭐⭐⭐⭐
------------

Used to select values within a range.

```
SELECT *
FROM employees
WHERE salary BETWEEN 40000 AND 60000;
```

👉 Returns salaries from **40,000 to 60,000**.

⚠️ `BETWEEN` includes both values.

> 40000 and 60000 are included.

* * * * *

LIKE ⭐⭐⭐⭐⭐
----------

Used for pattern matching.

### Names starting with `A`

```
SELECT *
FROM employees
WHERE name LIKE 'A%';
```

👉 `%` means **any number of characters**.

Results: `Aniket`, `Amit`

* * * * *

### Names ending with `t`

```
WHERE name LIKE '%t';
```

* * * * *

### Names containing `mi`

```
WHERE name LIKE '%mi%';
```

* * * * *

### `_` wildcard

`_` means **exactly one character**.

```
WHERE name LIKE '_mit';
```

👉 Matches `Amit` because `_` represents `A`.

### 🧠 Memory:

-   `%` → Any number of characters
-   `_` → Exactly one character

* * * * *

IS NULL ⭐⭐⭐⭐⭐
-------------

Used to find missing/NULL values.

```
SELECT *
FROM employees
WHERE salary IS NULL;
```

👉 Returns Priya.

⚠️ Never write:

```
WHERE salary = NULL; ❌
```

Correct:

```
WHERE salary IS NULL; ✅
```

* * * * *

IS NOT NULL
-----------

Returns records where the value exists.

```
SELECT *
FROM employees
WHERE salary IS NOT NULL;
```

👉 Returns employees having a salary value.

* * * * *

🧠 Quick Revision
=================

| Operator | Meaning |
| --- | --- |
| `AND` | Both conditions true |
| `OR` | At least one condition true |
| `NOT` | Exclude condition |
| `IN` | Match multiple values |
| `BETWEEN` | Value within a range |
| `LIKE` | Pattern matching |
| `IS NULL` | Find missing values |
| `IS NOT NULL` | Find available values |
