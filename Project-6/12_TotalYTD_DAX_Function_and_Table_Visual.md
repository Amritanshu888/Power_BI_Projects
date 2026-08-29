# Power BI – Total YTD Sales Using `TOTALYTD()` + Table Visual

## 1. Session Overview

In this session, a new visual is added to the **second report page (Sales Performance)**.

The objective is to:

* Create a DAX measure for **Total YTD Sales**.
* Use the **`TOTALYTD()`** DAX function.
* Display the cumulative Year-to-Date sales in a **Table visual**.
* Also display the daily **Purchase Price** alongside the YTD sales.
* Format the table to match the existing report design.
* Make some additional formatting changes to the **Sales by Region** bar chart.

---

# 2. Business Requirement – Total YTD Sales

The requirement is to calculate:

> **Total Year-to-Date (YTD) Sales**

YTD means the cumulative sales starting from the **beginning of the current year up to the current date**.

For example, if the data contains:

| Date  | Sales |
| ----- | ----: |
| Jan 1 |   100 |
| Jan 2 |   150 |
| Jan 3 |   200 |

Then YTD sales would be:

| Date  | YTD Sales |
| ----- | --------: |
| Jan 1 |       100 |
| Jan 2 |       250 |
| Jan 3 |       450 |

So unlike normal sales, YTD sales are **cumulative**.

---

# 3. Creating the Total YTD Sales Measure

Since a dedicated Measures table was created earlier, the new measure is created there.

### Steps

1. Right-click on the **Measures table**.
2. Select:

> **New Measure**

3. Expand the formula bar if necessary.
4. Name the measure:

```text id="j2f8w4"
Total YTD Sales
```

---

# 4. DAX Function Used – `TOTALYTD()`

The lecture uses the DAX:

> **`TOTALYTD()`**

This function calculates the year-to-date value of an expression.

### Basic syntax

```DAX id="8j7v2m"
TOTALYTD(
    <expression>,
    <dates>
)
```

In this example, the expression is the sum of Purchase Price, and the date column comes from the Housing table.

---

# 5. DAX Measure

The measure created in the lecture is:

```DAX id="w5s9ka"
Total YTD Sales =
TOTALYTD(
    SUM(Housing[Purchase Price]),
    Housing[Date]
)
```

### Breakdown

### `SUM(Housing[Purchase Price])`

Calculates the sales/purchase amount.

```DAX id="e1c4r7"
SUM(Housing[Purchase Price])
```

### `Housing[Date]`

Provides the dates over which the YTD calculation is performed.

```DAX id="a8n2x5"
Housing[Date]
```

### Complete logic

```text id="p6k4t1"
Purchase Price
      ↓
SUM()
      ↓
TOTALYTD()
      ↓
Cumulative sales for the year
```

After entering the formula:

1. Press **Enter**.
2. The **Total YTD Sales** measure is created.
3. Collapse the formula bar if desired.

---

# 6. Understanding What `TOTALYTD()` Does

`TOTALYTD()` calculates a cumulative value from the start of the year through the current date in the filter context.

For example:

```text id="2b7r8n"
January sales
       ↓
January cumulative sales

February sales
       ↓
January + February

March sales
       ↓
January + February + March

...
```

Therefore, when dates are placed into a visual, the YTD value progressively increases throughout the year.

---

# 7. Creating the Table Visual

The instructor wants to display the YTD sales using a **Table visual**.

### Steps

1. Click on a **blank area of the canvas**.
2. Select the:

> **Table visual**

3. A blank table is created.
4. Resize the table.
5. Position it toward the **top area of the report page**.

---

# 8. Adding Date to the Table

The table should show the YTD value for different dates.

### Steps

1. Locate the **Date** column under the Housing table.
2. Double-click it or drag it into the table.
3. Place it in the:

> **Columns** bucket.

The table now contains the dates.

---

# 9. Adding Total YTD Sales

Next, add the measure created earlier.

### Steps

1. Locate:

> **Total YTD Sales**

under the **Measures table**.

2. Double-click it or drag it into the table.
3. Add it to the **Columns** bucket.

The table now displays the cumulative YTD sales against the dates.

---

# 10. Result – Cumulative Sales

After adding the measure, the instructor observes that:

> **Cumulative sales are being displayed.**

Conceptually, the table will look like:

| Date   | Total YTD Sales |
| ------ | --------------: |
| Date 1 |             100 |
| Date 2 |             250 |
| Date 3 |             450 |
| Date 4 |             700 |

The exact values depend on the dataset.

The important point is:

> The YTD value accumulates as the date progresses.

---

# 11. Adding Total Purchase Price

The instructor also wants to show the normal Purchase Price alongside the YTD value.

### Steps

1. Select the existing table visual.
2. Locate:

> **Purchase Price**

under the Housing table.

3. Double-click **Purchase Price**.
4. Drag it into the table's **Columns** bucket.

The table now shows both:

* Total Purchase Price for the given date/context
* Total YTD Sales

Conceptually:

| Date  | Purchase Price | Total YTD Sales |
| ----- | -------------: | --------------: |
| Jan 1 |            100 |             100 |
| Jan 2 |            150 |             250 |
| Jan 3 |            200 |             450 |

This makes it possible to compare:

> **Individual/current sales value vs cumulative YTD sales.**

---

# 12. Formatting the Table Visual

The instructor now formats the table so that it matches the report's visual theme.

### Steps

1. Select the table.
2. Click:

> **Format Visual**

---

# 13. Changing the Table Style

Under:

> **Styles Presets**

the instructor changes the default style.

### Setting

Change the default style to:

> **None**

This removes the predefined styling.

---

# 14. Removing Totals

The instructor does not want a totals row displayed at the bottom of the table.

### Steps

1. In the formatting options, locate:

> **Totals**

2. Change:

> **Totals → Off**

The total row disappears.

This keeps the table focused on the date-level values.

---

# 15. Formatting Values

The instructor then changes the appearance of the values.

Under the relevant **Values** settings:

* Change text color from black to **gray**.
* Adjust the appearance as required.

The same approach can be used for alternate text colors.

---

# 16. Formatting Alternate Text Color

The instructor also changes:

> **Alternate text color**

to gray.

This helps maintain consistency with the report's overall color scheme.

---

# 17. Formatting Background Color

The table background is also customized.

The instructor chooses a background color similar to the colors already being used elsewhere in the report.

The important point is:

> Use a background color that matches the overall report theme.

The exact color is optional.

---

# 18. Formatting Column Headers

The column headers are formatted separately.

### Steps

1. Open:

> **Column headers**

2. Choose an appropriate font.
3. Make the text:

> **Bold**

4. Set the text color to a **dark gray** shade.

This improves the readability and hierarchy of the table.

---

# 19. Additional Formatting – Sales by Region Chart

The instructor then returns to the previously created:

> **Sales by Region**

bar chart.

Additional formatting is applied to the chart.

---

# 20. Adding a Border to Sales by Region

### Steps

1. Select the **Sales by Region** bar chart.
2. Go to:

> **Format Visual**

3. Open the **Bars** section.
4. Enable/configure the border.

The border color is changed to:

> **Dark gray**

This provides a clearer boundary around the bars/visual.

---

# 21. Border Formatting for Ribbons

The instructor also checks the border settings for the ribbons.

The ribbons can be formatted by:

1. Selecting the bar chart.
2. Opening the ribbon settings.
3. Turning the ribbon border on if desired.
4. Selecting an appropriate border color.

However, after testing the option, the instructor decides that the ribbon border does **not look good**.

Therefore:

> **Ribbon border is changed back to Off.**

This is an important practical point:

**Not every available formatting option needs to be enabled.**

Visual formatting should be based on how the final report actually looks.

---

# 22. Adding a Border to the Table

The instructor finally adds a border around the newly created table.

### Steps

1. Select the **Table visual**.
2. Go to:

> **Format Visual**

3. Open:

> **General → Effects**

4. Locate:

> **Border**

5. Turn the border:

> **On**

This gives the table a defined boundary and makes it visually consistent with the other report elements.

---

# 23. Final Table Structure

The table created in this session conceptually contains:

```text id="q6h2n8"
┌────────────┬────────────────┬───────────────────┐
│    Date    │ Purchase Price │  Total YTD Sales  │
├────────────┼────────────────┼───────────────────┤
│ Date 1     │      ...       │        ...        │
│ Date 2     │      ...       │        ...        │
│ Date 3     │      ...       │        ...        │
│ Date 4     │      ...       │        ...        │
└────────────┴────────────────┴───────────────────┘
```

The **Total YTD Sales** column represents cumulative sales through each date.

---

# 24. Important DAX Concept – `TOTALYTD()`

### Syntax

```DAX id="n4v6s1"
TOTALYTD(
    <expression>,
    <dates>
)
```

### In this project

```DAX id="r8w3p5"
Total YTD Sales =
TOTALYTD(
    SUM(Housing[Purchase Price]),
    Housing[Date]
)
```

### Interpretation

> Calculate the cumulative sum of Purchase Price from the beginning of the year through the current date.

---

# 25. `TOTALYTD()` vs Normal `SUM()`

This distinction is important.

### Normal SUM

```DAX id="7y1k3d"
Total Sales =
SUM(Housing[Purchase Price])
```

This gives the sales amount for the current filter context.

### TOTALYTD

```DAX id="6q9m2v"
Total YTD Sales =
TOTALYTD(
    SUM(Housing[Purchase Price]),
    Housing[Date]
)
```

This gives the **cumulative sales from the beginning of the year up to the current date**.

---

# 26. Complete Workflow

```text id="3p8w6c"
Measures Table
      ↓
Right-click
      ↓
New Measure
      ↓
Name → Total YTD Sales
      ↓
TOTALYTD()
      ↓
SUM(Housing[Purchase Price])
      ↓
Housing[Date]
      ↓
Press Enter
      ↓
Create Table Visual
      ↓
Add Date
      ↓
Add Total YTD Sales
      ↓
Observe cumulative sales
      ↓
Add Purchase Price
      ↓
Format Visual
      ↓
Styles Presets → None
      ↓
Totals → Off
      ↓
Format Values
      ↓
Text → Gray
      ↓
Alternate Text → Gray
      ↓
Set Background
      ↓
Format Column Headers
      ↓
Bold + Dark Gray
      ↓
Format Sales by Region chart
      ↓
Bars → Border → Dark Gray
      ↓
Ribbon border → Test
      ↓
Not visually suitable → Turn Off
      ↓
Table → General → Effects
      ↓
Border → On
```

---

# 27. Quick Revision Table

| Requirement            | Power BI Action                |
| ---------------------- | ------------------------------ |
| Create YTD measure     | Measures table → New Measure   |
| Measure name           | Total YTD Sales                |
| DAX function           | `TOTALYTD()`                   |
| Expression             | `SUM(Housing[Purchase Price])` |
| Date argument          | `Housing[Date]`                |
| Visual                 | Table                          |
| Date field             | Columns bucket                 |
| YTD measure            | Columns bucket                 |
| Additional field       | Purchase Price                 |
| Table style            | None                           |
| Totals                 | Off                            |
| Value text             | Gray                           |
| Alternate text         | Gray                           |
| Background             | Customized                     |
| Column headers         | Bold + dark gray               |
| Sales by Region border | On                             |
| Border color           | Dark gray                      |
| Ribbon border          | Ultimately Off                 |
| Table border           | On                             |

---

# 28. Key Takeaways

1. **`TOTALYTD()`** is used to calculate cumulative Year-to-Date values.
2. The expression used here is:

   ```DAX
   SUM(Housing[Purchase Price])
   ```
3. The date column used is:

   ```DAX
   Housing[Date]
   ```
4. The resulting **Total YTD Sales** measure is stored in the dedicated **Measures table**.
5. A **Table visual** is used to display the YTD sales against dates.
6. **Purchase Price** is also added to provide the non-cumulative value alongside the YTD value.
7. Turning **Totals Off** removes the unwanted totals row.
8. Table styling can be customized through **Styles Presets, Values, Column Headers, and Effects**.
9. Borders can be added through:

   > **Format Visual → General → Effects → Border**
10. Formatting options should be enabled based on the **actual appearance of the report**—for example, the ribbon border was tested but ultimately turned off because it did not look visually appropriate.
11. The session continues building the **Sales Performance** page, with additional visuals to be added in subsequent sessions.
