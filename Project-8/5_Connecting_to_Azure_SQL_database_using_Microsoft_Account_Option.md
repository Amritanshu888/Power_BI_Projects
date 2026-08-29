# Connecting Power BI to Azure SQL Database Using Microsoft Account

## 1. Objective of the Session

This session continues the discussion on establishing a connection between **Power BI Desktop and Azure SQL Database**.

In the previous session, the connection was established using the **Database** authentication option. In this session, the instructor demonstrates the **Microsoft Account** authentication method.

The main objective is therefore:

> **Connect Power BI Desktop to Azure SQL Database using a Microsoft Account.**

The session also demonstrates:

* Clearing previously saved data-source permissions.
* Configuring **Microsoft Entra ID** in Azure.
* Setting a Microsoft Entra administrator for the SQL Server.
* Signing into Power BI using the Microsoft account.
* Handling an authenticator-app verification.
* Loading the Azure SQL data into Power BI.
* Removing a duplicate table.
* Renaming the remaining table.

---

# 2. Connection Methods Discussed

The instructor has now demonstrated two ways of connecting Power BI to Azure SQL Database.

### Method 1 — Database Authentication

Used in the previous session:

```text
Power BI
   ↓
Azure SQL Database
   ↓
Database
   ↓
SQL Login + Password
```

### Method 2 — Microsoft Account Authentication

Used in this session:

```text
Power BI
   ↓
Azure SQL Database
   ↓
Microsoft Account
   ↓
Microsoft Entra ID
   ↓
Authentication
```

The current session focuses on **Method 2**.

---

# 3. Clear Existing Data Source Permissions

Because a connection to this data source has already been established, the instructor first removes the saved permissions.

This is done so that the Microsoft Account authentication method can be demonstrated from the beginning.

### Steps

1. Open **Power BI Desktop**.
2. Go to:

**Transform Data → Data Source Settings**

3. Locate/select the existing data-source setting.
4. Click **Clear Permissions**.
5. Click **Delete** to confirm.

The instructor explains that this is useful in real-world situations when you want to remove credentials/settings saved on a particular computer and **re-establish the connection**. 

### Important Concept

If Power BI has already saved credentials for a particular data source, you can clear those permissions and establish the connection again using another authentication method.

---

# 4. Close Data Source Settings

After deleting the saved permissions:

1. Close the **Data Source Settings** window.
2. Return to Power BI Desktop.

---

# 5. Open Get Data

Now establish the Azure SQL connection again.

### Steps

1. Click **Get Data**.
2. Click **More**.
3. In the search box, type:

```text
Azure SQL Database
```

You can also type only a few characters, such as:

```text
Azure
```

and Power BI will show possible matching connectors.

4. Select **Azure SQL Database**.
5. Click **Connect**.

---

# 6. Copy the Azure SQL Server Name

Power BI now asks for the Azure SQL Server details.

The instructor returns to the Azure Portal to obtain the server name.

### Steps

1. Open the Azure account.
2. Navigate to the SQL Server.
3. Open:

**Test Server Power BI / Test**

4. Locate the **Server Name**.
5. Copy the server name.

---

# 7. Enter Server Details in Power BI

Return to Power BI Desktop.

### Steps

1. Paste the copied server name into the **Server** field.
2. Select **Import** as the connectivity mode.
3. Click **Connect/OK**.

The instructor again chooses **Import mode**, meaning the data will be imported into the Power BI model.

---

# 8. Select Microsoft Account Instead of Database

Power BI then displays the available authentication methods.

In the previous session, the instructor selected:

**Database**

This time, the instructor deliberately chooses:

**Microsoft Account**

### Steps

1. Select **Microsoft Account**.
2. Click **Sign in**.

At this point, the instructor encounters an error.

---

# 9. Error: Tenant Identifier Problem

When attempting to sign in using the Microsoft Account, the instructor receives an error related to the tenant identifier.

The error indicates that the:

**Requested tenant identifier**

is invalid/empty.

The instructor is therefore unable to establish the connection at this point.

Instead of continuing in Power BI, the instructor closes the dialog and modifies the Azure configuration.

---

# 10. Configure Microsoft Entra ID in Azure

To fix the authentication issue, the instructor changes settings in the Azure Portal.

The relevant setting is:

**Microsoft Entra ID**

This needs to be configured for the SQL Server.

---

# 11. Open SQL Servers in Azure

### Steps

1. Open the **Azure Portal**.
2. Click **Home**.
3. Locate the search box.
4. Search for:

```text
SQL servers
```

5. Select **SQL servers**.
6. Select the previously created server:

**Test Server Power BI**

The instructor then opens the server configuration.

---

# 12. Open Microsoft Entra ID Settings

Inside the SQL Server configuration:

1. Look under **Settings**.
2. Locate:

**Microsoft Entra ID**

3. Select **Microsoft Entra ID**.

This is where the Microsoft Entra administrator needs to be configured.

---

# 13. Set the Microsoft Entra Administrator

The instructor now clicks:

**Set Admin**

This allows a Microsoft Entra administrator to be associated with the SQL Server.

### Steps

1. Click **Set Admin**.
2. Select the appropriate user/account.
3. The instructor selects the account associated with:

**Cyber Solutions Private Limited on Microsoft.com**

4. Check/select the account.
5. Click **Select**.

The instructor explains that this is the email/account used for the Azure environment.

---

# 14. Save the Microsoft Entra ID Configuration

After selecting the administrator:

1. Click **Save**.
2. Wait while Azure updates the Microsoft Entra administrator settings.
3. Open the notifications area if required.
4. Verify that the operation was successful.

The instructor confirms that setting the Microsoft Entra administrator was successful.

---

# 15. Retry the Power BI Connection

After configuring Microsoft Entra ID, the instructor returns to Power BI Desktop.

The connection process is started again.

### First, cancel the previous connection dialog

1. Return to Power BI.
2. Cancel the previous connection attempt.

---

# 16. Clear Data Source Permissions Again

The instructor repeats the process of clearing the existing data-source settings.

### Steps

1. Go to:

**Transform Data → Data Source Settings**

2. Select the Azure SQL data-source settings.
3. Click **Clear Permissions**.
4. Click **Delete**.
5. Close the Data Source Settings window.

This ensures that Power BI doesn't automatically reuse the previous authentication credentials.

---

# 17. Open Azure SQL Database Connector Again

Now repeat the connection process.

### Steps

1. Click **Get Data**.
2. Click **More**.
3. Search for:

**Azure SQL Database**

4. Select **Azure SQL Database**.
5. Click **Connect**.

The instructor notes that you can type only a few characters in the search box and Power BI will show matching options.

---

# 18. Copy the Server Name Again

The instructor again opens Azure:

1. Click **Home**.
2. Open the SQL Server/database resource.
3. Navigate to:

**Test Server Power BI / Test**
4. Copy the **Server Name**.

Return to Power BI and paste the server name into the connection dialog.

---

# 19. Select Import Mode

The instructor again chooses:

**Import**

This means that Power BI will import a copy of the data into its data model.

Then:

1. Click **Connect/OK**.
2. Proceed to authentication.

---

# 20. Select Microsoft Account

This time, instead of selecting **Database**:

1. Select **Microsoft Account**.
2. Click **Sign in**.

The Microsoft Account authentication process now proceeds successfully because the Microsoft Entra administrator has been configured.

---

# 21. Select the Microsoft Account

Power BI asks which Microsoft account should be used.

The instructor selects the account:

**Cyber Solutions Private Limited on Microsoft.com**

### Steps

1. Select the appropriate Microsoft account.
2. Enter the account password.
3. Click **Sign in**.

---

# 22. Authenticator App Verification

The instructor has **Microsoft Authenticator** activated on the account.

Because of this, an additional verification step appears.

The instructor explains that:

> In a general case, you may not necessarily receive this particular prompt.

In this demonstration, however, the authenticator app asks for a number.

The instructor receives the number:

```text
19
```

from the mobile phone/authenticator application.

### Steps

1. Check the authenticator app on your phone.
2. Obtain the number displayed there.
3. Enter/select the requested number.
4. Complete the verification.

Once the information is verified, the sign-in process is allowed to continue.

> **Important:** The number shown in the lecture is specific to that demonstration. Your authenticator verification number will be different.

---

# 23. Connect After Authentication

After successful Microsoft Account authentication:

1. Click **Connect**.
2. Wait for Power BI to retrieve the available databases and tables.

The instructor mentions that this may take some time.

---

# 24. Select the Database and Table

After authentication succeeds, Power BI displays the available database.

The instructor sees the previously created database.

### Steps

1. Locate the database.
2. Expand it.
3. Locate the required table.
4. Select the table containing the men's T-shirt data.

The same data that was previously connected using Database authentication is now accessible using the Microsoft Account authentication method.

---

# 25. Load the Data

The instructor wants to load the data directly into Power BI.

### Steps

1. Select the required table.
2. Click **Load**.
3. Wait while Power BI imports the data into the model.

The instructor notes that the data had already been imported previously, but loads this table again for demonstration purposes.

---

# 26. Duplicate Table Is Created

Because the same data had already been loaded into Power BI, loading it again creates another table.

The newly loaded table is named approximately:

**men t shirt 2**

The instructor explains that both tables contain the **same data**.

Conceptually:

```text
Existing Table
    ↓
Men's T-shirt data

Newly Loaded Table
    ↓
Men's T-shirt data
```

Since both are duplicates, one of them should be removed.

---

# 27. Remove the Duplicate Table

The instructor decides to remove the first/original table.

### Steps

1. Locate the first table in the Power BI model.
2. Right-click/select it.
3. Delete it from the model.

The duplicate/newly imported table is retained.

---

# 28. Rename the Remaining Table

After deleting the first table, the instructor renames the remaining table.

### Steps

1. Locate the remaining table.
2. Double-click the table name.
3. Rename it to:

**T Shirt**

The instructor mentions that you can give the table **any suitable name**.

The purpose is simply to have a cleaner and more meaningful table name in the Power BI model.

---

# 29. Final State of the Power BI Model

After removing the duplicate and renaming the remaining table:

```text
Power BI Model
      │
      └── T Shirt
             │
             ├── Column 1
             ├── Column 2
             ├── Original Price
             └── Sales Price
```

The table now contains the same Azure SQL data but has a cleaner name.

---

# 30. Database Authentication vs Microsoft Account

The two methods covered across the sessions can now be compared.

| Feature                                                      | Database Authentication | Microsoft Account            |
| ------------------------------------------------------------ | ----------------------- | ---------------------------- |
| Authentication option                                        | Database                | Microsoft Account            |
| Credentials                                                  | SQL login + password    | Microsoft account            |
| Used in previous session                                     | Yes                     | No                           |
| Used in current session                                      | No                      | **Yes**                      |
| Microsoft Entra configuration required in this demonstration | No                      | **Yes**                      |
| Sign-in process                                              | Database credentials    | Microsoft account sign-in    |
| Additional authenticator verification                        | Not demonstrated        | Occurs in instructor's setup |

---

# 31. Why Clear Permissions Is Important

One of the important practical concepts from this session is **clearing saved permissions**.

Suppose Power BI already has credentials saved for a data source.

If you want to try another authentication method, the old credentials/settings may interfere with the process.

Therefore:

```text
Transform Data
      ↓
Data Source Settings
      ↓
Select Data Source
      ↓
Clear Permissions
      ↓
Delete
      ↓
Close
      ↓
Re-establish Connection
```

The instructor specifically highlights this as something that can happen when working on a real-time project.

---

# 32. Why Microsoft Entra ID Configuration Was Required

Initially, the instructor tried to connect using a Microsoft Account and encountered a **tenant identifier error**.

The solution demonstrated was:

```text
Azure SQL Server
       ↓
Microsoft Entra ID
       ↓
Set Admin
       ↓
Select Microsoft Account/User
       ↓
Save
       ↓
Retry Power BI Connection
```

After this configuration, the Microsoft Account connection could proceed.

---

# 33. Important Troubleshooting Flow

### Problem

Microsoft Account authentication fails with a tenant identifier-related error.

### Steps demonstrated to resolve it

1. Close/cancel the connection attempt.
2. Open Azure Portal.
3. Go to **Home**.
4. Search for **SQL servers**.
5. Open the relevant SQL Server.
6. Go to **Settings → Microsoft Entra ID**.
7. Click **Set Admin**.
8. Select the appropriate Microsoft account/user.
9. Click **Select**.
10. Click **Save**.
11. Wait for the configuration update to complete.
12. Return to Power BI.
13. Clear the existing data-source permissions.
14. Reopen the Azure SQL Database connector.
15. Enter the server name.
16. Select **Import**.
17. Select **Microsoft Account**.
18. Click **Sign in**.
19. Select the appropriate Microsoft account.
20. Enter the password.
21. Complete authenticator verification if prompted.
22. Click **Connect**.
23. Select the database/table.
24. Click **Load**.

---

# 34. Complete Practical Workflow

Here's the entire process in one sequence:

```text
Open Power BI Desktop
        ↓
Transform Data
        ↓
Data Source Settings
        ↓
Clear Permissions
        ↓
Delete
        ↓
Close
        ↓
Get Data
        ↓
More
        ↓
Azure SQL Database
        ↓
Connect
        ↓
Copy Server Name from Azure
        ↓
Paste Server Name
        ↓
Select Import
        ↓
OK / Connect
        ↓
Microsoft Account
        ↓
Sign In
        ↓
Tenant Identifier Error
        ↓
Open Azure
        ↓
Home → SQL Servers
        ↓
Select Test Server Power BI
        ↓
Settings → Microsoft Entra ID
        ↓
Set Admin
        ↓
Select Microsoft Account/User
        ↓
Select
        ↓
Save
        ↓
Return to Power BI
        ↓
Clear Permissions Again
        ↓
Get Data → Azure SQL Database
        ↓
Enter Server Name
        ↓
Import
        ↓
Microsoft Account
        ↓
Sign In
        ↓
Select Account
        ↓
Enter Password
        ↓
Authenticator Verification
        ↓
Connect
        ↓
Select Database
        ↓
Select Table
        ↓
Load
        ↓
Duplicate Table Created
        ↓
Delete Original Table
        ↓
Rename Remaining Table → T Shirt
```

---

# 35. Key Points to Remember

### Power BI connection

**Home → Get Data → More → Azure SQL Database → Connect**

### Server

Get the server name from the Azure SQL Server resource.

### Connectivity mode

The instructor uses:

**Import**

### First authentication method

Previous session:

**Database**

### Authentication method in this session

Current session:

**Microsoft Account**

### Azure configuration

For Microsoft Account authentication, the instructor configures:

**SQL Server → Settings → Microsoft Entra ID → Set Admin**

### If old credentials are stored

Use:

**Transform Data → Data Source Settings → Clear Permissions → Delete**

### MFA/Authen­ticator

If Microsoft Authenticator is enabled, an additional verification step may appear.

### Duplicate data

If the same table is loaded twice:

1. Delete the unwanted duplicate.
2. Rename the remaining table appropriately.

---

# 36. Topics Covered So Far in the Project

The instructor now has established the major data-source workflow:

```text
1. Create Azure Account
          ↓
2. Create Azure SQL Database
          ↓
3. Create SQL Server
          ↓
4. Configure Firewall
          ↓
5. Connect using SSMS
          ↓
6. Import CSV/Flat File
          ↓
7. Clean Data Using SQL
          ↓
8. Connect Azure SQL → Power BI
          ↓
9. Database Authentication
          ↓
10. Microsoft Account Authentication
          ↓
11. Load Data into Power BI
```

---

# 37. What Comes Next?

The instructor states that after getting the data into Power BI, the project will move toward:

* **Data cleaning**
* **Power Query Editor**
* **Reporting**
* **Publishing the report**
* Other topics included in the project

So the next major phase is to work with the imported data **inside Power BI**, rather than focusing only on the Azure SQL connection.

---

## Quick Revision

The most important sequence from this lecture is:

> **Clear existing permissions → Get Data → Azure SQL Database → Enter Server Name → Import → Microsoft Account → Sign In → Configure Microsoft Entra ID if required → Set Admin → Save → Retry connection → Sign in with Microsoft Account → Complete authentication → Select Database → Select Table → Load → Remove duplicate table → Rename remaining table.**

The key new concept in this session is that **Azure SQL Database can be connected to Power BI using a Microsoft Account, but the SQL Server needs the appropriate Microsoft Entra ID administrator configuration for the demonstrated authentication flow.**
