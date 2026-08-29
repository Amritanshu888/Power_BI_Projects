# Power BI — Creating and Formatting a Matrix Visual + Using Slicers and Report-Level Filters

## 1. Objective of the Video

In this video, the focus is on adding a **Matrix visual** to **Page 2** of the Power BI report.

The matrix will be used to analyze:

* **Transaction Amount**
* **Remaining Balance**
* Across different **months**
* For different **cities**
* For different **currencies**

The video also demonstrates:

1. Creating a Matrix visual.
2. Adding numerical fields to the Values bucket.
3. Formatting numbers with thousand separators and zero decimal places.
4. Using Month in Rows.
5. Using City and Currency in Columns.
6. Expanding a hierarchy.
7. Removing row and column subtotals.
8. Renaming automatically generated measure labels.
9. Formatting values, row headers, and column headers.
10. Adding gridlines and a border.
11. Using slicers to filter the matrix.
12. Using the Currency filter configured for **all report pages**.
13. Understanding how a report-level/all-pages filter affects both pages.
14. Clearing the filter and restoring the matrix.

---

# 2. Navigate to Page 2

The matrix visual is going to be added to the **second report page**.

### Steps

1. Go to the bottom of the Power BI window.
2. Click **Page 2**.
3. This opens the second report page containing the slicers created earlier.

---

# 3. Expand the Required Panes

Before creating the matrix:

1. Expand the **Visualizations** pane.
2. Expand the **Data** pane.
3. Expand the **UPI Transactions** table.

The Data pane now shows the available fields/columns.

---

# 4. Add a Matrix Visual

### Steps

1. Click on a **blank area of the report canvas**.
2. In the Visualizations pane, select **Matrix**.

Power BI creates a blank Matrix visual.

### Resize and Position

After creating the matrix:

* Resize it according to the available space.
* Move it to the desired position on the report page.

The exact size and position can be adjusted according to the report design.

---

# 5. Add Transaction Amount to the Matrix

The matrix should display transaction amounts.

The relevant field is:

**`Amount`**

### Steps

1. Locate `Amount` under the `UPI Transactions` table.
2. Double-click it or drag it.
3. Place it in the **Values** bucket of the Matrix visual.

Power BI automatically aggregates the field, so it initially appears as:

**Sum of Amount**

---

# 6. Add Remaining Balance

The matrix should also show the remaining balance.

The relevant field is:

**`Remaining Balance`**

### Steps

1. Locate `Remaining Balance` in the Data pane.
2. Drag it to the **Values** bucket.
3. Alternatively, double-click the field and then place it in Values.

The matrix now contains two numerical values:

* Sum of Amount
* Sum of Remaining Balance

---

# 7. Format the Numerical Values

The values should be displayed in a more readable format.

The desired formatting includes:

* **Thousands separator**
* **Zero decimal places**

---

## Format Amount

### Steps

1. Select the `Amount` field/value.
2. Click the **comma (,)** formatting option to add a thousand separator.
3. Change the number of **decimal places to 0**.

For example:

```text
1642.50
```

can be displayed as:

```text
1,643
```

depending on the actual value and formatting/rounding.

---

## Format Remaining Balance

Repeat the same process for `Remaining Balance`:

1. Select `Remaining Balance`.
2. Enable the **comma/thousands separator**.
3. Change **decimal places to 0**.

This keeps both numerical fields consistently formatted.

---

# 8. Add Transaction Date to Rows

The matrix needs to show the information by **month**.

The relevant field is:

**`Transaction Date`**

### Steps

1. Locate `Transaction Date` in the Data pane.
2. Drag it to the **Rows** bucket.

Power BI may automatically create a date hierarchy containing:

* Year
* Quarter
* Month
* Day

---

# 9. Keep Only Month in the Rows

The matrix does not need all levels of the date hierarchy.

The requirement is to represent the data by **month**.

Therefore, remove:

* **Quarter**
* **Day**

The required level is:

**Month**

The matrix will now show the transaction information month by month.

---

# 10. Add City to Columns

The matrix should also compare the values for different cities.

The relevant field is:

**`City`**

### Steps

1. Locate `City` in the Data pane.
2. Drag it into the **Columns** bucket.

The matrix now creates separate column groupings for different cities.

---

# 11. Add Currency Under City

The matrix should also distinguish between different currencies.

The relevant field is:

**`Currency`**

### Steps

1. Locate `Currency` in the Data pane.
2. Drag it into the **Columns** bucket.
3. Place it **under the City field** in the column hierarchy.

The resulting column hierarchy is conceptually:

```text
City
   └── Currency
```

This means the matrix can show currency-level information within each city.

---

# 12. Expand the City → Currency Hierarchy

Power BI provides an option to expand the hierarchy.

The lecture uses:

**Expand all down one level in the hierarchy**

### Steps

1. Select the Matrix visual.
2. Locate the hierarchy expansion controls.
3. Select the option to **expand all down one level in the hierarchy**.

This expands the cities so that their corresponding currencies are visible.

---

# 13. Initial Matrix Structure

At this point, the matrix is conceptually structured as:

### Rows

**Month**

### Columns

**City → Currency**

### Values

* Amount
* Remaining Balance

So the matrix answers questions such as:

> What was the transaction amount and remaining balance for a particular month, city, and currency?

---

# 14. Turn Off Column Subtotals

The matrix may initially display subtotals for the column hierarchy.

The lecture removes these because they are not required.

### Steps

1. Select the Matrix visual.
2. Open **Format your visual**.
3. Locate the **Column subtotals** setting.
4. Change it to:

**Off**

---

# 15. Turn Off Row Subtotals

Row subtotals are also disabled.

### Steps

1. In the Matrix formatting options, locate **Row subtotals**.
2. Change it to:

**Off**

The matrix now displays the detailed values without unnecessary subtotal rows/columns.

---

# 16. Rename "Sum of Amount" to "Amount"

Power BI automatically labels the numerical field as:

**Sum of Amount**

However, the desired display is simply:

**Amount**

### Steps

1. Select the Matrix visual.
2. Click **Add data to your visual** / access the Values field area.
3. Locate **Sum of Amount** in the Values bucket.
4. Double-click the field name.
5. Rename it to:

**Amount**

6. Press **Enter**.

The matrix now displays **Amount** rather than **Sum of Amount**.

---

# 17. Rename "Sum of Remaining Balance"

Similarly, Power BI initially displays:

**Sum of Remaining Balance**

The desired label is:

**Remaining Balance**

### Steps

1. Locate **Sum of Remaining Balance** in the Values bucket.
2. Double-click its name.
3. Change the name to:

**Remaining Balance**

4. Press **Enter**.

The matrix now has cleaner value labels:

* Amount
* Remaining Balance

---

# 18. Enable Blank Rows

The Matrix visual can be formatted further by enabling blank rows.

### Steps

1. Select the Matrix visual.
2. Open **Format your visual**.
3. Locate **Blank rows**.
4. Turn it:

**On**

The matrix now has blank rows where appropriate, which can make the structure easier to read.

---

# 19. Format the Values

The numerical values can be formatted using the **Values** section.

### Steps

1. Select the Matrix visual.
2. Open **Format your visual**.
3. Go to **Values**.
4. Change the font style as desired.

The lecture changes the font style to a preferred font.

The exact font is optional; the important point is that the **Values** section controls the appearance of the numerical values displayed in the matrix.

---

# 20. Format Column Headers

The column headers represent the hierarchy involving:

* City
* Currency

These can also be formatted.

### Steps

1. Open the **Column headers** section.
2. Change the font style.
3. Increase the text size.

The lecture increases the text size to approximately:

**12**

This makes the city/currency headers more readable.

---

# 21. Format Row Headers

The row headers represent the months.

### Steps

1. Open the **Row headers** formatting section.
2. Increase the font size.
3. Change the font style if desired.

The lecture changes the font and increases the size to make the month labels easier to read.

---

# 22. Add Vertical Gridlines

Gridlines can be added to make the matrix easier to read.

### Steps

1. Select the Matrix visual.
2. Open **Format your visual**.
3. Locate the **Grid** settings.
4. Enable **Vertical gridlines**.

The vertical lines help visually separate the columns.

---

# 23. Change Vertical Gridline Color

The vertical gridline color can also be customized.

### Steps

1. Under the Grid settings, locate the color option for vertical gridlines.
2. Select an appropriate color.

The lecture chooses a somewhat darker color.

The exact color is a design choice.

---

# 24. Add Horizontal Gridlines

Horizontal gridlines can also be enabled.

### Steps

1. Locate the **Horizontal gridlines** option.
2. Turn it on if desired.
3. Choose an appropriate color.
4. Adjust the line width if necessary.

The lecture indicates that both horizontal and vertical gridlines can be customized according to preference.

---

# 25. Adjust Gridline Width

The width of the gridlines can be modified.

### Steps

1. Locate the gridline **Width** setting.
2. Increase or decrease it according to the desired appearance.

The goal is to make the matrix readable without making the gridlines visually overpowering.

---

# 26. Add a Border to the Matrix

A border can be added around the Matrix visual.

### Steps

1. Select the Matrix visual.
2. Open **Format your visual**.
3. Go to:

**General → Effects**

4. Locate **Visual border**.
5. Turn it:

**On**

---

## Change Border Color

The border color can be customized.

The lecture changes it to approximately:

**Gray**

This gives the matrix a subtle boundary.

---

# 27. Final Matrix Structure

The matrix now contains:

### Rows

**Month**

### Columns

**City → Currency**

### Values

**Amount**

**Remaining Balance**

### Formatting

* Thousand separators
* Zero decimal places
* Clean field names
* Column subtotals off
* Row subtotals off
* Blank rows on
* Formatted values
* Formatted row headers
* Formatted column headers
* Optional gridlines
* Visual border

---

# 28. Using Slicers to Filter the Matrix

The matrix can now be interactively filtered using the slicers already present at the top of the report page.

This is one of the main advantages of Power BI visuals.

When a user selects an option in a slicer, the Matrix visual automatically responds to the selection.

---

# 29. Filtering by Gender

Suppose we want to see transactions only for **Male** customers.

### Steps

1. Go to the **Gender** slicer.
2. Select:

**Male**

The Matrix visual is automatically filtered.

Only transactions corresponding to the selected gender are now represented.

---

# 30. Filtering by Bank Name Received

Suppose we want to see transactions where the amount was received in **HDFC Bank**.

### Steps

1. Locate the **Bank Name Received** slicer.
2. Select:

**HDFC**

The Matrix visual updates and displays only the relevant transactions.

This demonstrates that multiple slicers can be used to filter the Matrix simultaneously.

---

# 31. Filtering by Merchant

The Matrix can also be filtered by merchant.

For example:

**IRCTC**

### Steps

1. Locate the **Merchant Name** slicer.
2. Select **IRCTC**.

The Matrix now displays the transactions associated with IRCTC.

Another merchant can be selected, for example:

**Swiggy**

The matrix updates accordingly to show transactions associated with Swiggy.

---

# 32. Filtering by Age Group

The `Age Groups` slicer created in the earlier video can also be used.

The available groups include:

* A1
* A2
* A3

### Example: Select A2

1. Locate the **Age Groups** slicer.
2. Select:

**A2**

The Matrix now displays data only for customers belonging to age group A2.

If **A1** is selected instead, the matrix updates to show the data for A1.

This demonstrates how the calculated `Age Groups` column created using DAX can now be used as an interactive report filter.

---

# 33. Applying the Currency Filter

In the previous video, the `Currency` field was added under:

**Filters on all pages**

This means it is not limited to Page 2.

It applies to the entire report.

---

# 34. Selecting GBP

To demonstrate this:

1. Open the **Filters pane**.
2. Locate the Currency filter.
3. Select:

**GBP**

The Matrix now displays only transactions associated with GBP.

According to the lecture, the GBP transactions shown in this example occurred only in:

**Hyderabad**

Therefore, the Matrix shows GBP transaction information for Hyderabad.

---

# 35. Understanding the Report-Level / All-Pages Filter

This is an important concept.

The Currency filter was placed under:

**Filters on all pages**

Therefore, when GBP is selected on Page 2, the same GBP filter affects Page 1.

### Demonstration

1. Select **GBP** in the Currency filter on Page 2.
2. Navigate to **Page 1**.
3. Page 1 is also filtered to GBP.

This occurs because the Currency filter is configured at the **all-pages/report-level scope**.

---

# 36. Important Terminology Clarification

The lecture refers to this as a page-level filter at one point, but the actual behavior being demonstrated is:

> A filter placed under **Filters on all pages** affects all pages in the report.

So conceptually, remember:

**Filters on all pages → affects every report page**

This is why selecting GBP on Page 2 also affects Page 1.

---

# 37. Removing the Currency Filter

Once the demonstration is complete, the Currency filter can be cleared.

### Steps

1. Open the Currency filter.
2. Remove/clear the **GBP** selection.
3. Navigate back to Page 2.

The Matrix returns to its original unfiltered state.

---

# 38. Final Page 2

After clearing the filters, Page 2 contains:

* The previously created slicers.
* The newly created Matrix visual.
* Month-based rows.
* City → Currency column hierarchy.
* Amount values.
* Remaining Balance values.
* Appropriate formatting.
* Interactive filtering through slicers.
* A Currency filter that can affect the entire report.

---

# 39. Matrix Configuration — Quick Reference

| Matrix Component             | Configuration                   |
| ---------------------------- | ------------------------------- |
| Visual                       | Matrix                          |
| Rows                         | Transaction Date → Month        |
| Columns                      | City → Currency                 |
| Values                       | Amount, Remaining Balance       |
| Amount formatting            | Thousands separator, 0 decimals |
| Remaining Balance formatting | Thousands separator, 0 decimals |
| Column subtotals             | Off                             |
| Row subtotals                | Off                             |
| Value label                  | Amount                          |
| Balance label                | Remaining Balance               |
| Blank rows                   | On                              |
| Values font                  | Customized                      |
| Column header size           | ~12 in lecture                  |
| Row header                   | Customized                      |
| Vertical gridlines           | Optional/On                     |
| Horizontal gridlines         | Optional/On                     |
| Gridline color               | Customized                      |
| Gridline width               | Customized                      |
| Visual border                | On                              |
| Border color                 | Gray                            |

---

# 40. Overall Workflow

The complete process demonstrated in this lecture is:

**Go to Page 2**

↓

**Add Matrix visual**

↓

**Resize and position it**

↓

**Amount → Values**

↓

**Remaining Balance → Values**

↓

**Format numbers with comma separator**

↓

**Set decimal places to 0**

↓

**Transaction Date → Rows**

↓

**Keep Month; remove unnecessary Quarter/Day**

↓

**City → Columns**

↓

**Currency → Columns under City**

↓

**Expand hierarchy one level**

↓

**Turn Row Subtotals Off**

↓

**Turn Column Subtotals Off**

↓

**Rename Sum of Amount → Amount**

↓

**Rename Sum of Remaining Balance → Remaining Balance**

↓

**Enable Blank Rows**

↓

**Format Values, Row Headers and Column Headers**

↓

**Add/configure gridlines**

↓

**Add visual border**

↓

**Use slicers to filter the Matrix**

↓

**Test Gender, Bank, Merchant and Age Group filters**

↓

**Apply GBP through the Currency all-pages filter**

↓

**Verify that Page 1 is also filtered**

↓

**Clear the Currency filter**

↓

**Return Matrix to original state**

---

# 41. Key Learning Points

### 1. Matrix visuals support multiple dimensions

A Matrix is useful when you want to analyze measures across multiple categorical dimensions.

Here, the hierarchy is:

**Month → City → Currency**

with:

**Amount + Remaining Balance**

as the measures.

---

### 2. Fields in Columns can form a hierarchy

Putting:

**City**

and then:

**Currency**

under City creates a hierarchy.

This allows the matrix to show currency-level information within each city.

---

### 3. Power BI automatically aggregates numerical fields

When `Amount` is placed in Values, Power BI initially displays:

**Sum of Amount**

This can be renamed for presentation purposes to simply:

**Amount**

The underlying aggregation remains the same.

---

### 4. Subtotals are optional

Row and column subtotals can sometimes make a matrix unnecessarily complicated.

If they are not useful for the intended analysis, they can be turned off.

---

### 5. Slicers interact with visuals

Selecting a value from a slicer automatically filters the Matrix visual.

For example:

**Gender = Male**

filters the Matrix to male transactions.

Similarly:

**Merchant = IRCTC**

filters the Matrix to IRCTC transactions.

---

### 6. All-pages filters affect the entire report

The Currency filter was configured under:

**Filters on all pages**

Therefore:

**GBP selected on Page 2 → Page 1 is also filtered to GBP**

This is an important distinction when designing multi-page Power BI reports.

---

## 42. Upcoming Topic

The next session will focus on **synchronizing slicers across the two report pages**.

This will allow slicer selections to remain consistent between Page 1 and Page 2, making the multi-page report more interactive and user-friendly.
