# Detailed Notes — Power BI Project 3: Data Profiling of UPI Transactions

This lecture continues the **UPI Transactions Power BI project**. The previous session focused on data preparation and transformations; this session focuses on **understanding the dataset in greater depth through data profiling** before starting the reporting work. 

---

# 1. Objective of This Session

The main objective is to get **more understanding and more details about the data** that will be used for the Power BI report.

The instructor specifically performs **data profiling** to determine:

* How many records are present.
* What values are present in each column.
* Whether columns contain blanks.
* Whether columns contain null/empty values.
* Whether columns contain errors.
* The minimum and maximum values of numerical columns.
* The number of distinct values.
* The number of unique values.
* How frequently different values occur.

The purpose is to determine whether the dataset is sufficiently clean to proceed with reporting.

---

# 2. Check the Total Number of Records

The instructor first goes to the **Table View**.

### Steps

1. Open Power BI Desktop.
2. Click **Table View**.
3. Allow the data to load if necessary.
4. Check the number of records in the dataset.

### Result

The UPI Transactions dataset contains:

> **20,000 records**

So the dataset has a total of **20,000 rows/records**.

---

# 3. Open Power Query Editor

After checking the total number of records, the instructor moves to Power Query Editor to perform data profiling.

### Steps

1. Go to **Report View**.
2. Click **Transform Data**.
3. Wait for Power Query Editor to open.

The data profiling options are available under the **View** tab.

---

# 4. Configure Data Profiling to Use the Entire Dataset

This is an important step.

By default, Power Query's column profiling can be based on only the **top 1,000 rows**.

The instructor wants the analysis to cover the **entire dataset**, not just the first 1,000 records.

### Initial setting

At the bottom of Power Query Editor, the instructor observes:

**Column profiling based on top 1000 rows**

### Change it to entire dataset

#### Steps

1. Look at the bottom of Power Query Editor.
2. Locate the setting indicating that column profiling is based on the **top 1,000 rows**.
3. Click that option.
4. Change it to:

**Column profiling based on entire data set**

This ensures that the profiling statistics are calculated using all **20,000 records**, rather than only the first 1,000.

---

# 5. Enable the Three Data Profiling Options

Under the **View** tab, the instructor enables three options:

1. **Column Distribution**
2. **Column Profile**
3. **Column Quality**

These three options provide different types of information about the dataset.

### Steps

Go to:

**View → Column Distribution**

**View → Column Profile**

**View → Column Quality**

Enable all three.

These options collectively fall under **Data Profiling**.

---

# 6. What Is Data Profiling?

**Data profiling** is the process of examining the data to understand its structure, values, quality, and characteristics before using it for analysis and reporting.

In this lecture, data profiling is used to answer questions such as:

* Are there blanks?
* Are there null values?
* Are there errors?
* How many different values exist?
* Which values occur most frequently?
* What are the minimum and maximum values?
* How many records are present?

The instructor emphasizes that data profiling helps you **understand your data better**.

---

# 7. Column Distribution

The **Column Distribution** option provides information about the distribution of values within a column.

It shows:

* **Distinct values**
* **Unique values**

### Distinct Values

Distinct values represent the different values that exist in a column.

For example, if a column contains:

`Delhi, Mumbai, Delhi, Bangalore`

then the distinct values are:

* Delhi
* Mumbai
* Bangalore

### Unique Values

Unique values refer to values that occur only once.

The column distribution therefore gives an understanding of how values are distributed within the column.

---

# 8. Column Quality

The **Column Quality** option provides information about the quality of the values in a column.

It identifies:

* **Valid values**
* **Error values**
* **Empty values**

This is particularly useful for determining whether the data needs cleaning.

### What you should look for

For every column, check whether there are:

* Blank values
* Null/empty values
* Errors

If such problems exist, they need to be investigated and potentially cleaned in Power Query before using the dataset for reporting.

---

# 9. Column Profile

The **Column Profile** option provides statistics about a selected column.

It can show information such as:

* Total count
* Minimum value
* Maximum value
* Distinct values
* Unique values
* Other column statistics

Therefore, Column Profile gives a more detailed statistical view of the selected column.

---

# 10. Value Distribution

The instructor also discusses the **value distribution** shown when Column Distribution is enabled.

Value distribution tells you:

> How values are distributed in a column and how many times a particular value occurs.

For example, if a city column contains:

* Delhi — 5,000 records
* Mumbai — 4,000 records
* Bangalore — 6,000 records
* Hyderabad — 5,000 records

the value distribution allows you to understand how frequently each city occurs.

---

# 11. Profiling the Transaction ID Column

The instructor begins examining individual columns, starting with **Transaction ID**.

Since each transaction ID appears only once:

* Each ID is unique.
* The value distribution reflects that each transaction ID occurs once.

This is expected because Transaction ID is intended to identify individual transactions.

---

# 12. Profiling the Transaction Date Column

Next, the instructor selects **Transaction Date**.

The profiling information for the date column is displayed.

The instructor also observes that there are:

* No null values.
* No empty values.
* No blanks requiring treatment.

Therefore, there is no data-cleaning requirement for this column based on the profiling performed.

The important point is not just to look at the column but to understand **how the data actually looks inside Power BI**.

---

# 13. Profiling the Amount Column

The next column examined is **Amount**.

The instructor identifies the following statistics:

### Minimum Amount

**0.05**

### Maximum Amount

**1999.87993**

The instructor also mentions an average value of approximately:

**993**

So the `Amount` column contains transaction values ranging approximately from **0.05 to 1999.87993**, with an average around **993**.

These statistics help provide an initial understanding of the numerical distribution of transaction amounts.

---

# 14. Bank Name Sent

The instructor then examines the **Bank Name Sent** column.

There are **four different banks** mentioned:

1. SBI
2. ICICI
3. Axis
4. HDFC Bank

This gives an understanding of the different banks from which transactions were sent.

---

# 15. Bank Name Received

The next column is **Bank Name Received**.

The banks mentioned are:

* HDFC
* SBI
* Axis Bank
* ICICI

So the received-bank column also contains four bank categories.

---

# 16. Remaining Balance

The instructor then examines the **Remaining Balance** column.

### Minimum value

**0.53**

### Maximum value

**9999.46**

The column also contains a total of:

**20,000 records**

This confirms that the column contains data across the entire dataset.

---

# 17. City

The `City` column is examined next.

The cities mentioned are:

* Delhi
* Bangalore
* Hyderabad
* Mumbai

These represent the cities associated with the transactions.

---

# 18. Gender

The `Gender` column contains:

* Male
* Female

So there are two categories identified in this column.

---

# 19. Transaction Type

The instructor again examines the `Transaction Type` column.

As discussed in the previous session, there are **two transaction types**.

The lecture does not repeat the names explicitly in this portion, but the previous session identified them as:

* Transfer
* Payment

The important point in this lecture is to use profiling to examine the values that actually exist in the dataset.

---

# 20. Status

The instructor then looks at the `Status` column.

This column had already been discussed in the previous session.

The status represents whether a transaction was successful or failed.

The earlier lecture identified:

* Success
* Failed

The instructor's point here is that previously discussed column definitions should now be connected with what is actually visible during data profiling.

---

# 21. Transaction Time

The instructor examines the **Transaction Time** column.

This column represents:

> The time at which the transactions took place.

This is the cleaned `Transaction Time` column produced during the previous session's transformation.

Recall that the date component had previously been removed so that the column represents the actual transaction time.

---

# 22. Device Type

The next column is `Device Type`.

This represents the different types of devices used for making transactions.

The previous session identified the device categories as:

* Laptop
* Mobile
* Tablet

The purpose of examining the column during profiling is to understand what values actually occur in the dataset.

---

# 23. Payment Method

The instructor also examines the `Payment Method` column.

This represents the method used for making the payment.

The previous session identified categories such as:

* Phone number
* QR code
* UPI ID

Again, the objective here is to inspect the actual distribution of those values.

---

# 24. Merchant Name

The `Merchant Name` column is examined.

The merchants mentioned are:

* Amazon
* Swiggy
* Zomato
* IRCTC
* Flipkart

This provides an understanding of the merchants represented in the dataset.

---

# 25. Purpose

The `Purpose` column represents the purpose for which the transaction amount was spent.

The earlier session identified categories including:

* Bill Payment
* Food
* Others
* Shopping
* Travel

The profiling stage allows you to understand the distribution of these categories.

---

# 26. Customer Age

The `Customer Age` column is also examined.

This is the age of the customer associated with the transaction.

The data type was previously confirmed as:

**Whole Number**

During profiling, the objective is to understand the values and statistics contained in this column.

---

# 27. Payment Mode

The instructor examines the `Payment Mode` column.

The previous session identified two categories:

* Instant
* Scheduled

This column indicates whether the payment was made instantly or scheduled for another time.

---

# 28. Currency

The `Currency` column is also examined.

This column is particularly important because the dataset contains two major numerical measures:

1. **Amount**
2. **Remaining Balance**

These numerical values are associated with a particular currency.

The `Currency` column tells us **which currency applies to those monetary values**.

So conceptually:

**Amount → transaction value**

**Remaining Balance → customer's remaining balance**

**Currency → currency in which those monetary values are represented**

---

# 29. Customer Account Number

The instructor then reaches the **Customer Account Number** column.

This contains the account number associated with the customer.

This column had already been transformed to **Text** in the previous session because account numbers had initially appeared in exponential notation.

The profiling stage is now used to examine the column as part of the overall dataset.

---

# 30. Merchant Account Number

The final column discussed is **Merchant Account Number**.

This represents the merchant's account number.

Like the customer account number, it was previously converted to **Text** to prevent inappropriate numerical/exponential representation.

---

# 31. Overall Data Quality Result

After examining the dataset through data profiling, the instructor reaches an important conclusion:

### The UPI Transactions dataset does not contain:

* Blanks
* Empty values
* Null values requiring treatment
* Errors

Therefore, the dataset appears to be **clean**.

The instructor concludes that the data looks sufficiently clean and can now be used for **reporting purposes**.

---

# 32. What If Blanks, Nulls, or Errors Were Found?

The lecture also explains what should happen if a dataset is **not** clean.

Suppose profiling reveals:

* Blank values
* Null values
* Errors
* Other data-quality problems

Then you should **clean the data in Power Query Editor first**.

Only after the necessary cleaning should the data be used for reporting.

### General workflow

**Load data**

↓

**Open Power Query**

↓

**Profile data**

↓

**Identify blanks/nulls/errors**

↓

**Clean/transform data**

↓

**Profile again / verify**

↓

**Use the cleaned data for reporting**

The instructor references previous project videos and Power Query Editor lessons where examples of handling such problems were discussed.

---

# 33. Why Data Profiling Is Important

The central lesson of this session is that you should **not immediately start creating visualizations just because the data has been loaded**.

First, investigate the dataset.

Data profiling gives you an understanding of:

### Data volume

How many records are present?

→ **20,000**

### Data quality

Are there:

* Blanks?
* Nulls?
* Errors?

### Data distribution

What values occur and how frequently?

### Numerical statistics

What are:

* Minimum values?
* Maximum values?
* Average values?

### Categories

What different categories exist in fields such as:

* Bank
* City
* Gender
* Transaction type
* Device type
* Merchant
* Purpose
* Payment mode?

This knowledge will help when designing the eventual Power BI report.

---

# 34. Important Difference Between the Three Profiling Features

This is worth memorizing:

| Feature                 | What it tells you                                                           |
| ----------------------- | --------------------------------------------------------------------------- |
| **Column Quality**      | Valid, error, and empty values                                              |
| **Column Distribution** | Distinct and unique values / value distribution                             |
| **Column Profile**      | Detailed statistics such as count, minimum, maximum, distinct, unique, etc. |

### Easy way to remember

**Quality → Is my data clean?**

**Distribution → What values are present and how are they distributed?**

**Profile → What statistics describe this column?**

---

# 35. Important Setting: Top 1,000 vs Entire Dataset

This is one of the most important practical Power Query steps from the lecture.

Power Query may initially show:

> **Column profiling based on top 1000 rows**

But the instructor changes it to:

> **Column profiling based on entire data set**

### Why?

Because the dataset contains **20,000 records**.

If you leave the setting at the top 1,000 rows, your profiling information may represent only that subset rather than the entire dataset.

### Steps to remember

**Power Query Editor → Bottom profiling setting → Top 1000 rows → Entire data set**

Then enable:

**View → Column Distribution**

**View → Column Profile**

**View → Column Quality**

---

# 36. Final Step — Close & Apply

After completing the profiling, the instructor returns to the report.

### Steps

1. Go to the **Home** tab in Power Query Editor.
2. Click **Close & Apply**.
3. Power BI returns to **Report View**.

However, there is an important point:

### No transformation was made in this session.

Therefore:

> **No changes were applied.**

The purpose of this session was to **inspect and understand the data**, not modify it.

---

# 37. Complete Lecture Workflow

The entire practical process from this lecture can be remembered as:

**Power BI Desktop**

↓

**Table View**

↓

**Check total records**

↓

**20,000 records**

↓

**Report View**

↓

**Transform Data**

↓

**Power Query Editor**

↓

**View tab**

↓

**Change profiling from Top 1,000 rows → Entire Dataset**

↓

**Enable Column Distribution**

↓

**Enable Column Profile**

↓

**Enable Column Quality**

↓

**Inspect every column**

↓

**Check valid / empty / error values**

↓

**Check distinct / unique values**

↓

**Check value distributions**

↓

**Check numerical statistics**

↓

**Determine whether cleaning is required**

↓

**Dataset is clean**

↓

**Home → Close & Apply**

↓

**Return to Report View**

↓

**Next session → Reporting**

---

# 38. Key Numbers From This Lecture

| Item                             |          Value |
| -------------------------------- | -------------: |
| Total records                    |     **20,000** |
| Amount minimum                   |       **0.05** |
| Amount maximum                   | **1999.87993** |
| Approx. Amount average mentioned |        **993** |
| Remaining Balance minimum        |       **0.53** |
| Remaining Balance maximum        |    **9999.46** |
| Banks mentioned                  |          **4** |
| Cities mentioned                 |          **4** |
| Gender categories                |          **2** |

---

# 39. Key Takeaways

### 1. Always profile your data

Before reporting, understand what the dataset contains.

### 2. Use the entire dataset for profiling

Change:

**Top 1000 rows → Entire data set**

when you want profiling statistics for all records.

### 3. Enable all three profiling features

* Column Quality
* Column Distribution
* Column Profile

### 4. Check data quality

Look for:

* Blanks
* Nulls
* Empty values
* Errors

### 5. Check distributions

Understand:

* Distinct values
* Unique values
* Frequency/distribution of values

### 6. Check numerical statistics

For numerical columns, inspect:

* Count
* Minimum
* Maximum
* Average/statistical information

### 7. Clean before reporting

If blanks, nulls, or errors exist:

**Clean them in Power Query first → then use the data for reporting.**

### 8. This particular dataset is clean

The instructor finds that the **UPI Transactions dataset has no problematic blanks, empty values, or errors**, so it is ready for reporting.

### 9. No changes were made in this session

Because this session was focused on **profiling/understanding**, the final **Close & Apply** does not apply any new transformations.

---

## One-Line Summary

**This lecture teaches you how to use Power Query's Data Profiling features to inspect the entire 20,000-record UPI Transactions dataset, understand its distributions and statistics, identify data-quality problems, determine whether cleaning is required, and confirm that the current dataset is clean and ready for the reporting stage.**
