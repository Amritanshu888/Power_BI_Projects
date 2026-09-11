# Power BI — Adding & Formatting Visuals

## 1. Session Objective

In this session, the focus is on:

* Adding visuals to a Power BI report.
* Formatting visuals.
* Creating **DAX measures** for KPIs.
* Creating a dedicated **Measures table** to store measures.
* Using an AI tool such as **Perplexity** to get:

  * KPI suggestions
  * Recommended chart/visual types
  * DAX formulas
* Adding **page-level filters** so users can interactively filter the visuals.

The report design is based on the previously prepared PDF containing KPI and chart recommendations.

---

# 2. Creating the First Report Page

The first page of the report is based on the recommended theme:

> **Diamond Quality and Physical Characteristics**

### Steps

1. Open **Power BI Desktop**.
2. At the bottom of the report, locate **Page 1**.
3. Double-click the page name.
4. Rename it to:

**Diamond Quality and Physical Characteristics**

5. Press **Enter**.

This gives the first report page a meaningful name corresponding to the report theme.

---

# 3. First KPI — Average Carat

According to the previously prepared PDF, the first KPI recommended for this page is:

> **Average Carat**

The recommended visual for representing this KPI is a:

> **Card visual**

The DAX measure recommended by the AI tool is based on the `AVERAGE()` function.

Conceptually:

```DAX
Average Carat = AVERAGE(diamonds[carat])
```

### What does this measure do?

It calculates the average value of the `carat` column across the diamonds dataset.

The result can then be displayed as a single KPI using a Card visual.

---

# 4. Why Create a Separate Measures Table?

Instead of creating measures directly inside the `diamonds` table, the instructor creates a separate table specifically for storing measures.

This table is named:

> **Measures table**

This is useful because as the report grows, you may create many DAX measures.

Having a dedicated table makes the model easier to organize:

```text
Measures table
    ├── Average Carat
    ├── Average Price
    ├── Average Depth
    ├── ...
```

The actual data columns remain inside the `diamonds` table.

---

# 5. Creating the Measures Table

### Step-by-step

In **Power BI Desktop**:

1. Go to the **Home** tab.
2. Click:

**Enter data**

3. Power BI opens the table creation interface.
4. Create the table and name it:

**Measures table**

5. Click **Load**.

After loading:

* The **Measures table** appears in the **Data pane** on the right-hand side.
* Previously, this table was not present because it had not yet been created.

### Important

This table is primarily being used as a container for measures. The goal is to keep the DAX measures organized separately from the raw dataset.

---

# 6. Creating the Average Carat Measure

Now that the Measures table has been created, create the DAX measure.

### Steps

1. In the **Data pane**, locate:

**Measures table**

2. Right-click on **Measures table**.
3. Select:

**New measure**

Power BI will open the DAX formula bar.

---

## 7. Entering the DAX Formula

The formula recommended in the PDF is based on the `AVERAGE()` function.

Create the measure:

```DAX
Average Carat = AVERAGE(diamonds[carat])
```

### Explanation

| Part              | Meaning                                    |
| ----------------- | ------------------------------------------ |
| `Average Carat`   | Name of the measure                        |
| `=`               | Assignment operator                        |
| `AVERAGE()`       | DAX aggregation function                   |
| `diamonds[carat]` | The `carat` column from the diamonds table |

The `AVERAGE()` function calculates the arithmetic mean of the values in the specified column.

After entering the formula:

1. Press **Enter**.
2. The measure is created.

You should now be able to find **Average Carat** under the Measures table.

---

# 8. Creating the Card Visual

Now the measure needs to be represented visually.

Since **Average Carat** is a single KPI value, the recommended visual is a **Card**.

### Steps

1. Go to the report canvas.
2. Select the **Card** visual from the Visualizations pane.
3. Power BI creates a Card visual on the canvas.

The Card is appropriate because it is designed to highlight an important single numerical value.

For example:

```text
┌──────────────────────┐
│     Average Carat    │
│                      │
│        0.797         │
└──────────────────────┘
```

The actual value will depend on the dataset and current filters.

---

# 9. Adding the Average Carat Measure to the Card

With the Card visual selected:

1. Locate **Average Carat** in the Data/Fields pane.
2. Check/select the box beside **Average Carat**.

Power BI automatically uses the measure in the Card.

The Card now displays the average carat value.

---

# 10. Resizing the Card

The instructor then resizes the Card visual.

### Steps

1. Click the Card visual.
2. Use the handles around the visual.
3. Drag the handles to increase or decrease its size.
4. Position it appropriately on the report canvas.

The exact size and position can be finalized later when the complete dashboard layout is created.

---

# 11. Formatting the Card Visual

Power BI allows us to customize the appearance of the visual.

### Steps

1. Select the Card visual.
2. Open:

**Format visual**

The formatting options will appear.

---

# 12. Adding a Visual Border

Under the formatting options:

1. Go to:

**General**

2. Expand:

**Effects**

3. Locate:

**Visual border**

4. Turn the **Visual border** option **On**.

This adds a border around the Card.

A border can make individual KPI cards visually distinct from the report background.

---

# 13. Adding a Shadow

The instructor also enables a shadow effect.

### Steps

1. Keep the Card selected.
2. Go to:

**Format visual → General → Effects**
3. Find:

**Shadow**
4. Turn **Shadow** **On**.

This adds a shadow around the visual and can make the Card stand out from the report canvas.

---

# 14. Changing the Shadow Color

Power BI also allows customization of the shadow.

### Steps

1. Expand the **Shadow** settings.
2. Locate **Color**.
3. Click the color selector.
4. Choose the desired color.

The instructor selects a color for the shadow.

The exact color is a design choice and can be changed according to the overall report theme.

---

# 15. Positioning the Card

The instructor mentions that the position of the Card can also be changed.

However, positioning is not covered in detail in this session.

For now:

* Leave the Card where it is.
* Later, when all visuals have been created, arrange them properly on the report page.

This is useful because final positioning is easier once you know how many visuals will be present on the page.

---

# 16. Adding a Filter to the Page

The Card currently shows the **overall average carat**.

But we can make the report interactive by allowing users to filter the page.

For example, the user may want to know:

> What is the average carat for a particular diamond clarity?

For this, the instructor uses the `clarity` column.

---

# 17. Using the Clarity Column as a Page-Level Filter

The filter needs to be applied at the **page level**.

### Steps

1. Locate the **diamonds** table in the Data pane.
2. Expand the table.
3. Locate the:

**clarity**

column.

4. Drag the `clarity` column into:

**Filters on this page**

Alternatively, the transcript describes double-clicking/dragging the field into the page-level filter area.

The important destination is:

> **Filters on this page**

---

# 18. What Is a Page-Level Filter?

A page-level filter applies to the visuals on the current report page.

In this case:

```text
clarity filter
       ↓
Current report page
       ↓
Average Carat Card
```

When the user selects a particular clarity value, the Card recalculates the **Average Carat** based on the selected filter.

---

# 19. Example of Interactive Filtering

Suppose the `clarity` column contains categories such as:

* `IF`
* `VVS1`
* `VVS2`
* `VS1`
* `VS2`
* `SI1`
* `SI2`
* `I1`

If the user selects one particular clarity category, Power BI applies that filter to the page.

The measure:

```DAX
Average Carat = AVERAGE(diamonds[carat])
```

does **not** need to be rewritten.

Power BI's filter context automatically changes the calculation.

For example:

```text
No filter
    ↓
Average Carat = average of all diamonds

clarity = VS1
    ↓
Average Carat = average carat of VS1 diamonds

clarity = SI1
    ↓
Average Carat = average carat of SI1 diamonds
```

This demonstrates one of the important concepts in Power BI:

> **DAX measures respond dynamically to filter context.**

---

# 20. Important Concept — Measure vs Column

This session also demonstrates the difference between a raw column and a measure.

### Column

`diamonds[carat]`

This is an actual column containing the carat values for individual records.

### Measure

```DAX
Average Carat = AVERAGE(diamonds[carat])
```

This is a calculated value that Power BI evaluates based on the current filter context.

So:

```text
Raw data
   ↓
diamonds[carat]
   ↓
AVERAGE()
   ↓
Average Carat measure
   ↓
Card visual
```

When a filter is applied, the measure recalculates accordingly.

---

# 21. Role of AI in Report Creation

The instructor is using an AI tool to assist with report development.

The previously created PDF contains:

* KPI recommendations
* Recommended visual types
* DAX suggestions
* Report page structure
* Suggested metrics

The workflow is essentially:

```text
Dataset
   ↓
AI-assisted analysis
   ↓
KPI suggestions
   ↓
Chart/visual recommendations
   ↓
DAX suggestions
   ↓
Power BI implementation
```

The AI tool acts as an assistant rather than replacing the Power BI implementation process.

---

# 22. Complete Workflow Covered in This Session

The entire process can be summarized as:

### Step 1 — Rename the page

Rename Page 1 to:

**Diamond Quality and Physical Characteristics**

### Step 2 — Check the recommended KPI

From the previously prepared PDF:

**KPI → Average Carat**

### Step 3 — Create a Measures table

Go to:

**Home → Enter data**

Create:

**Measures table**

Then click **Load**.

### Step 4 — Create a measure

Right-click:

**Measures table → New measure**

### Step 5 — Write DAX

```DAX
Average Carat = AVERAGE(diamonds[carat])
```

Press **Enter**.

### Step 6 — Add a Card

Select the **Card** visual.

### Step 7 — Add the measure

Select/check:

**Average Carat**

The Card now displays the KPI.

### Step 8 — Resize the Card

Adjust the Card size using its handles.

### Step 9 — Format the Card

Go to:

**Format visual → General → Effects**

Enable:

* **Visual border**
* **Shadow**

Optionally customize the shadow color.

### Step 10 — Add a page-level filter

From the `diamonds` table:

**clarity → Filters on this page**

### Step 11 — Test the filter

Select different clarity values.

The **Average Carat** KPI changes dynamically based on the selected clarity.

---

# 23. Key Power BI Concepts From This Session

### 1. Measures table

A dedicated table used to organize DAX measures.

### 2. DAX measure

```DAX
Average Carat = AVERAGE(diamonds[carat])
```

Calculates average carat dynamically.

### 3. Card visual

Used to display a single important KPI.

### 4. Page-level filter

A filter applied to the current report page.

### 5. Filter context

The conditions/filters currently affecting a DAX calculation.

### 6. Dynamic measures

Measures automatically recalculate when the filter context changes.

---

# 24. Interview Perspective

A common Power BI interview question could be:

**Q: Why would you create a measure instead of simply calculating the average in the source data?**

**Answer:**
A DAX measure is evaluated dynamically according to the current filter context. Therefore, when users filter the report—for example, by `clarity`—the `Average Carat` measure automatically recalculates for the selected subset of data.

Another question:

**Q: Why create a separate Measures table?**

**Answer:**
A Measures table provides a centralized and organized location for DAX measures, especially when a Power BI report contains many KPIs and calculations. It improves model organization and makes measures easier to locate and maintain.

---

# 25. Quick Revision

```text
Page 1
   ↓
Diamond Quality and Physical Characteristics
   ↓
KPI: Average Carat
   ↓
Create Measures table
   ↓
New Measure
   ↓
Average Carat = AVERAGE(diamonds[carat])
   ↓
Card Visual
   ↓
Format
   ├── Visual Border → ON
   └── Shadow → ON
   ↓
Page Filter
   ↓
clarity → Filters on this page
   ↓
Select clarity
   ↓
Average Carat changes dynamically
```

### Most important takeaway

The core Power BI workflow demonstrated here is:

> **Create a DAX measure → place it in an appropriate visual → format the visual → add filters → observe how the measure dynamically responds to filter context.**
