# Loading Excel Data into Microsoft SQL Server for Power BI Data Flow

## 1. Introduction

This session focuses on preparing **Microsoft SQL Server as the data source for a Power BI Data Flow**.

The overall process in this project is:

**Excel file → SQL Server → Data Flow → Power BI**

The Excel file already contains the data, but instead of directly using Excel as the Data Flow source, the project uses **Microsoft SQL Server**.

The reason for this is that the project specifically demonstrates how to use SQL Server as the source for creating a Data Flow.

---

# 2. Prerequisite — SQL Server and SSMS

Before following this session, you should already have:

* Microsoft SQL Server installed
* SQL Server Management Studio (SSMS) installed
* A working SQL Server connection

If you don't know how to install SQL Server and SSMS, the instructor recommends referring to the earlier project in the course that specifically explains:

> **Microsoft SQL Server as a Data Source**

The first video of that project covers:

* Downloading SQL Server
* Installing SQL Server
* Installing SSMS
* Connecting to SQL Server

So, if SQL Server is already installed on your system, you can directly continue with this session.

---

# 3. Open SQL Server Management Studio

First, open:

**SQL Server Management Studio (SSMS)**

SSMS may take some time to open.

Once the **Connect to Server** window appears, provide the required server details.

### Connection settings

Use:

* **Server Type:** Database Engine
* **Server Name:** Your SQL Server instance/server name
* **Authentication:** Windows Authentication

Then click:

**Connect**

---

# 4. Open a New Query Window

After successfully connecting to SQL Server:

1. Click **New Query**.
2. A new SQL query window will open.

We will use this window to:

* Create a database
* Select the database
* Execute SQL commands
* Verify the imported data

---

# 5. Overall Data Flow Architecture

The project has the following data movement:

```text
Excel File
    ↓
Microsoft SQL Server
    ↓
Power BI Data Flow
    ↓
Power BI
```

The Excel file is the original source.

However, the project does **not** directly create the Data Flow from Excel.

Instead:

1. Data is first loaded from Excel into SQL Server.
2. SQL Server becomes the source for the Data Flow.
3. The Data Flow will later bring the processed data into Power BI.

---

# 6. Why Use SQL Server Instead of Excel Directly?

The instructor mentions that **Excel could also be used as a source** for creating the Data Flow.

However, this particular project intentionally uses:

> **Microsoft SQL Server**

as the source.

Therefore, the immediate task is to transfer the data:

**Excel → SQL Server**

After that, SQL Server will be used as the source when creating the Data Flow.

The benefits and reasons for using Data Flows will be discussed in the upcoming sessions.

---

# 7. Create a Database in SQL Server

The first step is to create a database where the Excel data will be loaded.

In the SSMS query window, write:

```sql
CREATE DATABASE loan;
```

Then execute the command.

If successful, SQL Server displays a message similar to:

> Commands completed successfully.

---

# 8. Switch to the Newly Created Database

After creating the database, select it as the active database.

Execute:

```sql
USE loan;
```

Again, SQL Server should display:

> Commands completed successfully.

Now the `loan` database is the active database for subsequent operations.

---

# 9. Verify the Database in Object Explorer

On the left side of SSMS, you will see:

**Object Explorer**

If the Databases section isn't expanded:

1. Click the **+** icon next to **Databases**.
2. Look for the newly created database.

You should see:

**loan**

So the structure will look approximately like:

```text
Databases
│
├── System Databases
│
├── ...
│
└── loan
```

---

# 10. Import the Excel Data into SQL Server

Now we need to load the Excel data into the `loan` database.

### Steps

1. In **Object Explorer**, locate the `loan` database.
2. Right-click on **loan**.
3. Select **Tasks**.
4. Select:

**Import Flat File**

This opens the SQL Server import wizard.

> The lecture uses the **Import Flat File** option to import the provided data file.

---

# 11. Start the Import Wizard

After selecting **Import Flat File**:

1. The import wizard opens.
2. Click **Next**.

The wizard will ask you to provide the location of the file.

---

# 12. Select the Data File

The project has a data file named:

**Loan Default**

The instructor selects this file.

### Steps

1. Click **Browse**.
2. Navigate to the location containing the data file.
3. Select **Loan Default**.
4. Double-click the file.
5. Continue by clicking **Next**.

The wizard may take some time to analyze the file.

---

# 13. Continue Through the Import Wizard

After selecting the file, the import wizard displays additional configuration screens.

The instructor proceeds through them by clicking:

**Next → Next → Finish**

The exact sequence shown in the lecture is:

1. Select the file.
2. Click **Next**.
3. Click **Next** again.
4. Click **Finish**.

The data insertion/import process then begins.

---

# 14. Wait for Data Import to Complete

After clicking **Finish**, SQL Server begins inserting the data into the database.

You may see a message indicating:

> **Data insertion is in progress**

This process may take some time depending on the size of the data.

Wait until the process completes.

Once successful, the wizard displays a success message.

The instructor then closes the dialog.

---

# 15. Locate the Imported Table

Now that the data has been imported, we need to verify that the table was created.

In **Object Explorer**:

1. Expand the `loan` database using the **+** icon.
2. Expand **Tables**.

You should see a table named:

**loan_default**

The structure will look approximately like:

```text
Databases
│
└── loan
    │
    └── Tables
        │
        └── dbo.loan_default
```

The imported Excel data is now stored inside this SQL Server table.

---

# 16. Open the Imported Table

The instructor then opens the table to inspect the data.

You can:

1. Double-click the `loan_default` table, or otherwise open/inspect it in SSMS.
2. The table/data can be brought into the query environment for inspection.

The table contains the loan-related dataset.

---

# 17. Query the Imported Table

To retrieve all records from the table, use:

```sql
SELECT *
FROM dbo.loan_default;
```

Here:

* `SELECT` → retrieves data
* `*` → selects all columns
* `FROM` → specifies the source table
* `dbo.loan_default` → the schema and table name

### Equivalent one-line form

```sql
SELECT * FROM dbo.loan_default;
```

---

# 18. Execute the Query

The instructor writes the query in the query window.

### Steps

1. Write:

```sql
SELECT * FROM dbo.loan_default;
```

2. Select/highlight the SQL statement.
3. Click **Execute**.
4. SQL Server returns the contents of the table.

The returned result confirms that the Excel data has successfully been loaded into SQL Server.

---

# 19. Data Available in the Table

The returned dataset contains multiple columns related to loan/customer information.

The instructor mentions examples such as:

* **Loan ID**
* **Age**
* **Income**
* **Loan Amount**
* Other columns

The exact column definitions are not discussed in this session.

The instructor states that the meanings of the columns will be discussed later.

---

# 20. Data Format Issue — Date Column

While examining the data, the instructor notices an issue with the **last column**, which contains date information.

The column name indicates that it represents a date, but the actual date values are not displayed in the expected format.

The lecture indicates that the dates appear to be in a format similar to:

**YYYYMDD / YYYYMMDD-style representation**

rather than the desired date representation.

Therefore, the raw imported data requires some cleaning/transformation.

---

# 21. Where Will Data Cleaning Be Performed?

The instructor does **not** clean the date format in SQL Server at this stage.

Instead, the plan is to handle this data-cleaning requirement later in:

> **Power BI**

So the current objective is simply to ensure that the data has been successfully loaded into SQL Server.

### Important distinction

At this stage:

**Data loading → SQL Server ✅**

**Data cleaning → Power BI later**

---

# 22. What Has Been Accomplished?

By the end of this session, the following has been completed:

### SQL Server setup

* SQL Server is available.
* SSMS is opened.
* Connection to the SQL Server Database Engine is established.

### Database creation

A database named:

```text
loan
```

has been created.

### Data loading

The Excel/flat-file data:

```text
Loan Default
```

has been imported into SQL Server.

### Table creation

The imported data is stored in:

```text
dbo.loan_default
```

### Verification

The table was queried using:

```sql
SELECT * FROM dbo.loan_default;
```

and the records were successfully returned.

Therefore:

> **Excel → SQL Server loading is successfully completed.**

---

# 23. Complete Process Flow

The complete process from this lecture can be remembered as:

```text
Loan Default Excel/File
        ↓
Open SQL Server Management Studio
        ↓
Connect to Database Engine
        ↓
Create Database
        ↓
CREATE DATABASE loan;
        ↓
USE loan;
        ↓
Right-click loan Database
        ↓
Tasks
        ↓
Import Flat File
        ↓
Browse
        ↓
Select Loan Default file
        ↓
Next → Next → Finish
        ↓
Data Insertion
        ↓
Import Successful
        ↓
Expand loan Database
        ↓
Expand Tables
        ↓
loan_default
        ↓
SELECT * FROM dbo.loan_default;
        ↓
Verify Data
```

---

# 24. SQL Commands Used

The main SQL commands from this session are:

### Create database

```sql
CREATE DATABASE loan;
```

### Select database

```sql
USE loan;
```

### Retrieve all data

```sql
SELECT * FROM dbo.loan_default;
```

---

# 25. Important Concepts

## Database

A **database** is a logical container used to organize and store data.

Here, the database created is:

```text
loan
```

---

## Table

A table stores the actual structured records.

Here, the imported table is:

```text
loan_default
```

---

## Schema

The table is referenced as:

```text
dbo.loan_default
```

Here:

* `dbo` → schema
* `loan_default` → table name

So:

```text
dbo.loan_default
       ↑
    table
```

---

# 26. Why Verify the Data Using SELECT?

Running:

```sql
SELECT * FROM dbo.loan_default;
```

is important because it verifies that:

1. The database was created successfully.
2. The import process worked.
3. The table was created.
4. The data was inserted.
5. SQL Server can successfully retrieve the imported records.

It is therefore a simple validation step before moving to the Data Flow creation.

---

# 27. Important Interview Points

### Q1. What is the source data in this project?

The original data is available in an **Excel/file-based source**.

### Q2. Why is SQL Server being used?

The project specifically demonstrates creating a **Power BI Data Flow using SQL Server as the source**.

### Q3. What is the overall data pipeline?

```text
Excel → SQL Server → Data Flow → Power BI
```

### Q4. What database was created?

```text
loan
```

### Q5. What table was created after importing the data?

```text
dbo.loan_default
```

### Q6. How do you import the file into SQL Server?

From SSMS:

**Database → Right-click → Tasks → Import Flat File → Browse → Select file → Next → Finish**

### Q7. How do you verify that the data was imported?

Run:

```sql
SELECT * FROM dbo.loan_default;
```

### Q8. Was data cleaning performed in this session?

No.

The instructor noticed a date-format issue but planned to handle the **data-cleaning step later in Power BI**.

---

# 28. Key Takeaways

* **SQL Server** is being used as the source for the upcoming Data Flow.
* The original data is available in an Excel/file format.
* Instead of directly using Excel, the project first loads the data into SQL Server.
* A database named **`loan`** is created.
* The data is imported using **Import Flat File**.
* The resulting table is **`dbo.loan_default`**.
* The imported data is verified using `SELECT *`.
* The dataset contains columns such as Loan ID, Age, Income, Loan Amount, etc.
* A date-format issue is observed.
* Data cleaning will be handled later in **Power BI**.
* The next step is to create the **Data Flow** using SQL Server as the source and eventually bring the data into Power BI.

### Final Architecture

**Excel / Loan Default File**
↓
**Microsoft SQL Server (`loan`)**
↓
**`dbo.loan_default` table**
↓
**Power BI Data Flow**
↓
**Power BI**

This session therefore completes the **SQL Server data preparation stage** required before creating the Data Flow.
