# Connecting Power BI Desktop to Azure SQL Database — Detailed Notes

## 1. Objective of the Session

This session explains how to **establish a connection between Power BI Desktop and an Azure SQL Database**.

In the previous session, basic **data-cleaning operations using Azure SQL** were performed. Now the cleaned data will be brought into Power BI Desktop. The overall goal is to eventually use this data to create a Power BI report.

The workflow demonstrated is:

```text
Azure SQL Database
        ↓
Power BI Desktop
        ↓
Get Data
        ↓
Azure SQL Database Connector
        ↓
Provide Server Details
        ↓
Select Connectivity Mode
        ↓
Database Authentication
        ↓
Select Database/Table
        ↓
Load
        ↓
Data Available in Power BI
```

---

# 2. Open Power BI Desktop

The instructor starts by opening **Power BI Desktop**.

### Steps

1. Go to the **Home** tab.
2. Click the **Power BI Desktop** icon.
3. Wait for Power BI Desktop to open.
4. Click **Blank Report**.

The application may take some time to open. 

---

# 3. Check Data Source Settings

Before establishing the new connection, the instructor checks whether there are any existing data-source permissions/settings saved in Power BI.

### Steps

1. In Power BI Desktop, go to the appropriate menu.
2. Click **Transform Data**.
3. Select **Data source settings**.
4. Check whether any previously saved data-source permissions are available.
5. In the demonstration, there are **no permissions saved on the computer**.
6. Close the Data Source Settings window.

### Why this is done

The instructor is checking whether there are existing credentials/permissions associated with the data source before creating the connection.

---

# 4. Open Get Data

After closing Data Source Settings:

1. Go to the **Home** tab.
2. Click **Get Data**.
3. Select **More**.

This opens the list of available data connectors.

---

# 5. Search for Azure SQL Database

The instructor uses the search functionality to quickly find the required connector.

### Steps

1. In the **Get Data** window, locate the search box.
2. Type:

```text
Azure
```

3. At the top of the results, locate:

**Azure SQL database**
4. Select it.
5. Click **Connect**.

This is the connector used to connect Power BI Desktop to the Azure SQL Database.

---

# 6. Provide the Azure SQL Server Details

After selecting the Azure SQL Database connector, Power BI asks for the **server details**.

The instructor returns to the Azure account to obtain the server name.

### Steps

1. Open the Azure account.
2. Open the previously created Azure SQL Server/database resource.
3. The instructor navigates to:

```text
Test Server Power BI / Test
```

4. Locate the **Server Name**.
5. Copy the server name.

The server name is the same Azure SQL Server that was created in the earlier session.

---

# 7. Enter the Server Name in Power BI

Return to Power BI Desktop.

In the Azure SQL Database connection window:

1. Paste the copied **server name** into the **Server** field.
2. Leave the connectivity mode as **Import**.

The instructor specifically chooses Import mode for this demonstration.

---

# 8. Import vs DirectQuery

An important concept discussed in this session is the **connectivity mode**.

For Azure SQL Database, Power BI supports two connectivity modes:

1. **Import**
2. **DirectQuery**

However, the instructor points out that Power BI does **not provide both connectivity modes for every possible data source**. The available modes depend on the particular connector/data source.

For Azure SQL Database, both **Import** and **DirectQuery** are available.

---

# 9. Import Connectivity Mode

The instructor chooses:

**Import**

### What the instructor explains

The reason for choosing Import is that the instructor wants a **copy of the data to be created in Power BI Desktop**.

Conceptually:

```text id="s0hrf6"
Azure SQL Database
        │
        │ Import
        ▼
Copy of data
inside Power BI Desktop
```

Therefore, Power BI imports the data into its model rather than querying the Azure SQL Database directly every time the report needs data.

---

# 10. DirectQuery Connectivity Mode

The other available option is:

**DirectQuery**

The lecture mentions DirectQuery as another connectivity mode supported by Azure SQL Database, but the instructor **does not use it in this session**.

For this demonstration, the selected mode is:

**Import**

---

# 11. Click OK

After:

* Entering the server name
* Selecting **Import**

the instructor clicks:

**OK**

Power BI then proceeds to the authentication/database selection stage.

---

# 12. Choose the Authentication Method

After clicking OK, Power BI presents multiple options for connecting/authenticating.

The instructor chooses the:

**Database** option.

The instructor explicitly says that another method using a **Microsoft Account** will be discussed in the **next session**.

Therefore, this session focuses specifically on connecting using **database credentials**.

---

# 13. Database Authentication Credentials

The database credentials were created earlier while setting up the Azure SQL Server.

During the Azure SQL Server creation, the instructor had configured:

* SQL Authentication
* Login ID
* Password

The same credentials are now used in Power BI.

### Steps

1. Select the **Database** authentication option.
2. Enter the login ID created earlier.
3. Enter the corresponding password.
4. Make sure you are using the same credentials configured for the Azure SQL Server.
5. Click **Connect**.

The instructor emphasizes that the credentials are the same ones created while configuring the Microsoft/Azure SQL Server.

---

# 14. Select the Database

After successful authentication, Power BI displays the available databases.

The instructor locates:

```text
Test Database
```

This is the database that was created in the earlier Azure SQL Database setup.

### Steps

1. Expand the available database list.
2. Locate **Test Database**.
3. Expand it.
4. Locate the table containing the imported men's T-shirt data.

---

# 15. Select the Table

The imported table is now visible under the database.

The instructor selects the required table because this is the data that needs to be loaded into Power BI.

The objective is:

```text
Test Database
      ↓
Men's T-shirt table
      ↓
Power BI Desktop
```

---

# 16. Load the Data

Once the required table is selected:

1. Select the table.
2. Click **Load**.

Power BI starts importing the data into the Power BI data model.

The instructor mentions that **loading the data into the model may take some time**, so you need to wait for the process to complete.

---

# 17. Data Successfully Loaded into Power BI

After the loading process finishes, the columns become visible on the **right-hand side** of Power BI Desktop.

The instructor confirms that the data is now available in Power BI.

---

# 18. View the Data in Table View

To actually inspect the imported data:

1. Look at the **left navigation pane** in Power BI Desktop.
2. Click the **Table view** icon.
3. The imported table/data is displayed.

The instructor uses Table view to verify what was loaded.

---

# 19. Verify the Columns

The instructor observes that the dataset contains **four columns**.

The two important price columns are:

* **Original Price**
* **Sales Price**

These were the columns that were cleaned in the previous session.

The instructor can now see the cleaned/relatively cleaner data in Power BI.

---

# 20. Connection Between Previous and Current Sessions

This session directly builds on the previous data-cleaning session.

### Previous session

The data was cleaned using Azure SQL:

```text
Original Price
       ↓
Question marks removed

Sales Price
       ↓
Question marks removed
```

### Current session

The cleaned data is brought into Power BI:

```text
Azure SQL Database
       ↓
Power BI Desktop
       ↓
Imported cleaned data
```

Therefore, the data that appears in Power BI is comparatively cleaner than the original imported data.

---

# 21. Future Data Cleaning in Power BI

Although some basic cleaning was already performed using Azure SQL, the instructor says that more detailed discussion of:

* **Data cleaning**
* **Power Query Editor**

will take place in upcoming sessions as part of the project/course.

So, the current session is primarily about **connecting Azure SQL Database to Power BI and loading the data**.

---

# 22. Important Concept — Credentials

There are credentials created during Azure SQL Server setup.

These credentials are reused while establishing the database connection in Power BI.

The basic flow is:

```text
Azure SQL Server Setup
        ↓
Create Login ID + Password
        ↓
Use same credentials
        ↓
Power BI Azure SQL connection
        ↓
Authenticate
        ↓
Access Database
```

It is therefore important to remember the login credentials created during the Azure SQL Server setup.

---

# 23. Complete Step-by-Step Procedure

If you need to reproduce the demonstration yourself, follow these steps:

### Step 1 — Open Power BI

1. Open **Power BI Desktop**.
2. Click **Blank Report**.

### Step 2 — Check Data Source Settings

3. Go to **Transform Data**.
4. Click **Data source settings**.
5. Check whether saved permissions exist.
6. If there are no saved permissions, close the window.

### Step 3 — Select Azure SQL Database

7. Go to **Home**.
8. Click **Get Data**.
9. Click **More**.
10. Search for **Azure**.
11. Select **Azure SQL database**.
12. Click **Connect**.

### Step 4 — Enter Server Details

13. Open Azure.
14. Navigate to the previously created SQL Server/database.
15. Locate the **Server Name**.
16. Copy the server name.
17. Return to Power BI.
18. Paste the server name into the Server field.

### Step 5 — Select Connectivity Mode

19. Select **Import**.
20. Click **OK**.

### Step 6 — Authenticate

21. Select the **Database** authentication option.
22. Enter the SQL Server login ID.
23. Enter the password created during Azure SQL Server setup.
24. Click **Connect**.

### Step 7 — Select Database and Table

25. Expand **Test Database**.
26. Locate the required men's T-shirt table.
27. Select the table.
28. Click **Load**.

### Step 8 — Verify

29. Wait for Power BI to finish loading the data.
30. Check the fields/columns on the right-hand side.
31. Click **Table view** from the left navigation pane.
32. Inspect the imported data.
33. Verify the cleaned **Original Price** and **Sales Price** columns.

---

# 24. Import Mode vs DirectQuery — Quick Comparison

| Feature                         | Import                                        | DirectQuery                 |
| ------------------------------- | --------------------------------------------- | --------------------------- |
| Used in this lecture            | **Yes**                                       | No                          |
| Data copied into Power BI model | **Yes**                                       | No                          |
| Azure SQL Database supported    | Yes                                           | Yes                         |
| Main approach demonstrated      | **Import data into Power BI**                 | Not demonstrated            |
| Purpose in this session         | Create a copy of the data in Power BI Desktop | Mentioned as an alternative |

The instructor specifically selects **Import** because the goal is to create a copy of the data inside Power BI Desktop.

---

# 25. Important Points to Remember

### Azure SQL connector

Use:

**Get Data → More → Search Azure → Azure SQL Database → Connect**

### Server name

The server name must be obtained from the Azure SQL Server resource created previously.

### Connectivity mode

For this lecture:

**Import** is selected.

### Authentication

For this lecture:

**Database** authentication is selected.

### Credentials

Use the **same SQL login ID and password created during Azure SQL Server setup**.

### Database

The demonstration uses:

**Test Database**

### Data

The imported table contains the **men's T-shirt data**.

### Verification

Use:

**Table View**

to inspect the loaded data.

---

# 26. What Is Not Covered in This Session?

The instructor explicitly indicates that some topics will be covered later.

### Microsoft Account connection

The instructor mentions that connecting using a **Microsoft Account** will be demonstrated in the **next session**.

So don't confuse the two methods:

```text
Current Session:
Power BI → Azure SQL → Database Authentication

Next Session:
Power BI → Azure SQL → Microsoft Account
```

### Detailed Power Query/Data Cleaning

More detailed data-cleaning operations and the **Power Query Editor in Power BI Desktop** will also be covered in upcoming sessions.

---

# 27. Final Workflow for the Project

The project workflow at this point is:

```text
                 DATA FILE
                    │
                    ▼
             SQL Server / SSMS
                    │
                    ▼
            Azure SQL Database
                    │
                    │
          Basic Data Cleaning
                    │
                    ▼
          Cleaned Azure SQL Data
                    │
                    ▼
              Power BI Desktop
                    │
             ┌──────┴──────┐
             │             │
          Import       DirectQuery
             │
             ▼
      Power BI Data Model
             │
             ▼
       Table / Data View
             │
             ▼
    Further Data Cleaning
    + Power Query Editor
             │
             ▼
        Power BI Report
```

---

## 28. Session Summary

The main objective of this lecture is to **connect Power BI Desktop with Azure SQL Database and load the required table into Power BI**.

The key sequence to memorize is:

> **Power BI Desktop → Get Data → More → Azure SQL Database → Connect → Enter Server Name → Select Import → OK → Database Authentication → Enter Login & Password → Connect → Select Test Database → Select Table → Load → Table View**

The instructor confirms that the previously cleaned **Original Price** and **Sales Price** data is now available in Power BI. The next session will demonstrate the **Microsoft Account connection method**, while further sessions will cover **Power Query/data cleaning and report creation**.
