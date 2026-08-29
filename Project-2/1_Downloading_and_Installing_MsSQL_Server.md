# Detailed Notes — Downloading & Installing Microsoft SQL Server

## 1. Objective of the Lecture

For the **second Power BI project**, Microsoft SQL Server will be used as the **data source**.

Before starting the project, you should:

1. Have **Microsoft SQL Server installed** on your system.
2. Know how to **import/load data into Microsoft SQL Server**.
3. Know how to use **SQL Server Management Studio (SSMS)** to work with the SQL Server database.
4. Later, connect **Power BI to SQL Server** and import the required data into Power BI.

> The instructor mentions that SQL Server itself will be covered in separate lectures. This lecture focuses specifically on **downloading and installing SQL Server and SSMS**.

---

# 2. SQL Server Editions

The instructor opens the SQL Server download webpage.

After scrolling down, two editions are available:

* **Developer Edition**
* **Express Edition**

### Developer Edition

For this project, the instructor chooses:

> **SQL Server Developer Edition**

The Developer Edition is suitable for learning and development purposes.

---

# 3. Download Microsoft SQL Server

### Step 1: Open the SQL Server Download Page

The instructor has already opened the relevant Microsoft webpage.

The link will be provided in the **resource section** of the course.

### Step 2: Select Developer Edition

On the download page:

1. Scroll down.
2. Locate the available editions.
3. Select **Developer Edition**.
4. Click **Download Now**.

An executable (`.exe`) installation file will be downloaded.

### Step 3: Run the Installer

Once the executable file is downloaded:

1. Click the downloaded executable.
2. If Windows displays a security/permission prompt, click **Yes**.

---

# 4. SQL Server Installation Options

After launching the SQL Server installer, different installation types are displayed.

The instructor chooses:

> **Basic**

### Steps

1. Select **Basic** installation.
2. Accept the license terms.
3. Click **Install**.

The SQL Server installation will then begin.

### Important

The installation can take some time.

You can:

* Wait for the installation to complete.
* Fast-forward/skip this portion of the lecture because there is no additional configuration being demonstrated during the installation process.

---

# 5. Install SQL Server Management Studio (SSMS)

After SQL Server installation, the instructor proceeds to install **SQL Server Management Studio**, commonly abbreviated as:

> **SSMS**

### What is SSMS?

**SQL Server Management Studio (SSMS)** is the tool used to interact with SQL Server.

It allows you to:

* Connect to a SQL Server instance.
* Create and manage databases.
* Write SQL queries.
* Execute SQL queries.
* View tables and other database objects.
* Manage SQL Server databases.

For this course/project, **SQL queries will be written and executed using SSMS**.

---

# 6. Download SSMS

After SQL Server installation, the installer provides an option:

> **Install SSMS**

The instructor clicks this option.

### Steps

1. Click **Install SSMS**.
2. A new webpage opens.
3. Scroll down.
4. Locate **Download SQL Server Management Studio**.
5. Click the download option.
6. Wait for the SSMS executable to download.

Again, downloading may take some time.

---

# 7. Install SSMS

Once the SSMS executable has been downloaded:

1. Click the executable file.
2. Click **Run** if prompted.
3. Click **Yes** if Windows asks for permission.
4. Proceed with the installation.

The installation may take some time.

After installation finishes:

5. Click **Close**.

SSMS is now installed.

---

# 8. Open SQL Server Management Studio

To open SSMS:

1. Open the Windows **Search** bar.
2. Type:

```text
SQL
```

3. Look for:

> **SQL Server Management Studio**

4. Click it.

SSMS will open.

---

# 9. Connect to the SQL Server Instance

When SSMS opens, you will see a **Connect to Server** window.

You need to provide the appropriate server details.

The instructor demonstrates the following configuration.

### Server Type

Select:

> **Database Engine**

The Database Engine is the SQL Server component that stores and manages databases.

### Server Name

Enter the SQL Server instance/server name installed on your computer.

In the instructor's example, the server name is shown as:

> `giant Lenovo`

Your server name will **not necessarily be the same**.

You should use the server name associated with your own SQL Server installation.

### Authentication

The instructor selects:

> **Windows Authentication**

This allows Windows credentials to be used for connecting to the local SQL Server instance.

### Optional Trust Server Certificate

The instructor also selects:

> **Trust server certificate**

This option is enabled before connecting.

### Final Configuration

The connection settings demonstrated are therefore:

| Setting                  | Value                         |
| ------------------------ | ----------------------------- |
| Server type              | Database Engine               |
| Server name              | Your SQL Server instance name |
| Authentication           | Windows Authentication        |
| Trust server certificate | Selected                      |

Then click:

> **Connect**

---

# 10. SQL Server Object Explorer

After successfully connecting, SSMS displays the **Object Explorer**.

The Object Explorer allows you to navigate through the SQL Server environment and its objects.

The instructor expands the Object Explorer to view the available database-related objects.

This is where you can work with things such as databases, tables, and other SQL Server objects.

---

# 11. Create a New SQL Query

The instructor then demonstrates how to open a SQL query window.

### Steps

1. In SSMS, click **New Query**.
2. A new query window opens.

This is the window where you will write and execute SQL commands.

For example, SQL queries can be written in this area when working with databases and tables.

---

# 12. How This Fits Into the Power BI Project

The overall workflow for the second Power BI project is:

```text
Data
  ↓
Microsoft SQL Server
  ↓
SQL Server Management Studio (SSMS)
  ↓
Power BI
  ↓
Power BI Report
```

More specifically:

### Step 1 — Install SQL Server

Install **Microsoft SQL Server Developer Edition**.

### Step 2 — Install SSMS

Install **SQL Server Management Studio**.

### Step 3 — Load Data into SQL Server

The next lecture will explain how to **import/load the project data into Microsoft SQL Server**.

### Step 4 — Connect Power BI to SQL Server

Once the data is available inside SQL Server, Power BI can connect to SQL Server as a **data source**.

### Step 5 — Bring Data Into Power BI

Import/connect the SQL Server data into Power BI.

### Step 6 — Start the Second Power BI Project

After the data is available in Power BI, you can proceed with the requirements and report-building steps discussed in the second Power BI project.

---

# 13. Real-World/Company Scenario

The instructor also explains that the installation process shown here is mainly necessary because this is a **learning/project environment**.

In an actual company or client environment:

* SQL Server may already be set up.
* The organization will provide the necessary credentials.
* You generally won't need to install SQL Server yourself.
* If SQL Server is the organization's data source, you can use the provided credentials to connect Power BI to that SQL Server.

For example:

```text
Company SQL Server
       ↓
Credentials provided by organization
       ↓
Power BI
       ↓
Reports / Dashboards
```

So, in a real project, your responsibility may primarily be to **connect to the existing SQL Server**, rather than install and configure the server from scratch.

---

# 14. Important Terminology

### Microsoft SQL Server

A relational database management system used to **store, manage, and query data**.

### SQL Server Database Engine

The core SQL Server component responsible for storing and processing databases.

### SQL Server Management Studio (SSMS)

A graphical application used to interact with SQL Server and write/execute SQL queries.

### SQL Query

A command written using SQL to retrieve, insert, update, delete, or manipulate data in a database.

### Server Name

The name/instance through which SSMS connects to a particular SQL Server installation.

### Windows Authentication

An authentication method that uses the user's Windows credentials to connect to SQL Server.

### Power BI

The reporting and data-analysis tool that can connect to SQL Server and use its data for creating reports and dashboards.

---

# 15. Complete Installation Procedure — Quick Revision

Follow this sequence when setting up the environment:

### SQL Server

1. Open the Microsoft SQL Server download page.
2. Scroll down to the available editions.
3. Select **Developer Edition**.
4. Click **Download Now**.
5. Run the downloaded executable.
6. Click **Yes** if prompted.
7. Select **Basic** installation.
8. Accept the license terms.
9. Click **Install**.
10. Wait for the installation to complete.

### SSMS

11. Click **Install SSMS** after SQL Server installation.
12. A new webpage opens.
13. Scroll down.
14. Click **Download SQL Server Management Studio**.
15. Wait for the executable to download.
16. Run the executable.
17. Click **Run/Yes** when prompted.
18. Wait for installation to complete.
19. Click **Close**.

### Connect to SQL Server

20. Search for **SQL Server Management Studio** in Windows.
21. Open SSMS.
22. Select **Database Engine** as the server type.
23. Enter your **SQL Server server/instance name**.
24. Select **Windows Authentication**.
25. Select **Trust server certificate** as demonstrated.
26. Click **Connect**.
27. Expand **Object Explorer**.
28. Click **New Query**.
29. The SQL query editor opens.

---

# 16. Key Takeaways

* The second Power BI project uses **Microsoft SQL Server as a data source**.
* Install **SQL Server Developer Edition** for the project.
* Install **SQL Server Management Studio (SSMS)** separately.
* **SSMS is where SQL queries will be written and executed.**
* Use **Database Engine** when connecting through SSMS.
* The demonstrated authentication method is **Windows Authentication**.
* Your server name will depend on your own SQL Server installation.
* Once SQL Server is installed, the next step is to **import the project data into SQL Server**.
* After loading the data into SQL Server, **Power BI can connect to SQL Server and bring the data into the Power BI project**.
* In real-world organizations, SQL Server is often already available, and you are provided with the necessary credentials to connect to it.
