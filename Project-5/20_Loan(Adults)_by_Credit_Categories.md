# Detailed Notes: Creating a Line Chart for Total Loan Amount by Credit Score Bins

## 1. Objective of the Session

In this session, another visual is added to the **second report page**.

The visual is a **Line Chart** that represents:

> **Total Loan Amount by different Credit Score Categories/Bins, considering only Adults.**

The session has two major parts:

1. **Create and format the line chart using a DAX measure.**
2. **Validate the line-chart data**:

   * First directly in Power BI without using the DAX measure.
   * Then against the original Excel data source.

The session also demonstrates why **data validation is important in real-world Power BI projects**.

---

# 2. Create the DAX Measure

Because the visual is being created on the second report page, the measure is created in **Measures Table 2**.

### Steps

1. Go to the **Data pane** on the right.
2. Locate **Measures Table 2**.
3. Right-click **Measures Table 2**.
4. Select **New Measure**.

Power BI may take some time to display the formula bar. The instructor mentions that Power BI can sometimes behave abruptly or take longer than expected while loading the formula bar.

---

# 3. Name the Measure

The measure can be given a suitable name such as:

> **Total Loan Amount by Credit Bins**

The lecture mentions that you can use either **Credit Categories** or **Credit Bins** in the measure name; the exact name is not critical as long as it clearly describes the calculation.

---

# 4. DAX Functions Used

The measure uses two important DAX functions:

* `CALCULATE()`
* `SUM()`

It also uses:

* `ALLSELECTED`-style filter-preservation logic via **`ALLEXCEPT()`** as described in the lecture.

The purpose is to calculate the **total loan amount for adults**, while controlling which filters are allowed to affect the measure.

---

# 5. DAX Measure Logic

The measure follows this basic structure:

```DAX
Total Loan Amount by Credit Bins =
CALCULATE(
    SUM('Loan Default'[Loan Amount]),
    'Loan Default'[Age Groups] = "Adults",
    ALLEXCEPT(
        'Loan Default',
        'Loan Default'[Age],
        'Loan Default'[Age Groups],
        'Loan Default'[Credit Score],
        'Loan Default'[Credit Score Bins]
    )
)
```

> Use the exact table and column names from your own model. The lecture uses the **Loan Default** table and the previously created Age Groups/Credit Score Bins columns.

---

# 6. Understanding the `SUM()` Function

Inside `CALCULATE()`, the first calculation is:

```DAX
SUM('Loan Default'[Loan Amount])
```

This calculates the:

> **Total Loan Amount**

by adding the Loan Amount values.

---

# 7. Filter the Data to Adults

The next condition specifies that only adults should be included:

```DAX
'Loan Default'[Age Groups] = "Adults"
```

Therefore, the measure ignores non-adult age groups for the purpose of this calculation.

The calculation becomes conceptually:

> **Total Loan Amount where Age Group = Adults**

---

# 8. Use `ALLEXCEPT()` to Control Filters

The lecture then introduces `ALLEXCEPT()`.

The purpose is to control which filters from other visuals/slicers should continue to affect the measure.

The lecture specifies these columns:

1. **Age**
2. **Age Groups**
3. **Credit Score**
4. **Credit Score Bins**

Conceptually:

```text
ALLEXCEPT(
    Loan Default,
    Age,
    Age Groups,
    Credit Score,
    Credit Score Bins
)
```

This means the measure removes other filter contexts from the table while preserving filters associated with these specified columns.

### Why this is being used

The instructor wants the line chart to respond to filters involving:

* Age
* Age Group
* Credit Score
* Credit Score Bins

while maintaining the **Adults** condition in the measure.

---

# 9. Complete Calculation Logic

The measure can therefore be understood as:

```text
Calculate
    ↓
Sum Loan Amount
    ↓
Only where Age Group = Adults
    ↓
Preserve filter context for:
    • Age
    • Age Groups
    • Credit Score
    • Credit Score Bins
```

After entering the DAX formula:

1. Press **Enter**.
2. Wait for Power BI to finish creating the measure.
3. Collapse the formula bar if desired.

---

# 10. Create the Line Chart

Instead of creating a completely new line chart from scratch, the lecture duplicates an existing line chart.

### Steps

1. Click a blank area of the report canvas.
2. Select the existing line chart.
3. Press:

**Ctrl + C**

4. Then press:

**Ctrl + V**

A copy of the line chart is created.

5. Move the newly created line chart to the desired position on the report page.

---

# 11. Configure the X-Axis

The duplicated line chart already contains **Credit Score Bins** along the X-axis.

This is exactly what is required because the objective is to show:

> Total Loan Amount by different Credit Score Bins.

Therefore, the existing **Credit Score Bins** field can remain on the X-axis.

---

# 12. Replace the Existing Measure

The original line chart was showing **Median**.

However, the new chart should show **Total Loan Amount**.

### Steps

1. Select the newly duplicated line chart.
2. Locate the existing **Median** field/measure.
3. Remove it.
4. Add the newly created **Total Loan Amount by Credit Bins** measure.

The chart now displays the total loan amount for different credit-score bins.

---

# 13. Format the Chart Title

The title should explain exactly what the visual represents.

### Steps

1. Select the line chart.
2. Open **Format Your Visual**.
3. Go to **General**.
4. Expand **Title**.
5. Change the title to something like:

> **Total Loan (Adults) by Credit Score Bins**

The lecture uses the wording:

> **Total Loan (Adults) by credit score Bins**

The capitalization can be adjusted according to the report's formatting convention.

---

# 14. Change the Line Color

The line itself is also formatted.

### Steps

1. Select the line chart.
2. Open **Format Your Visual**.
3. Go to **Visual**.
4. Expand **Lines**.
5. Scroll down to the color settings.
6. Open **Colors**.
7. Select **More Colors**.
8. Enter the color code used in the lecture:

> **#8C8CE1**

The line is now displayed using the selected color.

---

# 15. Optional Marker Formatting

The lecture also demonstrates some additional formatting options.

### Markers

Under the line-chart formatting options:

1. Locate **Markers**.
2. Expand the section.
3. You can change the marker style.

The instructor selects a different marker as an example.

### Marker colors

You can also change the marker color if required.

However, the lecture does **not** make an additional marker-color change in the final version.

---

# 16. Shaded Area and Transparency

The lecture also points out that other formatting options are available.

For example, you can:

* Change the shaded area.
* Adjust transparency.

These settings can be customized depending on the desired appearance.

They are demonstrated as optional formatting possibilities rather than being essential to the final chart.

---

# 17. Resulting Line Chart

The final line chart represents:

> **Total Loan Amount for Adults across different Credit Score Bins.**

The X-axis represents the **Credit Score Bins**, while the Y-axis represents the **total loan amount** calculated through the DAX measure.

---

# 18. Data Validation

After creating the visual, the instructor emphasizes the importance of validating the data.

The validation is performed in two stages:

### Stage 1

Validate the value directly in **Power BI** without using the DAX measure.

### Stage 2

Validate the same result using the **original Excel source data**.

This ensures that the calculation shown in the report is correct.

---

# 19. Create a Temporary Table Visual in Power BI

To independently validate the line chart:

1. Click on a blank area of the canvas.
2. Expand the **Visualizations** pane.
3. Select **Table Visual**.

A blank table is created.

---

# 20. Add Fields to the Validation Table

Add the following fields:

* **Age Groups**
* **Credit Score Bins**
* **Loan Amount**

### Steps

1. Add **Age Groups** to the table.
2. Add **Credit Score Bins**.
3. Add **Loan Amount**.

The table now allows the loan amount to be inspected for different combinations of age groups and credit-score bins.

---

# 21. Validate the High Credit Category for Adults

The lecture uses an example where the filters/categories are:

* **Age Group = Adults**
* **Credit Score Bin = High**

The total loan amount for this combination is approximately:

> **4.5 billion**

The exact value displayed in Power BI can be compared with the corresponding point on the line chart.

The instructor hovers over the relevant point in the line chart to see the exact value and compares it with the value in the table.

The transcript mentions a displayed number beginning around:

> **4,339...**

The important point is that the values agree.

---

# 22. Why Hover Over the Line Chart?

When you hover over a point on the line chart, Power BI displays the detailed value in a tooltip.

This makes it easy to compare:

**Table Visual Value**

against

**Line Chart Tooltip Value**

If both values match, the line chart is correctly representing the calculation.

---

# 23. Validate Other Credit Score Categories

The same approach can be used for other credit-score bins.

For example:

1. Select a different **Credit Score Bin**.
2. Keep **Age Group = Adults**.
3. Check the total loan amount in the table.
4. Hover over the corresponding line-chart point.
5. Compare the two values.

This allows multiple points on the line chart to be independently validated.

---

# 24. Validate Against the Excel Source

After validating the line chart within Power BI, the original Excel source is opened.

The objective is to reproduce the same calculation directly from the source data.

Because the report needs data only for **Adults**, a new helper column is created in Excel.

---

# 25. Create an Age Group Identifier in Excel

The lecture creates a new column to identify the **Adults** category.

The adult age range used is:

> **20 to 39 years**

The instructor uses cell **V2** for the new calculation.

---

# 26. Excel `IF` + `AND` Formula

In cell **V2**, enter an `IF` function containing an `AND` condition.

The logic is:

```excel
=IF(AND(B2>=20,B2<=39),"Adults","N/A")
```

### Formula breakdown

The `AND()` function checks two conditions:

```text
B2 >= 20
AND
B2 <= 39
```

If both conditions are true:

> **Adults**

Otherwise:

> **N/A**

---

# 27. Logic of the Excel Formula

The classification works as follows:

|             Age | Identifier |
| --------------: | ---------- |
|    Less than 20 | N/A        |
|           20–39 | Adults     |
| Greater than 39 | N/A        |

Therefore, only ages **20 through 39 inclusive** are classified as Adults.

---

# 28. Fill the Formula Down

After entering the formula in **V2**:

1. Select cell **V2**.
2. Move to the bottom-right corner of the cell.
3. Double-click the fill handle.

Excel automatically fills the formula down through the dataset.

---

# 29. Rename the Helper Column

The new column is renamed:

> **Identifier**

This column is used to identify records belonging to the Adult age group.

---

# 30. Create an Excel PivotTable

The PivotTable is used to independently calculate the total loan amount.

### Steps

1. Click any cell within the Excel dataset.
2. Go to the **Insert** tab.
3. Select **PivotTable**.
4. Confirm the data range.
5. Click **OK**.

An Excel PivotTable is created.

---

# 31. Apply the Credit Category Filter

The Excel sheet already contains the **Credit Category** column created during the previous validation exercise.

That column identifies:

> **High**

for high-credit-score records.

### Steps

1. Locate **Credit Category** in the PivotTable Fields pane.
2. Place it in the **Filters** section.
3. Open the filter.
4. Select:

> **High**

Now the PivotTable is restricted to high-credit records.

---

# 32. Apply the Adult Filter

Next, use the newly created **Identifier** column.

### Steps

1. Drag **Identifier** into the **Filters** area.
2. Open its filter.
3. Select:

> **Adults**

The PivotTable now contains only records satisfying both:

```text
Credit Category = High
AND
Identifier = Adults
```

---

# 33. Add Loan Amount

Now add the numerical field that needs to be validated.

### Steps

1. Locate **Loan Amount**.
2. Double-click it or drag it into the **Values** section.

Excel initially calculates:

> **Sum of Loan Amount**

This is exactly what is required for this line chart because the line chart represents **total loan amount**, not average or median.

---

# 34. Check the Excel Total

The resulting PivotTable value should match the total displayed in Power BI.

The lecture observes that:

> The total in Excel is the same as the total shown in Power BI Desktop.

This confirms that the Power BI calculation is correctly representing the underlying source data.

---

# 35. Why This Validation Matters

The instructor emphasizes that validation is a very important part of real-world data work.

When data goes through multiple stages:

```text
Excel Source
    ↓
SQL Server
    ↓
Data Flow
    ↓
Power BI Dataset
    ↓
DAX Calculations
    ↓
Report Visual
```

there are multiple opportunities for a calculation, transformation, filter, or aggregation to produce an unexpected result.

Therefore, validating the final report against the original source is an important part of the job.

---

# 36. Three-Level Validation for This Visual

The line chart is effectively validated through three levels:

### 1. Power BI Table

Calculate the total loan amount directly using the table visual.

### 2. Power BI Line Chart

Hover over the relevant line-chart point and compare its value with the table.

### 3. Excel Source

Use an Excel PivotTable to calculate:

**High Credit + Adults → Total Loan Amount**

If all three results agree, the visual is validated.

---

# 37. Remove the Temporary Validation Table

Once the validation is complete, the temporary table visual is no longer required.

### Steps

1. Return to the Power BI report.
2. Select the temporary table visual.
3. Delete/remove it from the canvas.

The table was created only for validation purposes.

---

# 38. Resize the Line Chart

After deleting the temporary validation table:

1. Select the line chart.
2. Adjust its size.
3. Reduce the size slightly if necessary.
4. Ensure it fits properly with the other visuals on the report page.

The final report should contain the line chart along with the other previously created visuals.

---

# 39. Important DAX Concepts

## `CALCULATE()`

`CALCULATE` changes the filter context in which an expression is evaluated.

Here, it is used to calculate the loan amount under the condition:

> Age Group = Adults

---

## `SUM()`

`SUM()` adds the values in the Loan Amount column.

It is used because the requirement is:

> **Total Loan Amount**

---

## `ALLEXCEPT()`

`ALLEXCEPT()` removes filters from a table except for the columns specifically mentioned.

In this measure, the lecture preserves filters related to:

* Age
* Age Groups
* Credit Score
* Credit Score Bins

This allows the measure to interact with relevant slicers/visuals while maintaining the intended calculation.

---

# 40. Important Excel Concepts

The Excel validation introduces/reinforces:

### `IF()`

Used to assign a category based on a condition.

### `AND()`

Used when multiple conditions must be true simultaneously.

The adult classification is:

```text
Age >= 20
AND
Age <= 39
```

### PivotTable

Used to independently summarize and validate the source data.

---

# 41. Final Configuration of the Line Chart

| Component              | Configuration                            |
| ---------------------- | ---------------------------------------- |
| **Visual**             | Line Chart                               |
| **X-axis**             | Credit Score Bins                        |
| **Y-axis/Values**      | Total Loan Amount by Credit Bins         |
| **Age condition**      | Adults                                   |
| **Adult age range**    | 20–39                                    |
| **Calculation**        | Sum of Loan Amount                       |
| **Main DAX functions** | `CALCULATE`, `SUM`, `ALLEXCEPT`          |
| **Title**              | Total Loan (Adults) by Credit Score Bins |
| **Line color**         | `#8C8CE1`                                |
| **Markers**            | Optional/customizable                    |
| **Validation**         | Power BI Table + Excel PivotTable        |

---

# 42. Complete Step-by-Step Workflow

### Part A — Create the Measure

1. Right-click **Measures Table 2**.
2. Select **New Measure**.
3. Name it **Total Loan Amount by Credit Bins**.
4. Use `CALCULATE()`.
5. Inside it, use `SUM()` on **Loan Amount**.
6. Apply the condition **Age Groups = Adults**.
7. Use `ALLEXCEPT()` to preserve the required filters:

   * Age
   * Age Groups
   * Credit Score
   * Credit Score Bins
8. Press **Enter**.

### Part B — Create the Line Chart

9. Click the blank report canvas.
10. Copy the existing line chart using **Ctrl+C**.
11. Paste it using **Ctrl+V**.
12. Move the duplicate to the desired location.
13. Keep **Credit Score Bins** on the X-axis.
14. Remove **Median**.
15. Add the newly created total-loan measure.
16. Change the title to **Total Loan (Adults) by Credit Score Bins**.
17. Format the line color.
18. Use `#8C8CE1`.
19. Optionally customize markers and transparency.
20. Resize the chart.

### Part C — Validate in Power BI

21. Add a temporary **Table Visual**.
22. Add **Age Groups**.
23. Add **Credit Score Bins**.
24. Add **Loan Amount**.
25. Check the **Adults + High Credit** combination.
26. Compare the table value with the line-chart tooltip.
27. Repeat for other categories if required.

### Part D — Validate in Excel

28. Open the original Excel source.
29. Create a new column at **V2**.
30. Use `IF` + `AND`.
31. Define Adults as ages **20–39**.
32. Return **Adults** if the condition is true.
33. Return **N/A** otherwise.
34. Fill the formula down.
35. Rename the column **Identifier**.
36. Create a PivotTable.
37. Filter **Credit Category = High**.
38. Filter **Identifier = Adults**.
39. Add **Loan Amount** to Values.
40. Verify that Excel's total matches Power BI.
41. Delete the temporary Power BI validation table.
42. Resize the final line chart.

---

## Final Takeaway

The key lesson of this session is that a Power BI visual should not just be created—it should also be **validated**.

The line chart uses a DAX measure to calculate the **total loan amount for Adults by Credit Score Bins**. The result is then independently checked using a Power BI table and finally verified against the original Excel data through a PivotTable.

The validation confirms that the data flowing through the transformation and reporting process is producing the expected result, which is especially important when working with real-world Power BI projects.
