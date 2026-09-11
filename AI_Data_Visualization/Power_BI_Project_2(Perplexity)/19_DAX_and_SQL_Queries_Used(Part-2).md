# 1. Overall purpose of the query

You have three tables:

### `Transactions`

Contains transaction-level information:

| TransactionID | AccountID | TransactionDate | Type       | Amount |
| ------------- | --------- | --------------- | ---------- | ------ |
| T001          | A101      | 2025-01-10      | Deposit    | 5000   |
| T002          | A102      | 2025-01-11      | Withdrawal | 2000   |

### `Accounts`

Contains account information:

| AccountID | CustomerID | Type    | OpenDate   | Balance |
| --------- | ---------- | ------- | ---------- | ------- |
| A101      | C001       | Savings | 2020-01-01 | 50000   |
| A102      | C002       | Current | 2021-03-15 | 30000   |

### `Customers`

Contains customer information:

| CustomerID | Name  | Gender | DateOfBirth |
| ---------- | ----- | ------ | ----------- |
| C001       | Rahul | Male   | 1995-05-10  |
| C002       | Priya | Female | 1998-08-20  |

The query combines these into one table:

**Transaction → Account → Customer**

So ultimately you can answer questions such as:

> "What transactions did each customer make, through which account, and for what amount?"

---

# 2. `SELECT`

```sql
SELECT 
    t.TransactionID, 
    t.AccountID AS Transaction_AccountID, 
    t.TransactionDate, 
    t.Type AS TransactionType, 
    t.Amount, 
    t.Description, 
    t.Currency,
```

This specifies **which columns you want in the final dataset**.

The `t.` means the column is coming from the `Transactions` table.

For example:

```sql
t.TransactionID
```

means:

> Take `TransactionID` from the `Transactions` table.

---

## Why `t`?

Later in the query we write:

```sql
Transactions t
```

This gives the `Transactions` table an **alias** called `t`.

So:

```sql
t.TransactionID
```

is simply a shorter way of writing:

```sql
Transactions.TransactionID
```

Aliases make queries easier to read.

---

# 3. `AS Transaction_AccountID`

```sql
t.AccountID AS Transaction_AccountID
```

The `Transactions` table has a column called:

```text
AccountID
```

But the `Accounts` table also has:

```text
AccountID
```

So if you select both, you could end up with two columns having the same name.

Therefore, you rename the transaction-side `AccountID`:

```sql
t.AccountID AS Transaction_AccountID
```

The output column will be called:

```text
Transaction_AccountID
```

### Important:

`AS` is used to create an **alias/temporary name for a column in the result**.

---

# 4. Transaction columns

These:

```sql
t.TransactionID, 
t.AccountID AS Transaction_AccountID, 
t.TransactionDate, 
t.Type AS TransactionType, 
t.Amount, 
t.Description, 
t.Currency,
```

give you:

| Output Column         | Source                 |
| --------------------- | ---------------------- |
| TransactionID         | Transactions           |
| Transaction_AccountID | Transactions.AccountID |
| TransactionDate       | Transactions           |
| TransactionType       | Transactions.Type      |
| Amount                | Transactions           |
| Description           | Transactions           |
| Currency              | Transactions           |

Again, notice:

```sql
t.Type AS TransactionType
```

The original column is called `Type`, but you're renaming it to:

```text
TransactionType
```

This makes it clearer that this `Type` refers to the transaction type.

---

# 5. Account columns

Next:

```sql
a.AccountID AS Account_AccountID, 
a.CustomerID AS Account_CustomerID, 
a.Type AS AccountType, 
a.OpenDate, 
a.Balance,
```

Here `a` is the alias for the `Accounts` table.

So:

```sql
a.AccountID
```

means:

```sql
Accounts.AccountID
```

The output becomes:

| Output Column      | Meaning                             |
| ------------------ | ----------------------------------- |
| Account_AccountID  | Account ID from Accounts            |
| Account_CustomerID | Customer ID associated with account |
| AccountType        | Type of bank account                |
| OpenDate           | Account opening date                |
| Balance            | Account balance                     |

Again, aliases are being used to avoid confusion.

For example:

```sql
a.Type AS AccountType
```

makes it clear that this `Type` refers to the **account type**, not transaction type.

---

# 6. Customer columns

Then:

```sql
c.CustomerID, 
c.Name, 
c.Gender, 
c.DateOfBirth, 
c.Address, 
c.Email, 
c.Phone
```

Here `c` represents the `Customers` table.

So you're bringing customer information into the combined dataset.

The final columns include:

```text
CustomerID
Name
Gender
DateOfBirth
Address
Email
Phone
```

---

# 7. `INTO CombinedBankingDataset`

This is one of the most important parts:

```sql
INTO CombinedBankingDataset
```

It means:

> Take the result of this SELECT query and create a **new table** called `CombinedBankingDataset`.

So this isn't simply displaying the joined data.

It actually creates a new table.

Conceptually:

```text
Transactions
     ↓
   JOIN
     ↓
 Accounts
     ↓
   JOIN
     ↓
 Customers
     ↓
CombinedBankingDataset
```

### Important SQL concept

`SELECT INTO` is commonly used to:

**Create a new table and populate it with the query result.**

---

# 8. `FROM Transactions t`

```sql
FROM Transactions t
```

This tells SQL:

> Start with the `Transactions` table.

And:

```sql
t
```

is its alias.

So throughout the query:

```sql
t.TransactionID
```

means:

```text
Transactions.TransactionID
```

---

# 9. First LEFT JOIN

```sql
Left JOIN Accounts a 
    ON t.AccountID = a.AccountID
```

This joins:

```text
Transactions
```

with:

```text
Accounts
```

using:

```sql
t.AccountID = a.AccountID
```

### Why?

Suppose:

### Transactions

| TransactionID | AccountID | Amount |
| ------------- | --------- | -----: |
| T001          | A101      |   5000 |
| T002          | A102      |   2000 |

### Accounts

| AccountID | CustomerID | Type    |
| --------- | ---------- | ------- |
| A101      | C001       | Savings |
| A102      | C002       | Current |

SQL matches:

```text
Transactions.AccountID
        ↓
Accounts.AccountID
```

So:

```text
T001 → A101 → C001
T002 → A102 → C002
```

---

# 10. Why `LEFT JOIN`?

This is very important.

You used:

```sql
LEFT JOIN
```

That means:

> Keep **all records from the left table**, even if a matching record doesn't exist in the right table.

Here the left table is:

```sql
Transactions
```

So **every transaction will be retained**.

Suppose you have:

### Transactions

| TransactionID | AccountID |
| ------------- | --------- |
| T001          | A101      |
| T002          | A102      |
| T003          | A999      |

But `A999` doesn't exist in `Accounts`.

The result will still contain:

| TransactionID | AccountID | CustomerID |
| ------------- | --------- | ---------- |
| T001          | A101      | C001       |
| T002          | A102      | C002       |
| T003          | A999      | NULL       |

For T003, account/customer information becomes `NULL` because there was no matching account.

That's the major difference between `LEFT JOIN` and `INNER JOIN`.

---

# 11. Second LEFT JOIN

Then you have:

```sql
Left JOIN Customers c 
    ON a.CustomerID = c.CustomerID
```

Now you're taking the result of:

```text
Transactions + Accounts
```

and joining it with:

```text
Customers
```

using:

```sql
a.CustomerID = c.CustomerID
```

So the relationship becomes:

```text
Transaction
     ↓
 Account
     ↓
 Customer
```

---

# 12. Understanding the complete JOIN relationship

The entire relationship can be visualized as:

```text
Transactions
     |
     | AccountID
     ↓
Accounts
     |
     | CustomerID
     ↓
Customers
```

For example:

```text
Transaction T001
       |
       | AccountID = A101
       ↓
Account A101
       |
       | CustomerID = C001
       ↓
Customer C001
       |
       ↓
Rahul
```

Therefore, your final dataset can contain something like:

| TransactionID | Transaction_AccountID | Amount | Account_AccountID | Account_AccountID | CustomerID | Name  |
| ------------- | --------------------- | -----: | ----------------- | ----------------- | ---------- | ----- |
| T001          | A101                  |   5000 | A101              | C001              | C001       | Rahul |

This gives you information from **all three tables in one row**.

---

# 13. Second query: `SELECT *`

After creating the table, you wrote:

```sql
SELECT * 
FROM CombinedBankingDataset
```

This simply means:

> Display all columns and all rows from `CombinedBankingDataset`.

The `*` means **all columns**.

So:

```sql
SELECT *
FROM CombinedBankingDataset
```

is useful for checking the newly created table.

---

# 14. Complete query in simple English

Your entire query essentially says:

> Take every transaction from the `Transactions` table. Match each transaction to its corresponding account using `AccountID`. Then match that account to its corresponding customer using `CustomerID`. Select relevant transaction, account, and customer information. Create a new table called `CombinedBankingDataset` containing this combined information. Finally, display the newly created table.

---

# 15. Why this is useful for Power BI / Data Analysis

This is particularly useful if you're preparing the data for **Power BI reporting**.

Instead of importing three separate tables and doing all the analysis through relationships, you can create a **flattened/combined dataset** containing:

### Transaction information

* Transaction ID
* Transaction date
* Transaction type
* Amount
* Currency
* Description

### Account information

* Account ID
* Account type
* Open date
* Balance

### Customer information

* Customer ID
* Name
* Gender
* Date of Birth
* Address
* Email
* Phone

Then you can easily perform analysis such as:

* Total transaction amount
* Transactions by customer
* Transactions by account type
* Transactions by gender
* Transactions by age
* Transaction trends over time
* Customer spending patterns
* Account balance analysis

---

## ⭐ Key SQL concepts from this query

| SQL Concept                 | Meaning                              |
| --------------------------- | ------------------------------------ |
| `SELECT`                    | Choose columns                       |
| `FROM`                      | Specify source table                 |
| `AS`                        | Rename a column/table temporarily    |
| `LEFT JOIN`                 | Keep all records from left table     |
| `ON`                        | Specify the matching condition       |
| `INTO`                      | Create a new table from query result |
| `*`                         | Select all columns                   |
| Table alias (`t`, `a`, `c`) | Short names for tables               |

### The most important part to remember:

```sql
Transactions t
LEFT JOIN Accounts a
    ON t.AccountID = a.AccountID
LEFT JOIN Customers c
    ON a.CustomerID = c.CustomerID
```

Think of it as:

**Transaction → Account → Customer**

That's the core logic of your query.