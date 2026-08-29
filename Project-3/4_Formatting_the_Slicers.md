# Detailed Notes — Power BI: Formatting, Resizing & Positioning Slicers

This lecture is the **practical continuation** of the previous discussion about resizing and positioning visuals. The instructor now demonstrates the process directly in Power BI, including canvas formatting, creating slicers, calculating their exact size and position, duplicating them, and aligning multiple rows. 

---

# 1. Objective of the Lecture

The lecture covers two major areas:

1. **Formatting the report page/canvas**
2. **Formatting, resizing, and positioning visuals/slicers**

The instructor wants to demonstrate how to make the report visually organized by ensuring that:

* Visuals have appropriate sizes.
* Visuals are positioned correctly.
* Slicers are aligned.
* Spacing between slicers is consistent.
* Multiple slicers fit within a row.
* Multiple rows of slicers are properly aligned.
* The overall report looks clean and professional.

The instructor also mentions that after this formatting work, the project will move toward the actual **reporting requirements**. 

---

# 2. Opening the Report Page Formatting Options

The instructor starts by working on the report canvas.

### Steps

1. Click on a **blank area of the canvas**.
2. Expand the **Visualizations pane**.
3. Select **Format your report page**.

Once the report page formatting options are opened, several sections become available.

These include:

* **Page Information**
* **Canvas Settings**
* **Canvas Background**
* **Wallpaper**
* **Filter Pane**
* **Filter Cards**

These options allow you to control the appearance and configuration of different parts of the report page. 

---

# 3. Canvas Background

The **Canvas Background** controls the background of the actual report canvas.

By default, the instructor has a:

**White background**

---

## Changing the Canvas Color

The instructor demonstrates changing the canvas from white to gray.

### Steps

1. Expand **Canvas Background**.
2. Locate the color setting.
3. Change the color from white to **gray**.
4. Reduce the transparency to **0% / make the color fully visible** as demonstrated.

The canvas color then changes to gray.

The instructor then changes it back to white because the project requirement is to keep the canvas white. 

### For this project

The canvas will remain:

**White**

---

# 4. Canvas Background Image

The canvas background does not have to be just a solid color.

You can also place an **image** as the canvas background.

### Steps

1. Open the **Canvas Background** section.
2. Use the **Browse** option.
3. Select the desired image.
4. The image can then be used as the canvas background.

This allows the report to have a custom visual background rather than a plain color. 

---

# 5. Wallpaper

The instructor next explains the **Wallpaper** option.

Wallpaper is another report-page appearance setting.

For example, the instructor demonstrates making the wallpaper:

**Gray**

### Steps

1. Open the **Wallpaper** section.
2. Select the desired color.
3. Change it to gray.
4. Set transparency to **0%** so the color is clearly visible.

The background/wallpaper area changes accordingly. 

---

## Keeping Wallpaper White

If you do not want a different wallpaper color:

1. Keep the wallpaper white.
2. Increase its transparency.

The instructor chooses not to use a different wallpaper for the current project. 

---

# 6. Wallpaper Image

Just as with the canvas background, an image can also be used for the wallpaper.

### Steps

1. Go to the **Wallpaper** section.
2. Use **Browse**.
3. Select an image.
4. The image can be placed as the wallpaper.

So both **Canvas Background** and **Wallpaper** can be customized using colors or images. 

---

# 7. Canvas Settings

The next important section is **Canvas Settings**.

This controls the size/aspect ratio of the report page.

The instructor currently has:

> **16:9**

selected.

---

## Selecting a Canvas Size

You can select different canvas sizes according to the report requirement.

### Steps

1. Click **Canvas Settings**.
2. Select the desired canvas size.
3. Alternatively, select **Custom**.
4. If Custom is selected, specify:

   * Height
   * Width

For this project, the instructor uses:

> **16:9**

rather than a custom size. 

---

# 8. Dimensions of the 16:9 Canvas

With the 16:9 canvas selected, the instructor identifies the dimensions as:

### Height

**720**

### Width

**1280**

Therefore:

> **Power BI report canvas = 1280 × 720**

These dimensions are important because the instructor uses the width of **1280** to calculate the size and position of the slicers. 

---

# 9. Creating the First Slicer

The instructor now demonstrates how to create the slicers that will be used in the report.

The requirement is to place:

> **Five slicers in one row**

### Steps

1. Expand the **Data pane**.
2. Under the Visualizations pane, select **Add Data to your visual**.
3. Select **Slicer**.
4. Power BI creates a slicer on the report canvas.
5. Resize the slicer as necessary.



---

# 10. Adding a Field to the Slicer

Once the slicer has been created, the instructor adds a field to it.

For demonstration, the selected field is:

> **Bank Name Sent**

### Steps

1. Select the slicer.
2. Select/click **Bank Name Sent** from the data pane.
3. The field is added to the slicer.

The slicer now represents the bank-name-sent values. 

---

# 11. Changing the Slicer Style

The instructor changes the slicer from a vertical list to a dropdown.

### Steps

1. Select the slicer.
2. Open **Format your visual**.
3. Open **Slicer settings**.
4. Locate the slicer style.
5. Change:

**Vertical list → Dropdown**

This gives the slicer a more compact appearance, which is useful when multiple slicers need to fit into a single row. 

---

# 12. Requirement: Five Slicers in One Row

The report requirement is to have:

**Five slicers in the first row**

Each slicer will eventually represent a **different field**.

However, for now, the instructor simply copies the same slicer for demonstration purposes.

The important objective at this stage is **layout and formatting**, not the final field assignment. 

---

# 13. Why Random Sizing and Positioning Is Bad

The instructor emphasizes that visuals should **not** be placed randomly.

A poor report might have:

* One slicer larger than another.
* Different widths.
* Different heights.
* Unequal spacing.
* Random positioning.

This makes the report look unprofessional.

Instead:

> **All visuals should be deliberately sized and positioned so that they are properly aligned.**

The objective is to create a report that looks:

* Beautiful
* Good
* Decent
* Organized
* Professional



---

# 14. Copying the Slicer

The instructor now starts creating multiple slicers.

### Steps

1. Select the first slicer.
2. Press:

**Ctrl + C**

3. Press:

**Ctrl + V**

4. Place the copied slicer beside the first one.

This creates the second slicer. 

---

# 15. Adding a Border to the Slicers

The instructor also adds a visual border to the slicers.

### Steps

With the slicer selected:

1. Open **Format your visual**.
2. Go to **General**.
3. Open **Effects**.
4. Turn **Visual border → On**.

The same border setting is applied to the other slicer.

This gives the slicers a more defined visual appearance. 

---

# 16. Creating More Slicers

The instructor continues copying the slicer.

### Process

**Ctrl + C → Ctrl + V**

This is repeated to create additional slicers.

The goal is to create five slicers.

However, when the instructor initially places them, the five slicers **do not fit properly in one row**.

---

# 17. Why Didn't Five Slicers Fit?

The instructor asks why the five slicers could not initially be placed in one row.

The answer:

> **They were not planned properly before placing them.**

The slicers had been created and placed without calculating the available space.

Therefore, the slicers must now be **resized and positioned mathematically**. 

This is a key practical lesson:

> **Plan the layout before placing and sizing the visuals.**

---

# 18. Calculate the Width of Each Slicer

The canvas width is:

**1280**

The requirement is:

**5 slicers per row**

The instructor assumes:

* 20 units from the left
* 20 units from the right
* 20 units between each pair of slicers

---

## Step 1 — Remove Left and Right Margins

Total width:

**1280**

Left margin:

**20**

Right margin:

**20**

Total outer spacing:

**20 + 20 = 40**

Remaining width:

**1280 − 40 = 1240**



---

# 19. Account for Spaces Between Slicers

There are five slicers.

Therefore, there are **four spaces between them**:

**Slicer 1 | Space | Slicer 2 | Space | Slicer 3 | Space | Slicer 4 | Space | Slicer 5**

Each space is:

**20 units**

Therefore:

**4 × 20 = 80**

Subtract this from the remaining 1240:

**1240 − 80 = 1160**

So the five slicers collectively have:

> **1160 units of usable width**



---

# 20. Calculate Individual Slicer Width

There are five slicers.

Available width:

**1160**

Therefore:

**1160 ÷ 5 = 232**

### Final answer

> **Each slicer should have a width of 232 units.**

This is the key calculation used throughout the rest of the exercise. 

---

# 21. Remove the Extra Slicers

The instructor now removes the four extra slicers temporarily.

### Steps

1. Select the four slicers on the right.
2. Delete them.
3. Keep only the first slicer.

The remaining slicer becomes the template from which the others will be copied.

This is useful because once the first slicer is correctly formatted, copying it ensures that the others inherit the same dimensions. 

---

# 22. Set the Size of the First Slicer

With the first slicer selected:

### Steps

1. Open **Format your visual**.
2. Go to **General**.
3. Open **Properties**.
4. Find the **Size** settings.

The instructor sets:

### Height

**80**

### Width

**232**

The width comes directly from the calculation above.



---

# 23. Set the Position of the First Slicer

The instructor then configures the slicer's position.

### Horizontal position

**20**

This represents the 20-unit left margin.

### Vertical position

**20**

This represents the 20-unit top margin.

Therefore, the first slicer has:

| Property            |   Value |
| ------------------- | ------: |
| Width               | **232** |
| Height              |  **80** |
| Horizontal position |  **20** |
| Vertical position   |  **20** |



---

# 24. Why Copy the First Slicer?

Now that the first slicer has been correctly configured, the instructor copies it.

This is important because the other slicers should have the **same size**.

### Steps

**Ctrl + C → Ctrl + V**

When a slicer is copied:

* Its width is copied.
* Its height is copied.
* Its formatting is copied.
* Its other relevant properties are copied.

Only its **position** needs to be changed.



---

# 25. Position of the Second Slicer

The second slicer needs to be placed:

**20 units after the first slicer.**

The calculation is:

**20 + 232 + 20**

Where:

* First `20` = left position of first slicer.
* `232` = width of first slicer.
* Second `20` = gap between slicers.

Therefore:

**20 + 232 + 20 = 272**

### Second slicer horizontal position

> **272**

### Vertical position

> **20**

The instructor notes that because the slicer was copied, its size does not need to be changed. 

---

# 26. Second Slicer Properties

The second slicer therefore has:

| Property            |                 Value |
| ------------------- | --------------------: |
| Width               |                   232 |
| Height              | Same as copied slicer |
| Horizontal position |               **272** |
| Vertical position   |                **20** |

The critical change is the horizontal position.

---

# 27. Position of the Third Slicer

The third slicer comes after:

* Two slicers
* Three spaces

The instructor calculates the position.

### Width occupied by two slicers

**232 × 2 = 464**

### Three spaces

**20 × 3 = 60**

### Total

**464 + 60 = 524**

Therefore:

> **Third slicer's horizontal position = 524**

Its vertical position remains:

**20**



---

# 28. Third Slicer Size Check

The instructor also checks the width.

It was showing approximately:

**231**

So it is manually changed to:

**232**

This demonstrates another important point:

> Even if a copied or manually resized visual appears close to the required dimension, check the actual property value and correct it if necessary.

The instructor also verifies the first slicer's width and changes it to 232 if required. 

---

# 29. Position of the Fourth Slicer

The fourth slicer comes after the third slicer.

The third slicer's horizontal position is:

**524**

The third slicer's width is:

**232**

The gap is:

**20**

Therefore:

**524 + 232 + 20**

**= 776**

### Fourth slicer horizontal position

> **776**

### Vertical position

> **20**

The instructor notes that the calculated value of **776** is already present. 

---

# 30. Position of the Fifth Slicer

The fifth slicer is the last slicer in the row.

There are four slicers before it.

### Width occupied by four slicers

**232 × 4 = 928**

There are five 20-unit spaces before the fifth slicer's starting position:

1. Left margin
2. Gap between slicer 1 and 2
3. Gap between slicer 2 and 3
4. Gap between slicer 3 and 4
5. Gap between slicer 4 and 5

Therefore:

**5 × 20 = 100**

Total:

**928 + 100 = 1028**

### Fifth slicer horizontal position

> **1028**



---

# 31. Final Positions of the Five Slicers

The resulting horizontal positions are:

| Slicer | Horizontal Position | Width | Vertical Position |
| ------ | ------------------: | ----: | ----------------: |
| 1      |              **20** |   232 |                20 |
| 2      |             **272** |   232 |                20 |
| 3      |             **524** |   232 |                20 |
| 4      |             **776** |   232 |                20 |
| 5      |            **1028** |   232 |                20 |

Notice the pattern:

**20 → 272 → 524 → 776 → 1028**

Each successive position increases by:

**232 + 20 = 252**

This is because each slicer occupies 232 units and the gap between slicers is 20 units.

---

# 32. Verify the Entire Row

Let's verify the layout mathematically.

### Five slicers

**5 × 232 = 1160**

### Six total 20-unit spaces

There are:

* Left margin
* Four internal gaps
* Right margin

Therefore:

**6 × 20 = 120**

### Total

**1160 + 120 = 1280**

So the five slicers fit exactly across the canvas.

This confirms that the positioning and sizing calculations are correct.

---

# 33. Visual Result

After collapsing the Visualizations and Data panes, the instructor observes that:

> **The five slicers look perfectly aligned.**

This is the desired result.

The slicers have:

* Equal widths
* Equal heights
* Equal spacing
* Consistent vertical alignment
* Proper left/right margins



---

# 34. Important Principle: Size + Position + Alignment

The instructor emphasizes that all visuals in the report should be placed in a way that makes them look:

* Properly aligned
* Correctly sized
* Correctly positioned
* Visually consistent

The **shape, size, and position** of the visuals should be deliberately controlled.

The purpose is to create a report that looks **professional and aesthetically pleasing**. 

---

# 35. Current Field Assignment Is Temporary

At this stage, all five slicers contain the same field:

> **Bank Name Sent**

This is only for demonstrating the formatting and positioning process.

The instructor explains that in upcoming sessions, the fields will be changed so that:

> **Different slicers will represent different fields according to the reporting requirement.**



---

# 36. Creating a Second Row

The report requirement also includes another row of slicers.

The instructor demonstrates how to duplicate the entire first row.

### Steps

1. Select the first slicer.
2. Hold **Ctrl** and select:

   * First slicer
   * Second slicer
   * Third slicer
   * Fourth slicer
   * Fifth slicer
3. Once all five are selected, press:

**Ctrl + C**

4. Press:

**Ctrl + V**

5. Move the duplicated group downward.

This creates another row of slicers. 

---

# 37. Aligning the Second Row

After copying the five slicers, the instructor moves them downward.

The objective is to make sure that the second row is also:

* Properly aligned
* Equally spaced
* Consistent with the first row

The instructor notes that the position can be adjusted as needed.



---

# 38. Using Power BI's Red Alignment Lines

Power BI provides **red alignment/guide lines** when you move visuals around.

The instructor demonstrates using these lines to help position the visuals.

### How to use them

When moving a slicer:

1. Drag the slicer.
2. Watch for the red alignment guides.
3. Use those guides to align the slicer with other visuals.
4. Adjust its position until the visuals appear properly aligned.

These guides make manual alignment easier. 

---

# 39. Changing Size and Position Manually

If any particular slicer needs a different:

* Shape
* Size
* Position

you can change these properties directly through the Visualizations pane.

### Steps

1. Select the required visual/slicer.
2. Open **Format your visual**.
3. Go to **General**.
4. Open **Properties**.
5. Change:

   * Size
   * Position

This gives precise control over the placement of each visual. 

---

# 40. Filters Pane

The instructor also briefly explains the **Filters pane**.

At the moment, the Filters pane is hidden.

If you want to display it:

### Steps

1. Go to the **View** tab.
2. Click **Filters**.
3. The Filters pane appears on the right side.

If you do not need it:

1. Go to **View**.
2. Click **Filters** again.
3. The Filters pane becomes hidden.



---

# 41. Final State of the Report

At the end of the session:

* Five slicers have been created in the first row.
* They have been resized to **232 width**.
* Their positions have been calculated.
* They are properly aligned.
* A second row has been duplicated.
* The slicers currently use the same field for demonstration.
* The actual fields will be changed later.
* The report canvas remains based on a **16:9 layout**.
* The Filters pane is hidden because it is not currently required.

---

# 42. Complete Practical Workflow

Here's the complete process demonstrated in the lecture:

### Step 1 — Format the report page

**Click blank canvas → Format your report page**

### Step 2 — Configure canvas

**Canvas Settings → 16:9**

Result:

**Width = 1280**

**Height = 720**

### Step 3 — Create slicer

**Data pane → Add Data to your visual → Slicer**

### Step 4 — Add a field

For demonstration:

**Bank Name Sent**

### Step 5 — Change slicer style

**Format your visual → Slicer settings → Style → Dropdown**

### Step 6 — Add border

**General → Effects → Visual border → On**

### Step 7 — Calculate slicer width

**1280 − 20 − 20 = 1240**

Then:

**1240 − (4 × 20) = 1160**

Then:

**1160 ÷ 5 = 232**

Therefore:

**Slicer width = 232**

### Step 8 — Set first slicer

* Width = **232**
* Height = **80**
* X/horizontal position = **20**
* Y/vertical position = **20**

### Step 9 — Copy slicers

**Ctrl + C → Ctrl + V**

### Step 10 — Set second position

**20 + 232 + 20 = 272**

### Step 11 — Set third position

**232 × 2 + 20 × 3 = 524**

### Step 12 — Set fourth position

**524 + 232 + 20 = 776**

### Step 13 — Set fifth position

**232 × 4 + 20 × 5 = 1028**

### Step 14 — Verify alignment

Collapse panes and visually inspect the row.

### Step 15 — Duplicate entire row

**Ctrl-select all five → Ctrl + C → Ctrl + V**

### Step 16 — Move second row downward

Use the red alignment guides to position it correctly.

### Step 17 — Make manual corrections if necessary

**Format your visual → General → Properties → Size / Position**

---

# 43. Important Formula — Horizontal Position of Each Slicer

A useful pattern from the lecture is:

### Slicer 1

**20**

### Slicer 2

**20 + 232 + 20 = 272**

### Slicer 3

**20 + 2(232) + 2(20) = 524**

### Slicer 4

**20 + 3(232) + 3(20) = 776**

### Slicer 5

**20 + 4(232) + 4(20) = 1028**

So the general formula is:

> **Horizontal position of slicer n = 20 + (n − 1) × (232 + 20)**

This produces evenly spaced slicers.

---

# 44. Key Numbers to Remember

| Setting                   |    Value |
| ------------------------- | -------: |
| Canvas ratio              | **16:9** |
| Canvas width              | **1280** |
| Canvas height             |  **720** |
| Slicers per row           |    **5** |
| Left margin               |   **20** |
| Right margin              |   **20** |
| Gap between slicers       |   **20** |
| Total internal gaps       |    **4** |
| Total usable slicer width | **1160** |
| Slicer width              |  **232** |
| Slicer height used        |   **80** |
| First slicer X            |   **20** |
| Second slicer X           |  **272** |
| Third slicer X            |  **524** |
| Fourth slicer X           |  **776** |
| Fifth slicer X            | **1028** |
| Row 1 Y                   |   **20** |

---

# 45. Key Lessons From the Lecture

### 1. Plan before placing visuals

Don't randomly place visuals and then try to make them fit.

Determine:

* Canvas size
* Number of visuals
* Margins
* Spacing
* Visual dimensions

first.

### 2. Use exact properties when precision matters

Instead of dragging a visual and guessing its size, use:

**Format your visual → General → Properties**

to enter exact values.

### 3. Copy correctly formatted visuals

Once one slicer has the correct:

* Size
* Formatting
* Border
* Style

copy it rather than recreating each slicer from scratch.

### 4. Only change the position of copied slicers

Since the copied slicer already has the correct dimensions, normally only its position needs to be adjusted.

### 5. Use alignment guides

The red Power BI guide lines help with visual alignment.

### 6. Formatting matters

A report isn't just about getting the correct data and charts.

You also need:

**Correct data + good visualization + proper formatting + alignment + aesthetics**

### 7. Current slicer fields are placeholders

All five slicers currently use **Bank Name Sent** merely for demonstration.

They will later be assigned different fields according to the report requirement.

---

# 46. Final Takeaway

The central practical lesson of this lecture is:

> **Power BI report design should be planned mathematically and visually.**

For the example:

**Canvas = 1280 × 720**

**5 slicers per row**

**20-unit margins and gaps**

**Each slicer width = 232**

**Slicer height = 80**

**X positions = 20, 272, 524, 776, 1028**

**Y position for first row = 20**

Once the first slicer is correctly formatted, duplicate it and modify only the required position. For additional rows, duplicate the entire group and use alignment guides or precise position properties to maintain consistency.

The next session will move from **formatting and positioning** toward **adding the appropriate different fields to the individual slicers**. 
