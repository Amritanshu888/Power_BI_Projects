# Power BI — Data Validation of Average Loan Amount by Age Group

## 1. Objective

The purpose of this session is to **validate the Average Loan Amount by Age Group chart** created in the previous session.

The validation is performed in **two ways**:

1. By creating a **table visual in Power BI** without using the previously created measure.
2. By validating the results against the **original Excel source data**.

This ensures that the calculations used in the chart are producing the correct results.

---

# 2. Create a Table Visual in Power BI for Validation

First, create a simple table visual in Power BI so that the average loan amount can be inspected directly.

### Steps

1. Go to **Report View**.
2. Click on a **blank area of the report canvas**.
3. Select the **Table** visual.
4. A blank table will be created.

---

# 3. Add Age Group to the Table

We need to see the average loan amount for each age group.

1. In the **Data/Fields pane**, locate the **Age Group** column.
2. Check the box next to **Age Group**.
3. The table will now display the different age-group categories.

The categories created previously are:

* Teen
* Adults
* Middle Age Adults
* Senior Citizens

---

# 4. Add Loan Amount to the Table

Next, add the Loan Amount column.

1. Locate the **Loan Amount** column.
2. Check the box next to **Loan Amount**.

### Important

Power BI will initially aggregate the Loan Amount as:

> **Sum of Loan Amount**

But we do **not** want the sum.

We need to compare the **average loan amount**, so change the aggregation.

### Change Sum to Average

1. Click the dropdown next to **Loan Amount** in the table visual.
2. Change the aggregation from **Sum** to **Average**.

The table will now show the average loan amount for each age group.

---

# 5. Compare the Power BI Table with the Line Chart

Now compare the values from this table with the values shown in the line chart created in the previous session.

### Example: Teen Age Group

For the **Teen** category:

* The table visual shows approximately **126,674**.
* The more precise value is approximately **126,673.94**.
* The line chart also displays approximately **126,674**, because the chart value is rounded.

Therefore, the values match after rounding.

### Validation Approach

You do not necessarily need to compare every single value.

You can:

1. Select one or two categories.
2. Compare the values from the table with the line chart.
3. Check whether the values match after accounting for rounding.

If the values match, it provides confidence that the measure and chart are working correctly.

---

# 6. Validate Against the Original Excel Source

The next step is to validate the Power BI results directly against the **source Excel file**.

This is a more reliable form of validation because we are comparing the calculated Power BI result with the original source data.

Open the Excel file containing the original dataset.

---

# 7. Remove the Previous Excel Validation Filters

The Excel sheet contains filters/pivot-table settings from the previous validation exercise.

These need to be cleared before performing the current validation.

### Remove the Default Filter

1. Locate the **Default** field/filter.
2. Click its dropdown.
3. Select **All**.
4. Click **OK**.

This removes the existing filtering based on Default.

### Remove Default from the Filter Section

1. Double-click the **Default** field in the filter area.
2. Remove it from the filter section.

---

# 8. Configure the Excel Data for Age Group Validation

Now configure the Excel data so that we can calculate the average loan amount for a particular age group.

### Remove Employment Type

1. Locate **Employment Type** in the Rows section.
2. Remove it.

We don't need Employment Type for this validation.

### Add Age to the Filters

1. Locate the **Age** field.
2. Move/drag **Age** into the **Filters** section.

This allows us to select the individual ages belonging to a particular age group.

---

# 9. Remove Count of Default

The Excel pivot currently has **Count of Default** being displayed.

That is not required for this validation.

1. Remove **Count of Default** from the values section.

We only need the **average Loan Amount**.

---

# 10. Add Loan Amount to the Values Section

Now add Loan Amount.

### Steps

1. In the Excel field/search box, type:

**Amount**

2. Locate **Loan Amount**.
3. Double-click **Loan Amount** or drag it into the **Values** section.
4. Excel will initially calculate:

> **Sum of Loan Amount**

5. Click the dropdown for Loan Amount.
6. Select **Value Field Settings**.
7. Change the calculation from **Sum** to **Average**.
8. Click **OK**.

The Excel pivot table will now calculate the **average loan amount**.

---

# 11. Validate the Teen Age Group

To validate the **Teen** category, remember how the Age Group calculated column was defined:

```text
Age ≤ 19 → Teen
```

Since the dataset starts at age 18, the Teen group consists of:

* **Age 18**
* **Age 19**

### Steps

1. Open the **Age** filter in Excel.
2. Select the option to select multiple items if necessary.
3. Select the ages:

   * 18
   * 19
4. Click **OK**.

Excel will now calculate the average loan amount only for borrowers aged 18 and 19.

---

# 12. Compare the Excel Result with Power BI

The Excel result for the Teen group is approximately:

> **126,673**

The Power BI table visual gives approximately:

> **126,673.94**

The line chart displays approximately:

> **126,674**

The small difference in appearance is simply due to **rounding**.

Therefore:

**Excel source ≈ Power BI table ≈ Power BI line chart**

This confirms that the calculation is correct.

---

# 13. Two-Level Data Validation

The lecture validates the calculation in **two different ways**.

## Validation Method 1 — Power BI Table

A table visual was created in Power BI using:

* **Age Group**
* **Loan Amount**

The Loan Amount aggregation was changed from:

> Sum → Average

This provides an independent calculation inside Power BI without directly using the previously created **Average Loan by Age Group** measure.

The resulting values were compared with the line chart.

---

## Validation Method 2 — Excel Source

The original Excel source data was then used to independently reproduce the calculation.

For example:

```text
Teen
↓
Age 18 + Age 19
↓
Average Loan Amount
↓
≈ 126,673
```

This was compared with the Power BI results.

Because the values match, the calculation has been validated against the source data.

---

# 14. Why This Validation Is Important

Data validation is important because a visual may look correct while the underlying calculation could still be incorrect.

Here, we verify the result at multiple levels:

```text
Original Excel Data
        ↓
Independent Excel Average
        ↓
Power BI Table Average
        ↓
Power BI Calculated Measure
        ↓
Power BI Line Chart
```

When these values agree, we have much greater confidence that the visual is correctly representing the underlying data.

---

# 15. Remove the Temporary Validation Table

Once validation is complete, the temporary table visual is no longer required in the final report.

### Steps

1. Select the temporary **table visual** in Power BI.
2. Press the **Delete** key on the keyboard.

The temporary validation table will be removed from the report canvas.

---

# 16. Complete Validation Workflow

The complete process from the lecture can be summarized as:

```text
Existing Average Loan Amount by Age Group Chart
                ↓
        Create Table Visual
                ↓
        Add Age Group
                ↓
        Add Loan Amount
                ↓
       Change Sum → Average
                ↓
     Compare with Line Chart
                ↓
        Open Excel Source
                ↓
       Remove Default Filter
                ↓
       Remove Employment Type
                ↓
          Add Age Filter
                ↓
      Remove Count of Default
                ↓
       Add Loan Amount
                ↓
        Sum → Average
                ↓
       Select Age 18 & 19
                ↓
      Validate Teen Category
                ↓
 Compare Excel ↔ Power BI Table
                ↓
 Compare Power BI Table ↔ Chart
                ↓
        Validation Complete
                ↓
      Delete Temporary Table
```

---

# Key Takeaways

### 1. Always validate calculated visuals

After creating a DAX measure and visual, independently verify the result.

### 2. Don't rely only on the visual

A chart can display a number, but creating a separate table using the underlying fields provides an independent way to check the calculation.

### 3. Validate against the source

The strongest validation in this session was comparing Power BI's result against the **original Excel data**.

### 4. Account for rounding

The line chart may show a rounded number such as:

**126,674**

while the underlying calculation may be:

**126,673.94**

These should be considered matching because the displayed chart value is rounded.

### 5. Validate multiple categories when possible

The instructor suggests checking one or two categories to establish that the calculation is behaving correctly. For more rigorous real-world reporting, it is preferable to validate **all categories or a representative sample**.

### 6. Remove temporary validation visuals

Once validation is complete, remove the temporary table so that only the intended report visuals remain.

**Next:** The following session will continue with adding additional visuals to the report.
