# Google BigQuery SQL — Data Profiling, Cleaning & Transformation

## 1. Objective of the Session

This session focuses on using **SQL within Google BigQuery** to:

* Understand/profile the data
* Perform data cleaning
* Perform data transformations
* Update existing data
* Prepare data before connecting it to Power BI

The instructor emphasizes that **understanding the data is extremely important in any reporting or data analytics project**. The better you understand the data, the easier it becomes to build meaningful stories and insights from it. 

---

# 2. Where Can Data Cleaning Be Performed?

There are two major places where data cleaning and transformation can be performed in this project.

### Option 1 — Power Query Editor

You can bring the data into Power BI and perform transformations using:

> **Power Query Editor**

### Option 2 — At the Data Source Using SQL

Since the project's data source is **Google BigQuery**, you can perform transformations directly in BigQuery using:

> **SQL**

The workflow can therefore be:

```text
Source Data
    ↓
Google BigQuery
    ↓
SQL Transformations / Cleaning
    ↓
Power BI
    ↓
Reporting
```

Alternatively:

```text
Source Data
    ↓
Google BigQuery
    ↓
Power BI
    ↓
Power Query Editor
    ↓
Reporting
```

The instructor states that, although SQL is demonstrated in this session, the project will **majorly focus on Power Query Editor** for data cleaning. 

---

# 3. Fundamental Data Analytics / Reporting Workflow

One of the most important conceptual points in the lecture is that the **fundamentals of a data analytics project remain the same regardless of the data source**.

A typical project follows this sequence:

```text
Extract Data
     ↓
Clean Data
     ↓
Transform Data
     ↓
Model Data
     ↓
Create Report
     ↓
Share Report / Dashboard
```

### Step-by-step understanding

### 1. Extract

Get data from one or multiple sources.

```text
Source → Data
```

There can be:

* A single data source
* Multiple data sources

### 2. Clean

Handle issues in the raw data.

### 3. Transform

Modify the data into a form suitable for analysis.

### 4. Model

Create the appropriate data model and relationships.

### 5. Report

Build visualizations and dashboards.

### 6. Share

Share the resulting reports/dashboards with:

* Colleagues
* Managers
* Clients
* Other stakeholders

The instructor emphasizes that these fundamentals remain the same even when the underlying data source changes. 

---

# 4. BigQuery SQL — Starting Point

The instructor starts with the same basic `SELECT` statement used in the previous session.

The query essentially retrieves all columns from the `housing` table:

```sql
SELECT *
FROM `project.dataset.housing`;
```

The instructor executes the query and opens the **Results** section to view the data. 

The purpose at this stage is simply to inspect the existing data.

---

# 5. Why Create a Test Table?

The instructor wants to demonstrate data transformation and updating without modifying the original `housing` table.

Therefore, a **copy of the original table** is created.

The copied table is called:

> `test`

This allows the instructor to safely experiment with changes.

Conceptually:

```text
Original Table
housing
   │
   │ Copy
   ↓
Test Table
test
```

The instructor explains that the new table will be created in the **same project and same dataset** as the original table. 

---

# 6. Create a Copy of the Housing Table

The instructor uses:

> `CREATE TABLE`

and copies all the records from the existing `housing` table.

The query follows this pattern:

```sql
CREATE TABLE `project.dataset.test` AS
SELECT *
FROM `project.dataset.housing`;
```

### What this does

* Creates a new table called `test`
* Copies all columns
* Copies all rows from `housing`
* Places the new table in the same project/dataset specified in the query

The instructor executes the statement and confirms that a new table named **test** has been created. 

---

# 7. Verify the New Test Table

After creating the table, the instructor checks the Explorer pane.

The project now contains:

```text
Project
  └── Dataset
       ├── housing
       └── test
```

The `test` table is therefore a replica/copy of the original `housing` table.

---

# 8. View Data from the Test Table

To confirm that the copied table contains the expected data, the instructor runs a simple `SELECT` query.

```sql
SELECT *
FROM `project.dataset.test`
LIMIT 1000;
```

### Executing the query

There are two ways demonstrated:

### Method 1 — Run Button

1. Select/highlight the SQL statement.
2. Click the **Run** button.

### Method 2 — Keyboard Shortcut

1. Select/highlight the SQL statement.
2. Press:

> **Ctrl + Enter**

The query results display the data from the `test` table. 

The instructor confirms that this data is a replica of the data in the original `housing` table.

---

# 9. Use SQL to Understand the Data

The instructor then demonstrates that SQL isn't only useful for modifying data.

It can also be used for **data profiling and data understanding**.

For example, suppose we want to understand:

> **What is the average purchase price for each sales type?**

This can be answered using SQL.

---

# 10. Calculate Average Purchase Price by Sales Type

The instructor uses:

* `SELECT`
* `AVG()`
* `GROUP BY`

The query follows this structure:

```sql
SELECT
    sales_type,
    AVG(purchase_price)
FROM `project.dataset.test`
GROUP BY sales_type;
```

### What is happening?

### `sales_type`

This identifies the different sales categories.

### `AVG(purchase_price)`

Calculates the average purchase price.

### `GROUP BY sales_type`

Calculates the average separately for each sales type.

Conceptually:

```text
Sales Type A → Average Purchase Price
Sales Type B → Average Purchase Price
Sales Type C → Average Purchase Price
...
```

This is an example of using SQL to **understand the characteristics of the dataset before building a report**. 

---

# 11. IntelliSense in BigQuery

While writing the SQL query, the instructor points out that BigQuery provides **IntelliSense/autocomplete**.

For example, when typing the first few characters of a column name, BigQuery suggests possible column names.

So when typing something like:

```text
sales...
```

BigQuery can suggest:

> `sales_type`

This makes writing SQL queries easier and reduces typing errors. 

---

# 12. Why Such Queries Are Useful

Queries like the average purchase price by sales type can help you:

* Understand the dataset
* Identify patterns
* Explore different categories
* Determine useful business metrics
* Prepare for reporting

The instructor's key point is that **SQL can be used as a data-understanding/data-profiling tool**, not just as a data extraction language. 

---

# Part 2 — Updating Data Using BigQuery SQL

## 13. Modify the Test Table

After profiling the data, the instructor demonstrates how SQL can be used to **modify/update records**.

The example focuses on:

* `SQL` column — represents the **area of the house in square metres**
* `no_rooms` — represents the **number of rooms**

The requirement is:

> Wherever the number of rooms is equal to **3**, change the area (`SQL`) to **100**.

In other words:

```text
IF no_rooms = 3
        ↓
Set SQL = 100
```

This update is performed on the **test table**, not the original `housing` table. 

---

# 14. UPDATE Statement

The instructor uses the SQL `UPDATE` statement.

The general structure is:

```sql
UPDATE `project.dataset.test`
SET SQL = 100
WHERE no_rooms = 3;
```

### Breakdown

### `UPDATE`

Specifies that existing records need to be modified.

### Table name

Specifies the table that should be modified.

In this example:

> `test`

### `SET`

Specifies the column and new value.

```sql
SET SQL = 100
```

### `WHERE`

Specifies which records should be changed.

```sql
WHERE no_rooms = 3
```

Therefore, **only records where the number of rooms is 3 are affected**. 

---

# 15. Selecting the Column Using IntelliSense

While writing the `UPDATE` statement, the instructor types the column name and uses the suggestion/IntelliSense functionality.

For example:

```text
SQL
```

and then uses the suggested column.

This helps select the correct field from the table.

---

# 16. Execute the UPDATE

Once the statement is written:

1. Select the `UPDATE` statement.
2. Press:

> **Ctrl + Enter**

The instructor then checks the result of the operation.

BigQuery reports that:

> **19,014 records were impacted**

This means 19,014 records satisfied:

```sql
no_rooms = 3
```

and were therefore updated. 

---

# 17. Verify the UPDATE

It is important to verify whether the update actually worked.

The instructor writes a `SELECT` query to retrieve the `SQL` column for records where the number of rooms equals 3.

The query follows this pattern:

```sql
SELECT SQL
FROM `project.dataset.test`
WHERE no_rooms = 3;
```

Then the query is executed.

### Result

The instructor observes that the `SQL` value is:

> **100**

for the relevant records.

This confirms that the update was successful. 

---

# 18. Verify Using DISTINCT

The instructor goes one step further and checks the **distinct values** of the `SQL` column for records having three rooms.

The query follows this pattern:

```sql
SELECT DISTINCT SQL
FROM `project.dataset.test`
WHERE no_rooms = 3;
```

### Result

Only one value is returned:

> **100**

This provides additional confirmation that the update was successfully applied to all records satisfying the condition. 

---

# 19. What We Learned from the UPDATE Example

The example demonstrates that BigQuery SQL can be used to:

* Select data
* Analyze data
* Profile data
* Group data
* Calculate aggregate metrics
* Modify existing records
* Apply conditional updates
* Verify changes

The basic pattern is:

```text
Identify records
      ↓
Apply condition
      ↓
Update selected column
      ↓
Verify the change
```

---

# Part 3 — SQL vs Power Query Editor

## 20. SQL Can Be Used for Data Transformations

The instructor reiterates that SQL can be used directly in BigQuery for:

* Data transformations
* Data cleaning
* Data understanding
* Data profiling
* Updating data

The transformed data can then be connected to Power BI for reporting. 

---

# 21. Power Query Editor Will Be the Major Focus

Even though SQL is demonstrated, the instructor clarifies that this particular course/project focuses heavily on **Power Query Editor** because the course is primarily about Power BI.

Therefore, the project will cover:

> **Power Query Editor → Data Cleaning → Data Profiling → Reporting**

SQL is being demonstrated mainly to show that **data transformation can also be performed at the source level**. 

---

# 22. SQL for Data Profiling

The instructor mentions that there are dedicated projects elsewhere in the course that cover SQL-based data profiling and transformation in greater depth.

Those projects use other data sources such as:

* Microsoft SQL Server
* MySQL Workbench

There, SQL is used extensively for:

* Data profiling
* Data transformation
* Data cleaning
* Preparing data for reporting



---

# 23. SQL Syntax Depends on the Data Source

A very important concept is:

> **The fundamentals of SQL remain similar, but the syntax can vary depending on the database/data source.**

For example, SQL can be used with:

* Google BigQuery
* Snowflake
* Microsoft SQL Server
* MySQL Workbench

However, there can be differences in SQL syntax and supported functionality between these platforms. 

### Important distinction

Don't think:

> "BigQuery SQL is completely different from SQL Server SQL."

Instead, understand that:

```text
SQL Fundamentals
       ↓
Mostly Common
       ↓
Platform-specific Syntax / Features
       ↓
BigQuery / Snowflake / SQL Server / MySQL
```

The **concepts and fundamentals remain largely the same**, while the exact syntax may differ.

---

# 24. End-to-End Understanding

The lecture's overall message can be summarized as:

```text
              DATA SOURCE
                  ↓
          Google BigQuery
                  ↓
        ┌─────────┴─────────┐
        ↓                   ↓
   BigQuery SQL       Power Query Editor
        ↓                   ↓
 Data Profiling       Data Cleaning
 Data Cleaning        Transformations
 Transformations            ↓
        └─────────┬─────────┘
                  ↓
             Data Model
                  ↓
             Power BI
                  ↓
               Report
                  ↓
         Share with Stakeholders
```

---

# Important SQL Queries from the Lecture

## 1. View all data

```sql
SELECT *
FROM `project.dataset.housing`;
```

---

## 2. Create a copy of the table

```sql
CREATE TABLE `project.dataset.test` AS
SELECT *
FROM `project.dataset.housing`;
```

---

## 3. View the copied table

```sql
SELECT *
FROM `project.dataset.test`
LIMIT 1000;
```

---

## 4. Average purchase price by sales type

```sql
SELECT
    sales_type,
    AVG(purchase_price)
FROM `project.dataset.test`
GROUP BY sales_type;
```

---

## 5. Update area for houses having 3 rooms

```sql
UPDATE `project.dataset.test`
SET SQL = 100
WHERE no_rooms = 3;
```

---

## 6. Verify the updated values

```sql
SELECT SQL
FROM `project.dataset.test`
WHERE no_rooms = 3;
```

---

## 7. Check distinct updated values

```sql
SELECT DISTINCT SQL
FROM `project.dataset.test`
WHERE no_rooms = 3;
```

---

# Practical Steps — Quick Revision

If you want to reproduce everything demonstrated in this lecture:

### Step 1 — Open BigQuery

Go to your Google Cloud project and open **BigQuery**.

### Step 2 — View the Original Table

Run:

```sql
SELECT *
FROM `project.dataset.housing`;
```

### Step 3 — Create a Test Copy

Run:

```sql
CREATE TABLE `project.dataset.test` AS
SELECT *
FROM `project.dataset.housing`;
```

### Step 4 — Verify the Copy

Run:

```sql
SELECT *
FROM `project.dataset.test`
LIMIT 1000;
```

### Step 5 — Profile the Data

Calculate average purchase price by sales type:

```sql
SELECT
    sales_type,
    AVG(purchase_price)
FROM `project.dataset.test`
GROUP BY sales_type;
```

### Step 6 — Perform an Update

Set area to 100 for houses with three rooms:

```sql
UPDATE `project.dataset.test`
SET SQL = 100
WHERE no_rooms = 3;
```

### Step 7 — Check Number of Records Affected

BigQuery reports the number of records impacted. In the lecture, **19,014 records** were affected. 

### Step 8 — Verify the Update

```sql
SELECT SQL
FROM `project.dataset.test`
WHERE no_rooms = 3;
```

### Step 9 — Verify Distinct Values

```sql
SELECT DISTINCT SQL
FROM `project.dataset.test`
WHERE no_rooms = 3;
```

The result should show `100` for the demonstrated test data.

---

# Key Takeaways

1. **Understanding the data is critical** before creating a Power BI report because better data understanding leads to better storytelling and insights. 
2. Data cleaning can be performed in **Power Query Editor** or directly at the source using **SQL**.
3. BigQuery supports SQL for **data profiling, querying, cleaning, transformation, and updates**.
4. A **test table** can be created to safely experiment with transformations without modifying the original table.
5. `GROUP BY` + aggregate functions such as `AVG()` can be used to understand the data.
6. `UPDATE ... SET ... WHERE` can be used to modify selected records.
7. Always **verify transformations after making changes**.
8. SQL fundamentals remain broadly similar across database platforms, but **syntax can differ**.
9. The major focus of this Power BI project will still be **Power Query Editor** for data cleaning and transformation.
10. The complete analytics workflow remains:

```text
Extract → Clean → Transform → Model → Report → Share
```

This session therefore establishes an important idea: **you don't necessarily have to wait until the data reaches Power BI to clean or transform it—you can perform transformations at the source itself using BigQuery SQL and then connect the prepared data to Power BI.** 
