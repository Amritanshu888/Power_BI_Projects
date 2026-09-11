# Power BI Project 2 — Creating a Banking Dataset Using SQL Server

## 1. Objective of the Session

This session begins the **second Power BI project**. The main objective is to create a realistic **banking dataset** that can later be used as the data source for a Power BI report.

The workflow followed is:

**Perplexity → Generate requirements/prompt → Generate SQL → SQL Server → Create tables → Populate data → Generate 10,000 transactions → Validate data → Use in Power BI**

The dataset is intentionally designed to contain **data-cleaning issues**, so that Power Query can later be used to practice real-world data cleaning.

---

# 2. Why Use Perplexity for Dataset Creation?

Instead of manually designing an entire banking dataset, an AI tool such as Perplexity can be used to:

* Design the dataset structure
* Suggest relevant banking entities
* Recommend columns
* Generate SQL queries
* Suggest Power BI KPIs
* Recommend charts
* Generate DAX measures
* Generate dummy data
* Troubleshoot SQL errors

The important learning point is that **AI-generated code should not always be expected to work perfectly on the first attempt**.

You may need to:

1. Review the generated output.
2. Identify problems.
3. Give the error back to the AI.
4. Ask it to correct the query.
5. Execute the corrected version.

This is demonstrated later when the transaction-generation query initially produces an error.

---

# 3. Requirements for the Banking Dataset

The dataset should satisfy the following requirements.

### Dataset type

A **banking dataset**.

### Data source

The data will ultimately be stored in:

**SQL Server**

and then connected to:

**Power BI**

### Number of records

The project requires approximately:

**10,000 records**

The 10,000 records are specifically generated for the transaction data.

### Data-cleaning practice

The dataset should contain some **intentional data-quality issues**.

This is important because the next stage of the project will involve learning:

> **Data cleaning using Power Query Editor**

Examples of potential data-quality issues include:

* Missing values
* Inconsistent values
* Formatting inconsistencies
* Duplicate records
* Incorrect data types
* Inconsistent text values

The idea is to make the dataset more realistic rather than perfectly clean.

---

# 4. Power BI Report Requirements

The dataset should also be useful for creating a **two-page Power BI report**.

The requirement is:

| Report    |        KPIs |
| --------- | ----------: |
| Page 1    |      5 KPIs |
| Page 2    |      5 KPIs |
| **Total** | **10 KPIs** |

Therefore, while designing the dataset, we need to make sure that sufficient information exists to calculate meaningful banking KPIs.

Along with the KPIs, the AI is asked to recommend:

* Charts
* Visualizations
* DAX measures
* Insights that can be represented visually

---

# 5. First Step — Ask Perplexity to Create a Good Prompt

Instead of directly asking Perplexity to generate the entire dataset, the instructor first asks it to **craft a good prompt**.

The purpose is to create a detailed prompt that can subsequently be reused to generate the SQL/database structure.

The prompt asks Perplexity to:

> Craft a good prompt including examples for every requirement listed below.

The requirements include:

* Banking dataset
* SQL Server
* Approximately 10,000 records
* Data-cleaning issues
* Two-page Power BI report
* Five KPIs per page
* Ten KPIs overall
* Chart recommendations
* DAX measures
* Example fields
* Sample data
* SQL insert statements

### Why this approach is useful

Rather than immediately generating code, we first ask AI to **structure the requirements clearly**.

This gives us a reusable and more comprehensive prompt.

---

# 6. Generated Banking Dataset Prompt

Perplexity produces a prompt describing a synthetic banking dataset.

The generated requirements include entities such as:

* Customers
* Accounts
* Transactions

The prompt also specifies that the data should contain intentional data-quality issues.

It additionally asks for:

* Example fields
* Sample data
* Sample SQL INSERT statements
* Recommended KPIs
* Chart recommendations
* DAX measures

The AI also provides recommendations for:

### Power BI Page 1

Five KPIs and their corresponding DAX measures/visual recommendations.

### Power BI Page 2

Another five KPIs and corresponding DAX measures/visual recommendations.

---

# 7. Use the Generated Prompt Again in Perplexity

Once the detailed prompt has been generated:

1. Copy the prompt from Perplexity.
2. Open a new tab.
3. Open Perplexity again.
4. Paste the generated prompt.
5. Press **Enter**.
6. Review the output.

The purpose is now to have Perplexity actually generate the required dataset/database design.

---

# 8. Initial AI Output — SQL Generation

The initial output contains information about the banking dataset.

Initially, the SQL required to generate the entire dataset may not be completely appropriate.

Therefore, a follow-up prompt is used.

The instructor asks Perplexity to:

> Write SQL query that will first create the required tables and then write SQL query that will insert data into that table.

This is an important refinement.

Instead of asking for one large SQL script, the database creation is broken into two stages:

### Stage 1

Create the required tables.

### Stage 2

Insert/populate data into those tables.

---

# 9. Database Tables

Perplexity proposes three main tables:

1. **Customers**
2. **Accounts**
3. **Transactions**

The basic relationship can be understood as:

```text
Customers
    |
    | Customer ID
    ↓
Accounts
    |
    | Account ID
    ↓
Transactions
```

This creates a simple banking relational structure.

---

# 10. Customers Table

The **Customers** table stores information related to bank customers.

Typical customer-related information can include fields such as:

* Customer ID
* Customer name
* Customer details
* Demographic information

The exact columns should be taken from the generated SQL provided by the instructor.

The important point is that the customer table represents the **customer entity**.

---

# 11. Accounts Table

The **Accounts** table represents bank accounts associated with customers.

An account is linked to a customer through the appropriate customer identifier.

Conceptually:

```text
One Customer
      ↓
One or More Accounts
```

The Accounts table therefore acts as an intermediate entity between customers and their transactions.

---

# 12. Transactions Table

The **Transactions** table stores individual banking transactions.

The important fields visible later during validation are:

| Column           | Purpose                              |
| ---------------- | ------------------------------------ |
| Transaction ID   | Unique identifier of the transaction |
| Account ID       | Identifies the account involved      |
| Transaction Date | Date on which transaction occurred   |
| Type             | Debit or Credit                      |
| Amount           | Transaction amount                   |
| Description      | Description of transaction           |
| Currency         | Currency of transaction              |

This table becomes particularly important because it contains the **10,000 transaction records**.

---

# 13. Open SQL Server Management Studio

After generating the SQL, the instructor moves to:

**SQL Server Management Studio (SSMS)**

### Steps

1. Open **SQL Server Management Studio**.
2. Click **Connect**.
3. Open a **New Query** window.

---

# 14. Create the Database

A new database is created for the Power BI project.

The instructor uses a database name similar to:

```sql
CREATE DATABASE PowerBI2;
```

The exact naming in the lecture appears to be the project-specific `PowerBI2` database.

After creating the database, switch to that database using:

```sql
USE PowerBI2;
```

Then execute the statement.

### Important concept

`CREATE DATABASE` creates the database.

`USE` tells SQL Server which database subsequent SQL commands should operate against.

---

# 15. Create the Customers Table

After selecting the appropriate database, copy the **Customers CREATE TABLE statement** generated by Perplexity.

Paste it into SSMS.

Then:

1. Select the Customers table creation SQL.
2. Execute it.
3. SQL Server creates the Customers table.

The instructor confirms that the **Customers table was successfully created**.

---

# 16. Create the Accounts Table

Next, go back to the SQL generated by Perplexity.

Copy the `CREATE TABLE` statement for **Accounts**.

In SSMS:

1. Paste the query.
2. Select the Accounts table creation statement.
3. Execute it.

The Accounts table is successfully created.

---

# 17. Create the Transactions Table

Next, create the Transactions table.

Steps:

1. Copy the transaction table `CREATE TABLE` query.
2. Paste it into SSMS.
3. Select the query.
4. Execute it.

The Transactions table is successfully created.

At this point, the database structure is ready.

We now have:

```text
PowerBI2
│
├── Customers
├── Accounts
└── Transactions
```

---

# 18. Populate the Customers Table

Once the tables are created, the next task is to populate them with data.

Return to Perplexity.

The generated response contains an `INSERT` statement for customer data.

Copy the customer `INSERT` statement.

Go back to SSMS and:

1. Open a new query if required.
2. Paste the INSERT statement.
3. Select the statement.
4. Execute it.

The Customers table is now populated.

---

# 19. Populate the Accounts Table

Repeat the same process for Accounts.

### Steps

1. Return to Perplexity.
2. Find the Accounts `INSERT` statement.
3. Copy it.
4. Go to SSMS.
5. Paste the query.
6. Select the INSERT statement.
7. Execute it.

The Accounts table is now populated.

---

# 20. Problem — Need 10,000 Transaction Records

The initial transaction INSERT statement generated by Perplexity does not contain enough records.

The instructor notices:

> This SQL query will not create a dataset with 10,000 records.

Therefore, instead of manually writing 10,000 INSERT statements, a better approach is required.

The instructor asks Perplexity to generate:

> **10,000 dummy transactions using system views and ROW_NUMBER().**

---

# 21. Why Use System Views and ROW_NUMBER()?

Writing 10,000 individual INSERT statements manually would be inefficient.

SQL Server can generate rows programmatically.

The general idea is:

```text
SQL Server system/catalog views
          ↓
Generate many rows
          ↓
ROW_NUMBER()
          ↓
Generate transaction IDs
          ↓
Generate transaction attributes
          ↓
10,000 transaction records
```

This is much more scalable than manually inserting every transaction.

---

# 22. Initial Transaction Query Error

The first generated query is copied into SSMS and executed.

The query produces an error:

> **Windowed functions can only appear in the SELECT or ORDER BY clause.**

This is an important example of why AI-generated SQL needs to be tested.

The query looked plausible, but SQL Server rejected it because of the way a window function was being used.

---

# 23. Use the SQL Error as a Prompt

Instead of trying to manually debug the query, the instructor copies the SQL Server error.

The workflow is:

```text
SQL Query
   ↓
Execute in SSMS
   ↓
Error
   ↓
Copy error
   ↓
Paste into Perplexity
   ↓
Ask for corrected query
   ↓
Copy corrected query
   ↓
Execute again
```

This is a useful practical technique when working with AI coding assistants.

---

# 24. Perplexity Generates Corrected Query

The error message is pasted into Perplexity.

Perplexity analyzes the error and provides a corrected SQL query.

The corrected query properly handles the use of the window function.

The instructor then:

1. Copies the corrected query.
2. Goes back to SSMS.
3. Removes the old query.
4. Pastes the new query.
5. Executes it using **Ctrl + E**.

---

# 25. 10,000 Transactions Successfully Generated

The corrected query executes successfully.

The result indicates:

> **10,000 records impacted**

This confirms that the required transaction dataset has been generated.

Therefore, the database now contains a transaction dataset with approximately:

**10,000 transaction records**

---

# 26. Validate the Transaction Data

After generating the data, it is important to verify that the records were actually inserted correctly.

The instructor runs a simple `SELECT` query.

Conceptually:

```sql
SELECT *
FROM Transactions;
```

### Steps

1. Open a new query.
2. Write:

```sql
SELECT *
FROM Transactions;
```

3. Execute the query.
4. Inspect the returned records.

---

# 27. Inspecting the Transaction Data

The output shows the transaction information.

The visible columns include:

### Transaction ID

Unique identifier for each transaction.

### Account ID

Identifies the account associated with the transaction.

### Transaction Date

Date on which the transaction occurred.

### Type

Indicates whether the transaction is:

* Debit
* Credit

### Amount

The monetary value of the transaction.

### Description

Provides a description of what the transaction represents.

### Currency

Specifies the currency associated with the transaction.

---

# 28. Confirm the Number of Records

The instructor verifies that the Transactions table contains:

**10,000 records**

This is important because the original requirement was to create a dataset of approximately 10,000 records.

A more explicit validation query could also be written as:

```sql
SELECT COUNT(*) AS TotalRecords
FROM Transactions;
```

which should return:

```text
10000
```

---

# 29. Final Dataset Structure

At the end of this session, the banking database contains three major entities:

```text
                 ┌──────────────┐
                 │  Customers   │
                 └──────┬───────┘
                        │
                  Customer ID
                        │
                        ↓
                 ┌──────────────┐
                 │   Accounts   │
                 └──────┬───────┘
                        │
                   Account ID
                        │
                        ↓
                 ┌──────────────┐
                 │ Transactions │
                 └──────────────┘
                        │
                        ↓
                  10,000 rows
```

This relational structure will later be connected to Power BI.

---

# 30. Important Learning — AI Does Not Always Give Correct SQL

One of the key lessons from this session is that **AI-generated code must be validated**.

The instructor encounters exactly this situation.

### First attempt

AI generates SQL → SQL Server returns an error.

### Second attempt

Error is copied → given back to AI → AI generates corrected SQL.

### Final attempt

Corrected SQL → executed successfully → 10,000 records created.

Therefore:

> **Do not blindly copy and trust AI-generated SQL. Always execute, inspect, validate, and troubleshoot it.**

---

# 31. Overall Workflow to Remember

The complete workflow from this lecture is:

### Step 1 — Define requirements

Decide:

* Domain → Banking
* Database → SQL Server
* Records → ~10,000
* Data quality issues → Yes
* Power BI pages → 2
* KPIs → 10
* KPIs per page → 5

### Step 2 — Ask AI to craft a detailed prompt

Use Perplexity to create a structured prompt containing all requirements.

### Step 3 — Give that prompt back to AI

Use the generated prompt to obtain:

* Tables
* Fields
* Sample data
* SQL
* KPIs
* DAX
* Charts

### Step 4 — Refine the SQL request

Ask specifically for:

```text
CREATE TABLE statements
+
INSERT statements
```

### Step 5 — Create database in SSMS

```sql
CREATE DATABASE PowerBI2;
```

### Step 6 — Select database

```sql
USE PowerBI2;
```

### Step 7 — Create tables

Create:

```text
Customers
Accounts
Transactions
```

### Step 8 — Insert customer data

Execute the Customers INSERT statement.

### Step 9 — Insert account data

Execute the Accounts INSERT statement.

### Step 10 — Generate transactions

Use SQL Server system views and `ROW_NUMBER()` to generate 10,000 transactions.

### Step 11 — Troubleshoot

If SQL Server returns an error:

```text
Copy error
→ Give error to Perplexity
→ Ask for correction
→ Copy corrected SQL
→ Execute again
```

### Step 12 — Validate

Run:

```sql
SELECT *
FROM Transactions;
```

and verify the data.

Optionally verify the count:

```sql
SELECT COUNT(*)
FROM Transactions;
```

Expected result:

```text
10,000
```

---

# 32. Why This Dataset Is Being Created

The database is **not the final goal**.

It is being created as the data source for the upcoming **Power BI Project 2**.

The upcoming workflow will therefore be approximately:

```text
SQL Server
     ↓
Banking Dataset
     ↓
Power BI
     ↓
Power Query
     ↓
Data Cleaning
     ↓
Data Model
     ↓
DAX Measures
     ↓
KPIs
     ↓
Charts/Visuals
     ↓
Two-Page Banking Dashboard
```

The next sessions will build the Power BI report using this dataset.

---

# 33. Key Concepts to Remember

### Perplexity / AI

Used to help with:

* Dataset design
* Prompt generation
* SQL generation
* KPI recommendations
* Chart recommendations
* DAX recommendations
* SQL troubleshooting

### SQL Server

Used as the actual database where the data is stored.

### SSMS

**SQL Server Management Studio** is used to:

* Connect to SQL Server
* Create databases
* Create tables
* Insert data
* Execute SQL
* Inspect data
* Troubleshoot errors

### SQL Commands Used

Important commands/concepts from this lecture:

```sql
CREATE DATABASE
```

Creates a database.

```sql
USE
```

Selects the database in which subsequent operations will occur.

```sql
CREATE TABLE
```

Creates a table.

```sql
INSERT INTO
```

Adds records to a table.

```sql
SELECT *
FROM
```

Retrieves records from a table.

```sql
COUNT(*)
```

Counts records.

### SQL Window Function

`ROW_NUMBER()` is used as part of the approach to generate a large number of dummy transaction records.

---

# 34. Most Important Takeaways

1. **Define the Power BI requirements before creating the dataset.**
2. Use AI to help design a realistic synthetic dataset.
3. Create a reusable, detailed prompt rather than giving vague instructions.
4. Keep the database relational using entities such as **Customers, Accounts, and Transactions**.
5. Store the data in **SQL Server**, because SQL Server will be the Power BI data source.
6. Intentionally include data-quality problems for **Power Query practice**.
7. Use SQL Server's capabilities rather than manually generating thousands of records.
8. `ROW_NUMBER()` and system/catalog views can help generate large dummy datasets.
9. AI-generated SQL may contain errors.
10. **Always execute and validate AI-generated code.**
11. SQL errors can be copied back into the AI tool to obtain a corrected query.
12. Confirm the final record count rather than assuming the query worked.
13. The final dataset contains **10,000 transactions**.
14. The dataset is being prepared specifically for a **two-page Power BI report with 10 KPIs — five per page**.
15. The next stage is to bring this SQL Server data into Power BI and work on **data cleaning, modeling, DAX, KPIs, and visualizations**.

### One-line revision summary

> **In this session, a synthetic banking database was designed with AI, implemented in SQL Server using Customers, Accounts, and Transactions tables, populated with 10,000 transaction records, and validated before using it as the source for the second Power BI project.**
