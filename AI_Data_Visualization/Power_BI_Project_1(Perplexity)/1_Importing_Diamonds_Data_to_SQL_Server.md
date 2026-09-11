# Microsoft SQL Server Data Import — Detailed Notes

## 1. Objective of the Session

The main objective of this session is to **import the project data into Microsoft SQL Server**.

For this Power BI project:

> **Microsoft SQL Server will be used as the data source for Power BI.**

The overall flow is:

**Data File → SQL Server → Power BI → Reports/Dashboard**

The instructor will first create a separate database for the Power BI project, import the data file into that database, verify the imported table and records, and then use this SQL Server database as the source for Power BI.

---

# 2. Prerequisite: SQL Server Installation

Before starting this lecture, you should have **Microsoft SQL Server** installed.

If SQL Server has not been installed yet, the instructor mentions that there is a previous case study in the **Advanced Prompt Engineering** section explaining how to download and install SQL Server.

So the prerequisite is:

1. Install Microsoft SQL Server.
2. Open the SQL Server environment/management tool.
3. Connect to the SQL Server instance.
4. Then follow the steps in this lecture.

---

# 3. Open SQL Server and Create a New Query

Once SQL Server is open:

1. Connect to the SQL Server instance.
2. Click **Connect**.
3. Click **New Query**.

A query window will open.

This query window is where SQL commands can be written and executed.

---

# 4. Create a New Database

Since this is a separate Power BI project, the instructor creates a **new database specifically for the project**.

The SQL command used is:

```sql
CREATE DATABASE PBI1;
```

The instructor refers to the database as **PBI one / PBI1**.

### Execution

After writing the command:

1. Select the SQL statement.
2. Press **Ctrl + E** to execute it.

Alternatively, depending on the SQL Server interface, the Execute button can be used.

### Result

The database is created successfully.

---

# 5. Refresh the Databases Folder

After creating the database, it may not immediately appear in the Object Explorer.

To make it visible:

1. Go to the **Databases** section on the left-hand side.
2. Right-click on **Databases**.
3. Select **Refresh**.

After refreshing, the newly created database appears:

```text
PBI1
```

---

# 6. Import the Flat File into the Database

Now the instructor imports the project's data file into SQL Server.

### Step-by-step

1. Locate the newly created database:

```text
Databases
   └── PBI1
```

2. Right-click on **PBI1**.
3. Go to:

```text
Tasks → Import Flat File
```

The **Import Flat File Wizard** opens.

---

# 7. Browse and Select the Data File

Inside the Import Flat File wizard:

1. Click **Next**.
2. Click **Browse**.
3. Locate the project data file.
4. Select the file.
5. Double-click the file.

The instructor mentions that the same data file will be provided in the **resource section**, so learners can download it from there.

---

# 8. Proceed Through the Import Wizard

After selecting the file:

1. Click **Next**.
2. Review the import configuration.
3. Click **Next** again.
4. Continue until the wizard reaches the final stage.
5. Click **Finish**.

However, during the import process, an error is encountered.

---

# 9. Handle the NULL Value Error

The import process displays an error similar to:

> Error inserting data into the table. Column Z does not allow DB null value.

### What does this mean?

The imported dataset contains some missing/NULL values in **column Z**, but the corresponding SQL Server table column has been configured in a way that does **not allow NULL values**.

Therefore, SQL Server cannot insert those rows as they currently are.

---

# 10. Allow NULL Values for Column Z

To resolve the problem:

1. Click **OK** on the error message.
2. Go back to the previous step in the import wizard.
3. Locate the configuration for **Column Z**.
4. Enable/allow **NULL values** for Column Z.
5. Click **Next**.
6. Continue through the wizard.
7. Click **Finish**.

The important change is:

```text
Column Z
     ↓
Allow NULL values
```

This allows rows containing missing values in column Z to be inserted into the SQL Server table.

---

# 11. Handle the Import Warning

Even after making the change, SQL Server displays a warning.

The warning indicates that:

> Up to 855 cells of data may have been dropped during the insert for the specified columns.

The instructor chooses to proceed because the warning is not considered a blocker for this project.

So:

1. Click **OK**.
2. Accept the warning.
3. Click **Close** after the import process finishes.

### Important distinction

There are two different messages here:

**Error:**

* NULL values were not allowed in Column Z.
* This needed to be addressed.

**Warning:**

* SQL Server indicates that up to 855 cells may have been dropped.
* The instructor accepts this warning and continues.

---

# 12. Select the Correct Database

After importing the data, the query window is initially connected to the **master database**.

At the top-left of the SQL Server query window, the selected database is shown.

Initially:

```text
master
```

But the project database is:

```text
PBI1
```

Therefore, the instructor explicitly switches to the project database.

Use:

```sql
USE PBI1;
```

Then select the `USE PBI1` statement and execute it.

### Why is this necessary?

It ensures that subsequent SQL queries are executed against the **PBI1 database** rather than the default `master` database.

---

# 13. Refresh the PBI1 Database

Now the instructor verifies whether the imported table has been created.

On the left-hand side:

1. Right-click **PBI1**.
2. Click **Refresh**.
3. Click the **+** icon next to PBI1.

Expand the database.

You should see something similar to:

```text
PBI1
 ├── Tables
 ├── ...
```

---

# 14. Locate the Imported Table

Expand:

```text
PBI1
   └── Tables
```

The imported table is:

```text
dbo.diamonds
```

### Understanding `dbo.diamonds`

The table name is:

```text
diamonds
```

`dbo` is the default database schema commonly used by SQL Server.

Therefore:

```text
dbo.diamonds
```

means:

> The `diamonds` table under the `dbo` schema.

---

# 15. Open the Table in the Query Window

The instructor then:

1. Double-clicks:

```text
dbo.diamonds
```

2. This places the table/reference into the query window.

The instructor then manually writes a query to retrieve all records.

---

# 16. Retrieve All Data Using SELECT

The SQL query used is:

```sql
SELECT *
FROM dbo.diamonds;
```

### Meaning

`SELECT *` means:

> Retrieve all columns.

`FROM dbo.diamonds` means:

> Retrieve the data from the `diamonds` table under the `dbo` schema.

Therefore:

```sql
SELECT * FROM dbo.diamonds;
```

returns the complete contents of the imported table.

---

# 17. Execute the Query

To execute the query:

1. Select the SQL statement.
2. Press **Ctrl + E**.

The results are displayed in the results grid.

The instructor verifies that the data has been successfully imported.

---

# 18. Number of Records

The imported `diamonds` dataset contains:

> **53,940 records**

So the SQL Server table contains approximately **54K rows**.

The data will now be used for the Power BI reporting project.

---

# 19. Overall Project Architecture

The workflow established in this lecture can be represented as:

```text
                 Data File
                    │
                    ▼
          Microsoft SQL Server
                    │
                    ▼
              Database: PBI1
                    │
                    ▼
             Table: diamonds
                    │
                    ▼
                Power BI
                    │
                    ▼
           Reports / Dashboard
```

The SQL Server database therefore acts as the **data source layer** for the Power BI project.

---

# 20. Role of AI Tools in the Upcoming Project

The instructor also explains that AI tools will be used later in the project.

In particular, tools such as **Perplexity and other AI tools** will help determine:

* Which KPIs should be represented.
* What types of visualizations should be created.
* How the Power BI report should be designed.
* What insights can be extracted from the dataset.
* How the reporting/dashboard structure should be approached.

So the project isn't simply about importing data into Power BI. AI tools will also assist in **planning and designing the Power BI report**.

---

# 21. Important Commands from the Lecture

### Create database

```sql
CREATE DATABASE PBI1;
```

### Switch to the project database

```sql
USE PBI1;
```

### View all data from the imported table

```sql
SELECT *
FROM dbo.diamonds;
```

Or in one line:

```sql
SELECT * FROM dbo.diamonds;
```

### Keyboard shortcut used

```text
Ctrl + E
```

Used to execute the selected SQL query.

---

# 22. Complete Practical Procedure

For revision, the entire process can be remembered as:

### Step 1 — Connect

Open SQL Server → **Connect** → **New Query**

### Step 2 — Create database

```sql
CREATE DATABASE PBI1;
```

Execute using **Ctrl + E**.

### Step 3 — Refresh databases

Right-click **Databases** → **Refresh**

### Step 4 — Import file

Right-click:

```text
PBI1 → Tasks → Import Flat File
```

### Step 5 — Select data file

```text
Next → Browse → Select file → Next
```

### Step 6 — Resolve NULL issue

If Column Z produces a NULL-related error:

```text
Previous → Allow NULLs for Column Z → Next
```

### Step 7 — Complete import

```text
Next → Finish
```

Accept the warning regarding potentially dropped cells.

### Step 8 — Switch database

```sql
USE PBI1;
```

Execute it.

### Step 9 — Refresh database

```text
Right-click PBI1 → Refresh
```

### Step 10 — Find table

```text
PBI1 → Tables → dbo.diamonds
```

### Step 11 — Verify data

```sql
SELECT * FROM dbo.diamonds;
```

Execute it.

### Step 12 — Verify row count

Expected dataset size:

```text
53,940 records
```

---

# 23. Key Takeaways

* **SQL Server is the data source** for this Power BI project.
* A separate database named **PBI1** is created for the project.
* The dataset is imported using **Tasks → Import Flat File**.
* The imported table is **dbo.diamonds**.
* A NULL-value issue occurs in **Column Z**, so NULL values are allowed for that column.
* SQL Server may display a warning about up to **855 cells** potentially being dropped; the instructor proceeds despite this warning.
* The query window initially uses the **master** database, so `USE PBI1` is executed to switch to the correct database.
* `SELECT * FROM dbo.diamonds` is used to verify the imported data.
* The dataset contains **53,940 records**.
* The data will subsequently be connected to **Power BI** for reporting and dashboard creation.
* **Perplexity and other AI tools** will later be used to help decide KPIs, report structure, and visualizations.

### One-line revision

> **Create PBI1 → Import Flat File → Fix Column Z NULL issue → Finish Import → `USE PBI1` → Open `dbo.diamonds` → `SELECT * FROM dbo.diamonds` → Verify 53,940 records → Use SQL Server as Power BI's data source.**
