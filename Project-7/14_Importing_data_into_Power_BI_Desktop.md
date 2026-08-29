# Power BI: Connecting Power BI Desktop to MySQL Database

## 1. Objective of the Session

The purpose of this session is to establish a connection between **Power BI Desktop** and the **MySQL database** that was prepared in the previous sessions.

The overall migration is moving from:

```text
Microsoft SQL Server
        ↓
   Power BI Report
```

to:

```text
MySQL Database
        ↓
   Power BI Report
```

In this session, we are **not yet transitioning the complete report**. We are first establishing the MySQL connection and loading the required data into Power BI.

---

# 2. Prerequisites

Before starting, the following should already be available:

* Power BI Desktop
* MySQL Server
* MySQL Workbench
* MySQL database named `prod`
* Required tables inside the `prod` database
* `New_Table` created in MySQL
* MySQL username and password

The MySQL database was prepared in the previous sessions by:

1. Creating the `prod` database.
2. Importing the production inventory dataset.
3. Importing the Products table.
4. Performing required data cleaning/updates.
5. Creating `New_Table` using the required `LEFT JOIN`.

---

# 3. Open Get Data in Power BI Desktop

Open **Power BI Desktop**.

From the Home tab:

**Home → Get Data**

The Get Data menu appears.

At the bottom, click:

**More...**

This opens the complete list of available connectors.

---

# 4. Search for the MySQL Connector

In the search box, type:

```text
MySQL
```

You will see:

```text
MySQL database
```

Select/double-click **MySQL database**.

This is the connector that allows Power BI Desktop to connect to MySQL.

---

# 5. Enter the MySQL Server Details

After selecting the MySQL connector, Power BI asks for the server and database information.

### Server

Enter:

```text
localhost
```

`localhost` means the MySQL Server is running on the same computer.

### Database

Enter:

```text
prod
```

This is the production database created earlier in MySQL Workbench.

So the connection information is conceptually:

| Setting  | Value       |
| -------- | ----------- |
| Server   | `localhost` |
| Database | `prod`      |

---

# 6. Use the Advanced Options

The connection dialog also provides **Advanced options**.

In the SQL statement/query box, enter:

```sql
SELECT * FROM New_Table;
```

The purpose of this query is to directly retrieve the data from the `New_Table` table.

The table was created in MySQL specifically so that it contains the data structure required for the Power BI report.

### Why use `New_Table`?

Because `New_Table` contains the prepared and joined data that we want to use for reporting.

Therefore:

```text
MySQL prod database
        ↓
    New_Table
        ↓
SELECT *
        ↓
    Power BI
```

---

# 7. Click OK

After entering:

* Server = `localhost`
* Database = `prod`
* SQL statement = `SELECT * FROM New_Table`

click:

**OK**

Power BI will now attempt to connect to the MySQL database.

---

# 8. Enter MySQL Credentials

Power BI will ask for authentication details.

You need to provide the **MySQL username and password** that were configured when MySQL Server was installed.

In the lecture, the username is:

```text
root
```

The password is the password that was set during the MySQL installation.

### Important

Use the credentials that belong to your own MySQL installation.

If you don't remember the credentials, refer back to the earlier course session covering:

* MySQL Server installation
* MySQL Workbench installation
* Username/password configuration

---

# 9. Connect to MySQL

After entering the credentials:

1. Enter username.
2. Enter password.
3. Click **Connect**.

Power BI should now successfully connect to MySQL.

---

# 10. Data Appears in Power BI

After successfully connecting, Power BI will display the data retrieved from MySQL.

The data corresponds to the `New_Table` created earlier.

At this point, Power BI is able to communicate with the MySQL database.

---

# 11. Load the Data

Once the data is displayed:

Click:

**Load**

Power BI will begin loading the data into the Power BI model.

The loading process may take some time depending on the amount of data.

In the lecture, the dataset contains:

```text
1043 records
```

The data is therefore loaded into the Power BI model from MySQL.

---

# 12. Verify the Model

After the data has finished loading, go to **Model View**.

You can see the tables/queries that exist in the Power BI model.

The lecture shows two relevant objects:

### 1. Query 1

`Query 1` represents the data that was imported through the newly established **MySQL connection**.

### 2. Demand / Availability Table

The **Demand/Availability** table was associated with the earlier SQL Server-based setup and had been renamed/created during the previous work.

So the model can contain objects originating from different stages of the exercise.

---

# 13. Understanding "Query 1"

The instructor specifically points out that:

> `Query 1` is the table/query where the data imported from the MySQL database has been loaded.

This is important because Power BI's name for an imported query may not automatically be the same as the database table name.

The database table is:

```text
New_Table
```

but Power BI may initially create a query named:

```text
Query 1
```

The next stage of the exercise will deal with transitioning the existing report to this MySQL-based data.

---

# 14. Connection Flow

The complete connection established in this session is:

```text
                  MySQL Server
                       │
                       │ localhost
                       ↓
                  prod database
                       │
                       ↓
                   New_Table
                       │
                       │ SELECT *
                       ↓
                MySQL Connector
                       │
                       ↓
                 Power BI Desktop
                       │
                       ↓
                Power BI Model
```

---

# 15. What Has Been Accomplished?

By the end of this session, we have successfully:

* Opened Power BI Desktop.
* Opened **Get Data**.
* Selected the **MySQL database** connector.
* Specified the MySQL server as `localhost`.
* Specified the database as `prod`.
* Used the `New_Table` table.
* Used a SQL query to retrieve the data.
* Provided MySQL credentials.
* Connected Power BI Desktop to MySQL.
* Loaded the data into the Power BI model.
* Verified the data in Model View.

---

# 16. Why This Is Only a Preparation Step

It is important to distinguish between **connecting to MySQL** and **migrating the existing report**.

### This session:

```text
Connect Power BI → MySQL
        ↓
Load MySQL data
        ↓
Verify connection
```

### Next session:

```text
Existing Power BI Report
        ↓
Currently uses SQL Server
        ↓
Change data source
        ↓
Use MySQL instead
        ↓
Test existing report
```

The goal is still **not to recreate the report**.

The existing report already contains:

* Visuals
* DAX measures
* Calculations
* Formatting
* Report pages
* Model logic

We want to reuse all of those wherever possible.

---

# 17. Important Concept: Data Source Migration

The larger project can now be understood as:

```text
BEFORE

SQL Server
    ↓
New Table
    ↓
Power BI
    ↓
Existing Report
```

After migration:

```text
AFTER

MySQL
    ↓
New_Table
    ↓
Power BI
    ↓
Existing Report
```

The **data source changes**, but the report should continue to provide the same business insights.

---

# 18. Things to Verify During the Connection

Before proceeding to the actual migration, make sure:

### Server

```text
localhost
```

is correct.

### Database

```text
prod
```

is correct.

### Table

```text
New_Table
```

exists.

### Query

```sql
SELECT * FROM New_Table;
```

returns the expected data.

### Authentication

The MySQL username and password are correct.

### Record count

The expected production data contains approximately:

```text
1043 records
```

---

# 19. Key Takeaways

### 1. MySQL requires its own connector

Power BI Desktop has a dedicated **MySQL database** connector.

### 2. Use the correct server and database

For this exercise:

```text
Server   → localhost
Database → prod
```

### 3. Advanced options can be used to provide SQL

The query:

```sql
SELECT * FROM New_Table;
```

can be supplied directly while establishing the connection.

### 4. MySQL authentication is required

Use the username/password configured during MySQL Server installation.

### 5. Loading data is different from migrating the report

Successfully loading MySQL data proves that the connection works, but the actual report migration comes next.

### 6. Existing report logic should be preserved

The objective is to change:

```text
SQL Server → MySQL
```

without unnecessarily recreating:

```text
DAX + Visuals + Formatting + Report Pages
```

---

# 20. Quick Revision — Exact Steps

```text
1. Open Power BI Desktop
        ↓
2. Home → Get Data
        ↓
3. Click More
        ↓
4. Search "MySQL"
        ↓
5. Select MySQL database
        ↓
6. Server = localhost
        ↓
7. Database = prod
        ↓
8. Advanced options
        ↓
9. Enter:
   SELECT * FROM New_Table;
        ↓
10. Click OK
        ↓
11. Enter MySQL username
        ↓
12. Enter MySQL password
        ↓
13. Click Connect
        ↓
14. Verify the data
        ↓
15. Click Load
        ↓
16. Wait for data to load
        ↓
17. Open Model View
        ↓
18. Verify the MySQL-loaded query/table
```

## Final Concept

> **The purpose of this session is to establish and verify a working connection between Power BI Desktop and the prepared MySQL `prod` database. Once Power BI can successfully retrieve `New_Table` from MySQL, we have the technical foundation required for the next step: transitioning the existing Power BI report from SQL Server to MySQL without recreating the report from scratch.**
