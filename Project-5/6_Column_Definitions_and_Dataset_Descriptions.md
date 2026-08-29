# Loan Default Dataset — Detailed Overview & Column Definitions

## 1. Introduction

This session explains the **Loan Default dataset**, its purpose, and the meaning of each column.

The dataset will be used throughout the project to:

* Analyze borrowers and their financial profiles.
* Analyze loan characteristics.
* Analyze repayment/default behavior.
* Identify patterns associated with loan defaults.
* Build a **Power BI report/dashboard**.
* Help bank officials make better **data-driven lending decisions**.

---

# 2. Loan Default Dataset — Description

The **Loan Default dataset** contains information about borrowers who have applied for loans.

### What does one record represent?

Each record/row represents:

> **One borrower's information related to a loan application.**

The dataset contains information about:

1. Borrower's personal characteristics
2. Financial status
3. Loan characteristics
4. Existing credit information
5. Employment information
6. Repayment/default behavior

---

# 3. Business Problem

The business scenario assumes that:

> **Loans were actually disbursed to all the borrowers present in the dataset.**

After the loans were disbursed, a large number of borrowers defaulted.

Therefore, the bank wants to analyze historical borrower and loan data to understand:

* Who is more likely to default?
* What borrower characteristics are associated with defaults?
* What financial characteristics are associated with defaults?
* Which types of borrowers should potentially be approved in the future?
* Which borrowers may represent higher lending risk?

---

# 4. Objective of the Power BI Report

As a **Power BI Developer/Data Analyst**, the responsibility is to analyze the data and create a report/dashboard that can help bank officials make better decisions.

The ultimate objective is to help the bank decide:

> **To whom should the bank provide loans in the future, and to whom should it avoid providing loans because of higher default risk?**

The report should help officials make:

* Data-driven decisions
* Faster decisions
* Better lending decisions

The idea is to convert historical loan data into useful business insights.

---

# 5. Dataset Columns

The dataset contains several columns related to:

* Loan identification
* Borrower demographics
* Financial information
* Credit history
* Employment
* Loan characteristics
* Existing financial obligations
* Loan purpose
* Default behavior
* Loan date

Let's understand each column.

---

# 6. Loan ID

### Column

**Loan ID**

### Definition

Loan ID is a **unique identifier for each loan**.

It allows us to uniquely identify individual loan records.

### Example

```text
Loan ID
10001
10002
10003
```

Each loan should have its own unique identifier.

### Purpose

Loan ID is useful for:

* Identifying individual loans
* Counting loans
* Tracking records
* Creating relationships if required

---

# 7. Age

### Column

**Age**

### Definition

Age represents the **borrower's age at the time the loan was issued**.

### Example

```text
25
35
42
50
```

### Business significance

Age can potentially be analyzed against:

* Loan amount
* Income
* Credit score
* Default behavior

For example, we may want to investigate whether default rates differ across different age groups.

---

# 8. Income

### Column

**Income**

### Definition

Income represents the **borrower's annual income**.

### Example

```text
₹5,00,000
₹8,00,000
₹12,00,000
```

The actual currency/unit depends on the dataset.

### Business significance

Income is an important indicator of the borrower's financial capacity.

It can be compared with:

* Loan amount
* Debt-to-income ratio
* Credit score
* Default status

A borrower with higher income may have greater capacity to repay a loan, although income alone does not determine default risk.

---

# 9. Loan Amount

### Column

**Loan Amount**

### Definition

Loan Amount represents the **total amount of loan requested or approved for the borrower**.

### Example

```text
10000
25000
50000
100000
```

### Business significance

Loan amount can be analyzed against:

* Income
* Credit score
* DTI ratio
* Interest rate
* Default status

A useful analysis could be determining whether larger loan amounts are associated with higher default rates.

---

# 10. Credit Score

### Column

**Credit Score**

### Definition

Credit Score is a numerical representation of the borrower's **creditworthiness**.

The lecture states that it typically ranges from:

> **300 to 850**

### Interpretation

Generally:

* Lower credit score → Lower creditworthiness
* Higher credit score → Higher creditworthiness

A higher credit score generally indicates that the borrower is more likely to repay their debt.

### Business significance

Credit score is an important factor for lending decisions.

It can be analyzed against:

* Default status
* Loan amount
* Income
* Interest rate
* Loan term

---

# 11. Months Employed

### Column

**Months Employed**

### Definition

This column represents the **number of months the borrower has been employed at their current job/current employer**.

### Example

```text
12 months
24 months
60 months
120 months
```

### Business significance

Employment duration can provide an indication of employment stability.

It can be analyzed against:

* Income
* Loan amount
* Default status
* Credit score

---

# 12. Number of Credit Lines

### Column

**Number of Credit Lines**

### Definition

This represents the **total number of active credit lines** that the borrower already has at the time of the loan application.

### What are credit lines?

Credit lines can include:

* Credit cards
* Existing loans
* Other forms of active credit

### Example

A borrower might have:

```text
2 credit cards
1 existing loan
```

Therefore, their number of active credit lines could be:

```text
3
```

### Business significance

A higher number of active credit lines may indicate that the borrower already has multiple financial obligations.

This can be analyzed against:

* Income
* DTI ratio
* Default
* Loan amount

---

# 13. Interest Rate

### Column

**Interest Rate**

### Definition

Interest Rate represents the rate at which interest is charged on the borrowed loan amount.

The lecture refers to it as the:

> **Annual Percentage Rate (APR)**

It is generally expressed as a percentage.

### Example

```text
5%
8%
10%
15%
```

### Business significance

Interest rate affects the overall cost of borrowing.

It can be analyzed against:

* Credit score
* Loan amount
* Default status
* Loan term

---

# 14. Loan Term

### Column

**Loan Term**

### Definition

Loan Term represents the **length of time, in months, over which the loan is expected to be repaid**.

### Example

```text
12 months
24 months
36 months
60 months
```

### Business significance

Loan term can affect the borrower's repayment burden.

It can be analyzed against:

* Loan amount
* Interest rate
* Default status
* Income

---

# 15. DTI Ratio

### Column

**DTI Ratio**

DTI stands for:

> **Debt-to-Income Ratio**

### Definition

DTI measures the borrower's **debt payments relative to their income**.

Conceptually:

**DTI = Debt Payments / Income**

Depending on how the dataset defines the field, it may be represented as a ratio or percentage.

### Interpretation

A **higher DTI ratio** generally indicates greater financial stress.

In simple terms:

```text
Higher DTI
     ↓
More income committed to debt
     ↓
Greater financial pressure
     ↓
Potentially greater difficulty repaying additional debt
```

### Business significance

DTI is an important metric for assessing whether a borrower has enough income relative to their existing debt obligations.

Bank officials can use DTI as one of the factors when assessing lending risk.

---

# 16. Education

### Column

**Education**

### Definition

Education represents the **highest level of education completed by the borrower**.

Examples mentioned in the lecture include:

* High school
* Bachelor's degree
* Master's degree

There may be other education categories depending on the dataset.

### Business significance

Education can be used for demographic analysis and can potentially be compared with:

* Income
* Employment
* Loan amount
* Default behavior

---

# 17. Employment Type

### Column

**Employment Type**

### Definition

Employment Type indicates the type of employment in which the borrower is engaged.

Examples include:

* Full-time
* Part-time
* Self-employed

There may be other categories in the dataset.

### Business significance

Employment type can provide insight into the borrower's employment situation.

It can be analyzed against:

* Income
* Months employed
* Loan amount
* Default status

---

# 18. Marital Status

### Column

**Marital Status**

### Definition

Marital Status indicates the borrower's marital status.

Examples include:

* Single
* Married
* Divorced

### Business significance

It can be used for demographic analysis and can potentially be compared with:

* Income
* Dependents
* Loan amount
* Default behavior

---

# 19. Has Mortgage

### Column

**Has Mortgage**

### Definition

This is a **Yes/No indicator** that tells whether the borrower currently has an existing mortgage on a property.

Possible values can be represented as:

```text
Yes
No
```

or equivalent binary values.

### Interpretation

* **Yes** → Borrower has an existing mortgage.
* **No** → Borrower does not have an existing mortgage.

### Business significance

Having an existing mortgage represents an additional financial obligation that can be considered while analyzing the borrower's financial situation.

---

# 20. Has Dependents

### Column

**Has Dependents**

### Definition

This is another **Yes/No indicator**.

It tells whether the borrower has dependents, such as:

* Children
* Family members
* Other people financially dependent on the borrower

### Interpretation

* **Yes** → Borrower has dependents.
* **No** → Borrower does not have dependents.

### Business significance

The number/type of financial responsibilities may be relevant when analyzing the borrower's financial situation and repayment behavior.

---

# 21. Loan Purpose

### Column

**Loan Purpose**

### Definition

Loan Purpose represents the **primary reason for taking out the loan**.

Examples mentioned include:

* Buying a home
* Debt consolidation
* Education

There can be other purposes depending on the dataset.

### Business significance

Different loan purposes may have different risk profiles.

For example, the bank could analyze:

```text
Loan Purpose
      ↓
Number of Loans
      ↓
Default Rate
```

This can help identify whether particular loan purposes have higher default rates.

---

# 22. Has Cosigner

### Column

**Has Cosigner**

### Definition

This is a **Yes/No indicator** showing whether the borrower has a cosigner for the loan.

### What is a cosigner?

A cosigner is someone who agrees to take responsibility for the loan if the primary borrower is unable to repay it.

In simple terms, a cosigner acts as a form of **additional financial assurance/guarantee** for the lender.

### Possible values

```text
Yes
No
```

### Business significance

The presence of a cosigner can potentially be analyzed against:

* Default rate
* Loan amount
* Credit score
* Income

---

# 23. Default

### Column

**Default**

### Definition

Default indicates whether the borrower **defaulted on the loan or failed to make timely payments**.

The lecture states that it can be represented using:

* Yes/No
* 0/1

For example:

```text
0 → No default
1 → Default
```

The exact encoding should be confirmed from the dataset.

### Business significance

This is one of the **most important columns in the dataset**.

It represents the outcome that the bank is interested in analyzing.

The report can use this column to calculate metrics such as:

* Number of defaults
* Default rate
* Default rate by age
* Default rate by income
* Default rate by credit score
* Default rate by loan purpose
* Default rate by employment type
* Default rate by DTI ratio

---

# 24. Loan Date

### Column

**Loan Date**

### Definition

Loan Date represents the **date on which the loan was issued/originated**.

### Business significance

Loan Date allows us to perform time-based analysis.

For example:

```text
Loan Date
    ↓
Month
    ↓
Quarter
    ↓
Year
```

This can help identify trends in:

* Loan applications
* Loan issuance
* Defaults
* Default rates over time

---

# 25. Complete Column Reference

| Column                     | Meaning                                                             |
| -------------------------- | ------------------------------------------------------------------- |
| **Loan ID**                | Unique identifier for each loan                                     |
| **Age**                    | Borrower's age when the loan was issued                             |
| **Income**                 | Borrower's annual income                                            |
| **Loan Amount**            | Total loan amount requested/approved                                |
| **Credit Score**           | Numerical measure of borrower's creditworthiness, typically 300–850 |
| **Months Employed**        | Number of months employed at the current job/employer               |
| **Number of Credit Lines** | Number of active credit lines such as credit cards and loans        |
| **Interest Rate**          | Annual interest rate/APR charged on the loan                        |
| **Loan Term**              | Loan repayment period in months                                     |
| **DTI Ratio**              | Debt-to-income ratio; debt payments relative to income              |
| **Education**              | Highest level of education completed                                |
| **Employment Type**        | Type of employment, such as full-time, part-time, self-employed     |
| **Marital Status**         | Borrower's marital status                                           |
| **Has Mortgage**           | Whether borrower has an existing mortgage                           |
| **Has Dependents**         | Whether borrower has dependents                                     |
| **Loan Purpose**           | Primary reason for taking the loan                                  |
| **Has Cosigner**           | Whether borrower has a cosigner                                     |
| **Default**                | Whether borrower defaulted/failed to make timely payments           |
| **Loan Date**              | Date on which the loan was issued/originated                        |

---

# 26. Categorizing the Columns

A useful way to understand the dataset is to group the columns by business category.

### A. Loan Identification

* Loan ID
* Loan Date

### B. Demographic Information

* Age
* Education
* Marital Status
* Has Dependents

### C. Employment Information

* Months Employed
* Employment Type
* Income

### D. Credit/Financial Information

* Credit Score
* Number of Credit Lines
* DTI Ratio
* Has Mortgage

### E. Loan Characteristics

* Loan Amount
* Interest Rate
* Loan Term
* Loan Purpose
* Has Cosigner

### F. Outcome

* Default

This categorization will be useful when designing Power BI visuals later.

---

# 27. Most Important Business Column — Default

Among all the columns, **Default** is particularly important because it represents the outcome the bank wants to understand.

The central business question is essentially:

> **What characteristics are associated with borrowers who default?**

For example, we may want to investigate relationships such as:

```text
Credit Score → Default
Income → Default
DTI Ratio → Default
Loan Amount → Default
Loan Purpose → Default
Employment Type → Default
Interest Rate → Default
```

These analyses can eventually help bank officials make better lending decisions.

---

# 28. Potential Power BI Analysis

Once the data is cleaned, several useful analyses can be created.

### Default by Credit Score

Analyze whether lower credit scores have higher default rates.

### Default by Income

Compare default behavior across different income ranges.

### Default by DTI Ratio

Analyze whether higher debt-to-income ratios correspond to higher default rates.

### Default by Loan Purpose

Compare default rates for:

* Education
* Home
* Debt consolidation
* Other purposes

### Default by Employment Type

Compare default behavior among:

* Full-time employees
* Part-time employees
* Self-employed borrowers

### Default by Loan Amount

Determine whether loan size is associated with default behavior.

### Default Over Time

Use **Loan Date** to analyze how loan/default behavior changes over time.

---

# 29. Business Decision-Making

The final purpose of these analyses is not simply to create charts.

The Power BI report should help bank officials answer practical questions such as:

* Which borrower profiles have higher default risk?
* Which financial indicators are associated with default?
* Which loan purposes show higher default rates?
* How does credit score affect default?
* How does DTI ratio affect default?
* Are borrowers with existing mortgages more likely to default?
* Does having a cosigner affect default behavior?
* Are there noticeable trends in default over time?

The ultimate goal is:

> **Use historical data to support better future lending decisions.**

---

# 30. Important Notes for the Upcoming Analysis

The lecture only introduces the columns in this session. Detailed analysis will be performed in the upcoming sessions.

The workflow will generally be:

```text
Loan Default Dataset
        ↓
Understand Columns
        ↓
Data Cleaning
        ↓
Data Transformation
        ↓
Data Analysis
        ↓
Power BI Visualizations
        ↓
Dashboard/Report
        ↓
Business Insights
        ↓
Data-Driven Lending Decisions
```

---

# 31. Key Interview Questions

### Q1. What is the Loan Default dataset about?

It contains information about borrowers who applied for loans, including their demographic, financial, employment, credit, loan, and repayment/default information.

### Q2. What does each row represent?

Each row represents information associated with a borrower and their loan application/loan.

### Q3. What is the main business objective?

To analyze historical loan data and identify patterns associated with default so that bank officials can make better future lending decisions.

### Q4. Which column represents the target/outcome?

**Default** represents whether the borrower defaulted or failed to make timely payments.

### Q5. What is DTI?

DTI stands for **Debt-to-Income Ratio** and measures debt payments relative to income.

### Q6. What does a high DTI generally indicate?

A high DTI generally indicates that a larger portion of the borrower's income is committed to debt payments and may indicate greater financial stress.

### Q7. What does Credit Score represent?

It is a numerical representation of a borrower's creditworthiness, typically ranging from **300 to 850** in the scale described in the lecture.

### Q8. What are credit lines?

Credit lines represent active credit facilities such as credit cards and loans that the borrower already has.

### Q9. What is a cosigner?

A cosigner is someone who agrees to take responsibility for the loan if the primary borrower cannot repay it.

### Q10. What does Loan Date represent?

It represents the date on which the loan was issued or originated.

---

# 32. Final Takeaways

* The **Loan Default dataset** contains borrower and loan-related information.
* Each record represents a borrower's loan information.
* The dataset contains demographic, financial, employment, credit, loan-characteristic, and repayment information.
* **Default** is a critical outcome column.
* **Credit Score** measures creditworthiness.
* **DTI Ratio** measures debt relative to income.
* **Months Employed** indicates employment duration.
* **Number of Credit Lines** represents active credit facilities.
* **Has Mortgage**, **Has Dependents**, and **Has Cosigner** are indicator variables.
* **Loan Purpose** identifies why the borrower took the loan.
* **Loan Date** enables time-based analysis.
* The ultimate goal is to build a **Power BI report** that helps bank officials make faster and better **data-driven lending decisions**.
* The detailed analysis and reporting will be covered in the upcoming sessions.
