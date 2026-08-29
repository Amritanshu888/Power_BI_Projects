# Detailed Notes — Power BI Project 3: UPI Transactions Data

These notes cover the lecture **in sequence**, including the reasoning behind the transformations and the exact steps performed in Power BI. I’ve kept the terminology and workflow from the lecture rather than adding outside material. 

---

## 1. Introduction to the Project

The instructor introduces the **third Power BI project**, which is based on **UPI transaction data**.

### Objective

The goal of the project is to:

1. Use **UPI transactions data** as the dataset.
2. Import that data into **Power BI**.
3. Perform necessary **data transformations and preparation**.
4. Load the prepared data into the Power BI data model.
5. Eventually create a **Power BI report** from this data.

The first session focuses primarily on **understanding and preparing the data**, rather than building visualizations. 

---

# 2. Opening Power BI Desktop

The first step is to open Power BI Desktop.

### Steps

1. Open **Power BI Desktop**.
2. Wait for Power BI Desktop to launch.
3. Signing in is **not required** for this process.
4. On the opening screen, select **Blank report**.

This opens a new, empty Power BI report. 

---

# 3. Connecting Excel as the Data Source

The project uses an **Excel workbook** as the source of the UPI transaction data.

### Steps

1. In Power BI Desktop, choose **Excel Workbook** as the data source.
2. Select the Excel workbook containing the **UPI transactions** dataset.
3. Power BI displays the sheets available in the workbook.
4. The required data is present in **Sheet1**.
5. Select **Sheet1**.
6. Power BI displays a **preview of the data**.

At this point, there are two possible approaches:

### Option 1 — Load Directly

The data can be loaded directly into the Power BI model.

### Option 2 — Transform First

Alternatively, the data can first be opened in **Power Query Editor**, where:

* The data can be examined.
* Columns can be reviewed.
* The meaning of the data can be understood.
* Transformations can be performed.
* The cleaned/transformed data can then be loaded into the model.

The instructor chooses **Transform Data** because the dataset should first be examined and prepared. 

---

# 4. Opening Power Query Editor

After clicking **Transform Data**, Power Query Editor opens.

The query is initially named **Sheet1**.

### Rename the Query

The instructor renames the query to make it more meaningful.

### Steps

1. Find the query named **Sheet1**.
2. Double-click the query name.
3. Rename it to **UPI transactions**.
4. Press **Enter**.

This makes the query name more descriptive and easier to work with. 

---

# 5. Understanding the Dataset

Before transforming anything, the instructor goes through the columns and explains what each one represents.

This is an important data-analysis practice:

> Before beginning analysis, first understand what the data represents.

Understanding the columns makes it easier to later create reports, dashboards, and insights. 

---

# 6. Transaction ID

### Column: `Transaction ID`

This column contains the **transaction IDs**.

Its purpose is to uniquely identify a transaction.

### Meaning

Each transaction has an identifier that can be used to distinguish one transaction from another.

### Expected data type

**Text**

The instructor later confirms that the transaction ID has a text data type. 

---

# 7. Transaction Date

### Column: `Transaction Date`

This column represents the **date on which the transaction took place**.

### Expected data type

**Date**

The instructor confirms that it is already correctly recognized as a date. 

---

# 8. Amount

### Column: `Amount`

This represents the **amount involved in the transaction**.

For example, if a transaction was made for a particular monetary amount, that value is stored here.

### Expected data type

**Decimal**

The instructor confirms that the amount column already has the decimal data type. 

---

# 9. Bank Name Sent

### Column: Bank Name Sent

This contains the name of the **bank from which the transaction amount was sent**.

### Expected data type

**Text**

The instructor confirms that this is correctly configured as text. 

---

# 10. Bank Name Received

### Column: Bank Name Received

This contains the name of the **bank into which the transaction amount was received**.

### Expected data type

**Text**

This is also correctly configured as text. 

---

# 11. Remaining Balance

### Column: `Remaining Balance`

This represents the **balance remaining in the customer's account after the transaction**.

This is important to distinguish from the `Amount` column:

* **Amount** → value of the transaction.
* **Remaining Balance** → customer's account balance after that transaction.

### Expected data type

**Decimal**

The instructor confirms that the column is already configured as decimal. 

---

# 12. City

### Column: `City`

This represents the **city from which the transaction was made**.

### Expected data type

**Text**

The instructor confirms that the column contains textual values. 

---

# 13. Gender

### Column: `Gender`

This represents the **gender of the customer making the transaction**.

### Expected data type

**Text**

The values are textual. 

---

# 14. Transaction Type

### Column: `Transaction Type`

This indicates **what type of transaction took place**.

The lecture identifies two categories:

* **Transfer**
* **Payment**

### Expected data type

**Text**



---

# 15. Status

### Column: `Status`

This tells us whether a transaction was successful or unsuccessful.

There are two status values:

* **Failed**
* **Success**

### Expected data type

**Text**



---

# 16. Transaction Time — Important Transformation

This is one of the most important transformations in the lecture.

### Problem

The Excel data originally contained **only the time**.

However, Power BI automatically detected the column in a way that included a **date component** along with the time.

So Power BI was displaying something resembling:

**Date + Time**

But the actual meaning of the column is only:

**Time**

The date component is therefore unnecessary and needs to be removed. 

---

## How to Remove the Date from Transaction Time

The instructor uses **Split Column by Delimiter**.

### Step 1 — Select the column

Select the **Transaction Time** column.

### Step 2 — Go to Transform

Go to the **Transform** tab.

### Step 3 — Select Split Column

Choose:

**Split Column → By Delimiter**

### Step 4 — Choose the delimiter

The delimiter is a **blank space**.

So select/specify:

**Space**

### Step 5 — Select the occurrence

Choose:

**Rightmost occurrence of the delimiter**

### Step 6 — Click OK

Power Query splits the original column into two columns.

They are named:

* `Transaction Time 1`
* `Transaction Time 2`

The resulting structure is essentially:

| New Column         | Contains |
| ------------------ | -------- |
| Transaction Time 1 | Date     |
| Transaction Time 2 | Time     |

The first column is unnecessary because the actual dataset requires only the time. 

---

## Step 7 — Delete the Date Column

The instructor removes `Transaction Time 1`.

### Steps

1. Right-click **Transaction Time 1**.
2. Select **Remove**.

Now only `Transaction Time 2` remains. 

---

## Step 8 — Rename the Remaining Column

The remaining column is called `Transaction Time 2`.

Rename it back to:

**Transaction Time**

### Steps

1. Double-click `Transaction Time 2`.
2. Remove the `2` from the name.
3. Press **Enter**.

Now the column correctly represents the **time of day at which the transaction occurred**. 

### Final data type

The column should be:

**Time**

The instructor confirms that Power BI has correctly identified it as a time data type. 

---

# 17. Device Type

### Column: `Device Type`

This represents the **device used to make the transaction**.

The lecture identifies three device categories:

* Laptop
* Mobile
* Tablet

### Expected data type

**Text**



---

# 18. Payment Method

### Column: `Payment Method`

This represents the method through which the payment was made.

The lecture identifies categories such as:

* Phone number
* QR code
* UPI ID

### Expected data type

**Text**



---

# 19. Merchant Name

### Column: `Merchant Name`

This represents the **name of the merchant** associated with the transaction.

Examples mentioned in the lecture include:

* Amazon
* Flipkart
* IRCTC
* Swiggy
* Zomato

### Expected data type

**Text**



---

# 20. Purpose

### Column: `Purpose`

This represents the **purpose/category of the transaction**.

The lecture identifies these categories:

* Bill Payment
* Food
* Others
* Shopping
* Travel

### Expected data type

**Text**



---

# 21. Customer Age

### Column: `Customer Age`

This represents the **age of the customer who made the transaction**.

### Expected data type

**Whole Number**

The instructor confirms that it is already a whole number. 

---

# 22. Payment Mode

### Column: `Payment Mode`

This indicates when the payment is supposed to occur.

The lecture identifies two categories:

* **Instant**
* **Scheduled**

In other words, the payment could happen immediately or be scheduled for another time. 

### Expected data type

**Text**

---

# 23. Currency

### Column: `Currency`

This indicates the **currency in which the transaction took place** and the currency associated with the remaining amount.

### Expected data type

**Text**

The instructor confirms that the currency column should remain textual. 

---

# 24. Customer Account Number

### Column: `Customer Account Number`

This contains the customer's account number.

### Problem observed

When imported from Excel, the account numbers appeared in **exponential/scientific notation**.

This is not the desired representation for an account number. 

---

## Correcting Customer Account Number

The instructor changes the data type to **Text**.

### Steps

1. Select/right-click the data type for the **Customer Account Number** column.
2. Change the data type to **Text**.
3. Verify the resulting account numbers.

After changing the data type, the account numbers are displayed properly rather than in exponential notation. 

---

# 25. Merchant Account Number

### Column: `Merchant Account Number`

This contains the merchant's account number.

It has the same issue as the customer account number: it was initially displayed in exponential notation after being imported from Excel.

### Solution

Change its data type to **Text**.

### Steps

1. Select the **Merchant Account Number** column.
2. Change its data type to **Text**.
3. Verify the resulting values.

The merchant account numbers are then displayed correctly. 

---

# 26. Important Validation After Converting Account Numbers

The instructor highlights an important data-quality check.

Whenever numbers such as account numbers are converted from one data type to another, **always verify the resulting values**.

### What specifically should be checked?

Look at the account numbers and make sure that **unwanted zeros have not appeared at the end**.

For example, after conversion, you should check whether the account number unexpectedly ends with:

`000`

or another sequence of zeros.

This can happen when a conversion does not take place correctly. 

### In this dataset

The instructor checks both:

* Customer Account Number
* Merchant Account Number

No unwanted trailing zeros are observed, so the conversion is considered correct. 

---

# 27. Complete Data-Type Check

After performing the transformations, the instructor systematically checks the data type of **every column**.

This is an important part of data preparation.

The final expected data types are:

| Column                  | Data Type    |
| ----------------------- | ------------ |
| Transaction ID          | Text         |
| Transaction Date        | Date         |
| Amount                  | Decimal      |
| Bank Name Sent          | Text         |
| Bank Name Received      | Text         |
| Remaining Balance       | Decimal      |
| City                    | Text         |
| Gender                  | Text         |
| Transaction Type        | Text         |
| Status                  | Text         |
| Transaction Time        | Time         |
| Device Type             | Text         |
| Payment Method          | Text         |
| Merchant Name           | Text         |
| Purpose                 | Text         |
| Customer Age            | Whole Number |
| Payment Mode            | Text         |
| Currency                | Text         |
| Customer Account Number | Text         |
| Merchant Account Number | Text         |

These data types are based on the instructor's walkthrough and checks in the lecture. 

---

# 28. Why Data Types Are Important

This is one of the major conceptual points of the lecture.

The instructor emphasizes that **checking the data type of every column is extremely important**.

### Why?

Data types affect:

1. **Data preparation**
2. **Data modeling**
3. **Report performance**
4. **Correctness of the data shown in the report**
5. Ultimately, the ability to create accurate reports and dashboards.

The instructor emphasizes that data modeling depends heavily on proper data preparation, and therefore the data types of all columns in all tables should be thoroughly checked. 

---

# 29. General Data-Analysis Principle

A key lesson from this session is:

> **Before analyzing data, first understand the data.**

The instructor recommends getting as much information and detail about the dataset as possible before starting the actual analysis.

### Why?

The better you understand the data:

**Better understanding of data → Easier report creation → Better dashboards → Better ability to communicate insights**

This is why the instructor spends significant time explaining the columns and checking their data types before moving to reporting. 

---

# 30. Loading the Transformed Data into the Model

Once the transformations and data-type checks are complete, the data is ready to be loaded into Power BI's model.

### Steps

1. Go to the **Home** tab in Power Query Editor.
2. Click the dropdown associated with the closing/applying options.
3. Select **Close & Apply**.
4. Power BI applies the transformations.
5. Power BI then loads the prepared data into the **data model**.

The process may take some time while Power BI applies the changes. 

---

# 31. What Has Been Completed in This Session?

By the end of the lecture, the following work has been completed:

### Data source

* Excel workbook

### Sheet used

* Sheet1

### Query renamed

* Sheet1 → **UPI transactions**

### Data examined

The instructor reviewed the meaning of the dataset's columns.

### Transformation performed

The `Transaction Time` column was split using a **space delimiter** so that the unnecessary date component could be removed.

### Column removed

* `Transaction Time 1`

### Column renamed

* `Transaction Time 2` → `Transaction Time`

### Account number formatting fixed

Both:

* Customer Account Number
* Merchant Account Number

were changed from their imported numerical/exponential representation to **Text**.

### Data quality checked

The instructor verified that the account numbers did not acquire unwanted trailing zeros.

### Data types checked

Every column's data type was reviewed.

### Data loaded

The transformed data was loaded into the Power BI model using **Close & Apply**.  

---

# 32. Workflow to Remember

For this project, the overall workflow demonstrated in the lecture is:

**Open Power BI Desktop**
↓
**Blank Report**
↓
**Get Data → Excel Workbook**
↓
**Select UPI transactions Excel file**
↓
**Select Sheet1**
↓
**Transform Data**
↓
**Open Power Query Editor**
↓
**Rename Sheet1 → UPI transactions**
↓
**Understand every column**
↓
**Check/perform transformations**
↓
**Fix Transaction Time**
↓
**Fix Account Number data types**
↓
**Validate converted account numbers**
↓
**Check data types of all columns**
↓
**Home → Close & Apply**
↓
**Data loaded into Power BI model**

This workflow is the practical sequence you should be able to reproduce from the lecture.

---

# 33. Important Exam/Interview Points

### 1. Why use Transform Data instead of immediately loading?

Because it allows you to:

* Inspect the data.
* Understand the columns.
* Check data types.
* Perform transformations.
* Prepare the data before loading it into the model. 

### 2. Why was Transaction Time split?

Because Power BI had detected a date component along with the time, whereas the source data represented **time only**.

### 3. How was Transaction Time fixed?

**Transform → Split Column → By Delimiter → Space → Rightmost occurrence → OK**

Then delete the date column and rename the remaining time column.

### 4. Why were account numbers changed to Text?

Because account numbers imported from Excel appeared in **exponential notation**. Converting them to text makes them display properly.

### 5. What should you check after converting account numbers?

Check that **unwanted trailing zeros** have not appeared.

### 6. Why are data types important?

Because they affect:

* Data modeling
* Report performance
* Correctness/accuracy of report results
* Data preparation

### 7. What should you do before beginning data analysis?

**Understand the data thoroughly first.**

---

# 34. What's Coming Next

The lecture ends by explaining what will be covered in the following sessions.

The next session will focus on **data profiling**.

The instructor says they will examine:

* Total number of records
* Different types of values
* What different columns contain
* Further understanding of the dataset

After that, the course will move toward the **reporting part** of the project. 

---

## Quick Revision Sheet

**Project:** Power BI Project 3 — UPI Transactions

**Source:** Excel workbook

**Sheet:** Sheet1

**Query name:** UPI transactions

**Main transformation:** Fix Transaction Time

**Transaction Time procedure:**

`Transform → Split Column → By Delimiter → Space → Rightmost occurrence → OK`

Then:

`Delete Transaction Time 1 → Rename Transaction Time 2 to Transaction Time`

**Account number procedure:**

`Customer Account Number → Data Type → Text`

`Merchant Account Number → Data Type → Text`

Then **check for unwanted trailing zeros**.

**Important data types:**

* IDs/account numbers → Text
* Dates → Date
* Time → Time
* Amount/balance → Decimal
* Age → Whole Number
* Categories/descriptions → Text

**Final step:**

`Home → Close & Apply`

**Core lesson:**
**Understand and properly prepare your data before building the Power BI report.** 
