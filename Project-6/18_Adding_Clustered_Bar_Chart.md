# Power BI – House Type Analysis Page & Average Offer/Purchase Price by House Type

## 1. Objective of the Session

In this session, a **new report page** is created to provide users with flexibility to analyze insights for different **House Types**.

The main visual created on this page compares:

* **Average Offer Price**
* **Average Purchase Price**

for each **House Type**.

The session also demonstrates several important report-design concepts:

* Choosing between column and bar charts
* Changing aggregation from **Sum → Average**
* Formatting axes and data labels
* Customizing colors
* Renaming series
* Formatting the chart title
* Adding a shadow
* Designing visuals for readability

---

# 2. Create a New Report Page

The first step is to add another page to the Power BI report.

### Steps

1. At the bottom of the Power BI report canvas, click the **`+` (plus) icon**.
2. A new report page will be created.
3. Rename the page.

The instructor suggests names such as:

> **House Type Analysis**

or simply:

> **House Type**

For this analysis, **House Type Analysis** is the more descriptive name.

---

# 3. Add a Header Shape

As with the other report pages, the instructor creates a shape at the top of the page to provide a consistent report-header design.

### Steps

1. Go to the **Insert** tab.
2. Select **Shapes**.
3. Choose any suitable shape.
4. Place the shape at the **top of the report page**.
5. Resize it so that it works as a header/background element.

---

## 4. Format the Header Shape

After adding the shape:

1. Select the shape.
2. Open **Style**.
3. Change the **Fill color** according to your preferred report theme.
4. Turn the **Border Off**.

The instructor chooses a color as an example, but you can use any color that matches your report design.

---

# 5. First Visual – Compare Offer Price and Purchase Price

The first visual on this page is intended to answer:

> **How do the offer price and purchase price compare across different house types?**

Because two numerical quantities need to be compared for multiple categories, a **Clustered Column Chart** or **Clustered Bar Chart** can be used.

The instructor initially chooses a **Clustered Column Chart**.

---

# 6. Create a Clustered Column Chart

### Steps

1. Click on a **blank area of the report canvas**.
2. Select **Clustered Column Chart** from the Visualizations pane.
3. A blank chart is created.
4. Resize the chart.
5. Position it appropriately on the page.

---

# 7. Add House Type to the Chart

The category we want to analyze is **House Type**.

### Steps

1. Expand the **Housing** table in the Data/Fields pane.
2. Locate **House Type**.
3. Double-click/select it or drag it into the chart.
4. Place it in the **X-axis** bucket.

The chart will now have different house types as categories.

Conceptually:

```text
House Type
     ↓
Category on X-axis
```

---

# 8. Add Offer Price

The next field is **Offer Price**.

The lecture notes that **Offer Price was a column created earlier**, whereas Purchase Price was already present in the original dataset.

### Steps

1. Locate **Offer Price**.
2. Add it to the chart's **Y-axis / Values** bucket.

---

# 9. Add Purchase Price

Next, add the existing Purchase Price field.

### Steps

1. Locate **Purchase Price**.
2. Drag and drop it into the same **Y-axis / Values** bucket.

The chart now contains two series:

* Offer Price
* Purchase Price

---

# 10. Change Aggregation from Sum to Average

By default, Power BI automatically aggregates numerical columns.

Therefore, Power BI initially displays something like:

* **Sum of Offer Price**
* **Sum of Purchase Price**

However, the purpose of this visual is to compare **average prices**, not total prices.

Therefore, both fields need to be changed from **Sum → Average**.

---

## Change Offer Price to Average

1. Click the dropdown associated with **Offer Price** in the visual's field bucket.
2. Change the aggregation from:

**Sum → Average**

The chart now represents:

**Average Offer Price**

---

## Change Purchase Price to Average

1. Click the dropdown associated with **Purchase Price**.
2. Change:

**Sum → Average**

The chart now represents:

**Average Purchase Price**

---

# 11. Result of the Initial Visual

The chart now compares:

```text
House Type
    │
    ├── Average Offer Price
    │
    └── Average Purchase Price
```

This allows the user to compare the two average values across different house types.

---

# 12. Format the Chart – Remove Gridlines

The instructor now begins formatting the visual.

### Steps

1. Select the chart.
2. Click **Format Visual**.
3. Locate the **Gridlines** settings.
4. Change **Gridlines → Off**.

This removes unnecessary horizontal/vertical gridlines and creates a cleaner appearance.

---

# 13. Change Colors of the Two Series

The instructor wants different colors for:

* Average Offer Price
* Average Purchase Price

### Steps

1. In **Format Visual**, open the **Columns** section.
2. Locate the series settings.
3. Select:

**Average of Offer Price**

4. Change its color.

Then:

5. Select:

**Average of Purchase Price**

6. Change its color as well.

The instructor chooses two different colors as examples.

### Important

The specific colors are not important. The goal is to make the two measures visually distinguishable.

---

# 14. Turn Data Labels On

The instructor then enables data labels.

### Steps

1. Select the chart.
2. Open **Format Visual**.
3. Find **Data Labels**.
4. Change:

**Data Labels → On**

The actual values will now appear on the bars/columns.

---

# 15. Problem with the Clustered Column Chart

After enabling the data labels, the instructor notices two readability problems:

### Problem 1 – Data labels

The data labels are not clearly visible for every bar/column.

### Problem 2 – House Type names

The house type names along the bottom of the chart are not being displayed/read easily.

This is an important **visual design issue**.

The objective is not merely to create a chart—it is to make the information **easy for the user to read and understand**.

---

# 16. Switch to a Clustered Bar Chart

To improve readability, the instructor decides to replace the column chart with a **Clustered Bar Chart**.

### Steps

1. Select the existing chart.
2. Click **Add Data to Your Visual** / change the visual type.
3. Select **Clustered Bar Chart**.

Power BI converts the visual into a horizontal bar chart.

---

# 17. Why the Clustered Bar Chart Is Better Here

After switching to the bar chart, the instructor observes that:

* House Type names are much easier to read.
* Data labels are more clearly visible.
* The visual uses horizontal space more effectively.
* The categories are easier to understand.

This demonstrates an important Power BI report-design principle:

> **Choose the visual based on readability and the type of data—not simply because a particular visual was initially selected.**

---

# 18. General Visualization Design Principle

When creating a report, always check:

* Are category names readable?
* Are data labels visible?
* Is the chart too crowded?
* Can users easily understand the comparison?
* Is the visual using the available space efficiently?

If the answer is no, consider changing the visual type.

In this example:

```text
Clustered Column Chart
          ↓
Poorer readability
          ↓
Clustered Bar Chart
          ↓
Better readability
```

---

# 19. Format the Clustered Bar Chart

After changing the visual, the instructor continues formatting it.

### Steps

1. Select the Clustered Bar Chart.
2. Click **Format Visual**.
3. Open the **Bars** section.
4. Customize the colors for the two series.

For example:

* Average Offer Price → one color
* Average Purchase Price → another color

The instructor demonstrates choosing different colors according to preference.

---

# 20. Hide Y-Axis Title and Values

The instructor then removes unnecessary axis information.

### Steps

1. Open the **Y-axis** formatting section.
2. Turn the **Title → Off**.

The instructor also collapses the Y-axis settings afterward.

The objective is to keep the chart visually clean.

---

# 21. Hide X-Axis Title and Values

The instructor also removes the X-axis information because the actual values will be displayed directly through data labels.

### Steps

1. Open the **X-axis** settings.
2. Turn:

**Values → Off**

3. Turn:

**Title → Off**

This creates a cleaner chart.

---

# 22. Format the Axis Values

For the values that remain visible where appropriate, the instructor adjusts the formatting.

The available formatting options include:

* Font color
* Font size
* Bold
* Font style

The instructor demonstrates:

* Increasing the size slightly.
* Making the values **Bold**.
* Choosing a suitable color.
* Choosing an appropriate font style.

The exact styling can be adapted to your report theme.

---

# 23. Format Data Labels

The data labels are also customized.

### Steps

1. Open the **Data Labels** section.
2. Adjust the label values.

The instructor demonstrates:

* Making the values **Bold**.
* Choosing an appropriate color.
* Reducing the font size slightly.
* Selecting an appropriate font style.

This ensures the labels remain readable without dominating the visual.

---

# 24. Change the Chart Title

The default Power BI title is not sufficiently descriptive, so it is changed.

### Steps

1. Select the chart.
2. Go to **Format Visual**.
3. Open **General**.
4. Open **Title**.
5. Enter:

> **Average Offer Price / Purchase Price by House Type**

The instructor notes that you can use **Avg** instead of **Average** if you prefer a shorter title.

For example:

> **Avg Offer / Purchase Price by House Type**

---

# 25. Format the Title

After creating the title, the instructor customizes its appearance.

Possible formatting includes:

* Font style
* Text color
* Alignment
* Font size
* Bold
* Italic
* Underline

The demonstrated configuration includes:

* **Center aligned**
* **Bold**
* **Italic**
* **Underlined**
* Slightly increased font size
* Gray text

---

# 26. Rename the Series

Power BI may initially display series names such as:

* Average of Offer Price
* Average of Purchase Price

The instructor wants cleaner names.

### Steps

1. Select the chart.
2. Click **Add Data to Your Visual**.
3. Locate the fields under the **X-axis**/relevant field bucket.
4. Double-click the series name **Average of Offer Price**.
5. Rename it to:

> **Offer Price**

6. Rename **Average of Purchase Price** to:

> **Purchase Price**

This makes the chart legend cleaner and easier to understand.

---

# 27. Why Rename the Series?

Instead of displaying:

```text
Average of Offer Price
Average of Purchase Price
```

the legend can simply show:

```text
Offer Price
Purchase Price
```

The title already communicates that these are **average values**, so the shorter legend names make the visual cleaner.

---

# 28. Add a Shadow

The instructor also demonstrates how to add a shadow around the visual.

### Steps

1. Select the bar chart.
2. Click **Format Visual**.
3. Go to **General**.
4. Open **Effects**.
5. Enable **Shadow**.

This gives the visual a subtle elevated/card-like appearance.

---

## 29. Change Shadow Color

If you want to customize the shadow:

1. Expand the **Shadow** settings.
2. Open **Shadow Color**.
3. Choose a suitable color.

The instructor demonstrates that you can select a color of your choice.

---

# 30. Final Visual Structure

The final visual represents:

> **Average Offer Price vs Average Purchase Price by House Type**

with:

* **House Type** as the category.
* **Offer Price** as one series.
* **Purchase Price** as another series.
* Both values calculated using **Average** aggregation.

---

# 31. Final Configuration

| Component                  | Configuration                                      |
| -------------------------- | -------------------------------------------------- |
| Report Page                | House Type Analysis                                |
| Visual                     | Clustered Bar Chart                                |
| Category                   | House Type                                         |
| First measure              | Average Offer Price                                |
| Second measure             | Average Purchase Price                             |
| Offer Price aggregation    | Average                                            |
| Purchase Price aggregation | Average                                            |
| Gridlines                  | Off                                                |
| Data Labels                | On                                                 |
| X-axis title               | Off                                                |
| X-axis values              | Off                                                |
| Y-axis title               | Off                                                |
| Series colors              | Customized                                         |
| Legend names               | Offer Price, Purchase Price                        |
| Chart title                | Average Offer Price / Purchase Price by House Type |
| Title alignment            | Center                                             |
| Title style                | Bold + Italic + Underlined                         |
| Title color                | Gray                                               |
| Shadow                     | Optional/Enabled                                   |
| Shadow color               | Customizable                                       |

---

# 32. Important Visualization Design Lesson

One of the most important lessons in this session is **visual selection based on readability**.

The instructor initially chooses:

**Clustered Column Chart**

but later notices that:

* House type names are difficult to read.
* Data labels are not clearly visible.

Therefore, the visual is changed to:

**Clustered Bar Chart**

The bar chart provides a better layout for the category names and makes the values easier to interpret.

### Remember

> A good Power BI report is not simply about adding visuals. The visuals should present insights in a way that is **clear, readable, and easy for the end user to understand**.

---

# 33. Complete Workflow

```text
Create New Page
      ↓
Rename → House Type Analysis
      ↓
Insert → Shapes
      ↓
Add Header Shape
      ↓
Format Fill + Remove Border
      ↓
Create Clustered Column Chart
      ↓
House Type → X-axis
      ↓
Offer Price → Y-axis
      ↓
Purchase Price → Y-axis
      ↓
Change Offer Price → Average
      ↓
Change Purchase Price → Average
      ↓
Turn Gridlines Off
      ↓
Customize Series Colors
      ↓
Turn Data Labels On
      ↓
Check Readability
      ↓
House Type Labels Not Clear
      ↓
Switch to Clustered Bar Chart
      ↓
Customize Bar Colors
      ↓
Hide Unnecessary Axis Titles/Values
      ↓
Format Data Labels
      ↓
Rename Series
      ↓
Format Chart Title
      ↓
Add Shadow
      ↓
Final House Type Analysis Visual
```

---

# 34. Key Takeaways

### Calculations

The visual uses **average**, not sum:

**Average Offer Price**

vs.

**Average Purchase Price**

### Visual selection

Both clustered column and clustered bar charts can represent the comparison, but the **Clustered Bar Chart** was ultimately preferred because it provided better readability.

### Formatting

The session covers:

* Gridlines
* Series colors
* Data labels
* Axis titles
* Axis values
* Font formatting
* Chart title
* Legend/series names
* Shadow
* Shadow color

### Report design

Always prioritize:

> **Readability → Clarity → Appropriate visual → Consistent formatting**

The final objective is to make the report easy for users to understand rather than simply filling the report page with visuals.
