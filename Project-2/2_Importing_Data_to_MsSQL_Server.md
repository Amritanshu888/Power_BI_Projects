# Detailed Notes — Loading Data into Microsoft SQL Server

## 1. Purpose of This Lecture

Before starting the **second Microsoft Power BI project**, the project will use **Microsoft SQL Server as the data source**.

Therefore, two SQL Server lectures should be completed before starting the project:

1. **Lecture 1:** Downloading and installing Microsoft SQL Server.
2. **Lecture 2:** Loading/importing the dataset into Microsoft SQL Server.

This lecture focuses on the **second part — importing the provided dataset into SQL Server**.

---

# 2. Overall Workflow

The workflow for the second Power BI project is:

```text
CSV Dataset
     ↓
Microsoft SQL Server
     ↓
Power BI
     ↓
Reporting / Visualization
```

For this practice project:

1. Install SQL Server.
2. Open SQL Server Management Studio (SSMS).
3. Connect to SQL Server.
4. Create a database.
5. Import the CSV dataset into that database.
6. Verify that the data was successfully imported.
7. Connect Power BI to this SQL Server database.
8. Begin building the Power BI report.

---

# 3. Open SQL Server Management Studio

The instructor starts by opening:

> **SQL Server Management Studio (SSMS)**

### Steps

1. Double-click the **SQL Server Management Studio** icon.
2. Wait for SSMS to open.

The application may take some time to launch.

---

# 4. Connect to SQL Server

When SSMS opens, you need to provide the server connection details.

The connection window requires:

* Server type
* Server name
* Authentication method

### Server Type

Select:

> **Database Engine**

### Server Name

Enter your SQL Server instance name.

In the instructor's example, the server name is:

> `Lenovo`

Your server name may be different depending on your installation.

### Authentication

The instructor uses:

> **Windows Authentication**

### Final Configuration

| Setting        | Value                    |
| -------------- | ------------------------ |
| Server type    | Database Engine          |
| Server name    | Your SQL Server instance |
| Authentication | Windows Authentication   |

Then click:

> **Connect**

---

# 5. Open a New Query Window

After successfully connecting to SQL Server:

1. Click **New Query**.
2. A new SQL query window will open.

This query window is where SQL commands can be written and executed.

---

# 6. Examine Existing Databases

The instructor clicks the **`+` icon next to Databases** in Object Explorer.

Several databases are already present.

The examples shown are:

* **AdventureWorks**
* **Insurance**
* **Practice**

### What is a Database?

A database is essentially a collection/container that can contain various database objects, such as:

* Tables
* Views
* Stored procedures
* Other database objects

For this Power BI project, the important thing is to have a database in which the project dataset can be stored.

---

# 7. Create a New Database

The instructor creates a new database specifically for the project.

The desired database name is:

> **InsuranceDB**

The SQL command used is:

```sql
CREATE DATABASE InsuranceDB;
```

### Steps

1. In the query window, write:

```sql
CREATE DATABASE InsuranceDB;
```

2. Click **Execute**.

If everything works correctly, SSMS displays:

> **Commands completed successfully.**

This confirms that the database was successfully created.

---

# 8. Refresh the Databases List

After creating the database, it might not immediately appear in Object Explorer.

Therefore, refresh the database list.

### Steps

1. Click the **Refresh** button.
2. If the database still doesn't appear, right-click **Databases**.
3. Select **Refresh**.

After refreshing, you should see:

> **InsuranceDB**

under the Databases section.

### Important

Refreshing Object Explorer is sometimes necessary because SSMS does not automatically update the displayed list immediately after creating a database.

---

# 9. Import the Dataset into InsuranceDB

Now that the database has been created, the next task is to load the dataset into it.

The instructor uses SQL Server's:

> **Import Flat File**

feature.

### Steps

1. Right-click **InsuranceDB**.
2. Go to **Tasks**.
3. Select:

> **Import Flat File**

This opens the Import Flat File wizard.

---

# 10. Start the Import Flat File Wizard

After selecting **Import Flat File**:

1. The import wizard opens.
2. Click **Next**.

The wizard now asks for the location of the file that needs to be imported.

---

# 11. Select the Dataset File

The instructor has the dataset stored inside an:

> **Insurance data**

folder on the Desktop.

### Steps

1. Click **Browse**.
2. Navigate to the location where the dataset is stored.
3. Open the **Insurance data** folder.
4. Select the required dataset file.
5. Double-click the file.
6. Click **Next**.
7. Click **Next** again.

The wizard then analyzes the dataset.

---

# 12. Review Automatically Detected Data Types

One important step in the import process is reviewing the **data types**.

SQL Server automatically detects the likely data type of each column in the dataset.

For example, a column might be detected as:

* Integer
* Decimal
* Date
* Character/string
* Money
* etc.

The instructor reviews the detected data types before completing the import.

---

# 13. Correct the Policy Number Data Type

The instructor notices an issue with the:

> **Policy Number**

column.

SQL Server has automatically detected its data type as:

> **Money**

This is not appropriate.

### Why?

A policy number is an **identifier**, not a monetary value.

Therefore, it should be stored as a character/string type rather than as a monetary numeric type.

The instructor changes the data type to:

> **VARCHAR / variable character**

and chooses the appropriate **maximum length** option.

### Important Lesson

Always review automatically detected data types before importing a dataset.

Automatic detection can sometimes incorrectly interpret a column based on the values it sees.

For example:

```text
Policy Number
-------------
10001
10002
10003
```

Although these values look numeric, they represent **identifiers**, not quantities or monetary values.

Therefore, a character/string data type is more appropriate.

---

# 14. Complete the Import

After reviewing and correcting the column data types:

1. Click **Next**.
2. Click **Finish**.

SQL Server will begin importing the dataset.

After the process completes, the instructor sees a message indicating that:

> **Data was imported successfully.**

Then:

3. Click **Close**.

The dataset has now been loaded into SQL Server.

---

# 15. Locate the Imported Table

Now the instructor verifies the imported data.

### Steps

1. In Object Explorer, find **InsuranceDB**.
2. Click the **`+` icon** next to InsuranceDB.
3. Locate:

> **Tables**

4. Click the **`+` icon** next to Tables.

The imported table will appear under the Tables section.

This confirms that the dataset has been imported as a SQL Server table.

---

# 16. Query the Imported Table

The instructor then wants to verify that the table actually contains the expected data.

The table name can be dragged into the query window.

### Steps

1. Locate the imported table under **Tables**.
2. Double-click the table name.
3. Drag and drop it into the query window.

SSMS can insert the table name into the query.

The instructor then writes a `SELECT` statement.

The basic query is:

```sql
SELECT *
FROM <table_name>;
```

Here:

* `SELECT *` means select all columns.
* `FROM <table_name>` specifies the table from which data should be retrieved.

---

# 17. Important Issue: Selecting the Correct Database

The instructor initially attempts to execute the query but receives an error similar to:

> **Invalid object name**

This happens because the query window is not currently working in the correct database context.

Even though the table exists inside **InsuranceDB**, the query needs to be executed against that database.

---

# 18. Select InsuranceDB from the Database Dropdown

At the top of the query window, SSMS provides a database dropdown.

The instructor selects:

> **InsuranceDB**

### Steps

1. Click the database dropdown at the top of the query window.
2. Select **InsuranceDB**.
3. Select the SQL statement.
4. Click **Execute**.

Now the query executes successfully.

The data from the imported table is displayed in the results section.

---

# 19. Why the Database Dropdown Matters

This is an important practical concept.

Suppose your table is:

```text
InsuranceDB
    └── Tables
         └── InsuranceTable
```

If your query window is currently connected to another database, such as `Practice`, then:

```sql
SELECT *
FROM InsuranceTable;
```

may produce:

> **Invalid object name**

because SQL Server is looking for `InsuranceTable` inside the currently selected database.

Therefore, make sure the correct database is selected before executing queries.

For this project:

> **Select InsuranceDB from the database dropdown.**

---

# 20. Verify the Imported Data

After selecting **InsuranceDB** and executing:

```sql
SELECT *
FROM <table_name>;
```

the imported dataset appears in the query results.

This verifies that:

* The database was created successfully.
* The dataset was imported successfully.
* The table was created successfully.
* The data is available inside SQL Server.
* The data can be queried using SQL.

---

# 21. Practice Project vs Real-World Scenario

The instructor emphasizes that this manual data-import process is mainly being demonstrated for **learning purposes**.

In a real company or client environment:

* The SQL Server database will generally already exist.
* The required tables will already be present.
* The data will already be loaded into SQL Server.
* You will typically receive the necessary credentials/access.
* You can then connect Power BI directly to the organization's SQL Server.

For example:

```text
Existing Company SQL Server
          ↓
Existing Database
          ↓
Existing Tables
          ↓
Power BI
```

You would not normally need to manually create the database and import a CSV file yourself unless your role specifically requires it.

---

# 22. Dataset Provided for Practice

For this course/project, the instructor will provide the:

> **CSV sheet**

in the **resource section**.

The recommended learning workflow is:

```text
Provided CSV
    ↓
Import into SQL Server
    ↓
InsuranceDB
    ↓
Imported Table
    ↓
Connect Power BI
    ↓
Build Power BI Report
```

---

# 23. Complete Step-by-Step Procedure

## Part A — Open SSMS

* [ ] Open **SQL Server Management Studio**.
* [ ] Wait for SSMS to load.

## Part B — Connect to SQL Server

* [ ] Set **Server type** to `Database Engine`.
* [ ] Enter your **Server name**.
* [ ] Select **Windows Authentication**.
* [ ] Click **Connect**.

## Part C — Open Query Window

* [ ] Click **New Query**.

## Part D — Create Database

Run:

```sql
CREATE DATABASE InsuranceDB;
```

* [ ] Click **Execute**.
* [ ] Confirm that **Commands completed successfully** appears.

## Part E — Refresh Databases

* [ ] Expand **Databases**.
* [ ] Click **Refresh**.
* [ ] If necessary, right-click **Databases → Refresh**.
* [ ] Confirm that **InsuranceDB** appears.

## Part F — Import CSV

* [ ] Right-click **InsuranceDB**.
* [ ] Select **Tasks**.
* [ ] Select **Import Flat File**.
* [ ] Click **Next**.
* [ ] Click **Browse**.
* [ ] Locate the provided insurance dataset.
* [ ] Select the file.
* [ ] Click **Next**.
* [ ] Review the automatically detected data types.
* [ ] Correct any inappropriate data types.
* [ ] In particular, change **Policy Number** from **Money** to an appropriate variable-character/string type.
* [ ] Click **Next**.
* [ ] Click **Finish**.
* [ ] Confirm that the data was imported successfully.
* [ ] Click **Close**.

## Part G — Verify the Table

* [ ] Expand **InsuranceDB**.
* [ ] Expand **Tables**.
* [ ] Locate the imported table.

## Part H — Query the Table

Use:

```sql
SELECT *
FROM <table_name>;
```

* [ ] Select **InsuranceDB** from the database dropdown.
* [ ] Select/execute the query.
* [ ] Verify that the imported data appears in the results.

---

# 24. Key Concepts to Remember

### 1. Database ≠ Table

A **database** is a container for database objects.

A **table** is one of the objects inside a database that stores rows and columns.

Example:

```text
InsuranceDB                  ← Database
    │
    └── Tables
          │
          └── InsuranceTable ← Table
```

### 2. `CREATE DATABASE`

Used to create a new SQL Server database:

```sql
CREATE DATABASE InsuranceDB;
```

### 3. `SELECT *`

Used to retrieve all columns from a table:

```sql
SELECT *
FROM TableName;
```

### 4. Database Context Matters

Before executing a query, make sure the correct database is selected in the SSMS database dropdown.

### 5. Check Data Types

Never blindly accept automatically detected data types during CSV import.

Make sure each column's data type makes sense for the actual meaning of the data.

For example:

| Column        | Appropriate Concept |
| ------------- | ------------------- |
| Policy Number | String/identifier   |
| Premium       | Monetary/numeric    |
| Age           | Integer             |
| Date          | Date                |
| Customer Name | String              |

---

# 25. Final Project Flow

After completing this lecture and the previous SQL Server installation lecture, you are ready to begin the **second Power BI project**:

```text
                    ┌─────────────────┐
                    │   CSV Dataset   │
                    └────────┬────────┘
                             ↓
                    ┌─────────────────┐
                    │ Microsoft SQL   │
                    │     Server      │
                    └────────┬────────┘
                             ↓
                    ┌─────────────────┐
                    │   InsuranceDB   │
                    └────────┬────────┘
                             ↓
                    ┌─────────────────┐
                    │ Imported Table  │
                    └────────┬────────┘
                             ↓
                    ┌─────────────────┐
                    │     Power BI    │
                    └────────┬────────┘
                             ↓
                    ┌─────────────────┐
                    │    Reporting    │
                    │  & Visualization│
                    └─────────────────┘
```

### Most Important Takeaway

For this project, the **CSV file is first loaded into SQL Server**, and **Power BI will then use SQL Server as its data source**.

In a real organization, the SQL Server database and data would generally already exist, and you would simply use the provided access/credentials to connect Power BI to it.
