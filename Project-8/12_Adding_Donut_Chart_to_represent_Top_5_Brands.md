# Power BI – Adding a Donut Chart to Represent Top 5 Brands by Number of Varieties

## 1. Objective of the Session

In this session, the objective is to add a **Donut Chart** to the existing Power BI report page.

The donut chart will represent:

> **Top 5 brands having the highest number of varieties**

The chart will show the brands and the number of distinct varieties/titles associated with each brand.

---

# 2. Reusing the Existing Bar Chart

Instead of creating a new visual from scratch, the existing bar chart is copied and modified.

### Steps

1. Select the existing **bar chart** on the report canvas.
2. Copy it using:

   * `Ctrl + C`
3. Paste it using:

   * `Ctrl + V`
4. Move the copied chart slightly downward.
5. Resize the copied chart as required.

The copied chart will initially contain the same fields and filters as the original bar chart.

---

# 3. Remove Existing Visual-Level Filter

The copied chart inherits the filters from the original visual.

Therefore, the existing **visual-level filter** needs to be removed before configuring the new chart.

### Steps

1. Select the newly copied bar chart.
2. Expand the **Filters pane**.
3. Locate the existing visual-level filter.
4. Remove the filter from the newly created chart.

---

# 4. Remove Existing Fields from the Chart

The copied chart currently contains fields from the previous visualization.

These fields need to be removed.

### Steps

1. Expand the **Visualizations pane**.
2. In the chart's field buckets:

   * Remove **Brand** from the **Y-axis** bucket.
   * Remove **Average Discount Percentage** from the **X-axis** bucket.

The chart is now ready to be configured for the new requirement.

---

# 5. Add Brand to the Chart

The objective is to analyze the brands having the highest number of varieties.

### Steps

1. Expand the **Data pane**.
2. Locate the **Brand** column.
3. Double-click the **Brand** column or drag it.
4. Drag and drop **Brand** into the **Y-axis** bucket.

The brands will now appear on the chart.

---

# 6. Add Title to Count Varieties

To determine the number of varieties for each brand, the **Title** column is used.

### Steps

1. Locate the **Title** column in the Data pane.
2. Double-click **Title** or drag it.
3. Drag and drop **Title** into the **X-axis** bucket.
4. Power BI will initially apply an aggregation such as **Count**.
5. Open the aggregation dropdown for the Title field.
6. Change the aggregation from **Count** to:

> **Distinct Count**

### Why Distinct Count?

Distinct Count ensures that the chart counts the unique titles/varieties rather than simply counting every row.

Thus, the chart represents the number of distinct varieties associated with each brand.

---

# 7. Apply a Top 5 Filter on Brand

At this stage, the chart contains all brands.

The requirement is to display only the **top five brands**.

### Steps

1. Keep the newly created bar chart selected.
2. Expand the **Filters pane**.
3. From the **Data pane**, select **Brand**.
4. Drag and drop **Brand** into:

> **Filters on this visual**

5. Click the filtering type, which is initially **Basic filtering**.
6. Change the filter type to:

> **Top N / Top**

7. Set the number of items to:

> **Top 5**

---

# 8. Determine the Top 5 Based on Distinct Count of Title

Simply selecting Top 5 brands is not enough.

The Top 5 must be determined based on the **number of distinct varieties/titles**.

### Steps

1. Locate the **Title** column.
2. Drag and drop **Title** into the relevant **Add data fields here** section under the visual filter.
3. Open the dropdown associated with Title.
4. Change the aggregation to:

> **Distinct Count**

5. Make sure to click:

> **Apply filter**

### Result

Power BI now filters the chart to display only the **five brands having the highest distinct count of titles/varieties**.

---

# 9. Convert the Bar Chart into a Donut Chart

Once the required data and filter configuration is complete, the bar chart can be converted into a donut chart.

### Steps

1. Select the newly created bar chart.
2. Go to the **Visualizations pane**.
3. Select the **Donut Chart** visualization.

Power BI converts the existing visual into a donut chart using the configured data.

---

# 10. Format the Donut Chart – Legend Position

The next step is to improve the appearance of the donut chart.

### Steps

1. Select the donut chart.
2. Click:

> **Format Your Visual**

3. Locate **Legends**.
4. Change the legend position.

The lecture demonstrates trying different positions, including:

* Bottom right
* Top left
* Center left
* Center right

The instructor ultimately chooses a suitable position based on how the chart looks.

---

# 11. Display Detailed Labels on the Donut Chart

Instead of relying on the legend to identify the brands, the brand names can be displayed directly on the donut chart.

### Steps

1. With the donut chart selected, open **Format Your Visual**.
2. Locate **Detail labels**.
3. Scroll down within the Detail labels settings.
4. Locate the **Values** section.
5. Under **Label contents**, several options are available, such as:

   * Data value
   * Percentage
   * Other available label information
6. Select:

> **All detail labels**

This causes the chart to display more complete information directly on the donut chart.

---

# 12. Turn Off the Legend

Once the brand names and other details are displayed directly on the donut chart, the legend is no longer necessary.

In fact, keeping the legend may create unnecessary confusion or duplication.

### Steps

1. Scroll back to the **Legend** settings.
2. Change the legend setting to:

> **Off**

### Result

The donut chart now displays the relevant brand names directly through the detail labels, without requiring a separate legend.

---

# 13. Collapse the Filters Pane

After completing the filtering configuration:

1. Collapse the **Filters pane** to provide more workspace on the report canvas.

---

# 14. Change the Donut Chart Title

The default title should be changed to clearly describe the insight represented by the visual.

### Steps

1. Select the donut chart.
2. Go to the **Format Your Visual** pane.
3. Open:

> **General**

4. Locate:

> **Title**

5. Enter the title:

> **Top 5 Brands by Highest Number of Varieties**

The title clearly communicates what the visualization represents.

---

# 15. Further Format the Donut Chart

Additional formatting can be applied to improve the appearance of the donut chart.

### Steps

1. Collapse the current panes if required.
2. Select the donut chart again.
3. Expand the **Visualizations pane**.
4. Open **Format Your Visual**.
5. Locate the relevant donut chart formatting options.

---

# 16. Adjust Donut Chart Spacing

The spacing between elements of the donut chart can be adjusted.

### Steps

1. Under the formatting options, scroll down to the relevant settings.
2. Adjust the **Spacing** setting.
3. Reduce the spacing if necessary to make the chart more compact.

---

# 17. Adjust the Inner Radius

The size of the empty space in the center of the donut can also be changed.

This is controlled by the **Inner radius** setting.

### Steps

1. Locate **Inner radius** in the formatting options.
2. Increase the inner radius as required.
3. Observe the appearance of the donut chart.
4. Keep the setting at a value that provides a visually appropriate donut shape.

The instructor increases the inner radius and concludes that the resulting appearance looks fine.

---

# 18. Final Cleanup

After formatting:

1. Collapse the **Visualizations pane**.
2. Collapse the **Data pane**.
3. Review the final donut chart on the report canvas.

The report now contains a donut chart showing the **top five brands based on the highest number of distinct varieties**.

---

# 19. Complete Workflow at a Glance

The entire process can be summarized as:

**Existing Bar Chart**
↓
**Copy & Paste (`Ctrl+C`, `Ctrl+V`)**
↓
**Move and Resize Chart**
↓
**Remove Existing Visual-Level Filter**
↓
**Remove Brand from Y-axis**
↓
**Remove Average Discount Percentage from X-axis**
↓
**Add Brand → Y-axis**
↓
**Add Title → X-axis**
↓
**Change Title aggregation → Distinct Count**
↓
**Add Brand → Filters on this visual**
↓
**Change Basic filtering → Top**
↓
**Select Top 5**
↓
**Add Title to the Top filter's value field**
↓
**Change Title → Distinct Count**
↓
**Click Apply filter**
↓
**Convert Bar Chart → Donut Chart**
↓
**Format Legend position**
↓
**Enable All detail labels**
↓
**Turn Legend Off**
↓
**Change Title**
↓
**Adjust Spacing**
↓
**Increase Inner Radius**
↓
**Collapse panes**

---

# 20. Key Concepts Learned

### Donut Chart

A donut chart is useful for showing how different categories contribute to a whole. Here, it is used to compare the top five brands based on their number of varieties.

### Distinct Count

**Distinct Count** counts unique values rather than counting every occurrence.

In this visualization:

> **Distinct Count of Title = Number of unique varieties/titles**

### Top N Filtering

Top N filtering allows the visual to display only the highest-ranking categories.

Here:

> **Top 5 Brands = Five brands with the highest distinct count of titles**

### Visual-Level Filtering

A visual-level filter affects only the selected visual rather than the entire report/page.

### Detail Labels

Detail labels allow information such as category names, values, percentages, etc., to be displayed directly on a visual.

### Inner Radius

For a donut chart, the inner radius controls the size of the hole in the center.

Increasing it makes the donut ring thinner and the center hole larger.

---

# Final Output

The final report page contains a **Donut Chart** titled:

> **Top 5 Brands by Highest Number of Varieties**

The chart displays the **five brands with the highest number of distinct varieties/titles**, with detailed labels shown directly on the chart and the legend turned off for a cleaner presentation.
