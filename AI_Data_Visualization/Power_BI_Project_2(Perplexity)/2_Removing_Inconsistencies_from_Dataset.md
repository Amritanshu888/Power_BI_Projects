# Power BI Project 2 — Data Cleaning: Fixing Inconsistent Date Formats in SQL Server

## 1. Objective of This Session

In the previous session, the three banking tables were created and populated:

1. **Customers**
2. **Accounts**
3. **Transactions**

In this session, the focus is on identifying and fixing **date-format inconsistencies** in these tables.

The important point is that the data may contain dates represented in different formats within the **same column**.

The instructor uses **Perplexity** to generate SQL `UPDATE` statements that standardize the dates.

The overall workflow is:

```text
Identify inconsistent dates
        ↓
Inspect each table
        ↓
Copy problematic data
        ↓
Ask Perplexity for SQL
        ↓
Generate UPDATE statement
        ↓
Execute UPDATE in SSMS
        ↓
Verify with SELECT
        ↓
Repeat for all affected tables
        ↓
Clean dataset ready for analysis
```

---

# 2. Identifying the Problem in the Transactions Table

The instructor first looks at the `Transactions` table.

A simple query is used to inspect the data:

```sql
SELECT *
FROM Transactions;
```

When looking at the date column, inconsistencies are immediately visible.

For example, different records contain dates represented differently:

* `19 7 2025`
* `2025 7 17`
* `16 7 2025`

So although these values represent dates, they don't follow the same format.

### Problem

The same column contains different date representations.

This is a classic **data-quality issue**.

---

# 3. Why Date Consistency Matters

A date column should follow a consistent representation.

If different records use different formats, it can cause problems during:

* Sorting
* Filtering
* Date calculations
* Grouping by month/year
* Time-series analysis
* Power BI visualizations
* DAX calculations
* Power Query transformations

For example, Power BI needs to correctly recognize a value as a **date** rather than treating it as inconsistent text.

Therefore, before using the data for reporting, the dates need to be standardized.

---

# 4. Check the Customers Table

The same problem exists in the `Customers` table.

The relevant column is:

**Date of Birth**

The instructor executes:

```sql
SELECT *
FROM Customers;
```

When inspecting the output, inconsistent date values are visible.

For example, one record may have a date resembling:

```text
1980 11 4
```

while another may have:

```text
21 7 1975
```

Again, the same column contains different date arrangements.

---

# 5. Check the Accounts Table

The third table is:

**Accounts**

The instructor again executes:

```sql
SELECT *
FROM Accounts;
```

The Accounts table also contains a date column with inconsistent date representations.

Therefore, the issue is not limited to Transactions.

It exists across:

```text
Customers
Accounts
Transactions
```

---

# 6. Overall Data-Quality Problem

At this point, the situation can be summarized as:

| Table        | Date Column          | Problem                  |
| ------------ | -------------------- | ------------------------ |
| Customers    | Date of Birth        | Inconsistent date format |
| Accounts     | Relevant date column | Inconsistent date format |
| Transactions | Transaction Date     | Inconsistent date format |

The goal is to standardize all of them.

---

# 7. Use Perplexity to Solve the Date Problem

Instead of manually fixing individual records, the instructor uses Perplexity to generate an SQL query.

For the Accounts table, the prompt essentially asks:

> The date column is not consistent. Write a SQL query that will bring the dates in all records to a consistent format.

The instructor specifies a desired format similar to:

```text
MM/DD/YYYY
```

The idea is that every record should follow the same date representation.

---

# 8. First AI Output — SELECT vs UPDATE

Initially, Perplexity provides a `SELECT` statement.

A `SELECT` statement is useful for **displaying/converting values in the query output**, but it does not permanently modify the data.

The instructor specifically needs to **change the stored data**.

Therefore, an:

```sql
UPDATE
```

statement is required.

This is an important distinction:

### SELECT

Used to view/retrieve data.

```sql
SELECT ...
```

### UPDATE

Used to modify existing data.

```sql
UPDATE ...
SET ...
```

Since the goal is to permanently correct the inconsistent date values, the instructor uses the `UPDATE` statement.

---

# 9. Fix the Accounts Table

Perplexity provides an `UPDATE` statement for the Accounts table.

The instructor:

1. Copies the generated `UPDATE` statement.
2. Goes back to SQL Server Management Studio.
3. Opens a new query window.
4. Pastes the query.
5. Selects the query.
6. Executes it.

The result shows:

> **5 rows impacted**

This indicates that five records were updated.

---

# 10. Verify the Accounts Table

After updating the data, the instructor returns to the Accounts query.

A simple query is executed:

```sql
SELECT *
FROM Accounts;
```

The instructor checks the date column again.

Previously:

```text
Different formats
```

After the update:

```text
Consistent format
```

Therefore, the date inconsistency in the Accounts table has been corrected.

---

# 11. Fix the Customers Table

The same process needs to be performed on the Customers table.

The problematic column here is:

**Date of Birth**

The instructor first inspects the data again.

A `SELECT` query is used:

```sql
SELECT *
FROM Customers;
```

The output confirms that inconsistent dates exist in the Date of Birth column.

---

# 12. Ask Perplexity to Generate the Customers UPDATE Statement

The instructor copies the relevant customer data and provides it to Perplexity.

The prompt essentially asks:

> There is similar date inconsistency here as well. Write a SQL query to update the date to the required format.

The desired format is again the standardized date format.

Perplexity generates an `UPDATE` statement for the `Customers` table.

---

# 13. Execute the Customers UPDATE Statement

In SSMS:

1. Click **New Query**.
2. Paste the generated UPDATE statement.
3. Select the query.
4. Execute it.

The result shows:

> **5 rows impacted**

Therefore, five customer records have been updated.

---

# 14. Verify Customers Data

Now execute:

```sql
SELECT *
FROM Customers;
```

Inspect the **Date of Birth** column.

Previously, different records had different date arrangements.

After the update, the dates are now consistently represented.

So the Customers table has also been cleaned.

---

# 15. Transactions Table — Special Situation

The Transactions table presents a slightly different situation.

Unlike Customers and Accounts, the Transactions table contains:

> **10,000 records**

The instructor therefore does not want to manually inspect and fix individual records.

Instead, the SQL should handle **all possible inconsistent date cases**.

The relevant column name needs to be identified first.

---

# 16. Identify the Transactions Date Column

The instructor checks the Transactions table and identifies the date column.

The column is named:

```text
Transaction Date
```

So the prompt to Perplexity must refer to this exact column.

---

# 17. Ask Perplexity to Handle All Date Cases

The instructor gives Perplexity a more comprehensive requirement.

The request is essentially:

> I have a Transactions table with a date column named Transaction Date. It contains 10,000 records and may contain different date formats. Considering all possible cases, write an UPDATE statement that will handle the inconsistencies and bring all dates into a consistent format.

The goal is to make sure that **all 10,000 records** are handled.

This is better than manually correcting individual records.

---

# 18. Why Consider All Possible Cases?

Because the Transactions table contains 10,000 records, there could potentially be many variations.

The SQL should therefore account for the different ways the generated data may represent dates.

The objective is:

```text
Different date representations
          ↓
Identify/interpret them
          ↓
Convert them
          ↓
Standardized date representation
```

This makes the cleanup scalable.

---

# 19. Copy the Transactions UPDATE Statement

After Perplexity generates the query:

1. Copy the complete `UPDATE` statement.
2. Return to SQL Server Management Studio.
3. Open a **New Query** window.
4. Paste the statement.

---

# 20. Execute the Transactions UPDATE

Select the UPDATE statement and execute it.

The result shows:

> **10,000 rows impacted**

This is an important result.

It indicates that the update operation processed all 10,000 transaction records.

---

# 21. Verify Transactions Data

After executing the UPDATE, the instructor runs:

```sql
SELECT *
FROM Transactions;
```

The data is inspected again.

Previously, inconsistent date representations were visible.

After the UPDATE, the dates now appear consistently formatted.

The instructor checks the visible records to ensure that no obvious inconsistent case remains.

---

# 22. Final Verification

The instructor confirms that there is no obvious remaining date-format inconsistency.

Therefore:

### Before cleaning

```text
19 7 2025
2025 7 17
16 7 2025
```

Different representations.

### After cleaning

All records follow the required consistent date representation.

The exact display formatting is less important than ensuring the column has a **consistent, correctly interpreted date value**.

---

# 23. Important SQL Concept — SELECT vs UPDATE

This session demonstrates an important SQL distinction.

### `SELECT`

Used to inspect data:

```sql
SELECT *
FROM Transactions;
```

It does **not permanently modify the table**.

### `UPDATE`

Used to modify existing records:

```sql
UPDATE TableName
SET ColumnName = ...
WHERE ...;
```

It permanently changes the stored values.

Therefore, when cleaning existing data:

> Use `UPDATE` when the objective is to modify the underlying records.

---

# 24. Important Concept — Always Verify an UPDATE

After running an UPDATE statement, don't simply assume it worked.

Use a `SELECT` query afterward.

The workflow should be:

```text
UPDATE
  ↓
Check "rows impacted"
  ↓
SELECT
  ↓
Inspect corrected data
```

For example:

```sql
UPDATE Accounts
...
```

Then:

```sql
SELECT *
FROM Accounts;
```

Likewise for Customers and Transactions.

---

# 25. Rows Impacted as a Validation Signal

The instructor observes:

### Accounts

```text
5 rows impacted
```

### Customers

```text
5 rows impacted
```

### Transactions

```text
10,000 rows impacted
```

These messages provide an immediate indication of how many records were affected by the update.

However, **rows impacted alone is not sufficient validation**. The resulting data should still be inspected.

---

# 26. Complete Data-Cleaning Workflow

The entire session can be remembered using this process:

```text
              SQL Server Data
                    │
                    ↓
             Inspect tables
                    │
                    ↓
          Identify date issues
                    │
        ┌───────────┼───────────┐
        ↓           ↓           ↓
   Customers     Accounts   Transactions
        │           │           │
        ↓           ↓           ↓
   Perplexity    Perplexity   Perplexity
        │           │           │
        ↓           ↓           ↓
     UPDATE       UPDATE       UPDATE
        │           │           │
        ↓           ↓           ↓
    Verify       Verify       Verify
        │           │           │
        └───────────┼───────────┘
                    ↓
          Clean, consistent dates
                    ↓
             Ready for Power BI
```

---

# 27. Why This Is Important for Power BI

The ultimate objective is not merely to make SQL Server data look cleaner.

The cleaned data will eventually be imported into **Power BI** for reporting and analysis.

Consistent dates are particularly important for:

* Date filtering
* Date slicers
* Monthly trends
* Yearly trends
* Time-series charts
* Date hierarchies
* DAX time-intelligence functions
* KPI calculations

For example, if Power BI correctly recognizes `Transaction Date` as a date field, you can later analyze:

```text
Transaction Amount by Year
Transaction Amount by Month
Debit vs Credit by Month
Monthly Transaction Count
```

---

# 28. Role of AI in This Session

The session demonstrates another practical use of AI in data analytics.

Perplexity is being used to:

* Analyze the data problem
* Generate SQL
* Convert date representations
* Generate UPDATE statements
* Handle multiple date cases
* Help troubleshoot/clean the database

But the important principle remains:

> **AI generates the solution; the analyst validates the solution.**

The SQL is always executed and checked in SSMS.

---

# 29. Resource Files

The instructor mentions that the **UPDATE statements will be provided in the resource section**.

Therefore, learners do not necessarily need to recreate the queries themselves.

They can:

1. Download/copy the provided SQL.
2. Open SSMS.
3. Select the appropriate database.
4. Execute the UPDATE statements.
5. Verify the corrected data.

The instructor also recommends following the process rather than simply copying the final answer because the purpose is to understand how the data-cleaning problem is identified and solved.

---

# 30. Final State of the Dataset

After completing this session:

| Table        | Issue                         | Action | Result                      |
| ------------ | ----------------------------- | ------ | --------------------------- |
| Customers    | DOB format inconsistent       | UPDATE | Dates standardized          |
| Accounts     | Date format inconsistent      | UPDATE | Dates standardized          |
| Transactions | Transaction Date inconsistent | UPDATE | 10,000 records standardized |

The banking dataset is now considered ready for the next stage of the project.

---

# 31. What Was Learned in This Session

### Data Quality

Real-world datasets may contain inconsistent formatting even when the values represent the same type of information.

### Date Standardization

Dates should be consistently represented and correctly interpreted.

### SQL UPDATE

Use `UPDATE` to modify existing records.

### Data Validation

Always verify changes using `SELECT`.

### AI-Assisted SQL

AI can generate SQL cleaning queries, but those queries should be tested.

### Handling Large Datasets

For 10,000 records, don't manually fix individual rows. Generate a query that can handle the entire dataset.

### Error/Output Validation

Check how many rows were affected and inspect the resulting data.

---

# 32. Exam/Interview-Style Notes

### Q: Why was the date column cleaned?

Because the same column contained dates in different formats, which can cause problems with analysis, filtering, sorting, and Power BI date operations.

### Q: Why use UPDATE instead of SELECT?

`SELECT` only retrieves/displays data, whereas `UPDATE` modifies the stored records.

### Q: How was the Accounts table cleaned?

An UPDATE statement generated with Perplexity was executed against the Accounts table, updating five affected records, followed by a SELECT query to verify the result.

### Q: How was the Customers table cleaned?

The Date of Birth column was identified as inconsistent, an UPDATE statement was generated, five records were updated, and the table was then rechecked.

### Q: Why was a different approach needed for Transactions?

Because Transactions contains **10,000 records**, so the solution needed to handle the entire column programmatically rather than manually correcting individual records.

### Q: What is the Transactions date column called?

**Transaction Date**

### Q: How many transaction rows were affected?

**10,000 rows.**

### Q: What should you do after an UPDATE?

Run a `SELECT` query and inspect the result to confirm that the data was actually corrected.

---

# 33. Final Revision Summary

> In this session, the banking dataset created in the previous session was cleaned by identifying inconsistent date formats in the **Customers, Accounts, and Transactions** tables. Perplexity was used to generate SQL `UPDATE` statements to standardize the dates. Five records were updated in the Accounts table, five in the Customers table, and all 10,000 transaction records were processed. Each update was followed by a `SELECT` query to verify the results. After the cleanup, the dataset was considered ready for further Power BI analysis and reporting.
