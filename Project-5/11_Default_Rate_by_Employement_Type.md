# Power BI — Default Rate by Employment Type, DAX Measure & Data Validation

## 1. Session Overview

In this session, the report is extended by adding a new visual to represent:

> **Default Rate by Employment Type**

The session covers several important Power BI concepts:

* Copying and formatting existing visuals
* Aligning visuals
* Creating a DAX measure
* Using **variables in DAX**
* Using `COUNTROWS()`
* Using `ALL()`
* Using `FILTER()`
* Using `CALCULATE()`
* Using `DIVIDE()`
* Using `ALLEXCEPT()`
* Understanding the difference between `ALL()` and `ALLEXCEPT()`
* Formatting a line chart
* Converting a ratio into a percentage
* Validating Power BI results against the source Excel data
* Validating DAX calculations manually

The final visual represents the **percentage of default cases for each employment type**.

---

# 2. Requirement — Default Rate by Employment Type

The requirement is:

> Create a visual showing the **default rate for different employment types**.

For example, the report should allow us to compare default rates for categories such as:

* Full-time
* Part-time
* Self-employed
* Unemployed
* Other available employment categories

The final result will be a line chart where:

```text
X-axis → Employment Type

Y-axis → Default Rate (%)
```

---

# 3. Correcting the Visual/Page Text

Before creating the new visual, the instructor corrects a spelling mistake in an existing visual/title.

### Steps

1. Select the relevant visual.
2. Open the **Visualizations** pane.
3. Go to:

**General → Style**

4. Correct the spelling of the relevant text/title.

The same correction is also made for another name by double-clicking it and correcting the spelling.

Power BI may take a short amount of time to apply the change.

---

# 4. Reuse an Existing Line Chart

Instead of creating a new line chart from scratch, the instructor uses an existing line chart.

The existing chart represents:

> **Average Income by Employment Type**

Since the new visual will also use:

> **Employment Type**

on the X-axis, the existing chart can be copied and modified.

### Steps

1. Select the existing line chart.
2. Press:

**Ctrl + C**

3. Press:

**Ctrl + V**

This creates a copy of the chart.

4. Move the copied chart to the right-hand side.
5. Position it next to the existing chart.

---

# 5. Resize and Align the Charts

The instructor adjusts the sizes of the charts to make the report layout cleaner.

### Steps

1. Select the first chart.
2. Resize it using the handles.
3. Select the second chart.
4. Resize it similarly.

To select both charts:

> Hold **Ctrl** and click each visual.

Then use the formatting/alignment options to:

> **Align Horizontally**

This helps ensure that the visuals are positioned neatly on the same horizontal level.

---

# 6. Remove Existing Fields from the Copied Chart

The copied chart still contains the fields from the original visual:

* Employment Type
* Average Income

These fields need to be removed because the new chart will represent:

> **Default Rate by Employment Type**

### Steps

1. Select the copied/third chart.
2. Remove:

   * `Employment Type`
   * `Average Income`
3. The chart is now ready to receive the new DAX measure and fields.

---

# 7. Create a New DAX Measure

The instructor creates a DAX measure to calculate the default rate.

### Steps

1. Locate the **Measures** table.
2. Right-click the Measures table.
3. Select:

> **New Measure**

A DAX formula bar appears.

The measure is named:

> **Default Rate by Employment Type**

---

# 8. DAX Measure — Overall Logic

The default rate is calculated as:

$$
\text{Default Rate} =
\frac{\text{Number of Default Cases}}
{\text{Total Number of Records}}
$$

In this project:

```text
Default Rate
      =
Default Cases ÷ Total Records
```

Later, the result is multiplied by `100` to display it as a percentage.

---

# 9. Use Variables in the DAX Measure

The instructor uses variables to make the DAX calculation easier to understand and manage.

Two variables are created:

1. `total records`
2. `default cases`

Conceptually:

```DAX
VAR total_records = ...
VAR default_cases = ...
RETURN ...
```

Variables allow intermediate results to be stored and then reused in the final calculation.

---

# 10. Variable 1 — Total Records

The first variable calculates the total number of records.

It is named:

> **total records**

The calculation uses:

> `COUNTROWS()`

along with:

> `ALL()`

Conceptually:

```DAX
VAR total_records =
    COUNTROWS(
        ALL('Loan Default')
    )
```

---

# 11. Understanding COUNTROWS()

`COUNTROWS()` returns the number of rows in a table.

For example:

```DAX
COUNTROWS('Loan Default')
```

counts the rows in the Loan Default table.

In this case, however, the instructor combines `COUNTROWS()` with `ALL()`.

---

# 12. Understanding ALL()

The purpose of `ALL()` here is very important.

`ALL()` removes filters from the specified table or column.

The instructor wants:

> **Total records without filters affecting the calculation.**

Therefore:

```DAX
ALL('Loan Default')
```

removes existing filters from the Loan Default table.

Then:

```DAX
COUNTROWS(ALL('Loan Default'))
```

returns the total number of records in the table, regardless of filters.

---

# 13. Variable 2 — Default Cases

The second variable is named:

> **default cases**

Its purpose is to count only records where:

> `Default = TRUE`

The instructor uses:

* `COUNTROWS()`
* `FILTER()`

Conceptually:

```DAX
VAR default_cases =
    COUNTROWS(
        FILTER(
            'Loan Default',
            'Loan Default'[Default] = TRUE
        )
    )
```

---

# 14. Understanding FILTER()

`FILTER()` returns the rows from a table that satisfy a particular condition.

Here, the condition is:

```DAX
'Loan Default'[Default] = TRUE
```

So the filter keeps only those records where:

> Default = True

Therefore:

```text
Loan Default table
       ↓
FILTER()
       ↓
Default = TRUE
       ↓
Only defaulted records
```

---

# 15. Understanding the Default Column

The `Default` column is a Boolean field.

It can contain:

```text
TRUE
FALSE
```

Therefore:

```DAX
'Loan Default'[Default] = TRUE
```

means:

> Select only borrowers who defaulted.

This was already identified during the data-type validation stage.

---

# 16. Return the Default Rate

After defining the two variables, the instructor uses:

> `RETURN`

Then the final calculation uses:

> `CALCULATE()`

and:

> `DIVIDE()`

The basic calculation is:

```DAX
DIVIDE(
    default_cases,
    total_records
)
```

So:

```text
Numerator   = Default Cases
Denominator = Total Records
```

---

# 17. Why DIVIDE() Is Used

Instead of directly writing:

```DAX
default_cases / total_records
```

the instructor uses:

```DAX
DIVIDE(default_cases, total_records)
```

`DIVIDE()` is generally preferred in DAX because it provides safer handling of division operations, particularly when the denominator could be zero.

---

# 18. Use CALCULATE()

The instructor wraps the division inside:

> `CALCULATE()`

The purpose is to control the filter context under which the calculation is evaluated.

The important requirement is:

> The default-rate calculation should be affected by **Employment Type**, but other filters should not affect this particular calculation.

This is where `ALLEXCEPT()` becomes important.

---

# 19. Understanding ALLEXCEPT()

The instructor uses:

> `ALLEXCEPT()`

The purpose of `ALLEXCEPT()` is:

> Remove filters except for the columns explicitly specified.

Conceptually:

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

This means:

```text
Remove other filters
       ↓
Keep Employment Type filter
```

---

# 20. Why ALLEXCEPT() Is Used Here

Suppose the report contains:

* Employment Type
* Education slicer
* Marital Status slicer
* Loan Purpose slicer
* Other filters

The requirement for this particular measure is that the calculation should be based on:

> **Employment Type**

Therefore, `ALLEXCEPT()` preserves the Employment Type filter while removing other filters from the table.

This allows the measure to calculate the default rate separately for each employment type.

---

# 21. ALL() vs ALLEXCEPT() — Important Interview Question

This is explicitly highlighted in the lecture as an important interview topic.

### `ALL()`

`ALL()` removes filters from the specified table/column.

Example:

```DAX
ALL('Loan Default')
```

means:

> Remove all filters from the Loan Default table.

---

### `ALLEXCEPT()`

`ALLEXCEPT()` removes filters except the filters on the specified column(s).

Example:

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

means:

> Remove filters except the Employment Type filter.

### Easy way to remember

```text
ALL()
 ↓
Remove filters

ALLEXCEPT()
 ↓
Remove filters
BUT
keep specified filter(s)
```

This distinction is particularly important for interviews.

---

# 22. Complete DAX Logic

The measure follows this logical structure:

```DAX
Default Rate by Employment Type =
VAR total_records =
    COUNTROWS(
        ALL('Loan Default')
    )

VAR default_cases =
    COUNTROWS(
        FILTER(
            'Loan Default',
            'Loan Default'[Default] = TRUE
        )
    )

RETURN
    CALCULATE(
        DIVIDE(
            default_cases,
            total_records
        ),
        ALLEXCEPT(
            'Loan Default',
            'Loan Default'[Employment Type]
        )
    )
```

> **Note:** The exact table name in your Power BI model should match the actual table name used in your project.

---

# 23. Create the Line Chart

Once the measure is created, it appears under the Measures table.

Now the third visual can be configured.

### Steps

1. Select the third line chart.
2. Select the newly created measure:

> `Default Rate by Employment Type`

3. Add:

> `Employment Type`

to the:

> **X-axis**

### Final structure

```text
X-axis
→ Employment Type

Y-axis / Values
→ Default Rate by Employment Type
```

Power BI now creates a line chart representing default rates for different employment types.

---

# 24. Format the Line Chart

The instructor then formats the new line chart.

### Change line color

1. Select the line chart.
2. Click:

> **Format Your Visual**

3. Locate the **Lines** section.
4. Choose the line color.

The instructor uses the color code:

> `#84C0C6`

---

# 25. Change Step Position

The instructor also changes the:

> **Step Position**

from:

> Before

to:

> After

This is a formatting/configuration option available for the visual.

---

# 26. Format Markers

Markers can be customized to make individual data points easier to see.

### Steps

1. Expand:

> **Markers**

2. Select a marker style.
3. The instructor chooses:

> **Bubble**

This changes the appearance of the points on the line.

Afterward, the **Markers** and **Lines** sections can be collapsed.

---

# 27. Review the Chart

After formatting, the chart shows different employment categories and their corresponding default-rate values.

The instructor then collapses the:

* Visualizations pane
* Data pane

to get a cleaner view of the report.

---

# 28. Initial Values Are Ratios

At this point, the default-rate values are less than `1`.

For example, a value could look like:

```text
0.0339
```

This is because the DAX calculation currently returns:

$$
\frac{\text{Default Cases}}{\text{Total Records}}
$$

rather than a percentage.

For example:

$$
0.0339 \times 100 = 3.39\%
$$

Therefore, the instructor converts the result into percentage form.

---

# 29. Convert Default Rate to Percentage

### Steps

1. Open the Data pane.
2. Select:

> `Default Rate by Employment Type`

3. Expand the formula bar.
4. Locate the `CALCULATE()` result.
5. Multiply the result by:

> `100`

Conceptually:

```DAX
CALCULATE(
    DIVIDE(
        default_cases,
        total_records
    ),
    ALLEXCEPT(...)
) * 100
```

Now the measure returns percentage values.

For example:

```text
0.0339
```

becomes:

```text
3.39
```

which represents:

> **3.39%**

---

# 30. Rename the Chart Title

The instructor then gives the chart a meaningful title.

### Steps

1. Select the third chart.
2. Open:

**Visualizations → Format Your Visual**

3. Go to:

**General → Title**

4. Change the title/description to:

> **Default Rate by Employment Type (%)**

This clearly communicates what the visual represents.

---

# 31. Data Validation

One of the most important parts of this session is **data validation**.

Creating a DAX measure is not enough.

You should verify that the results produced by Power BI are actually correct.

The instructor validates the result in two ways:

### Validation 1

Using another Power BI table visual.

### Validation 2

Comparing Power BI results with the original Excel source data.

---

# 32. Create a Temporary Table Visual

To validate the numbers, the instructor creates a temporary table.

### Steps

1. Click on a blank area of the canvas.
2. Select a **Table** visual.
3. Expand the Data pane.
4. Collapse the Measures table because the validation will use the original fields directly.

---

# 33. Add Employment Type

From the Loan Default table:

1. Select:

> **Employment Type**

This displays the different employment categories in the table.

---

# 34. Add Default

Next, the instructor selects:

> **Default**

This displays the possible Boolean values:

```text
FALSE
TRUE
```

---

# 35. Count Default Cases

The objective is to determine how many defaulted and non-defaulted records exist for each employment type.

### Steps

1. Drag `Default` into the table.
2. Open its dropdown.
3. Change the aggregation to:

> **Count**

Now Power BI displays the count of:

* False/default = false
* True/default = true

for each employment type.

---

# 36. Total Number of Records

The total shown by the table is:

> **255,347**

This matches the number of records identified during the earlier data-profiling session.

Therefore:

```text
Total Records = 255,347
```

---

# 37. Show Values as Percentage of Grand Total

The instructor then changes the display of the count to:

> **Show value as → Percentage of grand total**

This allows the instructor to compare the percentage of records represented by each category.

This is useful for validating the default-rate calculation.

---

# 38. Validate the Unemployed Category

For the:

> **Unemployed**

employment category, the instructor checks the value where:

> `Default = TRUE`

The percentage is approximately:

> **3.39%**

The same value appears in the newly created Default Rate visual.

Therefore:

```text
Power BI calculated value ≈ 3.39%
Validation table value ≈ 3.39%
```

The numbers match.

---

# 39. Validate the Part-Time Category

The instructor performs the same validation for:

> **Part-time**

where:

> `Default = TRUE`

The percentage shown is approximately:

> **3.01%**

The Default Rate visual also shows approximately:

> **3.01%**

Therefore, this result also matches.

---

# 40. Validate Against the Excel Source

The instructor then performs another important validation step.

Instead of relying only on Power BI calculations, the source Excel file is opened.

The goal is to manually reproduce the default-rate calculation.

This is an important real-world data-analysis practice:

> **Compare the transformed/reporting result against the original source data.**

---

# 41. Filter Excel Data for Default = True

In Excel, the instructor applies a filter to the `Default` column.

### Steps

1. Locate the `Default` column.
2. Search/select `Default`.
3. Apply the filter.
4. Select the value corresponding to:

> **True**

In the source data, the Boolean True value is represented as:

> **1**

So the filter is effectively:

```text
Default = 1
```

---

# 42. Calculate Default Counts in Excel

The instructor removes the existing:

> **Average of Income**

calculation because it is not needed for this validation.

Then:

1. Double-click/drag the `Default` field into the **Values** area.
2. Open **Value Field Settings**.
3. Change the aggregation from:

> Sum

to:

> Count

4. Click **OK**.

Now Excel shows the count of default cases by employment type.

---

# 43. Calculate Default Rate Manually

The default rate is:

$$
\text{Default Rate}
=
\frac{\text{Default Cases}}
{\text{Total Records}}
$$

The total number of records is:

> **255,347**

The instructor enters this value into Excel for each relevant category.

Conceptually:

```text
Employment Type | Default Count | Total Records
------------------------------------------------
Unemployed      | Count         | 255347
Part-time       | Count         | 255347
...
```

Then the formula is:

```text
Default Count ÷ 255347
```

---

# 44. Convert the Excel Result to Percentage

After calculating the ratio, multiply by:

> **100**

to convert it into percentage.

For example:

```text
Default Count / 255347 × 100
```

This produces the default rate percentage.

---

# 45. Excel Validation — Unemployed

For the **Unemployed** category, Excel produces approximately:

> **3.387%**

Power BI displays:

> **3.39%**

The difference is only due to rounding.

Therefore:

> **The values match.**

---

# 46. Excel Validation — Part-Time

For the **Part-time** category, Excel produces approximately:

> **3.00649%**

Power BI displays:

> **3.01%**

Again, the difference is caused by rounding.

Therefore:

> **The Power BI calculation is correct.**

---

# 47. Why Validation Is Important

Data validation ensures that:

> The numbers displayed in the Power BI report are consistent with the underlying/source data.

A useful validation flow is:

```text
Source Data
    ↓
Manual Calculation
    ↓
Power BI Calculation
    ↓
Compare Results
    ↓
Confirm Accuracy
```

If the values don't match, investigate:

* Filters
* Relationships
* Data types
* DAX logic
* Aggregations
* Missing values
* Duplicate records
* Filter context

---

# 48. Important DAX Concepts From This Session

## `COUNTROWS()`

Counts the number of rows in a table.

```DAX
COUNTROWS(Table)
```

---

## `ALL()`

Removes filters from a specified table/column.

```DAX
ALL(Table)
```

---

## `FILTER()`

Returns rows satisfying a specified condition.

```DAX
FILTER(
    Table,
    Condition
)
```

---

## `CALCULATE()`

Evaluates an expression under a modified filter context.

```DAX
CALCULATE(
    Expression,
    Filters
)
```

---

## `DIVIDE()`

Performs division safely.

```DAX
DIVIDE(
    Numerator,
    Denominator
)
```

---

## `ALLEXCEPT()`

Removes filters except those on specified columns.

```DAX
ALLEXCEPT(
    Table,
    Column
)
```

---

# 49. Most Important Interview Concept — ALL vs ALLEXCEPT

| Function      | Behavior                                   |
| ------------- | ------------------------------------------ |
| `ALL()`       | Removes filters                            |
| `ALLEXCEPT()` | Removes filters except specified column(s) |

### Example

```DAX
ALL('Loan Default')
```

→ Removes all filters from Loan Default.

Whereas:

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

→ Removes other filters but retains Employment Type filtering.

### Interview answer

If asked:

**"What is the difference between ALL and ALLEXCEPT?"**

Answer:

> `ALL()` removes filters from the specified table or column, whereas `ALLEXCEPT()` removes filters while preserving the filters on the columns explicitly specified inside the function.

---

# 50. Final Report Structure

After completing the session, the report contains the existing visual for:

> **Average Income by Employment Type**

and a new visual for:

> **Default Rate by Employment Type (%)**

The new visual is a:

> **Line Chart**

with:

```text
X-axis → Employment Type
Y-axis → Default Rate (%)
```

---

# 51. Complete Process Flow

```text
Requirement
    ↓
Default Rate by Employment Type
    ↓
Copy Existing Line Chart
    ↓
Resize & Align
    ↓
Remove Average Income
    ↓
Create DAX Measure
    ↓
Create total_records variable
    ↓
COUNTROWS + ALL
    ↓
Create default_cases variable
    ↓
COUNTROWS + FILTER
    ↓
Default = TRUE
    ↓
RETURN
    ↓
CALCULATE
    ↓
DIVIDE(default cases, total records)
    ↓
ALLEXCEPT(Employment Type)
    ↓
Multiply by 100
    ↓
Default Rate %
    ↓
Add Employment Type to X-axis
    ↓
Format Line Chart
    ↓
Validate in Power BI
    ↓
Validate against Excel
    ↓
Confirm results
```

---

# 52. Key Takeaways

> **1. The requirement is to represent Default Rate by Employment Type.**

> **2. An existing line chart can be copied using `Ctrl + C` and `Ctrl + V` instead of creating a new visual from scratch.**

> **3. The new DAX measure is called `Default Rate by Employment Type`.**

> **4. Variables are used to store `total_records` and `default_cases`.**

> **5. `COUNTROWS()` is used to count records.**

> **6. `ALL()` removes filters from the table.**

> **7. `FILTER()` is used to identify records where `Default = TRUE`.**

> **8. `DIVIDE()` calculates Default Cases ÷ Total Records.**

> **9. `CALCULATE()` modifies the filter context for the calculation.**

> **10. `ALLEXCEPT()` keeps the Employment Type filter while removing other filters.**

> **11. `ALL()` vs `ALLEXCEPT()` is an important Power BI/DAX interview question.**

> **12. The initial DAX result is a ratio, so it is multiplied by 100 to represent a percentage.**

> **13. The chart title is changed to `Default Rate by Employment Type (%)`.**

> **14. The result should always be validated against the source data.**

> **15. The total dataset contains 255,347 records.**

> **16. The Unemployed default rate validates at approximately 3.39%.**

> **17. The Part-time default rate validates at approximately 3.01%.**

> **18. Small differences between Excel and Power BI are due to rounding.**

> **19. Data validation helps confirm that the DAX calculation and report output are accurate.**

### Core formula to remember

$$
\boxed{\text{Default Rate (\%)} =
\frac{\text{Default Cases}}{\text{Total Records}}\times100}
$$

And the DAX concepts to remember from this lecture are:

**`VAR → COUNTROWS → ALL → FILTER → CALCULATE → DIVIDE → ALLEXCEPT`**.
