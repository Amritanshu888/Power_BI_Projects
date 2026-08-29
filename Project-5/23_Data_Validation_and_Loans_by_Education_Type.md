# Power BI — Number of Loans by Education Type

## 1. Objective of the Visual

The objective of this final visual is to represent the **number of loans for different education types** using a **line chart**.

The visual will show:

* **X-axis:** Education Type
* **Y-axis:** Number of Loans
* **Measure:** A DAX measure that counts valid/non-blank Loan IDs

The final chart helps us understand how the total number of loans is distributed across different education categories.

---

# 2. Remove the Data Validation Table

Before creating the final visual, the temporary table that was used for data validation is removed.

### Steps

1. Select the existing **table visual** on the report canvas.
2. Press the **Delete** key on the keyboard.
3. The validation table will be removed from the report page.

> This table was only being used temporarily to validate the numbers and is not part of the final report.

---

# 3. Create the Line Chart

Instead of creating a completely new line chart from scratch, an existing line chart is duplicated.

### Steps

1. Select an existing **Line Chart** on the report page.
2. Press:

   * `Ctrl + C`
   * `Ctrl + V`
3. A copy of the line chart will be created.
4. Move the newly created line chart to the **right-hand side** of the report page.

This allows the formatting/layout of the existing visual to be reused.

---

# 4. Remove the Existing Measure

The duplicated line chart already contains an existing measure, **Total Loan**.

Since this visual needs to represent the number of loans by education type, the existing measure needs to be removed.

### Steps

1. Select the newly duplicated line chart.
2. Expand the **Visualizations** pane.
3. Locate the existing **Total Loan** field.
4. Remove it from the visual.

The chart is now ready to receive the new measure.

---

# 5. Create the DAX Measure

A new measure is required to calculate the number of valid loans.

The measure will count records where **Loan ID is not blank**.

### Steps

1. Expand the **Data** pane.
2. Locate the table named **Measures Table 2**.
3. Right-click on **Measures Table 2**.
4. Select **New Measure**.

Power BI will open the formula bar where the DAX expression can be entered.

### Measure Name

The measure is named:

**Number of Loans by Education Type**

The transcript also refers to it informally as **Loans by Education Type**.

### DAX logic

The measure uses:

* `COUNTROWS()`
* `FILTER()`
* `NOT()`
* `ISBLANK()`

The logic is:

```DAX
Number of Loans by Education Type =
COUNTROWS(
    FILTER(
        'Loan Default',
        NOT(
            ISBLANK('Loan Default'[Loan ID])
        )
    )
)
```

### How the DAX works

#### `COUNTROWS()`

`COUNTROWS()` counts the number of rows returned by a table expression.

```DAX
COUNTROWS(...)
```

Here, it counts the rows returned by the `FILTER()` function.

---

#### `FILTER()`

```DAX
FILTER(
    'Loan Default',
    ...
)
```

The `FILTER()` function examines the **Loan Default** table and keeps only records satisfying the specified condition.

---

#### `ISBLANK()`

```DAX
ISBLANK('Loan Default'[Loan ID])
```

Checks whether the **Loan ID** value is blank.

---

#### `NOT()`

```DAX
NOT(ISBLANK('Loan Default'[Loan ID]))
```

Reverses the result.

Therefore, only records where:

**Loan ID ≠ Blank**

are retained.

---

### Overall calculation

The complete logic is:

> Filter the Loan Default table → keep only rows where Loan ID is not blank → count those rows.

Therefore, the measure represents the **number of valid loans**.

---

# 6. Create the Measure

After entering the DAX expression:

1. Press **Enter**.
2. Power BI creates the measure.
3. The measure appears in the Data/Fields pane.
4. The measure can now be used in the line chart.

---

# 7. Add the Measure to the Line Chart

Now the newly created measure needs to be placed on the Y-axis.

### Steps

1. Select the newly created line chart.
2. Locate the newly created measure:
   **Number of Loans by Education Type**
3. Drag and drop the measure into the **Y-axis** bucket.

The Y-axis will now represent the number of loans.

---

# 8. Add Education to the X-axis

The education category needs to be used to divide the loans into different groups.

### Steps

1. Locate the **Education** field under the **Loan Default** table.
2. Drag and drop **Education** into the **X-axis** bucket.

The resulting visual now represents:

| Axis   | Field                             |
| ------ | --------------------------------- |
| X-axis | Education                         |
| Y-axis | Number of Loans by Education Type |

The line chart will therefore show the number of loans for each education category.

---

# 9. Correct the Visual Title

The duplicated visual may initially have an incorrect title because it was copied from another chart.

The title needs to be changed to reflect the actual data being displayed.

### Steps

1. Select the line chart.
2. Open **Format Your Visual**.
3. Go to:

**General → Title**

4. Select the existing title text.
5. Change the title so that it represents:

**Number of Loans by Education Type**

The transcript initially mentions employment type but corrects it because the required field is **Education Type**.

### Important correction

The visual should **NOT** use:

> Employment Type

It should use:

> Education Type

---

# 10. Change the Line Color

The line chart can be formatted by changing the line color.

### Steps

1. Select the line chart.
2. Open **Format Your Visual**.
3. Locate the **Lines** section.
4. Scroll down to the **Colors** option.
5. Select the color option.
6. Click **More Colors**.
7. Enter the specified color code.

The transcript gives the intended color as:

**`#E66969`**

So the line should be formatted using the color:

> E66969

---

# 11. Final Visual Configuration

The completed visual should essentially have the following configuration:

### Visual Type

**Line Chart**

### X-axis

**Education**

### Y-axis

**Number of Loans by Education Type**

### Filter condition inside the measure

**Loan ID is not blank**

### Line Color

**#E66969**

### Suggested Title

**Number of Loans by Education Type**

---

# 12. Data Validation

After creating the visual, the numbers can be validated using a temporary table visual.

This ensures that the DAX measure is producing the correct counts.

---

## 13. Create a Temporary Table for Validation

### Steps

1. Click on a **blank area of the report canvas**.
2. In the Visualizations pane, select the **Table** visual.
3. Power BI will create a blank table.
4. Resize the table as required.

This table is only for validation.

---

# 14. Add Education to the Validation Table

Expand the **Loan Default** table in the Data pane.

Locate the:

**Education**

field.

Add **Education** to the table visual.

This will create rows for the different education categories.

---

# 15. Add Loan ID and Count It

Next, we need to count Loan IDs for each education category.

### Steps

1. Add **Loan ID** to the table visual.
2. Click the Loan ID field/dropdown.
3. Change its aggregation to:

**Count**

The table will now show the count of Loan IDs for each education category.

---

# 16. Apply the "Is Not Blank" Filter

The DAX measure counts only records where Loan ID is not blank.

Therefore, the validation table must apply the same condition.

Otherwise, the validation numbers may not match the measure.

### Steps

1. Select the validation table.
2. Expand the **Filters** pane.
3. Locate the **Loan ID** field.
4. Drag **Loan ID** into the **Add Data Fields** section under the Filters pane.
5. Change the filter type from:

**Basic filtering**

to:

**Advanced filtering**

6. Select:

**is not blank**

7. Click:

**Apply filter**

Now the validation table will count only records where Loan ID contains a value.

---

# 17. Validate the Numbers

After applying the filter, compare the counts shown in the table with the values represented by the line chart.

For example, the transcript gives:

**Bachelors → 64,366 loans**

So the value for the **Bachelors** education category should be:

> **64,366**

Other education categories can be checked in the same way.

---

# 18. Validate Against the Original Excel Dataset

The Power BI results can also be compared with the original Excel source data.

This provides an additional level of validation.

### Steps in Excel

1. Open the original **Excel** file containing the Loan Default data.
2. Open the **Loan Default** worksheet/table.
3. Select the data.
4. Go to:

**Insert → PivotTable**

5. Choose the relevant **Table/Range**.
6. Create the PivotTable.

---

# 19. Configure the Excel PivotTable

The objective is to reproduce the same calculation in Excel.

We want:

> Education Type → Count of Loan ID

### Rows

Drag:

**Education**

into the **Rows** section.

This creates one row for each education category.

### Values

Drag:

**Loan ID**

into the **Values** section.

Change the aggregation to:

**Count**

The PivotTable will now show the number of Loan IDs for each education category.

---

# 20. Compare Excel and Power BI

For example:

**Bachelors**

Excel PivotTable:

**64,366**

Power BI validation table:

**64,366**

Since both values match, the Power BI calculation can be considered validated for that category.

The same process can be followed for the remaining education categories.

---

# 21. Important Concepts Covered

### 1. Duplicating visuals

Existing visuals can be copied using:

```text
Ctrl + C
Ctrl + V
```

This is useful when the new visual requires similar formatting.

---

### 2. Measures Table

Measures can be organized in a dedicated table such as:

**Measures Table 2**

This keeps DAX measures separate from the actual data columns and helps keep the model organized.

---

### 3. Counting valid records

Instead of blindly counting all rows, the measure specifically counts records where **Loan ID is not blank**.

The key condition is:

```DAX
NOT(ISBLANK('Loan Default'[Loan ID]))
```

This ensures blank Loan IDs aren't counted.

---

### 4. Context from the X-axis

Although the measure itself doesn't explicitly mention Education, placing **Education** on the X-axis causes Power BI to evaluate the measure separately for each education category.

Conceptually:

```text
Education = Bachelors
        ↓
Measure calculates valid Loan IDs
        ↓
64,366
```

Then Power BI repeats the calculation for the other education categories.

This is an important example of how **filter context** works in Power BI.

---

# 22. Complete Workflow

The entire process can be remembered as:

```text
Remove temporary validation table
        ↓
Duplicate existing Line Chart
        ↓
Move chart to required location
        ↓
Remove existing Total Loan measure
        ↓
Create New Measure
        ↓
COUNTROWS + FILTER
        ↓
Keep Loan ID ≠ Blank
        ↓
Add measure to Y-axis
        ↓
Add Education to X-axis
        ↓
Change chart title
        ↓
Change line color to #E66969
        ↓
Create temporary validation table
        ↓
Education → Rows
Loan ID → Count
        ↓
Apply Loan ID = "is not blank"
        ↓
Compare Power BI values
        ↓
Validate against Excel PivotTable
```

## Final Result

The final line chart communicates:

> **How many valid loans exist for each education type.**

The measure counts only records having a **non-blank Loan ID**, while the **Education** field provides the category-wise filter context. The result is then validated both within Power BI and against an Excel PivotTable, with **Bachelors = 64,366** given as one validation example.
