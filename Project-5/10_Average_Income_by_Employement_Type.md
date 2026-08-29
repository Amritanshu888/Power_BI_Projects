# Detailed Notes — Power BI: Average Income by Employment Type, DAX, Filter Context & Data Validation

## 1. Overview of the Session

In this session, the second visual is created for the **Loan Default and Overview** report page.

### Objective

The second visual will represent:

> **Average Income by Employment Type**

The session also continues the discussion of:

* DAX measures
* `CALCULATE()`
* `AVERAGE()`
* `ALLEXCEPT()`
* Filter context
* Visual interactions
* Data validation
* Validating DAX results against Excel
* Validating DAX results without using DAX
* Formatting line charts

---

# 2. Revisiting the Previous DAX Calculation Without DAX

Before creating the second visual, the lecture revisits the logic used for the first visual.

The first visual represents:

> **Loan Amount by Purpose**

The DAX measure used previously ensured that records where **Loan Amount is blank** were excluded.

The same condition can be implemented without writing DAX by using the **Filters pane**.

---

# 3. Creating a Table Visual for Validation

A temporary table visual is created to demonstrate how the same filtering condition can be applied without a DAX measure.

### Steps

1. Click on a blank area of the report canvas.
2. Select the **Table** visual.
3. A blank table visual is created.
4. Expand the **Loan Default** table in the Data pane.
5. Add **Loan Purpose** to the table.
6. Add **Loan Amount** to the table.

Power BI displays the loan amounts for the different loan-purpose categories.

---

# 4. Applying a "Loan Amount Is Not Blank" Filter

The previous DAX measure included a condition that Loan Amount must not be blank.

The same logic can be implemented through the Filters pane.

### Steps

1. Select the temporary table visual.

2. Open/expand the **Filters pane**.

3. From the Data pane, locate **Loan Amount**.

4. Add **Loan Amount** to the appropriate filter section.

5. Select the **Advanced filtering** option.

6. Specify the condition:

   **Loan Amount is not blank**

7. Click **Apply filter**.

Power BI now excludes rows where Loan Amount is blank.

### Important Concept

The condition implemented through DAX previously:

```DAX id="9mdxv5"
NOT(ISBLANK('Loan Default'[Loan Amount]))
```

can also be implemented through the visual-level filtering functionality.

This demonstrates that certain filtering requirements can be achieved either through:

* DAX
* Power BI's Filters pane

---

# 5. Converting the Table Visual into a Line Chart

The table created for validation can also be converted into a chart.

### Steps

1. Select the table visual.
2. Select the **Line chart** visual type.
3. Power BI converts the visual into a line chart.

The resulting chart represents similar numbers to the original Loan Amount by Purpose chart.

This demonstrates that you can reproduce the result without necessarily using a DAX measure, provided the appropriate fields and filters are applied.

---

# 6. Removing the Temporary Table/Chart

The temporary visual was created only for demonstration and validation.

### Steps

1. Select the temporary table/chart.
2. Press **Delete** on the keyboard.

The visual is removed from the report.

---

# 7. Removing the Filters Pane

The Filters pane is no longer required for the next part of the exercise.

### Steps

1. Go to the **View** tab.
2. Locate **Filters pane**.
3. Click it to hide/remove the pane from the workspace.

---

# 8. Creating the Second DAX Measure

The second visual requires a new DAX measure.

The measure will calculate:

> **Average Income by Employment Type**

The important requirement is that **only Employment Type should affect this measure's result**.

Other filters from visuals or slicers should not affect it.

To achieve this, `ALLEXCEPT()` is used together with `CALCULATE()`.

---

# 9. Creating the `Average Income by Employment Type` Measure

### Steps

1. Go to **Measures Table 1**.

2. Right-click the table.

3. Select **New Measure**.

4. Expand the formula bar.

5. Name the measure:

   **Average Income by Employment Type**

6. Create the DAX measure using:

   * `CALCULATE()`
   * `AVERAGE()`
   * `ALLEXCEPT()`

The conceptual DAX expression is:

```DAX id="sjg4v1"
Average Income by Employment Type =
CALCULATE(
    AVERAGE('Loan Default'[Income]),
    ALLEXCEPT(
        'Loan Default',
        'Loan Default'[Employment Type]
    )
)
```

Press **Enter** to create the measure.

---

# 10. Understanding the `CALCULATE()` Function

`CALCULATE()` is one of the most important DAX functions.

It evaluates an expression after modifying the filter context.

The general structure is:

```DAX id="e83qzz"
CALCULATE(
    Expression,
    Filter1,
    Filter2,
    ...
)
```

In this measure:

```DAX id="g7s6n0"
CALCULATE(
    AVERAGE(...),
    ALLEXCEPT(...)
)
```

the expression being calculated is the average income.

The `ALLEXCEPT()` function modifies which filters are allowed to remain active.

---

# 11. Understanding the `AVERAGE()` Function

The requirement is to calculate **average income**, so the `AVERAGE()` function is used.

The relevant column is:

**Income**

Conceptually:

```DAX id="mxk4hm"
AVERAGE('Loan Default'[Income])
```

This calculates the average value of the Income column within the applicable filter context.

---

# 12. Understanding `ALLEXCEPT()`

The key concept in this measure is `ALLEXCEPT()`.

### Purpose

`ALLEXCEPT()` removes filters from a table **except for the specified column(s)**.

The requirement here is:

> Only the Employment Type filter should affect the average income calculation.

Therefore:

```DAX id="i6d1bq"
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

means:

* Remove other filters from the Loan Default table.
* Keep the filter on **Employment Type**.

---

# 13. Why `ALLEXCEPT()` Is Used

Suppose the report contains multiple visuals or slicers.

If a user selects something in another visual, that selection may normally affect the other visual through Power BI's filter context.

But this particular requirement says:

> The Average Income by Employment Type visual should respond only to Employment Type.

Therefore, `ALLEXCEPT()` is used to preserve only the Employment Type filter.

This is an important example of **filter-context manipulation in DAX**.

---

# 14. Understanding the Filter Interaction Between the Two Visuals

After creating the second visual, the interaction between the two charts is tested.

There are two charts:

### First chart

**Loan Amount by Purpose**

### Second chart

**Average Income by Employment Type**

---

## Selecting the Second Chart

Suppose you select an employment type such as **Unemployed** on the second chart.

The first chart changes.

This means the selection from the second chart is affecting the first chart.

This is expected because the normal visual interaction/filtering behavior is still active.

---

## Selecting the First Chart

Now select a value/category on the first chart.

The second chart does **not** change.

This is the important behavior being demonstrated.

Why?

Because the DAX measure for the second chart uses:

```DAX id="zy0zqf"
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

Therefore, only the **Employment Type** filter is retained for that measure.

Filters coming from other fields/visuals are removed from the calculation.

---

# 15. Important Filter Context Concept

This example demonstrates an important DAX interview concept:

> A measure can be designed to respond to only specific filters while ignoring other filters.

### In this project

The measure:

**Average Income by Employment Type**

responds to:

✅ Employment Type

while ignoring other filters applied to the Loan Default table through the measure's filter context.

This behavior is different from the first measure:

**Loan Amount by Purpose**

which did not use `ALLEXCEPT()`.

Therefore, the first measure is not restricted in the same way.

---

# 16. Creating the Second Line Chart

The second chart is created by duplicating the existing chart to save time and maintain a consistent design.

### Steps

1. Select the existing line chart.

2. Press:

   **Ctrl + C**

3. Press:

   **Ctrl + V**

A duplicate line chart is created.

4. Move the duplicate chart to the **right-hand side** of the first chart.
5. Resize/position the charts as necessary.

---

# 17. Reconfiguring the Duplicate Chart

The duplicated chart initially contains the fields from the first chart.

These fields need to be replaced.

### Remove the existing fields

From the second chart:

* Remove **Loan Purpose** from the X-axis.
* Remove **Loan Amount by Purpose** from the Y-axis.

---

# 18. Adding the New Measure

Now add the newly created measure.

### Steps

1. Locate **Measures Table 1**.
2. Find:

   **Average Income by Employment Type**
3. Drag it into the **Y-axis** bucket.

---

# 19. Adding Employment Type

Now add the field that determines the categories.

### Steps

1. Locate the **Loan Default** table.
2. Find the **Employment Type** column.
3. Add **Employment Type** to the **X-axis** bucket.

The resulting line chart represents:

> **Average Income by Employment Type**

---

# 20. Changing the Chart Title

The duplicated chart initially has the old chart title.

It needs to be changed.

### Steps

1. Select the second chart.
2. Open **Format your visual**.
3. Go to **General**.
4. Expand **Title**.
5. Change the title to:

   **Average Income by Employment Type**

---

# 21. Formatting the Second Line Chart

The second chart can be customized further.

The lecture demonstrates changing the interpolation type.

### Steps

1. Select the second line chart.

2. Open **Format your visual**.

3. Go to the **Lines** section.

4. Locate **Interpolation type**.

5. Change it from:

   **Smooth**

   to:

   **Step**

6. Change the **Step position**.

The lecture selects:

**Before**

This produces a stepped line representation.

---

# 22. Changing the Line Color

The line color can also be customized.

### Steps

1. Select the second chart.
2. Go to the **Lines** settings.
3. Locate **Color**.
4. Select the desired color.

The lecture chooses a different color from the available palette.

The exact color is not essential—the objective is to demonstrate that the visual can be customized.

---

# 23. Validating the Average Income Values Against Excel

The next major step is **data validation**.

The original Excel file is used as the source for comparison.

The objective is to independently calculate:

> Average Income by Employment Type

in Excel and compare those results with Power BI.

---

# 24. Preparing the Excel PivotTable

Open the original Excel data source.

The existing PivotTable may contain fields from the previous validation exercise, so those fields are removed.

### Remove existing fields

Remove:

* Loan Purpose
* Sum of Loan Amount

The PivotTable is now ready for the new validation.

---

# 25. Adding Employment Type to Excel

### Steps

1. In the PivotTable Fields pane, search for:

   **Employment Type**
2. Double-click **Employment Type**.
3. Drag it to the **Rows** section.

The PivotTable now displays the different employment types.

---

# 26. Adding Income to Excel

### Steps

1. Search for:

   **Income**
2. Double-click **Income**.
3. Drag it to the **Values** section.

Excel initially uses:

**Sum of Income**

But the requirement is to calculate the **average**, so the aggregation needs to be changed.

---

# 27. Changing Sum of Income to Average of Income

### Steps

1. Click the dropdown associated with the Income value field.
2. Select **Value Field Settings**.
3. Change the calculation from:

   **Sum**

   to:

   **Average**
4. Click **OK**.

The PivotTable now shows:

> **Average Income for each Employment Type**

---

# 28. Comparing Excel and Power BI

The Excel PivotTable can now be used to validate the Power BI visual.

For example, select the:

**Self-employed**

category.

The Excel PivotTable shows an average income of approximately:

**82,446**

More precisely, the Power BI visual shows:

**82,446.71**

The values correspond.

This confirms that the Power BI DAX measure is producing the expected result.

---

# 29. Validating Without Using DAX

The lecture also demonstrates a second validation method.

Instead of using the DAX measure, a normal Power BI table visual can independently calculate the average.

---

## Steps

1. Click a blank area on the report canvas.
2. Select the **Table** visual.
3. Expand the **Loan Default** table.
4. Add **Employment Type** to the table.
5. Add **Income** to the table.

Power BI initially displays the sum of Income.

---

# 30. Changing the Income Aggregation to Average

### Steps

1. Locate the Income field in the table visual.
2. Open its dropdown.
3. Change the aggregation from:

   **Sum**

   to:

   **Average**

The table now displays average income by employment type.

---

# 31. Three-Way Validation for the Second Visual

The values can now be compared in three places.

### 1. DAX measure

**Average Income by Employment Type**

### 2. Power BI table without the DAX measure

* Employment Type
* Income → Average

### 3. Excel PivotTable

* Employment Type → Rows
* Income → Values → Average

The values should match.

Since the values match across all three, the calculation can be considered validated.

---

# 32. Removing the Temporary Validation Table

The table visual was created only for validation.

### Steps

1. Select the temporary table visual.
2. Press **Delete**.

It is removed from the report.

---

# 33. Additional Formatting of the First Visual

The lecture also demonstrates that the first visual can be further customized.

### Steps

1. Select the first line chart.
2. Open **Format your visual**.
3. Go to **Lines**.
4. Change the **Interpolation type**.
5. Change it from smooth to:

   **Step**

The chart can then be adjusted according to the desired appearance.

---

# 34. Creativity in Report Design

The exact design shown in the lecture is primarily for demonstration/reference.

You can customize:

* Line colors
* Interpolation type
* Step position
* Font
* Font size
* Title
* Marker style
* Marker size
* Data labels
* Borders
* Other visual properties

The important objective is to maintain a professional and consistent report design.

---

# 35. Important DAX Concepts Covered

## `CALCULATE()`

Used to evaluate an expression under a modified filter context.

```DAX id="rxw0pg"
CALCULATE(
    Expression,
    Filter
)
```

---

## `AVERAGE()`

Calculates the average of a column.

```DAX id="l8k0f6"
AVERAGE('Loan Default'[Income])
```

---

## `ALLEXCEPT()`

Removes filters except those explicitly specified.

```DAX id="5af3ut"
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

---

# 36. Complete DAX Measure

The complete measure created in this session is:

```DAX id="2f7t1w"
Average Income by Employment Type =
CALCULATE(
    AVERAGE('Loan Default'[Income]),
    ALLEXCEPT(
        'Loan Default',
        'Loan Default'[Employment Type]
    )
)
```

### Logic in plain English

> Calculate the average Income, but preserve only the Employment Type filter and ignore other filters affecting the Loan Default table.

---

# 37. Difference Between the Two Measures

| Feature             | Loan Amount by Purpose                | Average Income by Employment Type   |
| ------------------- | ------------------------------------- | ----------------------------------- |
| Main calculation    | Loan Amount                           | Income                              |
| Aggregation         | Sum                                   | Average                             |
| Main category       | Loan Purpose                          | Employment Type                     |
| Important functions | `SUMX`, `FILTER`, `NOT`, `ISBLANK`    | `CALCULATE`, `AVERAGE`, `ALLEXCEPT` |
| Blank handling      | Explicitly excludes blank Loan Amount | No explicit blank filter            |
| Filter behavior     | Normal filter context                 | Keeps only Employment Type filter   |
| Purpose             | Loan amount analysis                  | Average income analysis             |

---

# 38. Key Data Validation Methods

This session demonstrates two major ways to validate a Power BI calculation.

### Method 1 — Validate inside Power BI

Create a simple table visual using the original fields and apply the required aggregation.

For this session:

* Employment Type
* Income → Average

Compare it against the DAX measure.

### Method 2 — Validate against the original source

Use the original Excel file.

Create a PivotTable:

* Employment Type → Rows
* Income → Values
* Values → Average

Compare those numbers against Power BI.

---

# 39. Important Real-World Learning

The session reinforces that **data validation is not optional when working with real-world Power BI reports**.

If a report shows an unexpected value:

1. Don't immediately assume the DAX is correct.
2. Reproduce the result using the raw fields.
3. Compare the result with the DAX measure.
4. Compare it with the source data.
5. Trace the data pipeline if necessary.
6. Correct the issue.
7. Validate the result again.

This is especially important during the development phase of Power BI projects.

---

# 40. Important Filter-Context Example

The most important conceptual demonstration in this session is the behavior of the two charts.

### When selecting Employment Type on Chart 2

**Chart 1 changes.**

This shows that the Employment Type selection can filter the other visual.

### When selecting Loan Purpose on Chart 1

**Chart 2 does not change.**

This is because the second measure uses:

```DAX id="8jqb7q"
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Employment Type]
)
```

Therefore, the measure preserves the Employment Type filter while removing other filters from the calculation.

This is an excellent practical example of **DAX filter context and `ALLEXCEPT()`**.

---

# 41. Final Report Structure After This Session

The report page now contains two primary visuals:

### Visual 1

**Loan Amount by Purpose**

* Uses `Loan Amount by Purpose`
* Category: Loan Purpose

### Visual 2

**Average Income by Employment Type**

* Uses `Average Income by Employment Type`
* Category: Employment Type
* Uses `ALLEXCEPT()` to retain Employment Type filtering

Both visuals are formatted as line charts and can be customized further.

---

# 42. End-to-End Workflow

The complete workflow covered in this session is:

**1. Recreate the previous table visual**
↓
**2. Add Loan Purpose and Loan Amount**
↓
**3. Apply Loan Amount ≠ Blank using Filters pane**
↓
**4. Optionally convert the table to a line chart**
↓
**5. Remove the temporary visual**
↓
**6. Hide the Filters pane**
↓
**7. Create a new measure in Measures Table 1**
↓
**8. Name it Average Income by Employment Type**
↓
**9. Use `CALCULATE()`**
↓
**10. Use `AVERAGE(Income)`**
↓
**11. Use `ALLEXCEPT()` to preserve Employment Type**
↓
**12. Duplicate the first line chart**
↓
**13. Remove Loan Purpose and Loan Amount by Purpose**
↓
**14. Add Average Income by Employment Type**
↓
**15. Add Employment Type to X-axis**
↓
**16. Change the title**
↓
**17. Format the line/interpolation/color**
↓
**18. Test visual interactions**
↓
**19. Verify that Employment Type affects the measure**
↓
**20. Verify that other visual filters do not affect it**
↓
**21. Open the original Excel source**
↓
**22. Create/configure a PivotTable**
↓
**23. Add Employment Type to Rows**
↓
**24. Add Income to Values**
↓
**25. Change Sum to Average**
↓
**26. Compare Excel values with Power BI**
↓
**27. Create a temporary Power BI table without the DAX measure**
↓
**28. Add Employment Type and Income**
↓
**29. Change Income aggregation to Average**
↓
**30. Compare all results**
↓
**31. Remove the temporary table**
↓
**32. Further format the charts if desired**

---

# 43. Key Takeaways for Interviews

### DAX

Be comfortable explaining:

* What `CALCULATE()` does
* What `AVERAGE()` does
* What `ALLEXCEPT()` does
* How filter context works
* How a measure can selectively preserve filters

### Data Validation

Be able to explain how you would validate a Power BI number:

> **DAX measure → raw-field aggregation in Power BI → original source data**

### Practical Scenario

If an interviewer asks:

**"How would you verify that a DAX measure is giving the correct result?"**

A good approach is:

1. Recreate the calculation using a simple table/matrix without the measure.
2. Compare the results.
3. Check the original source using something like an Excel PivotTable or source-system query.
4. Investigate the data pipeline if discrepancies exist.

### Most Important DAX Concept from This Lecture

`ALLEXCEPT()` is being used to ensure that the **Average Income by Employment Type** measure retains the **Employment Type** filter while removing other filters from the Loan Default table.

This is the central DAX/filter-context concept demonstrated in the session.
