# Power BI Desktop — Importing Data from Microsoft SQL Server

## 1. Objective of the Session

The main objective of this session is to learn **how to import data from Microsoft SQL Server into Power BI Desktop**.

In this project:

```text
SQL Server = Data Source
Power BI Desktop = Data Analysis & Visualization Tool
```

The overall workflow is:

```text
Microsoft SQL Server
        ↓
Power BI Desktop
        ↓
Data Model
        ↓
Power Query / DAX
        ↓
Reports & Dashboard
```

In the previous session, KPIs and chart suggestions were obtained from **Perplexity**. In this session, the focus shifts to actually bringing the SQL Server data into Power BI.

---

# 2. Open Power BI Desktop

The instructor first opens **Power BI Desktop**.

Since Power BI Desktop may take some time to start, the instructor waits for it to load.

Once Power BI Desktop opens, there are different options available.

Because the project will use SQL Server as the data source, you can either:

### Option 1 — Start with a blank report

Click:

```text
Blank report
```

### Option 2 — Connect directly to data

Since the data source is SQL Server, you can also directly select the appropriate data connection option.

For this lecture, the instructor chooses:

> **Blank report**

---

# 3. Use Perplexity to Learn the SQL Server Connection Process

The instructor assumes that a user may not know how to connect Power BI Desktop to SQL Server.

Instead of manually figuring it out, the instructor demonstrates how an AI tool such as **Perplexity** can provide step-by-step guidance.

The instructor goes to Perplexity and asks essentially:

> I am using Power BI Desktop. How may I import data from SQL Server? Describe the steps step by step.

The purpose of this is to obtain instructions for connecting Power BI to SQL Server.

---

# 4. Perplexity's Suggested Steps

Perplexity provides the following general process:

1. Go to the **Home** tab in Power BI Desktop.
2. Click **Get Data**.
3. Select **SQL Server database**.
4. Enter the **SQL Server name**.
5. Optionally provide the **database name**.
6. Choose the appropriate connectivity mode.
7. Select the required tables.
8. Either:

   * Load the data directly, or
   * Transform the data before loading.

These are the steps that the instructor follows.

---

# 5. Go to the Home Tab in Power BI

Return to Power BI Desktop.

At the top of the Power BI interface, locate the:

```text
Home
```

tab.

Under the Home tab, locate:

```text
Get Data
```

The **Get Data** option allows Power BI to connect to different external data sources.

Examples of possible data sources include:

* SQL Server
* Excel
* CSV
* Web
* Other databases
* Cloud services

For this project, SQL Server is the required source.

---

# 6. Select SQL Server as the Data Source

Click:

```text
Home → Get Data
```

A list of available data sources appears.

Locate:

```text
SQL Server
```

Select it.

This opens the SQL Server database connection dialog.

---

# 7. Enter SQL Server Connection Details

Power BI now asks for the SQL Server connection details.

The important fields include:

### Server

You need to provide the name of the SQL Server instance/server.

### Database

The database name is **optional** at this stage.

In this project, the database created previously is:

```text
PBI1
```

The instructor chooses to provide the server name first and then selects the database from the available databases.

---

# 8. Find the Server Name in SSMS

To obtain the correct SQL Server name, the instructor goes back to **SSMS**.

The instructor uses the **Connect to Database Engine** window.

The server name is visible there.

The instructor:

1. Goes to SSMS.
2. Looks at the **Server name**.
3. Copies the server name.
4. Returns to Power BI Desktop.
5. Pastes the server name into the SQL Server connection dialog.

### Important

The Power BI server name must correspond to the SQL Server instance where the `PBI1` database was created.

---

# 9. Choose the Connectivity Mode

Power BI provides different ways to connect to SQL Server.

The instructor chooses:

> **Import**

### Import mode

With Import mode:

```text
SQL Server
     ↓
Data is imported
     ↓
Power BI stores a copy of the data
     ↓
Power BI works with that imported data
```

The instructor specifically chooses Import because they want:

> **A copy of the data to be created inside Power BI Desktop itself.**

This is an important concept.

---

# 10. Import vs. DirectQuery — Basic Understanding

Although the lecture focuses on Import, it is useful to understand why the connectivity choice matters.

### Import

Data is brought into Power BI's data model.

```text
SQL Server → Power BI Data Model
```

Power BI can then work with the imported copy.

### DirectQuery

Power BI generally keeps the data in the source system and sends queries back to the database when required.

```text
Power BI
   ↓
SQL Server
   ↓
Query result
   ↓
Power BI
```

For this project, the instructor chooses:

> **Import connectivity mode**

because the intention is to create a copy of the data in Power BI.

---

# 11. Connect to the SQL Server

After entering the server name:

1. Paste the SQL Server name.
2. Select **Import** as the connectivity mode.
3. Click:

```text
OK
```

Power BI connects to the SQL Server.

---

# 12. Select the PBI1 Database

After establishing the connection, Power BI displays the databases available on the SQL Server.

The instructor expands:

```text
PBI1
```

This is the database created in the previous SQL Server session.

Inside the database, the imported table is visible.

The relevant table is:

```text
diamonds
```

---

# 13. Select the Diamonds Table

The instructor expands the `PBI1` database and sees the available table:

```text
diamonds
```

This is the same table that was previously verified in SQL Server as:

```text
dbo.diamonds
```

The data source relationship is therefore:

```text
SQL Server
    ↓
PBI1 Database
    ↓
dbo.diamonds
    ↓
Power BI
```

---

# 14. Preview the Data

Power BI provides a preview of the selected table.

The instructor waits for the preview to load.

The preview allows you to verify that:

* The correct database has been selected.
* The correct table has been selected.
* The data looks as expected.
* The columns are present.
* The connection is working correctly.

---

# 15. Load vs. Transform

At this point, Power BI provides two important options:

### Load

```text
Load
```

Use this when you want to directly bring the data into Power BI.

### Transform Data

```text
Transform Data
```

Use this when you want to clean, modify, or transform the data before loading it.

---

# 16. What Does "Load" Mean?

If you click **Load**, Power BI directly imports the selected data into its data model.

The flow is:

```text
SQL Server
     ↓
diamonds table
     ↓
Power BI
     ↓
Data Model
```

The instructor chooses this option in the current session.

---

# 17. What Does "Transform" Mean?

The alternative is:

```text
Transform Data
```

This opens the **Power Query Editor**.

Power Query can be used for tasks such as:

* Removing unwanted columns
* Changing data types
* Handling missing values
* Removing duplicates
* Renaming columns
* Filtering rows
* Creating calculated/transformed columns
* Splitting columns
* Merging data
* Other data-cleaning operations

However, the instructor **does not perform these transformations in this session**.

The instructor says that:

> Data cleaning and better data understanding will be discussed in upcoming sessions.

Those sessions will use **Power Query Editor**.

---

# 18. Directly Load the Data

For the current session, the instructor wants to directly load the data.

So:

1. Select/check the `diamonds` table.
2. Wait for the preview to load.
3. Click:

```text
Load
```

Power BI begins importing the data.

The instructor waits while the data is loaded.

---

# 19. Verify the Data in the Data Pane

Once loading is complete, look at the **right-hand side** of Power BI Desktop.

The **Data pane** contains the imported table.

Click the dropdown/expand option for the table.

You can now see the columns contained in the dataset.

These are the same columns that were previously examined in SSMS.

The Power BI model now contains the imported SQL Server data.

---

# 20. View the Data Using Table/Data View

Power BI also provides a table/data view.

The instructor clicks the **Table/Data view** icon.

This allows the actual records to be inspected.

The instructor verifies that:

* The `diamonds` table is available.
* The columns are available.
* The records are visible.
* The data corresponds to what was previously seen in SQL Server.

Therefore, the SQL Server → Power BI connection and import have been successful.

---

# 21. Compare SQL Server Data with Power BI Data

The instructor verifies that the data visible in Power BI is the same data that was previously viewed in SQL Server.

Previously:

```text
SQL Server
   ↓
dbo.diamonds
   ↓
53,940 records
```

Now:

```text
SQL Server
   ↓
PBI1
   ↓
dbo.diamonds
   ↓
Power BI
```

This confirms that Power BI has successfully imported the SQL Server dataset.

---

# 22. Complete Process

The complete procedure from this lecture is:

```text
1. Open Power BI Desktop
          ↓
2. Select Blank Report
          ↓
3. Home → Get Data
          ↓
4. Select SQL Server
          ↓
5. Get Server Name from SSMS
          ↓
6. Enter Server Name
          ↓
7. Select Import connectivity mode
          ↓
8. Click OK
          ↓
9. Select PBI1 database
          ↓
10. Select diamonds table
          ↓
11. Review data preview
          ↓
12. Choose Load
          ↓
13. Wait for import to complete
          ↓
14. Expand table in Data pane
          ↓
15. Open Data/Table view
          ↓
16. Verify columns and records
```

---

# 23. Important Power BI Concepts

## Get Data

**Get Data** is the starting point for connecting Power BI to external data sources.

For this project:

```text
Home → Get Data → SQL Server
```

---

## Server Name

The server name identifies the SQL Server instance to which Power BI needs to connect.

You can obtain it from the SQL Server/SSMS connection details.

---

## Database

The database contains the tables that Power BI can import.

In this project:

```text
Database = PBI1
```

---

## Table

The actual project data is stored in:

```text
dbo.diamonds
```

Power BI imports this table.

---

## Import Connectivity

Import creates a copy of the source data in Power BI's data model.

For this project:

```text
Connectivity Mode = Import
```

---

## Load

**Load** directly imports the selected table into Power BI.

---

## Transform Data

**Transform Data** opens Power Query and allows you to clean/transform the data before loading it.

The instructor postpones this step for upcoming sessions.

---

# 24. Why the Instructor Chooses Load Now

The instructor intentionally doesn't perform data cleaning yet.

The current objective is simply:

> **Understand how to connect SQL Server to Power BI and import the data.**

Data cleaning and deeper data understanding will be handled later using **Power Query Editor**.

This keeps the current session focused on establishing the data connection.

---

# 25. Role of Perplexity in This Session

Perplexity is used as a learning assistant.

The instructor doesn't assume that everyone already knows the connection procedure.

The process is:

```text
Question
   ↓
Ask Perplexity
   ↓
Get step-by-step instructions
   ↓
Apply those instructions in Power BI
   ↓
Verify the result
```

This is another example of using AI tools to assist with technical workflows.

---

# 26. Key Takeaways

* **SQL Server is the data source** for this Power BI project.
* Power BI Desktop can directly connect to SQL Server.
* Use:

```text
Home → Get Data → SQL Server
```

* The **server name** can be copied from SSMS.
* The database can be selected after establishing the connection.
* The project's database is:

```text
PBI1
```

* The required table is:

```text
dbo.diamonds
```

* The instructor uses **Import** connectivity.
* Import means Power BI creates a copy of the source data in its own data model.
* **Load** directly imports the table.
* **Transform Data** would open Power Query for cleaning/transformation.
* Data cleaning is intentionally postponed to upcoming sessions.
* After loading, the table and its columns appear in Power BI's **Data pane**.
* The **Data/Table view** can be used to verify the imported records.
* The Power BI data is confirmed to be the same dataset previously viewed in SQL Server.

---

# 27. Quick Revision

### SQL Server → Power BI

```text
Open Power BI
      ↓
Blank Report
      ↓
Home
      ↓
Get Data
      ↓
SQL Server
      ↓
Enter Server Name
      ↓
Select Import
      ↓
OK
      ↓
Select PBI1
      ↓
Select diamonds
      ↓
Preview
      ↓
Load
      ↓
Data Pane
      ↓
Table/Data View
      ↓
Verify Data
```

### Most important distinction

| Option             | Purpose                                                  |
| ------------------ | -------------------------------------------------------- |
| **Load**           | Directly import data into Power BI                       |
| **Transform Data** | Open Power Query and clean/transform data before loading |
| **Import**         | Store an imported copy of the data in Power BI           |
| **SQL Server**     | Source/database from which the data is obtained          |

### One-line takeaway

> **Power BI Desktop → Get Data → SQL Server → enter server name → choose Import → select PBI1 → select diamonds → Load → verify the table and columns in Power BI.**
