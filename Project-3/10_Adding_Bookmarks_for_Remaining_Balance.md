# Detailed Notes: Extending Bookmarks to Switch Between Amount & Balance Charts

## 1. Introduction

In the previous session, bookmarks were used to give the user the flexibility to switch between two charts representing **transactions by month**:

* Line chart
* Column chart

In this session, the same concept is extended further.

The new requirement is to add **two more charts** that represent **Balance by Month**, and the user should be able to switch between all four chart views:

1. Transactions by Month — Line Chart
2. Transactions by Month — Column Chart
3. Balance by Month — Line Chart
4. Balance by Month — Column Chart

The source dataset contains both an **Amount** column and a **Remaining Balance** column, so the remaining balance can be used to create the additional charts. 

---

# 2. Existing Bookmark Setup

Before making changes, the report already has bookmarks for:

* **Line Chart Amounts**
* **Column Chart Amounts**

These bookmarks control the visibility of the transaction/amount charts.

The goal is now to add two additional bookmarks:

* **Line Chart Balance**
* **Column Chart Balance**

---

# 3. Create the Line Chart Balance Bookmark

First, open the **Bookmarks pane**.

### Steps

1. Click on the **Bookmarks pane**.
2. Click **Add**.
3. A new bookmark will be created.
4. Rename this bookmark.

The lecture refers to this as **Bookmark 3**.

Rename it to:

> **Line Chart Balance**

### Rename process

1. Double-click the bookmark name.
2. Press **Ctrl + A**.
3. Type **Line Chart Balance**.
4. Press **Enter**.

---

# 4. Create the Column Chart Balance Bookmark

Create another bookmark for the column chart.

### Steps

1. Click **Add** again in the Bookmarks pane.
2. A fourth bookmark will be created.
3. Double-click the bookmark name.
4. Press **Ctrl + A**.
5. Rename it:

> **Column Chart Balance**

6. Press **Enter**.

Now there are four bookmarks:

| Bookmark             | Purpose                                   |
| -------------------- | ----------------------------------------- |
| Line Chart Amounts   | Transactions/Amount shown as line chart   |
| Column Chart Amounts | Transactions/Amount shown as column chart |
| Line Chart Balance   | Balance shown as line chart               |
| Column Chart Balance | Balance shown as column chart             |

---

# 5. Bookmark Navigator Automatically Gets Additional Options

Once the two new bookmarks are created, the existing **Bookmark Navigator** will also display the additional bookmark options.

The navigator now contains four options.

The navigator can be resized if required.

### Resize the Bookmark Navigator

Simply select the navigator and drag its edges to make it larger or smaller.

The lecture also mentions that the navigator can be formatted further.

---

# 6. Formatting the Bookmark Navigator

The Bookmark Navigator can be customized using its formatting options.

For example, you can change:

* Style
* Size
* Text size

In the lecture, the **text size is kept at 8**.

You can resize the navigator further so that all four bookmark names can be displayed properly.

---

# 7. Adding the First Balance Visual

Now we need to create the actual visuals corresponding to the new bookmarks.

The first new visual will be a **Balance by Month Column Chart**.

The easiest way is to duplicate an existing column chart.

### Steps

1. Select the existing **Transactions by Month Column Chart**.
2. Press:

**Ctrl + C**

3. Press:

**Ctrl + V**

A duplicate column chart is created.

4. Place the newly created chart **on top of the existing chart** so that they overlap.

This is important because the bookmarks will later control which visual is visible.

---

# 8. Change the Column Chart from Amount to Remaining Balance

The copied chart currently represents **Amount**.

We need to change it so that it represents **Remaining Balance**.

### Steps

1. Select the newly copied column chart.
2. Locate the **Y-axis** field/bucket.
3. Remove the existing **Sum of Amount / Amount** field from the Y-axis.
4. Expand the **Data pane**.
5. Locate the **Remaining Balance** column.
6. Select/check **Remaining Balance**.

The chart now represents:

> **Balance by Month**

Instead of transaction amount by month.

The underlying month-based structure remains the same; only the numerical field being represented has been changed. 

---

# 9. Rename the Balance Column Chart

The newly created visual should be given a meaningful title.

### Steps

1. Select the chart.
2. Go to **Format your visual**.
3. Open **General**.
4. Go to **Title**.
5. Change the title to indicate that it represents balance by month.

The lecture ultimately refers to this visual as:

> **Balance by Month Column Chart**

Make sure the title identifies both:

* The metric: **Balance**
* The visualization type: **Column**

---

# 10. Create the Second Balance Visual

We now need a **Balance by Month Line Chart**.

Instead of creating it from scratch, duplicate the newly created balance column chart.

### Steps

1. Select the **Balance by Month Column Chart**.
2. Press:

**Ctrl + C**

3. Press:

**Ctrl + V**

4. Place the newly created chart directly over the existing balance column chart.

Now the two balance charts overlap.

---

# 11. Convert the Balance Column Chart into a Line Chart

The duplicated chart is currently a column chart.

### Steps

1. Select the duplicated balance chart.
2. Open the **Visualizations** pane.
3. Select:

> **Line Chart**

The chart is now a **Balance by Month Line Chart**.

---

# 12. Format the Balance Line Chart

The line chart can be formatted to make it visually different or more appealing.

### Change the interpolation type

1. Select the balance line chart.
2. Click **Format Your Visual**.
3. Go to **Lines**.
4. Find **Interpolation type**.
5. Change it to:

> **Smooth**

This creates a smoother-looking line.

### Change the line color

Within the relevant color settings:

1. Locate the line color.
2. Change it from blue.
3. Select:

> **Purple**

The line chart is now displayed using a purple line.

---

# 13. Optional Line Chart Formatting

The lecture also mentions that additional formatting can be applied.

For example, you can add:

* **Markers**
* **Shaded area**

These are optional formatting choices.

The important point is that the visual now represents **Balance by Month** using a line chart. 

---

# 14. Rename the Balance Line Chart

Because the duplicated chart was originally a column chart, its title needs to be changed.

### Steps

1. Select the balance line chart.
2. Go to **Format Visual**.
3. Select **General**.
4. Select **Title**.
5. Change **Column** to:

> **Line**

The title should therefore identify it as the **Balance by Month Line Chart**.

---

# 15. Four Visual States Now Exist

At this stage, there are four charts:

### Amount charts

1. **Transactions by Month Line Chart**
2. **Transactions by Month Column Chart**

### Balance charts

3. **Balance by Month Line Chart**
4. **Balance by Month Column Chart**

The four charts overlap in the report page, and bookmarks will determine which one is visible at a particular time.

---

# 16. Why the Bookmarks Must Be Updated

This is one of the most important parts of the lecture.

After adding new visuals, the existing bookmarks need to be **updated**.

A bookmark stores the state of the report, including which visuals are visible or hidden.

Therefore, simply creating the new visuals is not enough.

You must update each bookmark so that it knows which chart should be displayed.

> **Important rule: After making changes to the visual state, always update the corresponding bookmark.** 

---

# 17. Update the Line Chart Amounts Bookmark

The first bookmark is:

> **Line Chart Amounts**

The desired state for this bookmark is:

* Bookmark Navigator → Visible
* Transactions by Month Line Chart → Visible
* Transactions by Month Column Chart → Hidden
* Balance by Month Line Chart → Hidden
* Balance by Month Column Chart → Hidden

---

## Step-by-Step

### Step 1: Open the Selection Pane

Expand the **Selection pane**.

### Step 2: Make sure Bookmark Navigator is at the top

Select the **Bookmark Navigator** and move it to the top.

The navigator must remain visible for every bookmark.

### Step 3: Update the bookmark

Right-click the **Line Chart Amounts** bookmark and select:

> **Update**

### Step 4: Set visual visibility

For this bookmark:

**Hide:**

* Balance by Month Line Chart
* Balance by Month Column Chart
* Transactions by Month Column Chart

**Show:**

* Transactions by Month Line Chart

### Step 5: Update again

After setting the required visibility, click the **three ellipses (...)** next to the Line Chart Amounts bookmark and select:

> **Update**

Now the bookmark stores the correct state.

---

# 18. Update the Column Chart Amounts Bookmark

Next, configure:

> **Column Chart Amounts**

The desired state is:

* Bookmark Navigator → Visible
* Transactions by Month Column Chart → Visible
* Transactions by Month Line Chart → Hidden
* Balance by Month Line Chart → Hidden
* Balance by Month Column Chart → Hidden

### Steps

1. Select **Column Chart Amounts**.
2. Confirm that the Bookmark Navigator remains at the top.
3. Hide the **Transactions by Month Line Chart**.
4. Unhide the **Transactions by Month Column Chart**.
5. Hide both balance charts.
6. Click the **three ellipses (...)** next to the bookmark.
7. Select **Update**.

Again, the update is essential. 

---

# 19. Update the Line Chart Balance Bookmark

Now configure the third bookmark:

> **Line Chart Balance**

The desired state is:

* Bookmark Navigator → Visible
* Balance by Month Line Chart → Visible
* Everything else → Hidden

### Required visibility

**Visible:**

* Bookmark Navigator
* Balance by Month Line Chart

**Hidden:**

* Transactions by Month Line Chart
* Transactions by Month Column Chart
* Balance by Month Column Chart

### Steps

1. Click **Line Chart Balance**.
2. Confirm Bookmark Navigator is at the top.
3. Hide Transactions by Month Line Chart.
4. Hide Transactions by Month Column Chart.
5. Hide Balance by Month Column Chart.
6. Make sure Balance by Month Line Chart is visible.
7. Click **...** next to the bookmark.
8. Click **Update**.

The bookmark now stores the Balance Line Chart state. 

---

# 20. Update the Column Chart Balance Bookmark

Finally, configure:

> **Column Chart Balance**

The desired state is:

* Bookmark Navigator → Visible
* Balance by Month Column Chart → Visible
* Everything else → Hidden

### Required visibility

**Visible:**

* Bookmark Navigator
* Balance by Month Column Chart

**Hidden:**

* Balance by Month Line Chart
* Transactions by Month Column Chart
* Transactions by Month Line Chart

### Steps

1. Click **Column Chart Balance**.
2. Confirm the Bookmark Navigator is at the top.
3. Hide Balance by Month Line Chart.
4. Unhide Balance by Month Column Chart.
5. Hide Transactions by Month Column Chart.
6. Hide Transactions by Month Line Chart.
7. Click **...** next to the bookmark.
8. Click **Update**. 

---

# 21. Final Bookmark Configuration

After configuring all four bookmarks, the visibility should look like this:

| Bookmark                 | Amount Line | Amount Column | Balance Line | Balance Column | Navigator |
| ------------------------ | ----------- | ------------- | ------------ | -------------- | --------- |
| **Line Chart Amounts**   | Visible     | Hidden        | Hidden       | Hidden         | Visible   |
| **Column Chart Amounts** | Hidden      | Visible       | Hidden       | Hidden         | Visible   |
| **Line Chart Balance**   | Hidden      | Hidden        | Visible      | Hidden         | Visible   |
| **Column Chart Balance** | Hidden      | Hidden        | Hidden       | Visible        | Visible   |

This is the core configuration that makes the four-way chart switching work.

---

# 22. Test the Bookmarks

After updating all bookmarks, collapse the **Selection pane**.

You can also collapse:

* UPI Transactions table in the Data pane
* Data pane
* Format pane

This gives you a cleaner view for testing. 

---

# 23. Test Line Chart Amounts

Click:

> **Line Chart Amounts**

The report should show:

> **Transactions by Month Line Chart**

This chart represents the variation in transaction amounts over the months.

---

# 24. Test Column Chart Amounts

Click:

> **Column Chart Amounts**

The report should now show:

> **Transactions by Month Column Chart**

This represents the variation in transaction amounts over time using columns.

---

# 25. Test Line Chart Balance

Click:

> **Line Chart Balance**

The visual should change to:

> **Balance by Month Line Chart**

The line chart represents the variation in balance across different months.

---

# 26. Test Column Chart Balance

Click:

> **Column Chart Balance**

The visual should change to:

> **Balance by Month Column Chart**

The balance variation for different months is now represented using columns. 

---

# 27. Align Chart Titles

After confirming that all bookmarks work, the chart titles can be formatted for consistency.

The lecture specifically changes the **title alignment**.

---

## Line Chart Amounts

### Steps

1. Click **Line Chart Amounts** in the Bookmark Navigator.
2. Select the line chart.
3. Open the **Visualizations** pane.
4. Go to **General**.
5. Open **Title**.
6. Change the title alignment to:

> **Left**

---

# 28. Resize the Bookmark Navigator

After changing the title alignment, select the Bookmark Navigator.

Resize it so that:

> **All bookmark names are completely visible.**

This is important because there are now four bookmark options.

---

# 29. Align the Column Chart Amounts Title

Next:

1. Select **Column Chart Amounts**.
2. Select the column chart.
3. Open **Format Your Visual**.
4. Go to **General**.
5. Go to **Title**.
6. Change the title alignment to:

> **Left**

---

# 30. Align the Balance Line Chart Title

Next:

1. Select **Line Chart Balance**.
2. Select the balance line chart.
3. Open the title formatting options.
4. Set the title alignment to:

> **Left**

---

# 31. Align the Balance Column Chart Title

Finally:

1. Select **Column Chart Balance**.
2. Select the balance column chart.
3. Open the title formatting options.
4. Set the horizontal/title alignment to:

> **Left**

Now all four charts have consistently aligned titles. 

---

# 32. Final Bookmark Navigator Test

Collapse the Bookmarks pane.

Now use the Bookmark Navigator to test all four options.

Because you're working in Power BI Desktop, use:

> **Ctrl + Click**

to activate a bookmark from the navigator.

---

## Test 1: Line Chart Amounts

**Ctrl + Click → Line Chart Amounts**

Result:

> Transaction amount variation is displayed using a line chart.

---

## Test 2: Column Chart Amounts

**Ctrl + Click → Column Chart Amounts**

Result:

> Transaction variation over time is displayed using a column chart.

---

## Test 3: Line Chart Balance

**Ctrl + Click → Line Chart Balance**

Result:

> Balance variation by month is displayed using a line chart.

---

## Test 4: Column Chart Balance

**Ctrl + Click → Column Chart Balance**

Result:

> Balance variation for different months is displayed using a column chart.

If all four behave correctly, the bookmark setup is working properly. 

---

# 33. Testing Bookmarks with Filters

An additional important test is to see how filters/slicers behave when switching between bookmarks.

For example, suppose we want to view the data only for:

> **Bangalore**

### Step 1: Select Bangalore

Use the **City slicer** and select:

> **Bangalore**

The currently displayed chart is filtered to Bangalore.

For example, the **Balance by Month Column Chart** will now display data for Bangalore.

---

# 34. Switch to Another Bookmark

Now switch to another chart—for example:

> **Line Chart Balance**

The lecture observes that the Bangalore filter is **not automatically applied** to the newly selected bookmark/chart.

This is because the slicers have not been synchronized across the different bookmark states.

---

# 35. Apply a Filter to the New Bookmark

You can manually apply the filter again.

For example:

1. Select the **City** slicer.
2. Choose **Delhi**.
3. The data for Delhi will now be displayed in the currently selected chart.

So the filter has to be selected again when switching bookmark states in this setup. 

---

# 36. Important Limitation Highlighted in the Lecture

The lecture specifically points out that:

> **The slicers have not been synchronized for the different bookmarks.**

Therefore, when switching between bookmarks, the filter selection does not automatically carry over in the way demonstrated.

For example:

1. Select Bangalore.
2. View Balance Column Chart.
3. Switch to Balance Line Chart.
4. The Bangalore selection is not automatically reflected there in the demonstrated setup.
5. You may need to select the required city again.

This is an important distinction from the earlier **Sync Slicers** functionality.

---

# 37. Complete Conceptual Picture

The report now provides the user with four different ways of looking at the same time-based information.

### Transaction Amount

**Line Chart**

Shows:

> Transaction amount variation by month using a line.

**Column Chart**

Shows:

> Transaction amount variation by month using columns.

### Remaining Balance

**Line Chart**

Shows:

> Balance variation by month using a line.

**Column Chart**

Shows:

> Balance variation by month using columns.

The user can switch between all four views using the Bookmark Navigator.

---

# 38. Key Workflow to Remember

The complete workflow is:

**Create/duplicate visual**

↓

**Change the numerical field**

↓

**Change the chart type**

↓

**Format the chart**

↓

**Rename the chart/title**

↓

**Create bookmark**

↓

**Set visual visibility**

↓

**Keep Bookmark Navigator visible**

↓

**Update bookmark**

↓

**Repeat for every bookmark**

↓

**Test every bookmark**

This sequence is particularly important because bookmarks depend on the saved visibility state.

---

# 39. Most Important Practical Rule

### Never forget to update bookmarks.

Whenever you make changes to:

* Visual visibility
* Which chart is displayed
* Which chart is hidden
* Bookmark Navigator placement

you should update the relevant bookmark.

The basic pattern is:

> **Make changes → Click `...` → Update**

Without updating, the changes may not be stored in the bookmark. 

---

# 40. Important Points for Revision

### Bookmarks

* Four bookmarks are ultimately used.
* Two are for **Amounts**.
* Two are for **Balance**.

### Amount Bookmarks

1. **Line Chart Amounts**
2. **Column Chart Amounts**

### Balance Bookmarks

3. **Line Chart Balance**
4. **Column Chart Balance**

### Balance Visuals

The Balance charts are created by:

1. Copying an existing chart.
2. Removing **Amount** from the Y-axis.
3. Adding **Remaining Balance**.
4. Creating one column chart.
5. Duplicating it.
6. Converting the duplicate to a line chart.

### Balance Line Chart Formatting

* Interpolation type → **Smooth**
* Color → **Purple**
* Markers → Can be added
* Shaded area → Can also be added

### Bookmark Navigator

* Automatically contains the newly created bookmarks.
* Can be resized.
* Can be formatted.
* Text size in the lecture is set to **8**.
* Should remain at the **top**.
* Should remain visible for every bookmark.

### Bookmark Visibility

Only one of the four charts should be visible at a time.

The Bookmark Navigator should remain visible in every state.

### Title Formatting

All four chart titles are aligned to the **left** for consistency.

### Testing

Use **Ctrl + Click** on the Bookmark Navigator in Power BI Desktop to test the bookmarks.

---

# 41. Final Result

The completed report page provides a single interactive chart area where the user can switch between:

> **Line Chart Amounts → Column Chart Amounts → Line Chart Balance → Column Chart Balance**

This allows the report to provide multiple insights without displaying four separate charts simultaneously.

The same bookmark technique can therefore be used to create a more interactive and less cluttered Power BI report. 

---

## 42. What Comes Next

The next session will cover **publishing the Power BI report to Power BI Service**.

The lecture also emphasizes that the completed report can be tested by applying different filters before publishing it, to make sure the visuals and bookmarks behave as expected. 
