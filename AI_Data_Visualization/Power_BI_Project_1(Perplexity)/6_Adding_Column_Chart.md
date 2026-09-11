# Power BI — Creating a Distribution of Cut Grades Chart

## 1. Objective of the Session

In the previous session, a **Card visual** was created to represent a KPI.

In this session, the goal is to create another visual based on the recommendations provided in the PDF.

The PDF recommends creating a KPI/measure that represents:

> **Distribution of Cut Grades**

The measure is designed to identify/count diamonds based on a particular **cut category**, specifically where the diamond's **cut is "Ideal"**.

The resulting measure can then be represented visually using a:

* Stacked Bar Chart, or
* Column Chart

The lecture chooses a **Stacked Column Chart**.

---

# 2. Create the DAX Measure

The first step is to create a DAX measure that calculates the required distribution.

### Step 1 — Open the PDF

Go to the PDF containing the recommended KPIs and charts.

Locate the DAX expression provided for:

**Distribution of Cut Grades**

The DAX expression is intended to find the row count for diamonds where:

```text
Cut = "Ideal"
```

Copy the DAX expression from the PDF.

---

## Step 2 — Go to Power BI Desktop

Open the Power BI Desktop report.

In the **Data/Fields pane**, locate the table being used for measures.

In this example, the lecture uses the:

**Measures table**

### Step 3 — Create a New Measure

Right-click on the **Measures table**.

Select:

**New Measure**

A DAX formula bar will appear.

Paste the DAX expression copied from the PDF.

---

## Step 4 — Name the Measure

The PDF provides the name of the KPI/measure.

Use:

### `Distribution of Cut Grades`

So the measure should be created with the appropriate DAX expression and this name.

Then press:

**Enter**

The measure is now available in the Measures table.

---

# 3. Create the Column Chart

The next step is to visually represent the measure.

The PDF recommends either:

* Stacked Bar Chart
* Column Chart

The instructor chooses a **Stacked Column Chart**.

---

## Step 1 — Select a Blank Area

Click on an empty/blank area of the Power BI report canvas.

This ensures that a new visual is created instead of modifying an existing visual.

---

## Step 2 — Select Stacked Column Chart

From the Visualizations pane, select:

**Stacked Column Chart**

A blank column chart will appear on the canvas.

Resize the chart as required.

---

# 4. Add the Distribution Measure

The newly created measure needs to be added to the chart.

### Step 1

Find:

**Distribution of Cut Grades**

in the Data/Fields pane.

### Step 2

Drag and drop the measure into the chart's:

**Y-axis / Y-axis values bucket**

Depending on the Power BI version, this area may be labelled **Y-axis** or **Y-axis values**.

This determines the numerical value represented by the height of each column.

---

# 5. Add Color as the Category

The instructor wants to show the distribution according to **diamond color**.

### Step 1

Find the:

**Color**

field in the Data pane.

### Step 2

Drag and drop **Color** into the:

**X-axis**

bucket.

The resulting chart now represents:

> **Distribution of Cut Grades by Color**

For example, the X-axis contains the different diamond color categories such as:

* D
* E
* F
* G
* H
* etc.

The Y-axis represents the value calculated by the **Distribution of Cut Grades** measure.

---

# 6. Resize the Visual

After adding the fields, the chart can be resized.

Click and drag the edges/corners of the visual to make it appropriately sized for the report page.

The goal is to ensure that:

* The chart fits properly within the dashboard.
* The labels are readable.
* The visual is aligned with the other visuals.

---

# 7. Formatting the Chart

After creating the chart, the next step is to format it so that it looks cleaner and more professional.

Select the chart and open:

**Format your visual**

---

# 8. Turn on the Border

Navigate to:

**General → Effects**

Find:

**Border**

Change it to:

**On**

This adds a border around the visual.

---

# 9. Turn on the Shadow

Still under:

**General → Effects**

Find:

**Shadow**

Change it to:

**On**

The chart will now have a shadow effect.

---

## Change Shadow Color

Click on the **Shadow** settings.

The lecture changes the shadow color to:

> **White — 30% darker**

This gives the visual a subtle shadow effect while keeping the overall design clean.

---

# 10. Remove Y-Axis Values

The instructor decides that the numerical values displayed along the vertical axis are not necessary.

Select the chart and go to:

**Format your visual → Y-axis**

Find:

**Values**

Change it to:

**Off**

This removes the numerical labels from the Y-axis.

---

# 11. Remove the Y-Axis Title

Still under:

**Y-axis**

find:

**Title**

Change it to:

**Off**

This removes the title associated with the vertical axis.

This makes the chart cleaner because the purpose of the axis is already understood from the visual context.

---

# 12. Remove Gridlines

Next, the horizontal gridlines are removed.

Go to the appropriate **Gridlines** settings under the visual formatting options.

The lecture notes that:

**Horizontal gridlines**

are already:

**Off**

Therefore, no further change is required.

### Purpose

Removing unnecessary gridlines gives the chart a cleaner dashboard appearance.

---

# 13. Collapse the Panes

After completing the formatting, the instructor collapses the:

* Filters pane
* Visualizations pane
* Data pane

This provides a clearer view of the final report page and allows you to see how the chart looks in the overall dashboard.

---

# 14. Change the Column Colors

The color of the bars/columns can also be customized.

### Step 1

Select the chart.

### Step 2

Open:

**Format your visual**

### Step 3

Find the settings related to:

**Columns / Data colors**

### Step 4

Open:

**Colors**

You can now choose an appropriate color for the columns.

The instructor changes the default color to another more suitable color.

### Important

The exact color isn't mandatory. The important point is to choose a color that:

* Fits the dashboard theme.
* Has sufficient contrast.
* Makes the data easy to read.

---

# 15. Add Data Labels

Initially, the numerical values on top of the columns are not visible.

To display them:

### Step 1

Select the chart.

### Step 2

Use:

**Add Data to your visual**

and then open:

**Format your visual**

### Step 3

Find:

**Data labels**

Change:

**Data labels → On**

The values will now appear directly on the columns.

---

# 16. Format Data Label Values

After enabling data labels, additional formatting options become available.

Expand:

**Data labels**

Scroll down to the **Values** settings.

The lecture changes the value color to:

> **Black**

This improves readability of the numbers displayed on the columns.

---

# 17. Format the Chart Title

Next, the chart title is formatted.

Go to:

**General → Title**

The instructor does **not** change the title itself.

Instead, the alignment is changed.

---

## Center Align the Title

Within the title settings:

Scroll down to:

**Horizontal Alignment**

Change the alignment to:

**Center**

This places the chart title in the center of the visual.

The instructor notes that this makes the chart look comparatively better.

---

# 18. Format the X-Axis Values

The X-axis contains the diamond color categories.

For example:

```text
D   E   F   G   H   ...
```

The instructor wants these labels to appear in black.

### Steps

Select the chart.

Go to:

**Format your visual → X-axis**

Find the:

**Color**

setting.

Change the color to:

**Black**

Now the category labels on the horizontal axis appear in black.

---

# 19. Format the X-Axis Title

The X-axis title can also be formatted.

Go to:

**X-axis → Title**

The instructor checks the title settings.

The title color is already:

**Black**

Therefore, no additional change is necessary.

---

# 20. Final Result

The final visual represents:

### **Distribution of Cut Grades by Color**

The chart contains:

* **X-axis:** Diamond Color
* **Y-axis:** Distribution of Cut Grades measure
* **Column chart:** Distribution/count represented for each color
* **Data labels:** Enabled
* **Y-axis values:** Hidden
* **Y-axis title:** Hidden
* **Gridlines:** Hidden
* **Border:** Enabled
* **Shadow:** Enabled
* **Shadow color:** White, 30% darker
* **Column color:** Customized
* **Data label color:** Black
* **Chart title:** Center aligned
* **X-axis label color:** Black

---

# 21. Complete Step-by-Step Workflow

For revision, the entire process can be remembered as:

```text
PDF Recommendation
       ↓
Copy DAX Expression
       ↓
Power BI Desktop
       ↓
Right-click Measures Table
       ↓
New Measure
       ↓
Paste DAX
       ↓
Name → Distribution of Cut Grades
       ↓
Enter
       ↓
Select Blank Canvas Area
       ↓
Stacked Column Chart
       ↓
Measure → Y-axis
       ↓
Color → X-axis
       ↓
Format Visual
       ↓
Border → ON
       ↓
Shadow → ON
       ↓
Shadow → White, 30% darker
       ↓
Y-axis Values → OFF
       ↓
Y-axis Title → OFF
       ↓
Gridlines → OFF
       ↓
Customize Column Color
       ↓
Data Labels → ON
       ↓
Data Label Values → Black
       ↓
Title → Center Align
       ↓
X-axis Color → Black
       ↓
X-axis Title → Black
```

---

# 22. Key Power BI Concepts from This Lecture

### Measure

A **measure** is a DAX calculation that dynamically calculates a value based on the current filter/context of the report.

Here, the measure is used to calculate the distribution of diamonds satisfying the required **cut condition**.

### Dimension / Category

**Color** acts as the category/dimension used to break down the measure.

Conceptually:

```text
Measure:
Distribution of Cut Grades

        ↓ broken down by ↓

Dimension:
Diamond Color
```

This allows us to compare the distribution across different diamond colors.

### Column Chart

A column chart is useful when comparing numerical values across discrete categories.

Here:

```text
Color → Category
Distribution → Numerical value
```

---

## Important Formatting Principle

The lecture demonstrates an important dashboard-design principle:

> **Not every piece of information needs to be displayed if it makes the visual unnecessarily crowded.**

For example:

* Y-axis values → removed
* Y-axis title → removed
* Gridlines → removed

But:

* Data labels → added

So the actual values remain visible directly on the columns without needing the Y-axis scale.

This produces a **cleaner and more dashboard-friendly visual**.

### Final takeaway

The overall process is:

**Create the DAX measure → create the column chart → assign measure and category → format the visual → remove unnecessary elements → add useful labels → align/style the chart for the dashboard.**
