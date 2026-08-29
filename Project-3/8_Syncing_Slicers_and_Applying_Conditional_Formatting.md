# Detailed Notes: Syncing Slicers & Conditional Formatting in Power BI

## 1. Syncing Slicers

### What is the requirement?

When a report contains multiple pages, the user may want the **same slicers to work across all pages**.

For example, suppose:

* Page 1 has a **Bank Name Sent** slicer.
* Page 2 also has the same **Bank Name Sent** slicer.
* The user selects **ICICI Bank** on Page 2.

The requirement is that:

* **ICICI Bank should automatically be selected on Page 1 as well.**
* The user should **not have to select ICICI Bank again** on Page 1.
* Similarly, if the filter is applied on Page 1, it should automatically apply to Page 2.
* If the filter is cleared from one page, it should also be cleared from the other page.

This functionality is achieved using **Sync Slicers**.

### Why is Sync Slicers important?

This becomes particularly useful when a report contains many pages.

For a small two-page report, manually applying filters on each page may not be a big problem. However, a real-world Power BI report may contain **many pages**, and users don't want to repeatedly apply the same slicer selections on every page.

With synchronized slicers:

> A slicer selection made on one page is automatically reflected on the other synchronized pages.

---

# 2. Current Situation Before Syncing

Initially, suppose **ICICI Bank** is selected in the **Bank Name Sent** slicer on Page 2.

If you navigate to Page 1:

* The corresponding slicer on Page 1 does not have ICICI Bank selected.
* The filter applied on Page 2 does not automatically affect Page 1.

After synchronizing the slicers, this behavior changes.

---

# 3. How to Sync Slicers

Follow these steps:

### Step 1: Select the slicer

First, select the slicer that you want to synchronize.

For example:

> **Bank Name Sent**

### Step 2: Open the View tab

From the Power BI ribbon, click:

**View**

### Step 3: Open Sync Slicers

Under the **View** tab, locate:

> **Sync Slicers**

Click on it.

A Sync Slicers pane will appear.

### Step 4: Check the pages

Because the same slicer exists on both pages, you will see:

* **Page 1**
* **Page 2**

Initially, the corresponding checkboxes are not selected.

### Step 5: Synchronize the slicer

For the selected slicer, check:

* ☑ **Page 1**
* ☑ **Page 2**

This tells Power BI that the slicer should be synchronized between these two pages.

---

# 4. Sync All Required Slicers

The process needs to be repeated for **each slicer** that should work across the pages.

For example:

### Slicer 1

Select the first slicer and check:

* Page 1
* Page 2

### Slicer 2

Select the second slicer and check:

* Page 1
* Page 2

### Slicer 3

Select the third slicer and check:

* Page 1
* Page 2

### Slicer 4

Select the fourth slicer and check:

* Page 1
* Page 2

Continue this process for **all slicers that are available on both pages**.

> **Important:** Simply opening the Sync Slicers pane does not synchronize every slicer automatically. Each relevant slicer needs to be selected and configured.

---

# 5. Testing the Synchronized Slicers

After synchronizing the slicers, test whether the functionality is working.

### Step 1: Go to Page 2

Navigate to Page 2.

### Step 2: Select a value

In the **Bank Name Sent** slicer, select:

> **ICICI Bank**

The Page 2 report will now be filtered according to the selected bank.

### Step 3: Navigate to Page 1

Click on Page 1.

You should now see that:

> **ICICI Bank is already selected in the corresponding slicer on Page 1.**

There is no need to select ICICI Bank manually again.

The visuals on Page 1 will also respond to the filter.

For example, the transactions shown in the report will correspond to transactions sent from **ICICI Bank**, and the relevant transaction amounts will be displayed.

---

# 6. Clearing a Synchronized Slicer

Syncing works in both directions.

Suppose ICICI Bank is selected on both pages.

### Step 1: Go to Page 1

Clear the selection from the slicer on Page 1.

### Step 2: Go to Page 2

When you navigate to Page 2, you will see that:

> The ICICI Bank selection has also been cleared from Page 2.

This happens because the slicers are synchronized.

### Key behavior

| Action                   | Result                           |
| ------------------------ | -------------------------------- |
| Select a value on Page 1 | Same selection appears on Page 2 |
| Select a value on Page 2 | Same selection appears on Page 1 |
| Clear filter on Page 1   | Filter is cleared on Page 2      |
| Clear filter on Page 2   | Filter is cleared on Page 1      |

So, synchronized slicers maintain a **common filter state across the selected report pages**.

---

# 7. Key Takeaway: Sync Slicers

**Sync Slicers** is an important Power BI functionality when the same slicer needs to control visuals across multiple report pages.

### Basic process

**Select slicer → View → Sync Slicers → Check Page 1 + Page 2**

Repeat this process for every slicer that needs to be synchronized.

### Practical use case

If a report has:

* Page 1 — Overview
* Page 2 — Transactions
* Page 3 — Analysis
* Page 4 — Summary

and the user wants the **Bank Name** filter to remain consistent throughout the report, the Bank Name slicer can be synchronized across all relevant pages.

---

# 8. Conditional Formatting in a Matrix Visual

The next concept covered is **Conditional Formatting**.

The requirement is to visually represent different transaction amounts using different background colors.

For example:

* **Higher amounts → darker background**
* **Lower amounts → lighter background**

This makes it easier for users to identify high and low values at a glance.

---

# 9. Matrix Visual Used for Conditional Formatting

The matrix visual contains two numerical columns:

1. **Amount**
2. **Remaining Balance**

We want to apply background-color conditional formatting to both columns.

---

# 10. Applying Conditional Formatting to the Amount Column

### Step 1: Select the Matrix visual

Click on the **Matrix visual** that was created previously.

### Step 2: Open the formatting options

Open:

> **Format a visual**

### Step 3: Find Cell Elements

Within the formatting options, locate:

> **Cell Elements**

This section allows formatting to be applied to individual cells in the matrix.

### Step 4: Select the Amount series

Since the matrix contains multiple numerical columns, first work with:

> **Amount**

### Step 5: Turn Background Color On

Enable:

> **Background color**

This activates background-color formatting for the Amount column.

Power BI will automatically use the values to create a color gradient.

As a result:

* Higher amounts receive comparatively darker colors.
* Lower amounts receive comparatively lighter colors.

---

# 11. Customize the Conditional Formatting Colors

The default colors can be changed.

### Step 1: Click FX

Next to the background-color setting, click:

> **FX**

This opens the conditional-formatting configuration.

### Step 2: Set the lowest value color

For the **lowest value**, select:

> **White**

### Step 3: Set the highest value color

For the **maximum/highest value**, select:

> **Purple**

### Step 4: Apply

Click:

> **OK**

The Amount column will now use a white-to-purple color scale.

Conceptually:

**Lower Amount → White / Light**

⬇️

**Higher Amount → Darker Purple**

---

# 12. Apply Conditional Formatting to Remaining Balance

The same process needs to be repeated for the **Remaining Balance** column.

### Step 1: Select Remaining Balance

In the **Series** selection, choose:

> **Remaining Balance**

### Step 2: Turn on Background Color

Enable:

> **Background color**

### Step 3: Click FX

Click the **FX** button to configure the conditional formatting.

### Step 4: Configure the minimum value

Set the lowest value to:

> **White**

### Step 5: Configure the maximum value

Set the highest value to:

> **Purple**

### Step 6: Click OK

Click:

> **OK**

The Remaining Balance column now also has conditional background formatting.

---

# 13. Result of Conditional Formatting

After applying the formatting:

* Cells with **no/very low transaction values** appear white or very light.
* Cells with **higher transaction values** appear progressively darker.
* The highest values are represented using the darkest shade in the selected color range.

This creates a visual **heatmap-like effect** inside the matrix.

Instead of reading every number individually, users can quickly identify areas with higher transaction amounts simply by looking at the background colors.

---

# 14. Overall Workflow Covered in the Lecture

The session covered two important Power BI functionalities:

## A. Syncing Slicers

Used when the same slicer/filter needs to work across multiple report pages.

**Workflow:**

1. Select slicer.
2. Go to **View**.
3. Open **Sync Slicers**.
4. Select/check the required pages.
5. Repeat for all relevant slicers.
6. Test by applying a filter.
7. Navigate between pages to verify that the filter remains synchronized.
8. Clear the filter on one page and verify that it is cleared on the other pages.

## B. Conditional Formatting

Used to visually distinguish numerical values using colors.

**Workflow:**

1. Select the Matrix visual.
2. Open **Format a visual**.
3. Go to **Cell Elements**.
4. Select the required numerical series.
5. Turn **Background color** on.
6. Click **FX**.
7. Set the lowest value color to **White**.
8. Set the highest value color to **Purple**.
9. Click **OK**.
10. Repeat for the other numerical column.

---

# 15. Important Points to Remember

### Sync Slicers

* Sync Slicers allows a slicer selection to be shared across multiple report pages.
* The same filter does not need to be manually selected on every page.
* Changes made on one synchronized page are reflected on the other synchronized pages.
* Clearing a filter also propagates to the synchronized pages.
* Each slicer must be configured individually.
* This is particularly useful for reports containing many pages.

### Conditional Formatting

* Conditional formatting makes numerical data easier to interpret visually.
* In a matrix, it can be applied through **Cell Elements**.
* Background color can be configured using the **FX** option.
* A color scale can be used to distinguish lower and higher values.
* In this example:

  * **Lowest value → White**
  * **Highest value → Purple**
* The technique was applied to both:

  * **Amount**
  * **Remaining Balance**

### Final takeaway

> **Sync Slicers** keeps filtering consistent across report pages, while **Conditional Formatting** makes important patterns in numerical data easier to identify visually.
