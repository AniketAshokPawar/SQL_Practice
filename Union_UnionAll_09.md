UNION / UNION ALL ⭐⭐⭐
=====================

Used to **combine results from two `SELECT` queries**.

Assume:

### `employees_2024`

| name |
| --- |
| Aniket |
| Rahul |

### `employees_2025`

| name |
| --- |
| Rahul |
| Amit |

* * * * *

`UNION`
-------

Combines results and **removes duplicate records**.

```
SELECT name FROM employees_2024
UNION
SELECT name FROM employees_2025;
```

### Result:

```
Aniket
Rahul
Amit
```

👉 `Rahul` appears only once.

* * * * *

`UNION ALL`
-----------

Combines results and **keeps duplicates**.

```
SELECT name FROM employees_2024
UNION ALL
SELECT name FROM employees_2025;
```

### Result:

```
Aniket
Rahul
Rahul
Amit
```

* * * * *

🔥 UNION vs UNION ALL
=====================

| UNION | UNION ALL |
| --- | --- |
| Removes duplicates | Keeps duplicates |
| Usually slower due to duplicate checking | Usually faster |
| Rahul appears once | Rahul appears twice |
