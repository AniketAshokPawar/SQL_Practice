CASE Statement ⭐⭐⭐
==================

`CASE WHEN` is like an **IF-ELSE condition in SQL**.

It lets you show different results based on a condition.

### Example: Categorize employees based on salary

```
SELECT name, salary,
CASE
    WHEN salary >= 60000 THEN 'High'
    WHEN salary >= 40000 THEN 'Medium'
    ELSE 'Low'
END AS salary_category
FROM employees;
```

### Result:

| name | salary | salary_category |
| --- | --- | --- |
| Aniket | 50000 | Medium |
| Rahul | 60000 | High |
| Amit | 30000 | Low |

### 🧠 Easy understanding

```
IF salary >= 60000 → High
ELSE IF salary >= 40000 → Medium
ELSE → Low
```

### Basic syntax

```
CASE
    WHEN condition THEN result
    WHEN condition THEN result
    ELSE result
END
```

### ⭐ Another common example

Show employee status based on salary:

```
SELECT name,
CASE
    WHEN salary > 50000 THEN 'Above 50K'
    ELSE '50K or Below'
END AS salary_status
FROM employees;
```

### 🧠 Remember

> **CASE WHEN = IF / ELSE logic in SQL**
