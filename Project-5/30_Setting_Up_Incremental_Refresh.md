# Power BI Data Flow — Incremental Refresh

## 1. Verifying the Scheduled Refresh

Before moving to incremental refresh, the instructor first verifies that the **scheduled refresh** configured in the previous session actually worked.

The refresh had been scheduled for **5:30 AM**.

At **5:32 AM**, the instructor checks the refresh history.

### Steps

1. Open the Data Flow.
2. Click the **three dots (...)**.
3. Select **Refresh History**.
4. Check the latest refresh entry.

### Result

The latest refresh:

* Completed at approximately **5:31 AM**
* Status: **Completed**

This confirms that the scheduled refresh was successfully executed.

> **Conclusion:** The scheduled refresh configuration is working correctly.

---

# 2. Introduction to Incremental Refresh

After verifying scheduled refresh, the session moves to **Incremental Refresh**.

The instructor opens the relevant **SQL Data Flow** and looks at the incremental refresh settings.

There is an option on the right-hand side to configure:

**Incremental Refresh**

The instructor switches the toggle **ON**.

---

# 3. Requirement for Incremental Refresh

After enabling incremental refresh, Power BI asks you to select a **Date/Time column to filter by**.

However, the dataset has a problem.

### Available column

The dataset contains a:

```text
Date
```

column.

### Missing column

But it does **not** contain a:

```text
Date/Time
```

column.

For the incremental refresh configuration being demonstrated, a **Date/Time column is required**.

Therefore, the existing `Date` column needs to be converted into a `Date/Time` column.

---

# 4. Changing Date Column to Date/Time

The instructor performs this transformation directly in the **Power Query Editor online through Power BI Service**.

### Steps

1. Cancel the current incremental refresh configuration.
2. Expand the **Loan Default** table.
3. Locate the existing **Date** column.
4. Click **Edit Table**.
5. Wait for the Power Query Editor to load.
6. Scroll horizontally to the right if required.
7. Locate the **Date** column.
8. At the top of the column, identify its current data type.
9. Click the small **data type icon**.
10. Change the data type from **Date** to **Date/Time**.
11. Click **Save and Close**.

After saving, the column is now recognized as a **Date/Time** column.

### Verification

Scroll down/check the `Loan Date` column and confirm that its data type is now:

```text
Date/Time
```

---

# 5. Enable Incremental Refresh Again

Now that a Date/Time column is available:

### Steps

1. Open **Incremental Refresh** again.
2. Switch the toggle **ON**.
3. Select the Date/Time column to use for filtering.

The lecture shows two column names as options and selects the **first one**.

The selected column will act as the basis for determining which data needs to be refreshed.

---

# 6. Configure "Store Rows from the Past"

The next setting is:

**Store rows from the past**

This determines the **total historical period of data that should be retained**.

For example, the instructor configures:

```text
5 Years
```

### Configuration

| Setting                  | Value |
| ------------------------ | ----: |
| Store rows from the past |     5 |
| Period                   | Years |

This means the incremental refresh policy will retain **five years of historical data** relative to the latest date.

---

# 7. Configure "Refresh Rows from the Past"

The next setting determines the period of data that should actually be refreshed.

The instructor configures:

```text
10 Days
```

### Configuration

| Setting                    | Value |
| -------------------------- | ----: |
| Refresh rows from the past |    10 |
| Period                     |  Days |

Therefore:

> Only the **latest 10 days of data** will be refreshed during the incremental refresh operation.

---

# 8. Understanding Store Period vs Refresh Period

This is one of the most important concepts in incremental refresh.

In the example:

```text
Store = 5 years
Refresh = 10 days
```

These two settings have **different purposes**.

### Store Period — 5 Years

Power BI retains data for the latest **5 years**.

### Refresh Period — 10 Days

Power BI refreshes only the latest **10 days**.

So conceptually:

```text
                 Latest Date
                      │
       ┌──────────────┴──────────────┐
       │                             │
   Last 10 Days                 Older Data
       │                             │
    REFRESH                    RETAIN/STORE
       │                             │
       └──────────────┬──────────────┘
                      │
               Up to 5 Years
```

Any data older than the configured **5-year retention period** is removed.

### Example

Suppose the latest available date is:

```text
31 March 2025
```

Then:

* Data within approximately the latest **10 days** → refreshed.
* Data within the retained **5-year period** → kept.
* Data older than the 5-year retention period → removed from the stored data.

---

# 9. Detect Data Changes

The next option is:

**Detect data changes**

You can enable this option by checking its checkbox.

The purpose is to avoid refreshing data unnecessarily.

### How it works

You select a column that can indicate whether the data has changed.

The instructor selects a suitable column for this purpose.

Power BI then checks the **maximum value** in that column.

### Logic

If the maximum value in the selected column **changes**:

```text
Maximum value changed
        ↓
Data has potentially changed
        ↓
Refresh data
```

If the maximum value **does not change**:

```text
Maximum value unchanged
        ↓
No detected data change
        ↓
Data does not need to be refreshed
```

Therefore, the refresh can be avoided when Power BI detects that the maximum value hasn't changed.

### Why is this useful?

It can prevent unnecessary refresh operations and reduce the amount of processing performed.

---

# 10. "Only Refresh Complete Days"

Another option available is:

**Only refresh complete days**

This option is useful when your business calculations or KPIs require a **complete day's worth of data**.

The instructor explains this with an example.

---

## Example

Suppose your Data Flow refreshes every day at:

```text
4:00 AM
```

Later, new data may appear during the day.

For example:

```text
12:00 PM
      ↓
New data appears
      ↓
2:00 PM / 3:00 PM
      ↓
More data arrives
```

If the Data Flow refreshes while the day is still in progress, the current day may contain only **partial data**.

For example:

```text
Today's Data

00:00 ─────────────── 24:00
        ↑
    Data available
    only up to 3 PM
```

The day is not complete yet.

---

# 11. Why Partial Data Can Be a Problem

Some KPIs and business metrics only make sense when data for the **entire day** has been collected.

For example, a KPI calculated using only part of today's data could be misleading.

Therefore, you may want Power BI to refresh only data corresponding to **fully completed days**.

### Solution

Enable:

**Only refresh complete days**

This prevents partial-day data from being included in the incremental refresh process when complete-day data is required.

---

# 12. Save the Incremental Refresh Policy

Once all settings have been configured:

1. Select the required Date/Time column.
2. Configure the historical storage period.
3. Configure the refresh period.
4. Optionally enable **Detect data changes**.
5. Optionally enable **Only refresh complete days**.
6. Click **Save**.

---

# 13. Premium Capacity Requirement

After clicking **Save**, the instructor receives a message indicating that the Data Flow contains tables with **active incremental refresh policies**.

The message explains that these policies require **Power BI Premium capacity** to perform the refresh.

The lecture environment is using a **free trial**, so the Premium-capacity requirement message is displayed.

### Important

The key takeaway from the lecture is:

> Incremental refresh for the Data Flow being demonstrated requires an appropriate **Power BI Premium/Fabric capacity** environment.

So if you encounter this message while practicing in a non-Premium environment, it does not mean that the incremental refresh configuration itself is conceptually wrong.

---

# 14. Complete Incremental Refresh Workflow

```text
Verify Scheduled Refresh
        ↓
Data Flow → Three dots (...)
        ↓
Refresh History
        ↓
Confirm Status = Completed
        ↓
Open Data Flow
        ↓
Incremental Refresh
        ↓
Enable Incremental Refresh
        ↓
Select Date/Time Column
        ↓
No Date/Time Column?
        ↓
Edit Table
        ↓
Power Query Editor
        ↓
Change Date → Date/Time
        ↓
Save and Close
        ↓
Incremental Refresh
        ↓
Enable
        ↓
Select Date/Time Column
        ↓
Store Rows = 5 Years
        ↓
Refresh Rows = 10 Days
        ↓
Optional: Detect Data Changes
        ↓
Optional: Only Refresh Complete Days
        ↓
Save
```

---

# 15. Key Settings at a Glance

| Incremental Refresh Setting | Example Used | Purpose                                                       |
| --------------------------- | -----------: | ------------------------------------------------------------- |
| Date/Time column            |    Loan Date | Determines the date range used for filtering                  |
| Store rows from the past    |  **5 Years** | Total historical data retained                                |
| Refresh rows from the past  |  **10 Days** | Recent data that gets refreshed                               |
| Detect data changes         |     Optional | Refresh only when the selected column's maximum value changes |
| Only refresh complete days  |     Optional | Prevent refreshing incomplete/partial days                    |

---

# 16. Scheduled Refresh vs Incremental Refresh

This session reinforces the distinction from the previous lecture.

### Scheduled Refresh

The schedule determines **when** the Data Flow refresh operation happens.

In the earlier example:

```text
Every day
    ↓
5:30 AM
    ↓
Refresh
```

The lecture's discussion treats this as a **full refresh**.

### Incremental Refresh

Incremental refresh determines **which portion of the data needs to be refreshed/retained**.

Example:

```text
Store → 5 Years
Refresh → 10 Days
```

Therefore:

```text
Scheduled Refresh
        ↓
WHEN should refresh happen?

Incremental Refresh
        ↓
WHAT portion of data should be refreshed?
```

These concepts can work together rather than being mutually exclusive.

---

# 17. Important Interview Points

### Q1. What is incremental refresh?

Incremental refresh is a technique where instead of processing all historical data during every refresh, only a defined portion of the data—typically recent/changed data—is refreshed.

---

### Q2. Why is incremental refresh useful?

It is particularly useful for large datasets because:

* Less data needs to be processed.
* Refresh operations can complete faster.
* Processing/resource requirements can be reduced.
* It avoids repeatedly processing unchanged historical data.

---

### Q3. What is the difference between Store and Refresh periods?

**Store period** determines how much historical data Power BI retains.

**Refresh period** determines how much recent data is refreshed during an incremental refresh.

Example:

```text
Store = 5 Years
Refresh = 10 Days
```

means:

> Keep up to five years of data, but refresh only the latest ten days.

---

### Q4. What happens to data older than the Store period?

Data outside the configured retention period is removed.

For example, if:

```text
Store = 5 Years
```

then data older than the retained five-year period is no longer retained.

---

### Q5. What does Detect Data Changes do?

It allows Power BI to determine whether data has changed by checking a selected column, specifically whether its **maximum value has changed**.

If the maximum value hasn't changed, the corresponding data doesn't need to be refreshed.

---

### Q6. Why use "Only refresh complete days"?

It is useful when business KPIs require complete daily data.

If a refresh occurs while today's data is still being generated, today's data may be incomplete. Enabling this option ensures that only **completed days** are considered for refresh.

---

# 18. Most Important Things to Memorize

```text
Date column
     ↓
Must be Date/Time for this incremental-refresh setup
```

```text
Store = How much historical data to RETAIN
Refresh = How much recent data to REFRESH
```

```text
Example:
Store → 5 Years
Refresh → 10 Days
```

```text
Detect Data Changes
→ Check whether maximum value changes
→ If changed → refresh
→ If unchanged → avoid unnecessary refresh
```

```text
Only Refresh Complete Days
→ Useful when partial-day data can distort KPIs
```

```text
Incremental Refresh
→ Requires appropriate Premium/Fabric capacity for the Data Flow scenario demonstrated
```

### Final takeaway

The central idea of incremental refresh is **not to repeatedly refresh the entire historical dataset**. Instead, you define a **retention window** (5 years in this example) and a **refresh window** (10 days in this example), allowing recent data to be refreshed while older unchanged data is retained.
