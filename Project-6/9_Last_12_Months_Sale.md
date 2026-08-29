# Power BI – Last 12 Months Sales & Measures Table

## 1. Session Overview

In this session, the instructor completes the remaining visual on the **House Market Overview** report page.

The main objective is to create a **Card visual** showing:

> **Total Sales Value for the Last 12 Months**

To calculate this KPI, a **DAX measure** using `CALCULATE()` and `DATESINPERIOD()` is created.

The session also introduces an important **Power BI best practice**:

> Keep measures in a separate dedicated **Measures Table**, especially when working with many tables and measures.

---

# 2. Business Requirement

The final KPI required on the **House Market Overview** page is:

> **Total sales/purchase value generated during the last 12 months.**

The instructor uses the **Purchase Price** column as the sales value.

Conceptually:

```text
Latest Date in Dataset
        ↓
Go back 12 months
        ↓
Take all dates in this period
        ↓
Calculate SUM(Purchase Price)
        ↓
Last 12 Months Sales
```

---

# 3. Creating the DAX Measure

### Steps

1. Go to the **Data pane**.
2. Locate the **Housing** table.
3. Right-click the Housing table.
4. Select:

> **New Measure**

5. Expand the formula bar.
6. Name the measure:

```text
Last 12 Month Sales
```

---

# 4. DAX Functions Used

The instructor uses two major functions:

* `CALCULATE()`
* `DATESINPERIOD()`

Along with:

* `SUM()`
* `MAX()`

The structure is essentially:

```text
CALCULATE(
    SUM(Purchase Price),
    DATESINPERIOD(...)
)
```

---

# 5. SUM of Purchase Price

The sales value is calculated by summing the Purchase Price column.

Conceptually:

```text id="qf6t8c"
SUM(Housing[Purchase Price])
```

This gives the total purchase/sales value.

---

# 6. Understanding DATESINPERIOD()

The instructor then uses:

> `DATESINPERIOD()`

This function is used to return a table containing dates within a specified period.

The general structure is:

```text
DATESINPERIOD(
    Date Column,
    Start Date,
    Number of Intervals,
    Interval
)
```

For this requirement, the four components are:

| Argument            | Value               |
| ------------------- | ------------------- |
| Date column         | Housing Date        |
| Start date          | Maximum/latest date |
| Number of intervals | `-12`               |
| Interval            | `MONTH`             |

---

# 7. Date Column

The first argument is the Date column from the Housing table.

Conceptually:

```text id="uh6p3a"
DATESINPERIOD(
    Housing[Date],
    ...
)
```

This tells Power BI which date column should be used to construct the period.

---

# 8. Start Date – Maximum Date

The second argument is the start date.

The instructor wants the calculation to start from the **highest/latest date available in the dataset**.

Therefore:

```text id="t1x3p9"
MAX(Housing[Date])
```

is used.

`MAX()` returns the latest date in the Date column.

For example, if the latest date is:

```text
31 December 2025
```

then this becomes the reference point for the calculation.

---

# 9. Going Back 12 Months

The third argument specifies the number of intervals.

Since the requirement is **last 12 months**, the instructor uses:

```text id="x8h4w1"
-12
```

The negative sign is important.

It tells `DATESINPERIOD()` to move **backward** from the maximum/latest date.

Conceptually:

```text
Latest Date
     ↓
-12 months
     ↓
12-month period
```

---

# 10. Specifying the Interval

The final argument specifies what the `-12` represents.

The instructor specifies:

```text
MONTH
```

Therefore:

```text id="m2k5z7"
-12 + MONTH
```

means:

> Go back 12 months from the specified start date.

---

# 11. Complete DAX Logic

The measure created in the session can be represented as:

```text id="g4n8q2"
Last 12 Month Sales =
CALCULATE(
    SUM(Housing[Purchase Price]),
    DATESINPERIOD(
        Housing[Date],
        MAX(Housing[Date]),
        -12,
        MONTH
    )
)
```

### What this does

It calculates:

> **The total Purchase Price for the 12-month period ending at the latest date in the dataset.**

---

# 12. Understanding the Measure With an Example

Suppose the latest date in the dataset is:

```text
31 December 2025
```

Then:

```text
MAX(Date)
```

returns:

```text
31 December 2025
```

`DATESINPERIOD()` then goes backward by 12 months.

Conceptually:

```text
Dec 2025
   ↑
12 months backward
   ↑
Dec 2024
```

The Purchase Price values within this period are then summed.

So the result represents:

> **Total sales value during the latest 12-month period available in the dataset.**

---

# 13. Why MAX(Date) Is Used

An important point is that the measure does **not** hard-code a year such as 2025.

Instead, it dynamically finds:

```text
MAX(Date)
```

This makes the measure adaptable.

For example, if new data is added and the latest date becomes 2026, the measure automatically uses the new latest date as its reference point.

Therefore, it is better than writing something fixed such as:

```text
Date = 2025
```

---

# 14. Creating the Card Visual

After creating the measure, the instructor creates a Card visual.

Instead of creating a new Card from scratch, the instructor copies an existing Card visual.

### Steps

1. Select the existing Card visual:

> **Units Sold in Latest Year and Quarter**

2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

This creates a duplicate Card.

---

# 15. Positioning the New Card

The copied Card is moved to the right-hand side of the existing Card.

The report now has another KPI card alongside the previous one.

Conceptually:

```text
┌─────────────────────┐   ┌─────────────────────┐
│ Units Sold          │   │ Last 12 Month Sales │
│                     │   │                     │
│       VALUE         │   │       VALUE         │
└─────────────────────┘   └─────────────────────┘
```

---

# 16. Removing the Existing Measure

Because the copied Card still contains:

> Units Sold in Latest Year and Quarter

the instructor removes that measure from the Card.

The copied Card is now ready to display the new measure.

---

# 17. Adding Last 12 Month Sales

The newly created measure:

> **Last 12 Month Sales**

is then added to the Card.

### Steps

1. Select the copied Card.
2. Locate `Last 12 Month Sales` in the Data pane.
3. Add/select the measure for the Card.

The Card now displays the calculated total sales value for the latest 12 months.

---

# 18. Renaming the Card Title

The instructor changes the title to make it more concise.

### Steps

1. Select the Card.
2. Open:

> **Format Visual**

3. Go to:

> **General**

4. Find:

> **Title**

5. Set the title to:

> **12 Month Sales**

This provides a concise description of the KPI.

---

# 19. Final Visual

The completed Card represents:

> **12 Month Sales**

The underlying calculation is:

```text
SUM(Purchase Price)
```

over:

```text
DATESINPERIOD(
    Date,
    MAX(Date),
    -12,
    MONTH
)
```

---

# 20. Important Best Practice – Separate Measures Table

After completing the visual, the instructor introduces an important real-world Power BI practice.

In an actual project, you may have:

* Many tables
* Many calculated measures
* Many report pages
* Dozens or even hundreds of DAX measures

Keeping measures scattered across different data tables can make the model difficult to maintain.

Therefore, the instructor recommends:

> **Keep all measures in a separate dedicated Measures Table.**

---

# 21. Why Create a Separate Measures Table?

Suppose the project has:

```text
Housing
Customer
Sales
Date
Region
Products
```

and each table contains many measures.

Finding measures becomes difficult.

Instead, you can have:

```text
Housing
Customer
Sales
Date
Region
Products
Measures Table
```

with all measures organized in one place.

This makes the model:

* Easier to navigate
* Easier to maintain
* More organized
* Easier for other developers to understand

---

# 22. Creating the Measures Table

The instructor creates a new table.

### Steps

1. Go to the:

> **Home** tab.

2. Click:

> **Enter Data**

3. A table creation window appears.
4. The instructor names the table:

> **Measures Table 1 for Page 1**

5. Click:

> **Load**

Power BI then loads the new table.

---

# 23. Loading the Measures Table

After clicking **Load**, Power BI may take some time to apply the changes.

The instructor points out that:

> Applying changes and loading data can take some time.

This is normal, especially as the model becomes larger.

---

# 24. Purpose of This Table

The new table is primarily intended to serve as a **container for measures**.

It does not necessarily represent a business entity or actual dataset like:

* Housing
* Customer
* Sales

Instead, it is used to organize the DAX measures created for the report.

---

# 25. Current Report Structure

By this point, the **House Market Overview** page has several important visuals.

### Visual 1 – Year-on-Year Sales Growth

```text
Line Chart
```

Shows:

> Year-on-Year Sales Growth by Sales Type

---

### Visual 2 – Offer Price vs Purchase Price

```text
Scatter Plot
```

Shows:

> Relationship between Offer Price and Purchase Price

---

### Visual 3 – Median Sales Price Change

```text
Bar Chart
```

Shows:

> Median Sales Price Change by Region

---

### Visual 4 – Units Sold

```text
Card
```

Shows:

> Units Sold in Latest Year and Quarter

---

### Visual 5 – Last 12 Month Sales

```text
Card
```

Shows:

> Total sales value for the latest 12 months

---

# 26. DAX Concepts to Remember

## `CALCULATE()`

Changes the filter context under which an expression is evaluated.

Here:

```text
CALCULATE(
    SUM(Purchase Price),
    DATESINPERIOD(...)
)
```

means:

> Calculate the sum of Purchase Price under the specified 12-month date filter.

---

## `SUM()`

Adds all Purchase Price values within the relevant filter context.

```text
SUM(Purchase Price)
```

---

## `MAX()`

Finds the latest/highest date:

```text
MAX(Date)
```

---

## `DATESINPERIOD()`

Generates a date period relative to a specified start date.

Here:

```text
DATESINPERIOD(
    Date,
    MAX(Date),
    -12,
    MONTH
)
```

means:

> Return the dates covering the previous 12 months relative to the latest date.

---

# 27. Key Point About `-12`

Remember:

```text
-12
```

is not twelve days or twelve years.

Because the interval is specified as:

```text
MONTH
```

the calculation means:

> **12 months backward**

So:

```text
-12 + MONTH
```

= previous 12 months.

---

# 28. Complete Workflow

```text
Housing Table
      ↓
Right-click Housing
      ↓
New Measure
      ↓
Name → Last 12 Month Sales
      ↓
SUM(Purchase Price)
      ↓
DATESINPERIOD()
      ↓
Date Column
      ↓
MAX(Date)
      ↓
-12
      ↓
MONTH
      ↓
CALCULATE()
      ↓
Measure Created
      ↓
Copy Existing Card
      ↓
Ctrl + C → Ctrl + V
      ↓
Move Card to Right
      ↓
Remove Units Sold Measure
      ↓
Add Last 12 Month Sales
      ↓
Format Visual
      ↓
General → Title
      ↓
"12 Month Sales"
      ↓
Create Separate Measures Table
      ↓
Home → Enter Data
      ↓
Name → Measures Table 1 for Page 1
      ↓
Load
```

---

# 29. Quick Revision

| Topic                   | Key Point                   |
| ----------------------- | --------------------------- |
| KPI                     | Last 12 Month Sales         |
| Measure                 | `Last 12 Month Sales`       |
| Main function           | `CALCULATE()`               |
| Date function           | `DATESINPERIOD()`           |
| Sales calculation       | `SUM(Purchase Price)`       |
| Reference date          | `MAX(Date)`                 |
| Period                  | `-12 MONTH`                 |
| Visual                  | Card                        |
| Card title              | `12 Month Sales`            |
| Shortcut used           | `Ctrl + C`, `Ctrl + V`      |
| Best practice           | Separate measures table     |
| Measures table creation | Home → Enter Data           |
| Measures table name     | Measures Table 1 for Page 1 |

---

# 30. Exam/Interview-Level Understanding

### What does this measure calculate?

```text
CALCULATE(
    SUM(Purchase Price),
    DATESINPERIOD(
        Date,
        MAX(Date),
        -12,
        MONTH
    )
)
```

**Answer:**

It calculates the **total Purchase Price/Sales Value for the 12-month period ending at the latest date available in the dataset.**

### Why `MAX(Date)`?

To dynamically identify the latest available date instead of hard-coding a date.

### Why `-12`?

To move backward by 12 intervals.

### Why `MONTH`?

Because the intervals are months.

### Why `CALCULATE()`?

To evaluate the sales sum within the date period generated by `DATESINPERIOD()`.

### Why a separate Measures Table?

To keep DAX measures organized and separate from the actual business/data tables, which becomes especially useful in large Power BI projects.
