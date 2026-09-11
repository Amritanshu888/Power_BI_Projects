# Detailed Notes: Renaming the Age Group Chart & Adding Accounts by Account Type

This session covers two main activities:

1. **Renaming the previously created Customer Age Group column chart**
2. **Creating a new Account Type visualization using a Treemap**

---

# 1. Rename the Customer Age Group Column Chart

The previously created chart currently has a default title/label such as:

> **Count of Customer ID**

This isn't descriptive enough, so the instructor changes the title to clearly communicate what the chart represents.

### Steps

1. Click on the **Customer Age Group column chart**.
2. With the chart selected, open **Format Visual**.
3. Go to the **General** section.
4. Locate **Title**.
5. Change the title to:

> **Number of Customers by Age Group**

### Why rename the chart?

A descriptive title makes the dashboard easier to understand.

Instead of:

> Count of Customer ID

the user immediately understands that the chart represents:

> **Number of Customers by Age Group**

---

# 2. Move to the Next Visualization

The Excel sheet contains recommendations for another visualization.

The fourth recommendation is:

> **Accounts by Account Type**

### Purpose

This visualization helps us understand:

> **The number of accounts available for each account type.**

For example, the banking dataset contains account types such as:

* Current
* Savings

The visualization will show how many accounts belong to each type.

---

# 3. Recommended Visualizations

The Excel sheet suggests two possible visualizations:

### Option 1: Clustered Bar Chart

A clustered bar chart can be used to compare the number of accounts across account types.

### Option 2: Treemap

A **Treemap** can also represent account types and their corresponding account counts.

In this session, the instructor chooses:

> **Treemap**

---

# 4. Create the Account Count Measure

The Excel sheet provides a **DAX measure** for calculating the number of accounts.

The measure is based on the **Account ID**.

Conceptually, the measure calculates:

> **Count of Account IDs**

This gives us the total number of accounts.

---

# 5. Copy the DAX Measure

### Step 1: Open the Excel sheet

Go to the Excel sheet containing the recommended DAX expression.

### Step 2: Select the measure

The instructor double-clicks/selects the DAX measure.

Then:

* **Ctrl + A**
* **Ctrl + C**

The instructor specifically copies the required portion of the formula rather than unnecessary text.

---

# 6. Create a New Measure in Power BI

Return to **Power BI Desktop**.

### Step 1: Locate the Measures table

In the Fields/Data pane, locate the:

> **Measures** table

### Step 2: Create a new measure

Right-click the **Measures** table.

Select:

> **New measure**

### Step 3: Paste the DAX formula

In the formula bar:

* Press **Ctrl + A**
* Press **Ctrl + V**
* Press **Enter**

This creates a measure that calculates the:

> **Count of Account IDs**

The resulting measure is referred to as:

> **Account Count by Type**

---

# 7. Understanding the Measure

The purpose of this measure is to calculate the number of accounts.

The visualization will ultimately use:

**Account Type + Account Count**

Conceptually:

```text
Account Type → Category
Account Count → Values
```

For example:

| Account Type | Account Count |
| ------------ | ------------: |
| Current      |           200 |
| Savings      |           200 |

The exact values shown in the lecture are **200 current accounts and 200 savings accounts**.

---

# 8. Create the Treemap

Now we can create the recommended Treemap.

### Step 1: Return to Power BI Desktop

Go back to the report page.

### Step 2: Select a blank area

Click on a **blank area of the report canvas**.

This ensures that a new visual is created.

### Step 3: Select Treemap

From the Visualizations pane, select:

> **Treemap**

A blank Treemap will appear on the canvas.

### Step 4: Position and resize it

Place the Treemap in the desired location on the report page.

The instructor also increases its size to make it more visible.

---

# 9. Add Account Type to the Treemap

The first field required is **Account Type**.

### Steps

1. Locate **Account Type**.
2. Double-click it or drag it into the Treemap.
3. Place it in the:

> **Category**

bucket.

Therefore:

> **Account Type → Category**

This determines the different sections/categories displayed in the Treemap.

---

# 10. Add Account Count by Type

Next, we need to determine the size/value of each Treemap section.

### Steps

1. Locate the previously created measure:

   > **Account Count by Type**
2. Double-click it or drag it into the Treemap.
3. Place it in:

> **Values**

Therefore:

> **Account Count by Type → Values**

The Treemap now represents the number of accounts for each account type.

---

# 11. Resulting Treemap

The completed Treemap shows the account types and their corresponding account counts.

Based on the data shown in the lecture:

* **Current Accounts → 200**
* **Savings Accounts → 200**

Because both account types have the same count, their Treemap areas are approximately equal.

### Conceptually:

```text
              Accounts by Account Type

        ┌─────────────────┬─────────────────┐
        │                 │                 │
        │     Current     │     Savings     │
        │      200        │       200       │
        │                 │                 │
        └─────────────────┴─────────────────┘
```

The actual appearance will depend on Power BI's Treemap rendering and formatting.

---

# 12. Apply Existing Formatting Using Format Painter

The instructor wants the new Treemap to have formatting consistent with an existing chart.

### Steps

1. Select the existing **column chart/bar chart** whose formatting you want to copy.
2. Go to the **Home** tab.
3. Click:

> **Format Painter**

4. Click on the newly created **Treemap**.

The Treemap inherits the formatting from the selected chart.

### Important

The instructor initially performs the action, then repeats it after navigating back to the report because of a selection/navigation issue.

The important workflow is:

```text
Select correctly formatted chart
        ↓
Home
        ↓
Format Painter
        ↓
Select Treemap
        ↓
Formatting applied
```

---

# 13. Resize the Visuals

After creating the Treemap, the instructor adjusts the size and positioning of the visuals.

The instructor mentions:

* Resizing the Treemap
* Increasing the size of the chart
* Adjusting the existing visuals
* Making better use of the available report canvas

### General resizing process

1. Click the visual.
2. Use the resize handles around the visual.
3. Drag the handles to increase/decrease:

   * Width
   * Height
4. Position the visual appropriately on the canvas.

This helps maintain a clean dashboard layout.

---

# 14. Data Observation

The instructor observes that the dataset contains:

> **200 Current Accounts**

and

> **200 Savings Accounts**

Therefore:

> **Total accounts = 400**

The Treemap represents the distribution of these accounts by account type.

---

# 15. Donut Chart Mentioned at the End

Toward the end of the lecture, the instructor also refers to the existing **donut chart**.

The instructor says that the donut chart can also be resized.

### Resizing process

* Click the donut chart.
* Use its resize handles.
* Increase or decrease its size according to the dashboard layout.

The instructor then mentions increasing the size of another column chart as well.

The purpose here is primarily **dashboard layout adjustment**—making the existing visuals fit properly and remain readable.

---

# 16. Complete Workflow

The entire session can be summarized as:

```text
Existing Age Group Chart
        ↓
Select chart
        ↓
Format Visual
        ↓
General → Title
        ↓
Rename to "Number of Customers by Age Group"
        ↓
Open Excel recommendations
        ↓
Recommendation: Accounts by Account Type
        ↓
Possible visuals:
Clustered Bar Chart / Treemap
        ↓
Choose Treemap
        ↓
Copy Account Count DAX measure
        ↓
Power BI
        ↓
Right-click Measures table
        ↓
New Measure
        ↓
Paste DAX
        ↓
Account Count measure created
        ↓
Create Treemap
        ↓
Account Type → Category
        ↓
Account Count by Type → Values
        ↓
Treemap created
        ↓
Apply Format Painter
        ↓
Resize/reposition visuals
        ↓
Dashboard layout improved
```

---

# 17. Important Power BI Concepts

| Concept                   | Meaning / Use                                                            |
| ------------------------- | ------------------------------------------------------------------------ |
| **Visual Title**          | Describes what a chart represents                                        |
| **Format Visual**         | Used to customize the selected visual                                    |
| **General → Title**       | Used to change the title of a visual                                     |
| **DAX Measure**           | A calculation evaluated dynamically based on the report context          |
| **New Measure**           | Creates a DAX measure in Power BI                                        |
| **Treemap**               | Visualizes hierarchical/category data using differently sized rectangles |
| **Category**              | Defines the categories represented in the Treemap                        |
| **Values**                | Determines the numerical size/value represented by the Treemap           |
| **Account Type**          | Category such as Current or Savings                                      |
| **Account Count by Type** | Measure calculating the number of accounts                               |
| **Format Painter**        | Copies formatting from one visual to another                             |
| **Resize Handles**        | Used to change the dimensions of a visual                                |

---

# 18. Key Takeaways

* Always give visuals **meaningful and descriptive titles**.
* The age-group chart is renamed to **Number of Customers by Age Group**.
* The next recommended analysis is **Accounts by Account Type**.
* The Excel sheet recommends either a **Clustered Bar Chart** or **Treemap**.
* The lecture chooses a **Treemap**.
* A DAX **measure** is created to count Account IDs.
* The **Measures** table is used to store the measure.
* In the Treemap:

  * **Account Type → Category**
  * **Account Count by Type → Values**
* The dataset shows **200 Current accounts and 200 Savings accounts**.
* **Format Painter** can be used to maintain consistent formatting across visuals.
* Visuals can be resized and repositioned to improve the overall **dashboard layout and readability**.
