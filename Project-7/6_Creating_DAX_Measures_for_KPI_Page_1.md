# Power BI — Creating KPI Measures Using DAX

This session focuses on creating **three KPI measures using DAX**, organizing measures in a dedicated measure table, displaying the KPIs using Card visuals, and allowing users to dynamically filter the KPI values by **Product Name** and **Date**.

---

## 1. KPIs Created in This Session

The three main KPIs are:

1. **Average Demand per Day**
2. **Average Availability per Day**
3. **Total Supply Shortage**

The basic logic is:

$$
\text{Average Demand per Day} =
\frac{\text{Total Demand}}{\text{Total Number of Days}}
$$

$$
\text{Average Availability per Day} =
\frac{\text{Total Availability}}{\text{Total Number of Days}}
$$

$$
\text{Total Supply Shortage} =
\text{Total Demand} - \text{Total Availability}
$$

---

# 2. Remove the Filters Pane Initially

The instructor first removes the Filters pane because it is not required while creating the measures.

### Steps

1. Go to the **View** tab.
2. Click **Filters**.
3. The Filters pane disappears.

This gives more working space while building the report.

---

# 3. Create a Separate Measures Table

A recommended Power BI practice is to keep measures in a **separate dedicated table** instead of mixing them with the actual data tables.

Here, the table is named:

> **Measures Table**

### Steps

1. Go to the **Home** tab.
2. Click **Enter Data**.
3. A small table creation window appears.
4. Name the table:

```text
Measures Table
```

5. Click **Load**.

Power BI creates the new table.

### Why create a separate Measures Table?

It keeps the model organized.

Instead of having measures scattered across tables such as:

* Demand/Availability Data
* Customer
* Product
* Date

all the measures can be stored in one place:

```text
Measures Table
    ├── Total Number of Days
    ├── Total Demand
    ├── Total Availability
    ├── Average Demand per Day
    ├── Average Availability per Day
    └── Total Supply Shortage
```

---

# 4. Create the Total Number of Days Measure

The first measure calculates how many **distinct dates** are present in the dataset.

### Steps

1. Right-click **Measures Table**.
2. Select **New Measure**.
3. Expand the formula bar if necessary.
4. Enter:

```DAX
Total Number of Days =
DISTINCTCOUNT('Demand/Availability Data'[Order Date])
```

> The exact table/column name should match the model. The transcript refers to the table as the **Demand/Availability Data** table and the date column as **Order Date**.

5. Press **Enter**.

### What does this measure do?

`DISTINCTCOUNT()` counts unique values.

For example, if the data contains:

| Order Date |
| ---------- |
| 01-Jan     |
| 01-Jan     |
| 02-Jan     |
| 03-Jan     |
| 03-Jan     |

There are five rows, but only **three distinct dates**.

Therefore:

```text
Total Number of Days = 3
```

This measure is important because the average KPIs are calculated based on the number of days for which data is available.

---

# 5. Create the Total Demand Measure

Next, create a measure to calculate the total demand.

### Steps

1. Right-click **Measures Table**.
2. Select **New Measure**.
3. Enter:

```DAX
Total Demand =
SUM('Demand/Availability Data'[Demand])
```

4. Press **Enter**.

This adds all the values in the **Demand** column.

For example:

| Demand |
| -----: |
|      5 |
|      3 |
|      7 |
|      4 |

Then:

```text
Total Demand = 5 + 3 + 7 + 4
             = 19
```

---

# 6. Create the Total Availability Measure

Similarly, create a measure for total availability.

### Steps

1. Right-click **Measures Table**.
2. Click **New Measure**.
3. Enter:

```DAX
Total Availability =
SUM('Demand/Availability Data'[Availability])
```

4. Press **Enter**.

This calculates the total available quantity.

For example:

| Availability |
| -----------: |
|            4 |
|            2 |
|            6 |
|            3 |

Then:

```text
Total Availability = 15
```

---

# 7. Remove the Unnecessary Column from Measures Table

When the Measures Table was created using **Enter Data**, Power BI created a column such as:

> `Column 1`

This column is not required because the table is being used only for storing measures.

### Steps

1. Find **Column 1** under the Measures Table.
2. Click the **three dots (...)** next to it.
3. Select **Delete from model**.

Now the Measures Table effectively acts as a container for the measures.

---

# 8. Create Average Demand per Day

Now we create the first actual KPI.

The logic is:

$$
\text{Average Demand per Day}
=
\frac{\text{Total Demand}}
{\text{Total Number of Days}}
$$

### DAX

```DAX
Average Demand per Day =
DIVIDE(
    [Total Demand],
    [Total Number of Days]
)
```

### Steps

1. Right-click **Measures Table**.
2. Select **New Measure**.
3. Enter the above DAX.
4. Press **Enter**.

### Why use `DIVIDE()`?

Instead of simply writing:

```DAX
[Total Demand] / [Total Number of Days]
```

the `DIVIDE()` function is preferred because it handles division-by-zero situations more safely.

---

# 9. Create Average Availability per Day

The second KPI is **Average Availability per Day**.

The logic is:

$$
\text{Average Availability per Day}
=
\frac{\text{Total Availability}}
{\text{Total Number of Days}}
$$

### DAX

```DAX
Average Availability per Day =
DIVIDE(
    [Total Availability],
    [Total Number of Days]
)
```

### Steps

1. Right-click **Measures Table**.
2. Click **New Measure**.
3. Enter the DAX.
4. Press **Enter**.

---

# 10. Create Total Supply Shortage

The final KPI is **Total Supply Shortage**.

A supply shortage occurs when:

> **Demand is greater than Availability.**

The transcript calculates the overall shortage using:

$$
\text{Supply Shortage}
=
\text{Total Demand}
-
\text{Total Availability}
$$

### DAX

```DAX
Total Supply Shortage =
[Total Demand] - [Total Availability]
```

### Steps

1. Right-click **Measures Table**.
2. Select **New Measure**.
3. Enter the DAX.
4. Press **Enter**.

For example:

```text
Total Demand = 10,000
Total Availability = 9,421
```

Then:

```text
Total Supply Shortage
= 10,000 - 9,421
= 579
```

Therefore, the KPI displays:

> **579**

### Important conceptual point

The transcript's formula measures the **net shortage** as total demand minus total availability.

It does not separately calculate shortage row-by-row using something like:

```DAX
SUMX(
    Data,
    MAX(Data[Demand] - Data[Availability], 0)
)
```

So these are conceptually different calculations. For this lecture, follow the instructor's approach:

```DAX
[Total Demand] - [Total Availability]
```

---

# 11. Measures Created So Far

At this point, the Measures Table contains:

| Measure                          | DAX Logic                                          |
| -------------------------------- | -------------------------------------------------- |
| **Total Number of Days**         | `DISTINCTCOUNT(Order Date)`                        |
| **Total Demand**                 | `SUM(Demand)`                                      |
| **Total Availability**           | `SUM(Availability)`                                |
| **Average Demand per Day**       | `DIVIDE(Total Demand, Total Number of Days)`       |
| **Average Availability per Day** | `DIVIDE(Total Availability, Total Number of Days)` |
| **Total Supply Shortage**        | `Total Demand - Total Availability`                |

The dependency structure is:

```text
Order Date
     ↓
Total Number of Days
     ↓
     ├───────────────┐
     ↓               ↓
Total Demand    Total Availability
     ↓               ↓
     ↓               ↓
Average Demand   Average Availability
     Per Day       Per Day
     │               │
     └───────┬───────┘
             ↓
    Total Supply Shortage
```

---

# 12. Create the First KPI Card

Now the measures are ready, so they need to be displayed visually.

The first KPI is:

> **Average Demand per Day**

### Steps

1. Expand the **Visualizations** pane.
2. Select the **Card** visual.
3. A blank Card visual is created.
4. Select the Card.
5. Add **Average Demand per Day** to the Card's field/data well.

The Card now displays the calculated value.

In the lecture, the value shown is approximately:

> **3.4**

---

# 13. Format the First Card

The instructor then formats the Card to match the report design.

### Background

1. Select the Card.
2. Go to **Format your visual**.
3. Go to **General**.
4. Open **Effects**.
5. Turn **Background** off.

The reason is that the report template already provides the background/design.

### Turn Off Category Label

The Card normally displays the measure name as a category label.

But the report already has the text:

> Average Demand per Day

at the bottom of the KPI box.

Therefore:

1. Go to **Visual**.
2. Find **Category label**.
3. Turn it **Off**.

### Format Callout Value

The actual KPI number is called the **Callout value**.

1. Open **Callout value**.
2. Change the font style according to the report design.
3. Make it **bold/italic** as required.
4. Change the font color to **white**.

The result is a cleaner KPI card.

---

# 14. Create the Second KPI Card

The second KPI is:

> **Average Availability per Day**

Instead of creating a new Card from scratch, the instructor duplicates the existing formatted Card.

### Steps

1. Select the first Card.
2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

4. Move the duplicated Card to the second KPI position.
5. Remove **Average Demand per Day** from its field/data well.
6. Select/check **Average Availability per Day**.

The Card now displays the second KPI.

The lecture shows approximately:

```text
Average Demand per Day      3.4
Average Availability       2.87
```

This approach is useful because the formatting of the first Card is automatically retained.

---

# 15. Create the Third KPI Card

The same duplication approach is used again.

### Steps

1. Select the **Average Availability per Day** Card.
2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

4. Move the new Card to the right-hand side.
5. Remove **Average Availability per Day** from the field/data well.
6. Select **Total Supply Shortage**.

The third Card now displays:

> **579**

So the report has three KPI Cards:

```text
┌────────────────────┐  ┌────────────────────┐  ┌────────────────────┐
│       3.4          │  │       2.87         │  │        579         │
│ Average Demand     │  │ Average Availability│ │ Total Supply       │
│ per Day            │  │ per Day             │ │ Shortage           │
└────────────────────┘  └────────────────────┘  └────────────────────┘
```

---

# 16. Make the KPIs Dynamic Using Filters

The instructor then adds user flexibility.

The requirement is:

> The user should be able to select a particular **Product** or **Date**, and the KPI values should automatically change according to that selection.

This is possible because DAX **measures respond to filter context**.

For example, if the user selects Product A, the measures calculate only for Product A.

---

# 17. Turn the Filters Pane Back On

### Steps

1. Go to the **View** tab.
2. Click **Filters**.

The Filters pane becomes visible again.

---

# 18. Add Product Name as a Page-Level Filter

The Product Name field comes from the:

> **Demand/Availability Data**

table.

### Steps

1. Find **Product Name** in the Demand/Availability Data table.
2. Drag it into:

> **Filters on this page**

Alternatively, the transcript describes double-clicking the field and then placing it into the page-level Filters section.

Now the user can select products.

For example:

```text
Product Name
☐ Product A
☐ Product B
☐ Product C
```

The user can select:

* One product
* Multiple products
* Different product combinations

The KPI values will update accordingly.

---

# 19. Add Date as a Page-Level Filter

The same approach is used for Date.

### Steps

1. Find the **Date** field in the Demand/Availability Data table.
2. Drag it into:

> **Filters on this page**

Now the user can select a particular date or date range.

For example:

```text
Date
01-Jan-2022
02-Jan-2022
03-Jan-2022
...
```

When a date is selected, the KPI calculations are recalculated according to the selected filter context.

---

# 20. Why Do the KPI Values Change?

This is an important DAX concept.

Measures are evaluated according to the **current filter context**.

Suppose the complete dataset has:

```text
Total Demand = 10,000
Total Availability = 9,421
```

Then:

```text
Supply Shortage = 579
```

But if the user filters:

```text
Product = Product A
```

Power BI recalculates:

```text
Total Demand → only Product A
Total Availability → only Product A
Total Supply Shortage → Product A
```

Similarly, if the user selects a particular date, the measures are evaluated for that date.

Therefore, the Cards are **dynamic KPIs**, not fixed numbers.

---

# 21. Format the Filters Pane

The instructor also formats the Filters pane so that it matches the dark-themed report.

### Steps

1. Select the report page.
2. Go to:

> **Format your report page**

3. Find:

> **Filters pane**

### Change Background

Set the Filters pane background to:

> **Black**

The default was white.

### Change Text Color

Set the text color to:

> **White**

This makes the filter text visible against the dark background.

---

# 22. Format Filter Cards

The instructor then formats the individual filter cards.

Under:

> **Filter cards**

the default state is customized.

### Text

Set the text color to:

> **White**

### Input Box

Set the input box color to:

> **Black**

### Background

Set the background color to:

> **Black**

This creates a consistent dark theme throughout the Filters pane.

The resulting design is visually more consistent with the report's dark-themed layout.

---

# 23. Final Report Page Structure

The completed page contains:

### KPI 1

**Average Demand per Day**

Example:

```text
3.4
```

### KPI 2

**Average Availability per Day**

Example:

```text
2.87
```

### KPI 3

**Total Supply Shortage**

Example:

```text
579
```

### Filters

The user can filter the page by:

* **Product Name**
* **Date**

The KPI values dynamically update based on those selections.

---

# 24. Complete DAX Code

For revision, these are the important measures from the session.

### 1. Total Number of Days

```DAX
Total Number of Days =
DISTINCTCOUNT('Demand/Availability Data'[Order Date])
```

### 2. Total Demand

```DAX
Total Demand =
SUM('Demand/Availability Data'[Demand])
```

### 3. Total Availability

```DAX
Total Availability =
SUM('Demand/Availability Data'[Availability])
```

### 4. Average Demand per Day

```DAX
Average Demand per Day =
DIVIDE(
    [Total Demand],
    [Total Number of Days]
)
```

### 5. Average Availability per Day

```DAX
Average Availability per Day =
DIVIDE(
    [Total Availability],
    [Total Number of Days]
)
```

### 6. Total Supply Shortage

```DAX
Total Supply Shortage =
[Total Demand] - [Total Availability]
```

---

# 25. Important Power BI Concepts from This Session

## A. Dedicated Measures Table

Creating a separate Measures Table is a good model-organization practice.

It makes the model easier to maintain:

```text
Measures Table
     ↓
All business calculations
     ↓
Cards / Charts / KPIs
```

---

## B. Measures Can Be Reused

Instead of repeatedly writing:

```DAX
SUM(Demand)
```

the instructor creates:

```DAX
[Total Demand]
```

and then reuses it:

```DAX
Average Demand per Day =
DIVIDE(
    [Total Demand],
    [Total Number of Days]
)
```

This makes DAX easier to read and maintain.

---

## C. `DISTINCTCOUNT()`

Used when we want the number of **unique values**.

```DAX
DISTINCTCOUNT([Order Date])
```

In this case:

> Number of unique dates = number of days represented in the dataset.

---

## D. `SUM()`

Used to calculate totals:

```DAX
SUM([Demand])
```

and:

```DAX
SUM([Availability])
```

---

## E. `DIVIDE()`

Used for division:

```DAX
DIVIDE(
    [Numerator],
    [Denominator]
)
```

In this session:

```DAX
DIVIDE(
    [Total Demand],
    [Total Number of Days]
)
```

---

## F. Filter Context

This is one of the most important concepts demonstrated indirectly in this session.

When the user applies:

```text
Product = Product A
```

or:

```text
Date = 01-Jan-2022
```

the measures automatically recalculate within that filter context.

Therefore, the same measure can produce different results depending on the user's selections.

---

# 26. Project Development Flow

This session is also part of a larger Power BI project workflow.

The current page focuses on:

> **Creating KPI measures and the first report page.**

The upcoming sessions will cover:

### Next

Creation of the **other report page and its KPIs**.

### Later

Moving the report from:

```text
Test Environment
        ↓
Production Environment
```

The instructor specifically mentions that an important upcoming topic will be:

> **How DAX measures are affected when the report is shifted from the test environment to the production environment.**

The project will also discuss:

* What needs to be considered when moving environments
* How DAX measures may be impacted
* What should be kept in mind for a smooth transition from test to production

---

# 27. End-to-End Workflow to Remember

The entire process from this lecture can be remembered as:

```text
Open Power BI Report
        ↓
Hide Filters Pane
        ↓
Create Measures Table
        ↓
Create Total Number of Days
        ↓
Create Total Demand
        ↓
Create Total Availability
        ↓
Delete unnecessary Column 1
        ↓
Create Average Demand per Day
        ↓
Create Average Availability per Day
        ↓
Create Total Supply Shortage
        ↓
Create Card Visual
        ↓
Add Average Demand per Day
        ↓
Format Card
        ↓
Duplicate Card
        ↓
Add Average Availability per Day
        ↓
Duplicate Card
        ↓
Add Total Supply Shortage
        ↓
Turn Filters Pane ON
        ↓
Add Product Name as Page Filter
        ↓
Add Date as Page Filter
        ↓
Format Filters Pane
        ↓
Complete KPI Page
        ↓
Next: Other Report Page
        ↓
Later: Test → Production
```

## Key takeaway

The central idea of this session is **building reusable DAX measures and using them as dynamic KPIs**. The measures are stored separately in a Measures Table, displayed through Card visuals, and automatically respond to Product and Date filters. This creates a clean, organized, and interactive Power BI report.
