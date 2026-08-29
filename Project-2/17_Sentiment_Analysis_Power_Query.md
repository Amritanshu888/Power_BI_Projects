# Power BI Text Analytics & Sentiment Analysis — Detailed Notes

## 1. Introduction to Text Analytics in Power BI

This session introduces **Text Analytics in Power BI** using customer feedback data.

### Business requirement

Suppose your manager has received **customer feedback data** and asks you to perform **sentiment analysis** on the feedback.

Power BI provides a **Text Analytics** feature within the **Power Query Editor** that can be used for this purpose.

The goal is to take textual customer feedback and convert it into a **sentiment score**, allowing the feedback to be analyzed quantitatively.

---

# 2. New Data Source: Excel Workbook

Until now, the project primarily used **Microsoft SQL Server** as the data source.

In this example, however, the customer feedback is provided in an:

> **Excel workbook**

This demonstrates an important Power BI capability:

> **Power BI can connect to many different types of data sources.**

In real-world projects, data may come from multiple sources, and Power BI allows you to bring that data into the same project.

---

# 3. General Power BI Project Workflow

The lecture also explains the general workflow followed when building Power BI projects.

A typical workflow is:

**Data Sources**

↓

**Power BI Desktop**

↓

**Power Query Editor**

Clean, prepare, and structure the data

↓

**Model View**

Create/manage the data model and relationships

↓

**Report View**

Create visuals and reports

↓

**Power BI Service**

Publish the report

↓

**Schedule Refresh**

Keep data updated

↓

**Row-Level Security**

Control what data different users can see

↓

**Share Report**

Share the report with colleagues/users

---

# 4. Importing the Excel Customer Feedback Data

The customer feedback data is available in an Excel workbook.

### Steps

In Power BI Desktop:

1. Click **Excel Workbook**.
2. Locate the Excel file:

**Insurance Customer Feedback**

3. Open/select the workbook.
4. Power BI displays the available sheets.
5. Select:

**Sheet 1**
6. Load the data into the model.

The customer feedback data is now available in Power BI.

---

# 5. Open Power Query Editor

After loading the data, the next step is to perform data preparation and Text Analytics.

### Steps

1. Go to Power BI Desktop.
2. Click:

**Transform Data**

This opens the **Power Query Editor**.

The loaded worksheet appears as:

**Sheet 1**

This contains the customer feedback data.

---

# 6. Inspect the Customer Feedback Data

Once inside Power Query Editor, inspect the table.

The first row contains the actual column headers.

Therefore, Power Query needs to recognize the first row as column headers.

### Steps

Go to:

**Home → Use First Row as Headers**

After selecting this option:

* The first row is converted into column names.
* The actual data begins below the header row.
* The columns are now correctly named.

---

# 7. Number of Customer Feedback Records

The dataset contains:

> **97 customer feedback records**

The important column for sentiment analysis is the:

> **Feedback column**

The objective is to analyze the sentiment of these 97 feedback entries.

---

# 8. Text Analytics Feature

Power Query provides a **Text Analytics** feature through the **AI Insights** functionality.

### Location

In Power Query Editor:

**Home → AI Insights → Text Analytics**

This functionality can analyze textual information and generate useful insights.

In this example, the feature is used for:

> **Sentiment analysis**

---

# 9. Open Text Analytics

### Steps

1. In Power Query Editor, go to the **Home** tab.
2. Find the **AI Insights** group.
3. Click:

**Text Analytics**

A Text Analytics window/interface will appear.

---

# 10. Sign-In Requirement

The first time you use the Text Analytics functionality, Power BI may ask you to sign in.

If prompted:

1. Enter the credentials associated with the **Power BI Service account**.
2. Use the same credentials that were used for the Power BI Service account created earlier in the course.
3. Continue after authentication.

The feature may also take some time to initialize/process.

---

# 11. Sentiment Analysis

Text Analytics provides different functionalities.

For this example, the required functionality is:

> **Score Sentiment**

The purpose is to analyze the sentiment of each customer feedback entry.

---

# 12. Select the Feedback Column

Inside the Text Analytics functionality:

1. Select **Score Sentiment**.
2. From the available columns on the left-hand side, select:

**Feedback**

3. Click **OK**.

Power BI processes the Feedback column and generates sentiment information.

---

# 13. Data Privacy Prompt

While using the Text Analytics functionality, Power BI may display a **Data Privacy** prompt.

The lecture selects:

> **Continue**

and then:

> **Ignore privacy level checks for current file**

This allows the current file to proceed with the Text Analytics operation.

---

# 14. Sentiment Score Column

After the Text Analytics operation completes, Power BI adds a **new column** to the dataset.

This column contains the sentiment score for each customer feedback entry.

The score is represented as a value between:

**0 and 1**

### Concept

**Score closer to 1 → comparatively better/more positive feedback**

**Score closer to 0 → comparatively less positive feedback / feedback requiring improvement**

The sentiment analysis therefore converts the original textual feedback into a **numeric representation**.

---

# 15. Why Sentiment Scores Are Useful

Originally, the feedback is textual.

For example:

> "The service was excellent and the staff were very helpful."

Text by itself is difficult to aggregate numerically.

Sentiment analysis converts that feedback into a score such as:

**0.92**

Similarly, a less positive feedback might receive a lower score.

This allows us to:

* Quantify customer feedback.
* Compare feedback.
* Group feedback into categories.
* Create Power BI visuals.
* Analyze overall customer sentiment.

---

# 16. Change Sentiment Score Data Type

The newly created sentiment score column may initially have an inappropriate/general data type.

Because the sentiment score is a decimal value between **0 and 1**, it should be stored as a:

> **Decimal Number**

### Steps

1. Locate the **Score Sentiment** column.
2. Click the data-type icon associated with the column.
3. Change the data type to:

**Decimal Number**

The lecture initially considers changing the type and removes the unnecessary step before applying the correct data type.

### Final desired type

**Score Sentiment → Decimal Number**

---

# 17. Creating a Sentiment Category Column

Now that we have numerical sentiment scores, the next requirement is to group them into meaningful categories.

The categories defined in the lecture are:

1. **Excellent**
2. **Good**
3. **Needs Improvement**

The grouping is based on the sentiment score.

---

# 18. Sentiment Classification Rules

The rules used are:

|      Sentiment Score | Category          |
| -------------------: | ----------------- |
|             `>= 0.8` | Excellent         |
| `>= 0.6` but `< 0.8` | Good              |
|              `< 0.6` | Needs Improvement |

### Important point

The conditions are evaluated in order.

So:

* First check whether the score is **≥ 0.8**.
* If not, check whether it is **≥ 0.6**.
* If neither condition is satisfied, classify it as **Needs Improvement**.

---

# 19. Create the Conditional Column

Power Query allows this classification to be created using a **Conditional Column**.

### Steps

Go to:

**Add Column → Conditional Column**

A conditional column dialog box will appear.

---

## Step 1: Name the column

Give the new column the name:

**Good / Improvement**

The lecture uses the name:

> **Good/Improvement**

---

## Step 2: Define the first condition

Set:

**If Score Sentiment ≥ 0.8**

Then output:

**Excellent**

---

## Step 3: Define the second condition

Add another condition:

**Else if Score Sentiment ≥ 0.6**

Then output:

**Good**

---

## Step 4: Define the Else condition

For all remaining values:

**Else → Needs Improvement**

---

## Step 5: Create the column

Click:

**OK**

Power Query processes the condition and creates the new column.

---

# 20. Resulting Classification

After creating the conditional column, each feedback record now has both:

* A numerical sentiment score
* A categorical sentiment classification

For example:

| Feedback          | Score Sentiment | Good/Improvement  |
| ----------------- | --------------: | ----------------- |
| Positive feedback |            0.91 | Excellent         |
| Positive feedback |            0.72 | Good              |
| Negative feedback |            0.43 | Needs Improvement |

The actual scores and feedback text will vary based on the dataset.

---

# 21. Change the Category Column Data Type

The newly created **Good/Improvement** column contains text values:

* Excellent
* Good
* Needs Improvement

Therefore, its data type should be:

> **Text**

### Steps

1. Select the **Good/Improvement** column.
2. Change its data type to:

**Text**

Power Query may take some time to apply the change.

---

# 22. Apply the Power Query Changes

Once the data preparation and sentiment analysis steps are complete, the changes need to be applied to the Power BI model.

### Steps

1. In Power Query Editor, use the dropdown associated with the close/apply option.
2. Select:

**Close & Apply**

Power BI will:

* Apply the transformations.
* Process the Text Analytics results.
* Load the transformed data into the Power BI model.

This may take some time depending on the processing requirements.

---

# 23. Final Data Structure

After completing the transformation, the dataset effectively contains:

### Original information

**Feedback**

↓

### Generated numerical information

**Score Sentiment**

↓

### Generated categorical information

**Good/Improvement**

This gives us two different ways of analyzing sentiment:

### Numeric analysis

Using:

**Score Sentiment**

### Category-based analysis

Using:

**Good/Improvement**

---

# 24. Why Create Both Score and Category?

Having the numerical score and category provides flexibility.

### Score Sentiment

Useful when you want to:

* Calculate averages.
* Compare sentiment levels.
* Create numerical charts.
* Analyze changes in sentiment.

### Good/Improvement

Useful when you want to:

* Count Excellent feedback.
* Count Good feedback.
* Count feedback needing improvement.
* Create categorical charts.
* Build easy-to-understand dashboards.

---

# 25. Example Classification

Suppose we have the following sentiment scores:

| Score | Result            |
| ----: | ----------------- |
|  0.95 | Excellent         |
|  0.87 | Excellent         |
|  0.80 | Excellent         |
|  0.75 | Good              |
|  0.65 | Good              |
|  0.60 | Good              |
|  0.55 | Needs Improvement |
|  0.30 | Needs Improvement |

Notice the boundary conditions:

* **0.80** → Excellent
* **0.60** → Good
* **Below 0.60** → Needs Improvement

This follows the exact conditions defined in the lecture.

---

# 26. Complete Process

The entire exercise can be remembered as:

### Import Data

**Power BI Desktop**

↓

**Excel Workbook**

↓

Select **Insurance Customer Feedback**

↓

Select **Sheet 1**

↓

**Load**

↓

### Transform Data

**Transform Data**

↓

**Power Query Editor**

↓

**Home → Use First Row as Headers**

↓

Identify **Feedback** column

↓

### Sentiment Analysis

**Home → AI Insights → Text Analytics**

↓

Select **Score Sentiment**

↓

Select **Feedback**

↓

**OK**

↓

If prompted:

**Continue → Ignore privacy level checks for current file**

↓

Power BI generates **Score Sentiment**

↓

### Format Sentiment Score

**Score Sentiment → Decimal Number**

↓

### Create Categories

**Add Column → Conditional Column**

↓

Column name:

**Good/Improvement**

↓

`Score Sentiment >= 0.8 → Excellent`

↓

`Score Sentiment >= 0.6 → Good`

↓

`Else → Needs Improvement`

↓

**OK**

↓

Change **Good/Improvement → Text**

↓

### Apply

**Close & Apply**

↓

Data is loaded into the model

↓

Next step:

**Create visuals based on sentiment scores/categories**

---

# 27. General Power BI Workflow Demonstrated

This exercise also demonstrates how a complete Power BI project can evolve.

### Step 1 — Get data

Data can come from:

* SQL Server
* Excel
* Other supported sources

### Step 2 — Clean and prepare

Use:

**Power Query Editor**

### Step 3 — Transform

Examples:

* Change data types
* Create conditional columns
* Perform Text Analytics
* Create calculated/derived information

### Step 4 — Model

Use:

**Model View**

to create/manage the data model.

### Step 5 — Report

Create:

* Charts
* Cards
* Tables
* Slicers
* Other visuals

### Step 6 — Publish

Publish the report to:

**Power BI Service**

### Step 7 — Maintain

Possible activities include:

* Schedule refresh
* Configure Row-Level Security

### Step 8 — Share

Share the report with relevant colleagues/users.

---

# 28. Important Concepts to Remember

### Text Analytics

A Power Query/Power BI capability that can be used to analyze textual data and derive useful information from it.

### Sentiment Analysis

Used to determine how positive/negative a piece of text is.

In this example, the result is represented as a score between:

**0 and 1**

### Score Sentiment

The numerical sentiment result generated from the customer feedback.

### Conditional Column

A Power Query feature used to create a new column based on conditions.

Here it is used to convert numerical sentiment scores into categories.

---

# 29. Interview/Exam Points

### Q: Where is Text Analytics used?

**Power Query Editor**, through the **AI Insights → Text Analytics** functionality.

### Q: What is the purpose of sentiment analysis?

To analyze textual feedback and quantify its sentiment.

### Q: What column is analyzed in this example?

**Feedback**

### Q: What does Score Sentiment represent?

A numerical sentiment score between **0 and 1**.

### Q: What happens when the sentiment score is higher?

A higher score indicates comparatively better/more positive feedback.

### Q: What happens when the score is lower?

A lower score indicates comparatively less positive feedback and feedback that may require improvement.

### Q: What categories were created?

* **Excellent**
* **Good**
* **Needs Improvement**

### Q: What are the classification conditions?

```text
Score Sentiment >= 0.8 → Excellent
Score Sentiment >= 0.6 → Good
Else → Needs Improvement
```

### Q: What data type should Score Sentiment have?

**Decimal Number**

### Q: What data type should Good/Improvement have?

**Text**

### Q: How do you apply Power Query changes?

**Close & Apply**

---

# 30. Key Takeaways

* Power BI can connect to **multiple data sources**, including Excel and SQL Server.
* In this exercise, customer feedback was provided through an **Excel workbook**.
* The workbook contained **97 customer feedback records**.
* The data was loaded from **Sheet 1**.
* **Transform Data** was used to open Power Query Editor.
* **Use First Row as Headers** was used to correctly identify the column headers.
* The **Feedback** column was selected for sentiment analysis.
* Text Analytics was accessed through:
  **Home → AI Insights → Text Analytics**
* **Score Sentiment** was used to generate a numerical sentiment score.
* The generated score ranges from **0 to 1**.
* The score was converted to the **Decimal Number** data type.
* A **Conditional Column** was created to classify the feedback.
* The classification was:

  * `>= 0.8` → **Excellent**
  * `>= 0.6` → **Good**
  * Otherwise → **Needs Improvement**
* The classification column was changed to **Text**.
* **Close & Apply** was used to load the transformed data into the model.
* The next session focuses on creating **visuals based on the sentiment scores and sentiment categories**.
