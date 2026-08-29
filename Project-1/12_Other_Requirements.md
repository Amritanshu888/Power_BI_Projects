# Power BI — Detailed Lecture Notes: Overview Page & Additional Requirements

This lecture continues the development of the **Overview** page in Power BI. It covers four additional requirements:

1. **Relationship between Sales and Profit**
2. **Average Discount by Promotion Category**
3. **Sales by City**
4. **Total Number of Orders**

The lecture also demonstrates important Power BI concepts such as **scatter plots, aggregation vs. “Don’t summarize,” Format Painter, data categories for geographical data, Power Query index columns, distinct count, and visual formatting**. 

---

# 1. Add a Border to the Existing Sales Trend Visual

At the beginning of the lecture, the previously created **Sales Trends by Period** visual on the Overview page is formatted further.

### Steps

1. Select the existing sales trend visual.
2. Click **Format a visual**.
3. Go to **General**.
4. Find the **Effects** section.
5. Turn **Visual border → On**.
6. Change the border color to **Gray**.

This gives the existing visual a clearly defined boundary. 

---

# 2. Requirements Covered in This Lecture

The requirements document is opened to determine the next visuals that need to be created.

The lecture states that requirements **1 and 2** were already completed.

This session covers:

* **Requirement 3**
* **Requirement 5**
* **Requirement 6**
* **Requirement 8**

So, four requirements are addressed in this lecture. 

---

# Requirement 3 — Relationship Between Sales and Profit

## 3.1 Objective

The third requirement is:

> Show the relationship between **Sales and Profit**.

Whenever we need to show the relationship between **two numerical quantities**, a **Scatter Plot / Scatter Chart** is preferred.

### Why a Scatter Plot?

A scatter plot represents two numerical variables using coordinates:

* One numerical variable → X-axis
* Another numerical variable → Y-axis

Each point represents an observation.

The lecture specifically uses a scatter plot for the Sales vs. Profit relationship. 

---

# 3.2 Create the Scatter Chart

### Steps

1. Go to the report canvas.
2. Click on a **blank area** of the canvas.
3. Select the **Scatter Chart** from the visualizations.
4. A blank scatter chart will be created.
5. Resize it as required.
6. Position it appropriately on the Overview page. 

---

# 3.3 Add Profit to the X-Axis

The relationship being analyzed is between **Profit** and **Net Sales**.

### Steps

1. Expand the **Fact table** in the Data pane.
2. Find the **Profit** field.
3. Drag and drop **Profit** into the **X-axis** bucket.

So:

**X-axis → Profit** 

---

# 3.4 Add Net Sales to the Y-Axis

### Steps

1. Find the **Net Sales** field in the Fact table.
2. Drag and drop **Net Sales** into the **Y-axis** bucket.

The configuration is now:

| Axis   | Field     |
| ------ | --------- |
| X-axis | Profit    |
| Y-axis | Net Sales |



---

# 3.5 Important Problem: Only One Point Appears

After adding Profit and Net Sales, only **one point** appears.

### Why?

Power BI is currently aggregating the fields:

* **Sum of Profit**
* **Sum of Net Sales**

Therefore, Power BI calculates one total Profit and one total Net Sales and plots only one coordinate.

For example conceptually:

**(Sum of Profit, Sum of Net Sales)**

That is not what is wanted.

The requirement is to have **individual coordinates/points** representing the individual observations.

The lecture explicitly explains that the values should not be summarized. 

---

# 3.6 Change Profit to "Don't Summarize"

### Steps

1. Go to the **Profit** field in the X-axis bucket.
2. Click its dropdown.
3. Change the aggregation from **Sum** to:

**Don't summarize**

---

# 3.7 Change Net Sales to "Don't Summarize"

Perform the same operation for Net Sales.

### Steps

1. Open the dropdown for **Net Sales**.
2. Change it from **Sum** to:

**Don't summarize**

Now the scatter plot contains individual points instead of one aggregated point. 

---

# 3.8 Interpretation of the Scatter Plot

The resulting scatter plot shows a **linear relationship** between Profit and Sales.

The reason is based on the assumption in the dataset that:

> Profit = approximately 10% of Net Sales.

Therefore, when sales increase, profit also increases proportionally.

This explains why the points follow a relatively linear pattern. 

---

# 3.9 Understanding Point Density

The scatter plot also shows that the points are not uniformly distributed.

There is a higher density of points around:

* **Profit ≈ 10K**
* **Net Sales ≈ 100K**

So the region around:

**(10K, 100K)**

contains a comparatively high number of observations.

Other areas contain points as well, but their density is lower.

This gives another useful insight from the scatter plot: **where most of the observations are concentrated**. 

---

# 4. Formatting the Scatter Plot

After creating the scatter plot, the visual is formatted.

---

## 4.1 Add a Border

### Steps

1. Select the scatter plot.
2. Click **Format a visual**.
3. Go to **General**.
4. Open **Effects**.
5. Turn **Visual border → On**.
6. Set the border color to **Gray**.



---

# 4.2 Keep X-Axis and Y-Axis Values and Titles

Unlike the earlier sales trend chart, the scatter plot should retain the axis information.

The lecture specifically says that the **values and titles along both vertical and horizontal axes should not be removed**.

This is important because the axes provide the numerical context needed to interpret each scatter point. 

---

# 4.3 Change the Scatter Plot Title

The default title can be replaced with:

**Profit versus Net Sales**

### Steps

1. Select the scatter plot.
2. Go to **Format a visual**.
3. Open **General**.
4. Expand **Title**.
5. Change the title to:

**Profit versus Net Sales**



---

# 4.4 Format the Title

The lecture applies the following formatting:

* **Font:** Times New Roman
* **Bold:** On
* **Font size:** 14
* **Italic:** On
* **Underline:** On
* **Horizontal alignment:** Center

### Steps

Under the Title formatting options:

1. Change font to **Times New Roman**.
2. Enable **Bold**.
3. Set size to **14**.
4. Enable **Italic**.
5. Enable **Underline**.
6. Set horizontal alignment to **Center**. 

---

# 4.5 Remove Gridlines

The lecture removes gridlines from the scatter chart.

### Steps

1. Select the scatter plot.
2. Go to the **Visual** formatting section.
3. Find **Grid lines**.
4. Turn **Horizontal grid lines → Off**.
5. Turn **Vertical grid lines → Off**.

This produces a cleaner visual. 

---

# 4.6 Change Marker Color

The individual points/markers can also be formatted.

### Steps

1. Go to the **Visual** formatting section.
2. Expand **Markers**.
3. Locate the color setting.
4. Choose the desired color.

The lecture uses **pink** as an example. 

---

# 4.7 Format the X-Axis Values

The X-axis represents **Profit**.

### Steps

1. Expand the **X-axis** section.
2. Under **Values**, change the font to **Times New Roman**.
3. Change the color to **Black**.



---

# 4.8 Format the X-Axis Title

The X-axis title can also be formatted.

### Steps

1. Under **X-axis**, expand **Title**.
2. Change the font to **Times New Roman**.
3. Keep the color black.
4. Increase the size if required.
5. The lecture uses **14** as an example.



---

# 4.9 Format the Y-Axis Values

The Y-axis represents **Net Sales**.

### Steps

1. Collapse the X-axis settings.
2. Expand **Y-axis**.
3. Under **Values**:

   * Font → Times New Roman
   * Bold → On
   * Color → Black



---

# 4.10 Format the Y-Axis Title

### Steps

Under the Y-axis **Title** settings:

* Font → Times New Roman
* Bold → On
* Increase the size as required



The X-axis values and title can similarly be made bold. 

---

# 4.11 Resize the Scatter Plot

Finally, resize the scatter plot so that it fits properly within the Overview page.

The final scatter plot provides the required relationship between the two numerical quantities:

**Profit ↔ Net Sales**

The key rule from this requirement is:

> **When you need to show the relationship between two numerical quantities, use a Scatter Plot.** 

---

# Requirement 5 — Average Discount by Promotion Category

## 5.1 Objective

The fifth requirement is:

> Represent the **average discount offered in each discount category**.

A **Stacked Bar Chart** is used for this requirement. 

---

# 5.2 Create the Bar Chart

### Steps

1. Click on a blank area of the Overview page.
2. Select **Stacked Bar Chart**.
3. A blank bar chart appears.
4. Resize it appropriately. 

---

# 5.3 Add the Discount Rate

The discount value is available in the Fact table.

The lecture explains that the **Discount Rate** column was not originally present but had previously been created in **Power Query Editor** during the data transformation portion of the course. 

### Steps

1. Locate the **Discount Rate** field in the Data pane.
2. Drag it into the appropriate value bucket of the bar chart.

Initially, Power BI displays:

**Sum of Discount**

But the requirement asks for the **average discount**.

---

# 5.4 Change Sum to Average

### Steps

1. Open the dropdown for the Discount field.
2. Change the aggregation from:

**Sum**

to:

**Average**

Now the visual represents the average discount instead of the total discount. 

---

# 5.5 Add Promotion Category

The promotion information exists in the **Promotion Dimension** table.

### Steps

1. Expand the **Promotion Dimension** table.
2. Locate **Promotion Name**.
3. Drag **Promotion Name** into the **Y-axis**.

The chart now shows:

**Average Discount by Promotion Category**



---

# 6. Format the Average Discount Chart

The lecture first removes gridlines.

### Steps

1. Select the bar chart.
2. Open **Format a visual**.
3. Find **Grid lines**.
4. Turn the available vertical gridlines **Off**.



---

# 7. Use Format Painter

The lecture wants the newly created bar chart to have formatting consistent with the other charts on the Overview page.

Instead of manually formatting every property again, **Format Painter** is used.

### Steps

1. Go to the existing **Top Bottom Five Analysis** page.
2. Select a chart whose formatting you want to copy.
3. Click **Format Painter**.
4. Navigate to the **Overview** page.
5. Click the newly created average-discount bar chart.

The formatting of the source chart is copied to the new bar chart. 

### Key Concept

**Format Painter = Copy the formatting of one visual and apply it to another visual.**

This is useful for maintaining a consistent report design without manually repeating formatting steps.

---

# 8. Change the Bar Chart Title

The title is changed to:

**Average Discount by Promotion Categories**

### Steps

1. Select the bar chart.
2. Click **Format your visual**.
3. Go to **General → Title**.
4. Change the title accordingly.

The lecture specifically changes "promotion name" wording to **promotion categories**. 

---

# 9. Why Is There a Blank Promotion Category?

An important data-modeling issue is discussed here.

The chart contains a **Blank** category.

The reason is related to the relationship between the Fact table and the Promotion Dimension table.

---

## 9.1 Discount Is Not Available for Every Order

The Fact table contains discount information.

However:

* Discount was not given for every Order ID.
* For some orders, the discount value is **0**.
* The corresponding promotion category does not exist in the Promotion Dimension table.

Therefore, Power BI can show a **Blank** category.

The blank isn't an actual promotion category; it results from unmatched/missing dimension information associated with those fact records. 

---

# 10. Remove the Blank Category Using Filters

Since the Blank category is not meaningful for this visual, it is removed.

### Steps

1. Select the bar chart.
2. Expand the **Filters** pane.
3. Find **Promotion Name**.
4. Select **Select All**.
5. Uncheck **Blank**.
6. The blank category disappears from the visual.



---

# 11. Understanding the Blank Category Using Power Query

The instructor opens Power Query Editor to demonstrate why the blank appears.

### Steps

1. Click **Transform Data**.
2. Power Query Editor opens.
3. Select **Dim Promotion**.

The Promotion Dimension contains promotion IDs such as:

* PR001
* PR002
* PR003
* PR004
* PR005

These promotion IDs are also referenced by the Fact table. 

---

# 12. Promotion ID = 0

When the Promotion ID column in the Fact table is inspected, an additional value is found:

**0**

The Promotion Dimension does not contain this value.

The value `0` represents:

> **No discount was given under any promotion category.**

Therefore:

**Fact table → Promotion ID = 0**

has no corresponding valid promotion category in the Promotion Dimension.

Because of this unmatched value, Power BI represents those records as **Blank** when the promotion dimension is used in the visual.

This explains why the Blank category appeared in the bar chart. 

---

# 13. Return to Report View

After inspecting the data:

### Steps

1. Click **Close & Apply**.
2. Power BI applies the changes and returns to the Report view.



---

# Requirement 6 — Sales by Different Cities

## 14.1 Objective

The next requirement is:

> Show sales for different cities.

A **Map visual** is used.

A different chart could technically be used, but the lecture chooses a map because cities are geographical locations. 

---

# 14.2 Create the Map Visual

### Steps

1. Go to the Overview page.
2. Click on a blank area.
3. Select the **Map** visual.
4. A blank map is created.
5. Resize and position it appropriately. 

---

# 14.3 Configure the City Column as Geographical Data

This is an important step.

The customer city field initially has its **Data Category** set to:

**Uncategorized**

Power BI therefore needs to be explicitly told that this field contains geographical city information.

---

## Steps

1. Expand the **Customer Dimension** table.
2. Select the **Customer City** column.
3. Look at its **Data Category**.
4. It is initially **Uncategorized**.
5. Open the Data Category dropdown.
6. Select:

**City**

This tells Power BI that the column contains geographical city information. 

---

# 14.4 Add City to the Location Bucket

### Steps

1. Select the map visual.
2. Find **City** in the Customer Dimension.
3. Drag **City** into the **Location** bucket.

Power BI now plots the different cities as bubbles on the map.

Each bubble represents a geographical location. 

---

# 14.5 Add Net Sales to Bubble Size

The requirement is not simply to show where the cities are. It is to show **sales for different cities**.

Therefore, Net Sales is used to control the bubble size.

### Steps

1. Expand the Fact table.
2. Locate **Net Sales**.
3. Drag **Net Sales** into the **Bubble Size** bucket.

Now the bubbles have different sizes depending on sales.



---

# 14.6 Interpret Bubble Size

The map now provides an immediate visual comparison:

* **Larger bubble → Higher sales**
* **Smaller bubble → Lower sales**

You can also hover over a bubble to see information about that city and its sales.

Therefore, the map makes it easy to identify cities generating higher sales. 

---

# 15. Format the Map Tooltip

When you hover over a bubble, the tooltip initially displays:

* City
* Sum of Net Sales
* Net Sales value

The lecture wants to remove the unnecessary **"Sum of"** wording.

---

## Steps

1. In the map visual, locate the **Bubble Size** field.
2. Click/double-click the Net Sales field.
3. Instead of **Sum of Net Sales**, rename the field to:

**Net Sales**

4. Press **Enter**.

Now the tooltip displays:

**City → Net Sales**

rather than:

**City → Sum of Net Sales**. 

---

# 16. Add a Border to the Map

### Steps

1. Select the map visual.
2. Click **Format a visual**.
3. Go to **General**.
4. Open **Effects**.
5. Turn **Visual border → On**.
6. Set the border color to **Gray**. 

---

# 17. Format the Map Title

The title can be changed to:

**Sales by City**

The lecture mentions either "Net Sales by City" or simply "Sales by City."

### Steps

1. Go to **Title**.
2. Change the title.
3. Use appropriate formatting.

The demonstrated formatting includes:

* Times New Roman
* Bold
* Italic
* Underline
* Center alignment



---

# 18. Enable Category Labels

The lecture also enables category labels.

### Steps

1. Collapse the Title section if necessary.
2. Collapse Effects.
3. Go to the **Visual** section.
4. Turn **Category labels → On**.

This allows the names of the different cities to be displayed on the visual. 

---

# Requirement 8 — Total Number of Orders

## 19.1 Objective

The final requirement covered in the lecture is:

> Show the **total number of orders**.

A **Card visual** is used because a card is appropriate for displaying a single important KPI/value. 

---

# 19.2 Create the Card Visual

### Steps

1. Go to the Overview page.
2. Click on a blank area of the canvas.
3. Select the **Card** visual.
4. A blank card is created.
5. Resize it.
6. Position it near the top of the page.



---

# 20. Create an Order ID

The Fact table contains records where:

> **Each record represents one unique order.**

However, the table does not currently contain a column that explicitly identifies each order uniquely.

Therefore, an **Index Column** is created in Power Query.



---

# 21. Add an Index Column in Power Query

### Steps

1. Open **Power Query Editor**.
2. Select the Fact table.
3. Use the option for adding an **Index Column**.
4. Select:

**From 1**

This creates an index beginning at 1.



---

# 22. Move the Index Column to the Beginning

The Index column is initially added at the end.

### Steps

1. Right-click the newly created Index column.
2. Select the option to move it.
3. Move it to the **Beginning**.

Now the Order ID column will appear at the beginning of the Fact table. 

---

# 23. Rename Index to Order ID

The Index column is renamed because it will represent the unique order identifier.

### Steps

1. Double-click the Index column name.
2. Rename it to:

**Order ID**

3. Press **Enter**.

Since each row represents one unique order, this Index can now identify the individual orders. 

---

# 24. Change Order ID Data Type to Text

The Order ID is an identifier rather than a numerical measure.

Therefore, we don't want Power BI to perform calculations such as:

* Sum
* Average
* Other numerical aggregations

### Steps

1. Select the **Order ID** column.
2. Change its data type from:

**Whole Number**

to:

**Text**

This is a useful modeling practice: **identifiers should generally be treated as identifiers rather than numerical measures** in this context. 

---

# 25. Apply Power Query Changes

### Steps

1. Click the dropdown/menu in Power Query.
2. Select:

**Close & Apply**

3. Power BI loads the updated Fact table into the model.
4. Return to the Report view.



---

# 26. Add Order ID to the Card

The newly created Order ID field is now available in the model.

### Steps

1. Select the blank Card visual.
2. Select/check **Order ID**.

Initially, Power BI may display the first Order ID or use an undesired aggregation.

But the requirement is:

> Count the unique Order IDs.

Therefore, a **Distinct Count** is required. 

---

# 27. Change Aggregation to Distinct Count

### Steps

1. Open the dropdown associated with Order ID.
2. Select:

**Count (Distinct)** / **Distinct Count**

The card now displays:

**3510 orders**

according to the lecture dataset. 

---

# 28. Add a Border to the Card

### Steps

1. Select the Card.
2. Open **Format a visual**.
3. Go to **General**.
4. Open **Effects**.
5. Turn **Visual border → On**.
6. Set the border color to **Gray**.



---

# 29. Rename the Card Category Label

The Card initially displays something like:

**Count of Order ID**

But this is not a user-friendly report label.

The desired wording is:

**Number of Orders**

### Steps

1. Select the Card.
2. Go to **Add Data to Your Visual** / the relevant field configuration.
3. Locate the field currently showing **Count of Order ID**.
4. Rename it to:

**Number of Orders**

5. Press **Enter**.



---

# 30. Format the Card

The lecture further formats the card's:

* Category label
* Callout value

---

## Category Label

The category label is formatted with:

* **Color:** Black
* Smaller font size
* Bold
* Times New Roman

The lecture considers a size around **8–10**.

---

## Callout Value

The callout value is the large number:

**3510**

The lecture changes the callout value size to approximately:

**25**

and later adjusts the visual sizing/layout.

The callout value is also formatted with:

* Times New Roman
* Bold



---

# 31. Final Overview Page — Requirements Completed

At the end of the lecture, the Overview page contains the required visuals.

| Requirement           | Visual Used       | Purpose                                |
| --------------------- | ----------------- | -------------------------------------- |
| Sales trend over time | Line Chart        | Show sales trends by time period       |
| Requirement 3         | Scatter Plot      | Relationship between Profit and Sales  |
| Requirement 5         | Stacked Bar Chart | Average Discount by Promotion Category |
| Requirement 6         | Map               | Sales by City                          |
| Requirement 8         | Card              | Total Number of Orders                 |

The lecture explicitly summarizes these four newly covered requirements as:

* Scatter plot → relationship between Sales and Profit
* Bar chart → average discount by promotion category
* Card → total number of orders
* Map → sales for different cities 

---

# 32. Reorder the Report Pages

The final step is to move the **Overview** page to the beginning.

### Steps

1. Locate the **Overview** page tab.
2. Double-click/select the page.
3. Move it to the beginning of the page sequence.

The resulting order is essentially:

**Page 1 → Overview**

followed by:

**Top Bottom Five Analysis**

and the other report pages. 

---

# Important Power BI Concepts From This Lecture

## 1. Scatter Plot

Use a **Scatter Plot** when you need to analyze the relationship between **two numerical variables**.

Example:

**Profit vs. Net Sales**

---

## 2. Don't Summarize

If you want individual observations/coordinates instead of a single aggregated value:

**Field dropdown → Don't summarize**

In this lecture, this was applied to:

* Profit
* Net Sales

---

## 3. Aggregation Matters

Power BI automatically applies aggregations such as:

* Sum
* Average
* Count
* Distinct Count

You need to choose the correct aggregation based on the requirement.

Examples:

**Average Discount → Average**

**Number of Orders → Distinct Count of Order ID**

---

## 4. Format Painter

**Format Painter** copies formatting from an existing visual to another visual.

Useful when multiple visuals need a consistent design.

---

## 5. Data Category

For geographical fields, Power BI needs to know what type of location the field represents.

Example:

**Customer City → Data Category → City**

This helps Power BI correctly interpret the values as geographical locations.

---

## 6. Map Bubble Size

In a map visual:

**Location → City**

**Bubble Size → Net Sales**

Therefore:

> Higher Sales → Larger Bubble

---

## 7. Dimension-Fact Mismatch and Blank Categories

A Blank category can appear when a value in the Fact table doesn't have a corresponding value in the related Dimension table.

In this example:

**Fact Promotion ID = 0**

but:

**Promotion Dimension → no Promotion ID 0**

Therefore, Power BI displays those unmatched records under **Blank**.

---

## 8. Index Column for Unique Identification

When every row in a table represents a unique record/order but there is no explicit identifier:

**Power Query → Add Index Column → From 1**

The index can then be renamed:

**Order ID**

---

## 9. Identifier vs. Numerical Measure

Although Order ID contains numbers, it is an **identifier**, not a value on which we normally perform mathematical operations.

Therefore, it is changed to:

**Data Type → Text**

---

## 10. Distinct Count

When the requirement is to count unique orders:

**Order ID → Distinct Count**

rather than:

**Sum**

or a normal count where duplicates could affect the result.

---

# Quick Revision Flow

### Sales vs Profit

**Blank canvas → Scatter Chart → Profit (X-axis) → Net Sales (Y-axis) → Don't Summarize both**

↓

### Average Discount

**Blank canvas → Stacked Bar Chart → Discount Rate → Average → Promotion Name (Y-axis)**

↓

Remove unwanted:

**Blank category → Filters → Select All → Uncheck Blank**

↓

### Sales by City

**Map → Customer City → Data Category = City → City → Location → Net Sales → Bubble Size**

↓

### Total Orders

**Power Query → Fact Table → Add Index Column → From 1 → Move to Beginning → Rename Order ID → Data Type = Text → Close & Apply**

↓

**Card → Order ID → Distinct Count → Rename to Number of Orders**

↓

**Format visuals → borders, titles, fonts, labels, gridlines**

↓

**Move Overview page to the beginning**

This completes the four requirements covered in the lecture.
