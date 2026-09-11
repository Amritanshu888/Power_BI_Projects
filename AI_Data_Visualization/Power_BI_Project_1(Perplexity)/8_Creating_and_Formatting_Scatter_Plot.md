# Power BI — Creating a Carat vs Price Scatter Plot

## 1. Objective of the Session

In the previous session, a **Card visual** was created to represent:

> **Average Depth Percentage**

In this session, the next visual recommended in the PDF is created.

The objective is to represent the **relationship between Carat and Price** of diamonds.

The recommended visual is a:

> **Scatter Plot / Scatter Chart**

Unlike the previous visuals, **no DAX measure is required** for this chart.

The existing columns from the Diamonds table can be used directly.

---

# 2. Recommended Visualization

The PDF recommends creating a scatter plot to show the relationship between:

* **Carat**
* **Price**

The recommended configuration is:

| Scatter Plot Component | Field |
| ---------------------- | ----- |
| X-axis                 | Carat |
| Y-axis                 | Price |

Therefore:

```text
Carat  → X-axis
Price  → Y-axis
```

### Why a Scatter Plot?

A scatter plot is useful for understanding the **relationship/correlation between two numerical variables**.

Here, we want to see how diamond:

> **Carat size**

relates to:

> **Price**

Each point in the scatter plot represents a combination of carat and price values.

---

# 3. No DAX Required

An important point from the lecture is that **DAX is not needed** for this visual.

The reason is that we are directly using existing numerical columns:

```text
Carat
Price
```

We are not creating a new calculated KPI or measure.

The columns can therefore be directly placed into the appropriate chart buckets.

---

# 4. Create the Scatter Plot

## Step 1 — Go to Power BI Desktop

Open the Power BI Desktop report.

---

## Step 2 — Select a Blank Area

Click on an empty area of the report canvas.

This ensures that a new visual is created.

---

## Step 3 — Select Scatter Chart

From the Visualizations pane, locate the **Scatter Chart** icon.

You can also search for the visual if necessary.

Click the Scatter Chart icon.

Power BI will create a:

> **Blank Scatter Plot**

on the canvas.

---

## Step 4 — Resize the Visual

Resize the newly created scatter plot according to the available space on the report page.

Use the edges/corners of the visual to adjust its size.

---

# 5. Add Carat to the X-Axis

The first field required is:

> **Carat**

### Steps

1. Locate the **Carat** column in the Data pane.
2. Double-click it or drag it.
3. Place it into the:

**X-axis**

bucket.

The horizontal axis will now represent **Carat**.

---

# 6. Change Carat to "Don't Summarize"

Power BI may automatically try to aggregate numerical columns.

For this scatter plot, the instructor does **not** want the Carat values to be summarized.

### Steps

1. Look at the **Carat** field inside the X-axis bucket.
2. Click the dropdown arrow next to the field.
3. Change the aggregation from its current setting to:

> **Don't summarize**

This ensures that Power BI uses the individual Carat values rather than calculating something such as:

* Sum of Carat
* Average of Carat
* Minimum Carat
* Maximum Carat

---

# 7. Add Price to the Y-Axis

The next field is:

> **Price**

### Steps

1. Locate the **Price** column in the Data pane.
2. Double-click it or drag it.
3. Place it into the:

**Y-axis**

bucket.

The vertical axis will now represent **Price**.

---

# 8. Change Price to "Don't Summarize"

Just like Carat, Power BI may automatically summarize the Price column.

The instructor does not want this.

### Steps

1. Locate the **Price** field in the Y-axis bucket.
2. Click the dropdown arrow.
3. Select:

> **Don't summarize**

Now the chart is configured as:

```text
X-axis → Carat → Don't summarize
Y-axis → Price → Don't summarize
```

The scatter plot will display the individual Carat–Price observations.

---

# 9. Basic Scatter Plot Structure

At this point, the chart represents:

```text
                 Price
                   ↑
                   │
                   │       •
                   │    •
                   │  •    •
                   │ •  •
                   │
                   └────────────────→ Carat
```

Each dot represents an observation from the dataset.

The chart can therefore be used to visually understand whether larger-carat diamonds generally tend to have higher prices.

---

# 10. Format the Scatter Plot

Once the basic chart has been created, the instructor proceeds to formatting.

Select the scatter plot and open:

**Format your visual**

---

# 11. Gridlines

The instructor discusses the gridlines.

For this chart, the gridlines are considered useful because they help users interpret the numerical positions of the points.

Therefore:

> **Gridlines are retained.**

This is different from the earlier column chart, where unnecessary gridlines were removed.

### Important principle

Gridlines don't always have to be removed.

Whether they should be displayed depends on whether they improve readability.

For a scatter plot with numerical X and Y axes, gridlines can help users estimate the values of individual points.

---

# 12. Axis Titles

The instructor initially considers the default titles for:

* Horizontal axis
* Vertical axis

The default axes represent:

```text
Horizontal → Carat
Vertical → Price
```

However, the instructor decides to create a more suitable overall chart title rather than relying only on the axis titles.

---

# 13. Create a Custom Chart Title

Go to:

**General → Title**

Enable/use the title settings.

Instead of leaving the title as the default, enter:

### `Carat versus Price`

So the chart title becomes:

> **Carat versus Price**

This clearly communicates the relationship being displayed.

---

# 14. Center Align the Chart Title

Within the title settings, find:

**Horizontal Alignment**

Change it to:

> **Center**

This places the chart title in the center of the visual.

The title is already black, so the instructor keeps the color as it is.

---

# 15. Format the Visual Border

Next, the overall visual container is formatted.

Go to:

**General → Effects**

Find:

**Border**

Change it to:

> **On**

This adds a border around the scatter plot.

---

# 16. Enable the Shadow

Still under:

**General → Effects**

find:

**Shadow**

Change it to:

> **On**

The visual now has a shadow effect.

---

# 17. Change the Shadow Color

Click/open the **Shadow** settings.

The instructor chooses:

> **White — 30% darker**

This gives the chart a subtle shadow effect.

This formatting is consistent with the formatting applied to the other visuals created earlier.

---

# 18. Format the X-Axis Values

The X-axis represents:

> **Carat**

The instructor wants the values on this axis to appear in black.

### Steps

Go to:

**Format your visual → X-axis**

Find:

**Values**

Change the color to:

> **Black**

This controls the appearance of the numerical values displayed along the horizontal axis.

---

# 19. Format the X-Axis Title

Still under the X-axis settings, locate:

**Title**

The title color can also be changed.

The instructor notes that you can choose an appropriate color according to your preference.

In this case, it is already:

> **Black**

So it can be left as it is.

---

# 20. Format the Y-Axis Values

The Y-axis represents:

> **Price**

Go to:

**Format your visual → Y-axis**

Under:

**Values**

change the color to:

> **Black**

This formats the numerical values displayed along the vertical axis.

---

# 21. Format the Y-Axis Title

Under:

**Y-axis → Title**

you can change the title color.

The instructor observes that it is already black.

Therefore, no change is necessary.

However, the user can choose another color if it matches the dashboard theme.

---

# 22. Font Customization

The lecture also points out that formatting isn't limited to color.

You can customize the:

> **Font**

for the relevant text elements according to your preference.

This can include the appropriate axis/title text depending on the available formatting options in the Power BI version being used.

The important idea is that Power BI allows further customization of the visual's typography.

---

# 23. Final Configuration

The final scatter plot can be summarized as follows:

| Element            | Configuration      |
| ------------------ | ------------------ |
| Visual             | Scatter Chart      |
| X-axis             | Carat              |
| X-axis aggregation | Don't summarize    |
| Y-axis             | Price              |
| Y-axis aggregation | Don't summarize    |
| DAX                | Not required       |
| Gridlines          | Kept/visible       |
| Chart title        | Carat versus Price |
| Title alignment    | Center             |
| Border             | On                 |
| Shadow             | On                 |
| Shadow color       | White, 30% darker  |
| X-axis values      | Black              |
| X-axis title       | Black              |
| Y-axis values      | Black              |
| Y-axis title       | Black              |
| Font               | Can be customized  |

---

# 24. Complete Step-by-Step Workflow

For revision, remember the complete workflow:

```text
Open PDF
       ↓
Find "Carat vs Price" recommendation
       ↓
No DAX required
       ↓
Go to Power BI Desktop
       ↓
Click blank area on canvas
       ↓
Select Scatter Chart
       ↓
Resize visual
       ↓
Carat → X-axis
       ↓
Carat → Don't summarize
       ↓
Price → Y-axis
       ↓
Price → Don't summarize
       ↓
Format your visual
       ↓
Keep gridlines
       ↓
General → Title
       ↓
Title → "Carat versus Price"
       ↓
Horizontal Alignment → Center
       ↓
General → Effects
       ↓
Border → On
       ↓
Shadow → On
       ↓
Shadow → White, 30% darker
       ↓
X-axis → Values → Black
       ↓
X-axis → Title → Black
       ↓
Y-axis → Values → Black
       ↓
Y-axis → Title → Black
       ↓
Customize font if required
       ↓
Final Scatter Plot
```

---

# 25. Key Concepts to Remember

### Scatter Plot

A scatter plot is primarily used to examine the **relationship between two numerical variables**.

Here:

```text
Carat ↔ Price
```

The chart can help identify whether there appears to be a positive relationship between diamond size and price.

---

### Don't Summarize

This is an important Power BI setting demonstrated in the lecture.

When a numerical column is added to a visual, Power BI may automatically apply an aggregation such as:

```text
Sum
Average
Minimum
Maximum
Count
```

Selecting:

> **Don't summarize**

tells Power BI to use the individual values rather than aggregating them.

For this scatter plot:

```text
Carat → Don't summarize
Price → Don't summarize
```

This is important when you want the individual observations represented as points.

---

# 26. Dashboard Formatting Pattern

This lecture also continues the formatting style established in the previous visuals.

The report is consistently using:

* Borders
* Shadows
* Center-aligned titles
* Black axis text
* Clean visual presentation
* Appropriate use of gridlines

The goal is not merely to create a technically correct chart, but to make the **entire report page visually consistent and professional**.

---

## Final Takeaway

The key workflow from this lecture is:

> **No DAX → Create Scatter Chart → Carat on X-axis → Price on Y-axis → Don't Summarize both → Keep useful gridlines → Add "Carat versus Price" title → Center the title → Add border and shadow → Format axis values/titles.**

This scatter plot is particularly useful because, unlike the KPI cards and distribution charts created earlier, it focuses on **exploring the relationship between two continuous numerical variables**.
