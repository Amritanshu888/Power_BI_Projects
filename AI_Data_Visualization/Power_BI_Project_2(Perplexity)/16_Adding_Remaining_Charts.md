# Detailed Notes: Adding Total Balance by Name & Monthly Transaction Balance Charts

This session focuses on adding **two more visuals to the second report page** by reusing existing visuals from Page 1 and modifying their fields/measures.

The two new visuals are:

1. **Total Balance by Name** — a bar chart
2. **Monthly Transaction Balance** — a line chart

The session also demonstrates important Power BI concepts such as **copying visuals, changing fields, clearing filters, creating new measures instead of modifying existing ones, formatting visuals, and maintaining the original Page 1 visuals**.

---

# 1. Add Total Balance by Name Chart

The first new visualization will show:

> **Total Balance by Customer Name**

There is already a similar chart on **Page 1** that shows:

> **Total Amount by Name**

Instead of creating the chart from scratch, the instructor reuses the existing chart.

---

## 2. Copy the Existing Bar Chart

### Step 1: Go to Page 1

Click on the **first report page**.

There is an existing bar chart representing:

> **Total Amount by Name**

### Step 2: Copy the chart

Select the chart and press:

**Ctrl + C**

### Step 3: Go to Page 2

Click on **Page 2**.

### Step 4: Paste the chart

Press:

**Ctrl + V**

The same bar chart is now copied to Page 2.

---

# 3. Change Amount to Balance

The copied chart currently represents the **sum of Amount**.

The goal is now to represent:

> **Total Balance by Name**

### Steps

1. Select the copied chart.
2. Look at the fields used by the visual.
3. The existing **Amount** field is being used on the **X-axis**.
4. Remove the existing Amount field from the X-axis.
5. Locate the **Balance** field in the Data pane.
6. Drag and drop **Balance** into the **X-axis** bucket.

Therefore, the visual changes from:

> **Sum of Amount by Name**

to:

> **Sum of Balance by Name**

---

# 4. Change the Display Units

The instructor then changes how the numerical values are displayed.

### Steps

1. Select the chart.
2. Open:

> **Format your visual**

3. Go to:

> **Data labels**

4. Change the **Position** to:

> **Auto**

5. Under the value settings, locate:

> **Display units**

The instructor experiments with different options:

* Thousands
* None

The **None** option does not make the values display suitably in this case, so the instructor keeps:

> **Thousands**

### Purpose

Display units help make large numbers easier to read.

For example, instead of displaying a very large number in full, Power BI can display it in thousands.

---

# 5. Resize the Chart

The instructor then reduces the size of the chart slightly.

### Steps

1. Select the chart.
2. Use the resize handles.
3. Reduce its dimensions as required.
4. Position it appropriately on Page 2.

This is part of arranging the dashboard layout.

---

# 6. Remove the Existing Top-N Filter

An important issue appears with the copied chart.

The original chart had a filter applied to it.

The chart was showing only:

> **Top 2 customers**

This filter was copied along with the visual.

However, for the new **Total Balance by Name** chart, the instructor wants to display the relevant customers without retaining that Top 2 restriction.

---

## Steps to Remove the Filter

1. Select the copied chart.
2. Expand the **Filters pane**.
3. Examine the filters applied to the visual.
4. Locate the filter responsible for limiting the chart to the top two customers.
5. Remove/clear the applied filter.
6. Collapse the Filters pane after removing it.

### Important concept

When you **copy and paste a visual**, its existing configuration—including relevant filters—can also be carried over.

Therefore, after copying a visual, always check:

* Fields
* Filters
* Sorting
* Formatting
* Aggregations

before using it for a different purpose.

---

# 7. Change the Bar Colors

The instructor then changes the color of the bars.

### Steps

1. Select the chart.
2. Open:

> **Format your visual**

3. Go to:

> **Bars**

4. Select:

> **All**

5. Locate the:

> **Color**

option.
6. Choose any desired color.

This changes the color of the bars in the chart.

---

# 8. Change the Chart Title

The copied chart still has the old title related to amount.

The instructor changes it to reflect the new metric.

### Steps

1. Select the chart.
2. Open:

> **Format your visual**

3. Go to:

> **General**

4. Open the **Title** settings.
5. Replace the existing title:

> **Total Amount**

with:

> **Total Balance**

The chart now clearly communicates that it represents balance rather than amount.

---

# 9. Final Configuration of the First New Chart

The final chart is essentially:

> **Total Balance by Name**

Conceptually:

| Component     | Configuration        |
| ------------- | -------------------- |
| Visual        | Bar chart            |
| Category      | Customer Name        |
| Value         | Balance              |
| Aggregation   | Sum                  |
| Data labels   | Position = Auto      |
| Display units | Thousands            |
| Filter        | Top 2 filter removed |
| Color         | Customized           |
| Title         | Total Balance        |

---

# 10. Add the Second Chart: Monthly Transaction Balance

The next requirement is to create a visualization showing:

> **Monthly Transaction Balance**

There is already a similar line chart on Page 1.

The existing chart represents:

> **Monthly Transaction Amount**

The instructor will reuse it but create a **new measure based on Balance**.

---

# 11. Copy the Existing Monthly Transaction Chart

### Step 1: Go to Page 1

Return to the first report page.

There is an existing **line chart** showing monthly transaction amount.

### Step 2: Copy it

Select the line chart and press:

**Ctrl + C**

### Step 3: Go to Page 2

Click **Page 2**.

### Step 4: Paste

Click on a blank area of the canvas and press:

**Ctrl + V**

The line chart is now available on Page 2.

### Step 5: Position and resize

Move the chart toward the top of Page 2 and resize it as required.

---

# 12. Understand the Existing Measure

The copied line chart uses:

> **Transaction Date**

from the **Combined Banking Data** table.

That part is correct and does not need to be changed.

However, the chart currently uses a measure called something similar to:

> **Monthly Transaction Amount**

The important point is that this measure is based on the:

> **Amount column**

But the new chart needs to use:

> **Balance**

Therefore, we need a new measure.

---

# 13. Important: Do NOT Modify the Existing Measure

This is one of the most important concepts in this session.

The instructor explains that if we simply edit the existing **Monthly Transaction Amount** measure and replace `Amount` with `Balance`, the original Page 1 chart would also change.

That would be undesirable because the Page 1 chart is supposed to continue showing:

> **Monthly Transaction Amount**

Therefore:

> **Do not modify the existing measure.**

Instead, create a **new measure**.

---

# 14. Copy the Existing Measure

### Step 1: Locate the existing measure

Find the:

> **Monthly Transaction Amount**

measure in the Measures table.

### Step 2: Copy its DAX

Open/select the measure's DAX expression.

Then:

**Ctrl + A → Ctrl + C**

Now we have a copy of the original measure's DAX formula.

---

# 15. Create a New Measure

Return to Power BI.

### Steps

1. Right-click the **Measures** table.
2. Select:

> **New measure**

3. In the formula bar:

   * Press **Ctrl + A**
   * Press **Ctrl + V**

Now the copied DAX formula is available in the new measure.

---

# 16. Replace Amount with Balance

The original measure calculates monthly transaction **amount**.

The new measure needs to calculate monthly transaction **balance**.

Therefore, replace:

> **Amount**

with:

> **Balance**

The instructor mentions replacing the relevant occurrence of `Amount` with `Balance` in the DAX expression.

The resulting measure is:

> **Monthly Transaction Balance**

### General concept

```text
Monthly Transaction Amount
          ↓
Uses Amount column
          ↓
Copy the measure
          ↓
Replace Amount with Balance
          ↓
Monthly Transaction Balance
```

This allows us to preserve the original measure while creating a new one.

---

# 17. Replace the Measure in the Line Chart

Now the new measure needs to be used by the copied line chart.

### Steps

1. Select the copied line chart on Page 2.
2. Locate the existing:

> **Monthly Transaction Amount**

measure.

3. Uncheck/remove that measure from the visual.
4. Locate:

> **Monthly Transaction Balance**

5. Select/add the new measure.

The line chart now represents:

> **Monthly Transaction Balance by Month**

The transaction date remains the same.

---

# 18. Line Chart Configuration

The chart now uses:

| Component        | Field/Measure               |
| ---------------- | --------------------------- |
| X-axis           | Transaction Date / Month    |
| Value/Y-axis     | Monthly Transaction Balance |
| Original measure | Removed                     |
| New measure      | Monthly Transaction Balance |

The chart therefore shows how transaction **balance changes across different months**.

---

# 19. Change the Line Color

The instructor also demonstrates how to customize the line color.

### Steps

1. Select the line chart.
2. Open:

> **Format your visual**

3. Go to:

> **Lines**

4. Scroll down if necessary.
5. Locate:

> **Color**

6. Choose any desired color.

The line in the chart will now use the selected color.

---

# 20. Why Create a New Measure?

This is a particularly important Power BI concept.

Suppose the existing measure is:

> **Monthly Transaction Amount**

and it uses:

> `Amount`

If we directly change that measure to use:

> `Balance`

then every visual using the original measure will immediately change.

### Problem

The Page 1 chart is supposed to continue displaying:

> Monthly Transaction Amount

Therefore, modifying the existing measure would break the original report.

### Correct approach

Create a separate measure:

> **Monthly Transaction Balance**

This allows both measures to coexist.

```text
Monthly Transaction Amount
        ↓
Uses Amount

Monthly Transaction Balance
        ↓
Uses Balance
```

This is a good practice when the same calculation logic needs to be reused with a different underlying field.

---

# 21. Final Page 2 Additions

After completing the session, Page 2 now contains two additional visuals:

### Chart 1 — Total Balance by Name

Shows:

> Total balance associated with each customer/name.

Important configurations:

* Bar chart
* Balance on X-axis
* Top 2 filter removed
* Display units = Thousands
* Bar color customized
* Title = **Total Balance**

### Chart 2 — Monthly Transaction Balance

Shows:

> Transaction balance across different months.

Important configurations:

* Line chart
* Transaction Date used for the timeline
* Monthly Transaction Balance measure used
* New measure created rather than modifying the existing measure
* Line color customized

---

# 22. Complete Workflow

```text
PAGE 1
  ↓
Copy Total Amount by Name bar chart
  ↓
PAGE 2
  ↓
Paste chart
  ↓
Remove Amount from X-axis
  ↓
Add Balance to X-axis
  ↓
Format Data Labels
  ↓
Display Units → Thousands
  ↓
Resize chart
  ↓
Check Filters
  ↓
Remove Top 2 filter
  ↓
Change bar color
  ↓
Change title → Total Balance
```

Then:

```text
PAGE 1
  ↓
Copy Monthly Transaction Amount line chart
  ↓
PAGE 2
  ↓
Paste chart
  ↓
Keep Transaction Date
  ↓
Do NOT modify existing measure
  ↓
Copy Monthly Transaction Amount DAX
  ↓
Measures table → New measure
  ↓
Paste DAX
  ↓
Replace Amount → Balance
  ↓
Create Monthly Transaction Balance
  ↓
Remove Monthly Transaction Amount from chart
  ↓
Add Monthly Transaction Balance
  ↓
Change line color
  ↓
Resize/reposition chart
```

---

# 23. Key Power BI Concepts from This Session

| Concept                         | Explanation                                                                       |
| ------------------------------- | --------------------------------------------------------------------------------- |
| **Copy/Paste Visual**           | Allows an existing visual to be reused on another report page                     |
| **X-axis**                      | Contains the field whose values are represented along the horizontal axis         |
| **Balance**                     | Replaces Amount when the analysis requires balance rather than transaction amount |
| **Data Labels**                 | Displays numerical values directly on a visual                                    |
| **Display Units**               | Controls how large numbers are displayed, such as thousands                       |
| **Filters Pane**                | Allows filters applied to a visual/page/report to be viewed and modified          |
| **Top N Filter**                | Limits a visual to the highest/lowest N values                                    |
| **Format Your Visual**          | Used to customize visual appearance                                               |
| **Bars → Color**                | Changes bar colors                                                                |
| **Lines → Color**               | Changes line-chart colors                                                         |
| **General → Title**             | Changes the visual title                                                          |
| **DAX Measure**                 | A dynamic calculation used by Power BI visuals                                    |
| **New Measure**                 | Creates a separate calculation without changing an existing measure               |
| **Transaction Date**            | Used to establish the monthly timeline                                            |
| **Monthly Transaction Amount**  | Existing measure based on Amount                                                  |
| **Monthly Transaction Balance** | New measure based on Balance                                                      |

---

# 24. Important Lessons to Remember

### 1. Reuse existing visuals when possible

You don't always need to create a visual from scratch.

You can:

> **Copy → Paste → Modify**

This saves time and preserves existing formatting.

---

### 2. Always check copied filters

A copied visual can retain filters from the original visual.

For example:

> Original chart → Top 2 customers

After copying it, the Top 2 filter may still exist.

Therefore, always inspect the **Filters pane** when repurposing a visual.

---

### 3. Don't unnecessarily modify existing measures

If an existing measure is already being used elsewhere, changing it can affect other visuals.

Instead:

> **Copy the DAX → Create New Measure → Modify the new measure**

This protects the original calculation.

---

### 4. Use descriptive titles

Instead of generic titles such as:

> Sum of Balance

use a business-friendly title such as:

> **Total Balance**

Similarly, a chart should clearly communicate what it represents.

---

### 5. Format visuals consistently

Use:

> **Format Painter**

when you want multiple visuals to have consistent formatting.

You can also manually customize:

* Colors
* Data labels
* Display units
* Titles
* Size
* Position

---

# 25. Overall Project Context

The instructor concludes that the Power BI project can be developed by combining:

**AI-generated data + AI-generated recommendations + Power BI experimentation**

The overall workflow is:

```text
AI Tools
   ↓
Generate/Create Data
   ↓
Import Data into Power BI
   ↓
Perform Analysis
   ↓
Use AI Recommendations
   ↓
Create Recommended Visuals
   ↓
Experiment with Additional Visuals
   ↓
Format Dashboard
   ↓
Publish Report to Power BI Service
```

The next session will cover:

> **Publishing the Power BI report to Power BI Service.**
