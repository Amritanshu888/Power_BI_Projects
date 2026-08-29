# Power BI — Handling Null Values, Merging Tables & Creating Calculated Columns

## 1. Objective of the Session

The main objective of this session is to **transform the fact table so that it no longer contains unnecessary/null values** and is ready to be used for reporting.

The lecture demonstrates how to:

1. Bring data from dimension tables into a fact table using **Merge Queries**.
2. Use a **Left Outer Join** to combine tables.
3. Expand merged columns.
4. Replace null values.
5. Create calculated/custom columns in Power Query.
6. Remove old columns containing null values.
7. Rename and reorder columns.
8. Change data types.
9. Apply transformations using **Close & Apply**.
10. Return to the Power BI Report View and understand the report canvas.

---

# 2. Fact Table and Dimension Tables

The model contains a **fact table** along with dimension tables such as:

* **Dimension Product**
* **Dimension Promotion**

The fact table contains transactional information such as:

* Product ID
* Promotion ID
* Unit Sold
* Price per Unit
* Total Sales
* Discount Percentage
* Discount Value
* Net Sales

However, some of these columns contain **null values**.

Instead of simply leaving those columns incomplete, the required information can often be obtained from the appropriate dimension tables.

### Key idea

> **Fact tables contain transactional data, while dimension tables often contain descriptive/master data that can be brought into the fact table using joins/merges.**

---

# 3. Inspecting Null Values

Before performing transformations, the instructor first checks the columns for missing values.

### Steps

1. Open **Power Query Editor**.
2. Uncheck the previously selected profiling/checking options if necessary.
3. Examine the columns of the fact table.
4. Identify columns containing null/empty values.

The lecture focuses on columns where useful information can be reconstructed from other tables.

---

# 4. Bringing Price Per Unit from Dimension Product

## Problem

The fact table has:

* `Product ID`
* `Price Per Unit`

But some values in the **Price Per Unit** column are null.

The **Dimension Product** table already contains:

* `Product ID`
* Price for each product

Therefore, the price can be brought from the Dimension Product table into the fact table.

---

# 5. Understanding Merge Queries

Power Query provides the **Merge Queries** functionality to combine information from two tables.

It is conceptually similar to performing a **JOIN** in SQL.

### Important distinction

There are two options:

### Merge Queries

Updates the **existing query/table**.

### Merge Queries as New

Creates a **new query/table** containing the merged result.

Since the instructor wants to modify the existing fact table, the option used is:

> **Merge Queries**

---

# 6. Merge Fact Table with Dimension Product

### Steps

1. Select the **Fact Table**.
2. Go to the **Home** tab.
3. Click **Merge Queries**.
4. Select **Merge Queries**, not **Merge Queries as New**.
5. The Fact Table becomes the first/left table.
6. Select the `Product ID` column in the Fact Table.
7. Select the **Dimension Product** table as the second table.
8. Select `Product ID` in the Dimension Product table.
9. Select the appropriate join type.

The lecture uses:

> **Left Outer Join**

---

# 7. What is a Left Outer Join?

A **Left Outer Join** means:

> Keep **all rows from the first/left table** and bring in the matching rows from the second/right table.

In this case:

**Fact Table**

⬇️ `Product ID`

**Dimension Product**

So every transaction in the fact table is retained, while matching product information is brought from the Dimension Product table.

### Matching result

Power Query shows:

> **3510 of 3510 rows matched**

This means all 3,510 rows in the fact table have corresponding Product IDs in the Dimension Product table.

---

# 8. Expanding the Merged Column

After the merge, Power Query creates a **new column containing nested table values**.

This column needs to be expanded.

### Steps

1. Click the **expand icon** on the newly created column.
2. Uncheck **Select All Columns**.
3. Select only:

   * `Price Per Unit`
4. Click **OK**.

Now the price information from the Dimension Product table appears in the Fact Table.

The resulting column initially has a name similar to:

`Dimension Product.Price Per Unit`

This naming indicates:

* `Dimension Product` → source table
* `Price Per Unit` → source column

---

# 9. Removing the Old Price Per Unit Column

The fact table already had a `Price Per Unit` column, but it contained null values.

Now that a correct Price Per Unit column has been brought from the Dimension Product table, the old column is unnecessary.

### Steps

1. Right-click the old `Price Per Unit` column.
2. Select **Remove**.

The removal operation is recorded automatically under:

> **Applied Steps**

---

# 10. Renaming the New Price Column

The newly imported column has a long name such as:

`Dimension Product.Price Per Unit`

It is renamed to:

`Price Per Unit`

### Steps

1. Double-click the column name.
2. Enter:
   **Price Per Unit**
3. Press Enter.

The column already has an appropriate **whole number** data type, so no further change is required.

---

# 11. Creating Total Sales

The next missing/incorrect column is:

> **Total Sales**

The fact table contains:

* `Unit Sold`
* `Price Per Unit`

Therefore:

**Total Sales = Unit Sold × Price Per Unit**

### Example

If:

* Unit Sold = 10
* Price Per Unit = ₹50

Then:

**Total Sales = 10 × 50 = ₹500**

---

# 12. Creating a Custom Column in Power Query

Power Query allows us to create calculated columns using **Custom Column**.

### Steps

1. Go to the **Add Column** tab.
2. Select **Custom Column**.
3. Enter the new column name.

Because a `Total Sales` column already exists, the instructor temporarily uses an extra space in the name to avoid a duplicate-name issue.

4. Enter the formula:

```text
[Unit Sold] * [Price Per Unit]
```

5. Click **OK**.

Power Query checks the formula for syntax errors before creating the column.

---

# 13. Setting Total Sales Data Type

Both:

* Unit Sold
* Price Per Unit

are whole numbers.

Therefore, the resulting Total Sales should also be a **Whole Number**.

### Steps

1. Click the `ABC 123` data-type icon for the newly created Total Sales column.
2. Select **Whole Number**.

---

# 14. Removing the Old Total Sales Column

The original Total Sales column contained null values.

Since we have now calculated a new Total Sales column, the old one is no longer required.

### Steps

1. Right-click the old Total Sales column.
2. Select **Remove**.
3. Rename the newly created Total Sales column to:
   **Total Sales**
4. Move/reorder the column so it appears in the desired position.

The lecture places it after `Price Per Unit`.

---

# 15. Bringing Discount Percentage from Dimension Promotion

The next requirement is to populate:

> **Discount Percentage**

The discount percentage is available in the **Dimension Promotion** table.

The Fact Table contains:

`Promotion ID`

The Dimension Promotion table also contains:

`Promotion ID`

Therefore, we can again use **Merge Queries**.

---

# 16. Understanding Promotion IDs

Not every transaction has a valid Promotion ID.

The lecture explains that discounts were **not provided for every transaction**.

Valid promotion IDs include examples such as:

* PR001
* PR002
* PR003
* PR004
* PR005

However:

`0`

does not represent a valid promotion code.

Instead, `0` indicates:

> **No discount was given.**

This explains why only some rows can be matched with the Dimension Promotion table.

---

# 17. Merge Fact Table with Dimension Promotion

### Steps

1. Select the **Fact Table**.
2. Go to **Home**.
3. Click the dropdown associated with **Merge**.
4. Select **Merge Queries**.
5. Do **not** select Merge Queries as New.
6. Select `Promotion ID` from the Fact Table.
7. Select **Dimension Promotion** as the second table.
8. Select `Promotion ID` from Dimension Promotion.
9. Use a **Left Outer Join**.
10. Click **OK**.

---

# 18. Understanding the Match Count

Power Query reports:

> **720 of 3510 rows matched**

This is expected.

Why?

Because discounts were only given to some transactions.

Therefore:

* Total Fact Table rows = **3510**
* Matching promotion rows = **720**
* Remaining rows = transactions without discounts

This is an important practical example of why a left join can result in null values in the newly imported column.

---

# 19. Expanding the Promotion Table

After merging, a new nested column appears.

We only need the percentage information.

### Steps

1. Click the **Expand** icon.
2. Uncheck **Select All Columns**.
3. Select only:
   **Percentage**
4. Click **OK**.

The resulting column will have a name similar to:

`Dim Promotion.Percentage`

This indicates:

* `Dim Promotion` → source table
* `Percentage` → source column

---

# 20. Understanding Null Discount Percentages

The newly imported Percentage column contains:

* Valid percentage values such as:

  * 10
  * 20
  * 50
  * 70
* `null`

Here, `null` does **not** mean bad or missing data.

It has a business meaning:

> **No discount was given for that transaction.**

Therefore, instead of leaving it as null, it should be represented as:

**0**

---

# 21. Checking Column Quality

Before replacing null values, the instructor demonstrates Power Query's data profiling features.

### Steps

1. Go to the **View** tab.
2. Enable the relevant data-quality/distribution/profile options.

The column profile shows approximately:

* **21% valid values**
* **0% errors**
* **79% empty/null values**

This confirms that the majority of transactions did not have a discount.

### Important distinction

* **Valid values** → actual discount percentages
* **Errors** → problematic values
* **Empty/null values** → no discount information

---

# 22. Replacing Null with Zero

Since null means **no discount**, we can replace null with `0`.

### Steps

1. Right-click the Percentage column.
2. Select **Replace Values**.
3. Replace the null values with:
   `0`
4. Click **OK**.

After the replacement:

* Empty values = **0%**
* Errors = **0%**
* Valid values = **100%**

The column is now complete.

---

# 23. Removing the Old Discount Percentage Column

The original Fact Table already contained a Discount Percentage column, but it contained null values.

The new percentage column has been populated from Dimension Promotion and nulls have been converted to zero.

Therefore, the old column is no longer required.

### Steps

1. Select the old `Discount Percentage` column.
2. Press **Delete** or right-click → **Remove**.

---

# 24. Renaming the New Discount Percentage Column

The newly imported column is renamed for simplicity.

### Steps

1. Double-click the newly imported percentage column.
2. Rename it:

**Discount Percentage**

3. Move the column to the desired position.

The lecture also checks the data type and changes it to:

> **Whole Number**

because the percentage values are whole numbers.

---

# 25. Calculating Discount Value

Now that we have:

* Total Sales
* Discount Percentage

we can calculate the actual **discount amount/value**.

The formula is:

**Discount Value = Total Sales × Discount Percentage / 100**

### Example

Suppose:

* Total Sales = ₹1,000
* Discount Percentage = 20%

Then:

**Discount Value = 1000 × 20 / 100**

**Discount Value = ₹200**

So the customer receives a ₹200 discount.

---

# 26. Creating the Discount Column

### Steps

1. Go to **Add Column**.
2. Select **Custom Column**.
3. Enter a temporary name such as `Discount` because a column with a similar name already exists.
4. Create the formula:

```text
([Total Sales] * [Discount Percentage]) / 100
```

5. Click **OK**.

Power Query creates a new column containing the actual discount amount.

---

# 27. Setting Discount Data Type

Since the calculation can produce decimal values, the new Discount column is set to:

> **Decimal Number**

### Steps

1. Click the `ABC 123` icon.
2. Select **Decimal Number**.

---

# 28. Removing the Old Discount Value Column

The original Discount Value column contained null values.

Now we have calculated the actual discount value.

Therefore:

1. Right-click the old Discount Value column.
2. Select **Remove**.
3. Rename the newly created Discount column appropriately.
4. Move it to the desired position.

---

# 29. Calculating Net Sales

The final important calculated column is:

> **Net Sales**

Net sales are obtained after subtracting the discount amount from total sales.

### Formula

**Net Sales = Total Sales − Discount**

### Example

If:

* Total Sales = ₹1,000
* Discount = ₹200

Then:

**Net Sales = ₹1,000 − ₹200**

**Net Sales = ₹800**

---

# 30. Creating the Net Sales Column

### Steps

1. Go to **Add Column**.
2. Select **Custom Column**.
3. Give the new column a temporary name because a Net Sales column already exists.
4. Enter:

```text
[Total Sales] - [Discount]
```

5. Check that there are no syntax errors.
6. Click **OK**.

A new Net Sales column is created.

---

# 31. Setting Net Sales Data Type

Since Net Sales can contain decimal values:

1. Click the `ABC 123` icon.
2. Select **Decimal Number**.

---

# 32. Removing the Old Net Sales Column

The old Net Sales column contained null values.

The new Net Sales column has now been calculated.

### Steps

1. Right-click the old Net Sales column.
2. Select **Remove**.

At this point, the unnecessary null-containing columns have been replaced by meaningful calculated/imported values.

---

# 33. Final Transformation Logic

The complete transformation performed in the lecture can be summarized as:

### Step 1 — Price Per Unit

Bring `Price Per Unit` from **Dimension Product** using:

**Fact Table[Product ID] → Dimension Product[Product ID]**

---

### Step 2 — Total Sales

Calculate:

**Total Sales = Unit Sold × Price Per Unit**

---

### Step 3 — Discount Percentage

Bring `Percentage` from **Dimension Promotion** using:

**Fact Table[Promotion ID] → Dimension Promotion[Promotion ID]**

Then:

**null → 0**

because null means no discount.

---

### Step 4 — Discount Value

Calculate:

**Discount = Total Sales × Discount Percentage / 100**

---

### Step 5 — Net Sales

Calculate:

**Net Sales = Total Sales − Discount**

---

# 34. Why This Transformation Is Important

The original fact table contained incomplete columns.

Instead of manually entering values, Power Query uses:

* **Dimension tables**
* **Merge operations**
* **Custom calculations**
* **Null replacement**

to create a clean dataset.

The final data is now much more suitable for:

* Report creation
* Visualizations
* Data analysis
* Aggregations
* Measures
* Business reporting

This is an important principle:

> **Transform and clean the data before using it for reporting.**

---

# 35. Applied Steps

Every transformation performed in Power Query is automatically recorded under:

> **Applied Steps**

For example, the steps may include operations such as:

1. Merge Queries
2. Expanded merged column
3. Removed column
4. Added custom column
5. Changed data type
6. Replaced values
7. Renamed column
8. Reordered columns

This is one of the major advantages of Power Query.

You don't have to manually repeat every transformation each time the data is refreshed. Power Query can execute the recorded transformation steps again.

---

# 36. Close & Apply

Once all transformations are complete, the changes need to be applied to the Power BI model.

Under the **Home** tab, the instructor opens the dropdown associated with **Close & Apply**.

Three options are discussed conceptually:

### 1. Close

Use this when you want to:

* Leave Power Query Editor
* Return to Power BI Desktop
* Not apply the current changes

---

### 2. Apply

Use this when you want to:

* Apply the changes
* Remain inside Power Query Editor

This is useful if you want to continue working in Power Query after applying the transformations.

---

### 3. Close & Apply

Use this when you want to:

* Apply all transformations
* Load the transformed data into Power BI
* Return to the Power BI Desktop Report View

### In this lecture

The instructor chooses:

> **Close & Apply**

because the transformations are complete and the intention is to return to the Report View.

---

# 37. Data Loading After Close & Apply

After clicking **Close & Apply**, Power BI may take some time to:

1. Apply the transformations.
2. Process the data.
3. Load the transformed data.
4. Update the model.

Once complete, the transformed table becomes available in Power BI Desktop.

---

# 38. Returning to Power Query Editor

If you later want to make additional transformations, you can return to Power Query Editor.

### Steps

From Power BI Desktop:

**Home → Transform Data**

This opens Power Query Editor again.

The previously created transformations remain available under **Applied Steps**.

---

# 39. Returning to Report View

After completing the transformations, the instructor returns to the **Report View**.

The Report View is where actual Power BI reports are designed.

---

# 40. Report Design Area / Canvas

The large blank area in Report View is called the:

* **Report Design Area**
* or **Canvas**

This is the area where you build your report.

You create reports by adding different **visuals** to this canvas.

Examples of visuals that can eventually be added include:

* Tables
* Charts
* Cards
* Slicers
* Graphs
* Other Power BI visualizations

The lecture states that creating visuals and deeper data modeling will be covered in upcoming sessions.

---

# 41. Complete Workflow Learned in This Lecture

The overall Power BI workflow demonstrated here is:

```text
Raw Data
   ↓
Power Query Editor
   ↓
Identify Null / Missing Values
   ↓
Find Required Data in Dimension Tables
   ↓
Merge Queries
   ↓
Left Outer Join
   ↓
Expand Required Columns
   ↓
Replace Null Values Where Appropriate
   ↓
Create Custom Columns
   ↓
Set Correct Data Types
   ↓
Remove Old/Unnecessary Columns
   ↓
Rename/Reorder Columns
   ↓
Close & Apply
   ↓
Power BI Data Model
   ↓
Report View
   ↓
Create Visuals
```

---

# 42. Important Concepts to Remember

### Merge Queries

Used to bring information from another table into the current table.

### Merge Queries as New

Creates a separate query from the merge instead of modifying the existing query.

### Left Outer Join

Keeps **all records from the left/first table** and only matching records from the right/second table.

### Expand

Used to extract specific columns from the nested table created by a merge.

### Null

Represents the absence of a value.

However, **null does not always mean an error**. In this example, a null discount percentage means:

> No discount was given.

### Replace Values

Used to replace unwanted/missing values with another value, such as:

`null → 0`

### Custom Column

Used to create a new calculated column using Power Query formulas.

### Applied Steps

Records every transformation performed in Power Query.

### Close & Apply

Applies Power Query transformations to the Power BI model and returns to Power BI Desktop.

### Report Canvas

The design area where visuals are placed to build the report.

---

# 43. Key Formulas from the Lecture

These are the most important calculations to remember:

### Price Per Unit

Obtained through merge:

```text
Fact Table ← Dimension Product
using Product ID
```

### Total Sales

```text
Total Sales = Unit Sold × Price Per Unit
```

### Discount Percentage

Obtained through merge:

```text
Fact Table ← Dimension Promotion
using Promotion ID
```

Then:

```text
Null Discount % = 0
```

### Discount Value

```text
Discount = (Total Sales × Discount Percentage) / 100
```

### Net Sales

```text
Net Sales = Total Sales − Discount
```

---

# 44. Practical Power BI Steps — Quick Revision

If you need to reproduce the entire practical later:

1. Open **Power Query Editor**.
2. Select the **Fact Table**.
3. **Home → Merge Queries**.
4. Select `Product ID` in Fact Table.
5. Select Dimension Product.
6. Select `Product ID` there.
7. Choose **Left Outer Join**.
8. Click **OK**.
9. Expand the merged column.
10. Select only `Price Per Unit`.
11. Remove the old Price Per Unit column.
12. Rename the new column to `Price Per Unit`.
13. **Add Column → Custom Column**.
14. Calculate:
    `Unit Sold × Price Per Unit`
15. Set Total Sales to **Whole Number**.
16. Remove the old Total Sales column.
17. Merge Fact Table with **Dimension Promotion** using `Promotion ID`.
18. Choose **Left Outer Join**.
19. Expand only `Percentage`.
20. Replace `null` with `0`.
21. Remove the old Discount Percentage column.
22. Rename the imported column to `Discount Percentage`.
23. Set it to **Whole Number**.
24. Create a Custom Column:
    `(Total Sales × Discount Percentage) / 100`
25. Set Discount to **Decimal Number**.
26. Remove the old Discount Value column.
27. Create another Custom Column:
    `Total Sales − Discount`
28. Set Net Sales to **Decimal Number**.
29. Remove the old Net Sales column.
30. Review **Applied Steps**.
31. Select **Home → Close & Apply**.
32. Wait for Power BI to load/process the transformed data.
33. Return to **Report View**.
34. Use the **Report Canvas** to begin creating visuals.

---

## Final Takeaway

This lecture demonstrates a very common real-world Power BI data-preparation workflow:

**Use dimension tables to fill missing fact-table information → merge using keys → expand required columns → replace business-meaningful nulls → calculate derived values → remove obsolete columns → apply transformations → build reports from the cleaned dataset.**

The most important business calculation chain from this session is:

**Unit Sold + Price Per Unit → Total Sales → Discount Percentage → Discount Value → Net Sales**

This transformed fact table is now in a much better state to be consumed by the Power BI reporting layer.
