# Power BI: Transitioning a Report from SQL Server to MySQL Using Advanced Editor

## 1. Objective of the Session

This is the **main migration step** of the project.

The objective is to transition an existing Power BI report from:

```text
Microsoft SQL Server
        ↓
Power BI Report
```

to:

```text
MySQL Database
        ↓
Same Power BI Report
```

### Most important requirement

We **do not want to recreate the report**.

We want to preserve:

* Existing DAX measures
* DAX calculations
* Visuals
* Report pages
* Formatting
* Existing report logic

Only the **underlying data source** should be changed.

---

# 2. Important Limitation of Data Source Settings

Previously, when moving the report from the **SQL Server test environment → SQL Server production environment**, we used:

**Transform Data → Data Source Settings → Change Source**

That worked because both environments were using the **same database technology: SQL Server**.

For example:

```text
SQL Server Test
      ↓
SQL Server Production
```

The server/database details could simply be changed.

However, when migrating between completely different database systems:

```text
SQL Server
    ↓
MySQL
```

the same **Data Source Settings → Change Source** approach cannot be used to perform the migration.

Instead, the lecture uses:

> **Power Query Editor → Advanced Editor**

---

# 3. Why Advanced Editor Is Required

The reason is that the underlying Power Query/M code describing the connection is different for SQL Server and MySQL.

Conceptually:

```text
SQL Server Connection
        ↓
Power Query M Code
```

is different from:

```text
MySQL Connection
        ↓
Power Query M Code
```

Therefore, we need to replace the SQL Server connection portion of the existing query with the MySQL connection portion.

---

# 4. Open Power Query Editor

In Power BI Desktop:

1. Go to **Home**.
2. Click **Transform Data**.

This opens the **Power Query Editor**.

---

# 5. Identify the MySQL Query

In the previous session, a connection was established between Power BI and MySQL.

That resulted in a query named:

```text
Query 1
```

This query contains the data coming from the MySQL database.

The first step is to rename it to something meaningful.

---

# 6. Rename `Query 1`

### Steps

1. In Power Query Editor, locate **Query 1**.
2. Double-click its name.
3. Rename it to:

```text
MySQL Database
```

4. Press Enter.

This makes the query easier to identify.

---

# 7. Open the MySQL Query's Advanced Editor

Select:

```text
MySQL Database
```

Then go to:

**Home → Advanced Editor**

The Advanced Editor displays the **Power Query M code** responsible for retrieving the MySQL data.

The instructor does not copy the entire code.

Instead, only the **connection/source-related portion** is selected.

---

# 8. Copy the MySQL Connection Code

Inside the Advanced Editor:

1. Identify the portion of the M code that represents the MySQL connection.
2. Highlight the relevant portion shown in the lecture.
3. Press:

```text
Ctrl + C
```

4. Click **Cancel** to close the Advanced Editor.

### Important

The purpose here is to copy the **MySQL source definition**, not to replace the entire query blindly.

---

# 9. Select the Existing SQL Server Query

Now locate:

```text
Demand / Availability Data
```

This is the existing query that was originally created using **Microsoft SQL Server** as its data source.

This is the query we actually want to modify.

### Current situation

```text
Demand / Availability Data
        ↓
Microsoft SQL Server
```

We want:

```text
Demand / Availability Data
        ↓
MySQL
```

---

# 10. Open Advanced Editor for Demand/Availability Data

With **Demand / Availability Data** selected:

1. Go to the **Home** tab.
2. Click **Advanced Editor**.

The Power Query M code for this query will appear.

This code currently contains the SQL Server connection information.

---

# 11. Replace the SQL Server Source with MySQL Source

This is the **most important step of the entire session**.

Inside the Advanced Editor:

1. Locate the SQL Server source/connection portion of the M code.
2. Select the relevant portion.
3. Replace it with the MySQL connection code that you copied earlier.
4. Press:

```text
Ctrl + V
```

The SQL Server connection details are now replaced with MySQL connection details.

---

# 12. What Changes in the Code?

After replacement, the query will now contain MySQL connection information.

The lecture points out that the code now contains details such as:

```text
localhost
prod
```

These represent:

* **`localhost`** → MySQL Server running locally
* **`prod`** → MySQL production database

So the source has effectively changed from:

```text
SQL Server → Production Database
```

to:

```text
MySQL → localhost → prod
```

---

# 13. Click Done

After replacing the source code:

1. Click **Done** in the Advanced Editor.
2. Power Query applies the modified M code.

The existing **Demand/Availability Data** query now retrieves its data from MySQL.

---

# 14. Apply the Changes

After modifying the source:

1. Click the dropdown beside **Close & Apply**.
2. Select **Apply**.

Power BI will refresh/load the data into the model.

The lecture shows:

```text
1043 records loaded
```

This is an important validation point because the production MySQL dataset contains the expected **1,043 records**.

---

# 15. Why `MySQL Database` Query Is No Longer Required

At this point, the existing:

```text
Demand / Availability Data
```

query itself is now connected directly to MySQL.

Therefore, the separate:

```text
MySQL Database
```

query that was created only for testing the MySQL connection is no longer needed.

Originally:

```text
MySQL Database
      ↓
MySQL data
```

was only created to establish and verify the connection.

Now:

```text
Demand / Availability Data
      ↓
MySQL
```

is using that source directly.

---

# 16. Delete the Temporary MySQL Query

### Steps

1. Right-click:

```text
MySQL Database
```

2. Select **Delete**.
3. Confirm the deletion if prompted.

The temporary MySQL query is removed.

### Important distinction

We are **not deleting the MySQL database or MySQL table**.

We are only deleting the temporary **Power Query query** that was created earlier to test/import the MySQL data.

---

# 17. Close & Apply Again

After deleting the temporary query:

1. Select **Demand / Availability Data**.
2. Click **Close & Apply**.

Power BI will apply the final Power Query changes and return to the report view.

---

# 18. Verify the Data Source

Now go back to:

**Transform Data → Data Source Settings**

You should see something representing:

```text
localhost
prod
```

This indicates that the report's query is now using the MySQL database.

Previously, the query was connected to SQL Server.

Now:

```text
localhost + prod
```

represents the MySQL connection.

---

# 19. What Has Actually Been Changed?

The important point is that we **didn't rebuild the report**.

We changed the source of the existing query.

### Before

```text
Demand / Availability Data
          ↓
     SQL Server
          ↓
     Power BI Model
          ↓
    DAX + Visuals
```

### After

```text
Demand / Availability Data
          ↓
        MySQL
          ↓
     Power BI Model
          ↓
    Same DAX + Visuals
```

This is the essence of the migration.

---

# 20. Why Existing DAX Measures Can Continue Working

The report's DAX measures are based on the Power BI model's tables and columns.

Because we preserved the expected table and column structure while creating the MySQL `New_Table`, the existing Power BI model can continue using the same logical fields.

Therefore, the goal is:

```text
Same table structure
       +
Same column names
       +
New data source
       =
Existing DAX/report can be reused
```

This is why the previous sessions focused heavily on making the MySQL table compatible with the SQL Server version.

---

# 21. Important: MySQL → SQL Server Would Require Advanced Editor Again

The lecture makes another important point.

After this migration:

```text
SQL Server → MySQL
```

you cannot simply use Data Source Settings to switch back to SQL Server.

If you want to migrate:

```text
MySQL → SQL Server
```

you would again need to use the **Advanced Editor** to modify the Power Query source definition.

So Advanced Editor is useful when moving between **different types of data sources/database connectors**.

---

# 22. Comparison: Same Database vs Different Database

| Migration                                     | Approach                                                        |
| --------------------------------------------- | --------------------------------------------------------------- |
| SQL Server Test → SQL Server Production       | Data Source Settings                                            |
| SQL Server Production → MySQL                 | Advanced Editor                                                 |
| MySQL environment → another MySQL environment | Data Source Settings can be used for appropriate source changes |
| MySQL → SQL Server                            | Advanced Editor                                                 |

### Key idea

**Same database technology/environment change:**

```text
Data Source Settings
```

**Different database technology:**

```text
Advanced Editor
```

---

# 23. Complete Migration Workflow

The entire project flow can now be understood clearly.

### Phase 1 — SQL Server Test

```text
SQL Server Test
      ↓
Power BI Report
```

### Phase 2 — SQL Server Production

```text
SQL Server Production
      ↓
Prepare/clean data
      ↓
Create New Table
      ↓
Change Data Source Settings
      ↓
Power BI Report
```

### Phase 3 — Prepare MySQL

```text
MySQL
  ↓
Create prod database
  ↓
Import inventory data
  ↓
Clean data
  ↓
Import Products table
  ↓
Create New_Table
```

### Phase 4 — Connect Power BI to MySQL

```text
Power BI
   ↓
Get Data
   ↓
MySQL Database
   ↓
localhost
   ↓
prod
```

### Phase 5 — Migrate Existing Query

```text
Existing SQL Server Query
          ↓
Open Advanced Editor
          ↓
Copy MySQL source code
          ↓
Replace SQL Server source
          ↓
Click Done
          ↓
Apply Changes
```

### Phase 6 — Cleanup

```text
Delete temporary "MySQL Database" query
          ↓
Keep Demand / Availability Data
          ↓
Close & Apply
```

---

# 24. Practical Example of the Concept

Suppose the original Power Query source is conceptually:

```text
SQL Server
   ↓
Database
   ↓
New Table
```

We don't want to change the downstream transformations and report logic.

Instead, we replace only:

```text
SQL Server Source
```

with:

```text
MySQL Source
```

while keeping:

```text
Transformations
Table structure
Column names
DAX
Visuals
```

unchanged wherever possible.

---

# 25. Important Real-World Lesson

In an actual organization, this type of migration can happen when:

* A company changes its database technology.
* Infrastructure is modernized.
* A client migrates from one database platform to another.
* A legacy database is replaced.
* Cloud/on-premises architecture changes.
* Data engineering teams migrate backend systems.

As a Power BI developer/analyst, you may not be responsible for performing the entire backend migration.

Your responsibility may simply be to:

1. Understand the new data source.
2. Verify the data.
3. Update the Power BI connection.
4. Ensure the schema is compatible.
5. Test the report.
6. Validate DAX calculations and visuals.
7. Confirm that refresh works.

---

# 26. Key Points to Remember

### ⭐ 1. Data Source Settings have limitations

They were sufficient for:

```text
SQL Server Test → SQL Server Production
```

but not for directly transitioning:

```text
SQL Server → MySQL
```

---

### ⭐ 2. Advanced Editor is used for the cross-database migration

The Power Query **Advanced Editor** allows us to modify the underlying M code.

---

### ⭐ 3. Don't recreate the report

The goal is:

> **Change the source, not rebuild the report.**

---

### ⭐ 4. Preserve table and column names

This helps protect:

* DAX measures
* DAX calculations
* Visuals
* Existing model logic

---

### ⭐ 5. Temporary queries can be deleted

Once the existing query itself is successfully connected to MySQL, the separate `MySQL Database` query used for testing can be deleted.

---

### ⭐ 6. Validate the record count

The lecture confirms that:

```text
1043 records
```

were loaded after the migration.

This helps verify that the expected production data is being retrieved.

---

# 27. Exact Steps for the Migration

```text
Power BI Desktop
      ↓
Transform Data
      ↓
Power Query Editor
      ↓
Select "Query 1"
      ↓
Rename → "MySQL Database"
      ↓
Home → Advanced Editor
      ↓
Copy MySQL source portion
      ↓
Cancel
      ↓
Select "Demand / Availability Data"
      ↓
Home → Advanced Editor
      ↓
Select SQL Server source portion
      ↓
Paste MySQL source portion
      ↓
Done
      ↓
Apply
      ↓
1043 records loaded
      ↓
Delete temporary "MySQL Database" query
      ↓
Close & Apply
      ↓
Data Source Settings
      ↓
Verify localhost / prod
```

---

# 28. Final Architecture After Migration

The final setup should look conceptually like this:

```text
                    POWER BI
                       │
                       ↓
          Demand / Availability Data
                       │
                       ↓
                Power Query M
                       │
                       ↓
                    MySQL
                       │
                 ┌─────┴─────┐
                 ↓           ↓
              localhost     prod
                               │
                               ↓
                           New_Table
                               │
                               ↓
                         1043 records
```

And the report continues to use its existing:

```text
DAX Measures
     +
Visuals
     +
Report Pages
     +
Formatting
     +
Model Logic
```

---

# 29. One-Line Exam/Interview Explanation

> **To migrate a Power BI report from SQL Server to MySQL without recreating the report, prepare an equivalent MySQL table with the same schema, then use Power Query Editor's Advanced Editor to replace the SQL Server source definition with the MySQL source definition while preserving the existing query structure and column names.**

## Final Takeaway

The biggest lesson from this session is:

**When changing the database technology, don't rebuild the Power BI report. Change the Power Query source definition using the Advanced Editor, while keeping the table/column structure compatible with the existing Power BI model.**
