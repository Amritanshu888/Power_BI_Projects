# Detailed Notes — Creating Credit Score Bins & Median Loan Amount Line Chart

## 1. Objective of the Session

This session covers two main tasks for the second report page, **Applicant Demographics and Financial Profile**:

1. Creating a **Credit Score Bins** calculated column using nested `IF` statements.
2. Creating and formatting a **line chart** to represent the **Median Loan Amount by Credit Score Category**.

The line chart will use:

* **Credit Score Bins** on the X-axis.
* **Median Loan Amount** on the Y-axis.

---

# 2. Inspect the Credit Score Column

Before creating the bins, the instructor first checks the range of credit score values available in the dataset.

### Steps

1. Go to **Table View** in Power BI.
2. Collapse:

   * **Measures Table 1**
   * **Measures Table 2**
3. Select the **Loan Default** table.
4. Scroll toward the left until you find the **Credit Score** column.

The Credit Score column contains the credit score values that need to be grouped.

---

## 3. Find the Minimum and Maximum Credit Scores

To understand the range of the data, sort the Credit Score column.

### Find the minimum

1. Click the dropdown on the **Credit Score** column.
2. Sort it in **ascending order**.

The minimum credit score is:

**300**

### Find the maximum

1. Sort the Credit Score column in **descending order**.

The maximum credit score is:

**849**

Therefore, the credit score range in this dataset is:

**300 to 849**

This range is used to design the credit score categories.

---

# 4. Return to Report View

After checking the credit score range:

1. Return to **Report View**.
2. The previously created card visual was only used to validate the median.
3. Since it is no longer required, remove the card visual.

### Why remove the card?

The card was created specifically for **validation** of the median calculation. It is not part of the final report visual being built in this session.

---

# 5. Create the Credit Score Bins Column

The next step is to create a new calculated column in the **Loan Default** table.

The instructor uses a **nested IF statement** to divide credit scores into four categories:

| Credit Score | Category |
| -----------: | -------- |
|        ≤ 400 | Very Low |
|      401–450 | Low      |
|      451–650 | Medium   |
|        > 650 | High     |

---

# 6. Create a New Column

### Steps

1. In the Fields/Data pane, locate the **Loan Default** table.
2. Right-click **Loan Default**.
3. Select **New Column**.

Power BI will open the DAX formula bar.

If the formula bar takes some time to open, wait for it to become available.

---

# 7. Name the Calculated Column

The calculated column is named:

**Credit Score Bins**

This column will store the category corresponding to each applicant's credit score.

---

# 8. Create the Nested IF Logic

The instructor uses multiple `IF` functions inside one another.

The logic is:

### First condition

If Credit Score is **less than or equal to 400**:

→ **Very Low**

### Second condition

Otherwise, if Credit Score is **less than or equal to 450**:

→ **Low**

### Third condition

Otherwise, if Credit Score is **less than or equal to 650**:

→ **Medium**

### Final ELSE condition

For all remaining values:

→ **High**

Because the conditions are evaluated sequentially, the categories effectively become:

* **300–400 → Very Low**
* **401–450 → Low**
* **451–650 → Medium**
* **651–849 → High**

---

# 9. DAX Formula for Credit Score Bins

The calculated column can be written as:

```DAX id="fomz8f"
Credit Score Bins =
IF(
    'Loan Default'[Credit Score] <= 400,
    "Very Low",
    IF(
        'Loan Default'[Credit Score] <= 450,
        "Low",
        IF(
            'Loan Default'[Credit Score] <= 650,
            "Medium",
            "High"
        )
    )
)
```

### Understanding the formula

The formula evaluates from top to bottom.

For example:

### Credit Score = 380

* Is 380 ≤ 400? → **Yes**
* Result = **Very Low**

### Credit Score = 425

* Is 425 ≤ 400? → No
* Is 425 ≤ 450? → Yes
* Result = **Low**

### Credit Score = 600

* Is 600 ≤ 400? → No
* Is 600 ≤ 450? → No
* Is 600 ≤ 650? → Yes
* Result = **Medium**

### Credit Score = 700

* Is 700 ≤ 400? → No
* Is 700 ≤ 450? → No
* Is 700 ≤ 650? → No
* ELSE → **High**

---

# 10. Important Point About Nested IF

The `IF` functions are **nested** because another `IF` is placed inside the `else` portion of the previous `IF`.

Conceptually:

```text
IF Credit Score <= 400
    → Very Low
ELSE
    IF Credit Score <= 450
        → Low
    ELSE
        IF Credit Score <= 650
            → Medium
        ELSE
            → High
```

This is a useful technique for creating categories from continuous numerical values.

---

# 11. Complete the Calculated Column

After entering the DAX:

1. Press **Enter**.
2. Power BI calculates the column for all rows.
3. Collapse the formula bar if required.

The **Credit Score Bins** column is now available in the Loan Default table.

It contains four possible categories:

* **Very Low**
* **Low**
* **Medium**
* **High**

---

# 12. Create the Line Chart

The next objective is to create a line chart showing the median loan amount for each credit score category.

Instead of creating the chart completely from scratch, the instructor reuses an existing chart from the first report page.

---

# 13. Copy an Existing Chart

### Steps

1. Click the blank area of the report canvas if required.
2. Go to the first report page:
   **Loan Default — An Overview**
3. Select an existing chart.
4. The instructor chooses the **first chart**.
5. Press **Ctrl + C**.
6. Navigate to the second report page.
7. Press **Ctrl + V**.

This creates a copy of the existing chart on the second page.

### Why copy an existing visual?

Copying an existing chart allows you to reuse its:

* Basic formatting
* Size
* Position
* Visual configuration
* General appearance

The fields can then be replaced with the fields required for the new analysis.

---

# 14. Remove the Existing Fields

The copied chart contains fields from the original visualization, so these need to be removed.

The original chart contains:

* **Loan Purpose** on the X-axis.
* **Loan Amount** on the Y-axis.

### Steps

Remove:

**Loan Purpose** from the X-axis bucket.

Then remove:

**Loan Amount** from the Y-axis bucket.

The copied chart is now effectively a blank chart ready for the new analysis.

---

# 15. Add Median Loan Amount to the Y-Axis

The previously created measure:

**Median by Credit Score Bins**

will be used as the value on the vertical axis.

### Steps

1. Select the copied/blank chart.
2. Locate **Measures Table 2**.
3. Find:

**Median by Credit Score Bins**

4. Drag and drop it into the **Y-axis** bucket.

The chart will now calculate/display the median loan amount.

---

# 16. Add Credit Score Bins to the X-Axis

Next, use the calculated Credit Score Bins column.

### Steps

1. Locate the **Loan Default** table.
2. Find:

**Credit Score Bins**

3. Drag and drop it into the **X-axis** bucket.

Now Power BI calculates the median loan amount separately for each credit score category.

---

# 17. Result of the Line Chart

The chart now represents:

> **Median Loan Amount by Credit Score Category**

The categories are:

* Very Low
* Low
* Medium
* High

The vertical axis represents the **median loan amount** for each category.

Therefore, the visual allows you to compare the median loan amount across different credit score groups.

---

# 18. Change the Line Color

The appearance of the line can be customized.

### Steps

1. Select the line chart.
2. Click **Format your visual**.
3. Find the **Lines** section.
4. Choose the line color.
5. Select any color according to your report design/preferences.

The instructor notes that the line color can be changed as required.

---

# 19. Change the Chart Title

The default title needs to be changed because the copied visual originally represented a different analysis.

The new title should describe what the chart actually represents.

### Steps

1. Select the chart.
2. Open **Format your visual**.
3. Go to:
   **General → Title**
4. Change the title to:

**Median Loan Amount by Credit Score Category**

This makes the purpose of the visual immediately clear to the report user.

---

# 20. Resize the Chart

The chart can be resized according to the available space on the report page.

### Steps

1. Select the chart.
2. Drag its edges/corners.
3. Adjust its width and height to fit appropriately on the page.

The instructor suggests resizing the chart slightly.

---

# 21. Additional Line Chart Formatting

Power BI provides several options for customizing the appearance and behavior of the line.

These settings are available under the **Lines** section of the Format pane.

---

## 22. Change the Line Type

The line can be configured as either a smoother or more linear representation.

The instructor mentions options such as:

* **Smooth**
* **Linear**

The instructor chooses:

**Smooth**

This makes the line appear curved/smoother between data points.

---

# 23. Change the Interpolation Method

The line can also be configured using different interpolation methods.

The instructor mentions:

* **Monotone**
* **Cardinal**

These options affect how the line is drawn between points.

The exact choice depends on the desired visual appearance.

---

# 24. Configure Markers

Markers are the points displayed on the line corresponding to each category/value.

The instructor demonstrates that markers can also be customized.

### Steps

1. Open the formatting options for the line chart.
2. Locate the **Markers** settings.
3. Choose the desired marker style.

The instructor selects one of the available marker types.

Markers make individual data points easier to identify.

---

# 25. Change Line Width

The width/thickness of the line can also be adjusted.

The instructor points out that the current line width is:

**3**

This can be changed to a smaller value, such as:

**1**

### Why change line width?

Changing the line width allows you to control how prominent the line appears and helps match the overall report design.

---

# 26. Final Visual Structure

The completed chart essentially contains:

### X-axis

**Credit Score Bins**

with categories:

* Very Low
* Low
* Medium
* High

### Y-axis

**Median by Credit Score Bins**

representing the median loan amount.

### Chart type

**Line chart**

### Title

**Median Loan Amount by Credit Score Category**

---

# 27. Complete Workflow

```text
Open Table View
      ↓
Collapse Measures Table 1 & Measures Table 2
      ↓
Open Loan Default table
      ↓
Locate Credit Score
      ↓
Sort ascending → Minimum = 300
      ↓
Sort descending → Maximum = 849
      ↓
Return to Report View
      ↓
Delete temporary median validation card
      ↓
Right-click Loan Default
      ↓
New Column
      ↓
Name = Credit Score Bins
      ↓
Create nested IF DAX
      ↓
≤ 400 → Very Low
≤ 450 → Low
≤ 650 → Medium
Else → High
      ↓
Create calculated column
      ↓
Go to Page 1
      ↓
Copy existing chart
      ↓
Go to Page 2
      ↓
Paste chart
      ↓
Remove Loan Purpose from X-axis
      ↓
Remove Loan Amount from Y-axis
      ↓
Add Median by Credit Score Bins → Y-axis
      ↓
Add Credit Score Bins → X-axis
      ↓
Format line
      ↓
Change line color if required
      ↓
Change title
      ↓
"Median Loan Amount by Credit Score Category"
      ↓
Resize chart
      ↓
Optional formatting:
Smooth line
Monotone/Cardinal
Markers
Line width
```

---

# 28. Key DAX Formula to Remember

The main DAX concept introduced in this session is **nested IF**.

```DAX id="zt2p7x"
Credit Score Bins =
IF(
    'Loan Default'[Credit Score] <= 400,
    "Very Low",
    IF(
        'Loan Default'[Credit Score] <= 450,
        "Low",
        IF(
            'Loan Default'[Credit Score] <= 650,
            "Medium",
            "High"
        )
    )
)
```

### Logic

| Condition                    | Result   |
| ---------------------------- | -------- |
| Credit Score ≤ 400           | Very Low |
| Credit Score > 400 and ≤ 450 | Low      |
| Credit Score > 450 and ≤ 650 | Medium   |
| Credit Score > 650           | High     |

---

# 29. Important Power BI Concepts From This Session

### Calculated Column vs. Measure

The **Credit Score Bins** is a **calculated column** because a category needs to be generated for every individual row based on that row's Credit Score.

The **Median by Credit Score Bins** is a **measure** because the median needs to be dynamically calculated based on the filter/grouping context of the visual.

### Nested IF

Nested `IF` statements are useful when a numerical field needs to be converted into multiple categories.

### Reusing visuals

Existing visuals can be copied between report pages using:

**Ctrl + C → Ctrl + V**

This is often faster and helps maintain consistent report formatting.

### Dynamic grouping

Putting **Credit Score Bins** on the X-axis and the median measure on the Y-axis causes Power BI to calculate the median separately for each credit score category.

### Formatting

Line charts can be customized through the Format pane, including:

* Line color
* Line type
* Interpolation
* Markers
* Line width
* Title
* Size/position

---

# 30. Final Outcome

By the end of the session, the second report page has a new analytical visual that shows:

**Median Loan Amount by Credit Score Category**

using four credit score groups:

**Very Low → Low → Medium → High**

The Credit Score Bins are generated through a nested DAX `IF` statement, while the median is provided by the measure created in the previous session.

The visual is then formatted and customized to suit the report design.
