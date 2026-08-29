## Donut Chart – Average Price per Square Meter by Region

### 1. Objective

The objective of this session is to create a **Donut Chart** in Power BI to represent the **average price per square meter for different regions**.

The overall process is:

1. Create a measure for average price per square meter.
2. Insert a Donut Chart.
3. Add the average price measure to the chart values.
4. Add **Region** as the legend.
5. Format the chart.
6. Understand how filtering/interactions work between this chart and other visuals.

---

# 2. Create the Average Price per Square Meter Measure

Before creating the visual, we need a measure that calculates the average price per square meter.

### Steps

1. Go to the **Measures table** in the Fields/Data pane.
2. **Right-click** on the Measures table.
3. Select **New Measure**.
4. Wait for the formula bar to load.
5. Create the measure for average square-meter price.

The lecture uses the following concept:

```DAX
Average Price per Square Meter =
AVERAGE(<Square Meter Price Column>)
```

> Replace `<Square Meter Price Column>` with the actual column containing the square-meter price.

6. Press **Enter**.

This creates the **Average Price per Square Meter** measure.

### Purpose of the measure

The measure calculates the average price per square meter and can then be evaluated separately for each **Region** when Region is used as a category/legend in the visual.

---

# 3. Create the Donut Chart

Now we will represent the measure visually.

### Steps

1. Click on a **blank area of the report canvas**.
2. From the **Visualizations** pane, select the **Donut Chart**.
3. Power BI creates a blank donut chart.
4. Resize the chart according to the available space.
5. Position it appropriately on the report page.

---

# 4. Add Data to the Donut Chart

The requirement is:

> Show the **average price per square meter for different regions**.

Therefore, we need:

* **Values → Average Price per Square Meter**
* **Legend → Region**

### Add the measure

1. Select the donut chart.
2. Drag and drop the **Average Price per Square Meter** measure into the **Values** field.

### Add Region

1. Double-click **Region** from the Fields pane or select it.
2. Drag and drop **Region** into the **Legend** bucket.

The donut chart will now divide itself into different slices, with each slice representing a different **region**.

Conceptually:

```text
                 Region
                   ↓
          ┌─────────────────┐
          │   DONUT CHART   │
          │                 │
          │ Average Price   │
          │ per Sq. Meter   │
          └─────────────────┘
```

---

# 5. Format the Donut Chart

The lecture then formats the donut chart so that it matches the overall report design.

## A. Copy Formatting Using Format Painter

The instructor uses an existing bar chart as a formatting reference.

### Steps

1. Click on the existing **bar chart**.
2. Click **Format Painter**.
3. Click on the newly created **Donut Chart**.

This copies the formatting from the existing chart to the donut chart.

---

# 6. Remove/Change the Background

The lecture does not want an unwanted background around the donut chart.

### Steps

With the donut chart selected:

1. Go to **Format Visual**.
2. Go to **General**.
3. Find **Effects**.
4. Locate **Background**.

You can either:

* Turn the background **Off**, or
* Keep it **On** and change the background color to **White**.

The objective is to ensure that an unwanted background does not appear behind the donut chart.

---

# 7. Change Donut Slice Colors

Next, the individual donut slices are formatted with different colors.

### Steps

1. Select the donut chart.
2. Go to **Format Visual**.
3. Open **Slices**.
4. Select the individual region/slice.
5. Change its color.
6. Repeat for the other regions.

The lecture specifically demonstrates:

* Selecting one slice.
* Choosing another color for another region.
* Using **More** to access additional color options.
* Selecting different colors for the different regions.

You can choose colors according to your own report/theme.

### Important

Each region should ideally have a visually distinct color so that users can easily differentiate the slices.

---

# 8. Display Detailed Labels

The lecture then configures the donut chart to display more information directly on the chart.

### Steps

1. Select the donut chart.
2. Go to **Format Visual**.
3. Open **Detail labels**.
4. Locate **Label contents**.
5. Select **All details**.

This allows Power BI to display all the relevant details that are available for the donut chart.

The labels can provide additional information associated with the values/slices.

---

# 9. Format the Detail Labels

After enabling the labels, additional formatting can be applied.

The lecture mentions the following formatting options:

### Label size

You can reduce the label size if the labels are too large.

### Label color

You can choose a suitable color for the labels.

### Font

You can make the label text **Bold** if required.

So the general formatting process is:

**Detail labels → Label contents → All details → Adjust size/color/font**

---

# 10. Format the Legend

The **Region** field is being used as the legend, so the legend can also be formatted.

### Steps

1. Keep the donut chart selected.
2. Go to the **Legend** formatting section.
3. Under **Text**, adjust the legend formatting.

You can:

* Change the **text color**.
* Make the legend text **Bold**.
* Reduce the **text size** if required.

This helps make the legend consistent with the rest of the report.

---

# 11. Final Donut Chart Structure

The completed visual essentially contains:

| Donut Chart Component | Field/Setting                          |
| --------------------- | -------------------------------------- |
| Visual type           | Donut Chart                            |
| Values                | Average Price per Square Meter         |
| Legend                | Region                                 |
| Slices                | Different colors for different regions |
| Detail Labels         | All details                            |
| Background            | Off or White                           |
| Labels                | Customized size/color/boldness         |
| Legend                | Customized size/color/boldness         |

---

# 12. Understanding Visual Interactions and Filtering

An important concept discussed at the end of the lecture is **how this donut chart interacts with other visuals** on the report page.

The lecture refers to a previously created **Sales by Region** chart and the use of the **ALL EXCEPT** function.

The important idea is that the earlier Sales by Region calculation was designed so that **Region remains the filtering field**.

In other words, the calculation was structured such that filtering by **Region** can affect the Sales by Region result, while other fields do not affect it in the same way.

---

## 13. Selecting a Region in the Donut Chart

Suppose you click on one of the regions in the donut chart.

Because the donut chart contains **Region**, selecting a region causes the other appropriate visuals to be filtered/highlighted based on that region.

For example:

```text
Donut Chart
    │
    │ Select Region
    ↓
Other Visuals
    │
    ↓
Filtered/Highlighted
```

So, selecting a region from the donut chart can affect the other visuals on the report page.

---

# 14. Interaction with the Table Visual

The lecture also discusses the interaction between the donut chart and a **table visual**.

If you select something from the table visual, the donut chart can get filtered because the table contains fields that participate in the relevant filtering context.

However, something important happens with the **Sales by Region** chart.

The Sales by Region chart does **not** get affected by the table visual in the same way.

### Why?

The reason is related to the DAX calculation used for the Sales by Region measure.

The calculation uses the **ALL EXCEPT** concept, meaning the calculation preserves the filtering effect of the **Region** field while removing the effect of other fields.

The lecture specifically points out:

> The table visual does not contain the Region field.

Therefore, the Sales by Region calculation continues to behave according to the Region-based filtering logic.

---

# 15. Key Concept – ALL EXCEPT

The important DAX concept being reinforced here is **`ALLEXCEPT()`**.

Conceptually:

```DAX
ALLEXCEPT(
    Table,
    Table[Region]
)
```

means:

> Remove filters from the table **except for the filter on Region**.

So if other columns attempt to filter the calculation, those filters can be ignored, while the **Region filter is preserved**.

### Example

Suppose the data contains:

* Region
* Property Type
* Price
* Area
* Other attributes

If the calculation uses:

```DAX
ALLEXCEPT(Table, Table[Region])
```

then:

| Filter                            | Effect on calculation |
| --------------------------------- | --------------------- |
| Region                            | ✅ Preserved           |
| Property Type                     | ❌ Removed             |
| Other columns                     | ❌ Removed             |
| Other filters from the same table | ❌ Generally removed   |

This is why the Sales by Region visual behaves differently from a normal visual when interacting with other report elements.

---

# 16. Important Takeaways

### Donut Chart Creation

* Use a **Donut Chart** when you want to show the contribution/distribution of categories as parts of a whole.
* Here, the categories are **Regions**.
* The numerical value is **Average Price per Square Meter**.

### Measure

Create a dedicated measure for:

**Average Price per Square Meter**

using the `AVERAGE()` aggregation.

### Field placement

```text
Values → Average Price per Square Meter
Legend → Region
```

### Formatting

The lecture demonstrates:

* Format Painter
* Background formatting
* Slice colors
* Detail labels
* Label contents → All details
* Label size
* Label color
* Bold labels
* Legend text color
* Bold legend
* Legend size

### Filtering

* Selecting a region in the donut chart can filter/interact with other visuals.
* The behavior of the **Sales by Region** chart is controlled by its DAX logic.
* `ALLEXCEPT()` is used so that **Region remains the relevant filter** while other filters can be removed.
* This explains why the Sales by Region visual may not respond to selections from a table that does not contain the Region field.

---

## Final Flow to Remember

```text
Create Measure
      ↓
Average Price per Square Meter
      ↓
Insert Donut Chart
      ↓
Values → Average Price per Square Meter
      ↓
Legend → Region
      ↓
Format Painter
      ↓
Format Background
      ↓
Format Slice Colors
      ↓
Enable Detail Labels
      ↓
Label Contents → All Details
      ↓
Format Labels
      ↓
Format Legend
      ↓
Test Visual Interactions
      ↓
Understand ALLEXCEPT-based filtering
```

This completes the session on **creating and formatting a Donut Chart for Average Price per Square Meter by Region**, along with the related concept of **visual interactions and `ALLEXCEPT()` filtering behavior**.
