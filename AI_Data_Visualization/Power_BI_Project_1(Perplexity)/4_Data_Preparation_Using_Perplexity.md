# Power Query Editor — Understanding, Profiling & Cleaning the Data

## 1. Objective of the Session

The main objective of this session is to **understand the dataset more deeply using Power Query Editor** and identify whether there are any data-quality or data-cleaning issues.

The approach is:

```text
SQL Server Data
      ↓
Power BI
      ↓
Power Query Editor
      ↓
Understand / Profile Data
      ↓
Identify Data Issues
      ↓
Use Perplexity for Cleaning Suggestions
      ↓
Clean Data
      ↓
Close & Apply
      ↓
Power BI Data Model
```

The instructor also establishes an important workflow:

> If a data-cleaning problem is encountered, use Perplexity to get suggestions on how to solve it and then apply the appropriate solution in Power Query.

---

# 2. Open Power Query Editor

The instructor is already working in Power BI Desktop with the SQL Server data loaded.

To open Power Query Editor:

1. Go to Power BI Desktop.
2. Click:

```text
Home → Transform Data
```

3. Power Query Editor opens.

### Why Power Query?

Power Query is used for:

* Understanding data
* Data profiling
* Data cleaning
* Data transformation
* Handling missing values
* Changing data types
* Removing unwanted records
* Preparing data before it enters the Power BI data model

---

# 3. Column Profiling in Power Query

Once Power Query Editor opens, Power BI provides **Column Profiling** features.

These features help you understand the quality and structure of your dataset.

The important profiling features discussed are:

1. **Column Quality**
2. **Column Profile**
3. **Column Distribution**

These are available under the **View** tab.

---

# 4. Change Column Profiling from Top 1,000 Rows to Entire Dataset

By default, Power BI may perform column profiling based on:

> **Top 1,000 rows**

This means the statistics shown may be calculated using only the first 1,000 rows rather than the complete dataset.

Since the dataset contains more than 1,000 records, the instructor changes this setting.

### Steps

At the bottom of Power Query Editor:

1. Locate the profiling option that currently refers to the **top 1,000 rows**.
2. Change it to:

```text
Entire dataset
```

### Why?

Because the instructor wants the profiling statistics to represent the **whole dataset**, rather than just the first 1,000 rows.

---

# 5. Go to the View Tab

Next, the instructor clicks:

```text
View
```

The View tab contains the data profiling options.

Initially, the instructor discusses the three important options:

```text
Column quality
Column profile
Column distribution
```

These three features help analyze the dataset.

---

# 6. Column Quality

The instructor first enables:

```text
Column Quality
```

Column Quality provides information about the values in each column.

It tells you about:

* **Valid values**
* **Empty values**
* **Error values**

Conceptually:

```text
Column Quality
      │
      ├── Valid
      ├── Empty
      └── Error
```

This is extremely useful for identifying data-quality problems.

---

# 7. Why Column Quality Is Important

Suppose a column has:

```text
Valid → 97%
Empty → 2%
Error → 1%
```

This immediately tells you that the column needs investigation.

You can then determine:

* Why values are missing.
* Why errors exist.
* Whether missing values should be replaced.
* Whether erroneous records should be removed or corrected.

In the current dataset, most columns don't have major quality issues, but the `z` column does have missing values.

---

# 8. Column Profile

Next, the instructor enables:

```text
Column Profile
```

Column Profile provides **statistics about the selected column**.

An important point is:

> The statistics displayed depend on the column's data type.

This is demonstrated using different columns.

---

# 9. Column Profile for a Decimal Column

When the instructor selects a numerical/decimal column, Power Query displays statistics such as:

* Minimum
* Maximum
* Average
* Standard deviation
* Other numerical statistics

For example, a decimal column may show:

```text
Minimum
Maximum
Average
Standard deviation
```

These statistics help understand the distribution and range of numerical data.

---

# 10. Column Profile for a Text Column

The instructor then selects the `cut` column.

Since `cut` is a **text/categorical column**, the statistics displayed are different.

Instead of numerical statistics such as average and standard deviation, Power Query shows statistics relevant to text/categorical data, such as:

* Minimum
* Maximum
* Empty strings
* Other applicable text statistics

### Important concept

The available column-profile statistics depend on:

> **The data type of the column.**

For example:

```text
Decimal column
→ Min, Max, Average, Standard Deviation, etc.

Text column
→ Text/category-related statistics
```

---

# 11. Column Distribution

The third profiling feature is:

```text
Column Distribution
```

The instructor selects a column and enables Column Distribution.

This helps understand:

* **Distinct values**
* **Unique values**

These two concepts are important and are explained using the `cut` column.

---

# 12. Distinct Count

The `cut` column contains five different categories:

```text
Ideal
Premium
Very Good
Good
Fair
```

Therefore:

> **Distinct count = 5**

### Why?

Because there are five different values/categories present in the column.

Conceptually:

```text
cut
│
├── Ideal
├── Premium
├── Very Good
├── Good
└── Fair

Total distinct values = 5
```

---

# 13. Unique Count

The instructor then discusses **unique count**.

Unique count means:

> The number of values that occur **exactly once** in the column.

In this case:

> **Unique count = 0**

### Why?

Because none of the five cut categories appears only once.

Each category occurs multiple times.

Therefore:

```text
Distinct count = 5
Unique count   = 0
```

### Very Important Difference

| Concept      | Meaning                             |
| ------------ | ----------------------------------- |
| **Distinct** | Different values/categories present |
| **Unique**   | Values that occur exactly once      |

For the `cut` column:

```text
Distinct = 5
Unique = 0
```

---

# 14. Data Types Are Extremely Important

The instructor emphasizes that **data type is one of the most important things to check when working with any dataset**.

Before beginning a data-analysis project, you should verify that every column has the correct data type.

Examples:

```text
Text
Whole Number
Decimal Number
Date
Date/Time
Boolean
```

Incorrect data types can cause problems throughout the Power BI project.

---

# 15. Why Correct Data Types Matter

Incorrect data types can affect:

### 1. Data Model

The way Power BI stores and works with the data can be affected.

### 2. Reports

Visualizations may not behave as expected.

For example, a numerical field incorrectly stored as text may not work properly in numerical calculations.

### 3. Performance

Data types can influence how efficiently Power BI processes data.

### 4. Data Preparation

Transformations and calculations may fail or behave incorrectly if the data type is inappropriate.

### 5. DAX Calculations

DAX functions often expect particular types of data.

Therefore:

> **Always verify the data type of every important column before building the report.**

---

# 16. Check the `cut` Column

The instructor checks the `cut` column.

Its data type is:

```text
Text
```

This is appropriate because `cut` represents categorical values such as:

```text
Ideal
Premium
Very Good
Good
Fair
```

Therefore, no change is required.

---

# 17. Check the `carat` Column

The instructor checks the first numerical column, `carat`.

Its data type is:

```text
Decimal
```

This is appropriate because diamond carat values can contain decimal values.

For example:

```text
0.23
0.50
1.25
2.10
```

Therefore:

> The `carat` data type is correct.

---

# 18. Check the `color` Column

Next, the instructor checks the `color` column.

The instructor also checks its:

* Data type
* Valid values
* Empty values
* Error values

No problematic empty or error values are identified.

The column is categorical/textual, which is appropriate.

---

# 19. Check the `clarity` Column

The instructor then selects:

```text
clarity
```

This is another textual/categorical column.

The instructor confirms that the text data type is appropriate.

Therefore, no data-type correction is required for this column.

---

# 20. Check the `depth` Column

Next:

```text
depth
```

The `depth` column has:

```text
Decimal
```

as its data type.

This is appropriate because depth is a numerical measurement/percentage.

Therefore, no change is required.

---

# 21. Check the `table` Column

The instructor then checks:

```text
table
```

This column contains decimal values.

Therefore:

```text
Data Type = Decimal
```

This is appropriate.

The instructor also observes that there are:

> No NULL/blank values.

So the column doesn't require cleaning.

---

# 22. Check the `x` Column

The instructor checks the `x` column.

Its data type is:

```text
Decimal
```

This is appropriate because `x` represents a numerical diamond dimension.

No issue is identified with the data type.

---

# 23. Check the `y` Column

The instructor then checks:

```text
y
```

Its data type is also:

```text
Decimal
```

This is appropriate because `y` represents another numerical dimension.

---

# 24. Check the `z` Column

The instructor then checks:

```text
z
```

Its data type is:

```text
Decimal
```

The data type itself is correct.

However, a **data-quality issue** is discovered.

There are:

> **Empty/NULL values in the `z` column.**

The instructor observes that approximately:

> **2% of the values are empty.**

This is the main data-cleaning issue identified during the session.

---

# 25. Check the `price` Column

Finally, the instructor checks:

```text
price
```

The data type is:

```text
Decimal
```

This is appropriate because price is numerical.

The instructor also verifies that there are:

* No empty values
* No error values

Therefore, the `price` column does not require cleaning.

---

# 26. Dataset Data-Type Summary

The checks performed can be summarized as:

| Column    | Data Type | Observation                      |
| --------- | --------- | -------------------------------- |
| `carat`   | Decimal   | Correct                          |
| `cut`     | Text      | Correct                          |
| `color`   | Text      | Correct                          |
| `clarity` | Text      | Correct                          |
| `depth`   | Decimal   | Correct                          |
| `table`   | Decimal   | Correct                          |
| `x`       | Decimal   | Correct                          |
| `y`       | Decimal   | Correct                          |
| `z`       | Decimal   | Correct type, but missing values |
| `price`   | Decimal   | Correct                          |

The main issue discovered:

```text
z → approximately 2% empty/NULL values
```

---

# 27. Investigate the NULL Values in `z`

The instructor now wants to see exactly which records contain missing values in `z`.

Click the dropdown/filter button for the:

```text
z
```

column.

A list of available values appears.

The instructor:

1. Clicks **Select All** to clear/select appropriately.
2. Selects:

```text
null
```

3. Clicks:

```text
OK
```

Now Power Query displays only the rows where `z` is NULL.

---

# 28. Number of Records with NULL `z`

After filtering, the instructor uses the column profiling information to determine the number of affected records.

The result is:

> **855 records have NULL values in the `z` column.**

So:

```text
Total dataset = 53,940 records
NULL z values = 855 records
```

This corresponds to roughly **1.6%**, which the lecture rounds/discusses as approximately **2%**.

---

# 29. Why Does `z` Matter?

Earlier, the dataset was understood using Perplexity.

The `z` column represents the **height/depth dimension of the diamond**.

Therefore, missing `z` values mean that the height dimension isn't available for those records.

This needs to be considered before creating the final Power BI report.

---

# 30. Ask Perplexity How to Clean the NULL Values

Rather than arbitrarily changing the data, the instructor asks Perplexity for a possible solution.

The prompt is essentially:

> In my dataset, there is a column named `z` which contains NULL values. How may I clean this data?

Perplexity suggests using **Power Query's Replace Values functionality**.

---

# 31. Suggested Solution — Replace NULL with Zero

Perplexity suggests that the NULL values can be replaced with an appropriate value.

One possible choice is:

```text
NULL → 0
```

The reasoning given in the lecture is:

> If missing height values are to be treated as zero, then zero can be used as the replacement value.

The instructor decides to follow this approach for the current project.

### Important

Replacing NULL with zero is a **business/data interpretation decision**, not a universal rule.

In a real project, you should first determine whether zero is genuinely meaningful for the field. Here, the instructor chooses it as the cleaning approach for this exercise.

---

# 32. Remove the Temporary Filter Step

Before replacing the NULL values, the instructor needs to remove the temporary filtering step that was used only to inspect the NULL records.

On the right-hand side, Power Query has:

```text
Applied Steps
```

The filtering operation appears there.

The instructor:

1. Finds the step where the rows were filtered to show NULL values.
2. Deletes that step.

### Why?

The filter was only used for **investigation**.

If it remained, Power Query would permanently filter the dataset down to only the records with NULL `z` values.

That is not what we want.

We want to modify the NULL values while retaining **all records**.

---

# 33. Replace NULL Values in `z`

Now select the `z` column.

Go to:

```text id="x7c9rj"
Transform
```

Under the Transform tab, locate:

```text id="h01v0m"
Replace Values
```

Click:

```text
Replace Values
```

The replacement dialog appears.

---

# 34. Configure Replace Values

The instructor wants:

```text
Find value → null
Replace with → 0
```

So the transformation is:

```text id="z08x93"
NULL
 ↓
0
```

Then click:

```text id="9v0c2n"
OK
```

Power Query processes the transformation.

It may take some time depending on the dataset.

---

# 35. Verify That NULL Values Are Gone

After the replacement completes, inspect the `z` column again.

The instructor confirms:

> There are no longer empty/NULL values in the `z` column.

Therefore:

```text
Before:
z → 855 NULL values

After:
z → NULL values replaced with 0
```

The data-cleaning transformation has been successfully performed.

---

# 36. Close & Apply

An extremely important final step is to **apply the changes**.

The changes made inside Power Query do not automatically become part of the Power BI model until they are applied.

Go to:

```text
Home → Close & Apply
```

Click:

```text
Close & Apply
```

---

# 37. Why "Close & Apply" Is Important

The instructor explicitly emphasizes this.

If you simply make transformations in Power Query and don't apply them, those transformations won't be applied to the Power BI model.

The correct workflow is:

```text
Make transformation
       ↓
Verify transformation
       ↓
Close & Apply
       ↓
Power BI applies the changes
       ↓
Updated data loaded into model
```

---

# 38. Return to Power BI Desktop

After clicking **Close & Apply**, Power BI processes the changes.

The instructor waits while the data is loaded into the model.

Once the process finishes, Power BI returns to the report environment.

The cleaned data is now available for the upcoming report-building stage.

---

# 39. Complete Data-Understanding Workflow

The entire session can be remembered as:

```text
Open Power BI
      ↓
Transform Data
      ↓
Power Query Editor
      ↓
Change profiling:
Top 1000 → Entire Dataset
      ↓
View Tab
      ↓
Column Quality
      ↓
Column Profile
      ↓
Column Distribution
      ↓
Check data types
      ↓
Check valid / empty / error values
      ↓
Identify NULLs in z
      ↓
Filter z = NULL for investigation
      ↓
Find 855 affected records
      ↓
Ask Perplexity for cleaning approach
      ↓
Remove temporary filter step
      ↓
Select z
      ↓
Transform → Replace Values
      ↓
NULL → 0
      ↓
Verify NULLs are gone
      ↓
Home → Close & Apply
      ↓
Load cleaned data into Power BI Model
```

---

# 40. Three Power Query Profiling Features — Quick Comparison

| Feature                 | What it tells you                        |
| ----------------------- | ---------------------------------------- |
| **Column Quality**      | Valid, empty and error values            |
| **Column Profile**      | Statistics for the selected column       |
| **Column Distribution** | Distribution, distinct and unique values |

### Easy way to remember

```text
Quality      → Is the data good?
Profile      → What are the statistics?
Distribution → How are the values distributed?
```

---

# 41. Distinct vs. Unique — Important Interview Concept

This concept is worth remembering for data-analysis interviews.

Suppose a column contains:

```text
A
A
B
B
C
C
```

Then:

```text
Distinct values = 3
```

because the different values are:

```text
A, B, C
```

But:

```text
Unique values = 0
```

because no value occurs exactly once.

If the column were:

```text
A
A
B
C
C
```

then:

```text
Distinct = 3
Unique = 1
```

because `B` occurs exactly once.

---

# 42. Important Data-Cleaning Lesson

The instructor demonstrates a very common real-world data-cleaning workflow:

```text
Detect
  ↓
Investigate
  ↓
Understand
  ↓
Decide
  ↓
Transform
  ↓
Validate
  ↓
Apply
```

For the `z` column:

```text
Detect:
NULL values

↓

Investigate:
Filter NULL values

↓

Quantify:
855 records

↓

Understand:
z = diamond height

↓

Decide:
Replace NULL with 0

↓

Transform:
Replace Values

↓

Validate:
No NULL values remain

↓

Apply:
Close & Apply
```

This is a very useful pattern to follow in Power Query projects.

---

# 43. Role of Perplexity in Data Cleaning

The instructor uses Perplexity specifically when a data-cleaning issue appears.

The workflow is:

```text
Power Query identifies issue
            ↓
Describe issue to Perplexity
            ↓
Get possible solutions
            ↓
Evaluate suggestions
            ↓
Implement appropriate solution
```

Again, the AI suggestion should be evaluated before applying it.

---

# 44. Key Takeaways

* **Power Query Editor** is used to understand and clean data before it is used in Power BI reporting.
* Open it using:

```text
Home → Transform Data
```

* Change profiling from **Top 1,000 rows** to **Entire dataset** when you want statistics based on all available records.
* The three important profiling tools are:

  * Column Quality
  * Column Profile
  * Column Distribution
* **Column Quality** shows valid, empty and error values.
* **Column Profile** shows statistics appropriate to the selected data type.
* **Column Distribution** helps understand distinct and unique values.
* Different data types produce different profile statistics.
* Data types are extremely important because they can affect:

  * Data model
  * Report calculations
  * Performance
  * Data preparation
  * DAX
* Most columns in the dataset have appropriate data types.
* The main issue is **NULL values in `z`**.
* Approximately **2%** of the values are empty, corresponding to **855 records**.
* The instructor temporarily filters `z = NULL` to investigate the affected records.
* The temporary filtering step must be **deleted before performing the actual cleaning**, otherwise only the filtered records would remain.
* Perplexity suggests replacing NULL values with an appropriate value.
* For this project, NULL `z` values are replaced with **0**.
* Use:

```text
Transform → Replace Values
```

* Replace:

```text
null → 0
```

* After verifying the result, use:

```text
Home → Close & Apply
```

* **Close & Apply is essential** because it commits the Power Query transformations to the Power BI model.

---

# 45. Final Revision Sheet

### Power Query Data Profiling

```text
Transform Data
      ↓
Power Query Editor
      ↓
View
      ↓
Set profiling → Entire Dataset
      ↓
Column Quality
      ↓
Column Profile
      ↓
Column Distribution
```

### Data Quality

```text
Column Quality
├── Valid
├── Empty
└── Error
```

### Dataset issue discovered

```text
Column = z
Data Type = Decimal
Problem = NULL values
Affected records = 855
```

### Cleaning

```text
Select z
   ↓
Transform
   ↓
Replace Values
   ↓
Find: null
   ↓
Replace with: 0
   ↓
OK
```

### Finalize

```text
Home
  ↓
Close & Apply
  ↓
Changes applied
  ↓
Cleaned data loaded into Power BI Model
```

### One-line takeaway

> **Use Power Query to profile the entire dataset, verify data types and quality, identify the 855 NULL values in `z`, remove the temporary inspection filter, replace NULL with 0, verify the result, and finally use Close & Apply to load the cleaned data into the Power BI model.**
