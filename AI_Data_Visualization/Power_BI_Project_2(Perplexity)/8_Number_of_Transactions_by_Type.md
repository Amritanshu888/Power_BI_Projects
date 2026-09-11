# Detailed Notes: Creating the First KPI Visual — Number of Transactions by Transaction Type

## 1. Overview of the Session

In the previous sessions, the **data cleaning and data preparation** part was completed.

This session now moves into the **report creation and visualization** stage in Power BI.

The instructor uses an Excel sheet that was downloaded from **Perplexity**. This Excel sheet contains recommendations for:

* KPIs
* KPI descriptions
* Recommended visuals
* DAX measures
* Calculated columns
* Other report-related information

The first visual to be created is based on:

> **Number of Transactions by Transaction Type**

The transaction types being considered are:

* **Credit**
* **Debit**

The instructor chooses to represent this KPI using a **Pie Chart**, although a **Stacked Column Chart** is also recommended.

---

# 2. Excel Sheet / KPI Recommendation

The Excel sheet contains columns such as:

* **KPI**
* **Description**
* **Visual**
* **DAX**
* **Calculated Columns**
* etc.

For the first KPI, the recommendation is essentially:

### KPI

**Number of Transactions by Transaction Type**

### Description

Shows the **volume or proportion of transactions** across different transaction types, such as:

* Credit
* Debit

### Recommended Visuals

Two possible visuals are suggested:

1. **Pie Chart**
2. **Stacked Column Chart**

The instructor decides to use:

> **Pie Chart**

for this particular report.

---

# 3. Understanding the KPI

The purpose of this visual is to understand how transactions are distributed between different transaction types.

For example, suppose the data contains:

| Transaction Type | Number of Transactions |
| ---------------- | ---------------------: |
| Credit           |                  6,000 |
| Debit            |                  4,000 |

A pie chart can show the **proportion** of total transactions represented by each type.

In this example:

* Credit = 60%
* Debit = 40%

Therefore, the visual provides a quick understanding of the transaction mix.

---

# 4. Creating a Separate Measures Table

Before creating the DAX measure, the instructor creates a separate table specifically for storing measures.

This is considered a **good practice** because it keeps DAX measures organized separately from the original data tables.

The instructor wants to create:

> **Measures Table**

---

## Steps to Create the Measures Table

### Step 1: Open Power BI Desktop

Go back to the Power BI Desktop report.

### Step 2: Click "Enter Data"

From the Power BI ribbon, select:

> **Enter Data**

### Step 3: Name the table

The newly created table is named:

> **Measures table**

### Step 4: Load the table

Click:

> **Load**

The Measures table is now added to the Power BI model.

---

# 5. Why Create a Measures Table?

A dedicated measures table is useful for organization.

Instead of having DAX measures scattered across multiple data tables, we can keep them in one location.

Conceptually:

**Combined Banking Dataset**

→ Contains original data columns

**Measures Table**

→ Contains DAX measures

For example:

```text
Measures Table
    ├── Count of Transactions
    ├── Total Transaction Amount
    ├── Average Transaction Amount
    └── Other Measures
```

This becomes especially useful as the report grows and more measures are created.

---

# 6. Creating the "Count of Transactions" Measure

After creating the Measures table, the instructor creates the first DAX measure.

## Steps

### Step 1: Find Measures Table

In the **Data/Fields pane**, locate:

> **Measures table**

### Step 2: Right-click the table

Right-click on **Measures table**.

### Step 3: Select New Measure

Choose:

> **New Measure**

A DAX formula bar appears where the measure can be written.

---

# 7. Copying the DAX Formula

The instructor goes back to the Excel sheet containing the recommended DAX formula.

The DAX formula is copied from the Excel sheet.

It is then pasted into the Power BI DAX formula bar.

The exact formula should be taken from the provided Excel recommendation rather than manually modifying the recommended logic.

The measure is given the name:

> **Count of Transactions**

So conceptually:

```text
Count of Transactions = [DAX formula from the Excel recommendation]
```

The instructor presses:

> **Enter**

The measure is successfully created.

---

# 8. Important Difference: Measure vs. Column

The instructor is creating a **measure**, not a calculated column.

### Measure

A measure calculates a value dynamically based on the context of the visual.

For example:

> Count of Transactions

can change depending on filters, slicers, transaction types, dates, etc.

### Calculated Column

A calculated column creates a value for each row of the table.

For this KPI, the instructor uses a **measure** because the goal is to dynamically calculate the number of transactions.

---

# 9. Removing the Unnecessary Column from Measures Table

When the Measures table was created using **Enter Data**, Power BI automatically created a column called:

> **Column 1**

The instructor does not need this column because the table is only being used to organize DAX measures.

Therefore, the column is deleted from the model.

## Steps

1. Locate **Column 1** under Measures table.
2. Click the **three dots (`...`)** next to Column 1.
3. Select:

   > **Delete from model**
4. Confirm by clicking:

   > **Yes**

The unnecessary Column 1 is now removed.

### Result

The Measures table effectively becomes a container for measures rather than a table containing useful data columns.

---

# 10. Creating the Pie Chart

Now that the measure has been created, the instructor creates the first visual.

## Steps

### Step 1: Select Pie Chart

From the Visualizations pane, click:

> **Pie Chart**

A blank pie chart appears on the report canvas.

---

# 11. Adding Transaction Type to the Pie Chart

The Excel recommendation says that the visual should use:

> **Transaction Type**

as the category/axis-type field.

However, a pie chart does not have an **Axis** bucket.

Instead, it has:

> **Legend**

Therefore, the instructor puts **Transaction Type** into the **Legend** field.

---

## Steps

### Step 1: Expand the dataset

Expand:

> **Combined Banking Data Set**

### Step 2: Find Transaction Type

Locate:

> **Transaction Type**

### Step 3: Add it to the visual

Either:

* Double-click the field, or
* Drag and drop it

into:

> **Legend**

The pie chart now knows that it should separate the data based on transaction type.

The resulting sectors represent:

* Credit
* Debit

---

# 12. Adding the Count of Transactions Measure

Now the actual transaction count needs to be added.

## Steps

### Step 1: Expand Measures Table

Expand:

> **Measures table**

### Step 2: Find the measure

Locate:

> **Count of Transactions**

### Step 3: Add it to Values

Double-click or drag and drop it into:

> **Values**

Now the pie chart is populated.

---

# 13. Pie Chart Structure

The final configuration is:

| Pie Chart Bucket | Field                 |
| ---------------- | --------------------- |
| **Legend**       | Transaction Type      |
| **Values**       | Count of Transactions |

Conceptually:

```text
Pie Chart
│
├── Legend
│     └── Transaction Type
│
└── Values
      └── Count of Transactions
```

This creates the visual:

> **Count of Transactions by Transaction Type**

---

# 14. Alternative: Stacked Column Chart

Perplexity also recommended a:

> **Stacked Column Chart**

The instructor demonstrates that the visual can easily be changed.

### Steps

1. Keep the pie chart selected.
2. Click the **Stacked Column Chart** icon in the Visualizations pane.

Power BI converts the visual into a stacked column chart.

The same underlying fields can be used.

However, the instructor decides:

> **For now, keep the Pie Chart.**

To return to the pie chart:

1. Select the stacked column chart.
2. Click the **Pie Chart** icon again.

---

# 15. Formatting the Pie Chart

After creating the visual, the instructor begins formatting it.

The goal is to make the chart more readable and visually appealing.

---

# 16. Changing the Colors of the Pie Sectors

The instructor wants different colors for:

* Credit
* Debit

## Steps

1. Select the pie chart.
2. Click:

   > **Format your Visual**
3. Find:

   > **Slices**
4. Expand:

   > **Colors**
5. Look under:

   > **Series**

Now individual transaction types can be formatted separately.

---

## Formatting Credit

Under Series:

1. Select:

   > **Credit**
2. Choose the desired color.

---

## Formatting Debit

Then:

1. Select:

   > **Debit**
2. Choose a different color.

### Result

Credit and Debit are visually distinguishable.

---

# 17. Formatting the Chart Title

The instructor checks the chart title.

The title is already:

> **Count of Transactions by Transaction Type**

This is appropriate for the visual, so the title text itself does not need to be changed.

---

# 18. Center-Aligning the Title

The instructor wants the title to be centered.

## Steps

1. Go to:

   > **General**
2. Open:

   > **Title**
3. Find the alignment option.
4. Set the alignment to:

   > **Center**

The chart title is now centered.

---

# 19. Configuring Detail Labels

The instructor then changes how information is displayed directly on the pie chart.

## Steps

1. Go to:

   > **Visual**
2. Expand:

   > **Detail labels**
3. Find:

   > **Label contents**
4. Select:

   > **All details**

This allows the pie chart labels to display more detailed information.

---

# 20. Turning Off the Legend

Once **All details** has been selected for the detail labels, the instructor decides that the separate legend is no longer necessary.

Why?

Because the chart itself is already showing the relevant information through its labels.

## Steps

1. Find:

   > **Legend**
2. Turn it:

   > **Off**

### Result

The separate legend is removed, making the chart less cluttered.

---

# 21. Formatting the Values

The instructor further formats the values displayed in the detail labels.

## Steps

1. Expand:

   > **Values**
   > under Detail Labels.
2. Change the text color to:

   > **Black**
3. Increase/decrease the text size as required.
4. The instructor ultimately keeps the size at:

   > **11**

The exact font style can also be changed according to preference.

---

# 22. Changing Font Style

The instructor mentions that the font style can be customized.

This can be done for:

* Detail label values
* Chart title

The instructor does not prescribe one mandatory font.

Instead:

> **Choose a font style according to your preference.**

---

# 23. Formatting the Title Font

The instructor returns to the title settings.

## Steps

1. Go to:

   > **General**
2. Expand:

   > **Title**
3. Select the desired font.
4. Make the title:

   > **Bold**
5. Reduce the font size slightly if necessary.

The purpose is to make the title clear without making it unnecessarily large.

---

# 24. Adding a Border

The instructor then adds a border around the visual.

## Steps

1. Collapse the Title section.
2. Go to:

   > **Effects**
3. Find:

   > **Border**
4. Enable/change the border setting.
5. Set it to:

   > **1**

This adds a subtle border around the chart.

---

# 25. Adding a Shadow

The instructor also adds a shadow effect.

## Steps

1. Under:

   > **Effects**
2. Find:

   > **Shadow**
3. Set the shadow setting to:

   > **1**

The chart now has a shadow effect.

---

# 26. Changing Shadow Color

The shadow color can also be customized.

## Steps

1. Expand the **Shadow** settings.
2. Click:

   > **Color**
3. Select the required color.

The instructor selects a color described as:

> **White, 30% darker**

This provides a subtle visual effect.

---

# 27. Collapsing the Panes

After completing the formatting, the instructor collapses:

* **Filters pane**
* **Visualizations pane**

This provides a cleaner view of the report canvas.

---

# 28. Positioning the Pie Chart

The created pie chart can be placed anywhere on the report canvas.

The instructor moves it toward:

> **The right-hand side**

The exact position is not finalized yet because the report will contain additional visuals.

Later sessions will cover:

* Resizing charts
* Moving charts
* Positioning charts
* Arranging visuals according to the overall dashboard layout

---

# 29. Naming the Report Page

The instructor checks the Power BI report page.

For now, the page is left as:

> **Page 1**

The instructor says that the page name can be changed later if required.

So there is no need to rename it at this stage.

---

# 30. Final Visual Created

At the end of this session, the first report visual has been created.

### KPI

**Number of Transactions by Transaction Type**

### Visual

**Pie Chart**

### Categories

* Credit
* Debit

### Measure

**Count of Transactions**

### Configuration

```text
Legend → Transaction Type
Values → Count of Transactions
```

### Formatting

* Credit and Debit given different colors
* Title: **Count of Transactions by Transaction Type**
* Title center aligned
* Detail labels enabled
* Label contents → **All details**
* Legend → Off
* Values → Black
* Value font size → **11**
* Title made bold
* Border → **1**
* Shadow → **1**
* Shadow color → White, 30% darker
* Chart positioned toward the right side of the page

---

# 31. Complete Step-by-Step Workflow

Here's the complete workflow from the beginning of the session:

### Step 1 — Open the Excel recommendation sheet

Review the KPI recommendations provided by Perplexity.

### Step 2 — Identify the first KPI

> **Number of Transactions by Transaction Type**

### Step 3 — Understand the KPI

It represents the volume/proportion of transactions based on:

* Credit
* Debit

### Step 4 — Review recommended visuals

Possible choices:

* Pie Chart
* Stacked Column Chart

### Step 5 — Open Power BI Desktop

Return to the Power BI report.

### Step 6 — Create Measures Table

Go to:

**Enter Data → Name: Measures table → Load**

### Step 7 — Create a new measure

Right-click:

**Measures table → New Measure**

### Step 8 — Copy the recommended DAX

Copy the DAX formula from the Excel sheet and paste it into Power BI.

### Step 9 — Name the measure

> **Count of Transactions**

Press **Enter**.

### Step 10 — Remove Column 1

Go to:

**Column 1 → Three dots → Delete from model → Yes**

### Step 11 — Create the pie chart

Select:

> **Pie Chart**

### Step 12 — Add Transaction Type

From **Combined Banking Data Set**:

> Transaction Type → Legend

### Step 13 — Add the measure

From **Measures table**:

> Count of Transactions → Values

### Step 14 — Format the slices

Set separate colors for:

* Credit
* Debit

### Step 15 — Format the title

Title:

> **Count of Transactions by Transaction Type**

Set:

* Center alignment
* Preferred font
* Bold
* Appropriate size

### Step 16 — Format detail labels

Go to:

**Visual → Detail labels → Label contents → All details**

### Step 17 — Remove legend

Set:

> **Legend → Off**

### Step 18 — Format values

Set:

* Color → Black
* Size → 11
* Font → As preferred

### Step 19 — Add effects

Set:

* Border → 1
* Shadow → 1
* Shadow color → White, 30% darker

### Step 20 — Clean the workspace

Collapse:

* Filters pane
* Visualizations pane

### Step 21 — Position the visual

Move the pie chart toward the **right-hand side**.

### Step 22 — Keep page name

Leave the page as:

> **Page 1**

for now.

---

# 32. Important Concepts to Remember

### Dedicated Measures Table

A separate table used to organize all DAX measures in one place.

### DAX Measure

A dynamic calculation that responds to the filter and visualization context.

### Legend

In a pie chart, the **Legend** determines the categories into which the pie is divided.

Here:

> Transaction Type → Legend

### Values

Determines the numerical value represented by each category.

Here:

> Count of Transactions → Values

### Detail Labels

Displays information directly on/around the pie chart instead of relying only on the legend.

### Pie Chart vs. Stacked Column Chart

**Pie Chart:**
Best for quickly showing the **proportion/share** of categories.

**Stacked Column Chart:**
Useful for comparing category values and showing composition, particularly when there are more categories or additional dimensions.

The instructor chooses the **Pie Chart** for this KPI.

---

# 33. Key Takeaways for Your Notes

> **Data Cleaning → Completed**

Now the workflow moves to:

> **Report Creation → KPI Visuals → Formatting → Dashboard Layout**

The first KPI is:

> **Number of Transactions by Transaction Type**

The first visual is:

> **Pie Chart**

The important field mapping is:

> **Transaction Type → Legend**

> **Count of Transactions → Values**

The instructor also establishes an important Power BI best practice:

> **Create a dedicated Measures table to store DAX measures.**

The next sessions will continue by adding the **other charts recommended in the Excel sheet**, followed eventually by arranging and formatting the complete report/dashboard.
