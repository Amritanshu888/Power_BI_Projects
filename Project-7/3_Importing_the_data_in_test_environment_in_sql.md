# Power BI Project — Importing Test Environment Data into Microsoft SQL Server

## 1. Session Overview

In the previous session, the project covered:

* The **KPIs** required for the Power BI report.
* The **test environment dataset**.
* The different real-world scenarios that will be handled in the project.

In this session, the focus is on:

> **Importing the test environment data into Microsoft SQL Server.**

The instructor uses **SQL Server Management Studio (SSMS)** to:

1. Connect to SQL Server.
2. Create a test environment database.
3. Import the inventory dataset.
4. Import the products dataset.
5. Verify that the tables and data were successfully imported.
6. Query the imported data using SQL.
7. Understand a date-format issue that occurs after importing the data.
8. Discuss how the same process can be followed for the production environment.

---

# 2. Tool Used — SQL Server Management Studio

The instructor begins by opening:

> **SQL Server Management Studio (SSMS)**

SSMS is used to interact with Microsoft SQL Server.

It allows us to:

* Create databases.
* Create and manage tables.
* Import data.
* Write SQL queries.
* Execute SQL statements.
* View/query database data.

---

# 3. Connecting to SQL Server

After opening SSMS, the instructor connects to the local SQL Server instance.

The connection window requires details such as:

* Server name
* Authentication method

The instructor's server name is:

```text
Lenovo
```

The instructor supplies the server name and selects the required authentication method.

Then:

> Click **Connect**

After successful connection, the SSMS interface is displayed.

---

# 4. Creating the Test Environment Database

The first task is to create a database for the test environment.

The instructor opens a new query window.

### Step 1 — Create a New Query

Click:

> **New Query**

This opens a new SQL query window.

---

## Step 2 — Create the Database

The instructor creates a database named:

```text
test_env
```

The SQL command is:

```sql
CREATE DATABASE test_env;
```

### Execute the query

The instructor selects the statement and uses the keyboard shortcut:

```text
Ctrl + E
```

to execute it.

The command completes successfully.

### Result

A new database is created:

```text
test_env
```

---

# 5. Selecting the Test Environment Database

After creating the database, we need to tell SQL Server that subsequent commands should work with this database.

The instructor uses:

```sql
USE test_env;
```

### Execute

1. Select the `USE` statement.
2. Press:

```text
Ctrl + E
```

The database is now selected.

The database name can be seen at the top/left side of the query environment, confirming that the current database is:

```text
test_env
```

---

# 6. Refreshing the Databases List

Although the database has been created, the Object Explorer may not immediately show it.

Therefore, the instructor refreshes the database list.

### Steps

In **Object Explorer**:

1. Right-click **Databases**.
2. Click **Refresh**.

After refreshing, expand the Databases section.

You should now see:

```text
test_env
```

---

# 7. Importing the Inventory Dataset

The first dataset that needs to be imported is the:

> **Test Environment Inventory Dataset**

The instructor imports this data as a table inside the `test_env` database.

---

## Step-by-Step Import Process

### Step 1

Right-click:

```text
test_env
```

### Step 2

Select:

```text
Tasks
```

### Step 3

Under Tasks, select:

> **Import Flat File**

This opens the SQL Server flat-file import wizard.

---

### Step 4 — Start the Import

Click:

> **Next**

---

### Step 5 — Browse for the File

Click:

> **Browse**

Locate the inventory dataset file.

The instructor selects:

```text
Test environment inventory data set
```

Double-click the file.

---

### Step 6 — Review the File

The wizard displays information about the selected data.

Click:

> **Next**

Continue through the wizard.

The instructor proceeds using:

```text
Next
Next
Next
Finish
```

---

# 8. Successful Import

After completing the wizard, SQL Server displays a success message.

This confirms that the inventory data was successfully imported into the test environment database.

The instructor closes the import window.

---

# 9. Importing the Products Data

The project also has a separate **Products** dataset.

This also needs to be imported into the same `test_env` database.

---

## Step-by-Step Process

Right-click:

```text
test_env
```

Then:

```text
Tasks
   ↓
Import Flat File
```

Click:

> **Next**

Then:

> **Browse**

Select the:

```text
Products table
```

Double-click the file.

Continue through the wizard:

```text
Next
Next
Next
Finish
```

The import completes successfully.

Therefore, the test environment database now contains both datasets.

---

# 10. Tables Created in the Test Environment

After importing both files, the database contains two tables.

Refresh the database to see them.

### Steps

1. Right-click `test_env`.
2. Click **Refresh**.
3. Expand `test_env`.
4. Expand:

> **Tables**

You will see two tables:

```text
dbo.test_environment_inventory_data_set
dbo.products
```

The `dbo` represents the default database schema being used for these tables.

---

# 11. Verifying the Products Table

The instructor now checks whether the Products table contains the expected data.

The table is:

```text
dbo.products
```

### Method demonstrated

The instructor:

1. Double-clicks `dbo.products`.
2. Drags and drops the table into the query window.

A query can then be written:

```sql
SELECT *
FROM dbo.products;
```

Select the query and click:

> **Execute**

---

# 12. Products Data Result

The query displays the data contained in the Products table.

The instructor confirms that the dataset contains information for:

> **20 different Product IDs**

Therefore, the Products table contains data for a total of **20 products**.

The table contains the product-related information discussed in the previous session, such as:

* Product ID
* Product Name
* Unit Price

---

# 13. Verifying the Inventory Table

The second table is:

```text
dbo.test_environment_inventory_data_set
```

The instructor now queries this table.

Again, the table can be dragged into the query window.

Then use:

```sql
SELECT *
FROM dbo.test_environment_inventory_data_set;
```

Select the statement and click:

> **Execute**

---

# 14. Inventory Dataset Result

The query displays the inventory data.

This is the **test environment data** that will eventually be used for building the Power BI report.

The instructor confirms that the data has been successfully imported into SQL Server.

---

# 15. Date Format Issue

While looking at the inventory table, the instructor notices an important issue.

SQL Server has changed the **format of the date column**.

In other words, the date data has been imported, but its displayed format is different from the original dataset.

The instructor points out that this is **not a major concern at this stage**.

The plan is to:

> **Find a way to handle/fix the date format in Power BI.**

This issue will therefore be addressed later during the Power BI portion of the project.

### Important takeaway

The underlying date information is available, but the **display/format of the date column has changed after import**.

---

# 16. Test Environment Is Ready

At this point, the test environment contains:

```text
test_env
│
└── Tables
    │
    ├── dbo.test_environment_inventory_data_set
    │
    └── dbo.products
```

These tables contain the data required to begin developing the Power BI report.

---

# 17. Production Environment

The instructor briefly explains that the same process can be followed to load data into the **production environment**.

The steps would be essentially the same.

For example:

```text
Create/Access Production Database
          ↓
Tasks
          ↓
Import Flat File
          ↓
Browse
          ↓
Select Production Data File
          ↓
Next
          ↓
Finish
```

The main difference would be:

> The **production data file/path** would be selected instead of the test environment file.

However, the instructor does **not** perform the production import in this session.

The current session focuses only on the **test environment**.

---

# 18. Why Are We Importing the Data Manually?

An important real-world clarification is provided by the instructor.

In an actual organization, data generally already exists in the data source.

For example:

```text
Real World
──────────

SQL Server
   ↓
Data already available

or

MySQL
   ↓
Data already available
```

A Power BI developer typically connects Power BI to these existing data sources.

They normally wouldn't manually create/import the organization's production data themselves.

---

## Why does this project manually import the data?

The instructor explains that the data is being imported manually **for learning/project purposes**.

The goal is to ensure that students understand the complete process:

```text
Data File
   ↓
SQL Server
   ↓
Database
   ↓
Tables
   ↓
Power BI
```

Therefore, students following the project should also perform the import steps.

---

# 19. Why You Should Follow These Steps

The instructor recommends that students:

> **Import the data in the same way demonstrated in the lecture.**

This is because the imported database and tables will ultimately be used as the source for the Power BI report.

So the learning workflow is:

```text
Import Dataset
      ↓
Create SQL Server Tables
      ↓
Connect Power BI
      ↓
Build Report
      ↓
Create KPIs
      ↓
Test / Validate
```

---

# 20. Complete SQL Commands Used

The core SQL commands demonstrated in this session are:

### Create database

```sql
CREATE DATABASE test_env;
```

### Select/use database

```sql
USE test_env;
```

### Query Products

```sql
SELECT *
FROM dbo.products;
```

### Query Inventory Data

```sql
SELECT *
FROM dbo.test_environment_inventory_data_set;
```

---

# 21. Complete Process — Quick Revision

## Part A — Create Database

```text
Open SSMS
   ↓
Connect to SQL Server
   ↓
New Query
   ↓
CREATE DATABASE test_env
   ↓
Ctrl + E
   ↓
USE test_env
   ↓
Ctrl + E
```

---

## Part B — Import Inventory Dataset

```text
Refresh Databases
   ↓
Right-click test_env
   ↓
Tasks
   ↓
Import Flat File
   ↓
Next
   ↓
Browse
   ↓
Select Test Environment Inventory Dataset
   ↓
Next
   ↓
Next
   ↓
Next
   ↓
Finish
```

---

## Part C — Import Products Dataset

```text
Right-click test_env
   ↓
Tasks
   ↓
Import Flat File
   ↓
Next
   ↓
Browse
   ↓
Select Products Table/File
   ↓
Next
   ↓
Next
   ↓
Next
   ↓
Finish
```

---

## Part D — Verify Tables

```text
Right-click test_env
   ↓
Refresh
   ↓
Expand test_env
   ↓
Expand Tables
```

You should see:

```text
dbo.test_environment_inventory_data_set
dbo.products
```

---

## Part E — Verify Data

Products:

```sql
SELECT *
FROM dbo.products;
```

Inventory:

```sql
SELECT *
FROM dbo.test_environment_inventory_data_set;
```

Execute using the **Execute** button or:

```text
Ctrl + E
```

---

# 22. Final Database Structure

After completing the session, your SQL Server setup should conceptually look like this:

```text
SQL Server
│
└── test_env
    │
    └── Tables
        │
        ├── dbo.products
        │     ├── Product ID
        │     ├── Product Name
        │     └── Unit Price
        │
        └── dbo.test_environment_inventory_data_set
              ├── Order Date
              ├── Product ID
              ├── Availability
              └── Demand
```

This corresponds to the dataset structure discussed in the previous lecture.

---

# 23. Connection to the Power BI Report

The data will eventually flow into Power BI:

```text
SQL Server
     │
     ├── dbo.products
     │
     └── dbo.test_environment_inventory_data_set
                │
                ↓
             Power BI
                ↓
        Data Model / Relationships
                ↓
             Measures
                ↓
              KPIs
                ↓
          Report Pages
```

The report will ultimately contain the KPIs discussed previously.

### Page 1

* Average Demand per Day
* Average Availability per Day
* Total Supply Shortage

### Page 2

* Total Loss
* Total Profit
* Average Daily Loss

---

# 24. Important Real-Time Concept

One of the most important points from this session is the distinction between **learning/project setup** and **real-world practice**.

### In this course/project

The instructor manually imports the files:

```text
CSV/Flat File
     ↓
SQL Server
     ↓
Tables
```

This is done so that students can understand the entire process.

### In a real organization

The data would generally already exist:

```text
SQL Server / MySQL
       ↓
Existing Tables
       ↓
Power BI connects to them
```

The Power BI developer primarily works with the existing data source rather than manually loading organizational data from scratch.

---

# 25. Key Takeaways

### Database

The test environment database created is:

```text
test_env
```

### Tables

Two tables are imported:

```text
dbo.test_environment_inventory_data_set
dbo.products
```

### Inventory table

Contains:

* Order Date
* Product ID
* Availability
* Demand

### Products table

Contains:

* Product ID
* Product Name
* Unit Price

### Important SQL

```sql
CREATE DATABASE test_env;

USE test_env;

SELECT *
FROM dbo.products;

SELECT *
FROM dbo.test_environment_inventory_data_set;
```

### Important SSMS operations

Remember this sequence:

**Connect → New Query → Create Database → USE Database → Refresh → Tasks → Import Flat File → Browse → Finish → Refresh → Tables → Verify with SELECT**

### Date issue

SQL Server changes the displayed format of the date column during import. The instructor plans to address the date-format issue later in **Power BI**.

### Production

The same import procedure can be followed for production by selecting the appropriate **production data file/path**, although production is not loaded in this session.

### Main purpose

The test environment data is now prepared in SQL Server and will be used as the **source for building the Power BI report** in the upcoming sessions.
