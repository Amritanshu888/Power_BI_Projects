# Detailed Notes: Creating the Second KPI Visual — Monthly Transaction Amount

## 1. Overview of the Session

This session continues the **Power BI report creation** process.

In the previous session, the first KPI visual was created:

> **Number of Transactions by Transaction Type**

In this session, the instructor creates the **next KPI visual** from the Excel sheet that was prepared/recommended by Perplexity.

The second KPI is:

> **Monthly Transaction Amount**

The session covers:

* Understanding the KPI
* Creating the required DAX measure
* Creating an Area Chart
* Adding Transaction Date to the X-axis
* Displaying months
* Adding Monthly Transaction Amount to the Y-axis
* Formatting the chart
* Adding markers and data labels
* Formatting the title, axes, border, and shadow

---

# 2. KPI: Monthly Transaction Amount

The instructor first opens the Excel sheet containing the KPI recommendations.

The next KPI is:

> **Monthly Transaction Amount**

### Description

The purpose of this KPI is to:

> **Show the total transaction value grouped by different months.**

In other words, we want to understand how much money was transacted during each month.

For example:

| Month    | Transaction Amount |
| -------- | -----------------: |
| January  |                 ₹X |
| February |                 ₹Y |
| March    |                 ₹Z |
| April    |                 ₹A |

This allows us to observe how the transaction amount changes over time.

---

# 3. Recommended Visual

The Excel sheet suggests that this KPI can be represented using:

* **Line Chart**
* **Area Chart**

The instructor decides to use an:

> **Area Chart**

An area chart is useful for showing the trend of a numerical value over time while also emphasizing the magnitude of the values.

---

# 4. DAX Measure Required

The Excel sheet also provides the DAX measure required for this KPI.

The instructor copies the recommended DAX formula directly from the Excel sheet.

## Steps

1. Go to the Excel sheet.
2. Locate the DAX formula for:

   > **Monthly Transaction Amount**
3. Select the formula.
4. Press:

   > **Ctrl + A**
5. Press:

   > **Ctrl + C**

The formula is now copied.

---

# 5. Creating the Monthly Transaction Amount Measure

Return to:

> **Power BI Desktop**

The instructor uses the previously created **Measures table** to store this new measure.

## Steps

1. Locate:

   > **Measures table**
2. Right-click the table.
3. Select:

   > **New Measure**
4. Wait for the DAX formula bar to appear if necessary.
5. Press:

   > **Ctrl + A**
6. Press:

   > **Ctrl + V**
7. Paste the DAX formula copied from Excel.
8. The measure is named:

   > **Monthly Transaction Amount**
9. Press:

   > **Enter**

Power BI successfully creates the measure.

The instructor checks whether any error occurs.

> **No error occurs, and the measure is created successfully.**

---

# 6. Creating the Area Chart

After creating the measure, the instructor creates the visual.

## Steps

### Step 1: Click on a blank area

Click somewhere on an empty area of the report canvas.

This ensures that a new visual can be created rather than modifying the previously created chart.

### Step 2: Open the Visualizations pane

Expand the:

> **Visualizations pane**

### Step 3: Select Area Chart

The instructor identifies the **Area Chart** icon and clicks it.

Power BI creates a:

> **Blank Area Chart**

---

# 7. Positioning and Resizing the Chart

The instructor places the new chart on the report canvas.

Initially, it is positioned somewhere on the canvas and then resized.

The instructor notes that:

> The chart can be resized according to the requirements of the report layout.

The exact final position can be adjusted later when all the visuals have been added.

---

# 8. Adding Transaction Date to the X-Axis

The next step is to determine what should appear along the horizontal axis.

The dataset contains:

> **Transaction Date**

This field is used to represent the months.

## Steps

1. Expand the relevant dataset:

   > **Combined Banking Data Set**
2. Find:

   > **Transaction Date**
3. Double-click or drag and drop it into:

   > **X-axis**

The transaction date is now added to the horizontal axis.

---

# 9. Displaying Month Instead of Year, Quarter, and Day

When a date field is added to a visual, Power BI may automatically create a **date hierarchy** containing:

* Year
* Quarter
* Month
* Day

However, this KPI is specifically about **monthly transaction amounts**.

Therefore, the instructor does **not** want:

* Year
* Quarter
* Day

The visual should represent:

> **Month only**

---

## Steps

After adding Transaction Date to the X-axis:

1. Examine the date hierarchy in the X-axis bucket.
2. Remove the unwanted levels:

   * Year
   * Quarter
   * Day
3. Keep only:

   > **Month**

### Important concept

The goal is:

```text
Transaction Date
        ↓
      Month
        ↓
Monthly Transaction Amount
```

rather than displaying the full date hierarchy.

---

# 10. Expanding the Data Pane

The instructor expands the data pane slightly so that the required fields are easier to access.

This is simply a workspace adjustment to make the fields easier to select and drag into the visual.

---

# 11. Adding Monthly Transaction Amount to the Y-Axis

Now the numerical measure needs to be added to the chart.

## Steps

1. Expand:

   > **Measures table**
2. Find:

   > **Monthly Transaction Amount**
3. Double-click it or drag and drop it into:

   > **Y-axis**

The chart now displays:

> **Monthly Transaction Amount by Month**

---

# 12. Basic Structure of the Area Chart

The visual configuration is:

| Area Chart Bucket | Field                      |
| ----------------- | -------------------------- |
| **X-axis**        | Transaction Date → Month   |
| **Y-axis**        | Monthly Transaction Amount |

Conceptually:

```text
X-axis → Month
Y-axis → Monthly Transaction Amount
```

The area chart now shows the monthly transaction value over time.

---

# 13. Resizing the Chart

The instructor adjusts the size of the chart to make it more suitable for the report layout.

The chart can be resized by selecting it and adjusting its boundaries.

The exact dimensions are not finalized yet because additional charts will be added in later sessions.

---

# 14. Formatting the Area Chart

After creating the chart, the instructor starts formatting it.

The instructor selects the area chart and opens:

> **Format Your Visual**

This provides access to the formatting options.

---

# 15. Formatting the Y-Axis

The instructor does not want the Y-axis title and values to be displayed in the current design.

Therefore, the Y-axis is formatted accordingly.

## Steps

1. Open:

   > **Y-axis**
2. Change:

   > **Values → Off**
3. Change:

   > **Title → Off**

So both the Y-axis values and title are hidden.

### Why?

The instructor considers the axis information unnecessary for this particular visual design.

---

# 16. Formatting the X-Axis

The instructor also does not want an explicit X-axis title because it is already obvious that:

> **Months are being represented along the horizontal axis.**

Therefore, the X-axis title is turned off.

---

## X-Axis Value Formatting

The instructor also changes the appearance of the values displayed along the X-axis.

The following can be customized:

* Font style
* Color
* Font size

The instructor chooses a preferred font style.

The color is changed as desired, and the size is reduced.

The exact font is a personal design choice.

---

# 17. Formatting the Chart Title

Next, the instructor goes to:

> **General → Title**

The title's font style is changed.

The instructor:

* Changes the font style
* Keeps the color black
* Keeps the title center aligned

The title is therefore visually consistent with the desired report design.

---

# 18. Center Aligning the Title

Under the Title settings, the instructor ensures that the title is:

> **Center aligned**

This keeps the title visually balanced above the chart.

---

# 19. Adding a Border

The instructor then adds a border around the chart.

## Steps

1. Collapse the Title section if required.
2. Expand:

   > **Effects**
3. Find:

   > **Border**
4. Turn the border:

   > **On**

The chart now has a visible border.

---

# 20. Adding a Shadow

The instructor also adds a shadow effect.

## Steps

1. Under:

   > **Effects**
2. Find:

   > **Shadow**
3. Turn:

   > **Shadow → On**

This gives the chart a slightly elevated appearance.

---

# 21. Changing the Shadow Color

The instructor expands the Shadow settings.

Then:

1. Click:

   > **Color**
2. Select:

   > **White, 30% darker**

This creates a subtle shadow rather than an overly strong effect.

---

# 22. Changing the Area/Line Color

The instructor then customizes the actual color used by the chart.

The area chart is selected and the instructor returns to:

> **Visual**

The X-axis settings are collapsed to make room for other formatting options.

---

# 23. Formatting the Lines

The instructor expands:

> **Lines**

The default chart color is changed.

The instructor chooses a different color according to preference.

### Important

The exact color is not a required technical setting.

The important concept is that Power BI allows the visual's line/area appearance to be customized through the formatting pane.

---

# 24. Changing Interpolation Type

The instructor finds:

> **Interpolation Type**

It is initially:

> **Linear**

The instructor changes it to:

> **Smooth**

### Difference

**Linear:**

The line connects points using straight-line segments.

**Smooth:**

The line is visually smoothed between data points.

For this report, the instructor chooses:

> **Smooth**

---

# 25. Adding Markers

The instructor wants markers to be displayed for the individual monthly data points.

## Steps

1. Expand:

   > **Markers**
2. Scroll down if necessary.
3. Turn:

   > **Markers → On**

Markers now appear at the data points along the chart.

### Why use markers?

Markers make individual monthly points easier to identify on the chart.

For example:

```text
January ●
February ●
March ●
April ●
```

Instead of relying only on the continuous area/line.

---

# 26. Turning on Data Labels

The instructor notices that the actual numerical values are not currently visible.

Therefore, data labels are enabled.

## Steps

1. Scroll down in the formatting options.
2. Find:

   > **Data labels**
3. Turn:

   > **Data labels → On**

The numerical values are now displayed for the different months.

---

# 27. Formatting Data Label Values

After turning on data labels, the instructor expands:

> **Data labels**

Then goes to the values formatting options.

The instructor changes the value color to:

> **Black**

This makes the numerical labels easier to read.

---

# 28. Final Area Chart Configuration

The resulting visual represents:

> **Monthly Transaction Amount**

with:

### X-axis

> Month

### Y-axis

> Monthly Transaction Amount

### Chart type

> Area Chart

### Interpolation

> Smooth

### Markers

> On

### Data labels

> On

### Data label color

> Black

### Y-axis

* Values → Off
* Title → Off

### X-axis

* Title → Off
* Values formatted according to preference

### Title

* Center aligned
* Font customized
* Black
* Font style selected according to preference

### Effects

* Border → On
* Shadow → On
* Shadow color → White, 30% darker

---

# 29. Visuals Created So Far

At this point, two charts have been created based on the recommendations from Perplexity.

### Visual 1

**KPI:** Number of Transactions by Transaction Type

**Visual:** Pie Chart

```text
Legend → Transaction Type
Values → Count of Transactions
```

---

### Visual 2

**KPI:** Monthly Transaction Amount

**Visual:** Area Chart

```text
X-axis → Month
Y-axis → Monthly Transaction Amount
```

---

# 30. DAX Measures Created So Far

The dedicated **Measures table** now contains at least two measures.

### Measure 1

> **Count of Transactions**

Used for:

> Number of Transactions by Transaction Type

### Measure 2

> **Monthly Transaction Amount**

Used for:

> Monthly Transaction Amount

This demonstrates why having a dedicated Measures table is useful: as more KPIs are created, their DAX measures can all be stored in one organized location.

---

# 31. Complete Step-by-Step Workflow

Here's the entire process from the Excel recommendation to the finished visual.

### Step 1 — Open the Excel sheet

Review the KPI recommendations generated/provided by Perplexity.

### Step 2 — Identify the next KPI

> **Monthly Transaction Amount**

### Step 3 — Understand the KPI

It shows:

> **Total transaction value grouped by different months.**

### Step 4 — Select a visual

Recommended:

* Line Chart
* Area Chart

Selected:

> **Area Chart**

### Step 5 — Copy the DAX

Copy the recommended DAX formula from Excel using:

> **Ctrl + A → Ctrl + C**

### Step 6 — Open Power BI

Return to Power BI Desktop.

### Step 7 — Create a measure

Right-click:

> **Measures table → New Measure**

### Step 8 — Paste the DAX

Use:

> **Ctrl + A → Ctrl + V**

### Step 9 — Name the measure

> **Monthly Transaction Amount**

Press **Enter**.

### Step 10 — Create the Area Chart

Click a blank area of the canvas and select:

> **Area Chart**

### Step 11 — Add Transaction Date

From the Combined Banking Data Set:

> **Transaction Date → X-axis**

### Step 12 — Keep only Month

Remove:

* Year
* Quarter
* Day

Keep:

> **Month**

### Step 13 — Add the measure

From the Measures table:

> **Monthly Transaction Amount → Y-axis**

### Step 14 — Resize the chart

Adjust the chart dimensions as required.

### Step 15 — Format Y-axis

Set:

* Values → Off
* Title → Off

### Step 16 — Format X-axis

Set:

* Title → Off
* Customize font, color, and size of values as desired

### Step 17 — Format title

Under:

> **General → Title**

Customize:

* Font
* Color
* Alignment

Set:

> **Center aligned**

### Step 18 — Add border

Under:

> **Effects → Border**

Turn it:

> **On**

### Step 19 — Add shadow

Under:

> **Effects → Shadow**

Turn it:

> **On**

### Step 20 — Change shadow color

Select:

> **White, 30% darker**

### Step 21 — Format lines

Under:

> **Visual → Lines**

Change the chart color according to preference.

### Step 22 — Change interpolation

Change:

> **Linear → Smooth**

### Step 23 — Enable markers

Under:

> **Markers**

Turn:

> **On**

### Step 24 — Enable data labels

Turn:

> **Data labels → On**

### Step 25 — Format data labels

Change the values' color to:

> **Black**

---

# 32. Important Power BI Concepts

## Date Hierarchy

When a date field is added to a visual, Power BI can automatically create a hierarchy:

```text
Year
 └── Quarter
      └── Month
           └── Day
```

If the analysis requires only monthly data, unwanted levels can be removed so that the visual works at the **Month** level.

---

## X-axis vs. Y-axis

For this area chart:

### X-axis

Represents the dimension/category over which the trend is analyzed:

> **Month**

### Y-axis

Represents the numerical measure:

> **Monthly Transaction Amount**

---

## Data Labels

Data labels show the actual numerical values directly on the chart.

Without data labels, the user mainly sees the visual trend.

With data labels, the user can also see the actual values associated with individual months.

---

## Markers

Markers identify individual data points.

They are particularly useful when the chart contains multiple monthly observations.

---

## Interpolation

Interpolation controls how the chart connects data points.

### Linear

Straight connections between points.

### Smooth

A visually smoother connection between points.

The instructor chooses:

> **Smooth**

---

# 33. Key Takeaways

The most important things to remember from this lecture are:

1. The second KPI is **Monthly Transaction Amount**.
2. Its purpose is to show the **total transaction value by month**.
3. The recommended visuals are **Line Chart or Area Chart**.
4. The instructor chooses an **Area Chart**.
5. A dedicated measure is created:

   > **Monthly Transaction Amount**
6. The measure is stored in the existing:

   > **Measures table**
7. **Transaction Date** is placed on the X-axis.
8. Only **Month** is retained from the date hierarchy.
9. **Monthly Transaction Amount** is placed on the Y-axis.
10. Y-axis values and title are turned off.
11. X-axis title is turned off.
12. The chart title is center aligned.
13. Border and shadow are enabled.
14. Shadow color is set to **White, 30% darker**.
15. The line/area color is customized.
16. Interpolation is changed from **Linear to Smooth**.
17. **Markers are turned on**.
18. **Data labels are turned on**.
19. Data label values are changed to **black**.
20. More charts will be added in the upcoming sessions to complete the report.
