# Power BI – Sales by Region Visual Using `ALLEXCEPT`

## 1. Session Overview

In this session, the focus is on:

1. Creating a new DAX measure called **Sales by Region**.
2. Using the **`CALCULATE()`** and **`ALLEXCEPT()`** functions.
3. Ensuring that the sales calculation is affected **only by the Region filter**.
4. Creating a **Stacked Bar Chart** using the measure.
5. Formatting the chart extensively.

The key requirement is:

> Calculate total sales by region while ignoring filters coming from other columns/tables, so that **only Region acts as a filter** on the sales value.

---

# 2. Business Requirement – Sales by Region

We want to create a visual that represents:

> **Total Sales for different regions**

However, there is an important condition.

Suppose the Housing table contains fields such as:

* Date
* House Type
* Sales Type
* Region
* City
* Area
* Purchase Price
* etc.

We **do not** want the sales calculation to respond to every possible filter.

Instead:

```text
Region filter → Should affect Sales
Other filters → Should NOT affect Sales
```

For example:

| Region   |                    Sales |
| -------- | -----------------------: |
| Region A | Total sales for Region A |
| Region B | Total sales for Region B |
| Region C | Total sales for Region C |
| Region D | Total sales for Region D |

The DAX function that helps achieve this behavior is:

> **`ALLEXCEPT()`**

---

# 3. Creating the Sales by Region Measure

## Step 1 – Select the Measures Table

Since we created a dedicated Measures table in the previous session:

1. Right-click on the **Measures table**.
2. Select:

> **New Measure**

A new DAX measure will be created.

---

# 4. Naming the Measure

Name the measure:

```text
Sales by Region
```

---

# 5. DAX Logic

The basic structure used in the lecture is:

```DAX
Sales by Region =
CALCULATE(
    SUM(Housing[Purchase Price]),
    ALLEXCEPT(
        Housing,
        Housing[Region]
    )
)
```

### Breakdown

The measure consists of two important functions:

```text
CALCULATE()
ALLEXCEPT()
```

---

# 6. Understanding `SUM()`

The first part is:

```DAX
SUM(Housing[Purchase Price])
```

This calculates the total of the **Purchase Price** column.

In this project, Purchase Price is being treated as the sales value from the perspective of the seller/developer.

So conceptually:

```text
Total Sales = SUM(Purchase Price)
```

---

# 7. Understanding `CALCULATE()`

The measure uses:

```DAX
CALCULATE()
```

`CALCULATE()` is used when we want to evaluate an expression under a **modified filter context**.

Here:

```DAX
CALCULATE(
    SUM(Housing[Purchase Price]),
    ...
)
```

means:

> Calculate the total purchase price while applying the specified filter-context modification.

---

# 8. Understanding `ALLEXCEPT()`

The most important part of this measure is:

```DAX
ALLEXCEPT(
    Housing,
    Housing[Region]
)
```

`ALLEXCEPT()` removes filters from the specified table **except for the column(s) explicitly mentioned**.

Here:

```DAX
ALLEXCEPT(
    Housing,
    Housing[Region]
)
```

means:

> Remove filters from the Housing table, but retain the filter on Region.

Therefore:

```text
Region filter
     ↓
RETAIN

Other Housing-table filters
     ↓
REMOVE
```

### Why is this useful?

It ensures that the Sales by Region measure focuses specifically on the regional breakdown rather than being affected by other filters applied to the Housing table.

---

# 9. Complete DAX Measure

The final measure created in the lecture is conceptually:

```DAX
Sales by Region =
CALCULATE(
    SUM(Housing[Purchase Price]),
    ALLEXCEPT(
        Housing,
        Housing[Region]
    )
)
```

After writing the formula:

1. Press **Enter**.
2. The measure is created.
3. Collapse the formula bar if required.

---

# 10. Creating the Bar Chart

Now the newly created measure needs to be represented visually.

### Steps

1. Click on a **blank area of the report canvas**.
2. Open the **Visualizations** pane.
3. Select:

> **Stacked Bar Chart**

A blank bar chart appears.

Resize it and position it appropriately on the report page.

---

# 11. Adding Sales by Region to the Chart

The newly created measure is:

> **Sales by Region**

### Steps

1. Select/double-click the **Sales by Region** measure.
2. Drag it to the appropriate axis bucket.

Because this is a **horizontal bar chart**, the sales value is placed on the:

> **X-axis**

---

# 12. Adding Region to the Chart

We now need to show separate bars for each region.

### Steps

1. Locate the **Region** field in the Data pane.
2. Drag it to the:

> **Y-axis**

The resulting structure is:

```text
X-axis → Sales by Region
Y-axis → Region
```

The chart now displays sales for the different regions.

---

# 13. Formatting the Chart Using Format Painter

The instructor uses an already formatted visual to maintain consistency.

### Steps

1. Select an existing formatted visual.
2. Click:

> **Format Painter**

3. Click the newly created bar chart.

This transfers formatting from the existing visual to the new bar chart.

This is useful because it helps maintain a **consistent visual design across the report**.

---

# 14. Formatting the Bar Layout

Select the bar chart and open:

> **Format Visual**

Then navigate to the **Bars** section.

Within Bars, locate:

> **Layout**

One of the options available is the spacing between categories.

---

# 15. Adjusting Space Between Categories

The instructor changes the:

> **Space between categories**

to adjust the distance between the individual bars.

You can:

* Increase the spacing
* Decrease the spacing

depending on how compact or spread out you want the chart to look.

The exact value is not mandatory.

---

# 16. Adding a Border

The instructor adds a border around the visual.

### Steps

1. Select the bar chart.
2. Go to:

> **Format Visual → General → Effects**

3. Turn:

> **Border → On**

4. Expand the Border settings.
5. Change the border color.

The instructor changes the default black border to approximately a **gray** color.

---

# 17. Adding a Background

A background is also added to the visual.

### Steps

1. Stay under:

> **General → Effects**

2. Open the **Background** settings.
3. Enable/configure the background.
4. Choose a suitable color.

Again, the exact color is a design choice.

---

# 18. Changing the Bar Color

The instructor then changes the color of the bars.

### Steps

1. Select the bar chart.
2. Go to:

> **Format Visual**

3. Find the relevant bar/color setting.
4. Change the bar color.

The example uses:

> **White**

However, any suitable color can be selected depending on the report theme.

---

# 19. Turning Ribbons On

The instructor also enables:

> **Ribbons**

This adds ribbon-like visual elements to the bar chart.

### Steps

1. Select the bar chart.
2. Open:

> **Format Visual**

3. Find the **Ribbons** option.
4. Turn it:

> **On**

The ribbons can then be further formatted.

---

# 20. Formatting Ribbons

After enabling ribbons:

1. Expand the **Ribbons** section.
2. Scroll through the available formatting options.
3. Adjust the transparency if required.

The instructor demonstrates changing the transparency level.

The exact transparency value isn't important; it can be adjusted according to the desired appearance.

---

# 21. Formatting the X-Axis

The instructor does **not** want the normal X-axis title and axis values displayed.

### Steps

1. Select the bar chart.
2. Go to:

> **Format Visual → X-axis**

3. Change:

> **Values → Off**

4. Change:

> **Title → Off**

Therefore, the horizontal axis itself no longer displays its normal axis values/title.

---

# 22. Showing Data Labels

Although the X-axis values are hidden, the instructor still wants the sales values to be visible directly on the bars.

Therefore, **Data Labels** are enabled.

### Steps

1. Collapse the X-axis settings if necessary.
2. Locate:

> **Data labels**

3. Turn:

> **Data labels → On**

Now the numerical sales values appear directly on the bars.

---

# 23. Positioning the Data Labels

The position of the data labels is then changed.

### Steps

1. Open the **Data labels** settings.
2. Find the label position.
3. Change it from:

> **Auto**

to:

> **Inside end**

This places the value near the end of each bar, inside the bar itself.

---

# 24. Formatting Data Label Values

The data-label values can also be customized.

Under the relevant **Values** section:

* Change text color.
* Change font weight.
* Adjust font size if necessary.

The instructor initially considers black and later chooses a dark-gray-like appearance.

The values are also made:

> **Bold**

This makes them easier to read.

---

# 25. Formatting the Y-Axis

The Y-axis contains the Region names.

The instructor does not want the axis title:

> **Region**

to be displayed.

### Steps

1. Open:

> **Format Visual → Y-axis**

2. Find **Title**.
3. Change:

> **Title → Off**

The Region labels themselves remain visible.

---

# 26. Formatting Region Labels

The region values displayed along the Y-axis are also formatted.

The instructor changes:

* Text color → Gray
* Font → Bold
* Font size → Increased

This makes the region names more visually prominent.

---

# 27. Adding the Chart Title

The instructor adds a suitable title to the visual.

### Steps

1. Select the bar chart.
2. Go to:

> **General → Title**

3. Turn the title on if necessary.
4. Enter:

```text
Sales by Region
```

---

# 28. Formatting the Chart Title

The title is then customized.

The instructor demonstrates:

* Text color → Gray
* Font → Bold
* Font size → Approximately **20**
* Italic → On
* Underline → On
* Horizontal alignment → Center

The exact formatting can be adjusted according to your report's design.

---

# 29. Adjusting Bar Width / Category Spacing

The instructor also demonstrates that the width/spacing of the bars can be adjusted.

### Steps

1. Select the bar chart.
2. Go to:

> **Format Visual → Bars**

3. Open:

> **Layout**

4. Adjust:

> **Space between categories**

Increasing the spacing makes bars thinner/more separated.

Reducing the spacing makes the bars thicker/closer together.

---

# 30. Final Visual Structure

The final chart follows this structure:

```text
             Sales by Region
────────────────────────────────────

Region A  ███████████████████  125M
Region B  ███████████████      98M
Region C  █████████████████    112M
Region D  ██████████            75M
```

The actual values will come from the dataset.

---

# 31. Important DAX Concept – `ALLEXCEPT()`

This is the most important technical concept from this session.

### Syntax

```DAX
ALLEXCEPT(
    <table>,
    <column1>,
    <column2>,
    ...
)
```

It removes filters from the specified table **except those on the specified columns**.

In this lecture:

```DAX
ALLEXCEPT(
    Housing,
    Housing[Region]
)
```

Therefore:

```text
Housing filters
       │
       ├── Region → KEEP
       │
       ├── Date → REMOVE
       ├── City → REMOVE
       ├── House Type → REMOVE
       ├── Sales Type → REMOVE
       └── Other Housing filters → REMOVE
```

---

# 32. Key Difference: Normal Sales vs Sales by Region

### Normal total sales

A simple measure:

```DAX
Total Sales =
SUM(Housing[Purchase Price])
```

responds to the normal filter context.

For example:

```text
Date + Region + City + Sales Type
              ↓
        Total Sales
```

### Sales by Region

The new measure:

```DAX
Sales by Region =
CALCULATE(
    SUM(Housing[Purchase Price]),
    ALLEXCEPT(
        Housing,
        Housing[Region]
    )
)
```

modifies the filter context so that the **Region filter is retained** while other filters on the Housing table are removed.

---

# 33. Complete Workflow

```text
Measures Table
      ↓
Right-click
      ↓
New Measure
      ↓
Name → Sales by Region
      ↓
CALCULATE()
      ↓
SUM(Housing[Purchase Price])
      ↓
ALLEXCEPT(Housing, Housing[Region])
      ↓
Press Enter
      ↓
Create blank Stacked Bar Chart
      ↓
X-axis → Sales by Region
      ↓
Y-axis → Region
      ↓
Format Painter
      ↓
Format Bars/Layout
      ↓
Adjust category spacing
      ↓
Add Border
      ↓
Add Background
      ↓
Change bar color
      ↓
Enable Ribbons
      ↓
Format Ribbons
      ↓
X-axis Values → Off
      ↓
X-axis Title → Off
      ↓
Data Labels → On
      ↓
Position → Inside End
      ↓
Format label color/font
      ↓
Y-axis Title → Off
      ↓
Format Region labels
      ↓
Title → Sales by Region
      ↓
Format title
      ↓
Adjust bar spacing
```

---

# 34. Quick Revision

| Component            | Setting/Action                 |
| -------------------- | ------------------------------ |
| Measure              | Sales by Region                |
| Main calculation     | `SUM(Purchase Price)`          |
| Context modification | `ALLEXCEPT()`                  |
| Filter retained      | Region                         |
| Table                | Housing                        |
| Visual               | Stacked Bar Chart              |
| X-axis               | Sales by Region                |
| Y-axis               | Region                         |
| Category spacing     | Adjust according to preference |
| Border               | On                             |
| Background           | Added                          |
| Bar color            | Changed                        |
| Ribbons              | On                             |
| X-axis values        | Off                            |
| X-axis title         | Off                            |
| Data labels          | On                             |
| Label position       | Inside End                     |
| Y-axis title         | Off                            |
| Region labels        | Gray/Bold                      |
| Chart title          | Sales by Region                |
| Title size           | ~20                            |
| Title alignment      | Center                         |

---

## 35. Key Takeaways

* **`CALCULATE()`** is used to modify the filter context in which a calculation is evaluated.
* **`ALLEXCEPT()`** removes filters from a table while retaining filters on specified columns.
* In this example, **Region is deliberately preserved**.
* The `Sales by Region` measure is then used as the numerical value in a **Stacked Bar Chart**.
* **Data Labels** can be used when you hide axis values but still want the exact values displayed.
* **Format Painter** is useful for maintaining a consistent design across visuals.
* Bar spacing, colors, borders, backgrounds, ribbons, labels, axes, and titles can all be customized to match the report's visual theme.
