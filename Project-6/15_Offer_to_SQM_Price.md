# Power BI – Offer-to-Square-Meter Ratio by Sales Type

## 1. Objective of the Session

In this session, the **last visual on the report page** is created.

The objective is to calculate and visualize the:

> **Offer Price to Square Meter Area Ratio**

for different **Sales Types**.

The process involves:

1. Creating a new DAX measure.
2. Using the `DIVIDE()` function to calculate the ratio.
3. Creating a **Stacked Bar Chart**.
4. Showing the ratio for different Sales Types.
5. Formatting the axes, data labels, bars, title, and border.
6. Reviewing the completed report.

---

# 2. Create the Offer-to-Square-Meter Ratio Measure

The required ratio is not directly available in the dataset, so a **measure** needs to be created.

### Steps

1. Go to the **Measures table**.
2. Right-click on the Measures table.
3. Select **New Measure**.
4. Wait for the formula bar to load.
5. Expand the formula bar if required.

The measure is named:

**Offer to SQM Ratio**

Here, **SQM** refers to **Square Meter Area**.

---

# 3. DAX Formula for the Ratio

The lecture uses the `DIVIDE()` function.

The logic is:

```DAX
Offer to SQM Ratio =
DIVIDE(
    SUM('Housing'[Offer Price]),
    SUM('Housing'[Area in Square Meter])
)
```

> Use the actual column names from your Housing table if they differ.

### Understanding the formula

The calculation is essentially:

**Offer-to-SQM Ratio = Total Offer Price ÷ Total Area in Square Meters**

### Components

#### Numerator

```DAX
SUM('Housing'[Offer Price])
```

This calculates the total/sum of **Offer Price**.

#### Denominator

```DAX
SUM('Housing'[Area in Square Meter])
```

This calculates the total/sum of the **square-meter area**.

#### DIVIDE()

```DAX
DIVIDE(Numerator, Denominator)
```

performs the division safely.

---

# 4. Why Use `DIVIDE()`?

Instead of directly using `/`, Power BI's `DIVIDE()` function is useful when creating ratios because it handles division more safely, particularly when the denominator could be zero or blank.

The basic structure is:

```DAX
DIVIDE(
    Numerator,
    Denominator
)
```

In this case:

```text
Offer Price
     ÷
Square Meter Area
     ↓
Offer-to-SQM Ratio
```

After entering the formula:

**Press Enter.**

The new measure is created.

---

# 5. Create the Stacked Bar Chart

The requirement is to represent the **Offer-to-SQM Ratio for different Sales Types**.

### Steps

1. Click on a **blank area of the report canvas**.
2. From the Visualizations pane, select **Stacked Bar Chart**.
3. Power BI creates a blank bar chart.
4. Resize and position the chart appropriately.

---

# 6. Add the Ratio to the Chart

The newly created **Offer to SQM Ratio** measure needs to be added to the chart.

### Steps

1. Select the Stacked Bar Chart.
2. Add **Offer to SQM Ratio** as the chart's value.

This tells Power BI that the numerical value represented by the bars should be the calculated ratio.

---

# 7. Add Sales Type

The requirement is to compare the ratio across different **Sales Types**.

### Steps

1. Locate the **Sales Type** field.
2. Select/check the Sales Type field.
3. Add it to the appropriate category/axis field of the bar chart.

The final chart represents:

```text
Sales Type
     ↓
Offer to SQM Ratio
```

So each bar corresponds to a different Sales Type and shows its corresponding offer-to-square-meter ratio.

---

# 8. Format the Y-Axis

After creating the visual, the instructor begins formatting the chart.

### Steps

1. Select the bar chart.
2. Click **Format Visual**.
3. Open the **Y-axis** settings.

The instructor does not want to display an unnecessary axis title.

Therefore:

* Turn the **Y-axis title Off**.

The axis values can then be formatted according to preference.

### Formatting the values

The instructor adjusts:

* Font
* Font size
* Font weight
* Text color

The demonstrated settings include:

* **Bold** text
* **Gray** text

---

# 9. Format the X-Axis

Next, the X-axis is formatted.

### Steps

1. Collapse the **Y-axis** settings.
2. Expand the **X-axis** settings.
3. Turn off the unnecessary axis elements.

The lecture specifically says:

* Do not show the **values**.
* Do not show the **title**.

The goal is to rely on the **data labels** to display the ratio values directly on the bars.

So the chart has a cleaner appearance.

---

# 10. Enable Data Labels

Because the X-axis values are being hidden, the ratio needs to be displayed directly on the bars.

### Steps

1. Scroll down in the formatting pane.
2. Locate **Data labels**.
3. Turn **Data labels → On**.

The values will now appear directly on the bars.

Conceptually:

```text
Sales Type A  █████████████  1250
Sales Type B  █████████      950
Sales Type C  ███████████    1100
```

The exact values depend on the dataset.

---

# 11. Format the Data Labels

The instructor then further formats the labels.

### Steps

1. Click on **Data labels**.
2. Scroll down to the relevant **Values** formatting options.
3. Change the value/text color.
4. Reduce the text size if required.
5. Choose an appropriate font style.

The demonstrated formatting includes:

* **Dark gray** text
* Reduced font size
* Font style of your choice

This makes the labels readable without overwhelming the chart.

---

# 12. Change the Bar Color

Next, the appearance of the bars is changed.

### Steps

1. Go to the formatting options for the **Bars**.
2. Locate the **Visual/Data color** option.
3. Choose a suitable color.

The instructor tries different colors and decides that the **previous color looks better**.

So the final color can be kept according to the overall report theme.

---

# 13. Change the Chart Title

The chart title is then customized.

### Steps

1. Select the bar chart.
2. Go to **Format Visual**.
3. Open **General**.
4. Open **Title**.
5. Enter the desired title.

The instructor uses the concept:

**Offer to Ratio by Sales Type**

This makes the purpose of the chart clear to the report user.

---

# 14. Format the Chart Title

After entering the title, additional formatting is applied.

The instructor changes:

### Font style

The title can be made **Italic**.

### Alignment

The title is **centered**.

### Text color

The text color is changed to **Gray**.

So the title formatting is approximately:

```text
Offer to Ratio by Sales Type
        ↑
     Centered
     Italic
     Gray
```

---

# 15. Add a Border to the Chart

The instructor then adds a border around the completed bar chart.

### Steps

1. Select the bar chart.
2. Click **Format Visual**.
3. Go to **General**.
4. Open **Effects**.
5. Turn **Border → On**.

This adds a visible border around the visual.

---

# 16. Change the Border Color

The default border color is initially black.

The instructor changes it to gray.

### Steps

1. Open the **Visual Border** settings.
2. Locate the border color.
3. Change the color from **Black → Gray**.

This makes the border consistent with the rest of the visual formatting.

---

# 17. Final Chart Configuration

The completed visual can be summarized as follows:

| Component         | Configuration                   |
| ----------------- | ------------------------------- |
| Visual            | Stacked Bar Chart               |
| Measure           | Offer to SQM Ratio              |
| Category          | Sales Type                      |
| Ratio calculation | Offer Price ÷ Square Meter Area |
| Y-axis title      | Hidden                          |
| Y-axis values     | Formatted                       |
| X-axis title      | Hidden                          |
| X-axis values     | Hidden                          |
| Data labels       | On                              |
| Data label color  | Dark Gray                       |
| Data label size   | Reduced                         |
| Bar color         | Customized                      |
| Chart title       | Offer to Ratio by Sales Type    |
| Title style       | Italic                          |
| Title alignment   | Center                          |
| Title color       | Gray                            |
| Border            | On                              |
| Border color      | Gray                            |

---

# 18. Complete DAX + Visual Workflow

The entire process can be remembered as:

```text
Measures Table
      ↓
Right-click
      ↓
New Measure
      ↓
Create Offer to SQM Ratio
      ↓
DIVIDE(
    SUM(Offer Price),
    SUM(Square Meter Area)
)
      ↓
Press Enter
      ↓
Blank Area on Canvas
      ↓
Insert Stacked Bar Chart
      ↓
Values → Offer to SQM Ratio
      ↓
Category/Axis → Sales Type
      ↓
Format Y-Axis
      ↓
Format X-Axis
      ↓
Turn Data Labels ON
      ↓
Format Data Labels
      ↓
Change Bar Color
      ↓
General → Title
      ↓
Set "Offer to Ratio by Sales Type"
      ↓
Italic + Center + Gray
      ↓
General → Effects → Border ON
      ↓
Border Color → Gray
```

---

# 19. Important Concepts from the Session

### Measure vs. Column

The **Offer to SQM Ratio** is created as a **measure** because it is an aggregated calculation:

```DAX
SUM(Offer Price) / SUM(Square Meter Area)
```

The result can dynamically change according to the filter context, such as Sales Type.

### Ratio Calculation

The key business metric is:

**Offer Price per Square Meter = Offer Price ÷ Area in Square Meters**

This allows the report user to compare different Sales Types on a common basis rather than simply comparing their total offer prices.

### Data Labels

When axis values are hidden, **Data Labels** become especially important because they allow users to see the actual ratio directly on each bar.

### Formatting

The instructor demonstrates several important Power BI formatting techniques:

* Axis formatting
* Hiding axis titles
* Hiding axis values
* Data labels
* Label formatting
* Bar colors
* Chart title formatting
* Text alignment
* Font style
* Background/visual styling
* Borders
* Border colors

---

# 20. Report Status at the End of the Session

At this point, the report has **two pages**.

The instructor mentions that **additional pages may be added later**, but the current session focuses on completing the last visual on the current report page.

The final visual added to the page is the:

> **Offer-to-SQM Ratio by Sales Type Stacked Bar Chart**

This completes the visual discussed in this session.
