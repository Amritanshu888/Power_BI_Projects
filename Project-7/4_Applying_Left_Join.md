# Power BI Project — Data Profiling, Validation, LEFT JOIN & Creating a Combined Table in SQL Server

## 1. Session Overview

In the previous session, the data was imported into **Microsoft SQL Server** under the **test environment**.

Two tables were created:

1. `products`
2. `test_environment_inventory_data_set`

In this session, the instructor focuses on:

* Understanding and profiling the data.
* Checking the number of distinct values.
* Checking for `NULL`/blank values.
* Understanding the test environment versus production environment.
* Checking specific columns such as Product ID, Order Date, Availability and Demand.
* Understanding the meaning of zero availability.
* Joining the two tables using a **LEFT JOIN**.
* Avoiding duplicate `Product ID` columns in the joined result.
* Creating a new combined table from the JOIN result.
* Preparing a single table that can eventually be connected to Power BI.

---

# 2. Tables Available

The project currently has two tables in SQL Server.

### Table 1 — Products

Contains product-related information:

| Column       | Description                      |
| ------------ | -------------------------------- |
| Product ID   | Unique identifier of the product |
| Product Name | Name of the product              |
| Unit Price   | Price of one unit of the product |

---

### Table 2 — Test Environment Inventory Dataset

Contains inventory/demand-related information:

| Column       | Description                    |
| ------------ | ------------------------------ |
| Order Date   | Date associated with the order |
| Product ID   | Identifier of the product      |
| Availability | Number of units available      |
| Demand       | Number of units demanded       |

---

# 3. Understanding the Products Table

The first step is to inspect the Products table.

The instructor executes a simple:

```sql
SELECT *
FROM products;
```

The result shows the available product information.

---

## Products Table Findings

The instructor observes:

* There are **20 distinct Product IDs**.
* Each Product ID corresponds to a product.
* Product names are available for the respective Product IDs.
* Unit prices are available.
* There are no obvious `NULL` or blank values.
* There are no other problematic values that need immediate treatment.

Therefore:

> **The Products table looks clean and ready to use.**

---

# 4. Understanding the Inventory Dataset

The instructor then executes a simple SELECT query against:

```text
test_environment_inventory_data_set
```

The table contains:

> **99 records**

Because the data volume is small, it is possible to scroll through the results and manually inspect the records.

The instructor checks the four columns:

* Order Date
* Product ID
* Availability
* Demand

No obvious `NULL` or blank values are found.

Therefore, at this stage, the inventory data also appears reasonably clean.

---

# 5. Why Data Profiling Is Important

Before using data for reporting, we should understand what is actually present in the dataset.

Data profiling can help answer questions such as:

* How many records are there?
* How many distinct products exist?
* What dates are available?
* What values exist in Availability?
* What values exist in Demand?
* Are there `NULL` values?
* Are there unexpected values?
* Are there duplicates or discrepancies?

This is an important step before building a Power BI report.

---

# 6. Checking Distinct Product IDs

The instructor wants to verify the Product IDs in the inventory table.

Instead of:

```sql
SELECT *
```

we select only:

```text
Product ID
```

and use `DISTINCT`.

The general query is:

```sql
SELECT DISTINCT Product_ID
FROM dbo.test_environment_inventory_data_set;
```

The instructor checks the distinct Product IDs.

### Result

There are:

> **20 distinct Product IDs**

This matches the number of products observed in the Products table.

This is a useful validation step.

---

# 7. Why Check Distinct Product IDs?

Suppose the Products table contains Product IDs from:

```text
1 → 20
```

We should verify that the inventory table is also using the expected Product IDs.

If unexpected values appeared, such as:

```text
25
50
ABC
NULL
```

then we would need to investigate them before using the data.

This is particularly important when preparing data for a Power BI data model.

---

# 8. Test Environment vs Production Environment

The instructor makes an important distinction here.

The data currently being examined belongs to the:

> **Test Environment**

Test data can potentially contain:

* Incorrect data
* Missing data
* Discrepancies
* Unexpected values
* Data-quality issues

This is possible because the test environment is used during development and testing.

---

# 9. Why Production Data Is Different

Once the report has been:

* Developed
* Tested
* Validated
* Approved

it can eventually be moved to the production environment.

Production reports are generally used for:

> **Business decision-making**

Therefore, production data and reports need to be reliable and accurate.

The instructor emphasizes that once the report is running against production data:

> **Correct numbers must be shown.**

---

# 10. Data Cleaning in Test vs Production

It is still important to check the test environment for data-quality problems.

For example:

```text
Test Environment
       ↓
Profile Data
       ↓
Find Issues
       ↓
Clean / Handle Issues
       ↓
Build & Test Report
```

However, the final production environment should provide reliable data because business decisions may depend on the resulting reports and dashboards.

---

# 11. Checking Distinct Values in Other Columns

The same technique used for Product ID can be applied to other columns.

For example:

```sql
SELECT DISTINCT Order_Date
FROM dbo.test_environment_inventory_data_set;
```

Similarly, we can check:

* Order Date
* Availability
* Demand
* Product ID
* Other columns

The general pattern is:

```sql
SELECT DISTINCT column_name
FROM table_name;
```

This is a simple but useful data-profiling technique.

---

# 12. Checking Distinct Order Dates

The instructor replaces `Product ID` with:

> **Order Date**

and executes the query.

The result contains:

> **93 distinct dates**

However, the table has:

> **99 total records**

So:

```text
Total records       = 99
Distinct Order Dates = 93
```

This tells us that some dates appear more than once.

That is completely possible because multiple records/products can be associated with the same date.

---

# 13. Important Distinction — Rows vs Distinct Values

This is an important data-profiling concept.

Suppose we have:

| Order Date |
| ---------- |
| Jan 1      |
| Jan 1      |
| Jan 2      |
| Jan 3      |

There are:

```text
4 total rows
3 distinct dates
```

Therefore:

> **Distinct values are not necessarily equal to the total number of records.**

In this dataset:

```text
99 records
93 distinct dates
```

---

# 14. Checking Availability Values

The instructor then checks the distinct values in:

> **Availability**

The query follows the same pattern:

```sql
SELECT DISTINCT Availability
FROM dbo.test_environment_inventory_data_set;
```

The result contains:

> **22 distinct availability values**

---

# 15. Important Finding — Availability = 0

One important value found in the Availability column is:

```text
Availability = 0
```

This is meaningful from the business perspective.

If:

```text
Availability = 0
```

then there are no units available for the product at that point.

If there is customer demand at that time, the demand cannot be fulfilled.

For example:

```text
Availability = 0
Demand       = 50
```

Then:

```text
Shortage = 50 units
```

---

# 16. Relationship to Supply Shortage

The business logic discussed previously was:

```text
Demand > Availability
        ↓
Supply Shortage
```

Therefore, when Availability is zero and Demand is greater than zero:

```text
Availability = 0
Demand       > 0
        ↓
Demand cannot be fulfilled
        ↓
Supply shortage
```

This information will eventually contribute to the KPI:

> **Total Supply Shortage**

---

# 17. Checking Demand Values

The instructor also checks the distinct values in the:

> **Demand**

column.

The process is the same as for Availability.

Replace:

```text
Availability
```

with:

```text
Demand
```

and execute the query.

This allows us to understand the different demand values present in the dataset.

The instructor also confirms that there are no obvious `NULL` or blank values requiring correction.

---

# 18. Data Profiling Summary

At this point, the instructor has inspected:

| Item                         |                     Finding |
| ---------------------------- | --------------------------: |
| Total inventory records      |                      **99** |
| Distinct Product IDs         |                      **20** |
| Distinct Order Dates         |                      **93** |
| Distinct Availability values |                      **22** |
| Products                     | **20 distinct Product IDs** |
| Obvious NULL/blank values    |           **None observed** |

The exact distinct Demand count is not stated in the transcript, so it should **not be assumed**.

---

# 19. Combining the Two Tables

The project currently has two separate tables:

```text
Products
```

and:

```text
Test Environment Inventory Data Set
```

The instructor wants to combine them.

### Why?

The goal is to eventually have a single table containing information such as:

* Order Date
* Product ID
* Availability
* Demand
* Product Name
* Unit Price

This combined data can then be used as a source for Power BI.

---

# 20. Choosing the JOIN

The instructor decides to use a:

> **LEFT JOIN**

The two tables are connected using:

```text
Product ID
```

The inventory table is treated as the **left table**, while the Products table is treated as the **right table**.

Conceptually:

```text
Inventory Dataset
       │
       │ Product ID
       ↓
    LEFT JOIN
       ↑
       │ Product ID
       │
   Products
```

---

# 21. Why LEFT JOIN?

The inventory table contains the transaction/inventory records we want to retain.

It has:

> **99 records**

The Products table provides additional product information.

Therefore, the objective is essentially:

> Keep the inventory records and bring the matching product information from the Products table.

A LEFT JOIN is suitable for this requirement.

---

# 22. Creating Table Aliases

Instead of repeatedly writing the long table names, aliases are assigned.

The inventory table is given alias:

```text
a
```

The Products table is given alias:

```text
b
```

Conceptually:

```sql
FROM inventory_table AS a
LEFT JOIN products AS b
```

This makes the SQL query shorter and easier to read.

---

# 23. Basic LEFT JOIN Query

The instructor first creates a query conceptually like:

```sql
SELECT *
FROM dbo.test_environment_inventory_data_set AS a
LEFT JOIN dbo.products AS b
    ON a.Product_ID = b.Product_ID;
```

The JOIN condition is:

```text
a.Product_ID = b.Product_ID
```

This means:

> Match records from the inventory table with records in the Products table when their Product IDs are the same.

---

# 24. Result of the LEFT JOIN

The result contains:

> **99 records**

This is expected because the inventory table contains 99 records and it is the left table.

The output contains:

### From inventory table

* Order Date
* Product ID
* Availability
* Demand

### From Products table

* Product ID
* Product Name
* Unit Price

---

# 25. Problem — Duplicate Product ID

There is an issue with using:

```sql
SELECT *
```

after the JOIN.

Both tables contain:

```text
Product ID
```

Therefore, the result contains Product ID twice.

Conceptually:

```text
Order Date
Product ID       ← from table A
Availability
Demand
Product ID       ← from table B
Product Name
Unit Price
```

There is no need to keep both copies.

---

# 26. Better Approach — Explicitly Select Columns

Instead of:

```sql
SELECT *
```

the instructor explicitly specifies the required columns.

This gives us better control over:

* Column selection
* Column order
* Duplicate columns
* Final table structure

---

# 27. Selecting Columns from Table A

From the inventory table (`a`), select:

```text
a.Order_Date
a.Product_ID
a.Availability
a.Demand
```

---

# 28. Selecting Columns from Table B

From the Products table (`b`), select:

```text
b.Product_Name
b.Unit_Price
```

Notice that:

> `b.Product_ID` is intentionally not selected.

Why?

Because `a.Product_ID` has already been selected.

Therefore, we don't need the second copy.

---

# 29. Improved JOIN Query

The query becomes conceptually:

```sql
SELECT
    a.Order_Date,
    a.Product_ID,
    a.Availability,
    a.Demand,
    b.Product_Name,
    b.Unit_Price
FROM dbo.test_environment_inventory_data_set AS a
LEFT JOIN dbo.products AS b
    ON a.Product_ID = b.Product_ID;
```

This produces a much cleaner result.

---

# 30. Result After Removing Duplicate Product ID

The output now contains only one Product ID.

The final structure is:

| Column       |
| ------------ |
| Order Date   |
| Product ID   |
| Availability |
| Demand       |
| Product Name |
| Unit Price   |

This is exactly the type of combined dataset required for subsequent reporting.

---

# 31. Why Explicit Column Selection Is Better

Using:

```sql
SELECT *
```

is convenient for exploration.

But when creating a final dataset for reporting, explicitly selecting columns is often preferable.

### `SELECT *`

Can cause:

* Duplicate columns
* Unnecessary columns
* Uncontrolled column order
* Problems when source tables change

### Explicit selection

Provides:

* Cleaner output
* Better control
* Easier maintenance
* No unnecessary columns
* Better preparation for Power BI

---

# 32. Creating a New Combined Table

The instructor now wants to physically store the JOIN result in a new table.

The objective is:

```text
Products
      +
Inventory
      ↓
LEFT JOIN
      ↓
Combined Data
      ↓
New Table
```

The new table is named:

```text
New Table
```

---

# 33. First Attempt — INSERT INTO

The instructor initially attempts to use:

```sql
INSERT INTO new_table
SELECT ...
```

The query fails with an error similar to:

> **Invalid object name 'new table'**

---

# 34. Why Did INSERT INTO Fail?

The problem is that:

> The table `new_table` does not exist yet.

`INSERT INTO` is generally used when you already have a target table into which records should be inserted.

Conceptually:

```text
Existing Table
      ↓
INSERT INTO
      ↓
Add Records
```

But here, the instructor wants to **create a new table from the query result**.

Therefore, `INSERT INTO` isn't appropriate for creating the table from scratch.

---

# 35. Solution — SELECT INTO

Instead, the instructor changes the query to:

```sql
SELECT *
INTO new_table
FROM (...);
```

`SELECT INTO` is useful when you want to:

> Create a new table and populate it with the result of a SELECT query.

Conceptually:

```text
SELECT Query Result
        ↓
    SELECT INTO
        ↓
  New Table Created
        ↓
Data Automatically Inserted
```

---

# 36. Using the JOIN as a Subquery

The existing JOIN query is placed inside a subquery.

Conceptually:

```sql
SELECT *
INTO new_table
FROM
(
    SELECT
        a.Order_Date,
        a.Product_ID,
        a.Availability,
        a.Demand,
        b.Product_Name,
        b.Unit_Price
    FROM dbo.test_environment_inventory_data_set AS a
    LEFT JOIN dbo.products AS b
        ON a.Product_ID = b.Product_ID
) AS x;
```

Here:

```text
x
```

is the alias given to the subquery.

---

# 37. Understanding the Query Structure

The query has two levels.

### Inner query

The inner query performs the JOIN:

```text
Inventory
    +
Products
    ↓
LEFT JOIN
    ↓
Combined result
```

### Outer query

The outer query creates the new table:

```text
Combined result
       ↓
SELECT INTO
       ↓
new_table
```

---

# 38. Successful Table Creation

After changing from `INSERT INTO` to `SELECT INTO`, the query executes successfully.

The result indicates:

> **99 rows impacted**

This makes sense because the inventory table had 99 records and the LEFT JOIN preserved those records.

The new table is now created.

---

# 39. Verifying the New Table

The instructor then runs:

```sql
SELECT *
FROM new_table;
```

The result shows the combined data.

The table contains the data obtained by joining the two original tables.

---

# 40. Final Combined Table

The resulting table conceptually looks like:

| Order Date | Product ID | Availability | Demand | Product Name | Unit Price |
| ---------- | ---------- | -----------: | -----: | ------------ | ---------: |
| Date 1     | 1          |          ... |    ... | Product A    |        ... |
| Date 2     | 2          |          ... |    ... | Product B    |        ... |
| Date 3     | 3          |          ... |    ... | Product C    |        ... |

The exact values aren't specified in the transcript, so only the structure should be remembered.

---

# 41. Why Create a Combined Table?

The instructor wants to eventually use this combined dataset as a data source for Power BI.

Instead of connecting Power BI separately to:

```text
Products
```

and:

```text
Inventory
```

the project can use:

```text
New Table
```

which already contains the required information.

Conceptually:

```text
Products ──────┐
               │
               ↓
            LEFT JOIN
               │
Inventory ─────┘
               ↓
          New Table
               ↓
            Power BI
```

---

# 42. Alternative — Use the JOIN Directly in Power BI

The instructor also mentions another possibility.

Instead of creating `new_table` in SQL Server, the JOIN query itself could potentially be used directly in Power BI.

So there are two approaches:

### Approach 1 — Create a table in SQL Server

```text
SQL Server
    ↓
JOIN
    ↓
New Table
    ↓
Power BI
```

### Approach 2 — Use JOIN query directly

```text
SQL Server
    ↓
JOIN Query
    ↓
Power BI
```

For this project, the instructor chooses to create the new table.

---

# 43. Overall Data Transformation Flow

The complete transformation performed in this session is:

```text
                SQL SERVER
                    │
        ┌───────────┴───────────┐
        ↓                       ↓
   Products              Inventory Dataset
        │                       │
        │ Product ID            │ Product ID
        └───────────┬───────────┘
                    ↓
                LEFT JOIN
                    ↓
            Combined Dataset
                    ↓
               SELECT INTO
                    ↓
                New Table
                    ↓
                 Power BI
```

---

# 44. Data Profiling Flow

Before joining the tables, the instructor follows this general process:

```text
Inspect Table
     ↓
Check Total Records
     ↓
Check Distinct Values
     ↓
Check NULL / Blank Values
     ↓
Check Unexpected Values
     ↓
Understand Business Meaning
     ↓
Join Tables
```

This is an important practical workflow for data analysts.

---

# 45. Important SQL Concepts Learned

## `SELECT DISTINCT`

Used to find unique values.

```sql
SELECT DISTINCT Product_ID
FROM table_name;
```

Useful for:

* Data profiling
* Finding unique categories
* Checking IDs
* Identifying unexpected values

---

## `LEFT JOIN`

Used to combine tables while preserving records from the left table.

```sql
FROM table_A AS a
LEFT JOIN table_B AS b
    ON a.Product_ID = b.Product_ID
```

---

## Table Aliases

Instead of repeatedly using long table names:

```sql
table_name
```

we can use:

```sql
table_name AS a
```

Then reference columns as:

```sql
a.Product_ID
```

---

## Explicit Column Selection

Instead of:

```sql
SELECT *
```

specify exactly what is required:

```sql
SELECT
    a.Order_Date,
    a.Product_ID,
    a.Availability,
    a.Demand,
    b.Product_Name,
    b.Unit_Price
```

---

## `SELECT INTO`

Used to create a new table from a query result:

```sql
SELECT *
INTO new_table
FROM (...);
```

---

# 46. `INSERT INTO` vs `SELECT INTO`

This distinction is particularly important.

| `INSERT INTO`                                 | `SELECT INTO`                                    |
| --------------------------------------------- | ------------------------------------------------ |
| Inserts data into an existing table           | Creates a new table and inserts the query result |
| Target table generally needs to already exist | New table is created                             |
| Used to add rows                              | Used to create/populate a new table              |

### Example

If `new_table` already exists:

```sql
INSERT INTO new_table
SELECT ...
```

If `new_table` doesn't exist:

```sql
SELECT *
INTO new_table
FROM (...);
```

In this lecture, `SELECT INTO` is required because the table does not yet exist.

---

# 47. Important Validation Numbers

Keep these numbers in mind from the lecture:

```text
Products
→ 20 distinct Product IDs

Inventory Dataset
→ 99 total records
→ 20 distinct Product IDs
→ 93 distinct Order Dates
→ 22 distinct Availability values

Joined result
→ 99 records
```

These numbers are useful for validating that your own implementation is behaving as expected.

---

# 48. Practical Validation Checklist

When following the lecture yourself, verify:

### Products table

* [ ] Products table exists.
* [ ] 20 distinct Product IDs are present.
* [ ] Product names are available.
* [ ] Unit prices are available.
* [ ] No obvious NULL/blank values.

### Inventory table

* [ ] 99 records are present.
* [ ] 20 distinct Product IDs are present.
* [ ] 93 distinct Order Dates are present.
* [ ] 22 distinct Availability values are present.
* [ ] Availability can contain `0`.
* [ ] No obvious NULL/blank values.

### JOIN

* [ ] Inventory table is the left table.
* [ ] Products table is the right table.
* [ ] JOIN is performed using Product ID.
* [ ] LEFT JOIN is used.
* [ ] Result contains 99 records.
* [ ] Product ID appears only once.

### New table

* [ ] `new_table` is created.
* [ ] It contains the combined data.
* [ ] It contains 99 records.
* [ ] It can be queried using `SELECT *`.

---

# 49. Full Query — Clean Version

A clean version of the main JOIN query is:

```sql
SELECT
    a.Order_Date,
    a.Product_ID,
    a.Availability,
    a.Demand,
    b.Product_Name,
    b.Unit_Price
FROM dbo.test_environment_inventory_data_set AS a
LEFT JOIN dbo.products AS b
    ON a.Product_ID = b.Product_ID;
```

To create the new table:

```sql
SELECT *
INTO new_table
FROM
(
    SELECT
        a.Order_Date,
        a.Product_ID,
        a.Availability,
        a.Demand,
        b.Product_Name,
        b.Unit_Price
    FROM dbo.test_environment_inventory_data_set AS a
    LEFT JOIN dbo.products AS b
        ON a.Product_ID = b.Product_ID
) AS x;
```

Then verify:

```sql
SELECT *
FROM new_table;
```

---

# 50. End-to-End Session Summary

The entire session can be remembered as:

```text
Previous Session
      ↓
Data imported into SQL Server
      ↓
Two tables available
      ↓
Products + Inventory
      ↓
Profile the data
      ↓
Check total records
      ↓
Check DISTINCT values
      ↓
Check NULL / blank values
      ↓
Understand Availability = 0
      ↓
Validate Product IDs
      ↓
Perform LEFT JOIN
      ↓
Join using Product ID
      ↓
Remove duplicate Product ID
      ↓
Create combined table using SELECT INTO
      ↓
Verify 99 records
      ↓
Combined table ready
      ↓
Use as Power BI data source
```

## ⭐ Core Takeaway

This session demonstrates a very practical **data preparation workflow before Power BI reporting**:

> **Profile → Validate → Join → Transform → Store → Connect to Power BI**

The instructor first understands the two SQL Server tables, checks their values and data quality, then combines them using a **LEFT JOIN on Product ID**. Rather than keeping duplicate Product ID columns, only the required columns are selected. Finally, the joined result is stored as a new table using **`SELECT INTO`**, which can subsequently be used as the data source for the Power BI report.
