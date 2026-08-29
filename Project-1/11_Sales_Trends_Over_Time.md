# Power BI — Sales Trend Analysis Using Line Chart

## 1. Objective of the Requirement

In the previous lecture, **Top/Bottom 5 Analysis** was completed.

The next requirement from the requirements document is:

> **Represent the sales trend over time.**

The report should show how sales vary at different time levels:

* **Daily**
* **Monthly**
* **Quarterly**
* **Annually**

To achieve this, a **Line Chart** is used because line charts are well suited for showing trends over time.

---

# 2. Rename the Existing Report Page

The existing first page was being used for the Top/Bottom 5 analysis.

### Steps

1. Go to **Page 1** at the bottom of the Power BI report.
2. Double-click on the page name.
3. Press **Ctrl + A** to select the existing name.
4. Rename it to:

**Top Bottom Five Analysis**

This makes the purpose of the page clear.

---

# 3. Create a New Page for the Sales Trend

Since the sales trend is a separate requirement, it is better to create a separate report page.

### Steps

1. Click the **+ (Plus)** icon at the bottom of the Power BI report.
2. A new blank page will be created.
3. Double-click the new page name.
4. Rename it to:

**Overview**

This page will contain the sales trend and other overview-level insights that will be added later.

---

# 4. Select a Line Chart

The requirement is to show how sales change over a period of time.

For time-based trends, common visual choices include:

* Line chart
* Column chart

In this example, a **Line Chart** is selected.

### Steps

1. Click on a blank area of the report canvas.
2. From the **Visualizations** pane, select the **Line Chart**.
3. A blank line chart will appear on the canvas.
4. Resize the chart as required and position it appropriately on the report page.

---

# 5. Add Net Sales to the Y-Axis

The requirement is to analyze **sales**, so the `Net Sales` field is used as the value.

### Steps

1. Select the line chart.
2. Locate the **Net Sales** field in the Data pane.
3. Drag and drop **Net Sales** into the **Y-axis** bucket.

The Y-axis now represents the sales value.

Conceptually:

**Y-axis → Net Sales**

---

# 6. Add Date to the X-Axis

The trend needs to be analyzed over time, so the `Date` field is added to the X-axis.

### Steps

1. Locate the **Date** field in the Data pane.
2. Drag and drop **Date** into the **X-axis** bucket.

The chart now represents:

**X-axis → Date/Time**
**Y-axis → Net Sales**

Initially, Power BI may display the data at the **daily level**, depending on how the Date hierarchy is being used.

---

# 7. Understanding Power BI's Date Hierarchy

When the Date field is added to a visual, Power BI can provide a date hierarchy containing different levels of time.

The hierarchy allows us to analyze:

**Year → Quarter → Month → Day**

This is extremely useful for the current requirement because the requirement specifically asks for sales trends at different time levels.

---

# 8. Drill Up to Year Level

Initially, the chart may display detailed date-level information.

The lecture demonstrates using **Drill Up** to move toward higher-level aggregation.

### Steps

Click the **Drill Up** button repeatedly.

For example:

**Day → Month → Quarter → Year**

After drilling up to the highest level, the chart displays sales by year.

The dataset contains the following years:

* 2020
* 2021
* 2022
* 2023
* 2024

Therefore, the chart can now show the total Net Sales associated with each year.

---

# 9. Go to the Next Level in Hierarchy

Power BI also provides an option called:

**Go to the next level in the hierarchy**

This allows you to move down one hierarchy level.

### Example

If the current chart is showing:

**Year**

Clicking **Go to the next level in hierarchy** moves to:

**Quarter**

The chart will then display quarter-level information.

---

## Quarter-Level Analysis

At the quarter level, Power BI aggregates the data across the years.

For example:

* Q1 → Q1 data from all available years
* Q2 → Q2 data from all available years
* Q3 → Q3 data from all available years
* Q4 → Q4 data from all available years

So the chart is not necessarily showing Q1 of one particular year. It is showing the aggregation of Q1 across the available years when using the hierarchy-level navigation shown in the lecture.

---

# 10. Move from Quarter to Month

Click **Go to the next level in hierarchy** again.

The chart moves from:

**Quarter → Month**

Now the chart shows sales according to months.

For example:

* January
* February
* March
* ...
* August
* ...
* December

If you look at August, for example, the displayed value represents the August data across the years included in the current hierarchy context.

---

# 11. Move from Month to Day

Click **Go to the next level in hierarchy** once again.

The chart now moves to:

**Month → Day**

At this level, the sales trend can be viewed for individual dates.

Therefore, using the Date hierarchy, the same visual can represent trends at:

**Year → Quarter → Month → Day**

This satisfies the requirement of analyzing sales trends across different time periods.

---

# 12. Drill Down into a Specific Year

There are two related concepts that should be understood:

### Go to Next Level

This moves the entire visual to the next hierarchy level.

### Drill Down

This allows you to explore the next hierarchy level **for a particular data point/category**.

For example, suppose you want to investigate only **2023**.

### Steps

1. First, use **Drill Up** to return to the Year level.
2. Enable **Drill Down** using the drill-down option.
3. Select the **2023** data point.

Power BI will now drill into 2023 and show its lower-level details.

For example:

**2023 → Quarters**

You can now see:

* Q1
* Q2
* Q3
* Q4

---

# 13. Drill Further into a Specific Quarter

Suppose you want to investigate **Q2 of 2023**.

### Steps

1. With Drill Down enabled, select **Q2**.
2. Power BI moves to the next hierarchy level.
3. You can now see the different months belonging to Q2.

For example:

**Q2 → April, May, June**

This allows you to investigate the sales trend at a much more granular level.

---

# 14. Drill Further into a Specific Month

You can continue drilling down.

For example:

**2023 → Q2 → May → Individual Days**

### Steps

1. Select the required month.
2. Power BI moves to the next level in the Date hierarchy.
3. Individual dates for that month are displayed.
4. The line chart then shows the sales trend for those individual days.

This provides a detailed view of sales behavior within a particular month.

---

# 15. Return the Chart to Year Level

After exploring the different hierarchy levels, the report should be returned to the desired overview state.

### Steps

1. Use **Drill Up**.
2. Continue drilling up until the chart reaches the **Year** level.

The final overview chart should therefore show the sales trend by year.

---

# 16. Formatting the Chart Title

Once the basic visual is created, formatting is performed to make the report more professional.

### Steps

1. Select the line chart.
2. Open **Format your visual**.
3. Go to the **General** section.
4. Expand **Title**.
5. Replace the default title.

The title used in the lecture is:

**Sales Trends by Period**

The title can be customized according to the reporting requirement.

---

## Title Formatting

The lecture demonstrates several formatting options.

You can modify:

* Font
* Font size
* Bold
* Alignment
* Italic
* Underline

The demonstrated formatting includes:

* **Font:** Times New Roman
* Reduced/increased font size as required
* **Bold:** Enabled
* **Alignment:** Center
* Italic/underline can also be enabled if desired

The important idea is that the title should clearly communicate what the visual represents.

---

# 17. Turn Off the Y-Axis Values

The lecture chooses not to display the numeric values along the vertical axis and instead uses data labels.

### Steps

1. Select the line chart.
2. Open the **Format** pane.
3. Go to the **Y-axis** section.
4. Turn **Values** → **Off**.
5. Turn **Title** → **Off**.

This removes the Y-axis values/title from the visual.

---

# 18. Enable Data Labels

Since the Y-axis values have been hidden, the actual sales values can instead be displayed directly on the chart.

### Steps

1. In the Format pane, find **Data labels**.
2. Turn **Data labels** → **On**.
3. Expand the **Values** section under Data labels.

Now the sales values will be displayed directly against the data points.

---

# 19. Format Data Labels

The data labels can be customized for readability.

The lecture demonstrates:

* Changing the label color
* Increasing the font size
* Making the labels bold

### Example settings

**Color → Black**

**Font size → Increased**

**Font weight → Bold**

The exact size can be adjusted according to the visual's layout.

---

# 20. Format the X-Axis

The horizontal axis represents the time period.

### Steps

1. Expand the **X-axis / Horizontal axis** section.
2. Turn the **Title** → **Off**.

This removes the unnecessary X-axis title.

The values displayed along the X-axis can also be formatted.

The lecture demonstrates:

* **Bold:** Enabled
* **Color:** Black
* **Font size:** Increased

This makes the year/time values easier to read.

---

# 21. Remove Gridlines

Gridlines can sometimes make a visual look cluttered.

The lecture removes both horizontal and vertical gridlines.

### Steps

1. Select the line chart.
2. Open the formatting options.
3. Locate **Gridlines**.
4. Make sure **Horizontal gridlines** are **Off**.
5. Turn **Vertical gridlines** → **Off** as well.

This gives the chart a cleaner appearance.

---

# 22. Change the Line Color

The line itself can also be formatted.

### Steps

1. Select the line chart.
2. Go to the **Visual** formatting options.
3. Find the **Lines** section.
4. Expand it.
5. Locate **Color**.
6. Choose the desired color.

In the lecture, **purple** is selected as an example.

---

# 23. Change Line Style

Power BI also provides different line styles.

Possible styles include:

* Solid
* Dashed
* Dotted

### Steps

1. Go to **Lines**.
2. Locate **Line style**.
3. Select the desired style.

The lecture demonstrates:

* Dashed
* Dotted
* Solid

The final selection is:

**Solid**

---

# 24. Enable Markers

Markers can be added to make individual data points more visible.

### Steps

1. In the formatting options, locate **Markers**.
2. Turn **Markers** → **On**.

Markers will now appear on the line at the individual data points.

You can further customize:

* Marker color
* Marker size

The lecture reduces the marker size after enabling them.

---

# 25. Change the Interpolation Type

The line chart also provides an option to control how the line connects data points.

The lecture refers to this as the **Interpolation Type**.

Possible behavior includes:

* Smooth
* Step

### Smooth

A smooth line connects the data points with a smoother-looking curve.

### Step

The line changes in a step-like manner.

### Final setting in the lecture

**Interpolation Type → Smooth**

This gives the sales trend a smoother appearance.

---

# 26. Final Visual

After all the formatting and hierarchy configuration, the final line chart represents:

**Sales Trends by Period**

with:

* **Net Sales** on the Y-axis
* **Date hierarchy** on the X-axis
* Data labels enabled
* Y-axis values hidden
* X-axis title hidden
* Gridlines removed
* Customized line color
* Solid line
* Markers enabled
* Smooth interpolation
* Formatted title
* Formatted axis labels

---

# 27. Most Important Concept — Drill Up vs Drill Down

This lecture demonstrates an important Power BI concept.

| Feature                           | Purpose                                               |
| --------------------------------- | ----------------------------------------------------- |
| **Drill Up**                      | Move to a higher-level aggregation                    |
| **Go to Next Level in Hierarchy** | Move the entire visual to the next hierarchy level    |
| **Drill Down**                    | Explore lower-level details for a selected data point |

### Example hierarchy

**Year → Quarter → Month → Day**

### Drill Up

**Day → Month → Quarter → Year**

### Drill Down Example

Select:

**2023 → Q2 → May → Individual Days**

This allows you to progressively investigate sales from a high-level overview to detailed daily information.

---

# 28. Complete Procedure at a Glance

### Create the report page

1. Rename existing Page 1 to **Top Bottom Five Analysis**.
2. Click **+** to create a new page.
3. Rename the new page **Overview**.

### Create the sales trend visual

4. Click a blank area on the canvas.
5. Select **Line Chart**.
6. Drag **Net Sales** → **Y-axis**.
7. Drag **Date** → **X-axis**.
8. Resize and position the chart.

### Explore time hierarchy

9. Use **Drill Up** to reach Year level.
10. Use **Go to Next Level in Hierarchy** to move:

* Year → Quarter
* Quarter → Month
* Month → Day

11. Enable **Drill Down** when you want to investigate a specific year/quarter/month.
12. Use **Drill Up** to return to the overview level.

### Format the visual

13. Change the title to **Sales Trends by Period**.
14. Format the title.
15. Turn Y-axis values off.
16. Turn Y-axis title off.
17. Turn Data Labels on.
18. Format data labels.
19. Turn X-axis title off.
20. Format X-axis values.
21. Turn horizontal gridlines off.
22. Turn vertical gridlines off.
23. Change line color.
24. Select the desired line style.
25. Turn markers on.
26. Adjust marker size/color.
27. Set interpolation type to **Smooth**.

---

# 29. Key Takeaways

* **Line charts** are useful for representing trends over time.
* A **Date hierarchy** allows analysis at multiple time levels.
* Power BI can navigate through **Year → Quarter → Month → Day**.
* **Drill Up** moves toward higher-level aggregation.
* **Drill Down** allows detailed investigation of a selected data point.
* **Go to Next Level in Hierarchy** changes the entire visual to the next hierarchy level.
* Data labels can be used when you don't want to display values directly on the Y-axis.
* Removing unnecessary gridlines and axis titles can make a report cleaner.
* Markers make individual data points easier to identify.
* Line interpolation can be changed between styles such as **Smooth** and **Step**.
* The completed visual fulfills the requirement to show **sales trends at daily, monthly, quarterly, and annual levels**.
