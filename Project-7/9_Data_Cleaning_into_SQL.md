# Power BI: Transitioning a Report from Test to Production Environment

## 1. Objective of the Session

The main objective of this session is to understand **how to move an existing Power BI report from a Test environment to a Production environment without recreating the report**.

The approach is:

**Test SQL Server Database → Production SQL Server Database → Change Power BI Data Source → Refresh Report**

The existing Power BI report, including its visuals, relationships, and DAX measures, should continue to work as long as the **table names and column names remain consistent** between the two environments.

---

# 2. First Step: Validate Production Data in SQL Server

Before moving the Power BI report to Production, we should first understand and validate the data available in the Production database.

The Production environment already contains the inventory table.

### Why validate the Production data?

The data in Test and Production environments may differ in:

* Number of records
* Number of distinct values
* Data quality
* Missing values
* Newly introduced values
* Data inconsistencies

Therefore, **never assume that Production data is exactly the same as Test data**.

---

# 3. Compare Test and Production Data Volumes

In the Test environment, the inventory table contained approximately:

**99 records**

In the Production environment, the same type of table contains:

**1,043 records**

So:

> Test and Production can have significantly different data volumes.

This is completely normal in real-world projects.

### Important point

Data quality issues can also be different between the two environments.

For example:

* An issue may exist in Test but not Production.
* An issue may exist in Production but not Test.
* Production may contain newer records that haven't yet appeared in Test.

Therefore, Production needs to be validated separately before deploying the report.

---

# 4. Check Distinct Order Dates

One of the first data-quality checks performed was checking the distinct values of the `OrderDate` column.

### SQL

```sql
SELECT DISTINCT OrderDate
FROM dbo.ProductInventoryEnvironmentInventoryDataSet;
```

The result showed:

**822 distinct Order Dates**

This tells us how many unique dates are present in the dataset.

---

# 5. Check for NULL or Blank Order Dates

Simply checking distinct values is not enough.

We should also check whether `OrderDate` contains:

* `NULL`
* Blank/empty values

### SQL

```sql
SELECT *
FROM dbo.ProductInventoryEnvironmentInventoryDataSet
WHERE OrderDate IS NULL
   OR OrderDate = '';
```

### Result

No records were returned.

Therefore:

> There are no NULL or blank values in the `OrderDate` column.

This is a positive data-quality result.

---

# 6. Important Data Quality Principle

Before moving a Power BI report from Test to Production:

> **Always validate the Production data.**

Do not assume that because the Test data was clean, Production will also be clean.

Production may contain:

* More records
* New products
* Missing values
* Invalid IDs
* Duplicate records
* Unexpected categories
* Different business scenarios

---

# 7. Check Distinct Product IDs

Next, the `ProductID` column was analyzed.

### SQL

```sql
SELECT DISTINCT ProductID
FROM dbo.ProductInventoryEnvironmentInventoryDataSet;
```

The Production inventory table contained:

**22 distinct Product IDs**

However, the Product table/dimension contained information for only:

**20 products**

This immediately indicates a potential data-quality/data-model problem.

---

# 8. The Product ID Mismatch Problem

The Production inventory table contained:

```text
Product IDs → 1, 2, 3, ..., 20, 21, 22
```

But the Product dimension table contained only:

```text
Product IDs → 1, 2, 3, ..., 20
```

Therefore:

**Product IDs 21 and 22 exist in the inventory/fact table but do not exist in the Product dimension table.**

This is a classic type of issue that can occur when working with fact and dimension tables.

---

# 9. Why Can This Happen in Real Projects?

The lecture assumes that:

* The Production inventory table is maintained by one team.
* The Product table is maintained by another team.
* The inventory table contains the latest data.
* The Product table may take another week or 10 days to get updated.

The data engineering team was expected to communicate this change but did not.

As a result, the Power BI developer discovered the inconsistency during data validation.

### Real-world lesson

If you find:

> A value exists in a fact table but does not exist in the corresponding dimension table,

you should investigate it with the team responsible for maintaining the data.

---

# 10. Communicating Data Issues

If such an issue is discovered, the developer should raise it with the responsible team.

For example, you may send an email to the data engineering team and keep:

* Your manager
* Their manager
* Other relevant stakeholders

in the communication loop when appropriate.

### Why?

Because later you could be asked:

> "Why is this product present in the fact table but missing from the Product dimension?"

You need to have documented the issue and your communication regarding it.

---

# 11. Business Explanation for Product IDs 21 and 22

After discussing the issue with the data engineering team, they clarified that:

| Production Product ID | Actually Represents |
| --------------------: | ------------------: |
|                    21 |        Product ID 7 |
|                    22 |       Product ID 11 |

They also informed the developer that they would fix the underlying issue within approximately a week.

However, the Power BI report was required **immediately**.

Therefore, a temporary data-cleaning transformation was required in Production.

---

# 12. Fixing the Product ID Issue in SQL Server

The solution was to update the Production inventory table.

We need to:

```text
21 → 7
22 → 11
```

This makes the Product IDs consistent with the Product dimension.

---

## 13. Update Product ID 21 → 7

### SQL

```sql
UPDATE dbo.ProductInventoryEnvironmentInventoryDataSet
SET ProductID = 7
WHERE ProductID = 21;
```

This replaces every occurrence of Product ID `21` with Product ID `7`.

The execution affected:

**37 records**

---

# 14. Update Product ID 22 → 11

### SQL

```sql
UPDATE dbo.ProductInventoryEnvironmentInventoryDataSet
SET ProductID = 11
WHERE ProductID = 22;
```

This replaces every occurrence of Product ID `22` with Product ID `11`.

The execution affected:

**51 records**

---

# 15. Verify the Data After the Update

After performing the updates, run:

```sql
SELECT DISTINCT ProductID
FROM dbo.ProductInventoryEnvironmentInventoryDataSet
ORDER BY ProductID;
```

### Result

There are now:

**20 distinct Product IDs**

ranging from:

```text
1 → 20
```

Therefore, Product IDs 21 and 22 have been successfully removed from the Production inventory data.

---

# 16. Key Data Engineering Principle

A very important principle from this lecture is:

> **Clean, prepare, and structure the data at the source itself as much as possible.**

In this case, the transformation was performed in SQL Server rather than bringing the problematic data into Power BI and fixing it there.

### Preferred approach

```text
Source
  ↓
Data Cleaning / Transformation
  ↓
Clean Data
  ↓
Power BI
```

Rather than:

```text
Source
  ↓
Power BI
  ↓
Fix everything inside Power BI
```

The goal should be to bring the **cleanest possible data into Power BI**.

---

# 17. Check Availability Column

The same validation process can be applied to other columns.

For example, check distinct values of `Availability`.

### SQL

```sql
SELECT DISTINCT Availability
FROM dbo.ProductInventoryEnvironmentInventoryDataSet;
```

The result contained:

**121 distinct values**

The values were inspected and no obvious blank or NULL values were found.

---

# 18. Check Demand Column

Similarly, check the `Demand` column.

### SQL

```sql
SELECT DISTINCT Demand
FROM dbo.ProductInventoryEnvironmentInventoryDataSet;
```

Again, there were:

**121 distinct values**

The values were inspected and no obvious blank or NULL values were identified.

---

## 19. More Direct NULL/Blank Checks

Instead of manually looking through the distinct values, you can explicitly check for NULL or blank values.

### Demand

```sql
SELECT *
FROM dbo.ProductInventoryEnvironmentInventoryDataSet
WHERE Demand IS NULL
   OR Demand = '';
```

The same approach can be applied to other columns.

For example:

```sql
SELECT *
FROM dbo.ProductInventoryEnvironmentInventoryDataSet
WHERE Availability IS NULL
   OR Availability = '';
```

### General rule

For important columns, check for:

* NULL
* Blank values
* Invalid values
* Unexpected values
* Duplicate values where applicable
* Referential integrity problems

---

# 20. Create the Production Version of the New Table

In the Test environment, a new table had already been created using a query involving a **LEFT JOIN**.

Now the same table needs to be created in Production.

### Important

We do **not** recreate the logic from scratch.

Instead:

1. Copy the SQL code used in Test.
2. Change the source table from Test to Production.
3. Execute the same logic in the Production database.

---

# 21. Create the New Table in Production

The lecture uses a `SELECT INTO` approach.

Conceptually:

```sql
SELECT *
INTO NewTable
FROM ...
LEFT JOIN ...
```

The exact query contains the previously developed LEFT JOIN logic.

The important difference is that the source inventory table should now be the **Production inventory table**.

---

# 22. Important Environment Check

Before executing the query, make sure:

> **Production database/environment is selected in SQL Server.**

The new table should be created in Production.

The table name should remain:

```text
New Table
```

The Production source table should replace the Test source table.

After executing the query:

**1,043 records** were created/impacted.

---

# 23. Why Table and Column Names Must Remain the Same

This is one of the most important points when transitioning Power BI between environments.

Suppose Test contains:

```text
New Table
```

and Production contains:

```text
New Table
```

This is good.

But if Production instead contained:

```text
Production New Table
```

then Power BI's existing DAX expressions and other model references could potentially be impacted.

The same applies to **column names**.

### Therefore:

When moving between environments:

> **Table names and column names should remain consistent.**

---

# 24. Why Does This Matter for DAX?

Power BI measures often directly reference table and column names.

For example:

```DAX
Total Sales =
SUM('New Table'[Sales])
```

If the Production table were renamed:

```text
Production New Table
```

the existing DAX expression would no longer point to the expected table.

Similarly, changing:

```text
Sales
```

to:

```text
Sales Amount
```

could break existing DAX expressions.

Therefore, consistency is extremely important.

---

# 25. Transitioning the Power BI Report

Once the Production database and tables are ready, we can move the Power BI report from Test to Production.

### Important:

**We do NOT recreate the Power BI report.**

We already have:

* Visuals
* DAX measures
* Relationships
* Formatting
* Report pages
* KPIs

All of this remains intact.

We simply change the **data source/database**.

---

# 26. Change the Data Source in Power BI Desktop

Open the existing Power BI report.

### Step 1: Open Data Source Settings

In Power BI Desktop:

**Home → Transform Data → Data Source Settings**

Depending on the interface, Data Source Settings can also be accessed through Power Query.

---

# 27. Change Test Database to Production

In Data Source Settings:

1. Select the existing SQL Server source.
2. Click **Change Source**.
3. The current database will be the Test environment.
4. Replace the Test database name with the Production database name.

In the lecture, the Production database is:

```text
prod
```

### Important

The following remain unchanged:

* SQL Server/server details
* Query logic
* Table name

Only the **database/environment** changes.

---

# 28. Existing Query Remains the Same

The Power BI query is still conceptually:

```sql
SELECT *
FROM NewTable
```

This is possible because the same `New Table` has been created in Production.

Therefore:

```text
Test → New Table
Production → New Table
```

Power BI can use the same query structure.

---

# 29. Apply the Changes

After changing the database:

1. Click **OK**.
2. Click **Close**.
3. Click **Apply Changes**.
4. Power BI will ask for confirmation regarding execution of the query.
5. Confirm/run the query.

Power BI will then retrieve data from the Production database.

---

# 30. Verify the Report After Switching

After the refresh completes, the numbers in the report change.

This is expected because:

```text
Test data ≠ Production data
```

For example:

```text
Test → 99 records
Production → 1,043 records
```

Therefore, the KPI values and visual outputs can change even though:

* The report itself hasn't been recreated.
* The DAX measures haven't been rewritten.
* The visuals haven't been redesigned.

Only the underlying data source has changed.

---

# 31. Verify Multiple Report Pages

The lecture checks the report on multiple pages.

For example:

### Page 1

The numbers change because the report is now connected to Production.

### Page 2

The KPI values also change.

This confirms that the existing DAX measures are now being calculated against the Production data.

---

# 32. Switching Back from Production to Test

The same process can be performed in reverse.

This is useful for demonstrating that the report can switch between environments.

### Open:

**Transform Data → Data Source Settings**

Select the SQL Server source.

Click:

**Change Source**

Change:

```text
Production
```

back to:

```text
Test
```

Click **OK**.

Then:

**Close → Apply Changes**

---

# 33. Result After Switching Back to Test

Power BI loads the Test data again.

The lecture shows:

**99 records loaded**

The report numbers change again.

This demonstrates that the report is now using the Test database.

---

# 34. Data Source Settings in Power Query Editor

The same Data Source Settings functionality can also be accessed through the Power Query Editor.

### Steps

Go to:

**Home → Transform Data**

This opens Power Query Editor.

Then:

**Home → Data Source Settings**

Select the SQL Server source.

Click:

**Change Source**

You can then change the database/environment.

---

# 35. Switch from Test Back to Production Again

For the final demonstration, the source is changed once again:

```text
Test → Production
```

### Steps

1. Open **Transform Data**.
2. Open **Data Source Settings**.
3. Select the Test SQL Server source.
4. Click **Change Source**.
5. Change the database to `prod`.
6. Click **OK**.
7. Click **Close**.
8. Click **Apply Changes**.

Power BI then loads:

**1,043 records**

The report's KPI values update accordingly.

---

# 36. Why the KPI Values Change

The report uses **DAX measures** to calculate its KPIs.

For example, a measure might calculate:

```DAX
Total Sales = SUM('New Table'[Sales])
```

When the underlying data changes:

```text
Test Data
     ↓
DAX Measure
     ↓
Test KPI
```

versus:

```text
Production Data
     ↓
Same DAX Measure
     ↓
Production KPI
```

the result naturally changes.

This is why using DAX measures in the demonstration helps clearly show the impact of switching environments.

---

# 37. Complete Environment Transition Flow

The overall process can be remembered as:

```text
             TEST ENVIRONMENT
                    │
                    │
             Validate Report
                    │
                    ↓
          Validate Production Data
                    │
                    ↓
        Identify Data Quality Issues
                    │
                    ↓
          Fix/Clean Production Data
                    │
                    ↓
       Create Required Production Table
                    │
                    ↓
        Ensure Same Table/Column Names
                    │
                    ↓
             Power BI Desktop
                    │
                    ↓
          Data Source Settings
                    │
                    ↓
             Change Source
                    │
                    ↓
        TEST DATABASE → PROD DATABASE
                    │
                    ↓
            Apply Changes
                    │
                    ↓
           Refresh/Load Data
                    │
                    ↓
          Validate Power BI Report
```

---

# 38. Important Real-World Considerations

When transitioning a Power BI report from Test to Production, remember:

### 1. Test and Production data can differ

The number of records may be completely different.

Example:

```text
Test       = 99 records
Production = 1,043 records
```

---

### 2. Data quality can differ

A column that is clean in Test might contain issues in Production.

---

### 3. Validate Production before deployment

Check important columns for:

* NULLs
* Blanks
* Invalid values
* Unexpected values
* Duplicate records
* Referential integrity issues

---

### 4. Check fact-dimension consistency

If a fact/inventory table contains:

```text
ProductID = 21
```

but the Product dimension doesn't contain 21, investigate it.

---

### 5. Communicate with the data engineering team

Don't silently assume that the data is wrong.

First determine:

* Why the value exists.
* Which team owns the table.
* Whether the value is legitimate.
* Whether a permanent fix is planned.

---

### 6. Clean data at the source where possible

Prefer:

```text
SQL Server
   ↓
Clean/Transform
   ↓
Power BI
```

rather than unnecessarily performing all transformations inside Power BI.

---

### 7. Keep schema consistent

The following should ideally remain unchanged between Test and Production:

* Table names
* Column names
* Data types
* Required relationships/schema structure

This protects existing DAX calculations and report logic.

---

### 8. Do not recreate the report

You don't need to rebuild:

* Visuals
* Measures
* Pages
* Formatting
* KPIs

Simply point the existing report to the Production data source.

---

# 39. Key SQL Commands from the Lecture

### Distinct values

```sql
SELECT DISTINCT OrderDate
FROM dbo.ProductInventoryEnvironmentInventoryDataSet;
```

### NULL/blank check

```sql
SELECT *
FROM dbo.ProductInventoryEnvironmentInventoryDataSet
WHERE OrderDate IS NULL
   OR OrderDate = '';
```

### Distinct Product IDs

```sql
SELECT DISTINCT ProductID
FROM dbo.ProductInventoryEnvironmentInventoryDataSet
ORDER BY ProductID;
```

### Fix Product ID 21

```sql
UPDATE dbo.ProductInventoryEnvironmentInventoryDataSet
SET ProductID = 7
WHERE ProductID = 21;
```

### Fix Product ID 22

```sql
UPDATE dbo.ProductInventoryEnvironmentInventoryDataSet
SET ProductID = 11
WHERE ProductID = 22;
```

### Check Availability

```sql
SELECT DISTINCT Availability
FROM dbo.ProductInventoryEnvironmentInventoryDataSet;
```

### Check Demand

```sql
SELECT DISTINCT Demand
FROM dbo.ProductInventoryEnvironmentInventoryDataSet;
```

### Check Demand for NULL/blank values

```sql
SELECT *
FROM dbo.ProductInventoryEnvironmentInventoryDataSet
WHERE Demand IS NULL
   OR Demand = '';
```

---

# 40. Important Numbers to Remember

| Item                                 |     Result |
| ------------------------------------ | ---------: |
| Test environment records             |     **99** |
| Production environment records       |  **1,043** |
| Distinct Order Dates                 |    **822** |
| Distinct Product IDs before cleaning |     **22** |
| Product IDs expected in dimension    |     **20** |
| Problematic Product IDs              | **21, 22** |
| 21 mapped to                         |      **7** |
| 22 mapped to                         |     **11** |
| Records affected by 21 → 7           |     **37** |
| Records affected by 22 → 11          |     **51** |
| Distinct Product IDs after cleaning  |     **20** |
| Distinct Availability values         |    **121** |
| Distinct Demand values               |    **121** |

---

# 41. Interview/Practical Takeaways

### Q: Do we recreate the Power BI report when moving from Test to Production?

**No.**

Change the data source/database and refresh the existing report.

### Q: Why can KPI values change after deployment?

Because the underlying Production data is different from Test data.

### Q: Why should table names remain the same?

Existing DAX measures, relationships, queries, and visuals may depend on those names.

### Q: Why should we validate Production separately?

Because Production can contain different records and different data-quality issues.

### Q: What should you do if a Product ID exists in the fact table but not in the dimension table?

Investigate it with the team responsible for the source data and resolve/handle the inconsistency before relying on the data.

### Q: Where should data cleaning ideally be performed?

As close to the source as practical, such as SQL Server, so that Power BI receives the cleanest possible data.

---

## Final Concept

The core lesson is:

> **Moving a Power BI report from Test to Production is primarily a data-source/environment change, not a report-recreation exercise.**

The correct workflow is:

**Validate Production → Fix data-quality issues → Create equivalent Production tables → Keep schema consistent → Change Power BI data source → Refresh → Validate the report.**

This allows the **same Power BI report and DAX logic** to operate against different environments while minimizing redevelopment effort.
