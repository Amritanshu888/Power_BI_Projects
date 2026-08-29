# Detailed Notes — Power BI Project 2: Insurance Data Analysis

## 1. Project Overview

This lecture begins the **second Microsoft Power BI project**, which is based on an **Insurance dataset**.

The overall project will involve:

* Connecting Power BI to **Microsoft SQL Server**
* Importing the insurance data into Power BI
* Understanding and profiling the data
* Cleaning and transforming the data
* Creating the Power BI report
* Publishing the report to **Power BI Service**
* Implementing **Row-Level Security (RLS)**
* Scheduling data refresh

The instructor will cover these topics throughout the project video series.

---

# 2. Create a Free Power BI Account Before Starting

Before following the complete project series, you should create a **free Power BI account**.

There is already a separate lecture available explaining how to create the account.

### Why is the account required?

During report development in **Power BI Desktop**, you do **not necessarily need to sign in**.

However, later in the project, the report will be:

> **Published to Power BI Service**

Therefore, you will need a Power BI account for the publishing/service portion of the project.

### Important distinction

Power BI consists of two major components being used here:

```text
Power BI Desktop
       ↓
Report Development
       ↓
Power BI Service
       ↓
Publishing / Online Features
```

### Before starting the project

You should therefore:

1. Create a free Power BI account.
2. Install/open Power BI Desktop.
3. Have Microsoft SQL Server available.
4. Have the insurance dataset loaded into SQL Server.

---

# 3. Open Power BI Desktop

The instructor starts Power BI Desktop.

### Steps

1. Locate the **Power BI Desktop** icon.
2. Double-click it.
3. Wait for Power BI Desktop to open.

It may take some time to launch.

---

# 4. Select Blank Report

Since SQL Server will be used as the data source, Power BI provides an option to directly select SQL Server.

You can either:

### Option 1 — Directly select SQL Server

Click:

> **Microsoft SQL Server**

from the available data-source options.

### Option 2 — Start with Blank Report

Click:

> **Blank Report**

The instructor chooses **Blank Report**.

---

# 5. Sign-In Decision

Power BI may provide a sign-in option.

For now:

> **Do not sign in.**

The instructor will sign in later when the report needs to be published to **Power BI Service**.

So, at the report-development stage, you can continue without signing in.

---

# 6. Connect Power BI to SQL Server

Since **Microsoft SQL Server** is the data source, Power BI needs to establish a connection to it.

There are two ways to select SQL Server.

### Method 1

Click:

> **Microsoft SQL Server**

directly from the available data-source options.

### Method 2

Use:

> **Get Data → SQL Server**

The instructor explains both possibilities.

---

# 7. Real-World Scenario: Connecting to an Organization's Database

In a real organization, clients/customers generally store their data in databases.

For example:

```text
Organization
     ↓
Database
     ↓
Tables
     ↓
Business Data
```

When working for such an organization, you will generally be provided with details such as:

* Server name
* Database name
* Authentication/credentials
* Other connection information

These details allow Power BI to connect to the organization's database.

---

# 8. Provide SQL Server Connection Details

Since the instructor is using the SQL Server installed locally on the system, the instructor provides the corresponding server details.

The SQL Server connection dialog requires the relevant server information.

### Server

Provide the appropriate:

> **Server name**

for your SQL Server installation.

### Database

Providing the database name is:

> **Optional**

The instructor does **not** provide the database name at this stage.

The database will instead be selected from the list after connecting.

---

# 9. Choose the Connectivity Mode

Power BI provides different connectivity modes.

The instructor mentions:

* **Import**
* **DirectQuery**

For this project, the selected mode is:

> **Import**

DirectQuery will be discussed later.

---

# 10. Import Connectivity Mode

In **Import mode**, Power BI creates a copy of the source data inside the Power BI model.

Conceptually:

```text
SQL Server
    │
    │ Import
    ↓
Power BI Data Model
    │
    ├── Data Cleaning
    ├── Data Transformation
    ├── Data Modeling
    └── Reporting
```

### Advantages in the context of this project

Once the data is imported into Power BI, you can:

* Clean the data.
* Transform the data.
* Create relationships/models.
* Create calculations.
* Build visualizations.
* Create reports.
* Publish the report to Power BI Service.

The instructor will discuss the relevant concepts throughout the project.

---

# 11. Connect to SQL Server

After entering the required server information:

1. Select **Import** connectivity mode.
2. Click **OK**.

Power BI then connects to SQL Server.

A database selection window appears.

---

# 12. Select the Required Database

Power BI displays the databases available through the SQL Server connection.

The instructor sees:

* **AdventureWorks 2019**
* **InsuranceDB**
* **Practice**

The required insurance dataset is located inside:

> **InsuranceDB**

Therefore:

1. Expand **InsuranceDB**.
2. Locate the insurance data table.
3. Select:

> **Insurance Data**

---

# 13. Load vs Transform Data

After selecting the table, Power BI provides two important options:

### Load

If you click:

> **Load**

Power BI directly loads the data into the Power BI data model.

### Transform Data

If you click:

> **Transform Data**

Power BI opens:

> **Power Query Editor**

The instructor chooses:

> **Transform Data**

---

# 14. Why Transform Data Instead of Directly Loading?

The instructor does not want to immediately load the data into the model.

Instead, the columns should first be reviewed.

The workflow is:

```text
SQL Server
    ↓
Power Query Editor
    ↓
Review / Clean / Transform
    ↓
Close & Apply
    ↓
Power BI Data Model
```

This allows us to inspect the dataset before putting it into the final model.

---

# 15. Power Query Editor — Dataset Preview

Power Query Editor opens and displays a preview of the dataset.

The instructor notes that the preview currently displays approximately:

> **Top 1,000 rows**

The complete dataset contains approximately:

> **10,000 rows**

The preview is therefore only a subset used to inspect the data.

---

# 16. Understanding the Insurance Dataset

The dataset contains a **single table**.

The instructor goes through each column to understand what the data represents.

The columns are important because they will later be used for:

* Data analysis
* Calculations
* Filtering
* Visualizations
* Reporting

---

# 17. Policy Number

### Column

> **Policy Number**

### Meaning

This represents the **unique policy number**.

It allows an individual insurance policy to be identified.

Conceptually:

```text
Policy Number
-------------
P001
P002
P003
...
```

Each policy should have its own identifying policy number.

---

# 18. Customer ID

### Column

> **Customer ID**

This identifies the customer associated with the insurance policy/claim.

A customer can potentially have relationships with different policies.

The dataset contains customer IDs for customers who have raised claims associated with the policies in the dataset.

---

# 19. Gender

### Column

> **Gender**

This represents the gender of the customer who has taken the insurance policy.

It is a customer-related attribute.

---

# 20. Age

### Column

> **Age**

This represents the age of the customer.

It is another customer demographic attribute.

It can later be useful for analysis such as:

* Claims by age
* Policy distribution by age
* Customer segmentation

---

# 21. Policy Type

### Column

> **Policy Type**

This represents the type/category of insurance policy.

The dataset contains different types of insurance policies, including:

* **Auto**
* **Health**
* **Home**
* **Life**
* **Travel**

These are the insurance policy categories available in the dataset.

---

# 22. Policy Start Date

### Column

> **Policy Start Date**

This represents the date on which the insurance policy started.

It can later be used for time-based analysis.

For example:

```text
Policy Start Date
       ↓
Monthly / Yearly analysis
       ↓
Policy trends
```

---

# 23. Policy End Date

### Column

> **Policy End Date**

This represents the date on which the insurance policy ended.

Together, Policy Start Date and Policy End Date can provide information about the policy's duration.

---

# 24. Premium Amount

### Column

> **Premium Amount**

The premium is the amount charged by the insurance company to the customer.

In other words, it represents the amount collected by the insurance company from the client/customer for the insurance policy.

For example:

```text
Customer
   ↓
Pays Premium
   ↓
Insurance Company
```

Premium amount can therefore be used for analyzing the revenue/amount collected through policies.

---

# 25. Coverage Amount

### Column

> **Coverage Amount**

Coverage amount represents the total amount of **risk coverage** provided to the customer by the insurance company.

It represents the maximum/defined coverage associated with the policy.

For example, if the policy provides coverage of ₹100, the customer may be covered for losses up to that policy's coverage amount, subject to the policy terms.

---

# 26. Claim Number

### Column

> **Claim Number**

Each policy in this dataset has a corresponding claim raised by the customer.

The claim number/claim ID allows an individual claim to be identified.

Conceptually:

```text
Policy
  ↓
Claim
  ↓
Claim Number
```

---

# 27. Claim Date

### Column

> **Claim Date**

This represents the date on which the insurance claim was raised.

This column can later be used for time-based claim analysis.

---

# 28. Claim Amount

### Column

> **Claim Amount**

This represents the actual amount for which the customer raised the claim.

### Example from the lecture

Suppose:

* Coverage amount = ₹100
* Customer's actual loss = ₹20

The customer would raise a claim for:

> **₹20**

rather than ₹100.

So:

```text
Coverage Amount = ₹100
Actual Loss     = ₹20
Claim Amount    = ₹20
```

The important distinction is:

> **Coverage Amount** = amount of risk/coverage provided by the insurance policy.

> **Claim Amount** = actual amount being claimed by the customer.

---

# 29. Claim Status

### Column

> **Claim Status**

This indicates the current outcome/status of the claim.

The instructor identifies three possible statuses:

* **Settled**
* **Pending**
* **Rejected**

### Settled

The insurance company has processed and settled the claim.

### Pending

The claim is still being processed.

### Rejected

The company has rejected the claim.

A claim could be rejected for various reasons. The instructor gives **fake claims** as an example.

For example:

```text
Fake claim detected
        ↓
Company identifies the issue
        ↓
Claim rejected
```

---

# 30. Complete Dataset Structure

The dataset consists of a **single table** containing the columns discussed above.

| Column            | Meaning                                       |
| ----------------- | --------------------------------------------- |
| Policy Number     | Unique identifier for the policy              |
| Customer ID       | Identifier of the customer                    |
| Gender            | Customer gender                               |
| Age               | Customer age                                  |
| Policy Type       | Type of insurance policy                      |
| Policy Start Date | Date policy started                           |
| Policy End Date   | Date policy ended                             |
| Premium Amount    | Amount charged/collected by insurance company |
| Coverage Amount   | Coverage/risk amount provided                 |
| Claim Number      | Identifier for the claim                      |
| Claim Date        | Date claim was raised                         |
| Claim Amount      | Amount claimed by customer                    |
| Claim Status      | Status of the claim                           |

---

# 31. Close & Apply

After reviewing the columns, the instructor is ready to load the data into the Power BI model.

### Steps

1. In Power Query Editor, click:

> **Close & Apply**

2. Power BI displays a message indicating that pending changes in the query need to be applied.
3. Power BI begins applying the changes.
4. Wait for the process to complete.

---

# 32. Data Loading Process

Power BI goes through stages such as:

> **Creating connection in the model**

and:

> **Loading data into the model**

This may take some time.

The instructor waits for the process to complete.

---

# 33. Approximately 10,000 Rows Loaded

The instructor notes that the dataset contains approximately:

> **10,000 rows**

These rows are successfully loaded into the Power BI model.

This means the data is now available for reporting and analysis.

---

# 34. View the Data in Power BI

After loading is complete, the insurance data appears in Power BI's data/model area.

The instructor can see:

> **Insurance Data**

along with the columns discussed earlier.

The available columns include:

* Policy Number
* Customer ID
* Gender
* Age
* Policy Type
* Policy Start Date
* Policy End Date
* Premium Amount
* Coverage Amount
* Claim Number
* Claim Date
* Claim Amount
* Claim Status

---

# 35. Table/Data View

The instructor then clicks the:

> **Table View**

option.

This displays the actual rows of the loaded dataset.

So you can now inspect the data that has been imported into the Power BI model.

At this point, the insurance dataset is ready to be used for reporting.

---

# 36. End-to-End Process Completed in This Lecture

The complete process demonstrated is:

```text
1. Create Power BI account
          ↓
2. Open Power BI Desktop
          ↓
3. Select Blank Report
          ↓
4. Get Data → SQL Server
          ↓
5. Provide SQL Server details
          ↓
6. Select Import mode
          ↓
7. Connect to SQL Server
          ↓
8. Select InsuranceDB
          ↓
9. Select Insurance Data
          ↓
10. Transform Data
          ↓
11. Open Power Query Editor
          ↓
12. Review columns
          ↓
13. Close & Apply
          ↓
14. Load ~10,000 rows
          ↓
15. View data in Power BI
```

---

# 37. Power BI Desktop vs Power BI Service

A key concept from this lecture is the distinction between **Power BI Desktop** and **Power BI Service**.

### Power BI Desktop

Used primarily for:

* Connecting to data
* Data transformation
* Data modeling
* Creating reports
* Creating visualizations

### Power BI Service

Used for online/cloud functionality such as:

* Publishing reports
* Sharing reports
* Managing published content
* Configuring certain security features
* Scheduling data refresh

For this project:

```text
Power BI Desktop
       ↓
Create & develop report
       ↓
Publish
       ↓
Power BI Service
```

---

# 38. Topics to Be Covered Later in the Project

The instructor previews several topics that will be covered in subsequent lectures.

## Data Profiling

The dataset will be analyzed to understand its quality and characteristics.

## Report Creation

Visualizations and report pages will be created based on the insurance data.

## Publishing to Power BI Service

The completed Power BI report will be published online.

## Row-Level Security (RLS)

Security rules will be implemented so that users can be restricted to viewing only the data they are authorized to see.

## Scheduled Refresh

The project will also cover how to configure scheduled data refresh so that data can be refreshed automatically.

---

# 39. Important Concepts to Remember

### 1. SQL Server is the Data Source

For this project:

> **Microsoft SQL Server → Power BI**

The data is not being loaded from an Excel file directly into Power BI.

---

### 2. Import Mode is Being Used

The project uses:

> **Import connectivity mode**

Power BI creates a copy of the source data in its model.

---

### 3. Transform Before Loading

Instead of directly clicking **Load**, the instructor selects:

> **Transform Data**

This opens Power Query Editor, allowing the dataset to be reviewed/transformed before loading it into the model.

---

### 4. Dataset Contains One Table

The insurance dataset consists of a **single table** containing all the columns discussed.

---

### 5. Approximately 10,000 Rows

The complete dataset contains approximately **10,000 rows**, while Power Query initially displays a preview of approximately **1,000 rows**.

---

### 6. Power BI Account Is Required Later

You don't need to sign in while initially developing the report in Power BI Desktop.

However, you need a Power BI account for the later:

> **Publish → Power BI Service**

workflow.

---

# 40. Final Project Architecture

The architecture established by this lecture is:

```text
                 SQL SERVER
                     │
                     │
              ┌──────▼──────┐
              │ InsuranceDB │
              └──────┬──────┘
                     │
                     │ SQL Server Connection
                     ▼
             ┌───────────────┐
             │ Power BI      │
             │ Desktop       │
             └───────┬───────┘
                     │
          ┌──────────┼──────────┐
          │          │          │
          ▼          ▼          ▼
      Transform   Modeling   Reporting
          │          │          │
          └──────────┼──────────┘
                     │
                     ▼
             Power BI Service
                     │
          ┌──────────┼───────────┐
          ▼          ▼           ▼
       Publish      RLS      Scheduled
                              Refresh
```

## Final Takeaway

The main objective of this lecture is to **connect Power BI Desktop to the InsuranceDB database in SQL Server, open the Insurance Data table in Power Query, review the dataset's columns, and finally load approximately 10,000 rows into the Power BI model using Import mode**.

Once this foundation is ready, the subsequent lectures can focus on **data profiling, report creation, publishing to Power BI Service, Row-Level Security, and scheduled refresh**.
