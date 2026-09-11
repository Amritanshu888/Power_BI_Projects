# Detailed Notes: Adding Customers by Age Group Chart in Power BI

## 1. Objective of the Visualization

The second chart on the report page is designed to show the **distribution of customers by age group**.

### Why is this useful?

The visualization helps us understand:

* How customers are distributed across different **age brackets**
* Which age groups have more customers
* The overall **customer demographic distribution**

The Excel recommendation suggests that this can be represented using either:

* **Column Chart**
* **Histogram**

In this session, the instructor chooses a **Column Chart**.

---

# 2. Problem: Age Group Is Not Directly Available

The existing banking dataset does **not have the required `Customer Age` and `Customer Age Group` columns**.

Therefore, these columns need to be created using **DAX calculated columns**.

There are two separate requirements:

1. Calculate the **Customer Age**
2. Categorize customers into **Customer Age Groups**

The instructor uses the DAX expressions provided in the Excel sheet.

---

# 3. Create the Customer Age Column

### Step 1: Open the Excel sheet

Go back to the Excel sheet containing the recommended DAX formulas.

The first formula is used to calculate the **Customer Age**.

### Step 2: Copy the DAX formula

* Select the DAX formula for **Customer Age**
* Press **Ctrl + A**
* Press **Ctrl + C**

### Step 3: Open Power BI Desktop

Go back to Power BI Desktop.

### Step 4: Select the banking dataset

In the Fields/Data pane:

* Locate the **Combined Banking Data** dataset/table
* Right-click on it

### Step 5: Create a new column

From the context menu:

**Right-click Combined Banking Data → New column**

Power BI may take some time to open the DAX formula bar.

### Step 6: Paste the formula

Once the formula area is available:

* Press **Ctrl + A**
* Press **Ctrl + V**
* Press **Enter**

This creates a new calculated column called:

> **Customer Age**

### Important

The instructor briefly considers undoing the action using **Ctrl + Z**, then goes back to the Excel sheet to verify the correct formula. The main point is that the **Customer Age column must be created using the provided DAX expression**.

---

# 4. Create the Customer Age Group Column

After calculating the customer's actual age, the next requirement is to divide customers into **age brackets**.

For example, the dataset shown in the session contains age groups such as:

* **26–35**
* **36–50**

The exact grouping is determined by the DAX formula provided in the Excel sheet.

### Step 1: Go back to the Excel sheet

Locate the DAX formula that calculates:

> **Customer Age Group**

### Step 2: Copy the formula

Select the formula and copy it.

**Ctrl + C**

### Step 3: Return to Power BI Desktop

Again:

* Right-click the **Combined Banking Data** table
* Select **New column**

### Step 4: Paste the DAX formula

Paste the copied formula:

**Ctrl + V**

Then press:

**Enter**

Power BI creates the second calculated column:

> **Customer Age Group**

---

# 5. Columns Created

After completing the above steps, the dataset now has two additional calculated columns:

| Column                 | Purpose                                            |
| ---------------------- | -------------------------------------------------- |
| **Customer Age**       | Stores the calculated age of each customer         |
| **Customer Age Group** | Categorizes customers into predefined age brackets |

These columns can now be used for visualization and analysis.

---

# 6. Create the Customers by Age Group Column Chart

Now that `Customer Age Group` is available, we can create the recommended visualization.

## Step 1: Go to the report page

Open **Power BI Desktop** and go to the appropriate report page, which in this session is **Page 2**.

## Step 2: Click on a blank area

Click anywhere on an empty area of the report canvas.

This ensures that a new visual is created rather than modifying an existing visual.

## Step 3: Select the Column Chart

From the Visualizations pane, select:

> **Stacked Column Chart**

This creates a blank column chart on the canvas.

Position the chart where you want it on the report page.

---

# 7. Configure the X-Axis

The purpose of the chart is:

> **Number of customers by Customer Age Group**

Therefore, the age group should be placed on the X-axis.

### Steps

* Locate **Customer Age Group**
* Double-click it or drag it into the visual
* Place it in the **X-axis** bucket

The X-axis will now contain the different age brackets.

For example:

```text
26–35
36–50
```

---

# 8. Configure the Customer Count

Next, we need to show **how many customers belong to each age group**.

For this, the instructor uses **Customer ID**.

### Steps

* Locate **Customer ID**
* Double-click it or drag it into the appropriate value/Y-axis bucket

Power BI automatically aggregates the Customer ID and provides a **count**.

Conceptually, the chart is performing:

> **Count of Customer ID grouped by Customer Age Group**

So the visualization tells us how many customers belong to each age bracket.

---

# 9. Result of the Chart

The resulting column chart contains the age groups on the X-axis and the number of customers on the Y-axis.

In the data shown during the session, two age groups are visible:

* **26–35**
* **36–50**

The height of each column represents the **number of customers** belonging to that particular age group.

### Analytical interpretation

This allows us to quickly answer questions such as:

* Which age group has the most customers?
* Which age group has fewer customers?
* How is the customer base distributed across different age brackets?

---

# 10. Format the New Column Chart

The instructor then demonstrates how to make the new chart consistent with the formatting of an existing visual.

Instead of manually formatting every property, we can use **Format Painter**.

## Step 1: Go to Page 1

Navigate to **Page 1**, where the previously created chart exists:

> **Total Balance by Account Type**

## Step 2: Select the existing chart

Click on the **Total Balance by Account Type** column chart.

## Step 3: Use Format Painter

Click:

> **Format Painter**

This copies the formatting of the selected chart.

## Step 4: Go to Page 2

Navigate back to **Page 2**.

## Step 5: Click the new age-group chart

Click the newly created **Customers by Age Group** column chart.

The formatting from the Page 1 chart is applied to the new chart.

### Benefit

This helps maintain **consistent formatting across report pages** without having to manually configure every visual.

---

# 11. Change the Column Color

After applying the Format Painter, the instructor demonstrates changing the color of the columns.

### Steps

With the new column chart selected:

1. Open **Format your visual**
2. Go to the **Columns** section
3. Locate the color option
4. Select a different color
5. Choose the desired color from the available options

This changes the appearance of the columns in the chart.

---

# 12. Complete Process — Quick Revision

The complete workflow is:

```text
Excel Sheet
     ↓
Copy Customer Age DAX formula
     ↓
Power BI Desktop
     ↓
Right-click Combined Banking Data
     ↓
New Column
     ↓
Paste DAX formula
     ↓
Customer Age created
     ↓
Excel Sheet
     ↓
Copy Customer Age Group DAX formula
     ↓
Power BI Desktop
     ↓
Right-click Combined Banking Data
     ↓
New Column
     ↓
Paste DAX formula
     ↓
Customer Age Group created
     ↓
Create Stacked Column Chart
     ↓
X-axis → Customer Age Group
     ↓
Values/Y-axis → Customer ID
     ↓
Power BI counts customers
     ↓
Apply Format Painter
     ↓
Customize column color
     ↓
Customers by Age Group chart completed
```

---

# 13. Key Concepts / Keywords

### **Customer Age**

A calculated column containing the age of each customer.

### **Customer Age Group**

A calculated/categorized column that places customers into predefined age brackets.

### **Calculated Column**

A column created using a DAX expression inside Power BI.

### **DAX**

**Data Analysis Expressions**, the formula language used in Power BI for calculations, calculated columns, and measures.

### **Stacked Column Chart**

A column-based visual that can be used to compare values across categories.

### **X-axis**

Contains the categories being compared.

Here:

> **Customer Age Group → X-axis**

### **Customer ID**

Used to count the number of customers.

### **Format Painter**

Copies the formatting of one visual and applies it to another visual.

### **Format Your Visual**

Power BI's formatting pane where properties such as colors and other visual settings can be customized.

---

## 14. Important Takeaways

* The dataset initially does **not** contain the required age-group information.
* We first create **Customer Age** using a DAX calculated column.
* We then create **Customer Age Group** using another DAX calculated column.
* A **column chart** is used to visualize customer distribution by age group.
* `Customer Age Group` goes on the **X-axis**.
* `Customer ID` is used to calculate the **customer count**.
* The chart can be formatted using **Format Painter** to maintain consistency with other visuals.
* Column colors can be customized through **Format your visual → Columns**.
* The final chart helps understand the **distribution of customers across age brackets**.
