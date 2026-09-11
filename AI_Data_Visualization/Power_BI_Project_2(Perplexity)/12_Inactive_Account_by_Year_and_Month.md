# Power BI – Creating “Inactive Accounts by Year & Month”

## 1. Objective of the Session

In this session, the instructor adds a **new visual to the first report page**.

The recommendation comes from the **7th record in the Excel sheet**.

The requirement is to identify:

> **Accounts that have been inactive during the previous 90 days**

This analysis can be performed with respect to:

* A particular date, or
* A particular month

### Business purpose

The visualization helps identify accounts/customers that **have not been active in the last 90 days**.

This can be useful for understanding inactive accounts and potentially taking actions such as customer re-engagement.

---

# 2. Recommended Visualizations

The AI tool recommends using either:

* **Clustered Bar Chart**, or
* **Table**

The instructor points out that these are only recommendations from the AI tool and that **other suitable visualizations can also be used**.

In this session, the instructor decides to use:

> **Line Chart**

---

# 3. DAX Measure for Inactive Accounts

The Excel sheet contains the DAX measure required for calculating the inactive accounts.

The instructor copies the provided DAX measure from the Excel sheet.

### Steps

1. Double-click the DAX measure text in the Excel sheet.
2. Select the measure.
3. Copy it using:

**Ctrl + A → Ctrl + C**

4. Go back to Power BI Desktop.

The exact DAX formula is not included in the transcript itself, so it should be copied directly from the course's Excel sheet rather than reconstructed.

---

# 4. Create the Inactive Accounts Measure

Once back in Power BI Desktop:

### Step 1: Open Measures Table

Find the:

> **Measures Table**

### Step 2: Create a New Measure

Right-click the **Measures Table**.

Select:

> **New Measure**

### Step 3: Paste the DAX

Use:

**Ctrl + A → Ctrl + V**

to paste the DAX measure copied from the Excel sheet.

### Step 4: Create the Measure

Press:

> **Enter**

The **Inactive Accounts** measure is now created.

---

# 5. Create the Line Chart

The instructor decides to use a **Line Chart** rather than the AI-recommended bar chart or table.

### Step 1: Select Blank Area

Click on an empty area of the report canvas.

This creates a new visual rather than modifying an existing visual.

### Step 2: Select Line Chart

From the Visualizations pane, select:

> **Line Chart**

A blank line chart is created.

### Step 3: Resize the Chart

Resize the chart appropriately so that it fits into the report page.

---

# 6. Add Inactive Accounts to the Chart

The newly created measure is:

> **Inactive Accounts**

### Steps

1. Find **Inactive Accounts** in the Data/Fields pane.
2. Double-click it or drag it.
3. Place it in the:

> **Y-Axis**

Therefore:

```text
Y-Axis → Inactive Accounts
```

The Y-axis represents the **number of inactive accounts**.

---

# 7. Add Transaction Date to the X-Axis

Next, the instructor uses the **Transaction Date** column to determine when the accounts were inactive.

### Steps

1. Find the **Transaction Date** column.
2. Double-click it or drag it.
3. Place it into the:

> **X-Axis**

Therefore:

```text
X-Axis → Transaction Date
Y-Axis → Inactive Accounts
```

The line chart now shows inactive accounts over time.

---

# 8. Configure the Date Hierarchy

When the Transaction Date field is added, Power BI automatically creates a **date hierarchy**.

The hierarchy contains levels such as:

* Year
* Quarter
* Month
* Day

The instructor does **not** want to show all these levels.

The requirement is to represent the data using:

> **Year and Month only**

---

## Removing Day

The instructor removes:

> **Day**

from the hierarchy.

---

## Removing Quarter

The instructor also removes:

> **Quarter**

from the hierarchy.

---

## Final Date Hierarchy

The chart should contain:

```text
Year
Month
```

So the visualization represents inactive accounts by:

> **Year → Month**

rather than:

> Year → Quarter → Month → Day

---

# 9. Final Axis Configuration

At this point, the chart is configured approximately as:

| Chart Element | Field                           |
| ------------- | ------------------------------- |
| X-Axis        | Transaction Date → Year & Month |
| Y-Axis        | Inactive Accounts               |

The chart is therefore:

> **Inactive Accounts by Year and Month**

---

# 10. Apply Existing Formatting Using Format Painter

The instructor wants the new line chart to have the **same formatting as an existing smooth line chart** created earlier.

The existing visual is the:

> **Smooth Line Chart**

located at the bottom of the report.

Instead of manually reproducing all the formatting, the instructor uses **Format Painter**.

### Steps

1. Select the existing **Smooth Line Chart**.
2. Go to the **Home** tab.
3. Click **Format Painter**.
4. Click the new:

> **Inactive Accounts by Year Month**

chart.

The formatting of the existing line chart is copied to the new chart.

### Key concept

**Format Painter** is useful when multiple visuals need to maintain a consistent appearance.

---

# 11. Turn Off Gridlines

After applying the formatting, the instructor makes additional changes to improve the appearance.

The first change is to remove the gridlines.

### Steps

1. Select the **Inactive Accounts by Year Month** chart.
2. Open:

> **Format Visual**

3. Locate the **Gridlines** section.
4. Turn the gridlines:

> **Off**

The instructor also turns off:

> **Vertical Gridlines**

### Final setting

```text
Gridlines → Off
Vertical Gridlines → Off
```

This creates a cleaner-looking line chart.

---

# 12. Change the Line Interpolation Type

The instructor then changes how the line is drawn.

### Steps

1. Stay inside **Format Visual**.
2. Go to the **Lines** section.
3. Scroll down.
4. Find:

> **Interpolation Type**

5. Change the interpolation type to:

> **Step**

### What does Step do?

Instead of connecting points with a continuously smooth/diagonal line, a **step line** displays changes in a stepped pattern.

Conceptually:

```text
Normal line:

      /
    /
  /
_/


Step line:

    ┌────
    │
────┘
```

This can make changes between time periods easier to see.

---

# 13. Change the Line Color

The instructor also changes the color of the line.

### Steps

1. Go to the **Line** formatting section.
2. Locate:

> **Color**

3. Click the color selector.
4. Choose a suitable color.

The instructor initially considers one color, decides it does not look good, and then chooses another color.

### Important point

The exact color is not essential to the concept. The purpose is simply to make the line visually appropriate and consistent with the dashboard.

---

# 14. Optional Shaded Area

The instructor mentions that a **shaded area** can also be included below/around the line.

This is optional.

### If you want the shaded area

You can enable it.

### If you don't want it

Turn the setting:

> **Off**

The instructor indicates that either choice is acceptable depending on the desired visual design.

---

# 15. Data Labels

The final chart also contains:

> **Data Labels**

These labels display the actual number associated with the data points.

Therefore, the chart can directly communicate the:

> **Number of inactive accounts**

for the relevant time period.

---

# 16. Understanding What the Chart Represents

The completed chart tells us how the number of inactive accounts changes over time.

For example, conceptually:

```text
Year → Month
     ↓
Inactive Accounts
```

It allows the user to observe:

* How many accounts are inactive
* How inactivity changes over different months
* Trends in inactive accounts over time

---

# 17. Drill Down / Hierarchy

The instructor then demonstrates the **Drill Down** functionality.

Because the X-axis contains a date hierarchy, Power BI can potentially allow movement between different levels of the hierarchy.

For example:

```text
Year
 ↓
Month
```

and potentially other date levels if they were included.

However, in this particular chart, the instructor notes that there isn't an additional useful level available beyond the configured hierarchy.

---

# 18. Selecting a Specific Data Point

The instructor attempts to click/select a particular point on the chart.

The purpose is to inspect the data associated with that particular point.

The instructor initially observes that the expected interaction is not working as intended.

They then use the available drill functionality.

---

# 19. Drill Down

The instructor clicks the **Drill Down** option.

The chart then displays a more detailed/specific point.

The instructor notes:

> It shows a single point only.

This demonstrates how Power BI can move from a higher-level date grouping to a more detailed level.

---

# 20. Moving to the Next Level in the Hierarchy

The instructor then demonstrates that we can:

> **Drill down → Go to the next level in the hierarchy**

This allows the user to move from one level of the date hierarchy to another.

For example:

```text
Year
 ↓
Month
```

The data changes according to the selected hierarchy level.

---

# 21. Drill Up

The instructor then demonstrates the opposite operation:

> **Drill Up**

Drill Up moves the visualization back to the higher level of the hierarchy.

For example:

```text
Month
 ↓
Year
```

So:

* **Drill Down** → move to a more detailed level
* **Drill Up** → move back to a higher/less detailed level

---

# 22. Final Visual

The final visual is essentially:

> **Inactive Accounts by Year Month**

### Main configuration

```text
Chart Type:
Line Chart
```

```text
X-Axis:
Transaction Date → Year + Month
```

```text
Y-Axis:
Inactive Accounts
```

### Formatting

```text
Gridlines → Off
Vertical Gridlines → Off
Interpolation Type → Step
Line Color → Customized
Data Labels → Enabled
Shaded Area → Optional
```

---

# 23. Complete Step-by-Step Workflow

For revision, remember the entire process in this order:

### Step 1 – Identify the requirement

From the Excel sheet:

> Find accounts that have been inactive during the previous 90 days.

---

### Step 2 – Copy the DAX Measure

From the Excel sheet:

**Double-click the DAX measure → Ctrl + A → Ctrl + C**

---

### Step 3 – Create the Measure in Power BI

Go to:

**Measures Table → Right-click → New Measure**

Paste:

**Ctrl + A → Ctrl + V**

Press:

**Enter**

---

### Step 4 – Create a New Visual

Click a blank area of the canvas.

Select:

> **Line Chart**

---

### Step 5 – Add Inactive Accounts

Drag:

> **Inactive Accounts → Y-Axis**

---

### Step 6 – Add Transaction Date

Drag:

> **Transaction Date → X-Axis**

---

### Step 7 – Configure Date Hierarchy

Remove:

* **Quarter**
* **Day**

Keep:

* **Year**
* **Month**

Final:

> **Year + Month**

---

### Step 8 – Copy Formatting

Select the existing:

> **Smooth Line Chart**

Then:

**Home → Format Painter → Inactive Accounts by Year Month**

---

### Step 9 – Remove Gridlines

Go to:

**Format Visual → Gridlines**

Set:

> **Gridlines = Off**

Also set:

> **Vertical Gridlines = Off**

---

### Step 10 – Change Line Interpolation

Go to:

**Format Visual → Lines → Interpolation Type**

Set:

> **Step**

---

### Step 11 – Change Line Color

Go to:

**Lines → Color**

Choose a suitable color.

---

### Step 12 – Optional Shading

Enable the shaded area if desired.

Otherwise:

> **Shaded Area = Off**

---

### Step 13 – Keep Data Labels

The chart displays **data labels**, allowing the number of inactive accounts to be seen directly.

---

### Step 14 – Test Drill Down

Use the **Drill Down** functionality to move into the next available hierarchy level.

---

### Step 15 – Drill Up

Use **Drill Up** to return to the previous/higher hierarchy level.

---

# 24. Important Power BI Concepts

## A. Date Hierarchy

When a date field is added to a visual, Power BI can automatically create a hierarchy such as:

```text
Year
Quarter
Month
Day
```

You can remove unnecessary levels and keep only the levels required for the analysis.

In this lecture:

```text
Year
Month
```

are retained.

---

## B. Drill Down

**Drill Down** allows you to move from a higher-level category to a more detailed level.

Example:

```text
Year → Month
```

---

## C. Drill Up

**Drill Up** moves back from a detailed level to a higher-level summary.

Example:

```text
Month → Year
```

---

## D. Interpolation Type

Interpolation controls how Power BI connects data points in a line chart.

The instructor changes it to:

> **Step**

This produces a stepped line rather than a smoothly connected line.

---

## E. Gridlines

Gridlines help users estimate values but can sometimes make a dashboard visually busy.

In this visualization, the instructor turns them off:

* Gridlines → Off
* Vertical Gridlines → Off

This produces a cleaner visual.

---

## F. Data Labels

Data labels display the actual values directly on the visual.

Here, they communicate:

> **Number of inactive accounts**

---

## G. Format Painter

The instructor again uses:

> **Home → Format Painter**

to copy the formatting of an existing visual to the new visual.

This is particularly useful for maintaining a consistent dashboard theme.

---

# 25. Recommended Visual vs. Actual Visual

An important point from the lecture is that the AI recommendation does **not** have to be followed exactly.

### AI recommendation

* Clustered Bar Chart
* Table

### Instructor's choice

> **Line Chart**

The instructor chooses the line chart because the objective involves looking at **inactive accounts over time**, making a time-based trend visualization appropriate.

---

# 26. Key Takeaways

* The objective is to identify **accounts inactive during the previous 90 days**.
* The analysis can be performed with respect to a **given date or month**.
* The Excel/AI recommendation suggests a **Clustered Bar Chart or Table**, but the instructor chooses a **Line Chart**.
* The required **Inactive Accounts DAX measure** is copied from the Excel sheet.
* The measure is created through:
  **Measures Table → New Measure**
* **Inactive Accounts** is placed on the **Y-axis**.
* **Transaction Date** is placed on the **X-axis**.
* The date hierarchy is simplified by removing:

  * Quarter
  * Day
* Only **Year and Month** are retained.
* Formatting is copied from an existing **Smooth Line Chart** using **Format Painter**.
* Gridlines are turned off.
* Vertical gridlines are also turned off.
* Line **Interpolation Type** is changed to **Step**.
* The line color is customized.
* A shaded area can optionally be enabled or disabled.
* **Data labels** show the number of inactive accounts.
* The instructor demonstrates **Drill Down** and **Drill Up** using the date hierarchy.
* The final visual is an **Inactive Accounts by Year Month** line chart.

## Quick Revision Flow

**Inactive Accounts requirement → Copy DAX → Measures Table → New Measure → Line Chart → Inactive Accounts to Y-axis → Transaction Date to X-axis → Keep Year + Month → Format Painter → Gridlines Off → Vertical Gridlines Off → Interpolation = Step → Customize Line Color → Optional Shading → Data Labels → Drill Down/Drill Up**
