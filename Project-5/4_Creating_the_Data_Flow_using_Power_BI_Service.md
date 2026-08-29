# Creating a Power BI Data Flow Gen1 Using SQL Server

## 1. Introduction

This session covers the complete process of creating a **Power BI Data Flow Gen1** using the SQL Server database that was prepared in the previous session.

The overall architecture being built is:

```text
Excel File
    ↓
Microsoft SQL Server
    ↓
Power BI Data Flow Gen1
    ↓
Power BI Desktop
```

The main objective of this session is to:

* Create a Data Flow in Power BI.
* Connect the Data Flow to SQL Server.
* Use the previously configured **On-premises Data Gateway**.
* Import the `loan_default` table into the Data Flow.
* Use **Power Query Online** for data transformation.
* Save the Data Flow.
* Manually refresh the Data Flow.
* Check refresh history.
* Understand why Data Flows are useful in a team environment.

---

# 2. Open Power BI Account

The instructor begins from the same **Power BI account** that was used earlier from Power BI Desktop.

### Steps

1. Open the Power BI account in the browser.
2. Click **Workspaces**.
3. Open the workspace named:

**Data Flow**

This is the workspace that was created in the earlier session.

---

# 3. Create a New Data Flow

Inside the **Data Flow** workspace:

1. Click **New Item**.
2. At the top, search for:

**Data Flow**

Power BI displays two options:

* **Data Flow Gen1**
* **Data Flow Gen2**

---

# 4. Data Flow Gen1 vs Gen2

The lecture mentions that Power BI may recommend using **Data Flow Gen2**.

Gen2 provides improved capabilities, particularly around:

* Data cleaning
* Data transformation
* Modern Fabric-based data workflows

However, for this particular project, the instructor deliberately chooses:

> **Data Flow Gen1**

### Steps

1. Search for Data Flow.
2. Select **Data Flow Gen1**.
3. Continue with the Data Flow creation process.

### Important

Even though Gen2 may be recommended, **do not switch to Gen2 for this particular project**, because the project demonstration is based on Gen1.

---

# 5. Add New Tables

After selecting Data Flow Gen1, Power BI provides an option to define tables for the Data Flow.

Select:

> **Add New Tables**

This allows us to choose the data source and specify which tables should be brought into the Data Flow.

---

# 6. Select SQL Server as the Data Source

The previous session loaded the Excel data into SQL Server.

Therefore, SQL Server will now be used as the Data Flow's source.

### Steps

1. Select **SQL Server**.
2. Provide the SQL Server connection details.

The SQL Server database created earlier was:

```text
loan
```

And the table containing the data is:

```text
loan_default
```

---

# 7. Find the SQL Server Name

You need the correct SQL Server **server name**.

The instructor obtains it from SQL Server Management Studio.

### Steps

1. Open **SQL Server Management Studio**.
2. Click **Connect** if required.
3. Select **Database Engine**.
4. Look at the server name shown in the connection window.
5. Copy the server name.

Then return to Power BI and paste this value into the **Server Name** field.

### Important

Your server name may be different from the instructor's.

Always use the server name configured on **your own SQL Server installation**.

---

# 8. Specify the Database

The database created in the previous session was:

```text
loan
```

Therefore, enter:

**Database: `loan`**

So the basic connection information is:

| Setting     | Value                       |
| ----------- | --------------------------- |
| Server      | Your SQL Server server name |
| Database    | `loan`                      |
| Data source | SQL Server                  |

---

# 9. Select/Create the Gateway Connection

The Data Flow needs to connect to the SQL Server through the gateway configured previously.

When configuring the connection, Power BI provides an option to create/select a connection.

The instructor selects the option related to:

> **On-premises Data Gateway**

The previously configured gateway was named:

**DF1**

Therefore, the gateway connection used here is associated with:

**Data Gateway — On-premises — DF1**

### Why is this gateway required?

The SQL Server is running on the local/on-premises computer.

Power BI Service needs the gateway to communicate with this SQL Server.

Therefore:

```text
Power BI Service
       ↓
On-premises Data Gateway (DF1)
       ↓
Local SQL Server
```

---

# 10. Select Authentication Method

The authentication method used in the lecture is:

> **Windows Authentication**

This means the connection will authenticate using the Windows account associated with the SQL Server access.

---

# 11. Provide Username

The next requirement is the Windows username.

The instructor obtains the username through the **Command Prompt**.

### Steps

1. Open **Command Prompt**.
2. Type:

```cmd
who am i
```

3. Press **Enter**.

The command returns the current Windows user/account information.

The instructor copies the required username portion.

4. Return to Power BI.
5. Paste the username into the **Username** field.

---

# 12. Provide Windows Password

Next, provide the password associated with the Windows account.

### Steps

1. Enter your Windows account password.
2. Make sure the password corresponds to the Windows account being used to access SQL Server.

---

# 13. Continue the Connection

After entering:

* Server name
* Database name
* Gateway
* Authentication method
* Username
* Password

click:

**Next**

Power BI will begin connecting to the SQL Server data source.

The connection process may take some time.

---

# 14. Privacy Level

Power BI asks for the privacy level.

In the lecture, the privacy level is kept as:

> **None**

Then click:

**Next**

Power BI will continue connecting to the data source.

---

# 15. Connect to the SQL Server Data

Power BI now starts connecting to the SQL Server.

You may see a message similar to:

> **Connecting to data source**

This can take some time.

Wait for the connection to complete.

Once connected, Power BI displays the available tables from the SQL Server database.

---

# 16. Select the `loan_default` Table

The SQL Server database contains the table created in the previous session:

```text
loan_default
```

The instructor selects this table.

### Steps

1. Locate `loan_default`.
2. Click/select the table.
3. Power BI will display a preview of the table data.

The table contains the loan dataset that was originally loaded from Excel.

---

# 17. Preview the Data

Once the table is selected, Power BI displays the data.

The available columns can be inspected before loading the data into the Data Flow.

The instructor waits for the data to load and confirms that the columns are visible.

---

# 18. Transform Data Using Power Query Online

The instructor then clicks:

> **Transform Data**

This opens the transformation environment.

An important concept here is that **Data Flows use Power Query Online**.

It is similar in concept to the **Power Query Editor available in Power BI Desktop**.

---

# 19. Power Query Online

Power Query Online allows you to perform various data preparation and transformation operations.

For example, you can perform operations such as:

* Removing unnecessary columns
* Renaming columns
* Changing data types
* Filtering rows
* Removing duplicates
* Replacing values
* Splitting columns
* Merging data
* Adding calculated/transformed columns
* Cleaning data

The key idea is:

> Data transformation can be performed centrally inside the Data Flow instead of every Power BI developer repeating the same transformations.

The instructor waits for the data to finish loading.

---

# 20. Columns in the Data Flow

After the data is loaded, the available columns are displayed.

The instructor observes the columns and then proceeds to save the Data Flow.

The columns also have associated **data types**.

These data types can be viewed in the Data Flow/Power Query interface.

---

# 21. Save and Close the Data Flow

After completing the required transformation setup:

1. Click **Save and Close**.
2. Power BI may take some time to save the Data Flow.

The Data Flow now needs a name.

---

# 22. Name the Data Flow

The instructor gives the Data Flow a suitable name:

> **dataflow SQL**

You can choose an appropriate name according to your project naming convention.

A description can also be provided.

### Description

The instructor provides a description similar to:

> Connecting to Power BI Desktop

The description is **optional**.

Therefore:

* Data Flow name → Required
* Description → Optional

After entering the details, click:

**Save**

---

# 23. Refresh the Data Flow

After saving, Power BI provides an option to:

* Refresh the Data Flow now
* Schedule a refresh for a later time

In this session, the instructor performs a **manual refresh**.

The Data Flow can therefore be refreshed immediately to retrieve the latest data from SQL Server.

---

# 24. Manual Refresh

The Data Flow can also be refreshed later directly from the workspace.

### Steps

1. Go to **Workspaces**.
2. Open the **Data Flow** workspace.
3. Locate the Data Flow.
4. Use the **Refresh** option.
5. Click the option to manually refresh the Data Flow.

Power BI begins retrieving/processing the data.

The refresh may take some time.

---

# 25. Refresh Status

After starting the refresh, you can check its status.

The instructor observes that the refresh is initially:

> **In Progress**

This means Power BI is still processing the refresh.

Wait for the process to complete.

Once completed, the refresh status changes accordingly.

---

# 26. Refresh History

Power BI provides a **Refresh History** option.

This allows you to check previous Data Flow refresh attempts.

### Steps

1. Locate the Data Flow in the workspace.
2. Open its options/menu.
3. Select **Refresh History**.
4. Check the status of the refresh.

The instructor initially sees:

> **In Progress**

After waiting and checking again, the status becomes:

> **Completed**

### If the status is still in progress

You can:

1. Open the Data Flow options.
2. Click the **three dots (`...`)**.
3. Select/check **Refresh History** again.
4. Verify the updated status.

---

# 27. Why Are Data Flows Useful?

This is one of the most important conceptual parts of the lecture.

Consider a team with:

> **5–7 Data Analysts**

Suppose all analysts need the **same data** for reporting.

The original data might be stored in SQL Server.

Without a centralized Data Flow, each analyst might have to:

1. Connect to SQL Server.
2. Extract the data.
3. Perform data cleaning.
4. Transform the data.
5. Prepare the data.
6. Use it for reporting.

The problem is that **all 5–7 analysts are repeating essentially the same data preparation process**.

---

# 28. Problem Without a Data Flow

Without a centralized transformation layer:

```text
                 SQL Server
                     ↓
        ┌────────────┼────────────┐
        ↓            ↓            ↓
    Analyst 1    Analyst 2    Analyst 3
        ↓            ↓            ↓
     Cleaning     Cleaning     Cleaning
        ↓            ↓            ↓
   Transformation Transformation Transformation
        ↓            ↓            ↓
      Report       Report       Report
```

This leads to:

* Repeated work
* Duplicate transformations
* Inconsistent logic
* More maintenance
* Wasted development time

For example, if an analyst performs a particular cleaning operation differently from another analyst, their reports could potentially produce different results.

---

# 29. Solution — Centralized Data Flow

A better approach is to create a **centralized Data Flow**.

The Data Flow performs the common data preparation/transformation once.

Then all analysts can consume the prepared data.

```text
                     SQL Server
                         ↓
                    Data Flow
                         ↓
              Cleaned / Transformed Data
                         ↓
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
      Analyst 1      Analyst 2      Analyst 3
          ↓              ↓              ↓
       Report          Report          Report
```

Instead of every analyst repeating the same transformations, the transformations are centralized.

---

# 30. Benefits of Data Flows

## 1. Centralized Data Preparation

Common cleaning and transformation logic can be maintained in one central location.

---

## 2. Avoids Repeated Work

Analysts do not need to independently perform the same transformations.

---

## 3. Consistent Data

Everyone can work with the same cleaned and transformed dataset.

This improves consistency between reports.

---

## 4. Reusability

Once data has been prepared in a Data Flow, it can be reused by multiple downstream reporting solutions.

---

## 5. Better Collaboration

Multiple analysts can consume the same prepared data instead of independently preparing their own versions.

---

## 6. Easier Maintenance

If a common transformation needs to change, it can be updated centrally rather than modifying the same transformation logic in multiple reports.

---

# 31. Data Flow as a Central Data Preparation Layer

A useful way to understand the role of a Data Flow is:

> **Data Flow acts as a centralized data preparation/transformation layer between the source system and reporting solutions.**

In this project:

```text
SQL Server
    ↓
Data Flow
    ↓
Cleaned/Transformed Data
    ↓
Power BI Desktop
```

This is especially useful when multiple reports or analysts need similar prepared data.

---

# 32. Important Note About Gen1 and Gen2

The lecture specifically uses **Data Flow Gen1**.

Although Power BI may recommend **Gen2** because of its newer and improved capabilities, the project remains on Gen1 for demonstration purposes.

So for following this particular course:

> **Use Data Flow Gen1.**

---

# 33. Complete Process — End-to-End

The entire process covered so far in the project is:

```text
Excel File
     ↓
SQL Server
     ↓
Create loan Database
     ↓
Import Loan Default Data
     ↓
dbo.loan_default Table
     ↓
Configure On-premises Gateway DF1
     ↓
Power BI Workspace
     ↓
New Item
     ↓
Data Flow Gen1
     ↓
Add New Tables
     ↓
SQL Server
     ↓
Server Name
     ↓
Database = loan
     ↓
Gateway = DF1
     ↓
Windows Authentication
     ↓
Username + Password
     ↓
Connect
     ↓
Select loan_default
     ↓
Transform Data
     ↓
Power Query Online
     ↓
Save and Close
     ↓
Name Data Flow
     ↓
Save
     ↓
Manual Refresh
     ↓
Check Refresh History
     ↓
Refresh Completed
```

---

# 34. Connection Details Used in This Session

| Configuration        | Value/Action                   |
| -------------------- | ------------------------------ |
| Workspace            | Data Flow                      |
| Data Flow Type       | Gen1                           |
| Source               | Microsoft SQL Server           |
| Database             | `loan`                         |
| Table                | `loan_default`                 |
| Gateway              | On-premises Data Gateway `DF1` |
| Authentication       | Windows Authentication         |
| Username             | Obtained using `who am i`      |
| Password             | Windows password               |
| Privacy Level        | None                           |
| Transformation Tool  | Power Query Online             |
| Data Flow Name       | `dataflow SQL`                 |
| Refresh              | Manual                         |
| Refresh Verification | Refresh History                |

---

# 35. Important Commands/Actions to Remember

### Find Windows username

Open Command Prompt and run:

```cmd
who am i
```

Copy the required username information and use it in the Power BI connection configuration.

### SQL Server table

The table being consumed is:

```text
dbo.loan_default
```

### Database

```text
loan
```

---

# 36. Interview Questions

### Q1. What is a Power BI Data Flow?

A Data Flow is a cloud-based data preparation/transformation process that allows organizations to centrally ingest, clean, and transform data so that it can be reused by downstream reporting and analytics solutions.

---

### Q2. Why would you use a Data Flow?

A Data Flow is useful when multiple analysts or reports need the same cleaned and transformed data.

Instead of every analyst independently extracting and transforming the data, the transformations can be performed centrally and the prepared data can be reused.

---

### Q3. What problem does a Data Flow solve?

It reduces:

* Repeated data-cleaning work
* Duplicate transformation logic
* Maintenance effort
* Potential inconsistencies between reports

---

### Q4. What is the difference between Power Query in Desktop and Power Query Online?

Both provide data transformation capabilities, but:

* **Power Query Editor in Power BI Desktop** → transformations are typically associated with the specific Desktop report/model.
* **Power Query Online in Data Flows** → transformations are performed in the cloud-based Data Flow and can provide a reusable centralized data-preparation layer.

---

### Q5. Why is a gateway required in this project?

The source SQL Server is running in an on-premises/local environment. The Power BI Service uses the **On-premises Data Gateway** to communicate with that SQL Server.

---

### Q6. Which gateway was used?

The previously configured:

> **DF1 On-premises Data Gateway**

---

### Q7. Which authentication method was used?

> **Windows Authentication**

---

### Q8. How did the instructor find the Windows username?

By opening Command Prompt and executing:

```cmd
who am i
```

---

### Q9. Which Data Flow generation was used?

> **Data Flow Gen1**

Although Gen2 may be recommended, Gen1 is used for this particular project.

---

### Q10. How can you manually refresh a Data Flow?

Go to:

**Workspace → Data Flow → Refresh**

and start the refresh manually.

---

### Q11. How can you check whether a Data Flow refresh was successful?

Open:

**Data Flow → Refresh History**

and check the refresh status.

The status can initially be **In Progress** and later become **Completed**.

---

# 37. Key Takeaways

* A **Data Flow** provides a centralized location for data preparation.
* This project uses **Data Flow Gen1**.
* SQL Server is used as the source.
* The SQL Server database is `loan`.
* The source table is `dbo.loan_default`.
* The **DF1 On-premises Data Gateway** provides connectivity between Power BI Service and the local SQL Server.
* **Windows Authentication** is used.
* The Windows username can be obtained using `who am i`.
* Data transformations can be performed using **Power Query Online**.
* The Data Flow is saved with an appropriate name and optional description.
* Data Flows can be manually refreshed.
* **Refresh History** can be used to monitor refresh status.
* The major advantage of a Data Flow is **centralized, reusable data preparation**, especially when multiple analysts need the same cleaned/transformed data.

### Current Project Architecture

**Excel → SQL Server → Data Flow Gen1 → Power BI Desktop**

The next step is to **bring the data from this Data Flow into Power BI Desktop** and use the Data Flow as the source for the Power BI report.
