# Power BI Project 2 — KPI, Visual & DAX Recommendation Planning

## 1. Session Objective

In this session, the instructor focuses on **planning the Power BI report before actually creating the visuals**.

The main objectives are:

1. Use the **Combined Banking Data Set** already imported into Power BI.
2. Extract all available column names from the combined dataset.
3. Provide those columns to **Perplexity** as context.
4. Ask Perplexity to recommend:

   * KPIs
   * Charts/visuals
   * DAX measures
   * KPI definitions/descriptions
5. Design a **two-page Power BI report**.
6. Refine the AI-generated recommendations so that the report does not rely heavily on Card visuals.
7. Generate **copyable KPI recommendation tables** for both report pages.
8. Download the recommendations as **CSV files** for later use.
9. Keep the dataset-generation/combined-dataset SQL code as a resource as well.

---

# 2. Background from the Previous Session

In the previous session:

* Data was created in SQL Server.
* The three banking tables were combined into a single table.
* The combined table was named:

**Combined Banking Data Set**

* This table was imported into Power BI Desktop.
* The instructor is now going to use this table to decide **what should actually be displayed in the Power BI report**.

The important idea is:

> Before creating Power BI visuals randomly, first identify the available columns and then use those columns to design meaningful KPIs, charts, and DAX measures.

---

# 3. Overall Workflow

The workflow followed in this lecture is:

```text
SQL Server
     ↓
Combined Banking Data Set
     ↓
Get all column names
     ↓
Copy column information/code
     ↓
Provide columns to Perplexity
     ↓
Ask for:
   • KPIs
   • Charts
   • DAX measures
   • KPI definitions
     ↓
Design 2-page report
     ↓
Review AI recommendations
     ↓
Improve visual variety
     ↓
Create KPI recommendation tables
     ↓
Download Page 1 CSV
     ↓
Download Page 2 CSV
```

---

# 4. Getting the Column Names from SQL Server

The instructor first goes to **SQL Server Management Studio (SSMS)**.

The purpose is to get the names of all the columns available in the **Combined Banking Data Set**.

The instructor mentions that the code used to create the combined dataset in the previous session also contains the names of all the columns.

### Why are the column names needed?

Perplexity needs to know:

* What data is available
* Which fields can be used for KPIs
* Which fields can be used for charts
* Which fields can be used in DAX calculations

For example, if the dataset contains:

```text
Customer ID
Customer Name
Date of Birth
Account ID
Account Type
Balance
Transaction ID
Transaction Date
Transaction Type
Amount
Currency
```

then the AI can suggest KPIs and visuals based specifically on those fields.

---

# 5. Copying the Column Information

### Step 1 — Go to SSMS

Open **SQL Server Management Studio**.

The instructor navigates to the SQL code used previously for creating the combined banking dataset.

### Step 2 — Copy the relevant code

The instructor copies the code containing the names of all the columns available in the combined dataset.

The instructor says that this code will also be provided in the **resource section of the lecture**.

Therefore, students can obtain the same code from the resources rather than manually recreating it.

---

# 6. Providing the Column Information to Perplexity

Next, the instructor opens **Perplexity**.

The copied SQL/column information is pasted into Perplexity.

The purpose is to give Perplexity enough context about the dataset.

The instructor initially asks Perplexity to:

* Take reference from the provided code.
* Suggest KPIs.
* Use the columns mentioned in the code.
* Recommend charts.
* Suggest DAX measures wherever required.

The important instruction is essentially:

> Take the reference from the provided code and suggest KPIs that can be created using the columns mentioned in the code. Also suggest recommended charts along with DAX measures wherever required.

---

# 7. Specifying That the Report Should Have Two Pages

The instructor then adds an important requirement:

> The Power BI report should contain **two pages**.

This is important because the AI should not simply generate a random collection of KPIs.

Instead, the KPIs and visuals should be organized into **two logical report pages**.

---

# 8. Initial AI Recommendation

Perplexity generates a complete recommendation for the two-page Power BI report.

The suggested structure is:

### Page 1

**Overall Banking Performance and Customer Profile**

### Page 2

**Transactions and Account Analysis**

These names provide a logical division of the banking analysis.

---

# 9. Page 1 — Overall Banking Performance and Customer Profile

The first page focuses on the overall performance of the banking dataset and customer-related information.

Perplexity recommends various:

* KPIs
* Visuals
* DAX measures

The instructor observes that many of the recommendations use a **Card visual**.

For example, Perplexity repeatedly recommends something like:

```text
KPI → Card visual
```

This is technically valid because Cards are commonly used for displaying:

* Total customers
* Total transactions
* Total balance
* Average balance
* Total transaction amount

However, using too many Cards can make a report visually repetitive.

---

# 10. Initial Visual Recommendations

The AI recommends different visual types, including:

### Card

Useful for displaying a single important number.

Example:

```text
Total Customers
1250
```

---

### Donut Chart

Useful for showing categorical distribution.

For example:

```text
Account Type
├── Savings
├── Current
└── Other
```

---

### Pie Chart

Can also be used for categorical proportions.

For example:

```text
Transaction Type
├── Credit
└── Debit
```

---

### Bar Chart

Useful for comparing categories.

For example:

```text
Account Type → Number of Accounts
```

---

### Column Chart

Useful for comparing values across categories or time periods.

For example:

```text
Month → Transaction Amount
```

---

### Histogram

Useful for examining the distribution of numerical data.

For example:

```text
Distribution of Account Balances
```

---

### Treemap

Useful for displaying hierarchical or categorical proportions using differently sized rectangles.

---

# 11. DAX Measures Suggested by Perplexity

Perplexity also generates **DAX measures** where calculations are required.

The instructor notes that sample DAX measures are available in the generated recommendation.

The DAX measures are intended to support the recommended KPIs and visuals.

For example, conceptually, a KPI could require:

```DAX
Total Amount = SUM('Combined Banking Data Set'[Amount])
```

or:

```DAX
Total Transactions = COUNTROWS('Combined Banking Data Set')
```

The exact DAX depends on the actual column names and the final KPI selected.

### Important point

The instructor does **not** immediately create all these measures.

At this stage, the goal is to use AI to **plan and recommend** the report components.

The actual DAX implementation will be done later.

---

# 12. Reviewing the First Page Recommendations

Perplexity provides a list of suggested KPIs for Page 1.

The instructor reviews these recommendations.

However, there is one concern:

> Almost everything is being recommended as a Card visual.

The instructor wants the report to contain **different types of visuals**.

This is important for creating a more visually appealing and interactive dashboard.

---

# 13. Refining the AI Prompt

Instead of accepting the initial recommendation, the instructor gives Perplexity additional instructions.

The instructor essentially says:

> For Page 1 KPIs, recommend KPIs that allow me to create different kinds of visuals.

The instructor specifically points out:

> Mostly you have suggested Card visuals, and I don't like that approach.

This is an important lesson when using AI tools:

### Don't blindly accept the first AI output.

If the recommendation isn't suitable:

1. Identify what is wrong.
2. Give additional constraints.
3. Ask the AI to regenerate/refine the recommendation.

---

# 14. Improved Visual Variety

After providing the additional instruction, Perplexity generates a more diverse set of visual recommendations.

Examples include:

| Visual               | Possible Use                   |
| -------------------- | ------------------------------ |
| Donut Chart          | Category distribution          |
| Stacked Column Chart | Category comparison            |
| Column Chart         | Category/value comparison      |
| Histogram            | Numerical distribution         |
| Bar Chart            | Ranking/comparison             |
| Treemap              | Proportional category analysis |

This creates greater visual variety.

---

# 15. Why Visual Variety Matters

Using only Cards would make a dashboard look something like:

```text
┌────────┐ ┌────────┐ ┌────────┐
│  KPI 1 │ │  KPI 2 │ │  KPI 3 │
└────────┘ └────────┘ └────────┘

┌────────┐ ┌────────┐
│  KPI 4 │ │  KPI 5 │
└────────┘ └────────┘
```

Although technically useful, this does not provide much analytical visualization.

A better dashboard might combine:

```text
KPI
  +
Donut
  +
Bar Chart
  +
Column Chart
  +
Histogram
  +
Treemap
```

This allows the user to understand:

* Overall values
* Distributions
* Comparisons
* Trends
* Category relationships

---

# 16. AI Recommendation for Page 2

Perplexity also recommends the second report page.

The proposed name is:

## Transactions and Account Analysis

This page focuses more specifically on:

* Transactions
* Accounts
* Transaction-related KPIs
* Account-related KPIs

The AI provides:

* KPI recommendations
* DAX measures
* Recommended charts
* KPI descriptions/definitions

---

# 17. KPI Definitions

Another useful part of the AI output is the **description/definition of each KPI**.

This is important because it tells us what each KPI actually represents.

For example, a KPI recommendation table could conceptually look like:

| KPI                      | Description                  | Visual       | DAX              |
| ------------------------ | ---------------------------- | ------------ | ---------------- |
| Total Transactions       | Total number of transactions | Column Chart | `COUNTROWS(...)` |
| Total Transaction Amount | Total value of transactions  | Bar Chart    | `SUM(...)`       |

The exact KPIs and DAX should come from the generated recommendation file.

---

# 18. Asking Perplexity to Create Copyable Tables

The instructor then gives another instruction.

Instead of having the recommendations displayed as scattered text, the instructor wants them in a **table format that can be directly copied**.

This makes the recommendations easier to:

* Save
* Download
* Use during Power BI development
* Share
* Reference later

---

# 19. Final KPI Table Structure

The instructor initially considers three columns:

1. KPI
2. Visual
3. DAX

Then decides to include a fourth column:

4. Description

Therefore, the final table structure becomes:

| KPI | Description | Visual | DAX |
| --- | ----------- | ------ | --- |

This structure is important because it combines the four pieces of information required to implement the dashboard.

### Column 1 — KPI

The name of the KPI.

Example:

```text
Total Transactions
```

### Column 2 — Description

Explains what the KPI means.

Example:

```text
Total number of transactions in the dataset.
```

### Column 3 — Visual

Specifies which Power BI visual should be used.

Example:

```text
Bar Chart
```

### Column 4 — DAX

Provides the DAX calculation needed to generate the KPI.

Example:

```DAX
Total Transactions = COUNTROWS('Combined Banking Data Set')
```

---

# 20. Generating the Final Tables

The instructor asks Perplexity to create recommendation tables for:

### Page 1

Overall Banking Performance and Customer Profile

### Page 2

Transactions and Account Analysis

Both pages should follow the same four-column structure:

```text
KPI
Description
Visual
DAX
```

The instructor then waits for Perplexity to generate the output.

---

# 21. Page 1 Table

Perplexity generates the final table for Page 1.

The instructor reviews it and confirms that it is suitable.

The table can now be used as the blueprint for creating Page 1 in Power BI.

---

# 22. Downloading Page 1 Recommendations

The instructor then downloads the Page 1 table.

### Steps

1. Locate the Page 1 recommendation table in Perplexity.
2. Click the **Download** button.
3. Choose/download it as a **CSV** file.
4. Save the file.

The CSV will contain the KPI recommendations in tabular form.

---

# 23. Downloading Page 2 Recommendations

The same process is repeated for Page 2.

### Steps

1. Locate the Page 2 recommendation table.
2. Click the **Download** button.
3. Download it as a **CSV**.
4. Save the file.

Therefore, there are now two CSV files:

```text
Page 1 KPI Recommendations.csv
Page 2 KPI Recommendations.csv
```

The exact filenames may vary.

---

# 24. Resources Provided by the Instructor

The instructor says that the following resources will be provided in the lecture's **resource section**:

### Resource 1 — Page 1 KPI Recommendations

Contains recommendations for:

**Overall Banking Performance and Customer Profile**

---

### Resource 2 — Page 2 KPI Recommendations

Contains recommendations for:

**Transactions and Account Analysis**

---

### Resource 3 — Combined Dataset SQL Code

The SQL code used to create the:

**Combined Banking Data Set**

will also be provided.

This is useful if students need to:

* Recreate the dataset
* Review the column names
* Understand the source data
* Rebuild the project

---

# 25. Important Lesson: Using AI for Power BI Planning

One of the most important lessons from this session is that AI can be used not only for writing DAX but also for **dashboard planning**.

The workflow is:

```text
Dataset
   ↓
Identify columns
   ↓
Give column context to AI
   ↓
Ask for KPI recommendations
   ↓
Ask for visual recommendations
   ↓
Ask for DAX measures
   ↓
Review recommendations
   ↓
Provide feedback
   ↓
Regenerate/improve
   ↓
Export final recommendation
   ↓
Build report in Power BI
```

---

# 26. Why the Column Names Must Be Provided

The AI cannot reliably recommend meaningful KPIs without knowing what fields exist.

For example, suppose the dataset contains:

```text
Customer ID
Account ID
Account Type
Balance
Transaction Date
Transaction Type
Amount
Currency
```

Then AI can reason about:

### Customer analysis

```text
Number of customers
```

### Account analysis

```text
Number of accounts
Accounts by type
```

### Transaction analysis

```text
Transaction count
Transaction amount
Debit vs Credit
```

### Time analysis

```text
Transactions by month
Transaction amount over time
```

The available columns therefore determine what can realistically be visualized.

---

# 27. Why DAX Is Included in the Recommendation

Some KPIs cannot simply be displayed directly from a column.

A calculation may be required.

For example:

### Count of transactions

```DAX
Total Transactions =
COUNTROWS('Combined Banking Data Set')
```

### Total transaction amount

```DAX
Total Transaction Amount =
SUM('Combined Banking Data Set'[Amount])
```

### Average transaction amount

```DAX
Average Transaction Amount =
AVERAGE('Combined Banking Data Set'[Amount])
```

These are examples of the kind of calculations that can be requested from AI.

**Important:** The actual column names in your Power BI model must match the DAX expressions.

---

# 28. Card vs Other Visuals

The lecture emphasizes an important dashboard-design consideration.

## Card

Best when you want to highlight a single number.

Example:

```text
Total Customers
10,000
```

## Bar Chart

Best for comparing categories.

```text
Account Type
Savings       █████████
Current       █████
```

## Column Chart

Good for categorical or time-based comparisons.

```text
Jan █████
Feb ███████
Mar █████████
```

## Donut Chart

Good for showing composition/proportion.

```text
Credit vs Debit
```

## Histogram

Good for understanding the distribution of numerical values.

```text
Transaction Amount Distribution
```

## Treemap

Good for comparing proportions across multiple categories.

---

# 29. Key Power BI Project Architecture So Far

At this point, the overall project flow is:

```text
             SQL Server
                 │
        ┌────────┴────────┐
        │                 │
    Customers          Accounts
        │                 │
        └───────┐ ┌───────┘
                │ │
             Transactions
                │
                ↓
      Combined Banking Data Set
                │
                ↓
          Power BI Desktop
                │
                ↓
       Data Cleaning / Modeling
                │
                ↓
       KPI + Visual Planning
                │
        ┌───────┴────────┐
        ↓                ↓
      Page 1           Page 2
        │                │
 Overall Banking     Transactions &
 Performance +       Account Analysis
 Customer Profile
```

---

# 30. Detailed Step-by-Step Procedure

## Step 1 — Open SQL Server Management Studio

Open SSMS.

---

## Step 2 — Locate the combined dataset SQL

Find the SQL code that was previously used to create the **Combined Banking Data Set**.

---

## Step 3 — Copy the column information

Copy the relevant code containing the columns available in the combined dataset.

---

## Step 4 — Open Perplexity

Open Perplexity and paste the copied code.

---

## Step 5 — Ask for KPI recommendations

Tell Perplexity to use the provided columns to recommend:

* KPIs
* Charts
* DAX measures

---

## Step 6 — Specify two report pages

Tell Perplexity that the Power BI report should contain **two pages**.

---

## Step 7 — Review the first output

Review:

* Page names
* KPIs
* Charts
* DAX measures
* Definitions

---

## Step 8 — Identify problems with the recommendation

The instructor notices that too many KPIs are being recommended as **Card visuals**.

---

## Step 9 — Refine the prompt

Ask Perplexity to recommend KPIs that support **different types of visuals**.

---

## Step 10 — Review the improved recommendation

Check that the recommendation includes a good mix such as:

* Donut
* Stacked column
* Column
* Bar
* Histogram
* Treemap
* Other appropriate visuals

---

## Step 11 — Ask for tables

Tell Perplexity to format the recommendations into directly copyable tables.

---

## Step 12 — Use four columns

The final table should contain:

```text
KPI
Description
Visual
DAX
```

---

## Step 13 — Generate Page 1 table

Generate the KPI table for:

**Overall Banking Performance and Customer Profile**

---

## Step 14 — Generate Page 2 table

Generate the KPI table for:

**Transactions and Account Analysis**

---

## Step 15 — Download Page 1

Use the **Download** button and download the table as CSV.

---

## Step 16 — Download Page 2

Repeat the same process and download the second table as CSV.

---

## Step 17 — Keep the SQL resource

Use the provided combined dataset SQL code whenever you need to recreate or understand the dataset.

---

# 31. Important Concepts to Remember

| Concept              | Meaning                                                                |
| -------------------- | ---------------------------------------------------------------------- |
| KPI                  | Key Performance Indicator used to measure an important business metric |
| DAX                  | Power BI's formula language used for calculations and measures         |
| Card                 | Visual generally used for displaying a single KPI value                |
| Bar Chart            | Used primarily for category comparison                                 |
| Column Chart         | Used for category/time comparison                                      |
| Donut Chart          | Used to show category proportions                                      |
| Histogram            | Used to analyze numerical distributions                                |
| Treemap              | Used to compare proportional values across categories                  |
| CSV                  | Tabular file format used here to save KPI recommendations              |
| AI-assisted planning | Using AI to design KPIs, visuals, and DAX before implementation        |

---

# 32. Key Learning: Prompt Refinement

This lecture demonstrates a very useful AI workflow:

### First prompt

Ask AI:

> Give me KPIs, charts, and DAX measures.

### Evaluate output

AI gives too many Card visuals.

### Second prompt

Tell AI:

> I want different kinds of visuals instead of mostly Cards.

### Evaluate again

AI provides:

* Donut
* Stacked column
* Bar
* Histogram
* Treemap
* etc.

### Final prompt

Ask AI to format the results as:

```text
KPI | Description | Visual | DAX
```

This produces a much more useful output.

### Lesson

**Prompting is iterative.**

You don't have to accept the first AI-generated answer. You can provide feedback and constraints until the result matches your requirements.

---

# 33. Why This Approach Is Useful

Instead of opening Power BI and thinking:

> "What charts should I create?"

you first create a **dashboard blueprint**.

The blueprint tells you:

```text
What to calculate?
       ↓
What KPI to create?
       ↓
What visual to use?
       ↓
What DAX measure is required?
       ↓
Where to place it?
```

This makes the actual Power BI development much more systematic.

---

# 34. Expected Two-Page Report Structure

### Page 1

## Overall Banking Performance and Customer Profile

Focus:

* Overall banking metrics
* Customer-related analysis
* Account/customer distributions
* Appropriate category and distribution visuals

Potential visual types:

* Donut
* Bar
* Column
* Histogram
* Treemap
* Selected KPI visuals

---

### Page 2

## Transactions and Account Analysis

Focus:

* Transaction performance
* Transaction types
* Transaction amounts
* Account analysis
* Time-based transaction analysis

Potential visual types:

* Bar
* Column
* Stacked column
* Donut
* Other suitable analytical visuals

---

# 35. Interview / Revision Questions

### Q1. Why were the column names provided to Perplexity?

Because the AI needs to know which fields are available before it can recommend meaningful KPIs, visuals, and DAX measures.

---

### Q2. Why was the requirement for two pages explicitly mentioned?

To make the AI organize the KPIs and visuals into two logical report pages rather than producing an unstructured list.

---

### Q3. Why didn't the instructor accept the initial recommendations?

Because Perplexity recommended too many **Card visuals**, resulting in insufficient visual variety.

---

### Q4. What was done when the initial recommendation wasn't suitable?

The prompt was refined by explicitly asking for KPIs that could be represented using different types of visuals.

---

### Q5. What visual types were recommended after refinement?

Examples include:

* Donut Chart
* Stacked Column Chart
* Column Chart
* Bar Chart
* Histogram
* Treemap

---

### Q6. Why is a Card visual useful?

A Card is useful for highlighting a single important numerical KPI.

---

### Q7. Why can too many Card visuals be undesirable?

They can make a dashboard repetitive and provide less visual analytical variety.

---

### Q8. What four columns were requested in the final KPI recommendation table?

```text
KPI
Description
Visual
DAX
```

---

### Q9. Why was the Description column added?

To explain what each KPI represents and make the recommendation easier to understand and implement.

---

### Q10. In what format were the KPI tables downloaded?

**CSV format.**

---

### Q11. How many recommendation files were downloaded?

Two:

1. Page 1 recommendations
2. Page 2 recommendations

---

### Q12. What additional resource will be provided?

The SQL code used to create the **Combined Banking Data Set**.

---

# 36. Final Revision Notes

Remember the complete process:

```text
Combined Banking Data Set
          ↓
Get all column names
          ↓
Copy column information
          ↓
Paste into Perplexity
          ↓
Ask for:
  • KPIs
  • Charts
  • DAX
  • Descriptions
          ↓
Specify 2-page report
          ↓
Review AI output
          ↓
Too many Cards?
          ↓
Refine prompt
          ↓
Request visual variety
          ↓
Create final tables
          ↓
KPI | Description | Visual | DAX
          ↓
Download Page 1 CSV
          ↓
Download Page 2 CSV
          ↓
Use recommendations to build
the actual Power BI report
```

### Most important takeaway

**The session is about report planning, not yet about creating the visuals.** The instructor uses the available columns from the Combined Banking Data Set as input to an AI tool, iteratively refines the AI's suggestions, and creates a structured **KPI + Description + Visual + DAX blueprint** for the two-page Power BI report.
