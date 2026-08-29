# Power BI: Preparing a MySQL Table for SQL Server → MySQL Report Migration

## 1. Objective of the Session

In the previous sessions, the Power BI report was originally connected to **Microsoft SQL Server**.

Now the client wants to move the data source to **MySQL**.

Before changing the Power BI data source, we need to prepare the data in MySQL in a way that is compatible with the existing Power BI report.

The main requirement is:

> **The new MySQL table must have the same table name and column names as the SQL Server table that the Power BI report was using.**

This is important because the existing Power BI report already contains:

* DAX measures
* DAX calculations
* Visuals
* Relationships
* Report logic

We don't want those existing calculations to break simply because the database has changed.

---

# 2. What We Are Trying to Achieve

The SQL Server environment already contains a table called:

```text
New Table
```

The MySQL database must also contain a table with the equivalent name:

```text
New_Table
```

and the **column names should match the SQL Server version**.

The desired architecture is:

```text
BEFORE

Microsoft SQL Server
        ↓
     New Table
        ↓
     Power BI
```

After migration:

```text
AFTER

MySQL
  ↓
New_Table
  ↓
Power BI
```

The Power BI report itself should remain essentially the same.

---

# 3. Why Must the Table and Column Names Be the Same?

The existing Power BI report contains DAX calculations that refer to specific tables and columns.

For example, a DAX measure might conceptually refer to:

```DAX
SUM('New Table'[Unit_Price])
```

If the new MySQL table has a different table or column name, the existing DAX expressions may no longer work correctly.

Therefore, when migrating the data source:

### Keep consistent:

* Table names
* Column names
* Data structure
* Data types where possible

### Change:

* Underlying database/data source

This allows the existing Power BI model to continue working with minimal changes.

---

# 4. Important Point: SQL Syntax Differs Between Databases

One of the major lessons of this session is:

> **SQL syntax is not necessarily identical across different database systems.**

The code previously written in Microsoft SQL Server cannot always be copied directly into MySQL.

For example, SQL Server and MySQL can have differences in:

* `CREATE TABLE` syntax
* `SELECT INTO`
* Identifier handling
* Table/column naming
* Functions
* Data types
* Other SQL-specific features

Therefore, when migrating from SQL Server to MySQL:

```text
SQL Server SQL Code
        ↓
Modify syntax where required
        ↓
MySQL-compatible SQL Code
```

---

# 5. Open a New Query in MySQL Workbench

Open **MySQL Workbench**.

Click:

**New Query**

This opens a new SQL query window.

---

# 6. Select the Production Database

Before creating the table, specify that we want to work with the `prod` database.

Write:

```sql
USE prod;
```

### Steps

1. Enter:

```sql
USE prod;
```

2. Select the statement.
3. Click **Execute**.

The command should execute successfully.

---

# 7. Understand the Existing SQL Server Logic

Before writing the MySQL code, look at the code previously created in Microsoft SQL Server.

The SQL Server code essentially did the following:

1. Took the **Production Environment Inventory Dataset**.
2. Joined it with the **Products** table.
3. Used a **LEFT JOIN**.
4. Joined the tables using **Product ID**.
5. Created a new table called **New Table**.
6. Selected the required columns.

Conceptually:

```text
Production Inventory
        │
        │ LEFT JOIN
        │ Product ID
        ↓
     Products
        │
        ↓
    New Table
```

---

# 8. Why a LEFT JOIN Is Being Used

The code uses a **LEFT JOIN** between the inventory table and the products table.

Conceptually:

```sql
Inventory A
LEFT JOIN
Products B
ON A.Product_ID = B.Product_ID
```

This means:

> Keep all records from the inventory table and bring matching information from the Products table wherever a match exists.

This is the same business logic that was used in the SQL Server environment.

---

# 9. MySQL Version of the Table Creation

In MySQL, instead of using the exact SQL Server syntax, the lecture creates the table using a different approach.

The basic structure is:

```sql
CREATE TABLE New_Table AS
SELECT ...
FROM ...
LEFT JOIN ...
ON ...;
```

The exact syntax and identifier quoting should match the MySQL environment.

The key idea is:

```text
CREATE TABLE
      ↓
SELECT required columns
      ↓
FROM inventory table
      ↓
LEFT JOIN products table
      ↓
ON Product ID
```

---

# 10. Give Aliases to the Tables

The inventory table is assigned an alias:

```text
A
```

The Products table is assigned an alias:

```text
B
```

So the structure becomes:

```sql
FROM inventory_table A
LEFT JOIN products B
```

This makes the join condition easier to write.

---

# 11. Define the JOIN Condition

The join is performed using Product ID.

Conceptually:

```sql
ON A.`Product ID` = B.`Product ID`
```

The important point is that the **actual MySQL column names** are used.

When typing:

```text
A.
```

MySQL Workbench's IntelliSense/autocomplete can show the available columns.

This makes it easier to identify the correct column names.

---

# 12. MySQL Column Names May Be Different

This is an important practical issue in the migration.

When the Excel data was imported into MySQL, some column names were automatically created differently from their SQL Server counterparts.

For example:

### SQL Server

```text
Product_ID
Product_Name
Unit_Price
```

### MySQL imported table

They may appear more like:

```text
Product ID
Product Name
Unit Price
```

Therefore, we cannot blindly copy the SQL Server query.

We need to use the **actual MySQL column names** when selecting the source columns.

---

# 13. Use Aliases to Preserve the Original Column Names

Although the source column names in MySQL may be different, the **output column names need to match the SQL Server table**.

This is achieved using:

```sql
AS
```

For example, conceptually:

```sql
SELECT
    A.`Order Date` AS Order_Date
```

The source column can have one name, while the resulting column in `New_Table` can have the required SQL Server-compatible name.

This is one of the most important techniques used in this migration.

---

# 14. Column-by-Column Preparation

The lecture prepares the required columns individually.

The objective is:

```text
MySQL Source Column
        ↓
       AS
        ↓
SQL Server-Compatible Output Column Name
```

---

## 14.1 Order Date

The MySQL table has an `Order Date` column.

Select the actual MySQL column and give it the required output alias.

Conceptually:

```sql
A.`Order Date` AS Order_Date
```

The important point is that the **output name** must match the existing Power BI model.

---

## 14.2 Product ID

The MySQL inventory table contains the Product ID column.

Select it from table alias `A`.

Conceptually:

```sql
A.`Product ID` AS Product_ID
```

Again:

* Source name → MySQL naming
* Output name → SQL Server naming

---

## 14.3 Availability

The Availability column already has the appropriate name in MySQL.

Therefore, it can be selected directly.

Conceptually:

```sql
A.Availability
```

---

## 14.4 Demand

Similarly, Demand can be selected directly:

```sql
A.Demand
```

---

## 14.5 Product Name

The Product Name column has a different naming convention in MySQL.

Therefore, select the actual MySQL column and assign the SQL Server-compatible output name.

Conceptually:

```sql
B.`Product Name` AS Product_Name
```

---

## 14.6 Unit Price

The Unit Price column is also selected from the MySQL Products table.

Conceptually:

```sql
B.`Unit Price` AS Unit_Price
```

Again, the output alias is important because Power BI expects the same column naming structure as before.

---

# 15. Why `AS` Is Important in This Migration

Suppose MySQL has:

```text
Product Name
```

but the existing Power BI model expects:

```text
Product_Name
```

We can write:

```sql
B.`Product Name` AS Product_Name
```

Therefore:

```text
Actual MySQL column
        ↓
 Product Name
        ↓
        AS
        ↓
Expected column
        ↓
 Product_Name
```

This allows us to adapt the MySQL schema to the structure expected by the existing Power BI model.

---

# 16. Organize the Columns on Separate Lines

The lecture recommends writing the selected columns in an organized way, with each column on a separate line.

Instead of:

```sql
SELECT A.col1, A.col2, A.col3, B.col1, B.col2
```

write them in a readable format:

```sql
SELECT
    A.column1,
    A.column2,
    A.column3,
    B.column1,
    B.column2
```

This makes the SQL code:

* Easier to read
* Easier to debug
* Easier to modify
* Easier to compare with the SQL Server version

---

# 17. Overall MySQL Query Structure

The query being constructed follows this structure:

```sql
USE prod;

CREATE TABLE New_Table AS
SELECT
    -- Inventory columns
    -- Product columns
    -- Aliases where required
FROM inventory_table A
LEFT JOIN products B
    ON A.Product_ID = B.Product_ID;
```

The exact identifier syntax depends on the actual names generated in MySQL Workbench.

---

# 18. Why We Are Rewriting the Query

The logic remains the same, but the syntax has to be adapted.

### SQL Server

```text
SQL Server syntax
       ↓
Existing table
       ↓
LEFT JOIN
       ↓
New Table
```

### MySQL

```text
MySQL syntax
       ↓
MySQL tables
       ↓
LEFT JOIN
       ↓
New_Table
```

So we are **not changing the business logic**.

We are changing the **database-specific implementation**.

---

# 19. Execute the CREATE TABLE Query

Once the query has been prepared:

1. Select the complete query.
2. Click **Execute/Run**.
3. MySQL should successfully execute the command.

The new table will now be created inside the `prod` database.

---

# 20. Refresh the Schema

After executing the query:

1. Go to the **Schemas** section on the left.
2. Click **Refresh**.
3. Expand the `prod` database.
4. Expand **Tables**.

You should now see:

```text
New_Table
```

or the exact `New_Table` naming used in the exercise.

---

# 21. Verify the New Table

Click the table/data icon for the newly created table.

MySQL Workbench will display the data.

The lecture initially shows the first **1,000 records**.

Since the table contains more records, the display limit is changed to approximately **5,000 records** so that all relevant records can be viewed.

The dataset contains approximately **1,400+ records** in this stage of the exercise.

---

# 22. Verify the Final Structure

The newly created table should contain:

* The required inventory information
* The required product information
* The expected column names
* The expected data

Most importantly, the table should have a structure compatible with the table previously used by Power BI.

---

# 23. The Key Migration Strategy

The overall strategy is:

### Step 1 — Keep the business logic unchanged

The same:

* Inventory data
* Product data
* LEFT JOIN
* Required columns

are used.

### Step 2 — Adapt SQL syntax

Rewrite the SQL Server query using MySQL syntax.

### Step 3 — Adapt source column names

Use the actual names present in MySQL.

### Step 4 — Preserve output column names

Use `AS` aliases to produce the names expected by Power BI.

### Step 5 — Create the same target table

Create `New_Table` in MySQL.

### Step 6 — Connect Power BI

In the next stage, Power BI's data source will be changed from SQL Server to MySQL.

---

# 24. Important Real-World Lesson

When migrating between database technologies, don't assume that:

> **"If the query works in SQL Server, it will work exactly the same way in MySQL."**

It may not.

You may have to modify:

* SQL syntax
* Functions
* Table references
* Column references
* Identifier quoting
* Data types
* Table creation logic

Therefore, database migration often requires **SQL code conversion/adaptation**.

---

# 25. Why We Preserve the Output Schema

The most important Power BI-specific concept is:

```text
Existing Power BI Model
        ↓
Expects specific table/column names
        ↓
MySQL New_Table
        ↓
Must provide those same names
```

This minimizes changes to:

* DAX measures
* DAX calculations
* Visuals
* Filters
* Relationships
* Report pages

The migration should therefore be designed around **schema compatibility**.

---

# 26. Complete Process So Far

The migration process across the previous sessions can now be viewed as:

```text
                 SQL SERVER
                     │
                     ↓
             Existing Report
                     │
                     ↓
              Client changes
              database source
                     │
                     ↓
                   MySQL
                     │
                     ↓
              Create prod DB
                     │
                     ↓
            Import inventory
                     │
                     ↓
             Clean inventory
                     │
                     ↓
             Import Products
                     │
                     ↓
        Rewrite SQL Server query
                     │
                     ↓
           Apply MySQL syntax
                     │
                     ↓
        Preserve output column names
                     │
                     ↓
              Create New_Table
                     │
                     ↓
             Validate the data
                     │
                     ↓
          Connect Power BI to MySQL
```

---

# 27. Important Commands/Concepts From the Session

### Select the database

```sql
USE prod;
```

### Create a table from a query

Conceptually:

```sql
CREATE TABLE New_Table AS
SELECT ...
FROM ...
LEFT JOIN ...
ON ...;
```

### Table aliases

```sql
FROM inventory_table A
LEFT JOIN products B
```

### Join condition

```sql
ON A.Product_ID = B.Product_ID
```

### Rename an output column

```sql
B.`Product Name` AS Product_Name
```

---

# 28. Quick Revision Table

| Concept         | Purpose                                   |
| --------------- | ----------------------------------------- |
| `USE prod`      | Select the Production database            |
| `CREATE TABLE`  | Create the new MySQL table                |
| `SELECT`        | Select required columns                   |
| `LEFT JOIN`     | Combine inventory and product information |
| Table alias `A` | Short reference to inventory table        |
| Table alias `B` | Short reference to Products table         |
| `ON`            | Define the join condition                 |
| `AS`            | Give the output column the required name  |
| Refresh Schema  | Make newly created table visible          |
| Table/Data icon | View the table's data                     |

---

# 29. Final Takeaways

1. **Create the MySQL table before changing the Power BI data source.**
2. The target table should have the **same logical structure and column names** expected by the existing Power BI report.
3. SQL syntax can differ between **SQL Server and MySQL**, so existing queries may need modification.
4. Use **table aliases** to make joins easier to write.
5. Use **`AS` aliases** when MySQL source column names differ from the names expected by Power BI.
6. The same **LEFT JOIN business logic** used in SQL Server is recreated in MySQL.
7. After creating the table, **refresh the schema and verify the data**.
8. Once the MySQL table is ready, the next step is to **change Power BI's data source from SQL Server to MySQL**.
9. The goal is **not to recreate the Power BI report**—the goal is to change its underlying data source while keeping the existing report logic intact.

### Core idea to remember

> **During a database migration, the database and SQL syntax may change, but if you preserve the table/column structure expected by Power BI, you can transition the existing report with far fewer changes to the model and DAX calculations.**
