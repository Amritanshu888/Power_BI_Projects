# Power BI — Creating the Average Depth Percentage Card

## 1. Objective of the Session

In this session, the next recommended visual from the PDF is created.

The visual represents:

> **Average Depth Percentage**

The PDF recommends:

* Creating a DAX **AVERAGE** measure using the `depth` column from the Diamonds table.
* Representing the resulting value using a **Card visual**.

Since a Card visual had already been created and formatted in an earlier session, the instructor reuses that existing card rather than formatting a new one from scratch.

---

# 2. Refer to the PDF Recommendations

The instructor first goes back to the PDF generated using **Perplexity**.

The PDF contains recommendations for different KPIs and charts.

The next recommended KPI is:

### Average Depth Percentage

The PDF recommends using the DAX:

```text
AVERAGE
```

on the `depth` column from the **diamonds** table.

The resulting value can then be displayed using a:

> **Card visual**

---

# 3. Create the Average Depth Measure

## Step 1 — Copy the DAX Expression

From the PDF, copy the recommended DAX expression.

Conceptually, the calculation is:

```DAX
AVERAGE(diamonds[depth])
```

This calculates the average value of the `depth` column across the diamonds data.

---

## Step 2 — Go to Power BI Desktop

Return to Power BI Desktop.

Expand the:

**Data pane**

This allows access to the tables and fields in the report.

---

## Step 3 — Right-Click the Measures Table

Locate the:

**Measures table**

Right-click it.

Select:

**New measure**

A DAX formula bar appears.

---

# 4. Enter the DAX Formula

The instructor initially attempts to paste the copied expression, but it was not copied successfully.

Therefore, the expression is typed manually.

The instructor starts by writing:

```DAX
AVERAGE
```

The complete measure should conceptually be:

```DAX
Average Depth Percentage = AVERAGE(diamonds[depth])
```

where:

* `Average Depth Percentage` = name of the measure
* `AVERAGE()` = DAX aggregation function
* `diamonds[depth]` = column whose average is being calculated

---

# 5. Name the Measure

The instructor goes back to the PDF to copy the recommended name.

The measure is named:

### `Average Depth Percentage`

The name is entered in the measure definition.

Then press:

**Enter**

The measure is now created successfully.

---

# 6. Understanding the DAX Calculation

The purpose of this measure is to calculate the **arithmetic average of all depth values** in the Diamonds table.

Conceptually:

**Average Depth = Sum of all depth values ÷ Number of depth values**

For example, if the depth values were:

```text
60
62
61
59
```

then:

```text
Average = (60 + 62 + 61 + 59) / 4
        = 60.5
```

In Power BI, the DAX `AVERAGE()` function performs this calculation automatically.

genui{"learning_viz":{"type_id":"ARITHMETIC_MEAN","initial_values":{"observation1":60,"observation2":62,"observation3":61},"locale_override":"en-IN"}}

> **Note:** Although the measure is named *Average Depth Percentage*, the DAX itself simply averages the `depth` column. The naming comes from the PDF recommendation.

---

# 7. Create the Card Visual

The PDF recommends representing this KPI using a **Card visual**.

Instead of creating a completely new card and formatting it again, the instructor reuses the previously created Card visual.

## Step 1 — Select the Existing Card

Click the previously created Card visual.

## Step 2 — Copy the Card

Use:

```text
Ctrl + C
```

## Step 3 — Paste the Card

Use:

```text
Ctrl + V
```

This creates a duplicate of the existing Card visual.

This is useful because the original card already has the desired formatting.

---

# 8. Replace the Existing Measure

The copied Card visual will initially contain the measure that was used by the original card.

The instructor needs to replace that measure with:

### `Average Depth Percentage`

## Step 1

Select the newly copied Card visual.

## Step 2

Go to the card's **Fields/Data bucket**.

The existing measure is currently present there.

The instructor removes the existing:

> Average / previous measure

from the fields bucket.

---

## Step 3 — Add the New Measure

Find:

**Average Depth Percentage**

in the Data/Fields pane.

Select it/add it to the Card visual.

The Card now displays the calculated:

> **Average Depth Percentage**

---

# 9. Why No Additional Formatting Is Required

Normally, after creating a new visual, we may need to configure:

* Font
* Text size
* Background
* Border
* Shadow
* Alignment
* Category label
* Callout value
* Title
* Colors

However, that is **not necessary here**.

Why?

Because the new Card was created by:

> **Copying the previously formatted Card visual**

Therefore, the new Card automatically inherits the formatting of the original Card.

This saves time and also ensures **visual consistency** across the report.

---

# 10. Complete Workflow

The entire process can be remembered as:

```text
Open PDF
   ↓
Find "Average Depth Percentage"
   ↓
Check recommended DAX
   ↓
AVERAGE(diamonds[depth])
   ↓
Power BI Desktop
   ↓
Expand Data pane
   ↓
Right-click Measures table
   ↓
New Measure
   ↓
Enter AVERAGE calculation
   ↓
Name → Average Depth Percentage
   ↓
Press Enter
   ↓
Select previously formatted Card
   ↓
Ctrl + C
   ↓
Ctrl + V
   ↓
New Card created
   ↓
Remove existing measure
   ↓
Add Average Depth Percentage
   ↓
Card displays average depth
   ↓
No additional formatting required
```

---

# 11. Important Power BI Concepts

## A. `AVERAGE()` DAX Function

The `AVERAGE()` function calculates the arithmetic mean of the numbers in a column.

Syntax:

```DAX
AVERAGE(<column>)
```

Example:

```DAX
AVERAGE(diamonds[depth])
```

It is an **aggregation function**.

---

## B. Measure

The calculation is created as a **measure**, rather than simply using the raw `depth` column.

This allows Power BI to dynamically calculate the average according to the current filter context.

For example, if the report is filtered by:

* Diamond color
* Cut
* Clarity
* Price range

the measure can recalculate the average based on the filtered data.

---

## C. Card Visual

A **Card** is particularly useful for displaying a single important KPI or summarized number.

Examples include:

```text
Total Diamonds
Average Price
Average Depth
Average Carat
Maximum Price
Minimum Price
```

In this case, the Card is used to display:

**Average Depth Percentage**

---

# 12. Reusing Existing Visuals

One of the practical Power BI techniques demonstrated in this lecture is:

> **Duplicate an already formatted visual instead of creating and formatting a new one from scratch.**

The process is:

```text
Select existing visual
       ↓
Ctrl + C
       ↓
Ctrl + V
       ↓
Replace the field/measure
       ↓
Keep the existing formatting
```

### Advantages

This approach:

* Saves time.
* Avoids repetitive formatting.
* Maintains a consistent dashboard design.
* Reduces the possibility of formatting differences between similar KPI cards.

---

# 13. Key Takeaways

### KPI being created

**Average Depth Percentage**

### DAX concept

```DAX
AVERAGE(diamonds[depth])
```

### Visual recommended

**Card**

### Efficient approach

Instead of creating a new Card from scratch:

**Duplicate the existing formatted Card → Replace its measure.**

### Formatting

**No additional formatting is required** because the copied Card inherits the formatting of the previously created Card.

---

## Final Revision Summary

The lecture demonstrates a very simple but useful Power BI workflow:

> **Use the PDF's recommendation → create the required DAX measure → duplicate an existing formatted visual → replace its field with the new measure → reuse the existing formatting.**

This approach is especially useful when building dashboards containing **multiple KPI cards**, because all the cards can maintain the same visual design while displaying different measures.
