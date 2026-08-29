# Power BI End-to-End Project — Electro Hub

## Lecture 3: Data Profiling, Data Types & Data Transformation

This lecture focuses on the **next stage after importing the Electro Hub dataset**: understanding, profiling, cleaning, and structuring the data so that it can be used reliably for reporting.

The central idea is:

> **Before building visuals and reports, understand the characteristics and quality of every column in every table.** 

---

# 1. Purpose of This Lecture

The objective is to further:

* Prepare the data
* Clean the data
* Structure the data
* Understand the characteristics of each field
* Check data quality
* Check data types
* Identify primary keys
* Perform required transformations

The ultimate goal is to make the dataset suitable for **reporting purposes**. 

---

# 2. Data Profiling in Power Query

The instructor starts by using the **View** tab in Power Query Editor.

### Steps

1. Open **Power Query Editor**.
2. Go to the **View** tab.
3. Enable the following three options:

   * **Column Distribution**
   * **Column Quality**
   * **Column Profile**

These options provide information about the quality and characteristics of the data.

---

# 3. Column Distribution

Enable:

**View → Column Distribution**

Once enabled, Power Query displays information such as:

* Distinct count
* Unique count

These help you understand the values contained in a column. 

---

## 3.1 Distinct Count

**Distinct count** tells you the number of different values appearing in a column.

For example:

| Customer ID |
| ----------- |
| C001        |
| C002        |
| C003        |
| C001        |

There are four rows, but only three different values:

**Distinct Count = 3**

---

## 3.2 Unique Count

**Unique count** tells you how many values occur **only once** in the column. 

For example:

| Customer ID |
| ----------- |
| C001        |
| C002        |
| C003        |
| C001        |

* C001 occurs twice
* C002 occurs once
* C003 occurs once

Therefore:

**Unique Count = 2**

---

# 4. Identifying a Primary Key

Column Distribution is particularly useful when identifying potential **primary keys**.

When multiple tables need to be connected through relationships, you need to identify the appropriate key columns.

For a column to be a suitable primary key, it should:

1. Not contain null values.
2. Uniquely identify each row.
3. Have its **Distinct Count = Unique Count**. 

### Example: Customer ID

In the `dim customers` table, the **Customer ID** column has the same:

* Distinct count
* Unique count

and does not contain null values.

Therefore, it can be used as the **primary key** of the customer dimension table. 

---

# 5. Primary Key — Important Definition

A **primary key** is a column, or combination of columns, that can be used to **uniquely identify a row in a table**. 

For example:

```text
Customer ID
C001
C002
C003
```

If every customer has a different Customer ID, it can uniquely identify each customer.

Primary and foreign keys become particularly important when creating **relationships between multiple tables**.

---

# 6. Column Quality

Enable:

**View → Column Quality**

Column Quality provides information such as:

* Valid values
* Errors
* Empty values

The instructor enables this option to determine whether columns contain problematic data. 

### Example

A column might show:

* 100% Valid
* 0% Error
* 0% Empty

This indicates that the column is clean according to these checks.

---

# 7. Column Profile

Enable:

**View → Column Profile**

This provides more detailed statistics about the selected column, including information such as:

* Count
* Error count
* Empty count
* Distinct count
* Other column statistics

It provides a more detailed view of the selected field. 

---

# 8. Data Type Icon

Power Query displays a small icon next to each column indicating its **data type**.

For example, a column can be:

* Text
* Whole Number
* Decimal Number
* Date
* etc.

You should inspect this for **every column**.

The instructor emphasizes that data types matter because incorrect data types can affect:

* Relationships
* Data modeling
* Calculations
* Reporting accuracy 

---

# 9. Important Data Profiling Setting — Entire Dataset

One of the most important practical steps in this lecture is changing the column profiling scope.

At the bottom of Power Query, you may see:

> **Column profiling based on top 1000 rows**

By default, Power Query may profile only the first **1,000 rows**.

### Change it to:

> **Column profiling based on entire data set**

### Steps

1. Go to the bottom of Power Query Editor.
2. Locate the column profiling option.
3. Change:
   **Top 1000 rows**
   → **Entire data set**



---

## Why is this important?

Suppose a fact table contains **3,510 rows**.

If profiling is based only on the first 1,000 rows, the statistics you see may not represent the complete dataset.

The instructor demonstrates this later:

* Top 1,000 rows → **Count = 1,000**
* Entire dataset → **Count = 3,510**



### Important rule

> **Always select "Column profiling based on entire data set" when analyzing the dataset.**

---

# 10. Customer Dimension Table — `dim customers`

The instructor now examines the customer dimension table column by column.

---

## 10.1 Customer ID

Customer ID is used to create relationships between:

* `dim customers`
* Fact Table

Since it is used as a key and no mathematical operations will be performed on it, the instructor wants it to be stored as **Text**, not as a number. 

### Change Customer ID to Text

1. Select **Customer ID**.
2. Click the data type icon.
3. Select **Text**.
4. Choose **Replace Current**.



The column contains valid values with no errors or empty values. 

---

## 10.2 Customer Name

Customer Name is already:

**Text**

This is appropriate because customer names are textual values. 

---

## 10.3 City

City is also:

**Text**

This is appropriate.

No null/empty/error problems are observed. 

---

## 10.4 State

The State column contains state names.

Its data type is:

**Text**

This is appropriate. 

---

## 10.5 PIN Code

PIN Code is stored as a number.

The instructor considers this acceptable in the context of this dataset. 

---

## 10.6 Email ID

Email ID is stored as:

**Text**

This is appropriate. 

---

## 10.7 Phone Number

The Phone Number column is also considered acceptable in its current data type according to the lecture. 

---

# 11. General Rule — Check Every Column

A major takeaway is:

> **Check the data type and data quality of every column in every table.** 

Why?

Because incorrect data types can eventually affect:

**Data → Relationships → Data Model → Calculations → Report Accuracy**

Understanding the data properly makes analysis easier. 

---

# 12. Product Dimension Table — `dim product`

Next, the instructor moves to:

**dim product**

The same profiling process is followed.

### Steps

1. Select `dim product`.
2. Enable **Column Profile**.
3. Change profiling to **Entire Data Set**.

The table contains **30 products**. 

---

## 12.1 Product ID

Product ID is:

**Text**

It is suitable because product IDs are identifiers rather than values on which mathematical operations are required.

The Product ID column also has:

**Distinct Count = Unique Count**

and does not contain null values.

Therefore, it can serve as the **primary key** for the product table. 

---

## 12.2 Product Name

Product Name is:

**Text**

This is appropriate. 

---

## 12.3 Product Line

Product Line is:

**Text**

This is also appropriate. 

Examples from the previous lecture include product categories such as electronics, footwear, clothing, etc.

---

## 12.4 Price

Price is represented in **Indian Rupees**.

Its data type is:

**Number**

This is appropriate because price is a numerical value. 

The table has:

* 30 records
* Valid values
* No empty values
* No errors

according to the profiling shown in the lecture. 

---

# 13. Promotion Dimension Table — `dim promotion`

Next, the instructor moves to the promotion table.

This table contains information about the promotions offered by the store. 

The columns include:

* Promotion ID
* Promotion Name
* Advertisement Type
* Coupon Code
* Price Reduction Type

---

# 14. Issue: Headers Are Not Correctly Configured

The instructor notices that the **column names are present in the first row of the data** rather than being recognized as actual column headers. 

This needs to be corrected.

---

# 15. Promote First Row to Headers

Power Query provides an option:

> **Use First Row as Headers**

### Steps

1. Go to the **Home** tab
   **OR**
2. Go to the **Transform** tab.
3. Select:
   **Use First Row as Headers**

After performing this operation, the correct column names appear.

The columns become:

* Promotion ID
* Promotion Name
* Advertisement Type
* Coupon Code
* Price Reduction Type



---

# 16. Promotion ID as Primary Key

The Promotion ID column has:

* Same Distinct Count and Unique Count
* No null values

Therefore, it can be used as the **primary key** for the promotion table. 

The data type is also changed/kept as:

**Text**

---

# 17. Promotion Name

Promotion Name contains textual values.

Therefore:

**Data Type = Text**

This is appropriate. 

---

# 18. Advertisement Type

Advertisement Type contains textual values.

Therefore:

**Data Type = Text**

This is appropriate. 

---

# 19. Coupon Code

Coupon Code is also:

**Text**

Different coupon codes are associated with different promotions. 

---

# 20. Price Reduction Type — Important Data Transformation

The **Price Reduction Type** column contains values such as:

* `20% off`
* `10% off`
* `Buy One, Get One Free`
* `Flash Sale`
* `Clearance Sale`

The important issue is that these are **textual descriptions**, not numerical percentage values. 

---

# 21. Why a Numerical Percentage Column Is Needed

Suppose we want to use the discount percentage in calculations or analysis.

A value like:

> `20% off`

is textual.

We therefore need a separate column containing the corresponding numerical value:

> `20`

Similarly:

* `10% off` → `10`
* `Buy One, Get One Free` → `50`
* etc.

The purpose is to create a **numerical percentage column** that can be used for analysis. 

---

# 22. Creating a Conditional Column

Power Query's **Conditional Column** feature is used to create this new numerical column.

### Steps

1. Select **Add Column**.
2. Select **Conditional Column**.
3. Enter the name of the new column.
4. Define conditions based on Promotion ID.
5. Assign the corresponding numerical discount value.

The new column is named:

> **Percentage**



---

# 23. Conditional Column Rules

The instructor creates conditions based on the Promotion ID.

### Rule 1

If:

**Promotion ID = P001**

Then:

**Percentage = 20**

because the promotion provides 20% off.

---

### Rule 2

If:

**Promotion ID = P002**

Then:

**Percentage = 10**

because the promotion provides 10% off.

---

### Rule 3

If:

**Promotion ID = P003**

Then the promotion is:

**Buy One, Get One Free**

The instructor treats this as equivalent to a:

**50% discount**

### Reasoning

Suppose one item costs ₹100.

Under Buy One, Get One Free:

* Pay ₹100
* Receive 2 items

Effectively, each item costs ₹50.

Therefore, it is treated as a **50% discount** for this analysis. 

---

### Rule 4

If:

**Promotion ID = P004**

Then it is a:

**Flash Sale**

The assigned value is:

**50%**



---

### Else Condition

The remaining promotion is:

**P005 — Clearance Sale**

The discount is:

**70%**

Rather than creating another explicit condition, the instructor uses the **Else** clause.

Therefore:

**Else → 70**



---

# 24. Complete Conditional Column Logic

The resulting logic is conceptually:

| Promotion ID | Promotion            | Percentage |
| ------------ | -------------------- | ---------: |
| P001         | 20% Off              |         20 |
| P002         | 10% Off              |         10 |
| P003         | Buy One Get One Free |         50 |
| P004         | Flash Sale           |         50 |
| P005         | Clearance Sale       |         70 |

The exact textual promotion descriptions are represented in the source data, while the new **Percentage** column contains numerical values.

---

# 25. Finish Creating the Conditional Column

After defining the conditions:

### Step

Click:

**OK**

Power Query creates the new **Percentage** column. 

---

# 26. Change Percentage Data Type

After creating the column, Power Query initially shows its data type as:

**ABC 123**

The instructor identifies it as an integer/number-type column and explicitly changes it to:

**Whole Number**

### Steps

1. Select the **Percentage** column.
2. Click its **data type icon**.
3. Select **Whole Number**.



---

# 27. Fact Table — Final Table

The instructor now moves to the last table:

> **Fact Table**

This is the transactional table that will be heavily used in the report.

The instructor again checks the profiling settings.

### Steps

1. Select the Fact Table.
2. Go to **View**.
3. Check/enable the required profiling options.
4. Select:
   **Column profiling based on entire data set**



---

# 28. Fact Table — Important Row Count Observation

Initially, when profiling is based on:

**Top 1000 rows**

the count displayed is:

**1,000**

After changing it to:

**Entire Data Set**

the count becomes:

**3,510**



### Why?

Because Power Query was previously displaying statistics based only on the first 1,000 rows.

The complete fact table contains:

> **3,510 records**

This demonstrates why the profiling setting must be changed to the entire dataset before analyzing the data.

---

# 29. Fact Table — Date Column

The first column is:

**Date**

Its data type is:

**Date**

The instructor considers this appropriate.

The column has:

* 100% valid values
* 0% errors
* No empty values



---

# 30. Fact Table — Customer ID

Customer ID appears again in the Fact Table.

It will be used to establish a relationship with:

**dim customers → Fact Table**

Therefore, it should be:

**Text**

even though the values themselves may look numeric.

No mathematical operations will be performed on Customer ID.

### Steps

1. Select Customer ID.
2. Click the data type icon.
3. Select **Text**.
4. Choose **Replace Current**.



The instructor notes that the detailed reasoning for this will be discussed later during **data modeling and reporting**.

---

# 31. Fact Table — Promotion ID

Promotion ID also needs to be converted to:

**Text**

### Steps

1. Select Promotion ID.
2. Click the data type icon.
3. Select **Text**.



This will eventually be relevant when establishing relationships with the promotion dimension table.

---

# 32. Fact Table — Product ID

Product ID already contains text values.

Therefore, the instructor considers its current data type appropriate:

**Text**

No change is required. 

---

# 33. Fact Table — Unit Sold

The instructor examines the **Unit Sold** column.

The column represents information about the number of units of an article sold.

The instructor opens the column's dropdown and selects:

**Load More**

This allows additional values from the column to be viewed. 

The lecture shows values such as:

* 1
* 2
* 3
* etc.

The instructor then cancels the dropdown.

---

# 34. Empty Columns in the Fact Table

The instructor discovers a major data-quality issue in the Fact Table.

Several columns are completely empty.

For example:

### Price Per Unit

Column Quality shows:

* **0% valid**
* **0% errors**
* **100% empty**

### Total Sales

Column Quality shows:

* **0% valid**
* **0% errors**
* **100% empty**

Other columns also show:

> **100% empty values**



---

# 35. Why the Empty Columns Are a Problem

These columns are important because they will be used in the project's analysis.

Therefore, leaving them empty would make it impossible to perform the required calculations/reporting correctly.

The instructor states that a way must be found to **populate these columns**. 

This transformation is **not completed in this lecture**.

It is explicitly left for the next session.

---

# 36. What Is Completed in This Lecture?

By the end of the lecture, the following has been done:

### Data Profiling

* Column Distribution enabled
* Column Quality enabled
* Column Profile enabled
* Profiling changed to entire dataset

### Customer Table

* Customer ID reviewed
* Customer ID changed to Text
* Other customer columns reviewed

### Product Table

* Product ID reviewed as potential primary key
* Product Name reviewed
* Product Line reviewed
* Price reviewed

### Promotion Table

* First row promoted to headers
* Promotion ID reviewed as primary key
* Data types reviewed
* Conditional Percentage column created
* Percentage converted to Whole Number

### Fact Table

* Entire dataset profiling enabled
* 3,510 records identified
* Date validated
* Customer ID converted to Text
* Promotion ID converted to Text
* Product ID validated
* Empty columns identified

---

# 37. Important Data Modeling Concepts Introduced

This lecture also prepares you for the upcoming **data modeling** section.

## Primary Key

A field that uniquely identifies a row in a table.

Potential primary keys identified:

* Customer ID → `dim customers`
* Product ID → `dim product`
* Promotion ID → `dim promotion`

---

## Foreign Key

Although the lecture does not explicitly perform the relationship creation yet, the Fact Table contains corresponding identifier fields such as:

* Customer ID
* Product ID
* Promotion ID

These will be relevant for connecting the Fact Table with the corresponding dimension tables.

The instructor emphasizes that primary/foreign keys are important when creating relationships between tables. 

---

# 38. Why Correct Data Types Matter

A particularly important lesson is:

> **Don't choose a data type simply because the values look like numbers.**

For example:

`Customer ID = 1001`

may look numerical, but if it is an identifier and you won't perform arithmetic on it, it is more appropriate in this project to treat it as **Text**.

This is important because the same identifier needs to have compatible data types when used to establish relationships between tables.

The instructor specifically connects data types with future **data modeling and report accuracy**. 

---

# 39. Important Rules to Remember

### Rule 1 — Profile the entire dataset

Do not rely only on the default 1,000-row preview.

**View → Column Profiling → Entire Data Set**

---

### Rule 2 — Check every column

For every table, examine:

* Data type
* Valid values
* Errors
* Empty values
* Distinct values
* Unique values

---

### Rule 3 — Identify potential primary keys

A potential primary key should:

* Uniquely identify records
* Have no null values
* Have distinct and unique counts matching

---

### Rule 4 — Use appropriate data types

Identifiers such as:

* Customer ID
* Product ID
* Promotion ID

should be treated as **Text** when they are identifiers rather than quantities.

---

### Rule 5 — Transform text into numerical values when necessary

If a value needs to participate in numerical analysis, create an appropriate numerical column.

Example:

`20% Off` → `20`

---

### Rule 6 — Fix completely empty fields

If columns required for analysis contain:

**100% empty values**

they need to be investigated and populated before report creation.

---

# 40. End-to-End Flow So Far

The project workflow now looks like:

**Excel Dataset**

↓

**Load into Power BI**

↓

**Open Power Query**

↓

**Profile the Data**

↓

**Check Column Quality**

↓

**Check Data Types**

↓

**Identify Primary Keys**

↓

**Fix Headers**

↓

**Create/Transform Columns**

↓

**Identify Missing/Empty Data**

↓

**Prepare Data for Modeling**

↓

**Data Model**

↓

**Report & Visualizations**

The current lecture gets us through the **data profiling and initial transformation stage**.

---

# 41. What Remains for the Next Lecture?

The major unresolved issue is the Fact Table's empty columns.

Several important fields currently contain:

**100% empty values**

The instructor says that these need to be populated because they are required for analysis. 

The next lecture will therefore continue with:

* More data transformation
* Populating the required fields
* Further preparing the data
* Eventually loading the transformed data back into the Power BI model 

---

# 42. Quick Revision Sheet

### Power Query profiling options

| Option                  | Purpose                                           |
| ----------------------- | ------------------------------------------------- |
| **Column Distribution** | Shows distinct and unique values                  |
| **Column Quality**      | Shows valid, error and empty values               |
| **Column Profile**      | Shows detailed statistics for the selected column |

### Key setting

**Column profiling based on entire data set**

instead of:

**Top 1000 rows**

### Primary keys identified

| Table           | Potential Primary Key |
| --------------- | --------------------- |
| `dim customers` | Customer ID           |
| `dim product`   | Product ID            |
| `dim promotion` | Promotion ID          |

### Key transformations

| Table           | Transformation                        |
| --------------- | ------------------------------------- |
| `dim customers` | Customer ID → Text                    |
| `dim promotion` | First row → Headers                   |
| `dim promotion` | Created Percentage conditional column |
| `dim promotion` | Percentage → Whole Number             |
| Fact Table      | Customer ID → Text                    |
| Fact Table      | Promotion ID → Text                   |

### Important Fact Table finding

**Total records = 3,510**

Several important columns are currently **100% empty** and need to be populated in the next lecture.

---

## Core takeaway

The most important lesson from this lecture is that **Power BI report development begins with data preparation, not visualization**.

Before building the Electro Hub dashboard, you need to understand every table and column, verify data quality, select correct data types, identify keys, fix structural issues, and resolve missing data. Only after the data is properly prepared should it be used for data modeling and report creation.
