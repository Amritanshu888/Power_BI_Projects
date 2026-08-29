# Power BI Power Query Editor — Understanding and Preparing the Data

## 1. Objective of the Session

In the previous session, the data was imported into **Power BI Desktop from an Azure SQL Database** and the connection was established.

In this session, the focus shifts to:

* Opening the **Power Query Editor**
* Understanding the dataset
* Understanding each column
* Identifying **data-type problems**
* Identifying **missing/invalid data**
* Using filters to investigate problematic records
* Understanding **Column Profiling**
* Deciding which records should be removed and which should be retained
* Preparing to create a new column to solve missing-value problems in the next session

The instructor also mentions that in upcoming sessions, **DAX calculations** may be used to create additional columns.

---

# 2. Open Power Query Editor

The first step is to open the Power Query Editor.

### Steps

1. Open the Power BI Desktop report containing the imported Azure SQL data.
2. Go to the **Home** tab.
3. Click **Transform Data**.

This opens the **Power Query Editor**.

The instructor uses Power Query to examine and clean the imported dataset before proceeding with report creation.

---

# 3. Understand the Dataset

The dataset represents **men's shirts / men's T-shirts data**.

The table was previously named:

**T Shirt**

The instructor mentions that the table can be given any suitable name, for example:

* `T Shirt`
* `Men's Clothes Data`
* Another suitable name

The specific name is not important; what matters is understanding and cleaning the underlying data.

---

# 4. Understand the Four Columns

The dataset contains four main columns:

1. **Brand**
2. **Title**
3. **Original Price**
4. **Sales Price**

The instructor explains the meaning and data type of each.

---

## 4.1 Brand Column

The **Brand** column contains the name of the product's brand.

For example, conceptually:

```text
Brand
------
Brand A
Brand B
Brand C
...
```

### Data Type

The Brand column has:

**Text** data type.

This is appropriate because brand names are textual values.

Therefore:

> **Brand → Text → Correct**

No change is required at this point.

---

# 5. Title Column

The **Title** column contains a small description of the product/article.

It provides descriptive information about the particular product.

For example, conceptually:

```text
Title
------------------------
Men's Casual Shirt
Cotton T-Shirt
Slim Fit Shirt
...
```

The instructor does not identify a specific data-type problem with this column in this session.

---

# 6. Original Price Column

The **Original Price** column represents the product's original/list/market price.

The instructor describes it as the:

* Market price
* List price
* Price written on the product tag

So conceptually:

```text
Original Price
       ↓
Price before the product was sold
```

For example:

```text
Original Price = 2000
```

---

# 7. Sales Price Column

The **Sales Price** column represents the actual price at which the product/article was sold.

Conceptually:

```text
Sales Price
       ↓
Actual selling price
```

For example:

```text
Original Price = 2000
Sales Price    = 1500
```

This allows the dataset to potentially be used for numerical analysis involving prices.

---

# 8. Problem #1 — Incorrect Data Type

The first major problem identified by the instructor is the data type of:

* **Original Price**
* **Sales Price**

Both columns currently have:

**Text** data type.

The instructor does **not** want them to remain as text because these columns represent numerical prices.

---

# 9. Why Text Data Type Is a Problem

The instructor wants to perform numerical calculations on these columns in upcoming sessions.

Potential calculations mentioned include:

* **Average**
* **Sum**
* Other numerical calculations

For example:

```text
Average Original Price
Sum of Sales Price
Average Sales Price
```

These calculations require the price values to be treated as numerical data.

Therefore, having:

```text
Original Price → Text
Sales Price    → Text
```

is problematic.

The desired data type is:

```text
Original Price → Whole Number
Sales Price    → Whole Number
```

---

# 10. Desired Data-Type Conversion

The desired structure is:

| Column         | Current Type | Desired Type     |
| -------------- | ------------ | ---------------- |
| Brand          | Text         | Text             |
| Title          | Text         | Text             |
| Original Price | Text         | **Whole Number** |
| Sales Price    | Text         | **Whole Number** |

The instructor wants to address this issue as part of the data-cleaning process.

---

# 11. Why Numerical Data Types Are Required

Once the price columns are converted to appropriate numerical types, they can be used for numerical calculations and report analysis.

For example:

```text
Sales Price
     ↓
Numerical values
     ↓
Sum
Average
Other calculations
```

The instructor specifically states that the upcoming report will be based on these numerical calculations.

---

# 12. Problem #2 — Missing / Not Available Values

The second major problem is the presence of:

**Not Available**

values in the data.

The instructor identifies this issue by inspecting individual records.

For example, the instructor points out **record number 7** as one of the places where `not available` appears in the price columns.

---

# 13. Investigating Missing Values Using Filters

Instead of simply deleting all records containing `not available`, the instructor investigates the data first.

The first column examined is:

**Original Price**

The goal is to identify records where:

```text
Original Price = Not Available
```

---

# 14. Filter Original Price for "Not Available"

### Steps

1. In Power Query Editor, locate the **Original Price** column.
2. Click its filter/dropdown button.
3. Click **Select All** if necessary to reset the existing selections.
4. Scroll through the available values.
5. Locate **not available**.
6. Select **not available**.
7. Apply the filter.

The table now displays only records where **Original Price is not available**.

---

# 15. Examine the Filtered Records

After applying the filter, the instructor observes that there are different types of situations.

For some records:

```text
Original Price = Not Available
Sales Price    = Not Available
```

For other records:

```text
Original Price = Not Available
Sales Price    = Valid Value
```

This distinction is extremely important.

The instructor does **not** want to treat these two situations in the same way.

---

# 16. Filter Sales Price for "Not Available"

The instructor then applies the same filter to the **Sales Price** column.

### Steps

1. Open the filter/dropdown for **Sales Price**.
2. Click **Select All**.
3. Scroll down.
4. Select **not available**.
5. Click **OK**.

Now both conditions are being investigated:

```text
Original Price = Not Available
AND
Sales Price    = Not Available
```

---

# 17. Identify Completely Invalid Records

After applying the filters, the instructor finds:

**16 records**

where both:

* Original Price is not available
* Sales Price is not available

So:

```text
Original Price = Not Available
Sales Price    = Not Available
```

for **16 records**.

---

# 18. Why These 16 Records Should Be Removed

The instructor examines these records further.

The problem is not limited to the price columns.

Other columns also contain problematic values.

For example:

* **Brand** may contain `not available`
* **Title** may contain `not available`

The instructor also mentions a case where the Brand value is simply:

```text
A
```

while the Title is:

```text
Not Available
```

The instructor concludes that these records do not provide meaningful product information for the intended analysis.

Therefore:

> These 16 records should be removed from the analysis.

---

# 19. Important Data-Cleaning Decision

This session demonstrates an important principle:

**Do not automatically remove every row containing a missing value.**

Instead, investigate the nature of the missing data first.

There are two different situations.

### Situation 1 — Both prices unavailable

```text
Original Price → Not Available
Sales Price    → Not Available
```

and other product information is also problematic.

### Decision:

**Remove these records.**

---

### Situation 2 — Original price unavailable but sales price is valid

```text
Original Price → Not Available
Sales Price    → Valid
Brand          → Valid
Title          → Valid
```

### Decision:

**Keep these records.**

The instructor wants to find a way to populate the missing Original Price values instead.

---

# 20. Why Some Records Should NOT Be Deleted

The instructor specifically identifies records where:

```text
Original Price = Not Available
Sales Price    = Valid
Brand          = Valid
Title          = Valid
```

These records still contain useful information.

For example:

```text
Brand       → Valid
Title       → Valid
Sales Price → Valid
Original Price → Not Available
```

Since the product itself is valid and the sales price is available, the instructor does **not** want to lose this record from the analysis.

---

# 21. Planned Solution for Missing Original Price

Instead of removing these useful records, the instructor plans to:

> **Find a way to populate the missing Original Price values.**

This will be handled in the next session.

The instructor specifically mentions that a **new column will be added** to the data to solve this issue.

So the next session will focus on creating a new column and determining how the missing Original Price values can be handled.

---

# 22. Column Profiling in Power Query

Another important concept introduced in this session is **Column Profiling**.

Power Query provides information about the data to help understand its quality.

By default, the instructor notes that Power BI displays column profiling based on:

**Top 1000 rows**

---

# 23. Default Column Profiling Behavior

At the bottom of the Power Query Editor, the instructor observes that column profiling is based on:

```text
Top 1000 rows
```

This means the displayed profiling information is initially calculated from only the first 1,000 rows rather than the complete dataset.

---

# 24. Change Column Profiling to Entire Dataset

For a more accurate understanding of the complete dataset, the instructor changes the profiling scope.

### Steps

1. Go to the bottom of the Power Query Editor.
2. Locate the **Column Profiling** option.
3. Change it from:

```text
Top 1000 rows
```

to:

```text
Entire data set
```

Now Power Query profiles the complete dataset.

---

# 25. Why Entire Dataset Profiling Is Important

If you analyze only the first 1,000 rows, problematic records outside those 1,000 rows may not be reflected in the profiling information.

Using the entire dataset provides a more complete picture.

Conceptually:

```text
Top 1000 rows
     ↓
Partial view of data

Entire dataset
     ↓
Complete view of data
```

The instructor uses the entire dataset option and still finds:

**16 records**

that need to be filtered out.

---

# 26. Apply the Filter to Remove Invalid Records

The instructor's planned approach is to use the filters on:

* Original Price
* Sales Price

to isolate the records where both values are unavailable.

The filtering logic is essentially:

```text
Original Price = Not Available
        AND
Sales Price = Not Available
```

These records are considered invalid for the analysis and will be filtered out.

---

# 27. Two Categories of Missing-Value Cases

This distinction is one of the most important concepts in the lecture.

### Category A — Completely unusable records

```text
Original Price → Not Available
Sales Price    → Not Available
Brand          → Not Available / problematic
Title          → Not Available / problematic
```

**Action: Remove.**

---

### Category B — Partially incomplete but useful records

```text
Original Price → Not Available
Sales Price    → Valid
Brand          → Valid
Title          → Valid
```

**Action: Keep and populate/fix Original Price.**

---

# 28. Data-Cleaning Decision Tree

You can remember the instructor's approach like this:

```text
Is Original Price unavailable?
              │
             YES
              │
              ▼
Is Sales Price also unavailable?
          /             \
        YES              NO
         │                │
         ▼                ▼
   Check other       Valid product
   fields            information
         │                │
         ▼                ▼
 Data is not useful   Keep record
         │                │
         ▼                ▼
   Remove record     Find a way to
                     populate Original
                     Price
```

This is the central data-cleaning decision discussed in the session.

---

# 29. Current Data Structure

At this point, the instructor is working with:

| Column         | Meaning                     | Current Data Type |
| -------------- | --------------------------- | ----------------- |
| Brand          | Brand name                  | Text              |
| Title          | Product/article description | Text              |
| Original Price | Market/list/tag price       | Text              |
| Sales Price    | Actual selling price        | Text              |

The desired eventual structure is:

| Column         | Desired Type |
| -------------- | ------------ |
| Brand          | Text         |
| Title          | Text         |
| Original Price | Whole Number |
| Sales Price    | Whole Number |

---

# 30. Important Observations From the Session

### Observation 1

The dataset is men's shirt/T-shirt product data.

### Observation 2

There are four primary columns:

**Brand, Title, Original Price, Sales Price**

### Observation 3

Brand is correctly represented as text.

### Observation 4

Title contains a short product description.

### Observation 5

Original Price represents the market/list/tag price.

### Observation 6

Sales Price represents the actual selling price.

### Observation 7

Original Price and Sales Price are currently stored as text.

### Observation 8

The instructor wants these two price columns to eventually be **Whole Number**.

### Observation 9

Some records contain `Not Available`.

### Observation 10

There are **16 records** where both Original Price and Sales Price are unavailable.

### Observation 11

Those 16 records are considered unsuitable for the analysis and should be removed.

### Observation 12

Other records have a valid Sales Price but a missing Original Price.

### Observation 13

Those records should **not** be removed because they contain useful information.

### Observation 14

A solution will be developed to populate the missing Original Price values.

### Observation 15

Column Profiling defaults to the **top 1000 rows**.

### Observation 16

The instructor changes Column Profiling to the **entire dataset**.

---

# 31. Complete Procedure Demonstrated

Here's the practical sequence from the lecture:

```text
Open Power BI Desktop
        ↓
Transform Data
        ↓
Power Query Editor opens
        ↓
Understand T-Shirt dataset
        ↓
Identify four columns
        ↓
Understand Brand
        ↓
Understand Title
        ↓
Understand Original Price
        ↓
Understand Sales Price
        ↓
Identify data-type problem
        ↓
Original Price = Text
Sales Price = Text
        ↓
Desired type = Whole Number
        ↓
Identify Not Available values
        ↓
Filter Original Price
        ↓
Select Not Available
        ↓
Inspect records
        ↓
Filter Sales Price
        ↓
Select Not Available
        ↓
Find 16 records where both are unavailable
        ↓
Inspect Brand/Title
        ↓
Determine records are not useful
        ↓
Remove/filter these records
        ↓
Investigate other records
        ↓
Original Price unavailable
BUT Sales Price valid
        ↓
Keep these records
        ↓
Plan to populate Original Price
        ↓
Change Column Profiling
Top 1000 rows → Entire dataset
        ↓
Prepare for next session
```

---

# 32. Key Power Query Concepts From This Session

## Transform Data

Used to open the **Power Query Editor** and perform data transformation/cleaning.

---

## Filters

Used to isolate records containing particular values such as:

```text
Not Available
```

This helps investigate the quality and structure of the data before deciding what to do with those records.

---

## Column Profiling

Provides information about the data in columns.

Default:

```text
Top 1000 rows
```

The instructor changes this to:

```text
Entire dataset
```

for a complete view.

---

## Data Types

Data types determine how Power BI treats the values.

For this dataset:

```text
Brand          → Text
Title          → Text
Original Price → Whole Number (desired)
Sales Price    → Whole Number (desired)
```

---

# 33. What Will Be Done in the Next Session?

The instructor ends the session by saying that the next session will focus on **solving the missing Original Price problem**.

The planned approach involves:

* Adding a **new column**
* Figuring out how to populate the missing values in Original Price
* Retaining useful records where Sales Price is available

The instructor also mentions that **DAX calculations** may be discussed in upcoming sessions to add additional columns.

---

# 34. Final Revision Notes

### Dataset

**Men's Shirts/T-Shirts data**

### Columns

```text
1. Brand
2. Title
3. Original Price
4. Sales Price
```

### Meaning

```text
Brand
→ Name of the brand

Title
→ Short product/article description

Original Price
→ Market/list/tag price

Sales Price
→ Actual selling price
```

### Main Problems Identified

**Problem 1:**

```text
Original Price → Text
Sales Price    → Text
```

Desired:

```text
Original Price → Whole Number
Sales Price    → Whole Number
```

**Problem 2:**

Missing values represented as:

```text
Not Available
```

### Critical filtering result

There are:

**16 records**

where:

```text
Original Price = Not Available
AND
Sales Price = Not Available
```

These records are considered unsuitable for analysis and should be removed.

### Important exception

If:

```text
Original Price = Not Available
Sales Price    = Valid
Brand          = Valid
Title          = Valid
```

the record should **not** be removed.

Instead, the missing Original Price should be handled/populated.

### Column Profiling

Default:

**Top 1000 rows**

Changed to:

**Entire dataset**

### Next step

**Add a new column and solve the missing Original Price problem.**
