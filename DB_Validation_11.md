Database Validation ⭐⭐⭐⭐⭐
=========================

**Database Validation = Checking whether the data shown/created/updated through the application is correctly stored in the database.**

As a QA, you basically compare:

> **UI/API action → Database data**

* * * * *

Example 1: User Registration
----------------------------

User registers through UI:

```
Name: Aniket
Email: aniket@test.com
```

QA verifies the database:

```
SELECT *
FROM users
WHERE email = 'aniket@test.com';
```

Check whether:

-   Correct user record is created
-   Name is correct
-   Email is correct
-   Other required fields are stored correctly

* * * * *

Example 2: Update Validation
----------------------------

User changes their name through UI:

```
Aniket → Aniket Pawar
```

Verify in DB:

```
SELECT name
FROM users
WHERE email = 'aniket@test.com';
```

Expected:

```
Aniket Pawar
```

* * * * *

Example 3: Delete Validation
----------------------------

User deletes their account.

Verify the record:

```
SELECT *
FROM users
WHERE email = 'aniket@test.com';
```

Expected:

> No record should be returned.

* * * * *

⭐ QA CRUD Validation
====================

| UI Action | Database Validation |
| --- | --- |
| **Create** | Check whether record is inserted |
| **Read** | Check whether correct data is displayed |
| **Update** | Check whether DB data is updated |
| **Delete** | Check whether record is removed |
