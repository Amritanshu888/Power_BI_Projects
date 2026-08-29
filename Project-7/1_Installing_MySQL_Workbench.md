# MySQL Server & MySQL Workbench — Detailed Lecture Notes

## 1. Objective of the Session

In this session, the instructor explains:

1. How to **download MySQL**.
2. How to install:

   * **MySQL Server**
   * **MySQL Workbench**
3. How to configure MySQL during installation.
4. How to connect to MySQL using MySQL Workbench.
5. How to execute basic SQL commands.
6. How to:

   * Create a database
   * Create a table
   * Insert records
   * Retrieve records using `SELECT`
7. Why MySQL is being installed for the Power BI project.

---

# 2. What is MySQL?

**MySQL** is a relational database management system (RDBMS) that allows us to store, manage, and query structured data using **SQL (Structured Query Language)**.

In this Power BI project, **MySQL will be used as one of the data sources**.

The basic architecture being demonstrated is:

```text
MySQL Server
     ↓
Database
     ↓
Tables
     ↓
Data
     ↓
MySQL Workbench
     ↓
SQL Queries
```

### MySQL Server vs MySQL Workbench

| Component           | Purpose                                                                       |
| ------------------- | ----------------------------------------------------------------------------- |
| **MySQL Server**    | Actually stores and manages the databases and tables                          |
| **MySQL Workbench** | GUI application used to connect to MySQL Server and write/execute SQL queries |

So, **Workbench is the interface**, while **MySQL Server is the database engine**.

---

# 3. Downloading MySQL

The instructor demonstrates the installation process on **Microsoft Windows**.

### Step 1: Search for MySQL

Open a browser and search:

```text
MySQL download
```

Select the official MySQL download page.

> The instructor mentions that the download link will be provided in the **resource section**, so students can directly access it.

---

## Step 2: Open MySQL Downloads

On the MySQL Downloads page:

1. Scroll down.
2. Find **MySQL Community (GPL) Downloads**.
3. Click on it.

The Community edition is the freely available MySQL edition being used in the lecture.

---

# 4. Download MySQL Installer for Windows

Since the operating system being used is Windows:

1. Select **MySQL Installer for Windows**.
2. Select the appropriate version.
3. Ensure that:

   * Operating System = **Microsoft Windows**

You will see two main installer options:

### Option 1: MySQL Installer for Windows — Web Community

This is the web-based installer.

### Option 2: MySQL Installer for Windows — Community

This is the full/community installer.

The instructor chooses the **second option — MySQL Installer Community**.

Click:

**Download**

---

## Step 3: Skip Oracle Account Sign-in

After clicking Download, a page may ask you to sign in or create an Oracle account.

Instead of doing that:

1. Click **No thanks, just start my download**.
2. Save the installer file.

The MySQL installer will then be downloaded to the computer.

---

# 5. Starting the Installation

Once the download is complete:

1. Open the downloaded installer file.
2. Windows may display a security prompt.
3. Click **Yes**.
4. If another confirmation appears, click **Yes** again.

The MySQL Installer will now start preparing for installation.

---

# 6. Choosing the Installation Type

The installer provides different installation options.

The instructor specifically chooses:

> **Custom**

### Why Custom?

The Custom option is selected because we **do not want to install every available MySQL product**.

Instead, we want to select only the products required for the project.

Click:

**Custom → Next**

---

# 7. Selecting MySQL Server

Now we need to select the MySQL Server component.

### Steps

1. Find **MySQL Servers**.
2. Click the **+** icon to expand it.
3. Expand the appropriate MySQL Server version.
4. Select:

```text
MySQL Server 8.0 – 64 bit
```

5. Add/select it so that it appears under:

> **Products to be Installed**

---

# 8. Selecting MySQL Workbench

Next, we need the GUI tool.

### Steps

1. Find **Applications**.
2. Click the **+** icon.
3. Find **MySQL Workbench**.
4. Expand/select it.
5. Select the appropriate **MySQL Workbench** version.
6. Click the **green arrow**.

The selected components should now appear under:

> **Products to be Installed**

Therefore, the two important products selected are:

```text
MySQL Server
MySQL Workbench
```

---

# 9. Execute the Installation

Once the required products have been selected:

1. Click **Next**.
2. Click **Execute**.

The installer will now download/install the selected components.

This process may take some time.

The instructor mentions that students can **fast-forward this portion of the video** because the installation/configuration process may take some time.

After the installation completes:

1. Click **Next**.
2. Continue through the configuration screens by clicking **Next** where appropriate.

---

# 10. MySQL Port Number

During configuration, MySQL asks for connection-related settings.

One important setting is the **port number**.

The instructor specifically tells students:

> **Keep note of the port number.**

The default MySQL port is commonly:

```text
3306
```

The instructor keeps the settings as they are and proceeds.

### Why is the port important?

The port is used for communication between applications such as MySQL Workbench and the MySQL Server.

Conceptually:

```text
MySQL Workbench
       ↓
   Port 3306
       ↓
MySQL Server
```

---

# 11. Setting the Root Password

The installer then asks you to create a password for the **root user**.

### Steps

1. Enter a password in the password field.
2. Enter the same password again for confirmation.
3. Click **Next**.

The instructor uses a weak password for demonstration purposes and explicitly notes that the password is weak, but it does not matter for this lecture.

### Important

The password created here will later be used to **log into MySQL through MySQL Workbench**.

Therefore:

```text
Root Password
      ↓
Used to authenticate/login
      ↓
MySQL Workbench
```

**In a real project, use a strong password and never expose it publicly.**

---

# 12. Completing Configuration

Continue through the configuration screens:

```text
Next
Next
Execute
```

The installer will perform the required configuration.

Again, this process may take some time.

Once everything is completed:

1. Click **Finish**.
2. Click **Next** if prompted.
3. Click **Finish** again where required.

The installation is now complete.

---

# 13. Opening MySQL Workbench

After installation, open:

> **MySQL Workbench**

MySQL Workbench is described in the lecture as:

> **The official GUI tool for MySQL.**

It provides a graphical interface where we can connect to the MySQL Server and write SQL queries.

---

# 14. Connecting to MySQL Server

On opening MySQL Workbench, you will see a MySQL connection such as:

```text
Local instance MySQL
```

### Steps

1. Click **Local instance MySQL**.
2. Workbench will ask for the password.
3. Enter the **root password** that you created during installation.
4. You can optionally save the password in the **vault**.
5. Click **OK**.

You are now connected to MySQL Server.

---

# 15. MySQL Workbench Interface

After successfully connecting, you will see the SQL editor/interface.

This is where we can:

* Write SQL queries
* Execute SQL statements
* Create databases
* Create tables
* Insert data
* Retrieve data
* Perform other database operations

The instructor will use this interface for the SQL portion of the Power BI project.

---

# 16. Creating a Database

The instructor now demonstrates a basic SQL command.

### SQL

```sql
CREATE DATABASE test;
```

### Explanation

`CREATE DATABASE` is used to create a new database.

Here:

```text
test
```

is the database name.

So:

```sql
CREATE DATABASE test;
```

means:

> Create a database named `test`.

### Executing the query

1. Write the SQL statement in the SQL editor.
2. Select the statement.
3. Execute the selected portion of code.

The database is then created.

---

# 17. Creating a Table

After creating the database, the instructor creates a table inside it.

The table is named:

```text
tab_one
```

The instructor uses the following structure:

```sql
CREATE TABLE test.tab_one (
    c1 INT,
    c2 FLOAT
);
```

### Understanding the query

Let's break it down:

```sql
CREATE TABLE
```

Creates a new table.

```text
test.tab_one
```

Specifies:

```text
Database = test
Table    = tab_one
```

The dot notation:

```text
test.tab_one
```

means:

> `tab_one` table inside the `test` database.

---

## Table Columns

The table contains two columns:

| Column | Data Type |
| ------ | --------- |
| `c1`   | `INTEGER` |
| `c2`   | `FLOAT`   |

So conceptually:

```text
test
 └── tab_one
      ├── c1 → INTEGER
      └── c2 → FLOAT
```

---

# 18. Executing the CREATE TABLE Statement

To create the table:

1. Write the `CREATE TABLE` statement.
2. Select the SQL statement.
3. Execute it.

After successful execution, the table is created.

---

# 19. Retrieving Data from the Table

The instructor then uses a `SELECT` statement:

```sql
SELECT *
FROM test.tab_one;
```

### Understanding `SELECT *`

The `*` means:

> Select all columns.

Therefore:

```sql
SELECT *
FROM test.tab_one;
```

means:

> Retrieve all columns and all records from `tab_one`.

---

## Initial Result

At this point, the table has been created but **no records have been inserted**.

Therefore, executing:

```sql
SELECT *
FROM test.tab_one;
```

will show the column names:

```text
c1
c2
```

but there are no rows/records.

Conceptually:

| c1 | c2 |
| -- | -- |
|    |    |
|    |    |

The table exists, but it is empty.

---

# 20. Inserting Data into the Table

Now the instructor demonstrates how to add records.

The command used is:

```sql
INSERT INTO test.tab_one
VALUES (1, 1.75);
```

This inserts the first record.

### First record

```text
c1 = 1
c2 = 1.75
```

---

## Inserting a Second Record

The instructor then inserts another record:

```sql
INSERT INTO test.tab_one
VALUES (2, 2.75);
```

This inserts:

```text
c1 = 2
c2 = 2.75
```

---

# 21. Resulting Table

After inserting both records, the table contains:

| c1 |   c2 |
| -: | ---: |
|  1 | 1.75 |
|  2 | 2.75 |

The instructor executes the insert statements and confirms that the code was successfully executed.

---

# 22. Retrieving the Inserted Records

Now run:

```sql
SELECT *
FROM test.tab_one;
```

The output will display the data stored in the table:

```text
c1     c2
1      1.75
2      2.75
```

This demonstrates the basic flow:

```text
CREATE DATABASE
       ↓
CREATE TABLE
       ↓
INSERT DATA
       ↓
SELECT DATA
```

---

# 23. Complete SQL Demonstration

The entire demonstration can be summarized as:

```sql
-- Create database
CREATE DATABASE test;

-- Create table
CREATE TABLE test.tab_one (
    c1 INT,
    c2 FLOAT
);

-- Check table contents
SELECT *
FROM test.tab_one;

-- Insert first record
INSERT INTO test.tab_one
VALUES (1, 1.75);

-- Insert second record
INSERT INTO test.tab_one
VALUES (2, 2.75);

-- Retrieve all records
SELECT *
FROM test.tab_one;
```

---

# 24. Important SQL Concepts Covered

### `CREATE DATABASE`

Creates a database.

```sql
CREATE DATABASE database_name;
```

Example:

```sql
CREATE DATABASE test;
```

---

### `CREATE TABLE`

Creates a table inside a database.

```sql
CREATE TABLE database_name.table_name (
    column1 datatype,
    column2 datatype
);
```

Example:

```sql
CREATE TABLE test.tab_one (
    c1 INT,
    c2 FLOAT
);
```

---

### `INSERT INTO`

Adds records to a table.

```sql
INSERT INTO database_name.table_name
VALUES (...);
```

Example:

```sql
INSERT INTO test.tab_one
VALUES (1, 1.75);
```

---

### `SELECT`

Retrieves data.

```sql
SELECT *
FROM database_name.table_name;
```

Example:

```sql
SELECT *
FROM test.tab_one;
```

---

# 25. Key Installation Flow — Quick Revision

For revision, remember the installation process in this order:

```text
Search "MySQL download"
        ↓
MySQL Community (GPL) Downloads
        ↓
MySQL Installer for Windows
        ↓
Select Windows
        ↓
MySQL Installer Community
        ↓
Download
        ↓
"No thanks, just start my download"
        ↓
Run installer
        ↓
Custom Installation
        ↓
Select MySQL Server
        ↓
Select MySQL Workbench
        ↓
Next → Execute
        ↓
Configure MySQL
        ↓
Note the port number
        ↓
Set Root Password
        ↓
Execute configuration
        ↓
Finish
        ↓
Open MySQL Workbench
        ↓
Local instance MySQL
        ↓
Enter Root Password
        ↓
Start writing SQL
```

---

# 26. Key Takeaways

### MySQL Server

* The actual database server.
* Stores and manages databases and tables.
* The lecture installs **MySQL Server 8.0, 64-bit**.

### MySQL Workbench

* GUI tool for working with MySQL.
* Used to connect to MySQL Server.
* Provides an SQL editor for writing and executing queries.

### Authentication

* A **root password** is configured during installation.
* The same password is used to connect to the local MySQL instance through Workbench.

### Port

* The MySQL connection uses a port number.
* The instructor emphasizes keeping note of this port.
* The standard/default MySQL port is generally **3306**.

### SQL Flow Demonstrated

```text
Database
   ↓
Table
   ↓
Records
```

Using:

```sql
CREATE DATABASE
CREATE TABLE
INSERT INTO
SELECT
```

---

# 27. Why MySQL is Being Installed for This Power BI Project

The main reason for installing MySQL in this session is **not just to learn MySQL**.

The instructor explains that:

> **MySQL will be used as one of the data sources in the Power BI project.**

The overall project workflow will therefore involve connecting Power BI to a MySQL database and using the data stored there for reporting and analysis.

Conceptually:

```text
MySQL Database
      ↓
MySQL Tables
      ↓
Power BI
      ↓
Data Transformation / Modeling
      ↓
Reports & Visualizations
```

So this installation is a **setup/preparation step for the upcoming Power BI project**.

---

## ⭐ Final Revision Summary

> **MySQL Server** = database engine that stores and manages data.

> **MySQL Workbench** = GUI used to connect to the server and execute SQL.

> **Root password** = password configured during installation and later used to log in.

> **Port number** = communication endpoint used to connect to MySQL Server.

> **Database** contains **tables**, and tables contain **records/rows**.

Basic SQL demonstrated:

```sql
CREATE DATABASE test;

CREATE TABLE test.tab_one (
    c1 INT,
    c2 FLOAT
);

INSERT INTO test.tab_one
VALUES (1, 1.75);

INSERT INTO test.tab_one
VALUES (2, 2.75);

SELECT *
FROM test.tab_one;
```

The key practical flow to remember is:

**Install MySQL Server + Workbench → Connect to local MySQL → Create database → Create table → Insert data → Query data → Use MySQL as a Power BI data source.**
