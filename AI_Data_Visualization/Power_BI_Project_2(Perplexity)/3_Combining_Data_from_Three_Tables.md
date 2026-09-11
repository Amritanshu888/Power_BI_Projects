# Power BI Project 2 — Combining Customers, Accounts & Transactions into One Table

## 1. Objective of the Session

In the previous sessions, three separate banking tables were created and cleaned:

1. **Transactions**
2. **Accounts**
3. **Customers**

In this session, the objective is to **combine all three tables into one physical table** so that the resulting single table can be used as the data source for the Power BI report.

The overall process is:

```text
Transactions
     │
     │ Account ID
     ↓
Accounts
     │
     │ Customer ID
     ↓
Customers
     │
     ↓
Combined Banking Dataset
     │
     ↓
Power BI
```

---

# 2. Why Combine the Tables?

Currently, the information is distributed across three different tables.

### Transactions

Contains transaction-level information and has:

```text
Account ID
```

### Accounts

Contains account information and has:

```text
Account ID
Customer ID
```

### Customers

Contains customer information and has:

```text
Customer ID
```

Therefore, the tables can be connected using their common IDs.

The relationships are:

```text
Transactions.Account ID
          ↓
Accounts.Account ID
```

and:

```text
Accounts.Customer ID
          ↓
Customers.Customer ID
```

---

# 3. Why Start With the Transactions Table?

The Transactions table contains the actual banking transactions.

The requirement is to create a dataset that retains **all transactions**.

Therefore, Transactions should be the **left/base table**.

Conceptually:

```text
Transactions
     LEFT JOIN
Accounts
```

and then:

```text
Result
     LEFT JOIN
Customers
```

This ensures that transaction records are not accidentally lost because of missing/mismatched account or customer information.

---

# 4. Understanding the Join Keys

There are two important keys.

## Account ID

The first relationship is:

```text
Transactions.Account ID
          =
Accounts.Account ID
```

This allows transaction information to be combined with account information.

---

## Customer ID

The second relationship is:

```text
Accounts.Customer ID
          =
Customers.Customer ID
```

This allows account information to be combined with customer information.

Therefore:

```text
Transactions
      │
 Account ID
      ↓
Accounts
      │
 Customer ID
      ↓
Customers
```

---

# 5. First Step — Find All Columns in the Tables

Before asking Perplexity to write the final SQL query, the instructor first wants to know:

> **What columns exist in each of the three tables?**

This is important because the final combined query needs to specify which columns should be selected.

Instead of manually opening every table and noting down the columns, SQL Server's metadata can be queried.

---

# 6. Using INFORMATION_SCHEMA.COLUMNS

The instructor uses:

```sql
INFORMATION_SCHEMA.COLUMNS
```

This is a SQL Server metadata view that provides information about columns in database tables.

The query used is conceptually:

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Transactions';
```

This returns information about the columns belonging to the Transactions table.

---

# 7. Retrieve Transactions Columns

In SSMS:

1. Open a new query or use the existing query window.
2. Write the query:

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Transactions';
```

3. Execute it using **Ctrl + E**.
4. Review the results.
5. Copy the column information, including headers.

The instructor copies the output because these column names will be provided to Perplexity.

---

# 8. Provide Transactions Columns to Perplexity

The copied output is pasted into Perplexity.

The instructor explains that these are the columns from the:

> **Transactions table**

This gives Perplexity the exact structure of the Transactions table rather than asking it to guess the column names.

---

# 9. Retrieve Customers Columns

Next, the same query is used for the Customers table.

Change:

```sql
WHERE TABLE_NAME LIKE 'Transactions'
```

to:

```sql
WHERE TABLE_NAME LIKE 'Customers'
```

Then execute the query.

Conceptually:

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Customers';
```

The output displays the available columns in the Customers table.

---

# 10. Copy Customers Column Information

The instructor copies the Customers column information and pastes it into Perplexity.

The prompt is structured so that Perplexity receives:

```text
These are the columns from Transactions table.

[Transactions columns]

Below are the columns in Customers table.

[Customers columns]
```

This gives the AI the schema of both tables.

---

# 11. Retrieve Accounts Columns

The same process is repeated for Accounts.

Change the table name to:

```sql
Accounts
```

So the query becomes:

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Accounts';
```

Execute the query.

The result displays the columns available in the Accounts table.

---

# 12. Provide Accounts Columns to Perplexity

Copy the Accounts column information.

Then add it to the Perplexity prompt.

The final prompt now contains information about:

```text
Transactions columns
Customers columns
Accounts columns
```

This is important because Perplexity can now build the SQL query using the **actual schema**.

---

# 13. Ask Perplexity to Combine the Tables

The instructor then asks Perplexity to:

> Combine the data from these three tables and create a single table that can ultimately be used for creating the Power BI report.

The requirement is specifically to create a **new physical table**.

So the desired output isn't merely a query that temporarily displays combined data.

The instructor wants an actual table in SQL Server.

---

# 14. Creating a Physical Combined Table

Perplexity provides multiple approaches.

The instructor chooses the query containing:

```sql
SELECT ... INTO ...
```

This is important.

`SELECT INTO` can be used to create a **new table** from the results of a SELECT query.

Conceptually:

```sql
SELECT columns
INTO NewTable
FROM ExistingTable
...
```

The result is a new physical table.

---

# 15. Name of the New Table

The new table is named:

```text
Combined Banking Data Set
```

This table will eventually become the main dataset used for Power BI analysis.

The structure will conceptually be:

```text
Customers + Accounts + Transactions
                    ↓
       Combined Banking Data Set
```

---

# 16. Initial Query Uses INNER JOIN

The first SQL query generated by Perplexity uses `INNER JOIN`.

Conceptually:

```sql
Transactions
INNER JOIN Accounts
INNER JOIN Customers
```

An INNER JOIN only retains records where the joining condition is satisfied.

This becomes a problem because the requirement is to retain **all transaction records**.

---

# 17. Why INNER JOIN Is Not Preferred Here

Suppose Transactions has:

```text
10,000 records
```

but some Transactions records don't have a matching Account ID in Accounts.

With an INNER JOIN:

```text
Transaction without matching Account
          ↓
       Removed
```

Therefore, the resulting table could contain fewer than 10,000 records.

The instructor wants to preserve all transactions.

---

# 18. Drop the Initial Combined Table

The first query is executed, and the result shows:

> **300 rows impacted**

This is not the expected result because the Transactions table contains 10,000 records.

The instructor therefore decides to recreate the combined table using `LEFT JOIN`.

First, the incorrectly created table needs to be removed.

The table is:

```text
Combined Banking Data Set
```

The instructor drops it.

Conceptually:

```sql
DROP TABLE [Combined Banking Data Set];
```

The exact syntax may depend on the table name and spaces used.

After execution, the incorrectly created combined table is removed.

---

# 19. Replace INNER JOIN with LEFT JOIN

The instructor changes the join type from:

```sql
INNER JOIN
```

to:

```sql
LEFT JOIN
```

The reason is:

> **We do not want to miss any records from the Transactions table.**

The Transactions table is the primary/base table.

Therefore:

```text
Transactions
     ↓
 LEFT JOIN
     ↓
Accounts
     ↓
 LEFT JOIN
     ↓
Customers
```

---

# 20. Why LEFT JOIN?

A LEFT JOIN keeps **all records from the left/base table**.

For example:

```text
Transactions = 10,000 rows
```

Even if some transactions don't have matching account/customer information, those transaction rows remain in the output.

The missing information will appear as:

```text
NULL
```

in the columns coming from the table where no matching record exists.

---

# 21. Execute the Revised Query

After changing the joins to LEFT JOIN:

1. Copy the revised SQL.
2. Go to SSMS.
3. Open a new query window if required.
4. Paste the SQL.
5. Select the query.
6. Press **Ctrl + E**.

The execution result shows:

> **10,000 rows impacted**

This is the expected result.

It confirms that all transaction records have been retained.

---

# 22. Validate the Combined Table

After creating the table, the instructor runs a simple SELECT query.

Conceptually:

```sql
SELECT *
FROM [Combined Banking Data Set];
```

The purpose is to inspect the newly created table.

---

# 23. Inspecting the Combined Data

The output now contains information brought together from the three original tables.

Conceptually, the resulting dataset contains:

```text
Transaction information
+
Account information
+
Customer information
```

This gives Power BI a single table containing the information needed for analysis.

---

# 24. NULL Values in the Combined Table

While inspecting the result, the instructor notices some:

```text
NULL
```

values.

This is expected because some joining conditions did not match.

For example:

```text
Transaction Account ID
        ↓
No matching Account ID
        ↓
Account columns = NULL
```

Similarly:

```text
Account Customer ID
        ↓
No matching Customer ID
        ↓
Customer columns = NULL
```

---

# 25. Why Not Fix the NULL Values Immediately?

The instructor decides not to worry about these issues at this stage.

The reason is that the dataset will later be processed in:

**Power BI**

and the instructor says that if necessary, these issues can be handled there.

This is also useful for learning data cleaning and transformation in Power Query.

So the workflow is intentionally:

```text
SQL Server
   ↓
Combine tables
   ↓
Retain all transactions
   ↓
Bring combined data into Power BI
   ↓
Handle remaining data-quality issues
```

---

# 26. Final Combined Dataset

At the end of the session, a new physical table has been created:

**Combined Banking Data Set**

It contains information derived from:

```text
Transactions
Accounts
Customers
```

The final table contains:

> **10,000 records**

because the Transactions table is the base table and a LEFT JOIN is used.

---

# 27. Why the Transactions Table Is the Base Table

This is a particularly important design decision.

The purpose of the report is primarily to analyze banking transactions.

Therefore, Transactions is the table whose records should not be lost.

Using:

```sql
FROM Transactions
LEFT JOIN Accounts
...
LEFT JOIN Customers
...
```

means:

> Keep every transaction, and attach account/customer information whenever a matching record exists.

---

# 28. Join Logic — Easy Way to Remember

Think of the database as a chain:

```text
CUSTOMERS
    ↑
    │ Customer ID
    │
ACCOUNTS
    ↑
    │ Account ID
    │
TRANSACTIONS
```

When creating the combined dataset, follow the chain from the bottom upward:

```text
Transactions
     │
     │ Account ID
     ↓
Accounts
     │
     │ Customer ID
     ↓
Customers
```

---

# 29. SQL Metadata Concept

One of the useful SQL concepts introduced in this session is:

```sql
INFORMATION_SCHEMA.COLUMNS
```

It allows you to inspect database metadata.

For example:

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Transactions';
```

This can help you discover:

* Column names
* Data types
* Maximum lengths
* Ordinal positions
* Other column metadata

This is useful when you don't want to manually inspect table structures.

---

# 30. SELECT INTO Concept

Another important SQL concept is:

```sql
SELECT ... INTO ...
```

It can create a new table from the output of a query.

Conceptually:

```sql
SELECT *
INTO NewTable
FROM ExistingTable;
```

Instead of only displaying the query result, SQL Server creates a new physical table.

In this project, it is used to create:

```text
Combined Banking Data Set
```

---

# 31. INNER JOIN vs LEFT JOIN

This session is especially important for understanding the difference between these two joins.

| Join       | What happens?                                |
| ---------- | -------------------------------------------- |
| INNER JOIN | Only matching records are retained           |
| LEFT JOIN  | All records from the left table are retained |

### Example

Suppose:

```text
Transactions = 10,000
```

and only 300 transactions have matching records across all required joins.

With INNER JOIN:

```text
Result ≈ 300
```

With LEFT JOIN:

```text
Result = 10,000
```

This explains why the first query resulted in only **300 rows impacted**, while the revised LEFT JOIN query resulted in **10,000 rows impacted**.

---

# 32. Important Practical Lesson

The join type should be selected based on the **business requirement**.

Don't automatically use INNER JOIN.

Ask:

> Which records absolutely must remain in my final dataset?

Here:

> **All transactions must remain.**

Therefore:

**Transactions → LEFT JOIN → Accounts → LEFT JOIN → Customers**

is appropriate.

---

# 33. Complete Step-by-Step Workflow

### Step 1 — Inspect Transactions

```sql
SELECT *
FROM Transactions;
```

Identify:

```text
Account ID
```

---

### Step 2 — Inspect Accounts

Identify:

```text
Account ID
Customer ID
```

---

### Step 3 — Inspect Customers

Identify:

```text
Customer ID
```

---

### Step 4 — Retrieve Transactions Metadata

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Transactions';
```

Copy the column information.

---

### Step 5 — Retrieve Customers Metadata

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Customers';
```

Copy the column information.

---

### Step 6 — Retrieve Accounts Metadata

```sql
SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME LIKE 'Accounts';
```

Copy the column information.

---

### Step 7 — Give All Column Information to Perplexity

Tell Perplexity:

* These are Transactions columns.
* These are Customers columns.
* These are Accounts columns.
* Combine them.
* Create one physical table.
* The table will be used for Power BI.

---

### Step 8 — Generate SQL

Use the `SELECT INTO` query generated by Perplexity.

Initially, it uses INNER JOIN.

---

### Step 9 — Execute Initial Query

The result is:

```text
300 rows impacted
```

This indicates that many transactions have been excluded.

---

### Step 10 — Drop Incorrect Table

Remove the initially created combined table:

```sql
DROP TABLE [Combined Banking Data Set];
```

---

### Step 11 — Change INNER JOIN → LEFT JOIN

Use Transactions as the base table.

Conceptually:

```sql
FROM Transactions
LEFT JOIN Accounts
    ON Transactions.AccountID = Accounts.AccountID
LEFT JOIN Customers
    ON Accounts.CustomerID = Customers.CustomerID
```

The exact column names should match the actual schema.

---

### Step 12 — Execute Again

The result:

```text
10,000 rows impacted
```

---

### Step 13 — Validate

Run:

```sql
SELECT *
FROM [Combined Banking Data Set];
```

Inspect the results.

---

### Step 14 — Check NULLs

Some NULL values may exist because certain join conditions did not match.

The instructor chooses to handle such issues later in Power BI if required.

---

# 34. Final Architecture of the Project So Far

After this session, the project looks like:

```text
              SQL SERVER
                  │
       ┌──────────┼──────────┐
       │          │          │
       ↓          ↓          ↓
   Customers   Accounts   Transactions
       │          │          │
       │ Customer │ Account  │
       │ ID       │ ID       │
       └─────┬────┴────┬─────┘
             │         │
             └────┬────┘
                  ↓
      Combined Banking Data Set
                  │
                  ↓
               Power BI
```

---

# 35. Important Takeaways

1. The project initially has **three separate tables**:

   * Customers
   * Accounts
   * Transactions

2. The tables can be connected through:

   * `Account ID`
   * `Customer ID`

3. `INFORMATION_SCHEMA.COLUMNS` can be used to inspect table column metadata.

4. Perplexity is used to generate the SQL required to combine the tables.

5. `SELECT INTO` can create a new physical table from a query result.

6. The first attempt used `INNER JOIN`.

7. Only **300 rows** were produced with the INNER JOIN approach.

8. This was undesirable because the Transactions table contains **10,000 records**.

9. The combined table was dropped.

10. The joins were changed to **LEFT JOIN**.

11. Transactions was kept as the left/base table.

12. The revised query produced **10,000 rows**.

13. Some `NULL` values appeared because some joining conditions did not match.

14. Those issues can be investigated/handled later in Power BI.

15. The resulting **Combined Banking Data Set** will be used as the primary dataset for the Power BI report.

---

# 36. Interview/Revision Questions

### Why combine the three tables?

To create a single dataset containing transaction, account, and customer information for Power BI analysis.

### What is the first join condition?

```text
Transactions.Account ID = Accounts.Account ID
```

### What is the second join condition?

```text
Accounts.Customer ID = Customers.Customer ID
```

### Why was INNER JOIN rejected?

Because it removed unmatched transaction records. The initial result contained only 300 records instead of the required 10,000.

### Why use LEFT JOIN?

To ensure that **all transactions remain** in the final dataset even if corresponding account/customer information is missing.

### Why is Transactions the left table?

Because every transaction needs to be retained for the analysis.

### What happened after changing to LEFT JOIN?

The query produced **10,000 rows**, matching the number of transaction records.

### What does `SELECT INTO` do?

It creates a new physical table from the result of a SELECT query.

### What is `INFORMATION_SCHEMA.COLUMNS` used for?

It provides metadata about columns in database tables, allowing you to inspect the table structure programmatically.

### Why are NULL values present?

Some records don't have a matching value in the related table based on the join condition.

### What will happen next?

The **Combined Banking Data Set** will be used as the data source for the Power BI reporting/analysis stage.

---

## Final Revision Summary

> **In this session, the three SQL Server banking tables—Transactions, Accounts, and Customers—were combined into a single physical table for Power BI analysis. The table schemas were first retrieved using `INFORMATION_SCHEMA.COLUMNS` and provided to Perplexity to generate the SQL. An initial INNER JOIN produced only 300 records, so the combined table was dropped and recreated using LEFT JOINs, keeping Transactions as the base table. This preserved all 10,000 transaction records, although some NULL values remained where account/customer join conditions did not match. The resulting Combined Banking Data Set is now ready to be used for the Power BI report.**
