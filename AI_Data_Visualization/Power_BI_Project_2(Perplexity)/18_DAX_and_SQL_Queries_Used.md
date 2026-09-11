# 1. Creating the Database

From Lecture 1:

```sql
CREATE DATABASE Power_BI2
```



### What does it do?

Creates a new SQL Server database called:

**`Power_BI2`**

Think of a database as a container that holds tables, views, procedures, etc.

---

## Selecting the database

```sql
USE Power_BI2
```

This tells SQL Server:

> "From now on, execute my queries inside the `Power_BI2` database."

So if you subsequently run:

```sql
CREATE TABLE Customers (...)
```

the table will be created inside `Power_BI2`.

---

# 2. Dropping Existing Tables

```sql
IF OBJECT_ID('Transactions', 'U') IS NOT NULL DROP TABLE Transactions;
IF OBJECT_ID('Accounts', 'U') IS NOT NULL DROP TABLE Accounts;
IF OBJECT_ID('Customers', 'U') IS NOT NULL DROP TABLE Customers;
```



This is basically a **reset script**.

## `OBJECT_ID()`

```sql
OBJECT_ID('Transactions', 'U')
```

checks whether an object called `Transactions` exists.

The second argument:

```text
'U'
```

means **user table**.

So:

```sql
IF OBJECT_ID('Transactions', 'U') IS NOT NULL
```

means:

> If the `Transactions` table exists...

then:

```sql
DROP TABLE Transactions;
```

deletes it.

### Why drop Transactions first?

The comment says:

> Drop tables if they exist (order due to FK dependencies)

Normally, if tables have foreign-key relationships, you should remove the dependent table first.

The intended dependency hierarchy is roughly:

```text
Customers
   ↓
Accounts
   ↓
Transactions
```

So `Transactions` is dropped first, then `Accounts`, then `Customers`.

---

# 3. Creating the Customers Table

```sql
CREATE TABLE Customers (
    CustomerID     INT PRIMARY KEY,
    Name           NVARCHAR(100),
    Gender         VARCHAR(10) NULL,
    DateOfBirth    VARCHAR(20),
    Address        NVARCHAR(200) NULL,
    Email          NVARCHAR(100) NULL,
    Phone          VARCHAR(20),
    AccountID      INT
);
```



This creates a table called **Customers**.

It has these columns:

| Column      | Data type     | Purpose            |
| ----------- | ------------- | ------------------ |
| CustomerID  | INT           | Unique customer ID |
| Name        | NVARCHAR(100) | Customer name      |
| Gender      | VARCHAR(10)   | Gender             |
| DateOfBirth | VARCHAR(20)   | Date of birth      |
| Address     | NVARCHAR(200) | Address            |
| Email       | NVARCHAR(100) | Email              |
| Phone       | VARCHAR(20)   | Phone number       |
| AccountID   | INT           | Associated account |

---

## Why is `CustomerID` a PRIMARY KEY?

```sql
CustomerID INT PRIMARY KEY
```

A primary key uniquely identifies every row.

For example:

```text
CustomerID
1
2
3
4
5
```

You cannot have:

```text
1
1
```

because two customers cannot have the same primary key.

---

## Why is DateOfBirth VARCHAR instead of DATE?

This is intentional:

```sql
DateOfBirth VARCHAR(20)
```

The comment says:

> to allow mixed formats

The dataset contains:

```text
1980-11-04
21-07-1975
1989/02/20
1995-05-14
04-12-1982
```

These dates use different formats.

A proper production database would ideally use:

```sql
DATE
```

But here we're deliberately creating **dirty data** so that we can practice data cleaning in Power BI/SQL.

---

# 4. Creating Accounts Table

```sql
CREATE TABLE Accounts (
    AccountID   INT PRIMARY KEY,
    CustomerID  INT,
    Type        NVARCHAR(20),
    OpenDate    VARCHAR(20),
    Balance     DECIMAL(18,2)
);
```



This creates the **Accounts** table.

### Columns

| Column     | Meaning                     |
| ---------- | --------------------------- |
| AccountID  | Unique account number       |
| CustomerID | Customer owning the account |
| Type       | Savings/current             |
| OpenDate   | Account opening date        |
| Balance    | Current balance             |

---

## `DECIMAL(18,2)`

```sql
Balance DECIMAL(18,2)
```

means:

* maximum 18 digits overall
* 2 digits after decimal

For example:

```text
10000.00
157874.40
50.00
```

This is appropriate for monetary values.

---

# 5. Creating Transactions Table

```sql
CREATE TABLE Transactions (
    TransactionID    INT,
    AccountID        INT,
    TransactionDate  VARCHAR(20),
    Type             VARCHAR(20),
    Amount           DECIMAL(18,2),
    Description      NVARCHAR(200) NULL,
    Currency         VARCHAR(10)
);
```



This stores individual banking transactions.

Example:

| TransactionID | AccountID | Type   | Amount |
| ------------: | --------: | ------ | -----: |
|        100001 |       101 | DEBIT  |   -500 |
|        100002 |       102 | Credit |   1000 |

Notice:

```sql
TransactionID INT
```

is **not declared as a primary key**.

Why?

The comment says:

> Not enforcing PK to allow duplicates

This is intentional because the exercise wants to demonstrate **duplicate data problems**.

---

# 6. Inserting Customers

```sql
INSERT INTO Customers 
(CustomerID, Name, Gender, DateOfBirth, Address, Email, Phone, AccountID)
VALUES
...
```



This inserts five customers.

For example:

```sql
(1, 'Ajay Sharma', 'M', '1980-11-04', 
 '123 Main St', NULL, '9891000001', 101)
```

means:

```text
CustomerID = 1
Name       = Ajay Sharma
Gender     = M
DOB        = 1980-11-04
Address    = 123 Main St
Email      = NULL
Phone      = 9891000001
AccountID  = 101
```

---

## Notice the dirty data

### Customer 2

```text
priya singh
```

lowercase name.

### Customer 3

```text
1989/02/20
```

different date format.

### Customer 5

```text
NAdea KUmar
```

inconsistent capitalization.

### NULL values

Some customers have:

```text
NULL Email
NULL Address
NULL Gender
```

These are intentional data-quality issues.

---

# 7. Inserting Accounts

```sql
INSERT INTO Accounts 
(AccountID, CustomerID, Type, OpenDate, Balance)
VALUES
...
```



Example:

```sql
(101, 1, 'SAVINGS', '03/14/2013', 10000.00)
```

means:

```text
AccountID = 101
CustomerID = 1
Type      = SAVINGS
OpenDate  = 03/14/2013
Balance   = 10000
```

---

## Notice the intentional problems

### Different capitalization

```text
SAVINGS
current
Savings
CURRENT
Savings
```

Ideally we want something consistent like:

```text
Savings
Current
```

---

### Negative balance

```text
-157874.40
```

This is an obvious potential **outlier/anomaly**.

---

### Invalid CustomerID

```sql
(105, 99, 'Savings', ...)
```

Customer `99` doesn't exist in the Customers table.

Customers only contain IDs:

```text
1, 2, 3, 4, 5
```

So:

```text
Account 105 → Customer 99
```

is a **referential integrity issue**.

The script deliberately does not enforce a foreign key so that this dirty data can exist.

---

# 8. Generating 10,000 Transactions

This is the most complicated query.

```sql
;WITH NumberedRows AS (
    SELECT 
        ROW_NUMBER() OVER (ORDER BY (SELECT NULL)) AS rn
    FROM
        sys.all_objects a
        CROSS JOIN sys.all_columns c
)
```



This creates a temporary result called a **CTE**.

CTE = **Common Table Expression**.

Here it is called:

```text
NumberedRows
```

---

# 9. `ROW_NUMBER()`

```sql
ROW_NUMBER() OVER (ORDER BY (SELECT NULL)) AS rn
```

generates sequential numbers:

```text
1
2
3
4
5
...
10000
```

The generated number is called:

```text
rn
```

Think of `rn` as the row number.

---

# 10. Why `sys.all_objects` and `sys.all_columns`?

```sql
FROM sys.all_objects a
CROSS JOIN sys.all_columns c
```

These are SQL Server system catalog views.

They contain many existing SQL Server objects and columns.

The query uses their combination to generate **a large number of rows**.

`CROSS JOIN` creates combinations between the two datasets.

For example:

```text
A1 × C1
A1 × C2
A1 × C3
A2 × C1
A2 × C2
...
```

This provides enough rows to generate 10,000 synthetic transactions.

---

# 11. Inserting the Generated Transactions

```sql
INSERT INTO Transactions (
    TransactionID,
    AccountID,
    TransactionDate,
    Type,
    Amount,
    Description,
    Currency
)
```



This says:

> Take the generated values and insert them into these columns of Transactions.

---

# 12. Generating Transaction IDs

```sql
100000 + rn AS TransactionID
```



If:

```text
rn = 1
```

then:

```text
100000 + 1 = 100001
```

If:

```text
rn = 2
```

then:

```text
100002
```

So IDs become:

```text
100001
100002
100003
...
```

---

# 13. Generating Account IDs

```sql
CASE 
    WHEN rn % 20 = 0 THEN 9999 
    ELSE 101 + (rn % 100) 
END AS AccountID
```



This uses a **CASE expression**.

It means:

> If the row number is divisible by 20, use AccountID 9999. Otherwise generate an account ID.

---

## What is `%`?

`%` means **modulo/remainder**.

For example:

```text
20 % 20 = 0
40 % 20 = 0
60 % 20 = 0
```

Therefore every 20th row gets:

```text
AccountID = 9999
```

But there is no account 9999.

So this deliberately creates **invalid AccountIDs**.

---

# 14. Generating Transaction Dates

```sql
CASE 
    WHEN rn % 3 = 0 
        THEN FORMAT(GETDATE() - (rn % 365), 'yyyy/MM/dd')
    ELSE CONVERT(VARCHAR(10), GETDATE() - (rn % 365), 105)
END
```



This generates transaction dates.

---

## `GETDATE()`

```sql
GETDATE()
```

returns the current date and time.

For example:

```text
2026-09-11 19:27:00
```

---

## Subtracting days

```sql
GETDATE() - (rn % 365)
```

subtracts between 0 and 364 days.

So transactions can get dates from roughly the previous year.

---

## Every third row

```sql
rn % 3 = 0
```

means:

```text
3
6
9
12
...
```

For these rows:

```sql
FORMAT(..., 'yyyy/MM/dd')
```

produces something like:

```text
2026/09/08
```

For other rows:

```sql
CONVERT(..., 105)
```

uses style `105`, producing:

```text
08-09-2026
```

So the transaction table intentionally contains **mixed date formats**.

---

# 15. Generating Transaction Type

```sql
CASE 
    WHEN rn % 2 = 0 THEN 'Credit' 
    ELSE 'DEBIT' 
END AS Type
```



Even rows:

```text
Credit
```

Odd rows:

```text
DEBIT
```

Therefore:

```text
Credit
DEBIT
Credit
DEBIT
...
```

Again, capitalization is inconsistent.

A cleaning process might convert everything to:

```text
Credit
Debit
```

---

# 16. Generating Transaction Amount

```sql
CASE 
    WHEN rn % 1000 = 0 THEN -99999.99
    WHEN rn % 250 = 0 THEN 1000000.99
    ELSE ...
END
```



This deliberately creates **outliers**.

### Every 1000th row

```sql
rn % 1000 = 0
```

gets:

```text
-99999.99
```

### Every 250th row

```sql
rn % 250 = 0
```

gets:

```text
1000000.99
```

So the dataset contains unusually large positive and negative transactions.

This is useful for practicing:

* outlier detection
* anomaly detection
* data cleaning
* Power BI analysis

---

# 17. Normal Transaction Amounts

For all other rows:

```sql
(ABS(CHECKSUM(NEWID())) % 5000) *
CASE 
    WHEN rn % 2 = 0 THEN 1 
    ELSE -1 
END
```

### `NEWID()`

Generates a unique identifier.

### `CHECKSUM()`

Converts that value into an integer-like value.

### `ABS()`

Makes it positive.

### `% 5000`

Restricts the number to approximately:

```text
0–4999
```

Then:

```sql
CASE WHEN rn % 2 = 0 THEN 1 ELSE -1 END
```

makes:

* even rows → positive
* odd rows → negative

So normal transactions might look like:

```text
2500
-430
1720
-3000
...
```

---

# 18. Generating Descriptions

```sql
CASE 
    WHEN rn % 50 = 0 THEN NULL
    ELSE CASE 
        WHEN rn % 2 = 0 THEN 'payment' 
        ELSE 'Salary Credit' 
    END
END AS Description
```



Every 50th transaction gets:

```text
NULL
```

Otherwise:

* even → `payment`
* odd → `Salary Credit`

Again, inconsistent capitalization:

```text
payment
Salary Credit
```

---

# 19. Generating Currency

```sql
CASE 
    WHEN rn % 3 = 0 THEN 'usd'
    WHEN rn % 5 = 0 THEN 'INR'
    ELSE 'USD'
END
```



This creates inconsistent currency values.

Possible values:

```text
usd
INR
USD
```

Notice:

```text
usd
```

and:

```text
USD
```

are logically the same currency but have different capitalization.

---

# 20. Limiting to 10,000 Rows

```sql
FROM NumberedRows
WHERE rn <= 10000;
```



The CTE may generate many rows.

This condition says:

> Only insert the first 10,000 rows.

Therefore:

```text
10,000 transactions
```

are generated.

---

# 21. Viewing the Transactions

```sql
SELECT * FROM Transactions
```



`*` means:

> Select all columns.

So this displays the entire Transactions table.

---

# Lecture 2 — Cleaning Dates

Now we come to the second file.

The main purpose of these queries is to **standardize mixed date formats**.

---

# 22. Cleaning `Accounts.OpenDate`

```sql
UPDATE Accounts
SET OpenDate = 
    CASE
        ...
    END;
```



This modifies existing rows in the Accounts table.

The important concept is:

```sql
UPDATE
```

means:

> Change existing data.

---

# 23. `TRY_CONVERT()`

The first condition is:

```sql
WHEN TRY_CONVERT(date, OpenDate, 101) IS NOT NULL
```



This tries to convert `OpenDate` into a SQL `date`.

The syntax is:

```sql
TRY_CONVERT(data_type, expression, style)
```

Here:

```sql
TRY_CONVERT(date, OpenDate, 101)
```

means:

> Try converting OpenDate into a date using date format style 101.

If conversion succeeds → returns a date.

If conversion fails → returns:

```text
NULL
```

That's why we use:

```sql
IS NOT NULL
```

to check whether conversion succeeded.

---

# 24. Date Style 101

```sql
101
```

represents:

```text
MM/DD/YYYY
```

Example:

```text
03/14/2013
```

So:

```sql
TRY_CONVERT(date, OpenDate, 101)
```

can successfully understand:

```text
03/14/2013
```

---

# 25. Formatting the Converted Date

```sql
FORMAT(
    TRY_CONVERT(date, OpenDate, 101),
    'MM/dd/yyyy'
)
```



First:

```sql
TRY_CONVERT(...)
```

converts the text into an actual date.

Then:

```sql
FORMAT(..., 'MM/dd/yyyy')
```

converts/displays it in the desired format.

For example:

```text
2013-03-14
```

becomes:

```text
03/14/2013
```

---

# 26. Why Multiple `WHEN`s?

The query checks multiple possible formats:

```sql
101
23
111
105
103
```



These correspond to:

| Style | Format     |
| ----: | ---------- |
|   101 | MM/DD/YYYY |
|    23 | YYYY-MM-DD |
|   111 | YYYY/MM/DD |
|   105 | DD-MM-YYYY |
|   103 | DD/MM/YYYY |

So the query is essentially saying:

> "Try to understand this date using several possible formats."

---

# 27. Why `CASE`?

The complete logic is:

```sql
CASE
    WHEN format 101 works
        THEN convert using 101

    WHEN format 23 works
        THEN convert using 23

    WHEN format 111 works
        THEN convert using 111

    WHEN format 105 works
        THEN convert using 105

    WHEN format 103 works
        THEN convert using 103

    ELSE OpenDate
END
```

This is extremely important.

`CASE` works like an **IF / ELSE IF / ELSE** structure.

---

# 28. The `ELSE`

```sql
ELSE OpenDate
```



If none of the date formats work, leave the original value unchanged.

For example, if the data contained:

```text
ABC123
```

the query doesn't know how to convert it.

Instead of replacing it with NULL, it keeps:

```text
ABC123
```

---

# 29. Cleaning Customer Date of Birth

The same approach is applied to:

```sql
Customers.DateOfBirth
```

```sql
UPDATE Customers
SET DateOfBirth =
    CASE
       ...
    END;
```



This handles mixed formats such as:

```text
1980-11-04
21-07-1975
1989/02/20
1995-05-14
04-12-1982
```

and standardizes successful conversions to:

```text
MM/dd/yyyy
```

---

# 30. Cleaning Transaction Dates

Finally:

```sql
UPDATE Transactions
SET Transactiondate =
    CASE
       ...
    END;
```



This does the same thing for:

```text
TransactionDate
```

The query explicitly documents the formats:

```sql
-- MM/DD/YYYY or MM-DD-YYYY
101

-- YYYY-MM-DD
23

-- YYYY/MM/DD
111

-- DD-MM-YYYY
105

-- DD/MM/YYYY
103
```



---

# The Big Picture

The entire SQL exercise is basically creating a **dirty banking dataset for Power BI data-cleaning practice**.

The flow is:

```text
                    SQL SERVER
                        │
                        ▼
                 Create Database
                   Power_BI2
                        │
                        ▼
              Create 3 Tables
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      Customers     Accounts    Transactions
          │            │            │
          └────────────┼────────────┘
                       ▼
                Insert Dirty Data
                       │
                       ▼
              Generate 10,000 rows
                       │
                       ▼
              ┌─────────────────┐
              │ Data Problems   │
              ├─────────────────┤
              │ Mixed dates     │
              │ NULLs           │
              │ Wrong IDs       │
              │ Duplicates      │
              │ Outliers        │
              │ Case mismatch   │
              │ Negative values │
              └─────────────────┘
                       │
                       ▼
                 Clean the dates
                       │
                       ▼
                Load into Power BI
```

## Most important SQL concepts from these queries

You should particularly understand these because they are **very interview-relevant**:

1. `CREATE DATABASE`
2. `USE`
3. `CREATE TABLE`
4. `PRIMARY KEY`
5. `INSERT INTO`
6. `UPDATE`
7. `DROP TABLE`
8. `IF`
9. `CASE WHEN`
10. `TRY_CONVERT()`
11. `CONVERT()`
12. `FORMAT()`
13. `IS NOT NULL`
14. `ROW_NUMBER()`
15. `CTE`
16. `CROSS JOIN`
17. `GETDATE()`
18. `%` modulo operator
19. `NEWID()`
20. `CHECKSUM()`
21. `ABS()`
22. `WHERE`
23. `SELECT *`

**The key idea:** Lecture 1 is primarily **creating realistic dirty data**, while Lecture 2 is primarily **cleaning inconsistent date formats** before the data is used in Power BI.
