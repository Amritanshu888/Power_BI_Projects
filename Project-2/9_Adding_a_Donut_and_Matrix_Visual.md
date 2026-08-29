# Power BI Lecture Notes — Adding Donut Chart and Matrix Visual

This lecture focuses on adding **two more visuals** to the existing Power BI report page:

1. **Donut Chart** — to show the count of active vs. inactive policies.
2. **Matrix Visual** — to show claim coverage amounts by policy type and claim status. 

---

## 1. Adding the Donut Chart

### Objective

The first visual is a **donut chart** that represents the:

* Number of **Active policies**
* Number of **Inactive policies**

However, the existing dataset does not contain a column that directly identifies whether a policy is active or inactive. Therefore, a new column needs to be created first. 

---

## 2. Create an Active/Inactive Column

Since the required field does not exist, we use **Power Query Editor** to create it.

### Steps

1. Go to **Power BI Desktop**.
2. Click **Transform Data**.
3. This opens the **Power Query Editor**.
4. Go to:
   **Add Column → Conditional Column**. 

### Create the conditional column

Rename the new column:

**Active / Inactive**

The logic used in the lecture is:

> If the **Policy End Date** is less than or equal to today's date → **Inactive**
> Otherwise → **Active**

For demonstration, the instructor assumes:

**Today's date = 10 December 2024**

Therefore:

| Condition                     | Result   |
| ----------------------------- | -------- |
| Policy End Date ≤ 10-Dec-2024 | Inactive |
| Policy End Date > 10-Dec-2024 | Active   |

The date is only an example; another date can be used depending on the requirement. 

### Complete the column

After defining the condition:

1. Click **OK**.
2. Power Query creates the new **Active / Inactive** column.
3. Change its **Data Type** to **Text**.
4. The column will contain values such as:

   * Active
   * Inactive 

---

# 3. Apply the Power Query Changes

Now return to the Power BI report.

### Steps

1. Click the **Home** tab in Power Query Editor.
2. Click the dropdown associated with the close/apply option.
3. Select **Close & Apply**. 

Power BI will now:

* Apply the Power Query transformation.
* Load the modified data into the model.
* Potentially take some time while evaluating/loading the data.

The lecture notes that the dataset contains **10,000 rows**, and all rows are loaded successfully. 

---

# 4. Create the Donut Chart

Once the data has loaded:

### Steps

1. Click on a **blank area of the report canvas**.
2. Select the **Donut Chart** visual.
3. A blank donut chart appears.
4. Resize it according to your report layout. 

### Add the Active/Inactive field

From the **Data pane**:

1. Find the newly created **Active / Inactive** column.
2. Drag it into the **Legend** field.
3. Drag the same field into the **Values** field.

The donut chart will now count how many records are:

* Active
* Inactive 

### Why the same column is used twice?

* **Legend** → determines the categories/segments.
* **Values** → counts the occurrences of each category.

So the donut is effectively showing:

**Count of Active vs. Count of Inactive policies.**

---

# 5. Format the Donut Chart

The instructor then formats the donut chart to make it more visually appealing.

Select the donut chart and click:

**Format Your Visual**

---

## 5.1 Change Segment Colors

The default colors are changed.

The desired representation is:

* **Green → Active**
* **Yellow → Inactive**

This makes the chart easier to interpret visually. 

---

## 5.2 Change the Chart Title

With the donut chart selected:

1. Go to **Format Your Visual**.
2. Open **General**.
3. Open **Title**.
4. Change the title.

Instead of the automatically generated title such as:

**Count of Active and Inactive**

use:

### **Count of Active / Inactive Policies**

The title can also be formatted by changing:

* Font style
* Bold
* Italic
* Underline
* Alignment

The lecture keeps the title **bold and centered**. 

---

## 5.3 Add a Border to the Donut Chart

To add a border:

1. Collapse the **Title** section.
2. Open **Effects**.
3. Turn **Visual Border** → **On**.
4. Change the border color to **White**. 

---

# 6. Format the Legends

The donut chart contains legends representing the categories.

To format them:

1. Go to **Visual** formatting.
2. Open **Legends**.
3. Under **Text**, change the text formatting.
4. Increase the font size if required.
5. Make the text **bold** if desired. 

---

# 7. Format the Donut Data Labels

The numbers displayed on the donut are the **detail labels**.

To format them:

1. Open **Detail Labels**.
2. Change the font style.
3. Increase the font size.
4. Make them bold if desired. 

The final donut chart shows approximately:

* **5.81K Active policies**
* **4.19K Inactive policies**

with:

* Green = Active
* Yellow = Inactive 

---

# 8. Adding the Matrix Visual

The second visual introduced in the lecture is a **Matrix visual**.

### Objective

The matrix should represent:

**Claim Coverage Amount**

broken down by:

1. **Policy Type**
2. **Claim Status**

The required claim status categories include:

* Pending
* Rejected
* Settled

The policy types include:

* Auto
* Health
* Home
* Life 

---

# 9. Create the Matrix Visual

### Step 1 — Insert the visual

1. Click on a **blank area of the report canvas**.
2. Select the **Matrix** visual.

A blank matrix appears.

---

## Step 2 — Add Coverage Amount

From the Data pane:

1. Locate **Coverage Amount**.
2. Drag it into the **Values** section.

This determines the numerical values displayed in the matrix. 

---

## Step 3 — Add Policy Type to Rows

1. Locate **Policy Type**.
2. Drag it into the **Rows** section.

The different policy types will now appear as rows:

* Auto
* Health
* Home
* Life 

---

## Step 4 — Add Claim Status to Columns

1. Locate **Claim Status**.
2. Drag it into the **Columns** section.

The matrix will now split the coverage amounts based on claim status:

* Pending
* Rejected
* Settled 

---

# 10. Understanding the Matrix Structure

The resulting matrix provides a cross-tabulation of:

**Policy Type × Claim Status**

Conceptually:

| Policy Type |  Pending | Rejected |  Settled | Total |
| ----------- | -------: | -------: | -------: | ----: |
| Auto        | Coverage | Coverage | Coverage | Total |
| Health      | Coverage | Coverage | Coverage | Total |
| Home        | Coverage | Coverage | Coverage | Total |
| Life        | Coverage | Coverage | Coverage | Total |

The exact numerical values are generated automatically from the dataset.

Power BI also automatically calculates:

* Totals for each policy type.
* Totals for each claim-status category.
* Overall totals where applicable.

The lecture specifically highlights that totals are represented for each policy type and for the claim-status categories. 

---

# 11. Format the Matrix

After creating the matrix, formatting is performed using:

**Format Your Visual**

---

## 11.1 Format Values

With the matrix selected:

1. Open **Format Your Visual**.
2. Go to **Values**.
3. Change the font style as required.

The instructor modifies the value formatting during the demonstration. 

---

## 11.2 Format Column Headers

Next:

1. Collapse the **Values** section.
2. Open **Column Headers**.
3. Change the font style.

This affects headers such as:

* Pending
* Rejected
* Settled



---

## 11.3 Format Row Headers

Similarly:

1. Open **Row Headers**.
2. Change the font style.

This affects the policy-type labels such as:

* Auto
* Health
* Home
* Life 

---

# 12. Configure Grid Lines

The matrix can also be formatted using grid lines.

The instructor demonstrates that grid lines can be turned on.

### Steps

1. Go to the relevant **Grid** / **Grid Lines** formatting options.
2. Turn grid lines **On**.
3. Configure the **vertical grid lines** if required.
4. Change their color.

The lecture uses **white** for the grid-line color. 

Similarly, the border color is also changed to white. 

---

# 13. Add Borders to the Matrix

The lecture demonstrates two different kinds of borders.

### A. Borders around the matrix's grid structure

With the matrix selected:

1. Open **Format Your Visual**.
2. Go to the **Grid Lines** section.
3. Configure the borders.
4. Add:

   * Top border
   * Bottom border
   * Left border
   * Right border
5. Use the desired color, demonstrated as white. 

---

## B. Outer Visual Border

An additional border can be placed around the **entire matrix visual**.

### Steps

1. Select the matrix.
2. Open **Format Your Visual**.
3. Go to **General**.
4. Open **Effects**.
5. Turn on the **Visual Border**.
6. Change its color if required.

The instructor changes the outer border color from black to white. 

### Important distinction

There are effectively two formatting concepts here:

* **Grid/border settings inside the matrix** → control the matrix structure.
* **Visual Border under General → Effects** → creates a border around the entire visual container.

---

# 14. Final Report Layout

After adding and formatting both visuals, the instructor adjusts their:

* Size
* Position
* Overall layout

according to convenience. 

The completed report page now contains the newly added visuals and their formatting.

---

# 15. Overall Workflow

The complete workflow demonstrated in this lecture is:

**Existing Power BI Report**

↓

**Identify missing field required for visual**

↓

**Transform Data**

↓

**Add Column → Conditional Column**

↓

Create **Active / Inactive**

↓

**Close & Apply**

↓

**Return to Report View**

↓

**Add Donut Chart**

↓

Add Active/Inactive to:

* Legend
* Values

↓

**Format Donut Chart**

* Colors
* Title
* Legends
* Detail labels
* Border

↓

**Add Matrix Visual**

↓

Configure:

* Coverage Amount → Values
* Policy Type → Rows
* Claim Status → Columns

↓

**Format Matrix**

* Values
* Column headers
* Row headers
* Grid lines
* Borders

↓

**Resize and position visuals**

↓

**Final Power BI Report**

---

# 16. Key Concepts to Remember

### Donut Chart

Used here to show a **categorical distribution**:

> Active vs. Inactive policies.

The important configuration is:

**Active/Inactive → Legend**

**Active/Inactive → Values**

This allows Power BI to count the records belonging to each category. 

### Conditional Column

Used when a required classification/category doesn't already exist in the dataset.

Here:

> Policy End Date ≤ assumed current date → Inactive
> Policy End Date > assumed current date → Active



### Matrix

Useful for displaying a measure across **multiple dimensions**.

Here:

> **Coverage Amount** by **Policy Type** and **Claim Status**

Configuration:

* **Values:** Coverage Amount
* **Rows:** Policy Type
* **Columns:** Claim Status 

### Formatting

The lecture demonstrates that Power BI visuals can be customized through **Format Your Visual**, including:

* Font styles
* Font sizes
* Bold/italic/underline
* Colors
* Titles
* Legends
* Data/detail labels
* Grid lines
* Borders
* Visual borders

---

## 17. What's Coming Next

The lecture ends by introducing the next topics:

1. **Creating roles**
2. **Implementing Row-Level Security (RLS)**
3. **Publishing the report to Power BI Service**

Power BI Service is described as the second major element of Power BI after Power BI Desktop in the context of the course. 
