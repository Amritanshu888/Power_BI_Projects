# Power BI Notes: Creating a Histogram for Price Distribution

## 1. Objective of the Session

The next visual recommended in the report-design PDF is **Price Distribution**.

The objective is to understand how the **price values are distributed across different ranges**.

For this visual:

* **No DAX measure is required.**
* The requirement is purely a visual representation.
* A **Histogram** is the recommended visualization.

A histogram groups numerical values into ranges called **bins** and shows how frequently values fall into each range.

---

# 2. What Is a Histogram?

A histogram is used to show the **distribution of a numerical variable**.

Instead of displaying every individual price, prices are divided into ranges.

For example:

```text
Price Range        Frequency
0–1000             ███████████
1000–2000          ███████████████
2000–3000          █████████
3000–4000          █████
4000–5000          ██
```

The:

* **X-axis** represents the price ranges/bins.
* **Y-axis** represents the frequency/count of observations.

This helps identify where most of the data is concentrated.

---

# 3. Using Perplexity for Guidance

The instructor does not know the exact process of creating a histogram in Power BI, so Perplexity is used again for step-by-step guidance.

The instructor provides the available database columns to Perplexity.

---

# 4. Step 1 — Check the Available Columns

The instructor opens **SQL Server Management Studio (SSMS)**.

The columns had already been retrieved using a query in the previous session.

The instructor:

1. Opens SQL Server Management Studio.
2. Views the available columns.
3. Copies the column names.
4. Goes back to Perplexity.
5. Pastes the column names into the prompt.
6. Asks Perplexity to explain how to create a histogram using the available data.

### Important point

This step is primarily used to provide Perplexity with context about the dataset.

The actual histogram is created later in **Power BI Desktop**.

---

# 5. Step 2 — Open Power BI Desktop

The data has already been loaded into Power BI Desktop.

Therefore:

* No data import is required.
* No new DAX measure is required.
* The existing dataset can be used directly.

The first important step is to create **bins** for the numerical column.

---

# 6. Step 3 — Create Bins

A histogram requires numerical values to be divided into ranges.

These ranges are called **bins**.

For example, if the price values are:

```text
500
750
1200
1500
1800
2300
2700
...
```

You could create bins such as:

```text
0–1000
1000–2000
2000–3000
...
```

Power BI can automatically create these bins.

---

# 7. How to Create a Bin in Power BI

The Perplexity instructions recommend creating a **New Group** for the numerical column.

### Process

1. Go to the **Data/Fields pane**.
2. Find the numerical column you want to use for the histogram.
3. Right-click the column.

Alternatively, depending on the Power BI interface, you can click the **three dots (`...`)** associated with the field.

4. Select:

**New Group**

A **Groups** dialog box will appear.

---

# 8. Step 4 — Select Bin as the Group Type

Inside the **Groups** dialog:

1. Locate **Group type**.
2. Select:

**Bins**

The Bin option should already be available/selected for a suitable numerical field.

This tells Power BI that the numerical data needs to be divided into ranges.

---

# 9. Step 5 — Set the Bin Size

The next important setting is **Bin size**.

Bin size determines the width of every range.

For example:

### Bin size = 1000

The ranges could be approximately:

```text
0–1000
1000–2000
2000–3000
3000–4000
...
```

### Smaller bin size

Creates more detailed ranges.

### Larger bin size

Creates fewer, broader ranges.

---

# 10. Examples Given in the Session

Perplexity gives examples depending on the numerical field.

For a field such as **Carat**, it suggests values such as:

```text
0.1
0.2
```

For **Price**, a possible bin size could be:

```text
1000
```

The exact value depends on the range and distribution of the data.

---

# 11. Bin Size Used in the Session

For the demonstration, the instructor chooses:

**Bin size = 0.2**

The value is entered into the Bin Size field.

Then:

1. Click **OK**.
2. Power BI creates the bins.

A new field is generated, referred to in the transcript as:

**Carat Bins**

This new field represents the ranges into which the original numerical values have been grouped.

---

# 12. Understanding the New Bin Field

After creating the bin, Power BI creates a new grouped field.

For example:

```text
Carat
   ↓
Carat Bins
   ↓
0.0–0.2
0.2–0.4
0.4–0.6
0.6–0.8
...
```

The original numerical column is still available.

The newly created **Bins** field is specifically useful for building the histogram.

---

# 13. Step 6 — Create a Clustered Column Chart

Power BI's native **Clustered Column Chart** can be used to create the histogram effect.

This is an important point:

> A dedicated Histogram visual is not necessarily required.

A histogram can be created using:

**Bins + Clustered Column Chart**

### Process

1. Click on a blank area of the report canvas.
2. Open the Visualizations pane.
3. Select **Clustered Column Chart**.

A blank clustered column chart will be created.

---

# 14. Step 7 — Add the Bin Field

The next step is to add the bin field to the chart.

Initially, the instructor follows the Perplexity recommendation to use the bin field.

The general configuration is:

```text
Bins → Axis
Bins/Relevant field → Values
```

The Values field should represent the **frequency/count** of observations in each bin.

---

# 15. Important Correction During the Process

The instructor notices that the initial field configuration needs to be adjusted.

The original bin field is removed from the X-axis configuration.

The actual numerical field, **Carat**, is then used on the X-axis.

### Process

1. Select the chart.
2. Remove the bin field from the X-axis bucket.
3. Select the original `Carat` field.
4. Drag it to the **X-axis**.

Power BI automatically treats the numerical field in a way that provides the required count/frequency representation.

---

# 16. Count of Values

The histogram needs to show **how many observations fall into each range**.

Therefore, the numerical field is aggregated as a **Count**.

When the field is added to the chart, Power BI can automatically display the count.

For example:

```text
Carat Range      Count
0.0–0.2           50
0.2–0.4           150
0.4–0.6           300
0.6–0.8           450
...
```

The exact values depend on the dataset.

---

# 17. Native Histogram Approach

The instructor chooses the first/native approach suggested by Perplexity:

### Option 1 — Native Power BI approach

**Bins + Clustered Column Chart**

This approach is used in the session.

Perplexity also mentions a second possibility:

### Option 2 — Marketplace Custom Visual

A custom histogram visual could be obtained from the Power BI marketplace.

However, the instructor does **not** use the custom visual because the native Power BI approach is sufficient.

---

# 18. Step 8 — Format the Histogram

Once the histogram has been created, the instructor begins formatting it.

The chart can be customized according to the report's design.

The transcript mentions several formatting options.

---

# 19. Step 9 — Use Format Painter

The instructor uses **Format Painter** to apply formatting.

### Process

1. Select the visual whose formatting you want to use as a reference.
2. Click **Format Painter**.
3. Click the histogram/chart.
4. The formatting is applied to the selected chart.

This is useful for keeping the formatting consistent across multiple visuals on the report page.

---

# 20. Step 10 — Turn Data Labels Off

For this histogram, the instructor does **not** want data labels displayed.

### Process

1. Select the histogram.
2. Open **Format your visual**.
3. Locate **Data labels**.
4. Change the setting to:

**Off**

This keeps the histogram visually cleaner.

---

# 21. Step 11 — Keep X-Axis Values Visible

The instructor wants the values along the horizontal axis to remain visible.

Therefore:

**X-axis → Values → On**

This allows users to understand the numerical ranges represented by the histogram.

---

# 22. Step 12 — Keep Y-Axis Values Visible

The Y-axis represents the frequency/count.

The instructor also keeps the Y-axis values visible.

### Process

1. Go to **Y-axis**.
2. Locate **Values**.
3. Set it to:

**On**

This allows the user to see the frequency/count associated with the bars.

---

# 23. Step 13 — Grid Lines

The instructor also considers keeping **grid lines** available for the chart.

Grid lines can make it easier to estimate the frequency represented by each column.

They are particularly useful on the Y-axis because they help users visually compare the heights of different bars.

---

# 24. Step 14 — Add Shadow and Border

The histogram is further formatted to match the other visuals.

### Process

1. Select the histogram.
2. Open **Format your visual**.
3. Go to **General**.
4. Open **Effects**.
5. Enable/configure **Shadow**.
6. Keep or adjust the shadow color as desired.
7. Enable/configure **Visual Border**.

The instructor is satisfied with the existing color and border configuration.

---

# 25. Step 15 — Resize the Existing Matrix

After creating the histogram, the instructor adjusts the layout of the report page.

The existing Matrix/heat-map visual occupies some space.

Therefore:

1. Select the Matrix visual.
2. Reduce its size slightly.
3. This creates additional room on the report page.

---

# 26. Step 16 — Increase Histogram Size

The histogram is then enlarged.

### Process

1. Select the histogram.
2. Drag its edges/corners.
3. Increase its size.
4. Position it appropriately within the report page.

The goal is to create a balanced report layout where the different visuals have enough space.

---

# 27. Final Histogram Concept

The resulting visualization represents the **distribution of the numerical variable** using bins and frequencies.

Conceptually:

```text
Frequency
   │
   │             ███
   │             ███
   │        ███  ███
   │        ███  ███       ███
   │   ███  ███  ███       ███
   │   ███  ███  ███  ███  ███
   └──────────────────────────────
       0.2  0.4  0.6  0.8  1.0
                Carat
```

The exact distribution depends on the underlying data.

---

# 28. Why Bins Are Necessary

A numerical field such as `Carat` contains many individual values.

Displaying every individual value would not give a useful distribution.

Bins group nearby values together.

For example:

```text
Individual values
0.21
0.22
0.23
0.24
0.25
...

        ↓

Bin

0.2–0.4
```

The histogram then counts how many observations belong to each bin.

---

# 29. Histogram Interpretation

A histogram can help answer questions such as:

* Where are most observations concentrated?
* Are values mostly low, medium, or high?
* Is the distribution symmetric?
* Is the distribution skewed?
* Are there relatively few high-value observations?
* Are there gaps in the distribution?
* Which range has the highest frequency?

Thus, the histogram provides an understanding of the **distribution of the underlying numerical variable**, rather than simply showing individual records.

---

# 30. Complete Step-by-Step Workflow

For revision, the complete process is:

```text
PDF Recommendation
        ↓
Price Distribution
        ↓
No DAX required
        ↓
Create Histogram
        ↓
Check available columns in SSMS
        ↓
Copy column names
        ↓
Provide columns to Perplexity
        ↓
Open Power BI Desktop
        ↓
Choose numerical field
        ↓
Right-click / three dots
        ↓
New Group
        ↓
Group Type → Bins
        ↓
Set Bin Size
        ↓
Click OK
        ↓
New Bin field created
        ↓
Insert Clustered Column Chart
        ↓
Add numerical/bin field
        ↓
Use Count for frequency
        ↓
Format chart
        ↓
Data Labels → Off
        ↓
X-axis Values → On
        ↓
Y-axis Values → On
        ↓
Keep/use Grid Lines
        ↓
General → Effects
        ↓
Shadow + Border
        ↓
Resize Matrix
        ↓
Increase Histogram size
        ↓
Position visuals appropriately
```

---

# 31. Important Power BI Concepts From This Session

## A. Bins

**Bins** divide continuous numerical data into ranges.

Example:

```text
0–100
100–200
200–300
...
```

They are fundamental for creating histograms.

---

## B. Bin Size

The **Bin Size** determines how wide each range is.

Smaller bin:

```text
0–0.2
0.2–0.4
0.4–0.6
...
```

Larger bin:

```text
0–1
1–2
2–3
...
```

Therefore:

> **Smaller bin size = more detailed distribution**

> **Larger bin size = broader distribution**

---

## C. Frequency

The histogram's vertical axis represents the number of records/observations within each bin.

This is why **Count** is important.

---

## D. Clustered Column Chart as Histogram

A standard Power BI **Clustered Column Chart** can be used to create a histogram when combined with appropriately created bins.

The general idea is:

```text
Numerical field
      ↓
     Bins
      ↓
Clustered Column Chart
      ↓
Count/Frequency
      ↓
Histogram
```

---

# 32. Formatting Choices Made in the Session

The final visual uses these important formatting decisions:

| Formatting             | Setting                     |
| ---------------------- | --------------------------- |
| Visual                 | Clustered Column Chart      |
| Purpose                | Price/variable distribution |
| Data labels            | Off                         |
| X-axis values          | On                          |
| Y-axis values          | On                          |
| Grid lines             | Kept/used                   |
| Shadow                 | On                          |
| Border                 | On                          |
| Shadow color           | Existing/selected color     |
| Formatting consistency | Format Painter              |
| Matrix size            | Reduced                     |
| Histogram size         | Increased                   |

---

# 33. Key Takeaways

1. **Price Distribution does not require a DAX measure.**
2. A **histogram** is appropriate for displaying numerical-data distribution.
3. Power BI can create a histogram using a **native Clustered Column Chart**.
4. The numerical field should first be divided into **bins**.
5. Bins can be created through:
   **Right-click numerical field → New Group → Bins**.
6. **Bin Size** determines the width of each range.
7. In the demonstration, a bin size of **0.2** is used for the numerical field shown in the transcript.
8. The resulting bin field can be used to construct the histogram.
9. The frequency is represented using a **Count**.
10. A marketplace histogram visual is another option, but it isn't necessary for this use case.
11. **Format Painter** can be used to maintain consistent formatting across visuals.
12. Data labels were turned **Off**.
13. X-axis and Y-axis values were kept **On**.
14. Grid lines can help with reading frequencies.
15. A border and shadow can be added under **General → Effects**.
16. The final visual can be resized and repositioned to maintain a clean report-page layout.
17. The histogram provides insight into **how the numerical data is distributed across different ranges**.

### One-line revision

> **To create a histogram in Power BI: create bins for a numerical field → insert a Clustered Column Chart → use the bins on the axis → use Count as frequency → format the axes and visual for readability.**
