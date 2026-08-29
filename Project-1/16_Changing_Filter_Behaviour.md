# Power BI — Dynamic Interaction Between Dimension Slicers Using Visual-Level Filters

## 1. Objective of This Lecture

The main objective of this lecture is to solve the problem identified in the previous session:

> **How can slicers containing fields from different dimension tables dynamically filter each other?**

Previously, the report had multiple slicers:

* Date
* Customer Name
* Product Name
* Promotion Name

Each slicer could filter the **Fact Table**, but the slicers themselves did not dynamically filter one another.

For example:

```text
Customer Slicer
      ↓
Fact Table
```

But the filter could not travel back to:

```text
Fact Table
      ↓
Promotion Dimension
```

because the model uses **unidirectional relationships**.

The solution demonstrated in this lecture is to create a **measure** and use it as a **visual-level filter** on each slicer.

---

# 2. First Format the Existing Slicers

Before implementing the dynamic filtering, the instructor first formats the existing report page.

## Change Slicer Style to Dropdown

The existing page contains four slicers.

### Steps

1. Select all four slicers.
2. Go to **Format your visual**.
3. Open **Slicer settings**.
4. Change the **Style** to:

**Dropdown**

This makes the slicers more compact.

Instead of displaying all possible values vertically, the user can click the dropdown and select a value.

---

# 3. Reposition the Slicers

The four slicers are rearranged to make the page look cleaner.

The instructor moves:

* The fourth slicer toward the end.
* The second slicer to another position.
* The third slicer to another position.

The exact positions are not important; the goal is to arrange the slicers neatly.

---

# 4. Align and Distribute the Slicers

After positioning the slicers approximately, they are made evenly spaced.

### Steps

1. Select all four slicers.
2. Go to:

**Format → Align → Distribute horizontally**

This makes the spacing between the slicers consistent.

### Key point

Power BI provides alignment and distribution options to quickly create a clean report layout.

---

# 5. Create a Separate Demonstration Page

The instructor creates a new page to explain the dynamic slicer interaction concept.

### Steps

1. Click the **`+` icon**.
2. A new page is created.
3. Add a **Slicer** visual.
4. Resize it as required.

---

# 6. Create Customer Name Slicer

The first slicer will contain values from the **Customer Dimension**.

### Steps

1. Expand the **Customer Dimension** table.
2. Select **Customer Name**.
3. The slicer now displays customer names.

---

# 7. Create Promotion Name Slicer

Rather than creating another slicer from scratch:

1. Select the Customer Name slicer.
2. Press:

`Ctrl + C`

3. Press:

`Ctrl + V`
4. Move the copied slicer to the right.
5. Remove **Customer Name** from its Fields bucket.
6. Expand the **Promotion Dimension** table.
7. Select **Promotion Name**.

Now there are two slicers:

* Customer Name
* Promotion Name

---

# 8. Problem With the Two Slicers

Initially, selecting a customer does **not** change the available promotion names.

For example:

```text
Customer Slicer → Select Customer
```

The Promotion Name slicer still displays the same promotion categories.

Similarly:

```text
Promotion Slicer → Select Promotion
```

does not automatically reduce the Customer Name slicer.

### Why?

Because the model has **unidirectional relationships**:

```text
Dimension
    ↓
Fact
```

The filter can travel from the dimension to the Fact Table, but it cannot travel from the Fact Table back to another dimension.

---

# 9. Solution: Create a Measure

The lecture solves this using a simple measure.

The measure is created in the **Promotion Dimension** table.

### Steps

1. Right-click the **Promotion Dimension** table.
2. Select **New Measure**.

Create the measure:

**Some Dim**

The measure uses the `SUM()` function on the **Net Sales** column from the Fact Table.

Conceptually:

```text
Some Dim = SUM(Fact Table[Net Sales])
```

This is a very simple measure.

---

# 10. Why Create This Measure?

The important idea is not the actual sales total itself.

The measure is being used to determine whether a particular dimension value has corresponding data under the current filter context.

For a particular Promotion Name:

* If there are corresponding Fact Table records → the measure has a value.
* If there are no corresponding records → the measure becomes **BLANK**.

Therefore, the measure can be used to identify which slicer values are relevant under the current selection.

---

# 11. Add the Measure as a Filter to Customer Slicer

Now the measure is used as a **visual-level filter**.

### Steps

1. Click on a blank area of the canvas.
2. Select the **Customer Name slicer**.
3. Expand the **Filters pane**.
4. Locate the `Some Dim` measure.
5. Drag the measure into the **Filters on this visual / Add data fields** section.
6. Under:

**Show items when the value is**

select:

**is not blank**

7. Click:

**Apply filter**

This is extremely important.

---

# 12. Add the Same Measure to Promotion Slicer

Now perform the same operation for the Promotion Name slicer.

### Steps

1. Select the **Promotion Name slicer**.
2. Add the `Some Dim` measure to the visual-level filter section.
3. Under:

**Show items when the value is**

select:

**is not blank**

4. Click:

**Apply filter**

Now both slicers have the same measure-based visual filter.

---

# 13. Test Customer → Promotion Interaction

Now select a customer.

For example:

**Out of Sync**

After selecting the customer, observe the Promotion Name slicer.

Previously, all promotion names were displayed.

Now only the promotion categories that have corresponding sales/data for that customer remain visible.

Therefore:

```text
Customer Selection
       ↓
Fact Table is filtered
       ↓
Some Dim measure is evaluated
       ↓
Blank categories are removed
       ↓
Promotion slicer shows relevant values
```

This creates the desired dynamic interaction.

---

# 14. How the Measure-Based Filtering Works

This is the most important concept in the lecture.

Suppose we select a particular customer.

The filter first propagates normally:

```text
Customer Dimension
        ↓
    Fact Table
```

Now Power BI evaluates the `Some Dim` measure for each Promotion Name.

Conceptually:

```text
Promotion A → Net Sales exists → Measure NOT BLANK
Promotion B → Net Sales exists → Measure NOT BLANK
Promotion C → No matching sales → Measure BLANK
```

Because the slicer is configured with:

**Show items when Some Dim is not blank**

Promotion C is removed from the slicer.

Thus, the slicer appears dynamically filtered.

---

# 15. Test With Another Customer

Select another customer, such as:

**Aditi Patel**

The available promotion categories change again.

Only those promotion categories for which the `Some Dim` measure is **not blank** remain visible.

This proves that the interaction is dynamic.

---

# 16. Reverse Interaction: Promotion → Customer

The same technique also works in the opposite direction.

Suppose the user selects a promotion such as:

**Clearance Sale**

The Customer Name slicer now displays only customers associated with that promotion.

The reason is again the measure-based visual filter.

Conceptually:

```text
Promotion Selection
        ↓
    Fact Table
        ↓
Some Dim evaluated for customers
        ↓
Only non-blank customers remain
```

---

# 17. Example: Clearance Sale

When **Clearance Sale** is selected:

* The table gets filtered.
* Only relevant customers remain in the Customer Name slicer.
* Only relevant products/dates/etc. can remain in their respective slicers once the same technique is applied.

The lecture demonstrates that different customers become available depending on the selected promotion.

---

# 18. Example: Festive Diwali

Select:

**Festive Diwali**

Only the customers who availed that promotion remain in the Customer slicer.

The lecture notes that only a small number of customers are associated with this promotion in the sample data.

This demonstrates that the slicer values are being dynamically reduced according to the current filter context.

---

# 19. Other Promotion Examples

The same behavior can be observed for:

* New Year Special
* Summer Sale
* Flash Sale
* Clearance Sale
* Festive Diwali
* Blank

Each selection produces a different set of relevant customers.

---

# 20. Apply the Technique to the Actual Report

After demonstrating the concept on the separate page, the same technique is applied to the main Requirement 7 page.

The main page contains four slicers:

1. Date
2. Customer Name
3. Product Name
4. Promotion Name

The same `Some Dim` measure is added as a visual-level filter to each slicer.

---

# 21. Add Measure to Date Slicer

### Steps

1. Go to the main report page.
2. Select **Date Slicer**.
3. Open the **Filters pane**.
4. Add the `Some Dim` measure to the visual-level filter.
5. Set:

**Show items when the value is → is not blank**

6. Click **Apply filter**.

---

# 22. Add Measure to Customer Name Slicer

### Steps

1. Select the Customer Name slicer.
2. Drag the `Some Dim` measure into the visual-level filter section.
3. Set:

**is not blank**

4. Click **Apply filter**.

---

# 23. Add Measure to Product Name Slicer

### Steps

1. Select Product Name slicer.
2. Add `Some Dim` to the visual-level filter.
3. Select:

**is not blank**

4. Click **Apply filter**.

---

# 24. Add Measure to Promotion Name Slicer

### Steps

1. Select Promotion Name slicer.
2. Add `Some Dim` to the visual-level filter.
3. Set:

**is not blank**

4. Click **Apply filter**.

---

# 25. Important: These Are Visual-Level Filters

The instructor specifically identifies these filters as **visual-level filters**.

The measure isn't being used as a normal page-level or report-level filter.

It is being applied individually to each slicer.

Therefore:

```text
Some Dim Measure
       ↓
Visual-level filter
       ↓
Slicer
```

This allows the slicer's available values to dynamically change according to the current filter context.

---

# 26. Test the Complete Report

Now test whether the dynamic filtering works correctly.

## Test 1 — Select a Date

Suppose we select:

**1 January 2020**

The table gets filtered to show records from that date.

But now, because the `Some Dim` measure is also filtering the slicers:

### Customer slicer

Only customers who made purchases on that date are displayed.

### Product slicer

Only products purchased on that date are displayed.

### Promotion slicer

Only promotions relevant to that date are displayed.

---

# 27. Example: No Promotion on a Date

Suppose the selected date has no promotional discounts.

Then the Promotion Name slicer may display only:

**Blank**

This is logical because the corresponding records have no promotion.

The lecture observes that this is exactly what happens for the demonstrated date.

---

# 28. Test Customer Selection

Now select a customer.

The report dynamically adjusts:

### Date Slicer

Only dates on which that customer made purchases remain.

### Product Slicer

Only products purchased by that customer remain.

### Promotion Slicer

Only promotions used by that customer remain.

### Table

Only that customer's relevant orders are displayed.

---

# 29. Test Product Selection

Now clear the other filters and select a product.

For example:

**Adidas Sneakers**

The slicers dynamically adjust to show:

* Relevant customers
* Relevant dates
* Relevant promotions

The table also shows only the corresponding product records.

This confirms that the dynamic filtering works in both directions between the different dimension-based slicers.

---

# 30. Test Promotion Selection

Now select a promotion.

For example:

**Festive Diwali**

The report dynamically filters:

* Table
* Product slicer
* Customer slicer
* Date slicer

Only the relevant values remain available.

The lecture gives an example where the corresponding transaction occurs on a particular date, such as **24 October**.

---

# 31. Overall Filtering Architecture

The resulting behavior can be understood as:

```text id="d3nq5a"
                    USER SELECTION
                          │
             ┌────────────┼────────────┐
             ↓            ↓            ↓
        Date Slicer  Customer Slicer  Product Slicer
             │            │            │
             └────────────┼────────────┘
                          ↓
                      Fact Table
                          ↓
                   Some Dim Measure
                          ↓
             Visual-Level "Not Blank"
                          ↓
             Remaining Slicer Values
```

The important point is that the measure allows the slicers to **simulate cross-dimension filtering** without changing the underlying relationship direction.

---

# 32. Why Does "Not Blank" Matter?

The filter condition is:

> **Show items when the value is not blank**

Suppose a slicer contains:

```text
A
B
C
D
```

Under the current filter context, the measure might return:

```text
A → 5000
B → BLANK
C → 2500
D → BLANK
```

The visual-level filter keeps only:

```text
A
C
```

because their measure values are not blank.

Thus:

**Not Blank = Relevant value exists in the current filter context**

---

# 33. Why Use Net Sales in the Measure?

The measure uses:

**SUM(Fact Table[Net Sales])**

The exact measure is less important than its behavior.

The goal is to have a measure that returns:

* A value when relevant Fact Table records exist.
* Blank when no relevant records exist.

This allows the slicer to determine which dimension values are actually associated with the current selection.

---

# 34. Format the Table Visual

After completing the functionality, the instructor formats the main table.

### Steps

1. Select the Table visual.
2. Expand the visualization/formatting pane.
3. Select **Format your visual**.

---

# 35. Enable Horizontal Gridlines

Under the table's gridline settings:

1. Find **Horizontal gridlines**.
2. Change it to:

**On**

This improves row separation.

---

# 36. Enable Vertical Gridlines

Similarly:

1. Find **Vertical gridlines**.
2. Change it to:

**On**

Now both horizontal and vertical gridlines are visible.

---

# 37. Format Vertical Gridline Color

For the vertical gridlines:

1. Select the gridline color option.
2. Choose a suitable **gray** color.
3. Increase the gridline width if required.

This improves readability without making the grid too visually dominant.

---

# 38. Format Horizontal Gridlines

Similarly, for horizontal gridlines:

1. Adjust the color if required.
2. Increase the width if required.

The exact formatting is a matter of design preference.

---

# 39. Format Column Headers

The column headers can also be customized.

### Steps

1. Open **Column headers** in the formatting pane.
2. Change the font style if desired.
3. The lecture uses:

**Times New Roman**

4. Increase the font size.
5. The lecture uses approximately:

**13**

This makes the table headers easier to read.

---

# 40. Format Slicer Values

The slicer values can also be formatted.

### Steps

1. Select a slicer.
2. Open the formatting options.
3. Go to **Values**.
4. Adjust the font size as required.
5. Bold can be enabled if desired.

However, the lecture observes that bold values don't necessarily look better in this particular design, so the default/non-bold formatting is retained.

---

# 41. Clean Up the Report Pages

After completing the project, some pages were created purely for demonstration purposes.

One such page was used only to demonstrate the dynamic slicer concept.

Since it is no longer needed:

1. Select that page.
2. Delete it.

This keeps the final report clean.

---

# 42. Rename the Main Table Page

The original page containing the table visual is renamed.

### Steps

1. Select the page.
2. Double-click the page name.
3. Press `Ctrl + A`.
4. Rename it:

**Table Visual**

This makes the purpose of the page clear.

---

# 43. Rename the Edit Interactions Page

Another page was created for the Requirement 4 demonstration.

Since that page specifically demonstrated Power BI's Edit Interactions feature, rename it:

**Edit Interactions**

---

# 44. Rename the Comparison Page

The page containing the Sales/Profit/Quantity comparison is renamed:

**Comparison Sales / Profit / Quantity**

This clearly identifies the purpose of that report page.

---

# 45. Final Report Structure

After cleaning up the pages, the report contains appropriately named pages such as:

```text id="7k7frc"
1. Table Visual
2. Edit Interactions
3. Comparison Sales / Profit / Quantity
```

The exact numbering may vary depending on the report's page structure.

---

# 46. Complete Conceptual Flow

The entire solution can be summarized as follows:

```text id="2t7d3g"
Dimension Slicer Selection
          ↓
     Fact Table
          ↓
    Some Dim Measure
          ↓
 Measure returns:
    Value / BLANK
          ↓
Visual-level filter:
    "is not blank"
          ↓
Only relevant values
remain in other slicers
```

This effectively gives the user **dynamic interaction between slicers from different dimension tables**.

---

# 47. Before vs After

## Before

Selecting a customer:

```text
Customer Slicer
      ↓
Fact Table
      ↓
Table Visual
```

But:

```text
Promotion Slicer → unchanged
Product Slicer   → unchanged
Date Slicer      → unchanged
```

because of the unidirectional relationships.

---

## After

With the measure-based visual filters:

```text
Customer Selection
        ↓
    Fact Table
        ↓
  Some Dim Measure
        ↓
 Visual-level filter
        ↓
Relevant values remain
in other slicers
```

Therefore:

```text
Customer ↔ Product
Customer ↔ Promotion
Customer ↔ Date
Product  ↔ Customer
Product  ↔ Promotion
Product  ↔ Date
Promotion ↔ Customer
Promotion ↔ Product
Promotion ↔ Date
```

The slicers now dynamically respond to the current filter context.

---

# 48. Important Power BI Concepts Covered

This lecture covers several important Power BI concepts.

### Slicer formatting

* Slicer settings
* Dropdown style
* Alignment
* Distribution

### Measures

* Creating a measure
* `SUM()` function
* Referencing a Fact Table column

### Visual-level filters

* Adding a measure to a visual's filter section
* Using **Show items when the value is not blank**
* Applying filters to slicers

### Filter context

The measure is evaluated according to the current filter context.

### Relationship direction

Understanding:

**Dimension → Fact**

versus the inability of the filter to automatically propagate:

**Fact → Dimension**

### Dynamic slicer filtering

Using a measure-based visual filter to dynamically restrict slicer values.

---

# 49. Important Practical Steps to Remember

When you need to make dimension-based slicers dynamically filter one another:

### Step 1 — Create a measure

Create a measure such as:

```text
Some Dim = SUM(Fact Table[Net Sales])
```

### Step 2 — Select the slicer

Select the slicer whose available values need to be dynamically filtered.

### Step 3 — Open Filters pane

Add the measure under the visual-level filter section.

### Step 4 — Configure the condition

Set:

**Show items when the value is → is not blank**

### Step 5 — Apply

Click:

**Apply filter**

### Step 6 — Repeat

Apply the same technique to the other dimension-based slicers.

---

# 50. Final Project Completion

The lecture concludes the Power BI project.

The project covered:

* Different Power BI visuals
* Filters and slicers
* Data modeling
* Relationships
* DAX measures
* Date tables
* Active/inactive relationships
* Edit Interactions
* Requirement-based report creation
* Order-level detail reporting
* Dynamic slicer interaction
* Visual-level filters
* Formatting and report design

The instructor notes that the project has now covered the **different requirements given for the project** and that the next session will begin the **next project**.
