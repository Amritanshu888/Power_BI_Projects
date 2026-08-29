# Power BI — Creating and Formatting a Line Chart + Currency Filter Across All Pages

## 1. Objective of the Video

In the previous video, the report was divided into **two pages**.

In this video, the focus is on adding and formatting a **Line Chart** to the first report page.

The major tasks covered are:

1. Add a Line Chart to the report.
2. Plot transaction amounts over time.
3. Configure the X-axis and Y-axis.
4. Format the line chart.
5. Add and format data labels.
6. Add a chart border.
7. Remove unnecessary gridlines.
8. Format the axis labels and chart title.
9. Understand the issue of having **multiple currencies**.
10. Add a **Currency filter** to all report pages.
11. Test the chart using different currencies.
12. Prepare for upcoming topics such as Matrix visuals and Bookmarks.

---

# 2. Adding a Line Chart

The first visual to be added to the report is a **Line Chart**.

The purpose of the chart is to show:

> **How transaction amounts change over time.**

---

## Steps to Add the Line Chart

### Step 1 — Expand the Required Panes

On the Power BI report page:

1. Expand the **Visualizations** pane.
2. Expand the **Data** pane.
3. Expand the table containing the required data.

The table being used in the lecture is:

**`UPI Transactions`**

---

### Step 2 — Select a Blank Area

1. Click on a **blank area of the report canvas**.
2. From the Visualizations pane, select the **Line Chart** visual.

Power BI creates a blank line chart on the canvas.

---

### Step 3 — Position and Resize the Chart

After creating the chart:

* Move it to the desired location on the report page.
* Resize it according to the available space.

The chart can be resized by dragging its edges/corners.

---

# 3. Adding Transaction Amount to the Y-Axis

The objective is to show the **transaction amount** over time.

The dataset contains an **Amount** column representing the transaction amount.

### Steps

1. Locate the **Amount** field under the `UPI Transactions` table.
2. Double-click it or drag it from the Data pane.
3. Place it into the **Y-axis** bucket of the line chart.

The Y-axis now represents the transaction amount.

### Interpretation

The vertical axis tells us **how much money was involved in the transactions**.

---

# 4. Adding Transaction Date to the X-Axis

Since the objective is to analyze the trend over time, we need a date field.

The dataset contains:

**`Transaction Date`**

### Steps

1. Locate `Transaction Date` in the Data pane.
2. Drag and drop it into the **X-axis** bucket.

Power BI may automatically create a date hierarchy containing levels such as:

* Year
* Quarter
* Month
* Day

---

# 5. Simplifying the Date Hierarchy

The chart does not need to display all levels of the date hierarchy.

The requirement is to show the transaction trend **by month**.

Therefore:

* Quarter is unnecessary.
* Day is unnecessary.
* Year is also unnecessary because the dataset contains data only for **2024**.

---

## Removing Quarter and Day

In the X-axis field well, remove:

* **Quarter**
* **Day**

This leaves the required time level, **Month**.

---

## Removing Year

The dataset contains transactions only for:

**2024**

Therefore, there is no need to display `2024` repeatedly as part of the X-axis hierarchy.

The year can instead be mentioned in the chart title.

After removing the unnecessary hierarchy levels, the chart essentially represents:

> **Transaction Amount by Month for 2024**

---

# 6. Result So Far

The line chart now represents:

* **X-axis → Month**
* **Y-axis → Transaction Amount**

This allows us to see how the transaction amount changes from month to month.

---

# 7. Formatting the Line Chart

Once the basic chart has been created, the next step is to format it.

### Steps

1. Select the line chart.
2. Open **Format your visual** in the Visualizations pane.

Several formatting options are available.

---

# 8. Changing the Line Interpolation

Under the line formatting options, the **Interpolation type** can be changed.

The default is:

**Linear**

The lecture changes it to:

**Smooth**

### Steps

1. Open the relevant **Lines** formatting section.
2. Find **Interpolation type**.
3. Change it from **Linear** to **Smooth**.

### Effect

The line becomes smoother rather than being represented only as straight line segments.

---

# 9. Changing the Line Color

The color of the line can also be customized.

### Steps

1. Under the line formatting options, locate **Color**.
2. Click the color selector.
3. Choose a color of your choice.

In the lecture, **purple** is selected.

The exact color is not mandatory; the important point is understanding that the line color can be customized.

---

# 10. Adding a Shaded Area

The line chart can optionally contain a shaded area beneath the line.

There is an option for the **shaded area**.

### To enable it

Turn the shaded-area option:

**On**

### To disable it

Turn it:

**Off**

In the lecture, the shaded area is eventually removed because the presenter feels the chart looks **cleaner without it**.

So:

> Shaded area is optional and depends on the desired visual design.

---

# 11. Adding Markers

Markers can also be displayed at the individual data points.

### Steps

1. Locate the **Markers** option in the formatting settings.
2. Change it to **On** if markers are required.

Markers make individual data points more visually apparent.

Again, this is optional and depends on the desired design.

---

# 12. Adding Data Labels

The presenter also wants the actual transaction values to be visible directly on the chart.

### Steps

1. Locate **Data labels** in the Format Visual pane.
2. Change the setting to:

**On**

The transaction values now appear directly on the chart.

This makes it easier for users to identify the values without having to hover over each point.

---

# 13. Formatting Data Labels

The data labels can be further customized.

### Steps

1. Click/open the **Data labels** section.
2. Look under the settings related to **Values / Data labels**.
3. Modify the formatting as required.

The lecture changes:

### Font weight

The labels are changed to:

**Bold**

### Font color

The color is changed to:

**Black**

### Font style

The font style can also be customized according to preference.

The purpose is to make the labels more readable and visually prominent.

---

# 14. Adding a Border to the Chart

A border is added around the entire visual.

### Steps

1. Select the chart.
2. Go to **Format Visual**.
3. Open **General**.
4. Open **Effects**.
5. Locate **Visual border**.
6. Turn it:

**On**

---

## Changing the Border Color

The default border color can also be changed.

### Steps

1. Click the border color selector.
2. The default color is black.
3. Change it to **gray**.

This provides a subtle boundary around the chart.

---

# 15. Removing Horizontal Gridlines

The presenter wants a cleaner chart and therefore removes the horizontal gridlines.

### Steps

1. Open **Format Visual**.
2. Go to the **Visual** formatting section.
3. Locate **Gridlines**.
4. Find **Horizontal gridlines**.
5. Change it to:

**Off**

The horizontal gridlines disappear.

### Vertical gridlines

The lecture notes that there are no vertical gridlines being used, so no additional action is required there.

---

# 16. Formatting the Y-Axis

The Y-axis contains transaction values.

However, because **data labels are already enabled**, there is no need to display the Y-axis title/value information redundantly.

### Steps

1. Go to the **Y-axis** formatting section.
2. Turn the **Title** off.

This produces a cleaner chart because the data labels already communicate the transaction values.

---

# 17. Formatting the X-Axis

The X-axis represents the months.

Since the axis already displays month names, there is no need to display an additional axis title such as:

**Month**

---

## Removing the X-Axis Title

### Steps

1. Open the **X-axis** formatting section.
2. Locate the **Title** option.
3. Turn it:

**Off**

The month names remain visible, but the redundant title is removed.

---

# 18. Formatting the Month Labels

The month names along the horizontal axis can also be formatted.

The lecture changes the font to:

**Trebuchet MS**

Other formatting can also be changed.

### Formatting options demonstrated

The month labels can be:

* Changed to a different font.
* Made **bold**.
* Changed to **black**.
* Increased in size.

These changes improve readability.

The exact font and size are design choices rather than mandatory settings.

---

# 19. Adding a Chart Title

The chart needs a meaningful title.

The title used is:

**Transactions by Month (Year 2024)**

The title communicates both:

* What is being measured → Transactions
* Time dimension → Month
* Year → 2024

---

## Steps to Add/Modify the Title

1. Go to the **General** formatting section.
2. Open **Title**.
3. Enter:

**Transactions by Month (Year 2024)**

---

# 20. Formatting the Chart Title

The title itself can be customized.

The lecture demonstrates several formatting options:

### Font

The font can be changed.

### Font size

The size can be increased to make the title more prominent.

### Alignment

The title alignment is changed to:

**Center**

### Font style

The title can be made:

* Italic
* Underlined
* Bold

The exact combination is a design preference.

The overall principle is:

> Format the title so that it is clearly visible and communicates what the chart represents.

---

# 21. Important Currency Problem

At this point, an important data issue is identified.

The dataset contains a **Currency** column.

This means the transaction amounts may be represented using **different currencies**.

For example, the dataset may contain:

* USD
* GBP
* Other currencies

---

## Why This Matters

Suppose the `Amount` column contains:

```text
100 USD
200 GBP
300 EUR
```

Simply aggregating these numbers together would be incorrect because:

> **100 USD + 200 GBP + 300 EUR cannot be treated as a meaningful single monetary total without conversion to a common currency.**

Therefore, the line chart should allow the user to analyze the transactions **for one currency at a time**.

This ensures that the displayed amounts are not misleading.

---

# 22. Adding the Filters Pane

The Filters pane is not currently visible.

To add the Currency filter:

### Steps

1. Go to the **View** tab.
2. Select **Filters**.

The **Filters pane** becomes visible.

---

# 23. Applying Currency as a Filter to All Pages

The report has two pages.

The requirement is that the Currency filter should be available on **both pages**.

Power BI provides different filter scopes.

The relevant option here is:

**Filters on all pages**

This means the selected currency filter will affect every report page.

---

# 24. Adding Currency to "Filters on All Pages"

### Steps

1. Locate the **Currency** field in the Data pane.
2. Drag and drop `Currency` into:

**Filters on all pages**

Now the Currency filter applies to both Page 1 and Page 2.

---

# 25. Why "Filters on All Pages" Is Used

Suppose the user selects:

**USD**

on Page 1.

Because the Currency field was placed under **Filters on all pages**, the same filter applies to Page 2 as well.

This maintains consistency throughout the report.

### Important distinction

| Filter location        | Scope                |
| ---------------------- | -------------------- |
| Filters on this visual | Only selected visual |
| Filters on this page   | Current page         |
| Filters on all pages   | Entire report        |

In this case, **Filters on all pages** is required because currency needs to be controlled consistently across both report pages.

---

# 26. Testing the Currency Filter — Example: INR

After adding the filter, the presenter tests it with a currency.

For example, selecting **INR** filters the transactions to only those associated with INR.

The chart then shows only the months in which INR transactions occurred.

The lecture observes that INR transactions occurred in:

* March
* July
* November

The line chart then shows how the INR transaction amounts varied across those months.

### Interpretation

The chart is now answering:

> How did the INR transaction amounts vary over time?

rather than incorrectly combining INR with other currencies.

---

# 27. Testing the Currency Filter — Example: GBP

The presenter then tests another currency:

**GBP**

After selecting GBP, the chart updates automatically.

For GBP, transactions occurred in:

* April
* August
* December

The line chart now shows how GBP transaction amounts varied across those months.

This demonstrates that the Currency filter dynamically changes the chart.

---

# 28. Removing the Currency Filter

After testing the different currencies, the filter can be cleared.

This returns the report to its previous state.

The Filters pane can then be collapsed to provide more working space.

### Steps

1. Clear/remove the selected currency filter.
2. Collapse the **Filters pane**.

---

# 29. Collapsing the Data Pane

The Data pane can also be collapsed once the required fields have been added.

This provides a cleaner working environment and more canvas space.

---

# 30. Final State of Page 1

At the end of the video, **Page 1** contains:

* The previously created slicers.
* A formatted line chart.
* Transaction amount plotted against month.
* Data labels.
* Customized line appearance.
* A border.
* Removed horizontal gridlines.
* Formatted X-axis labels.
* A descriptive chart title.
* A Currency filter that applies across all report pages.

---

# 31. Final Line Chart Configuration

The main configuration can be summarized as:

| Component            | Configuration                                  |
| -------------------- | ---------------------------------------------- |
| Visual               | Line Chart                                     |
| X-axis               | Transaction Date → Month                       |
| Y-axis               | Amount                                         |
| Year                 | 2024, removed from axis and mentioned in title |
| Quarter              | Removed                                        |
| Day                  | Removed                                        |
| Line interpolation   | Smooth                                         |
| Line color           | Purple in lecture                              |
| Shaded area          | Disabled in final version                      |
| Markers              | Optional                                       |
| Data labels          | On                                             |
| Data label font      | Bold                                           |
| Data label color     | Black                                          |
| Visual border        | On                                             |
| Border color         | Gray                                           |
| Horizontal gridlines | Off                                            |
| X-axis title         | Off                                            |
| Y-axis title         | Off                                            |
| X-axis font          | Trebuchet MS                                   |
| Chart title          | Transactions by Month (Year 2024)              |
| Title alignment      | Center                                         |
| Currency filter      | Applied to all pages                           |

---

# 32. Overall Workflow

The complete workflow from this lecture is:

**Select blank canvas**

↓

**Insert Line Chart**

↓

**Add Amount → Y-axis**

↓

**Add Transaction Date → X-axis**

↓

**Remove Year, Quarter and Day where unnecessary**

↓

**Keep Month for time-based analysis**

↓

**Change line interpolation to Smooth**

↓

**Customize line color**

↓

**Configure shaded area / markers as desired**

↓

**Turn Data Labels On**

↓

**Format data labels**

↓

**Add visual border**

↓

**Remove horizontal gridlines**

↓

**Format X-axis and Y-axis**

↓

**Add descriptive title**

↓

**Identify multi-currency issue**

↓

**Open View → Filters**

↓

**Add Currency → Filters on all pages**

↓

**Test with different currencies**

↓

**Clear filter and collapse panes**

---

# 33. Key Learning Points

### 1. A line chart is useful for trend analysis

A line chart is appropriate when the objective is to understand how a numerical value changes over time.

Here:

> **Transaction Amount → Month**

---

### 2. Don't unnecessarily display every level of a date hierarchy

Power BI may automatically add:

**Year → Quarter → Month → Day**

But you should keep only the levels that are actually useful for the analysis.

In this example, **Month** is sufficient.

---

### 3. Formatting should improve readability

Useful formatting changes include:

* Smooth lines
* Appropriate line color
* Data labels
* Clear title
* Proper font
* Removing unnecessary gridlines
* Subtle borders
* Removing redundant axis titles

The objective is not to format every available option, but to make the report easier to understand.

---

### 4. Be careful when aggregating currencies

A numerical `Amount` column should **not automatically be aggregated across different currencies**.

Different currencies represent different monetary units.

Therefore, adding a **Currency filter** allows the user to analyze one currency at a time.

---

### 5. Use "Filters on all pages" when a filter should affect the entire report

Since this report has two pages and currency is relevant to both, `Currency` is placed under:

**Filters on all pages**

This ensures that the currency selection remains consistent throughout the report.

---

# 34. Upcoming Topics

The lecture concludes by introducing the next topics that will be covered.

### Next visual

A **Matrix visual** will be added, particularly on the second report page.

### Bookmarks

The upcoming sessions will also cover **Bookmarks**.

### Switching between charts

One of the planned requirements is to allow the user to switch between:

* **Line Chart**
* **Clustered Column Chart**

The mechanism for achieving this chart-switching functionality will be explained using **Bookmarks and related Power BI features**.

So the report is gradually being developed into a more interactive dashboard rather than simply a collection of static visuals.
