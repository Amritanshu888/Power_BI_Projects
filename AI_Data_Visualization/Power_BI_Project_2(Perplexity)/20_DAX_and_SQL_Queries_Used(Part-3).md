## 1. Customer Gender Distribution

**Purpose:** Find how many unique customers belong to each gender.

### DAX

```DAX
Customer Count by Gender =
DISTINCTCOUNT(CombinedBankingDataset[CustomerID])
```

### Explanation

`DISTINCTCOUNT()` counts **unique values**.

So:

```DAX
DISTINCTCOUNT(CombinedBankingDataset[CustomerID])
```

means:

> Count the number of unique Customer IDs.

We use `DISTINCTCOUNT` instead of `COUNT` because the same customer may appear in multiple transactions.

### Example

Suppose the data is:

| CustomerID | Gender |
| ---------- | ------ |
| C101       | Male   |
| C102       | Female |
| C101       | Male   |
| C103       | Female |

`COUNT(CustomerID)` → 4

`DISTINCTCOUNT(CustomerID)` → **3**

When Gender is placed on the chart axis, Power BI calculates the distinct customers separately for Male/Female.

### Visual

**Donut Chart / Stacked Column**

* Axis/Legend → `Gender`
* Values → `Customer Count by Gender`

---

# 2. Customers by Age Group

This KPI actually requires **two calculated columns**.

## Step 1: Calculate Customer Age

```DAX
Customer Age =
DATEDIFF(
    CombinedBankingDataset[DateOfBirth],
    TODAY(),
    YEAR
)
```

### Explanation

`DATEDIFF()` calculates the difference between two dates.

Syntax:

```DAX
DATEDIFF(StartDate, EndDate, Interval)
```

Here:

```DAX
DATEDIFF(DateOfBirth, TODAY(), YEAR)
```

means:

> Calculate how many years have passed between the customer's date of birth and today.

`TODAY()` returns today's date.

`YEAR` tells DAX to calculate the difference in years.

### Example

If:

```text
DateOfBirth = 10-Jan-1998
Today = 11-Sep-2026
```

the customer age is approximately:

```text
28 years
```

---

## Step 2: Create Age Groups

```DAX
Customer Age Group =
SWITCH(
    TRUE(),
    [Customer Age] <= 25, "≤25",
    [Customer Age] <= 35, "26-35",
    [Customer Age] <= 50, "36-50",
    "51+"
)
```

### Important function: `SWITCH(TRUE())`

This is a very common DAX technique for creating categories based on conditions.

It works like an:

> **IF → ELSE IF → ELSE**

structure.

The logic is:

```text
Age <= 25       → ≤25
Age <= 35       → 26-35
Age <= 50       → 36-50
Otherwise       → 51+
```

### Example

| Age | Age Group |
| --: | --------- |
|  22 | ≤25       |
|  25 | ≤25       |
|  30 | 26-35     |
|  35 | 26-35     |
|  42 | 36-50     |
|  50 | 36-50     |
|  61 | 51+       |

### Visual

**Column Chart / Histogram**

* Axis → `Customer Age Group`
* Values → Customer Count

---

# 3. Accounts by Account Type

### DAX

```DAX
Account Count by Type =
COUNT(CombinedBankingDataset[Account_AccountID])
```

### Explanation

`COUNT()` counts the number of **non-blank numeric values** in a column.

So this:

```DAX
COUNT(CombinedBankingDataset[Account_AccountID])
```

counts the number of account IDs.

### Visual

**Clustered Bar Chart / Treemap**

* Axis/Group → `AccountType`
* Values → `Account Count by Type`

For example:

| Account Type | Count |
| ------------ | ----: |
| Savings      |   450 |
| Current      |   250 |
| Salary       |   150 |

This tells us the distribution of accounts by type.

---

# 4. Transaction Volume Trend

### DAX

```DAX
Transactions by Month =
CALCULATE(
    COUNT(CombinedBankingDataset[TransactionID]),
    ALLEXCEPT(
        CombinedBankingDataset,
        CombinedBankingDataset[TransactionDate].[Month]
    )
)
```

This one contains two important functions:

* `CALCULATE()`
* `ALLEXCEPT()`

---

## `COUNT()`

```DAX
COUNT(CombinedBankingDataset[TransactionID])
```

Counts transactions.

---

## `CALCULATE()`

`CALCULATE()` is one of the **most important DAX functions**.

It means:

> Calculate an expression after modifying the filter context.

Here the expression is:

```DAX
COUNT(TransactionID)
```

---

## `ALLEXCEPT()`

```DAX
ALLEXCEPT(
    CombinedBankingDataset,
    CombinedBankingDataset[TransactionDate].[Month]
)
```

means:

> Remove filters from the table except the specified Month filter.

Therefore, the measure calculates transaction counts while keeping the **month context**.

### Visual

**Line Chart / Area Chart**

* X-axis → Month
* Y-axis → `Transactions by Month`

This lets you see whether transaction activity is increasing or decreasing over time.

---

# 5. Transaction Amount by Account Type

The file uses:

```DAX
SUM(CombinedBankingDataset[Amount])
```

### Explanation

`SUM()` simply adds all values in the `Amount` column.

For example:

```text
1000
2500
1500
```

Result:

```text
SUM = 5000
```

When you put `AccountType` on the axis, Power BI automatically calculates the sum separately for each account type.

### Visual

**Stacked Column Chart**

* Axis → `AccountType`
* Values → `SUM(Amount)`

---

# 6. Transactions by Type

The file specifies:

```DAX
COUNT(CombinedBankingDataset[TransactionID])
```

### Explanation

This counts transactions.

Put:

```text
TransactionType
```

on the Axis/Legend.

For example:

| Transaction Type | Transactions |
| ---------------- | -----------: |
| Credit           |          650 |
| Debit            |          850 |

Power BI calculates the count separately for each transaction type.

### Visual

**Pie Chart / Stacked Column**

---

# 7. Monthly Transaction Amount

### DAX

```DAX
Monthly Transaction Amount =
CALCULATE(
    SUM(CombinedBankingDataset[Amount]),
    ALLEXCEPT(
        CombinedBankingDataset,
        CombinedBankingDataset[TransactionDate].[Month]
    )
)
```

Let's break it down.

### `SUM()`

```DAX
SUM(CombinedBankingDataset[Amount])
```

calculates the total transaction amount.

### `CALCULATE()`

Allows us to modify the filtering applied to that calculation.

### `ALLEXCEPT()`

Keeps the **Month** filter while removing other filters from the table.

So the overall meaning is:

> Calculate the total transaction amount for each month.

### Visual

**Line Chart / Area Chart**

* X-axis → Month
* Y-axis → `Monthly Transaction Amount`

Example:

| Month |    Amount |
| ----- | --------: |
| Jan   | ₹5,00,000 |
| Feb   | ₹6,20,000 |
| Mar   | ₹7,10,000 |

This is useful for identifying monthly transaction trends.

---

# 8. Top N Customers by Transaction Value

The file uses this measure:

```DAX
Total by Customer =
CALCULATE(
    SUM(CombinedBankingDataset[Amount]),
    ALLEXCEPT(
        CombinedBankingDataset,
        CombinedBankingDataset[CustomerID]
    )
)
```

### What does it mean?

First:

```DAX
SUM(CombinedBankingDataset[Amount])
```

calculates total transaction amount.

Then:

```DAX
ALLEXCEPT(..., CustomerID)
```

keeps the Customer ID filter.

Therefore:

> Calculate the total transaction value for each customer.

### Example

| Customer | Total Transaction Value |
| -------- | ----------------------: |
| C101     |               ₹8,50,000 |
| C102     |               ₹7,20,000 |
| C103     |               ₹5,80,000 |
| C104     |               ₹4,10,000 |

Then we can use the **Top N filter** in Power BI to show, for example, the top 5 customers.

### Visual

**Bar Chart**

* Axis → Customer Name / Customer ID
* Values → `Total by Customer`
* Filter → Top N

### Important

There is **no special Top N DAX required here**.

You create the measure and then use Power BI's:

> Filters → Top N

---

# 9. Average Account Balance

### DAX

```DAX
Average Balance =
AVERAGE(CombinedBankingDataset[Balance])
```

### Explanation

`AVERAGE()` calculates the arithmetic mean.

Formula:

```text
Average = Sum of values / Number of values
```

Example:

```text
10,000
20,000
30,000
```

Average:

```text
(10,000 + 20,000 + 30,000) / 3
= 20,000
```

Therefore:

```DAX
AVERAGE(CombinedBankingDataset[Balance])
```

gives the average account balance.

### Visual

**Column Chart / Gauge**

---

# 10. Total Balance by Account Type

### DAX

```DAX
Total Balance =
SUM(CombinedBankingDataset[Balance])
```

### Explanation

This adds all account balances.

When `AccountType` is placed on the axis, Power BI automatically calculates the total separately for each account type.

Example:

| Account Type | Total Balance |
| ------------ | ------------: |
| Savings      |    ₹50,00,000 |
| Current      |    ₹35,00,000 |
| Salary       |    ₹20,00,000 |

### Visual

**Clustered Bar / Column Chart**

* Axis → `AccountType`
* Values → `Total Balance`

---

# 11. Inactive Accounts — Last 90 Days

This is the most advanced DAX expression in your file.

### DAX

```DAX
Inactive Accounts =
CALCULATE(
    DISTINCTCOUNT(CombinedBankingDataset[Account_AccountID]),
    FILTER(
        VALUES(CombinedBankingDataset[Account_AccountID]),
        CALCULATE(
            MAX(CombinedBankingDataset[TransactionDate])
        ) < TODAY() - 90
    )
)
```

Let's understand it step by step.

---

## Step 1 — `DISTINCTCOUNT()`

```DAX
DISTINCTCOUNT(
    CombinedBankingDataset[Account_AccountID]
)
```

Counts unique accounts.

---

## Step 2 — `VALUES()`

```DAX
VALUES(CombinedBankingDataset[Account_AccountID])
```

returns the unique account IDs currently being considered.

Think:

> Give me a list of unique accounts.

---

## Step 3 — `FILTER()`

```DAX
FILTER(
    VALUES(CombinedBankingDataset[Account_AccountID]),
    condition
)
```

`FILTER()` keeps only the rows that satisfy a condition.

Here, the condition is:

```DAX
CALCULATE(
    MAX(CombinedBankingDataset[TransactionDate])
) < TODAY() - 90
```

---

## Step 4 — `MAX(TransactionDate)`

```DAX
MAX(CombinedBankingDataset[TransactionDate])
```

finds the **latest transaction date** for an account.

For example:

```text
Account A → latest transaction = 01-Jan-2026
Account B → latest transaction = 01-Sep-2026
```

---

## Step 5 — `TODAY() - 90`

```DAX
TODAY() - 90
```

means:

> The date 90 days before today.

So if today were September 11:

```text
September 11 - 90 days
≈ June 13
```

---

## Step 6 — Compare the dates

```DAX
MAX(TransactionDate) < TODAY() - 90
```

means:

> The account's latest transaction happened more than 90 days ago.

If yes → **Inactive**

If no → **Active**

---

## Step 7 — Count those accounts

Finally:

```DAX
DISTINCTCOUNT(Account_AccountID)
```

counts the inactive accounts.

### Simple example

Suppose:

| Account | Latest Transaction |
| ------- | ------------------ |
| A101    | Jan 1              |
| A102    | Sep 1              |
| A103    | Mar 10             |
| A104    | Aug 20             |

If the 90-day cutoff is June 13:

* A101 → inactive
* A102 → active
* A103 → inactive
* A104 → active

Therefore:

```text
Inactive Accounts = 2
```

### Visual

**Clustered Bar Chart / Table**

This KPI is useful for identifying accounts that haven't been used recently.

---

# ⭐ Important DAX Functions From Your Files

These are the functions you should focus on learning:

| DAX Function      | Meaning                               | Used for                      |
| ----------------- | ------------------------------------- | ----------------------------- |
| `DISTINCTCOUNT()` | Counts unique values                  | Unique customers/accounts     |
| `COUNT()`         | Counts non-blank numeric values       | Transactions/accounts         |
| `SUM()`           | Adds values                           | Transaction amount/balance    |
| `AVERAGE()`       | Calculates average                    | Average balance               |
| `DATEDIFF()`      | Calculates difference between dates   | Customer age                  |
| `TODAY()`         | Returns today's date                  | Age/inactivity calculations   |
| `SWITCH()`        | Tests multiple conditions             | Age groups                    |
| `TRUE()`          | Makes `SWITCH` behave like IF/ELSE IF | Conditional categories        |
| `CALCULATE()`     | Changes filter context                | Advanced calculations         |
| `ALLEXCEPT()`     | Removes filters except specified ones | Monthly/customer calculations |
| `FILTER()`        | Filters a table based on a condition  | Inactive accounts             |
| `VALUES()`        | Returns unique values                 | Filtering unique accounts     |
| `MAX()`           | Returns maximum value                 | Latest transaction date       |

## 🧠 The most important concepts to remember

### 1. Aggregation functions

```DAX
SUM()
COUNT()
DISTINCTCOUNT()
AVERAGE()
MAX()
```

These calculate numbers from your data.

### 2. Date functions

```DAX
TODAY()
DATEDIFF()
```

These work with dates.

### 3. Conditional functions

```DAX
SWITCH()
TRUE()
```

These are useful for creating categories such as:

```text
≤25
26-35
36-50
51+
```

### 4. Filter-context functions

```DAX
CALCULATE()
FILTER()
ALLEXCEPT()
VALUES()
```

These are **very important for Power BI DAX** because they control **which rows are included in a calculation**.

A good learning order is:

**SUM/COUNT → DISTINCTCOUNT/AVERAGE → DATEDIFF/TODAY → SWITCH → CALCULATE → FILTER/VALUES/ALLEXCEPT**

That progression will make the more advanced measures, especially **Monthly Transaction Amount, Top N Customers, and Inactive Accounts**, much easier to understand.
