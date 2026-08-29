# Power BI — Creating the Second KPI Page Using DAX

This session continues the Power BI project and focuses on creating the **second report page** and the DAX measures required for its KPIs.

The three KPIs on this page are:

1. **Total Profit**
2. **Total Loss**
3. **Average Loss per Day**

The session also covers:

* Creating a calculated column for Profit/Loss
* Using `SUMX()` with `FILTER()`
* Multiplying profit/loss by Unit Price
* Creating the Average Loss per Day measure
* Reusing Card visuals from Page 1
* Adding Product and Order Date filters
* Formatting the Filters pane for both **Default** and **Applied** states
* Finalizing the report built using the **test environment**
* Preparing to move the report from **Test → Production**

---

# 1. Objective of the Second Report Page

The second page of the report is designed to show financial KPIs based on the relationship between:

* **Availability**
* **Demand**
* **Unit Price**

The basic business logic is:

```text
Availability - Demand
```

This difference determines whether the business has a **profit** or **loss** situation.

---

# 2. Understanding the Profit/Loss Logic

Before writing DAX, understand the business rule.

Suppose:

```text
Availability = 50
Demand       = 30
```

Then:

```text
Availability - Demand
= 50 - 30
= +20
```

The result is **positive**.

The instructor considers this a **profit** situation because the available supply was sufficient to fulfill the demand.

The value is then multiplied by the **Unit Price** to determine the monetary profit.

Conceptually:

$$
Profit = (Availability - Demand) \times Unit\ Price
$$

---

## Loss Scenario

Now suppose:

```text
Availability = 30
Demand       = 50
```

Then:

```text
Availability - Demand
= 30 - 50
= -20
```

The result is **negative**.

This represents a **loss** situation because:

```text
Availability < Demand
```

The negative difference is multiplied by the Unit Price to determine the loss amount.

Conceptually:

$$
Loss = (Availability - Demand) \times Unit\ Price
$$

Since the difference is negative, the resulting loss value will also be negative under the transcript's calculation.

---

## Important Rule

The instructor defines the categories as:

| Availability − Demand | Interpretation          |
| --------------------: | ----------------------- |
|              Positive | Profit                  |
|                  Zero | Neither profit nor loss |
|              Negative | Loss                    |

Therefore:

```text
> 0  → Profit
= 0  → No profit / No loss
< 0  → Loss
```

---

# 3. Create the Profit/Loss Calculated Column

The first implementation step is to create a **calculated column** in the Demand/Availability Data table.

### Why a calculated column?

We need to determine the difference between Availability and Demand **for each row**.

The instructor creates a new column called:

> **Loss/Profit**

### Steps

1. Expand the **Data pane**.
2. Locate the:

> **Demand/Availability Data**

table.

3. Right-click the table.
4. Select:

> **New column**

5. Expand the formula bar.
6. Create the following calculated column:

```DAX
Loss/Profit =
'Demand/Availability Data'[Availability]
    - 'Demand/Availability Data'[Demand]
```

7. Press **Enter**.

---

# 4. What the Loss/Profit Column Represents

Suppose the original data looks like this:

| Availability | Demand | Loss/Profit |
| -----------: | -----: | ----------: |
|           50 |     30 |          20 |
|           30 |     50 |         -20 |
|           40 |     40 |           0 |
|           80 |     60 |          20 |

The newly created column tells us immediately which rows represent:

* Profit
* Loss
* Neither

For example:

```text
50 - 30 = +20 → Profit
30 - 50 = -20 → Loss
40 - 40 = 0   → Neither
```

This calculated column becomes the basis for the next measures.

---

# 5. Create the Total Loss Measure

Now the instructor creates a measure to calculate **Total Loss**.

The requirement is:

> Consider only those rows where the Loss/Profit value is negative.

Then calculate the loss amount using:

```text
Loss/Profit × Unit Price
```

---

## DAX Structure

The instructor uses:

* `SUMX()`
* `FILTER()`

The basic structure is:

```DAX
SUMX(
    FILTER(Table, Condition),
    Expression
)
```

`FILTER()` identifies the rows we want.

`SUMX()` evaluates an expression for each of those rows and then adds the results.

---

## Steps

1. Right-click **Measures Table**.
2. Select **New Measure**.
3. Enter:

```DAX
Total Loss =
SUMX(
    FILTER(
        'Demand/Availability Data',
        'Demand/Availability Data'[Loss/Profit] < 0
    ),
    'Demand/Availability Data'[Loss/Profit]
        * 'Demand/Availability Data'[Unit Price]
)
```

4. Press **Enter**.

---

# 6. Breaking Down the Total Loss Formula

Let's understand the formula from inside out.

### Step 1 — FILTER

```DAX
FILTER(
    'Demand/Availability Data',
    'Demand/Availability Data'[Loss/Profit] < 0
)
```

This keeps only rows where:

```text
Loss/Profit < 0
```

For example:

| Loss/Profit | Included? |
| ----------: | --------- |
|          20 | ❌         |
|         -15 | ✅         |
|           0 | ❌         |
|         -30 | ✅         |
|          10 | ❌         |

Only the negative values are considered losses.

---

### Step 2 — Calculate the Loss Amount

For each filtered row:

```DAX
Loss/Profit * Unit Price
```

For example:

```text
Loss/Profit = -20
Unit Price  = $5
```

Then:

```text
-20 × $5 = -$100
```

---

### Step 3 — SUMX

`SUMX()` evaluates this expression for every filtered row and adds the results together.

So conceptually:

```text
Row 1 → -20 × $5 = -100
Row 2 → -10 × $8 = -80
Row 3 → -15 × $4 = -60

Total Loss = -100 - 80 - 60
           = -240
```

The exact values depend on the dataset.

---

# 7. Create the Total Profit Measure

The next KPI is **Total Profit**.

The logic is exactly the opposite.

We consider only rows where:

```text
Loss/Profit > 0
```

because positive values represent profit.

---

## DAX

```DAX
Total Profit =
SUMX(
    FILTER(
        'Demand/Availability Data',
        'Demand/Availability Data'[Loss/Profit] > 0
    ),
    'Demand/Availability Data'[Loss/Profit]
        * 'Demand/Availability Data'[Unit Price]
)
```

Press **Enter**.

---

# 8. Understanding Total Profit

The calculation works as follows.

### Filter

Only positive Loss/Profit values:

```DAX
'Demand/Availability Data'[Loss/Profit] > 0
```

For example:

| Loss/Profit | Included? |
| ----------: | --------- |
|          20 | ✅         |
|         -15 | ❌         |
|           0 | ❌         |
|          30 | ✅         |
|          -5 | ❌         |

Then for every included row:

```text
Loss/Profit × Unit Price
```

is calculated.

Finally, `SUMX()` adds all those values.

---

# 9. Why `SUMX()` Is Used Instead of `SUM()`

This is an important DAX concept from the lecture.

We cannot simply do:

```DAX
SUM([Loss/Profit])
```

because we don't just want to sum the Loss/Profit values.

We need to perform a calculation **for every row**:

```text
Loss/Profit × Unit Price
```

and then sum the results.

That's exactly what `SUMX()` is designed for.

### General syntax

```DAX
SUMX(
    Table,
    Expression
)
```

In this case:

```DAX
SUMX(
    Filtered Table,
    Loss/Profit * Unit Price
)
```

So remember:

> **`SUMX()` = Iterate through rows → calculate an expression → add the results.**

---

# 10. Correction Made to Total Loss and Total Profit

An important correction happens in the lecture.

Initially, the measures were being calculated using only:

```text
SUM(Loss/Profit)
```

But that would give us the **number of units**, not the monetary value.

The instructor realizes that we must also consider **Unit Price**.

Therefore, the expression must be:

```DAX
[Loss/Profit] * [Unit Price]
```

and `SUMX()` must calculate that expression row by row.

So the final logic is:

### Total Loss

```text
Negative Loss/Profit
        ×
Unit Price
        ↓
Loss for each row
        ↓
SUMX
        ↓
Total Loss
```

### Total Profit

```text
Positive Loss/Profit
        ×
Unit Price
        ↓
Profit for each row
        ↓
SUMX
        ↓
Total Profit
```

This correction is important.

---

# 11. Create Average Loss per Day

The third KPI is:

> **Average Loss per Day**

The instructor already created the **Total Number of Days** measure on Page 1.

Therefore, it can be reused.

The logic is:

$$
Average\ Loss\ per\ Day
=
\frac{Total\ Loss}{Total\ Number\ of\ Days}
$$

---

## Steps

1. Right-click **Measures Table**.
2. Click **New Measure**.
3. Enter:

```DAX
Average Loss per Day =
DIVIDE(
    [Total Loss],
    [Total Number of Days]
)
```

4. Press **Enter**.

The lecture shows the result as approximately:

> **$89**

The exact value depends on the dataset and filters applied.

---

# 12. Measures Created on This Page

At this stage, the major measures are:

```text
Total Profit
Total Loss
Average Loss per Day
```

Along with previously created reusable measures:

```text
Total Number of Days
Total Demand
Total Availability
Average Demand per Day
Average Availability per Day
Total Supply Shortage
```

The Measures Table therefore becomes the central location for the report's DAX calculations.

---

# 13. Create KPI Cards on Page 2

The instructor already has formatted Card visuals on **Page 1**.

Rather than recreating the Cards from scratch, the existing Card visual is copied.

This preserves the formatting and saves time.

---

# 14. Copy a Card from Page 1

### Steps

1. Go to **Page 1**.
2. Select an existing Card visual.
3. Press:

```text
Ctrl + C
```

4. Go to **Page 2**.
5. Press:

```text
Ctrl + V
```

The Card is copied to Page 2.

---

# 15. Configure the First Card — Total Profit

The copied Card initially contains:

> Average Demand per Day

because that was the measure used in the original Card.

### Steps

1. Select the copied Card.
2. Expand the **Visualizations** pane if required.
3. Remove:

```text
Average Demand per Day
```

from the field bucket.
4. Select:

```text
Total Profit
```

Now the Card represents:

> **Total Profit**

---

# 16. Create the Second Card — Total Loss

Instead of creating another Card from scratch:

1. Select the Total Profit Card.
2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

4. Move the new Card to the right.
5. Remove:

```text
Total Profit
```

from the field bucket.
6. Select:

```text
Total Loss
```

Now the second KPI represents:

> **Total Loss**

---

# 17. Create the Third Card — Average Loss per Day

Again, duplicate the existing Card.

### Steps

1. Select the Total Loss Card.
2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

4. Move it to the right.
5. Remove:

```text
Total Loss
```

6. Select:

```text
Average Loss per Day
```

The third Card now represents:

> **Average Loss per Day**

The lecture shows a value of approximately:

```text
$89
```

---

# 18. Final KPI Layout for Page 2

The second page therefore contains three KPI Cards:

```text
┌─────────────────────┐
│                     │
│     Total Profit    │
│                     │
└─────────────────────┘

┌─────────────────────┐
│                     │
│      Total Loss     │
│                     │
└─────────────────────┘

┌─────────────────────┐
│                     │
│ Average Loss / Day  │
│                     │
└─────────────────────┘
```

They are positioned side-by-side according to the Canva template.

---

# 19. Add Product Filter to Page 2

Just like Page 1, the user should be able to filter the KPIs based on **Product Name**.

### Steps

1. Expand the **Filters pane**.
2. Locate **Product Name** in the Data pane.
3. Double-click it or drag it.
4. Place it under:

> **Filters on this page**

Now the user can select:

* One product
* Multiple products
* Different combinations of products

The KPI values will automatically update.

---

# 20. Add Order Date Filter to Page 2

The user should also be able to filter by date.

### Steps

1. Find:

> **Order Date**

in the Data pane.

2. Double-click it or drag it.
3. Place it under:

> **Filters on this page**

Now the user can select:

* A single date
* Multiple dates
* A date range, depending on the filter configuration

The KPI values will update based on the selected date context.

---

# 21. Why Do the KPI Values Change?

Because these are **DAX measures**, they respond to the current filter context.

For example, suppose the complete dataset has:

```text
Total Profit = $10,000
Total Loss = -$4,000
Average Loss per Day = -$100
```

If the user selects:

```text
Product = Product A
```

Power BI recalculates the measures using only the data relevant to Product A.

Similarly:

```text
Order Date = January 10
```

causes the measures to be recalculated for that date.

This makes the report interactive.

---

# 22. Format the Filters Pane

The instructor then formats the Filters pane to match the report's dark theme.

### Steps

1. Select the report page.
2. Go to:

> **Format your page**

3. Open:

> **Filters pane**

---

## Background

Change the Filters pane background to:

> **Black**

---

## Input Box

Change the input box color to:

> **Black**

---

## Text

Change the text color to:

> **White**

The result is a dark Filters pane with white text.

---

# 23. Format Filter Cards

Next, the instructor formats the individual Filter cards.

Go to:

> **Filter cards**

There are different states, particularly:

* **Default**
* **Applied**

Both need to be formatted.

---

# 24. Format the Default State

Under Filter cards:

1. Select the **Default** state.
2. Set the **input box color** to:

> Black

3. Set the **text color** to:

> White

4. Set the **background color** to:

> Black

This gives the default filter state the desired dark appearance.

---

# 25. Format the Applied State

The instructor then points out an important detail:

> Formatting only the Default state is not enough.

There is also an **Applied** state.

### Steps

1. Open the state dropdown currently showing **Default**.
2. Select:

> **Applied**

3. Apply the same formatting:

**Text:**

```text
White
```

**Input box:**

```text
Black
```

**Background:**

```text
Black
```

Now both states are consistently formatted.

---

# 26. Important Lesson — Default vs Applied Filter State

This is a useful Power BI formatting point.

Filter cards can visually change depending on whether a filter has been applied.

Therefore:

```text
Default State
      ↓
Formatting

Applied State
      ↓
Formatting
```

Both should be configured if you want a consistent report design.

Otherwise, the filter may look correct before selection but change appearance after the user applies a filter.

---

# 27. Fix the Same Formatting Issue on Page 1

The instructor then returns to **Page 1** to verify the Filters pane formatting.

### Steps

1. Go to **Page 1**.
2. Open **Filter cards**.
3. Check the state formatting.
4. Select **Default**.
5. Confirm/apply:

```text
Text → White
Input Box → Black
Background → Black
```

6. Select **Applied**.
7. Confirm/apply the same settings.

This ensures Page 1 and Page 2 have consistent filter formatting.

---

# 28. Test the Filter

The instructor then tests the filter functionality.

For example, select a product.

The KPI values should change according to the selected product.

Then the filter can be cleared again.

This confirms that:

* Product filtering works.
* The measures respond correctly.
* The Cards update dynamically.

---

# 29. Final Cleanup of the Report

Once the report is completed, the instructor collapses unnecessary panes to get a clean final view.

The following panes are collapsed:

* **Measures Table**
* **Filters pane**
* **Visualizations pane**
* **Data pane**

This provides a cleaner view of the finished report.

---

# 30. Final Report Structure

At this point, the project contains **two report pages**.

## Page 1 — Operational KPIs

The first page contains:

1. **Average Demand per Day**
2. **Average Availability per Day**
3. **Total Supply Shortage**

With filters:

* Product Name
* Order Date

---

## Page 2 — Profit/Loss KPIs

The second page contains:

1. **Total Profit**
2. **Total Loss**
3. **Average Loss per Day**

With filters:

* Product Name
* Order Date

---

# 31. Complete DAX for Page 2

### Calculated Column

```DAX
Loss/Profit =
'Demand/Availability Data'[Availability]
    - 'Demand/Availability Data'[Demand]
```

### Total Loss

```DAX
Total Loss =
SUMX(
    FILTER(
        'Demand/Availability Data',
        'Demand/Availability Data'[Loss/Profit] < 0
    ),
    'Demand/Availability Data'[Loss/Profit]
        * 'Demand/Availability Data'[Unit Price]
)
```

### Total Profit

```DAX
Total Profit =
SUMX(
    FILTER(
        'Demand/Availability Data',
        'Demand/Availability Data'[Loss/Profit] > 0
    ),
    'Demand/Availability Data'[Loss/Profit]
        * 'Demand/Availability Data'[Unit Price]
)
```

### Average Loss per Day

```DAX
Average Loss per Day =
DIVIDE(
    [Total Loss],
    [Total Number of Days]
)
```

---

# 32. DAX Logic — Easy Way to Remember

You can memorize the entire calculation as:

```text
Availability - Demand
          ↓
     Loss/Profit
       ↙       ↘
   Negative    Positive
      ↓           ↓
     Loss       Profit
      ↓           ↓
 × Unit Price × Unit Price
      ↓           ↓
 Total Loss   Total Profit
      ↓
 ÷ Total Number of Days
      ↓
Average Loss per Day
```

---

# 33. Example to Understand the Complete Logic

Consider the following simplified data:

| Availability | Demand | Unit Price |
| -----------: | -----: | ---------: |
|           50 |     30 |        $10 |
|           30 |     50 |        $20 |
|           80 |     60 |         $5 |
|           40 |     50 |        $10 |

First calculate:

```text
Loss/Profit = Availability - Demand
```

| Availability | Demand | Unit Price | Loss/Profit |
| -----------: | -----: | ---------: | ----------: |
|           50 |     30 |        $10 |         +20 |
|           30 |     50 |        $20 |         -20 |
|           80 |     60 |         $5 |         +20 |
|           40 |     50 |        $10 |         -10 |

### Profit

Positive rows:

```text
20 × $10 = $200
20 × $5  = $100
```

Therefore:

```text
Total Profit = $300
```

### Loss

Negative rows:

```text
-20 × $20 = -$400
-10 × $10 = -$100
```

Therefore:

```text
Total Loss = -$500
```

If the dataset contains 10 distinct days:

```text
Average Loss per Day
= -$500 / 10
= -$50
```

This illustrates exactly what the DAX measures are doing.

---

# 34. Important Concepts to Remember

## `FILTER()`

Used to restrict the table to rows satisfying a condition.

```DAX
FILTER(
    Table,
    Condition
)
```

Here:

```DAX
FILTER(
    'Demand/Availability Data',
    [Loss/Profit] < 0
)
```

means:

> Give me only rows where Loss/Profit is negative.

---

## `SUMX()`

Used when we need to perform a calculation for every row and then sum the results.

```DAX
SUMX(
    Table,
    Expression
)
```

Here:

```DAX
SUMX(
    FilteredTable,
    [Loss/Profit] * [Unit Price]
)
```

means:

> For every filtered row, multiply Loss/Profit by Unit Price and then add everything together.

---

## `DIVIDE()`

Used for safe division:

```DAX
DIVIDE(
    [Total Loss],
    [Total Number of Days]
)
```

---

## Calculated Column vs Measure

This session uses both.

### Calculated Column

```DAX
Loss/Profit =
Availability - Demand
```

This calculation is performed at the **row level**.

### Measures

```DAX
Total Profit
Total Loss
Average Loss per Day
```

These are evaluated dynamically according to the current **filter context**.

---

# 35. One Important Distinction in the Lecture's Logic

The lecture describes a **positive** Availability − Demand value as profit and a **negative** value as loss.

However, the exact business interpretation depends on what the dataset's Demand and Availability represent.

For the purposes of this project, follow the instructor's defined business rule:

```text
Availability > Demand → Profit
Availability < Demand → Loss
Availability = Demand → No profit/loss
```

Also, because the transcript's `Total Loss` formula retains the negative sign, **Total Loss may appear as a negative monetary value**. If the desired dashboard convention is to show loss as a positive magnitude, the measure would need an additional adjustment such as taking the absolute value. That is **not** what the instructor does in this session.

---

# 36. Overall Project Progress

The project has now completed the report-building phase using the **Test Environment**.

### Completed

```text
Test Environment
       ↓
Data
       ↓
DAX Measures
       ↓
Page 1
       ↓
Page 2
       ↓
KPI Cards
       ↓
Product Filters
       ↓
Date Filters
       ↓
Filter Formatting
       ↓
Completed Test Report
```

The instructor emphasizes that these two pages represent the expected report.

---

# 37. What Comes Next?

The next major phase is:

# **Test → Production Environment**

The instructor says that from the next session onward, the discussion will shift toward moving the report from the **test environment to the production environment**.

Important topics to be discussed include:

* How to move the report from Test to Production
* What changes when moving environments
* How DAX measures can be affected
* What needs to be kept in mind during deployment
* How to make the transition as smooth as possible

So this session essentially marks the completion of the **report development phase**, before beginning the **deployment/migration phase**.

---

# Quick Revision Sheet

| Item                  | Key Point                                         |
| --------------------- | ------------------------------------------------- |
| **Calculated Column** | `Availability - Demand`                           |
| Positive value        | Profit                                            |
| Negative value        | Loss                                              |
| Zero                  | No profit/no loss                                 |
| **Total Profit**      | Sum of positive `(Loss/Profit × Unit Price)`      |
| **Total Loss**        | Sum of negative `(Loss/Profit × Unit Price)`      |
| **Average Loss/Day**  | Total Loss ÷ Total Number of Days                 |
| `FILTER()`            | Filters rows based on a condition                 |
| `SUMX()`              | Calculates expression row-by-row and sums results |
| `DIVIDE()`            | Performs safe division                            |
| KPI visuals           | Card visuals                                      |
| Page 2 filters        | Product Name + Order Date                         |
| Filter theme          | Black background/input, white text                |
| Filter states         | Format both Default and Applied                   |
| Current project stage | Test environment completed                        |
| Next stage            | Test → Production                                 |

### Most important formulas to memorize

```DAX
Loss/Profit =
Availability - Demand
```

```DAX
Total Profit =
SUMX(
    FILTER(Data, [Loss/Profit] > 0),
    [Loss/Profit] * [Unit Price]
)
```

```DAX
Total Loss =
SUMX(
    FILTER(Data, [Loss/Profit] < 0),
    [Loss/Profit] * [Unit Price]
)
```

```DAX
Average Loss per Day =
DIVIDE(
    [Total Loss],
    [Total Number of Days]
)
```

**Core takeaway:** Page 2 uses a row-level **Availability − Demand** calculation to classify records as profit or loss, then uses `SUMX()` + `FILTER()` + `Unit Price` to convert those differences into monetary KPIs. The resulting measures are displayed through Card visuals and respond dynamically to Product and Date filters.
