# Power BI: Data Validation After Migrating SQL Server → MySQL

## 1. Objective of the Session

In the previous sessions, we successfully transitioned the Power BI report from:

```text
Microsoft SQL Server
        ↓
Power BI Report
```

to:

```text
MySQL Database
        ↓
Power BI Report
```

The purpose of this session is to **validate that the migration was successful**.

The key question is:

> **Did the report produce exactly the same results after changing the data source?**

Since the underlying business data and calculations were not intentionally changed, the numbers in the migrated report should match the numbers from the original SQL Server-based report.

---

# 2. Why Data Validation Is Important

Changing a data source can potentially introduce problems.

For example:

* Different records may be loaded.
* Some records may be missing.
* Column mappings may be incorrect.
* Data types may be different.
* Transformations may behave differently.
* SQL logic may have been incorrectly converted.
* DAX measures may return different results.
* Relationships may behave differently.

Therefore, after a migration, we should **compare the old report against the migrated report**.

The basic validation principle is:

```text
Original SQL Server Report
          ↕
     Compare Numbers
          ↕
New MySQL Report
```

If the numbers match, it provides strong evidence that the migration was performed correctly.

---

# 3. Reports Being Compared

There are two versions involved.

### Original report

This was published earlier to the Power BI Service in:

```text
SQL Server Data Source
```

It uses:

```text
SQL Server → Power BI
```

### Migrated report

This is currently open in Power BI Desktop and uses:

```text
MySQL → Power BI
```

The objective is to compare both.

---

# 4. Important Principle

The instructor emphasizes:

> **The data itself did not change. Only the data source changed.**

Therefore:

```text
SQL Server
       ↓
Same Data
       ↓
Power BI

MySQL
       ↓
Same Data
       ↓
Power BI
```

Because the data and report logic are supposed to remain the same, the resulting KPIs should also remain the same.

---

# 5. Open the Original Report in Power BI Service

The first step is to open the original SQL Server-based report that was published earlier.

### Steps

1. Open **Power BI Service**.
2. Go to **Workspaces**.
3. Select:

```text
SQL Server Data Source
```

4. Locate the previously published Power BI report.
5. Open the report.

This is the reference version against which the migrated report will be validated.

---

# 6. Validate Page 1

The instructor compares the KPI values shown in Power BI Service with the values shown in Power BI Desktop.

### KPI 1 — Average Demand per Day

Power BI Service shows:

```text
48.65
```

Power BI Desktop shows:

```text
48.65
```

### Result

✅ Values match.

---

# 7. Validate the Other Page 1 KPIs

The next values shown in the report are:

```text
24.70
61K
```

The Power BI Desktop report also shows:

```text
24.70
61K
```

Therefore:

```text
Power BI Service     Power BI Desktop
      24.70    =          24.70
      61K      =          61K
```

### Result

✅ Values match.

---

# 8. Validate Page 2

The instructor then moves to **Page 2** and validates the KPIs there as well.

The following values are compared.

---

## Total Profit

Power BI Service:

```text
301K
```

Power BI Desktop:

```text
301K
```

✅ Match.

---

## Total Loss

Power BI Service:

```text
8 Million
```

Power BI Desktop:

```text
8 Million
```

✅ Match.

---

## Average Daily Loss

Power BI Service:

```text
2.97K
```

Power BI Desktop:

```text
2.97K
```

✅ Match.

---

# 9. Validation Results

All the compared KPIs match between the two versions.

| KPI                    | SQL Server Report | MySQL Report | Result  |
| ---------------------- | ----------------: | -----------: | ------- |
| Average Demand per Day |             48.65 |        48.65 | ✅ Match |
| KPI 2                  |             24.70 |        24.70 | ✅ Match |
| KPI 3                  |               61K |          61K | ✅ Match |
| Total Profit           |              301K |         301K | ✅ Match |
| Total Loss             |                8M |           8M | ✅ Match |
| Average Daily Loss     |             2.97K |        2.97K | ✅ Match |

Therefore, the migration appears to have been successful.

---

# 10. What Does Matching Data Tell Us?

Since the numbers match, we have evidence that:

* The MySQL data was loaded correctly.
* The required transformations were preserved.
* The table structure is compatible.
* The DAX measures are producing the expected results.
* The report visuals are displaying the expected values.
* The SQL Server → MySQL transition was successful.

The important point is that we didn't recreate the report.

Instead:

```text
Same Power BI Report
        ↓
Different Data Source
        ↓
Same Results
```

---

# 11. Why This Can Be an Interview Question

The instructor specifically mentions that this type of scenario can appear in a **Power BI interview**.

A potential interview question could be:

> **How would you migrate an existing Power BI report from SQL Server to MySQL without recreating the report?**

A good answer would be:

1. Prepare equivalent data in MySQL.
2. Ensure table and column names are compatible.
3. Establish a MySQL connection in Power BI.
4. Use Power Query's **Advanced Editor** to replace the SQL Server source definition with the MySQL source definition.
5. Apply the changes.
6. Validate the migrated report against the original report.
7. Compare important KPIs and ensure they match.
8. Publish the validated report to the appropriate Power BI workspace.

---

# 12. Real-World Example: MySQL → PostgreSQL

The instructor gives a real-world example from a friend's experience.

Initially, the client was using:

```text
MySQL
```

as the data source.

Later, because of **cost-related considerations**, the client decided to move to:

```text
PostgreSQL
```

Therefore, the report/data source migration required adapting the SQL/query logic to the syntax supported by PostgreSQL.

The same general principle applies:

```text
Existing Database
       ↓
Database Migration
       ↓
New Database
       ↓
Adapt SQL/Power Query logic
       ↓
Validate Report
```

---

# 13. General Lesson About Database Migration

The example demonstrates that this isn't limited to:

```text
SQL Server → MySQL
```

The same type of situation can occur with:

```text
MySQL → PostgreSQL
```

or other database technologies.

Whenever the underlying database changes, you may need to modify:

* SQL queries
* Power Query M code
* Connection details
* Table references
* Column references
* Database-specific syntax
* Data type handling

But the objective remains:

> **Preserve the existing reporting logic wherever possible.**

---

# 14. Publish the Migrated Report to the MySQL Workspace

After validating the migrated report, the instructor publishes it to the separate MySQL workspace.

The workspace created earlier was:

```text
MySQL Database Data Source
```

This keeps the migrated version separate from the original SQL Server version.

---

# 15. Publishing Steps

From **Power BI Desktop**:

1. Make sure the latest migrated report is open.
2. Go to the **Home** tab.
3. Click **Publish**.

Power BI will take some time to display the available workspaces.

---

# 16. Select the MySQL Workspace

From the workspace list, select:

```text
MySQL Database Data Source
```

Then click:

**Select**

Power BI begins publishing the report.

The publishing process may take some time.

---

# 17. Open the Published MySQL Report

After publishing:

1. Open the published Power BI report.
2. The report is now available in the:

```text
MySQL Database Data Source
```

workspace.

The instructor refers to the published Power BI report/PBIX report in the workspace.

---

# 18. Final Workspace Structure

At the end of the exercise, there are two separate versions.

```text
POWER BI SERVICE
│
├── SQL Server Data Source
│      │
│      └── Original SQL Server Report
│
└── MySQL Database Data Source
       │
       └── Migrated MySQL Report
```

This is a good practice because the original version remains available for reference and rollback purposes.

---

# 19. Complete Migration Lifecycle

The entire project can now be summarized as follows:

```text
STEP 1
SQL Server Test Environment
        ↓
Create Power BI Report
        ↓

STEP 2
SQL Server Production Environment
        ↓
Prepare/Clean Production Data
        ↓
Create New Table
        ↓
Change Data Source Settings
        ↓

STEP 3
Create MySQL Database
        ↓
Import Production Data
        ↓
Clean/Transform Data
        ↓
Import Products Table
        ↓
Create New_Table
        ↓

STEP 4
Connect Power BI to MySQL
        ↓
Verify MySQL Data
        ↓

STEP 5
Power Query Editor
        ↓
Advanced Editor
        ↓
Replace SQL Server Source
        ↓
MySQL Source
        ↓

STEP 6
Apply Changes
        ↓
1043 records loaded
        ↓

STEP 7
Delete Temporary MySQL Query
        ↓

STEP 8
Validate KPIs
        ↓
Compare SQL Server Report
        ↕
Compare MySQL Report
        ↓

STEP 9
Numbers Match
        ↓

STEP 10
Publish Migrated Report
        ↓
MySQL Database Data Source Workspace
```

---

# 20. Data Validation Checklist

After a database migration, don't simply check one number and assume everything is correct.

A useful validation checklist is:

### Data-level validation

* [ ] Record count matches
* [ ] Required columns exist
* [ ] Column names are correct
* [ ] Data types are appropriate
* [ ] Null/blank values are checked
* [ ] Duplicate records are checked
* [ ] Join results are correct

### Power BI model validation

* [ ] Tables are loaded
* [ ] Relationships are correct
* [ ] DAX measures work
* [ ] Calculated columns work
* [ ] Filters work
* [ ] Slicers work

### Report validation

* [ ] KPI values match
* [ ] Charts show expected values
* [ ] Totals match
* [ ] Page-level calculations match
* [ ] Formatting remains intact

### Refresh validation

* [ ] Data refresh works
* [ ] No connection errors
* [ ] No query errors
* [ ] No credential errors

---

# 21. Why KPI Comparison Is Useful

KPI comparison is particularly useful because a single visual can depend on several layers of the Power BI solution.

For example:

```text
Database
   ↓
SQL Query / Power Query
   ↓
Power BI Model
   ↓
DAX Measure
   ↓
Visual
   ↓
KPI
```

If the KPI matches between the old and new versions, it gives us confidence that the entire chain is behaving as expected.

However, in a real production migration, **KPI comparison should be combined with deeper data/model validation**, rather than being the only test.

---

# 22. Key Interview Answer

### Question:

**How do you validate a Power BI report after migrating its data source from SQL Server to MySQL?**

### Answer:

> First, I would preserve the original SQL Server-based report as a reference. After migrating the Power Query source to MySQL, I would validate record counts, schema, data types, nulls, joins, relationships, and important DAX measures. I would then compare key KPIs and report outputs between the original SQL Server report and the migrated MySQL report. Finally, I would test refresh and publish the validated report to the new workspace.

---

# 23. Most Important Concepts From This Session

### ⭐ 1. Migration isn't complete until validation is done

```text
Migration
   ≠
Successful migration
```

until the migrated report has been tested.

---

### ⭐ 2. Compare the old and new reports

```text
SQL Server Report
       ↕
   Validation
       ↕
MySQL Report
```

---

### ⭐ 3. The numbers should remain unchanged

Because the intended change was only:

```text
Data Source
```

not:

```text
Business Logic
```

---

### ⭐ 4. Keep the original report

The SQL Server workspace provides a safe reference version.

---

### ⭐ 5. Publish the migrated report separately

The MySQL version goes into:

```text
MySQL Database Data Source
```

---

### ⭐ 6. Database migrations are common in real projects

The same approach can be applied when migrating between other database systems, such as:

```text
MySQL → PostgreSQL
SQL Server → MySQL
SQL Server → PostgreSQL
etc.
```

The exact SQL/M code changes depend on the databases involved.

---

# 24. Final Takeaway

The complete lesson is:

> **Changing the Power BI data source is only half of the migration. After transitioning from SQL Server to MySQL using Power Query's Advanced Editor, you must validate the migrated report against the original report. Compare record counts, data, DAX measures, KPIs, and visuals. Once the results match and refresh works correctly, publish the migrated report to its dedicated MySQL workspace.**

In this exercise, the validation was successful because the key KPIs matched:

**48.65, 24.70, 61K, 301K, 8M, and 2.97K.**

Therefore, the SQL Server → MySQL Power BI report migration was successfully validated.
