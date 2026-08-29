# Azure SQL Database — Creating the Database and Loading Data

## 1. Objective of the Session

The session focuses on **creating an Azure SQL Database** and loading data into it.

For the project, **Azure SQL Database will be used as the data source**. The overall workflow discussed in the lecture is:

**Load data into Microsoft Azure → Connect Azure SQL Database to Power BI → Bring data into Power BI → Create a Power BI report**

The instructor explains that in a real-time project, the data may already be available in Azure. However, for this project, it is important to understand the **complete data-loading process**, so the lecture starts by demonstrating how to load the data into Microsoft Azure. 

The instructor also assumes that the learner has already gone through the previous lecture about **creating a free Azure account**. 

---

# 2. Overall Workflow

The complete process covered in this lecture is:

```text
Azure Portal
     ↓
SQL Databases
     ↓
Create Azure SQL Database
     ↓
Apply Free Azure SQL Database Offer
     ↓
Create Resource Group
     ↓
Create Database
     ↓
Create SQL Server
     ↓
Configure SQL Authentication
     ↓
Create Server Login & Password
     ↓
Review + Create
     ↓
Wait for Deployment
     ↓
Go to Resource
     ↓
Configure Server Firewall
     ↓
Allow Client IPv4 Address
     ↓
Open SQL Server Management Studio (SSMS)
     ↓
Connect to Azure SQL Server
     ↓
Import Flat File
     ↓
Load CSV Data into Azure SQL Database
     ↓
Verify Data Using SQL Query
     ↓
Check Data in Azure Query Editor
     ↓
Next: Clean Data + Connect to Power BI
```

---

# 3. Open SQL Databases in Azure

After logging into the Azure account:

1. Go to **Azure Services**.
2. Locate **SQL databases**.
3. Click **SQL databases**.
4. Click **Create SQL database**.

This opens the configuration page where the required database details need to be provided. 

---

# 4. Apply the Free Azure SQL Database Offer

While creating the database, Azure provides an offer for trying **Azure SQL Database for free**.

### Steps

1. Locate the available offer.
2. If you want to use the free offer, select it.
3. Click **Apply Offer**.
4. Continue down the configuration page.

The instructor specifically applies the available free offer before continuing with the database configuration. 

---

# 5. Create a Resource Group

The next requirement is a **Resource Group**.

A resource group is used to organize Azure resources associated with the project.

### Steps

1. Locate the **Resource Group** field.
2. Select **Create New**.
3. Enter a suitable name.

The instructor uses:

```text
power BI
```

4. Check whether the name is available.
5. Once Azure confirms that the name is available, click **OK**.

The instructor then continues with the database configuration. 

### Important

The exact name doesn't have to be `power BI`. You can provide an appropriate name for your own project, as long as Azure accepts it.

---

# 6. Create the Azure SQL Database

After creating the resource group, provide a name for the database.

The instructor chooses:

```text
test database
```

Azure checks whether the database name is available.

In the demonstration, the name is available. 

### Steps

1. Locate the **Database Name** field.
2. Enter a suitable database name.
3. Check availability.
4. Continue once the name is accepted.

---

# 7. Create the SQL Server

An Azure SQL Database requires a SQL Server.

The instructor creates a new server.

### Steps

1. Locate the **Server** section.
2. Click **Create New**.
3. Enter a suitable server name.

The instructor initially tries:

```text
test server
```

However, Azure reports that the specified server name is already in use. 

So the instructor changes the name to something similar to:

```text
test server power BI
```

Azure then confirms that the new server name is available. 

### Important Point

The server name must be **unique/available**. If Azure reports that the name is already in use, choose another name.

---

# 8. Select Server Location

The instructor keeps the server location as:

```text
US East
```

The location is selected while configuring the SQL Server. 

For your own project, the available region can depend on your requirements and Azure configuration.

---

# 9. Select SQL Authentication

Next, configure the authentication method.

The instructor selects:

**SQL Authentication**

This means the SQL Server can be accessed using a SQL Server login and password. 

---

# 10. Create the Server Administrator Login

After selecting SQL Authentication, provide the server administrator credentials.

The instructor creates a server admin login similar to:

```text
insidebi
```

Then a password is entered.

The password needs to be entered again for confirmation. 

### Steps

1. Select **SQL Authentication**.
2. Enter the **Server Admin Login**.
3. Enter a suitable password.
4. Re-enter the password for confirmation.
5. Remember these credentials.

### Important

These credentials will be needed later when connecting to the Azure SQL Server through **SQL Server Management Studio (SSMS)** and the Azure Query Editor.

---

# 11. Review and Create the Database

After entering all required configuration information:

1. Click **OK** where required for the server configuration.
2. Click **Review + Create**.
3. Azure validates the configuration.
4. Click **Create**.

The deployment process then begins. 

---

# 12. Wait for Azure Deployment

After clicking **Create**, Azure begins deploying the SQL Database.

The instructor notes that:

* The configuration is being validated.
* Deployment is initialized.
* The process can take some time.
* The learner may fast-forward this portion of the lecture.

The deployment status remains **in progress** until Azure finishes creating the resources. 

Eventually, the instructor receives the message that:

**Deployment is complete.**

---

# 13. Go to the Azure SQL Database Resource

Once deployment is completed:

1. Click **Go to resource**.
2. Close the notifications if necessary.

You will now be able to see the Azure SQL Database resource and its configuration options. 

---

# 14. Configure the Server Firewall

One important configuration step is the **server firewall**.

The instructor explains that firewall settings may otherwise cause errors when trying to load data from Microsoft SQL Server/SSMS into Azure SQL Database. 

### Steps

1. Locate the **Set server firewall** option.
2. Open the firewall configuration.
3. Select **Selected networks**.
4. Locate the option to add the client IP address.
5. Click:

**Add your client IPv4 address**

6. Click **Save**.

This allows the client machine's IPv4 address to connect to the Azure SQL Server. 

---

# 15. Verify the Firewall Update

After saving the firewall configuration:

1. Azure updates the server firewall rules.
2. Open the notifications area if necessary.
3. Verify that the firewall rules were successfully updated.
4. Click **Go to resource**.

The instructor confirms that the server firewall rules were successfully updated. 

---

# 16. Why SQL Server Management Studio (SSMS) Is Used

The next part involves loading data into the Azure SQL Database.

The instructor uses:

**SQL Server Management Studio (SSMS)**

The instructor explains that if you don't know how to download and install Microsoft SQL Server/SSMS, you should refer to an earlier project/lecture where the installation process was discussed.

SSMS is required in this workflow because it will be used to **load the data into Microsoft Azure SQL Database**. 

### Workflow

```text
CSV / Flat File
      ↓
SSMS
      ↓
Azure SQL Database
```

---

# 17. Open SQL Server Management Studio

The instructor now opens **SSMS**.

### Steps

1. Open SQL Server Management Studio.
2. Wait for it to launch.
3. In **Object Explorer**, click **Connect**.
4. Select **Database Engine**.

The connection dialog then appears. 

---

# 18. Enter Azure SQL Server Connection Details

You now need to provide the server details created earlier in Azure.

### Server Name

Go back to the Azure SQL Server details and copy the **server name**.

Then return to SSMS and enter that server name in the connection dialog. 

### Authentication

Select:

**SQL Server Authentication**

Then provide:

* Login
* Password

The login is the server administrator login created earlier during Azure SQL Server setup.

The instructor uses the login created earlier and enters its corresponding password. 

### Finally

Click:

**Connect**

---

# 19. Handling a Connection Error

During the first connection attempt, the instructor receives:

> **A transport-level error has occurred while receiving the results from the server.**

The instructor does not change the configuration immediately.

Instead:

1. Try to connect again.
2. Click **Connect → Database Engine**.
3. Enter the same server details.
4. Select **SQL Server Authentication**.
5. Enter the login.
6. Enter the password.
7. Click **Connect** again.

On the second attempt, the connection is successfully established. 

### Key Takeaway

A temporary connection error may occur while establishing the Azure SQL connection. The instructor resolves it simply by trying the connection again.

---

# 20. Locate the Azure SQL Database in SSMS

Once connected:

1. Expand **Databases** in Object Explorer.
2. Locate the database created earlier.

The instructor finds the database:

```text
test database
```

This confirms that the Azure SQL Database is accessible through SSMS. 

---

# 21. Import the Flat File

The next objective is to load the project data into the Azure SQL Database.

The instructor uses a **flat file** provided in the lecture's resource section.

### Steps

1. Locate your Azure SQL Database in SSMS.
2. Right-click the database.
3. Select **Tasks**.
4. Under Tasks, select:

**Import Flat File**

This launches the import process. 

---

# 22. Select the Data File

The instructor mentions that the flat file will be provided in the **resource section**.

You need to download/use that file.

The dataset contains information related to:

**Men's T-shirts**

### Steps

1. In the Import Flat File wizard, click **Next**.
2. Browse to the location of the flat file.
3. Select the provided data file.
4. Click **Next**.

The instructor selects the dataset file and continues. 

---

# 23. Review the Dataset Columns

The imported dataset contains multiple columns.

The instructor specifically observes two columns containing monetary information:

* **Original Price**
* **Sales Price**

These values represent amounts in **Indian Rupees (INR)**. 

---

# 24. Check Detected Data Types

The Import Flat File wizard automatically detects data types for the different columns.

The instructor proceeds to the data-type configuration screen.

Azure/SSMS automatically detects the data types of the various columns. 

---

# 25. Change Original Price and Sales Price to Text

The instructor makes a specific modification to the data types.

For now:

* **Original Price → Text**
* **Sales Price → Text**

### Steps

1. Locate the **Original Price** column.
2. Change its data type to **Text**.
3. Locate the **Sales Price** column.
4. Change its data type to **Text**.
5. Allow **NULL values** where applicable.
6. Click **Next**.
7. Click **Finish**.



### Why?

The instructor later notes that this results in question marks appearing in those columns, because they have temporarily been stored as text.

The data will be cleaned later.

---

# 26. Complete Data Insertion

After clicking **Finish**, the import process runs.

The instructor confirms:

**Data insertion was complete.**

Then the import window is closed. 

---

# 27. Verify the Imported Table

To check whether the data was successfully imported:

1. Expand the Azure SQL database.
2. Click the **+** icon next to the database.
3. Locate **Tables**.
4. Expand **Tables**.
5. Locate the newly imported table.

The instructor waits briefly while the database and tables load. 

---

# 28. Verify the Data Using a SQL Query

The instructor then verifies the imported data using a SQL query.

### Steps

1. Click **New Query**.
2. Enter a SELECT query.

The instructor uses a query equivalent to:

```sql
SELECT TOP 1 *
FROM dbo.[men t shirt];
```

The purpose is to retrieve one row from the imported table and verify that the data exists. 

After executing the query, the imported data appears in the results.

---

# 29. Observe the Price Columns

While checking the query result, the instructor notices that the:

* Original Price
* Sales Price

columns contain **question marks**.

This happens because the instructor changed their data type to **Text** during the import process. 

The instructor does not attempt to fix this immediately.

Instead, it is explicitly mentioned that:

**The data will be cleaned later in Microsoft Azure.**

So, at this stage, the important objective is simply to ensure that the data has been successfully loaded into the database. 

---

# 30. Open the Microsoft Azure Account

After verifying the data through SSMS, the instructor returns to the **Microsoft Azure account**.

The Azure SQL Database resource is opened again. 

---

# 31. Use Azure Query Editor

Azure provides a **Query Editor** that can be used to access the database directly from the Azure Portal.

### Steps

1. In the Azure SQL Database resource, look at the left-hand menu.
2. Click **Query Editor**.
3. Azure asks for credentials.
4. Provide the SQL Server credentials created earlier.

The login is already populated in the instructor's example. 

---

# 32. Enter the Password

The password required here is the same password that was created while setting up the Microsoft SQL Server/Azure SQL Server.

### Steps

1. Enter the server password.
2. Click **OK**.

The instructor emphasizes that these are the **same credentials used while creating the Azure resource**. 

---

# 33. View the Table in Query Editor

After successfully logging into Query Editor:

1. Expand **Tables**.
2. Locate the imported men's T-shirt data table.
3. Expand the table.
4. You can see the columns belonging to the table.

The columns displayed correspond to the columns previously observed in SSMS. 

---

# 34. Select Top 1000 Rows

Azure Query Editor provides an option to quickly retrieve rows from a table.

### Steps

1. Locate the imported table.
2. Click the **three dots (`...`)** next to the table.
3. Select:

**Select top 1000 rows**

The query is then executed. 

The data appears in the query results.

The instructor points out that the columns can be seen on the right-hand side.

---

# 35. Confirm That Data Is Available in Azure SQL Database

At this point, the instructor confirms that the data is successfully available inside the **SQL Database in Microsoft Azure**. 

So the data-loading portion is complete.

---

# 36. What Happens Next?

The instructor explains that the next stages will be:

### Stage 1 — Data Cleaning

The imported data needs to be cleaned in Microsoft Azure.

For example, the price columns need to be addressed because of the temporary text-type configuration and the resulting question marks.

### Stage 2 — Connect Azure SQL Database to Power BI

The Azure SQL Database will then be connected to **Power BI Desktop**.

### Stage 3 — Bring Data into Power BI

The cleaned data will be imported/accessed in Power BI.

### Stage 4 — Create Power BI Report

Finally, a report will be created in Power BI using the Azure SQL Database data. 

---

# 37. CSV/Flat File Provided in Resource Section

The instructor states that the **CSV/flat file** used in the project will be provided in the resource section.

You can use that file to follow along with the lecture. 

The instructor's demonstrated dataset is related to **men's T-shirts**.

---

# 38. Real-Time Project Scenario

The instructor distinguishes between the demonstration/project setup and a real-world scenario.

### In this project

You are learning the entire process:

```text
File
 ↓
SSMS
 ↓
Azure SQL Database
 ↓
Power BI
```

This is done so that you understand **how data is loaded into Azure**.

### In a real-time project

You would generally already have:

* Data available in the Azure SQL Database
* Appropriate credentials provided to you

Therefore, you may not personally perform the initial data-loading step.

The instructor nevertheless covers it because understanding the data-loading process is important from a project perspective. 

---

# 39. Important Credentials to Keep Track Of

During the process, the same SQL Server credentials are used in multiple places.

### Credentials created during Azure SQL Server setup

You create:

```text
Server Admin Login
+
Password
```

These are subsequently used for:

**SSMS connection**

and

**Azure Query Editor**

So, remember the credentials created during the SQL Server setup.  

---

# 40. Key Concepts Covered

| Concept             | Purpose                                                            |
| ------------------- | ------------------------------------------------------------------ |
| Azure SQL Database  | Cloud-based SQL database used as the project's data source         |
| Resource Group      | Organizes Azure resources                                          |
| SQL Server          | Server associated with the Azure SQL Database                      |
| SQL Authentication  | Allows login using SQL username/password                           |
| Server Admin Login  | Administrator credential for the SQL Server                        |
| Firewall Rules      | Controls which client/network connections can access the server    |
| Client IPv4 Address | Added to firewall to allow the current machine to connect          |
| SSMS                | Used to connect to Azure SQL Server and import the data            |
| Import Flat File    | Used to load the CSV/flat-file dataset into the database           |
| Query               | Used to verify the imported data                                   |
| Azure Query Editor  | Used to access and query the database directly from Azure          |
| Power BI            | Will later connect to the Azure SQL Database and create the report |

---

# 41. Important Troubleshooting Points

### Problem 1: Server name already in use

If Azure says:

**Specified server name is already in use**

### Solution

Choose another server name and check availability again.

The instructor changes the server name and successfully creates it. 

---

### Problem 2: Firewall error

When connecting/loading data, a firewall error can occur.

### Solution

Go to the server firewall settings:

```text
Server Firewall
      ↓
Selected Networks
      ↓
Add your client IPv4 address
      ↓
Save
```

Then verify that the firewall rules were successfully updated. 

---

### Problem 3: Transport-level connection error

During the first SSMS connection attempt, the instructor encounters a transport-level error.

### Solution demonstrated

Try establishing the connection again with the same:

* Server name
* Authentication method
* Login
* Password

The second attempt succeeds. 

---

### Problem 4: Question marks in price columns

After importing the data, the **Original Price** and **Sales Price** columns show question marks.

### Reason in the lecture

The instructor changed these columns to **Text** during the import process.

### Planned solution

The instructor states that the data will be **cleaned later in Microsoft Azure**. 

---

# 42. Complete Practical Procedure

If you need to perform the entire lecture yourself, follow this sequence:

### Part A — Create Azure SQL Database

1. Log into Azure.
2. Open **SQL databases**.
3. Click **Create SQL database**.
4. Apply the free SQL Database offer.
5. Create a new **Resource Group**.
6. Give the resource group a suitable name.
7. Provide a database name.
8. Create a new SQL Server.
9. Choose an available server name.
10. Select the server location.
11. Select **SQL Authentication**.
12. Create the server admin login.
13. Create and confirm the password.
14. Click **Review + Create**.
15. Click **Create**.
16. Wait for deployment.
17. Click **Go to resource**.

### Part B — Configure Firewall

18. Open **Set server firewall**.
19. Select **Selected networks**.
20. Click **Add your client IPv4 address**.
21. Click **Save**.
22. Confirm that the firewall rules were successfully updated.

### Part C — Connect Using SSMS

23. Open **SQL Server Management Studio**.
24. Click **Connect**.
25. Select **Database Engine**.
26. Copy the Azure SQL Server name.
27. Enter the server name in SSMS.
28. Select **SQL Server Authentication**.
29. Enter the server admin login.
30. Enter the password.
31. Click **Connect**.
32. If a temporary transport-level error occurs, try connecting again.

### Part D — Import the Dataset

33. Expand **Databases**.
34. Locate your Azure SQL Database.
35. Right-click the database.
36. Select **Tasks**.
37. Select **Import Flat File**.
38. Click **Next**.
39. Browse to the provided CSV/flat file.
40. Select the file.
41. Click **Next**.
42. Review the detected columns/data types.
43. Change **Original Price** to Text.
44. Change **Sales Price** to Text.
45. Allow NULL values where applicable.
46. Click **Next**.
47. Click **Finish**.
48. Wait for data insertion to complete.

### Part E — Verify Through SSMS

49. Expand the database.
50. Expand **Tables**.
51. Locate the imported table.
52. Click **New Query**.
53. Run a SELECT query such as:

```sql
SELECT TOP 1 *
FROM dbo.[men t shirt];
```

54. Execute the query.
55. Verify that the imported data is displayed.

### Part F — Verify Through Azure Query Editor

56. Return to Azure.
57. Open **Query Editor**.
58. Enter the SQL credentials.
59. Click **OK**.
60. Expand **Tables**.
61. Locate the imported table.
62. Click the **three dots (`...`)**.
63. Select **Select top 1000 rows**.
64. Verify that the data is displayed.

---

# 43. Final Architecture From This Lecture

The key architecture introduced in this session is:

```text
             CSV / Flat File
                    │
                    ▼
          SQL Server Management
             Studio (SSMS)
                    │
                    │ Import Flat File
                    ▼
          ┌─────────────────────┐
          │   Azure SQL Server  │
          │         +           │
          │    SQL Database     │
          └─────────────────────┘
                    │
                    │
                    ▼
              Power BI Desktop
                    │
                    ▼
              Power BI Report
```

The lecture has therefore completed the **Azure SQL database creation and data-loading stage**. The upcoming work is to **clean the data, connect Azure SQL Database to Power BI, bring the data into Power BI, and build the report**. 
