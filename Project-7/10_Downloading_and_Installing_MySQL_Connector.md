# Power BI: Switching Data Source from SQL Server to MySQL

## 1. Objective of the Session

In the previous session, the Power BI report was moved from the **Test environment to the Production environment** while continuing to use **Microsoft SQL Server** as the data source.

Now a new requirement has been introduced:

> The company/client has decided to change the database technology from **Microsoft SQL Server to MySQL**.

The challenge is that we **do not want to recreate the Power BI report from scratch**.

We want to preserve:

* Existing report pages
* Visuals
* DAX measures
* Calculations
* Formatting
* Report logic

and simply move the report to use **MySQL as the new data source**.

---

# 2. The Scenario

### Earlier architecture

```text
Microsoft SQL Server
        ↓
   Power BI
        ↓
 Power BI Report
```

Now the client wants:

```text
MySQL Database
        ↓
   Power BI
        ↓
 Same Power BI Report
```

The objective is therefore to **change the underlying data source without rebuilding the report**.

---

# 3. First Requirement: Connect Power BI to MySQL

Before we can migrate the report, Power BI must be able to connect to MySQL.

In Power BI Desktop:

### Steps

1. Open **Power BI Desktop**.
2. Click **Get Data**.
3. Click **More**.
4. In the search box, type:

```text
MySQL
```

5. Select **MySQL database**.
6. Double-click the connector.

---

# 4. Initial MySQL Connector Error

When attempting to use the MySQL connector, Power BI displays an error indicating that:

> The connector requires one or more additional components to be installed before it can be used.

### Meaning

Power BI has the MySQL connector option available, but the required supporting component/driver is not installed on the machine.

Therefore:

**Power BI cannot connect to MySQL yet.**

We need to install the required MySQL connector components first.

---

# 5. Required Component: MySQL Connector/NET

The lecture uses the **MySQL Connector/NET** component.

This is required so that Power BI can properly connect to and import data from a MySQL database.

The overall process is:

```text
Install MySQL Connector/NET
          ↓
Restart Power BI Desktop
          ↓
Use MySQL Database connector
          ↓
Provide Server + Database details
          ↓
Connect to MySQL
```

---

# 6. Download MySQL Connector/NET

Open a web browser and search for:

```text
Download MySQL Connector NET
```

Open the official MySQL download page for **MySQL Connector/NET**.

---

# 7. Select the Operating System

On the download page:

1. Select the appropriate operating system.
2. In the lecture, **Microsoft Windows** is selected.
3. Locate the Windows installer.

The lecture selects:

**Windows 32-bit MSI Installer**

and clicks **Download**.

> The important concept is to download the appropriate Connector/NET installer for your Windows/Power BI setup.

---

# 8. Download Without Creating an Account

After clicking Download, MySQL may provide options to sign in or create an account.

You **do not need to sign up or log in** for this installation.

Select:

**No thanks, just start my download**

The installer will then download to your computer.

---

# 9. Install MySQL Connector/NET

Once the installer has downloaded:

1. Open the downloaded installer.
2. Proceed through the installation wizard.
3. Click **Next** as required.
4. Allow the installation to proceed.
5. If Windows asks for permission, click **Yes**.
6. Wait for the installation to complete.
7. Click **Finish**.

The installation may take some time.

---

# 10. Restart Power BI Desktop

After installing the connector, close Power BI Desktop if it is already open.

This is important because Power BI needs to reload the newly installed connector/driver components.

### Steps

1. Close Power BI Desktop.
2. Open Power BI Desktop again.
3. Wait for it to load.

---

# 11. Test the MySQL Connection Again

After restarting Power BI Desktop:

1. Click **Blank Report**.
2. Click **Get Data**.
3. Search for:

```text
MySQL
```

4. Select **MySQL database**.
5. Double-click the connector.

This time, the previous error should no longer appear.

---

# 12. MySQL Connection Window

After the connector has been installed correctly, Power BI displays the MySQL connection dialog.

You should now see fields where you can provide:

* **Server**
* **Database**

This confirms that Power BI is now ready to connect to a MySQL database.

Previously:

```text
MySQL connector
      ↓
Error: additional components required
```

After installing Connector/NET:

```text
MySQL connector
      ↓
Server + Database fields
      ↓
Ready to connect
```

---

# 13. MySQL Workbench

The lecture also reminds us that **MySQL Workbench** was already discussed earlier in the project/course.

MySQL Workbench will be used for working with the MySQL database.

If it has not already been installed, you should download and install **MySQL Workbench** as covered in the earlier session.

### Important distinction

**MySQL Workbench** and **MySQL Connector/NET** serve different purposes.

| Component               | Purpose                                                                                            |
| ----------------------- | -------------------------------------------------------------------------------------------------- |
| **MySQL Workbench**     | Work with/manage the MySQL database and execute SQL                                                |
| **MySQL Connector/NET** | Provides the required connectivity component for applications such as Power BI to connect to MySQL |

---

# 14. What Will Happen Next?

The current session focuses primarily on getting the **MySQL connectivity setup ready**.

The broader migration will involve two major activities:

### Part 1 — Bring the data into MySQL

The existing data needs to be available in the MySQL database.

Conceptually:

```text
Existing Data
     ↓
MySQL Database
```

### Part 2 — Connect Power BI to MySQL

Once the data exists in MySQL:

```text
MySQL Database
      ↓
Power BI
      ↓
Existing Report
```

The next sessions will discuss these steps in more detail.

---

# 15. Important Migration Principle

The key concept is that changing the database technology does **not necessarily mean rebuilding the Power BI report**.

The desired approach is:

```text
Existing Power BI Report
        │
        │ Keep
        ↓
Existing DAX + Visuals + Formatting
        │
        │ Change data source
        ↓
      MySQL
```

Instead of:

```text
SQL Server Report
       ↓
Delete everything
       ↓
Recreate report
       ↓
Recreate DAX
       ↓
Recreate visuals
       ↓
Recreate formatting
```

The second approach would be unnecessarily time-consuming.

---

# 16. SQL Server → MySQL Migration Flow

The complete scenario can be visualized as:

```text
             SQL SERVER
                 │
                 ↓
         Existing Power BI
             Report
                 │
                 │
        Client changes DB
                 │
                 ↓
              MySQL
                 │
        ┌────────┴────────┐
        ↓                 ↓
 MySQL Workbench    Connector/NET
        │                 │
        ↓                 ↓
   MySQL Data       Power BI Connectivity
        │                 │
        └────────┬────────┘
                 ↓
             Power BI
                 ↓
        Existing Report
```

---

# 17. Why the Connector Is Necessary

Power BI needs the appropriate connectivity components to communicate with MySQL.

Installing **MySQL Connector/NET** provides the necessary component required by the Power BI MySQL connector in this setup.

Without it:

```text
Power BI
   ↓
MySQL Connector
   ↓
❌ Required component missing
```

After installation:

```text
Power BI
   ↓
MySQL Connector
   ↓
Connector/NET
   ↓
MySQL Database
   ↓
✅ Connection possible
```

---

# 18. Practical Steps — Complete Checklist

## A. Prepare MySQL

* Install **MySQL Workbench** if not already installed.
* Ensure the MySQL database is available.
* Bring the required project data into MySQL.

## B. Prepare Power BI

* Open Power BI Desktop.
* Go to **Get Data → More**.
* Search for **MySQL**.
* Select **MySQL database**.
* If the additional-components error appears, install **MySQL Connector/NET**.

## C. Install Connector/NET

1. Search for **Download MySQL Connector NET**.
2. Open the MySQL download page.
3. Select the appropriate operating system.
4. Download the appropriate MSI installer.
5. Choose **No thanks, just start my download** if prompted for login.
6. Open the downloaded installer.
7. Complete the installation wizard.
8. Click **Finish**.

## D. Restart Power BI

1. Close Power BI Desktop.
2. Reopen Power BI Desktop.
3. Click **Blank Report**.
4. Go to **Get Data → More**.
5. Search for **MySQL**.
6. Select **MySQL database**.

## E. Verify Connectivity

You should now get the MySQL connection dialog with fields for:

* Server
* Database

This confirms that the required connector setup is working.

---

# 19. Key Takeaways

### 1. Changing the data source does not automatically mean rebuilding the report

The goal is to reuse the existing Power BI report.

### 2. Power BI has a MySQL connector

It can be found through:

**Get Data → More → MySQL database**

### 3. Additional components may be required

If Power BI shows:

> This connector requires one or more additional components...

install the required **MySQL Connector/NET** component.

### 4. Restart Power BI after installation

This ensures Power BI recognizes the newly installed connector.

### 5. MySQL Workbench and Connector/NET are different

* Workbench → work with the MySQL database.
* Connector/NET → enables required connectivity from Power BI.

### 6. Data must ultimately be available in MySQL

Installing the connector only solves the **connectivity** problem. The actual project data must also be brought into the MySQL database.

---

# 20. One-Line Revision

> **To migrate a Power BI report from SQL Server to MySQL, first make the data available in MySQL, install the required MySQL Connector/NET component, restart Power BI, verify the MySQL connection, and then change the report's underlying data source rather than rebuilding the report.**
