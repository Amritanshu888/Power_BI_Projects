# Power BI — Requirement 7: Order-Level Detail Report with Dimension-Based Slicers

## 1. Requirement Overview

This is the **last requirement of the project — Requirement 7**.

The requirement is to create a report page that shows **all relevant details for each order** from the Fact Table.

The report should display fields such as:

* Customer ID
* Order ID
* Date
* Discount
* Discount Percentage
* Net Sales
* Price per Unit
* Product ID
* Profit
* Promotion ID
* Total Sales
* Units Sold

Additionally, users should be able to **filter this order-level table using slicers** coming from different dimension tables.

The required slicers include values such as:

| Dimension Table     | Field used for filtering |
| ------------------- | ------------------------ |
| Date Dimension      | Date                     |
| Customer Dimension  | Customer Name            |
| Product Dimension   | Product Name             |
| Promotion Dimension | Promotion Name           |

The important objective is that selecting a value in these slicers should filter the order-level data accordingly.

---

# 2. Create a New Report Page

We already have an existing Power BI report.

### Steps

1. Open the existing Power BI report.
2. At the bottom of the report, click the **`+` icon**.
3. A new report page will be created.
4. This page will be used for **Requirement 7**.

---

# 3. Create the Order-Level Table Visual

The main visual for this requirement is a **Table**.

### Steps

1. Click on a blank area of the canvas.
2. Select the **Table** visual from the Visualizations pane.
3. A blank table visual will be created.
4. Move and resize the table according to your requirements.

The purpose of this table is to display the details of **each individual order**.

---

# 4. Add Fact Table Fields to the Table

With the table visual selected, expand the **Fact Table**.

Add the required fields by selecting their checkboxes.

The fields demonstrated in the lecture are:

1. **Customer ID**
2. **Date**
3. **Discount**
4. **Discount Percentage**
5. **Net Sales**
6. **Order ID**
7. **Price per Unit**
8. **Product ID**
9. **Profit**
10. **Promotion ID**
11. **Total Sales**
12. **Unit Sold**

These fields collectively provide the required order-level information.

---

# 5. Understanding the Grain of the Table

The table is intended to show information at the **order level**.

Therefore, the table should contain the different attributes and measures associated with each order, such as:

```text
Customer
    ↓
Order
    ↓
Date
    ↓
Product
    ↓
Sales / Discount / Profit / Quantity / Promotion
```

The exact fields available depend on the structure of the Fact Table.

---

# 6. Format the Table Visual

Once the required fields have been added, format the table.

### Add a Border

1. Select the table visual.
2. Go to **Format your visual**.
3. Select **General**.
4. Open **Effects**.
5. Turn **Visual border** → **On**.

This adds a border around the table.

---

# 7. Change the Table Style

Power BI provides different table styles.

With the table selected:

1. Open the table's **Visual** formatting options.
2. Look for the available **Style** options.
3. You can choose a style such as:

   * Alternating rows
   * Flashy rows
   * Other available styles

The lecture demonstrates trying different styles to make the table visually better.

> The exact style is a matter of preference. The important point is that Power BI provides built-in styles for improving table readability.

---

# 8. Reorder the Columns

The order in which fields are added may not be the desired order.

For example, the lecture wants **Order ID** to appear near the beginning.

### Steps

1. Select the table.
2. Go to **Add data to your visual / Columns**.
3. Locate **Order ID**.
4. Drag it upward.
5. Place it immediately below **Customer ID**.

The resulting beginning of the table becomes:

```text
Customer ID
Order ID
Date
...
```

---

# 9. Rename Aggregated Column Names

Some numerical fields may automatically appear with aggregation names such as:

**Sum of Discount**

However, the requirement is to show the actual field name rather than unnecessarily displaying "Sum of".

### Example

Instead of:

**Sum of Discount**

we can rename it to:

**Discount**

### Steps

1. Locate **Sum of Discount** in the visual's field bucket.
2. Double-click the field.
3. Replace the name with:

**Discount**

The same approach can be used wherever required.

---

# 10. Disable Summarization

This is an important part of configuring the table.

For fields where we want to display the **individual value for each row/order**, we don't want Power BI to aggregate the values.

For example, we don't want:

```text
Sum of Discount
Sum of Discount Percentage
Sum of Net Sales
Sum of Price Per Unit
Sum of Profit
Sum of Total Sales
Sum of Unit Sold
```

Instead, we want the actual value associated with each order.

Therefore, use:

**Don't summarize**

---

# 11. Change Discount to Don't Summarize

For Discount:

1. Open the dropdown beside the Discount field.
2. Select **Don't summarize**.

Now Power BI will display the individual discount value rather than summing it.

---

# 12. Change Discount Percentage to Don't Summarize

For Discount Percentage:

1. Open the dropdown beside the field.
2. Select **Don't summarize**.

This prevents Power BI from displaying:

**Sum of Discount Percentage**

and instead displays the individual percentage value.

---

# 13. Change Net Sales to Don't Summarize

For Net Sales:

1. Open its dropdown.
2. Select **Don't summarize**.

This is important because we want the Net Sales value for each order rather than a combined total in each row.

---

# 14. Change Price Per Unit to Don't Summarize

For Price Per Unit:

1. Open its dropdown.
2. Select **Don't summarize**.

This displays the actual price per unit associated with each row.

---

# 15. Change Profit to Don't Summarize

For Profit:

1. Open the dropdown next to Profit.
2. Select **Don't summarize**.

Although Profit is a numerical field, it is being displayed as an individual order-level value.

---

# 16. Change Total Sales to Don't Summarize

For Total Sales:

1. Open its dropdown.
2. Select **Don't summarize**.

This allows the table to show the sales value associated with each order.

---

# 17. Change Unit Sold to Don't Summarize

For Unit Sold:

1. Open the dropdown beside Unit Sold.
2. Select **Don't summarize**.

Now the table displays the quantity sold for each individual row/order.

---

# 18. Fields That Don't Need This Change

Fields such as:

* Customer ID
* Order ID
* Date
* Product ID
* Promotion ID

are categorical/identifier/date fields and don't require the same numerical summarization configuration.

---

# 19. Final Order-Level Table

After configuration, the table contains information such as:

| Customer ID | Order ID | Date | Discount | Discount % | Net Sales | Price/Unit | Product ID | Profit | Promotion ID | Total Sales | Units Sold |
| ----------- | -------- | ---- | -------: | ---------: | --------: | ---------: | ---------- | -----: | ------------ | ----------: | ---------: |

The actual values come from the Fact Table.

---

# 20. Create Date Slicer

Now we need to provide filtering functionality.

The first slicer will come from the **Date Dimension**.

### Steps

1. Click on a blank area of the canvas.
2. Select the **Slicer** visual.
3. Resize it as required.
4. Expand the **Date Dimension** table.
5. Select the **Date** field.

The slicer now displays available dates.

---

# 21. Test the Date Slicer

The slicer allows the user to select a date or date range.

For example, the lecture demonstrates selecting a range such as:

**10/01/2020 to 31/12/2024**

The table then displays only the records corresponding to the selected date range.

Therefore:

> Date Slicer → filters the Order-Level Table.

---

# 22. Clear a Slicer Selection

To remove the current filter:

1. Select the slicer.
2. Click **Clear selections**.

The table will return to displaying the unfiltered data.

---

# 23. Format the Date Slicer

To make the slicer visually consistent:

1. Select the Date slicer.
2. Go to **Format your visual**.
3. Select **General**.
4. Open **Effects**.
5. Turn **Visual border** → **On**.

---

# 24. Create Customer Name Slicer

The second slicer should come from the **Customer Dimension**.

Instead of creating a new slicer from scratch, the lecture duplicates the existing slicer.

### Steps

1. Select the Date slicer.
2. Press:

`Ctrl + C`

3. Press:

`Ctrl + V`
4. Move the newly created slicer to the desired location.
5. Remove the **Date** field from its Fields bucket.
6. Expand the **Customer Dimension**.
7. Select **Customer Name**.

The slicer now displays different customer names.

---

# 25. Test Customer Slicer

For example, if the user selects:

**Arun Joshi**

the table is filtered to show only orders belonging to that customer.

The lecture observes that:

* Arun Joshi has Customer ID **7**
* The table displays the orders placed by that customer.
* The corresponding dates, discounts, sales, products, profit, etc. are shown.

Therefore:

> Customer Name Slicer → filters the Fact Table/order-level table.

---

# 26. Reorder Product ID

The lecture also demonstrates that columns can be rearranged.

For example, **Product ID** can be moved closer to Order ID.

### Steps

1. Select the table.
2. Locate Product ID in the field bucket.
3. Drag it upward.
4. Place it below **Order ID**.

The table can therefore be arranged according to the business requirement.

---

# 27. Reorder Promotion ID

Similarly, Promotion ID can be repositioned.

Move:

**Promotion ID**

to appear below:

**Product ID**

The resulting sequence becomes approximately:

```text
Customer ID
Order ID
Date
Product ID
Promotion ID
...
```

The exact column order is configurable.

### Important takeaway

> Power BI allows you to easily drag and drop fields within the visual's field bucket to change the order of columns.

---

# 28. Create Product Name Slicer

Now create another slicer for products.

### Steps

1. Select the Customer Name slicer.
2. Press `Ctrl + C`.
3. Press `Ctrl + V`.
4. Move the copied slicer to the desired location.
5. Remove **Customer Name** from the Fields bucket.
6. Expand the **Product Dimension** table.
7. Select **Product Name**.

The slicer now displays the available product names.

---

# 29. Test Product Name Slicer

For example, select:

**Fossil Smartwatch**

The table will be filtered to display only records related to that product.

Therefore:

> Product Name Slicer → filters the Order-Level Table.

After testing, clear the selection to restore the complete dataset.

---

# 30. Create Promotion Name Slicer

The fourth slicer will come from the **Promotion Dimension**.

### Steps

1. Select the Product Name slicer.
2. Press `Ctrl + C`.
3. Press `Ctrl + V`.
4. Move the new slicer to the required position.
5. Remove **Product Name** from its field bucket.
6. Expand the **Promotion Dimension** table.
7. Select **Promotion Name**.

The slicer now displays the available promotion names.

---

# 31. Blank Promotion Category

An important data scenario is demonstrated here.

The Promotion Name slicer contains a **blank** value.

This represents records where **no promotion/discount was applied**.

If the user selects:

**Blank**

the table is filtered accordingly.

The lecture observes that for these records:

* Discount = **0**
* Discount Percentage = **0**

This is an important example of how blank dimension values can represent a meaningful business condition.

---

# 32. Test a Specific Promotion

For example, select:

**Clearance Sale**

The table will show only orders associated with the selected promotion.

The lecture notes that these records represent a particular discount scenario, with **70% discount** in the demonstrated data.

The number of records is smaller because only a subset of orders belongs to that promotion.

---

# 33. Four Slicers Created

At this stage, the report contains four slicers:

| Slicer           | Source Table        | Field          |
| ---------------- | ------------------- | -------------- |
| Date Slicer      | Date Dimension      | Date           |
| Customer Slicer  | Customer Dimension  | Customer Name  |
| Product Slicer   | Product Dimension   | Product Name   |
| Promotion Slicer | Promotion Dimension | Promotion Name |

These slicers can filter the main order-level table.

---

# 34. Important Observation: Slicers Do Not Filter Each Other

At this stage, something important happens.

When we select a value in one of the four slicers:

> The **table visual gets filtered**.

However:

> The **other dimension slicers do not get filtered**.

For example, suppose we select a product.

The table is filtered to that product's records.

But the Customer Name slicer may still display customers that are not associated with that selected product.

This behavior is caused by the structure of the Power BI data model.

---

# 35. Understand the Data Model

The model contains:

* Multiple Dimension Tables
* One Fact Table

Conceptually:

```text
                 Date Dimension
                       |
                       ↓
Customer Dimension → Fact Table ← Product Dimension
                       ↑
                       |
                Promotion Dimension
```

The dimension tables are related to the Fact Table.

---

# 36. Direction of Relationships

The relationships between the dimension tables and Fact Table are **unidirectional**.

The filter direction is:

```text
Dimension Table
       ↓
   Fact Table
```

For example:

```text
Customer Dimension
       ↓
   Fact Table
```

A customer selection can therefore filter the Fact Table.

---

# 37. Why Doesn't the Filter Reach Other Dimensions?

Suppose the user selects a product.

The filtering process is:

```text
Product Dimension
       ↓
   Fact Table
```

The Fact Table gets filtered.

But the filter **does not continue from the Fact Table back up to Customer Dimension**.

So:

```text
Product Dimension
       ↓
   Fact Table
       X
Customer Dimension
```

The filter cannot propagate in that direction because the relationship is unidirectional.

---

# 38. Example: Product → Customer

Suppose the user selects:

**Fossil Smartwatch**

The filter travels:

```text
Product Dimension
       ↓
Fact Table
```

Therefore, only Fossil Smartwatch records are displayed in the table.

But the filter does not travel:

```text
Fact Table
       ↓
Customer Dimension
```

Therefore, the Customer Name slicer does not automatically reduce its list to only customers who purchased the Fossil Smartwatch.

---

# 39. Example: Customer → Product

The same principle applies in the opposite direction.

If the user selects:

**Arun Joshi**

the filter travels:

```text
Customer Dimension
       ↓
Fact Table
```

The table shows Arun Joshi's orders.

But the filter doesn't automatically propagate back into:

```text
Fact Table
       ↓
Product Dimension
```

because the relationship is unidirectional.

---

# 40. Why This Happens

The reason is the relationship configuration.

The model uses **single-direction/unidirectional relationships**:

> Dimension → Fact

This is generally a common and desirable modeling pattern because it avoids unnecessary ambiguity and complicated filter propagation.

However, it means dimension tables don't automatically filter one another through the Fact Table.

---

# 41. Requirement Identified for the Next Step

The lecture ends by introducing another requirement:

> What if we want the different dimension tables to filter each other?

For example:

```text
Select Product
      ↓
Customer slicer should show
only relevant customers
```

or:

```text
Select Customer
      ↓
Product slicer should show
only relevant products
```

This does **not happen automatically** with the current unidirectional model.

---

# 42. Proposed Solution

The lecture states that this requirement can be achieved using **measures**.

The next video will discuss how measures can be used to make the different dimension-based slicers respond to one another.

So the current lecture establishes the problem, while the **next lecture will implement the solution**.

---

# 43. Complete Report Architecture

The final page created in this lecture can be visualized as:

```text
┌──────────────────────────────────────────────────────────────┐
│                    REQUIREMENT 7 PAGE                        │
│                                                              │
│  Date Slicer     Customer Slicer    Product Slicer           │
│                                                              │
│  Promotion Slicer                                           │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │                   ORDER-LEVEL TABLE                    │  │
│  │                                                        │  │
│  │ Customer ID                                            │  │
│  │ Order ID                                               │  │
│  │ Date                                                   │  │
│  │ Discount                                               │  │
│  │ Discount %                                             │  │
│  │ Net Sales                                              │  │
│  │ Price per Unit                                         │  │
│  │ Product ID                                             │  │
│  │ Profit                                                 │  │
│  │ Promotion ID                                           │  │
│  │ Total Sales                                            │  │
│  │ Unit Sold                                              │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
```

---

# 44. Key Concepts to Remember

### 1. Order-level reporting

A Table visual can be used to display detailed information for each order rather than only aggregated KPIs.

### 2. Don't Summarize

For order-level numerical fields, use:

**Dropdown → Don't summarize**

when the requirement is to show the individual value instead of an aggregate.

### 3. Slicers from Dimension Tables

Slicers should ideally use fields from dimension tables, such as:

* Date Dimension → Date
* Customer Dimension → Customer Name
* Product Dimension → Product Name
* Promotion Dimension → Promotion Name

### 4. Dimension → Fact filtering

With a standard unidirectional relationship:

```text
Dimension → Fact
```

The dimension can filter the Fact Table.

### 5. Fact → Dimension filtering doesn't occur

The filter doesn't automatically travel back:

```text
Dimension → Fact → Dimension
                 ↑
              blocked
```

Therefore, one dimension doesn't automatically filter another dimension through the Fact Table.

### 6. Measures can solve cross-dimension filtering

If the requirement is to make dimension slicers dynamically filter one another, additional logic using **measures** can be implemented.

That topic is covered in the next lecture.

---

# 45. Exam/Interview-Oriented Summary

**Requirement 7:** Create an order-level detail report containing all relevant Fact Table fields and provide slicers from different dimensions.

**Main visual:** Table

**Fact Table fields:** Customer ID, Order ID, Date, Discount, Discount %, Net Sales, Price per Unit, Product ID, Profit, Promotion ID, Total Sales, Unit Sold.

**Slicers:**

* Date
* Customer Name
* Product Name
* Promotion Name

**Important formatting:**

* Add visual border.
* Choose an appropriate table style.
* Reorder columns using drag-and-drop.
* Use **Don't summarize** for numerical fields where individual row-level values are required.

**Important modeling concept:**

With unidirectional relationships:

```text
Dimension → Fact
```

a dimension filters the Fact Table, but a filter does not propagate from the Fact Table back to another dimension.

Therefore, selecting a product can filter the order table but does not automatically filter the Customer slicer.

**Next topic:** Using **measures** to make different dimension tables/slicers filter each other.
