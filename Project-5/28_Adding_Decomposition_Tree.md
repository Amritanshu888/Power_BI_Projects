# Power BI — Decomposition Tree for Loan Amount Analysis

## 1. Objective of the Session

In this session, a **Decomposition Tree** visual is added to the **third report page**.

### Purpose

The decomposition tree is used to represent the **breakup of Loan Amount** based on:

1. **Income Bracket**
2. **Employment Type**

The problem is that the dataset does not initially contain an **Income Bracket** column, so the first step is to create this column using DAX.

---

# 2. Creating the Income Bracket Column

Since the **Income Bracket** field is not available in the dataset, create a **calculated column**.

### Steps

1. Open the **Data pane**.
2. Collapse the **Measures** table if required.
3. Locate the **Loan Default** table.
4. **Right-click → New column**.
5. Wait for the formula bar to appear.
6. Expand the formula bar for easier editing.
7. Name the new column:

```text
Income Bracket
```

---

## 3. Using the SWITCH Function

The lecture uses the **SWITCH** function instead of nested `IF` statements.

The important pattern is:

```DAX
SWITCH(
    TRUE(),
    condition1, result1,
    condition2, result2,
    condition3, result3
)
```

Using `SWITCH(TRUE())` allows us to evaluate multiple conditions sequentially.

### Income categories

The following three categories are created:

| Income condition              | Income Bracket |
| ----------------------------- | -------------- |
| Income < 30,000               | Low Income     |
| Income >= 30,000 and < 60,000 | Medium Income  |
| Income >= 60,000              | High Income    |

### DAX

```DAX
Income Bracket =
SWITCH(
    TRUE(),
    'Loan Default'[Income] < 30000, "Low Income",
    'Loan Default'[Income] >= 30000 &&
    'Loan Default'[Income] < 60000, "Medium Income",
    'Loan Default'[Income] >= 60000, "High Income"
)
```

### Important logic

#### Condition 1 — Low Income

```DAX
'Loan Default'[Income] < 30000
```

If income is less than **30,000**, assign:

```text
Low Income
```

#### Condition 2 — Medium Income

```DAX
'Loan Default'[Income] >= 30000 &&
'Loan Default'[Income] < 60000
```

If income is between **30,000 and 60,000**, assign:

```text
Medium Income
```

The lower boundary is inclusive, while 60,000 itself is excluded from this category.

#### Condition 3 — High Income

```DAX
'Loan Default'[Income] >= 60000
```

If income is **60,000 or greater**, assign:

```text
High Income
```

### Alternative

The instructor mentions that the same logic could also be implemented using **nested IF statements**, but `SWITCH(TRUE())` is used in this example.

---

# 4. Verifying the Income Bracket Column

After writing the formula:

1. Press **Enter**.
2. Collapse the formula bar.
3. Go to **Table/Data view**.
4. Check the newly created **Income Bracket** column.
5. Click the column's dropdown.

The available categories should be:

* **High Income**
* **Low Income**
* **Medium Income**

This confirms that the calculated column has been created successfully.

---

# 5. Creating the Decomposition Tree

Now create the visual on the **third report page**.

### Steps

1. Go to **Report View**.
2. Navigate to the **third report page**.
3. Click on a **blank area of the canvas**.
4. Expand the **Visualizations** pane if necessary.
5. The **Filters** pane is not required for this task.
6. If necessary, use:

**View → Filters**

to manage the Filters pane.
7. Select the **Decomposition Tree** visual.

A blank decomposition tree will be created.

---

# 6. Configure the Decomposition Tree

The decomposition tree has two important areas:

* **Analyze**
* **Explain by**

The objective is:

> Analyze the Loan Amount and explain it using Income Bracket and Employment Type.

---

## 6.1 Analyze — Loan Amount

In the **Analyze** field:

1. Locate **Loan Amount**.
2. Drag **Loan Amount** into the **Analyze** field.

The decomposition tree will calculate the **sum of Loan Amount** for analysis.

Conceptually:

```text
Analyze
└── Sum of Loan Amount
```

---

# 7. Adding Income Bracket to Explain By

The first explanatory field should be **Income Bracket**.

### Steps

1. Locate the newly created **Income Bracket** column.
2. Drag it into the **Explain by** field.

Now the tree can break down the total loan amount according to income category.

Conceptually:

```text
Loan Amount
   │
   └── Income Bracket
       ├── High Income
       ├── Medium Income
       └── Low Income
```

---

# 8. Adding Employment Type

Next, add **Employment Type**.

### Steps

1. Locate the existing **Employment Type** column.
2. Drag it into the **Explain by** field.

The decomposition tree can now analyze Loan Amount by:

```text
Loan Amount
   ↓
Income Bracket
   ↓
Employment Type
```

---

# 9. Exploring the Decomposition Tree

The main advantage of the decomposition tree is that you can interactively drill into different categories.

For example:

1. Click the **+** icon next to **Income Bracket**.
2. Select **High Income**.
3. The tree expands and displays the corresponding breakdown.
4. You can then select **Employment Type** to further break down the High Income category.

Similarly, you can select:

* **Medium Income**
* **Low Income**

and then investigate their respective employment types.

### Example analytical flow

```text
Total Loan Amount
        ↓
   High Income
        ↓
 Employment Type
    ├── Salaried
    ├── Self-employed
    └── ...
```

This allows you to understand **which income groups and employment types contribute to the loan amount**.

---

# 10. Locking a Level

The instructor also demonstrates that levels of the decomposition tree can be **locked**.

### Steps

1. Select the relevant level/category.
2. Open its options.
3. Select **Lock level**.

Locking a level prevents that particular level from being changed while interacting with the decomposition tree.

---

# 11. Formatting the Decomposition Tree

After creating the visual, the lecture demonstrates several formatting options.

### Steps to access formatting

1. Select the **Decomposition Tree**.
2. Open **Format visual**.

Several formatting sections are available.

---

# 12. Formatting the Visual Border

Navigate to:

**Format visual → General → Effects**

### Visual border

1. Enable/set the **Visual border**.
2. Set the border width to:

```text
1
```

3. Change the border color to the specified **magenta** color.

This adds a visible border around the decomposition tree.

---

# 13. Formatting Connectors

Under the formatting options, open:

**Trees → Connectors**

The connector formatting contains options for:

* **Selected**
* **Unselected**

These control the lines connecting the different levels of the decomposition tree.

---

## Selected Connector

1. Select the **Selected** connector option.
2. Click **More colors**.
3. Enter the color code:

```text
#666666
```

---

## Unselected Connector

1. Select the **Unselected** connector option.
2. Click **More colors**.
3. Enter:

```text
#CCCCCC
```

So the connector colors are:

| Connector  | Color     |
| ---------- | --------- |
| Selected   | `#666666` |
| Unselected | `#CCCCCC` |

---

# 14. Formatting the Bars

Collapse the **Trees** section.

Then expand:

**Bars**

The bar formatting provides three types of bars:

1. **Positive**
2. **Negative**
3. **Bar Background**

---

## 14.1 Positive Bars

For positive bars:

1. Select **Positive**.
2. Click **More colors**.
3. Use RGB values:

```text
R = 199
G = 184
B = 231
```

Therefore:

```text
RGB(199, 184, 231)
```

This is the color applied to positive bars.

---

## 14.2 Negative Bars

For negative bars:

1. Select **Negative**.
2. Click **More colors**.
3. Use:

```text
R = 71
G = 177
B = 201
```

Therefore:

```text
RGB(71, 177, 201)
```

The lecture notes that there are **currently no negative values** being represented in the tree, so this color may not actually be visible at present.

However, the formatting is configured so that if negative values appear later, they will use this color.

---

## 14.3 Bar Background

For the bar background:

1. Select **Bar Background**.
2. Click **More colors**.
3. Use:

```text
R = 230
G = 230
B = 230
```

Therefore:

```text
RGB(230, 230, 230)
```

---

# 15. Formatting Category Labels

Collapse the **Bars** section.

Then expand:

**Category labels**

Here you can modify the appearance of the category labels.

### Changes made in the lecture

* Change the **font**
* Change the **font color**
* Make the text **Bold**

The font color is set to the **white 60% darker** option shown in the Power BI color palette.

---

# 16. Formatting Values

Collapse **Category labels**.

Expand:

**Values**

### Font formatting

For the values:

1. Change the font style as required.
2. Set the font to **Bold**.
3. Change the font color to the same **white 60% darker** color used for the category labels.

---

## Display Units

Within the Values formatting:

1. Open **Display units**.
2. Select:

```text
Billions
```

This changes the way large loan amount values are displayed.

### Decimal places

The lecture also demonstrates changing decimal places.

Set the number of decimal places to:

```text
2
```

So values are displayed using **billions with two decimal places**.

---

# 17. Formatting Headers

Finally, expand:

**Headers**

The headers can also be formatted.

### Changes made

* Change the font style.
* Make the headers **Bold**.
* Reduce the font size slightly.
* Change the font color to **white 60% darker**.

---

# 18. Final Decomposition Tree Structure

After configuration, the decomposition tree conceptually represents:

```text
                 Sum of Loan Amount
                         │
                 ┌───────┴───────┐
                 │               │
            Income Bracket       ...
                 │
        ┌────────┼────────┐
        │        │        │
   High Income  Medium   Low Income
        │       Income       │
        │        │           │
   Employment Type      Employment Type
```

The exact branches shown depend on the selections made while interacting with the visual.

---

# 19. Key Concepts to Remember

### Decomposition Tree

A **Decomposition Tree** is useful when you want to analyze a measure by progressively breaking it down using different categorical dimensions.

In this example:

**Measure being analyzed:**

```text
Sum of Loan Amount
```

**Breakdown dimensions:**

```text
Income Bracket
Employment Type
```

---

### Income Bracket Logic

|          Income | Category      |
| --------------: | ------------- |
|      `< 30,000` | Low Income    |
| `30,000–59,999` | Medium Income |
|     `>= 60,000` | High Income   |

---

### DAX Function Used

The lecture specifically demonstrates:

```DAX
SWITCH(TRUE(), ...)
```

instead of nested `IF`.

This is particularly useful when you have **multiple mutually exclusive conditions**.

---

# 20. Complete Workflow — Quick Revision

```text
Loan Default Table
        ↓
Right-click → New Column
        ↓
Create Income Bracket
        ↓
SWITCH(TRUE())
        ↓
< 30,000 → Low Income
30,000–59,999 → Medium Income
≥ 60,000 → High Income
        ↓
Verify column in Data/Table View
        ↓
Go to Report View → Page 3
        ↓
Insert Decomposition Tree
        ↓
Analyze → Loan Amount
        ↓
Explain by → Income Bracket
        ↓
Explain by → Employment Type
        ↓
Expand categories using "+"
        ↓
Optionally lock levels
        ↓
Format Visual
        ↓
General → Effects → Border
        ↓
Trees → Connectors
        ↓
Bars → Positive / Negative / Background
        ↓
Category Labels
        ↓
Values → Billions → 2 decimals
        ↓
Headers
```

## Important takeaway

The overall purpose of this visual is to make the **Loan Amount decomposition interactive**. Instead of looking at one aggregate loan amount, you can progressively break it down by **income bracket** and then **employment type**, allowing you to identify how different borrower segments contribute to the overall loan amount.
