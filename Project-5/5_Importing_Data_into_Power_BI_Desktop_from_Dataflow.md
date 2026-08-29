# Connecting Power BI Desktop to a Data Flow

## 1. Introduction

This session explains how to **connect Power BI Desktop to the Data Flow created in the previous sessions** and bring the Data Flow data into Power BI Desktop.

The overall project architecture is now:

```text
Excel File
    ↓
SQL Server
    ↓
Power BI Data Flow
    ↓
Power BI Desktop
    ↓
Data Cleaning
    ↓
Report Creation
    ↓
Power BI Service
    ↓
Scheduled Refresh
```

The main objective of this session is to retrieve the `loan_default` data from the previously created Data Flow and load it into Power BI Desktop.

---

# 2. Prerequisites

Before following this session, you should already have:

* Power BI Desktop installed
* Power BI account
* Access to the Power BI workspace
* Data Flow created successfully
* Data Flow containing the `loan_default` table
* Data Flow refreshed/available

The Data Flow created earlier was:

> **dataflow SQL**

and it contains:

> **Loan Default**

---

# 3. Open Power BI Desktop

Open **Power BI Desktop**.

We will use the **Get Data** functionality to connect Power BI Desktop to the Data Flow.

---

# 4. Open Get Data

### Steps

1. Open Power BI Desktop.
2. Click:

**Get Data**

3. Select:

**More**

This opens the complete list of available data connectors.

---

# 5. Search for Data Flows

In the Get Data window:

1. Search for:

**Data Flow**

2. Select the first option:

> **Dataflows**

3. Click **Connect**.

Power BI will now ask you to sign in.

---

# 6. Sign in to Power BI

Click:

**Sign in**

Use the same Power BI credentials that were used earlier to access the Power BI account.

### Steps

1. Click **Sign in**.
2. Enter your Power BI account email/username.
3. Enter the password.
4. Complete the authentication process.

---

# 7. Authenticator App / Additional Authentication

The instructor has an **Authenticator app** activated on the account.

Therefore, an additional sign-in request appears.

You may see an authentication/approval request.

### Important

This additional step may **not appear for every user**.

If you have not configured an Authenticator app or additional authentication, you may simply be able to sign in using your normal credentials.

After successful authentication, continue with the connection.

---

# 8. Connect to the Data Flow

After signing in, Power BI displays the available Data Flows/workspaces.

Under:

**Workspaces**

you should be able to locate the Data Flow workspace created earlier.

The navigation is approximately:

```text
Workspaces
    ↓
Data Flow
    ↓
dataflow SQL
    ↓
Loan Default
```

The instructor selects:

> **dataflow SQL**

Then selects:

> **Loan Default**

---

# 9. Select the Loan Default Data

Once `Loan Default` is selected, Power BI displays a preview of the available data.

You can inspect the data before loading it.

The data is the same data that was:

```text
Excel
  ↓
SQL Server
  ↓
Data Flow
```

and is now being brought into:

```text
Power BI Desktop
```

---

# 10. Load the Data

Once the `Loan Default` table is visible:

1. Select the table.
2. Verify that the data is available.
3. Click:

**Load**

Power BI will load the Data Flow data into the Power BI Desktop model.

---

# 11. Important Issue — Data Flow May Initially Appear Empty

This is an important practical point mentioned in the lecture.

If you have **just created the Data Flow**, the data may not immediately be available when you try to connect from Power BI Desktop.

You may encounter:

* Empty table
* No visible data
* Data Flow appearing without the expected records

### Why can this happen?

The Data Flow may require some time to:

* Process the data
* Complete its initial refresh
* Make the data available for downstream consumption

Therefore, if you have just created the Data Flow:

> **Wait for some time before trying to connect to it from Power BI Desktop.**

Then try the connection again.

### Practical sequence

```text
Create Data Flow
      ↓
Wait for Data Flow processing/refresh
      ↓
Open Power BI Desktop
      ↓
Get Data → Dataflows
      ↓
Connect
      ↓
Select Data Flow
      ↓
Select Table
```

This can prevent confusion when the table initially appears empty.

---

# 12. Verify the Data in the Data Pane

After loading the Data Flow:

1. Look at the **Data pane** on the right side of Power BI Desktop.
2. Expand the `Loan Default` table.

You should now see the columns contained in the table.

The instructor expands the table and confirms that the expected columns are available.

---

# 13. View the Data Using Table View

Power BI Desktop provides a **Table View** where you can inspect the loaded data.

### Steps

1. Click the **Table View** icon.
2. Select the `Loan Default` table.
3. Inspect the records.

You should now be able to see the actual loan data that came from the Data Flow.

This confirms that the connection was successful.

---

# 14. End-to-End Connection

At this point, the data has successfully traveled through the entire source-to-Power-BI pipeline:

```text
Excel File
     ↓
Microsoft SQL Server
     ↓
SQL Server Table
dbo.loan_default
     ↓
Power BI Data Flow
dataflow SQL
     ↓
Loan Default
     ↓
Power BI Desktop
```

This demonstrates how Power BI Desktop can consume a **Data Flow as a data source**.

---

# 15. Why This Architecture Is Useful

The important concept is that Power BI Desktop is **not directly connecting to the original Excel file** in this setup.

Instead, it connects to the centralized Data Flow.

The Data Flow acts as an intermediate data-preparation layer.

```text
             Data Source
                 ↓
            SQL Server
                 ↓
             Data Flow
       (Centralized Preparation)
                 ↓
          Power BI Desktop
                 ↓
              Reports
```

This becomes especially useful when multiple reports or users require the same prepared data.

---

# 16. Verification Steps

After loading the Data Flow, perform these checks:

### Check 1 — Table exists

In the Data pane, verify that:

**Loan Default**

is available.

### Check 2 — Columns exist

Expand the table and verify that the expected columns are present.

### Check 3 — Data exists

Open **Table View** and verify that records are visible.

If all three checks are successful, the Data Flow connection is working correctly.

---

# 17. Important Steps to Remember

The complete connection procedure is:

### Step 1

Open **Power BI Desktop**.

### Step 2

Click:

**Get Data**

### Step 3

Click:

**More**

### Step 4

Search for:

**Data Flow**

### Step 5

Select:

**Dataflows**

### Step 6

Click:

**Connect**

### Step 7

Sign in using your Power BI credentials.

### Step 8

Complete additional authentication if required.

### Step 9

Go to:

**Workspaces**

### Step 10

Select the Data Flow workspace.

### Step 11

Select:

**dataflow SQL**

### Step 12

Select:

**Loan Default**

### Step 13

Click:

**Load**

### Step 14

Check the **Data pane**.

### Step 15

Expand the table and verify the columns.

### Step 16

Open **Table View**.

### Step 17

Verify that the actual data is visible.

---

# 18. Important Interview Questions

### Q1. How do you connect a Power BI Desktop report to a Data Flow?

Go to:

**Get Data → More → Dataflows → Connect**

Then sign in, select the required workspace, select the Data Flow and table, and click **Load**.

---

### Q2. What happens if a newly created Data Flow appears empty?

If the Data Flow was created recently, it may take some time to process/refresh and make the data available.

Wait for some time and then try connecting again.

---

### Q3. What Data Flow was used in this project?

The project uses:

> **Data Flow Gen1**

---

### Q4. Which table was loaded into Power BI Desktop?

> **Loan Default**

This table originated from the SQL Server table:

> `dbo.loan_default`

---

### Q5. What is the purpose of a Data Flow between SQL Server and Power BI Desktop?

The Data Flow acts as a centralized data preparation layer where data can be cleaned and transformed before being consumed by Power BI reports.

---

### Q6. How can you verify that the Data Flow connection worked?

You can:

1. Expand the table in the **Data pane**.
2. Verify the expected columns.
3. Open **Table View**.
4. Confirm that the actual records are visible.

---

# 19. What Has Been Completed So Far?

At this stage of the project:

* ✅ SQL Server installed and configured
* ✅ `loan` database created
* ✅ `loan_default` table created
* ✅ Excel data loaded into SQL Server
* ✅ On-premises Data Gateway configured
* ✅ Data Flow workspace created
* ✅ Data Flow Gen1 created
* ✅ SQL Server connected to Data Flow
* ✅ `loan_default` data added to Data Flow
* ✅ Data Flow saved
* ✅ Data Flow manually refreshed
* ✅ Refresh history checked
* ✅ Power BI Desktop connected to Data Flow
* ✅ `Loan Default` table loaded into Power BI Desktop
* ✅ Data verified in Table View

---

# 20. Upcoming Project Steps

The lecture indicates that the upcoming sessions will cover the remaining parts of the project:

### 1. Data Cleaning

The data loaded from the Data Flow will be cleaned and transformed.

This will include handling issues such as the date-format problem identified earlier.

### 2. Reporting

After preparing the data, Power BI visuals and reports will be created.

### 3. Publishing

The completed Power BI report will be published to:

**Power BI Service**

### 4. Scheduled Refresh

The project will also cover configuring **scheduled refresh**, so that the data can be refreshed automatically rather than manually.

---

# 21. Final Project Architecture

The complete architecture being developed through these sessions is:

```text
                    EXCEL FILE
                        │
                        ▼
                MICROSOFT SQL SERVER
                        │
                        │
                  loan database
                        │
                        ▼
                 loan_default table
                        │
                        ▼
             ON-PREMISES DATA GATEWAY
                        │
                        ▼
              POWER BI DATA FLOW GEN1
                        │
                        │
                 dataflow SQL
                        │
                        ▼
                POWER BI DESKTOP
                        │
                        ▼
                 DATA CLEANING
                        │
                        ▼
                    REPORTING
                        │
                        ▼
                POWER BI SERVICE
                        │
                        ▼
                SCHEDULED REFRESH
```

## Key Takeaway

The most important concept from this session is:

> **Power BI Desktop can consume a Power BI Data Flow just like other supported data sources.**

The Data Flow acts as a centralized layer between the original SQL Server data and Power BI Desktop, allowing the organization to prepare data centrally and make that prepared data available to reporting users.
