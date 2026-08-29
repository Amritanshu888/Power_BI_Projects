# MySQL Workbench: Preparing Production Data for Power BI Migration

## 1. Objective of the Session

In the previous sessions, the Power BI report was using **Microsoft SQL Server** as its data source.

The client has now decided to migrate the data source to **MySQL**.

Before connecting Power BI to MySQL, we first need to make sure that the required data is available inside MySQL.

The session therefore focuses on:

1. Opening MySQL Workbench.
2. Creating a Production database.
3. Importing the Production Inventory dataset from Excel.
4. Importing the Product table.
5. Applying the same data-cleaning updates that were performed in SQL Server.
6. Resolving MySQL Safe Update Mode issues.
7. Verifying the imported and cleaned data.
8. Preparing MySQL so that Power BI can use it as the new data source.

---

# 2. Real-World Scenario vs. Practice Scenario

In a real project, the migration of data from SQL Server to MySQL would normally be handled by a **data engineering/backend team**.

For example:

```text
Microsoft SQL Server
        ↓
   Data Engineering Team
        ↓
      MySQL
        ↓
     Power BI
```

The Power BI developer/data analyst would generally not be responsible for performing the entire backend migration.

However, for this project/course, the migration is being performed manually **for practice purposes**.

Therefore, we will directly import the required Excel data into MySQL Workbench.

---

# 3. Open MySQL Workbench

First, open **MySQL Workbench**.

### Steps

1. Locate the MySQL Workbench application.
2. Double-click the MySQL Workbench icon.
3. On the MySQL Workbench home screen, locate the local MySQL instance.
4. Click **Local instance MySQL**.

This opens the MySQL Workbench environment.

---

# 4. Create the Production Database

We need a database corresponding to the Production environment.

The database is named:

```text
prod
```

### SQL

```sql
CREATE DATABASE prod;
```

### Steps

1. Open a new SQL query tab.
2. Write:

```sql
CREATE DATABASE prod;
```

3. Select the statement.
4. Click **Run/Execute**.

The database will be created.

---

# 5. Select the Production Database

After creating the database, we need to tell MySQL that subsequent operations should be performed within the `prod` database.

Use:

```sql
USE prod;
```

### Steps

1. Write:

```sql
USE prod;
```

2. Select the statement.
3. Click **Execute**.

If successful, MySQL reports that the command completed successfully.

---

# 6. Refresh the Schemas

On the left side of MySQL Workbench, you will see the **Schemas** section.

Because the database was just created, it may not immediately appear.

### Steps

1. Go to the **Schemas** section.
2. Click the **Refresh** icon.
3. You should now see:

```text
prod
```

This confirms that the Production database has been created successfully.

---

# 7. Import the Production Inventory Dataset

The next task is to bring the Production inventory data into MySQL.

The source file is the:

**Production Environment Inventory Dataset**

This is the same type of dataset that was previously imported into SQL Server.

---

## Steps to Import the Data

### Step 1 — Open the Data Import Wizard

Right-click the:

```text
prod
```

database/schema.

Select:

**Table Data Import Wizard**

---

### Step 2 — Select the Excel File

The import wizard will ask you to provide the file path.

Click:

**Browse**

Locate the:

**Production Environment Inventory Dataset**

Excel file.

Double-click/select the file.

---

### Step 3 — Continue Through the Wizard

Click:

**Next**

The wizard will display the data and import configuration.

For this exercise, continue using the provided/default configuration.

---

### Step 4 — Create the New Table

The wizard will ask for the table name.

Create the table with the name:

```text
prod environment inventory data set
```

The table will therefore represent the Production inventory dataset inside the `prod` database.

Continue by clicking **Next**.

---

### Step 5 — Review Import Steps

The wizard displays the operations that it is going to perform.

Review them and click **Next**.

The import process will begin.

Once completed, click:

**Next → Finish**

---

# 8. Verify the Imported Inventory Table

After the import is complete:

1. Refresh the `prod` schema if necessary.
2. Expand the **Tables** section.
3. You should see:

```text
prod environment inventory data set
```

This confirms that the Production inventory table has been successfully imported.

---

# 9. View the Imported Data

Click the small table/data icon associated with the table.

MySQL Workbench will execute a SELECT query for you.

Conceptually, the query is:

```sql
SELECT *
FROM prod.`prod environment inventory data set`;
```

This displays the imported Production inventory data.

---

# 10. Reapply the Data Cleaning Performed in SQL Server

Recall from the previous session that the Production inventory data had a Product ID problem.

The Production inventory table contained:

```text
Product ID 21
Product ID 22
```

but the Product dimension only contained 20 valid products.

The data engineering team clarified:

```text
21 → 7
22 → 11
```

In SQL Server, these were corrected using `UPDATE` statements.

Since we are now preparing the same data in MySQL, we need to apply the equivalent updates here as well.

---

# 11. Important Difference in Column Names

There is an important schema difference in the imported MySQL table.

The Product ID column is named:

```text
Product ID
```

rather than:

```text
Product_ID
```

or the exact column naming used previously in SQL Server.

Therefore, when copying the SQL Server update statements into MySQL, the column name needs to be adjusted to match the actual MySQL table.

### General lesson

> SQL statements must use the actual table and column names present in the target database.

---

# 12. Prepare the First UPDATE Statement

We want to replace:

```text
Product ID = 21
```

with:

```text
Product ID = 7
```

Conceptually:

```sql
UPDATE `prod environment inventory data set`
SET `Product ID` = 7
WHERE `Product ID` = 21;
```

Because the table/column names contain spaces, they need to be referenced appropriately in MySQL.

---

# 13. Prepare the Second UPDATE Statement

Similarly, we want:

```text
Product ID = 22
```

to become:

```text
Product ID = 11
```

Conceptually:

```sql
UPDATE `prod environment inventory data set`
SET `Product ID` = 11
WHERE `Product ID` = 22;
```

Therefore, the two required transformations are:

| Existing Product ID | Replacement |
| ------------------: | ----------: |
|                  21 |           7 |
|                  22 |          11 |

---

# 14. MySQL Safe Update Mode Error

When the two UPDATE statements were initially executed, MySQL Workbench produced an error related to:

**Safe Update Mode**

The error essentially indicates that you are trying to update a table without using a sufficiently restrictive `WHERE` condition involving a key column.

MySQL Workbench has **Safe Updates** enabled by default in this setup.

This is a protection mechanism designed to prevent accidentally updating a large number of rows.

---

# 15. Why Safe Update Mode Exists

Imagine accidentally writing:

```sql
UPDATE some_table
SET ProductID = 7;
```

without a `WHERE` clause.

That could modify **every row in the table**.

Safe Update Mode helps protect against such accidental mass updates.

In our case, the update does have a `WHERE` clause, but MySQL Workbench's safe-update rules still reject it because the condition doesn't satisfy its key-column requirement.

---

# 16. Disable Safe Update Mode

To allow these updates to execute:

### Steps

1. Go to the MySQL Workbench menu.
2. Click:

**Edit → Preferences**

3. Open:

**SQL Editor**

4. Scroll down until you find the Safe Updates option.
5. The Safe Updates option is currently enabled.
6. Uncheck/disable it.
7. Click **OK**.

This changes the MySQL Workbench configuration.

---

# 17. Reconnect to MySQL

After changing Safe Update Mode, reconnect to the MySQL instance.

The lecture returns to the MySQL Workbench home screen and reconnects to the local MySQL instance.

This is necessary for the configuration change to take effect.

---

# 18. Select the Production Database Again

After reconnecting, execute:

```sql
USE prod;
```

### Result

The command completes successfully.

This confirms that the `prod` database is selected as the active database.

---

# 19. Verify the Inventory Table

Before running the updates, execute a simple SELECT statement:

```sql
SELECT *
FROM `prod environment inventory data set`;
```

This confirms that:

* The database exists.
* The table exists.
* The data was imported successfully.
* MySQL can read the table.

---

# 20. Execute the Data-Cleaning Updates

Now execute the two UPDATE statements.

### Update 21 → 7

```sql
UPDATE `prod environment inventory data set`
SET `Product ID` = 7
WHERE `Product ID` = 21;
```

### Update 22 → 11

```sql
UPDATE `prod environment inventory data set`
SET `Product ID` = 11
WHERE `Product ID` = 22;
```

The updates should now execute successfully after Safe Update Mode has been disabled.

---

# 21. Verify the Updated Data

After executing the updates, run a SELECT statement again:

```sql
SELECT *
FROM `prod environment inventory data set`;
```

Inspect the resulting data.

The Product ID values that were previously `21` and `22` should now have been replaced by:

```text
21 → 7
22 → 11
```

This ensures that the MySQL data is consistent with the Product dimension, just as it was prepared in SQL Server.

---

# 22. Import the Product Table

The inventory table alone is not sufficient.

The Power BI model also uses the **Product table/dimension**, so this table must also be available in MySQL.

---

## Steps

1. Right-click the `prod` database.
2. Select:

**Table Data Import Wizard**

3. Click **Browse**.
4. Locate the **Products** table/file.
5. Select it.
6. Click **Next**.
7. Continue through the import wizard.
8. Click **Next** as required.
9. Complete the import.
10. Click **Finish**.

---

# 23. Verify the Product Table

After importing:

1. Refresh the `prod` schema.
2. Expand **Tables**.
3. You should now see both tables.

Conceptually:

```text
prod
 └── Tables
      ├── prod environment inventory data set
      └── products
```

Click the table icon for the Products table to view its data.

This confirms that the Product dimension has also been imported.

---

# 24. Final MySQL Database Structure

At this point, the MySQL Production database contains the required tables.

Conceptually:

```text
MySQL
  │
  └── prod
       │
       ├── prod environment inventory data set
       │
       └── products
```

This provides the basic data structure needed for the Power BI report.

---

# 25. Why Are We Doing the Same Data Preparation Again?

The SQL Server database and MySQL database are now separate data sources.

The cleaning performed in SQL Server does **not automatically carry over** to MySQL.

Therefore, when the data is migrated:

```text
SQL Server
    ↓
Cleaned Data
```

does not mean:

```text
MySQL
    ↓
Automatically Cleaned Data
```

The corresponding transformations must exist in the MySQL version of the data as well.

---

# 26. Real-World Responsibility

Again, in an actual organization, this migration and backend preparation would normally be handled by a dedicated team.

For example:

```text
Data Engineering Team
        ↓
Migrate SQL Server → MySQL
        ↓
Create required tables
        ↓
Apply required transformations
        ↓
Validate data
        ↓
Notify BI/Data Analyst
        ↓
Power BI Developer
        ↓
Connect report to MySQL
```

The Power BI developer can then consume the prepared MySQL data and refresh the report.

---

# 27. Next Step: Connect MySQL to Power BI

After completing the MySQL preparation, the next task is to connect Power BI to this database.

The intended flow is:

```text
Excel
  ↓
MySQL Workbench
  ↓
MySQL prod database
  ↓
Power BI MySQL Connector
  ↓
Existing Power BI Report
```

The objective remains:

> **Use the same Power BI report instead of recreating it.**

---

# 28. Overall SQL Server → MySQL Migration Process

The complete process covered across the sessions can be summarized as:

```text
                SQL SERVER
                    │
                    │ Existing Production Data
                    ↓
             Validate Data
                    │
                    ↓
          Identify Data Issues
                    │
                    ↓
          Clean/Transform Data
                    │
                    │
          Client changes source
                    │
                    ↓
                 MySQL
                    │
                    ↓
           Create prod database
                    │
                    ↓
           Import inventory data
                    │
                    ↓
            Clean inventory data
                    │
                    ↓
             Import products
                    │
                    ↓
          Validate MySQL tables
                    │
                    ↓
              Connect Power BI
                    │
                    ↓
        Reuse Existing Power BI Report
```

---

# 29. Important Concepts to Remember

### **1. Create the MySQL database**

```sql
CREATE DATABASE prod;
```

### **2. Select the database**

```sql
USE prod;
```

### **3. Import Excel data**

Use:

**Right-click database → Table Data Import Wizard → Browse → Select file → Next → Finish**

### **4. Replicate required data transformations**

For this project:

```text
Product ID 21 → 7
Product ID 22 → 11
```

### **5. Safe Update Mode may prevent UPDATE statements**

If you receive a Safe Update Mode error:

**Edit → Preferences → SQL Editor → Disable Safe Updates → OK → Reconnect**

### **6. Import the Product table as well**

The Power BI model requires both the inventory/fact data and the Product dimension.

### **7. Validate the final MySQL data**

Make sure the tables and values are correct before connecting Power BI.

---

# 30. Important Difference Between This Session and the Previous One

In the previous SQL Server session, we worked with:

```text
Microsoft SQL Server
```

and performed data preparation using SQL Server queries.

In this session, we recreated the required environment using:

```text
MySQL
```

The key lesson is that **the database technology has changed, but the business/data requirements remain the same**.

We still need:

* The same Production data
* The same Product data
* The same data-cleaning logic
* Consistent table/column structure where required
* A database that Power BI can query

---

# 31. Quick Revision Table

| Task                   | MySQL Workbench Action                                 |
| ---------------------- | ------------------------------------------------------ |
| Open MySQL             | Open MySQL Workbench → Local instance                  |
| Create database        | `CREATE DATABASE prod;`                                |
| Select database        | `USE prod;`                                            |
| Refresh schemas        | Click Refresh                                          |
| Import inventory       | Right-click `prod` → Table Data Import Wizard          |
| Select inventory file  | Browse → Production Environment Inventory Dataset      |
| Create inventory table | `prod environment inventory data set`                  |
| Fix Product ID 21      | `21 → 7`                                               |
| Fix Product ID 22      | `22 → 11`                                              |
| Safe Update error      | Edit → Preferences → SQL Editor → Disable Safe Updates |
| Reconnect              | Reconnect to MySQL instance                            |
| Verify data            | `SELECT * FROM ...`                                    |
| Import Product table   | Right-click `prod` → Table Data Import Wizard          |
| Final step             | Connect MySQL to Power BI                              |

---

# 32. Final Takeaway

The most important idea from this session is:

> **Before switching an existing Power BI report from SQL Server to MySQL, prepare the equivalent data environment in MySQL.**

For this project, that means:

**Create `prod` → Import inventory data → Apply required data cleaning → Import Products table → Verify data → Connect Power BI to MySQL.**

The Power BI report itself should **not be recreated**. The objective is to migrate the **data source**, while preserving the existing report logic and calculations.
