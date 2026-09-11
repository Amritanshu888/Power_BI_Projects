# Detailed Notes: Creating the Third KPI Visual — Top Customers by Transaction Value

## 1. Overview of the Session

This session continues the **Power BI report creation** process.

The instructor returns to the Excel sheet generated/recommended by Perplexity and discusses the **third KPI recommendation**.

The KPI is:

> **Top Customers by Transaction Value**

The purpose is to identify customers who have the highest transaction values.

Unlike the previous KPIs, this KPI does **not require a new DAX calculation**. The existing **Transaction Amount** field can be used directly, and Power BI's **Top N filtering** can be applied.

The instructor ultimately creates a:

> **Stacked Bar Chart**

and configures it to show the **Top 2 customers** based on transaction amount, because only a small number of identifiable customer names are available in the data.

---

# 2. Third KPI Recommendation

The instructor opens the Excel sheet again.

The third recommendation is related to:

> **Top-end customers by transaction value**

The recommendation indicates that:

* No additional DAX calculation is required.
* A **bar chart** can be used.

The instructor chooses:

> **Stacked Bar Chart**

---

# 3. Why No New DAX Measure Is Required

For the previous KPIs, measures were created such as:

* Count of Transactions
* Monthly Transaction Amount

For this KPI, the existing:

> **Transaction Amount**

column can be directly aggregated by Power BI.

Therefore, there is no need to create a separate DAX measure for this particular visual.

Power BI can automatically calculate:

> **Sum of Transaction Amount**

when the Amount field is placed in the appropriate value bucket.

---

# 4. Creating the Stacked Bar Chart

## Steps

### Step 1: Open Power BI Desktop

Return to the Power BI report.

### Step 2: Click on a blank area

Click an empty area of the report canvas so that a new visual can be created.

### Step 3: Select Stacked Bar Chart

From the Visualizations pane, select:

> **Stacked Bar Chart**

A blank bar chart appears.

### Step 4: Resize the chart

The instructor resizes the chart and initially positions it toward the:

> **Right-hand side**

The exact position can be adjusted later as more visuals are added.

---

# 5. Adding Transaction Amount

The dataset contains a column for:

> **Transaction Amount**

This is the numerical value that will determine which customers have the highest transaction value.

## Steps

From:

> **Combined Banking Data Set**

locate the **Amount/Transaction Amount** column.

Then:

> Double-click or drag and drop it into the **X-axis**

For a horizontal bar chart:

* X-axis → numerical values
* Y-axis → categories

Power BI therefore uses the transaction amount as the horizontal measure.

The aggregation shown by Power BI is essentially:

> **Sum of Amount**

---

# 6. Adding Customer Name

The dataset also contains:

> **Customer Name**

This field identifies the customers.

## Steps

1. Locate the customer name field.
2. Double-click it or drag and drop it into the:

   > **Y-axis**

The chart now represents:

> **Transaction Amount by Customer Name**

---

# 7. Problem: Blank Customer Names

After adding Customer Name to the chart, the instructor observes that there are:

* Three identifiable customer names
* Many blank values

The blank values mean that the dataset contains records where the customer name is not available.

The instructor does not want these blank customer names to remain unidentified.

Instead, the instructor decides to replace the blank/null values with:

> **Unknown**

This is a data-cleaning operation and is performed in **Power Query Editor**.

---

# 8. Replacing Null Customer Names with "Unknown"

The instructor opens:

> **Power Query Editor**

using:

> **Transform Data**

---

## Steps

### Step 1: Open Power Query

In Power BI Desktop, select:

> **Transform Data**

This opens Power Query Editor.

### Step 2: Find the Customer Name column

Scroll horizontally to the right until the relevant:

> **Name / Customer Name**

column is visible.

### Step 3: Right-click the column

Right-click the customer name column.

### Step 4: Select Replace Values

Choose:

> **Replace Values**

### Step 5: Replace null values

Specify that the null values should be replaced with:

> **Unknown**

### Step 6: Click OK

Click:

> **OK**

The blank/null customer names are now replaced with the text:

> **Unknown**

---

# 9. Apply the Power Query Changes

After replacing the null values, the instructor returns the data to Power BI.

## Steps

Click:

> **Close & Apply**

Power BI applies the transformation and returns to the report.

The data loading process may take some time.

The instructor waits until the data is successfully loaded.

---

# 10. Verifying the Replacement

After the data has loaded, the instructor checks the chart.

Previously, blank customer names were displayed.

Now those blank values appear as:

> **Unknown**

So the transformation has worked correctly.

---

# 11. Removing "Unknown" from the Chart

The next issue is that the instructor wants to show the **top customers**, not the unknown category.

There are only:

* Three actual customer names
* One `Unknown` category

Therefore, displaying `Unknown` does not provide useful information for identifying top customers.

The instructor decides to remove it from this visual using a **visual-level filter**.

---

# 12. Filtering Out the Unknown Customer

## Steps

### Step 1: Select the chart

Click the bar chart.

### Step 2: Open the Filters pane

Expand:

> **Filters**

### Step 3: Locate the Name field

Find the customer name filter.

### Step 4: Select all values

Click:

> **Select All**

### Step 5: Uncheck Unknown

Remove the check mark from:

> **Unknown**

Now only the actual customer names remain.

### Step 6: Collapse the Filters pane

After applying the filter, the Filters pane can be collapsed.

---

# 13. Understanding Why "Unknown" Is Removed

The instructor's objective is to identify the **top customers**.

`Unknown` is not a customer name.

Therefore, including it would make the visualization less meaningful.

The data-cleaning step converts missing names to a meaningful label:

> `Unknown`

Then the visualization step excludes that label when analyzing actual customers.

This is a useful distinction:

> **Data cleaning** handles missing information.

> **Filtering** determines what should be included in a particular visual.

---

# 14. Top N Filtering

The instructor now demonstrates an important Power BI feature:

> **Top N Filtering**

The dataset contains only three actual customer names.

Therefore, there is no point in displaying **Top 5** customers because only three named customers are available.

The instructor decides to demonstrate:

> **Top 2**

instead.

This is useful for learning how the **Top N filter** works.

---

# 15. Applying a Top 2 Filter

## Step 1: Select the chart

Click the bar chart.

### Step 2: Expand the Filters pane

Open the:

> **Filters pane**

### Step 3: Add the Name field to the filter

Locate the customer:

> **Name**

field.

Drag and drop it into the appropriate:

> **Filters on this visual / Add Data Fields**

section.

---

# 16. Change Basic Filtering to Top N Filtering

Initially, Power BI provides basic filtering options.

The instructor changes this to:

> **Top N filtering**

This tells Power BI:

> Only display the top N categories according to a specified numerical value.

---

# 17. Specify Top 2

The instructor wants the top two customers.

Therefore, under the Top N setting, enter:

> **2**

So the filter becomes:

> **Top 2**

---

# 18. Selecting "By Value"

Top N filtering requires Power BI to know:

> Top according to what value?

In this case, customers should be ranked according to:

> **Transaction Amount**

Therefore, Transaction Amount is used in the:

> **By value**

bucket.

---

## Steps

1. Find:

   > **By value**
2. Select/double-click:

   > **Amount**
3. Drag it into the **By value** area.
4. Power BI uses:

   > **Sum of Amount**

as the ranking criterion.

---

# 19. Apply the Top N Filter

This is an important step.

After specifying:

* Top N → Top 2
* By value → Sum of Amount

click:

> **Apply Filter**

### Important

The instructor specifically emphasizes not forgetting to click:

> **Apply Filter**

Without applying the filter, the desired Top N result will not be reflected in the visual.

---

# 20. Result of the Top 2 Filter

The chart now displays:

> **The two customers with the highest transaction amounts.**

The instructor observes that one transaction amount is negative.

A negative transaction amount may represent something such as:

> **Debit**

The instructor acknowledges this possibility but does not change the data or filtering logic.

The Top N filter continues to work based on the transaction amount.

---

# 21. Formatting the Bar Chart

After applying the required filtering, the instructor formats the visual.

The goal is to improve:

* Readability
* Appearance
* Consistency with the other report visuals

---

# 22. Changing the Chart Title

The default title may display something like:

> **Sum of Amount**

The instructor changes this to:

> **Total Amount by Name**

This is more meaningful and user-friendly.

---

## Steps

1. Select the chart.
2. Open:

   > **Format Your Visual**
3. Go to:

   > **General**
4. Expand:

   > **Title**
5. Change the title text to:

   > **Total Amount by Name**

---

# 23. Center-Aligning the Title

The instructor scrolls within the title settings and changes the alignment.

Set:

> **Alignment → Center**

This makes the title consistent with the desired report layout.

---

# 24. Formatting the Title Font

The instructor changes the title's font style.

The font can be selected according to personal preference.

The instructor also makes the title:

> **Bold**

The title color is already:

> **Black**

so it can remain unchanged.

---

# 25. Adding Border and Shadow

The instructor collapses the Title settings and expands:

> **Effects**

Two effects are enabled:

### Border

> **On**

### Shadow

> **On**

These effects make the visual stand out from the report canvas.

---

# 26. Changing Shadow Color

The shadow settings are expanded.

The instructor changes the shadow color from the default black to:

> **White, 30% darker**

This is the same general styling approach used for the other charts in the report.

---

# 27. Removing Gridlines

The instructor now moves to the visual-specific formatting options.

Under:

> **Gridlines**

there are visible vertical gridlines.

The instructor does not want these gridlines in the current design.

## Steps

1. Find:

   > **Gridlines**
2. Turn:

   > **Gridlines → Off**

The chart becomes cleaner.

---

# 28. Formatting the X-Axis

The X-axis represents the numerical transaction amount.

The instructor does not want the X-axis title or numerical values to be displayed.

## Steps

Expand:

> **X-axis**

Then set:

> **Values → Off**

and:

> **Title → Off**

### Result

The horizontal axis no longer displays its values or title.

---

# 29. Formatting the Y-Axis

The Y-axis contains the customer names.

The instructor wants to keep the names visible but does not need a separate Y-axis title.

## Steps

Expand:

> **Y-axis**

Set:

> **Title → Off**

The customer names remain visible.

---

# 30. Formatting Customer Names

The customer names displayed along the Y-axis can be formatted.

The instructor changes:

* Font style
* Color
* Font size

The color may be set to:

> **Black**

The font size is increased slightly to improve readability.

---

# 31. Formatting the Bars

The instructor then customizes the colors of the individual bars.

There are only two customer categories remaining after applying the Top 2 filter.

For each customer, a separate color can be selected.

---

## Formatting Sara Khan

The instructor selects:

> **Sara Khan**

and changes the bar color.

The instructor considers a color such as:

* Green
* A lighter shade of green

The reason mentioned is that the transaction amount is positive.

The exact color is not mandatory.

---

# 32. Formatting the Other Customer

The instructor selects the other customer.

This customer's transaction amount is negative.

Therefore, the instructor chooses a:

> **Red**

or reddish shade for this bar.

Again, the exact shade can be selected according to preference.

### Design logic

Conceptually:

* **Positive transaction amount → Green**
* **Negative transaction amount → Red**

This makes the sign of the transaction visually intuitive.

---

# 33. Enabling Data Labels

The instructor then decides to display the actual values directly on the bars.

## Steps

1. Select the chart.
2. Expand the Visualizations pane if it is collapsed.
3. Click:

   > **Format Your Visual**
4. Find:

   > **Data labels**
5. Turn:

   > **Data labels → On**

The transaction values are now displayed directly on the chart.

---

# 34. Formatting Data Label Position

The instructor expands:

> **Data labels**

The current position is:

> **Auto**

The instructor changes it to:

> **Outside end**

### Why?

This places the numerical value at the end of the bar, making it easier to read.

---

# 35. Formatting Data Label Values

Under the data label value settings, the instructor changes:

> **Color → Black**

The instructor also mentions that the following can be customized:

* Font style
* Font size

The size is reduced slightly to make the labels fit comfortably.

---

# 36. Final Chart Configuration

The completed visual represents:

> **Top Customers by Transaction Value**

using a:

> **Stacked Bar Chart**

### Data fields

| Bucket     | Field                              |
| ---------- | ---------------------------------- |
| **X-axis** | Transaction Amount / Sum of Amount |
| **Y-axis** | Customer Name                      |

### Filter

> **Top 2 customers by Sum of Amount**

### Excluded

> **Unknown**

---

# 37. Data Cleaning Performed in This Session

An important part of this session is that the instructor did not only create a visualization.

A data-cleaning transformation was also performed.

### Problem

Customer Name contained:

> Null/blank values

### Solution

In Power Query:

> **Replace Values**

Null values were replaced with:

> **Unknown**

### Then

For the specific visual, `Unknown` was excluded using a filter.

This gives us:

```text
Raw Data
   ↓
Null Customer Names
   ↓
Power Query
   ↓
Replace null with "Unknown"
   ↓
Power BI
   ↓
Exclude "Unknown" from this visual
```

---

# 38. Why Replace Null with "Unknown" Instead of Leaving It Blank?

Replacing nulls with `Unknown` makes the missing information explicit.

Instead of seeing:

```text
Blank
Blank
Blank
```

we see:

```text
Unknown
Unknown
Unknown
```

This is more understandable when analyzing the dataset.

However, because this particular KPI is specifically about **named top customers**, the `Unknown` category is subsequently excluded.

---

# 39. Understanding Top N Filtering

Top N filtering is an important Power BI feature demonstrated in this session.

Suppose we have:

| Customer   | Amount |
| ---------- | -----: |
| Customer A | 50,000 |
| Customer B | 40,000 |
| Customer C | 25,000 |
| Customer D | 10,000 |

If we apply:

> **Top 2 by Amount**

Power BI returns:

| Customer   | Amount |
| ---------- | -----: |
| Customer A | 50,000 |
| Customer B | 40,000 |

The ranking is determined by the numerical field selected under:

> **By value**

In this lecture:

> **Sum of Amount**

is the ranking value.

---

# 40. Important: Top N vs. Basic Filtering

### Basic Filtering

Used when you want to manually choose categories.

For example:

```text
☑ Customer A
☑ Customer B
☐ Customer C
☐ Unknown
```

### Top N Filtering

Used when you want Power BI to automatically select categories based on a numerical value.

For example:

> Top 2 customers by Sum of Amount

This is especially useful when there are many customers and manually selecting the top customers would be impractical.

---

# 41. Important: Why Top 2 Instead of Top 5?

The original recommendation discusses top customers, potentially with a larger Top N value.

However, the instructor observes that the dataset contains only:

* Three named customers
* One Unknown category

After removing `Unknown`, only three actual customer categories remain.

Therefore:

> Showing Top 5 would not be meaningful.

The instructor uses:

> **Top 2**

to demonstrate the Top N filtering functionality.

This is a practical example of adapting a recommended visualization to the actual data available.

---

# 42. Negative Transaction Amount

The instructor notices that one of the displayed transaction amounts is negative.

The instructor suggests that it may represent:

> **Debit**

This is plausible because transaction datasets can contain positive and negative values depending on how credits/debits are represented.

However, the lecture does not modify the negative value.

The value is retained as it exists in the dataset.

---

# 43. Complete Step-by-Step Workflow

## Part A — Create the visual

1. Open the Excel recommendation sheet.
2. Identify the third KPI:

   > **Top Customers by Transaction Value**
3. Note that no new DAX calculation is required.
4. Open Power BI Desktop.
5. Click a blank area of the canvas.
6. Select:

   > **Stacked Bar Chart**
7. Resize and position the chart.

---

## Part B — Add fields

8. Expand:

   > **Combined Banking Data Set**
9. Add:

   > **Transaction Amount → X-axis**
10. Add:

> **Customer Name → Y-axis**

---

## Part C — Handle missing customer names

11. Notice the blank customer names.
12. Open:

> **Transform Data**

13. In Power Query, locate the Customer Name column.
14. Right-click it.
15. Select:

> **Replace Values**

16. Replace null values with:

> **Unknown**

17. Click:

> **OK**

18. Click:

> **Close & Apply**

19. Wait for the data to reload.

---

## Part D — Exclude Unknown

20. Select the chart.
21. Open the:

> **Filters pane**

22. Locate the Name field.
23. Click:

> **Select All**

24. Uncheck:

> **Unknown**

25. Collapse the Filters pane.

---

## Part E — Apply Top N filtering

26. Select the chart.
27. Open the Filters pane.
28. Add the **Name** field to the visual filters.
29. Change filtering from:

> **Basic filtering**

to:

> **Top N**

30. Enter:

> **2**

31. Under **By value**, add:

> **Amount**

32. Use:

> **Sum of Amount**

33. Click:

> **Apply Filter**

The chart now displays the top two customers based on transaction amount.

---

## Part F — Format the chart

34. Select the chart.
35. Open:

> **Format Your Visual**

36. Go to:

> **General → Title**

37. Change title to:

> **Total Amount by Name**

38. Center-align the title.
39. Change the font style.
40. Make the title bold.
41. Keep the title black.
42. Go to:

> **Effects**

43. Turn:

> **Border → On**

44. Turn:

> **Shadow → On**

45. Change shadow color to:

> **White, 30% darker**

46. Go to:

> **Gridlines**

47. Turn:

> **Gridlines → Off**

48. Open:

> **X-axis**

49. Turn:

> **Values → Off**

50. Turn:

> **Title → Off**

51. Open:

> **Y-axis**

52. Turn:

> **Title → Off**

53. Format the customer-name font.
54. Change customer-name color if desired.
55. Adjust the font size.

---

## Part G — Format individual bars

56. Go to the bar formatting options.
57. Select the first customer, such as **Sara Khan**.
58. Choose a suitable color, such as a green shade.
59. Select the second customer.
60. Choose a suitable color, such as a red shade because its transaction value is negative.

---

## Part H — Add data labels

61. Open:

> **Data labels**

62. Turn:

> **Data labels → On**

63. Expand the Data Labels settings.
64. Change:

> **Position → Outside end**

65. Change label color to:

> **Black**

66. Adjust font style and size as required.
67. Collapse the Visualizations pane when finished.

---

# 44. Final Visual Summary

The final chart is essentially:

```text
              Total Amount by Name

Customer A  █████████████████████  ₹XXXX
Customer B  █████████              -₹XXXX
```

The exact customers and amounts depend on the dataset.

The chart provides a quick way to identify the **highest-value customers**.

---

# 45. Key Concepts / Keywords

### **Top Customers**

Customers ranked according to a numerical metric such as transaction amount.

### **Top N**

A Power BI filtering technique used to display only the highest/lowest N categories according to a selected value.

### **By Value**

The numerical field used to determine the Top N ranking.

Here:

> **Sum of Amount**

### **Visual-Level Filter**

A filter applied only to a particular visual rather than the entire report.

### **Replace Values**

A Power Query transformation used to replace specific values, including null values.

### **Null**

Represents missing data.

### **Unknown**

A descriptive replacement for missing customer names.

### **Stacked Bar Chart**

A horizontal bar-based visual used to compare numerical values across categories.

### **Data Labels**

Display numerical values directly on the visual.

### **Outside End**

Places a data label at the outer end of the corresponding bar.

---

# 46. Important Interview/Exam Takeaways

### Q1. Does this KPI require a DAX measure?

**No.**

The existing Transaction Amount field can be aggregated directly.

### Q2. What visual was used?

> **Stacked Bar Chart**

### Q3. What goes on the X-axis?

> **Transaction Amount / Sum of Amount**

### Q4. What goes on the Y-axis?

> **Customer Name**

### Q5. How were missing customer names handled?

In Power Query:

> **Replace Values → Null → Unknown**

### Q6. Why was Unknown removed?

Because the KPI is intended to show **actual named customers**, and `Unknown` is not an identifiable customer.

### Q7. How were the top customers selected?

Using:

> **Top N filter**

### Q8. What Top N value was used?

> **Top 2**

### Q9. What was used under "By Value"?

> **Sum of Amount**

### Q10. What must you remember after configuring Top N?

Click:

> **Apply Filter**

### Q11. What was the final chart title?

> **Total Amount by Name**

### Q12. What happened to gridlines?

> **Turned Off**

### Q13. What happened to X-axis values and title?

> **Both turned Off**

### Q14. What happened to Y-axis title?

> **Turned Off**

The customer names themselves remained visible.

### Q15. Were data labels added?

> **Yes**

### Q16. Where were the data labels positioned?

> **Outside end**

### Q17. What color were the data labels?

> **Black**

---

# 47. Overall Learning From This Session

This session teaches several important Power BI skills at once:

**1. Creating a bar chart without a new DAX measure**

↓

**2. Handling missing values in Power Query**

↓

**3. Replacing nulls with a meaningful label**

↓

**4. Applying visual-level filters**

↓

**5. Using Top N filtering**

↓

**6. Ranking categories using a numerical measure**

↓

**7. Formatting individual bars separately**

↓

**8. Adding and positioning data labels**

The most important practical concept is the **Top N filter**:

> **Select the category field → choose Top N → specify N → select the numerical "By Value" field → Apply Filter.**

This allows Power BI to automatically identify and display the highest-performing categories instead of manually selecting them.
