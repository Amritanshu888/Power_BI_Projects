# Power BI Project 2 — Connecting SQL Server to Power BI Desktop & Importing the Data

## 1. Objective of the Session

In the previous sessions, the banking dataset was:

* Created in SQL Server
* Populated with data
* Cleaned for date inconsistencies
* Combined into one physical table

In this session, the goal is to **connect SQL Server to Power BI Desktop** and import the newly created **Combined Banking Data Set** into Power BI.

The workflow is:

```text id="5u2y8w"
SQL Server
    ↓
Power BI Desktop
    ↓
SQL Server Connector
    ↓
Server Name
    ↓
Import Connectivity Mode
    ↓
PowerBI2 Database
    ↓
Combined Banking Data Set
    ↓
Load
    ↓
10,000 Records in Power BI
    ↓
Further Data Cleaning
```

---

# 2. Starting Point

The previous session focused on removing inconsistencies from the date columns.

Now the cleaned data needs to be brought into Power BI.

The important table created previously is:

> **Combined Banking Data Set**

This table contains the combined information from:

* Transactions
* Accounts
* Customers

and contains **10,000 records**.

---

# 3. Open Power BI Desktop

The first step is to open:

**Power BI Desktop**

The application may take some time to launch.

Once Power BI Desktop opens, the objective is to establish a connection with SQL Server.

---

# 4. Select SQL Server as the Data Source

On the Power BI Desktop home screen, select:

> **SQL Server**

This is important because the banking dataset is stored in SQL Server.

### Steps

1. Open Power BI Desktop.
2. Click **SQL Server**.
3. Wait for the SQL Server connection dialog to appear.

---

# 5. Obtain the SQL Server Name

Power BI needs the **server name** to establish the connection.

The instructor gets the server name from SQL Server Management Studio (SSMS).

### Steps in SSMS

1. Open **SQL Server Management Studio**.
2. Press:

```text
F8
```

This opens the:

> **Object Explorer**

3. Click:

> **Connect → Database Engine**

4. The SQL Server connection window displays the **Server name**.

The instructor copies this server name.

---

# 6. Enter Server Name in Power BI

Return to Power BI Desktop.

In the SQL Server connection dialog:

1. Paste the copied SQL Server **Server name**.
2. Select the appropriate data connectivity mode.
3. Choose:

> **Import**

4. Click **OK**.

---

# 7. Import vs Other Connectivity Modes

The instructor specifically selects:

> **Import Data Connectivity Mode**

This means Power BI will import a copy of the selected data into the Power BI model.

Conceptually:

```text id="8q4y0w"
SQL Server
    ↓
Power BI Import
    ↓
Power BI Data Model
```

The data is therefore available inside Power BI for reporting and analysis.

---

# 8. Wait for the SQL Server Connection

After clicking **OK**, Power BI may take some time to establish the connection.

Once the connection succeeds, Power BI displays the available databases/tables through the Navigator interface.

---

# 9. Select the Database

The database created in the earlier sessions is:

> **PowerBI2**

The lecture refers to the database as `power_BI_two` / `power underscore BI two`; the exact database name should match the one created in SQL Server.

Select this database in the Navigator.

---

# 10. Select Combined Banking Data Set

Inside the database, the instructor finds:

> **Combined Banking Data Set**

This is the table that will be used for the Power BI report.

### Steps

1. Expand/select the database.
2. Locate **Combined Banking Data Set**.
3. Check the checkbox beside the table.
4. Wait for the preview to load.

---

# 11. Preview the Data Before Loading

Power BI displays a preview of the selected table.

The instructor checks the preview before loading.

The preview contains the same data that was available in SQL Server.

This is a useful validation step because it allows you to confirm:

* Correct table selected
* Expected columns are present
* Data is visible
* SQL Server connection is working
* The expected dataset is being imported

---

# 12. Click Load

Once the correct table has been selected and the preview has loaded:

> Click **Load**

Power BI now begins importing the data into the Power BI data model.

The import may take some time.

---

# 13. Data Is Loaded into Power BI

After the loading process finishes, the instructor confirms that:

> **All 10,000 records were loaded.**

This confirms that the Combined Banking Data Set has successfully been imported into Power BI.

The basic flow is:

```text id="q1t6tr"
SQL Server
    ↓
PowerBI2
    ↓
Combined Banking Data Set
    ↓
Power BI Import
    ↓
10,000 records
```

---

# 14. Open the Table/Data View

After the data is loaded, Power BI provides access to the imported table.

The instructor clicks on:

> **Table/Data View**

This allows the imported records to be inspected directly inside Power BI.

The data shown here corresponds to the data that was previously available in SQL Server.

---

# 15. Inspect the Imported Data

The instructor examines the imported dataset.

An important issue becomes visible:

> **There are many NULL/blank values.**

These values existed because of the joins used while creating the Combined Banking Data Set.

---

# 16. Why Are There NULL Values?

Recall the previous session.

The combined table was created using:

```text id="oj7b4s"
Transactions
    LEFT JOIN
Accounts
    LEFT JOIN
Customers
```

The purpose of using `LEFT JOIN` was to preserve all 10,000 transaction records.

However, some transactions had an `Account ID` that did not have a corresponding record in the Accounts table.

Therefore, when the tables were combined:

```text id="tdxg98"
Transaction Account ID
        ↓
No matching Account ID
        ↓
Account information = NULL
```

Similarly, missing customer matches can result in blank customer-related fields.

---

# 17. Account ID Example

The instructor specifically examines the **Account ID** field.

When the drop-down/filter is opened, there are:

* Valid Account ID values
* Blank values

This confirms that some transaction records contain an Account ID for which no corresponding account record was found during the join.

---

# 18. Why the NULL Values Are Not an Immediate Problem

The instructor does not consider this a critical issue at this stage.

The reason is that the project is going to perform additional:

> **Data cleaning in Power BI**

Therefore, these blank values will be handled later.

This is actually useful for learning because the dataset contains realistic data-quality problems that can be addressed using Power BI's transformation tools.

---

# 19. Important Learning — LEFT JOIN and Missing Values

This session reinforces an important concept from the previous session.

Using a LEFT JOIN allowed us to preserve all transaction records.

But the trade-off is that unmatched records can contain:

```text id="6wwk9e"
NULL / Blank
```

in the columns coming from the related tables.

So:

```text id="b1k3n4"
LEFT JOIN
    ↓
Preserve all left-table records
    ↓
Unmatched records
    ↓
NULL values in right-table columns
```

This is exactly what we are now seeing in Power BI.

---

# 20. Complete Step-by-Step Process

## Step 1 — Open Power BI Desktop

Launch Power BI Desktop.

---

## Step 2 — Select SQL Server

On the start screen, click:

> **SQL Server**

---

## Step 3 — Open SSMS

Open SQL Server Management Studio to obtain the server name.

---

## Step 4 — Open Object Explorer

Press:

```text
F8
```

This opens Object Explorer.

---

## Step 5 — Connect to Database Engine

In SSMS:

```text
Connect
   ↓
Database Engine
```

---

## Step 6 — Copy Server Name

Copy the server name displayed in the connection window.

---

## Step 7 — Return to Power BI

Paste the server name into the SQL Server connection dialog.

---

## Step 8 — Choose Import

Select:

> **Import**

as the Data Connectivity Mode.

Then click:

> **OK**

---

## Step 9 — Select Database

Choose:

> **PowerBI2**

---

## Step 10 — Select Table

Check:

> **Combined Banking Data Set**

---

## Step 11 — Wait for Preview

Allow Power BI to load the preview.

Inspect the data.

---

## Step 12 — Click Load

Click:

> **Load**

Power BI imports the dataset.

---

## Step 13 — Wait for Import

Allow Power BI to finish loading the data.

---

## Step 14 — Verify Record Count

Confirm that:

> **10,000 records**

have been loaded.

---

## Step 15 — Open Data/Table View

Click the table/data view to inspect the imported data.

---

## Step 16 — Inspect Data Quality

Look for:

* Blank Account IDs
* NULL values
* Missing related information
* Other potential data-quality issues

These will be addressed in the upcoming data-cleaning stage.

---

# 21. Connection Architecture

The connection created in this session can be visualized as:

```text id="c5vbrv"
┌───────────────────────────────┐
│        SQL Server             │
│                               │
│        PowerBI2 DB            │
│              │                │
│              ↓                │
│   Combined Banking Data Set   │
└───────────────┬───────────────┘
                │
                │ Import
                ↓
┌───────────────────────────────┐
│       Power BI Desktop        │
│                               │
│      Power BI Data Model      │
│              │                │
│              ↓                │
│       10,000 records          │
└───────────────────────────────┘
```

---

# 22. Key Power BI Concept — Import Mode

The lecture uses:

> **Import Data Connectivity Mode**

In Import mode, the data is brought into the Power BI model.

This generally allows Power BI to work with the imported data efficiently for report creation and analysis.

The important thing to remember for this lecture is simply:

```text
SQL Server → Import → Power BI Model
```

---

# 23. Why Use the Combined Table?

Instead of importing three separate tables:

```text
Customers
Accounts
Transactions
```

the instructor has already created:

> **Combined Banking Data Set**

Therefore, Power BI can work with one consolidated dataset.

This simplifies the upcoming analysis because transaction, account, and customer information is available together.

---

# 24. Why Not Clean Everything in SQL Server?

The instructor intentionally leaves some issues to be handled in Power BI.

This allows the project to demonstrate the **Power Query Editor** and data-cleaning capabilities.

The overall learning progression is therefore:

```text id="q6g5d9"
SQL Server
   ↓
Create data
   ↓
Basic SQL cleaning
   ↓
Combine tables
   ↓
Import into Power BI
   ↓
Power Query cleaning
   ↓
Analysis
   ↓
KPIs
   ↓
Visualizations
   ↓
Final Report
```

---

# 25. Important Issues Identified in This Session

After importing the data, the instructor notices:

### Issue 1 — Blank Account IDs

Some rows have valid Account IDs, while others contain blanks.

### Issue 2 — NULL values

Some fields contain NULL/blank values because the corresponding records did not match during the joins.

### Issue 3 — Data Cleaning Still Required

Although some cleaning was already done in SQL Server, the dataset still requires additional transformation in Power BI.

These issues will be addressed in subsequent sessions.

---

# 26. Key Concepts to Remember

### SQL Server

The original database where the banking data is stored.

### SSMS

Used to obtain the SQL Server connection information and manage the database.

### Power BI Desktop

Used to import the SQL Server data and build the report.

### Import Mode

Copies/imports the selected SQL Server data into the Power BI model.

### Combined Banking Data Set

The consolidated table created in the previous session and selected as the Power BI data source.

### Data View/Table View

Used to inspect the imported data inside Power BI.

### NULL/Blank Values

Can appear when the LEFT JOIN cannot find a corresponding record in the related table.

---

# 27. Interview/Revision Questions

### Q1. Which data source is being used?

**SQL Server.**

### Q2. Which Power BI connectivity mode is used?

**Import mode.**

### Q3. Which database is selected?

**PowerBI2** — using the exact database name created in the previous sessions.

### Q4. Which table is imported?

**Combined Banking Data Set.**

### Q5. How many records are imported?

**10,000 records.**

### Q6. Why are there blank Account IDs?

Some Account IDs in Transactions do not have corresponding records in the Accounts table.

### Q7. Why are NULL values present?

Because the Combined Banking Data Set was created using LEFT JOINs, which preserve transaction records even when matching account/customer information is unavailable.

### Q8. Where will the remaining data cleaning be performed?

In **Power BI**, particularly using Power Query/data-transformation functionality.

---

# 28. Final Revision Summary

> **In this session, the Combined Banking Data Set created in SQL Server was imported into Power BI Desktop. The SQL Server connector was selected, the server name was obtained from SSMS using Object Explorer, and Import connectivity mode was chosen. The PowerBI2 database and Combined Banking Data Set were selected, previewed, and loaded into Power BI. All 10,000 records were successfully imported. In the Power BI data view, blank Account IDs and other NULL values were observed because some transaction records did not have matching records in the Accounts/Customers tables. These remaining data-quality issues will be handled during the upcoming Power BI data-cleaning stage.**
