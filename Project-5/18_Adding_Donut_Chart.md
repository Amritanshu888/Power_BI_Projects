# Detailed Notes: Adding a Donut Chart for High Credit Score Loan Amount

## 1. Objective of the Session

The goal of this session is to add a **donut chart** to the second report page in Power BI.

The donut chart will be used to represent:

* The **average loan amount** for customers belonging to the **High Credit Score** category.
* The information broken down by:

  * **Age Group**
  * **Marital Status**

The session covers:

1. Creating a DAX measure for average loan amount for the high credit-score category.
2. Adding and configuring a donut chart.
3. Using age groups as the chart's legend.
4. Using marital status as the chart's detail/category.
5. Formatting donut-chart colors.
6. Adding and formatting a border.
7. Formatting the chart title.
8. Showing detailed data labels.
9. Formatting data-label fonts.

---

# 2. Create the DAX Measure

Since the visual is being created on the **second report page**, the measure is created inside **Measures Table 2**.

### Step 1: Open Measures Table 2

In the **Data pane** on the right:

1. Locate **Measures Table 2**.
2. Right-click on **Measures Table 2**.
3. Select **New Measure**.

Power BI may take a moment to display the formula bar.

---

## 3. Name the Measure

Expand the formula bar and give the measure the following name:

**Average Loan Amount High Credit**

The purpose of this measure is to calculate the **average loan amount only for customers whose Credit Score Bin is "High"**.

---

# 4. DAX Formula

The measure uses the **AVERAGEX** and **FILTER** functions.

The structure used in the lecture is:

```DAX
Average Loan Amount High Credit =
AVERAGEX(
    FILTER(
        'Default Loan Default',
        'Default Loan Default'[Credit Score Bins] = "High"
    ),
    'Default Loan Default'[Loan Amount]
)
```

> The exact table name should match the table name in your Power BI model. In the lecture, IntelliSense is used to select the appropriate table and columns.

### How the formula works

### `AVERAGEX()`

`AVERAGEX` calculates an average by evaluating an expression over a table.

Here, the expression being averaged is:

**Loan Amount**

---

### `FILTER()`

The `FILTER` function is used to restrict the rows that are considered.

The filter condition is:

```DAX
[Credit Score Bins] = "High"
```

Therefore, only rows where the **Credit Score Bins** column contains **High** are considered.

---

### Overall logic

The measure essentially means:

> Calculate the average Loan Amount for records where Credit Score Bins is equal to High.

After entering the formula:

1. Press **Enter**.
2. The measure is created under **Measures Table 2**.

---

# 5. Add the Donut Chart

After creating the measure:

1. Click on a **blank area of the report canvas**.
2. Select the **Donut Chart** visual from the Visualizations pane.
3. A blank donut chart is added to the canvas.

### Position and sizing

The lecture then adjusts the layout:

* Move the donut chart toward the **top of the report page**.
* Increase its size slightly.
* The existing line chart is also resized to make better use of the available space.

---

# 6. Add the Average Loan Amount to the Donut Chart

The newly created measure:

**Average Loan Amount High Credit**

needs to be used as the numerical value for the donut chart.

### Steps

1. Select the donut chart.
2. Locate the newly created **Average Loan Amount High Credit** measure.
3. Drag it into the **Values** bucket.

This tells Power BI what numerical quantity the donut chart should represent.

---

# 7. Add Marital Status

The requirement is to show insights for different **marital status** categories.

### Steps

1. Locate **Marital Status** in the Data pane.
2. Drag **Marital Status** into the **Details** bucket of the donut chart.

This allows the chart to represent the information for different marital-status categories.

---

# 8. Add Age Groups

The lecture also wants the results to be broken down by different **age-group categories**.

### Steps

1. Locate the previously created **Age Groups** column in the Data pane.
2. Drag **Age Groups** into the **Legend** bucket.

Now the donut chart is broken down using age groups.

### Result

The visual represents the:

> **Average loan amount for the High Credit Score category across different age groups and marital-status categories.**

The age groups are represented through the **legend**, while marital status is represented through the **details**.

---

# 9. Change the Donut Chart Colors

The next step is to customize the colors used for the different age-group categories.

### Steps

1. Select the donut chart.
2. Click **Format Your Visual**.
3. Locate the formatting options for the visual's category/legend colors.
4. Change the colors according to preference.

The lecture uses the following color codes:

| Age Group         | Color Code |
| ----------------- | ---------- |
| Young Adults      | `#EB5B9F`  |
| Middle Age Adults | `#C7B8E7`  |
| Senior Citizens   | `#F3B4DC`  |
| Teens             | `#B82749`  |

The exact age-group names depend on how the **Age Groups** column was created in the report.

### Important

When changing a color manually:

1. Select the category.
2. Open its color selector.
3. Enter the required hexadecimal color code.
4. Apply it.

This provides consistent color coding across the donut chart.

---

# 10. Add a Border to the Donut Chart

A border is added to make the visual stand out from the rest of the report.

### Steps

With the donut chart selected:

1. Open **Format Your Visual**.
2. Go to **General**.
3. Expand **Effects**.
4. Turn **Visual Border** **On**.
5. Expand the border settings.
6. Click the **border color** option.

The lecture chooses the same **magenta color** that was previously used for the shape at the top of the report.

This keeps the report's visual design consistent.

---

# 11. Change the Donut Chart Title

The default title is changed to clearly explain what the visual represents.

### Steps

1. Keep the donut chart selected.
2. Expand the **Title** formatting section.
3. Change the title to:

> **Average Loan Amount High Credit by Age Group and Marital Status**

This title clearly communicates:

* The metric → Average Loan Amount
* The credit category → High Credit
* First breakdown → Age Group
* Second breakdown → Marital Status

---

# 12. Format the Chart Title

After changing the title text, the title is formatted.

### Font

Choose a suitable font style according to the report design.

### Font color

The lecture uses a **gray color**, specifically the previously used:

> **White, 60% darker**

### Horizontal alignment

Scroll down in the title settings and change:

**Horizontal alignment → Center**

This centers the title above the donut chart.

---

# 13. Display Detailed Labels

The donut chart can display additional information directly on the chart.

### Steps

1. In the formatting pane, locate the **Visuals** section.
2. Find **Detail Labels**.
3. Expand **Detail Labels**.
4. Look at **Label contents**.

Initially, the chart displays:

* Data value
* Percentage of total

The lecture changes this so that **all available detail labels** are displayed.

### Select:

**All detail labels**

This provides more information directly on the donut chart.

The labels can now show details such as:

* Marital-status category
* Corresponding value
* Percentage/details associated with the category

This makes the chart more informative without requiring the user to hover over every section.

---

# 14. Format the Data Labels

The appearance of the labels can also be customized.

### Steps

1. Under the **Detail Labels/Data Labels** formatting options, locate **Values**.
2. Expand the values/data-label formatting section.
3. Change the **Font Style**.
4. Choose the desired font.
5. Adjust the font size if required.
6. Make the font **Bold**.
7. Change the font color.

The lecture uses the same gray tone:

> **White, 60% darker**

This keeps the data labels consistent with the title styling.

---

# 15. Final Layout Adjustments

After completing the formatting:

1. Collapse the **Data** and **Visualizations** panes if required.
2. Review the overall report layout.
3. Increase the donut chart size slightly.
4. Reduce the size of the existing line chart if necessary to make room.
5. Check that the visuals are properly positioned and aligned.

The goal is to achieve a balanced layout where both the donut chart and the existing line chart fit comfortably on the page.

---

# 16. Final Donut Chart Configuration

The final configuration can be summarized as follows:

| Donut Chart Component           | Field/Setting                                                                            |
| ------------------------------- | ---------------------------------------------------------------------------------------- |
| **Visual**                      | Donut Chart                                                                              |
| **Values**                      | `Average Loan Amount High Credit`                                                        |
| **Details**                     | `Marital Status`                                                                         |
| **Legend**                      | `Age Groups`                                                                             |
| **Filter condition in measure** | `Credit Score Bins = "High"`                                                             |
| **Title**                       | Average Loan Amount High Credit by Age Group and Marital Status                          |
| **Title alignment**             | Center                                                                                   |
| **Visual Border**               | On                                                                                       |
| **Detail Labels**               | All detail labels                                                                        |
| **Data Labels**                 | Formatted/bold                                                                           |
| **Purpose**                     | Show average loan amount for High Credit Score customers by age group and marital status |

---

# 17. Key DAX Concept Learned

The major DAX concept introduced in this session is combining **`AVERAGEX` with `FILTER`**.

The general pattern is:

```DAX
AVERAGEX(
    FILTER(
        Table,
        Condition
    ),
    Expression
)
```

In this case:

```text
Table
   ↓
Default Loan table

Filter condition
   ↓
Credit Score Bins = "High"

Expression
   ↓
Loan Amount

Result
   ↓
Average Loan Amount for High Credit customers
```

This is useful whenever you need to calculate an aggregation only for records satisfying a particular condition.

---

# 18. Overall Workflow

The complete process followed in the lecture is:

**Measures Table 2**
↓
**New Measure**
↓
Create **Average Loan Amount High Credit**
↓
Use `AVERAGEX`
↓
Use `FILTER` to keep `Credit Score Bins = "High"`
↓
Average the **Loan Amount**
↓
Add a **Donut Chart**
↓
Put measure in **Values**
↓
Put **Marital Status** in **Details**
↓
Put **Age Groups** in **Legend**
↓
Customize category colors
↓
Turn **Visual Border** on
↓
Customize border color
↓
Change and center the title
↓
Enable **All detail labels**
↓
Format data-label font/style/color
↓
Resize and reposition visuals
↓
**Final donut chart showing average loan amount for High Credit customers by age group and marital status**
