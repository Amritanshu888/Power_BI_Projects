# Detailed Notes — Power BI: Resizing & Positioning Visuals and Slicers

This lecture introduces an important **report-formatting and layout concept** in Power BI: how to determine the **size and position of visuals and slicers** so that the report page looks properly aligned, consistent, and aesthetically pleasing.

The lecture mainly uses a **canvas/layout example** to explain the calculations that will later be applied directly in Power BI.

---

# 1. Main Objective of the Lecture

The topic is:

> **Resizing and positioning visuals and slicers on a Power BI report page.**

When creating a Power BI report, it is not enough to simply add visuals.

You also need to make sure that:

* Visuals have appropriate sizes.
* Slicers have consistent sizes.
* Visuals are properly positioned.
* Spacing between visuals is consistent.
* Rows and columns are aligned.
* The overall report looks organized.
* The report has good aesthetics.

The instructor emphasizes that **formatting is important** because reports are eventually presented to other people.

---

# 2. Understanding the Report Canvas

The instructor first creates a simple example.

Imagine a **green-colored triangle ABCD**.

This represents the **canvas** or **report design area**.

In Power BI, the canvas is the area where you place your:

* Visuals
* Slicers
* Charts
* Other report elements

So conceptually:

**Canvas = Report design area = Area where visuals are placed**

The objective is to properly position and size everything inside this area.

---

# 3. Example Layout of Slicers

The instructor gives an example containing **10 blue-colored visuals/slicers**.

They are numbered:

**1, 2, 3, 4, 5, 6, 7, 8, 9, 10**

They are arranged in **two rows**.

### Row 1

Slicers:

**1 | 2 | 3 | 4 | 5**

### Row 2

Slicers:

**6 | 7 | 8 | 9 | 10**

So:

* Total slicers = **10**
* Number of rows = **2**
* Slicers per row = **5**

The report being created later will use a similar arrangement, which is why the instructor introduces this calculation before demonstrating it directly in Power BI.

---

# 4. Why Consistent Sizing Matters

The instructor points out that the slicers currently appear:

* Properly aligned
* Similar in size
* Visually consistent

Imagine instead that:

* Slicer 1 has one size.
* Slicer 2 has another size.
* Slicer 3 has another size.

Even if the information inside them is correct, the report would look **odd and poorly formatted**.

Therefore, slicers and visuals should have consistent dimensions wherever the layout requires it.

### Important principle

> **Visuals that are intended to form a grid should generally have consistent sizing and spacing.**

This creates a clean and professional report layout.

---

# 5. Canvas Dimensions Used in the Example

The instructor uses a hypothetical canvas to demonstrate the calculation.

Two dimensions are given.

### Width

The horizontal length, represented as **CD**, is:

**1280 units**

### Other dimension

The instructor refers to **AD** as:

**720 units**

So the example canvas has dimensions:

**720 × 1280**

The main calculation in the lecture focuses on the **1280-unit horizontal dimension**, because five slicers need to fit across each row.

---

# 6. The Layout Problem

The challenge is:

> **How do we determine the width/length of each slicer so that five slicers fit perfectly across the 1280-unit-wide canvas?**

The instructor introduces spacing assumptions to solve this.

---

# 7. Spacing Assumption

The instructor assumes that the space from the left side is:

**20 units**

There is also **20 units of space between adjacent slicers**.

And similarly, there is space on the right-hand side.

So the horizontal layout looks conceptually like:

**20 + Slicer + 20 + Slicer + 20 + Slicer + 20 + Slicer + 20 + Slicer + 20**

This is extremely important for understanding the calculation.

---

# 8. Counting the 20-Unit Spaces

There are **six spaces of 20 units**.

Why six?

Because there are:

* One space on the left
* Four spaces between the five slicers
* One space on the right

Therefore:

**Total spaces = 1 + 4 + 1 = 6**

Each space is:

**20 units**

Therefore:

**Total spacing = 6 × 20**

**= 120 units**

---

# 9. Calculate the Space Available for Slicers

The total canvas width is:

**1280 units**

The total space consumed by margins/gaps is:

**120 units**

Therefore, the remaining width available for the five slicers is:

**1280 − 120 = 1160 units**

So:

> **1160 units are available for the five slicers.**

---

# 10. Calculate the Width of Each Slicer

There are **five slicers in each row**.

The remaining width is:

**1160 units**

Therefore:

**Width of each slicer = 1160 ÷ 5**

**= 232 units**

### Final result

> **Each slicer should have a width/length of 232 units.**

This ensures that all five slicers fit perfectly across the row while maintaining the 20-unit spacing.

---

# 11. Complete Horizontal Calculation

The complete calculation can be remembered as:

### Given:

**Canvas width = 1280**

**Number of slicers per row = 5**

**Spacing = 20**

### Number of spaces:

**6**

### Total spacing:

**6 × 20 = 120**

### Remaining width:

**1280 − 120 = 1160**

### Width of each slicer:

**1160 ÷ 5 = 232**

Therefore:

> **Each slicer = 232 units wide**

---

# 12. Visual Representation of the Calculation

The row can be thought of as:

**20 | 232 | 20 | 232 | 20 | 232 | 20 | 232 | 20 | 232 | 20**

Let's verify:

* Five slicers = `5 × 232 = 1160`
* Six spaces = `6 × 20 = 120`
* Total = `1160 + 120 = 1280`

So the entire row exactly occupies the 1280-unit canvas width.

---

# 13. Positioning the Slicers Vertically

The instructor then explains how to determine the **vertical position** of the slicers.

The assumption is that there will also be:

**20 units of space from the top**

Therefore, the first row begins **20 units from the top**.

---

# 14. Position of the First Row

For the first row:

> **Top position = 20 units**

So the first row of slicers begins 20 units down from the top edge of the canvas.

---

# 15. Position of the Second Row

For the second row, the instructor explains that its vertical position depends on:

1. The initial 20-unit top margin.
2. The height of the slicers in the first row.
3. Another 20-unit gap between the two rows.

So conceptually:

**Second-row position = 20 + height of first-row slicer + 20**

Therefore:

> **Second-row position = top margin + slicer height + gap**

The exact numerical height of the slicers is **not specified in the lecture**, so the lecture does not calculate a final numerical Y-position for the second row.

---

# 16. General Formula for Row Positioning

The concept can therefore be expressed as:

### First row

**Y₁ = 20**

### Second row

**Y₂ = 20 + slicer height + 20**

Or:

**Y₂ = 40 + slicer height**

The important concept is that the next row is positioned based on:

**Previous row's position + previous row's height + desired gap**

---

# 17. Applying the Same Principle to Multiple Rows

The same concept can be extended to additional rows.

For example, conceptually:

**Row 1 position**

→ Top margin

**Row 2 position**

→ Row 1 position + Row 1 height + gap

**Row 3 position**

→ Row 2 position + Row 2 height + gap

And so on.

The goal is to maintain **consistent vertical spacing** between rows.

---

# 18. Position vs Size

An important distinction in the lecture is between **size** and **position**.

### Size

Determines how large the visual/slicer is.

For example:

* Width = 232 units
* Height = some specified value

### Position

Determines where the visual/slicer is placed on the canvas.

For example:

* Distance from left
* Distance from top

So when formatting a report, you need to control both:

> **Size + Position**

---

# 19. Why This Matters in Power BI

A Power BI report can contain many:

* Slicers
* Charts
* Cards
* Tables
* Graphs
* Other visuals

If these are placed randomly, the report can look:

* Unorganized
* Uneven
* Difficult to read
* Visually inconsistent

Proper positioning and sizing makes the report:

* Cleaner
* Easier to understand
* More professional
* Better aligned
* More aesthetically pleasing

---

# 20. Formatting Is Part of Report Development

The instructor explicitly emphasizes that **formatting is important**.

Creating a technically correct report is not enough.

When presenting a report, you also need to consider:

* Size
* Position
* Alignment
* Spacing
* Aesthetics

The final report should look intentionally designed rather than having visuals placed randomly.

---

# 21. Important Concept: Alignment

The objective is to make all visuals appear **perfectly aligned**.

For a grid-based layout, this means:

### Horizontally

* Same width
* Same horizontal gaps
* Same left/right alignment

### Vertically

* Same height where appropriate
* Same vertical gaps
* Rows aligned with each other

This gives the report a consistent visual structure.

---

# 22. Important Concept: Consistent Spacing

The example assumes **20 units** of spacing.

This 20-unit spacing is applied:

* On the left side
* Between adjacent slicers
* On the right side
* At the top
* Between rows

The purpose is to create consistent whitespace throughout the report.

---

# 23. Practical Calculation Method

When you have to fit multiple visuals across a Power BI canvas, the calculation process demonstrated in the lecture is:

### Step 1 — Determine canvas width

Example:

**1280**

### Step 2 — Determine number of visuals per row

Example:

**5**

### Step 3 — Decide desired spacing

Example:

**20 units**

### Step 4 — Count the spaces

For five visuals:

**5 + 1 = 6 spaces**

### Step 5 — Calculate total spacing

**6 × 20 = 120**

### Step 6 — Calculate usable width

**1280 − 120 = 1160**

### Step 7 — Divide usable width by number of visuals

**1160 ÷ 5 = 232**

### Step 8 — Give every visual the same width

**Width = 232 units**

This produces an evenly spaced row.

---

# 24. Vertical Positioning Method

For vertical positioning:

### First row

Start at:

**20 units from the top**

### Next row

Use:

**Previous top position + previous visual height + desired gap**

For this example:

**20 + slicer height + 20**

This keeps the rows consistently separated.

---

# 25. What Will Be Done in the Next Session?

This lecture is primarily conceptual.

The instructor says that in the **next session**, these concepts will be demonstrated directly in Power BI.

The next session will involve:

* Placing actual visuals on the report page.
* Positioning them.
* Resizing them.
* Applying the calculations discussed here.
* Getting a practical understanding of how the layout works in Power BI.

So this lecture establishes the **mathematical/layout foundation**, while the next lecture will apply it practically.

---

# 26. Key Formula to Remember

For the horizontal layout:

### General formula

**Width of each visual =**

**(Total canvas width − total spacing) ÷ number of visuals per row**

For the specific example:

**(1280 − (6 × 20)) ÷ 5**

**= (1280 − 120) ÷ 5**

**= 1160 ÷ 5**

**= 232 units**

---

# 27. Key Points to Memorize

### Canvas

The report design area where visuals are placed.

### Example canvas dimensions

* Height-related dimension: **720**
* Width: **1280**

### Layout

* Total slicers = **10**
* Rows = **2**
* Slicers per row = **5**

### Spacing

* Horizontal spacing = **20 units**
* Left/right spacing = **20 units**
* Top spacing = **20 units**
* Row gap = **20 units**

### Horizontal calculation

* Total spaces = **6**
* Total spacing = **120**
* Remaining width = **1160**
* Width of each slicer = **232**

### Vertical positioning

First row:

**20 units from top**

Second row:

**20 + first-row height + 20**

---

# 28. Final Conceptual Workflow

The lecture's overall approach is:

**Determine canvas dimensions**

↓

**Determine number of visuals/slicers**

↓

**Decide desired spacing**

↓

**Calculate total spacing**

↓

**Subtract spacing from canvas dimension**

↓

**Divide remaining space among visuals**

↓

**Give visuals consistent dimensions**

↓

**Position first row**

↓

**Use visual height + spacing to position subsequent rows**

↓

**Check alignment**

↓

**Check aesthetics**

↓

**Apply the same principles to the actual Power BI report**

---

# 29. Core Takeaway

The most important lesson from this lecture is:

> **When designing a Power BI report, don't place visuals arbitrarily. Calculate and control their size, position, spacing, and alignment so that the entire report looks structured and professional.**

For the specific example, remember:

**1280 canvas width + 5 slicers + 20-unit spacing → each slicer width = 232 units.**

And for vertical positioning:

**Next row position = previous row position + previous row height + desired gap.**

The instructor's broader point is that **report formatting, aesthetics, sizing, and positioning are just as important as the data and visualizations themselves when presenting a professional Power BI report.**
