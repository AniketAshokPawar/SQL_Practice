INSERT / UPDATE / DELETE ⭐⭐⭐⭐
=============================

These are used to **add, modify, or remove data**.

Assume the table:

### `employees`

| id | name | department | salary |
| --- | --- | --- | --- |
| 1 | Aniket | QA | 50000 |
| 2 | Rahul | Dev | 60000 |

* * * * *

1\. `INSERT` → Add a new record
-------------------------------

```
INSERT INTO employees (id, name, department, salary)
VALUES (3, 'Amit', 'QA', 45000);
```

👉 Adds a new employee record.

### QA use:

Sometimes QA may insert test data directly into the database when UI/API is not convenient.

* * * * *

2\. `UPDATE` → Modify existing data
-----------------------------------

```
UPDATE employees
SET salary = 55000
WHERE id = 1;
```

👉 Updates Aniket's salary.

### ⚠️ Important

```
UPDATE employees
SET salary = 55000;
```

❌ Without `WHERE`, this may update **all employee records**.

* * * * *

3\. `DELETE` → Remove records
-----------------------------

```
DELETE FROM employees
WHERE id = 3;
```

👉 Deletes the employee with ID 3.

### ⚠️ Important

```
DELETE FROM employees;
```

❌ Without `WHERE`, it deletes **all records** from the table.

* * * * *

🧪 How QA might use these
=========================

| Command | QA Example |
| --- | --- |
| `INSERT` | Create test data directly in DB |
| `UPDATE` | Modify data to test a specific scenario |
| `DELETE` | Remove test data / prepare a negative test scenario |

### ⭐ Easy Memory

> **INSERT → Add**\
> **UPDATE → Modify**\
> **DELETE → Remove**

### 🔥 Interview Point

Always mention:

> **"Before running UPDATE or DELETE, I use SELECT with the same WHERE condition to verify which records will be affected."**

Example:

```
SELECT *
FROM employees
WHERE id = 3;
```

Then run:

```
DELETE FROM employees
WHERE id = 3;
```

This is a good practical habit, especially in shared QA databases.
