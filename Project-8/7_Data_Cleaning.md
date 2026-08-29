# Power BI – Data Cleaning: Replacing NA Values in Original Price

## 1. Objective of the Session

The main objective of this session is to clean the **Original Price** column in Power Query.

The dataset contains two important columns:

* **Original Price**
* **Sales Price**

The problem is that some records have:

* `Original Price = NA`
* `Sales Price = valid number`

For these records, we want to calculate the missing Original Price using the Sales Price.

### Logic used

The lecture assumes:

> **Original Price should be 50% more than Sales Price.**

Therefore:

**Original Price = Sales Price × 1.5**

For example:

| Sales Price | Original Price |
| ----------: | -------------: |
|         100 |            150 |
|         200 |            300 |
|         500 |            750 |

The session also filters out records where the **Sales Price itself is NA**, because those records cannot be used to calculate the missing Original Price.

---

# 2. Remove Existing Filters

Before applying the required filtering, remove any existing filters from the relevant columns.

### Steps

1. Go to the **Power Query Editor**.
2. Remove the filters from:

   * **Original Price**
   * **Sales Price**
3. Click the drop-down arrow on each column.
4. Select **Clear Filter**.

This ensures that we are starting with the complete dataset before applying the required filter.

---

# 3. Filter Out NA Values from Sales Price

The first cleaning operation is to remove records where **Sales Price is NA**.

### Why?

We need a valid Sales Price to calculate the missing Original Price.

If:

> Sales Price = NA

then we cannot perform:

> Sales Price × 1.5

### Steps

1. Click the **drop-down arrow** on the **Sales Price** column.
2. Scroll down through the filter values.
3. Locate the **NA** value.
4. **Uncheck NA**.
5. Click **OK**.

Now the dataset contains only records where Sales Price has a valid value.

At this point, there can still be records where:

> Original Price = NA
> Sales Price = valid number

These are the records that we need to fix.

---

# 4. Create a Factor Column

To calculate the replacement value for Original Price, create a temporary/helper column called **Factor**.

The purpose of this column is to identify the records where Original Price is missing.

### Logic

If:

> Original Price = NA

then:

> Factor = 1.5

Otherwise:

> Factor = 0

The value `1.5` is used because the required Original Price is 50% greater than Sales Price.

---

## Steps to Create the Factor Column

1. Go to the **Add Column** tab at the top.
2. Click **Conditional Column**.
3. Name the new column:

**Factor**

4. Configure the condition:

**If**

* Column: `Original Price`
* Condition: `equals`
* Value: `NA`

**Then**

* `1.5`

**Else**

* `0`

5. Click **OK**.

Power Query will create a new column named **Factor**.

### Result

Conceptually, the data will look like:

| Original Price | Sales Price | Factor |
| -------------: | ----------: | -----: |
|             NA |         100 |    1.5 |
|            200 |         150 |      0 |
|             NA |         400 |    1.5 |
|            500 |         300 |      0 |

The Factor column therefore identifies exactly where the Original Price needs to be calculated.

---

# 5. Change Factor Data Type to Decimal Number

The Factor contains values such as `1.5`, so it should be stored as a decimal number.

### Steps

1. Click the data type icon (`ABC 123`) on the **Factor** column.
2. Select **Decimal Number**.

The Factor column now has the appropriate numeric data type.

---

# 6. Change Sales Price Data Type

Since the Sales Price column no longer contains NA values and will be used in mathematical calculations, change its data type to decimal number as well.

### Steps

1. Click the data type icon on the **Sales Price** column.
2. Select **Decimal Number**.

Now Sales Price can safely be used in arithmetic operations.

---

# 7. Create Sales Multiplied by Factor Column

Next, create another helper column.

This column will calculate:

> **Sales Price × Factor**

This is the value that will eventually replace the missing Original Price.

### Example

If:

* Sales Price = 100
* Factor = 1.5

then:

> 100 × 1.5 = 150

If Original Price is already available:

* Sales Price = 150
* Factor = 0

then:

> 150 × 0 = 0

Therefore, this column will contain:

* A calculated value for records where Original Price is NA.
* `0` for records where Original Price already exists.

---

## Steps to Create the Column

1. Go to the **Add Column** tab.
2. Select **Custom Column**.
3. Enter the name:

**Sales multiplied by factor**

4. In the formula box:

   * Select/insert **Sales Price**
   * Enter `*`
   * Select/insert **Factor**

The formula is conceptually:

```text
Sales Price * Factor
```

5. Make sure there are **no syntax errors**.
6. Click **OK**.

Power Query creates the new helper column.

---

# 8. Change the New Column to Decimal Number

Since the new column contains calculated numerical values:

1. Click the data type icon on **Sales multiplied by factor**.
2. Select **Decimal Number**.

---

# 9. Create the Final Mark Price Column

Now we have all the information needed to create the cleaned version of Original Price.

The final column will be called:

**Mark Price**

It can also be thought of as **List Price**.

### Required logic

If:

> Original Price = NA

then:

> Mark Price = Sales multiplied by factor

Otherwise:

> Mark Price = Original Price

In other words:

```text
If Original Price is NA
    → use Sales Price × 1.5
Else
    → use existing Original Price
```

This ensures that existing valid Original Price values are preserved while missing values are replaced.

---

# 10. Steps to Create Mark Price

1. Go to the **Add Column** tab.
2. Select **Conditional Column**.
3. Name the column:

**Mark Price**

4. Set the condition:

**If**

* Column: `Original Price`
* Condition: `equals`
* Value: `NA`

**Then**

* Select column: `Sales multiplied by factor`

**Else**

* Select column: `Original Price`

5. Click **OK**.

Power Query creates the new **Mark Price** column.

---

# 11. Change Mark Price Data Type

The newly created Mark Price column needs to be numeric.

### Steps

1. Click the `ABC 123` data type icon on **Mark Price**.
2. Select **Decimal Number**.

Now Mark Price can be used for mathematical operations such as:

* Average
* Sum
* Standard deviation
* Other numerical calculations

---

# 12. Why Mark Price Is Better Than Original Price

At this point, **Mark Price** acts as the cleaned/replacement version of **Original Price**.

It contains:

* The original Original Price wherever it was valid.
* A calculated value wherever Original Price was NA.

### Example

Before cleaning:

| Original Price | Sales Price |
| -------------: | ----------: |
|             NA |         100 |
|            250 |         200 |
|             NA |         400 |
|            600 |         500 |

After creating Mark Price:

| Original Price | Sales Price | Mark Price |
| -------------: | ----------: | ---------: |
|             NA |         100 |        150 |
|            250 |         200 |        250 |
|             NA |         400 |        600 |
|            600 |         500 |        600 |

Thus, Mark Price provides a complete numeric price column.

---

# 13. Validate the Mark Price Column

The lecture then checks whether the NA values have been successfully replaced.

### Steps

1. Click the drop-down arrow on the **Mark Price** column.
2. Look through the available filter values.
3. Verify that there are no `NA` values.

If no NA values appear, the replacement has worked successfully.

---

# 14. Apply the Power Query Changes

Once the transformation is complete, the changes need to be applied.

The lecture specifically demonstrates remaining in the **Power Query Editor** while applying the changes.

### Steps

1. Go to the **Home** tab.
2. Click the drop-down associated with **Close & Apply**.
3. Select **Apply**.

The transformations performed in Power Query are applied to the dataset while remaining in the Power Query workflow as demonstrated in the lecture.

---

# 15. Remove Unnecessary Helper Columns

The lecture emphasizes an important data-cleaning principle:

> **Do not keep unnecessary columns in the final dataset.**

We created temporary/helper columns only to construct Mark Price.

These include:

* Factor
* Sales multiplied by factor

The original Original Price column is also no longer required because Mark Price is now its cleaned replacement.

Keeping unnecessary columns increases the amount of data that Power BI needs to store and process.

Therefore, unnecessary columns should be removed, especially when working with real-world/large datasets.

---

# 16. Remove the Factor Column

### Steps

1. Select the **Factor** column.
2. Press the **Delete** key on the keyboard.

The temporary Factor column is removed.

---

# 17. Remove Sales Multiplied by Factor

### Steps

1. Select the **Sales multiplied by factor** column.
2. Remove/delete the column.

This was only a helper column used to calculate Mark Price.

It is no longer needed.

---

# 18. Remove Original Price

The original Original Price column is also no longer required because **Mark Price** now contains the cleaned values.

### Steps

1. Right-click the **Original Price** column.
2. Select **Remove**.

The dataset now contains the cleaned Mark Price column instead of the problematic Original Price column.

---

# 19. Final Dataset

After removing the unnecessary columns, the relevant final columns are:

| Column      | Data Type      | Purpose                   |
| ----------- | -------------- | ------------------------- |
| Sales Price | Decimal Number | Valid sales price         |
| Mark Price  | Decimal Number | Cleaned/replacement price |

The final data contains:

* **Sales Price** → Decimal Number
* **Mark Price** → Decimal Number
* No NA values in Mark Price
* No unnecessary helper columns

---

# 20. Apply the Final Changes

After deleting the unnecessary columns:

1. Click the **Home** tab.
2. Click **Apply**.
3. The final Power Query transformations are applied.

The dataset is now ready for further analysis and report creation.

---

# 21. Complete Transformation Logic

The entire process can be summarized as follows:

### Step 1 – Remove existing filters

Clear filters from:

* Original Price
* Sales Price

### Step 2 – Remove records where Sales Price is NA

Filter the Sales Price column and uncheck:

> NA

### Step 3 – Create Factor

```text
If Original Price = NA
    Factor = 1.5
Else
    Factor = 0
```

### Step 4 – Create helper calculation

```text
Sales multiplied by factor
    = Sales Price × Factor
```

### Step 5 – Create Mark Price

```text
If Original Price = NA
    Mark Price = Sales multiplied by factor
Else
    Mark Price = Original Price
```

### Step 6 – Change data types

Set:

* Sales Price → Decimal Number
* Factor → Decimal Number
* Sales multiplied by factor → Decimal Number
* Mark Price → Decimal Number

### Step 7 – Remove helper/unnecessary columns

Delete:

* Factor
* Sales multiplied by factor
* Original Price

### Step 8 – Keep the cleaned columns

Keep:

* Sales Price
* Mark Price

### Step 9 – Apply changes

Use:

**Home → Apply**

---

# 22. Important Concept: Why 1.5?

The lecture assumes that the Original/Marked Price should be **50% higher than the Sales Price**.

Mathematically:

```text
Original Price = Sales Price + 50% of Sales Price
```

Therefore:

```text
Original Price
= Sales Price + (Sales Price × 0.5)
= Sales Price × 1.5
```

For example:

```text
Sales Price = 800

Mark Price = 800 × 1.5
           = 1200
```

So the Factor is `1.5`.

---

# 23. Important Power Query/Data-Cleaning Lessons

### 1. Clean data before analysis

Data containing missing or invalid values can cause problems during analysis and visualization.

Cleaning should therefore be performed before creating the final report.

### 2. Use helper columns when necessary

Temporary columns such as:

* Factor
* Sales multiplied by factor

can make complex transformations easier to understand and implement.

### 3. Remove helper columns afterward

Once the required final column has been created, temporary columns should be removed.

This keeps the final dataset clean and reduces unnecessary data volume.

### 4. Use appropriate data types

Price columns should be numeric.

For this example, the lecture uses:

> **Decimal Number**

This allows calculations such as:

* Sum
* Average
* Standard deviation
* Other mathematical operations

### 5. Don't overwrite useful original data unnecessarily

Instead of directly modifying Original Price, the lecture creates **Mark Price** as a cleaned replacement.

After validating Mark Price, the original column can be removed.

### 6. Validate transformations

Always check the resulting column after a transformation.

In this case, the Mark Price filter was checked to ensure that NA values were no longer present.

---

# 24. Final Workflow at a Glance

```text
Original Dataset
       ↓
Clear existing filters
       ↓
Filter out Sales Price = NA
       ↓
Create Factor column
       ↓
Original Price = NA → Factor = 1.5
Otherwise → Factor = 0
       ↓
Create Sales × Factor
       ↓
Create Mark Price
       ↓
Original Price = NA
      → Sales × Factor
Otherwise
      → Original Price
       ↓
Change Mark Price to Decimal Number
       ↓
Validate that Mark Price has no NA
       ↓
Remove helper columns
       ↓
Remove Original Price
       ↓
Keep Sales Price + Mark Price
       ↓
Apply changes
       ↓
Clean dataset ready for reporting
```

## Key Takeaway

The important transformation from this session is:

> **Use Sales Price to calculate missing Original Price values, create a cleaned Mark Price column, validate it, and then remove the temporary/helper columns used during the transformation.**

This produces a clean numeric **Mark Price** column that can safely be used in the Power BI report for further calculations and visualizations.

