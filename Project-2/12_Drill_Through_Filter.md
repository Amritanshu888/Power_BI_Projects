# Power BI Lecture Notes — Drill Through Filters

This lecture explains the **Drill Through Filters** functionality in Power BI. The objective is to create a second report page containing the detailed underlying data and allow the user to navigate to that page filtered according to a selected **Policy Type** from a visual on the first page.

---

# 1. What Is Drill Through?

**Drill through** allows you to navigate from one report page to another page while carrying a selected filter context with you.

In this lecture, the requirement is:

> Create a separate page containing all the detailed data used to build the report, and allow that page to be filtered according to the **Policy Type** selected on the first page.

For example:

**Page 1**

Premium Amount by Policy Type

→ Select **Auto**

→ Drill through to Page 2

→ Page 2 shows only **Auto** policies.

Similarly:

**Page 1**

→ Select **Travel**

→ Drill through to Page 2

→ Page 2 shows only **Travel** policies.

---

# 2. Business Requirement

The instructor wants to:

1. Create a **second page**.
2. Display the detailed data from the underlying table on this page.
3. Use **Policy Type** as the drill-through field.
4. Select a policy type from the existing **Premium Amount by Policy Type** bar chart on Page 1.
5. Drill through to Page 2.
6. Automatically filter Page 2 based on the selected policy type.

The underlying data is the same data that was used to create the report. 

---

# 3. Create the Second Report Page

The report currently has the original report page.

### Steps

1. Go to **Report View**.
2. Click the **+ (plus) icon** at the bottom of the report.
3. Power BI creates a new blank page.

This becomes **Page 2**.

The purpose of Page 2 is to display the detailed underlying data. 

---

# 4. Add a Table Visual to Page 2

Since the requirement is to display the detailed data, a **Table visual** is used.

### Steps

1. Make sure you are on **Page 2**.
2. Click on a blank area of the canvas.
3. Select the **Table** visual.
4. A blank table is created.
5. Resize the table as required.

The instructor then adds the relevant columns from the underlying dataset to this table. 

---

# 5. Add the Required Columns

The lecture adds multiple columns to the table.

The columns demonstrated include:

1. **Policy Number**
2. **Customer ID**
3. **Claim Number**
4. **Age**
5. **Gender**
6. **Coverage Amount**
7. **Premium Amount**
8. **Policy End Date**
9. **Policy Start Date**
10. **Policy Type**
11. **Claim Status**
12. **Claim Date**
13. **Claim Amount**
14. **Age Group**
15. **Active / Inactive**

The purpose is to provide a detailed representation of the underlying data rather than an aggregated summary.

---

# 6. Important: Don't Summarize Numerical Columns

When numerical fields are added to a Power BI table, Power BI may automatically summarize them.

For example, when **Age** is added, Power BI initially displays:

> **Sum of Age**

But that is not what is required.

The requirement is to show the actual value for every record.

### Therefore:

For numerical columns where individual values are required:

1. Click the dropdown next to the field.
2. Select:

### **Don't summarize**

---

## 6.1 Age

When Age is added:

**Age → Sum**

needs to be changed to:

**Age → Don't summarize**

This ensures that individual customer ages are displayed rather than the sum of ages. 

---

## 6.2 Coverage Amount

Similarly:

**Coverage Amount → Don't summarize**

The objective is to display the individual coverage amount for each row.

---

## 6.3 Premium Amount

Change:

**Premium Amount → Don't summarize**

Again, this prevents Power BI from aggregating the values.

---

## 6.4 Claim Amount

For **Claim Amount**:

**Claim Amount → Don't summarize**

This ensures the individual claim amount is displayed for each record.

---

# 7. Date Fields — Remove Date Hierarchy

Power BI may automatically add dates using a **Date Hierarchy**.

For example, a date field might appear as:

* Year
* Quarter
* Month
* Day

However, the requirement here is to display the **actual date**.

Therefore, the Date Hierarchy needs to be replaced with the actual date column.

---

# 8. Configure Policy End Date

For **Policy End Date**, Power BI initially shows the date hierarchy.

### Steps

1. Locate **Policy End Date** in the table's field configuration.
2. Click the dropdown.
3. Instead of the **Date Hierarchy**, select:
   **Policy End Date**

Now the actual date will be displayed instead of separate:

* Year
* Quarter
* Month
* Day



---

# 9. Configure Policy Start Date

Do the same thing for **Policy Start Date**.

### Change:

**Policy Start Date → Date Hierarchy**

to:

**Policy Start Date → Policy Start Date**

This displays the actual start date.

The instructor also rearranges the fields so that **Policy Start Date** and **Policy End Date** appear in the desired order. 

---

# 10. Add Policy Type

Add:

### **Policy Type**

to the table.

This field is particularly important because it will later be used for **Drill Through**.

The same Policy Type field will connect:

**Page 1 → Page 2**

---

# 11. Add Claim Status

Add:

### **Claim Status**

to the table.

This allows the detailed page to show the claim status associated with each record.

---

# 12. Configure Claim Date

The **Claim Date** is another date field.

Power BI may initially use the date hierarchy.

### Steps

1. Locate **Claim Date**.
2. Open its dropdown.
3. Change it from:
   **Date Hierarchy**
4. To:
   **Claim Date**

Now the table displays the actual claim date rather than Year/Quarter/Month/Day. 

---

# 13. Add Claim Amount

Add:

### **Claim Amount**

Then change its summarization to:

### **Don't summarize**

This is required because we want the individual claim amount for each record rather than an aggregated value.

---

# 14. Add the Additional Columns

The lecture then adds the additional columns that had been created earlier:

### Age Group

and

### Active / Inactive

These are added to the detailed table as well.

At this point, Page 2 contains the detailed information required for the drill-through page. 

---

# 15. Why "Don't Summarize" Is Important

The objective of Page 2 is fundamentally different from many of the summary visuals on Page 1.

### Page 1

Generally focuses on:

* Aggregations
* Counts
* Totals
* Comparisons
* Charts

### Page 2

Focuses on:

* Individual records
* Detailed data
* Actual values from the underlying table

Therefore, numerical fields should generally be configured as:

> **Don't summarize**

when the requirement is to display the record-level values.

---

# 16. Test Drill Through — Before Configuration

Now the instructor wants to test whether drill through is available.

On Page 1 there is already a bar chart:

### **Premium Amount by Policy Type**

This visual contains different policy-type categories.

The instructor right-clicks one of the bars.

However, there is **no Drill Through option** available.

### Why?

Because Power BI hasn't yet been told which field should be used as the drill-through field.

Therefore, additional configuration is required. 

---

# 17. Configure the Drill Through Field

Now go back to **Page 2**.

In the Data/Visual configuration area, there is a section labelled:

### **Add drill-through fields here**

This is where we tell Power BI which field should be passed from the source page to the drill-through page.

The required field is:

### **Policy Type**

---

# 18. Add Policy Type to Drill Through

### Steps

1. Go to **Page 2**.
2. Locate **Policy Type** in the Data pane.
3. Drag **Policy Type** into:
   **Add drill-through fields here**
4. Drop it there.

Now Page 2 has been configured as a drill-through destination based on **Policy Type**. 

---

# 19. Test Drill Through Again

Now return to **Page 1**.

The existing bar chart is:

### Premium Amount by Policy Type

### Steps

1. Go to Page 1.
2. Find the **Premium Amount by Policy Type** bar chart.
3. Right-click one of the policy-type bars.

This time, the context menu contains:

### **Drill through**

This means Power BI recognizes Page 2 as a valid drill-through destination.

---

# 20. Drill Through Using Auto

Suppose we right-click:

### **Auto**

in the Policy Type bar chart.

Then:

1. Right-click **Auto**.
2. Select **Drill through**.
3. Select **Page 2**.

Power BI navigates to Page 2.

But importantly, Page 2 is now filtered by:

### Policy Type = Auto

Therefore, the table shows only records where the policy type is **Auto**.

This demonstrates how drill-through carries the selected filter context from the source visual to the destination page. 

---

# 21. Back Button Automatically Added

When Power BI creates/configures a drill-through page, it provides a **back button** on the drill-through page.

The purpose of this button is to allow the user to return to the page from which they drilled through.

This becomes especially useful in larger reports where there may be many report pages.

---

# 22. How to Use the Back Button

The lecture specifies the interaction as:

1. Hover over the back-button area.
2. Hold **Ctrl**.
3. Click the back button.

Power BI takes you back to the page from which you performed the drill-through.

So:

**Page 1 → Drill Through → Page 2**

then:

**Ctrl + Click Back Button → Page 1**



---

# 23. Test Drill Through Using Travel

The instructor demonstrates the same process with another policy type.

### Steps

1. Return to Page 1.
2. Locate the **Premium Amount by Policy Type** bar chart.
3. Right-click the **Travel** bar.
4. Select **Drill through**.
5. Select **Page 2**.

Page 2 now displays only records where:

### **Policy Type = Travel**

This confirms that the drill-through functionality works for different policy types. 

---

# 24. Return to Page 1 Again

On Page 2:

1. Locate the automatically provided back button.
2. Hold **Ctrl**.
3. Click the back button.

You are returned to the original Page 1 from which the drill-through was initiated.

---

# 25. How Drill Through Works Conceptually

The functionality can be represented as:

### Page 1

**Premium Amount by Policy Type**

| Policy Type | Premium |
| ----------- | ------: |
| Auto        |     ... |
| Health      |     ... |
| Home        |     ... |
| Life        |     ... |
| Travel      |     ... |

↓

User right-clicks **Auto**

↓

**Drill through → Page 2**

↓

Page 2 receives:

**Policy Type = Auto**

↓

Detailed table shows:

**Only Auto policies**

---

For Travel:

### Page 1

Right-click **Travel**

↓

**Drill through → Page 2**

↓

Filter passed:

**Policy Type = Travel**

↓

Page 2:

**Only Travel policies**

---

# 26. Why Drill Through Is Useful

Drill-through is useful when a report contains:

### Summary Page

High-level information such as:

* Charts
* KPIs
* Aggregated values
* Comparisons

and you want users to investigate the underlying details without cluttering the main report page.

The user can:

1. Analyze the summary.
2. Identify something interesting.
3. Right-click the relevant category.
4. Drill through.
5. See the detailed records associated with that category.

This is exactly the approach demonstrated in the lecture.

---

# 27. Important Distinction: Filtering vs. Drill Through

### Normal filtering

A slicer or visual selection filters data within the report/page based on the interaction.

### Drill Through

Drill-through:

1. Takes the selected context from one visual.
2. Navigates to another report page.
3. Applies that context to the destination page.

So drill-through combines:

> **Navigation + Filtering**

---

# 28. Complete Step-by-Step Implementation

For exam/practical purposes, remember this exact sequence:

### Step 1

Create a new report page.

**Click + → New Page**

### Step 2

Add a **Table** visual.

### Step 3

Add the required underlying data fields.

### Step 4

For numerical fields that should show individual values:

**Dropdown → Don't summarize**

Apply this to fields such as:

* Age
* Coverage Amount
* Premium Amount
* Claim Amount

### Step 5

For date fields:

Change:

**Date Hierarchy → Actual Date**

for:

* Policy End Date
* Policy Start Date
* Claim Date

### Step 6

Add additional fields:

* Policy Type
* Claim Status
* Age Group
* Active / Inactive

### Step 7

On the drill-through page, find:

**Add drill-through fields here**

### Step 8

Drag:

**Policy Type → Add drill-through fields here**

### Step 9

Return to Page 1.

### Step 10

Right-click a Policy Type in:

**Premium Amount by Policy Type**

### Step 11

Select:

**Drill through → Page 2**

### Step 12

Verify that Page 2 displays only records corresponding to the selected Policy Type.

### Step 13

Use:

**Ctrl + Click → Back Button**

to return to Page 1.

---

# 29. Key Takeaways

### Drill Through

Allows users to navigate from a summary visual to a detailed page while passing the selected filter context.

### Drill-through field

The field that determines what filter context is passed to the destination page.

In this lecture:

> **Policy Type**

### Source visual

The existing:

> **Premium Amount by Policy Type** bar chart

### Destination

The newly created:

> **Page 2**

### Destination content

A detailed table containing the underlying data.

### Example

**Select Auto → Drill through → Page 2 → Only Auto records**

**Select Travel → Drill through → Page 2 → Only Travel records**

### Back navigation

Use the Power BI-provided back button, with:

> **Ctrl + Click**

to return to the source page.

---

# 30. Final Conceptual Flow

```text
PAGE 1
Premium Amount by Policy Type
            │
            │ Right-click a category
            ▼
       Drill Through
            │
            │ Policy Type filter is passed
            ▼
PAGE 2
Detailed Table
            │
            ▼
Only records matching
the selected Policy Type
            │
            │ Ctrl + Click Back
            ▼
PAGE 1
```

The main idea of the lecture is therefore:

> **Use Drill Through when you want a summary report page to provide a pathway to a detailed page filtered according to the user's selected category.**
