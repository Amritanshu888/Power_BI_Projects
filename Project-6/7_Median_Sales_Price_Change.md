# Power BI – Median Sales Price Change by Region

## 1. Session Overview

In this session, another visual is added to the **House Market Overview** report page.

### Objective

The goal is to create a **bar chart** that represents:

> **Median Sales Price Change by Region**

To achieve this, two things are required:

1. Create a **DAX measure** to calculate the median sales price change.
2. Create a **bar chart** using:

   * Median Sales Price Change
   * Region

---

# 2. Business Requirement

The report should show how the **median sales price has changed** between:

* The **latest/highest year** available in the dataset.
* The **previous year**.

The result should then be displayed separately for each **region**.

Conceptually:

```text
Latest Year Median Price
          ↓
        Compare
          ↓
Previous Year Median Price
          ↓
Calculate Change
          ↓
Show by Region
```

---

# 3. Creating the DAX Measure

The first step is to create a measure.

### Steps

1. Go to the **Data pane**.
2. Locate the **Housing** table.
3. Right-click the Housing table.
4. Select:

> **New Measure**

5. Expand the formula bar.
6. Name the measure:

```text
Median Sales Price Change
```

---

# 4. Why Variables Are Used

The instructor uses the `VAR` concept to divide the calculation into separate logical pieces.

Two variables are required:

```text
Current Median Price
Previous Year Median Price
```

Then the `RETURN` statement calculates the change between them.

The overall structure is:

```text
VAR Current Median Price = ...
VAR Previous Median Price = ...

RETURN
    IF(...)
```

---

# 5. Current Median Price

The first variable is:

> **Current Median Price**

This represents the median purchase price for the **maximum/highest year** in the dataset.

The instructor uses the:

> `MEDIANX()`

function.

---

## 5.1 MEDIANX()

`MEDIANX()` is an iterator function.

Its basic structure is:

```text
MEDIANX(
    Table,
    Expression
)
```

The instructor uses it because the median needs to be calculated over the filtered set of records.

---

# 6. Filtering the Current Year

Inside `MEDIANX()`, the instructor uses:

> `FILTER()`

The Housing table is filtered so that only records belonging to the **maximum year** are considered.

Conceptually:

```text
FILTER(
    Housing,
    YEAR(Date) = YEAR(MAX(Date))
)
```

This means:

> Keep only those records whose year is equal to the year of the latest date in the dataset.

---

# 7. Purchase Price as the Median Expression

After specifying the filtered table, the expression whose median is required is:

> **Purchase Price**

Therefore, the current median price is conceptually:

```text
Current Median Price =
MEDIANX(
    FILTER(
        Housing,
        YEAR(Date) = YEAR(MAX(Date))
    ),
    Purchase Price
)
```

So the process is:

```text
Housing Data
     ↓
Find Maximum Date
     ↓
Extract Maximum Year
     ↓
Filter Housing to Maximum Year
     ↓
Take Median of Purchase Price
     ↓
Current Median Price
```

---

# 8. Previous Year Median Price

The second variable is:

> **Previous Year Median Price**

This calculates the median purchase price for the year immediately before the maximum year.

For example, if:

```text
Maximum Year = 2025
```

then:

```text
Previous Year = 2024
```

---

# 9. Filtering the Previous Year

Again, the instructor uses:

> `MEDIANX()`

and:

> `FILTER()`

The difference is that the year condition becomes:

```text
YEAR(Date) = YEAR(MAX(Date)) - 1
```

Conceptually:

```text
Previous Median Price =
MEDIANX(
    FILTER(
        Housing,
        YEAR(Date) = YEAR(MAX(Date)) - 1
    ),
    Purchase Price
)
```

The Purchase Price column is again used as the expression.

---

# 10. Calculating Median Sales Price Change

After calculating both variables, the instructor uses:

> `RETURN`

followed by an `IF()` condition.

The calculation is:

$$
\text{Median Sales Price Change}
=
\frac{\text{Current Median Price} - \text{Previous Median Price}}
{\text{Previous Median Price}}
$$

Conceptually:

```text
Current Median Price
        -
Previous Median Price
        ↓
Difference
        ↓
Divide by Previous Median Price
        ↓
Median Sales Price Change
```

---

# 11. Protecting Against Division by Zero

The instructor checks whether:

```text
Previous Median Price <> 0
```

If it is not zero, the percentage/change calculation is performed.

Otherwise:

```text
BLANK()
```

is returned.

Conceptually:

```text
IF(
    Previous Median Price <> 0,
    (Current Median Price - Previous Median Price)
        / Previous Median Price,
    BLANK()
)
```

### Why?

Because dividing by zero is invalid.

The `IF()` condition prevents this issue.

---

# 12. Complete DAX Logic

The lecture's DAX can be represented conceptually as:

```text
Median Sales Price Change =
VAR CurrentMedianPrice =
    MEDIANX(
        FILTER(
            Housing,
            YEAR(Housing[Date]) = YEAR(MAX(Housing[Date]))
        ),
        Housing[Purchase Price]
    )

VAR PreviousMedianPrice =
    MEDIANX(
        FILTER(
            Housing,
            YEAR(Housing[Date]) = YEAR(MAX(Housing[Date])) - 1
        ),
        Housing[Purchase Price]
    )

RETURN
    IF(
        PreviousMedianPrice <> 0,
        (CurrentMedianPrice - PreviousMedianPrice)
            / PreviousMedianPrice,
        BLANK()
    )
```

The exact table/column syntax may vary depending on how the model is named, but this captures the calculation demonstrated in the lecture.

---

# 13. Important Difference From the Previous Session

In the previous session, the instructor created:

> **Year on Year Sales Growth**

Here, the calculation is based on:

> **Median Sales Price**

rather than total sales/purchase price.

### Previous KPI

```text
SUM(Purchase Price)
```

### Current KPI

```text
MEDIAN(Purchase Price)
```

More specifically, the lecture uses:

```text
MEDIANX()
```

over a filtered table.

This is important because **median is less influenced by extreme values/outliers than an average** and is often useful for representing a typical property price.

---

# 14. Creating the Bar Chart

Once the measure has been created, it needs to be represented visually.

### Steps

1. Click on a **blank area of the report canvas**.
2. Select:

> **Stacked Bar Chart**

3. A blank bar chart is created.

---

# 15. Adding Median Sales Price Change

The newly created measure:

> `Median Sales Price Change`

is added to the chart.

### Steps

1. Locate `Median Sales Price Change` in the Data pane.
2. Drag and drop it into the:

> **X-axis**

bucket.

Because this is a **horizontal bar chart**, the numerical value is represented along the X-axis.

---

# 16. Adding Region

The objective is to show the median sales price change for different regions.

### Steps

1. Locate the:

> `Region`

field.

2. Drag and drop it into the:

> **Y-axis**

bucket.

The chart will now contain:

```text
X-axis → Median Sales Price Change
Y-axis → Region
```

---

# 17. Understanding the Final Chart

The bar chart allows comparison of median sales price change across the different regions.

Conceptually:

```text
Region A  █████████
Region B  ██████
Region C  ███████████
Region D  ████
```

The length of each bar represents the **median sales price change** for that region.

---

# 18. Applying Existing Formatting

Rather than manually formatting the bar chart from scratch, the instructor copies formatting from an existing visual.

### Steps

1. Select the existing **scatter plot**.
2. Click:

> **Format Painter**

3. Click the newly created **bar chart**.

This applies the existing visual styling to the bar chart.

---

# 19. Removing the Zoom Slider

After applying the formatting, the instructor notices that a **zoom slider** is visible.

The instructor does not want the zoom slider on this bar chart.

### Steps

1. Select the bar chart.
2. Open:

> **Format Visual**

3. Find:

> **Zoom Slider**

4. Change it to:

> **Off**

The zoom slider is now removed.

---

# 20. Final Bar Chart Configuration

The completed visual represents:

> **Median Sales Price Change by Region**

### Field configuration

| Chart Component | Field                     |
| --------------- | ------------------------- |
| Visual          | Stacked Bar Chart         |
| X-axis          | Median Sales Price Change |
| Y-axis          | Region                    |
| Zoom Slider     | Off                       |

---

# 21. Renaming the Report Page

At the end of the session, the instructor renames the report page.

The page was initially called:

> **Page 1**

It is renamed to:

> **House Market Overview**

### Steps

1. Locate the page tab at the bottom of Power BI.
2. Double-click the page name.
3. Select the existing name.
4. Press `Ctrl + A`.
5. Enter:

```text
House Market Overview
```

6. Press **Enter**.

---

# 22. Current Report Page – Visuals So Far

At this point, the report page contains several visuals created during the previous sessions.

### 1. Line Chart

**Year on Year Sales Growth by Sales Type**

Uses:

```text
X-axis → Sales Type
Y-axis → Year on Year Sales Growth
```

---

### 2. Scatter Plot

**Offer Price versus Purchase Price**

Uses:

```text
Offer Price
Purchase Price
```

and is used to analyze the relationship between the two numerical variables.

---

### 3. Bar Chart

**Median Sales Price Change by Region**

Uses:

```text
X-axis → Median Sales Price Change
Y-axis → Region
```

---

# 23. Important DAX Concepts From This Session

## `MEDIANX()`

Used to calculate the median of an expression over a table.

Structure:

```text
MEDIANX(Table, Expression)
```

In this case:

```text
MEDIANX(
    Filtered Housing Table,
    Purchase Price
)
```

---

## `FILTER()`

Used to restrict the Housing table to a specific year.

For current year:

```text
YEAR(Date) = YEAR(MAX(Date))
```

For previous year:

```text
YEAR(Date) = YEAR(MAX(Date)) - 1
```

---

## `MAX()`

Used to identify the latest date available in the dataset.

```text
MAX(Date)
```

---

## `YEAR()`

Used to extract the year from the maximum date.

```text
YEAR(MAX(Date))
```

---

## `VAR`

Used to store intermediate results:

```text
VAR CurrentMedianPrice = ...
VAR PreviousMedianPrice = ...
```

This makes the calculation easier to structure and read.

---

## `RETURN`

Specifies the final calculation that should be returned by the measure.

---

## `IF()`

Used to prevent division by zero:

```text
IF(
    PreviousMedianPrice <> 0,
    calculation,
    BLANK()
)
```

---

## `BLANK()`

Returns an empty result when the previous year's median price is zero.

---

# 24. Why Median Is Used

The session specifically asks for **median sales price change**, not average sales price change.

For property data, this can be useful because property prices can contain extreme values.

For example:

```text
₹50L
₹55L
₹60L
₹65L
₹5Cr
```

The very expensive property can significantly affect the **average**, whereas the **median** provides a more representative middle value.

Therefore, median can be useful when analyzing property prices with potentially skewed distributions.

---

# 25. Complete Workflow

The complete process from the beginning of the session is:

```text
Housing Table
      ↓
Right-click Housing
      ↓
New Measure
      ↓
Name → Median Sales Price Change
      ↓
Calculate Current Median Price
      ↓
Filter to Maximum Year
      ↓
MEDIANX(Purchase Price)
      ↓
Calculate Previous Median Price
      ↓
Filter to Maximum Year - 1
      ↓
MEDIANX(Purchase Price)
      ↓
Calculate:
(Current Median - Previous Median)
÷ Previous Median
      ↓
Check Previous Median ≠ 0
      ↓
Return BLANK if zero
      ↓
Create Stacked Bar Chart
      ↓
X-axis → Median Sales Price Change
      ↓
Y-axis → Region
      ↓
Use Format Painter
      ↓
Turn Zoom Slider Off
      ↓
Rename Page
      ↓
House Market Overview
```

---

# 26. Quick Revision Notes

### Requirement

> Show **Median Sales Price Change by Region**.

### Measure

```text
Median Sales Price Change
```

### Current year

```text
YEAR(MAX(Date))
```

### Previous year

```text
YEAR(MAX(Date)) - 1
```

### Current median

```text
MEDIANX(
    FILTER(Housing, Year = Maximum Year),
    Purchase Price
)
```

### Previous median

```text
MEDIANX(
    FILTER(Housing, Year = Maximum Year - 1),
    Purchase Price
)
```

### Change

$$
\boxed{
\frac{Current\ Median - Previous\ Median}
{Previous\ Median}
}
$$

### Visual

```text
Stacked Bar Chart

X-axis → Median Sales Price Change
Y-axis → Region
```

### Formatting

* Copy formatting using **Format Painter**.
* Turn **Zoom Slider → Off**.

### Page name

> **House Market Overview**

---

# 27. Key Takeaways

1. A **DAX measure** is created to calculate median sales price change.
2. `MEDIANX()` is used instead of `SUM()` because the requirement is to calculate a **median**.
3. `FILTER()` restricts the calculation to the desired year.
4. `MAX(Date)` identifies the latest date/year.
5. The previous year is obtained using **maximum year − 1**.
6. The percentage change is calculated as:

$$
\frac{Current - Previous}{Previous}
$$

7. An `IF()` check prevents division by zero.
8. A **stacked bar chart** is used to compare the result across regions.
9. The chart uses:

   * **X-axis → Median Sales Price Change**
   * **Y-axis → Region**
10. **Format Painter** is used to maintain consistency with the existing report.
11. The **Zoom Slider** is turned off.
12. The report page is renamed **House Market Overview**.
13. The session adds another KPI/visual to the growing **House Market Overview** report.
