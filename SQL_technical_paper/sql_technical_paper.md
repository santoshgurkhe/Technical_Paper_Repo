# Database Concepts

## 1. ACID Properties

ACID properties make sure that database transactions are handled safely and correctly.

ACID stands for:

- Atomicity
- Consistency
- Isolation
- Durability

### Atomicity

Atomicity means a transaction should either complete fully or not happen at all.

For example, when transferring money from one bank account to another, two things need to happen:

1. Money should be deducted from the sender's account.
2. Money should be added to the receiver's account.

If the first step happens but the second step fails, the complete transaction should be cancelled.

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```

If something goes wrong:

```sql
ROLLBACK;
```

### Consistency

Consistency means the database should always follow its rules and constraints.

For example, if an account has only ₹500, a transaction should not allow the user to withdraw ₹1000 if negative balances are not allowed.

The database should move from one valid state to another valid state.

### Isolation

Isolation means transactions running at the same time should not interfere with each other.

For example, if two users try to withdraw money from the same account at the same time, the database should handle both transactions properly and prevent incorrect results.

### Durability

Durability means once a transaction is committed, the changes should remain saved.

For example, after a successful money transfer, the server may crash. When the database starts again, the committed transaction should still be available.

---

## 2. CAP Theorem

CAP Theorem is mainly related to distributed systems where data is stored on multiple servers.

CAP stands for:

- Consistency
- Availability
- Partition Tolerance

### Consistency

Consistency means all servers should return data that satisfies the system's consistency guarantee.

For example, if a user's account balance changes from ₹5000 to ₹4000, a strongly consistent system ensures that reads do not return an incorrect stale value.

### Availability

Availability means the system should respond to requests even if some servers have problems.

For example, if one server is down, another server should still respond to the user.

### Partition Tolerance

Partition tolerance means the system can continue operating even when communication between servers fails.

For example:

```text
Server A  ---- Network ----  Server B
```

If the network connection breaks, this is called a network partition.

During a network partition, a distributed system generally has to choose between stronger consistency and availability.

---

## 3. Joins

Joins are used to combine data from two or more tables based on a related column.

Suppose we have these tables.

### Employees

| employee_id | name  | department_id |
|-------------|-------|---------------|
| 1           | Rahul | 101           |
| 2           | Priya | 102           |

### Departments

| department_id | department_name |
|---------------|-----------------|
| 101           | Engineering     |
| 102           | HR              |

### INNER JOIN

`INNER JOIN` returns only the matching records from both tables.

```sql
SELECT employees.name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.department_id;
```

### LEFT JOIN

`LEFT JOIN` returns all records from the left table and matching records from the right table.

```sql
SELECT employees.name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.department_id;
```

If there is no matching department, the department value will be `NULL`.

### RIGHT JOIN

`RIGHT JOIN` returns all records from the right table and matching records from the left table.

```sql
SELECT employees.name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.department_id;
```

### FULL JOIN

`FULL OUTER JOIN` returns matching records and non-matching records from both tables.

```sql
SELECT employees.name, departments.department_name
FROM employees
FULL OUTER JOIN departments
ON employees.department_id = departments.department_id;
```

---

## 4. Aggregations and Filters in Queries

Aggregation functions are used to perform calculations on multiple rows.

Some common aggregate functions are:

- `COUNT()`
- `SUM()`
- `AVG()`
- `MIN()`
- `MAX()`

### COUNT

Count the total number of employees.

```sql
SELECT COUNT(*)
FROM employees;
```

### SUM

Calculate the total salary.

```sql
SELECT SUM(salary)
FROM employees;
```

### AVG

Find the average salary.

```sql
SELECT AVG(salary)
FROM employees;
```

### GROUP BY

Group employees based on their department.

```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
```

### WHERE

`WHERE` is used to filter rows before grouping.

```sql
SELECT *
FROM employees
WHERE salary > 50000;
```

### HAVING

HAVING is used to filter grouped data.

```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id
HAVING COUNT(*) > 5;
```

In simple words:

- WHERE filters rows.
- HAVING filters groups.

---

## 5. Normalization

Normalization is the process of organizing database tables to reduce duplicate data and avoid data-related problems.

For example, consider this table:

| student_id | student_name | course_name | teacher_name |
|------------|--------------|-------------|--------------|
| 1          | Rahul        | Python      | Amit         |
| 2          | Priya        | Python      | Amit         |
| 3          | Kiran        | SQL         | Ravi         |

Here, the course and teacher information is repeated.

Instead of storing everything in one table, we can split the data.

### Students Table

| student_id | student_name |
|------------|--------------|
| 1          | Rahul        |
| 2          | Priya        |
| 3          | Kiran        |

### Courses Table

| course_id | course_name | teacher_name |
|-----------|-------------|--------------|
| 1         | Python      | Amit         |
| 2         | SQL         | Ravi         |

### Student Courses Table

| student_id | course_id |
|------------|-----------|
| 1          | 1         |
| 2          | 1         |
| 3          | 2         |

This reduces duplicate data and makes updates easier.

The commonly discussed normal forms are:

### First Normal Form (1NF)

Each column should contain a single value. A table should not store multiple values in one column.

### Second Normal Form (2NF)

The table should already follow First Normal Form, and non-key columns should depend on the complete primary key.

### Third Normal Form (3NF)

The table should already follow Second Normal Form, and non-key columns should not depend on other non-key columns.

The main purpose of normalization is to reduce unnecessary duplication and keep data organized.

---

## 6. Indexes

An index helps the database find data faster.

It works similarly to the index at the end of a book. Instead of reading every page, we can use the index to find the required topic quickly.

For example, if an employees table contains millions of rows and we frequently search using email:

```sql
SELECT *
FROM employees
WHERE email = 'rahul@example.com';
```

We can create an index on the email column.

```sql
CREATE INDEX idx_employee_email
ON employees(email);
```

This can make searching faster.

However, indexes also have some cost. When data is inserted, updated, or deleted, the database may also need to update the index.

So, indexes should be created mainly on columns that are frequently used for searching, joining, or sorting.

---

## 7. Transactions

A transaction is a group of database operations treated as one unit of work.

For example, while transferring ₹1000 between two accounts:

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE account_id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE account_id = 2;

COMMIT;
```

If both operations are successful, COMMIT permanently saves the changes.

If an error occurs:

```sql
ROLLBACK;
```

`ROLLBACK` cancels the changes made during the transaction.

The main transaction commands are:

- `BEGIN` - starts a transaction.
- `COMMIT` - saves the transaction.
- `ROLLBACK` - cancels the transaction.

---

## 8. Locking Mechanism

A lock is used by the database to control access to data when multiple transactions are running at the same time.

For example, imagine an account with ₹10,000.

Two users try to withdraw money at the same time.

Without proper locking, both users may read the same balance and perform transactions based on old information.

With locking, the database can temporarily lock the required data while one transaction is updating it.

```text
User A updates account
        ↓
Account row is locked
        ↓
User B waits
        ↓
User A completes the transaction
        ↓
Lock is released
        ↓
User B continues
```

### Common Types of Locks

#### Shared Lock

A shared lock is generally related to reading data. Multiple transactions can usually read the same data at the same time.

#### Exclusive Lock

An exclusive lock is used when data is being modified. Other transactions may need to wait before modifying the same data.

#### Row-Level Lock

Only the specific row being used is locked.

For example:

```sql
UPDATE employees
SET salary = 50000
WHERE employee_id = 101;
```

The database can lock the row for employee 101 instead of locking the whole table.

#### Table-Level Lock

The complete table is locked. This can affect other transactions that need access to the table.

---

## 9. Database Isolation Levels

Isolation levels control how transactions can see changes made by other transactions.

They are important when multiple transactions run at the same time.

There are four commonly discussed isolation levels:

### Read Uncommitted

A transaction can read changes made by another transaction even before those changes are committed.

This can cause a dirty read.

Example:

```text
Transaction A changes balance to ₹5000
Transaction B reads ₹5000
Transaction A performs ROLLBACK
```

Transaction B has read data that was never permanently saved.

### Read Committed

A transaction can only read data that has been committed.

This prevents dirty reads.

However, if the same transaction reads the same row twice, it may get different values if another transaction changes and commits the data between the two reads.

### Repeatable Read

Once a transaction reads a row, it continues to get a consistent result when reading that row again during the same transaction.

This prevents dirty reads and non-repeatable reads.

### Serializable

This is the highest standard isolation level.

Transactions are handled in a way that produces results equivalent to some serial ordering of transactions.

For example, if two users try to book the last available seat, the database ensures that the concurrent operations do not incorrectly allow both users to book the same seat.

Higher isolation provides better protection but can also reduce performance because transactions may need to wait.

### Quick Comparison

| Isolation Level | Dirty Read | Non-Repeatable Read |
|-----------------|------------|---------------------|
| Read Uncommitted | Possible | Possible |
| Read Committed | Prevented | Possible |
| Repeatable Read | Prevented | Prevented |
| Serializable | Prevented | Prevented |

---

## 10. Triggers

A trigger is a database action that automatically runs when a specific event happens.

Common trigger events include:

- INSERT
- UPDATE
- DELETE

For example, suppose we want to keep a record whenever an employee's salary is updated.

We can create an audit table.

```sql
CREATE TABLE salary_audit (
    employee_id INT,
    old_salary DECIMAL,
    new_salary DECIMAL,
    changed_at TIMESTAMP
);
```

A trigger can automatically store the old and new salary values whenever an update happens.

Example in PostgreSQL:

```sql
CREATE OR REPLACE FUNCTION log_salary_change()
RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO salary_audit (
        employee_id,
        old_salary,
        new_salary,
        changed_at
    )
    VALUES (
        OLD.employee_id,
        OLD.salary,
        NEW.salary,
        CURRENT_TIMESTAMP
    );

    RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

Now we can create the trigger:

```sql
CREATE TRIGGER salary_update_trigger
AFTER UPDATE OF salary
ON employees
FOR EACH ROW
EXECUTE FUNCTION log_salary_change();
```

Whenever the salary column is updated, the trigger automatically adds a record to the `salary_audit` table.

Triggers are useful for tasks such as:

- Keeping audit logs.
- Tracking changes.
- Automatically updating related data.
- Applying certain business rules.

However, too many triggers can make a database harder to understand and maintain because some actions happen automatically in the background.

## References

- GeeksForGeeks - https://www.geeksforgeeks.org/sql/sql-tutorial/
- ACID principles Video - https://www.youtube.com/watch?v=-GS0OxFJsYQ
- SQL Youtube Video - https://www.youtube.com/watch?v=yE6tIle64tU
