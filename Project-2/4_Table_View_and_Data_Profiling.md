# Detailed Notes — Power BI Data Profiling & Understanding the Insurance Dataset

## 1. Purpose of This Lecture

In the previous lecture, the **Insurance dataset was loaded from Microsoft SQL Server into Power BI**.

In this lecture, the focus is **data profiling**.

Before creating a Power BI report, it is important to understand:

* What data is available
* What each column represents
* The data type of every column
* Number of rows
* Number of distinct values
* Number of unique values
* Empty/null values
* Errors
* Minimum and maximum values
* Distribution of values

> **Key principle:** Before creating a report, you should have a very good understanding of the data you are going to analyze.

---

# 2. First Look at the Data — Table View

The instructor first opens:

> **Table View**

Table View allows you to directly inspect the data loaded into Power BI.

### Steps

1. Open Power BI Desktop.
2. Select the **Table View** icon.
3. Select the **Insurance Data** table.
4. Click/select any column.

At the bottom of the Power BI window, general information about the selected column is displayed.

---

# 3. Information Available in Table View

When a column is selected, Power BI displays information such as:

* Table name
* Total number of records
* Selected column name
* Number of distinct values

For this dataset:

> **Total records = 10,000**

---

# 4. Example — Gender Column

The instructor selects the **Gender** column.

The Gender column has two possible values:

* Male
* Female

Therefore:

> **Distinct values = 2**

The total number of rows remains:

> **10,000**

### What are Distinct Values?

Distinct values represent the **different values that occur in a column**.

For example:

```text
Gender
------
Male
Female
Male
Male
Female
```

Distinct values are:

```text
Male
Female
```

Therefore, the distinct count is:

> **2**

---

# 5. Return to Report View

After inspecting the data in Table View:

1. Click **Report View**.
2. Power BI returns to the report canvas.

The instructor now wants more detailed information about the dataset.

For this purpose, **Power Query Editor** is opened.

---

# 6. Open Power Query Editor

### Steps

1. Go to the **Home** tab.
2. Click:

> **Transform Data**

3. Power Query Editor opens.

There is only **one table** in this project:

> **Insurance Data**

This table contains all the columns that will be used for insurance data analysis.

---

# 7. Enable Data Profiling Features

Power Query provides several useful data-profiling features.

The instructor enables three options:

1. **Column quality**
2. **Column distribution**
3. **Column profile**

### Steps

Inside Power Query Editor:

1. Go to the **View** tab.
2. Locate the data preview/data profiling options.
3. Check:

* ☑ Column quality
* ☑ Column distribution
* ☑ Column profile

These features provide detailed information about the quality and structure of the dataset.

---

# 8. Change Column Profiling from Top 1,000 Rows to Entire Dataset

By default, Power BI may perform column profiling based on:

> **Top 1,000 rows**

However, for proper analysis, the instructor wants profiling to be performed against the **entire dataset**.

### Steps

1. Locate the column profiling option.
2. Change:

> **Column profiling based on top 1000 rows**

to:

> **Column profiling based on entire data set**

### Why is this important?

If you profile only the first 1,000 rows, the results may not represent the entire 10,000-row dataset.

For example, a value may not occur in the first 1,000 rows but may occur later in the dataset.

Therefore, for this project, use:

> **Entire dataset**

for profiling.

---

# 9. Three Important Data Profiling Features

The three options enabled are extremely important:

| Feature                 | Main Information                        |
| ----------------------- | --------------------------------------- |
| **Column Quality**      | Valid, Error, Empty                     |
| **Column Distribution** | Distinct and Unique values/distribution |
| **Column Profile**      | Value distribution + column statistics  |

These features help you understand the quality and characteristics of the dataset.

---

# 10. Column Quality

**Column Quality** provides information about:

* Valid values
* Errors
* Empty values

For example:

```text
Valid   → 100%
Error   → 0%
Empty   → 0%
```

This tells you whether the column contains problematic values.

### If Column Quality is unchecked

The:

* Valid
* Error
* Empty

information disappears.

### If Column Quality is checked

These statistics are displayed again.

---

# 11. Column Distribution

**Column Distribution** provides information about the distribution of values in a column.

It helps identify:

* Distinct values
* Unique values
* Frequency/distribution of values

### If Column Distribution is unchecked

The distinct/unique distribution information is not shown.

### If Column Distribution is checked

The distinct and unique counts/distribution are displayed.

---

# 12. Column Profile

**Column Profile** provides detailed statistics about the selected column.

It can show:

* Value distribution
* Column statistics
* Total count
* Error count
* Empty count
* Distinct count
* Unique count
* Empty string count
* Minimum
* Maximum

### If Column Profile is unchecked

The profile information disappears.

### If Column Profile is checked

The value distribution and column statistics become visible.

---

# 13. Difference Between Distinct and Unique Count

This is an important concept from the lecture.

### Distinct Count

Distinct count represents:

> **The total number of different values present in a column.**

Example:

```text
A
A
B
C
C
```

Distinct values:

```text
A
B
C
```

Therefore:

> Distinct count = 3

---

### Unique Count

Unique count represents:

> **The number of different values that occur exactly once in the column.**

Using the same example:

```text
A
A
B
C
C
```

* A occurs twice
* B occurs once
* C occurs twice

Therefore:

> Unique count = 1

because only `B` occurs exactly once.

---

# 14. Why Distinct and Unique Counts Matter for Primary Keys

This becomes especially useful when working with multiple tables.

When identifying a potential **primary key**, a column should uniquely identify each row.

A useful indication is:

> **Distinct Count = Unique Count = Total Row Count**

For example, the Policy Number column has:

```text
Total = 10,000
Distinct = 10,000
Unique = 10,000
```

This indicates that every Policy Number occurs exactly once.

Therefore, **Policy Number is a strong candidate for being a primary key** in this table.

---

# 15. Policy Number — Data Profiling

The instructor starts examining individual columns.

### Column

> **Policy Number**

### Required Data Type

> **Text**

The column is correctly detected as Text.

### Why Text?

Policy Number is an identifier.

We are not going to perform numerical operations such as:

* Average policy number
* Sum of policy numbers
* Mathematical calculations

Instead, the policy number will be useful for things such as:

* Identifying policies
* Slicers
* Visual filters
* Other filtering/selection operations

Therefore:

> **Text is the appropriate data type.**

---

# 16. Policy Number Statistics

For Policy Number, the instructor observes:

| Statistic    |  Value |
| ------------ | -----: |
| Total count  | 10,000 |
| Errors       |      0 |
| Empty        |      0 |
| Distinct     | 10,000 |
| Unique       | 10,000 |
| Empty string |      0 |
| Minimum      |     P1 |
| Maximum      |  P9999 |

The important point is that:

> **Distinct = Unique = 10,000**

This means every policy number occurs only once.

---

# 17. Customer ID

Next, the instructor examines:

> **Customer ID**

### Data Type

The required data type is:

> **Text**

Power BI has detected it correctly.

### Column Quality

The instructor observes:

* Valid = 100%
* Error = 0%
* Empty = 0%

### Column Statistics

The profiling information also shows:

* Total count = 10,000
* Error = 0
* Empty = 0
* Distinct = 10,000
* Unique = 10,000
* Empty string = 0
* Minimum and maximum values
* Value distribution

The instructor is satisfied with the detected data type and quality.

---

# 18. Gender

The **Gender** column contains textual values.

### Data Type

Power BI displays:

> **ABC / Text**

This is appropriate because Gender contains categories such as:

* Male
* Female

There are:

* No null values
* No blanks
* No errors

The value distribution is also available.

---

# 19. Age

The instructor checks the **Age** column.

### Required Data Type

> **Whole Number**

Power BI has correctly detected it as a whole number.

### Why Whole Number?

Age represents integer values such as:

```text
18
25
32
45
60
87
```

There is no need for decimal values such as `25.7`.

---

# 20. Sorting Age Values

Power Query allows the values in a column to be sorted.

Click the dropdown/arrow associated with the column and select:

> **Sort Ascending**

This places values from smallest to largest.

### Minimum Age

After sorting ascending, the minimum age is:

> **18 years**

---

### Sort Descending

Click the column dropdown again and select:

> **Sort Descending**

This places the largest values first.

### Maximum Age

The maximum customer age in the dataset is:

> **87 years**

Therefore:

```text
Minimum Age = 18
Maximum Age = 87
```

---

# 21. Policy Type

The next column examined is:

> **Policy Type**

### Data Type

> **Text**

This is correct because Policy Type contains categories.

The dataset contains policy categories such as:

* Auto
* Health
* Home
* Life
* Travel

### Value Distribution

The value distribution helps determine how frequently each policy type occurs.

The instructor notes that:

> **Travel has the maximum number of claims/policies in the displayed distribution.**

The exact interpretation should follow the context of the table being analyzed.

---

# 22. Policy Start Date

The next column is:

> **Policy Start Date**

This represents:

> The date on which the insurance policy started/incepted.

### Data Type

> **Date**

Power BI has correctly detected it as Date.

No change is required.

---

# 23. Policy End Date

The next column is:

> **Policy End Date**

This represents:

> The date on which the policy ended.

### Data Type

> **Date**

The instructor confirms that Date is the appropriate data type.

No change is required.

---

# 24. Premium Amount

The next column is:

> **Premium Amount**

This represents the amount charged/collected by the insurance company.

### Data Type

> **Decimal Number**

The instructor confirms that the existing data type is appropriate.

No change is required.

The column also has:

* Column statistics
* Value distribution

available through Power Query's profiling features.

---

# 25. Coverage Amount

The next column is:

> **Coverage Amount**

This represents the risk/coverage amount provided by the insurance company.

### Data Type

> **Decimal Number**

The instructor confirms that Decimal Number is appropriate.

No change is required.

The column's:

* Value distribution
* Column statistics

can also be reviewed.

---

# 26. Claim Number

The next column is:

> **Claim Number**

### Data Type

> **Text**

This is appropriate because Claim Number is an identifier rather than a value on which mathematical operations will be performed.

Power BI has already detected it as Text.

No change is required.

---

# 27. Claim Date

The next column is:

> **Claim Date**

This represents the date on which the customer raised the claim.

### Data Type

> **Date**

The data type is appropriate.

However, there is a data-quality issue.

---

# 28. Claim Date — Null/Empty Values

The profiling information shows:

* **Valid = 56%**
* **Empty = 44%**
* **Errors = 0%**

So approximately:

> **44% of the Claim Date values are empty/null.**

This is an important data-quality observation.

### Should the null values be replaced?

At this stage:

> **No.**

The instructor decides not to replace the null values yet.

The reason is that the column may or may not require transformation depending on the analysis requirements.

If a later report requirement requires handling these missing dates, the appropriate transformation can be performed then.

Therefore:

> **Leave the null values as they are for now.**

---

# 29. Claim Amount

The next column is:

> **Claim Amount**

### Data Type

> **Decimal Number**

This is appropriate because claim amounts can contain decimal values.

No change is required.

Column statistics and value distribution can also be reviewed.

---

# 30. Claim Status

The final column examined is:

> **Claim Status**

### Data Type

> **Text**

This is appropriate because Claim Status contains categorical values.

The dataset has three claim statuses:

* **Rejected**
* **Settled**
* **Pending**

Therefore, the value distribution shows three categories.

---

# 31. Summary of Data Types

The expected data types for the insurance table are:

| Column            | Data Type      |
| ----------------- | -------------- |
| Policy Number     | Text           |
| Customer ID       | Text           |
| Gender            | Text           |
| Age               | Whole Number   |
| Policy Type       | Text           |
| Policy Start Date | Date           |
| Policy End Date   | Date           |
| Premium Amount    | Decimal Number |
| Coverage Amount   | Decimal Number |
| Claim Number      | Text           |
| Claim Date        | Date           |
| Claim Amount      | Decimal Number |
| Claim Status      | Text           |

These should always be checked when loading data into Power BI.

---

# 32. Data Quality Summary

The profiling exercise reveals that most columns have good data quality.

The main issue specifically identified in this lecture is:

> **Claim Date has approximately 44% empty values.**

For the current stage, these values are intentionally left unchanged.

Other columns examined generally have:

* Correct data types
* No errors
* No problematic empty values

---

# 33. Why Data Profiling Is Important

Data profiling is a critical step before report creation.

You should understand your dataset before creating visuals.

Data profiling helps answer questions such as:

### What is the size of my dataset?

> 10,000 rows.

### Does a column contain errors?

Check:

> **Column Quality**

### Does a column contain missing values?

Check:

> **Column Quality → Empty**

### How many different values are present?

Check:

> **Distinct Count**

### Does every value occur only once?

Check:

> **Unique Count**

### What are the minimum and maximum values?

Check:

> **Column Statistics**

### How are categorical values distributed?

Check:

> **Value Distribution**

---

# 34. Three Data Profiling Options — Quick Revision

### Column Quality

Shows:

```text
Valid
Error
Empty
```

Useful for identifying data-quality problems.

---

### Column Distribution

Shows:

```text
Distinct
Unique
Value Distribution
```

Useful for understanding the distribution and uniqueness of values.

---

### Column Profile

Shows detailed statistics such as:

```text
Count
Error
Empty
Distinct
Unique
Minimum
Maximum
Value Distribution
```

Useful for detailed analysis of an individual column.

---

# 35. Important Rule — Check Data Types

The instructor emphasizes an important best practice:

> **Whenever you load data into Power BI Desktop, you should check the data type of every column in every table that you are going to use.**

Do not blindly assume Power BI has detected every data type correctly.

For example:

```text
Policy Number → Text
Customer ID   → Text
Age           → Whole Number
Premium       → Decimal Number
Claim Date    → Date
```

Each type should match the actual meaning of the data.

---

# 36. Data Profiling vs Data Cleaning

These are related but different activities.

### Data Profiling

Understanding the existing data.

Examples:

* Finding null values
* Checking errors
* Checking distinct values
* Checking unique values
* Finding minimum/maximum
* Understanding distributions
* Checking data types

### Data Cleaning/Transformation

Actually modifying the data.

Examples:

* Replacing null values
* Removing errors
* Changing data types
* Removing duplicates
* Splitting columns
* Merging columns

In this lecture, the primary focus is:

> **Data profiling**

The instructor mentions that any required **data cleaning or transformation** will be discussed later when the report requirements make it necessary.

---

# 37. Important Observation About Primary Keys

The Policy Number column demonstrates an important concept.

For a column to be a potential primary key, its values should uniquely identify rows.

For Policy Number:

```text
Total rows     = 10,000
Distinct       = 10,000
Unique         = 10,000
```

Therefore:

```text
Distinct Count = Unique Count = Total Row Count
```

This strongly indicates that Policy Number uniquely identifies every row.

This concept becomes especially important when working with **multiple tables**, because primary and foreign keys are essential for creating relationships between tables.

---

# 38. Complete Data Profiling Procedure

Use the following procedure whenever you need to profile a dataset in Power Query.

### Step 1 — Open Power Query

**Home → Transform Data**

### Step 2 — Open View Tab

Click:

> **View**

### Step 3 — Enable Profiling Options

Enable:

* **Column Quality**
* **Column Distribution**
* **Column Profile**

### Step 4 — Use Entire Dataset

Change profiling from:

> Top 1,000 rows

to:

> **Entire dataset**

### Step 5 — Examine Every Column

For each column, check:

1. Data type
2. Valid values
3. Errors
4. Empty/null values
5. Distinct count
6. Unique count
7. Minimum
8. Maximum
9. Value distribution

### Step 6 — Identify Issues

Look for:

* Incorrect data types
* Null values
* Errors
* Duplicate values
* Unexpected categories
* Unusual minimum/maximum values

### Step 7 — Decide on Transformations

Do **not** automatically modify every issue.

Determine whether the issue actually affects the reporting requirements.

For example:

> Claim Date has 44% empty values, but the instructor leaves them unchanged for now.

---

# 39. Final Data Profiling Findings

After profiling the Insurance dataset:

* **Total rows:** approximately 10,000
* **Number of tables:** 1
* **Policy Number:** Text, 10,000 distinct and 10,000 unique
* **Customer ID:** Text
* **Gender:** Text/categorical
* **Age:** Whole Number, minimum 18, maximum 87
* **Policy Type:** Text/categorical
* **Policy Start Date:** Date
* **Policy End Date:** Date
* **Premium Amount:** Decimal Number
* **Coverage Amount:** Decimal Number
* **Claim Number:** Text
* **Claim Date:** Date, approximately 44% empty, 56% valid, 0% errors
* **Claim Amount:** Decimal Number
* **Claim Status:** Text with three categories — Rejected, Settled, Pending

---

# 40. Key Takeaways

1. **Always understand the data before creating a report.**
2. Use **Table View** for a general view of the loaded data.
3. Use **Power Query Editor** for detailed data profiling.
4. Enable:

   * Column Quality
   * Column Distribution
   * Column Profile
5. Change profiling from **Top 1,000 rows** to **Entire Dataset** when you want complete profiling.
6. **Distinct count** = number of different values.
7. **Unique count** = number of values occurring exactly once.
8. Equal distinct and unique counts can help identify a potential **primary key**.
9. Always verify the **data type of every column**.
10. Don't automatically replace null values; first determine whether the reporting requirements require it.
11. **Claim Date** currently contains approximately **44% empty values**, but no transformation is performed yet.
12. Data profiling is an essential preparation step before **data cleaning, modeling, and report creation**.
