# Power BI — Report Page 2: Market Value and Color/Clarity Trends

## 1. Objective of the Session

The first report page has already been created.

Now the objective is to create the **second report page** based on the recommendations provided in the PDF generated using Perplexity.

The recommended name for the second page is:

> **Market Value and Color / Clarity Trends**

The first visual recommended for this page is a **Card visual** representing:

> **Average Price**

The session therefore focuses on:

1. Creating the second report page.
2. Creating an **Average Price** DAX measure.
3. Reusing an already formatted Card visual.
4. Replacing its existing measure with Average Price.
5. Adding a **page-level filter** using the `depth` column.
6. Using basic filtering to analyze Average Price for selected depth values.

---

# 2. Refer to the PDF

The instructor first goes back to the PDF created using **Perplexity**.

The PDF contains recommendations for the report pages and their visuals.

For the second page, the recommended page name is:

### Market Value and Color / Clarity Trends

This name is copied from the PDF.

---

# 3. Create the Second Report Page

## Step 1 — Go to Power BI Desktop

Open the Power BI report.

At the bottom of the Power BI canvas, the existing first report page is visible.

---

## Step 2 — Add a New Page

Click the:

**`+` icon**

This creates a new report page.

---

# 4. Rename the New Page

The newly created page needs to be renamed.

The instructor uses the page-name editing functionality and pastes the name copied from the PDF.

The page is renamed to:

> **Market Value and Color / Clarity Trends**

The instructor uses:

```text id="f3x9k7"
Ctrl + A
Ctrl + V
Enter
```

The process is:

```text
Copy page name from PDF
        ↓
Create new page (+)
        ↓
Select page name
        ↓
Ctrl + A
        ↓
Ctrl + V
        ↓
Enter
```

Now the second report page is ready.

---

# 5. First Visual on Page 2 — Average Price

According to the PDF, the first visual recommended for this page is a:

> **Card visual**

The purpose of this Card is to display:

### Average Price

This will give the report user a quick KPI representing the average price of the diamonds.

---

# 6. Create the Average Price DAX Measure

A new measure is required because the Card needs to calculate the average of the `price` column.

## Step 1 — Go to the Data Pane

Expand the:

**Data pane**

---

## Step 2 — Select the Measures Table

Locate:

**Measures Table**

Right-click on it.

Select:

> **New Measure**

This opens the DAX formula bar.

---

# 7. Enter the Average Price DAX Expression

The DAX expression recommended by the PDF calculates the average of the `price` column from the Diamonds table.

Conceptually, the expression is:

```DAX
AVERAGE(diamonds[price])
```

The measure should be named:

```DAX
Average Price = AVERAGE(diamonds[price])
```

The instructor enters the expression on the right-hand side and gives the measure the name:

> **Average Price**

Then press:

**Enter**

The measure is now created.

---

# 8. Why Use a Measure?

The measure allows Power BI to dynamically calculate the average price according to the current filter context.

This becomes particularly useful later in the lecture when a **depth filter** is added.

For example:

```text
All diamonds
      ↓
Average Price
```

But if the report is filtered to a particular depth:

```text
Diamonds with selected depth
      ↓
Average Price for selected depth
```

Thus, the same measure can dynamically respond to filters.

---

# 9. Reuse the Existing Card Visual

The instructor does not create a new Card from scratch.

Instead, an existing Card visual from the first report page is reused.

This is because the first page already contains properly formatted Card visuals.

### Advantage

By copying an existing Card:

* Formatting is preserved.
* Design remains consistent.
* No need to repeat formatting.
* Time is saved.

---

# 10. Go Back to the First Report Page

Click on:

> **Page 1**

The instructor uses the first page because it already contains a formatted Card visual.

The selected Card represents:

> **Average Carat**

---

# 11. Copy the Existing Card

Select the existing Card visual.

Use:

```text id="t8o6yx"
Ctrl + C
```

This copies the Card along with its formatting.

---

# 12. Go to the Second Page

Return to:

> **Market Value and Color / Clarity Trends**

page.

Paste the copied Card using:

```text id="m6xq9e"
Ctrl + V
```

The Card now appears on the second page.

Because it was copied from the first page, it retains the same formatting.

---

# 13. Replace the Existing Measure

The copied Card is still configured to display:

> **Average Carat**

But the requirement for Page 2 is:

> **Average Price**

Therefore, the existing measure needs to be replaced.

---

## Step 1 — Expand the Visualizations Pane

Open/expand the:

**Visualizations pane**

---

## Step 2 — Remove Average Carat

Look at the Card's field bucket.

It currently contains:

> **Average Carat**

Remove this field from the bucket.

---

## Step 3 — Add Average Price

Locate the newly created:

> **Average Price**

measure in the Data pane.

Select/check the box next to it.

This adds **Average Price** to the Card.

The Card now displays:

> **Average Price**

---

# 14. Resulting Card

The Card has now been converted from:

```text
Average Carat
```

to:

```text
Average Price
```

The formatting remains the same because the visual was copied from the already-formatted Card on Page 1.

So there is no need to redo the formatting.

---

# 15. Add a Page-Level Filter

The lecture then demonstrates another useful Power BI feature:

> **Page-level filtering**

The instructor wants to analyze the Average Price according to different values of:

> **Depth**

For example, the user may want to know:

> What is the average diamond price for a particular depth?

Instead of creating another visual, a filter can be added to the entire report page.

---

# 16. Open the Filters Pane

Expand the:

**Filters pane**

Power BI provides different levels at which filters can be applied.

The relevant option here is:

> **Filters on this page**

This means the filter will affect visuals on the current report page.

---

# 17. Add Depth as a Page-Level Filter

Locate the:

> **Depth**

column in the Data pane.

The instructor then drags the `depth` field into:

> **Filters on this page**

The structure becomes:

```text
Filters pane
     ↓
Filters on this page
     ↓
Depth
```

Now the depth field acts as a page-level filter.

---

# 18. Change the Filter Type

Power BI initially provides an **Advanced filtering** option.

The instructor changes this to:

> **Basic filtering**

### Steps

1. Open the filtering options for `Depth`.
2. Change the filter type from:
   **Advanced filtering**
3. Select:
   **Basic filtering**

Basic filtering is useful here because it allows the user to simply select specific depth values.

---

# 19. Select Depth Values

After changing to Basic filtering, the available depth values are displayed.

You can select particular values.

For example, conceptually:

```text
☐ 55
☐ 60
☐ 61
☐ 62
☐ 63
...
```

The actual available values depend on the dataset.

When a particular depth value is selected, the Average Price Card responds to the filter.

---

# 20. Multiple Selection

The instructor points out that you can select:

> **Multiple values**

For example:

```text
Depth = 60
Depth = 61
Depth = 62
```

The Average Price calculation will then be based on the records satisfying the selected filter criteria.

This allows comparison/analysis across multiple depth values.

---

# 21. Single Selection

You can also choose:

> **A single value**

For example:

```text
Depth = 61
```

The Card will then show the average price for the filtered data corresponding to that selection.

---

# 22. Understanding Page-Level Filtering

This is an important Power BI concept.

A filter under:

> **Filters on this page**

affects the visuals on the **current report page**.

Conceptually:

```text
Depth Filter
     ↓
Current Report Page
     ↓
Visuals on that page
     ↓
Updated results
```

So when the user changes the Depth selection, the Average Price Card can dynamically change.

---

# 23. Why This Is Useful

Suppose the overall average price is:

```text
Average Price = X
```

You can then filter by a particular depth and ask:

> What is the average price for diamonds with this depth?

The Card updates accordingly.

This transforms a static KPI into an **interactive analytical KPI**.

---

# 24. Complete Workflow

The entire process can be remembered as:

```text
Open PDF
      ↓
Find Page 2 recommendation
      ↓
Copy page name
      ↓
Power BI Desktop
      ↓
Click + to create new page
      ↓
Rename page
      ↓
Market Value and Color / Clarity Trends
      ↓
Read first visual recommendation
      ↓
Average Price Card
      ↓
Expand Data pane
      ↓
Right-click Measures Table
      ↓
New Measure
      ↓
AVERAGE(diamonds[price])
      ↓
Name → Average Price
      ↓
Enter
      ↓
Go to Page 1
      ↓
Copy existing formatted Card
      ↓
Ctrl + C
      ↓
Go to Page 2
      ↓
Ctrl + V
      ↓
Open Visualizations pane
      ↓
Remove Average Carat
      ↓
Add Average Price
      ↓
Card now shows Average Price
      ↓
Open Filters pane
      ↓
Depth → Filters on this page
      ↓
Change Advanced filtering
      ↓
Basic filtering
      ↓
Select depth value(s)
      ↓
Average Price updates dynamically
```

---

# 25. Important Concepts from This Lecture

## A. Reusing Visuals

Instead of repeatedly creating and formatting Cards:

**Copy an existing formatted Card → replace the measure.**

This is a very efficient dashboard-building technique.

---

## B. Measures Can Respond to Filters

The measure:

```DAX
Average Price = AVERAGE(diamonds[price])
```

is dynamic.

When a filter is applied, Power BI recalculates the measure based on the filtered data.

Therefore:

```text
No filter
→ Average price across all relevant data

Depth filter
→ Average price for selected depth

Multiple depth values
→ Average price for the selected set of depths
```

---

## C. Basic vs Advanced Filtering

### Basic Filtering

Useful when you want to select specific values from a list.

Example:

```text
Depth = 60
Depth = 61
Depth = 62
```

### Advanced Filtering

Useful when you want to define conditions such as:

* Greater than
* Less than
* Between
* Contains
* Begins with
* etc., depending on the field type.

The lecture uses **Basic filtering** because the requirement is simply to select depth values.

---

## D. Page-Level Filter

A filter added under:

> **Filters on this page**

is intended to affect the visuals on that report page.

This is different from a visual-level filter, which affects only a particular visual.

---

# 26. Final Page 2 Status

At the end of this session, Page 2 contains:

### Page Name

**Market Value and Color / Clarity Trends**

### First Visual

**Average Price Card**

### DAX Measure

```DAX
Average Price = AVERAGE(diamonds[price])
```

### Filter

**Depth**

### Filter Location

**Filters on this page**

### Filter Type

**Basic filtering**

### Selection

Can be:

* Single depth value
* Multiple depth values

### Card Behavior

The **Average Price** displayed by the Card dynamically responds to the selected depth filter.

---

# Quick Revision

**Page 2 → Create page → Rename → Create Average Price measure → Copy formatted Card from Page 1 → Replace Average Carat with Average Price → Add Depth as page-level filter → Change to Basic filtering → Select one or multiple depth values.**

The key idea of this session is **reusability + interactivity**: reuse an existing formatted visual, then make the KPI dynamically respond to a page-level filter.
