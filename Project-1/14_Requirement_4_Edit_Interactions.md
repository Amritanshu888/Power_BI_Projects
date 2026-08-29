# Power BI — Requirement 4: Comparing Two Periods Using Edit Interactions

## 1. Objective of Requirement 4

The requirement is to allow the **user to compare Sales, Profit, and Quantity Sold between any two periods** selected by the user.

In other words:

* The user should be able to select **Period 1**.
* The user should be able to select **Period 2**.
* The report should show:

  * Total Sales for Period 1 vs Period 2
  * Total Profit for Period 1 vs Period 2
  * Total Quantity Sold for Period 1 vs Period 2

This lecture demonstrates the **second approach** for achieving this requirement.

> **Important:** The first approach used two separate date tables and DAX measures. The second approach uses **Edit Interactions**, avoiding the need to add additional date tables to the data model.

---

# 2. Create a New Report Page

Since Requirement 1/4 was already implemented using the first approach, create another page to demonstrate the second approach.

### Steps

1. Click the **`+` icon** at the bottom of Power BI Desktop.
2. A new report page will be created.
3. Double-click the new page name.
4. Press `Ctrl + A`.
5. Rename the page to:

**Req 4**

The purpose of this naming is to distinguish this page from the page where the first approach was implemented.

---

# 3. Create Date Filter 1

We need two independent date slicers because the user must be able to select two different periods.

### Steps

1. Click on a blank area of the report canvas.
2. From the **Visualizations** pane, select **Slicer**.
3. A blank slicer will be created.
4. Resize and position the slicer as required.
5. From the **Fact Table**, select the **Date** column.
6. The Date column will be added to the slicer.

This becomes the first date filter.

### Rename the slicer

1. In the **Fields** bucket, locate the Date field.
2. Double-click the field name.
3. Press `Ctrl + A`.
4. Rename it to:

**Date Filter 1**

This makes it easier to distinguish between the two slicers.

---

# 4. Add a Border to Date Filter 1

To make the slicer visually distinguishable:

1. Select **Date Filter 1**.
2. Go to **Format your visual**.
3. Open **General**.
4. Go to **Effects**.
5. Turn **Visual border** → **On**.

Now the first date filter has a visible border.

---

# 5. Create Date Filter 2

We now need another slicer for selecting the second period.

### Steps

1. Click on a blank area of the canvas.
2. Select the **Slicer** visual again.
3. A second blank slicer will appear.
4. Move it to the desired location.
5. From the **Fact Table**, select the **Date** column.
6. The Date field will be added to the second slicer.

### Rename Date Filter 2

1. Select the second slicer.
2. In the **Fields** bucket, locate the Date field.
3. Double-click it.
4. Press `Ctrl + A`.
5. Rename it to:

**Date Filter 2**

### Add its border

1. Select Date Filter 2.
2. Go to **Format your visual → General → Effects**.
3. Turn **Visual border** → **On**.

We now have:

* **Date Filter 1** → Period 1
* **Date Filter 2** → Period 2

---

# 6. Create Total Sales Bar Chart

We now need three visuals for the first period:

1. Total Sales
2. Total Profit
3. Total Quantity Sold

### Create Total Sales

1. Click on a blank area of the canvas.
2. Select **Stacked Bar Chart**.
3. A blank bar chart will appear.
4. From the **Fact Table**, select the **Net Sales** column.
5. Net Sales will be added to the visual.

The bar chart now represents:

**Total Sales**

---

# 7. Format the Total Sales Visual

Several formatting changes are applied to make the visual cleaner.

### Add a border

With the bar chart selected:

1. Go to **Format your visual**.
2. Select **General**.
3. Open **Effects**.
4. Turn **Visual border** → **On**.

### Remove gridlines

1. Go to the visual formatting options.
2. Find the **X-axis** settings.
3. Locate **Gridlines**.
4. Change Gridlines → **Off**.

### Turn on data labels

1. Find **Data labels**.
2. Change Data labels → **On**.

This displays the actual value next to the bar.

### Turn off X-axis values

Since the value is already displayed through data labels:

1. Open **X-axis**.
2. Change the axis values/labels → **Off**.

This prevents unnecessary duplication of values.

---

# 8. Format Data Labels

The data labels can be further customized.

Under **Data labels → Values**, the lecture demonstrates changing:

* **Font color** → Black
* **Font family** → Times New Roman
* **Font style** → Bold
* **Font size** → Increase as required

The objective is to make the values easier to read.

---

# 9. Add the Title "Total Sales"

To change the title:

1. Select the bar chart.
2. Go to **Format your visual**.
3. Select **General**.
4. Open **Title**.
5. Set the title to:

**Total Sales**

---

# 10. Change Bar Color

To change the bar's appearance:

1. Select the bar chart.
2. Go to **Visual** formatting.
3. Open the **Bars** section.
4. Change the color to any desired color.

The exact color is not important; it is simply used to visually distinguish the first set of charts.

---

# 11. Create Total Profit Visual

Instead of creating another bar chart from scratch, duplicate the existing Total Sales visual.

### Steps

1. Select the **Total Sales** bar chart.
2. Press:

`Ctrl + C`

3. Press:

`Ctrl + V`

4. Move the copied chart below/next to the first chart.

Now modify it to represent Total Profit.

### Replace Net Sales with Profit

1. Select the copied bar chart.
2. In the X-axis/data field bucket, remove **Sum of Net Sales**.
3. From the Fact Table, select the **Profit** column.

The visual now represents:

**Total Profit**

### Change title

1. Go to **Format your visual**.
2. Select **General → Title**.
3. Change the title to:

**Total Profit**

The other formatting can remain the same.

---

# 12. Create Total Quantity Sold Visual

Again, duplicate an existing bar chart.

### Steps

1. Copy one of the existing bar charts.
2. Paste it using `Ctrl + V`.
3. Move it below the other charts.

### Replace Net Sales

1. Remove **Sum of Net Sales** from the data field.
2. Select **Unit Sold** from the Fact Table.
3. The visual now represents the total quantity sold.

### Change title

Go to:

**Format your visual → General → Title**

Set the title to:

**Total Quantity Sold**

---

# 13. Final Structure of First Set of Visuals

At this stage, the first group of three bar charts represents:

| Visual      | Represents          |
| ----------- | ------------------- |
| Bar Chart 1 | Total Sales         |
| Bar Chart 2 | Total Profit        |
| Bar Chart 3 | Total Quantity Sold |

These will eventually be controlled by **Date Filter 1**.

---

# 14. Create a Second Set of Three Bar Charts

We now need another identical set of visuals for the second period.

The easiest method is to copy all three existing visuals.

### Steps

1. Select the three existing bar charts:

   * Total Sales
   * Total Profit
   * Total Quantity Sold
2. Press `Ctrl + C`.
3. Press `Ctrl + V`.
4. Move the newly created three charts to another area of the canvas.

You now have **six bar charts**:

### First group

* Total Sales
* Total Profit
* Total Quantity Sold

### Second group

* Total Sales
* Total Profit
* Total Quantity Sold

---

# 15. Change Colors of the Second Group

To make it visually obvious which charts belong to which date filter:

1. Select the three copied charts.
2. Go to **Visual → Bars**.
3. Change their bar color.

The lecture uses **pink** as an example.

Therefore:

* First three charts → one color
* Second three charts → pink

This makes the relationship between the two groups easier to understand.

---

# 16. Understand the Purpose of the Two Groups

The report should now conceptually look like this:

### Date Filter 1

Controls:

* Total Sales — Group 1
* Total Profit — Group 1
* Total Quantity Sold — Group 1

### Date Filter 2

Controls:

* Total Sales — Group 2
* Total Profit — Group 2
* Total Quantity Sold — Group 2

The key challenge is preventing each date filter from affecting the **wrong group**.

This is where **Edit Interactions** is used.

---

# 17. Edit Interactions in Power BI

Power BI normally allows a slicer to interact with other visuals automatically.

For example:

> Selecting a date in a slicer normally filters all relevant visuals on the page.

But here we don't want that default behavior.

We want:

**Date Filter 1 → Group 1 only**

and

**Date Filter 2 → Group 2 only**

Therefore, we need to customize the interaction behavior.

---

# 18. Configure Date Filter 1

### Steps

1. Select **Date Filter 1**.
2. Go to the **Format** tab.
3. Select **Edit interactions**.

After clicking Edit interactions, small interaction icons will appear above the visuals.

These icons determine how the selected slicer interacts with each visual.

---

# 19. Understand the Interaction Icons

When Edit Interactions is enabled, Power BI displays different options above each visual.

These options determine the behavior of the selected slicer.

The important behaviors discussed are:

### Filter

The slicer filters the visual.

So when a user changes the date selection, the visual's values change accordingly.

### None

The slicer has **no effect** on that visual.

Therefore, even if the date selection changes, that visual remains unchanged.

---

# 20. Configure Date Filter 1 Correctly

We want Date Filter 1 to affect only the **first/orange group**.

### For the first three charts

Leave the interaction as the default **Filter** behavior.

Therefore:

**Date Filter 1 → Filter → First three charts**

### For the second/pink group

Change the interaction to:

**None**

Do this for all three pink charts.

Therefore:

**Date Filter 1 → None → Second three charts**

---

# 21. Test Date Filter 1

After configuring the interactions:

1. Change/select a different date in **Date Filter 1**.
2. Observe the first/orange group.

The values in the first group should change.

Now observe the pink group.

The values in the pink group should remain unchanged.

Therefore:

> **Date Filter 1 affects only the first group of charts.**

---

# 22. What Happens if We Don't Use "None"?

The lecture also demonstrates what happens when the interaction is changed back to **Filter**.

If Date Filter 1 is set to **Filter** for all six charts:

* First three charts change.
* Pink three charts also change.

That means all six visuals are responding to Date Filter 1.

But this is **not what the requirement asks for**.

Therefore, the pink charts must have their interaction set to **None**.

---

# 23. Configure Date Filter 2

Now repeat the process for the second slicer.

### Steps

1. Select **Date Filter 2**.
2. Go to the **Format** tab.
3. Select **Edit interactions**.

Now configure the interactions in the opposite manner.

---

# 24. Date Filter 2 Interaction Settings

We want Date Filter 2 to affect only the **second/pink group**.

### For the first/orange three charts

Set interaction to:

**None**

Therefore:

**Date Filter 2 → None → First three charts**

### For the second/pink three charts

Keep the default:

**Filter**

Therefore:

**Date Filter 2 → Filter → Second three charts**

---

# 25. Test Date Filter 2

1. Click on a blank area of the canvas to exit Edit Interactions.
2. Clear Date Filter 1 if necessary.
3. Change the selected date in **Date Filter 2**.

Expected result:

* Orange charts → **Do not change**
* Pink charts → **Change**

Therefore, Date Filter 2 affects only the second group.

---

# 26. Final Interaction Architecture

The final setup can be represented as:

```text
                 DATE FILTER 1
                       |
              -------------------
              |        |        |
            Sales    Profit   Quantity
              |
          Group 1
          Orange


                 DATE FILTER 2
                       |
              -------------------
              |        |        |
            Sales    Profit   Quantity
              |
          Group 2
           Pink
```

More precisely:

| Date Filter   | Group 1 | Group 2 |
| ------------- | ------- | ------- |
| Date Filter 1 | Filter  | None    |
| Date Filter 2 | None    | Filter  |

This is the core concept of the second approach.

---

# 27. How the Requirement Is Fulfilled

Suppose the user selects:

**Date Filter 1 → January**

and

**Date Filter 2 → February**

Then:

### Group 1

Shows:

* January Sales
* January Profit
* January Quantity Sold

### Group 2

Shows:

* February Sales
* February Profit
* February Quantity Sold

This allows the user to compare the three metrics between two independently selected periods.

---

# 28. Why This Approach Is Better Than the First Approach

The lecture previously discussed another approach using **two separate date tables and DAX measures**.

That approach works, but it has an important disadvantage.

### First approach

It requires creating:

* Date Table 1
* Date Table 2
* Additional DAX measures
* Additional relationships/relationship management

These additional tables increase the size and complexity of the Power BI data model.

---

# 29. Advantage of the Edit Interactions Approach

The second approach uses:

**Edit Interactions**

instead of creating additional date tables.

Therefore, it can fulfill the same business requirement **without unnecessarily increasing the data model size**.

### Key advantage

> If a requirement can be fulfilled without increasing the model size, that approach is generally preferable.

Therefore, the lecture recommends the **Edit Interactions approach** over the first approach for this particular requirement.

---

# 30. Why Was the First Approach Still Important?

Even though the second approach is recommended, the first approach was still useful for learning.

The first approach demonstrated important Power BI concepts such as:

* Multiple date tables
* DAX measures
* Active relationships
* Inactive relationships
* Using DAX to work with different date contexts

So the first approach should not be considered useless.

It was primarily valuable for understanding **Power BI data modeling and relationship concepts**.

---

# 31. Key Concept: Edit Interactions

**Edit Interactions** allows you to control how one visual affects other visuals on the report page.

Instead of allowing Power BI's default interaction behavior, you can explicitly specify:

* **Filter** → Visual responds to the selected visual.
* **None** → Visual does not respond to the selected visual.

This is particularly useful when a report contains multiple slicers that should control different groups of visuals.

---

# 32. Complete Procedure — Quick Revision

### Create the slicers

1. Add a new page.
2. Rename it **Req 4**.
3. Add a slicer.
4. Add Fact Table → Date.
5. Rename it **Date Filter 1**.
6. Add a border.
7. Create another slicer.
8. Add Fact Table → Date.
9. Rename it **Date Filter 2**.
10. Add a border.

### Create Group 1

11. Create a Stacked Bar Chart.
12. Add **Net Sales**.
13. Format the chart.
14. Turn on Data Labels.
15. Turn off Gridlines.
16. Turn off X-axis values.
17. Add a border.
18. Set title to **Total Sales**.
19. Duplicate it for Profit.
20. Replace Net Sales with **Profit**.
21. Change title to **Total Profit**.
22. Duplicate it again.
23. Replace Net Sales with **Unit Sold**.
24. Change title to **Total Quantity Sold**.

### Create Group 2

25. Copy the three charts.
26. Paste them.
27. Move them to the second section.
28. Change their bar color, e.g. pink.

### Configure Date Filter 1

29. Select Date Filter 1.
30. Go to **Format → Edit interactions**.
31. Keep **Filter** for Group 1.
32. Set **None** for Group 2.

### Configure Date Filter 2

33. Select Date Filter 2.
34. Go to **Format → Edit interactions**.
35. Set **None** for Group 1.
36. Keep **Filter** for Group 2.

### Verify

37. Change Date Filter 1 → only Group 1 changes.
38. Change Date Filter 2 → only Group 2 changes.
39. The report now supports comparison between two independently selected periods.

---

# 33. Important Takeaways

### Requirement

Compare:

* **Sales**
* **Profit**
* **Quantity Sold**

between **any two user-selected periods**.

### Approach 2

Uses:

**Two date slicers + Edit Interactions + two sets of visuals**

### Interaction configuration

```text
                 Group 1       Group 2
Date Filter 1     FILTER         NONE
Date Filter 2     NONE           FILTER
```

### Recommended approach

The **Edit Interactions approach is recommended** over creating two additional date tables because it achieves the requirement without increasing the Power BI model size.

### Learning point from Approach 1

The first approach was still useful for understanding:

* Active relationships
* Inactive relationships
* DAX measures
* Multiple date tables
* Date context manipulation

### Most important Power BI feature from this lecture

**Format → Edit Interactions**

It allows you to precisely control which visuals respond to a slicer or another visual.
