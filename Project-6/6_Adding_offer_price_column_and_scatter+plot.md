# Power BI – Scatter Plot: Offer Price vs Purchase Price

## 1. Session Overview

In this session, the report is enhanced by adding a **Scatter Plot**.

### Objective

The scatter plot is used to represent the relationship between:

* **Offer Price**
* **Purchase Price**

The important challenge is that the dataset **does not directly contain an Offer Price column**.

It only contains:

* `Purchase Price`
* `Percentage Change Between Offer and Purchase`

Therefore, the instructor first **derives Offer Price using a calculated column**, and then uses it together with Purchase Price in a scatter plot.

---

# 2. Understanding the Available Data

The instructor first switches to **Table/Data View** to inspect the dataset.

### Available columns

The dataset contains:

> `Purchase Price`

But it does **not** contain:

> `Offer Price`

However, it contains:

> `Percentage Change Between Offer and Purchase`

Therefore, the available information is sufficient to mathematically derive the missing Offer Price.

---

# 3. Deriving Offer Price

The instructor creates a new calculated column called:

> **Offer Price**

This is different from the YoY calculation from the previous session.

Previously, a **measure** was created.

Here, a **calculated column** is created because an Offer Price value needs to exist for **each individual row/property**.

---

# 4. Creating the Offer Price Calculated Column

### Steps

1. Go to the **Data pane**.
2. Locate the **Housing** table.
3. Right-click the Housing table.
4. Select:

> **New Column**

5. Expand the formula bar.
6. Name the new column:

```text
Offer Price
```

---

# 5. Offer Price Formula

The instructor uses the following formula:

$$
\text{Offer Price}
=
\frac{100 \times \text{Purchase Price}}
{100-\text{Percentage Change}}
$$

In DAX, conceptually:

```text
Offer Price =
100 * [Purchase Price]
/
(100 - [Percentage Change Between Offer and Purchase])
```

The percentage-change column is used in the denominator.

### Logic

Suppose:

* Purchase Price = 95
* Percentage Change = 5%

Then:

$$
Offer\ Price =
\frac{100 \times 95}{100-5}
$$

$$
=\frac{9500}{95}
$$

$$
=100
$$

So the calculated Offer Price is 100.

---

# 6. Why Is This Formula Used?

The relationship between offer price, purchase price, and percentage change can be represented as:

$$
Purchase\ Price
=
Offer\ Price
\times
\frac{100-\text{Percentage Change}}{100}
$$

Rearranging for Offer Price:

$$
Offer\ Price
=
\frac{100\times Purchase\ Price}
{100-\text{Percentage Change}}
$$

Therefore, the formula allows us to reconstruct the missing Offer Price using the two columns that already exist.

---

# 7. Applying the Calculated Column

After entering the formula:

1. Press **Enter**.
2. Collapse the formula bar if required.
3. Scroll horizontally to the right in the table.

You will now see:

> **Offer Price**

as a newly created column.

This column was not originally present in the dataset.

---

# 8. Switching to Report View

After creating the Offer Price column:

1. Go to **Report View**.
2. Click on a blank area of the report canvas.

Now the scatter plot can be created.

---

# 9. Creating the Scatter Plot

### Steps

1. Click on a blank area of the report canvas.
2. Select the **Scatter Chart/Scatter Plot** visual.
3. A blank scatter plot will appear.
4. Resize the visual as required.
5. Position it appropriately on the report page.

The instructor places the scatter plot toward the **right-hand side** of the report page.

---

# 10. Adding Offer Price to the Scatter Plot

The first numerical field added is:

> **Offer Price**

This is used for one axis of the scatter plot.

The instructor then adds:

> **Purchase Price**

for the other axis.

---

# 11. Removing Aggregation

An important step is performed after adding both columns.

By default, Power BI may automatically aggregate numerical columns.

For example, it may display:

> **Sum of Offer Price**

and:

> **Sum of Purchase Price**

But this is not what we want for a scatter plot representing the relationship between the two individual numerical values.

We want the actual values of each property.

Therefore, aggregation must be removed.

---

# 12. Set Offer Price to "Don't Summarize"

### Steps

1. Locate **Offer Price** in the scatter plot's field bucket.
2. Click its dropdown.
3. Change the aggregation from:

> **Sum**

to:

> **Don't summarize**

---

# 13. Set Purchase Price to "Don't Summarize"

Similarly:

1. Locate **Purchase Price**.
2. Click its dropdown.
3. Change it from:

> **Sum**

to:

> **Don't summarize**

---

# 14. Why "Don't Summarize"?

This is an important Power BI concept.

A scatter plot is being used here to examine the relationship between **two numerical variables at the individual-record level**.

Therefore, we don't want Power BI to calculate:

```text
SUM(Offer Price)
SUM(Purchase Price)
```

Instead, we want:

```text
Individual Offer Price
vs
Individual Purchase Price
```

for each property.

This produces individual points on the scatter plot.

---

# 15. Understanding the Scatter Plot

After configuring the two fields, the scatter plot displays many points.

Each point represents a property/record.

Conceptually:

```text
Purchase Price
       ↑
       │                •
       │             •
       │          •
       │       •
       │    •
       │ •
       └────────────────────→
             Offer Price
```

The scatter plot helps us understand whether there is a relationship between:

> **Offer Price and Purchase Price**

---

# 16. Identifying Outliers

The instructor observes that there are:

> **Some outliers**

in the scatter plot.

However, the majority of the data points are concentrated within a particular range.

### Important concept

An **outlier** is a data point that is significantly different from the majority of observations.

Scatter plots are particularly useful for identifying:

* Outliers
* Clusters
* Trends
* Relationships
* Correlations

---

# 17. Formatting the Scatter Plot

After creating the scatter plot, the instructor formats it to match the existing report design.

One shortcut used is:

> **Format Painter**

---

# 18. Using Format Painter

Instead of manually repeating all formatting settings from the line chart, the instructor copies the formatting.

### Steps

1. Select the existing **line chart**.
2. Click **Format Painter**.
3. Click the newly created **scatter plot**.

This copies the formatting from the line chart to the scatter plot.

### Advantage

Format Painter helps maintain:

> **Consistency across visuals**

without manually configuring every property again.

---

# 19. Formatting the Markers

The instructor then selects the scatter plot and opens:

> **Format Visual**

Then the **Markers** section is used.

### Steps

1. Select the scatter plot.
2. Click **Format Visual**.
3. Open **Markers**.
4. Change the marker color.
5. Select a color that matches the report theme.

The instructor uses the same general color theme as the other report elements.

---

# 20. Displaying Y-Axis Values

The instructor wants the values on the vertical axis to be visible.

### Steps

1. Select the scatter plot.
2. Open **Format Visual**.
3. Expand the **Y-axis** section.
4. Turn:

> **Values → On**

Now the numerical values are displayed along the vertical axis.

---

# 21. Formatting Y-Axis Values

The Y-axis values are then formatted to match the formatting of the horizontal axis.

The instructor adjusts properties such as:

* Font style
* Font size
* Text weight

The values are kept:

> **Bold**

and the font size can be increased slightly.

The objective is to maintain visual consistency.

---

# 22. Chart Title

The scatter plot needs a meaningful title.

The instructor uses:

> **Offer Price versus Purchase Price**

### Steps

1. Select the scatter plot.
2. Go to **General**.
3. Open **Title**.
4. Change the title to:

```text
Offer Price versus Purchase Price
```

---

# 23. Formatting the Chart Title

The chart title can then be formatted using the same style as the other visual.

The instructor uses the existing report theme and formatting.

The title is made visually consistent with the other chart titles.

---

# 24. Adding a Border

The scatter plot is given a visual border.

### Steps

1. Select the scatter plot.
2. Go to **Format Visual**.
3. Open:

```text
General
    ↓
Effects
```

4. Expand **Border** / **Visual Border**.
5. Enable the border.
6. Select an appropriate color.

Because the instructor previously used **Format Painter**, some of the border formatting has already been carried over from the line chart.

---

# 25. Enabling Gridlines

The instructor explains that gridlines can also be enabled on a scatter plot.

Gridlines can make it easier to estimate the position of individual points.

### Horizontal Gridlines

1. Select the scatter plot.
2. Go to **Format Visual**.
3. Open **Gridlines**.
4. Turn:

> **Horizontal Gridlines → On**

### Vertical Gridlines

Similarly:

> **Vertical Gridlines → On**

The instructor notes that the vertical gridlines are already enabled.

---

# 26. Zoom Sliders

Power BI also provides the option to add **Zoom Sliders** to the scatter plot.

### Steps

1. Select the scatter plot.
2. Open **Format Visual**.
3. Find **Zoom Slider**.
4. Enable it.

This adds sliders to the scatter plot.

---

# 27. Purpose of Zoom Sliders

Zoom sliders allow users to focus on a specific portion of the data.

For example, if the scatter plot contains:

* Many points
* Outliers
* A large numerical range

the user can adjust the sliders to zoom into a particular region.

This makes it easier to inspect the data.

---

# 28. Final Scatter Plot Configuration

The completed scatter plot contains:

### Numerical variables

**Offer Price**

vs.

**Purchase Price**

### Aggregation

Both fields:

> **Don't summarize**

### Visual

> Scatter Plot

### Formatting

* Appropriate marker color
* Visible axis values
* Bold axis values
* Chart title
* Visual border
* Gridlines
* Optional zoom sliders
* Consistent formatting with the existing report

---

# 29. Final Visual Structure

Conceptually:

```text
          Offer Price versus Purchase Price

Purchase
Price
  ↑
  │                         •
  │                    •
  │                •
  │             •
  │          •
  │      •
  │   •
  │ •
  └────────────────────────────────→
             Offer Price
```

The actual direction/axis assignment may depend on how the fields are placed in the scatter visual, but the objective is to analyze the relationship between the two variables.

---

# 30. Important Concepts Learned

## Calculated Column

A calculated column was created because the dataset did not directly contain Offer Price.

```text
Offer Price =
100 × Purchase Price
────────────────────────────
100 - Percentage Change
```

The result is calculated **row by row**.

---

## Scatter Plot

A scatter plot is useful for showing the relationship between **two numerical variables**.

Here:

> Offer Price ↔ Purchase Price

---

## Don't Summarize

When the objective is to plot individual record-level values, automatic aggregation such as `SUM` should be avoided.

Therefore:

```text
Offer Price → Don't summarize
Purchase Price → Don't summarize
```

---

## Outliers

The scatter plot makes it possible to visually identify points that are significantly different from the majority of the dataset.

The lecture observes that there are some outliers, while most observations lie within a particular range.

---

## Format Painter

Format Painter allows you to copy formatting from an existing visual to another visual.

In this case:

```text
Line Chart
    ↓
Format Painter
    ↓
Scatter Plot
```

This saves time and maintains consistency.

---

## Zoom Slider

Zoom sliders allow users to focus on a specific range of the scatter plot and inspect the data more closely.

---

# 31. Complete Step-by-Step Workflow

Here's the complete process from the beginning of the session:

```text
Existing Housing Dataset
        ↓
Check Table/Data View
        ↓
Purchase Price exists
        ↓
Offer Price does NOT exist
        ↓
Percentage Change Between
Offer and Purchase exists
        ↓
Create Calculated Column
        ↓
Housing → Right-click → New Column
        ↓
Column Name → Offer Price
        ↓
Calculate Offer Price
        ↓
Press Enter
        ↓
Offer Price column created
        ↓
Go to Report View
        ↓
Insert Scatter Plot
        ↓
Add Offer Price
        ↓
Add Purchase Price
        ↓
Remove aggregation
        ↓
Offer Price → Don't Summarize
Purchase Price → Don't Summarize
        ↓
Observe relationship/outliers
        ↓
Format Painter from Line Chart
        ↓
Format Markers
        ↓
Enable Y-axis values
        ↓
Format axis values
        ↓
Add chart title
        ↓
"Offer Price versus Purchase Price"
        ↓
Add/format border
        ↓
Enable gridlines if required
        ↓
Enable Zoom Slider if required
        ↓
Final Scatter Plot
```

---

# 32. Quick Revision Table

| Component                  | Configuration                                            |
| -------------------------- | -------------------------------------------------------- |
| Visual                     | Scatter Plot                                             |
| Purpose                    | Show relationship between Offer Price and Purchase Price |
| Offer Price                | Newly created calculated column                          |
| Purchase Price             | Existing column                                          |
| Offer Price aggregation    | Don't Summarize                                          |
| Purchase Price aggregation | Don't Summarize                                          |
| Title                      | Offer Price versus Purchase Price                        |
| Markers                    | Formatted to match report theme                          |
| Y-axis values              | On                                                       |
| Gridlines                  | Can be enabled                                           |
| Zoom Slider                | Can be enabled                                           |
| Border                     | Added/formatted                                          |
| Formatting shortcut        | Format Painter                                           |

---

# 33. Key Takeaway

The most important lesson from this session is that **you don't always need a column to already exist in the source dataset**.

If the required business metric can be mathematically derived from existing columns, you can create a **calculated column** in Power BI.

Here:

$$
\boxed{
Offer\ Price =
\frac{100 \times Purchase\ Price}
{100 - Percentage\ Change}
}
$$

Once the missing Offer Price was derived, it could be used alongside Purchase Price in a **scatter plot** to analyze their relationship and identify potential outliers.
