# Power BI – Creating Report Page 2: Customer Gender Distribution

## 1. Objective of the Session

In this session, the instructor begins creating the **second report page** of the Power BI report.

The main objectives are:

1. Create **Report Page 2**.
2. Use recommendations from the **second Excel sheet** generated/suggested by Perplexity.
3. Create different visuals on the second report page.
4. Start with the first recommended visual:

   > **Customer Gender Distribution**

The instructor also emphasizes that **it is not necessary to implement every recommendation** from the AI tool. We can select the recommendations that are useful for the report.

---

# 2. First Visual: Customer Gender Distribution

The first recommendation selected for Report Page 2 is:

> **Customer Gender Distribution**

### Purpose

This visual helps us understand:

> **The proportion/distribution of customers by gender.**

In other words, it allows us to see how customers are distributed among categories such as:

* Male
* Female
* Blank/unknown

---

# 3. Recommended Visualizations

The Excel sheet suggests that Customer Gender Distribution can be represented using:

* **Donut Chart**, or
* **Stacked Column Chart**

The instructor chooses:

> **Donut Chart**

### Why a Donut Chart?

A donut chart is useful for showing the **proportion of categories within a whole**.

For example:

```text
Total Customers
      ↓
 ┌────┼────┐
Male Female Blank
```

It gives a quick visual understanding of the contribution of each gender category.

---

# 4. DAX Measure Required

The Excel sheet provides a DAX measure for calculating the number of customers.

The measure is based on:

> **Distinct Count of Customer ID**

The concept is:

```DAX
Customer Count by Gender =
DISTINCTCOUNT('Combined Banking Data Set'[Customer ID])
```

The exact table/column reference should be copied from the Excel sheet used in the lecture.

### Why DISTINCTCOUNT?

We want to count **unique customers**, not simply count every row.

If the same customer appears multiple times in the dataset, `DISTINCTCOUNT()` ensures that the customer is counted only once.

---

# 5. Create Report Page 2

The instructor now creates the second report page.

### Step 1: Click the Plus (+) Icon

At the bottom of Power BI Desktop, click:

> **+**

This creates a new report page.

Power BI names it:

> **Page 2**

---

# 6. Existing Measure in the Instructor's File

The instructor mentions that the measure already exists in their Power BI file because they had created it earlier.

Therefore, they delete the existing measure first.

### Important clarification

The instructor specifically says:

> This measure **may not already exist in your system**.

If you don't already have the measure, **do not delete anything**.

Simply follow the normal procedure:

**Measures Table → Right-click → New Measure**

---

# 7. Create the Customer Count by Gender Measure

### Step 1: Select Measures Table

In the Data/Fields pane, locate:

> **Measures Table**

### Step 2: Right-click

Right-click on:

> **Measures Table**

### Step 3: Select New Measure

Choose:

> **New Measure**

### Step 4: Paste the DAX

Use:

**Ctrl + V**

to paste the DAX copied from the Excel sheet.

### Step 5: Press Enter

Press:

> **Enter**

The measure is now created.

The resulting measure is:

> **Customer Count by Gender**

---

# 8. Create the Donut Chart

Now the instructor creates the actual visualization.

### Step 1: Click a Blank Area

Click on an empty area of the Page 2 canvas.

This ensures that a new visual is created.

### Step 2: Select Donut Chart

From the Visualizations pane, select:

> **Donut Chart**

A blank donut chart appears.

---

# 9. Position and Resize the Donut Chart

The instructor then adjusts the chart's position.

The chart is:

* Dragged toward the **right-hand side**
* Positioned appropriately on the page
* Increased in size slightly

### General principle

Resize and position the visual according to the available report-page layout.

---

# 10. Add Customer Count by Gender to the Donut Chart

The measure created earlier is:

> **Customer Count by Gender**

### Steps

1. Find **Customer Count by Gender**.
2. Double-click or drag it.
3. Place it into the:

> **Values** bucket

Therefore:

```text id="j8b3m1"
Values → Customer Count by Gender
```

This determines the numerical value represented by the donut chart.

---

# 11. Add Gender to the Legend

Next, the instructor uses the:

> **Gender**

column.

### Steps

1. Find the **Gender** column.
2. Double-click or drag it.
3. Place it into:

> **Legend**

Therefore:

```text id="t1n1w8"
Legend → Gender
```

The final field configuration is:

| Bucket | Field                    |
| ------ | ------------------------ |
| Values | Customer Count by Gender |
| Legend | Gender                   |

The donut chart now shows customer distribution according to gender.

---

# 12. Important Data Observation: Blank Gender Values

After creating the visual, the instructor observes something important about the dataset.

There are many **blank gender values**.

The instructor mentions that there are a total of **four Customer IDs** for which the gender information is available as categories such as:

* Male
* Female
* Unknown/blank

The transcript specifically describes the available values as:

> **Male, Female, or blank**

### Important point

The instructor does **not** clean or remove the blank values.

Instead, the data is left as it is.

The reason is that:

> **This is how the available dataset is structured.**

Therefore, the blank category remains visible in the donut chart.

---

# 13. Why We Don't Remove the Blank Values

The instructor explains that the dataset simply contains gender information for only some customers.

Therefore, rather than modifying the underlying data at this point, the visual is allowed to represent the actual available data.

### Key principle

> **Don't automatically remove missing values from a visualization unless the business requirement calls for it.**

Missing/blank data can itself be an important insight.

---

# 14. Copy Formatting from Page 1

The instructor now wants the new donut chart to have the same formatting as the **pie chart on Report Page 1**.

This helps maintain a consistent dashboard design.

### Steps

1. Go to:

> **Page 1**

2. Select the existing **Pie Chart**.
3. Go to the:

> **Home** tab.

4. Select:

> **Format Painter**

5. Return to:

> **Page 2**

6. Click the new **Donut Chart**.

The donut chart now inherits the formatting from the pie chart on Page 1.

---

# 15. Why Use Format Painter?

The **Format Painter** avoids having to manually reproduce the same formatting.

It helps maintain:

* Consistent colors
* Consistent fonts
* Consistent labels
* Consistent visual appearance
* Consistent dashboard design

### General workflow

```text
Existing Visual
      ↓
Format Painter
      ↓
New Visual
```

---

# 16. Customize Donut Chart Colors

After applying the previous chart's formatting, the instructor wants to customize the colors for the different gender categories.

The instructor uses the:

> **Format Visual**

pane.

---

# 17. Open Format Visual

With the donut chart selected:

1. Click the chart.
2. Open:

> **Format Visual**

The instructor then works with the category/color settings.

---

# 18. Change the Blank Category Color

The instructor first selects:

> **Blank**

under the category/color settings.

Then the color can be changed to any color of choice.

The instructor selects a suitable color.

### Important

The exact color isn't the main concept.

The important point is:

> **Individual categories in the donut chart can be assigned different colors.**

---

# 19. Change the Female Color

Next, the instructor selects:

> **Female**

and changes its color.

The instructor chooses approximately:

> **Pink**

### Result

```text
Female → Pink
```

Again, the exact shade can be selected according to the dashboard design.

---

# 20. Change the Male Color

Next, the instructor selects:

> **Male**

and chooses another color.

The instructor demonstrates that the user can select **any suitable color**.

### Example

```text
Male → Selected Color
Female → Pink
Blank → Selected Color
```

The important concept is the ability to format each category independently.

---

# 21. Donut Chart Rotation

The instructor then demonstrates another formatting option:

> **Rotation**

### Purpose

The donut chart can be rotated so that the different categories appear at different positions around the donut.

### Steps

1. Select the donut chart.
2. Open:

> **Format Visual**

3. Find the:

> **Rotation**

setting.
4. Adjust the rotation value as required.

This allows you to control where the Male, Female, and Blank sections appear within the donut.

---

# 22. Why Rotate a Donut Chart?

Rotation can be useful for:

* Improving visual balance
* Positioning an important category appropriately
* Making labels easier to read
* Matching the layout/design of other visuals

The instructor notes that you can rotate the donut according to your convenience.

---

# 23. Donut Chart Spacing

Another formatting option demonstrated is:

> **Spacing**

The instructor finds the **Spacing** setting under the formatting options.

This setting can be used to modify the appearance of the donut.

---

# 24. Adjusting the Inner Radius

Within the spacing-related settings, the instructor demonstrates that the **inner radius** can be changed.

### If you reduce the inner radius

The donut's center hole becomes:

> **Smaller**

The colored ring becomes relatively thicker.

### If you increase the inner radius

The center hole becomes:

> **Larger**

The colored ring becomes relatively thinner.

Conceptually:

```text
Smaller Inner Radius

     ███████
   ██       ██
  ██         ██
   ██       ██
     ███████


Larger Inner Radius

    █████████
   ██       ██
  ██         ██
   ██       ██
    █████████
```

The exact appearance depends on the selected radius.

---

# 25. Final Donut Chart Configuration

The completed visualization represents:

> **Customer Count by Gender**

### Measure

> **Customer Count by Gender**

Based on a distinct count of Customer ID.

### Legend

> **Gender**

### Chart

> **Donut Chart**

### Categories

* Male
* Female
* Blank

### Formatting

* Formatting copied from Page 1
* Individual category colors customized
* Female can be represented with pink
* Male assigned a separate color
* Blank assigned a separate color
* Rotation can be adjusted
* Inner radius can be adjusted through spacing settings

---

# 26. Complete Step-by-Step Workflow

For revision, the complete process is:

### Step 1 – Open the Excel recommendation

Go to the **second Excel sheet** suggested by Perplexity.

Select:

> **Customer Gender Distribution**

---

### Step 2 – Understand the objective

The goal is to determine:

> **The proportion of customers by gender.**

---

### Step 3 – Copy the DAX

Copy the highlighted DAX measure from the Excel sheet.

Use:

**Ctrl + A → Ctrl + C**

---

### Step 4 – Create Report Page 2

In Power BI:

> **Click the + icon**

A new page is created:

> **Page 2**

---

### Step 5 – Create the Measure

Go to:

**Measures Table → Right-click → New Measure**

Paste the copied DAX:

**Ctrl + V**

Press:

**Enter**

---

### Step 6 – Create the Visual

Click a blank area of the Page 2 canvas.

Select:

> **Donut Chart**

---

### Step 7 – Position and Resize

Move the donut chart toward the desired position and resize it as needed.

---

### Step 8 – Add the Measure

Drag:

> **Customer Count by Gender → Values**

---

### Step 9 – Add Gender

Drag:

> **Gender → Legend**

---

### Step 10 – Inspect the Data

Observe that the dataset contains:

* Male
* Female
* Blank

The blank values are retained.

---

### Step 11 – Copy Formatting

Go to:

> **Page 1**

Select the existing **Pie Chart**.

Then:

> **Home → Format Painter**

Return to Page 2 and click the donut chart.

---

### Step 12 – Customize Colors

Select the donut chart.

Go to:

> **Format Visual**

Change the colors for:

* Blank
* Female
* Male

For example:

> Female → Pink

---

### Step 13 – Adjust Rotation

Under the formatting options, adjust:

> **Rotation**

if required.

---

### Step 14 – Adjust Spacing/Inner Radius

Go to:

> **Spacing**

Adjust the:

> **Inner Radius**

* Reduce it → smaller hole
* Increase it → larger hole

---

# 27. Important Power BI Concepts

## A. DISTINCTCOUNT

`DISTINCTCOUNT()` counts unique values.

For customer analysis, this is useful because one customer may appear in multiple records.

Conceptually:

```text
Customer IDs:

101
101
102
103
103

DISTINCTCOUNT = 3
```

rather than:

```text
COUNT = 5
```

Therefore, distinct count is appropriate for counting unique customers.

---

## B. Legend

The **Legend** determines how the visual is divided into categories.

Here:

> **Gender → Legend**

This causes the donut to be divided into Male, Female, and Blank categories.

---

## C. Values

The **Values** bucket contains the numerical calculation represented by the visual.

Here:

> **Customer Count by Gender → Values**

---

## D. Donut Chart

A donut chart is useful for displaying:

> **Category proportions within a total**

For this report:

> Customer distribution by gender.

---

## E. Format Painter

Used to copy the formatting of one visual to another.

Here:

```text
Page 1 Pie Chart
       ↓
Format Painter
       ↓
Page 2 Donut Chart
```

---

## F. Rotation

Controls the orientation/starting position of the segments in the donut chart.

---

## G. Inner Radius

Controls the size of the hole in the middle of the donut.

```text
Decrease Inner Radius
        ↓
Smaller hole
        ↓
Thicker donut

Increase Inner Radius
        ↓
Larger hole
        ↓
Thinner donut
```

---

# 28. Important Observations from the Lecture

### Observation 1

The instructor starts working on **Report Page 2**.

### Observation 2

The recommendations come from a **second Excel sheet suggested by Perplexity**.

### Observation 3

It is **not necessary to implement every AI recommendation**.

Only useful recommendations need to be selected.

### Observation 4

The first selected recommendation is:

> **Customer Gender Distribution**

### Observation 5

The AI recommends:

* Donut Chart
* Stacked Column Chart

The instructor chooses:

> **Donut Chart**

### Observation 6

The measure uses a **distinct count of Customer ID**.

### Observation 7

The measure is stored in the:

> **Measures Table**

### Observation 8

The donut chart uses:

> **Customer Count by Gender → Values**

and:

> **Gender → Legend**

### Observation 9

The dataset contains **blank gender values**.

The instructor leaves them as they are.

### Observation 10

The formatting from the Page 1 pie chart is reused using:

> **Format Painter**

### Observation 11

The individual gender categories can be given different colors.

### Observation 12

The donut chart can be rotated using:

> **Rotation**

### Observation 13

The donut's center/hole can be resized using:

> **Spacing → Inner Radius**

---

# 29. Quick Revision Sheet

### Report Page

**Page 2**

### Visual

**Customer Gender Distribution**

### Chart

**Donut Chart**

### Measure

**Customer Count by Gender**

### Calculation

**Distinct Count of Customer ID**

### Fields

```text
Values → Customer Count by Gender
Legend → Gender
```

### Categories

```text
Male
Female
Blank
```

### Formatting

```text
Page 1 Pie Chart
      ↓
Format Painter
      ↓
Page 2 Donut Chart
```

### Additional Formatting

```text
Gender → Individual Colors
Rotation → Adjust as required
Spacing → Adjust
Inner Radius → Increase/Decrease as required
```

---

# 30. One-Line Workflow to Remember

**Excel Recommendation → Customer Gender Distribution → Copy DAX → Create Page 2 → Measures Table → New Measure → Donut Chart → Customer Count by Gender to Values → Gender to Legend → Keep Blank Values → Format Painter from Page 1 → Customize Colors → Adjust Rotation → Adjust Inner Radius**
