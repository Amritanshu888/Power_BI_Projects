# Power BI — Data Validation of “Default Rate by Year”

## 1. Objective

This session focuses on **validating the last visual added to the first report page**.

The visual represents:

> **Default Rate (%) by Year**

The validation is performed in two ways:

1. **Inside Power BI** using a temporary table visual.
2. **Against the original Excel data source** using an Excel PivotTable.

The goal is to make sure that the DAX calculation is producing the correct default-rate percentages.

---

# 2. Create a Temporary Table Visual in Power BI

First, create a table visual to independently verify the values shown in the line chart.

### Steps

1. Go to **Report View**.
2. Click on a **blank area of the canvas**.
3. Select the **Table** visual.
4. A blank table will be created.
5. Place it somewhere on the canvas temporarily.

> This table is only for validation and will be deleted after the validation is complete.

---

# 3. Add the “Default Rate by Year” Measure

From the **Data/Fields pane**:

1. Locate the previously created **Default Rate by Year** measure.
2. Add it to the table's **Columns/Values** bucket.

The table will now contain the calculated default-rate value.

---

# 4. Add the Year Field

Next, add the Year field.

### Steps

1. Locate the **Year** column from the Loan Default table.
2. Double-click it or drag it into the table's **Columns** bucket.
3. Power BI may automatically summarize Year as:

> **Sum of Year**

We don't want Year to be summed.

### Change Year to Don't Summarize

1. Click the dropdown next to **Sum of Year**.
2. Select:

> **Don't summarize**

Now the individual years can be displayed.

---

# 5. Add the Default Column

The next step is to independently obtain the number of default and non-default records for each year.

1. Locate the **Default** column in the Loan Default table.
2. Double-click it or drag it into the table's **Columns** bucket.

The Default field contains two values:

* **TRUE** → Default case
* **FALSE** → Non-default case

---

# 6. Change Default from Sum to Count

Power BI may initially try to summarize the Default field.

We need the **number of records**, so add the Default field again and change its aggregation to **Count**.

### Steps

1. Double-click/drag the **Default** column into the Columns/Values bucket again.
2. Click its dropdown.
3. Change the aggregation to:

> **Count**

Now the table can show how many records are TRUE and FALSE for each year.

---

# 7. Sort the Data by Year

For easier validation, sort the table chronologically.

### Steps

1. Click the **Year** column/header.
2. Click the sort arrow.
3. If necessary, click it again until the years are arranged in **ascending order**.

The table should now show the years from earlier to later years.

---

# 8. Important Difference Between the Two Default Rate Measures

Before performing the calculation, the instructor highlights an important DAX difference.

There are two relevant measures:

* **Default Rate by Year**
* **Default Rate by Employment Type**

The key difference is how the total number of records is calculated using `ALL()` versus `ALLEXCEPT()`.

---

# 9. `ALL()` vs `ALLEXCEPT()`

## `ALL()`

The previously created **Default Rate by Employment Type** measure uses `ALL()` when calculating the total records.

`ALL()` removes **all filters** from the specified table/column context.

Therefore, the denominator represents the **overall total**, rather than the total for a particular category/year.

---

## `ALLEXCEPT()`

The new **Default Rate by Year** measure uses:

```DAX id="j4l8s0"
ALLEXCEPT('Loan Default', 'Loan Default'[Year])
```

`ALLEXCEPT()` removes filters **except for the field specified**.

In this case:

> The Year filter is retained.

Therefore, when calculating the default rate for 2013, the denominator is the **total number of records for 2013**, rather than the total number of records across all years.

---

# 10. Why This Matters

Suppose we want to calculate the default rate for 2013.

The calculation should be:

```text id="h4b3b4"
Default cases in 2013
---------------------- × 100
Total cases in 2013
```

It should **not** be:

```text id="g7xg09"
Default cases in 2013
---------------------- × 100
Total cases across all years
```

Because `ALLEXCEPT()` preserves the Year filter, the first calculation is performed.

This is a major point to remember when validating this measure.

---

# 11. Validate the 2013 Default Rate

Now manually calculate the default rate for one year.

The instructor uses **2013** as the example.

From the Power BI table, for **2013**:

### TRUE / Default cases

There are:

> **4,973**

records where Default = TRUE.

### FALSE / Non-default cases

There are:

> **37,812**

records where Default = FALSE.

---

# 12. Calculate the Total Records for 2013

Add the two numbers:

```text id="m3j1cd"
4,973 + 37,812 = 42,785
```

Therefore:

> **Total records for 2013 = 42,785**

---

# 13. Calculate the Default Rate Manually

The default rate is:

```text id="r4yq2k"
Default cases
---------------- × 100
Total cases
```

Substitute the numbers:

```text id="q2ykm0"
4,973
------ × 100
42,785
```

This gives approximately:

> **11.62%**

---

# 14. Compare with the Power BI Visual

Now return to the Power BI report.

For **2013**, the **Default Rate by Year** visual shows:

> **11.62%**

The manually calculated value is also:

> **11.62%**

Therefore:

**Manual calculation = Power BI calculation**

The visual is correct for 2013.

---

# 15. Why Only the 2013 Total Is Used

This is an important validation concept.

The total used in the calculation is:

> **42,785 records for 2013**

rather than the total number of records across the entire dataset.

Why?

Because the DAX measure uses:

```DAX id="5t0j9k"
ALLEXCEPT('Loan Default', 'Loan Default'[Year])
```

This means:

> Keep the Year filter.

Therefore, when calculating the 2013 default rate, only the **2013 records** are considered in the denominator.

---

# 16. Validate Against the Original Excel Source

The next step is to independently validate the result using the **original Excel dataset**.

The temporary Power BI table can be removed after this validation, but the instructor proceeds to the Excel source to perform a second validation.

---

# 17. Prepare the Excel Source

Open the Excel workbook containing the original Loan Default data.

The workbook contains some filters from the previous validation exercise.

These need to be modified.

### Remove the Previous Age Filter

1. Open the relevant Excel sheet/PivotTable.
2. Remove the existing **Age filter**.
3. Remove the **Age** field from the Filters section.

---

# 18. Create a Year Column in the Source Data

At this point, the source data does not have a Year column available for the PivotTable.

Therefore, create one.

### Steps

1. Go to the **Loan Default** data sheet.
2. Add a new column, for example in **Column T**.
3. Give the column the heading:

**Year**

4. In the first data cell below the heading, enter a YEAR formula using the existing date column.

The formula is conceptually:

```excel id="7cys0q"
=YEAR(Date)
```

where `Date` represents the relevant date column from the dataset.

5. Press **Enter**.
6. Populate the formula down through all records.

The lecture uses:

> **Ctrl + Down Arrow**

to move through/populate the column.

Now every record has its corresponding Year.

---

# 19. Create a New Excel PivotTable

After creating the Year column, create a new PivotTable.

### Steps

1. Click any cell within the data.
2. Go to **Insert**.
3. Select **PivotTable** / **PivotTable from Table/Range**.
4. Select the complete data range.
5. Click **OK**.

A new PivotTable will be created.

---

# 20. Add Year to the PivotTable Filter

Use the newly created Year column.

### Steps

1. In the PivotTable field/search box, type:

**Year**

2. Drag **Year** into the **Filters** section.
3. Open the Year filter.
4. Select:

> **2013**

You can also validate another year if desired. The instructor notes that checking one or two years is sufficient to demonstrate the validation approach.

---

# 21. Add Default to the PivotTable

Now we need to determine how many TRUE and FALSE records exist for 2013.

### Steps

1. Search for:

**Default**

2. Drag **Default** into the **Rows** section.
3. Drag **Default** into the **Values** section as well.

The PivotTable will now attempt to calculate a count/sum for the Default values.

---

# 22. Correct the Default Aggregation

Initially, Excel may show an unexpected result such as **0** because it is attempting to use the wrong aggregation.

The Default field contains Boolean values:

* TRUE
* FALSE

We need the **count of records**, not their sum.

### Steps

1. Click the dropdown for the Default field in the **Values** section.
2. Select **Value Field Settings**.
3. Change the calculation from:

> **Sum**

to:

> **Count**

4. Click **OK**.

Now the PivotTable will display the number of records.

---

# 23. Understand the Excel PivotTable Result

The PivotTable will show:

* **FALSE** → non-default records
* **TRUE** → default records

For 2013, the numbers correspond to:

| Default |  Count |
| ------- | -----: |
| FALSE   | 37,812 |
| TRUE    |  4,973 |

These are the same numbers obtained in Power BI.

---

# 24. Validate the Ratio from Excel

The Excel PivotTable independently confirms the two numbers:

```text id="m9gt0q"
TRUE  = 4,973
FALSE = 37,812
```

Therefore:

```text id="30k5a7"
Total = 4,973 + 37,812
      = 42,785
```

And:

```text id="1qeg4m"
Default Rate
= 4,973 / 42,785 × 100
≈ 11.62%
```

This matches the Power BI visual.

Therefore, the calculation has been validated against the **original source data**.

---

# 25. Overall Validation Approach

The instructor effectively performs validation at multiple levels:

```text id="zsp1ov"
Power BI DAX Measure
        ↓
Default Rate by Year
        ↓
Power BI Table Visual
        ↓
TRUE + FALSE counts
        ↓
Manual calculation
        ↓
11.62% for 2013
        ↓
Compare with Line Chart
        ↓
11.62%
        ↓
Validate against Excel Source
        ↓
TRUE = 4,973
FALSE = 37,812
        ↓
Manual calculation
        ↓
11.62%
```

The values agree at every stage.

---

# 26. What to Do if the Numbers Don't Match

An important practical point from the lecture is what to do if you encounter an inaccuracy or discrepancy.

If the number displayed in the Power BI report does not match the expected value:

1. **Drill down into the calculation.**
2. Go back to the **source data**.
3. Check the underlying records.
4. Verify the filters being applied.
5. Verify the DAX calculation.
6. Identify exactly where the discrepancy originates.
7. Correct the issue.
8. Revalidate the result.
9. Only then publish/share the report again.

---

# 27. Why Data Validation Is Important

Data validation is a critical part of a data analyst's work.

During the **development stage**, there may occasionally be inaccuracies because the report is still being built and tested.

However, once the report reaches:

* Stakeholders
* Business users
* Final users
* Decision-makers

the report should not contain errors.

This is especially important because decisions may be made based on the numbers displayed in the Power BI report.

Therefore:

> **Data validation is an essential part of developing a reliable Power BI report.**

---

# 28. Key DAX Concept — `ALL()` vs `ALLEXCEPT()`

This is one of the most important concepts from this lecture.

| Function      | Behavior                                      |
| ------------- | --------------------------------------------- |
| `ALL()`       | Removes all filters                           |
| `ALLEXCEPT()` | Removes filters except the specified field(s) |

For the **Default Rate by Year** calculation:

```DAX id="7c7b1b"
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Year]
)
```

means that the Year filter remains active.

Therefore:

> Default rate for 2013 is calculated using the total records belonging to 2013.

This is different from a calculation using `ALL()`, where the denominator could represent the overall dataset total.

---

# 29. Final Validation Checklist

### Power BI validation

* [x] Create a temporary Table visual.
* [x] Add **Default Rate by Year**.
* [x] Add **Year**.
* [x] Change Year to **Don't summarize**.
* [x] Add **Default**.
* [x] Change Default aggregation to **Count**.
* [x] Sort Year in ascending order.
* [x] Identify TRUE and FALSE counts.
* [x] Manually calculate the default rate.
* [x] Compare the manual result with the line chart.

### Excel/source validation

* [x] Remove the previous Age filter.
* [x] Remove Age from the filter section.
* [x] Create a **Year** column from the date.
* [x] Populate Year for all records.
* [x] Create a new PivotTable.
* [x] Add Year to Filters.
* [x] Select 2013.
* [x] Add Default to Rows.
* [x] Add Default to Values.
* [x] Change aggregation from **Sum → Count**.
* [x] Verify TRUE/FALSE counts.
* [x] Manually calculate the default percentage.
* [x] Compare it with Power BI.

---

# 30. Final Result for 2013

The validation performed in the lecture gives:

| Metric             |       Value |
| ------------------ | ----------: |
| Default = TRUE     |       4,973 |
| Default = FALSE    |      37,812 |
| Total 2013 records |      42,785 |
| Default Rate       |  **11.62%** |
| Power BI visual    |  **11.62%** |
| Validation         | **Correct** |

Thus, the **Default Rate by Year** visual on the first report page has been successfully validated against both an independent Power BI table calculation and the original Excel source data.

The next part of the course moves on to **adding two additional pages to the Power BI report**.
