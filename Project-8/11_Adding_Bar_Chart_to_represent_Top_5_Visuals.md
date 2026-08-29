# Power BI – Details Page: Creating Top 5 Brands by Average Discount

## 1. Objective of the Session

In this session, the first analytical visual is added to the **Details** report page.

The objective is to create a **bar chart** showing:

> **Top 5 brands that have offered the highest average discount percentage.**

The session covers:

* Creating a bar chart
* Adding Brand and Discount Percentage
* Changing aggregation from Sum to Average
* Applying a Top 5 filter
* Applying conditional formatting using a gradient
* Customizing colors using hex codes
* Removing gridlines and axis values
* Formatting axis labels
* Adding data labels
* Formatting the chart title
* Formatting the legend
* Adding a border and shadow
* Formatting the existing company scroller
* Sorting the chart by Brand or Average Discount Percentage

---

# 2. Correct the Company Name in the Scroller

Before creating the new visual, the instructor makes a small correction to the text displayed in the existing Scroller.

### Steps

1. Select the existing **Scroller**.
2. Expand the **Visualizations** pane.
3. Click **Format Visual**.
4. Correct the company name/text if necessary.
5. The spelling is corrected to:

**Solutions**

The instructor then collapses the Scroller.

---

# 3. Create the Bar Chart

The first visual to be added is a **bar chart**.

### Objective

The chart should show:

> **Top 5 Brands by Highest Average Discount Percentage**

### Steps

1. Click on a **blank area of the report canvas**.
2. From the Visualizations pane, select the **Stacked Bar Chart**.
3. Power BI creates a blank bar chart.
4. Resize the chart.
5. Position it appropriately on the Details page.

---

# 4. Add Brand to the Y-Axis

The Brand field will be used as the category.

### Steps

1. Select the newly created bar chart.
2. Expand the **Data pane**.
3. Expand the **T Shirt** table.
4. Locate **Brand**.
5. Drag and drop **Brand** into the:

**Y-axis**

bucket.

The brands now appear along the vertical axis.

---

# 5. Add Discount Percentage to the X-Axis

The Discount Percentage column created in the previous DAX session will be used as the numerical value.

### Steps

1. Locate **Discount Percentage** in the T Shirt table.
2. Drag and drop it into the:

**X-axis**

bucket.

Power BI initially aggregates the field as:

> **Sum of Discount Percentage**

But this is not what is required.

---

# 6. Change Discount Percentage from Sum to Average

The requirement is to find the brands with the **highest average discount**, not the highest total discount.

### Steps

1. In the X-axis field bucket, locate **Discount Percentage**.
2. Click its dropdown arrow.
3. Change the aggregation from:

**Sum**

to:

**Average**

Now the chart represents:

> **Average Discount Percentage by Brand**

This is an important step because using Sum would produce a different result.

---

# 7. Apply a Top 5 Filter

At this point, the chart may contain many brands.

The requirement is specifically to display only the **top five brands**.

### Steps

1. Expand the **Filters pane**.
2. Make sure the bar chart is selected.
3. In the Filters pane, locate the section for:

**Filters on this visual**

4. Add **Brand** to the filter area.

You can do this by double-clicking Brand or dragging it into the appropriate filter bucket.

---

# 8. Change Brand Filter to Top N

The default filtering mode is basic filtering.

It needs to be changed to **Top N** filtering.

### Steps

1. Locate the Brand filter under **Filters on this visual**.
2. Change the filtering type from:

**Basic filtering**

to:

**Top N**

3. Select:

**Top**

4. Enter:

**5**

This means that Power BI should return only the top five brands.

---

# 9. Define What "Top" Means

Power BI now needs to know which measure should be used to determine the top five brands.

The requirement is:

> Top 5 based on Average Discount Percentage.

### Steps

1. In the Top N filter, locate the **By value** section.
2. Add **Discount Percentage**.
3. Make sure its aggregation is:

**Average**

The filtering logic is therefore:

```text
Top 5 Brands
       ↓
Based on
       ↓
Average Discount Percentage
```

---

# 10. Apply the Top 5 Filter

This is an important step.

Simply configuring the Top N filter does not complete the filtering process.

### Steps

1. Click:

**Apply filter**

2. Power BI applies the Top 5 filtering condition.

The chart now displays only:

> **The five brands with the highest average discount percentage.**

---

# 11. Verify the Top 5 Chart

After applying the filter, the chart represents:

> **Top 5 brands by highest average discount percentage**

This confirms that:

* Brand is being used as the category.
* Discount Percentage is being averaged.
* Only five brands are displayed.

---

# 12. Remove the Chart Background

The instructor now begins formatting the visual.

### Steps

1. Collapse the Filters pane.
2. Select the bar chart.
3. Click **Format your visual**.
4. Go to:

**General → Effects**

5. Locate **Background**.
6. Turn the background:

**Off**

This allows the chart to blend with the report's background design.

---

# 13. Apply Conditional Formatting to the Bars

The instructor wants the bars to have a gradient based on the average discount percentage.

### Purpose

The color intensity of the bars will represent the value of the average discount percentage.

Higher/lower values will receive different colors.

---

## Steps

1. Select the bar chart.
2. Go to:

**Format your visual → Visual**

3. Under **Bars**, scroll down.
4. Locate:

**Conditional Formatting**

5. Click **Conditional Formatting**.
6. Select the appropriate **Effects** option.
7. Choose:

**Gradient**

---

# 14. Set the Conditional Formatting Field to Average Discount Percentage

The gradient should be based on the same metric used to determine the Top 5 brands.

### Steps

1. In the conditional formatting settings, locate the field used for the gradient.
2. Select **Discount Percentage**.
3. Make sure the aggregation is:

**Average**

Do not leave it as Sum.

The final logic is:

```text
Bar Color
   ↓
Average Discount Percentage
   ↓
Gradient
```

---

# 15. Set the Lowest Value Color

The instructor uses an Excel sheet containing the project's predefined color codes.

### Steps

1. Open the Excel sheet containing the color codes.
2. Locate the color referred to as:

**Visual Light**

3. Copy its hex/color code.
4. Return to Power BI.
5. In the conditional formatting settings, select:

**Lowest Value Color**

6. Click **More Colors**.
7. Paste the copied color code.
8. Click **OK**.

The lowest values in the gradient now use the selected light visual color.

---

# 16. Set the Highest Value Color

The highest values receive the darker visual color.

### Steps

1. Select:

**Highest Value Color**
2. Click **More Colors**.
3. Open the Excel color reference again.
4. Locate:

**Visuals Dark**
5. Copy the corresponding color code.
6. Return to Power BI.
7. Paste the color code.
8. Click **OK**.

The gradient now transitions between:

> **Visual Light → Visual Dark**

based on the Average Discount Percentage.

---

# 17. Remove Gridlines

The instructor does not want gridlines displayed in the chart.

### Steps

1. Select the bar chart.
2. Open the visual formatting options.
3. Locate **Gridlines**.
4. Find the **Vertical Gridlines** option.
5. Turn it:

**Off**

This gives the chart a cleaner appearance.

---

# 18. Turn Off X-Axis Values

The instructor does not want numerical values displayed along the horizontal X-axis because data labels will be used instead.

### Steps

1. Open the **X-axis** formatting options.
2. Locate **Values**.
3. Turn **Values**:

**Off**

---

# 19. Turn Off X-Axis Title

The X-axis title is also unnecessary.

### Steps

1. In the X-axis settings, locate **Title**.
2. Turn it:

**Off**

The numerical information will instead be communicated through the data labels.

---

# 20. Format the Y-Axis

The Y-axis contains the Brand names.

The instructor does not want a separate axis title.

### Steps

1. Open **Y-axis** settings.
2. Locate **Title**.
3. Turn the title:

**Off**

The brand names themselves remain visible.

---

# 21. Format Y-Axis Values

The brand names are then formatted.

### Font

1. Under Y-axis **Values**, locate the font settings.
2. Select a suitable font style.

### Font Size

The instructor increases the font size to:

**50**

### Color

The color is changed to the project's dark visual color.

### Steps

1. Click **Color**.
2. Click **More Colors**.
3. Use the dark color from the Excel color-reference sheet.
4. Paste the corresponding hex code.
5. Apply the color.

---

# 22. Make Y-Axis Values Bold

The instructor then makes the brand labels bold.

### Steps

1. Remain under the Y-axis value settings.
2. Change the text style to:

**Bold**

This makes the brand names more prominent.

---

# 23. Adjust Maximum Width

The instructor also checks the **Maximum Width** setting.

The value is increased to:

**50%**

However, the instructor notes that this does not make a noticeable difference in this particular case.

This setting can still be adjusted depending on the length of the category labels.

---

# 24. Turn On Data Labels

Since the X-axis values are hidden, the actual discount percentages need to be displayed directly on the bars.

### Steps

1. Select the bar chart.
2. Open **Data Labels**.
3. Turn:

**Data Labels → On**

The values now appear directly on the bars.

---

# 25. Format Data Labels

The data labels are then customized.

### Steps

1. Expand the **Data Labels** settings.
2. Scroll down to the **Values** settings.
3. Change the font style to your preferred font.
4. Change the text color to the project's dark visual color.

To use the color:

1. Open the Excel color sheet.
2. Copy the dark visual color.
3. Return to Power BI.
4. Click **More Colors**.
5. Paste the color code.

---

# 26. Increase Data Label Size

The default data-label font size is approximately:

**9**

The instructor increases it to:

**50**

The labels are also made bold and italic.

### Final styling

* Font size → **50**, later adjusted to **55**
* Bold → **On**
* Italic → **On**
* Color → Dark visual color

The instructor finally keeps the data label size at approximately:

**55**

---

# 27. Increase Y-Axis Font Size Further

The instructor also adjusts the Y-axis values to match the data-label sizing.

### Final setting

**Y-axis values → 55**

This creates consistency between:

* Brand names
* Discount percentage labels

---

# 28. Create and Format the Chart Title

The chart needs a descriptive title.

### Steps

1. Select the bar chart.
2. Go to:

**Format your visual → General → Title**

3. Turn the title on if necessary.
4. Replace the title text with:

**Top Five Brands by Average Discount Percentage**

The title communicates exactly what the chart represents.

---

# 29. Format the Chart Title

The title is customized.

### Font Size

Set the title font size to:

**60**

The instructor tries to increase it further, but Power BI does not allow a larger size in this configuration.

### Font

Choose the desired font style.

### Color

Use the appropriate project color from the Excel reference sheet.

### Style

The title is formatted as:

* **Bold**
* **Italic**
* Underlined as demonstrated
* Horizontally aligned

The exact alignment shown in the lecture is kept as the chosen horizontal alignment.

---

# 30. Format the Legend

The instructor then formats the chart legend.

### Steps

1. Collapse the Title settings.
2. Go to:

**Visual → Legends**

3. Open the legend text settings.

---

# 31. Change Legend Font Size

The legend font size is changed to:

**50**

### Steps

1. Locate the legend text settings.
2. Set the font size to **50**.
3. Choose a suitable font style.

---

# 32. Change Legend Color

The instructor uses the **Visual Light** color for the legend.

### Steps

1. Click **Colors**.
2. Click **More Colors**.
3. Open the Excel color-reference sheet.
4. Locate **Visual Light**.
5. Copy its color code.
6. Return to Power BI.
7. Paste the code.
8. Apply the color.

---

# 33. Change Legend Position

The legend position is changed.

The available positioning can be adjusted from something such as:

**Top Left**

to:

**Bottom Right**

The instructor selects:

**Bottom Right**

This places the legend in the lower-right area of the visual.

---

# 34. Add a Border to the Chart

The instructor adds an outer border to the chart.

### Steps

1. Select the bar chart.
2. Go to:

**Format your visual → General → Effects**

3. Locate **Border**.
4. Turn the border:

**On**

5. Open the Border Color setting.
6. Select the desired **Visual Light** color from the project's Excel color reference.

The chart now has a visible outline.

---

# 35. Add a Shadow to the Chart

A shadow is also added to improve the visual appearance.

### Steps

1. Stay under:

**General → Effects**
2. Turn **Shadow** on.
3. Expand the Shadow settings.
4. Click **Color**.
5. Select the same light color used for the legend.
6. Apply the color.

The instructor then collapses the Shadow settings.

---

# 36. Format the Existing Scroller

The instructor also makes a small formatting change to the company name displayed in the Scroller.

### Steps

1. Select the existing Scroller.
2. Click the text/company name.
3. Open **Format your visual**.
4. Locate the Scroller text color setting.
5. Change the text color.
6. Use the **Visual Light** color.

The instructor considers the light color to be the better choice and keeps it.

---

# 37. Collapse the Data Pane

After completing the formatting:

1. Collapse the **Data pane**.
2. This gives a cleaner workspace for continuing with the report design.

The first analytical visual on the Details page is now complete.

---

# 38. Sorting the Chart

The instructor also demonstrates that the chart can be sorted in different ways.

The chart can be sorted by:

1. **Brand**
2. **Average Discount Percentage**

Each can be sorted in:

* Ascending order
* Descending order

---

# 39. Sort by Brand – Descending

### Steps

1. Select the chart.
2. Click the **three dots (...)** in the top-right corner of the visual.
3. Select:

**Sort axis**

4. Choose:

**Brand**

5. Select:

**Descending**

The brands are now sorted in descending alphabetical order.

---

# 40. Sort by Brand – Ascending

To change the Brand sorting:

1. Click the chart's **three dots (...)**.
2. Select **Sort axis**.
3. Select **Brand**.
4. Choose:

**Sort ascending**

The brands are now displayed in ascending alphabetical order.

---

# 41. Sort by Average Discount Percentage

The chart can instead be sorted according to the metric being analyzed.

### Steps

1. Click the chart's **three dots (...)**.
2. Select **Sort axis**.
3. Choose:

**Average Discount Percentage**

This sorts the chart according to the average discount values.

---

# 42. Sort Average Discount Percentage in Ascending Order

### Steps

1. Select:

**Sort axis → Average Discount Percentage**
2. Choose:

**Ascending**

The brands will now be ordered from lower average discount to higher average discount.

The instructor leaves the chart in ascending order at the end of the lecture.

---

# 43. Sorting Options Summary

| Sort By                     | Order      |
| --------------------------- | ---------- |
| Brand                       | Ascending  |
| Brand                       | Descending |
| Average Discount Percentage | Ascending  |
| Average Discount Percentage | Descending |

The choice depends on what the report designer wants the user to focus on.

---

# 44. Final Bar Chart Configuration

The completed visual represents:

> **Top 5 Brands by Average Discount Percentage**

### Data configuration

| Property        | Value                       |
| --------------- | --------------------------- |
| Chart Type      | Stacked Bar Chart           |
| Category/Y-axis | Brand                       |
| Value/X-axis    | Discount Percentage         |
| Aggregation     | Average                     |
| Filter          | Top N                       |
| N               | 5                           |
| Top N based on  | Average Discount Percentage |

---

# 45. Final Formatting Configuration

| Element                | Setting                                        |
| ---------------------- | ---------------------------------------------- |
| Background             | Off                                            |
| Conditional Formatting | Gradient                                       |
| Gradient Metric        | Average Discount Percentage                    |
| Lowest Value Color     | Visual Light                                   |
| Highest Value Color    | Visual Dark                                    |
| Vertical Gridlines     | Off                                            |
| X-axis Values          | Off                                            |
| X-axis Title           | Off                                            |
| Y-axis Title           | Off                                            |
| Y-axis Font Size       | 55                                             |
| Y-axis Font Style      | Bold                                           |
| Data Labels            | On                                             |
| Data Label Font Size   | 55                                             |
| Data Labels            | Bold + Italic                                  |
| Data Label Color       | Visual Dark                                    |
| Chart Title            | Top Five Brands by Average Discount Percentage |
| Title Size             | 60                                             |
| Title                  | Bold + Italic + Underlined                     |
| Legend Size            | 50                                             |
| Legend Color           | Visual Light                                   |
| Legend Position        | Bottom Right                                   |
| Border                 | On                                             |
| Border Color           | Visual Light                                   |
| Shadow                 | On                                             |
| Shadow Color           | Visual Light                                   |

---

# 46. Important DAX Column Used

The chart uses the **Discount Percentage** calculated column created in the previous session.

Its underlying calculation was:

```DAX
Discount Percentage =
DIVIDE(
    'T Shirt'[Mark Price] - 'T Shirt'[Sales Price],
    'T Shirt'[Mark Price]
) * 100
```

For this visual, Power BI calculates the **average of this column by brand**.

Conceptually:

```text
For each Brand
       ↓
Calculate Discount Percentage for its products
       ↓
Calculate Average Discount Percentage
       ↓
Rank Brands
       ↓
Select Top 5
```

---

# 47. Important Concept: Sum vs. Average

One of the most important points in this lecture is changing the Discount Percentage aggregation from **Sum** to **Average**.

### Incorrect for this requirement

```text
Sum of Discount Percentage
```

This would add the discount percentages across all products belonging to a brand.

### Correct for this requirement

```text
Average Discount Percentage
```

This tells us the average discount offered by each brand.

Therefore, when the requirement says:

> "Brands with the highest average discount"

the field must use:

**Average**, not **Sum**.

---

# 48. Important Concept: Top N Filtering

The Top N filter is applied at the **visual level**.

The logic is:

```text
Brand
  ↓
Top N filter
  ↓
Top 5
  ↓
Based on Average Discount Percentage
  ↓
Apply Filter
```

This is different from simply sorting the entire dataset.

The filter actually removes all brands except the five qualifying brands from the visual.

---

# 49. Important Concept: Conditional Formatting

Conditional formatting is used to make the bars visually communicate the values.

The gradient is based on:

> **Average Discount Percentage**

Therefore:

* Lower average discount → lighter color
* Higher average discount → darker color

This makes it easier to visually compare the five brands.

---

# 50. Important Concept: Data Labels Instead of X-Axis Values

The instructor intentionally turns off:

**X-axis Values**

because the values are shown directly on the bars using:

**Data Labels**

This produces a cleaner visual and prevents duplicate information from appearing.

---

# 51. Color Management Using Excel

Throughout the lecture, an Excel sheet is used as a reference for the project's color palette.

The workflow is:

```text
Excel Color Sheet
       ↓
Locate required color
       ↓
Copy Hex Code
       ↓
Power BI
       ↓
More Colors
       ↓
Paste Hex Code
       ↓
Apply
```

Colors referenced include:

* **Visual Light**
* **Visual Dark**

Using a predefined color palette helps maintain consistency across the report.

---

# 52. Complete Workflow

```text
Existing Details Page
        ↓
Correct Scroller Text
        ↓
Create Stacked Bar Chart
        ↓
Add Brand → Y-axis
        ↓
Add Discount Percentage → X-axis
        ↓
Change Sum → Average
        ↓
Filters on This Visual
        ↓
Add Brand
        ↓
Basic Filtering → Top N
        ↓
Top = 5
        ↓
By Value → Discount Percentage
        ↓
Aggregation → Average
        ↓
Apply Filter
        ↓
Top 5 Brands Identified
        ↓
Format Visual
        ↓
Background → Off
        ↓
Conditional Formatting → Gradient
        ↓
Based on Average Discount Percentage
        ↓
Set Light/Dark Colors
        ↓
Gridlines → Off
        ↓
X-axis Values → Off
        ↓
X-axis Title → Off
        ↓
Y-axis Title → Off
        ↓
Format Y-axis Values
        ↓
Data Labels → On
        ↓
Format Data Labels
        ↓
Add/Format Title
        ↓
Format Legend
        ↓
Add Border
        ↓
Add Shadow
        ↓
Format Scroller Text
        ↓
Collapse Data Pane
        ↓
Visual Completed
        ↓
Optional: Sort by Brand or Average Discount
```

# 53. Key Takeaways

### 1. Use Average when analyzing average discount

The requirement is not to find brands with the largest total discount. It is specifically to find brands with the **highest average discount percentage**.

### 2. Use Top N filtering

For a requirement such as:

> "Show the top 5 brands"

use:

**Filters on this visual → Top N → 5 → By Value → Average Discount Percentage → Apply filter**

### 3. Conditional formatting can communicate magnitude

A gradient based on Average Discount Percentage makes higher and lower values visually distinguishable.

### 4. Data labels can replace axis values

Turning off the X-axis values while enabling Data Labels creates a cleaner bar chart.

### 5. Formatting is part of report design

The lecture demonstrates customization of:

* Background
* Colors
* Fonts
* Font sizes
* Borders
* Shadows
* Gridlines
* Titles
* Legends
* Data labels
* Axis labels

### 6. Sorting is independent of Top N filtering

After selecting the Top 5 brands, you can still decide how those five brands should be ordered:

* By Brand ascending
* By Brand descending
* By Average Discount ascending
* By Average Discount descending

### 7. Keep report-wide colors consistent

Using the same **Visual Light** and **Visual Dark** colors across the Scroller, chart, legend, border, shadow, and gradient helps maintain a consistent report theme.

---

# 54. Final Result

The Details page now contains its **first analytical visual**:

> **Top Five Brands by Average Discount Percentage**

The visual allows the report user to immediately identify the five brands that provide the highest average discounts and compare their average discount percentages visually.

The session ends with this chart completed, and the next session will add **additional charts to the Details page**.
