# Detailed Notes — Multi-row Card & Ribbon Chart in Power BI

## 1. Objective of This Lecture

In the previous lecture, we:

* Formatted the slicers
* Added Premium Amount, Coverage Amount, and Claim Amount card visuals

In this lecture, two new visuals are added:

1. **Multi-row Card**
2. **Ribbon Chart**

The lecture also demonstrates how to:

* Configure fields for these visuals
* Format their labels and values
* Add borders
* Change fonts and sizes
* Change colors
* Rename chart titles
* Use the Multi-row Card as an interactive filter for other visuals

---

# 2. Add a Multi-row Card

The first visual to be added is a:

> **Multi-row Card**

The purpose is to represent the **number of male and female customers**.

---

## 3. Create the Multi-row Card

### Steps

1. Click on a **blank area of the report canvas**.
2. From the Visualizations pane, select:

> **Multi-row Card**

3. A blank Multi-row Card appears.
4. Move it to the desired location.
5. Resize it according to the report layout.

---

# 4. Add Gender to the Multi-row Card

The instructor wants to show:

* Number of Male customers
* Number of Female customers

The **Gender** column will be used twice.

### First Gender Field

1. Select the Multi-row Card.
2. Locate **Gender** in the Data pane.
3. Double-click it or drag it into the visual's **Fields** bucket.

This adds Gender to the card.

### Second Gender Field

The same Gender column is added a second time.

1. Again select **Gender**.
2. Drag/drop it into the Fields bucket.

The Multi-row Card now contains two Gender fields.

---

# 5. Change the Second Gender Field to Count

Simply adding Gender twice does not yet give the required count.

The second field needs to be aggregated using:

> **Count**

### Steps

1. Locate the second Gender field in the Fields bucket.
2. Click its dropdown.
3. Change the aggregation to:

> **Count**

Now Power BI counts the number of records for each gender.

The Multi-row Card displays approximately:

```text id="v9x2ne"
Male       → Count
Female     → Count
```

Thus, it represents the total number of male and female customers/records.

---

# 6. Why Is Gender Added Twice?

This is an important technique demonstrated in the lecture.

The first Gender field provides the **category**:

> Male / Female

The second Gender field provides the **count**:

> Number of Male / Number of Female

Conceptually:

```text id="o8xq6k"
Gender Category
      +
Count of Gender
      ↓
Male    → Count
Female  → Count
```

This allows the Multi-row Card to show the category along with its corresponding count.

---

# 7. Format the Multi-row Card

After configuring the fields, the instructor formats the visual.

### Steps

1. Select the Multi-row Card.
2. Click:

> **Format Your Visual**

Several formatting sections are available.

---

# 8. Turn Off Category Labels

The instructor does not want the category labels displayed separately.

### Steps

1. Expand:

> **Category labels**

2. Change it to:

> **Off**

This removes the category-label formatting/display.

---

# 9. Format Callout Values

The actual numbers displayed in the Multi-row Card are formatted using:

> **Callout values**

### Steps

1. Expand **Callout values**.
2. Change the font.
3. The instructor chooses:

> **Trebuchet MS**

4. Increase the font size.
5. The instructor uses approximately:

> **14**

This makes the displayed values more readable.

---

# 10. Format the Cards Section

Next, the instructor expands:

> **Cards**

This section allows formatting of the card itself.

The instructor changes the **title** appearance.

### Changes made

* Title color → **Gray**
* Font → Bold
* Font size → approximately **15**

This gives the card a more polished appearance.

---

# 11. Add a Border to the Multi-row Card

A border is added around the Multi-row Card.

### Steps

1. Go to the **Style** section.
2. Enable/add a border.
3. Configure the border for:

* Top
* Bottom
* Left
* Right

4. Set the border outline color to:

> **White**

The Multi-row Card now has a white outline.

---

# 12. Resize and Position the Multi-row Card

After formatting:

1. Resize the Multi-row Card.
2. Move it to the desired position.
3. Ensure that it fits properly with the other visuals.

---

# 13. Multi-row Card as an Interactive Filter

An important Power BI behavior is demonstrated next.

The Multi-row Card can also interact with other visuals.

Suppose the user clicks:

> **Female**

The other visuals on the page can be filtered to show information related to female customers.

If the user clicks:

> **Male**

the other visuals can be filtered to male customers.

---

# 14. Example — Selecting Female

When the user selects **Female** in the Multi-row Card:

* Premium Amount card is filtered
* Coverage Amount card is filtered
* Claim Amount card is filtered
* Slicers/other visuals can respond
* Any additional visuals added to the page can also respond

The report therefore displays information for:

> **Female customers only**

---

# 15. Example — Selecting Male

When the user selects **Male**:

The report filters to:

> **Male customers only**

The Premium Amount, Coverage Amount, Claim Amount and other visuals update according to the selected customer category.

---

# 16. Important Concept — Visual Interactions

The Multi-row Card is not simply displaying information.

It can also create a **filter context** when a category is selected.

Conceptually:

```text id="a6d5kq"
Click "Female"
      ↓
Filter Context = Female
      ↓
Insurance Data is filtered
      ↓
All interacting visuals update
```

Similarly:

```text id="nqj8y1"
Click "Male"
      ↓
Filter Context = Male
      ↓
Insurance Data is filtered
      ↓
All interacting visuals update
```

This is one of the key advantages of interactive Power BI reports.

---

# 17. Add a Ribbon Chart

The second major visual added in this lecture is a:

> **Ribbon Chart**

The objective is to represent:

> **Number of claims by claim status**

The three claim-status categories are:

* Rejected
* Settled
* Pending

---

# 18. Create the Ribbon Chart

### Steps

1. Click on a blank area of the report canvas.
2. Select:

> **Ribbon Chart**

3. A blank Ribbon Chart appears.
4. Resize it according to the report layout.
5. Position it appropriately.

---

# 19. Add Claim Status to the Ribbon Chart

The instructor uses the **Claim Status** column twice.

### First Claim Status

1. Locate **Claim Status** in the Data pane.
2. Drag it into the:

> **X-axis**

The claim status categories become the categories along the horizontal axis.

### Second Claim Status

1. Again select **Claim Status**.
2. Drag it into the:

> **Y-axis**

Power BI then performs a count.

The chart now represents the:

> **Count of Claim Status**

for the different claim categories.

---

# 20. Claim Status Categories

The Ribbon Chart displays three categories:

1. **Rejected**
2. **Settled**
3. **Pending**

The chart therefore allows you to compare the number of claims across these statuses.

---

# 21. Format the X-Axis

The instructor now formats the Ribbon Chart.

### Steps

1. Select the Ribbon Chart.
2. Click:

> **Format Your Visual**

3. Expand:

> **X-axis**

The instructor wants to keep the values but remove the axis title.

### Changes

* X-axis title → **Off**
* Font style → changed
* Font size → adjusted
* Font may be made **bold**

The instructor again uses a preferred font style.

---

# 22. Format the Y-Axis

Next, the Y-axis is formatted.

### Steps

1. Collapse the X-axis settings.
2. Expand:

> **Y-axis**

The instructor turns off:

* Y-axis values
* Y-axis title

So:

> **Y-axis values → Off**

> **Y-axis title → Off**

---

# 23. Why Turn Off the Y-Axis Values?

The instructor removes the Y-axis values because the actual numerical counts will instead be shown directly on the chart through:

> **Data Labels**

This produces a cleaner-looking chart.

---

# 24. Turn On Data Labels

Since the Y-axis values are hidden, data labels are enabled.

### Steps

1. Locate:

> **Data labels**

2. Change it to:

> **On**

Now the numerical values are displayed directly on the Ribbon Chart.

---

# 25. Format Data Labels

The data labels can also be formatted.

### Steps

1. Expand **Data labels**.
2. Locate the formatting options for the values.
3. Change the font style.
4. The instructor chooses a preferred font.
5. The values can also be made:

> **Bold**

This improves readability.

---

# 26. Change Ribbon Chart Colors

The instructor wants to customize the colors used by the Ribbon Chart.

### Steps

1. Expand:

> **Columns**

2. Locate the color option.
3. Select a new color.

The instructor chooses:

> **Green**

This changes the appearance of the columns/ribbon chart.

---

# 27. Rename the Ribbon Chart Title

The default title is changed to something more meaningful.

The desired title is:

> **Number of Claims by Claim Status**

### Steps

1. Select the Ribbon Chart.
2. Go to:

> **General**

3. Expand:

> **Titles**

4. Select the existing title text.
5. Press:

```text id="g3y6pl"
Ctrl + A
```

6. Replace it with:

> **Number of Claims by Claim Status**

7. Press **Enter**.

---

# 28. Format the Ribbon Chart Title

The title itself is formatted.

The instructor changes:

* Font style
* Bold
* Underline
* Horizontal alignment

The title is ultimately:

> **Centered**

### Steps

Under the title formatting options:

1. Choose the desired font.
2. Enable **Bold**.
3. Enable **Underline** if desired.
4. Set **Horizontal alignment → Center**.

---

# 29. Add a Border to the Ribbon Chart

A border is also added to the Ribbon Chart.

### Steps

1. Select the Ribbon Chart.
2. Go to:

> **Format Your Visual → General**

3. Expand:

> **Effects**

4. Locate:

> **Visual border**

5. Enable the border.
6. Set the border color to:

> **White**

This gives the chart a clear outline against the dark report background.

---

# 30. Final Multi-row Card

The Multi-row Card now provides:

> **Male vs Female customer counts**

It has been formatted with:

* Category labels adjusted/turned off
* Trebuchet MS callout values
* Font size around 14
* Gray title
* Bold title
* Font size around 15
* White border
* Adjusted position and size

---

# 31. Final Ribbon Chart

The Ribbon Chart now provides:

> **Number of Claims by Claim Status**

It contains:

* Claim Status categories
* Count of claims
* Data labels
* Customized fonts
* Green chart color
* Custom title
* Centered title
* Bold/underlined title
* White visual border

---

# 32. Report Interaction at This Stage

The report has now become increasingly interactive.

For example:

```text id="gkw4g6"
Multi-row Card
   │
   ├── Female
   │      ↓
   │   Filter report
   │
   └── Male
          ↓
       Filter report
```

The selected gender can affect:

* Premium Amount card
* Coverage Amount card
* Claim Amount card
* Ribbon Chart
* Slicers
* Future visuals

assuming the normal visual interactions are enabled.

---

# 33. Visuals Added So Far

At this stage of the project, the report contains the following major elements:

| Visual               | Purpose                               |
| -------------------- | ------------------------------------- |
| Policy Number Slicer | Filter by policy                      |
| Claim Number Slicer  | Filter by claim                       |
| Customer ID Slicer   | Filter by customer                    |
| Premium Amount Card  | Show total premium                    |
| Coverage Amount Card | Show total coverage                   |
| Claim Amount Card    | Show total claim amount               |
| Multi-row Card       | Show male/female customer counts      |
| Ribbon Chart         | Show number of claims by claim status |
| Text Box             | Display company name                  |

---

# 34. Important Techniques Learned

## Selecting multiple visuals

Use:

```text id="7g7q4x"
Ctrl + Click
```

Useful when applying common formatting.

---

## Duplicate visuals

Use:

```text id="7s9jzr"
Ctrl + C
Ctrl + V
```

This preserves much of the existing formatting.

---

## Add a Multi-row Card

> Blank canvas → Multi-row Card → Add fields

---

## Count a categorical field

Add the same field and change its aggregation to:

> **Count**

For example:

```text id="0p7p7n"
Gender → Category
Gender → Count
```

---

## Add a Ribbon Chart

> Blank canvas → Ribbon Chart → Add Claim Status to X-axis and Y-axis

---

## Hide axis settings

Use:

> Format Your Visual → X-axis/Y-axis → Off

---

## Show values directly on chart

Use:

> **Data Labels → On**

---

## Add a border

Use:

> **General → Effects → Visual border**

---

# 35. Key Takeaways

1. **Multi-row Card** can be used to display multiple categories and their corresponding values.
2. Adding **Gender twice** allows the category and its count to be represented.
3. Change the second Gender field to **Count** to calculate the number of male/female records.
4. Visuals in Power BI can act as interactive filters when selected.
5. The **Ribbon Chart** is used here to compare the number of claims across claim-status categories.
6. The Claim Status categories are:

   * Rejected
   * Settled
   * Pending
7. **Data Labels** can be enabled when axis values are hidden.
8. Titles can be customized through **General → Titles**.
9. Borders can be added through **General → Effects → Visual border**.
10. Consistent fonts, borders, colors, alignment, and sizing help create a professional report.
11. The report is progressively becoming an interactive dashboard rather than simply a collection of static charts.
