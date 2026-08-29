# Power BI Project — Fixing Loss KPIs & Creating the Production Database

This session marks the transition from **report development in the Test environment** to preparing the **Production environment**.

The session has two major parts:

1. **Correct the Total Loss and Average Daily Loss KPIs** so that loss values are displayed as positive numbers.
2. **Create and populate the Production database in SQL Server**, and understand the differences between Test and Production data.

---

# 1. Correcting the Loss KPI Values

In the previous session, the report had two loss-related KPIs:

* **Total Loss**
* **Average Daily Loss / Average Loss per Day**

The problem is that both the **label** and the **value** already communicate that it is a loss.

For example, the Card might show:

```text
Loss
-$579
```

This is somewhat redundant because the negative sign already indicates a loss, while the word **Loss** is already written on the report template.

Therefore, the instructor decides to display the loss amount as a **positive value**.

### Desired result

Instead of:

```text
Loss
-$579
```

the report should show:

```text
Loss
$579
```

---

# 2. Modify the Total Loss Measure

The existing **Total Loss** measure produces a negative number because the calculation is based on:

```text
Availability - Demand
```

For loss situations:

```text
Availability < Demand
```

so:

```text
Availability - Demand < 0
```

Therefore, the resulting loss amount is negative.

Since the report already contains the word **Loss**, the instructor changes the measure to return the positive magnitude of the loss.

---

## Steps

1. Expand the **Data pane**.
2. Expand the **Measures Table**.
3. Locate:

> **Total Loss**

4. Click **Total Loss**.
5. Expand the **Formula bar**.
6. Take the existing Total Loss calculation and multiply the complete expression by:

```text
-1
```

Conceptually:

```DAX
Total Loss =
(
    existing Total Loss calculation
) * -1
```

7. Press **Enter**.
8. Wait for Power BI to apply the change.

The KPI now displays a **positive value**.

---

# 3. Why Multiply Total Loss by -1?

Previously:

```text
Total Loss = -579
```

After multiplying by `-1`:

$$
-579 \times -1 = 579
$$

So:

```text
Before → -579
After  →  579
```

This is a presentation/business-reporting decision.

The word **Loss** is already displayed in the report, so the instructor wants the numerical value to represent the **magnitude of the loss**, rather than showing a negative number.

---

# 4. Average Daily Loss Also Becomes Positive

The second affected KPI is:

> **Average Daily Loss / Average Loss per Day**

Since this measure was originally calculated from **Total Loss**:

```DAX
Average Loss per Day =
DIVIDE(
    [Total Loss],
    [Total Number of Days]
)
```

when `[Total Loss]` becomes positive, the Average Loss per Day also becomes positive automatically.

For example:

```text
Total Loss = -900
Days = 10

Average Loss per Day = -900 / 10
                     = -90
```

After changing Total Loss:

```text
Total Loss = 900

Average Loss per Day = 900 / 10
                     = 90
```

Therefore, there is no need to separately multiply the Average Loss per Day measure by `-1` if it is directly dependent on the corrected Total Loss measure.

---

# 5. Final Loss KPI Presentation

The intended presentation is now:

```text
┌──────────────────────┐
│                      │
│        $579          │
│                      │
│     Total Loss       │
│                      │
└──────────────────────┘
```

rather than:

```text
┌──────────────────────┐
│                      │
│       -$579          │
│                      │
│     Total Loss       │
│                      │
└──────────────────────┘
```

The same principle applies to Average Daily Loss.

---

# 6. Move to SQL Server Management Studio

After correcting the report, the instructor moves to:

> **SQL Server Management Studio (SSMS)**

The purpose is now to create the **Production database**.

The project has so far been developed using data from the **Test environment**.

The next phase is:

```text
Test Environment
       ↓
Production Environment
```

---

# 7. Create the Production Database

The instructor creates a new database called:

> **Prod**

### SQL command

```sql
CREATE DATABASE Prod;
```

### Steps

1. Open **SQL Server Management Studio**.
2. Open a query window.
3. Write:

```sql
CREATE DATABASE Prod;
```

4. Execute the statement.

The transcript mentions using:

> **Shift + Up Arrow**

to select the statement, followed by:

> **Ctrl + E**

to execute it.

The database is successfully created.

---

# 8. Switch to the Production Database

After creating the database, the instructor wants to work inside it.

The command is:

```sql
USE Prod;
```

### Steps

1. Write:

```sql
USE Prod;
```

2. Select the statement.
3. Press:

```text
Ctrl + E
```

4. Execute it.

Now SQL Server is using:

> **Prod**

as the current database.

---

# 9. Refresh the Databases in Object Explorer

The instructor then refreshes the database list so that the newly created `Prod` database becomes visible.

### Steps

1. In **Object Explorer**, right-click:

> **Databases**

2. Select:

> **Refresh**

3. Expand the Databases section.
4. The newly created:

> **Prod**

database appears.

---

# 10. Load the Production Inventory Dataset

The next step is to load the production inventory data into the new database.

The instructor uses SQL Server's:

> **Import Flat File**

feature.

### Steps

1. Right-click the **Prod** database.
2. Select:

> **Tasks**

3. Select:

> **Import Flat File**

A wizard opens.

---

## Select the Production Dataset

The instructor browses to the Desktop and selects:

> **Production Environment Inventory Data Set**

### Steps

1. Click **Browse**.
2. Navigate to the Desktop.
3. Locate:

```text
Production Environment Inventory Data Set
```

4. Double-click the file.
5. Click **Next**.
6. Continue through the wizard by clicking **Next**.
7. Finally, click **Finish**.

The data is successfully loaded into the Production database.

---

# 11. Load the Products Table

The production database also needs the **Products** table.

The instructor repeats the same process.

### Steps

1. Right-click **Prod**.
2. Select:

> **Tasks → Import Flat File**

3. Click **Next**.
4. Click **Browse**.
5. Select the:

> **Products**

table/file.
6. Double-click it.
7. Click **Next**.
8. Continue with **Next**.
9. Click **Finish**.

The Products data is successfully inserted into the Production database.

---

# 12. Close the Import Process

Once the data loading is complete:

1. Click **Close**.

At this point, the Production database contains the required production data.

---

# 13. Verify the Production Data

The instructor then checks the data using a simple SQL query.

First, refresh the database.

### Steps

1. Right-click **Prod**.
2. Click:

> **Refresh**

3. Expand **Prod**.
4. Expand:

> **Tables**

The newly created production inventory table is visible.

The table is referred to as:

> `dbo.prod_environment_inventory_data_set`

---

# 14. Query the Production Inventory Table

The instructor uses:

```sql
SELECT *
FROM dbo.prod_environment_inventory_data_set;
```

This retrieves all records from the Production inventory table.

### Steps

1. Write the `SELECT` statement.
2. Select the statement.
3. Click **Execute** or press:

```text
Ctrl + E
```

The production data appears in the results window.

---

# 15. Compare Test and Production Data Volume

This is one of the most important observations in the session.

The Production environment contains:

> **1,043 records**

Previously, the Test environment contained only:

> **99 records**

So:

```text
Test       → 99 records
Production → 1,043 records
```

This demonstrates that **Test and Production environments can have different data volumes**.

---

# 16. Why Are Test and Production Data Different?

This is common in real-world data projects.

Usually, development begins using a Test/Development environment.

The Test environment may contain:

* Smaller datasets
* Sample data
* Limited historical data
* Data specifically prepared for development/testing

Production generally contains:

* Actual operational data
* Much larger volumes
* More complete historical information
* Real business transactions

Therefore, a report that works with 99 records in Test may eventually need to work with thousands, millions, or even billions of records in Production.

---

# 17. Standard Development Workflow

The instructor highlights a common real-world workflow:

```text
Development / Test
        ↓
Build Report
        ↓
Create DAX Measures
        ↓
Validate Report
        ↓
Move to Production
        ↓
Connect to Production Data
```

The important point is:

> **You normally don't build the entire report again for Production.**

Instead, you develop and validate the report using the Test environment and then move the report to Production by changing the appropriate **data source/settings**.

---

# 18. Data Quality Can Also Differ Between Environments

Another important observation is that data quality can differ between Test and Production.

The instructor mentions that you may encounter certain **data-quality issues in the Test environment** that may not necessarily exist in Production.

For example, Test data may contain:

* Missing values
* Incomplete records
* Sample/test records
* Inconsistent values
* Limited data
* Artificially created scenarios

Production data may have a different quality profile because it comes from the actual operational system.

### Important point

This doesn't mean Production data is always perfect.

Rather:

> **The characteristics and quality of Test and Production data can be different.**

Therefore, data profiling should be performed again when moving to Production.

---

# 19. Production Database Structure

At this stage, the Production database contains at least:

```text
Prod
│
└── Tables
    │
    ├── dbo.prod_environment_inventory_data_set
    │
    └── Products
```

The exact naming depends on how the import wizard created the tables.

---

# 20. Why Are We Creating the Production Database?

The ultimate objective is to take the Power BI report that was developed using Test data and connect it to the Production database.

Instead of rebuilding:

```text
Page 1
Page 2
Cards
DAX measures
Filters
Formatting
```

from scratch, the plan is to **change the data source configuration**.

Conceptually:

```text
CURRENT

Power BI Report
      ↓
Test SQL Server Database
      ↓
Test Data


NEXT

Power BI Report
      ↓
Production SQL Server Database
      ↓
Production Data
```

The report itself should largely remain the same.

---

# 21. Next Step — Profile Production Data

Before changing the Power BI data source, the instructor plans to first understand the Production data.

The next session will focus on:

> **Data profiling and understanding the Production data in SQL Server itself.**

This is important because the Production environment has:

```text
1,043 records
```

compared with only:

```text
99 records
```

in Test.

So the instructor wants to inspect the Production data before connecting the Power BI report to it.

---

# 22. Next Major Phase — Test to Production

After profiling the Production data, the project will begin the actual process of:

# **Shifting the Power BI Report from Test to Production**

The instructor explicitly states that:

> The entire report will **not** be created again.

Instead, the focus will be on:

* Changing the data source
* Updating the data source settings
* Connecting to the Production database
* Understanding Production data
* Checking whether the existing report continues to work
* Understanding the impact on DAX measures

---

# 23. Important DAX Point — Measures vs Data Source

The report's DAX measures were created against the model fields.

For example:

```DAX
Total Demand =
SUM('Demand/Availability Data'[Demand])
```

When moving to Production, the goal is not to rewrite all the DAX measures.

Instead, if the Production source provides the required columns with compatible names/types, the existing model and measures can continue to work after the data source is switched appropriately.

This is why the upcoming migration process is focused on **data source settings**, rather than recreating the entire report.

---

# 24. Overall Project Progress

The project has now reached this stage:

```text
             POWER BI PROJECT
                    │
                    ▼
          Test Environment
                    │
                    ▼
             Data Cleaning
                    │
                    ▼
            DAX Calculations
                    │
                    ▼
              Report Page 1
                    │
                    ▼
              Report Page 2
                    │
                    ▼
             KPI Cards
                    │
                    ▼
             Filters Added
                    │
                    ▼
          Test Report Completed
                    │
                    ▼
       Create Production Database
                    │
                    ▼
        Load Production Data
                    │
                    ▼
       Profile Production Data
                    │
                    ▼
       Change Power BI Data Source
                    │
                    ▼
          Production Report
```

---

# 25. Key Commands From This Session

### Create Production Database

```sql
CREATE DATABASE Prod;
```

### Switch to Production Database

```sql
USE Prod;
```

### View Production Inventory Data

```sql
SELECT *
FROM dbo.prod_environment_inventory_data_set;
```

---

# 26. Important Numbers to Remember

| Environment    | Number of Records |
| -------------- | ----------------: |
| **Test**       |            **99** |
| **Production** |         **1,043** |

This difference is deliberately demonstrated to show that:

> **Production data volume can be significantly larger than Test data volume.**

---

# 27. Important Practical Lessons

### 1. Don't recreate the report for Production

The report is developed once in Test and then migrated.

```text
Build once → Change source → Use Production
```

---

### 2. Test and Production data can differ

The number of rows may be very different.

```text
Test       → 99
Production → 1,043
```

---

### 3. Always understand Production data

Before connecting the report to Production, inspect and profile the Production data.

---

### 4. Data quality may differ

Test and Production may have different data-quality characteristics.

---

### 5. DAX measures depend on the model

The objective is to maintain the existing measures rather than recreate them, provided the Production model remains compatible.

---

### 6. Loss values are now displayed positively

Because the report already labels the KPI as **Loss**, the negative sign is removed from the numerical display by multiplying the Total Loss calculation by `-1`.

---

# 28. Quick Revision

### Report correction

```text
Total Loss
    ↓
Multiply by -1
    ↓
Positive Loss Amount
```

Because:

```text
"Loss" is already displayed as the label.
```

---

### Production database

```sql
CREATE DATABASE Prod;
```

Then:

```sql
USE Prod;
```

---

### Load data

```text
Prod
 ↓
Tasks
 ↓
Import Flat File
 ↓
Production Environment Inventory Data Set
 ↓
Next → Next → Finish
```

Then repeat for:

```text
Products table
```

---

### Validate

```sql
SELECT *
FROM dbo.prod_environment_inventory_data_set;
```

Result:

```text
1,043 records
```

compared with:

```text
99 records in Test
```

---

# 29. Final Takeaway

This session is the **bridge between report development and deployment**.

The report was successfully developed using the Test environment, and now the Production environment has been created and populated.

The major workflow is:

> **Build and test the Power BI report → Create Production database → Load Production data → Profile Production data → Change the Power BI data source → Validate the report in Production.**

The next session will begin with **profiling and understanding the Production data in SQL Server**, after which the actual **Test → Production migration of the Power BI report** will begin.
