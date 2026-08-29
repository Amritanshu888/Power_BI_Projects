# Detailed Notes — Power BI: Loan Amount by Purpose, DAX Measure & Data Validation

## 1. Changing the Color of the Shape

The report page being worked on is **Page 1 — Loan Default and Overview**.

A shape had previously been inserted on this page. The first task is to format this shape.

### Steps to change the shape color

1. Select the shape on the report canvas.

2. Open the **Format Shape** pane.

3. Under **Styles**, expand **Colors**.

4. Click **More colors**.

5. Enter the hexadecimal color code:

   **`#993955`**

6. Apply the color.

The shape can also be resized as required.

> **Note:** A visual that was accidentally inserted is removed before continuing.

---

# 2. Preparing Additional Fields for Analysis

Before creating the first visual, additional fields required for the analysis are created.

The existing table contains a date column called:

**`Loan Date`**

The date is displayed in the format:

**DD/MM/YYYY**

The requirement is to extract the **year** from this date column.

---

# 3. Creating a Year Calculated Column Using DAX

A new calculated column is created to extract the year from `Loan Date`.

### Steps

1. Go to the **Data pane**.
2. Locate the **Loan Default** table.
3. Right-click the **Loan Default** table.
4. Select **New Column**.
5. Expand the formula bar if necessary.
6. Name the calculated column **Year**.
7. Use the DAX `YEAR()` function.
8. Pass the `Loan Date` column as the argument.

Conceptually, the formula is:

```DAX
Year = YEAR('Loan Default'[Loan Date])
```

### Important points

* `YEAR()` extracts the year portion from a date.
* Because **New Column** was selected, this creates a **calculated column**.
* The resulting `Year` column becomes part of the dataset.
* Power BI displays a **calculated-column icon** next to the newly created field.

### Verify the column

1. Switch to **Table view**.
2. Locate the newly created **Year** column.
3. Verify that it contains the year extracted from `Loan Date`.
4. Return to **Report view**.

---

# 4. Importance of DAX and Data Validation

The project focuses on two major areas:

1. **DAX**
2. **Data validation**

These are particularly important from an interview perspective and in real-world Power BI development.

## Why data validation is important

In real-time projects, you may sometimes notice that numbers displayed in a Power BI report are inaccurate or unexpected.

When this happens, you may need to:

1. Identify the incorrect number.
2. Drill down into the calculation.
3. Go back to the underlying data.
4. Check the source data.
5. Compare the values manually.
6. Identify where the discrepancy occurred.
7. Correct the issue.

Therefore, understanding **how to validate Power BI results against the original source data** is an important practical skill.

## Why DAX is important

DAX is also highly important from an interview perspective.

The project therefore demonstrates:

* Different DAX functions
* DAX measures
* Calculated columns
* Filtering data using DAX
* Aggregating data using DAX
* Validating DAX results against non-DAX results
* Validating Power BI results against the original Excel source

---

# 5. Creating the `Loan Amount by Purpose` DAX Measure

The first major measure created in this session is:

**Loan Amount by Purpose**

The purpose of this measure is to calculate the total loan amount while excluding blank loan amount values.

---

## Steps to create the measure

1. Go to the **Data pane**.

2. Right-click the **Loan Default** table.

3. Select **New Measure**.

4. Expand the formula bar.

5. Name the measure:

   **`Loan Amount by Purpose`**

6. Build the DAX expression using:

   * `SUMX`
   * `FILTER`
   * `NOT`
   * `ISBLANK`

The measure follows this logic:

```DAX
Loan Amount by Purpose =
SUMX(
    FILTER(
        'Loan Default',
        NOT(ISBLANK('Loan Default'[Loan Amount]))
    ),
    'Loan Default'[Loan Amount]
)
```

---

## Understanding the DAX logic

### `SUMX()`

`SUMX()` is an iterator function.

It evaluates an expression for each row of a table and then adds the resulting values.

The general structure is:

```DAX
SUMX(Table, Expression)
```

Here:

* **Table** → filtered Loan Default table
* **Expression** → Loan Amount

---

### `FILTER()`

The `FILTER()` function is used to filter the Loan Default table.

The logic says:

> Consider only those records where Loan Amount is not blank.

---

### `ISBLANK()`

`ISBLANK()` checks whether a value is blank.

For example:

```DAX
ISBLANK('Loan Default'[Loan Amount])
```

returns TRUE when Loan Amount is blank.

---

### `NOT()`

`NOT()` reverses the result.

Therefore:

```DAX
NOT(ISBLANK('Loan Default'[Loan Amount]))
```

means:

> Loan Amount must NOT be blank.

Thus, only records having a value in the Loan Amount column are considered for the calculation.

---

## Result

After pressing **Enter**, Power BI creates the measure.

A **calculator icon** appears next to the measure, indicating that it is a **measure** rather than a regular column.

---

# 6. Creating a Separate Measures Table

It is considered good practice to keep measures in a separate table rather than mixing them with the original data table.

This makes the model cleaner and makes measures easier to locate and manage.

Since the project will contain **three report pages**, separate measures tables are planned:

* Measures Table 1 → Page 1
* Measures Table 2 → Page 2
* Measures Table 3 → Page 3

The current page therefore uses **Measures Table 1**.

---

## Steps to create Measures Table 1

1. Go to the **Home** tab.

2. Click **Enter Data**.

3. Create a new table.

4. Name it:

   **Measures Table 1**

5. Click **Load**.

Power BI creates the new table.

You can now see **Measures Table 1** in the Data pane.

---

# 7. Moving the Measure to Measures Table 1

The measure initially belongs to the **Loan Default** table.

It is now moved to the dedicated measures table.

### Steps

1. Expand the **Loan Default** table.
2. Select the **Loan Amount by Purpose** measure.
3. Go to the **Measure tools** area.
4. Locate **Home table**.
5. Open the dropdown.
6. Select:

   **Measures Table 1**

The measure is now stored under the Measures Table 1 table.

---

# 8. Removing the Unnecessary Column

The column created automatically while using **Enter Data** is no longer required.

### Steps

1. Locate the unwanted column under **Measures Table 1**.
2. Click the **three dots (...)** next to it.
3. Select **Delete from model**.

Now Measures Table 1 effectively acts as a dedicated location for the measures.

---

# 9. Creating the Loan Amount by Purpose Line Chart

The newly created measure is now used to create a visual.

The objective is to show:

> **Loan Amount by Loan Purpose**

---

## Steps

1. Click a blank area on the report canvas.
2. Select the **Line chart** visual.
3. Resize the chart.
4. Position it near the top of the report page.
5. Keep the blank line chart selected.
6. Select the **Loan Amount by Purpose** measure.
7. From the Loan Default table, locate the **Loan Purpose** column.
8. Select/check **Loan Purpose**.

Power BI creates the line chart showing loan amounts for the different loan-purpose categories.

---

# 10. Formatting the Line Chart

After creating the visual, several formatting changes are made to improve its appearance.

---

## A. Change the Chart Title

1. Select the line chart.

2. Open **Format your visual**.

3. Go to **General** / **Title**.

4. Turn on or expand the title settings.

5. Replace the existing title with:

   **Loan Amount by Purpose**

6. Choose the desired font.

7. Change the text color if required.

8. Set horizontal alignment to:

   **Center**

9. Make the title **Bold**.

---

# 11. Removing the Y-Axis

The values along the vertical axis are not required because the values will be displayed through data labels.

### Steps

1. Select the line chart.
2. Open the formatting options.
3. Expand **Y-axis**.
4. Turn **Values** → **Off**.
5. Turn **Title** → **Off**.
6. Collapse the Y-axis section.

---

# 12. Removing the X-Axis Title

The loan-purpose names should remain visible, but the explicit axis title is unnecessary.

### Steps

1. Expand **X-axis**.
2. Turn **Title** → **Off**.
3. Keep the category values available.
4. Collapse the X-axis section.

---

# 13. Formatting X-Axis Values

The category labels along the horizontal axis are formatted.

### Steps

1. In the **X-axis** settings, locate **Values**.
2. Change the font style as desired.
3. Increase the font size slightly.
4. Make the text **Bold** if required.
5. Change the text color.

The lecture uses the following hexadecimal color:

**`#666666`**

---

# 14. Changing the Line Color

The line itself is given a specific color.

### Steps

1. Select the line chart.

2. Expand the **X-axis** section if necessary and then move to the **Lines** settings.

3. Expand **Lines**.

4. Click **Color**.

5. Select **More colors**.

6. Enter:

   **`#6B1C9F`**

7. Apply the color.

> The exact colors used in the lecture can be followed using their hexadecimal codes, but Power BI allows you to choose your own color combinations as well.

---

# 15. Using Color Combinations in Power BI

The lecture recommends using online color references when designing reports.

You can:

1. Search Google for different color combinations.
2. Find suitable color palettes.
3. Copy their hexadecimal color codes.
4. Use those codes in Power BI.

This helps create more visually appealing and consistent report designs.

---

# 16. Changing Line Interpolation

The line's appearance can also be changed.

### Steps

1. Select the line chart.
2. Locate the **Interpolation type** setting.
3. Change it to:

   **Smooth**

This changes the appearance of the line from a standard/angular representation to a smoother line.

---

# 17. Adding a Shaded Area

A shaded area can be added beneath the line.

### Steps

1. Locate the **Shaded area** option.
2. Change it to:

   **On**

The chart now displays a shaded region underneath the line.

---

# 18. Adding Markers

Markers can be used to make individual data points more visible.

### Steps

1. Locate **Markers**.
2. Change **Markers** to:

   **On**

The individual points on the line become visible.

---

# 19. Customizing Marker Type and Size

The marker appearance can also be customized.

### Steps

1. Expand the **Markers** section.
2. Locate the marker **Type**.
3. Select a different marker shape if desired.
4. Increase or decrease the marker **Size** according to your preference.

---

# 20. Turning On Data Labels

Since the Y-axis values were removed, the actual values need to be displayed directly on the chart.

### Steps

1. Collapse the **Markers** section.
2. Locate **Data labels**.
3. Turn **Data labels** → **On**.

The numerical loan amount values now appear directly on the chart.

---

# 21. Formatting Data Labels

The data labels are further formatted.

### Steps

1. Expand **Data labels**.
2. Scroll to the relevant **Values/Data labels** settings.
3. Select the desired font style.
4. Change the font color.
5. Make the text **Bold** if required.

The lecture uses a white/darker variant color for the labels.

---

# 22. Adding a Border to the Chart

A border is added around the line chart.

### Steps

1. Select the chart.

2. Go to **General**.

3. Expand **Effects**.

4. Locate **Visual border**.

5. Turn **Visual border** → **On**.

6. Expand the visual-border settings.

7. Under **Color**, select **More colors**.

8. Enter the same magenta color used for the top shape:

   **`#993955`**

9. Press **Enter**.

The line chart now has a border matching the overall report design.

---

# 23. Final Line Chart Configuration

The resulting line chart represents:

**Loan Amount by Purpose**

It contains:

* Loan Purpose on the X-axis
* Loan Amount as the calculated value
* Smooth line interpolation
* Shaded area
* Markers
* Data labels
* Customized title
* Customized axis formatting
* Custom line color
* Custom data-label formatting
* Custom visual border

---

# 24. Why Data Validation Is Required

The loan amount values displayed by the DAX measure have been calculated using DAX.

Therefore, it is important to verify that the calculation is producing the correct results.

The validation is performed at **two levels**:

### Level 1 — Validate inside Power BI

Compare:

* DAX measure results
* Results obtained directly from the source columns

### Level 2 — Validate against the original Excel source

Compare:

* Power BI results
* Original Excel data

The values should match.

---

# 25. Validating the DAX Measure Without Using DAX

A table visual is created to independently reproduce the same results without using the DAX measure.

This provides a simple way of checking whether the DAX calculation is correct.

---

## Steps

1. Click a blank area of the canvas.
2. Select the **Table** visual.
3. A blank table is created.
4. Select the **Loan Purpose** field from the Loan Default table.
5. Add the **Loan Amount** column to the table.

Power BI automatically aggregates Loan Amount, showing the **Sum of Loan Amount** for each loan-purpose category.

### Important

The DAX measure is **not** used in this table.

Instead, the raw fields are used:

* Loan Purpose
* Loan Amount

---

# 26. Comparing the DAX Results with the Table Visual

Now compare the values shown in:

### Line chart

The line chart uses:

**Loan Amount by Purpose DAX measure**

### Table visual

The table uses:

**Loan Purpose + Loan Amount**

The values should match.

For example, the **Home** category produces a value around **65,452...**, ending in **527**.

The same ending/value can be observed in both visuals.

This confirms that the DAX calculation is producing the expected result.

---

# 27. General Data Validation Technique in Power BI

This is an important technique for real-world Power BI development.

When a DAX calculation produces a number:

1. Create a simple table or matrix.
2. Use the relevant raw fields.
3. Avoid using the DAX measure.
4. Allow Power BI to perform the basic aggregation.
5. Compare the result with the DAX measure.
6. Investigate any differences.

This helps determine whether an issue exists in the DAX logic.

---

# 28. Validating Against the Original Excel Data Source

The original data source for the project was an **Excel file**.

The data flow was:

**Excel → Microsoft SQL Server → Data Flow → Power BI**

Therefore, Excel represents the original/source-level data that can be used for an additional validation.

The values in Power BI should ultimately agree with the original Excel source.

---

# 29. Creating a Pivot Table in Excel for Validation

The original Excel workbook is opened.

A PivotTable is created to calculate the same loan-purpose totals.

### Steps

1. Open the original Excel file.
2. Select the relevant data.
3. Go to the **Insert** tab.
4. Click **PivotTable**.
5. Choose **New Worksheet**.
6. Create the PivotTable.

---

# 30. Configuring the Excel PivotTable

The same fields used in Power BI are added to the PivotTable.

### Loan Purpose

1. Find the **Loan Purpose** field.
2. Double-click it or drag it to the **Rows** area.

This creates one row for each loan-purpose category.

### Loan Amount

1. Search for **Loan Amount**.
2. Double-click it or drag it into the **Values** area.
3. Excel calculates the sum of Loan Amount for each purpose.

The resulting PivotTable now provides an independent calculation from the original source data.

---

# 31. Three-Way Validation

The same number can now be checked in three places:

### 1. Power BI line chart

Uses the DAX measure:

**Loan Amount by Purpose**

### 2. Power BI table visual

Uses:

* Loan Purpose
* Loan Amount

without the custom DAX measure.

### 3. Excel PivotTable

Uses the original Excel data source:

* Loan Purpose → Rows
* Loan Amount → Values

The numbers should match across all three.

---

# 32. Example of Validation

For the **Home** loan-purpose category:

* The Power BI DAX line chart shows a value ending in **527**.
* The Power BI table visual shows the same value.
* The Excel PivotTable shows the same value.

This demonstrates that the DAX calculation and Power BI aggregation are consistent with the original source data.

---

# 33. Why Source-Level Validation Matters

In a real project, Power BI data may have passed through several stages:

**Original Excel → SQL Server → Data Flow → Power BI**

Changes can potentially occur during:

* Data loading
* Data transformation
* Data type conversion
* Filtering
* DAX calculations
* Data modeling
* Aggregation

Therefore, when a report number looks suspicious, you should not simply assume that the visual is correct.

Instead, trace the number backward through the data pipeline and compare it against the source.

---

# 34. Real-Time Troubleshooting Approach

If you encounter an inaccurate number in a Power BI report:

1. Identify the problematic visual.
2. Check the number shown by the visual.
3. Reproduce the calculation using a simple table/matrix visual.
4. Check whether the problem is caused by the DAX measure.
5. Compare the result with the underlying Power BI fields.
6. Go back to the source system.
7. Compare against the original source data.
8. Identify whether the discrepancy occurred during:

   * Data extraction
   * Data transformation
   * Data loading
   * Data modeling
   * DAX calculation
   * Aggregation
9. Correct the underlying issue.
10. Revalidate the report.

---

# 35. Removing the Temporary Validation Visual

The Power BI table visual was created only for validation and understanding.

It is not part of the final report.

### Steps

1. Select the temporary table visual.
2. Delete/remove it from the canvas.

The final report therefore retains the intended **Loan Amount by Purpose** line chart.

---

# 36. Key DAX Functions Covered

This session introduces several important DAX functions.

| Function    | Purpose                                                    |
| ----------- | ---------------------------------------------------------- |
| `YEAR()`    | Extracts the year from a date                              |
| `SUMX()`    | Iterates through a table and calculates/sums an expression |
| `FILTER()`  | Filters rows based on a condition                          |
| `NOT()`     | Reverses a logical result                                  |
| `ISBLANK()` | Checks whether a value is blank                            |

---

# 37. Calculated Column vs Measure

This session also demonstrates the difference between a calculated column and a measure.

### Calculated Column

The **Year** field is created using:

```DAX
Year = YEAR('Loan Default'[Loan Date])
```

It creates a value for each row of the table.

### Measure

**Loan Amount by Purpose** is created as a measure.

It performs an aggregation dynamically based on the filter context of the visual.

A calculator icon identifies the measure in the Data pane.

---

# 38. Best Practices Demonstrated

### 1. Keep measures in dedicated measure tables

Instead of keeping measures mixed with business/data columns, create dedicated tables such as:

* Measures Table 1
* Measures Table 2
* Measures Table 3

### 2. Validate DAX calculations

Never blindly trust a complex DAX calculation. Compare it with a simpler aggregation.

### 3. Validate against the original source

For important reports, trace results back to the original data source.

### 4. Use consistent colors

Using the same color codes across shapes, borders, and visuals produces a consistent report design.

### 5. Use data labels when axis values are hidden

If the Y-axis is intentionally hidden, turn on data labels so users can still read the actual values.

---

# 39. Important Hex Color Codes Used

| Purpose            | Hex Code  |
| ------------------ | --------- |
| Shape color        | `#993955` |
| Line color         | `#6B1C9F` |
| Axis/category text | `#666666` |
| Chart border       | `#993955` |

---

# 40. Overall Workflow of the Session

The complete workflow was:

**1. Select the existing shape**
↓
**2. Change shape color to `#993955`**
↓
**3. Resize the shape**
↓
**4. Create Year calculated column from Loan Date**
↓
**5. Create Loan Amount by Purpose DAX measure**
↓
**6. Use `SUMX + FILTER + NOT + ISBLANK`**
↓
**7. Create Measures Table 1**
↓
**8. Move the measure to Measures Table 1**
↓
**9. Delete the unnecessary default column**
↓
**10. Create a line chart**
↓
**11. Add Loan Amount by Purpose measure**
↓
**12. Add Loan Purpose to the chart**
↓
**13. Format title, axes, line, markers, labels, shading and border**
↓
**14. Create a temporary table visual for validation**
↓
**15. Compare DAX results with direct Power BI aggregation**
↓
**16. Open the original Excel source**
↓
**17. Create an Excel PivotTable**
↓
**18. Compare Excel results with Power BI results**
↓
**19. Confirm that the numbers match**
↓
**20. Remove the temporary validation table**

---

## Key Takeaways

* **DAX and data validation are both critical Power BI skills.**
* `YEAR()` can be used to extract the year from a date.
* `SUMX()` can be combined with `FILTER()` to perform conditional aggregation.
* `NOT(ISBLANK(...))` ensures blank loan amounts are excluded.
* A dedicated **Measures Table** is a good modeling practice.
* A table/matrix visual can be used to independently validate a DAX measure.
* The **original source data** should also be used for validation when necessary.
* Excel PivotTables provide a convenient way to independently verify Power BI aggregations.
* In real-time projects, always investigate unexpected numbers instead of assuming the visual or DAX calculation is correct.
* Consistent use of hexadecimal colors helps maintain a professional report design.
