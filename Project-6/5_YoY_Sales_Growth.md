# Power BI – House Market Overview: YoY Sales Growth & Line Chart

## 1. Session Overview

In the previous session, we covered:

* Column definitions.
* Data cleaning.
* Data profiling using Power Query.
* Loading the cleaned data into the Power BI model.

Now that the data has been loaded into the model, the next step is to **create the report**.

The project will contain multiple report pages. In this stage, the instructor starts with **two pages**, with additional pages to be discussed later.

The focus of this session is:

1. Creating a **Year-on-Year (YoY) Sales Growth** measure using DAX.
2. Understanding the `Sales Type` categories.
3. Creating a **line chart** to display YoY sales growth by sales type.
4. Formatting the report page.
5. Adding a canvas background image.
6. Creating and formatting a report title/shape.
7. Formatting the line chart.

---

# 2. Understanding the Business Perspective

The dataset is essentially about **property purchases**.

However, from the perspective of someone who is selling the properties—such as:

* A builder
* A developer
* A property seller

the same transactions can be considered **sales**.

Therefore, although the dataset contains property purchase information, the report will analyze it from a **sales perspective**.

Hence, the report will contain:

> **Sales-related analysis**

---

# 3. Sales Type Categories

The instructor first checks the `Sales Type` column.

### Steps to inspect the data

1. Go to **Data/Table View** in Power BI.
2. Locate the housing table.
3. Look at the `Sales Type` column.

The dataset contains four sales-type categories:

* **Auction**
* **Family Sale**
* **Other Sale**
* **Regular Sale**

These categories will later be used as the categorical dimension in the line chart.

---

# 4. KPI – Year-on-Year Sales Growth

The first KPI that needs to be represented is:

> **Year-on-Year Sales Growth**

### Business requirement

The objective is to compare:

> Sales value in the **highest year available in the Date column**

against:

> Sales value in the **year immediately before the highest year**.

For example, suppose the maximum year in the dataset is 2025.

Then the calculation compares:

```text
2025 Sales
      vs
2024 Sales
```

The result is expressed as a percentage growth/change.

---

# 5. DAX Measure – Year-on-Year Sales Growth

The calculation is created as a **measure**, not a calculated column.

### Steps to create the measure

1. Go to the **Data pane**.
2. Locate the **Housing** table.
3. Right-click the Housing table.
4. Select **New Measure**.
5. Expand the formula bar if necessary.
6. Give the measure the name:

```text
Year on Year Sales Growth
```

---

# 6. DAX Logic Used in the Measure

The instructor uses **variables** to make the DAX calculation easier to structure.

Conceptually, the measure consists of three major parts:

```text
Current Year Sales
        ↓
Previous Year Sales
        ↓
Calculate Growth %
```

---

## 6.1 Variable 1 – Current Year Sales

The first variable is:

```text
Current Year Sales
```

It calculates the total purchase price for the **maximum year available in the Date column**.

Conceptually:

```text
Current Year Sales =
SUM(Purchase Price)
for Maximum Year
```

The DAX uses:

* `VAR`
* `CALCULATE`
* `SUM`
* `YEAR`
* `MAX`

### Logic

The maximum date is obtained first:

```text
MAX(Date)
```

Then its year is extracted:

```text
YEAR(MAX(Date))
```

The purchase prices for that year are then summed.

---

# 7. Variable 2 – Previous Year Sales

The second variable is:

```text
Previous Year Sales
```

This calculates the total purchase price for the year immediately before the maximum year.

Conceptually:

```text
Previous Year Sales =
SUM(Purchase Price)
for Maximum Year - 1
```

For example:

If:

```text
Maximum Year = 2025
```

then:

```text
Previous Year = 2024
```

Again, the calculation uses:

* `VAR`
* `CALCULATE`
* `SUM`
* `YEAR`
* `MAX`

---

# 8. Calculating YoY Growth

After calculating current-year and previous-year sales, the instructor uses:

```text
RETURN
```

and an:

```text
IF
```

condition.

The calculation is conceptually:

$$
YoY\ Growth =
\frac{Current\ Year\ Sales - Previous\ Year\ Sales}
{Previous\ Year\ Sales}
$$

---

## 8.1 Why Check Previous Year Sales?

The instructor checks whether:

```text
Previous Year Sales ≠ 0
```

This is important because dividing by zero would cause an invalid calculation.

Therefore:

```text
IF Previous Year Sales ≠ 0
    calculate YoY growth
ELSE
    return BLANK()
```

### Conceptual DAX structure

```text
IF(
    Previous Year Sales <> 0,
    (Current Year Sales - Previous Year Sales)
        / Previous Year Sales,
    BLANK()
)
```

This protects the calculation from division-by-zero errors.

---

# 9. DAX Structure to Remember

The overall structure demonstrated in the lecture is:

```text
Year on Year Sales Growth
        │
        ├── Current Year Sales
        │       └── Sales for maximum year
        │
        ├── Previous Year Sales
        │       └── Sales for maximum year - 1
        │
        └── YoY Growth
                ├── Current - Previous
                └── ÷ Previous
```

### Formula

$$
\boxed{
YoY = \frac{Current - Previous}{Previous}
}
$$

---

# 10. Creating the Report Page Design

Before creating the line chart, the instructor performs some page formatting.

The goal is to make the report visually appealing.

---

# 11. Adding a Rectangle Shape

The instructor adds a rectangle to the report page.

### Steps

1. Go to the **Insert** tab.
2. Select **Shapes**.
3. Select **Rectangle**.
4. A rectangle is added to the canvas.
5. Resize the rectangle according to the desired page layout.

---

# 12. Formatting the Rectangle

The rectangle is used as part of the report header/design.

### Change the border

1. Select the rectangle.
2. Open the **Format Shape** options.
3. Locate the **Border** option.
4. Turn the border **Off**.

### Change the color

Select the fill/background color of the rectangle.

The instructor chooses a **light red/pink shade**.

The exact color used visually is approximately:

```text
#F7B8B8
```

---

# 13. Adding Text to the Shape

The rectangle is also used to display the report title.

### Steps

1. Select the rectangle.
2. Under the shape's **Style** options, turn **Text** on.
3. Enter:

> **House Market Overview**

This becomes the title of the report page.

---

# 14. Formatting the Page Title

The instructor further formats the title.

The formatting includes:

* Changing font style.
* Increasing font size.
* Making the text **Bold**.
* Making it **Italic**.
* Making it **Underlined**.

The exact font can be selected according to preference.

---

# 15. Adding a Canvas Background Image

The instructor also adds a background image to the report canvas.

### Steps

1. Click on a **blank area of the canvas**.
2. Open the **Format** options for the report page.
3. Go to:

```text
Report Page
    → Canvas Background
```

4. Choose **Browse**.
5. Select the required background image.

The instructor mentions that the background images will be provided in the **resource section**.

---

# 16. Fixing Background Image Transparency

Initially, the background image may not be visible because its transparency is set to:

```text
100%
```

At 100% transparency, the image is effectively invisible.

### Steps

1. Locate the **Transparency** setting.
2. Change it from:

```text
100%
```

to:

```text
0%
```

3. The background image becomes visible.

### Important concept

```text
100% transparency → Image invisible
0% transparency   → Image fully visible
```

---

# 17. Creating the Line Chart

Now the actual visual for YoY sales growth is created.

### Steps

1. Click on a blank area of the report canvas.
2. Select **Line Chart** from the Visualizations pane.
3. A blank line chart appears.
4. Resize it as required.
5. Position it appropriately on the report page.

---

# 18. Adding YoY Sales Growth to the Line Chart

The newly created measure needs to be added to the chart.

### Steps

1. Locate the:

> `Year on Year Sales Growth`

measure in the Data pane.
2. Drag and drop it into the:

> **Y-axis**

bucket.

This determines the numerical value plotted on the chart.

---

# 19. Adding Sales Type to the X-Axis

The instructor wants to compare YoY sales growth across the different sales categories.

### Steps

1. Locate the `Sales Type` field.
2. Drag and drop it into the:

> **X-axis**

bucket.

The X-axis therefore contains:

* Auction
* Family Sale
* Other Sale
* Regular Sale

The Y-axis contains:

> Year-on-Year Sales Growth

---

# 20. Final Line Chart Structure

The visual is essentially:

```text
                 Year-on-Year Sales Growth
                           ↑
                           │
                           │
                           │
                           │
                           │
                           └────────────────────────→
                              Sales Type
```

### X-axis

**Sales Type**

### Y-axis

**Year on Year Sales Growth**

This allows the user to compare the YoY sales growth across different sales categories.

---

# 21. Formatting the Line Chart

Once the chart is created, the instructor formats it to improve its appearance.

The main formatting changes include:

* Removing gridlines.
* Smoothing the line.
* Changing line color.
* Adding shaded area.
* Adding markers.
* Hiding unnecessary axis titles.
* Formatting axis values.
* Adding data labels.
* Adding a chart title.
* Adding a border.

---

# 22. Removing Horizontal Gridlines

The instructor does not want horizontal gridlines visible.

### Steps

1. Select the line chart.
2. Open **Format Visual**.
3. Find the **Gridlines** settings.
4. Locate **Horizontal gridlines**.
5. Change it to:

> **Off**

This produces a cleaner-looking chart.

---

# 23. Changing Line Interpolation

The instructor changes the line style from:

> **Linear**

to:

> **Smooth**

### Why?

A smooth interpolation makes the line chart visually softer and more polished.

### Steps

1. Select the chart.
2. Open the relevant **Lines** formatting section.
3. Locate **Interpolation type**.
4. Change:

```text
Linear → Smooth
```

---

# 24. Changing Line Color

The instructor changes the line color to match the page design.

The selected color is:

```text
#F7B8B8
```

This matches the light red/pink shade used for the page design.

---

# 25. Adding a Shaded Area

The instructor also chooses to add a **shaded area** beneath/around the line.

This helps make the visual more visually appealing.

The exact availability of this option can depend on the Power BI visual/version being used.

---

# 26. Adding Markers

Markers are added to make individual data points easier to identify.

### Steps

1. Open the **Markers** formatting section.
2. Turn markers on if necessary.
3. Adjust the marker size.

The instructor mentions that the marker size can be increased if desired.

---

# 27. Formatting the X-Axis

The instructor wants the Sales Type values to remain visible but does not want an X-axis title.

### Steps

1. Select the line chart.
2. Open the **X-axis** formatting section.
3. Turn the **X-axis title**:

> **Off**

The actual category values remain visible.

### Important distinction

The instructor is **not hiding the X-axis values**.

Only the **axis title** is removed.

So categories such as:

```text
Auction
Family Sale
Other Sale
Regular Sale
```

remain visible.

---

# 28. Formatting X-Axis Values

The instructor further formats the X-axis values.

Possible formatting changes include:

* Font style
* Text color
* Font size
* Bold formatting

The instructor chooses:

* A gray text color.
* Bold text.
* Slightly increased font size.

---

# 29. Formatting the Y-Axis

The instructor then formats the Y-axis.

### Changes

The instructor turns:

> **Y-axis values → Off**

and:

> **Y-axis title → Off**

This creates a cleaner visual.

The chart still communicates the values through data labels.

---

# 30. Data Labels

The instructor enables data labels so that the actual values are displayed directly on the chart.

### Steps

1. Select the line chart.
2. Open the **Data Labels** section.
3. Change Data Labels:

> **On**

The values are now displayed near the data points.

---

# 31. Formatting Data Labels

The instructor further formats the data labels.

### Possible changes

* Text color
* Font size
* Bold formatting

The instructor chooses:

* A suitable text color.
* **Bold** text.
* Slightly larger font size.

This makes the values easier to read.

---

# 32. Adding a Chart Title

The chart needs a meaningful title.

The instructor names it:

> **Year on Year Sales Growth by Sales Type**

### Steps

1. Select the line chart.
2. Go to **General**.
3. Open **Title**.
4. Enter:

```text
Year on Year Sales Growth by Sales Type
```

---

# 33. Formatting the Chart Title

The title is then formatted.

The instructor changes:

* Font style.
* Text color.
* Font weight.
* Alignment.

The selected style includes:

* Gray text.
* Bold.
* Italic.
* Underlined.
* Appropriate horizontal alignment.

---

# 34. Adding a Border to the Visual

The instructor adds a border around the line chart.

### Steps

1. Select the line chart.
2. Open:

```text
Format Visual
    → General
    → Effects
```

3. Locate **Visual Border**.
4. Expand the Visual Border section.
5. Turn the border on.
6. Choose an appropriate border color.

By default, Power BI may use a black border, but the instructor changes it to a more suitable color.

---

# 35. Final Visual

After all the formatting, the visual contains:

### Title

**Year on Year Sales Growth by Sales Type**

### X-axis

Sales Type:

* Auction
* Family Sale
* Other Sale
* Regular Sale

### Y-axis

Year-on-Year Sales Growth

### Visual formatting

* Smooth line
* Matching line color
* Markers
* Shaded area
* Data labels
* No horizontal gridlines
* No X-axis title
* No Y-axis title
* Formatted category values
* Formatted data labels
* Border around the visual

---

# 36. Complete Process – Quick Revision

The entire session can be remembered as:

```text
Cleaned Housing Dataset
        ↓
Loaded into Power BI Model
        ↓
Identify Sales Analysis Requirement
        ↓
Create YoY Sales Growth Measure
        ↓
Calculate Current Year Sales
        ↓
Calculate Previous Year Sales
        ↓
Calculate YoY %
        ↓
Add Report Page Design
        ↓
Add Rectangle Shape
        ↓
Add "House Market Overview"
        ↓
Add Canvas Background
        ↓
Create Line Chart
        ↓
X-axis → Sales Type
Y-axis → YoY Sales Growth
        ↓
Format Chart
        ↓
Add Title + Data Labels + Markers
        ↓
Final Report Visual
```

---

# 37. DAX Concept – Most Important Part

The core DAX logic is:

```text
Current Year Sales
=
Sales in Maximum Year

Previous Year Sales
=
Sales in Maximum Year - 1

YoY Growth
=
(Current Year Sales - Previous Year Sales)
/
Previous Year Sales
```

With protection against division by zero:

```text
IF(
    Previous Year Sales <> 0,
    (Current Year Sales - Previous Year Sales)
        / Previous Year Sales,
    BLANK()
)
```

### Why use variables?

The lecture uses `VAR` to separately calculate:

```text
VAR Current Year Sales = ...
VAR Previous Year Sales = ...
RETURN ...
```

This makes a complex DAX calculation easier to organize and understand.

---

# 38. Important Power BI Concepts From This Session

## Measure vs Column

The YoY Sales Growth calculation is created as a **measure** because it is an aggregated/calculated business metric that needs to respond to the report's evaluation context.

---

## CALCULATE

`CALCULATE()` is used to calculate sales under a specified year condition.

Conceptually:

```text
CALCULATE(
    SUM(Purchase Price),
    Year = Maximum Year
)
```

---

## MAX

`MAX(Date)` identifies the latest date available in the dataset.

Then:

```text
YEAR(MAX(Date))
```

extracts the year from that date.

---

## IF

`IF()` is used to ensure that the calculation only performs the division when previous-year sales are non-zero.

---

## BLANK

`BLANK()` is returned when previous-year sales are zero.

This avoids displaying an invalid percentage.

---

# 39. Report Design Concepts

The instructor also demonstrates several Power BI design techniques:

### Shapes

Used to create:

* Headers
* Background sections
* Decorative elements

### Canvas Background

Used to give the report page a visual background.

### Transparency

Controls how visible a background image is.

### Visual Border

Creates separation around individual visuals.

### Data Labels

Display actual values directly on the chart.

### Markers

Highlight individual data points.

### Smooth Interpolation

Makes line charts visually smoother.

---

# 40. Practical Checklist for Recreating This Page

When recreating the report yourself, follow this order:

### Step 1 – Create the measure

**Housing → Right-click → New Measure**

Create:

> `Year on Year Sales Growth`

---

### Step 2 – Create page header

**Insert → Shapes → Rectangle**

Then:

* Resize it.
* Turn border off.
* Choose a light red/pink fill.
* Turn text on.
* Enter **House Market Overview**.
* Format the title.

---

### Step 3 – Add background

**Canvas → Background → Browse**

Select the supplied image.

Set:

> Transparency = **0%**

---

### Step 4 – Create line chart

Insert:

> **Line Chart**

---

### Step 5 – Add fields

```text
X-axis → Sales Type

Y-axis → Year on Year Sales Growth
```

---

### Step 6 – Format chart

Apply:

* Horizontal gridlines → Off
* Interpolation → Smooth
* Line color → `#F7B8B8`
* Shaded area → On, if desired
* Markers → On
* Data labels → On
* X-axis title → Off
* Y-axis title → Off
* Y-axis values → Off
* Appropriate font formatting

---

### Step 7 – Add title

Set:

> **Year on Year Sales Growth by Sales Type**

Format the title according to the page design.

---

### Step 8 – Add border

Go to:

**General → Effects → Visual Border**

Enable and format the border.

---

# 41. Key Takeaways

1. **YoY Sales Growth** compares sales in the latest year with the previous year.
2. The latest year is dynamically identified using `MAX(Date)`.
3. The previous year is calculated as **maximum year − 1**.
4. The growth formula is:

$$
\frac{Current - Previous}{Previous}
$$

5. `IF()` prevents division by zero.
6. `BLANK()` is returned when previous-year sales are zero.
7. `VAR` makes complex DAX calculations easier to structure.
8. `Sales Type` provides the categories for the line chart.
9. The line chart uses:

   * **X-axis → Sales Type**
   * **Y-axis → YoY Sales Growth**
10. Power BI visuals can be significantly improved using:

* Shapes
* Background images
* Data labels
* Markers
* Smooth lines
* Borders
* Proper titles
* Consistent colors

### Final objective of this session

The cleaned housing dataset has now been transformed into the beginning of a **House Market Overview report**, with a DAX-based **Year-on-Year Sales Growth** metric and a formatted line chart showing that metric across the different **Sales Type** categories.
