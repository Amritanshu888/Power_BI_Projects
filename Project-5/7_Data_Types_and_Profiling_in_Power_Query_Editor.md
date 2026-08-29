# Power BI — Data Cleaning, Data Profiling & Data Types

## 1. Session Overview

This session focuses on the **data cleaning and data validation stage** of the Loan Default Power BI project.

The main objectives are:

1. Open the **Power Query Editor**.
2. Understand **Column Profiling**.
3. Change profiling from the default **top 1,000 rows** to the **entire dataset**.
4. Inspect:

   * Column Quality
   * Column Distribution
   * Column Profile
5. Check the dataset size.
6. Verify whether columns contain:

   * Valid values
   * Errors
   * Empty/null values
7. Verify the **data type of every column**.
8. Check the `Loan Date` formatting.
9. Understand why checking data types is important.
10. Apply/close Power Query and return to Power BI Report View.

---

# 2. Open Power Query Editor

The first step is to open the Power Query Editor.

### Steps

From **Power BI Desktop**:

1. Go to **Report View**.
2. Click:

**Transform Data**

This opens the:

> **Power Query Editor**

Power Query Editor is where we can perform operations such as:

* Data cleaning
* Data transformation
* Data type conversion
* Removing errors
* Handling missing values
* Filtering
* Renaming columns
* Merging/combining data

In this particular session, the primary focus is **data profiling and data type validation**.

---

# 3. Column Profiling in Power Query

Once Power Query Editor opens, we can see the dataset.

Power BI provides a useful feature called:

> **Column Profiling**

Column profiling provides information about the data contained within each column.

It can help us understand:

* Whether values are valid
* Whether errors exist
* Whether empty values exist
* Distribution of values
* Number of unique values
* Number of distinct values
* Other statistical information

---

# 4. Default Column Profiling — Top 1,000 Rows

By default, Power BI performs column profiling based on:

> **Top 1,000 rows**

This is important to remember.

If the dataset contains a large number of records, the profiling information shown by default may not represent the entire dataset.

Therefore, for proper analysis in this project, the instructor changes the profiling option to:

> **Entire Dataset**

---

# 5. Change Column Profiling to Entire Dataset

### Steps

In Power Query Editor:

1. Locate the profiling option at the bottom of the Power Query window.
2. Click the option that currently indicates profiling is based on the **top 1,000 rows**.
3. Change it to:

> **Entire Dataset**

Now Power BI will calculate the profiling information using the complete dataset rather than only the first 1,000 records.

---

# 6. Important Performance Consideration

The dataset contains approximately:

> **255,347 records**

or around:

> **2.5 lakh records**

When Column Profiling is changed from the top 1,000 rows to the **entire dataset**, Power BI needs to process significantly more data.

Therefore, it can take some time to display the profiling information.

### Important practical point

The larger the dataset:

```text
More records
     ↓
More data to process
     ↓
More processing required
     ↓
Potentially longer profiling time
```

So do not assume that Power BI has stopped working simply because the profiling information takes some time to appear.

---

# 7. Enable Column Quality, Column Distribution and Column Profile

The instructor then goes to the:

> **View** tab

and works with the following options:

* Column Quality
* Column Distribution
* Column Profile

### Steps

Go to:

**View**

Then make sure these three options are enabled:

```text
☑ Column Quality
☑ Column Distribution
☑ Column Profile
```

The instructor first unchecks them and then checks them again so that Power BI recalculates/displays the information.

---

# 8. Column Quality

### What is Column Quality?

**Column Quality** provides an overview of the quality of values in a column.

It allows you to identify:

* Valid values
* Errors
* Empty values

For example, you may see something like:

```text
100% Valid
0% Error
0% Empty
```

This indicates that all values in that column are valid.

---

# 9. Column Profile

### What is Column Profile?

**Column Profile** provides detailed statistics about the selected column.

It can provide information such as:

* Value statistics
* Valid values
* Empty values
* Errors
* Distinct values
* Unique values
* Distribution-related information

It is useful when trying to understand the actual contents of a column before performing data transformations.

---

# 10. Column Distribution

### What is Column Distribution?

**Column Distribution** gives information about how values are distributed within a column.

It helps you understand:

* Different values/categories
* Frequency/distribution
* Distinct values
* Data patterns

For categorical columns, it can help identify the categories present.

For numerical columns, it can help understand the distribution of values.

---

# 11. Dataset Size

After allowing Power BI some time to process the complete dataset, the instructor observes that the dataset contains approximately:

> **255,347 records**

This is around:

> **2.5 lakh records**

This is important because the size of the dataset affects Power BI's processing time.

---

# 12. Checking Loan ID

The first column discussed is:

> **Loan ID**

The Column Quality information shows:

* **100% valid values**
* **0% errors**
* **0% empty values**

Therefore, the Loan ID column does not require any cleaning.

---

# 13. Unique Count vs Distinct Count

An important concept discussed for `Loan ID` is:

> **Unique Count**

and

> **Distinct Count**

In this dataset, the unique count and distinct count are the same.

This indicates that every Loan ID is unique.

### Why is this important?

If the dataset contained multiple tables and we needed to create relationships between them, a unique Loan ID column could potentially serve as a **primary key** on the appropriate table.

For example:

```text
Loan ID
   ↓
Unique
   ↓
Can identify each loan
```

### Important distinction

A primary key must uniquely identify records in its table.

The lecture's point is that because:

> **Unique Count = Distinct Count**

the `Loan ID` column is suitable as a unique identifier in this dataset.

---

# 14. Check Every Column

The same profiling process should be applied to every column.

The instructor explains that you can go through the columns one by one and inspect:

* Column Quality
* Column Profile
* Column Distribution
* Data type

For example, the following columns are checked:

* Loan ID
* Age
* Income
* Loan Amount
* Credit Score
* Months Employed
* Number of Credit Lines
* Interest Rate
* Loan Term
* DTI Ratio
* Education
* Employment Type
* Marital Status
* Has Mortgage
* Has Dependents
* Loan Purpose
* Has Cosigner
* Default
* Loan Date

---

# 15. Column Quality Results

For the dataset, the instructor observes that the columns have:

> **100% valid values**

and:

> **0% empty values**

and:

> **0% error values**

This indicates that there are no obvious missing or erroneous values that require correction at this stage.

Therefore:

> **No major data-cleaning operation is required based on Column Quality.**

---

# 16. Important Performance Consideration During Profiling

The instructor makes an important practical observation.

Even though the dataset contains only around:

> **2.5 lakh records**

Power BI takes some time to calculate and display the profiling information for the complete dataset.

Therefore, with much larger datasets, processing can take even longer.

### Larger data volume can affect:

* Column profiling
* Data transformations
* Query execution
* Dataset refresh
* Report refresh
* Overall Power BI performance

So when working with large datasets, always consider the volume of data being processed.

---

# 17. Data Refresh Performance

The same concept applies when refreshing the Power BI report.

If more data needs to be processed:

```text
Larger Dataset
      ↓
More data processing
      ↓
Longer transformation/refresh time
```

Therefore, data volume is an important consideration when designing Power BI solutions.

---

# 18. Checking Loan Date

The instructor specifically revisits the `Loan Date` column because there was previously a concern regarding its format in SQL Server.

The column description indicated a format corresponding to:

> **DDMMYYYY**

Meaning:

```text
Day → Month → Year
```

The instructor had previously observed that the date values in SQL Server did not appear to match the expected format.

However, after bringing the data into Power BI, the date values are displayed correctly.

---

# 19. Loan Date in Power BI

In Power Query, the date values appear in the expected order:

```text
Day → Month → Year
```

Therefore, the instructor concludes that Power BI has correctly interpreted the date values.

### Important conclusion

No transformation is required for the `Loan Date` column.

The existing date format is acceptable for the project.

---

# 20. Verify More Date Values

To make sure that the date interpretation is correct, the instructor scrolls down and checks additional records.

The dates continue to appear correctly as:

```text
Day
 ↓
Month
 ↓
Year
```

Therefore, the date column does not need to be modified.

---

# 21. Why Data Types Must Be Checked

One of the most important points of this session is:

> **Before starting any Power BI project, always verify the data type of every column.**

Power BI automatically detects data types, but you should **not blindly trust the automatic detection**.

Incorrect data types can lead to:

* Incorrect calculations
* Incorrect aggregations
* Incorrect visualizations
* Incorrect filtering
* Incorrect sorting
* Problems with DAX
* Incorrect date/time analysis
* Inaccuracies in the final report

Therefore:

> **Data type validation should be an essential part of the data-cleaning process.**

---

# 22. Data Types of All Columns

Let's go through every column and its detected data type.

---

## 22.1 Loan ID

### Data Type:

**Text**

This is correct.

### Reason

Loan ID is an identifier, not a numerical measure.

Even if IDs contain numbers, they should generally be treated as identifiers rather than values on which mathematical calculations are performed.

Therefore:

> **Loan ID → Text ✅**

---

# 23. Age

### Data Type:

**Whole Number**

Example:

```text
25
35
42
```

This is correct because age is represented using whole numbers.

> **Age → Whole Number ✅**

---

# 24. Income

### Data Type:

**Whole Number**

Income is stored as whole-number values.

Therefore:

> **Income → Whole Number ✅**

---

# 25. Loan Amount

### Data Type:

**Whole Number**

The loan amount is represented using whole numbers.

Therefore:

> **Loan Amount → Whole Number ✅**

---

# 26. Credit Score

### Data Type:

**Whole Number**

Credit scores are represented as whole numbers.

Therefore:

> **Credit Score → Whole Number ✅**

---

# 27. Months Employed

### Data Type:

**Whole Number**

The number of months employed is a whole-number value.

Therefore:

> **Months Employed → Whole Number ✅**

---

# 28. Number of Credit Lines

### Data Type:

**Whole Number**

The number of active credit lines is a count, so a whole number is appropriate.

Therefore:

> **Number of Credit Lines → Whole Number ✅**

---

# 29. Interest Rate

### Data Type:

**Decimal Number**

The instructor observes that Power BI represents the data using a decimal number format.

For example:

```text
1.2
```

This is appropriate because interest rates can contain decimal values.

Therefore:

> **Interest Rate → Decimal Number ✅**

---

# 30. Loan Term

### Data Type:

**Whole Number**

Loan term is represented in months.

For example:

```text
12
24
36
60
```

Therefore:

> **Loan Term → Whole Number ✅**

---

# 31. DTI Ratio

### Data Type:

**Decimal Number**

DTI Ratio can contain decimal values.

Therefore:

> **DTI Ratio → Decimal Number ✅**

---

# 32. Education

### Data Type:

**Text**

Education contains categorical/textual values such as:

* High school
* Bachelor's
* Master's

Therefore:

> **Education → Text ✅**

---

# 33. Employment Type

### Data Type:

**Text**

Employment Type contains categories such as:

* Full-time
* Part-time
* Self-employed

Therefore:

> **Employment Type → Text ✅**

---

# 34. Marital Status

### Data Type:

**Text**

Marital status contains categorical values.

For example:

* Single
* Married
* Divorced

Therefore:

> **Marital Status → Text ✅**

---

# 35. Has Mortgage

### Data Type:

**Boolean**

The column represents a Yes/No type of condition.

Power BI detects this as a Boolean field.

Therefore:

> **Has Mortgage → Boolean ✅**

---

# 36. Has Dependents

### Data Type:

**Boolean**

The column contains True/False-type information.

Therefore:

> **Has Dependents → Boolean ✅**

---

# 37. Loan Purpose

### Data Type:

**Text**

Loan Purpose represents a category/reason for taking the loan.

Therefore:

> **Loan Purpose → Text ✅**

---

# 38. Has Cosigner

### Data Type:

**Boolean**

This is another True/False type field indicating whether the borrower has a cosigner.

Therefore:

> **Has Cosigner → Boolean ✅**

---

# 39. Default

### Data Type:

**Boolean**

The Default column represents whether the borrower defaulted.

It is represented as a True/False type field in Power BI.

Therefore:

> **Default → Boolean ✅**

---

# 40. Loan Date

### Data Type:

**Date**

Power BI has correctly identified `Loan Date` as a Date field.

Therefore:

> **Loan Date → Date ✅**

The date values also appear in the expected day-month-year format.

---

# 41. Complete Data Type Reference

| Column                 | Data Type      | Correct? |
| ---------------------- | -------------- | -------- |
| Loan ID                | Text           | ✅        |
| Age                    | Whole Number   | ✅        |
| Income                 | Whole Number   | ✅        |
| Loan Amount            | Whole Number   | ✅        |
| Credit Score           | Whole Number   | ✅        |
| Months Employed        | Whole Number   | ✅        |
| Number of Credit Lines | Whole Number   | ✅        |
| Interest Rate          | Decimal Number | ✅        |
| Loan Term              | Whole Number   | ✅        |
| DTI Ratio              | Decimal Number | ✅        |
| Education              | Text           | ✅        |
| Employment Type        | Text           | ✅        |
| Marital Status         | Text           | ✅        |
| Has Mortgage           | Boolean        | ✅        |
| Has Dependents         | Boolean        | ✅        |
| Loan Purpose           | Text           | ✅        |
| Has Cosigner           | Boolean        | ✅        |
| Default                | Boolean        | ✅        |
| Loan Date              | Date           | ✅        |

---

# 42. Summary of Data Quality

After profiling the dataset, the instructor finds that:

### Dataset size

Approximately:

> **255,347 records**

### Data quality

The columns show:

> **100% valid values**

with:

> **0% errors**

and:

> **0% empty values**

### Data types

The data types detected by Power BI are appropriate for the columns.

### Date

`Loan Date` is correctly recognized as a Date field and appears in the expected day-month-year format.

Therefore:

> **No data-cleaning changes are required in this particular session.**

---

# 43. Close and Apply

Once the data validation is complete, return to the:

> **Home** tab

in Power Query Editor.

Then click:

> **Close & Apply**

### What does Close & Apply do?

It:

1. Applies the transformations/changes made in Power Query.
2. Closes Power Query Editor.
3. Returns you to Power BI Desktop's Report View.

In this particular session, no actual transformation was made.

However, if you had made changes such as:

* Changing data types
* Removing columns
* Removing errors
* Replacing values
* Filtering records

then **Close & Apply** would apply those changes to the Power BI model.

---

# 44. Power Query Editor vs Report View

The lecture makes the distinction between the two interfaces:

### Power Query Editor

Used primarily for:

* Data cleaning
* Data transformation
* Data profiling
* Data type validation

### Power BI Report View

Used primarily for:

* Creating visuals
* Designing reports
* Adding charts
* Adding slicers
* Building dashboards

The flow is:

```text
Power BI Desktop
       ↓
Transform Data
       ↓
Power Query Editor
       ↓
Clean / Transform / Validate
       ↓
Close & Apply
       ↓
Power BI Report View
```

---

# 45. Practical Data-Cleaning Checklist

Before starting the reporting part of a Power BI project, use this checklist.

### Step 1 — Open Power Query

**Transform Data → Power Query Editor**

### Step 2 — Check profiling

Make sure profiling is based on:

> **Entire Dataset**

when you need complete-data profiling.

### Step 3 — Enable

* Column Quality
* Column Distribution
* Column Profile

### Step 4 — Check data quality

Look for:

* Errors
* Empty/null values
* Invalid values

### Step 5 — Check unique identifiers

Determine whether identifier columns contain duplicate values.

### Step 6 — Check data types

Verify every column individually.

### Step 7 — Check dates

Verify:

* Date data type
* Date interpretation
* Day/month/year order
* Whether dates are being interpreted correctly

### Step 8 — Apply changes

Click:

**Home → Close & Apply**

---

# 46. Interview Questions

## Q1. What is Column Profiling in Power BI?

Column Profiling is a Power Query feature that provides statistical and quality-related information about the values contained in columns.

---

## Q2. What is the default number of rows used for column profiling?

By default, Power Query profiles the:

> **Top 1,000 rows**

The instructor changes this to:

> **Entire Dataset**

for this project.

---

## Q3. What are the three important column profiling features?

The three features are:

1. **Column Quality**
2. **Column Distribution**
3. **Column Profile**

---

## Q4. What does Column Quality show?

It provides information about:

* Valid values
* Errors
* Empty values

---

## Q5. Why should you check data types before creating a Power BI report?

Incorrect data types can cause inaccurate:

* Calculations
* Aggregations
* Filtering
* Sorting
* DAX results
* Visualizations
* Date analysis

Therefore, data types should always be validated before reporting.

---

## Q6. What data type is Loan ID?

> **Text**

because it is an identifier rather than a value used for mathematical calculations.

---

## Q7. What is the data type of Interest Rate?

> **Decimal Number**

---

## Q8. What is the data type of DTI Ratio?

> **Decimal Number**

---

## Q9. What is the data type of Loan Date?

> **Date**

---

## Q10. Which columns are Boolean?

The following are Boolean:

* Has Mortgage
* Has Dependents
* Has Cosigner
* Default

---

## Q11. Why is Loan ID potentially useful as a primary key?

Because each Loan ID is unique in this dataset, with the unique count matching the distinct count.

---

## Q12. What happens when you click Close & Apply?

Power Query applies the transformations/changes and returns you to Power BI Desktop's Report View.

---

# 47. Key Takeaways

> **1. Always profile your data before reporting.**

> **2. By default, Power Query profiles the top 1,000 rows.**

> **3. For complete analysis, profiling can be changed to Entire Dataset.**

> **4. Column Quality helps identify valid, error, and empty values.**

> **5. Column Distribution helps understand how values are distributed.**

> **6. Column Profile provides detailed column statistics.**

> **7. Always verify the data type of every column before starting report development.**

> **8. Incorrect data types can cause inaccurate Power BI reports and calculations.**

> **9. The Loan ID column contains unique values and can serve as a unique identifier.**

> **10. The Loan Date column is correctly recognized as Date and requires no changes.**

> **11. This dataset contains approximately 255,347 records.**

> **12. The dataset currently shows 100% valid values with no empty/error values.**

> **13. Larger datasets can increase the time required for profiling, transformations, and refreshes.**

> **14. After completing data preparation, use `Home → Close & Apply` to return to Report View.**

The next stage is the **reporting/analysis phase**, where these validated columns will be used to create Power BI visuals and apply DAX-based analysis.
