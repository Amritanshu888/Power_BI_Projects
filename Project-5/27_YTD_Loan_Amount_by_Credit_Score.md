# Detailed Notes — YTD Loan Amount & Ribbon Chart in Power BI

## 1. Objective of the Session

The main objective of this session is to:

1. Create a **YTD (Year-to-Date) Loan Amount** measure.
2. Use that measure in a **Ribbon Chart**.
3. Represent **YTD Loan Amount by Credit Score Bins and Marital Status**.
4. Format the ribbon chart to match the report's existing design.
5. Understand an important point about how YTD calculations behave when the dataset does not contain the current year.

The lecture specifically introduces the YTD concept and then implements it using DAX. 

---

# 2. What is YTD?

**YTD = Year-to-Date**

YTD means calculating a value starting from the **beginning of the year up to the relevant/latest date**.

### Example from the lecture

Suppose we are analyzing the year **2025**.

If today's date is **16 March 2025**, then:

> YTD Loan Amount = Total loan amount from **1 January 2025 through 16 March 2025**

So instead of looking at the loan amount for only one day or one month, we accumulate the loan amount from the beginning of the year until the relevant date. 

### Conceptually

```text
1 Jan 2025 ───────────────────────► 16 Mar 2025
       |                              |
       └────── YTD calculation ──────┘
```

Therefore:

**YTD = cumulative value from January 1 to the current/relevant date within that year.**

---

# 3. Why the DATESYTD Function is Used

To perform the YTD calculation, the lecture uses the **DATESYTD** DAX function.

The purpose of `DATESYTD` is to return the relevant dates starting from the **beginning of the year up to the current date in the filter context**.

For example, if the relevant date is March 16, 2025:

```text
DATESYTD(Date[Date])
```

returns the dates approximately covering:

```text
1 Jan 2025
2 Jan 2025
3 Jan 2025
...
16 Mar 2025
```

The `SUM` function can then calculate the loan amount across those dates. 

---

# 4. Creating the YTD Loan Amount Measure

The lecture creates the measure in the **Measures Table 3**, because the measure is intended to be used on **Page 3**. 

## Step-by-step

### Step 1: Select the Measures Table

In the **Fields/Data pane**:

1. Locate **Measures Table 3**.
2. Right-click on it.
3. Select **New Measure**.

Power BI opens the DAX formula bar where the measure can be created.

---

## Step 2: Give the measure a name

The measure is named:

```DAX
YTD Loan amount
```

The lecture then moves to the next line and begins writing the DAX expression. 

---

# 5. DAX Formula Used

The basic structure created in the lecture is:

```DAX
YTD Loan amount =
CALCULATE(
    SUM('Loan Default'[Loan Amount]),
    DATESYTD('Loan Default'[Date]),
    ALLEXCEPT(
        'Loan Default',
        'Loan Default'[Credit Score Bins],
        'Loan Default'[Marital Status]
    )
)
```

> The exact table/column naming should follow the names available in your Power BI model. The lecture refers to the loan amount field as the amount/loan amount column and the date field as `Date`.

The measure consists of **three major parts**:

1. `CALCULATE`
2. `SUM`
3. `DATESYTD`
4. `ALLEXCEPT`

The lecture explicitly explains the role of each of these components. 

---

# 6. Understanding SUM()

The first calculation inside `CALCULATE` is:

```DAX
SUM('Loan Default'[Loan Amount])
```

The purpose is straightforward:

**Add together the loan amounts.**

The lecture selects the loan amount field and uses it inside the `SUM` function. 

Conceptually:

```text
Loan 1 = 10,000
Loan 2 = 20,000
Loan 3 = 15,000

Total = 45,000
```

For YTD, however, we don't want the sum over an arbitrary period. We want the sum over the **year-to-date date range**.

That's where `DATESYTD()` comes in.

---

# 7. Understanding DATESYTD()

The next part of the measure is:

```DAX
DATESYTD('Loan Default'[Date])
```

The lecture uses the **Date column** as the input to `DATESYTD`. 

### What does it do?

It determines the dates that belong to the year-to-date period.

For example:

```text
Relevant Date = 15 August 2018

DATESYTD(Date)
        ↓
1 Jan 2018 → 15 Aug 2018
```

The `SUM` then calculates the loan amount over those dates.

Therefore, conceptually:

```text
DATESYTD()
      ↓
Returns YTD dates
      ↓
CALCULATE()
      ↓
SUM loan amount over those dates
      ↓
YTD Loan Amount
```

---

# 8. Why ALLEXCEPT() is Used

This is an important part of the measure.

The requirement is that the YTD Loan Amount should respond to filters coming specifically from:

* **Credit Score Bins**
* **Marital Status**

The lecture states that filters coming from other columns should not affect this measure in the same way. 

Therefore, the lecture uses:

```DAX
ALLEXCEPT()
```

---

# 9. ALLEXCEPT() Structure

The structure is:

```DAX
ALLEXCEPT(
    'Loan Default',
    'Loan Default'[Credit Score Bins],
    'Loan Default'[Marital Status]
)
```

The first argument is the table:

```DAX
'Loan Default'
```

Then we specify the columns whose filter context we want to **retain**:

```DAX
Credit Score Bins
Marital Status
```

This is exactly the logic explained in the lecture. 

### In simple words

`ALLEXCEPT()` essentially says:

> Remove the filters from the Loan Default table **except** the filters coming from Credit Score Bins and Marital Status.

So the measure preserves the grouping/filtering required for the ribbon chart.

---

# 10. Complete Logic of the Measure

The complete calculation can be understood as:

```text
CALCULATE
    │
    ├── SUM(Loan Amount)
    │
    ├── DATESYTD(Date)
    │
    └── ALLEXCEPT(
            Loan Default,
            Credit Score Bins,
            Marital Status
        )
```

### Meaning

**CALCULATE**

Changes the filter context in which the calculation is performed.

**SUM(Loan Amount)**

Calculates total loan amount.

**DATESYTD(Date)**

Restricts the calculation to the year-to-date period.

**ALLEXCEPT(...)**

Keeps the filters for:

* Credit Score Bins
* Marital Status

while removing other filters from the Loan Default table.

The lecture summarizes the same three key responsibilities: `SUM` calculates loan amount, `DATESYTD` returns relevant dates, and `ALLEXCEPT` ensures the desired filters are applied. 

---

# 11. Creating the Ribbon Chart

After creating the measure:

1. Press **Enter** to save the measure.
2. Click on a **blank area of the report canvas**.
3. From the Visualizations pane, select **Ribbon Chart**.
4. Resize the chart according to the available space.

The lecture then uses this chart to represent the loan amount based on credit score bins and marital status. 

---

# 12. Adding Credit Score Bins to the Ribbon Chart

The first field required is **Credit Score Bins**.

### Steps

1. Expand the **Loan Default** table in the Data pane.
2. Search for:

```text
Credit Score Bins
```

3. Drag **Credit Score Bins** into the **X-axis** bucket.

The lecture specifically places Credit Score Bins in the X-axis bucket. 

---

# 13. Adding Marital Status

Next, add **Marital Status**.

### Steps

1. Search for:

```text
Marital Status
```

2. Find the Marital Status column.
3. Drag it into the **Legend** bucket.

This allows the ribbon chart to distinguish the different marital-status categories. 

The chart therefore has:

| Ribbon Chart Field | Field             |
| ------------------ | ----------------- |
| X-axis             | Credit Score Bins |
| Legend             | Marital Status    |
| Y-axis             | YTD Loan Amount   |

---

# 14. Adding the YTD Loan Amount Measure

Now add the measure created earlier.

### Steps

1. Locate:

```text
YTD Loan amount
```

2. Double-click/select it.
3. Drag it into the **Y-axis** bucket.

The ribbon chart is now created using the YTD loan amount measure. 

---

# 15. Final Data Representation

The chart represents:

> **YTD Loan Amount by Credit Score Bins and Marital Status**

Conceptually:

```text
                  Marital Status
                       ↓
Credit Score Bins → Ribbon Chart ← YTD Loan Amount
```

The different marital-status categories are represented as different series/ribbons, while credit score bins are represented along the horizontal axis.

---

# 16. Formatting the Ribbon Chart

After creating the visual, the lecture formats it to improve its appearance.

Select the ribbon chart and choose:

**Format Visual**

The following formatting changes are made.

---

# 17. Turn Off Horizontal Gridlines

### Steps

1. Select the ribbon chart.
2. Open **Format Visual**.
3. Find **Gridlines**.
4. Expand the Gridlines section.
5. Set **Horizontal Gridlines → Off**.

There are no vertical gridlines to change, so those are left as they are. 

---

# 18. Change Series Colors

The lecture changes the colors of the different marital-status series.

Navigate to:

**Format Visual → Columns → Series → Colors**

Then select each category individually.

The lecture uses the following color codes:

### First category

```text
FB5B9F
```

### Second category — Married

```text
46B1C9
```

### Third category — Single

```text
F5C4AF
```

These colors are applied using **More Colors** under the series color settings. 

### Important

The exact categories/order shown in your chart may depend on your dataset and Power BI's series ordering.

---

# 19. Formatting the Column Layout

The lecture then adjusts spacing between the categories and series.

### Steps

Go to:

**Format Visual → Columns → Layout**

From here, you can control:

* Space between categories
* Space between series

The lecture chooses:

```text
Space between series = 5
```

The remaining spacing is adjusted according to the desired appearance. 

---

# 20. Adding a Column Border

A border can also be added to the columns.

The lecture chooses a **white** border.

### Steps

1. Go to the relevant column/border settings.
2. Enable the border if required.
3. Select the border color.
4. Choose white.

This is primarily a visual/design adjustment. 

---

# 21. Formatting the Ribbons

The ribbon itself can also be formatted.

The lecture goes to:

**Format Visual → Ribbons**

Within the ribbon settings, the layout/spacing can be changed.

The lecture chooses to keep the ribbon spacing at:

```text
0
```

It also mentions that ribbon transparency can be changed if required. 

---

# 22. Match Series Color

The lecture also chooses to match the ribbon colors with the series colors.

This helps maintain consistency between:

```text
Series color
      ↓
Column color
      ↓
Ribbon color
```

A ribbon border is also enabled, with **white** being used as the border color. 

---

# 23. Formatting the Y-axis

The lecture does not want the Y-axis title/values displayed in the same way.

### Steps

1. Select the ribbon chart.
2. Go to **Y-axis** under Format Visual.
3. Turn the required Y-axis display/title settings **Off**.

The lecture specifically turns off the Y-axis values/title as part of the visual formatting. 

---

# 24. Formatting the X-axis

The lecture also changes the X-axis title.

### Steps

1. Expand **X-axis**.
2. Set:

```text
Title → Off
```

The category values themselves remain visible.

The lecture then formats the appearance of those category labels, including:

* Font style
* Font color
* Bold formatting
* Font size

The exact size can be adjusted based on the report design. 

---

# 25. Turning Data Labels On

The lecture also enables data labels.

### Steps

1. Open **Data labels**.
2. Set:

```text
Data labels → On
```

3. Expand the Data labels section.
4. Customize:

   * Font style
   * Font color
   * Font size

The lecture chooses **bold** font for the labels and adjusts the size according to the visual appearance. 

---

# 26. Formatting the Chart Title

The title is set to:

> **YTD Loan Amount by Credit Score Bins and Marital Status**

The lecture considers this title appropriate but then formats it. 

### Steps

1. Select the chart.
2. Go to:

**General → Title**

3. Format:

   * Font style
   * Text color
   * Alignment
   * Bold formatting

The lecture chooses to keep the title **center aligned** and **bold**. 

---

# 27. Formatting the Legend

The legend position can also be changed.

### Steps

1. Select the visual.
2. Go to **Visual → Legends**.
3. Change the legend position as required.

Initially, the legend is positioned at:

```text
Top Left
```

The lecture changes it to:

```text
Top Center
```

This is optional and depends on the report layout. 

---

# 28. Adding a Visual Border

The lecture then adds a border around the entire visual.

### Steps

1. Select the ribbon chart.
2. Go to:

**General → Effects → Visual Border**

3. Turn:

```text
Visual Border → On
```

4. Expand the visual border settings.
5. Change the default border color.

The default is black, but the lecture wants the border to match another shape already present in the report. 

---

# 29. Finding the Existing Report Color

Instead of guessing the color, the lecture takes the color from an existing shape at the top of the report.

### Steps

1. Click the existing shape at the top of the report.
2. Check its formatting/style settings.
3. Identify its color code.
4. Copy the color code.

The lecture identifies the color code as:

```text
#959395
```

It then copies that code. 

---

# 30. Applying the Same Border Color to the Ribbon Chart

Now return to the ribbon chart.

### Steps

1. Select the ribbon chart.
2. Go to:

**General → Effects**
3. Turn **Visual Border → On**.
4. Click the border color.
5. Select **More Colors**.
6. Paste the copied color code.
7. Press **Enter**.

This makes the ribbon chart's border consistent with the existing report design. 

---

# 31. Final Cleanup

After completing the formatting, the lecture collapses:

* **Visualizations pane**
* **Data pane**

This provides a cleaner view of the completed report page. 

---

# 32. Very Important Point About YTD and Dataset Dates

The final part of the lecture contains an important concept.

The dataset's latest available year is:

```text
2018
```

Therefore, the YTD calculation is based on the **latest available data in the dataset**, not necessarily today's actual calendar year.

The lecture explicitly states that because **2018 is the latest year available in the dataset**, the YTD calculation will be performed according to that available data. 

### Example

Suppose the dataset contains:

```text
2016
2017
2018
```

and 2018 is the latest year.

Then Power BI's YTD calculation will work within the available 2018 data.

It does **not** mean:

```text
YTD 2026
```

just because today's real-world date is in 2026.

The available date context in the model determines the calculation.

---

# 33. Complete Workflow — Quick Revision

The entire lecture workflow can be remembered as:

```text
START
  ↓
Understand YTD
  ↓
Right-click Measures Table 3
  ↓
New Measure
  ↓
Name: YTD Loan amount
  ↓
CALCULATE()
  ↓
SUM(Loan Amount)
  ↓
DATESYTD(Date)
  ↓
ALLEXCEPT(
    Loan Default,
    Credit Score Bins,
    Marital Status
)
  ↓
Press Enter
  ↓
Create Ribbon Chart
  ↓
Credit Score Bins → X-axis
  ↓
Marital Status → Legend
  ↓
YTD Loan Amount → Y-axis
  ↓
Format Gridlines
  ↓
Format Series Colors
  ↓
Format Columns
  ↓
Format Ribbons
  ↓
Format X/Y axes
  ↓
Enable Data Labels
  ↓
Format Title
  ↓
Format Legend
  ↓
Add Visual Border
  ↓
Match report color
  ↓
Collapse panes
  ↓
DONE
```

---

# 34. DAX Formula — Remember This

The central DAX concept from this lecture is:

```DAX
YTD Loan amount =
CALCULATE(
    SUM('Loan Default'[Loan Amount]),
    DATESYTD('Loan Default'[Date]),
    ALLEXCEPT(
        'Loan Default',
        'Loan Default'[Credit Score Bins],
        'Loan Default'[Marital Status]
    )
)
```

### Formula breakdown

| DAX Function        | Purpose                                                   |
| ------------------- | --------------------------------------------------------- |
| `CALCULATE()`       | Changes/modifies filter context for the calculation       |
| `SUM()`             | Calculates total loan amount                              |
| `DATESYTD()`        | Returns dates from beginning of year to the relevant date |
| `ALLEXCEPT()`       | Removes filters except specified columns                  |
| `Credit Score Bins` | Filter/grouping that is retained                          |
| `Marital Status`    | Filter/grouping that is retained                          |

---

# 35. Key Concepts to Remember for Exams/Interviews

### YTD

**Year-to-Date** — calculation from the beginning of the year up to the relevant/current date.

### DATESYTD

Used to obtain the date range corresponding to the year-to-date period.

### CALCULATE

Used to evaluate an expression under a modified filter context.

### ALLEXCEPT

Removes filters from a table **except** the columns explicitly specified.

### Ribbon Chart

Useful for showing how the **ranking/position of categories changes across another categorical dimension**.

In this lecture:

```text
X-axis  → Credit Score Bins
Legend  → Marital Status
Y-axis  → YTD Loan Amount
```

### Dataset date limitation

YTD calculations are dependent on the **date context/data available in the dataset**. In this lecture, **2018 is the latest available year**, so the YTD calculation is based on that data. 

---

## Final Visual Structure

The finished visual is essentially:

**Title:**
`YTD Loan Amount by Credit Score Bins and Marital Status`

**Visual:**
Ribbon Chart

**Fields:**

```text
X-axis       → Credit Score Bins
Legend       → Marital Status
Y-axis       → YTD Loan Amount
```

The measure calculates the cumulative loan amount for the YTD period while retaining the required **Credit Score Bins** and **Marital Status** filter context. This is the central learning outcome of the session. 
