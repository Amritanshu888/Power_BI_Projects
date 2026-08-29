# Detailed Notes: Bookmarks in Power BI — Switching Between Charts

## 1. Introduction to Bookmarks

The main concept covered in this session is **Bookmarks in Power BI**.

### Objective

The requirement is to provide the user with the ability to **switch between two different charts** on the same report page.

For example, the user should be able to switch between:

* **Line Chart**
* **Column Chart**

Instead of displaying both charts simultaneously, we can place them in the same location and use **Bookmarks** to control which chart is visible.

This provides the user with flexibility to choose the type of visualization they prefer.

---

# 2. Opening the Selection Pane

Before creating bookmarks, the first step is to open the **Selection pane**.

### Steps

1. Go to the **View** tab.
2. Click on **Selection**.

The **Selection pane** will now become visible.

### What is the Selection Pane?

The Selection pane displays all the objects/visuals present on the current report page.

In the example, the Selection pane contains:

* 10 different slicers
* A line chart

The line chart is currently named:

> `Transactions by Month Year 2024`

---

# 3. Rename the Existing Line Chart

To make it easier to distinguish between the line chart and column chart, rename the existing line chart.

### Steps

1. In the **Selection pane**, locate the line chart.
2. Double-click its name.
3. Rename it to something that clearly indicates that it is a line chart.

For example:

> **Transactions by Month [Line] Year 2024**

The word **Line** is included in the name so that it is easy to identify the visual as the line-chart version.

---

# 4. Create a Copy of the Line Chart

We need two visuals:

1. Line chart
2. Column chart

Instead of creating the second visual from scratch, we can duplicate the existing line chart.

### Steps

1. Select the existing line chart.
2. Press:

**Ctrl + C**

3. Then press:

**Ctrl + V**

A copy of the line chart will be created.

---

# 5. Place the Two Charts on Top of Each Other

The newly created chart should be positioned exactly over the original chart.

The objective is for the two charts to **completely overlap**.

Why?

Because we eventually want the user to see only one chart at a time.

For example:

```text
┌───────────────────────────────┐
│                               │
│       Column Chart            │  ← Top visual
│                               │
│   ───────────────────────     │
│                               │
│       Line Chart              │  ← Behind
│                               │
└───────────────────────────────┘
```

Only one will be visible depending on the selected bookmark.

---

# 6. Convert the Top Chart into a Column Chart

The copied line chart is currently still a line chart.

We will convert the **top chart** into a column chart.

### Steps

1. Select the newly copied/top line chart.
2. Expand the **Visualizations** pane.
3. Select:

> **Stacked Column Chart**

The copied chart will now become a **column chart**.

### What does the column chart represent?

The column chart represents the:

> **Variation/change in transaction amounts over a period of time**

In this example, the amounts are represented across the different months of **2024**.

---

# 7. Rename the Column Chart

Since the copied chart is now a column chart, its name should also be changed.

### Steps

1. Go to the **Selection pane**.
2. Locate the newly created column chart.
3. Double-click its name.
4. Replace **Line** with **Column**.

For example:

> **Transactions by Month [Column] Year 2024**

Press **Enter**.

Now the Selection pane clearly identifies which visual is the line chart and which is the column chart.

---

# 8. Optional: Format the Column Chart

The column chart can be formatted according to your requirements.

### Steps

1. Select the column chart.
2. Open **Format your visual**.
3. Go to the **Columns** formatting option.
4. Change the column color.

In the lecture, the color is changed from **blue to purple**.

This formatting step is optional and does not affect the bookmark functionality.

---

# 9. Open the Bookmarks Pane

Now that the two charts have been created, we need to create bookmarks.

### Steps

1. Go to the **View** tab.
2. Click on:

> **Bookmarks**

The **Bookmarks pane** will open.

You can resize the pane if required.

---

# 10. Create the First Bookmark — Line Chart

The first bookmark will represent the state in which the **line chart is visible**.

### Step 1: Add a bookmark

In the Bookmarks pane, click:

> **Add**

Power BI creates a bookmark named something like:

> **Bookmark 1**

### Step 2: Rename the bookmark

Double-click **Bookmark 1**.

Press:

**Ctrl + A**

Rename it to:

> **Line Chart Amounts**

Press **Enter**.

This bookmark will represent the line-chart view of the report.

---

# 11. Create the Second Bookmark — Column Chart

Now create another bookmark for the column chart.

### Steps

1. Click **Add** again.
2. A second bookmark will be created.
3. Double-click the second bookmark.
4. Rename it to:

> **Column Chart Amounts**

5. Press **Enter**.

Now we have two bookmarks:

1. **Line Chart Amounts**
2. **Column Chart Amounts**

---

# 12. Configure the Line Chart Bookmark

At this point, both charts are still available.

We need to configure the **Line Chart Amounts** bookmark so that only the line chart is visible.

### Steps

1. Click the **Line Chart Amounts** bookmark.
2. Go to the **Selection pane**.
3. Locate the column chart:

> `Transactions by Month [Column] Year 2024`

4. Hide the column chart by clicking the visibility/eye option next to it.

The line chart remains visible while the column chart is hidden.

---

# 13. Very Important: Update the Bookmark

After changing the visibility of the chart, the bookmark needs to be updated.

This is a very important step.

### Steps

1. Locate the **Line Chart Amounts** bookmark.
2. Click the **three ellipses (...)** next to the bookmark.
3. Select:

> **Update**

### Why is Update necessary?

The bookmark stores the state of the report.

If you change the visibility of a visual after creating the bookmark but **do not update the bookmark**, the bookmark will not remember the latest change.

Therefore:

> **Whenever you make a change to a bookmark's state, click the three dots (...) → Update.**

---

# 14. Configure the Column Chart Bookmark

Now configure the second bookmark.

### Steps

1. Click the **Column Chart Amounts** bookmark.
2. Go to the **Selection pane**.
3. Locate the line chart:

> `Transactions by Month [Line] Year 2024`

4. Hide the line chart.

Now:

* Column chart → Visible
* Line chart → Hidden

---

# 15. Update the Column Chart Bookmark

Again, the bookmark must be updated.

### Steps

1. Click the three ellipses **(...)** next to **Column Chart Amounts**.
2. Click:

> **Update**

Now the bookmark stores the state where:

> **Column chart is visible and line chart is hidden.**

---

# 16. Test the Bookmarks

Now test whether the bookmarks work correctly.

### Test 1: Line Chart Bookmark

Click:

> **Line Chart Amounts**

The result should be:

* Line chart → Visible
* Column chart → Hidden

### Test 2: Column Chart Bookmark

Click:

> **Column Chart Amounts**

The result should be:

* Column chart → Visible
* Line chart → Hidden

Therefore, bookmarks allow us to switch between the two different chart views.

---

# 17. Creating a Bookmark Navigator

Instead of expecting the user to interact directly with the Bookmarks pane, we can provide a **Bookmark Navigator** on the report page.

This gives the user a convenient button/interface for switching between the charts.

---

# 18. Insert a Bookmark Navigator

### Steps

1. Go to the **Insert** tab.
2. Click:

> **Buttons**

3. Select:

> **Bookmark Navigator**

Power BI will add a bookmark navigator to the report page.

The navigator will contain options corresponding to the bookmarks that were created.

For example:

* Line Chart Amounts
* Column Chart Amounts

---

# 19. Position the Bookmark Navigator

Move the Bookmark Navigator to an appropriate location on the report page.

In the lecture, it is positioned:

> **At the top of the column chart**

You can resize it according to your requirements.

### Important recommendation

The Bookmark Navigator should be positioned somewhere that remains **visible regardless of which chart is displayed**.

The lecture specifically recommends keeping it:

> **At the top**

This ensures that when the charts switch, the navigator remains visible and the user can always switch between the chart views.

---

# 20. Ensure the Bookmark Navigator Is Always Visible

Check the **Selection pane**.

You should see the Bookmark Navigator listed separately.

The navigator should:

* Remain visible.
* Not be hidden by either bookmark.
* Stay at the top of the relevant visual arrangement.

### Important point

Do **not hide the Bookmark Navigator**.

It needs to remain visible so that the user can switch between the bookmarks at any time.

---

# 21. Collapse the Panes

Once everything is configured, you can collapse the different panes to get a cleaner view.

The lecture collapses:

* Selection pane
* Bookmarks pane
* Formatting/other relevant panes

This allows you to see the final report page more clearly.

---

# 22. Using the Bookmark Navigator

The Bookmark Navigator can now be used to switch between the two charts.

### Switch to Line Chart

Hold:

> **Ctrl**

and click:

> **Line Chart Amounts**

The visual changes to the line chart.

### Switch to Column Chart

Again, hold:

> **Ctrl**

and click:

> **Column Chart Amounts**

The visual changes to the column chart.

Thus, the user can easily switch between the two visualizations.

---

# 23. Why Use Ctrl + Click?

When working in Power BI Desktop, buttons and navigators generally require:

> **Ctrl + Click**

to activate them while editing the report.

This allows you to distinguish between:

* Selecting/moving the object during report editing
* Actually interacting with the button/navigator

When the report is being used by an end user in the appropriate viewing experience, the interaction behaves as a normal navigation/control action.

---

# 24. Resize and Reposition the Navigator

The Bookmark Navigator can be customized further.

You can:

* Resize it.
* Move it.
* Change its position.
* Adjust its formatting.
* Place it wherever it is convenient for the report design.

The key requirement is that it should remain **visible and accessible**.

---

# 25. Complete Bookmark Workflow

The entire process can be summarized as follows:

### Create the visuals

1. Start with an existing line chart.
2. Rename it to identify it as the **Line** version.
3. Duplicate it using **Ctrl + C → Ctrl + V**.
4. Place the duplicate directly over the original.
5. Convert the duplicate into a **Stacked Column Chart**.
6. Rename it to identify it as the **Column** version.
7. Optionally format the column chart.

### Create bookmarks

8. Go to **View → Bookmarks**.
9. Click **Add**.
10. Rename the first bookmark to **Line Chart Amounts**.
11. Click **Add** again.
12. Rename the second bookmark to **Column Chart Amounts**.

### Configure Line Chart bookmark

13. Select **Line Chart Amounts**.
14. Hide the column chart in the Selection pane.
15. Click **... → Update**.

### Configure Column Chart bookmark

16. Select **Column Chart Amounts**.
17. Hide the line chart in the Selection pane.
18. Click **... → Update**.

### Create navigation

19. Go to **Insert → Buttons → Bookmark Navigator**.
20. Position the navigator at the top of the charts.
21. Resize it as required.
22. Ensure the navigator remains visible.
23. Test both bookmarks using **Ctrl + Click**.

---

# 26. Important Concepts to Remember

## Selection Pane

The **Selection pane** allows you to:

* See the visuals/objects on the report page.
* Identify individual visuals.
* Rename visuals.
* Control their visibility.
* Hide or show visuals.

It is particularly important when working with bookmarks because bookmarks can store different visibility states.

---

## Bookmarks

A **bookmark stores a particular state of the report page**.

In this example:

### Line Chart Amounts bookmark

Stores the state:

> Line chart visible + Column chart hidden

### Column Chart Amounts bookmark

Stores the state:

> Column chart visible + Line chart hidden

Therefore, clicking between bookmarks effectively changes the visible chart.

---

## Bookmark Navigator

The **Bookmark Navigator** provides a user-friendly way of interacting with bookmarks.

Instead of requiring users to open the Bookmarks pane, they can simply use the navigator placed directly on the report page.

---

# 27. Important Rule: Update the Bookmark

One of the most important practical points from this lecture is:

> **After making a change to the visual state associated with a bookmark, you must update the bookmark.**

The process is:

**Make change → Select bookmark → `...` → Update**

If you forget to click **Update**, the bookmark may continue using its previously stored state.

---

# 28. Final Result

After completing the setup, the user gets a single report area where they can switch between:

### Line Chart View

**Line Chart Amounts**

and

### Column Chart View

**Column Chart Amounts**

The charts occupy the same location, so the report remains clean and uncluttered.

The user doesn't have to deal with two charts displayed simultaneously.

Instead, they can select the required view using the **Bookmark Navigator**.

---

# 29. Key Takeaways

* **Bookmarks** can be used to save different states of a Power BI report.
* They can be used to create interactive report experiences.
* In this example, bookmarks are used to switch between a **line chart and column chart**.
* The **Selection pane** controls which chart is visible.
* Two copies of the chart are placed on top of each other.
* One chart is hidden in each bookmark state.
* The bookmarks are named:

  * **Line Chart Amounts**
  * **Column Chart Amounts**
* Always use **... → Update** after changing a bookmark's state.
* A **Bookmark Navigator** provides an easy interface for the user.
* The navigator should remain **visible and accessible**, preferably at the top of the chart area.
* The navigator can be resized and repositioned according to the report design.
* In Power BI Desktop, use **Ctrl + Click** to interact with the navigator while editing.

---

## 30. What Will Be Covered Next?

The next session will extend this concept to another numerical column in the dataset:

> **Remaining Balance / Balance**

The same idea will be used to create different charts based on the **Balance** column and provide the user with the ability to switch between different visualizations representing those insights.
