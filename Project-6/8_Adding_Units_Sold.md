# Power BI – Units Sold in Latest Year and Quarter

## 1. Session Overview

In this session, another **DAX measure** and **Card visual** are added to the **House Market Overview** report.

### Objective

The requirement is to calculate and display:

> **The number of houses/units sold in the latest quarter of the latest year available in the dataset.**

The calculation needs to consider **both**:

* The latest/highest **year**
* The latest/highest **quarter associated with the latest date**

The result will then be displayed using a **Card visual**.

---

# 2. Business Requirement

The report needs to answer:

> **How many houses were sold during the latest quarter of the latest year in the dataset?**

For example, suppose the latest date in the dataset belongs to:

```text
Year    = 2025
Quarter = Q4
```

Then the measure should count the distinct houses sold during:

> **Q4 of 2025**

It should **not** simply count all houses sold in 2025.

Therefore, both conditions must be applied:

```text
Year = Latest Year
AND
Quarter = Latest Quarter
```

---

# 3. Creating the DAX Measure

The first step is to create a new measure.

### Steps

1. Go to the **Data pane**.
2. Locate the **Housing** table.
3. Right-click the Housing table.
4. Select:

> **New Measure**

5. Expand the formula bar.

The instructor names the measure:

> **Units Sold in Latest Year and Quarter**

---

# 4. DAX Functions Used

The calculation uses several DAX functions:

* `CALCULATE()`
* `DISTINCTCOUNT()`
* `YEAR()`
* `QUARTER()`
* `MAX()`

The important concept is that **both year and quarter conditions are applied inside `CALCULATE()`**.

---

# 5. DISTINCTCOUNT of House IDs

The first part of the calculation is:

> Count the distinct House IDs.

The instructor uses:

```text id="lyxw7p"
DISTINCTCOUNT(Housing[House ID])
```

### Why DISTINCTCOUNT?

A house should be counted only once.

If the same `House ID` appears multiple times, using a normal row count could potentially count the same house multiple times.

`DISTINCTCOUNT()` ensures that each unique house is counted once.

---

# 6. Using CALCULATE()

The distinct count is placed inside:

> `CALCULATE()`

Conceptually:

```text id="8a8m9n"
CALCULATE(
    DISTINCTCOUNT(House ID),
    conditions...
)
```

`CALCULATE()` allows us to modify the filter context in which the distinct count is calculated.

---

# 7. First Condition – Latest Year

The first filter condition is:

> The year of the Date column must equal the year of the maximum/latest date.

The logic is:

```text id="1t6f3j"
YEAR(Date) = YEAR(MAX(Date))
```

### Breaking this down

First:

```text id="r7wh6y"
MAX(Date)
```

finds the **latest date** in the dataset.

Then:

```text id="ynm3h6"
YEAR(MAX(Date))
```

extracts the year from that latest date.

Finally, that year is compared against the year of every record.

Therefore:

```text id="7lq4vv"
YEAR(Housing[Date])
=
YEAR(MAX(Housing[Date]))
```

---

# 8. Second Condition – Latest Quarter

The second condition checks the quarter.

The instructor uses:

> `QUARTER()`

The logic is:

```text id="b3jz4h"
QUARTER(Date) = QUARTER(MAX(Date))
```

Again, `MAX(Date)` identifies the latest date.

Then:

```text id="2fnq7x"
QUARTER(MAX(Date))
```

identifies the quarter containing that latest date.

---

# 9. Combining Year and Quarter Conditions

The two conditions are joined using:

> `&&`

which represents logical **AND** in DAX.

Conceptually:

```text id="qf5e8u"
YEAR(Date) = YEAR(MAX(Date))
    &&
QUARTER(Date) = QUARTER(MAX(Date))
```

This means a record must satisfy **both conditions**.

```text id="7d9v6h"
Year = Latest Year
        AND
Quarter = Latest Quarter
```

Only then is its House ID included in the distinct count.

---

# 10. Complete DAX Logic

The measure can be represented as:

```text id="y1r1j7"
Units Sold in Latest Year and Quarter =
CALCULATE(
    DISTINCTCOUNT(Housing[House ID]),
    YEAR(Housing[Date]) = YEAR(MAX(Housing[Date]))
        &&
    QUARTER(Housing[Date]) = QUARTER(MAX(Housing[Date]))
)
```

This captures the logic demonstrated in the lecture.

---

# 11. Understanding the Calculation

Suppose the latest date in the dataset is:

```text
15 December 2025
```

Then:

```text
YEAR(MAX(Date))    → 2025
QUARTER(MAX(Date)) → Q4
```

The measure effectively filters the dataset to:

```text
Year = 2025
AND
Quarter = Q4
```

Then it performs:

```text
DISTINCTCOUNT(House ID)
```

Therefore, the final result is:

> **Number of unique houses sold in Q4 2025**

---

# 12. Why Both Year and Quarter Are Required

It is important not to filter only by quarter.

For example:

```text
Quarter = Q4
```

could include:

* Q4 2022
* Q4 2023
* Q4 2024
* Q4 2025

That would not satisfy the requirement.

Instead, we need:

```text
Year = Latest Year
AND
Quarter = Latest Quarter
```

This restricts the calculation to the **latest quarter of the latest year**.

---

# 13. Applying the Measure

After entering the DAX:

1. Press **Enter**.
2. The measure is created in the Housing table.

The measure can now be used in a visual.

---

# 14. Creating a Card Visual

The instructor wants to display the resulting number as a KPI/card.

### Steps

1. Click on a blank area of the report canvas.
2. Open the **Visualizations** pane.
3. Select the **Card** visual.
4. Resize the card.
5. Position it appropriately on the report page.

---

# 15. Adding the Measure to the Card

With the card selected:

1. Locate:

> `Units Sold in Latest Year and Quarter`

2. Add it to the card's field/value area.

The card now displays the number of units/houses sold during the latest year and quarter.

---

# 16. Formatting the Card

The instructor then formats the card so that it matches the rest of the report.

One of the formatting shortcuts used is:

> **Format Painter**

---

# 17. Using Format Painter

The instructor copies formatting from an existing visual.

### Steps

1. Select an existing visual, such as the bar chart.
2. Click:

> **Format Painter**

3. Click the new Card visual.

This transfers the formatting from the existing visual to the card.

### Benefit

It maintains a consistent visual theme across the report without manually reproducing every formatting setting.

---

# 18. Formatting the Card Callout Value

The main number displayed by the card is called the:

> **Callout Value**

### Steps

1. Select the Card visual.
2. Open:

> **Format Visual**

3. Locate:

> **Callout Value**

4. Adjust the font formatting.

The instructor changes the font style and adjusts the size.

The size is set to approximately:

> **25**

---

# 19. Formatting the Category Label

The category label is also formatted.

The instructor:

* Changes its font style.
* Reduces the font size.
* Makes the text bold.
* Uses a gray color.

The category label size is reduced to approximately:

> **10**

---

# 20. Renaming the Card Label

The instructor wants a more concise and user-friendly label.

Instead of displaying the long measure name:

> Units Sold in Latest Year and Quarter

the visual is given a shorter label:

> **Units Sold (Latest Year and Quarter)**

The instructor initially considers changing the field label directly, then uses the visual's formatting/title settings.

---

# 21. Turning Off the Category Label

The category label can be hidden because a custom visual title will be used instead.

### Steps

1. Select the Card.
2. Open **Format Visual**.
3. Locate:

> **Category Label**

4. Change it to:

> **Off**

This removes the automatically generated category label.

---

# 22. Adding a Custom Card Title

The instructor then uses the visual title.

### Steps

1. Select the Card visual.
2. Go to:

> **General**

3. Open:

> **Title**

4. Turn the title on.
5. Enter:

> **Units Sold (Latest Year and Quarter)**

This provides a cleaner and more controlled label for the KPI.

---

# 23. Formatting the Card Title

The title can then be resized and formatted to fit the card.

The instructor reduces the size slightly so that it fits appropriately within the visual.

---

# 24. Final Card Structure

The final card essentially communicates:

```text id="f75k1q"
┌─────────────────────────────┐
│ Units Sold (Latest Year     │
│        and Quarter)         │
│                             │
│            123              │
│                             │
└─────────────────────────────┘
```

The actual number will depend on the dataset.

---

# 25. DAX Functions – Detailed Understanding

## `DISTINCTCOUNT()`

Counts unique values in a column.

Here:

```text id="8y5s9h"
DISTINCTCOUNT(House ID)
```

means:

> Count the number of unique houses.

---

## `CALCULATE()`

Changes the filter context before evaluating an expression.

Here it means:

> Count unique House IDs after restricting the data to the latest year and latest quarter.

---

## `MAX()`

Returns the maximum/latest date.

```text id="j2v8v6"
MAX(Date)
```

---

## `YEAR()`

Extracts the year from a date.

```text id="w2xgq0"
YEAR(MAX(Date))
```

---

## `QUARTER()`

Extracts the quarter number from a date.

For example:

```text
January–March     → Q1
April–June        → Q2
July–September    → Q3
October–December  → Q4
```

Therefore:

```text id="31pr5f"
QUARTER(MAX(Date))
```

returns the quarter associated with the latest date.

---

## `&&`

Represents logical **AND**.

For example:

```text id="w2d6a8"
Condition 1 && Condition 2
```

means both conditions must be true.

---

# 26. Important Difference From Previous Measures

This measure counts **units/houses**, rather than calculating a price or growth percentage.

### Previous examples

**Year-on-Year Sales Growth**

```text
(Current Sales - Previous Sales)
/
Previous Sales
```

**Median Sales Price Change**

```text
(Current Median Price - Previous Median Price)
/
Previous Median Price
```

### Current measure

```text
DISTINCTCOUNT(House ID)
```

with filters for:

```text
Latest Year
+
Latest Quarter
```

So this KPI answers a completely different business question:

> **How many unique properties were sold during the latest quarter of the latest year?**

---

# 27. Complete Workflow

```text id="f6qkz0"
Housing Table
      ↓
Right-click Housing
      ↓
New Measure
      ↓
Name:
Units Sold in Latest Year and Quarter
      ↓
DISTINCTCOUNT(House ID)
      ↓
Filter:
YEAR(Date) = YEAR(MAX(Date))
      ↓
AND
      ↓
QUARTER(Date) = QUARTER(MAX(Date))
      ↓
Press Enter
      ↓
Measure Created
      ↓
Insert Card Visual
      ↓
Add Measure to Card
      ↓
Format Painter
      ↓
Format Callout Value
      ↓
Format Category Label
      ↓
Turn Category Label Off
      ↓
General → Title → On
      ↓
Title:
Units Sold (Latest Year and Quarter)
```

---

# 28. Quick Revision Table

| Requirement        | Configuration                         |
| ------------------ | ------------------------------------- |
| KPI                | Units Sold in Latest Year and Quarter |
| Measure type       | DAX Measure                           |
| Count function     | `DISTINCTCOUNT()`                     |
| ID column          | House ID                              |
| Latest year        | `YEAR(MAX(Date))`                     |
| Latest quarter     | `QUARTER(MAX(Date))`                  |
| Year condition     | `YEAR(Date) = YEAR(MAX(Date))`        |
| Quarter condition  | `QUARTER(Date) = QUARTER(MAX(Date))`  |
| Logical operator   | `&&`                                  |
| Visual             | Card                                  |
| Callout value size | Approximately 25                      |
| Category label     | Turned Off                            |
| Card title         | Units Sold (Latest Year and Quarter)  |
| Title formatting   | Adjusted to fit card                  |

---

# 29. Key Takeaways

1. **`DISTINCTCOUNT(House ID)`** is used to count unique properties.
2. `CALCULATE()` applies the required year and quarter filters.
3. `MAX(Date)` identifies the latest date in the dataset.
4. `YEAR()` extracts the latest year.
5. `QUARTER()` extracts the latest quarter.
6. `&&` ensures that **both** year and quarter conditions must be satisfied.
7. The result is displayed using a **Card visual**.
8. **Format Painter** can be used to maintain consistency with existing visuals.
9. The automatically generated category label can be switched off.
10. A custom title can be added through **General → Title**.
11. The final KPI shows the **number of unique houses sold in the latest quarter of the latest year**.
12. This is another KPI being added to the **House Market Overview** report, with one more Card visual still remaining to be added in the next session.
