# Detailed Notes: Creating a Clustered Column Chart for Middle-Aged Adults

## 1. Objective of the Session

In this session, a **Clustered Column Chart** is added to the second report page.

The purpose of the chart is to represent:

> **Total Loan Amount for Middle-Aged Adults**

The visual also provides additional insights by showing:

* Whether the person **has a mortgage or not**
* Whether the person **has dependents or not**

A **DAX measure** is created first and then used in the clustered column chart.

---

# 2. Overall Workflow

The process followed in the session is:

**Measures Table 2**
↓
Create a **New Measure**
↓
Use `SUMX()` + `FILTER()`
↓
Filter `Age Group = Middle Age Adults`
↓
Calculate total `Loan Amount`
↓
Create/duplicate a **Clustered Column Chart**
↓
Place the measure on the **Y-axis**
↓
Place **Has Mortgage** on the **X-axis**
↓
Place **Has Dependents** in **Legend**
↓
Format colors
↓
Change chart title
↓
Adjust spacing/layout

---

# 3. Create the DAX Measure

Since the measure is intended to be used on the **second report page**, it is created inside **Measures Table 2**.

### Steps

1. Expand the **Data pane** on the right.
2. Locate **Measures Table 2**.
3. Right-click **Measures Table 2**.
4. Select **New Measure**.

The lecture notes that Power BI may sometimes take some time to display the formula bar. This is normal if the interface is temporarily slow.

---

# 4. Name the Measure

Expand the formula bar and give the measure a meaningful name.

A suitable name used in the lecture is:

> **Total Loan Middle Age Adults**

The exact naming can be adjusted, as long as the name clearly indicates that the measure calculates the total loan amount for middle-aged adults.

---

# 5. DAX Functions Used

The measure uses:

* `SUMX()`
* `FILTER()`

The basic logic is:

> Filter the Loan Default table to only Middle Age Adults and then calculate the total Loan Amount.

---

# 6. DAX Formula

The measure follows this structure:

```DAX id="j0h0fl"
Total Loan Middle Age Adults =
SUMX(
    FILTER(
        'Loan Default',
        'Loan Default'[Age Group] = "Middle Age Adults"
    ),
    'Loan Default'[Loan Amount]
)
```

> Use the exact table and column names from your own Power BI model. In the lecture, IntelliSense is used to select the appropriate table/columns.

---

# 7. Understanding the `FILTER()` Function

The first important part is:

```DAX id="o2q4l7"
FILTER(
    'Loan Default',
    'Loan Default'[Age Group] = "Middle Age Adults"
)
```

The `FILTER()` function filters the **Loan Default** table.

The condition is:

```text id="7v6k5f"
Age Group = "Middle Age Adults"
```

Therefore, only records belonging to the **Middle Age Adults** category are considered.

---

# 8. Understanding the `SUMX()` Function

After filtering the table, `SUMX()` evaluates the **Loan Amount** for each remaining row and adds the results.

Conceptually:

```text id="fdx9qg"
Loan Default table
       ↓
Filter Age Group
       ↓
Middle Age Adults only
       ↓
Take Loan Amount
       ↓
Add all Loan Amount values
       ↓
Total Loan Amount
```

So the final measure represents:

> **Total Loan Amount for Middle Age Adults**

---

# 9. Finish Creating the Measure

After writing the DAX expression:

1. Press **Enter**.
2. Wait for Power BI to finish processing the measure.
3. Collapse the formula bar if desired.

The measure is now available under **Measures Table 2**.

---

# 10. Create the Clustered Column Chart

The next step is to create the visual.

The lecture initially creates a blank clustered column chart, but then uses a more convenient approach by duplicating an existing chart.

### Recommended approach demonstrated in the lecture

1. Select the existing line chart.
2. Press **Ctrl + C**.
3. Press **Ctrl + V**.
4. Move the copied chart to the desired location.
5. Change the copied visual to a **Clustered Column Chart**.

This avoids creating and formatting a completely new visual from scratch.

---

# 11. Change the Visual to Clustered Column Chart

With the copied visual selected:

1. Go to the **Visualizations** pane.
2. Select **Clustered Column Chart**.

The copied visual is converted into a clustered column chart.

---

# 12. Remove the Existing Fields

Because the copied chart originally contained fields related to the previous line chart, these fields need to be removed.

The lecture removes:

* **Total Loan Credit**
* **Credit Score Bins**

The objective is to configure the chart specifically for **Middle Age Adults**.

---

# 13. Add the Middle-Age Loan Measure to the Y-Axis

The newly created measure:

> **Total Loan Middle Age Adults**

is used as the numerical value.

### Steps

1. Locate the **Total Loan Middle Age Adults** measure.
2. Drag it into the **Y-axis** bucket.

This establishes the measure that the columns will represent.

---

# 14. Add Has Mortgage to the X-Axis

The chart should show whether middle-aged adults have a mortgage.

The field used is:

> **Has Mortgage**

### Steps

1. Locate **Has Mortgage** in the Data pane.
2. Double-click it or drag it.
3. Place it into the **X-axis** bucket.

The X-axis now contains the mortgage categories, such as:

* `True`
* `False`

depending on the underlying data.

---

# 15. Add Has Dependents to the Legend

The chart also needs to distinguish whether people have dependents.

The field used is:

> **Has Dependents**

### Steps

1. Locate **Has Dependents**.
2. Drag it into the **Legend** bucket.

Now the chart can compare the loan amounts based on both:

* Mortgage status
* Dependent status

---

# 16. How the Chart Is Structured

The final structure is:

| Chart Component | Field                        |
| --------------- | ---------------------------- |
| **X-axis**      | Has Mortgage                 |
| **Y-axis**      | Total Loan Middle Age Adults |
| **Legend**      | Has Dependents               |

This creates multiple columns for each mortgage category, with different series representing whether the person has dependents.

---

# 17. Example of the Analysis

The visual allows you to answer questions such as:

* What is the total loan amount for middle-aged adults who **have a mortgage**?
* What is the total loan amount for middle-aged adults who **do not have a mortgage**?
* How does the total differ between people who **have dependents** and those who **do not have dependents**?

Thus, the chart provides a multi-dimensional view of the loan data.

---

# 18. Format the Column Colors

The next step is to customize the colors of the different **Has Dependents** series.

### Steps

1. Select the clustered column chart.
2. Click **Format Your Visual**.
3. Locate the **Columns** section.
4. Under **Series**, select the relevant category.

The lecture formats the two categories:

* `False`
* `True`

---

## 19. Color for `False`

For the **False** category:

1. Select the `False` series.
2. Open **Colors**.
3. Select **More Colors**.
4. Enter:

> **#46B1C9**

This color is used for the series where the person does **not** have dependents.

---

## 20. Color for `True`

For the **True** category:

1. Select the `True` series.
2. Open **Colors**.
3. Select **More Colors**.
4. Enter:

> **#BCC1B**

The lecture specifies this color as `BCC1B`.

---

# 21. Change the Chart Title

The default title should be replaced with a title that clearly describes the visual.

### Steps

1. Select the clustered column chart.
2. Click **Format Your Visual**.
3. Go to **General**.
4. Expand **Title**.
5. Enter:

> **Loan for Middle Age Adults by Has Mortgage / Dependents**

This title communicates that the chart shows:

* Loan amount
* Middle-aged adults
* Mortgage status
* Dependents status

---

# 22. Format the Chart Layout

The chart can be further formatted to improve readability.

### Steps

1. Select the chart.
2. Open **Format Your Visual**.
3. Go to **Columns**.
4. Scroll down.
5. Under **Series**, select **All**.
6. Locate the **Layout** options.

The lecture discusses two spacing-related settings.

---

# 23. Increase Spacing Between Categories

The spacing between categories can be increased using the appropriate layout setting.

This helps separate the different **Has Mortgage** categories visually.

Increasing the spacing can make the chart easier to read when there are multiple series.

---

# 24. Increase Spacing Between Series

The spacing between the individual series can also be increased.

This is particularly useful because the chart contains different **Has Dependents** categories.

Adjusting this spacing makes the individual columns easier to distinguish.

---

# 25. Resize the Chart

The chart can also be resized according to the report layout.

### Steps

1. Select the clustered column chart.
2. Drag its edges/corners.
3. Adjust its width and height.
4. Ensure that it fits properly with the other report visuals.

The lecture notes that the chart can be resized as required.

---

# 26. Final Chart Configuration

The completed chart can be summarized as:

| Property                | Configuration                                           |
| ----------------------- | ------------------------------------------------------- |
| **Visual**              | Clustered Column Chart                                  |
| **Purpose**             | Total loan amount for Middle Age Adults                 |
| **X-axis**              | Has Mortgage                                            |
| **Y-axis**              | Total Loan Middle Age Adults                            |
| **Legend**              | Has Dependents                                          |
| **Measure calculation** | Sum of Loan Amount                                      |
| **Age filter**          | Age Group = Middle Age Adults                           |
| **False series color**  | `#46B1C9`                                               |
| **True series color**   | `#BCC1B`                                                |
| **Title**               | Loan for Middle Age Adults by Has Mortgage / Dependents |
| **Layout**              | Adjust category and series spacing                      |

---

# 27. DAX Logic at a Glance

The calculation is essentially:

```text id="w3cyyv"
                 Loan Default Table
                         │
                         ▼
                 FILTER function
                         │
             Age Group = Middle Age Adults
                         │
                         ▼
                Filtered records
                         │
                         ▼
                    SUMX function
                         │
                         ▼
                   Loan Amount
                         │
                         ▼
               Total Loan Amount
```

The resulting measure is then used in the clustered column chart.

---

# 28. Important Concepts Learned

## A. `SUMX()` with `FILTER()`

This is useful when you need to:

1. Filter a table according to a condition.
2. Perform a row-by-row calculation.
3. Aggregate the resulting values.

The pattern is:

```DAX id="3kq6s2"
SUMX(
    FILTER(
        Table,
        Condition
    ),
    Expression
)
```

In this case:

```text id="9z6y7d"
Table     → Loan Default
Condition → Age Group = Middle Age Adults
Expression → Loan Amount
```

---

## B. Using a Measure in a Visual

The DAX measure isn't just calculated independently; it is placed into the chart's **Y-axis** to provide the numerical values displayed by the columns.

---

## C. Using a Field as a Legend

**Has Dependents** is placed in the **Legend** bucket.

This creates separate series within each mortgage category.

For example, conceptually:

```text
Has Mortgage = False
    ├── Has Dependents = False
    └── Has Dependents = True

Has Mortgage = True
    ├── Has Dependents = False
    └── Has Dependents = True
```

This allows multiple dimensions to be represented in one clustered column chart.

---

# 29. Why a Clustered Column Chart Is Used

A clustered column chart is appropriate here because the goal is to **compare categories side-by-side**.

The chart makes it possible to compare:

**Mortgage Status**

against

**Dependent Status**

while measuring:

**Total Loan Amount**

for:

**Middle Age Adults**

This makes category-to-category comparison easier than using a single-series chart.

---

# 30. Complete Step-by-Step Procedure

### Part A — Create the Measure

1. Expand the Data pane.
2. Right-click **Measures Table 2**.
3. Select **New Measure**.
4. Expand the formula bar.
5. Give the measure a suitable name, such as **Total Loan Middle Age Adults**.
6. Use `SUMX()`.
7. Inside it, use `FILTER()`.
8. Filter the **Loan Default** table.
9. Set **Age Group = Middle Age Adults**.
10. Use **Loan Amount** as the expression to be summed.
11. Press **Enter**.

### Part B — Create the Chart

12. Select the existing line chart.
13. Press **Ctrl+C**.
14. Press **Ctrl+V**.
15. Move the copied visual.
16. Change it to **Clustered Column Chart**.
17. Remove the old fields from the copied chart.
18. Add **Total Loan Middle Age Adults** to the **Y-axis**.
19. Add **Has Mortgage** to the **X-axis**.
20. Add **Has Dependents** to the **Legend**.

### Part C — Format the Chart

21. Open **Format Your Visual**.
22. Go to **Columns**.
23. Under **Series**, select `False`.
24. Set its color to `#46B1C9`.
25. Select `True`.
26. Set its color to `#BCC1B`.
27. Go to **General → Title**.
28. Set the title to **Loan for Middle Age Adults by Has Mortgage / Dependents**.
29. Go back to **Columns**.
30. Select **All** under Series.
31. Adjust the spacing between categories.
32. Adjust the spacing between series.
33. Resize the chart as required.

---

# 31. What Will Be Validated in the Next Session?

The current session focuses on **creating and formatting** the clustered column chart.

The next session, as mentioned at the end of the lecture, will focus on **data validation** for this chart.

The validation will likely follow the same principle used for the previous visuals:

**Power BI visual**
→ **Independent Power BI table calculation**
→ **Original Excel source**
→ **Compare the results**

This ensures that the total loan amounts displayed for Middle Age Adults are accurate.
