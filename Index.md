### Must Know

1.  **SQL Basics**
    -   Database, Table, Row, Column
    -   Primary Key / Foreign Key
    -   NULL
    -   `SELECT`
    -   `WHERE`
    -   `DISTINCT`
    -   `ORDER BY`
2.  **Filtering & Operators**
    -   `AND`, `OR`, `NOT`
    -   `IN`
    -   `BETWEEN`
    -   `LIKE`
    -   `IS NULL` / `IS NOT NULL`
3.  **SQL Functions**
    -   Aggregate: `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`
    -   String functions --- basic
    -   Date functions --- basic
4.  **GROUP BY & HAVING** ⭐⭐⭐⭐⭐
    -   `GROUP BY`
    -   `HAVING`
    -   Difference between `WHERE` and `HAVING`
5.  **Joins** ⭐⭐⭐⭐⭐ VVIP

    -   `INNER JOIN`
    -   `LEFT JOIN`
    -   `RIGHT JOIN` --- basic understanding
    -   `FULL OUTER JOIN` --- basic understanding
    -   Self Join --- basic

    **This is probably the most important SQL topic for QA interviews.**

6.  **Subqueries** ⭐⭐⭐⭐
    -   Simple subquery
    -   `IN` with subquery
    -   Correlated subquery --- basic understanding
7.  **INSERT / UPDATE / DELETE** ⭐⭐⭐⭐
    -   Know syntax
    -   Understand when QA might use them
    -   Be careful with `UPDATE`/`DELETE` without `WHERE`
8.  **Constraints** ⭐⭐⭐
    -   Primary Key
    -   Foreign Key
    -   Unique
    -   NOT NULL
    -   CHECK
    -   DEFAULT
9.  **UNION / UNION ALL** ⭐⭐⭐
    -   Difference between them
    -   Basic query
10. **CASE Statement** ⭐⭐⭐

-   `CASE WHEN`
-   Useful for conditional results.

* * * * *

🧪 QA-Specific SQL --- VERY IMPORTANT
===================================

This is where I would spend extra time because **you're preparing as a QA, not a SQL developer**.

### 11\. Database Validation ⭐⭐⭐⭐⭐

Understand how QA uses SQL to verify backend data.

Example:

> User registers through UI → verify user record was correctly inserted into the database.

```
SELECT *
FROM users
WHERE email = 'test@gmail.com';
```

* * * * *

### 12\. UI vs Database Validation ⭐⭐⭐⭐⭐

Be able to explain:

> **"How do you validate UI data against the database?"**

Example:

UI shows:

**Name:** Aniket\
**Email:** <aniket@test.com>

QA queries DB and verifies the corresponding record.

* * * * *

### 13\. Finding Duplicate Records ⭐⭐⭐⭐⭐

Very common interview question.

Example:

```
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

* * * * *

### 14\. Finding Missing / Mismatched Data ⭐⭐⭐⭐

Example:

> Find users present in one table but missing from another.

This will naturally require **JOINs**, especially `LEFT JOIN`.

* * * * *

### 15\. CRUD Validation ⭐⭐⭐⭐

Understand:

**Create → Read → Update → Delete**

Example:

-   Create user through UI
-   Verify with `SELECT`
-   Update user
-   Verify updated data
-   Delete user
-   Verify record is removed/updated as expected

* * * * *

🎯 SQL Interview Questions You Should Practice
==============================================

Don't just learn topics. Practice queries for:

1.  Find second-highest salary.
2.  Find duplicate records.
3.  Find employees who don't have a department.
4.  Find records present in Table A but not Table B.
5.  Count employees in each department.
6.  Find departments having more than 5 employees.
7.  Find the highest salary in each department.
8.  Fetch records between two dates.
9.  Find employees whose name starts with `A`.
10. Difference between `WHERE` and `HAVING`.
11. Difference between `INNER JOIN` and `LEFT JOIN`.
12. Difference between `UNION` and `UNION ALL`.
13. Primary Key vs Foreign Key.
14. `DELETE` vs `TRUNCATE` vs `DROP`.
15. How do you validate UI data against DB?

* * * * *

📅 Your 3--4 Day Plan
====================

### Day 1 --- SQL Fundamentals

**SELECT → WHERE → operators → ORDER BY → DISTINCT → NULL → functions**

### Day 2 --- 🔥 Joins + Grouping

**JOINs → GROUP BY → HAVING → aggregate functions**

### Day 3 --- Advanced-enough SQL

**Subqueries → CASE → UNION → constraints → INSERT/UPDATE/DELETE**

### Day 4 --- QA SQL + Interview Practice

**DB validation → UI vs DB → duplicates → mismatched data → 15--20 interview queries**

### ⭐ Priority

**JOINs > GROUP BY/HAVING > SELECT/WHERE > Subqueries > QA DB validation > everything else**
