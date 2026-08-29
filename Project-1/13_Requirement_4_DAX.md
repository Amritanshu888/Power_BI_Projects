# Power BI — Detailed Notes: Requirement 4 — Compare Sales, Profit & Quantity Between Two User-Selected Periods

This lecture explains **Approach 1** for fulfilling **Requirement 4**.

## Requirement 4

The report must allow the **user to select any two different dates/periods** and then compare:

* **Sales**
* **Profit**
* **Quantity Sold**

for those two selected periods.

The approach in this lecture uses:

* Two separate date tables
* Two date slicers
* One active relationship
* One inactive relationship
* DAX measures using `CALCULATE()`, `ALL()`, and `USERELATIONSHIP()`
* Three clustered column charts

---

# 1. Requirement and Overall Approach

The requirement is to provide flexibility to the user:

> Select one date/period using **Date Filter 1** and another date/period using **Date Filter 2**, then compare Sales, Profit, and Quantity Sold between the two selections.

The lecture discusses **two approaches** for achieving this functionality.

This video covers **Approach 1** only.

The basic architecture is:

```text
Date Table 1 ────── Active Relationship ────── Fact Table
Date Table 2 - - - Inactive Relationship - - - Fact Table
      ↓                                      ↑
Date Filter 1                         Date Filter 2
```

The reason for the inactive relationship will become important when creating the DAX measures.

---

# 2. Create Date Table 1

We first need **two separate date tables**.

## Steps

1. Go to the **Modeling** tab.
2. Click **New Table**.
3. Name the table:

```text
Date Table 1
```

4. Use the `CALENDARAUTO()` DAX function.

### DAX

```DAX
Date Table 1 = CALENDARAUTO()
```

5. Press **Enter**.

---

## What Does `CALENDARAUTO()` Do?

`CALENDARAUTO()` automatically creates a table containing a single column of dates.

It determines the date range automatically by looking at the dates available throughout the data model.

So instead of manually specifying a start and end date, Power BI automatically determines the required date range.

---

# 3. Create Date Table 2

We need another independent date table.

## Steps

1. Go to **Modeling → New Table**.
2. Name it:

```text
Date Table 2
```

3. Use:

```DAX
Date Table 2 = CALENDARAUTO()
```

4. Press **Enter**.

You now have:

```text
Date Table 1
Date Table 2
```

Both contain their own Date columns.

---

# 4. Check the Date Column Data Type and Format

The date columns in the two new tables should have the same formatting as the Date column in the Fact table.

The lecture checks the Fact table's Date column first.

## Fact Table

The Date column has:

* **Data type:** Date
* **Format:** Long Date

The same configuration should be applied to both newly created date tables.

---

## Date Table 1

1. Select **Date Table 1**.
2. Select its **Date** column.
3. Set:

```text
Data Type → Date
Format → Long Date
```

---

## Date Table 2

1. Select **Date Table 2**.
2. Select its **Date** column.
3. Set:

```text
Data Type → Date
Format → Long Date
```

Now all three relevant Date columns have the same data type and formatting.

---

# 5. Create the Relationship Between Date Table 1 and Fact Table

Now go to **Model View**.

The first date table should have an **active relationship** with the Fact table.

## Steps

1. Drag:

```text
Date Table 1[Date]
```

onto:

```text
Fact Table[Date]
```

2. Power BI opens the relationship configuration.
3. The relationship should be:

```text
One-to-Many (1:*)
```

The direction is:

```text
Date Table 1 → Fact Table
```

4. **Cross-filter direction:** Single
5. Keep the relationship **Active**.
6. Click **Save/OK**.

---

## Relationship Meaning

The Date Table acts as the **one** side:

```text
Date Table 1
     1
     |
     |
     *
Fact Table
```

The Date Table can filter the Fact table.

The reverse filtering does not occur because the cross-filter direction is **Single**.

---

# 6. Create the Relationship Between Date Table 2 and Fact Table

Repeat the same process for Date Table 2.

## Steps

1. Drag:

```text
Date Table 2[Date]
```

onto:

```text
Fact Table[Date]
```

2. Keep:

```text
Cardinality → One-to-Many
Cross-filter direction → Single
```

3. However, **uncheck Active**.
4. Save the relationship.

---

# 7. Active vs. Inactive Relationship

This is one of the most important concepts in this lecture.

After creating the relationships, Model View shows:

### Date Table 1 → Fact Table

**Solid line**

Meaning:

> Active relationship

### Date Table 2 → Fact Table

**Dotted line**

Meaning:

> Inactive relationship

So the model looks conceptually like:

```text
Date Table 1 ───────── Fact Table
              Active

Date Table 2 - - - - - Fact Table
              Inactive
```

---

# 8. Why Is Date Table 2 Inactive?

Power BI normally allows only one active relationship between the same two tables for this type of filtering path.

Therefore, Date Table 1 is used as the active relationship, while Date Table 2 is kept inactive.

This creates the exact situation we need for the DAX solution:

* Date Filter 1 can directly filter the Fact table.
* Date Filter 2 cannot directly filter the Fact table.
* We will later activate the second relationship **inside a DAX measure** using `USERELATIONSHIP()`.

---

# 9. Create Date Filter 1

Now go back to **Report View**.

The report needs two slicers because the user needs to select two different dates.

## Steps

1. Click on a blank area of the canvas.
2. Select the **Slicer** visual.
3. Resize the slicer.
4. Add:

```text
Date Table 1[Date]
```

to the slicer.

This becomes the first date selector.

---

# 10. Rename Date Filter 1

The field initially appears as Date.

Rename it for clarity.

### Steps

1. Select the slicer.
2. Under the **Fields** bucket, double-click the Date field.
3. Rename it to:

```text
Date Filter 1
```

4. Press **Enter**.

---

# 11. Create Date Filter 2

Instead of creating another slicer from scratch, the lecture copies the first slicer.

## Steps

1. Select the first slicer.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the copied slicer to the desired location.

---

# 12. Change the Second Slicer's Date Field

The copied slicer initially still uses:

```text
Date Table 1[Date]
```

But the second slicer must use:

```text
Date Table 2[Date]
```

## Steps

1. Select the second slicer.
2. Remove the existing Date field from the Fields bucket.
3. Add:

```text
Date Table 2[Date]
```

4. Rename this field to:

```text
Date Filter 2
```

Now we have:

```text
Date Filter 1 → Date Table 1
Date Filter 2 → Date Table 2
```

---

# 13. Add Borders to the Slicers

The lecture formats both slicers by adding borders.

## Date Filter 1

1. Select the first slicer.
2. Go to:

**Format Visual → General → Effects**

3. Turn:

**Visual Border → On**

---

## Date Filter 2

Repeat the same process:

**Format Visual → General → Effects → Visual Border → On**

Now both date slicers have borders.

---

# 14. Create the First Column Chart — Sales

The first metric to compare is **Sales**.

A **Clustered Column Chart** is used.

## Steps

1. Click on a blank area of the canvas.
2. Select **Clustered Column Chart**.
3. Resize the visual.
4. Expand the Fact table.
5. Add:

```text
Net Sales
```

to the chart.

Power BI initially creates a column representing the sales value.

---

# 15. Turn On Data Labels

To make the sales values visible directly on the chart:

1. Select the column chart.
2. Go to **Format Visual**.
3. Find **Data Labels**.
4. Turn:

```text
Data Labels → On
```

---

# 16. Test Date Filter 1

At this stage, Date Filter 1 uses an **active relationship**.

Therefore, if the user selects a date or date range using Date Filter 1:

> The sales column changes.

This confirms that Date Filter 1 is correctly filtering the Fact table.

---

# 17. Test Date Filter 2

Now select a different date/date range using Date Filter 2.

The sales column **does not change**.

### Why?

Because:

```text
Date Table 2 → Fact Table
```

is an **inactive relationship**.

Therefore, the slicer based on Date Table 2 cannot directly filter the sales visual.

This demonstrates the problem that Requirement 4 needs us to solve.

---

# 18. Solution — Use a DAX Measure

To make Date Filter 2 work, we create a measure.

The measure will:

1. Calculate Net Sales.
2. Ignore filtering from Date Table 1.
3. Temporarily activate the relationship between Date Table 2 and Fact Table.

The three important DAX functions are:

```text
CALCULATE()
ALL()
USERELATIONSHIP()
```

---

# 19. Create the `Sum of Net Sales` Measure

The lecture initially creates the measure under Date Table 1.

## Steps

1. Right-click **Date Table 1**.
2. Select **New Measure**.
3. Expand the formula bar.
4. Name the measure:

```text
Sum of Net Sales
```

The DAX structure is:

```DAX
Sum of Net Sales =
CALCULATE(
    SUM('Fact Table'[Net Sales]),
    ALL('Date Table 1'),
    USERELATIONSHIP(
        'Date Table 2'[Date],
        'Fact Table'[Date]
    )
)
```

> Use the actual table names in your model if they differ.

---

# 20. Understand the `CALCULATE()` Function

The overall calculation is:

```DAX
CALCULATE(...)
```

`CALCULATE()` evaluates an expression under modified filter conditions.

Here, the expression is:

```DAX
SUM('Fact Table'[Net Sales])
```

So we are calculating total Net Sales.

---

# 21. Understand `SUM(Net Sales)`

Inside `CALCULATE()`:

```DAX
SUM('Fact Table'[Net Sales])
```

means:

> Add all Net Sales values from the Fact table.

---

# 22. Understand `ALL(Date Table 1)`

The next argument is:

```DAX
ALL('Date Table 1')
```

This tells Power BI to remove the filtering coming from Date Table 1 for this measure.

This is important because the normal Net Sales column is already being filtered by **Date Filter 1**.

For the second comparison value, we don't want Date Filter 1 to interfere.

Therefore:

```text
ALL(Date Table 1)
```

removes that filter.

---

# 23. Understand `USERELATIONSHIP()`

The final part is:

```DAX
USERELATIONSHIP(
    'Date Table 2'[Date],
    'Fact Table'[Date]
)
```

This tells Power BI:

> For this particular calculation, use the relationship between Date Table 2 and the Fact table.

Although that relationship is inactive in the model, `USERELATIONSHIP()` temporarily activates it **for the calculation of this measure**.

This is the key technique used to make Date Filter 2 work.

---

# 24. Add the Measure to the Sales Chart

After creating the measure:

1. Collapse the formula bar.
2. Select the sales column chart.
3. Add/check:

```text
Sum of Net Sales
```

Now the chart contains two columns:

### Original Net Sales

Controlled by:

```text
Date Filter 1
```

### Sum of Net Sales Measure

Controlled by:

```text
Date Filter 2
```

---

# 25. Test the Two Sales Columns

Suppose:

```text
Light blue column = Date Filter 1
Dark blue column = Date Filter 2
```

If you change **Date Filter 2**:

* Dark blue column changes.
* Light blue column remains unchanged.

If you change **Date Filter 1**:

* Light blue column changes.
* Dark blue column remains unchanged.

Therefore, we can now compare two different periods.

---

# 26. Why the Two Columns Initially Have the Same Value

If neither slicer has a filter selected, both columns represent the same overall sales value.

Therefore:

```text
Sales 1 = Sales 2
```

This is expected.

Once the user selects different dates, the values become different.

---

# 27. Format the Sales Column Chart

The lecture then formats the chart.

## Change Title

Go to:

**Format Visual → General → Title**

Change the title to:

```text
Total Sales
```

---

## Remove Horizontal Gridlines

Go to:

**Visual → Grid Lines**

Turn:

```text
Horizontal Grid Lines → Off
```

---

## Remove Y-Axis Values

Under:

**Y-axis**

Change:

```text
Values → Off
Title → Off
```

The actual values will instead be displayed through data labels.

---

## Add Border

Go to:

**General → Effects → Visual Border**

Turn:

```text
On
```

---

# 28. Format the Column Colors

Under:

**Visual → Columns**

select the relevant series.

The lecture uses different colors for the two periods.

For example:

```text
Sales 1 → Purple
Sales 2 → Another contrasting color
```

This makes it easy for the user to distinguish the two selected periods.

---

# 29. Rename the Sales Legends

Both columns initially have the same name:

```text
Sum of Net Sales
```

That is confusing.

Rename the two series.

### First Series

Rename to:

```text
Sales 1
```

### Second Series

Rename to:

```text
Sales 2
```

This makes the purpose of each column clearer.

---

# 30. Create the Total Profit Chart

The same approach is now used for **Profit**.

Instead of creating a completely new visual, the lecture copies the sales column chart.

## Steps

1. Select the Total Sales column chart.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the copied chart to another location.
4. Remove the existing Sales fields.
5. Add:

```text
Profit
```

Now the chart represents Total Profit.

---

# 31. Change the Profit Chart Title

Go to:

**Format Visual → General → Title**

Change it to:

```text
Total Profit
```

The lecture notes that the total profit is approximately:

```text
12.2 million
```

for the complete dataset.

---

# 32. Create the Measures Table

The lecture introduces an important **Power BI best practice**:

> Keep measures in a separate table.

Instead of keeping measures scattered across Date Table 1, Fact Table, etc., create a dedicated table.

---

## Steps

1. Go to the **Home** tab.
2. Click **Enter Data**.
3. Create a new table.
4. Name it:

```text
Measures Table
```

5. Click **Load**.

Power BI creates a new Measures Table.

---

# 33. Move `Sum of Net Sales` to Measures Table

The previously created `Sum of Net Sales` measure currently resides under Date Table 1.

Move it to the Measures Table.

## Steps

1. Select the `Sum of Net Sales` measure.
2. Find its table assignment.
3. Change it from:

```text
Date Table 1
```

to:

```text
Measures Table
```

Now the measure resides under the dedicated Measures Table.

---

# 34. Delete the Unnecessary Column

When using **Enter Data**, Power BI creates a default column such as:

```text
Column 1
```

This column isn't required.

### Steps

1. Right-click `Column 1`.
2. Select:

**Delete from Model**

The Measures Table now functions as a dedicated place for measures.

---

# 35. Create the `Total Profit` Measure

Right-click:

**Measures Table → New Measure**

Name it:

```text
Total Profit
```

The intended DAX structure is:

```DAX
Total Profit =
CALCULATE(
    SUM('Fact Table'[Profit]),
    ALL('Date Table 1'),
    USERELATIONSHIP(
        'Date Table 2'[Date],
        'Fact Table'[Date]
    )
)
```

### Important

The lecture initially demonstrates an error where **Net Sales** was accidentally used instead of **Profit**.

The mistake was identified because the chart showed the sales total instead of the profit total.

The expression was then corrected to:

```DAX
SUM('Fact Table'[Profit])
```

This is an important debugging lesson:

> Always verify that the column being aggregated matches the metric being calculated.

---

# 36. Add Total Profit Measure to the Profit Chart

1. Select the Total Profit column chart.
2. Add/check:

```text
Total Profit
```

Now the chart has:

```text
Profit 1
Profit 2
```

corresponding to the two date filters.

---

# 37. Format the Profit Chart

The lecture uses **Format Painter** to copy formatting from the Total Sales chart.

## Steps

1. Select the **Total Sales** chart.
2. Click **Format Painter**.
3. Click the **Total Profit** chart.

This copies the visual formatting.

The colors are then adjusted manually if required.

For example:

```text
Profit 1 → Purple
Profit 2 → Different color
```

---

# 38. Rename the Profit Legends

To make the comparison clear:

### First series

```text
Profit 1
```

### Second series

```text
Profit 2
```

This indicates that the first value is controlled by Date Filter 1 and the second by Date Filter 2.

---

# 39. Test the Total Profit Chart

Select a value/range in **Date Filter 2**.

Expected behavior:

* Profit 2 changes.
* Profit 1 does not.

Then select a value/range in **Date Filter 1**.

Expected behavior:

* Profit 1 changes.
* Profit 2 does not.

This confirms that the DAX measure is working correctly.

---

# 40. Create the Total Quantity Sold Chart

The same concept is now applied to **Quantity Sold**.

## Steps

1. Copy the Total Profit chart:

```text
Ctrl + C
Ctrl + V
```

2. Move the copied chart.
3. Rename the title to:

```text
Total Quantity Sold
```

4. Remove the Profit fields from the new chart.

---

# 41. Add Unit Sold to the Quantity Chart

From the Fact table:

```text
Unit Sold
```

is used to represent quantity.

Add it to the new column chart.

This creates the first quantity column.

---

# 42. Create the Quantity Sold Measure

Go to:

**Measures Table → New Measure**

Name it:

```text
Quantity Sold
```

The intended DAX is:

```DAX
Quantity Sold =
CALCULATE(
    SUM('Fact Table'[Unit Sold]),
    ALL('Date Table 1'),
    USERELATIONSHIP(
        'Date Table 2'[Date],
        'Fact Table'[Date]
    )
)
```

---

# 43. Understand the Quantity Measure

The calculation consists of:

### Expression

```DAX
SUM('Fact Table'[Unit Sold])
```

Calculates total quantity sold.

### Remove Date Filter 1

```DAX
ALL('Date Table 1')
```

Removes the Date Table 1 filter.

### Activate Date Table 2 Relationship

```DAX
USERELATIONSHIP(
    'Date Table 2'[Date],
    'Fact Table'[Date]
)
```

Makes Date Table 2 control this measure.

---

# 44. Add Quantity Sold Measure to the Chart

Select the Total Quantity Sold chart and add:

```text
Quantity Sold
```

Now there are two columns:

* Original `Unit Sold`
* `Quantity Sold` measure

---

# 45. Rename Quantity Legends

Rename the first series:

```text
Quantity 1
```

Rename the second series:

```text
Quantity 2
```

This makes the relationship with the two date filters obvious.

---

# 46. Format Quantity Column Colors

Go to:

**Format Visual → Columns**

Set different colors for the two series.

For example:

```text
Quantity 1 → Color 1
Quantity 2 → Color 2
```

The exact colors can be chosen according to the report design.

---

# 47. Final Testing of Requirement 4

At this stage, there are three comparison visuals:

### 1. Total Sales

```text
Sales 1 | Sales 2
```

### 2. Total Profit

```text
Profit 1 | Profit 2
```

### 3. Total Quantity Sold

```text
Quantity 1 | Quantity 2
```

And two slicers:

```text
Date Filter 1
Date Filter 2
```

---

# 48. Test Date Filter 2

Select a date/range using:

**Date Filter 2**

Expected result:

| Visual              | Column affected |
| ------------------- | --------------- |
| Total Sales         | Sales 2         |
| Total Profit        | Profit 2        |
| Total Quantity Sold | Quantity 2      |

The first columns should remain unchanged.

---

# 49. Test Date Filter 1

Now select a date/range using:

**Date Filter 1**

Expected result:

| Visual              | Column affected |
| ------------------- | --------------- |
| Total Sales         | Sales 1         |
| Total Profit        | Profit 1        |
| Total Quantity Sold | Quantity 1      |

The second columns should remain unchanged.

Therefore, the user can independently select two periods and compare all three metrics.

---

# 50. Final Report Layout

The final page conceptually looks like:

```text
┌──────────────────────────────────────────────────────┐
│ Date Filter 1              Date Filter 2             │
│                                                      │
│              TOTAL SALES                            │
│                 ███   ███                           │
│                Sales1 Sales2                        │
│                                                      │
│              TOTAL PROFIT                           │
│                 ███   ███                           │
│               Profit1 Profit2                       │
│                                                      │
│           TOTAL QUANTITY SOLD                       │
│                 ███   ███                           │
│             Quantity1 Quantity2                     │
└──────────────────────────────────────────────────────┘
```

The exact placement and sizing can be adjusted according to the report design.

---

# 51. Key DAX Pattern to Remember

The most important pattern from this lecture is:

```DAX
Measure =
CALCULATE(
    SUM(FactTable[Column]),
    ALL(DateTable1),
    USERELATIONSHIP(
        DateTable2[Date],
        FactTable[Date]
    )
)
```

This pattern effectively says:

> Calculate the metric using Date Table 2, while ignoring the Date Table 1 filter.

This allows the two date slicers to independently control two different values.

---

# 52. Why the Approach Works

The model contains:

```text
Date Table 1
     |
     | Active
     ↓
Fact Table
     ↑
     | Inactive
     |
Date Table 2
```

### Normal column

The original metric uses the active relationship:

```text
Date Filter 1
     ↓
Date Table 1
     ↓
Fact Table
     ↓
Metric 1
```

### Measure

The DAX measure removes Date Table 1's filtering and activates Date Table 2's relationship:

```text
Date Filter 2
     ↓
Date Table 2
     ↓
USERELATIONSHIP()
     ↓
Fact Table
     ↓
Metric 2
```

Therefore:

```text
Metric 1 ← Date Filter 1
Metric 2 ← Date Filter 2
```

---

# 53. Important Concepts From This Lecture

## `CALENDARAUTO()`

Creates a date table automatically based on dates present in the data model.

```DAX
Date Table 1 = CALENDARAUTO()
```

---

## Active Relationship

Represented by a **solid line** in Model View.

It is used normally by Power BI for filtering.

---

## Inactive Relationship

Represented by a **dotted line**.

It does not normally participate in filtering.

It can be activated within a DAX calculation using:

```DAX
USERELATIONSHIP()
```

---

## `CALCULATE()`

Allows a calculation to be evaluated under modified filter conditions.

---

## `ALL()`

Removes filters from the specified table/column.

Here:

```DAX
ALL('Date Table 1')
```

removes Date Table 1 filtering from the measure.

---

## `USERELATIONSHIP()`

Temporarily uses an inactive relationship during a calculation.

Here:

```DAX
USERELATIONSHIP(
    'Date Table 2'[Date],
    'Fact Table'[Date]
)
```

makes Date Table 2 control the measure.

---

## Measures Table Best Practice

Instead of scattering measures throughout different tables, create a dedicated:

```text
Measures Table
```

and store your measures there.

---

# 54. Common Mistake Highlighted in the Lecture

While creating **Total Profit**, the lecturer initially used:

```DAX
SUM(Fact Table[Net Sales])
```

instead of:

```DAX
SUM(Fact Table[Profit])
```

As a result, the Total Profit visual showed the **sales value** rather than the profit value.

### Lesson

When a visual produces an unexpected result:

1. Open the measure.
2. Check the underlying expression.
3. Verify the column being aggregated.
4. Verify the filters.
5. Verify the relationship being activated.

---

# 55. Final Requirement 4 Result

Requirement 4 is successfully fulfilled by providing:

### Two independent date selectors

```text
Date Filter 1
Date Filter 2
```

### Three comparison charts

```text
Total Sales
Total Profit
Total Quantity Sold
```

The user can select **any two periods** and independently compare:

```text
Sales
Profit
Quantity Sold
```

between those periods.

Finally, the page is renamed:

**Requirement Four**

by:

1. Double-clicking the page name.
2. Pressing `Ctrl + A`.
3. Entering:

```text
Requirement Four
```

4. Pressing **Enter**.

The lecture concludes by noting that the **next session will cover Approach 2** for achieving the same requirement.
