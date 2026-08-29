# Detailed Notes — Bar Chart, Conditional Column & Line Chart in Power BI

This lecture continues building the **Insurance Data Analysis Power BI report**. Three major things are covered:

1. Creating and formatting a **Stacked Bar Chart** for Premium Amount by Policy Type
2. Creating an **Age Group** column using a Conditional Column in Power Query
3. Creating and formatting a **Line Chart** for Claim Amount by Age Group
4. Understanding how visuals and slicers **interact and filter the entire report page**

---

# 1. Add a Stacked Bar Chart

## Objective

Create a bar chart showing:

> **Premium Amount by Policy Type**

The report should allow us to compare the total premium amount across different insurance policy types.

---

## 2. Create the Bar Chart

### Steps

1. Click on a **blank area of the report canvas**.
2. Select:

> **Stacked Bar Chart**

3. A blank bar chart will be created.
4. Resize the chart according to the report layout.

---

# 3. Add Policy Type to the Bar Chart

The **Policy Type** column will represent the different categories.

### Steps

1. Locate **Policy Type** in the Data pane.
2. Double-click it or drag it to:

> **Y-axis**

The policy types are now represented vertically.

---

# 4. Add Premium Amount

Next, we need the total premium for each policy type.

### Steps

1. Locate **Premium Amount** in the Data pane.
2. Drag it into the:

> **X-axis**

Power BI automatically aggregates the numeric field.

It therefore displays:

> **Sum of Premium Amount**

for each Policy Type.

Conceptually:

```text
Policy Type → Category
Premium Amount → Sum
```

The chart now compares total premium amounts across the different policy categories.

---

# 5. Format the Y-Axis

The instructor now formats the vertical axis.

### Steps

1. Select the bar chart.
2. Click:

> **Format Your Visual**

3. Expand:

> **Y-axis**

---

## Remove Y-axis Title

The text such as **Policy Type** appearing as the axis title is unnecessary.

Change:

> **Title → Off**

The policy names themselves remain visible.

---

## Format Y-axis Values

The policy names are still required.

Under the font formatting:

* Change font to **Trebuchet MS**
* Increase font size to approximately **10**
* Make the text **Bold**

This improves readability.

---

# 6. Format the X-Axis

The horizontal axis contains the premium values.

However, the instructor decides not to display either the values or the axis title because the values will instead be shown through data labels.

### Steps

Under **X-axis**:

* **Values → Off**
* **Title → Off**

Then collapse the X-axis section.

---

# 7. Enable Data Labels

Since the X-axis values have been hidden, users still need to know the actual premium amount represented by each bar.

Therefore:

> **Data Labels → On**

Now the actual values are displayed directly on the bars.

---

# 8. Format Data Labels

### Steps

1. Expand **Data Labels**.
2. Locate the **Values** formatting.
3. Change the font to:

> **Trebuchet MS**

4. Increase the font size as appropriate.
5. Make the values **Bold**.

This makes the premium values easier to read.

---

# 9. Change Bar Color

The instructor wants consistency with the colors already used in the report.

### Steps

1. Expand:

> **Bars**

2. Locate the color option.
3. Select the same color used for the Ribbon Chart.

This creates a more consistent visual theme across the report.

---

# 10. Format the Bar Chart Title

The default title is something similar to:

> **Sum of Premium Amount by Policy Type**

The instructor wants a cleaner title:

> **Premium Amount by Policy Type**

### Steps

1. Select the bar chart.
2. Go to:

> **General → Titles**

3. Select the title text.
4. Remove **"Sum of"**.
5. Ensure proper spacing:

   * Premium Amount
   * by
   * Policy Type

Final title:

> **Premium Amount by Policy Type**

---

## Format the Title

The title can then be customized with:

* Preferred font
* Bold
* Italic
* Underline
* Center alignment

---

# 11. Add a Border

A border can be added to make the visual stand out against the dark background.

### Steps

1. Go to:

> **General → Effects**

2. Turn:

> **Visual border → On**

3. Expand **Visual border**.
4. Change the border color to:

> **White**

The bar chart now has a white outline.

---

# 12. Need for an Age Group Column

The next requirement is to create another visual showing:

> **Claim Amount for different age groups**

However, the existing dataset only contains an:

> **Age**

column.

There is no:

> **Age Group**

column.

Therefore, a new calculated/category column needs to be created in **Power Query Editor**.

---

# 13. Open Power Query Editor

### Steps

From Power BI Desktop:

1. Go to the **Home** tab.
2. Click:

> **Transform Data**

This opens the **Power Query Editor**.

---

# 14. Examine the Age Column

Before creating the age groups, the instructor checks the existing Age data.

The Age column contains customer ages.

The data profiling is changed to:

> **Column profiling based on entire dataset**

The range is:

* **Minimum Age = 18**
* **Maximum Age = 87**

Therefore, the dataset contains customers between:

> **18 and 87 years**

This information is used to create meaningful age categories.

---

# 15. Create an Age Group Using Conditional Column

The instructor uses a **Conditional Column**.

### Steps

1. Go to:

> **Add Column**

2. Select:

> **Conditional Column**

A dialog box appears.

---

# 16. Define the Age Group Column

The new column is named:

> **Age Group**

Instead of the default **Custom**, enter:

> **Age Group**

---

# 17. First Condition — Young Adult

The first condition is:

> If Age ≤ 24

Then assign:

> **Young Adult**

Conceptually:

```text
IF Age <= 24
THEN "Young Adult"
```

---

# 18. Second Condition — Adult

Click:

> **Add Clause**

Create the second condition:

> If Age ≤ 60

Assign:

> **Adult**

Conceptually:

```text
IF Age <= 60
THEN "Adult"
```

Because the first condition has already captured ages up to 24, the second condition effectively captures ages:

> **25–60**

---

# 19. Third Condition — Elder

For all remaining ages, assign:

> **Elder**

Conceptually, the final categorization becomes:

| Age Range | Age Group   |
| --------- | ----------- |
| 18–24     | Young Adult |
| 25–60     | Adult       |
| 61–87     | Elder       |

The third category acts as the **Else** condition.

---

# 20. Create the Conditional Column

After configuring the conditions:

1. Click:

> **OK**

Power Query creates a new column:

> **Age Group**

The new column contains three categories:

* Young Adult
* Adult
* Elder

---

# 21. Change Age Group Data Type

Initially, the newly created column may have an **Any** data type.

The instructor changes it to:

> **Text**

### Steps

1. Select **Age Group**.
2. Change its data type to:

> **Text**

This is appropriate because Age Group contains text categories rather than numerical values.

---

# 22. Understanding Applied Steps

Power Query records every transformation in the:

> **Applied Steps**

section.

After creating Age Group and changing its type, you can see steps similar to:

```text
Added Conditional Column
Changed Type
```

The exact order depends on the actions performed.

---

# 23. Review the Conditional Column Step

The conditional column step can be inspected.

### Steps

1. Locate **Added Conditional Column** under Applied Steps.
2. Click its **gear icon**.

The same conditions used to create the Age Group column will appear.

This allows you to review or modify the transformation.

---

# 24. Delete an Applied Step

Power Query allows individual transformation steps to be removed.

For example, if you want to remove:

> **Changed Type**

you can delete that step.

The subsequent state of the query changes accordingly.

This demonstrates that Power Query transformations are stored as a sequence of steps rather than being permanent manual changes to the raw data.

---

# 25. Importance of Applied Steps

The **Applied Steps** section is important because it allows you to:

* Review transformations
* Go back to an earlier transformation
* Modify transformations
* Delete unnecessary transformations
* Understand how the final dataset was created

For example:

```text
Original Data
     ↓
Added Conditional Column
     ↓
Changed Type
     ↓
Final Dataset
```

---

# 26. Close & Apply the Power Query Changes

Once the Age Group column has been created:

1. Go to the **Home** tab in Power Query Editor.
2. Click the dropdown associated with the close option.
3. Select:

> **Close & Apply**

This does two things:

1. Applies the Power Query transformations.
2. Returns you to the Power BI Report View.

Power BI may take some time while:

> **Loading data to the model**

The dataset contains:

> **10,000 rows**

---

# 27. Add a Line Chart

Now that **Age Group** exists in the model, it can be used to create the next visual.

The objective is:

> **Claim Amount by Age Group**

---

## 28. Create the Line Chart

### Steps

1. Click on a blank area of the canvas.
2. Select:

> **Line Chart**

3. Resize the chart.

---

# 29. Add Age Group to X-Axis

### Steps

1. Locate **Age Group** in the Data pane.
2. Drag it into:

> **X-axis**

The categories become:

* Adult
* Elder
* Young Adult

---

# 30. Add Claim Amount to Y-Axis

### Steps

1. Locate **Claim Amount**.
2. Drag it into:

> **Y-axis**

Power BI aggregates it as:

> **Sum of Claim Amount**

The line chart therefore shows the total claim amount for each age group.

---

# 31. Format the X-Axis

The instructor wants to retain the actual categories but remove the axis title.

### Steps

Under **X-axis**:

* Keep the values/categories visible
* Turn:

> **Title → Off**

The labels such as:

* Adult
* Elder
* Young Adult

remain visible.

---

## Format X-Axis Font

The instructor also changes:

* Font style
* Font size
* Bold formatting

The font is adjusted to match the rest of the report.

---

# 32. Format the Y-Axis

The instructor decides not to display the Y-axis values or title.

### Steps

Under **Y-axis**:

* **Values → Off**
* **Title → Off**

This creates a cleaner visual.

---

# 33. Gridlines

The instructor also checks the gridline setting.

The gridlines are kept:

> **Off**

This avoids unnecessary visual clutter.

---

# 34. Change the Line Color

The default line color is changed to match the color theme used throughout the report.

### Steps

1. Expand:

> **Lines**

2. Locate the line color.
3. Change it from the default blue to the same color used in the other visuals.

This creates visual consistency.

---

# 35. Enable Markers

Markers are added to the line chart.

### Steps

Under the line formatting options:

> **Markers → On**

Markers make individual data points easier to identify.

---

# 36. Add a Shaded Area

The instructor also enables the shaded area beneath/around the line.

### Steps

Change the appropriate:

> **Shaded area → On**

This adds additional visual emphasis to the line chart.

---

# 37. Enable Data Labels

Because the Y-axis values have been removed, the actual claim amounts still need to be visible.

Therefore:

> **Data Labels → On**

The numerical claim amounts now appear directly on the chart.

---

# 38. Format Data Labels

### Steps

1. Expand **Data Labels**.
2. Scroll to the values formatting.
3. Change the font style.
4. Increase the font size.
5. Make the values **Bold**.

This makes the numerical values clearly visible.

---

# 39. Format the Line Chart Title

The default title would be similar to:

> **Sum of Claim Amount by Age Group**

The instructor changes this to:

> **Claim Amount by Age Group**

### Steps

1. Select the Line Chart.
2. Go to:

> **General → Titles**

3. Remove:

> **Sum of**

4. Keep proper spacing.

Final title:

> **Claim Amount by Age Group**

---

# 40. Format the Title

The title can be customized with:

* Font style
* Increased font size
* Bold
* Italic
* Underline
* Center alignment

The instructor chooses a centered title to match the other visuals.

---

# 41. Add a Border to the Line Chart

### Steps

1. Select the Line Chart.
2. Go to:

> **Format Your Visual → General → Effects**

3. Turn:

> **Visual border → On**

4. Expand Visual Border.
5. Set the border color to:

> **White**

The line chart now matches the bordered style of the other visuals.

---

# 42. Report Interactivity

An important part of this lecture is understanding how all the visuals interact with each other.

The instructor demonstrates this by selecting a category from the Ribbon Chart.

For example, selecting a particular **Claim Status** filters the other visuals on the page.

---

# 43. Example — Filtering Through Ribbon Chart

Suppose a user selects:

> **Rejected**

The entire report page can respond to that selection.

The following can be filtered:

* Male/Female counts
* Premium Amount by Policy Type
* Premium Amount card
* Coverage Amount card
* Claim Amount card
* Line Chart
* Slicers
* Other visuals

This demonstrates **cross-filtering/cross-highlighting** between visuals.

---

# 44. Filtering Through Slicers

The same behavior works in the opposite direction.

Suppose we select a particular:

> **Customer ID**

from the Customer ID slicer.

The entire page is filtered according to that customer.

The instructor gives an example involving:

> **Customer C1**

The customer is identified as female, and only one claim was raised for that customer.

That claim was:

> **Rejected**

Therefore, the claim amount paid is:

> **₹0**

while the report shows the associated premium and coverage values.

---

# 45. Slicers Become Dependent on Other Filters

Once a customer is selected, the other slicers also become filtered.

For example:

```text
Customer ID = C1
        ↓
Claim Number slicer
        ↓
Only claims related to C1
```

And:

```text
Customer ID = C1
        ↓
Policy Number slicer
        ↓
Only policies related to C1
```

This is an important Power BI interaction.

The available values in one slicer can change based on selections made elsewhere.

---

# 46. Clear Selections

After applying filters, you can return the report to its original state.

The instructor mentions clearing the selections from the slicers.

This allows you to:

> Remove the applied filter context and return to the overall dataset.

---

# 47. Visuals Added/Available After This Lecture

At this stage, the report contains several different types of visuals.

| Visual               | Purpose                          |
| -------------------- | -------------------------------- |
| Policy Number Slicer | Filter policies                  |
| Claim Number Slicer  | Filter claims                    |
| Customer ID Slicer   | Filter customers                 |
| Premium Amount Card  | Total premium                    |
| Coverage Amount Card | Total coverage                   |
| Claim Amount Card    | Total claim amount               |
| Multi-row Card       | Male/Female customer counts      |
| Ribbon Chart         | Number of claims by Claim Status |
| Stacked Bar Chart    | Premium Amount by Policy Type    |
| Line Chart           | Claim Amount by Age Group        |
| Text Box             | Company name                     |

---

# 48. Data Transformation Added in This Lecture

A new column was created:

> **Age Group**

Using the existing **Age** column.

### Final logic

| Condition | Result      |
| --------- | ----------- |
| Age ≤ 24  | Young Adult |
| Age ≤ 60  | Adult       |
| Otherwise | Elder       |

Given the dataset's observed age range of **18–87**, the effective groups are:

```text
18–24  → Young Adult
25–60  → Adult
61–87  → Elder
```

---

# 49. Key Power Query Concepts Learned

### Conditional Column

Used to create a new column based on conditions.

Path:

> **Transform Data → Add Column → Conditional Column**

---

### Applied Steps

Every transformation is recorded in Power Query's:

> **Applied Steps**

You can:

* Review steps
* Edit steps
* Delete steps
* Go back to previous steps

---

### Data Type

After creating a categorical column such as Age Group, verify its data type.

For Age Group:

> **Text**

is appropriate.

---

# 50. Key Power BI Visualization Concepts Learned

### Bar Chart

Useful for comparing numerical values across categories.

Here:

> **Premium Amount by Policy Type**

---

### Line Chart

Used here to compare:

> **Claim Amount by Age Group**

---

### Data Labels

Useful when axis values are hidden but the actual numerical values still need to be displayed.

---

### Markers

Make individual points on a line chart easier to identify.

---

### Shaded Area

Adds visual emphasis to the line chart.

---

### Visual Border

Creates a defined boundary around a visual.

Path:

> **Format Your Visual → General → Effects → Visual Border**

---

# 51. Overall Flow of This Lecture

The complete workflow can be summarized as:

```text
Create Stacked Bar Chart
        ↓
Policy Type → Y-axis
Premium Amount → X-axis
        ↓
Format Axes
        ↓
Enable Data Labels
        ↓
Format Bars & Title
        ↓
Add Border
        ↓
Open Power Query
        ↓
Inspect Age Column
        ↓
Age = 18–87
        ↓
Add Conditional Column
        ↓
Create Age Group
        ↓
18–24 → Young Adult
25–60 → Adult
61–87 → Elder
        ↓
Change Age Group → Text
        ↓
Close & Apply
        ↓
Create Line Chart
        ↓
Age Group → X-axis
Claim Amount → Y-axis
        ↓
Format Axes
        ↓
Enable Markers
        ↓
Enable Shaded Area
        ↓
Enable Data Labels
        ↓
Format Title & Border
        ↓
Test Visual Interactions
```

## Key Takeaway

This lecture demonstrates an important real-world Power BI workflow: **when the existing dataset doesn't contain a category needed for analysis, create it during data transformation in Power Query, apply the changes, and then use the new column in your report visuals.** It also reinforces that Power BI visuals are interconnected—selecting a category in one visual or slicer can dynamically filter the other visuals on the page.
