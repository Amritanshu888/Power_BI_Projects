# Power BI – Understanding & Cleaning Data Using Power Query

## 1. Purpose of This Session

In the previous session, SQL in **Google BigQuery** was used to:

* Understand the dataset.
* Perform data profiling.
* Perform data cleaning.
* Perform data transformations.

In this session, the same dataset is explored further using **Power Query Editor in Power BI**.

### Main objectives

1. Understand the meaning of each column.
2. Explore the dataset in Power Query.
3. Profile the data.
4. Check:

   * Data types
   * Null/empty values
   * Errors
   * Distinct values
   * Unique values
   * Value distributions
5. Perform required data-cleaning operations.
6. Prepare the data for report creation.

---

# 2. Housing Dataset

The project uses a **housing dataset** containing information about properties that were sold/purchased.

The dataset contains approximately **100,000 records** in this particular project.

The instructor also mentions that the column definitions are available in an **Excel sheet**, which is provided in the course resources.

---

# 3. Column Definitions

Understanding column definitions is important because it helps us correctly interpret the data during analysis and report creation.

## 3.1 Date

The **Date** column represents:

> The date on which the transaction/property sale took place.

It indicates when the property was sold.

**Data type:** Date

---

## 3.2 Quarter

The **Quarter** column represents:

> The fiscal quarter in which the event occurred.

Here, the event refers to the date on which the property was sold.

For example, a year can be divided into:

* Q1
* Q2
* Q3
* Q4

---

## 3.3 House ID

**House ID** is the unique identifier for a particular property.

It allows us to uniquely identify a house that was sold or purchased.

### Important

Because it is an identifier, two different houses should ideally not have the same House ID.

---

## 3.4 House Type

**House Type** represents the category/type of property.

The dataset contains categories such as:

* Villa
* Apartment
* Summer house
* Town house
* Farm

The instructor mentions that these categories will be explored further during data analysis.

---

## 3.5 Sales Type

**Sales Type** represents the category/type of sale.

Examples include:

* Regular sale
* Family sale
* Other sale
* Auction

This column can be useful when analyzing how properties were sold.

---

## 3.6 Year Build

**Year Build** represents:

> The year in which the property was built.

For example:

`1998`, `2005`, `2015`, etc.

---

## 3.7 Purchase Price

**Purchase Price** represents:

> The price at which the property was purchased.

This is one of the important numerical columns for analysis.

---

## 3.8 Percentage Change Between Offer and Purchase

This column represents the **percentage difference between the property's offer price and its final purchase price**.

There can be a difference between:

* The price at which the property was offered
* The price at which the property was ultimately purchased

This column represents that difference in percentage terms.

### Example

If a property was offered at ₹100 and purchased for ₹95:

The percentage change would indicate the difference between the two prices.

The actual dataset contains values such as `0`, meaning there are cases where there was no percentage difference between offer and purchase price.

---

## 3.9 No. of Rooms

**No. of Rooms** represents:

> The number of rooms available in the house.

The lecture observes that the highest number of rooms appearing in the dataset is **4**.

---

## 3.10 SQM

**SQM** represents:

> The total area of the house in square meters.

SQM = Square Meter

This is a numerical measurement of the property's size.

---

## 3.11 SQM Price

**SQM Price** represents:

> The price per square meter of the property.

This can be useful for comparing property prices independent of their total size.

---

## 3.12 Address

The **Address** column contains the street address of the property.

It identifies the specific street/location of the property.

**Data type:** Text

---

## 3.13 ZIP Code

**ZIP Code** represents:

> The postal code where the property is located.

---

## 3.14 City

**City** represents:

> The city or urban area in which the property is located.

This column is useful for city-level analysis.

---

## 3.15 Area

**Area** represents:

> The specific district, neighborhood, or part of the city where the property is located.

### Hierarchy

You can think of the geographical information as:

**Region → City → Area → Address**

---

## 3.16 Region

**Region** represents:

> A broader administrative region of Denmark.

The lecture mentions that Denmark has **five regions**.

The `Region` column identifies the broader region in which the property is located.

Later, Power Query is used to inspect the actual regions present in the dataset.

---

## 3.17 Nominal Interest Rate Percentage

This represents:

> The nominal interest rate that a customer may have to pay if they take a loan for the property.

For example, if someone purchases a property using a loan/mortgage, the applicable interest rate may be represented in this column.

---

## 3.18 Annual Inflation Rate Percentage

Inflation refers to the general increase in the prices of goods and services over time.

The **Annual Inflation Rate Percentage** represents:

> The annual percentage increase associated with inflation.

For example:

`1.85%`

would represent an annual inflation rate of 1.85%.

---

## 3.19 Yield on Mortgage Credit Bond Percentage

This is a more financial/technical column.

Suppose a customer purchases a property using a loan and the property is used as collateral/mortgage.

There can be **mortgage credit bonds** backed by residential properties.

Investors can purchase these credit bonds.

The return earned by those investors is represented by the:

> **Yield on Mortgage Credit Bond Percentage**

In simple terms:

**Property → Mortgage/Loan → Mortgage-backed credit bonds → Investors → Yield/Return**

---

# 4. Opening Power Query Editor

The dataset has already been loaded into Power BI Desktop.

### Steps

1. Open **Power BI Desktop**.
2. Ensure that the housing dataset has been loaded.
3. Go to the **Home** tab.
4. Click **Transform Data**.

This opens:

> **Power Query Editor**

---

# 5. Exploring the Dataset in Power Query

Once Power Query Editor opens, the different columns of the housing dataset can be viewed.

The instructor first expands the data pane and observes the available columns.

At this stage, the goal is **not immediately to transform the data**.

Instead, first:

> Understand → Profile → Identify problems → Clean → Transform

This is an important general data-preparation workflow.

---

# 6. Column Profiling in Power Query

Power Query provides several tools to understand the quality and distribution of the data.

The three important options are:

1. **Column Quality**
2. **Column Distribution**
3. **Column Profile**

---

# 7. Change Column Profiling from Top 1000 Rows to Entire Dataset

By default, Power BI may show column profiling information based on the **top 1,000 rows**.

However, this can give an incomplete picture of the dataset.

For better profiling, change it to:

> **Entire Dataset**

### Why?

Suppose the first 1,000 rows have no null values, but the remaining 99,000 rows contain nulls.

If you profile only the first 1,000 rows, you might incorrectly conclude:

> "There are no null values."

Therefore, for accurate profiling, use the entire dataset when practical.

---

# 8. Enabling Column Quality, Distribution and Profile

The instructor demonstrates toggling these options.

### Steps

In **Power Query Editor**:

1. Go to the **View** tab.
2. Locate the column profiling options.
3. Enable:

   * **Column quality**
   * **Column distribution**
   * **Column profile**

If necessary, uncheck them first and then check them again.

Once enabled, Power Query displays additional information about the selected column.

---

# 9. Column Quality

**Column Quality** helps identify the quality of values in a column.

It allows you to identify things such as:

* Valid values
* Errors
* Empty values

This is useful for detecting data-quality problems.

### General interpretation

You want to identify:

**Valid values → Good**

**Errors → Need investigation**

**Empty/Null values → Need investigation**

---

# 10. Column Distribution

**Column Distribution** shows how values are distributed within a column.

It helps answer questions such as:

* Which values occur most frequently?
* What are the different categories?
* How frequently does each value occur?
* Are there unusual values?

For categorical columns, this is especially useful.

---

# 11. Column Profile

**Column Profile** provides statistical information about the selected column.

It can show information such as:

* Count of records
* Errors
* Empty values
* Distinct values
* Unique values
* Empty strings
* Minimum
* Maximum
* Other statistics depending on the data type

This makes it easier to understand the structure and quality of the data.

---

# 12. Checking the Date Column

The instructor first examines the **Date** column.

### Observations

* No errors.
* No empty values.
* Values are valid.
* Data type is **Date**.

Power BI automatically detected the column as a Date data type.

### Conclusion

No transformation is required.

---

# 13. Checking Individual Columns

The same profiling process can be repeated for every column.

For each column, check:

### 1. Data type

Is it:

* Date?
* Text?
* Integer?
* Decimal?
* etc.

### 2. Errors

Are there any invalid/error values?

### 3. Empty values

Are there any null/blank values?

### 4. Distinct values

How many different values exist?

### 5. Unique values

How many values occur only once?

### 6. Distribution

Which values occur frequently?

---

# 14. House ID Column

The instructor checks the **House ID** column.

The purpose is to understand the values and verify the column's characteristics.

Since House ID is an identifier, it is particularly important to understand its uniqueness.

---

# 15. House Type Column

The instructor examines **House Type**.

The available categories include:

* Villa
* Apartment
* Summer house
* Town house
* Farm

This confirms the meaning of the column definition.

### Why this is useful

These categories can later be used to create reports such as:

* Number of properties by house type
* Average purchase price by house type
* Sales by house type
* Property distribution by house type

---

# 16. Sales Type Column

The instructor then checks **Sales Type**.

The categories include:

* Regular sale
* Family sale
* Other sale
* Auction

Again, the distribution can be examined through Power Query.

This allows us to understand how many records belong to each sales category.

---

# 17. Year Build Column

The **Year Build** column represents the year in which the property was constructed.

The column can be examined for:

* Data type
* Errors
* Null values
* Minimum year
* Maximum year
* Distribution

---

# 18. Purchase Price Column

The **Purchase Price** column represents the price at which the property was purchased.

The instructor checks its:

* Data type
* Distribution
* Validity
* Errors
* Empty values

The data type appears to be appropriate, so no change is required.

---

# 19. Percentage Change Between Offer and Purchase

The instructor examines the percentage-change column.

### Observation

There are several values in the distribution.

The value occurring **most frequently is 0**.

This means:

> There are many properties where there was zero percentage change between the offer price and purchase price.

This is an example of how column distribution can provide business insights even before creating visuals.

---

# 20. Number of Rooms

The **No. of Rooms** column is examined.

The distribution shows the different room counts.

The lecture observes:

> The highest number of rooms in the dataset is 4.

This can later be useful for analyzing properties by room count.

---

# 21. SQM and SQM Price

The instructor checks:

* SQM
* SQM Price

Both are numerical columns.

The instructor does not identify any major data-quality issue in these columns.

### Conclusion

No significant cleaning is required for these columns.

---

# 22. Address Column

The **Address** column contains property street addresses.

The instructor checks the column and finds the data to be acceptable.

No significant cleaning is required.

---

# 23. ZIP Code Column

The **ZIP Code** column is examined.

It represents the postal location of the property.

The data type is checked as part of the profiling process.

---

# 24. City Column – Identifying Null Values

The **City** column is where the instructor identifies a data-quality issue.

### Observation

The column contains:

> Some null/empty values.

The percentage of empty values is **less than 1%**.

The column's data type is:

> **Text**

---

# 25. Replacing Null Values in City

The instructor decides to replace the null values with:

> `Unknown`

### Steps

1. Right-click the **City** column.
2. Select **Replace Values**.
3. Specify the value that needs to be replaced:

   * `null`
4. Specify the replacement value:

   * `Unknown`
5. Click **OK**.

Power Query then applies the transformation.

### Result

The null city values are replaced with:

`Unknown`

### Why?

Instead of leaving missing city information as null, we explicitly label it as:

> **Unknown**

This makes the data easier to handle during analysis.

---

# 26. Important Observation: Power Query May Take Time

The instructor emphasizes that Power Query may require some time when applying transformations.

This becomes particularly noticeable when the dataset is large.

Even though this project has approximately **100,000 records**, operations such as:

* Profiling
* Replacing values
* Calculating distributions
* Applying transformations

may take some time.

### Key point

Don't assume Power BI has frozen simply because an operation takes some time.

Depending on:

* Dataset size
* Transformation complexity
* Number of columns
* Machine performance

Power Query may take some time to complete an operation.

---

# 27. Area Column

The instructor checks the **Area** column.

### Observations

* Contains area/district/neighborhood names.
* No null values.
* No errors.
* Data type is Text.
* Data is acceptable.

### Conclusion

No cleaning is required.

---

# 28. Region Column

The instructor then examines the **Region** column.

The column is:

> Text data type

The instructor wants to inspect the different regions available in the dataset.

### Steps

1. Click the dropdown/filter icon on the **Region** column.
2. Select **Load More**.

This displays more of the distinct values present in the column.

### Observation

The dataset contains data for **four regions**.

The lecture earlier mentioned that Denmark has five broader administrative regions, but the dataset contains property records for only four of them.

### Important distinction

**Number of regions in Denmark ≠ Number of regions present in the dataset.**

The dataset only contains records for the regions represented in the data.

---

# 29. Nominal Interest Rate Percentage

The instructor checks the nominal interest rate percentage column.

The data appears to be valid and does not require additional cleaning.

---

# 30. Annual Inflation Rate Percentage

The instructor identifies another data-quality issue in this column.

### Observation

There are:

> Less than 1% empty/null values.

The value that occurs most frequently is:

> **1.85**

The instructor decides to replace the null values with this most frequently occurring value.

---

# 31. Replacing Null Inflation Values with 1.85

### Steps

1. Right-click the **Annual Inflation Rate Percentage** column.
2. Select **Replace Values**.
3. Specify the value to replace:

   * `null`
4. Specify the replacement value:

   * `1.85`
5. Click **OK**.

Power Query applies the transformation.

### Result

The null values are replaced with:

`1.85`

---

# 32. Why Replace with 1.85?

The lecture uses the **most frequently occurring value** as the replacement.

From the column distribution:

> 1.85 is the most common inflation-rate value.

Therefore, it is used to replace missing values.

### General technique

For certain numerical columns, one possible missing-value strategy is:

> Replace missing values with the mode (most frequently occurring value).

However, remember that in real-world projects, the correct strategy depends on the business meaning of the column.

---

# 33. Data Type of Inflation Column

Power BI automatically detects the Annual Inflation Rate Percentage column as:

> **Decimal**

The instructor considers this appropriate.

Therefore:

> No data-type change is required.

---

# 34. Yield on Mortgage Credit Bond Percentage

The instructor examines the final column:

> **Yield on Mortgage Credit Bond Percentage**

### Observation

There are:

> Less than 1% null values.

The column distribution shows that:

> **1.47**

is the value occurring most frequently.

Therefore, the instructor decides to replace null values with:

`1.47`

---

# 35. Replacing Null Yield Values with 1.47

### Steps

1. Right-click **Yield on Mortgage Credit Bond Percentage**.
2. Select **Replace Values**.
3. Replace:

   * `null`
4. With:

   * `1.47`
5. Click **OK**.

Power Query applies the transformation.

---

# 36. Final Data-Cleaning Checks

After performing the required transformations, the instructor checks:

* Column Quality
* Column Distribution
* Column Profile

again.

The objective is to verify that the data has been cleaned correctly.

For example:

### Before

Annual Inflation Rate:

`Null → present`

### After

Annual Inflation Rate:

`Null → 1.85`

Similarly:

### Before

Yield on Mortgage Credit Bond:

`Null → present`

### After

Yield on Mortgage Credit Bond:

`Null → 1.47`

And:

### Before

City:

`Null → present`

### After

City:

`Unknown`

---

# 37. Summary of Data Cleaning Performed

| Column                          | Issue             | Action                      |
| ------------------------------- | ----------------- | --------------------------- |
| City                            | Null values (<1%) | Replace null with `Unknown` |
| Annual Inflation Rate %         | Null values (<1%) | Replace null with `1.85`    |
| Yield on Mortgage Credit Bond % | Null values (<1%) | Replace null with `1.47`    |
| Date                            | No issue          | No change                   |
| House Type                      | No major issue    | No change                   |
| Sales Type                      | No major issue    | No change                   |
| Year Build                      | No major issue    | No change                   |
| Purchase Price                  | No major issue    | No change                   |
| % Change Offer/Purchase         | No major issue    | No change                   |
| No. of Rooms                    | No major issue    | No change                   |
| SQM                             | No major issue    | No change                   |
| SQM Price                       | No major issue    | No change                   |
| Address                         | No major issue    | No change                   |
| ZIP Code                        | No major issue    | No change                   |
| Area                            | No major issue    | No change                   |
| Region                          | No major issue    | No change                   |
| Nominal Interest Rate %         | No major issue    | No change                   |

---

# 38. Important Power Query Workflow

The overall workflow demonstrated in this lecture can be remembered as:

```text
Load Data
    ↓
Open Power Query
    ↓
Understand Column Definitions
    ↓
Enable Column Profiling
    ↓
Change Profiling → Entire Dataset
    ↓
Check Column Quality
    ↓
Check Column Distribution
    ↓
Check Column Profile
    ↓
Check Data Types
    ↓
Identify Nulls / Errors
    ↓
Perform Required Cleaning
    ↓
Re-check Data Quality
    ↓
Close & Apply
    ↓
Create Report
```

This is an important workflow to follow in Power BI projects.

---

# 39. Closing Power Query Editor

After all transformations are complete, the instructor explains how to return to Power BI's Report View.

### Steps

1. Go to the **Home** tab in Power Query Editor.
2. Click **Close & Apply**.

Power BI will:

1. Apply all transformations.
2. Load the transformed data into the Power BI data model.
3. Return you to **Power BI Desktop → Report View**.

---

# 40. Data Loading May Take Time

After clicking **Close & Apply**, Power BI may take some time to:

* Apply transformations.
* Load the data into the model.
* Process the dataset.

The amount of time depends on the:

* Dataset size
* Number of transformations
* Complexity of the model
* Computer performance

This is normal behavior.

---

# 41. Final Outcome of the Session

By the end of this session, the housing dataset has been:

### Understood

The meaning of all important columns has been established.

### Profiled

The dataset was examined using:

* Column Quality
* Column Distribution
* Column Profile

### Validated

Data types, errors, nulls, distinct values and distributions were checked.

### Cleaned

The following transformations were performed:

* **City null → `Unknown`**
* **Annual Inflation Rate null → `1.85`**
* **Yield on Mortgage Credit Bond null → `1.47`**

### Loaded

The cleaned dataset was applied back to Power BI Desktop.

---

# 42. Key Concepts to Remember

### 1. Column Quality

Used to identify:

> Valid values, errors and empty values.

### 2. Column Distribution

Used to understand:

> How frequently different values occur.

### 3. Column Profile

Used to obtain:

> Detailed statistics about a column.

### 4. Entire Dataset

Profiling the entire dataset gives a more complete understanding than profiling only the default top 1,000 rows.

### 5. Null Handling

Null values should not simply be ignored.

They should be investigated and handled according to the business context.

### 6. Mode-Based Replacement

In this lecture, missing numerical values were replaced with the **most frequently occurring value**:

* Inflation → `1.85`
* Mortgage bond yield → `1.47`

### 7. Categorical Missing Values

For City, missing values were replaced with:

`Unknown`

This explicitly communicates that the city information is unavailable.

### 8. Data Type Validation

Even when Power BI automatically detects data types, you should still **verify them**.

### 9. Power Query Before Reporting

The general principle is:

> **Prepare and clean the data before building visuals and reports.**

---

# 43. Exam/Interview Perspective

If asked **"How do you profile data in Power BI?"**, you can answer:

> In Power Query Editor, I enable Column Quality, Column Distribution and Column Profile from the View tab. I change the profiling scope from the default top 1,000 rows to the entire dataset. Then I inspect each column for data types, errors, null values, distinct/unique values and value distributions. Based on the findings, I perform the necessary transformations and recheck the data before using Close & Apply.

### If asked "How did you handle missing values in this project?"

The lecture's approach was:

* **City:** Null → `Unknown`
* **Annual Inflation Rate:** Null → `1.85`, the most frequent value
* **Yield on Mortgage Credit Bond:** Null → `1.47`, the most frequent value

---

# 44. One Important Takeaway

The most important idea from this lecture is not just the individual replacements. It is the **data-preparation mindset**:

> **Don't immediately start creating charts after loading data. First understand what every column means, profile the dataset, identify data-quality problems, clean the data, validate the result, and then move toward report creation.**

The next stage of the project is therefore **Report Creation**, where the cleaned housing dataset will be used to build Power BI visuals and the actual report.
