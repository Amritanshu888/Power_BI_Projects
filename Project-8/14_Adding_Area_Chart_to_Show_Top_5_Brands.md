# Power BI — Creating and Formatting a Top 5 Brands by Average Profit Percentage Chart

## 1. Objective of the Session

The objective of this session is to create a visual that represents the:

> **Top 5 brands with the highest Average Profit Percentage**

The chart is created by modifying an existing bar chart, configuring the required fields, applying a **Top N filter**, and then formatting the resulting visual.

The session also demonstrates how to:

* Duplicate an existing visual
* Configure **Y-axis** and **X-axis** fields
* Change aggregation from **Sum** to **Average**
* Apply a **Top N filter**
* Convert the visual into an **area/line-style chart**
* Format line colors
* Format shaded areas
* Configure markers
* Format data labels
* Change axis text size
* Modify the chart title
* Change text/scroller colors
* Save the Power BI report

---

# 2. Starting Point — Duplicate the Existing Bar Chart

The instructor starts with an already-created **bar chart**.

### Steps

1. Click on the existing bar chart.

2. Press:

   **Ctrl + C**

3. Press:

   **Ctrl + V**

This creates a copy/duplicate of the existing chart.

4. Move the newly created chart to the **right-hand side** of the report page.

The duplicated chart will be used to create the new **Top 5 Brands by Average Profit Percentage** visual.

---

# 3. Clean the Existing Filters and Fields

After duplicating the chart, the instructor modifies the fields used by the copied visual.

First, expand the **Filters pane**.

### Remove unnecessary filters

Under the Filters pane:

* Remove **Brands** from the filters pane.

Then remove unnecessary fields from the visual:

* Remove **Brand** from the **Y-axis** bucket.
* Remove **Average of Discount Percentage** from the **X-axis** bucket.

The purpose is to clear the old configuration so that the chart can be configured specifically for the new requirement.

---

# 4. Add Brand to the Y-Axis

Now the visual needs to represent different brands.

### Steps

1. Expand the **Data pane**.
2. Find the **Brand** field.
3. Double-click **Brand** or drag and drop it into the:

   **Y-axis**

bucket.

The Y-axis will now contain the different brands.

---

# 5. Add Profit Percentage to the X-Axis

Next, the instructor adds the profit percentage.

### Steps

1. In the Data pane, find **Profit Percentage**.
2. Double-click it or drag and drop it into the:

   **X-axis**

bucket.

### Default aggregation

Power BI will initially aggregate the Profit Percentage as:

> **Sum of Profit Percentage**

However, the requirement is to calculate the **average profit percentage**, not the sum.

---

# 6. Change Profit Percentage from Sum to Average

### Steps

1. Click the dropdown next to **Profit Percentage** in the X-axis field.
2. Power BI will show the available summarization options.
3. Change:

**Sum → Average**

The X-axis now represents:

> **Average Profit Percentage**

This is important because the requirement is specifically to find brands based on their **highest average profit percentage**.

---

# 7. Add Brand to the Visual-Level Filters

To identify only the **Top 5 brands**, Brand needs to be used in the filter configuration.

### Steps

1. Double-click **Brand** in the Data pane.
2. Drag and drop **Brand** into the **Filters on this visual** section.

Now Brand is available as a visual-level filter.

---

# 8. Apply a Top 5 Filter

The next step is to restrict the visual to only the five brands having the highest average profit percentage.

### Steps

Under:

**Filters on this visual → Brand**

change the filtering type from:

**Basic filtering**

to:

**Top N**

Then configure:

> **Top 5**

This tells Power BI that only the five highest-ranked brands should be displayed.

---

# 9. Configure the "By Value" Field

The Top N filter needs to know **which measure/value should be used for ranking the brands**.

Therefore, **Profit Percentage** is added to the **By value** section.

### Steps

1. Find **Profit Percentage** in the Data pane.
2. Drag and drop it into:

   **By value**

Power BI will initially select:

> **Sum of Profit Percentage**

But that is not what we need.

### Change Sum to Average

1. Click the dropdown next to Profit Percentage under **By value**.
2. Change:

**Sum → Average**

Therefore, the Top N filter will rank brands according to:

> **Average Profit Percentage**

---

# 10. Apply the Filter

After configuring:

* Top N = **Top 5**
* By value = **Average of Profit Percentage**

click:

> **Apply filter**

Power BI will now filter the visual and display only the **five brands with the highest average profit percentage**.

### Final logic

The visual effectively answers:

> **Which five brands have the highest average profit percentage?**

The ranking is based on **Average Profit Percentage**, not Sum.

---

# 11. Resulting Chart

The resulting visual displays the top five brands and their average profit percentages.

The instructor notes that:

> Some brands may have the same value of average profit percentage.

This is completely acceptable and is **not an issue**.

If two or more brands have the same average percentage, they can appear with the same value.

---

# 12. Collapse the Panes

After creating the chart, the instructor cleans up the Power BI interface.

The following panes are collapsed:

* **Filters pane**
* **Visualizations pane**
* **Data pane**

The Visualizations pane is then expanded again when further formatting is required.

---

# 13. Change the Chart Type

The instructor now wants to change the appearance of the visual.

The existing chart is selected and the instructor chooses to replace it with another chart type, referring to it as an **area chart/line chart** during the formatting discussion.

### Steps

1. Select the chart.
2. In the Visualizations pane, click the appropriate chart-type option/add chart option.
3. The visual is converted to the new chart type.

The resulting chart is then formatted as a line/area-style visual.

---

# 14. Format the Line

With the chart selected:

1. Open:

   **Format your visual**

2. Scroll down to the **Lines** section.

3. Expand **Colors**.

The instructor changes the line color.

### Color selection

A specific color is selected, referred to in the transcript by its color/hex value:

> **#DBCDAD**

The exact visual appearance depends on the selected theme and report design.

---

# 15. Configure the Shaded Area

The chart contains a shaded area underneath the line.

### Steps

1. Expand:

   **Shaded area**

2. Set the shaded area's color to:

> **Match color line**

This makes the shaded area use the same color as the line.

### Reduce transparency

The instructor then reduces the transparency of the shaded area.

The transparency is set to approximately:

> **39%**

This makes the shaded area visible without overpowering the line itself.

---

# 16. Configure Markers

Markers can be used to highlight individual data points on the line.

### Steps

1. Expand:

   **Markers**

2. The instructor notes that the marker:

   * Type can be changed.
   * Size can also be increased if desired.

The exact marker type is left as a choice based on preference.

The important point is that Power BI provides formatting controls for:

* Marker type
* Marker size

---

# 17. Format Data Labels

The instructor next formats the values displayed on the chart.

### Steps

1. Collapse the **Lines** section.

2. Collapse the **Shaded area** section.

3. Collapse the **Markers** section.

4. Expand:

   **Data labels**

5. Scroll down.

6. Click:

   **Value**

7. Change the value/text color to:

> **White**

This improves the visibility of the displayed data values against the chart background.

---

# 18. Format the X-Axis Values

The instructor then changes the formatting of the X-axis.

### Steps

1. Collapse **Data labels**.
2. Scroll upward.
3. Expand the **X-axis** section.
4. Locate the formatting option for the values/text.
5. Reduce the size to approximately:

> **40**

The instructor also attempts to change the **maximum height**, but observes that changing it does not make any noticeable difference.

Therefore, no further adjustment is required.

---

# 19. Font Formatting

The font style can also be changed according to personal/report design preferences.

The instructor mentions that:

* Font style can be selected according to choice.
* The text is currently **bold**, which is acceptable.

Therefore, no mandatory change is required here.

---

# 20. Change the Chart Title

The default title needs to be replaced with a meaningful title.

### Steps

1. Select the chart.

2. Go to:

   **General → Title**

3. Change the title to:

> **Top Five Brands by Highest Average Profit Percentage**

This makes the purpose of the visual immediately clear to the report user.

---

# 21. Save the Report

Once the formatting is complete, save the Power BI report.

### Shortcut

Press:

**Ctrl + S**

This saves the current report.

---

# 22. Change the Text Color in the Scroller

The instructor then makes one additional formatting adjustment to the text/company/brand names displayed in the scroller/visual.

### Steps

1. Select the relevant visual.

2. Expand the **Visualizations** pane.

3. Select:

   **Format your visual**

4. Locate the **Scroller** section.

5. Click:

   **Text Color**

6. Select the color that was previously used for the **light-colored visuals** in the Excel sheet/theme.

7. Return to the Power BI report.

8. Use **More Colors** if necessary.

9. Paste/select the desired color value.

The instructor concludes that the new text color looks better with the overall report design.

---

# 23. Complete Workflow at a Glance

The complete process can be remembered as:

**Existing Bar Chart**
↓
**Ctrl+C → Ctrl+V**
↓
Move duplicate to right side
↓
Remove old filters/fields
↓
Add **Brand → Y-axis**
↓
Add **Profit Percentage → X-axis**
↓
Change **Sum → Average**
↓
Add **Brand → Filters on this visual**
↓
Change **Basic filtering → Top N**
↓
Set **Top 5**
↓
Add **Profit Percentage → By value**
↓
Change **Sum → Average**
↓
**Apply filter**
↓
Top 5 brands by average profit percentage
↓
Change chart type to area/line-style visual
↓
Format lines
↓
Format shaded area
↓
Format markers
↓
Format data labels
↓
Format X-axis
↓
Change title
↓
Change scroller/text color
↓
**Ctrl + S**

---

# 24. Important Power BI Concepts Demonstrated

## A. Sum vs Average

One of the most important concepts in this exercise is choosing the correct aggregation.

Power BI may automatically select:

> **Sum**

when a numeric field is added to a visual.

But if the business requirement says:

> **Average Profit Percentage**

you must explicitly change the aggregation to:

> **Average**

This is done using the dropdown beside the field in the relevant field bucket.

---

## B. Top N Filtering

A **Top N filter** is useful when you don't want to display every category.

For example:

* Top 5 brands by profit
* Top 10 products by sales
* Bottom 5 customers by revenue
* Top 10 employees by performance

The important configuration is:

**Category field → Top N → N value → By value measure → Apply filter**

In this example:

| Configuration   | Value             |
| --------------- | ----------------- |
| Category        | Brand             |
| Filter type     | Top N             |
| N               | 5                 |
| Ranking measure | Profit Percentage |
| Aggregation     | Average           |

---

## C. Visual-Level Filtering

The Top 5 filter is applied under:

> **Filters on this visual**

This means the Top 5 restriction applies specifically to this chart.

It does **not** necessarily filter other visuals on the report page.

This is different from applying a filter at the page or report level.

---

# 25. Why Profit Percentage Is Added Twice

A useful point from this exercise is that **Profit Percentage appears in two different places**.

### X-axis

Profit Percentage is added to the X-axis to **display the value**.

Aggregation:

> **Average**

### By value

Profit Percentage is added under **By value** to **rank the brands** for the Top N filter.

Aggregation:

> **Average**

So conceptually:

**X-axis → What value should the chart display?**

**By value → What value should Power BI use to determine the Top 5?**

Both need to use **Average Profit Percentage** because that is the business requirement.

---

# 26. Important Formatting Options Covered

The session also demonstrates several useful formatting properties.

### Lines

You can modify:

* Line color

### Shaded Area

You can modify:

* Shaded area color
* Match color with line
* Transparency

### Markers

You can modify:

* Marker type
* Marker size

### Data Labels

You can modify:

* Value color
* Visibility and other label properties

### X-Axis

You can modify:

* Text/value size
* Other axis formatting options

### General → Title

You can modify:

* Title text
* Title formatting

### Scroller

You can modify:

* Text color

---

# 27. Key Takeaways

1. **Duplicate an existing visual** using `Ctrl + C` and `Ctrl + V` when you want to reuse its basic configuration/design.

2. Remove unnecessary fields and filters before configuring the new visual.

3. Add **Brand** to the Y-axis and **Profit Percentage** to the X-axis.

4. Power BI may automatically use **Sum** for a numeric field, so always verify the aggregation.

5. Change:
   **Sum of Profit Percentage → Average of Profit Percentage**

6. To display only the highest-performing brands, use:
   **Filters on this visual → Top N**

7. Set:
   **Top 5**

8. Use **Average Profit Percentage** under **By value** to determine which brands qualify for the Top 5.

9. Always click **Apply filter** after configuring the Top N filter.

10. Equal average profit percentages among multiple brands are not necessarily a problem.

11. Power BI provides extensive visual formatting options for:

* Lines
* Shaded areas
* Markers
* Data labels
* Axes
* Titles
* Scroller text

12. Use meaningful titles such as:
    **Top Five Brands by Highest Average Profit Percentage**

13. Finally, save the report using:
    **Ctrl + S**

---

## Final Visual Requirement

The final visual created in this session is essentially:

> **Top 5 Brands ranked by Average Profit Percentage**

where:

**Brand** = Category
**Average Profit Percentage** = Metric
**Top 5** = Filter condition
**Area/Line-style chart** = Visualization
**Average Profit Percentage** = Ranking criterion
