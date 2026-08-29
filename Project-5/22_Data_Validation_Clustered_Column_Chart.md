# Detailed Notes: Data Validation of the Clustered Column Chart

## 1. Objective of the Session

The previous session covered the creation of a **Clustered Column Chart** showing:

> **Total Loan Amount for Middle Age Adults**, broken down by **Has Mortgage** and **Has Dependents**.

In this session, the objective is to **validate the data displayed in that clustered column chart**.

The validation is performed in two stages:

1. **Validate inside Power BI** using a temporary Table Visual, without using the DAX measure.
2. **Validate against the original Excel data source** using an Excel PivotTable.

The values from these independent calculations are then compared with the values shown in the clustered column chart.

---

# 2. Overall Validation Process

The complete validation flow is:

```text
Clustered Column Chart
        ↓
Temporary Power BI Table Visual
        ↓
Filter = Middle Age Adults
        ↓
Compare Has Mortgage + Has Dependents combinations
        ↓
Check chart tooltip/value
        ↓
Open original Excel source
        ↓
Create/modify Age Group Identifier
        ↓
Refresh PivotTable source
        ↓
Filter = Middle Age Adults
        ↓
Filter Has Mortgage
        ↓
Group by Has Dependents
        ↓
Calculate Total Loan Amount
        ↓
Compare with Power BI
```

---

# 3. Create a Temporary Table Visual in Power BI

The first step is to independently calculate the values directly in Power BI.

### Steps

1. Open the report in **Power BI Desktop**.
2. Expand the **Visualizations** pane.
3. Click on a **blank area of the canvas**.
4. Select **Table Visual**.

Power BI creates a blank table visual.

This table is temporary and is used only for data validation.

---

# 4. Add Fields to the Validation Table

The required fields are:

* **Has Mortgage**
* **Has Dependents**
* **Loan Amount**
* **Age Group**

### Steps

1. Expand the **Loan Default** table in the Data pane.
2. Add **Has Mortgage** to the table.
3. Add **Has Dependents**.
4. Add **Loan Amount**.

Power BI automatically summarizes Loan Amount as **Sum of Loan Amount**, which is appropriate because the clustered column chart represents **total loan amount**.

---

# 5. Apply the Middle Age Adults Filter

The clustered column chart is specifically calculating the total loan amount for **Middle Age Adults**.

Therefore, the temporary table must also be restricted to the same age group.

### Steps

1. With the table visual selected, locate **Age Group**.
2. Drag **Age Group** into the **Filters** section.
3. Expand the filter.
4. Select:

> **Middle Age Adults**

The table now contains only Middle Age Adult records.

---

# 6. Compare the Power BI Values

After applying the filter, the table shows the total loan amount for combinations of:

* Has Mortgage
* Has Dependents

The table calculation is independent of the DAX measure used by the clustered column chart.

This makes it useful for validation.

---

# 7. Example Validation: Has Mortgage = False and Has Dependents = True

The lecture uses one particular combination as an example.

The conditions are:

```text
Age Group = Middle Age Adults
Has Mortgage = False
Has Dependents = True
```

The table displays a total loan amount beginning with approximately:

> **31,391...**

and ending with approximately:

> **...793**

The exact value should be read from the table in Power BI.

---

# 8. Compare with the Clustered Column Chart

The next step is to compare the independently calculated table value with the corresponding column in the clustered column chart.

### Steps

1. Identify the column corresponding to:

   * **Has Mortgage = False**
   * **Has Dependents = True**
2. Hover the mouse over the corresponding column.
3. Power BI displays a tooltip containing the value.
4. Compare this value with the value in the temporary table.

The values should match.

This confirms that the clustered column chart is correctly representing the total loan amount for that particular combination.

---

# 9. Why This Is an Independent Validation

The temporary table does **not** use the custom DAX measure created for the clustered column chart.

Instead, it uses:

> **Loan Amount → Sum**

and applies the relevant category filter.

Therefore, the calculation is independently performed by Power BI.

This helps verify that the DAX measure is producing the expected result.

---

# 10. Collapse the Power BI Panes for Easier Comparison

Once the table has been configured, the lecture collapses the panes to make comparison easier.

You can collapse:

* **Filters**
* **Visualizations**
* **Data**

This gives more screen space for viewing the table and comparing it with the chart.

---

# 11. Validate Against the Excel Source

The next step is to validate the result against the **original Excel data source**.

The Excel file was the source from which the data was originally brought into the data pipeline.

The validation therefore checks:

> **Power BI → Original Excel Source**

This provides another level of confidence in the result.

---

# 12. Open the Excel Data Source

### Steps

1. Open the original Excel workbook.
2. Go to the **Loan Default** data/table.
3. Locate the dataset being used as the source.

The lecture then creates a PivotTable from this source data.

---

# 13. Create an Excel PivotTable

### Steps

1. Click any cell within the Loan Default dataset.
2. Go to the **Insert** tab.
3. Select **PivotTable**.
4. Excel opens the PivotTable creation dialog.

Select the entire dataset.

The lecture uses keyboard shortcuts:

* **Ctrl + Shift + Right Arrow** → select across the columns.
* **Down Arrow** → extend the selection through the data.

Then:

5. Click **OK**.

An Excel PivotTable is created.

---

# 14. Update the Age Group Identifier

The Excel sheet needs a way to identify **Middle Age Adults**.

A helper column had already been created in the previous validation exercise.

The lecture now modifies that formula because the age range for **Middle Age Adults** is:

> **40 to 59**

Previously, the formula had been used for another age category, so it needs to be updated.

---

# 15. Modify the Age Group Formula

The helper column is located in **column V**, with the formula starting in **V2**.

Click cell:

> **V2**

The formula should classify ages from **40 through 59** as Middle Age Adults.

The logic is:

```excel id="afp0s7"
=IF(AND(B2>=40,B2<=59),"Middle Age Adults","N/A")
```

> The exact reference to the Age column may differ depending on the workbook. Use the actual Age column/cell reference in your sheet.

---

# 16. Understand the Formula

The `AND()` function checks two conditions:

```text
Age >= 40
AND
Age <= 59
```

If both conditions are true:

> **Middle Age Adults**

Otherwise:

> **N/A**

So the classification is:

|      Age | Identifier        |
| -------: | ----------------- |
| Below 40 | N/A               |
|    40–59 | Middle Age Adults |
| Above 59 | N/A               |

The important point is that the adult category used for this visual is now correctly represented in Excel.

---

# 17. Fill the Formula Down

After modifying the formula:

1. Select **V2**.
2. Move to the bottom-right corner of the cell.
3. Double-click the fill handle.

Excel fills the updated formula down through the dataset.

---

# 18. Refresh the PivotTable Data Source

Because the helper column has been changed/added, the PivotTable needs to recognize the updated data range.

### Steps

1. Go to the worksheet containing the PivotTable.
2. Select the PivotTable.
3. Open the **PivotTable Analyze** tab.
4. Select **Change Data Source**.

---

# 19. Select the Updated Data Range

The PivotTable's original source range needs to include the newly created **Identifier** column.

### Steps

1. Select the complete updated dataset again.
2. Use:

   * **Ctrl + Shift + Right Arrow**
   * followed by the appropriate downward selection.
3. Ensure the new **Identifier** column is included.
4. Click **OK**.

The PivotTable now recognizes the helper column.

---

# 20. Refresh the PivotTable

The lecture also demonstrates refreshing the workbook data.

If the updated column isn't immediately reflected:

1. Go to the **Home** tab.
2. Select **Refresh All** under the data refresh options.

This ensures the PivotTable is working with the latest source data.

---

# 21. Filter the PivotTable to Middle Age Adults

Now use the newly updated **Identifier** column.

### Steps

1. Locate **Identifier** in the PivotTable Fields pane.
2. Drag it into the **Filters** section.
3. Open the filter.
4. Select:

> **Middle Age Adults**

5. Click **OK**.

The PivotTable is now restricted to Middle Age Adults.

---

# 22. Add Has Mortgage as a Filter

The clustered column chart analyzes loan amounts according to mortgage status.

Therefore, add **Has Mortgage** as a filter.

### Steps

1. Locate **Has Mortgage**.
2. Drag it into the **Filters** section.
3. Select a category to validate.

The lecture first chooses:

> **Yes**

and then changes it to:

> **No**

---

# 23. Add Has Dependents

Next, add **Has Dependents** to the PivotTable.

### Steps

1. Locate **Has Dependents**.
2. Drag it into the **Rows** section.

This allows the PivotTable to display separate totals for:

* Has Dependents = Yes
* Has Dependents = No

---

# 24. Add Loan Amount to Values

Now calculate the total loan amount.

### Steps

1. Locate **Loan Amount**.
2. Drag it into the **Values** section.

Because the requirement is **Total Loan Amount**, keep the aggregation as:

> **Sum**

Unlike the previous validation exercise for average loan amount, we do **not** change this to Average.

---

# 25. Compare the Excel Result

The PivotTable now provides the total loan amount for Middle Age Adults according to:

* Has Mortgage
* Has Dependents

For example, after selecting:

```text
Identifier = Middle Age Adults
Has Mortgage = No
Has Dependents = Yes
```

the PivotTable shows a value beginning with:

> **31,391...**

and ending with approximately:

> **...793**

This is the same value that was observed in Power BI.

---

# 26. Compare Power BI and Excel

The validation now has two independent results:

### Power BI Table

```text
Middle Age Adults
+ Has Mortgage = False
+ Has Dependents = True
→ Total Loan Amount
```

### Excel PivotTable

```text
Middle Age Adults
+ Has Mortgage = No
+ Has Dependents = Yes
→ Total Loan Amount
```

The results match.

This confirms that the data represented in the clustered column chart is consistent with the original Excel source.

---

# 27. Important Difference Between True/False and Yes/No

The Power BI field may represent the Boolean value as:

* **True**
* **False**

while Excel may display the corresponding category as:

* **Yes**
* **No**

When validating, understand that these represent the same logical conditions.

For example:

| Power BI | Excel |
| -------- | ----- |
| True     | Yes   |
| False    | No    |

So:

> Power BI **Has Mortgage = False** corresponds to Excel **Has Mortgage = No**.

Similarly:

> Power BI **Has Dependents = True** corresponds to Excel **Has Dependents = Yes**.

---

# 28. Data Validation Principle

The lecture emphasizes that data validation is an important part of working with data in real-world projects.

The report's data passes through multiple stages before being displayed:

```text
Excel
  ↓
SQL Server
  ↓
Data Flow
  ↓
Power BI
  ↓
DAX Calculation
  ↓
Visual
```

Because transformations and calculations happen at different stages, it is important to verify that the final report still represents the correct source information.

---

# 29. What Was Validated?

The validation checks:

### Dimension 1

**Age Group**

Only:

> Middle Age Adults

### Dimension 2

**Has Mortgage**

For example:

> False / No

### Dimension 3

**Has Dependents**

For example:

> True / Yes

### Measure

> **Total Loan Amount**

The same combination is checked in both Power BI and Excel.

---

# 30. Remove the Temporary Validation Table

After validation is complete, the Power BI table visual is no longer needed.

### Steps

1. Return to Power BI Desktop.
2. Select the temporary Table Visual.
3. Remove/delete it from the canvas.

The table was only used as a validation tool.

---

# 31. Final Report Layout

After removing the temporary table:

1. Keep the **Clustered Column Chart**.
2. Resize it if necessary.
3. Make sure it fits correctly with the other visuals.
4. Maintain a clean and readable report layout.

The final report page should not contain the temporary validation table.

---

# 32. Key Concepts Learned

## A. Independent Power BI Validation

A visual using a DAX measure can be checked using a temporary table that does not use that measure.

For this chart:

> **Loan Amount → Sum**

is used directly.

---

## B. Excel PivotTable Validation

The original source data can be independently summarized with a PivotTable.

This provides a second way to verify the Power BI result.

---

## C. Helper Columns for Validation

The **Identifier** column is created in Excel specifically to identify the required age group.

For Middle Age Adults:

> **40 ≤ Age ≤ 59**

---

## D. Updating PivotTable Data Sources

If a new column is added outside the original PivotTable source range, the PivotTable may not automatically include it.

Therefore:

**PivotTable Analyze → Change Data Source**

is used to include the newly created column.

A refresh may also be required.

---

# 33. Important Values/Conditions from the Lecture

| Item                   | Value                                       |
| ---------------------- | ------------------------------------------- |
| **Target age group**   | Middle Age Adults                           |
| **Age range**          | 40–59                                       |
| **Power BI measure**   | Total Loan Amount                           |
| **Aggregation**        | Sum                                         |
| **Power BI example**   | Has Mortgage = False, Has Dependents = True |
| **Excel equivalent**   | Has Mortgage = No, Has Dependents = Yes     |
| **Example result**     | Begins around 31,391 and ends around 793    |
| **Validation sources** | Power BI Table + Excel PivotTable           |

---

# 34. Complete Step-by-Step Workflow

## Part A — Validate in Power BI

1. Open Power BI Desktop.
2. Expand **Visualizations**.
3. Click a blank area on the canvas.
4. Add a **Table Visual**.
5. Add **Has Mortgage**.
6. Add **Has Dependents**.
7. Add **Loan Amount**.
8. Keep Loan Amount as **Sum**.
9. Add **Age Group** to the Filters section.
10. Select **Middle Age Adults**.
11. Examine the different Has Mortgage/Has Dependents combinations.
12. Choose an example such as:

    * Has Mortgage = False
    * Has Dependents = True
13. Note the total loan amount.
14. Hover over the corresponding column in the clustered column chart.
15. Compare the tooltip value with the table value.

---

## Part B — Prepare Excel for Validation

16. Open the original Excel source.
17. Go to the **Loan Default** table.
18. Locate the helper/identifier column.
19. Click **V2**.
20. Modify the formula so that ages 40–59 are classified as Middle Age Adults.
21. Use `IF()` with `AND()`.
22. Fill the formula down.
23. Ensure the column is named **Identifier**.

---

## Part C — Update the Excel PivotTable

24. Go to the PivotTable.
25. Open **PivotTable Analyze**.
26. Select **Change Data Source**.
27. Select the complete updated dataset.
28. Make sure the Identifier column is included.
29. Click **OK**.
30. If necessary, go to **Home → Refresh All**.

---

## Part D — Validate in Excel

31. Add **Identifier** to Filters.
32. Select **Middle Age Adults**.
33. Add **Has Mortgage** to Filters.
34. Select the required category, such as **No**.
35. Add **Has Dependents** to Rows.
36. Add **Loan Amount** to Values.
37. Keep the aggregation as **Sum**.
38. Locate the **Has Dependents = Yes** value.
39. Compare it with the Power BI table and chart.
40. Confirm that the values match.

---

## Part E — Clean Up Power BI

41. Return to Power BI.
42. Select the temporary Table Visual.
43. Delete it.
44. Resize the clustered column chart if necessary.
45. Leave the final report page with the intended visuals only.

---

# 35. Final Takeaway

The key lesson of this session is **data validation**.

The clustered column chart calculates and displays the **total loan amount for Middle Age Adults**, categorized by **mortgage status** and **dependent status**. Instead of trusting the DAX measure alone, the instructor independently calculates the same result in a Power BI table and then verifies it against the original Excel source using a PivotTable.

The successful match between the **Power BI calculation**, **chart value**, and **Excel PivotTable value** demonstrates that the data is being represented correctly.

This kind of source-to-report validation is an essential practice when working with Power BI in real-world projects.
