# Power BI Notes: Creating a Bar Chart for Average Price by Clarity Grade

## 1. Objective of the Session

The next visualization recommended in the PDF/report is:

> **Price by Clarity Grade**

The objective is to create a **bar chart** showing the **average diamond price for each clarity grade**.

The same DAX measure created earlier is reused:

```DAX id="3k7pm"
Average Price = AVERAGE(diamonds[price])
```

There is **no need to create this measure again** because it already exists.

---

# 2. Required Fields

The visual requires two things:

| Field           | Purpose                                            |
| --------------- | -------------------------------------------------- |
| `Clarity`       | Category used to group the diamonds                |
| `Average Price` | Numerical measure displayed on the horizontal axis |

The desired relationship is:

**Clarity Grade → Average Price**

---

# 3. Step 1 — Add a Bar Chart

Open the existing Power BI report in **Power BI Desktop**.

### Process

1. Go to the report page.
2. Click on a **blank area of the canvas**.
3. From the Visualizations pane, select the **Stacked Bar Chart** visual.
4. A blank bar chart will be created.
5. Position it in the desired location on the report page.
6. Resize it as required.

The instructor places the chart in the available space and increases its size.

---

# 4. Step 2 — Add Average Price to the X-Axis

The objective is to represent **Average Price along the horizontal axis**.

### Process

1. Locate the `Average Price` measure.
2. Drag and drop it into the **X-axis** field/bucket.

The horizontal axis will now represent the average price.

Conceptually:

```text
X-Axis → Average Price
```

---

# 5. Step 3 — Add Clarity to the Y-Axis

Since the requirement is **Average Price by Clarity Grade**, the `Clarity` column needs to be used as the category.

### Process

1. Locate the `Clarity` column in the Data/Fields pane.
2. Drag and drop it into the **Y-axis** field/bucket.

So the final configuration is:

```text
X-Axis → Average Price
Y-Axis → Clarity
```

The resulting chart displays a horizontal bar for each clarity grade.

---

# 6. Understanding the Chart

The chart now answers:

> **What is the average diamond price for each clarity grade?**

The clarity grades are represented vertically, while the average prices extend horizontally.

Conceptually:

```text
Clarity       Average Price
   D          ███████████
   E          █████████
   F          ████████████
   G          █████████████
   H          █████████
   I          ███████████
   J          ██████████
```

The actual bar lengths depend on the dataset.

---

# 7. Step 4 — Change the Bar Color

The default bar color can be customized.

### Process

1. Select the bar chart.
2. Open **Format your visual**.
3. Locate the **Bars** formatting section.
4. Choose the color option.
5. Select the desired color.

The instructor chooses one color, but **any suitable color can be selected** depending on the report's design/theme.

---

# 8. Step 5 — Turn Data Labels On

Data labels are useful because they display the actual average-price value directly on the bars.

### Process

1. Select the chart.
2. Open **Format your visual**.
3. Select **Data labels**.
4. Turn **Data labels → On**.

The numerical values will now appear on the bars.

---

# 9. Step 6 — Change Data Label Text Color

The transcript specifically changes the data-label text color to black.

### Process

1. Keep **Data labels** selected.
2. Go to the **Values** settings within the data-label formatting.
3. Find the text/color setting.
4. Change the color to **Black**.

This improves readability of the displayed values.

---

# 10. Step 7 — Format the Chart Title

The chart title can also be customized.

### Process

1. Select the chart.
2. Open **Format your visual**.
3. Go to **General**.
4. Locate **Title**.
5. Change the **horizontal alignment** to:

**Center**

This centers the title above the chart.

---

## Font Style

The transcript also mentions that the font style can be changed.

If required:

1. Go to the title formatting options.
2. Locate the font settings.
3. Select a suitable font style.

The exact font is a matter of personal/report-design preference.

---

# 11. Step 8 — Remove the Y-Axis Title

The instructor does not want separate axis titles displayed because the chart is already clear from its context.

### Process

1. Select the chart.
2. Open **Format your visual**.
3. Go to **Y-axis**.
4. Locate **Title**.
5. Change it to:

**Off**

The Y-axis title will disappear.

---

# 12. Step 9 — Remove the X-Axis Title

The same process is performed for the horizontal axis.

### Process

1. Go to **X-axis**.
2. Locate **Title**.
3. Change it to:

**Off**

Now neither axis displays a separate title.

---

# 13. Step 10 — Hide the X-Axis Values

The transcript also turns off the numerical values displayed along the horizontal axis.

### Process

1. Select **X-axis**.
2. Locate the setting for the axis **values/labels**.
3. Change it to:

**Off**

This removes the numerical tick values from the horizontal axis.

### Why?

The actual average-price values are already being displayed through the **Data Labels**, so the horizontal-axis numbers are not considered necessary in this design.

---

# 14. Step 11 — Format the Y-Axis Values

The clarity grades are still required because they identify each bar.

Therefore, the Y-axis values remain visible.

The instructor changes their color to black.

### Process

1. Select **Y-axis**.
2. Locate the text/value formatting option.
3. Change the color to:

**Black**

---

# 15. Step 12 — Increase Y-Axis Text Size

The clarity-grade labels can also be made larger.

### Process

1. Select **Y-axis**.
2. Locate the text-size setting.
3. Increase the size as required.

The goal is simply to make the clarity grades easy to read.

---

# 16. Step 13 — Add a Border

The visual can be enhanced with a border.

### Process

1. Select the bar chart.
2. Open **Format your visual**.
3. Go to **General**.
4. Open **Effects**.
5. Find **Border**.
6. Turn the border **On**.

This gives the chart a clearer boundary.

---

# 17. Step 14 — Add a Shadow

A shadow is also added to improve the visual appearance.

### Process

1. Stay under **General → Effects**.
2. Locate **Shadow**.
3. Turn **Shadow → On**.
4. Open the shadow settings.
5. Change the shadow color if desired.

The instructor chooses a light/white-toned option described as:

**White 30% darker**

This produces a softer appearance than a standard dark black shadow.

---

# 18. Step 15 — Collapse the Panes

After completing the formatting, the instructor collapses the unnecessary panes to get a cleaner view of the report.

The panes mentioned are:

* **Filters pane**
* **Visualizations pane**
* **Data pane**

Collapsing these gives more room to inspect the completed report page and its visuals.

---

# 19. Final Chart Configuration

The final bar chart is configured approximately as follows:

| Setting           | Configuration                       |
| ----------------- | ----------------------------------- |
| Visual            | Stacked Bar Chart                   |
| X-axis            | Average Price                       |
| Y-axis            | Clarity                             |
| Bar color         | Custom selected color               |
| Data labels       | On                                  |
| Data-label text   | Black                               |
| Title alignment   | Center                              |
| Y-axis title      | Off                                 |
| X-axis title      | Off                                 |
| X-axis values     | Off                                 |
| Y-axis values     | Visible                             |
| Y-axis text color | Black                               |
| Y-axis text size  | Increased as required               |
| Border            | On                                  |
| Shadow            | On                                  |
| Shadow color      | White 30% darker                    |
| Position          | Adjusted according to report layout |

---

# 20. Overall Workflow

For quick revision, remember the complete process:

```text
PDF Recommendation
       ↓
Price by Clarity Grade
       ↓
Use existing Average Price measure
       ↓
Insert Stacked Bar Chart
       ↓
Average Price → X-axis
       ↓
Clarity → Y-axis
       ↓
Change bar color
       ↓
Turn Data Labels ON
       ↓
Set data-label text to black
       ↓
Center chart title
       ↓
Turn Y-axis title OFF
       ↓
Turn X-axis title OFF
       ↓
Turn X-axis values OFF
       ↓
Format Y-axis values
       ↓
Add Border
       ↓
Add Shadow
       ↓
Collapse unnecessary panes
       ↓
Final Average Price by Clarity chart
```

---

# 21. Key Learning Points

### 1. Bar chart orientation

Because a **Stacked Bar Chart** is being used:

* **X-axis → numerical measure**
* **Y-axis → categorical field**

Therefore:

```text
Average Price → X-axis
Clarity → Y-axis
```

This produces **horizontal bars**.

---

### 2. Reusing an existing DAX measure

There is no need to create a separate measure for every visual.

The existing:

```DAX id="j8x4p"
Average Price = AVERAGE(diamonds[price])
```

can be reused across multiple visuals, including:

* Card
* Heat map
* Bar chart
* Other appropriate visuals

---

### 3. Data labels can replace axis values

In this design, the instructor turns off the X-axis values because the actual values are already displayed using **Data Labels**.

This reduces visual clutter.

---

### 4. Formatting improves report readability

The chart is not considered complete merely after placing the fields.

Additional formatting is performed:

* Bar color
* Data labels
* Text color
* Title alignment
* Axis titles
* Axis values
* Text size
* Border
* Shadow
* Visual positioning

These formatting steps make the report more polished and easier to read.

---

# 22. Final Insight Being Represented

The purpose of this visual is to represent:

> **Average Diamond Price by Clarity Grade**

So the report user can visually compare the average price associated with each clarity category.

The final chart complements the previously created visuals and contributes another KPI/insight to the overall **diamond analysis report page**.
