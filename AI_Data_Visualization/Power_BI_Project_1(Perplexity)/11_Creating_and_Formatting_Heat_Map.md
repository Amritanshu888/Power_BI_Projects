# Power BI Notes: Creating a Heat Map for Average Price by Color Grade

## 1. Objective of the Session

In the previous session, a **Card Visual** was created to display a KPI.

In this session, the next KPI from the prepared PDF/report recommendations is implemented:

> **Price by Color Grade**

The objective is to visualize the **average diamond price for each color grade** using a **heat map**.

The recommended DAX measure is:

```DAX
Average Price = AVERAGE(diamonds[price])
```

This measure has already been created and was previously used in the Card Visual, so there is no need to create it again.

---

# 2. KPI: Price by Color Grade

The report recommendation specifies:

* **Dimension/Column:** `Color`
* **Measure:** `Average Price`
* **Recommended visual options:**

  * Bar Chart
  * Heat Map

A **bar chart** was already created in the previous work, so this session focuses on creating a **heat map**.

---

# 3. Using Perplexity for Guidance

Since the exact process for creating a heat map in Power BI Desktop was not known, an AI tool such as **Perplexity** was used for guidance.

The prompt given was essentially:

> I have to create a heat map in Power BI Desktop. I have a column called Color and a DAX measure called Average Price. I don't know how to create a heat map in Power BI Desktop. Guide me step by step.

The response explained that a heat-map effect can be created using Power BI's built-in **Matrix Visual** combined with **Conditional Formatting**.

### Important point

Power BI Desktop does not necessarily require a dedicated "Heat Map" visual for this use case.

A **Matrix + Conditional Formatting → Background Color** can produce the desired heat-map effect.

---

# 4. Step 1 — Open Power BI Desktop

Open the existing Power BI report.

The data has already been loaded and the required fields/measures are already available.

Therefore, there is **no need to reload or prepare the data**.

---

# 5. Step 2 — Confirm the Required Measure

The required DAX measure is:

```DAX
Average Price = AVERAGE(diamonds[price])
```

This measure calculates the **average price of diamonds**.

It was already created in the previous session and used in the Card Visual.

Therefore, the same measure can be reused for this heat map.

### Required fields

You should have:

| Field           | Purpose                      |
| --------------- | ---------------------------- |
| `Color`         | Diamond color grade/category |
| `Average Price` | Average diamond price        |

---

# 6. Step 3 — Select the Matrix Visual

Go to the **Visualizations** pane in Power BI Desktop.

Instead of selecting a dedicated heat-map chart, select the:

**Matrix visual**

### Process

1. Click on a **blank area of the report canvas**.
2. Go to the **Visualizations** pane.
3. Locate the **Matrix** visual.
4. Click the Matrix icon.

A blank Matrix Visual will appear on the report canvas.

### Why Matrix?

The Matrix allows us to:

* Display the `Color` categories as rows.
* Display `Average Price` as values.
* Apply **conditional background colors** to the values.
* Use those colors to create the heat-map appearance.

---

# 7. Step 4 — Resize the Matrix

Once the Matrix Visual has been created:

1. Select the Matrix.
2. Resize it according to the available space on the report canvas.
3. Adjust its width and height so the values and color categories are clearly visible.

The exact size depends on the report-page layout.

---

# 8. Step 5 — Add the Color Field

Now populate the Matrix.

The first field required is the **Color** column.

### Process

From the Data/Fields pane:

1. Locate the `Color` column.
2. Drag it into the **Rows** field/bucket of the Matrix.

Alternatively, the transcript mentions double-clicking the field and then moving it into the appropriate bucket.

After this, the different diamond color grades will appear as rows.

For example, the Matrix may contain categories such as:

* D
* E
* F
* G
* H
* I
* J

---

# 9. Step 6 — Add the Average Price Measure

Now add the measure that represents the price.

### Process

1. Locate the **Average Price** DAX measure.
2. Drag it into the **Values** field/bucket of the Matrix.

The Matrix will now contain:

**Rows → Color**

**Values → Average Price**

Conceptually:

| Color | Average Price |
| ----- | ------------: |
| D     | Average price |
| E     | Average price |
| F     | Average price |
| G     | Average price |
| H     | Average price |
| I     | Average price |
| J     | Average price |

At this point, the Matrix is functioning as a normal table/matrix.

---

# 10. Step 7 — Apply Conditional Formatting

This is the most important step.

The Matrix itself is not yet a heat map.

The **heat-map effect is created using Conditional Formatting**.

### Process

1. Select the Matrix Visual.
2. Locate the **Values** section in the Visualizations pane.
3. Find the `Average Price` field.
4. Click the **dropdown arrow** next to the value field.
5. Select:

**Conditional formatting → Background color**

This allows Power BI to automatically change the background color of each value based on its numerical value.

---

# 11. Step 8 — Configure the Background Color

After selecting:

**Conditional formatting → Background color**

Power BI opens the conditional-formatting configuration window.

Here you can configure the color scale.

The idea is:

* **Low values** → lighter color
* **Higher values** → stronger/darker color

This produces the visual appearance of a heat map.

---

# 12. Step 9 — Configure the Color Scale

The formatting logic can be based on the value.

The transcript describes using a **low → medium → high** type of color scale.

For example:

### Low value

Choose a very light color, such as:

**White**

### High value

Choose a stronger color.

The exact color is a design choice and can be selected according to the report's theme.

The important concept is that Power BI automatically assigns colors according to the numerical value.

So:

> Lower average price → lighter background

> Higher average price → stronger/darker background

This allows the user to identify relative price differences quickly.

---

# 13. Step 10 — Apply the Conditional Formatting

After selecting the desired colors:

1. Configure the lowest-value color.
2. Configure the highest-value color.
3. Use the appropriate value-based formatting logic.
4. Click **OK**.

Power BI then applies the background-color scale to the `Average Price` values.

The Matrix now visually behaves like a **heat map**.

---

# 14. Understanding the Heat Map

The resulting visual allows you to quickly compare average prices across diamond color grades.

Instead of looking only at the numerical values, the user can also interpret the intensity of the background color.

For example:

| Color | Average Price | Heat-map interpretation |
| ----- | ------------: | ----------------------- |
| D     |         Lower | Lighter                 |
| E     |         Lower | Lighter                 |
| F     |        Medium | Medium                  |
| G     |        Medium | Medium                  |
| H     |        Higher | Darker                  |
| I     |        Higher | Darker                  |
| J     |        Higher | Darker                  |

The exact values and color intensity depend on the underlying dataset.

---

# 15. Step 11 — Format the Matrix

After creating the heat map, additional formatting can be performed to improve readability.

Select the Matrix and open:

**Format your visual**

The transcript demonstrates several formatting changes.

---

## 15.1 Increase Column Header Size

To make the column headings easier to read:

1. Select the Matrix.
2. Open **Format your visual**.
3. Go to **Column headers**.
4. Increase the text size.

This makes the column header more readable.

---

# 16. Increase Values Text Size

The values inside the Matrix can also be enlarged.

### Process

1. Open **Format your visual**.
2. Go to **Values**.
3. Increase the text size.

This improves readability of the average-price numbers.

---

# 17. Rename the Row Header

The default row heading may appear as:

**color**

The transcript changes it to:

**Color**

This is a small but useful formatting improvement.

The purpose is simply to make the report look more polished and consistent.

---

# 18. Adjust Row Header Size

The row headers can also be formatted.

### Process

1. Select the Matrix.
2. Open **Format your visual**.
3. Select **Row headers**.
4. Increase the text size as required.

This makes the Color categories easier to read.

---

# 19. Explore Matrix Layout and Style

The Matrix also provides different layout and style options.

Under the formatting options, you can explore:

* **Layout**
* **Style**

The transcript mentions that the default style can be changed.

For example, the style can be changed to:

* Default
* None
* Minimal

The exact options available can vary depending on the Power BI version.

### Recommendation from the session

The instructor experiments with the available styles and chooses a style that looks cleaner.

The important takeaway is that **Matrix formatting is customizable**, so you can choose the appearance that fits the overall report design.

---

# 20. Change the Matrix Layout

The Matrix also provides layout options.

The transcript mentions trying options such as:

* Outline
* Tabular

These control how the Matrix structure is displayed.

Again, the appropriate choice depends on the report design.

The objective is to choose the layout that makes the Color and Average Price information easiest to understand.

---

# 21. Add a Border

The Matrix can also be given a border.

### Process

1. Select the Matrix.
2. Open **Format your visual**.
3. Go to **General**.
4. Locate **Effects**.
5. Enable/configure **Border**.

A border can help visually separate the heat map from other report elements.

---

# 22. Add a Shadow

The transcript also adds a shadow to the visual.

### Process

1. Select the Matrix.
2. Open **Format your visual**.
3. Go to **General**.
4. Go to **Effects**.
5. Select **Shadow**.
6. Enable the shadow.
7. Adjust the shadow settings as desired.

The instructor changes the shadow color from the default black to a lighter/white-toned option and adjusts the appearance.

The goal is to make the visual look cleaner and better integrated with the report page.

---

# 23. Resize and Reposition the Heat Map

Once all formatting is complete, the Matrix can be resized and repositioned.

The instructor mentions that the visual can be placed at a suitable location, for example:

**On the right-hand side of the report page.**

### Process

1. Select the Matrix.
2. Drag its edges to change the dimensions.
3. Drag the entire visual to the desired position.
4. Align it with the other visuals on the report page.

The final position should be chosen based on the overall report layout.

---

# 24. Final Structure of the Heat Map

The completed visual essentially consists of:

```text
            Average Price
Color       ┌──────────────┐
D           │     value    │
E           │     value    │
F           │     value    │
G           │     value    │
H           │     value    │
I           │     value    │
J           │     value    │
            └──────────────┘
             ↑
       Background color
       represents value
```

The numerical values remain visible, while their background colors provide an additional visual cue.

---

# 25. Complete Step-by-Step Workflow

For quick revision, the entire process is:

### Data/Measure Preparation

1. Open the existing Power BI report.
2. Confirm that the `Color` column exists.
3. Confirm that the `Average Price` measure already exists.

```DAX
Average Price = AVERAGE(diamonds[price])
```

### Create Heat Map

4. Click a blank area of the report canvas.
5. Select the **Matrix** visual.
6. Resize the Matrix.
7. Drag `Color` → **Rows**.
8. Drag `Average Price` → **Values**.

### Create Heat-map Effect

9. Select the dropdown next to `Average Price`.
10. Select **Conditional formatting**.
11. Select **Background color**.
12. Configure the color scale.
13. Select a light color for the lower values.
14. Select a stronger/darker color for higher values.
15. Click **OK**.

### Format the Visual

16. Open **Format your visual**.
17. Adjust **Column headers** text size.
18. Adjust **Values** text size.
19. Adjust **Row headers** text size.
20. Change `color` to `Color` if required.
21. Explore **Layout** options.
22. Explore **Style** options.
23. Select an appropriate style such as Minimal if desired.
24. Experiment with layout options such as Outline or Tabular.
25. Go to **General → Effects**.
26. Add a **Border** if required.
27. Enable a **Shadow** if required.
28. Adjust the shadow appearance.
29. Resize the Matrix.
30. Position it appropriately on the report page.

---

# 26. Key Concept to Remember

### A Matrix + Conditional Formatting = Simple Heat Map

You don't necessarily need a specialized heat-map visual.

For this particular requirement:

```text
Color
  ↓
Matrix Rows

Average Price
  ↓
Matrix Values

Conditional Formatting
  ↓
Background Color

Background Color Scale
  ↓
Heat Map Effect
```

This is the central technique demonstrated in the session.

---

# 27. Why This Visualization Is Useful

The heat map provides two pieces of information simultaneously:

### Numerical information

The actual **Average Price** is displayed.

### Visual information

The background color indicates whether the value is relatively low, medium, or high.

This makes it easier for report users to scan the data quickly rather than reading every number individually.

---

# 28. Session Takeaways

* The KPI being implemented is **Price by Color Grade**.
* The required measure is **Average Price**.
* The `Average Price` measure was already created in the previous session.
* A bar chart had already been created, so this session demonstrates a heat-map alternative.
* Power BI's **Matrix Visual** can be used to create a heat map.
* `Color` goes into **Rows**.
* `Average Price` goes into **Values**.
* The heat-map effect is created using:
  **Conditional Formatting → Background Color**.
* A color scale can be configured from low to high values.
* Lower values can use a lighter color, while higher values can use a stronger/darker color.
* The Matrix can be further customized using:

  * Column Headers
  * Row Headers
  * Values
  * Layout
  * Style
  * Border
  * Shadow
  * General/Effects
* The completed visual can be resized and positioned anywhere appropriate on the report page.
* The overall purpose is to make **average diamond prices across color grades visually easy to compare**.
