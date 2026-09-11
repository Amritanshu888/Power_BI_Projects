# Power BI — Data Cleaning Using Power Query Editor

## 1. Objective of the Session

The main purpose of this session is to perform **data cleaning in Power BI** before creating the actual report.

Initially, the data was directly loaded into the Power BI model. In this session, the instructor opens **Power Query Editor** and cleans:

* Missing/null values
* Inconsistent text values
* Inconsistent capitalization
* Data types
* Date conversion errors
* Data coming from joined tables
* Column profiling and data quality

The cleaned data is then loaded back into the Power BI model using **Close & Apply**. 

---

# 2. Opening Power Query Editor

After loading the data into Power BI:

### Steps

1. Go to **Report View**.
2. Click **Transform Data**.
3. Power BI opens the **Power Query Editor**.

The Power Query Editor is where the instructor performs the data-cleaning operations. 

### Why Power Query?

Power Query is used to:

* Inspect data
* Clean data
* Replace missing values
* Correct inconsistent values
* Change data types
* Handle errors
* Transform columns
* Prepare data before loading it into the Power BI model

---

# 3. Configure Column Profiling

Power BI provides several tools to understand the quality and distribution of the data.

By default, Power BI's column profiling is based on only the **top 1,000 rows**.

However, this dataset contains **10,000 records**.

Therefore, the instructor changes the profiling to use the **entire dataset**. 

## Steps

At the bottom of Power Query:

1. Locate the **Column profiling** option.
2. Change it from profiling based on the top 1,000 rows to profiling based on the **entire dataset**.

### Why?

If your dataset contains 10,000 rows but Power BI profiles only 1,000 rows, you might miss:

* Null values
* Errors
* Rare categories
* Incorrect values
* Unusual distributions

Therefore, profiling the entire dataset provides a more complete picture.

---

# 4. Column Quality, Column Distribution and Column Profile

The instructor also works with the three important Power Query data-inspection features:

### Column Quality

Shows information such as:

* Valid
* Empty
* Error

### Column Distribution

Shows the distribution of values within a column.

### Column Profile

Provides statistics about the selected column.

The instructor toggles these options through the **View** tab by unchecking and checking them again. 

These features help identify data-quality problems before performing transformations.

---

# 5. Understanding the Transaction Dataset

The dataset contains approximately **10,000 transaction records**.

The important columns discussed include:

| Column                 | Purpose                                         |
| ---------------------- | ----------------------------------------------- |
| Transaction ID         | Unique identifier for the transaction           |
| Transaction Account ID | Account associated with transaction             |
| Date                   | Date on which transaction occurred              |
| Transaction            | Type of transaction                             |
| Amount                 | Transaction amount                              |
| Description            | Reason/type of transaction                      |
| Currency               | Currency used                                   |
| Account ID             | Account information obtained from accounts data |
| Customer ID            | Customer information                            |
| Account Type           | Savings/current                                 |
| Open Date              | Account opening date                            |
| Balance                | Account balance                                 |
| Name                   | Customer name                                   |
| Gender                 | Customer gender                                 |
| DOB                    | Date of birth                                   |
| Address                | Customer address                                |
| Email                  | Customer email                                  |
| Phone Number           | Customer phone number                           |

The transaction table contains significantly more records than the related account/customer tables. 

---

# 6. Handling Null Values in Description

The instructor examines the **Description** column.

Possible values include:

* Salary Credit
* Payment
* Null

There are some transactions for which no description is available. 

Instead of leaving these null values, the instructor replaces them with:

> **Unknown**

## Steps

First, the instructor had filtered the column to display only null values.

But this filtering step isn't needed for the final transformation.

### Step 1 — Remove the temporary filtering

On the right side under **Applied Steps**:

1. Locate the filtering step.
2. Delete the filtered-rows step.

### Step 2 — Replace null values

1. Right-click the **Description** column.
2. Select **Replace Values**.
3. Replace:

   * Old value → `null`
   * New value → `Unknown`
4. Click **OK**.

This converts missing descriptions into a meaningful category rather than leaving them blank. 

### Important concept

Instead of:

```text
Description
-----------
Payment
Salary Credit
null
Payment
null
```

we now have:

```text
Description
-----------
Payment
Salary Credit
Unknown
Payment
Unknown
```

This is useful later when building visualizations because `"Unknown"` becomes an explicit category.

---

# 7. Cleaning the Currency Column

The next issue is **inconsistent capitalization**.

The dataset contains currencies such as:

* USD
* usd
* INR

The problem is that:

```text
USD
```

and

```text
usd
```

represent the same currency but are treated as different text values.

The instructor wants a consistent representation. 

## Steps

1. Right-click the **Currency** column.
2. Select **Replace Values**.
3. Replace lowercase:

```text
usd
```

with:

```text
USD
```

4. Click **OK**.

After cleaning, the number of distinct currencies decreases.

The instructor verifies this by checking the **Column Profile** again.

Now the dataset has only:

* USD
* INR

instead of treating `USD` and `usd` as separate categories. 

### Key lesson

Text values should be standardized before analysis.

For example:

```text
USD
usd
Usd
```

should ideally become:

```text
USD
```

Otherwise Power BI may interpret them as different categories.

---

# 8. Understanding Nulls in Account ID

The instructor then examines the **Account ID** column and notices many null values.

These nulls are not necessarily a data-cleaning mistake.

They occurred because of how the data was created using a **JOIN in SQL Server**. 

---

# 9. Why Are There So Many Nulls After the JOIN?

Initially, the instructor had used a SQL join.

Perplexity had suggested an **INNER JOIN**, but the instructor specifically did **not** want an inner join.

Instead, a **LEFT JOIN** was used.

### Why LEFT JOIN?

The instructor wanted to retain **all transaction records**.

The transactions table contains many different account IDs.

However, the accounts table only had information for certain account IDs:

```text
102
103
104
105
```

Therefore:

* Transaction table → many account IDs
* Accounts table → only a few account IDs

When a transaction has an account ID that doesn't exist in the accounts table, the columns coming from the accounts table become `NULL`.

### Conceptually

Suppose Transactions contains:

| Transaction | Account ID |
| ----------- | ---------: |
| T1          |        102 |
| T2          |        103 |
| T3          |        110 |
| T4          |        120 |

Accounts contains:

| Account ID | Account Type |
| ---------- | ------------ |
| 102        | Savings      |
| 103        | Current      |

After a LEFT JOIN:

| Transaction | Account ID | Account Type |
| ----------- | ---------: | ------------ |
| T1          |        102 | Savings      |
| T2          |        103 | Current      |
| T3          |        110 | NULL         |
| T4          |        120 | NULL         |

This is why the instructor leaves the null values as they are for now.

---

# 10. Why the Instructor Does NOT Remove These Nulls

The instructor explicitly says that these null values will be considered later if the associated columns are actually needed.

The important point is:

> **Not every null value is a data-quality problem.**

Some nulls are a natural consequence of the data model and joins.

Therefore, you should first understand **why the null exists** before blindly replacing or deleting it. 

---

# 11. Nulls in Customer and Account Columns

The same issue exists for other columns extracted from:

* Accounts table
* Customers table

There are only certain customers and accounts for which information is available.

The transactions table contains much more data.

Therefore, columns originating from the customer/accounts tables can contain many nulls.

The instructor leaves them unchanged for now and says that if those columns are used later, their cleaning requirements can be reconsidered. 

### Important takeaway

Don't automatically do:

```text
Null → Unknown
```

for every column.

Ask:

> Why is this value null?

If the null is expected because of a LEFT JOIN, it may be perfectly valid to leave it.

---

# 12. Cleaning Account Type

The **Account Type** column contains account categories such as:

* Savings
* Current

But there is inconsistent capitalization in the values.

For example, one version of Current may be lowercase while another version uses uppercase/capitalized formatting.

The instructor wants the values to have a uniform representation. 

## Steps

1. Right-click **Account Type**.
2. Select **Replace Values**.
3. Replace the inconsistent version.
4. Convert it into the desired capitalization.

The instructor chooses a representation where the first letter is capitalized:

```text
Current
```

rather than having inconsistent variants such as:

```text
current
CURRENT
Current
```

The same concept applies to other categorical columns.

---

# 13. Open Date

The **Open Date** column contains dates.

The instructor notes that there had previously been some inconsistencies with dates.

However, those issues had already been addressed in **SQL Server**, where the data was made consistent. 

Nevertheless, the data type still needs to be checked in Power Query.

---

# 14. Reviewing the Remaining Columns

The instructor goes through the remaining columns and checks their data types and contents.

### Balance

Represents the account balance.

### Customer ID

Identifies the customer.

### Name

Customer name.

### Gender

Customer gender.

### DOB

Customer date of birth.

### Address

Customer address.

### Email

Customer email.

### Phone Number

Customer phone number. 

The goal at this stage is to ensure that every column has an appropriate Power BI data type.

---

# 15. Checking and Correcting Data Types

One of the most important parts of the session is assigning the correct **data type** to each column.

The instructor checks the columns one by one.

---

## Transaction ID

Current type:

> Number

The instructor considers this appropriate.

---

## Transaction Account ID

Current type:

> Number

This is also considered appropriate.

---

## Transaction Date

The instructor wants:

> Date

instead of another data type.

### Initial approach

The instructor selects the column and changes the data type to **Date**.

However, this produces errors.

This becomes an important issue that is resolved later.

---

## Transaction Type

Data type:

> Text

This is appropriate because the column contains categorical values such as transaction types.

---

## Amount

Data type:

> Decimal Number

This is appropriate because transaction amounts can contain decimal values.

For example:

```text
1250.50
```

should not necessarily be treated as an integer.

---

## Description

Data type:

> Text

Correct.

---

## Currency

Data type:

> Text

Correct.

Currencies such as:

```text
USD
INR
```

are categorical text values.

---

## Account ID

Data type:

> Number

Correct.

---

## Customer ID

Data type:

> Number

Correct.

---

## Account Type

Data type:

> Text

Correct.

Values such as:

```text
Savings
Current
```

are categorical text.

---

## Open Date

The instructor changes this to:

> Date

because it represents a date rather than ordinary text.

---

## Balance

The instructor considers the existing type appropriate.

---

## Customer ID

Number type is appropriate.

---

## Name

Data type:

> Text

Correct.

---

## Gender

Data type:

> Text

Correct.

---

## Date of Birth

The instructor changes this to:

> Date

because DOB is a date field.

---

## Address

Data type:

> Text

Correct.

---

## Email

Data type:

> Text

Correct.

---

## Phone Number

The instructor changes the phone number to:

> Whole Number

The intention is to treat the phone number as a numeric field according to the lecture's dataset setup. 

---

# 16. The Date Conversion Error

When changing the transaction date column to **Date**, Power BI generates errors.

The instructor clicks the error to investigate.

Power BI displays an error indicating:

> It couldn't parse the input provided as a date value.

In other words, Power BI was unable to interpret some of the existing values as dates using its current interpretation rules. 

---

# 17. How to Fix the Date Parsing Error

This is one of the most important practical steps in the lecture.

The instructor does **not** simply leave the error.

Instead, the existing incorrect data-type transformation is removed and the conversion is performed using a specific **locale**.

## Step 1 — Remove the incorrect Changed Type step

Go to:

**Applied Steps**

Find:

> Changed Type

Delete this step.

This removes the unsuccessful date conversion.

---

## Step 2 — Use "Using Locale"

At the top of the column/data-type controls, click the small icon showing:

> ABC

Then choose:

> **Using Locale**

This allows you to explicitly specify how Power BI should interpret the date values.

---

## Step 3 — Select Date

In the **Data Type** option, select:

> Date

---

## Step 4 — Select Locale

For **Locale**, select:

> English (United States)

---

## Step 5 — Click OK

Click **OK**.

Power BI now interprets the date values according to the selected locale.

The instructor confirms that the errors disappear. 

---

# 18. Why Did the Date Error Happen?

The instructor explains that Power BI tries to interpret dates based on the **regional settings of the system**.

The dates in this dataset were in a particular format, and Power BI's default regional interpretation was not matching the format of the data.

Therefore, Power BI couldn't parse some values as dates. 

### General concept

A date such as:

```text
01/02/2025
```

can potentially be interpreted differently depending on the expected regional format.

For example:

```text
MM/DD/YYYY
```

versus:

```text
DD/MM/YYYY
```

Therefore, specifying a **locale** can solve date parsing problems.

---

# 19. Important Power Query Technique — Using Locale

When Power BI cannot correctly convert a column to a date:

### Don't immediately:

* Delete the data
* Replace values randomly
* Ignore the errors

Instead:

1. Remove the incorrect **Changed Type** step.
2. Select the data-type icon.
3. Choose **Using Locale**.
4. Select the intended data type.
5. Select the appropriate locale.
6. Click **OK**.
7. Verify that the errors disappear.

This is especially useful when working with data received from different countries or systems.

---

# 20. Applying All Changes

Once the cleaning is complete:

1. Go to the **Home** tab in Power Query.
2. Click:

> **Close & Apply**

Power BI then applies all Power Query transformations and loads the cleaned data back into the Power BI model. 

---

# 21. Verify the Cleaned Data

After clicking **Close & Apply**, Power BI returns to the report environment.

The instructor waits for the data to load.

Then:

1. Open **Table View**.
2. Check whether any errors remain.

The instructor confirms:

> No errors were thrown.

The data has been successfully loaded. 

---

# 22. Final Result

The instructor confirms that the data types were successfully converted according to requirements and the data was loaded into the model without errors.

The overall workflow was:

```text
Raw Data
   ↓
Power BI Desktop
   ↓
Transform Data
   ↓
Power Query Editor
   ↓
Column Profiling
   ↓
Inspect Data Quality
   ↓
Handle Null Values
   ↓
Standardize Text Values
   ↓
Check JOIN-related Nulls
   ↓
Correct Data Types
   ↓
Fix Date Parsing Error
   ↓
Using Locale
   ↓
Verify No Errors
   ↓
Close & Apply
   ↓
Power BI Data Model
   ↓
Report Creation
```

---

# 23. Complete Cleaning Checklist From This Lecture

Use this as your practical checklist whenever you perform similar Power BI data cleaning.

### Step 1 — Open Power Query

**Power BI → Report View → Transform Data**

### Step 2 — Configure profiling

Change profiling from:

```text
Top 1,000 rows
```

to:

```text
Entire dataset
```

### Step 3 — Inspect Column Quality

Check:

* Valid
* Empty
* Error

### Step 4 — Inspect Column Distribution

Look for:

* Unexpected categories
* Duplicate representations
* Inconsistent capitalization
* Unusual values

### Step 5 — Inspect Column Profile

Look at:

* Distinct values
* Unique values
* Statistics
* Null/empty values
* Errors

### Step 6 — Handle genuine missing values

For Description:

```text
null → Unknown
```

using:

**Right-click column → Replace Values**

### Step 7 — Standardize categorical values

Example:

```text
usd → USD
```

### Step 8 — Investigate nulls before removing them

Especially when they come from:

* LEFT JOIN
* Missing lookup records
* Related tables

Don't blindly replace every null.

### Step 9 — Standardize capitalization

For example:

```text
current
Current
CURRENT
```

should be standardized into one representation.

### Step 10 — Verify data types

Typical mappings from this lecture:

| Column                 | Data Type      |
| ---------------------- | -------------- |
| Transaction ID         | Number         |
| Transaction Account ID | Number         |
| Transaction Date       | Date           |
| Transaction            | Text           |
| Amount                 | Decimal Number |
| Description            | Text           |
| Currency               | Text           |
| Account ID             | Number         |
| Customer ID            | Number         |
| Account Type           | Text           |
| Open Date              | Date           |
| Balance                | Number         |
| Name                   | Text           |
| Gender                 | Text           |
| DOB                    | Date           |
| Address                | Text           |
| Email                  | Text           |
| Phone Number           | Whole Number   |

### Step 11 — Fix date errors using locale

If direct conversion fails:

**Delete Changed Type → ABC/Data Type icon → Using Locale → Date → English (United States) → OK**

### Step 12 — Apply

**Home → Close & Apply**

### Step 13 — Verify

Go to **Table View** and confirm:

* No unexpected errors
* Data loaded correctly
* Data types are correct

---

# 24. Key Concepts to Remember for Interviews

### 1. What is Power Query used for?

Power Query is used for **data extraction, transformation, cleaning, and preparation** before data is loaded into the Power BI model.

### 2. What is Column Quality?

It helps identify:

* Valid values
* Empty values
* Errors

### 3. Why profile the entire dataset?

Because profiling only the first 1,000 rows can hide problems that occur later in a larger dataset.

### 4. Should every NULL be removed?

**No.**

First understand why the value is null.

A null may be expected because of a **LEFT JOIN** or missing lookup information.

### 5. Why standardize categorical values?

Because:

```text
USD
usd
Usd
```

can be treated as separate categories.

Standardization ensures accurate aggregation and visualization.

### 6. Why can date conversion fail?

Because Power BI may interpret dates according to the system's regional settings, while the source data may use another date format.

### 7. How can date parsing errors be fixed?

Use:

**Using Locale**

and specify the appropriate:

* Data Type
* Locale

### 8. What does Close & Apply do?

It applies the transformations performed in Power Query and loads the transformed data into the Power BI model.

---

# 25. Most Important Practical Takeaways

If you are actually doing this project yourself, the **five things I would especially remember from this lecture** are:

1. **Always inspect data before building visuals.**
2. **Use Column Quality/Profile/Distribution to identify data problems.**
3. **Don't blindly remove NULLs—understand their source first.**
4. **Standardize categorical/text values such as `usd` → `USD`.**
5. **When date conversion fails, use `Using Locale` rather than forcing the conversion.**

The lecture concludes that the data-cleaning stage is complete, and the next sessions will move into **calculations and report creation**. 
