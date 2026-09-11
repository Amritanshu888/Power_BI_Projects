# Power BI – Creating “Total Balance by Account Type”

## 1. Session Objective

In this session, the instructor creates the next chart/KPI based on the recommendations available in an **Excel sheet**.

The Excel sheet initially contains a recommendation related to:

> **Average Account Balance**

However, instead of creating that particular KPI, the instructor decides to work on another KPI:

> **Total Balance by Account Type**

### What does this KPI show?

It shows the **aggregate (total) balance for each account type**.

In this dataset, the account types include:

* **Savings**
* **Current**

Therefore, the visualization answers:

> **“What is the total balance associated with each type of account?”**

---

# 2. Recommended Visualization

According to the Excel recommendation, **Total Balance by Account Type** can be represented using either:

* **Clustered Bar Chart**, or
* **Column Chart**

The instructor initially chooses a:

> **Clustered Column Chart**

Later, after checking the visualization, the instructor changes it to a **Clustered Bar Chart**.

---

# 3. DAX Measure Required

To calculate the total balance, a **DAX measure** needs to be created.

The required calculation is:

```DAX
Total Balance = SUM('Combined Banking Data Set'[Balance])
```

### What does this formula do?

`SUM()` adds all the values present in the **Balance** column.

So:

```text
Balance 1
+ Balance 2
+ Balance 3
+ ...
= Total Balance
```

The important idea is:

> **Total Balance = Sum of the Balance column**

---

# 4. Why Use a Measure?

The instructor creates **Total Balance as a DAX measure** rather than simply using the column directly.

The measure is calculated according to the **filter/context of the visualization**.

For example, once `Account Type` is placed on the chart, Power BI can calculate the total separately for each category:

```text
Savings       → Total Savings Balance
Current       → Total Current Balance
```

Therefore, the same measure can dynamically produce different totals depending on the category/filter context.

---

# 5. Creating the Total Balance Measure

## Step 1: Open Power BI Desktop

Go back to the Power BI Desktop report.

---

## Step 2: Expand the Data Pane

On the right side of Power BI Desktop, expand the **Data pane** so that the available tables, columns, and measures can be accessed.

---

## Step 3: Locate the Measures Table

Find the:

> **Measures Table**

This is where the instructor stores the DAX measures.

---

## Step 4: Create a New Measure

Right-click on:

**Measures Table → New measure**

Power BI will open the DAX formula bar.

---

## Step 5: Enter the DAX Formula

Create the measure:

```DAX
Total Balance = SUM('Combined Banking Data Set'[Balance])
```

The instructor mentions that the measure is already named **Total Balance**, so the name is retained.

---

## Step 6: Press Enter

After entering the formula, press:

**Enter**

The **Total Balance** measure is now created.

---

# 6. Create the Visualization

After creating the measure, the instructor creates the chart.

## Step 1: Click a Blank Area of the Canvas

Click on an empty area of the Power BI report canvas.

This allows Power BI to create a **new visual** rather than modifying an existing one.

---

## Step 2: Open the Visualizations Pane

Expand the **Visualizations** pane.

---

## Step 3: Select Clustered Column Chart

Select:

> **Clustered Column Chart**

A new blank column chart appears on the report canvas.

---

## Step 4: Resize the Chart

The instructor resizes the chart so that it fits appropriately on the report.

---

# 7. Add Total Balance to the Chart

Now the newly created measure needs to be added to the visual.

The measure is:

> **Total Balance**

### Steps

1. Find **Total Balance** in the Data/Fields pane.
2. Drag it into the chart.
3. Place it in the **Y-axis** bucket.

So the configuration becomes:

```text
Y-Axis → Total Balance
```

The Y-axis now represents the total balance.

---

# 8. Add Account Type

Next, the instructor wants to compare the balance between different account types.

The required field is:

> **Account Type**

### Steps

1. Find the **Account Type** column.
2. Drag it into the chart.
3. Place it in the **X-axis** bucket.

The configuration is now:

```text
X-Axis → Account Type
Y-Axis → Total Balance
```

Therefore, the chart represents:

> **Total Balance by Account Type**

---

# 9. Account Types in the Chart

The chart contains two account types:

1. **Savings**
2. **Current Account**

The instructor observes that there is a **significant difference** between the balances of the two account types.

---

# 10. Reuse Existing Formatting with Format Painter

The instructor wants this new chart to have the **same formatting as the chart created in the previous session**.

The previous chart is:

> **Total Amount by Name**

Instead of manually applying all the formatting again, the instructor uses **Format Painter**.

## Steps

1. Select the existing **Total Amount by Name** chart.
2. Go to the **Home** tab.
3. Click **Format Painter**.
4. Click the new **Total Balance by Account Type** chart.

The formatting is copied from the old chart to the new chart.

### Why use Format Painter?

It helps:

* Save formatting time
* Maintain a consistent design
* Keep charts visually similar
* Avoid manually repeating formatting settings

### Key concept

> **Format Painter copies the formatting of one visual and applies it to another visual.**

---

# 11. Problem with the Displayed Values

After applying the formatting, the instructor notices that the values are not displayed clearly.

The chart is showing values approximately as:

* **0.0 million**
* **-15.8 million**

The instructor wants the numbers to be more readable.

Therefore, the **Display Units** setting needs to be changed.

---

# 12. Changing the Chart Type

The instructor considers whether changing the chart type will make the visualization better.

## First attempt: Stacked Bar Chart

The chart is changed to:

> **Stacked Bar Chart**

However, this does not solve the display issue.

Therefore, the instructor decides to use:

> **Clustered Bar Chart**

### Final chart type

**Clustered Bar Chart**

---

# 13. Changing Display Units

The instructor now changes how the numerical values are displayed.

## Steps

1. Select the chart.
2. Open **Format Visual**.
3. Go to **Data Labels**.
4. Scroll down.
5. Locate **Value**.
6. Scroll further down.
7. Find **Display Units**.

The current setting is:

> **Auto**

Change it to:

> **Thousands**

### Final setting

```text
Display Units:
Auto → Thousands
```

### Why change it?

When Power BI uses **Auto**, it may automatically display large values using units such as millions.

In this case, the instructor wants the values to be more directly readable, so **Thousands** is selected.

After making this change, the numbers become more visible and easier to compare.

---

# 14. Changing the Colors of the Bars

The instructor also wants to give different colors to the different account types.

The desired color scheme is:

| Account Type | Color |
| ------------ | ----- |
| Savings      | Green |
| Current      | Red   |

This follows the same color scheme used in the previously created chart.

---

# 15. Formatting the Savings Category

The instructor first changes the color for **Savings**.

## Steps

1. Select the chart.
2. Open **Format Visual**.
3. Collapse the **Value/Data Labels** section if required.
4. Go to the relevant **Columns/Categories** formatting section.
5. Select **Savings**.
6. Open the **Colors** option.
7. Choose **Green**.

### Result

> **Savings → Green**

The instructor notes that Savings is positive, so green is used.

---

# 16. Formatting the Current Category

Next, the instructor changes the color for the Current account category.

## Steps

1. Go to the category settings.
2. Select:

> **Current**

3. Open **Colors**.
4. Select **Red**.

### Result

> **Current → Red**

The red color is used because the value is negative.

---

# 17. Hexadecimal Color Codes

The instructor points out that the **hexadecimal color code** is visible on the screen.

These colors have already been used in the previous chart.

Therefore, the instructor reuses the same colors.

### Why reuse the same colors?

Consistent colors across visuals make the dashboard:

* Easier to understand
* More professional
* More visually consistent
* Easier to interpret

For example, if **green always represents positive values** and **red represents negative values**, users can quickly understand the meaning of the visual.

---

# 18. Final Chart Configuration

The final visualization is:

> **Total Balance by Account Type**

### DAX Measure

```DAX
Total Balance = SUM('Combined Banking Data Set'[Balance])
```

### Chart Type

> **Clustered Bar Chart**

### Axis Configuration

```text
X-Axis → Account Type
Y-Axis → Total Balance
```

### Display Units

```text
Thousands
```

### Category Colors

```text
Savings → Green
Current → Red
```

---

# 19. Complete Power BI Procedure

Here is the complete procedure in one sequence.

### Step 1: Choose the KPI

From the Excel recommendations, select:

> **Total Balance by Account Type**

---

### Step 2: Create the DAX Measure

Go to:

**Measures Table → Right-click → New measure**

Enter:

```DAX
Total Balance = SUM('Combined Banking Data Set'[Balance])
```

Press **Enter**.

---

### Step 3: Create a New Visual

Click a blank area on the Power BI canvas.

Select:

> **Clustered Column Chart**

---

### Step 4: Add the Measure

Drag:

> **Total Balance → Y-Axis**

---

### Step 5: Add Account Type

Drag:

> **Account Type → X-Axis**

The visual now represents total balance for each account type.

---

### Step 6: Resize the Visual

Resize the chart as required to fit the report layout.

---

### Step 7: Copy Formatting

Select:

> **Total Amount by Name**

Then:

**Home → Format Painter → Click Total Balance by Account Type**

---

### Step 8: Change Chart Type

If required, change the chart type.

The instructor tries:

> Stacked Bar Chart

but then chooses:

> **Clustered Bar Chart**

---

### Step 9: Change Display Units

Go to:

**Format Visual → Data Labels → Value → Display Units**

Change:

> **Auto → Thousands**

---

### Step 10: Format Savings

Under the category/color settings:

> **Savings → Green**

---

### Step 11: Format Current

Under the category/color settings:

> **Current → Red**

---

# 20. Power BI Concepts to Remember

## A. DAX Measure

A measure performs a calculation dynamically based on the context of the report.

Example:

```DAX
Total Balance = SUM('Combined Banking Data Set'[Balance])
```

---

## B. Aggregation

`SUM()` is an aggregation function.

It combines multiple balance values into one total.

```text
Multiple Balance Values
          ↓
        SUM()
          ↓
    Total Balance
```

---

## C. Dimension/Category

**Account Type** is used as the category by which the measure is analyzed.

It allows us to compare:

```text
Total Balance
      ↓
 ┌───────────┐
 │           │
Savings    Current
```

---

## D. Format Painter

Used when you want another visual to have the same formatting as an existing visual.

**Path:**

**Home → Format Painter → Target Visual**

---

## E. Display Units

Display Units control how Power BI represents numerical values.

Common options include:

* Auto
* None
* Thousands
* Millions
* Billions

In this lecture:

> **Auto → Thousands**

---

## F. Category-Specific Colors

Power BI allows individual categories in a visual to have different colors.

Here:

* **Savings → Green**
* **Current → Red**

This makes the visual easier to interpret.

---

# 21. Important Observations from the Lecture

### Observation 1

The Excel sheet suggested **Average Account Balance**, but the instructor chose to create **Total Balance by Account Type** instead.

### Observation 2

The instructor initially selected a **Clustered Column Chart**.

### Observation 3

The instructor later experimented with a **Stacked Bar Chart**.

### Observation 4

The final visualization was changed to a **Clustered Bar Chart**.

### Observation 5

The values were initially displayed in **millions**, such as approximately `0.0 million` and `-15.8 million`.

### Observation 6

To make the numbers easier to read, **Display Units** was changed from:

> **Auto → Thousands**

### Observation 7

The formatting of the previous **Total Amount by Name** chart was reused using **Format Painter**.

### Observation 8

The instructor reused the existing color scheme:

> **Savings = Green**

> **Current = Red**

### Observation 9

The hexadecimal color codes are visible in the color settings and can be reused for maintaining consistency.

---

# 22. Quick Revision Sheet

### KPI

**Total Balance by Account Type**

### DAX

```DAX
Total Balance = SUM('Combined Banking Data Set'[Balance])
```

### Visual

**Clustered Bar Chart**

### Fields

```text
X-Axis → Account Type
Y-Axis → Total Balance
```

### Formatting

```text
Format Painter → From Total Amount by Name
Display Units → Thousands
Savings → Green
Current → Red
```

### Account Types

* Savings
* Current Account

### Main Purpose

> Compare the **aggregate balance** across different account types.

---

# 23. One-Line Flow to Remember

**Excel Recommendation → Create DAX Measure → Create Chart → Add Total Balance → Add Account Type → Format Painter → Clustered Bar Chart → Display Units = Thousands → Savings = Green → Current = Red**

This is the complete workflow covered in the lecture.
