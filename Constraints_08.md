SQL Constraints ⭐⭐⭐
===================

**Constraints = rules applied to table columns to control what data can be stored.**

* * * * *

1\. PRIMARY KEY ⭐⭐⭐⭐⭐
---------------------

Uniquely identifies each row.

-   Must be **unique**
-   Cannot be `NULL`

```
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50)
);
```

👉 Two employees cannot have the same `id`.

* * * * *

2\. FOREIGN KEY ⭐⭐⭐⭐
--------------------

Creates a relationship between two tables.

```
CREATE TABLE employees (
    id INT PRIMARY KEY,
    department_id INT,
    FOREIGN KEY (department_id)
        REFERENCES departments(department_id)
);
```

👉 `department_id` in `employees` must refer to a valid department in the `departments` table.

* * * * *

3\. UNIQUE
----------

Does not allow duplicate values.

```
email VARCHAR(100) UNIQUE
```

👉 Two users cannot have the same email.

### Primary Key vs UNIQUE

-   **Primary Key:** Unique + Cannot be NULL
-   **UNIQUE:** No duplicate values; NULL handling can vary by database

* * * * *

4\. NOT NULL
------------

The column must have a value.

```
name VARCHAR(50) NOT NULL
```

👉 You cannot insert an employee without a name.

* * * * *

5\. CHECK
---------

Restricts values based on a condition.

```
age INT CHECK (age >= 18)
```

👉 Age below 18 cannot be inserted.

* * * * *

6\. DEFAULT
-----------

Provides a default value if no value is given.

```
status VARCHAR(20) DEFAULT 'Active'
```

If you insert a user without specifying status:

```
status = Active
```

* * * * *

🧠 Quick Revision
=================

| Constraint | Meaning |
| --- | --- |
| **PRIMARY KEY** | Unique + Not NULL |
| **FOREIGN KEY** | Connects two tables |
| **UNIQUE** | No duplicate values |
| **NOT NULL** | Value is mandatory |
| **CHECK** | Value must follow a condition |
| **DEFAULT** | Automatically assigns a default value |
