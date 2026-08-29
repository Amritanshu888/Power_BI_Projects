# Connecting Google BigQuery to Power BI

## 1. Objective of the Session

The main objective of this session is to learn how to:

1. **Load data from a local file into Google BigQuery**
2. Verify the data inside BigQuery using SQL
3. **Connect Google BigQuery to Power BI Desktop**
4. Load the BigQuery data into Power BI
5. Understand the difference between **Import** and **DirectQuery** connectivity modes
6. Understand where data cleaning/transformation can be performed.

The project uses **Google BigQuery as the data source** for Power BI. 

---

# 2. Overall Workflow

The complete process followed in the lecture is:

```text
Local CSV File
      ↓
Google BigQuery
      ↓
Create Dataset
      ↓
Create Table
      ↓
Verify Data using SQL
      ↓
Connect BigQuery to Power BI
      ↓
Select Dataset & Table
      ↓
Choose Connectivity Mode
      ↓
Import Data
      ↓
Power BI Data Model
      ↓
Create Reports
```

The instructor specifically follows this approach from a **project-learning perspective**: first load the local data into BigQuery and then connect BigQuery to Power BI. 

---

# Part 1 — Loading Local Data into Google BigQuery

## 3. Open Google BigQuery

The instructor assumes that the Google Cloud account was created in the previous session.

You should already have your Google Cloud account/project available.

### Steps

1. Open **Google Cloud**.
2. At the top, locate the **search box**.
3. Search for:

> **BigQuery**

4. Select:

> **Data Warehouse Analytics**

5. Open **BigQuery Data Warehouse Analytics**. 

---

# 4. Real-World Scenario vs. Project Scenario

The instructor explains an important distinction.

### In a real-time/real-world environment

As a Power BI developer, you would typically already have:

* Access to certain datasets
* Required permissions
* Data available in BigQuery

You could then directly connect:

```text
BigQuery → Power BI → Report
```

You wouldn't necessarily need to upload the data yourself.

### In this project

Since we need to demonstrate the entire process, the instructor first loads a **local file into BigQuery**.

The project workflow is therefore:

```text
Local File
    ↓
BigQuery
    ↓
Power BI
    ↓
Report
```

This is also useful from an **interview perspective**, because you can demonstrate knowledge of connecting Power BI to multiple data sources, including BigQuery. 

---

# 5. Add a Local File to BigQuery

There are different ways to add data.

The instructor mentions that you can either:

* Use the option to add data directly from the interface, or
* Click **Add** at the top.

### Steps

1. Click **Add**.
2. Select:

> **Local file**

This allows you to upload a file stored on your computer. 

---

# 6. Select the Local File

The instructor clicks **Browse** to locate the file.

The file being used in the project is:

> **Housing data**

### File format

The data is stored as:

> **CSV**

The instructor also mentions that this file will be provided in the course's **Resource section**. 

### Steps

1. Click **Browse**.
2. Locate the housing CSV file.
3. Select the file.
4. Double-click the file to select it.

---

# 7. Information Required to Load the File

When uploading the file, BigQuery requires several pieces of information.

You need to provide:

* **File format**
* **Project**
* **Dataset ID**
* **Table name**

These details determine where and how the uploaded data will be stored. 

---

# 8. Select File Format

Since the housing file is a CSV file:

> **File format = CSV**

The instructor confirms that the file format is automatically/explicitly specified as CSV. 

---

# 9. Create a Dataset

The next step is to create a dataset in BigQuery.

The instructor selects:

> **Dataset → Create a new dataset**

A **Dataset ID** needs to be specified.

### Example used in the lecture

The instructor names the Dataset ID:

> `1`

This is simply an example name; the important point is that a Dataset ID must be provided. 

---

## 10. Choose Dataset Location

BigQuery provides a location option.

The instructor mentions that you can choose between:

* A specific **region**
* A **multi-region**

For this demonstration, the instructor keeps:

> **Multi-region**

### Steps

1. Select the desired location type.
2. Keep **Multi-region** selected.
3. Click:

> **Create Dataset**



---

# 11. Specify the Table Name

After creating/providing the Dataset ID, you also need to provide the **table name**.

The instructor chooses:

> `housing`

So the hierarchy becomes:

```text
Google Cloud Project
       ↓
Dataset ID: 1
       ↓
Table: housing
```

---

# 12. Configure Schema

BigQuery needs to know the structure/schema of the table.

Instead of manually specifying every column and its data type, the instructor uses:

> **Auto Detect**

### Steps

1. Enter the table name:

   > `housing`
2. Under Schema, select:

   > **Auto Detect**
3. Click:

   > **Create Table**

BigQuery will attempt to detect the columns and their data types from the CSV file. 

---

# Part 2 — Verify the Data in BigQuery

## 13. Locate the Dataset and Table

After the table is created, the instructor navigates through the BigQuery project structure.

### Hierarchy

```text
Project
  ↓
Dataset
  ↓
Table
```

The instructor clicks the arrow next to the project/dataset to expand them.

The Dataset ID created earlier is:

> `1`

Then the table created inside that dataset is:

> `housing` 

---

# 14. Open SQL Query

To verify that the data has actually been loaded, the instructor opens an SQL query.

### Steps

1. Click the **three dots** next to the table.
2. Select the option to open/write an **SQL query**.

A query similar to the following is generated:

```sql
SELECT *
FROM `project.dataset.table`
LIMIT 1000;
```

The exact project/dataset/table reference shown in the lecture corresponds to:

```text
Project → Dataset 1 → housing
```

The purpose is to retrieve rows from the `housing` table. 

---

# 15. Execute the SQL Query

Once the query is available:

1. Select the query if necessary.
2. Click the:

> **Run**

button.

BigQuery executes the query and displays the result in the:

> **Query Results**

section. 

---

# 16. Examine the Query Results

The instructor confirms that the data has been successfully loaded.

The table contains several columns, including:

* `date`
* `quarter`
* `house ID`
* `house type`
* `sales type`
* `year build`
* `purchase price`
* And many other columns.

The instructor explicitly says that the **column definitions are not being discussed yet**.

Those will be covered later during:

* Data cleaning
* Data transformation
* Reporting



### Important takeaway

At this point, the objective is **only to verify that the data has successfully been loaded into BigQuery**.

---

# Part 3 — Connect Google BigQuery to Power BI

## 17. Open Power BI Desktop

After successfully loading the data into BigQuery, the next objective is to connect it to Power BI.

### Steps

1. Open **Power BI Desktop**.
2. Click:

> **Blank Report**

Power BI Desktop may take some time to load. 

---

# 18. Check Data Source Settings Before Connecting

Before actually establishing the BigQuery connection, the instructor explains **Data Source Settings**.

This is useful because Power BI stores credentials/permissions for previously connected data sources.

### Steps

1. Click:

> **Transform Data**

2. Select:

> **Data Source Settings**

Here, you can see the different data sources to which Power BI has previously connected. 

---

# 19. Clear Existing BigQuery Permissions

In the instructor's Power BI environment, Google BigQuery is already listed because the instructor had previously connected to BigQuery before recording the video.

Therefore, the instructor clears the existing permission.

### Steps

1. Select:

> **Google BigQuery**

2. Click:

> **Clear Permissions**

3. Confirm/delete the permissions if prompted.

### Important

**You do NOT need to perform this step when connecting to BigQuery for the first time.**

This step is demonstrated only because the instructor had already established a BigQuery connection earlier.

However, clearing permissions can sometimes be useful when troubleshooting connection or authentication issues. 

---

# 20. Close Data Source Settings

After clearing the permission:

1. Close the Data Source Settings window.
2. Click:

> **Close & Apply**

You are returned to the Power BI report view. 

---

# Part 4 — Select Google BigQuery as the Data Source

## 21. Get Data

From Power BI Desktop:

1. Click:

> **Get Data**

2. Click:

> **More**

3. Search for:

> **BigQuery**

4. Select:

> **Google BigQuery**

5. Double-click/select it.



---

# 22. Sign in Using Your Google Account

Power BI will require authentication to access your BigQuery data.

The instructor sees an option for:

> **Organizational Account**

and indicates that the account is not currently signed in.

### Steps

1. Click:

> **Sign In**

2. Select the Google account that was used while creating the Google Cloud account.
3. Double-click/select the account.
4. Click:

> **Allow**

This completes the authentication process. 

---

# 23. Return to Power BI

After authentication, the browser indicates that sign-in is complete.

### Steps

1. Return to the Power BI application.
2. The browser tab used for authentication can be closed.
3. Continue working in Power BI Desktop.

The BigQuery connection should now be authenticated. 

---

# 24. Select the BigQuery Project

After authentication, Power BI displays the available BigQuery hierarchy.

The instructor identifies:

> **Project:** `stalwart bliss`

Then expands it using the arrow.

Inside the project is the dataset:

> **Dataset:** `1`

Then the instructor expands the dataset.

Inside it is:

> **Table:** `housing`

So the hierarchy in Power BI is:

```text
Google BigQuery
      ↓
Project: stalwart bliss
      ↓
Dataset: 1
      ↓
Table: housing
```



---

# 25. Preview the Data

After selecting the table, Power BI loads a preview.

The preview displays columns such as:

* Date
* Quarter
* Housing ID
* House Type
* Sales Type
* Year Build
* And other columns

The instructor again mentions that detailed explanations of these columns will be covered during the **data-cleaning and reporting sections**. 

---

# Part 5 — Transform or Load the Data

At this stage, Power BI gives you two broad choices.

You can either:

### Option 1 — Transform the Data

Use this if you need to perform data cleaning/transformation before loading it into the Power BI model.

For example, you might perform transformations in **Power Query Editor**.

### Option 2 — Load the Data

If the data is already suitable for loading, you can directly load it into Power BI.

For this session, the instructor chooses:

> **Load**

because data cleaning will be discussed in upcoming sessions. 

---

# Part 6 — Import vs DirectQuery

After clicking **Load**, Power BI asks which connectivity mode should be used.

The two modes discussed are:

1. **Import**
2. **DirectQuery**

This is one of the most important concepts from this lecture.

---

# 26. Import Mode

In **Import mode**, Power BI creates a copy of the data inside the Power BI Desktop model.

### Flow

```text
Google BigQuery
      ↓
Data copied
      ↓
Power BI Desktop Model
      ↓
Visuals / Reports
```

Therefore, Power BI works with the imported copy of the data.

The instructor chooses **Import mode** for this project. 

### Advantages mentioned/implied by the lecture

Import mode allows you to work with the data inside Power BI's model rather than querying BigQuery every time a visual needs information.

---

# 27. DirectQuery Mode

With **DirectQuery**, Power BI does **not create a copy of the data in Power BI Desktop**.

Instead, when Power BI needs information—for example, when displaying a visual—it sends a query back to Google BigQuery.

### Flow

```text
Power BI Visual
      ↓
Query sent to BigQuery
      ↓
BigQuery processes/query data
      ↓
Results returned to Power BI
      ↓
Visual displayed
```

So the underlying data remains in BigQuery rather than being imported into the Power BI model. 

---

# 28. DirectQuery Limitations

The instructor points out that **DirectQuery has certain limitations**.

Examples mentioned include limitations related to:

* Certain data-cleaning operations
* Certain DAX functions

Therefore, DirectQuery can impose restrictions compared with Import mode. 

---

# 29. Connectivity Mode Selected in This Project

For this project, the instructor chooses:

> **Import**

### Steps

1. Select **Import**.
2. Click:

> **OK**

Power BI then begins loading the data into its model. 

---

# Part 7 — Data Loading into Power BI

## 30. Wait for the Data to Load

The time required to load the data depends on:

* The volume/size of the data
* The amount of data being loaded

The instructor waits for the loading process to complete. 

---

# 31. Verify the Loaded Data

The instructor states that the dataset contains approximately:

> **1 lakh records**

and confirms that the data was successfully loaded into Power BI. 

---

# 32. View the Data in Power BI

To inspect the imported data:

1. Click the:

> **Table View**

icon in Power BI.

2. The data can now be viewed directly inside Power BI.

This confirms that the BigQuery data has successfully been loaded into the Power BI model. 

---

# Part 8 — Data Cleaning Options

The instructor explains that there are **two possible places** where data cleaning/transformation can be performed.

## Option 1 — Google BigQuery

You can perform transformations in BigQuery itself using:

> **SQL**

BigQuery supports SQL-based data transformations.

## Option 2 — Power BI

You can perform data cleaning/transformation using:

> **Power Query Editor**

So the overall architecture can be:

```text
                 ┌──→ BigQuery SQL
Raw Data → BigQuery
                 └──→ Power Query Editor → Power BI
```

The instructor emphasizes that both approaches are possible. 

---

# 33. Using SQL in BigQuery

Google BigQuery supports SQL for:

* Querying data
* Transforming data
* Performing data-cleaning operations

The instructor compares this with SQL environments previously discussed, such as:

* Microsoft SQL Server
* MySQL Workbench
* Snowflake SQL

However, the **SQL syntax can have certain differences** between these platforms. 

---

# 34. Upcoming SQL Discussion

The instructor says that upcoming sessions will demonstrate using **SQL in Google BigQuery** to obtain more information and details about the data.

This is similar to how SQL was used with **Snowflake** in an earlier part of the course.

The upcoming discussions will therefore cover:

* BigQuery SQL
* Data transformations
* Data cleaning
* Power Query Editor
* Power BI reporting



---

# Important Concepts to Remember

## BigQuery Hierarchy

Remember the relationship:

```text
Google Cloud Project
        ↓
Dataset
        ↓
Table
        ↓
Rows + Columns
```

In this lecture:

```text
Project: stalwart bliss
        ↓
Dataset: 1
        ↓
Table: housing
        ↓
~100,000 records
```

---

# Import vs DirectQuery — Quick Comparison

| Feature                                        | Import                                   | DirectQuery          |
| ---------------------------------------------- | ---------------------------------------- | -------------------- |
| Data copied into Power BI?                     | **Yes**                                  | **No**               |
| Data remains in BigQuery?                      | Yes, original remains                    | **Yes**              |
| Query sent to BigQuery when visuals need data? | Generally no, visuals use imported model | **Yes**              |
| Certain transformation limitations             | Fewer                                    | **More limitations** |
| Some DAX limitations                           | Fewer                                    | **Yes**              |
| Mode used in this project                      | **Yes**                                  | No                   |

The lecture specifically selects **Import** for this project. 

---

# Complete Practical Procedure — Quick Revision

If you need to reproduce this entire lecture practically, follow these steps:

### A. BigQuery Setup

1. Open Google Cloud.
2. Search **BigQuery**.
3. Open **BigQuery Data Warehouse Analytics**.
4. Click **Add**.
5. Select **Local file**.
6. Click **Browse**.
7. Select the **housing CSV file**.
8. Confirm the file format as **CSV**.
9. Select/create a **Dataset**.
10. Provide a **Dataset ID**.
11. Keep the location as **Multi-region** for this demonstration.
12. Click **Create Dataset**.
13. Provide table name:

    > `housing`
14. Select **Auto Detect** for schema.
15. Click **Create Table**.

### B. Verify BigQuery Data

16. Expand the project.
17. Expand the dataset.
18. Locate the `housing` table.
19. Click the table's **three dots**.
20. Open an SQL query.
21. Run a query such as:

```sql
SELECT *
FROM `project.dataset.housing`
LIMIT 1000;
```

22. Check the **Query Results**.

### C. Connect Power BI

23. Open **Power BI Desktop**.
24. Select **Blank Report**.
25. Go to **Transform Data → Data Source Settings**.
26. If BigQuery permissions already exist, you may clear them for troubleshooting/testing.
27. Click **Close & Apply**.
28. Select **Get Data → More**.
29. Search for **BigQuery**.
30. Select **Google BigQuery**.
31. Click **Sign In**.
32. Select the Google account used for BigQuery.
33. Click **Allow**.
34. Return to Power BI.
35. Expand the BigQuery project.
36. Expand the dataset.
37. Select the `housing` table.
38. Wait for the data preview.

### D. Load the Data

39. Choose **Load** if no transformation is required at this stage.
40. Select **Import** connectivity mode.
41. Click **OK**.
42. Wait for the data to load.
43. Open **Table View** to verify the imported records.

---

# Key Interview Takeaway

The instructor highlights that knowing how to connect Power BI to different data sources is valuable from an interview perspective.

A good way to describe this workflow conceptually is:

> **"I can connect Power BI to cloud data sources such as Google BigQuery, navigate through projects, datasets and tables, authenticate using an organizational account, choose an appropriate connectivity mode such as Import or DirectQuery, and load the data into Power BI for reporting."**

The lecture's larger objective is therefore not merely uploading a CSV—it is demonstrating the complete **BigQuery → Power BI data-source integration workflow**. 

### What comes next

The upcoming sessions will move from **connection/setup** into actual **data analysis and transformation**, including BigQuery SQL and Power Query Editor, followed eventually by the Power BI reporting work. 
