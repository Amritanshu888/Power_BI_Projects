# Power BI — Creating “Default Rate by Year” Visual

## 1. Objective

The objective of this session is to add the **last visual to the first report page**.

The visual will represent:

> **Default Rate by Year (%)**

To create this visual, we first need to create a new DAX measure called **Default Rate by Year**.

The important concept in this measure is the use of:

* `VAR`
* `CALCULATE()`
* `COUNTROWS()`
* `FILTER()`
* `ALLExcept()`
* `DIVIDE()`

The measure is specifically designed so that the **Year filter is retained**, while other filters are ignored for the calculation.

---

# 2. Create the “Default Rate by Year” Measure

### Steps

1. Go to the **Data/Fields pane**.
2. Right-click **Measures Table 1**.
3. Select **New Measure**.
4. Expand the formula bar.
5. Name the measure:

**Default Rate by Year**

---

# 3. Create the `total loans` Variable

The first variable will calculate the total number of loans.

Start by declaring a variable:

```DAX
VAR total_loans =
```

Then use `CALCULATE()`.

The structure is:

```DAX
VAR total_loans =
    CALCULATE(
        COUNTROWS('Loan Default'),
        ALLEXCEPT('Loan Default', 'Loan Default'[Year])
    )
```

### Explanation

#### `COUNTROWS()`

```DAX
COUNTROWS('Loan Default')
```

counts the number of rows in the **Loan Default** table.

In this context, each row represents a loan record, so this gives us the total number of loans.

---

# 4. Use `ALLEXCEPT()` to Keep Only the Year Filter

The important part of the calculation is:

```DAX
ALLEXCEPT('Loan Default', 'Loan Default'[Year])
```

`ALLEXCEPT()` removes filters from the specified table **except** the filter(s) explicitly mentioned.

Here, we specify:

```DAX
'Loan Default'[Year]
```

Therefore:

> Keep the **Year** filter, while removing the other filters affecting the Loan Default table.

This is important because the visual needs to show the default rate **for each year**.

For example:

```text
2020 → calculate default rate for 2020
2021 → calculate default rate for 2021
2022 → calculate default rate for 2022
...
```

The Year filter must therefore remain active.

---

# 5. Create the `default` Variable

The second variable calculates the number of default cases.

Create another variable:

```DAX
VAR default =
```

Then use `CALCULATE()` again.

However, this time we need to count only those records where the **Default** column is `TRUE`.

The basic structure is:

```DAX
VAR default =
    CALCULATE(
        COUNTROWS(
            FILTER(
                'Loan Default',
                'Loan Default'[Default] = TRUE
            )
        ),
        ALLEXCEPT('Loan Default', 'Loan Default'[Year])
    )
```

---

# 6. Understand the `FILTER()` Function

Inside `COUNTROWS()`, the lecture uses `FILTER()`:

```DAX
FILTER(
    'Loan Default',
    'Loan Default'[Default] = TRUE
)
```

This filters the Loan Default table so that only records satisfying:

```text
Default = TRUE
```

are retained.

Then `COUNTROWS()` counts those filtered rows.

Therefore:

> `default` = number of loans that went into default.

---

# 7. Apply the Year Filter to Default Cases

The `default` variable also uses:

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Year]
)
```

This ensures that the calculation retains the **Year** filter while removing other filters.

So the measure calculates the number of default cases separately for each year.

---

# 8. Calculate the Default Rate

After defining both variables, return the ratio between default loans and total loans.

Use:

```DAX
RETURN
    DIVIDE(default, total_loans) * 100
```

### Why `DIVIDE()`?

Instead of simply writing:

```DAX
default / total_loans
```

the `DIVIDE()` function is used because it is designed to handle division more safely, particularly when the denominator could be zero or blank.

### Why multiply by 100?

Normally:

```DAX
DIVIDE(default, total_loans)
```

returns a ratio.

For example:

```text
0.12
```

Multiplying by 100 gives:

```text
12
```

which represents a **12% default rate**.

---

# 9. Complete DAX Measure

The complete measure created in the lecture can be represented as:

```DAX id="8b9m8q"
Default Rate by Year =
VAR total_loans =
    CALCULATE(
        COUNTROWS('Loan Default'),
        ALLEXCEPT(
            'Loan Default',
            'Loan Default'[Year]
        )
    )
VAR default =
    CALCULATE(
        COUNTROWS(
            FILTER(
                'Loan Default',
                'Loan Default'[Default] = TRUE
            )
        ),
        ALLEXCEPT(
            'Loan Default',
            'Loan Default'[Year]
        )
    )
RETURN
    DIVIDE(default, total_loans) * 100
```

After entering the formula:

1. Press **Enter**.
2. Power BI may take some time to create the measure.
3. The **Default Rate by Year** measure will now be available.

---

# 10. Create the Line Chart

The lecture uses another line chart to represent the result.

Instead of creating a completely new visual:

1. Select the existing **Average Loan Amount by Age Group** line chart.
2. Press **Ctrl + C**.
3. Press **Ctrl + V**.
4. Move the newly copied chart to the **right-hand side** of the report page.

---

# 11. Remove the Existing Fields

The copied chart contains fields from the previous visualization.

Remove:

* **Age Group**
* **Average Loan by Age Group**

These fields are no longer required.

---

# 12. Add the Default Rate by Year Measure

From the Measures table:

1. Locate **Default Rate by Year**.
2. Check the box next to it.

This measure will become the value represented on the chart.

---

# 13. Add Year to the Chart

Now add Year from the **Loan Default** table.

1. Expand the **Loan Default** table.
2. Locate the **Year** column.
3. Check the box next to **Year**.

Power BI may initially place Year into the **Y-axis** and summarize it as:

> **Sum of Year**

We do not want Year to be summed.

Year is a categorical/time dimension and should be used as the X-axis.

---

# 14. Move Year from Y-axis to X-axis

### Steps

1. Locate **Sum of Year** under the **Y-axis** bucket.
2. Drag and drop it into the **X-axis** bucket.

Now the chart will display:

* **X-axis → Year**
* **Y-axis → Default Rate by Year**

The chart will show different default-rate values for the different years.

Conceptually:

```text
Year        Default Rate
------------------------
Year 1      Rate %
Year 2      Rate %
Year 3      Rate %
Year 4      Rate %
...
```

---

# 15. Change the Chart Title

The default title should be changed to clearly describe the visual.

### Steps

1. Select the chart.
2. Open **Format visual**.
3. Go to **General**.
4. Expand **Title**.
5. Change the title to:

**Default Rate by Year (Percentages)**

The lecture describes the title as:

> **Default Rate by Year (percentages)**

The important point is to make it clear that the chart represents the default rate by year and that the values are percentages.

---

# 16. Change the Line Color

The line color is also customized.

### Steps

1. Select the chart.
2. Open **Format visual**.
3. Go to the **Lines** formatting section.
4. Locate **Color**.
5. Select **More colors**.
6. Enter:

**#F2D2E2**

7. Press **Enter**.

This changes the line color of the chart.

---

# 17. Additional Chart Formatting

The lecture demonstrates several optional formatting changes.

## A. Turn Off Grid Lines

If you don't want grid lines:

1. Select the chart.
2. Open **Format visual**.
3. Locate **Grid lines**.
4. Turn **Vertical grid lines** to **Off**.

This produces a cleaner-looking chart.

---

## B. Change the Smooth Type

Under the line formatting options, the smooth type can be changed.

For example:

* **Monotone**
* **Cardinal**

The lecture demonstrates changing the smooth type from **Monotone** to **Cardinal**.

You can choose whichever appearance works best.

---

## C. Change the Interpolation Type

The interpolation type can also be changed.

Possible choices can include options such as:

* Smooth
* Step

The lecture considers changing it to Step but ultimately keeps the chart **smooth**.

---

## D. Change Line Width

The line width can also be adjusted.

You can:

* Increase the width to make the line more prominent.
* Decrease the width to make it thinner.

The instructor reduces the width and notes that the chart still clearly communicates the insights.

---

# 18. Difference Between “Default Rate by Employment Type” and “Default Rate by Year”

An important concept covered toward the end of the lecture is the difference between the new measure and a previously created measure.

Previously, a measure called:

> **Default Rate by Employment Type**

was created.

The new measure is:

> **Default Rate by Year**

The primary difference is the field used inside `ALLEXCEPT()`.

---

# 19. Previous Measure — Default Rate by Employment Type

The earlier measure used:

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

This means:

> Keep the **Employment Type** filter while removing other filters.

Therefore, the calculation changes according to Employment Type.

For example:

```text
Salaried       → Default Rate
Self-employed  → Default Rate
Business       → Default Rate
...
```

---

# 20. New Measure — Default Rate by Year

The new measure uses:

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Year]
)
```

This means:

> Keep the **Year** filter while removing the other filters.

Therefore, the calculation changes according to Year.

For example:

```text
2020 → Default Rate
2021 → Default Rate
2022 → Default Rate
...
```

---

# 21. Core Difference

The difference can be summarized as:

| Measure                         | Field preserved by `ALLEXCEPT()` | Purpose                         |
| ------------------------------- | -------------------------------- | ------------------------------- |
| Default Rate by Employment Type | Employment Type                  | Default rate by employment type |
| Default Rate by Year            | Year                             | Default rate by year            |

So the fundamental change is:

```DAX
-- Employment Type version
ALLEXCEPT('Loan Default', 'Loan Default'[Employment Type])
```

versus:

```DAX
-- Year version
ALLEXCEPT('Loan Default', 'Loan Default'[Year])
```

This is the key concept to remember.

---

# 22. Why `ALLEXCEPT()` Is Important Here

Suppose the report page contains multiple filters or slicers.

Without controlling the filter context, the default-rate calculation could be affected by filters that we don't want to consider for this particular visual.

Using:

```DAX
ALLEXCEPT('Loan Default', 'Loan Default'[Year])
```

allows us to essentially say:

> "For this calculation, ignore other filters on the Loan Default table, but continue calculating separately for each Year."

This makes the measure specifically suited for a **Default Rate by Year** analysis.

---

# 23. Overall Calculation Logic

The entire calculation can be understood as:

```text id="g4kv30"
                    Loan Default Table
                           │
             ┌─────────────┴─────────────┐
             ↓                           ↓
        Count all loans             Filter Default = TRUE
             │                           │
             ↓                           ↓
        Total Loans                 Default Loans
             │                           │
             └─────────────┬─────────────┘
                           ↓
                 Default ÷ Total Loans
                           ↓
                         × 100
                           ↓
                   Default Rate %
                           │
                           ↓
                    Grouped by Year
```

The resulting line chart therefore shows how the **default rate changes over the years**.

---

# 24. Final Report Visual Configuration

The final visual should have:

| Property      | Configuration                         |
| ------------- | ------------------------------------- |
| Visual        | Line Chart                            |
| X-axis        | Year                                  |
| Y-axis        | Default Rate by Year                  |
| Title         | Default Rate by Year (Percentages)    |
| Line color    | `#F2D2E2`                             |
| Interpolation | Smooth                                |
| Grid lines    | Vertical grid lines can be turned off |
| Smooth type   | Monotone/Cardinal as desired          |
| Line width    | Adjusted as required                  |

---

# 25. Important DAX Concepts from This Session

### `VAR`

Variables allow intermediate calculations to be stored and reused.

```DAX
VAR total_loans = ...
VAR default = ...
RETURN ...
```

This makes a complex measure easier to understand.

### `COUNTROWS()`

Counts rows in a table.

```DAX
COUNTROWS('Loan Default')
```

### `FILTER()`

Creates a filtered table based on a condition.

```DAX
FILTER(
    'Loan Default',
    'Loan Default'[Default] = TRUE
)
```

### `CALCULATE()`

Changes the filter context under which an expression is evaluated.

### `ALLEXCEPT()`

Removes filters while preserving specified filters.

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Year]
)
```

### `DIVIDE()`

Divides one expression by another in a safer DAX-friendly way.

```DAX
DIVIDE(default, total_loans)
```

### Multiplication by 100

Converts the ratio into a percentage-style numeric value:

```DAX
DIVIDE(default, total_loans) * 100
```

---

# 26. Complete Workflow

```text id="b2b3j0"
Right-click Measures Table 1
        ↓
Select New Measure
        ↓
Name → Default Rate by Year
        ↓
Create total_loans variable
        ↓
COUNTROWS(Loan Default)
        ↓
Use ALLEXCEPT → preserve Year
        ↓
Create default variable
        ↓
FILTER Default = TRUE
        ↓
COUNTROWS(filtered records)
        ↓
Use ALLEXCEPT → preserve Year
        ↓
RETURN
        ↓
DIVIDE(default, total_loans) × 100
        ↓
Create/copy Line Chart
        ↓
Remove Age Group
        ↓
Remove Average Loan by Age Group
        ↓
Add Default Rate by Year
        ↓
Add Year
        ↓
Move Year → X-axis
        ↓
Format chart
        ↓
Change title
        ↓
Change line color
        ↓
Optional formatting
        ↓
Default Rate by Year chart complete
```

---

## Final Takeaways

1. **Default Rate by Year** is created as a separate DAX measure even though a Default Rate measure already exists.
2. The measure calculates:
   **Default Loans ÷ Total Loans × 100**.
3. `FILTER()` is used to identify records where **Default = TRUE**.
4. `ALLEXCEPT()` is crucial because it preserves the **Year filter** while removing other filters from the Loan Default table.
5. The line chart uses:

   * **Year → X-axis**
   * **Default Rate by Year → Y-axis**
6. The previously created **Default Rate by Employment Type** measure uses `Employment Type` inside `ALLEXCEPT()`, whereas the new measure uses `Year`.
7. The next session will focus on **data validation of the Default Rate by Year calculation**.
