# Detailed Notes: Data Validation of the Donut Chart

## 1. Objective of the Session

In the previous session, a **donut chart** was created to show the average loan amount for the **High Credit Score** category by:

* Age Group
* Marital Status

In this session, the purpose is to **validate the data shown in the donut chart**.

The validation is performed at two levels:

1. **Power BI validation** — create a temporary table visual and calculate the average directly without using the custom DAX measure.
2. **Excel validation** — go back to the original Excel data source, create the required credit-category column, build a PivotTable, and independently calculate the average loan amount.

The values from both methods are then compared with the values displayed in the donut chart.

---

# 2. Validation Approach

The basic validation process is:

**Donut Chart**
↓
Create a temporary **Table Visual** in Power BI
↓
Calculate Average Loan Amount directly
↓
Check individual combinations of:

* Marital Status
* Age Group
* Credit Score Bin
  ↓
  Compare the result with the donut chart
  ↓
  Open the original **Excel data source**
  ↓
  Create a Credit Category column
  ↓
  Create an Excel PivotTable
  ↓
  Filter to High Credit Category
  ↓
  Calculate Average Loan Amount
  ↓
  Compare Excel result with Power BI

This is an important data-validation technique because it ensures that the DAX measure and visual are producing the expected results.

---

# 3. Create a Temporary Table Visual in Power BI

The first step is to independently calculate the values in Power BI without relying on the previously created DAX measure.

### Steps

1. Click on a **blank area of the report canvas**.
2. Expand the **Visualizations** pane.
3. Select **Table Visual**.

A blank table visual is created.

---

# 4. Add Fields to the Table Visual

The table is used to examine the data by different categories.

The lecture initially discusses adding:

* **Marital Status**
* **Age Groups**
* **Credit Score Bins**

The important category for the validation is **Credit Score Bins**.

### Add Credit Score Bins

1. Select the table visual.
2. Locate **Credit Score Bins** in the Data pane.
3. Add it to the table.

You can also add **Marital Status** and **Age Groups** when needed to inspect specific combinations.

---

# 5. Sort Credit Score Bins

The Credit Score Bins can be sorted so that the categories appear in a desired order.

### Steps

1. Select the table visual.
2. Use the sorting option for **Credit Score Bins**.
3. Choose either:

   * **Ascending**, or
   * **Descending**

The lecture sorts the data using the **Credit Score Bins** field.

---

# 6. Add Loan Amount to the Table

The next objective is to calculate the average loan amount directly.

### Steps

1. With the table visual selected, locate **Loan Amount**.
2. Double-click **Loan Amount** or drag it into the table's columns/values area.
3. Power BI will initially aggregate the field as **Sum of Loan Amount**.

However, the donut chart is showing an **average**, so the aggregation must be changed.

---

# 7. Change Loan Amount from Sum to Average

### Steps

1. In the table visual, locate the **Loan Amount** field.
2. Click the **drop-down arrow** beside the field.
3. Change the aggregation from:

   * **Sum**
   * to **Average**

Now the table directly calculates the **Average Loan Amount**.

### Why this is important

This calculation is being performed directly by Power BI rather than using the custom DAX measure created for the donut chart.

Therefore, it provides an independent way of checking whether the DAX measure is producing the correct result.

---

# 8. Validate a Specific Category in Power BI

The lecture demonstrates validation using a specific combination of categories.

The selected combination is:

* **Age Group:** Teen
* **Marital Status:** Single
* **Credit Score Bin:** High

The average loan amount displayed is approximately:

> **128,565.39**

This value can then be compared with the corresponding section/data shown in the donut chart.

If the values match, it provides evidence that the donut chart and its underlying calculation are correct for that category.

---

# 9. Validate Another Category

The same process can be repeated for another combination.

The lecture uses:

* **Age Group:** Teen
* **Marital Status:** Married
* **Credit Score Bin:** High

The average loan amount is approximately:

> **124,870.61**

This value can again be compared with the corresponding value represented by the donut chart.

### Key point

You don't need to validate every possible combination manually.

Instead, you can select a few representative categories and verify that the values calculated directly in Power BI match the values displayed by the visual.

---

# 10. Why Validate Without the DAX Measure?

The custom DAX measure created earlier was essentially calculating:

> Average Loan Amount where Credit Score Bins = High.

To validate that measure, we should not simply use the same measure again.

Instead, the lecture calculates:

**Loan Amount → Average**

directly in a temporary table and applies the required category selections.

This gives an independent calculation against which the DAX measure can be compared.

---

# 11. Validate Against the Original Excel Data

After validating the values in Power BI, the lecture goes one step further.

The **Excel sheet**, which is the original data source, is opened.

The objective is to independently reproduce the same calculation in Excel.

This provides an additional layer of validation:

**Power BI Visual → Power BI Table → Excel Source**

If all three produce the same value, confidence in the result increases significantly.

---

# 12. Create a Credit Category Column in Excel

The Excel source does not already contain a separate identifier for the **High Credit Score** category.

Therefore, a new column needs to be created.

The lecture uses the following criterion:

> **Credit Score greater than 650 = High**

---

# 13. Create the Credit Category Formula

Suppose the new column is being created starting at cell **U2**.

Click cell **U2** and enter an IF formula.

The logic is:

```excel
=IF(Credit_Score>650,"High","Not Available")
```

The exact cell reference for Credit Score depends on the structure of the Excel sheet.

### Logic of the formula

```text
If Credit Score > 650
        ↓
      High

Otherwise
        ↓
   Not Available
```

The lecture uses **Not Available** for the non-high category because the validation is specifically concerned with the **High Credit** records.

---

# 14. Fill the Formula Down

After entering the formula:

1. Select cell **U2**.
2. Use the fill handle on the bottom-right corner of the cell.
3. **Double-click the fill handle**.

Excel automatically copies the formula down for the relevant rows.

---

# 15. Rename the New Column

The new column is renamed to:

> **Credit Category**

This makes its purpose clear.

The column now identifies whether each record belongs to the High Credit category.

---

# 16. Create an Excel PivotTable

The next step is to create an independent summary using an Excel PivotTable.

### Steps

1. Click any cell inside the dataset.
2. Go to the **Insert** tab.
3. Select **PivotTable**.
4. Excel opens the **PivotTable from Table/Range** dialog.

---

# 17. Select the Entire Data Range

The lecture selects the complete dataset.

One way demonstrated is using keyboard shortcuts:

1. Click the first cell of the data.
2. Press **Ctrl + Shift + Right Arrow** to extend the selection horizontally.
3. Press the **Down Arrow** as required to include the complete dataset.

Then click:

**OK**

A PivotTable is created.

---

# 18. Filter the PivotTable to High Credit

The newly created **Credit Category** field is used as a filter.

### Steps

1. Locate **Credit Category** in the PivotTable Fields pane.
2. Drag **Credit Category** into the **Filters** area.
3. Open the filter.
4. Select:

> **High**

Now the PivotTable contains only records that meet the High Credit criterion.

---

# 19. Add Marital Status

To validate the result by marital status:

1. Locate **Marital Status**.
2. Drag it into the appropriate **Rows** area of the PivotTable.

This allows the average loan amount to be examined separately for different marital-status categories.

---

# 20. Filter for the Teen Age Group

The original Excel data does not have the same Age Groups categorization available directly, so the lecture uses the **Age** column.

For the **Teen** category, the defined ages are:

* **18**
* **19**

### Steps

1. Locate the **Age** field.
2. Add it to the PivotTable.
3. Open the age filter.
4. Select the option for **multiple items** if required.
5. Select **All** initially.
6. Keep only:

   * **18**
   * **19**
7. Click **OK**.

Now the PivotTable is restricted to the Teen age group.

---

# 21. Add Loan Amount to the PivotTable

The next step is to calculate the average loan amount.

### Steps

1. Locate **Loan Amount** in the PivotTable Fields pane.
2. Double-click **Loan Amount** or drag it into the **Values** section.
3. Excel initially calculates:

> **Sum of Loan Amount**

This needs to be changed to an average.

---

# 22. Change Sum of Loan Amount to Average

### Steps

1. Open the drop-down beside the Loan Amount value field.
2. Select **Value Field Settings**.
3. Change the calculation from **Sum** to **Average**.
4. Click **OK**.

The PivotTable now shows the **Average Loan Amount**.

---

# 23. Validate the Single Category

The PivotTable is now filtered to:

* **Credit Category:** High
* **Age:** 18 and 19 / Teen
* **Marital Status:** Single

The Excel result is approximately:

> **128,565.38**

This matches the value previously observed in Power BI:

> **128,565.39**

The very small difference in the last decimal place is due to displayed precision/rounding.

### Validation conclusion

The value calculated from the Excel source agrees with the Power BI result, confirming that the calculation is working correctly.

---

# 24. Validate the Married Category

The same validation can be performed for the **Married** category.

Keep:

* **Credit Category:** High
* **Age:** 18 and 19 / Teen
* **Marital Status:** Married

The Excel PivotTable gives approximately:

> **124,870.61**

This matches the value checked previously in Power BI.

Therefore, this provides another confirmation that the donut chart is correctly representing the data.

---

# 25. Three-Level Validation

The lecture effectively validates the result at three levels:

### Level 1 — Donut Chart

The final visual displays the average loan amount.

↓

### Level 2 — Power BI Table

A temporary table calculates the average loan amount directly using:

**Loan Amount → Average**

with the appropriate category selections.

↓

### Level 3 — Excel PivotTable

The original Excel data is independently filtered and summarized using:

**Credit Category → High**
**Age → 18 and 19**
**Marital Status → Single/Married**
**Loan Amount → Average**

When the values agree, the visual and calculation can be considered validated.

---

# 26. Important Validation Values

| Age Group | Marital Status | Credit Category | Average Loan Amount |
| --------- | -------------- | --------------- | ------------------: |
| Teen      | Single         | High            |         ~128,565.39 |
| Teen      | Married        | High            |         ~124,870.61 |

These are the examples explicitly checked in the lecture.

---

# 27. Remove the Temporary Table Visual

Once validation is complete, the temporary Power BI table is no longer needed.

### Steps

1. Return to Power BI.
2. Select the temporary **Table Visual**.
3. Delete/remove the visual from the canvas.

The temporary table was only created for validation and should not remain as part of the final report page.

---

# 28. Key Concepts Learned

## Data Validation

Always validate important calculations rather than assuming that a visual is correct.

A useful validation approach is:

> **Visual → Independent Power BI calculation → Original source data**

---

## Independent Calculation

When validating a DAX measure, don't simply reuse the same measure.

Instead, calculate the value independently using the visual's built-in aggregation.

For this example:

**Loan Amount → Average**

rather than using the custom **Average Loan Amount High Credit** measure.

---

## Excel PivotTable Validation

PivotTables provide a convenient way to independently reproduce Power BI aggregations.

The key operations used here are:

* Filtering
* Grouping
* Selecting categories
* Value Field Settings
* Average aggregation

---

## Credit Score Classification

The validation uses the rule:

```text
Credit Score > 650 → High
```

This criterion is implemented in Excel using an `IF` function so that the Excel data can be filtered consistently with the Power BI **High Credit** category.

---

# 29. Complete Step-by-Step Workflow

### Power BI Validation

1. Click a blank area on the report canvas.
2. Open **Visualizations**.
3. Add a **Table Visual**.
4. Add **Credit Score Bins**.
5. Add **Marital Status** and/or **Age Groups** as required.
6. Sort Credit Score Bins if necessary.
7. Add **Loan Amount**.
8. Change Loan Amount aggregation from **Sum** to **Average**.
9. Select a specific combination such as:

   * Teen
   * Single
   * High
10. Check the average loan amount.
11. Compare it with the donut chart.
12. Repeat for another combination such as Teen + Married + High.

### Excel Validation

1. Open the original Excel source.
2. Create a new column.
3. Enter an `IF` formula based on Credit Score > 650.
4. Return **High** when the condition is true.
5. Return **Not Available** otherwise.
6. Fill the formula down.
7. Rename the column **Credit Category**.
8. Select the complete dataset.
9. Go to **Insert → PivotTable**.
10. Create the PivotTable.
11. Put **Credit Category** in Filters.
12. Select **High**.
13. Add **Marital Status**.
14. Add **Age**.
15. Filter Age to **18 and 19** for the Teen category.
16. Add **Loan Amount** to Values.
17. Open **Value Field Settings**.
18. Change **Sum** to **Average**.
19. Check the Single category.
20. Compare with Power BI.
21. Check the Married category.
22. Compare with Power BI again.
23. Return to Power BI.
24. Delete the temporary validation table.

---

## Final Takeaway

The main purpose of this session is **not to create another report visual**, but to demonstrate how to verify that an existing Power BI visual is displaying correct information.

The donut chart's values are independently checked in **Power BI** and then cross-checked against the **original Excel source using a PivotTable**. The matching results for the Teen–Single–High and Teen–Married–High combinations confirm that the donut chart's underlying calculation is producing the expected results.
