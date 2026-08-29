# Power BI Filters — Detailed Lecture Notes

This lecture explains the **different types of filters available in Power BI Desktop**, how to apply them using the **Filters pane**, and—most importantly—the scope of each filter.

The three filter types covered are:

1. **Visual-level filter**
2. **Page-level filter**
3. **Report-level filter / Filters on all pages**

---

# 1. Why Filters Are Used in Power BI

Filters are used when you don't want a visual or report to display **all available data**.

For example, suppose a bar chart shows:

> Net Sales for different Customer IDs.

Instead of displaying all customers, you may want to display only:

* Customer 1
* Customer 10
* Customer 11
* Customer 12

You can accomplish this using the **Filters pane**.

The important thing is that the same filter can have different scopes:

```text
Specific Visual
      ↓
Visual-level Filter

Entire Page
      ↓
Page-level Filter

Entire Report
      ↓
Report-level Filter
```

---

# 2. Creating the Initial Visual

The lecture first creates a bar chart that will be used to demonstrate the different filter types.

## Step 1 — Select a Blank Area

Click on a blank area of the Power BI report canvas.

This ensures that you are creating a new visual rather than modifying an existing visual.

---

## Step 2 — Select a Stacked Bar Chart

From the Visualizations pane:

**Select → Stacked Bar Chart**

A blank bar chart is created.

The instructor then:

* Moves the visual to an appropriate position.
* Resizes it as required.

---

# 3. Adding Net Sales to the Visual

The objective is to show **Net Sales for different Customer IDs**.

The `Net Sales` field is available under the **Fact Table**.

### Steps

1. Locate the **Net Sales** column in the Data pane.
2. Double-click the `Net Sales` field.
3. Alternatively, drag and drop it into the appropriate axis bucket.

In the lecture, it is placed in the **X-axis bucket**.

Therefore:

```text
X-axis → Net Sales
```

---

# 4. Adding Customer ID to the Visual

Next, the instructor adds `Customer ID`.

### Steps

1. Locate `Customer ID` in the Data pane.
2. Double-click the field.
3. Drag and drop it into the **Y-axis bucket**.

Therefore:

```text
Y-axis → Customer ID
X-axis → Net Sales
```

The resulting chart represents:

> **Net Sales for different Customer IDs**

Customer IDs appear along the vertical/Y axis, while Net Sales is represented along the horizontal/X axis.

---

# 5. Turning Data Labels On

The instructor then enables **Data Labels** so that the values are visible directly on the chart.

### Steps

1. Select the bar chart.
2. Open **Format your visual**.
3. Locate **Data labels**.
4. Turn **Data labels → On**.

Now the values are displayed directly on the bars.

---

# 6. Creating Multiple Pages for Demonstration

To demonstrate the difference between the filter scopes, the same visual is copied onto three different pages.

The report eventually has:

```text
Page 1
Page 2
Page 3
```

and the same bar chart is available on each page.

---

## Step-by-Step

### Copy the Visual

Select the visual and press:

```text
Ctrl + C
```

### Create a New Page

Click the:

**+ icon**

This creates **Page 2**.

### Paste the Visual

Click on a blank area of Page 2 and press:

```text
Ctrl + V
```

The same visual is pasted.

---

### Create Page 3

Click the **+ icon** again.

A third page is created.

Paste the visual again:

```text
Ctrl + V
```

Now the same visual exists on:

```text
Page 1
Page 2
Page 3
```

This setup is necessary for demonstrating how the different filter scopes behave.

---

# 7. Creating a Second Visual on Page 1

The instructor also creates another copy of the visual on Page 1.

### Steps

1. Select the existing visual.
2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

4. Move the copied visual to an appropriate location.
5. Resize it if required.

Now Page 1 contains two similar bar charts.

---

# 8. Changing the Color of the Second Visual

The second visual is given a different color so that it is easy to distinguish between the two charts.

### Steps

1. Select the second bar chart.
2. Open the **Visualizations** pane.
3. Select **Format your visual**.
4. Locate the bar formatting/color option.
5. Change the bar color to **purple**.

Now we have:

* **Blue bar chart**
* **Purple bar chart**

These two visuals are used to demonstrate the difference between visual-level and page-level filtering.

---

# 9. Filters Pane

When a visual is selected, the **Filters pane** contains three important sections:

### 1. Filters on this visual

Controls filtering for the selected visual only.

### 2. Filters on this page

Controls filtering for all visuals on the current page.

### 3. Filters on all pages

Controls filtering across the entire report.

Conceptually:

```text
Filters Pane
│
├── Filters on this visual
│
├── Filters on this page
│
└── Filters on all pages
```

These correspond to three different filter scopes.

---

# 10. Visual-Level Filter

## Definition

A **visual-level filter** is a filter applied to **one specific visual**.

It does not affect:

* Other visuals on the same page.
* Visuals on other pages.

Only the selected visual is affected.

---

# 11. Applying a Visual-Level Filter

The instructor applies a visual-level filter to the **blue bar chart**.

### Step 1

Select the blue bar chart.

### Step 2

Go to the **Filters pane**.

Locate:

**Filters on this visual**

### Step 3

Open the dropdown under:

**Filters on this visual**

### Step 4

Add/select the `Customer ID` field.

### Step 5

Select specific Customer IDs.

The lecture selects:

* Customer ID 1
* Customer ID 10
* Customer ID 11
* Customer ID 12

So the filter effectively becomes:

```text
Customer ID ∈ {1, 10, 11, 12}
```

---

# 12. Result of the Visual-Level Filter

Only the **blue bar chart** is filtered.

The blue chart now displays Net Sales only for:

```text
1
10
11
12
```

The purple chart remains unchanged.

It continues to show Net Sales for **all customers**.

This demonstrates the key property of a visual-level filter:

```text
Visual-level filter
        ↓
Selected visual only
```

---

# 13. Visual-Level Filter Does Not Affect Other Pages

The lecture then checks Page 2 and Page 3.

Even though the same blue bar chart exists on those pages, they are **not affected**.

Why?

Because the filter was applied specifically to the blue visual on **Page 1**.

Therefore:

```text
Page 1
Blue visual → Filtered

Page 2
Blue visual → Not filtered

Page 3
Blue visual → Not filtered
```

This is an important distinction.

The filter is associated with that **specific visual instance**, not every copy of the visual throughout the report.

---

# 14. Page-Level Filter

The next type is:

# Filters on this page

This is called a **page-level filter**.

## Definition

A page-level filter affects **all visuals present on the selected/current page**.

However, it does **not** affect visuals on other pages.

Conceptually:

```text
Page 1
│
├── Visual 1 ← Filtered
├── Visual 2 ← Filtered
└── Visual 3 ← Filtered

Page 2
└── Not affected

Page 3
└── Not affected
```

---

# 15. Applying a Page-Level Filter

The instructor first removes/clears the previous visual-level filter.

Then the page-level filter is demonstrated.

### Step 1

Go to:

**Filters on this page**

### Step 2

Locate `Customer ID` in the Data pane.

### Step 3

Drag `Customer ID` into:

**Filters on this page**

### Step 4

Select the required Customer IDs.

The lecture selects:

* 1
* 10
* 11
* 12

---

# 16. Result of a Page-Level Filter

Because the filter is applied at the page level, **all visuals on that page are affected**.

For example, Page 1 contains:

* Blue bar chart
* Purple bar chart

Both charts are now filtered.

```text
Page 1
│
├── Blue Chart   → Filtered
│
└── Purple Chart → Filtered
```

Both visuals display data only for the selected Customer IDs.

---

# 17. What About Other Pages?

Now open:

* Page 2
* Page 3

The visuals on these pages remain unaffected.

Therefore:

```text
Page 1 → Filtered
Page 2 → Not filtered
Page 3 → Not filtered
```

This is why it is called a **page-level filter**.

Its scope is limited to the particular page where the filter is applied.

---

# 18. Report-Level Filter

The third type is:

# Filters on all pages

This is also referred to in the lecture as a:

**Report-level filter**

## Definition

A report-level filter affects **all relevant visuals across all pages of the report**.

Conceptually:

```text
Report
│
├── Page 1
│    ├── Visual 1 → Filtered
│    └── Visual 2 → Filtered
│
├── Page 2
│    └── Visual 3 → Filtered
│
└── Page 3
     └── Visual 4 → Filtered
```

---

# 19. Applying a Report-Level Filter

The instructor first removes the page-level filter.

Then the filter is added under:

**Filters on all pages**

### Step 1

Locate `Customer ID` in the Data pane.

### Step 2

Drag `Customer ID` into:

**Filters on all pages**

### Step 3

Select the desired Customer IDs.

The lecture selects:

* Customer ID 1
* Customer ID 10
* Customer ID 11
* Customer ID 12
* Customer ID 13

Therefore:

```text
Customer ID ∈ {1, 10, 11, 12, 13}
```

---

# 20. Result of Report-Level Filter

Now the filter applies across the entire report.

### Page 1

All available charts are filtered.

### Page 2

All available charts are filtered.

### Page 3

All available charts are filtered.

So:

```text
Page 1 → Filtered
Page 2 → Filtered
Page 3 → Filtered
```

This is why it is called a **report-level filter** or **filter on all pages**.

---

# 21. Comparison of the Three Filter Types

| Filter Type      | Scope               | Affects Other Visuals on Same Page? | Affects Other Pages? |
| ---------------- | ------------------- | ----------------------------------- | -------------------- |
| **Visual-level** | One visual          | ❌ No                                | ❌ No                 |
| **Page-level**   | Entire current page | ✅ Yes                               | ❌ No                 |
| **Report-level** | Entire report       | ✅ Yes                               | ✅ Yes                |

This table is one of the most important things to remember from the lecture.

---

# 22. Easy Way to Remember

Think about the **scope** of the filter:

```text
VISUAL
  ↓
One visual only

PAGE
  ↓
Everything on one page

REPORT
  ↓
Everything across the report
```

Or:

```text
Visual Level → Smallest scope
Page Level   → Medium scope
Report Level → Largest scope
```

---

# 23. Practical Example

Suppose your report has:

```text
Page 1:
    Sales Chart
    Profit Chart
    Customer Chart

Page 2:
    Product Chart
    Region Chart

Page 3:
    Monthly Sales Chart
```

### If you apply a Visual-Level Filter

Only the selected chart changes.

```text
Sales Chart → Filtered
Everything else → Unchanged
```

### If you apply a Page-Level Filter

Every visual on the current page changes.

```text
Page 1:
Sales Chart    → Filtered
Profit Chart   → Filtered
Customer Chart → Filtered

Page 2 → Unchanged
Page 3 → Unchanged
```

### If you apply a Report-Level Filter

Everything across the report changes.

```text
Page 1 → Filtered
Page 2 → Filtered
Page 3 → Filtered
```

---

# 24. Important Practical Steps From the Lecture

### Creating the demonstration chart

```text
1. Click blank canvas
2. Select Stacked Bar Chart
3. Add Net Sales to X-axis
4. Add Customer ID to Y-axis
5. Format visual
6. Turn Data Labels ON
```

### Creating additional pages

```text
1. Select visual
2. Ctrl + C
3. Click + to create new page
4. Ctrl + V
5. Repeat for another page
```

### Creating a second visual

```text
1. Select visual
2. Ctrl + C
3. Ctrl + V
4. Move copied visual
5. Format it
6. Change bar color to purple
```

### Visual-level filter

```text
1. Select specific visual
2. Filters pane
3. Filters on this visual
4. Add Customer ID
5. Select required IDs
```

### Page-level filter

```text
1. Clear visual-level filter
2. Filters on this page
3. Add Customer ID
4. Select required IDs
```

### Report-level filter

```text
1. Remove page-level filter
2. Filters on all pages
3. Add Customer ID
4. Select required IDs
```

---

# 25. Key Takeaways

### Visual-Level Filter

> Filters **only one specific visual**.

Example:

```text
Blue Chart → Filtered
Purple Chart → Not filtered
```

---

### Page-Level Filter

> Filters **all visuals on one page**.

Example:

```text
Page 1 → All visuals filtered
Page 2 → Not affected
Page 3 → Not affected
```

---

### Report-Level Filter

> Filters **all visuals across all pages of the report**.

Example:

```text
Page 1 → Filtered
Page 2 → Filtered
Page 3 → Filtered
```

---

# 26. Final Mental Model

The complete concept can be remembered as:

```text
                 FILTERS
                    │
        ┌───────────┼───────────┐
        │           │           │
        ↓           ↓           ↓
     VISUAL        PAGE       REPORT
       │            │            │
       ↓            ↓            ↓
 One visual    One page     All pages
```

### Scope increases from left to right:

**Visual → Page → Report**

The lecture concludes by noting that these filtering concepts—especially **visual-level filters**—will be used in the upcoming report-building exercises when different business requirements are implemented.
