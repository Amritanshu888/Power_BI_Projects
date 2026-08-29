# Power BI – House Type Analysis Page: Multiple Visuals, Slicers & Republishing

## 1. Session Objective

In this session, the **House Type Analysis** report page is further developed.

The session covers:

1. Customizing the colors of the existing visual.
2. Creating a second bar chart for:

   * Average Inflation
   * Average Interest Rate
   * Average Yield
3. Creating a third **Line and Stacked Column Chart** for:

   * Average Area in Square Meter
   * Average Square Meter Price
4. Formatting chart titles, colors, labels, and spacing.
5. Creating and formatting slicers for:

   * Area
   * City
   * Sales Type
   * Region
6. Adding search functionality to slicers.
7. Aligning multiple slicers.
8. Publishing the updated report to the **Housing Project** workspace.
9. Replacing the existing report with the updated version.
10. Understanding the importance of regularly publishing/saving Power BI work.

---

# 2. Customize Colors of the Existing Chart

The previous session created the:

> **Average Offer Price / Purchase Price by House Type**

chart.

The instructor explains that the colors and design of the report can be customized according to your preference.

You can:

* Choose your own colors.
* Use a predefined color palette.
* Search Google for suitable 3-color combinations.
* Use ChatGPT to suggest professional Power BI color combinations.

The instructor has selected some sample colors from Google for demonstration.

---

## 3. Change Offer Price Color

### Steps

1. Select the existing bar chart.
2. Click **Format Visual**.
3. Open the **Bars** section.
4. Select the **Offer Price** series.
5. Click the color option.
6. Click **More colors**.
7. Enter the desired hexadecimal color code.

The instructor uses:

```text
F4D8B4
```

for **Offer Price**.

> Hexadecimal colors allow you to use a specific color rather than selecting approximately from the default palette.

---

## 4. Change Purchase Price Color

Next, change the color of the Purchase Price series.

### Steps

1. Select **Purchase Price** under the bar/series settings.
2. Click **Color**.
3. Click **More colors**.
4. Enter:

```text
D0D9D9
```

The exact color palette can be changed according to your report design.

---

# 5. Change the Header Shape Color

The shape at the top of the report page is also customized.

### Steps

1. Select the rectangular/header shape.
2. Open **Style**.
3. Go to the color/fill settings.
4. Select **More colors**.
5. Enter the hexadecimal color:

```text
EDFC3E
```

The shape now uses the selected color.

---

# 6. Create the Second Chart

The first chart shows:

> Average Offer Price / Purchase Price by House Type

The instructor now wants another chart showing:

* Average Inflation
* Average Interest Rate
* Average Yield

by House Type.

Instead of creating a new chart from scratch, the existing chart is copied.

---

# 7. Copy the Existing Chart

### Steps

1. Select the existing **Average Offer/Purchase Price by House Type** chart.
2. Press:

**Ctrl + C**

3. Press:

**Ctrl + V**

A copy of the chart is created.

4. Move the copied chart to the desired position.

---

# 8. Remove the Existing Measures

The copied chart still contains:

* Offer Price
* Purchase Price

These fields need to be removed.

### Steps

1. Select the copied chart.
2. Go to **Add Data to Your Visual**.
3. Remove:

   * Offer Price
   * Purchase Price

from the relevant axis/value bucket.

The chart is now ready to receive the new fields.

---

# 9. Add Average Inflation

The first new field is **Inflation**.

### Steps

1. Locate **Inflation** in the Data pane.
2. Add it to the appropriate value/axis bucket.
3. Power BI initially applies **Sum**.
4. Click the field's dropdown.
5. Change:

**Sum → Average**

The chart now represents:

> **Average Inflation**

---

# 10. Add Average Interest Rate

Next, add the **Nominal Interest Rate Percentage** field.

### Steps

1. Locate **Nominal Interest Rate Percentage**.
2. Add it to the chart.
3. Power BI initially displays **Sum**.
4. Open its dropdown.
5. Change:

**Sum → Average**

Now the chart includes:

> **Average Interest Rate**

---

# 11. Add Average Yield

The third field is the **Yield on Mortgage Credit Bonds Percentage**.

### Steps

1. Locate the yield percentage field.
2. Add it to the chart.
3. Open its aggregation dropdown.
4. Change:

**Sum → Average**

The chart now contains three measures:

```text
Average Inflation
Average Interest
Average Yield
```

These are represented for each **House Type**.

---

# 12. Result of the Second Chart

The second chart is therefore a:

> **Clustered Bar Chart**

showing:

| Metric                     | Aggregation |
| -------------------------- | ----------- |
| Inflation                  | Average     |
| Nominal Interest Rate      | Average     |
| Mortgage Credit Bond Yield | Average     |

The categories remain based on **House Type**.

---

# 13. Customize Colors of the Second Chart

The instructor then assigns different colors to the three series.

### Steps

1. Select the second chart.
2. Click **Format Visual**.
3. Open **Bars**.
4. Select **Inflation**.
5. Click **Colors → More colors**.
6. Enter the desired hexadecimal code.

The instructor uses:

```text
F4D8B4
```

for Inflation.

---

### Interest Color

Select **Interest** and use another color.

The instructor uses:

```text
CFCF48
```

---

### Yield Color

Select the **Yield on Mortgage Credit Bond Percentage** series.

Another color is selected:

```text
DCE09
```

The purpose is simply to give each measure a visually distinct color.

---

# 14. Rename the Series

Power BI may automatically display long names such as:

* Average of Inflation
* Average of Nominal Interest Rate Percentage
* Average of Yield on Mortgage Credit Bonds Percentage

These are too long for the legend.

The instructor therefore renames them.

### Steps

1. Select the second chart.
2. Click **Add Data to Your Visual**.
3. Locate the fields in the relevant axis/value bucket.
4. Rename the first field:

**Average of Inflation → Inflation**

5. Rename the second:

**Average of Interest → Interest**

6. Rename the third:

**Average of Yield → Yield**

The legend becomes much cleaner:

```text
Inflation
Interest
Yield
```

---

# 15. Change the Second Chart Title

The copied chart still has the old title related to offer/purchase price.

That title needs to be changed.

### Steps

1. Select the second chart.
2. Go to **Format Visual**.
3. Select **General**.
4. Select **Title**.
5. Change the title to something representing:

> **Inflation / Interest / Yield by House Type**

The instructor uses a title along the lines of:

**Inflation / Interest / Yield**

with the house-type context.

The important point is that the title should accurately describe the three measures being displayed.

---

# 16. Adjust Title Size

The instructor also adjusts the title size so that it fits properly within the visual.

### Steps

1. Select the title formatting settings.
2. Reduce the font size if necessary.
3. Ensure that the title fits cleanly within the chart.

---

# 17. Be Careful with Format Painter

The instructor briefly attempts to use **Format Painter** to copy formatting from one chart to another.

However, this also changes other formatting/colors that were not intended to be changed.

Therefore, the instructor uses:

**Ctrl + Z**

to undo the unwanted formatting.

### Important lesson

Format Painter can copy multiple formatting properties at once. If you only want to change one particular formatting property, manually modify that property instead.

---

# 18. Create the Third Chart

The third chart needs to show:

* Average Area in Square Meter
* Average Square Meter Price

for different house types.

For this purpose, a **Combo Chart** is used.

A combo chart allows two different types of visual representations to be combined:

* Columns
* Line

The instructor chooses:

> **Line and Stacked Column Chart**

---

# 19. Copy an Existing Chart Again

Instead of creating the chart from scratch:

### Steps

1. Select the second chart.
2. Press:

**Ctrl + C**

3. Press:

**Ctrl + V**

4. Move the new chart to the right-hand side.
5. Increase its size if necessary.

---

# 20. Change the Visual Type

The copied chart is converted into a combo chart.

### Steps

1. Select the new chart.
2. Choose **Line and Stacked Column Chart**.

The visual now supports:

* Column Y-axis
* Line Y-axis

---

# 21. Remove the Existing Fields

The copied chart still contains:

* Inflation
* Interest
* Yield

These are removed.

### Steps

Remove the existing fields from the relevant value buckets.

The chart is now empty and ready for:

* Area
* Square Meter Price

---

# 22. Add Average Square Meter Area

The first measure is the **Square Meter** field.

### Steps

1. Locate **Square Meter** in the Data pane.
2. Drag it to the **Column Y-axis**.
3. Power BI initially uses **Sum**.
4. Open the field dropdown.
5. Change:

**Sum → Average**

Now the columns represent:

> **Average Square Meter Area**

---

# 23. Add Average Square Meter Price

The second measure is the **Square Meter Price** field.

### Steps

1. Locate **Square Meter Price** in the Data pane.
2. Drag it to the **Line Y-axis**.
3. Power BI initially uses **Sum**.
4. Open the dropdown.
5. Change:

**Sum → Average**

The line now represents:

> **Average Square Meter Price**

---

# 24. Structure of the Combo Chart

The final combo chart contains:

```text
House Type
    │
    ├── Columns → Average Square Meter
    │
    └── Line → Average Square Meter Price
```

This allows two related metrics to be represented in the same visual.

---

# 25. Change the Combo Chart Title

### Steps

1. Select the combo chart.
2. Go to **Format Visual**.
3. Select **General → Title**.
4. Enter a title representing:

> **Average Square Meter / Square Meter Price by House Type**

The instructor uses a title along these lines.

---

# 26. Change Column Colors

Next, format the columns.

### Steps

1. Select the combo chart.
2. Click **Format Visual**.
3. Open **Columns**.
4. Locate the relevant series/category.
5. Select the desired color.

The instructor chooses a suitable color to match the report's overall theme.

---

# 27. Change Line Color

The line is formatted separately.

### Steps

1. In **Format Visual**, scroll to **Lines**.
2. Open the line settings.
3. Change the line color.

A different color can be selected to clearly distinguish the line from the columns.

---

# 28. Change Line Width

The instructor also demonstrates that the line width can be changed.

This allows you to make the line:

* Thinner
* Thicker

depending on the visual design.

---

# 29. Change Line Interpolation

Another formatting option is the **Interpolation Type**.

The instructor changes the interpolation to:

> **Step**

This makes the line appear in a stepped pattern rather than a smooth/straight interpolation between points.

---

# 30. Add Markers to the Line

Markers can also be added to make individual data points easier to identify.

### Steps

1. Scroll down in the **Line** formatting section.
2. Locate **Markers**.
3. Turn:

**Markers → On**

4. Adjust the marker size if required.

The instructor increases the marker size slightly.

---

# 31. Adjust Bar/Category Spacing

Power BI allows you to control the spacing between bars/categories.

For the first chart:

1. Select the chart.
2. Go to **Format Visual**.
3. Open **Bars**.
4. Find **Layout**.
5. Adjust the spacing between categories.

You can also adjust:

> **Spacing between series**

This controls how much space exists between multiple bars belonging to different series.

---

# 32. Apply Spacing to the Second Chart

The same concept can be applied to the:

> **Inflation / Interest / Yield by House Type**

chart.

### Steps

1. Select the chart.
2. Open **Format Visual → Bars → Layout**.
3. Adjust:

   * Category spacing
   * Series spacing

until the chart looks clean.

---

# 33. Apply Spacing to the Combo Chart

The same can also be done with the third chart.

### Steps

1. Select the combo chart.
2. Open the appropriate **Layout** settings.
3. Increase or decrease category spacing as needed.

The goal is to avoid charts appearing too crowded.

---

# 34. Rename Combo Chart Legend Fields

The combo chart may initially show:

* Average of Square Meter
* Average of Square Meter Price

These names are unnecessarily long.

### Rename them

For the **Column Y-axis**:

> **Average of Square Meter → Square Meter**

For the **Line Y-axis**:

> **Average of Square Meter Price → Square Meter Price**

### Steps

1. Select the combo chart.
2. Click **Add Data to Your Visual**.
3. Double-click the first field.
4. Rename it to:

**Square Meter**

5. Double-click the second field.
6. Rename it to:

**Square Meter Price**

The legend is now cleaner.

---

# 35. Create a Slicer for Area

The instructor now wants to give users the ability to **filter the entire report page**.

The first slicer will filter by **Area**.

### Important step

Before inserting the slicer, make sure you click on a **blank area of the canvas**.

This is important because if another visual is selected, Power BI may replace/change that selected visual rather than creating a new slicer.

---

## Create the Area Slicer

### Steps

1. Click on a **blank area of the canvas**.
2. Select **Slicer**.
3. Power BI creates a blank slicer.
4. Place it at the top of the report page.
5. Add **Area** to the slicer's field.

The slicer now displays the available areas.

---

# 36. Format the Area Slicer

Select the slicer and click:

**Format Visual**

---

## 37. Remove the Slicer Background

### Steps

1. Go to:

**General → Effects**

2. Turn:

**Background → Off**

The slicer's default background disappears.

---

# 38. Add a Visual Border

The instructor wants a visible border around the slicer.

### Steps

1. Stay in the formatting options.
2. Turn:

**Visual Border → On**

3. Expand the border settings.
4. Change the border color to:

**White**

This makes the slicer visually fit with the report design.

---

# 39. Change Slicer Style to Drop-Down

Initially, the slicer may display a vertical list.

The instructor changes it to a **Drop-down** style to save space.

### Steps

1. Select the slicer.
2. Go to **Slicer Settings**.
3. Change the style from:

**Vertical List → Drop-down**

This creates a compact slicer.

---

# 40. Format Slicer Values

The values displayed inside the slicer can also be customized.

You can change:

* Font
* Font size
* Font color
* Font style

The instructor chooses:

* White text
* Slightly increased font size
* A suitable font style

---

# 41. Format the Slicer Header

The slicer header is formatted separately.

### Steps

Under **Slicer Header**:

* Choose the font style.
* Change the font color to white.
* Increase the size slightly.

The objective is to make the slicer consistent with the overall page design.

---

# 42. Change Slicer Value Background

The instructor notices that when the slicer is opened/selected, the value area has a white background.

This doesn't match the report design.

The instructor therefore changes the background to match the header shape color.

### Steps

1. Select the slicer.
2. Go to the **Values** formatting section.
3. Locate **Background**.
4. Click **More Colors**.
5. Enter the shape's color code:

```text
EADFC3
```

The value area now uses the same color theme as the rectangular header shape.

---

# 43. Rename "Area" to Capital Letters

The slicer header/field is displayed as:

> area

The instructor wants it to appear as:

> **AREA**

### Steps

1. Select the slicer.
2. Click **Add Data to Your Visual**.
3. Double-click the **Area** field.
4. Rename it to:

**AREA**

---

# 44. Make Slicer Text Bold

The instructor further improves readability by making the slicer text bold.

### Steps

Under the appropriate formatting settings:

* Make the slicer values **Bold**.
* Make the slicer header **Bold** as well.

---

# 45. Filtering the Entire Report Page

Now the Area slicer is functional.

When the user selects an area:

> **The visuals on the report page are filtered accordingly.**

For example:

```text
Select Area A
      ↓
All visuals update
      ↓
Only Area A-related insights shown
```

Selecting another area applies the corresponding filter.

---

# 46. Clear Slicer Selection

If the user wants to remove the filter:

Use the slicer's **clear selection** option.

This restores the report page to the unfiltered state.

---

# 47. Add Search Functionality to a Slicer

The instructor explains an important practical feature.

If a slicer contains a **large number of categories**, scrolling through the entire list can be inconvenient.

Power BI allows you to add a **Search** box.

### Steps

1. Click the **three dots (`...`)** on the slicer.
2. Select/enable **Search**.

A search box appears within the slicer.

---

# 48. Why Slicer Search Is Useful

The instructor gives a real-world example.

While working on a Power BI project, a client required a search box because there were many categories.

For example, instead of scrolling through hundreds of areas:

```text
Search:
[ del ]
```

Power BI can show possible matching options.

The user can then select the desired option and the report is filtered accordingly.

### Practical lesson

> When a slicer contains a large number of categories, adding a search box can significantly improve user experience.

---

# 49. Create a City Slicer

The Area slicer can be duplicated instead of creating another slicer from scratch.

### Steps

1. Select the Area slicer.
2. Press:

**Ctrl + C**

3. Press:

**Ctrl + V**
4. Move the copied slicer to the right.
5. Remove **Area** from its field bucket.
6. Add **City**.

Now the slicer filters the page based on City.

---

# 50. Rename City in Capital Letters

The instructor changes the field name to:

> **CITY**

### Steps

1. Select the City slicer.
2. Click **Add Data to Your Visual**.
3. Double-click the City field.
4. Rename it:

**CITY**

---

# 51. Create a Sales Type Slicer

Again, duplicate an existing slicer.

### Steps

1. Select the City slicer.
2. Press **Ctrl + C**.
3. Press **Ctrl + V**.
4. Move the new slicer to the right.
5. Remove **City**.
6. Add **Sales Type**.

The slicer now allows users to filter by Sales Type.

---

# 52. Rename Sales Type

Rename the field to:

> **SALES TYPE**

### Steps

1. Select the slicer.
2. Click **Add Data to Your Visual**.
3. Double-click the Sales Type field.
4. Rename it using capital letters.

---

# 53. Create a Region Slicer

Duplicate the slicer again.

### Steps

1. Select the Sales Type slicer.
2. Press **Ctrl + C**.
3. Press **Ctrl + V**.
4. Move the new slicer to the right.
5. Remove **Sales Type**.
6. Add **Region**.

Now the fourth slicer filters the page based on Region.

---

# 54. Rename Region

Rename the field to:

> **REGION**

### Steps

1. Select the Region slicer.
2. Click **Add Data to Your Visual**.
3. Double-click the Region field.
4. Rename it in capital letters.

---

# 55. Four Slicers on the Page

The page now has four slicers:

```text
┌──────────┐ ┌──────────┐ ┌────────────┐ ┌──────────┐
│   AREA   │ │   CITY   │ │ SALES TYPE │ │  REGION  │
└──────────┘ └──────────┘ └────────────┘ └──────────┘
```

These provide users with multiple ways to filter the report.

---

# 56. Align the Slicers

The instructor notices that the four slicers are not perfectly aligned.

They need to be placed at equal distances from each other.

### Steps

1. Position the slicers approximately where you want them.
2. Place the two outer slicers at the extreme ends.
3. Hold **Ctrl**.
4. Select each slicer that you want to align.
5. Go to the formatting/alignment options.
6. Choose:

**Align → Align Horizontally**

Power BI then distributes/alines the selected objects consistently.

---

# 57. Final Slicer Layout

The result is a clean row of four slicers:

```text id="9m6n4b"
AREA       CITY       SALES TYPE       REGION
  ↓          ↓             ↓              ↓
Filter     Filter        Filter         Filter
  ↓          ↓             ↓              ↓
Entire House Type Analysis Page
```

This makes the page interactive and allows users to dynamically explore the data.

---

# 58. Collapse the Housing Dataset

The instructor finally collapses the **Housing** dataset/table in the Data pane to keep the interface organized.

This does not change the report; it simply makes the Data pane cleaner.

---

# 59. Final House Type Analysis Page

The completed page now contains multiple analytical visuals and slicers.

### Visual 1

**Average Offer Price / Purchase Price by House Type**

Shows the comparison between:

* Average Offer Price
* Average Purchase Price

---

### Visual 2

**Inflation / Interest / Yield by House Type**

Shows:

* Average Inflation
* Average Interest
* Average Yield

---

### Visual 3

**Average Square Meter / Square Meter Price by House Type**

Combo chart showing:

* Average Square Meter → Columns
* Average Square Meter Price → Line

---

### Slicers

The page also contains:

* Area
* City
* Sales Type
* Region

---

# 60. Publish the Updated Report

After completing the new page, the instructor publishes the updated report to the previously created **Housing Project** workspace.

The instructor is already signed in.

### Steps

1. Go to **Home**.
2. Click **Publish**.
3. Select **Housing Project**.
4. Publish the report.

---

# 61. Existing Report Warning

Power BI detects that a report with the same name already exists in Power BI Service.

Therefore, Power BI displays a message asking whether you want to **replace the existing report**.

The instructor chooses:

> **Yes**

### Why replace it?

The report has been modified by adding the new page and additional visuals.

Therefore, the updated version needs to replace the older version.

Conceptually:

```text
Old Report
   ↓
Add new page + visuals + slicers
   ↓
Updated Report
   ↓
Publish
   ↓
Replace Existing Report
```

---

# 62. Important Best Practice – Publish Regularly

The instructor highlights an important practical recommendation:

> Whenever you are working on a Power BI report, regularly publish your completed work to Power BI Service.

For example, if you have completed your work for the day:

```text
Daily Work Completed
        ↓
Save Report
        ↓
Publish to Power BI Service
```

### Why?

Publishing regularly provides another saved copy of your work in the Power BI Service account/workspace.

This can be useful as part of your regular development workflow.

---

# 63. Open the Updated Report

After successful publishing:

1. Click the **Open** option.
2. Power BI Service opens the updated report.
3. Verify that the newly added page is present.

The instructor confirms that the report now contains the newly created page.

---

# 64. Report Pages

The instructor mentions the report pages, including:

### Page 1

> **House Market Overview**

### Page 2

> **Sales Performance**

### New Page

> **House Type Analysis**

The new House Type Analysis page is the page developed throughout this session.

The transcript refers to it as the **fourth page** at the end, indicating that additional report pages had been created in the overall course workflow.

---

# 65. Complete Session Workflow

```text
Existing House Type Analysis Page
              ↓
Customize Existing Chart Colors
              ↓
Create Copy of Chart
              ↓
Remove Offer/Purchase Price
              ↓
Add Average Inflation
              ↓
Add Average Interest
              ↓
Add Average Yield
              ↓
Rename Series
              ↓
Format Colors + Title
              ↓
Create Another Copy
              ↓
Change to Line + Stacked Column Chart
              ↓
Remove Inflation/Interest/Yield
              ↓
Add Average Square Meter
              ↓
Add Average Square Meter Price
              ↓
Format Columns + Line
              ↓
Add Markers + Change Interpolation
              ↓
Rename Legend Fields
              ↓
Create Area Slicer
              ↓
Format Slicer
              ↓
Enable Search
              ↓
Copy Slicer → City
              ↓
Copy Slicer → Sales Type
              ↓
Copy Slicer → Region
              ↓
Align Four Slicers
              ↓
Complete House Type Analysis Page
              ↓
Home → Publish
              ↓
Housing Project Workspace
              ↓
Replace Existing Report
              ↓
Open Updated Report in Power BI Service
```

---

# 66. Key Power BI Concepts Learned

## A. Average Aggregation

Power BI defaults numerical columns to **Sum** in many visual contexts.

When the business requirement is to analyze average values, manually change:

**Sum → Average**

This was done for:

* Inflation
* Interest
* Yield
* Square Meter
* Square Meter Price
* Offer Price
* Purchase Price

---

## B. Combo Charts

A **Line and Stacked Column Chart** can be used when you want to compare two related metrics using different visual representations.

Here:

**Columns → Average Square Meter**

**Line → Average Square Meter Price**

---

## C. Series Renaming

Long automatically generated names such as:

> Average of Offer Price

can be renamed to:

> Offer Price

This improves readability and creates cleaner legends.

---

## D. Visual Selection Matters

The instructor demonstrates that a visual should be selected based on:

* Data characteristics
* Available space
* Category-name length
* Data-label readability
* User experience

A visually correct chart is not necessarily a well-designed chart.

---

## E. Slicers Make Reports Interactive

Slicers allow report users to dynamically filter the report.

In this page:

```text
Area
City
Sales Type
Region
```

are available as filtering dimensions.

---

## F. Slicer Search

For large numbers of categories, enabling the slicer's **Search** option can significantly improve usability.

Users can enter a few characters and quickly find the required category.

---

## G. Consistent Formatting

Using a consistent color palette across:

* Header
* Charts
* Bars
* Slicers
* Text

helps create a professional-looking Power BI report.

The instructor demonstrates using hexadecimal color codes to maintain consistency.

---

## H. Alignment

When multiple visuals are placed together, alignment is important.

Power BI provides alignment/distribution options such as:

> **Format → Align → Align Horizontally**

These help maintain equal spacing and a clean layout.

---

## I. Republishing an Existing Report

If a report with the same name already exists in Power BI Service, publishing the updated `.pbix` file can trigger a replacement prompt.

Choose **Yes** when you intentionally want the updated Desktop version to replace the existing published version.

---

# 67. Most Important Practical Lessons

1. **Don't be afraid to change the visual type** if the current visual isn't readable.
2. Use **Average** instead of Sum when the business requirement calls for average metrics.
3. Use **different colors for different measures** so users can distinguish them quickly.
4. Keep legend names short and meaningful.
5. Use **combo charts** when two related measures benefit from different visual representations.
6. Add **slicers** when users need interactive filtering.
7. Enable **slicer search** when there are many categories.
8. Keep slicers and visuals properly aligned.
9. Maintain a **consistent color palette** throughout the report.
10. Regularly **publish your Power BI work** so the latest version is available in Power BI Service.
11. When publishing an updated report with the same name, **replace the existing report** if that is the intended behavior.

Overall, this session turns the **House Type Analysis** page into an interactive analytical page containing **three complementary visuals and four interactive slicers**, while also demonstrating how to publish the updated report to the **Housing Project** workspace.
