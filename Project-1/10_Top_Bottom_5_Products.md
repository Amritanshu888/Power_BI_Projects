# Power BI — Top & Bottom 5 Products by Sales, Quantity, and Profit

## 1. Objective of the Session

This session marks the beginning of the **reporting/visualization phase**.

The first requirement is:

> **Show the Top 5 and Bottom 5 Products based on Sales, Profit, and Quantity Sold.**

This will require:

* Creating a **Profit** column.
* Using the **Product Dimension** table for product names.
* Using numerical columns from the **Fact Table**:

  * Net Sales
  * Profit
  * Unit Sold / Quantity
* Creating **six bar-chart visuals**:

  1. Top 5 Products by Sales
  2. Bottom 5 Products by Sales
  3. Top 5 Products by Quantity
  4. Bottom 5 Products by Quantity
  5. Top 5 Products by Profit
  6. Bottom 5 Products by Profit
* Applying **visual-level Top N/Bottom N filters**.
* Formatting the visuals for readability.

---

# 2. Initial Report Cleanup

Previously, Page 2 and Page 3 were only used to understand filters. They are no longer required.

### Remove Page 2 and Page 3

1. Go to the report pages at the bottom of Power BI Desktop.
2. Right-click/delete **Page 2**.
3. Delete **Page 3**.
4. Keep only the required report page.

### Remove Existing Visuals

1. Select the two visuals that were created for the previous filtering demonstration.
2. Press **Delete**.
3. The canvas is now ready for the actual report.

### Remove Customer ID Filter

The previously used **Customer ID filter** is also no longer required.

Remove it from the report pages.

---

# 3. Understanding the Data Model

Before creating the visuals, identify where the required fields are located.

There are two important tables:

### Fact Table

The Fact Table contains numerical/business transaction information such as:

* Discount
* Discount Percentage
* Net Sales
* Price Per Unit
* Total Sales
* Unit Sold

However, there is **no Profit column** currently available.

Therefore, a Profit column must be created.

### Product Dimension Table

The Product Dimension table contains product-related information, particularly:

* Product ID
* Product Name

The **Product Name** will be used in the visuals.

---

# 4. Relationship Between the Tables

Go to **Model View**.

You can see that:

**Product Dimension → Fact Table**

are connected through:

**Product ID**

The relationship works conceptually as:

```text
Product Dimension Table
        |
        | Product ID
        |
        ↓
Fact Table
```

### Keys

* `Product ID` in the **Product Dimension table** = **Primary Key**
* `Product ID` in the **Fact Table** = **Foreign Key**

This relationship allows us to use:

> Product Name from the Product Dimension

together with:

> Sales / Profit / Quantity from the Fact Table.

### How to inspect the relationship

1. Go to **Model View**.
2. Hover over the relationship line between the two tables.
3. Power BI displays information about the relationship and the columns involved.

---

# 5. Creating the Profit Column

The requirement needs Profit, but the Fact Table doesn't contain a Profit column.

The assumption given in the requirement is:

> **Profit = 10% of Net Sales**

Therefore:

[
Profit = Net Sales \times 10%
]

or:

[
Profit = Net Sales \times 0.1
]

---

## Steps to Create Profit in Power Query

### Step 1 — Open Power Query Editor

1. Go to **Report View**.
2. Open **Power Query Editor**.

### Step 2 — Select Fact Table

1. In Power Query Editor, select the **Fact Table**.
2. Go to the **Add Column** tab.
3. Select **Custom Column**.

### Step 3 — Create the Formula

Give the new column the name:

```text
Profit
```

The formula is:

```text
Net Sales × 0.1
```

In Power Query, select **Net Sales** from Available Columns and insert it into the formula.

Conceptually:

```text
Profit = [Net Sales] * 0.1
```

Power Query should show:

> No syntax errors have been detected.

Click **OK**.

---

# 6. Change Profit Data Type

After creating the Profit column:

1. Select the **Profit** column.
2. Change its **Data Type**.
3. Select **Decimal Number**.

This is important because the calculated profit values can contain decimal values.

---

# 7. Apply Power Query Changes

Once the column has been created:

1. Go to the **Home** tab.
2. Click the dropdown associated with applying changes.
3. Select **Close & Apply**.

Power BI will:

1. Apply the Power Query changes.
2. Load the updated data into the model.
3. Return you to the report view.

Depending on the data/model size, this may take some time.

---

# 8. Requirement 1 — Top 5 Products by Sales

We now start creating the actual report visuals.

## Step 1 — Create a Bar Chart

1. Click on a blank area of the report canvas.
2. Select **Stacked Bar Chart**.

A blank bar chart appears.

### Why a Bar Chart?

Products can have relatively long names.

A horizontal bar chart makes long product names easier to read because:

* Product names are displayed vertically along the Y-axis.
* Numerical values are displayed horizontally along the X-axis.

When choosing a visualization, always prioritize:

> **Readability and clarity of the insight.**

The visual should make it easy for the report user to understand the information.

---

# 9. Add Product Name to the Chart

Products need to be represented along the vertical axis.

From the **Data pane**:

1. Locate **Product Name** from the Product Dimension table.
2. Drag it to the **Y-axis** bucket.

Alternatively, the lecture demonstrates double-clicking the field and then moving it to the appropriate bucket.

---

# 10. Add Net Sales

From the Data pane:

1. Locate **Net Sales**.
2. Drag it to the **X-axis** bucket.

The chart now displays:

> Net Sales for all products.

However, we only want the **Top 5 Products**.

---

# 11. Apply Top 5 Filter

This is a **visual-level filter**.

### Steps

1. Select the bar chart.
2. Open the **Filters pane**.
3. Locate **Product Name** under the filter section for the visual.
4. Change the filtering type from:

   * **Basic Filtering**
     to
   * **Top N**
5. Enter:

```text
5
```

This means we want the Top 5.

But Power BI also needs to know:

> Top 5 based on what?

### Set the "By Value"

1. Locate **Net Sales** in the Data pane.
2. Drag **Net Sales** into the **By value / Values** section of the Top N filter.
3. Power BI uses **Sum of Net Sales**.
4. Click **Apply Filter**.

Now the visual displays only:

> **Top 5 Products based on Net Sales**

---

# 12. Format the Top 5 Sales Visual

Now make the visual easier to read.

## Remove Y-Axis Title

The product names should remain visible, but the generic category/title on the Y-axis isn't necessary.

Steps:

1. Select the visual.
2. Open **Format Visual**.
3. Expand **Y-axis**.
4. Turn **Title** → **Off**.

### Maximum Width

The **Maximum width** setting can be increased when product names are long and aren't being displayed properly.

For example, the lecture demonstrates changing the width to approximately:

```text
50%
```

This provides additional space for product names.

---

# 13. Remove X-Axis Values and Title

The lecture chooses not to display the X-axis values directly.

Steps:

1. Expand **X-axis**.
2. Set **Values** → **Off**.
3. Set **Title** → **Off**.

But if the X-axis values are removed, we still need to show the actual sales values.

Therefore, use **Data Labels**.

---

# 14. Turn On Data Labels

1. Open the formatting options.
2. Find **Data Labels**.
3. Set them to **On**.

Now the numerical values appear directly next to the bars.

This provides the sales values without requiring the X-axis values.

---

# 15. Change the Chart Title

Go to:

**Format Visual → General → Title**

Change the title to:

> **Top 5 Products by Sales**

You can use another meaningful title if required.

### Title Formatting

The lecture demonstrates formatting the title by changing:

* Font
* Font size
* Bold
* Italic
* Underline
* Horizontal alignment
* Indentation

The horizontal alignment is changed to:

> **Center**

The lecture uses **Times New Roman** as an example font.

---

# 16. Change Bar Color

To change the bar color:

1. Select the visual.
2. Go to **Format Visual**.
3. Open the **Bars** section.
4. Change the color.

The lecture uses a **purple** color for the Top 5 Sales chart.

---

# 17. Format Product Names

The product names appear on the Y-axis.

Under:

**Format Visual → Y-axis**

you can change:

* Font
* Color
* Font size
* Bold/other formatting

The lecture uses:

* **Times New Roman**
* Black color
* Bold
* Increased font size

---

# 18. Format Data Labels

Under **Data Labels → Values**, you can format the numerical values.

You can change:

* Color
* Font
* Font size

The lecture uses:

* Black
* Times New Roman
* Increased font size

The visual can also be resized to improve readability.

---

# 19. Add a Border

To add a border around the visual:

1. Select the visual.
2. Go to **Format Visual**.
3. Go to **General**.
4. Expand **Effects**.
5. Turn **Visual Border** → **On**.
6. Select a border color.

The lecture uses:

> **Gray**

---

# 20. Bottom 5 Products by Sales

Instead of creating the entire visual from scratch, duplicate the Top 5 Sales chart.

### Duplicate

1. Select the Top 5 Sales chart.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the duplicated chart to the right side of the canvas.

---

## Change Top N to Bottom N

With the duplicated visual selected:

1. Open the **Filters pane**.
2. Locate the Product Name filter.
3. Change:

```text
Top 5
```

to:

```text
Bottom 5
```

4. Click **Apply Filter**.

The visual now displays the bottom five products according to Net Sales.

---

## Change the Title

Go to:

**Format Visual → General → Title**

Change:

> Top 5 Products by Sales

to:

> **Bottom 5 Products by Sales**

---

## Change the Bar Color

Go to:

**Format Visual → Bars → Color**

Choose a different color.

The lecture uses a **pink** color as an example.

---

# 21. Top 5 Products by Quantity

Now create another visual for quantity sold.

The quantity field in the Fact Table is:

> **Unit Sold**

### Duplicate Existing Chart

1. Select the Top 5 Sales chart.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the duplicated chart to the desired position.

---

## Remove the Existing Sales Filter

Open the Filters pane and remove the existing Net Sales-related filter from this new visual.

---

## Replace Net Sales with Unit Sold

1. Select the new chart.
2. Remove **Net Sales** from the X-axis.
3. From the Data pane, locate **Unit Sold**.
4. Drag **Unit Sold** into the **X-axis**.

The chart now represents quantity sold.

---

# 22. Apply Top 5 Filter by Quantity

We need the **Top 5 Products according to Unit Sold**.

### Steps

1. Add/select **Product Name** in the visual-level filter.
2. Change **Basic Filtering** → **Top N**.
3. Enter:

```text
5
```

4. Drag **Unit Sold** into the **By Value** section.
5. Click **Apply Filter**.

The visual now shows:

> **Top 5 Products by Quantity**

---

## Rename the Chart

Go to:

**Format Visual → General → Title**

Set the title to:

> **Top 5 Products by Quantity**

---

# 23. Bottom 5 Products by Quantity

Again, duplicate the Top 5 Quantity chart.

### Steps

1. Select Top 5 Products by Quantity.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the new chart to the desired location.
4. Open the Filters pane.
5. Change:

```text
Top 5
```

to:

```text
Bottom 5
```

6. Click **Apply Filter**.

---

## Change Color Using Format Painter

The lecture demonstrates using **Format Painter**.

1. Select the existing Bottom 5 Sales chart whose formatting/color you want to reuse.
2. Click **Format Painter**.
3. Click the newly created Bottom 5 Quantity chart.

The formatting/color is copied to the new visual.

---

## Change the Title

Go to:

**Format Visual → General → Title**

Change:

> Top 5 Products by Quantity

to:

> **Bottom 5 Products by Quantity**

---

# 24. Top 5 Products by Profit

Now create the Top 5 Products based on Profit.

### Duplicate the Quantity Chart

1. Select the **Top 5 Products by Quantity** chart.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the duplicated chart into position.

---

## Remove Existing Quantity Filter

Open the Filters pane and remove the existing Unit Sold filter.

---

## Replace Unit Sold with Profit

1. Remove **Unit Sold** from the X-axis.
2. Locate **Profit** in the Data pane.
3. Drag **Profit** to the **X-axis**.

---

## Apply Top 5 Profit Filter

1. Select/add **Product Name** in the visual-level filter.
2. Change **Basic Filtering** → **Top N**.
3. Enter:

```text
5
```

4. Drag **Profit** into the **By Value** section.
5. Click **Apply Filter**.

The visual now shows:

> **Top 5 Products by Profit**

---

## Change Title

Go to:

**Format Visual → General → Title**

Change the title to:

> **Top 5 Products by Profit**

---

# 25. Bottom 5 Products by Profit

Again, duplicate the Top 5 Profit chart.

### Steps

1. Select the Top 5 Profit chart.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the duplicated chart into position.
4. Open the Filters pane.
5. Change:

```text
Top 5
```

to:

```text
Bottom 5
```

6. Click **Apply Filter**.

The visual now shows the bottom five products according to Profit.

---

## Change Title

Go to:

**Format Visual → General → Title**

Change it to:

> **Bottom 5 Products by Profit**

---

## Change Bar Color

Go to:

**Format Visual → Bars → Colors**

Select a suitable color.

---

# 26. Final Six Visuals

At the end of the exercise, the report page contains six bar-chart visuals:

| Metric       | Top 5                      | Bottom 5                      |
| ------------ | -------------------------- | ----------------------------- |
| **Sales**    | Top 5 Products by Sales    | Bottom 5 Products by Sales    |
| **Quantity** | Top 5 Products by Quantity | Bottom 5 Products by Quantity |
| **Profit**   | Top 5 Products by Profit   | Bottom 5 Products by Profit   |

---

# 27. Important Concept — Visual-Level Top N/Bottom N Filtering

One of the most important concepts demonstrated in this lecture is the use of **visual-level filters**.

The Top/Bottom filtering is applied separately to each visual.

For example:

### Sales

```text
Product Name
     ↓
Top N
     ↓
5
     ↓
By Value = Net Sales
```

### Quantity

```text
Product Name
     ↓
Top N
     ↓
5
     ↓
By Value = Unit Sold
```

### Profit

```text
Product Name
     ↓
Top N
     ↓
5
     ↓
By Value = Profit
```

For Bottom 5, simply change **Top N → Bottom N**.

### Critical Step

After configuring the Top N/Bottom N filter, you must click:

> **Apply Filter**

Otherwise, the filter configuration will not become operational.

---

# 28. Important Concept — Why Use Product Name from Dimension Table?

The **Product Name** comes from the **Product Dimension table**, while numerical measures such as:

* Net Sales
* Unit Sold
* Profit

come from the **Fact Table**.

This is possible because the two tables are related through:

> **Product ID**

This is a common Power BI dimensional modeling pattern:

```text
Product Dimension
-----------------
Product ID
Product Name
     |
     | Product ID relationship
     ↓
Fact Table
-----------------
Product ID
Net Sales
Unit Sold
Profit
```

---

# 29. Important Visualization Principle

The lecture emphasizes that choosing a visualization isn't merely about making a chart.

You should select the visual that communicates the insight **clearly and efficiently**.

For product names, a **bar chart** is preferable because product names can be long.

A horizontal bar chart provides more horizontal space for those names and makes the report easier for users to read.

### General principle

> **Choose the visualization based on the type of data and how easily the end user can understand the insight.**

---

# 30. Key Power BI Techniques Learned

### Data Preparation

* Open Power Query Editor.
* Create a Custom Column.
* Create calculated values using existing columns.
* Change column data types.
* Apply changes using **Close & Apply**.

### Data Modeling

* Understand Fact and Dimension tables.
* Identify primary and foreign keys.
* Understand relationships through Product ID.

### Visual Creation

* Create a Stacked Bar Chart.
* Add categorical fields to the Y-axis.
* Add numerical fields to the X-axis.

### Filtering

* Use visual-level filters.
* Change Basic Filtering to Top N.
* Configure Top 5.
* Configure Bottom 5.
* Specify the **By Value** field.
* Apply the filter.

### Formatting

* Turn axis titles on/off.
* Turn axis values on/off.
* Enable Data Labels.
* Format titles.
* Change fonts.
* Change font sizes.
* Change colors.
* Add borders.
* Resize visuals.
* Use Format Painter.

### Efficiency

Instead of creating every visual from scratch:

> **Create one well-formatted visual → duplicate it → change the required field/filter/title.**

This saves considerable time while keeping the report visually consistent.

---

# 31. Complete Workflow to Remember

The overall process from this lecture can be remembered as:

```text
Requirement
    ↓
Understand Tables
    ↓
Check Required Columns
    ↓
Create Missing Profit Column
    ↓
Apply Power Query Changes
    ↓
Create Bar Chart
    ↓
Product Name → Y-axis
    ↓
Metric → X-axis
    ↓
Product Name → Visual Filter
    ↓
Top N / Bottom N
    ↓
N = 5
    ↓
Metric → By Value
    ↓
Apply Filter
    ↓
Format Visual
    ↓
Duplicate for Other Requirements
    ↓
Change Metric / Filter / Title
```

---

# 32. Final Outcome

The **first reporting requirement has been successfully completed**:

> **Top and Bottom 5 Products by Sales, Quantity, and Profit**

The report now contains six visuals using **visual-level Top N/Bottom N filters**.

The next session will move on to the **remaining requirements**, including additional visuals and additional report pages.
