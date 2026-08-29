# Microsoft SQL Server — Download and Installation Notes

## 1. Introduction

This session covers the complete process of:

* Downloading **Microsoft SQL Server**
* Choosing the appropriate SQL Server edition
* Installing **SQL Server Developer Edition**
* Downloading and installing **SQL Server Management Studio (SSMS)**
* Opening SSMS
* Connecting to the SQL Server Database Engine
* Running a basic SQL query to verify that the installation is working

The next sessions will begin with **SQL (Structured Query Language)** and cover different SQL concepts, components, questions, and examples.

---

# 2. SQL Server Editions

Microsoft provides multiple SQL Server editions. In this session, two editions are discussed:

1. **Developer Edition**
2. **Express Edition**

---

## 3. Developer Edition

The **Developer Edition** is:

* Free
* Full-featured
* Licensed for **development and testing**
* Intended for **non-production environments**

### Important

Developer Edition provides the full capabilities of SQL Server, making it suitable for learning and practicing SQL Server features.

For this course/project, the **Developer Edition** is selected because the purpose is practice and development.

---

# 4. Express Edition

The **Express Edition** is also:

* Free
* Intended for lightweight SQL Server scenarios
* Suitable for development and production applications within its limitations

It is described as being ideal for:

* Desktop applications
* Web applications
* Server applications

### Developer vs Express

| Feature         | Developer Edition             | Express Edition                 |
| --------------- | ----------------------------- | ------------------------------- |
| Cost            | Free                          | Free                            |
| Features        | Full-featured SQL Server      | Limited compared with Developer |
| Development     | ✅ Yes                         | ✅ Yes                           |
| Testing         | ✅ Yes                         | ✅ Yes                           |
| Production      | ❌ Not licensed for production | ✅ Yes, within its limitations   |
| Course practice | **Recommended**               | Possible                        |

### Key point

For **learning, practice, and development**, the lecture chooses:

> **SQL Server Developer Edition**

---

# 5. Download SQL Server Developer Edition

The instructor provides a Microsoft download link in the **Resource section** of the course.

### Steps

1. Open the SQL Server download page.
2. Scroll down to the available editions.
3. Locate:

   * Developer Edition
   * Express Edition
4. Select **Developer Edition**.
5. Click **Download Now**.

An executable/installer file will be downloaded.

---

# 6. Install SQL Server

Once the executable file has downloaded:

1. Open the downloaded executable file.
2. Windows may display a security/permission prompt.
3. Click **Yes**.
4. Proceed with the installation.
5. Select/accept the appropriate installation options.
6. Start the installation.

The SQL Server download and installation process can take some time.

> **Note:** The installation portion can be fast-forwarded when following the lecture because it may take considerable time.

After waiting for the installation to complete:

**SQL Server installation is completed.**

---

# 7. SQL Server Management Studio (SSMS)

Installing SQL Server alone is not the end of the setup.

You also need a tool through which you can interact with SQL Server.

That tool is:

> **SQL Server Management Studio (SSMS)**

SSMS provides a graphical interface for:

* Connecting to SQL Server
* Creating and managing databases
* Writing SQL queries
* Executing SQL statements
* Viewing query results
* Managing SQL Server objects

---

# 8. Download SQL Server Management Studio

After SQL Server installation is complete, the installer provides an option:

> **Install SSMS**

Click:

**Install SSMS**

This takes you to the Microsoft page from where SSMS can be downloaded.

### Steps

1. Click **Install SSMS**.
2. The Microsoft SSMS download page opens.
3. Scroll down if required.
4. Locate the SSMS download link.
5. Click the download link.
6. Wait for the SSMS executable/setup file to download.

---

# 9. Install SSMS

Once the SSMS setup file has been downloaded:

1. Open the downloaded executable file.
2. Windows may ask for permission.
3. Click **Yes**.
4. The SSMS installer will start.
5. Begin the installation.
6. Wait for the installation to complete.

The installation may take some time.

After installation finishes, you should see a message indicating that the required components have been installed successfully.

Click:

**Close**

---

# 10. Open SQL Server Management Studio

After installing SSMS, you can search for it using the Windows search bar.

### Steps

1. Open the Windows **Search** bar.
2. Search for:

**SQL Server Management Studio**

3. You should see an entry similar to:

**SQL Server Management Studio 20**

4. Click it to launch SSMS.

SSMS may take some time to open for the first time.

---

# 11. Connect to SQL Server from SSMS

When SSMS opens, you will see the **Connect to Server** window.

Several connection options are available.

### Server Type

Select:

**Database Engine**

This tells SSMS that you want to connect to the SQL Server Database Engine.

---

## 12. Server Name

Next, provide the SQL Server's server name.

In the lecture, the server name is:

**Lenovo**

So the Server Name field contains:

`Lenovo`

Your server name may be different.

Therefore, **do not necessarily use `Lenovo`**. Use the server/instance name configured on your own computer.

---

# 13. Authentication

The lecture uses:

**Windows Authentication**

Windows Authentication uses your Windows account credentials to authenticate with SQL Server.

### Connection configuration in the lecture

| Setting        | Value                  |
| -------------- | ---------------------- |
| Server Type    | Database Engine        |
| Server Name    | Lenovo                 |
| Authentication | Windows Authentication |
| Encryption     | Optional               |

Once these settings are configured:

1. Verify the server details.
2. Select **Windows Authentication**.
3. Click **Connect**.

SSMS will attempt to establish a connection to SQL Server.

---

# 14. Create a New Query

After successfully connecting to SQL Server, you can start writing SQL queries.

In SSMS:

1. Click **New Query**.
2. A new query editor/window will open.
3. Write your SQL statement in the editor.

This is where you will execute SQL commands throughout the course.

---

# 15. Execute a Simple SQL Statement

To verify that SQL Server and SSMS are working correctly, the instructor executes a very simple calculation.

The query is:

```sql
SELECT 5 + 5;
```

### What does it do?

SQL Server evaluates:

**5 + 5 = 10**

and returns:

**10**

---

# 16. Selecting and Executing the Query

In the lecture, the statement is written in the query window.

Then:

1. Select the SQL statement.
2. Click **Execute**.
3. SQL Server processes the query.
4. The result appears in the results section.

The output is:

| Result |
| -----: |
|     10 |

This confirms that:

* SQL Server is installed correctly.
* SSMS is connected to SQL Server.
* SQL queries can be executed successfully.

---

# 17. Complete Installation Flow

The entire setup can be remembered as:

**Open Microsoft SQL Server download page**
↓
**Choose Developer Edition**
↓
**Click Download Now**
↓
**Open downloaded executable**
↓
**Click Yes**
↓
**Install SQL Server**
↓
**Wait for installation to complete**
↓
**Install SSMS**
↓
**Open SSMS download page**
↓
**Download SSMS**
↓
**Open SSMS installer**
↓
**Click Yes**
↓
**Install SSMS**
↓
**Close installer after successful installation**
↓
**Search for SQL Server Management Studio**
↓
**Open SSMS**
↓
**Server Type → Database Engine**
↓
**Enter Server Name**
↓
**Authentication → Windows Authentication**
↓
**Click Connect**
↓
**Click New Query**
↓
**Write `SELECT 5 + 5;`**
↓
**Execute**
↓
**Result = 10**

---

# 18. SQL Server vs SSMS

An important distinction is:

### SQL Server

**SQL Server** is the actual database management system/database engine.

It is responsible for:

* Storing data
* Processing SQL queries
* Managing databases
* Executing SQL operations

### SSMS

**SQL Server Management Studio** is the graphical management and development tool used to interact with SQL Server.

You can think of it as:

> **SQL Server = Database Engine**
> **SSMS = Tool/interface used to work with SQL Server**

Installing SSMS does not mean that SQL Server itself has been installed. They are separate components.

---

# 19. Creating an SSMS Desktop Shortcut

The lecture also mentions that you can create a desktop shortcut for SSMS.

This makes it easier to launch SSMS without searching for it every time.

### General approach

1. Search for **SQL Server Management Studio** in Windows.
2. Locate the SSMS application.
3. Create a desktop shortcut for the application.
4. Use the shortcut to directly launch SSMS in the future.

---

# 20. Important Points to Remember

### SQL Server Editions

* **Developer Edition**

  * Free
  * Full-featured
  * For development and testing
  * Non-production use

* **Express Edition**

  * Free
  * Suitable for desktop, web, and server applications
  * Can be used for production within its limitations

### For this course

The instructor chooses:

> **SQL Server Developer Edition**

because the objective is learning/practice and development.

---

### SSMS

* SSMS stands for **SQL Server Management Studio**.
* It is used to interact with SQL Server.
* It allows you to write and execute SQL queries.
* It provides a graphical interface for managing SQL Server.

---

### Connection Settings

The lecture uses:

* **Server Type:** Database Engine
* **Server Name:** Lenovo
* **Authentication:** Windows Authentication
* **Encryption:** Optional

Your server name may differ from the instructor's.

---

# 21. Verification Test

After connecting to SQL Server, run:

```sql
SELECT 5 + 5;
```

Expected result:

```text
10
```

If the query executes successfully and returns `10`, your basic SQL Server + SSMS setup is working.

---

# 22. Key Interview/Exam Questions

### Q1. What is SQL Server Developer Edition?

It is a free, full-featured SQL Server edition intended for development and testing in non-production environments.

### Q2. What is SQL Server Express Edition?

It is a free SQL Server edition designed for lightweight applications and can be used for development and production within its resource/functionality limitations.

### Q3. Which edition was selected for the course?

**Developer Edition.**

### Q4. Why was Developer Edition selected?

Because the course is focused on learning, practice, development, and testing rather than production deployment.

### Q5. What is SSMS?

**SQL Server Management Studio** is Microsoft's graphical tool for connecting to, querying, and managing SQL Server.

### Q6. Is SSMS the same thing as SQL Server?

**No.**

SQL Server is the database engine, while SSMS is the management/development interface used to work with SQL Server.

### Q7. What Server Type was selected in SSMS?

**Database Engine**

### Q8. Which authentication method was used?

**Windows Authentication**

### Q9. How can you verify that SQL Server is working?

Connect to the Database Engine through SSMS and execute:

```sql
SELECT 5 + 5;
```

If the result is `10`, the connection and query execution are working correctly.

---

# 23. Final Setup Checklist

* [ ] Download SQL Server Developer Edition
* [ ] Install SQL Server
* [ ] Install SQL Server Management Studio
* [ ] Open SSMS
* [ ] Select **Database Engine**
* [ ] Enter the appropriate server name
* [ ] Select **Windows Authentication**
* [ ] Click **Connect**
* [ ] Open **New Query**
* [ ] Execute `SELECT 5 + 5;`
* [ ] Verify that the result is **10**
* [ ] Optionally create an SSMS desktop shortcut

### End Result

At the end of this session, **SQL Server and SSMS are installed and connected successfully**, and the environment is ready for the upcoming SQL lessons, where the course will begin working with **Structured Query Language (SQL)** and its different concepts and components.
