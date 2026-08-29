# Detailed Notes — Adding the Second Report Page & Validating Median by Credit Score

## 1. Objective of the Session

In this session, the focus is on:

1. Creating the **second report page**.
2. Naming the page **Applicant Demographics and Financial Profile**.
3. Reusing the existing page heading/style on the new page.
4. Creating a separate **Measures Table 2** for measures related to the second page.
5. Creating a DAX measure to calculate the **median loan amount**.
6. Creating a card visual to display and validate the median.
7. Manually validating the DAX-calculated median using **Power Query Editor**.
8. Understanding how to deal with large datasets while manually finding the median.
9. Preparing for the next step: creating **Credit Score bins** and a **line chart**.

---

# 2. Create the Second Report Page

### Step 1: Add a new page

At the bottom of the Power BI report:

1. Click the **`+` icon**.
2. A new report page will be created.
3. Double-click the **Page 1** control.
4. Press **Ctrl + A**.
5. Rename the page to:

**Applicant Demographics and Financial Profile**

You can split the name conceptually as:

* Applicant Demographics
* Financial Profile

This page will contain visuals related to applicant demographics and financial information.

---

# 3. Copy the Existing Page Heading/Shape

Instead of recreating the heading design from scratch, reuse the heading from the first page.

### Steps

1. Go back to **Page 1**.
2. Click the heading **shape** at the top of the page.
3. Press **Ctrl + C** to copy it.
4. Open the newly created second page.
5. Press **Ctrl + V** to paste it.

Now the same heading/style is available on Page 2.

---

## 4. Change the Heading Text

The copied shape still contains the heading from Page 1, so the text needs to be changed.

### Steps

1. Select the copied shape.
2. Open the **Format Shape** pane.
3. Go to the **Text** section.
4. Alternatively, double-click the page name at the bottom:

   * Double-click the Page 2 control.
   * Press **Ctrl + A**.
   * Press **Ctrl + C**.
5. Copy the page name:

**Applicant Demographics and Financial Profile**

6. Paste this text into the **Text** section of the Format Shape pane.
7. Press **Enter**.

The heading on the second page now matches the name of the page.

### Why copy the existing shape?

This allows the existing formatting, styling, positioning, and appearance to be reused rather than manually recreating the heading.

---

# 5. Requirement: Median by Credit Score

The next visual to be created will represent:

> **Median Loan Amount by Credit Score Bins**

The dataset already contains credit score values, but the requirement is to group those values into **Credit Score Bins**.

This will be similar to the **Age Group bins** created earlier.

### Important concept

The credit score values will eventually need to be grouped into ranges/bins.

For example, conceptually:

* Low credit score range
* Medium credit score range
* High credit score range

The exact bin logic will be created in the next session.

The instructor mentions that the **IF function** or **SWITCH function** can be used for creating these bins.

---

# 6. Why Calculate the Median First?

Before creating the Credit Score Bin column, the session focuses on calculating the median.

The median will be required for the visual that will eventually show:

**Median by Credit Score Bin**

Therefore, the first requirement is to create a DAX measure for the median.

---

# 7. Create a Separate Measures Table

Since the measures being created are related to the second report page, a separate measures table is created.

### Steps

1. Go to the **Home** tab.
2. Click **Enter Data**.
3. A table creation window will appear.
4. Name the table:

**Measures Table 2**

5. Click/press **Enter**.

The new table is now created.

---

# 8. Create a New Measure in Measures Table 2

After creating the table:

1. Collapse the **Loan Default** table if necessary.
2. Right-click **Measures Table 2**.
3. Select **New Measure**.

A DAX formula bar will appear.

---

# 9. Create the Median Measure

The measure is named:

**Median by Credit Score Bins**

Although the name refers to Credit Score Bins, the actual credit-score grouping will be handled later. At this stage, the measure calculates the overall median of the **Loan Amount** field.

### DAX logic

The instructor uses the `MEDIANX` function.

The structure is:

```DAX
Median by Credit Score Bins =
MEDIANX(
    'Loan Default',
    'Loan Default'[Amount]
)
```

### Steps while entering the formula

1. Type the measure name:

   `Median by Credit Score Bins`

2. Use **Shift + Enter** to move to the next line.

3. Type:

   `MEDIANX`

4. Press the **Tab** key when Power BI suggests the function.

5. Enter the table name:

   `'Loan Default'`

6. Add a comma.

7. Enter the field for which the median needs to be calculated:

   `[Amount]`

8. Close the bracket.

9. Press **Enter**.

The median measure is now created.

---

# 10. Remove the Unnecessary Column from Measures Table 2

When the `Measures Table 2` table was created using **Enter Data**, Power BI created an unnecessary `Column 1`.

Since this table is intended to act as a **measures table**, there is no need to retain that column.

### Steps

1. Select or locate **Measures Table 2**.
2. Click the **three dots (`...`)** beside it.
3. Select **Delete** for `Column 1` / remove the unnecessary column from the model.

The table can now be used simply for storing measures.

---

# 11. Validate the DAX Median

After creating a DAX calculation, it is good practice to verify that the result is correct.

The instructor therefore manually calculates/validates the median using the underlying data.

This is especially useful when working with real-world datasets because it helps ensure that:

* The DAX formula is correct.
* The correct column was used.
* The result is consistent with the underlying data.

---

# 12. Create a Card Visual to Display the Median

To see the median value calculated by DAX:

### Steps

1. Click on a **blank area of the report canvas**.
2. Select the **Card** visual.
3. A blank card will be created.
4. Keep the card selected.
5. Select the measure:

**Median by Credit Score Bins**

The card will display the median value.

---

# 13. Format the Card

The displayed value may initially use automatic display units.

To show the actual number without units:

### Steps

1. Select the card.
2. Open **Format your Visual**.
3. Go to **Callout value**.
4. Find **Display units**.
5. Change it to:

**None**

The card now displays:

**127,556**

This is the median calculated using DAX.

---

# 14. Manually Validate the Median in Power Query

The next objective is to verify whether **127,556** is actually the correct median.

To do this, the instructor uses **Power Query Editor**.

### Open Power Query Editor

1. Go to the **Home** tab.
2. Click **Transform Data**.
3. Power Query Editor opens.

---

# 15. Sort Loan Amount in Ascending Order

To manually find the median, the loan amounts need to be ordered.

### Steps

1. Locate the **Loan Amount / Amount** column.
2. Sort the column in **ascending order**.

The instructor chooses ascending order, although descending order would also work.

### Important

The data is already sorted after applying this operation, and the sorting operation appears in the **Applied Steps** section on the right.

---

# 16. Use Column Profiling

Power Query provides column statistics that can be used to understand the dataset.

### Steps

1. Go to the **View** tab.
2. Locate the **Column profile** option.
3. Uncheck it.
4. Check it again.

The purpose of doing this is to refresh/recalculate the column profiling information.

---

# 17. Change Column Profiling to the Entire Dataset

By default, Power BI's Power Query column profiling is based on only the **first 1,000 rows**.

That is not sufficient for this dataset because the dataset contains more than 255,000 records.

Therefore:

1. Locate the profiling option at the bottom of the Power Query window.
2. Click it.
3. Select:

**Column profiling based on entire dataset**

Power Query may take some time to process the entire dataset.

### Important practical point

When the dataset becomes large:

* Data profiling can take longer.
* Data cleaning can take longer.
* Power Query may need additional processing time.

The amount of time depends on the size and complexity of the dataset.

---

# 18. Determine the Number of Records

After Power Query finishes profiling the entire dataset, the **Count** statistic is displayed.

The count is:

**255,347**

This is an **odd number**.

For an odd number of observations, the median is the value at the middle position.

---

# 19. Find the Middle Observation

The instructor divides the total number of records by 2:

**255,347 ÷ 2 = 127,673.5**

Since the result falls between two positions, the middle observation is:

**127,674**

Therefore, we need to locate the record whose index is:

**127,674**

Because the data has already been sorted by loan amount, the loan amount at this middle position will give us the median.

---

# 20. Add an Index Column

To locate the middle observation easily, an index column is added.

### Steps

1. In Power Query, go to the option for adding an index column.
2. Click the small dropdown/icon.
3. Select:

**Add Index Column → From 1**

This creates an index beginning at 1:

|   Index |             Amount |
| ------: | -----------------: |
|       1 |      Lowest amount |
|       2 |        Next amount |
|       3 |        Next amount |
|     ... |                ... |
| 127,674 | Middle observation |
|     ... |                ... |

Because the data was sorted by Amount first, the index allows us to locate the required middle observation.

---

# 21. Why Not Use the Index Dropdown Directly?

The instructor tries to locate:

**127,674**

using the index column's dropdown search.

However, Power Query displays a message indicating:

> Limit of 1,000 values reached.

This happens because the dropdown list is not designed to display/search through all 255,347 individual values in this way.

Therefore, another method is required.

---

# 22. Use Number Filters

Instead of searching through the dropdown values, use a numeric filter.

### Steps

1. Click the dropdown on the **Index** column.
2. Select:

**Number Filters**

3. Select:

**Equals**

4. Enter:

**127674**

5. Apply the filter.

Power Query may again take some time to process the filter because the dataset is large.

---

# 23. Find the Median Value

After filtering to index **127,674**, only the relevant record is displayed.

Now scroll toward the left to find the **Amount / Loan Amount** column.

The value corresponding to index 127,674 is:

**127,556**

Therefore:

> **Median Loan Amount = 127,556**

This matches the value produced by the DAX `MEDIANX` calculation.

---

# 24. DAX vs. Manual Validation

At this point, both methods produce the same result:

### DAX calculation

**127,556**

### Manual calculation using Power Query

**127,556**

Therefore, the DAX measure has been successfully validated.

---

# 25. Do Not Apply the Power Query Changes

The operations performed in Power Query were only for **validation**.

The instructor does not want these transformations to become part of the final model.

This is important because operations such as:

* Sorting
* Adding the Index column
* Filtering to index 127,674

were performed only to manually verify the median.

### Steps to exit without applying changes

1. Go to the **Home** tab in Power Query.
2. Click the dropdown beside **Close & Apply**.
3. Select **Close** rather than applying the changes.

This closes Power Query and returns to the Power BI report view **without applying those temporary transformations**.

---

# 26. Final Validation Result

Back in the report view, the median displayed in the card remains:

**127,556**

This confirms that the manually calculated median and the DAX-calculated median are identical.

---

# 27. Why Manual Data Validation Is Important

The instructor emphasizes that manually checking calculations is useful when working with real-world data.

In actual projects, you may encounter situations where you need to:

* Drill down into the data.
* Analyze individual records.
* Search for particular values.
* Verify calculations.
* Investigate unexpected results.
* Validate DAX measures.
* Answer specific business questions.
* Reach conclusions based on underlying records.

Therefore, knowing how to inspect and manually validate the data is an important Power BI skill.

You should not always rely blindly on a calculated value simply because Power BI produced it.

---

# 28. Key Concepts Learned

### Second report page

A new report page was created and named:

**Applicant Demographics and Financial Profile**

### Reusing formatting

The heading shape from Page 1 was copied and pasted onto Page 2 to maintain consistent report design.

### Measures table

A separate table named:

**Measures Table 2**

was created to organize measures for the second report page.

### Median calculation

The `MEDIANX` DAX function was used to calculate the median of the Amount field.

### Card visual

The median measure was displayed using a Card visual.

### Median result

**127,556**

### Data validation

The median was independently validated using Power Query.

### Dataset size

**255,347 records**

### Middle observation

Since the number of records is odd:

**255,347 ÷ 2 = 127,673.5**

Therefore, the middle observation is:

**127,674**

### Validation result

The Amount corresponding to index **127,674** is:

**127,556**

Thus:

**DAX Median = Manual Median = 127,556**

---

# 29. Important Power Query Practical Points

### Default column profiling

Power Query initially profiles approximately the first **1,000 rows**.

### Entire dataset profiling

For accurate statistics on a large dataset, change the setting to:

**Column profiling based on entire dataset**

### Large datasets

When working with large volumes of data:

* Profiling can take longer.
* Data cleaning can take longer.
* Filtering can take longer.
* Adding an index can take longer.

Do not assume Power Query has frozen simply because processing takes some time.

---

# 30. Session Workflow at a Glance

```text
Create Page 2
      ↓
Name it "Applicant Demographics and Financial Profile"
      ↓
Copy Page 1 heading/shape
      ↓
Paste it on Page 2
      ↓
Change heading text
      ↓
Plan Median by Credit Score Bins visual
      ↓
Create Measures Table 2
      ↓
Create Median by Credit Score Bins measure
      ↓
Use MEDIANX on Loan Default[Amount]
      ↓
Create Card visual
      ↓
Display median
      ↓
Set Display Units = None
      ↓
Median = 127,556
      ↓
Open Power Query
      ↓
Sort Amount ascending
      ↓
Profile entire dataset
      ↓
Count = 255,347
      ↓
Find middle observation = 127,674
      ↓
Add Index Column from 1
      ↓
Filter Index = 127,674
      ↓
Amount = 127,556
      ↓
DAX result confirmed
      ↓
Close Power Query without applying changes
```

---

# 31. What Comes Next

The next session will cover two main tasks:

### 1. Create the Credit Score Bin column

Credit score values will be grouped into appropriate ranges.

The instructor will discuss using either:

* `IF`
* `SWITCH`

to implement the binning logic.

### 2. Create the Line Chart

After creating the Credit Score bins, a **line chart** will be created to represent:

**Median by Credit Score**

This will allow the report to show how the median loan amount varies across different credit score groups.
