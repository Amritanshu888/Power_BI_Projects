# Power BI — Creating Meaningful Slicers, Age Groups Using DAX & Duplicating Report Pages

## 1. Objective of the Video

In the previous video, multiple slicers were added to the report page. However, **all slicers were using the same field — `Bank Name Sent`**.

The objective of this video is to:

1. Create an additional **Age Groups** column using DAX.
2. Replace the repeated `Bank Name Sent` field in each slicer with a different, meaningful field.
3. Create different slicers for different customer/transaction attributes.
4. Duplicate the first report page to create a second page.
5. Prepare the report structure for adding different visuals on the two pages.

---

# 2. Understanding the Existing `Customer Age` Column

Before creating the new column, the existing `Customer Age` column is examined.

### Steps

1. Go to **Table View**.
2. Locate the **Customer Age** column.
3. Sort the column in **ascending order**.

   * The minimum customer age is **20 years**.
4. Sort the column in **descending order**.

   * The maximum customer age is **59 years**.

Therefore:

> `Customer Age` contains the individual age of each customer, ranging from **20 to 59 years** in this dataset.

However, instead of showing every individual age, the requirement is to **group customers into age categories**.

For example:

* Age ≤ 25 → **A1**
* Age 26–35 → **A2**
* Age > 35 → **A3**

To accomplish this, a new column called **Age Groups** will be created.

---

# 3. Creating a New Column Using DAX

Previously, columns were created using **Power Query Editor**.

In this video, a new column is created using **DAX** instead.

### Why create the column?

The new column will group customers according to their age and will later be used in one of the slicers.

---

## Steps to Create the `Age Groups` Column

### Step 1 — Go to Report View

1. Click on **Report View**.
2. Expand the **Data pane** if it is not already visible.
3. Locate the table named **UPI Transactions**.

The Data pane contains the different columns belonging to this dataset.

---

### Step 2 — Create a New Column

1. Right-click on the **UPI Transactions** table.
2. Select **New column**.
3. Power BI will open the DAX formula bar for creating the column.

---

### Step 3 — Name the Column

Name the new column:

**`Age Groups`**

---

# 4. Using Nested IF in DAX

A **nested IF** is used to categorize customers into three age groups.

The logic is:

| Condition               | Age Group |
| ----------------------- | --------- |
| Customer Age ≤ 25       | A1        |
| Customer Age ≤ 35       | A2        |
| All remaining customers | A3        |

The DAX logic used in the lecture is equivalent to:

```DAX
Age Groups =
IF(
    [Customer Age] <= 25,
    "A1",
    IF(
        [Customer Age] <= 35,
        "A2",
        "A3"
    )
)
```

### How the logic works

The first `IF` checks:

```DAX
Customer Age <= 25
```

If this is **TRUE**, the customer is assigned:

```text
A1
```

If it is **FALSE**, another `IF` is evaluated.

The second `IF` checks:

```DAX
Customer Age <= 35
```

If this is **TRUE**, the customer is assigned:

```text
A2
```

If this is also **FALSE**, the customer is assigned:

```text
A3
```

### Important point

Because the second condition is evaluated only when the first condition is false:

* `A1` = ages **20–25**
* `A2` = ages **26–35**
* `A3` = ages **36–59**

---

## Entering the Formula

The lecture demonstrates the following workflow:

1. Type `IF`.
2. Press **Tab** to autocomplete/select the IF function.
3. Specify the `Customer Age` column.
4. Enter the condition `<= 25`.
5. Enter `"A1"` as the result when the condition is true.
6. If false, move to the next line.
7. Enter another `IF`.
8. Check whether `Customer Age <= 35`.
9. Return `"A2"` if true.
10. Return `"A3"` if false.
11. Close the nested IF.
12. Close the outer IF.
13. Press **Enter**.

Power BI then creates the new calculated column.

---

# 5. Verifying the New `Age Groups` Column

After pressing Enter:

1. Look at the **Data pane**.
2. You will see a new column named **Age Groups** under the `UPI Transactions` table.
3. Go to **Table View** to inspect the data.
4. The new column appears as the last column.
5. It contains values such as:

   * `A1`
   * `A2`
   * `A3`

This demonstrates that **DAX can also be used to create calculated columns**, rather than relying only on Power Query.

---

# 6. Replacing the Repeated Fields in the Slicers

Now return to **Report View**.

The report currently contains multiple slicers, but they all contain:

**`Bank Name Sent`**

The requirement is to make each slicer represent a **different attribute**.

The general process for every slicer is:

1. Select the slicer.
2. Open/expand the **Visualizations** pane.
3. Locate the field currently present in the slicer's **Fields bucket**.
4. Remove `Bank Name Sent`.
5. Select the appropriate field from the Data pane.
6. The slicer will then represent the newly selected field.

---

# 7. Slicer 1 — Bank Name Sent

The **first slicer** remains unchanged.

It will continue to use:

**`Bank Name Sent`**

This slicer represents the different banks **from which the money was sent**.

So there is no need to modify the first slicer.

---

# 8. Slicer 2 — Bank Name Received

The second slicer should represent the bank where the transaction amount was received.

### Steps

1. Select the **second slicer**.
2. Expand the **Visualizations** pane.
3. Locate `Bank Name Sent` in the Fields bucket.
4. Remove `Bank Name Sent`.
5. In the Data pane, find **Bank Name Received**.
6. Select/check the `Bank Name Received` field.

The slicer now displays the different banks **in which the money/transaction was received**.

### Difference between the first two slicers

| Slicer   | Field              | Represents                     |
| -------- | ------------------ | ------------------------------ |
| Slicer 1 | Bank Name Sent     | Bank from which money was sent |
| Slicer 2 | Bank Name Received | Bank where money was received  |

---

# 9. Slicer 3 — City

The third slicer will represent the **city** from which transactions were made.

### Steps

1. Select the **third slicer**.
2. Remove `Bank Name Sent` from the Fields bucket.
3. Find the **City** column in the Data pane.
4. Select/check `City`.

The slicer now displays the different cities.

Users can therefore select a city to filter the report based on the city associated with the transactions.

---

# 10. Slicer 4 — Device Type

The fourth slicer will represent the **device type** used for transactions.

### Steps

1. Select the **fourth slicer**.
2. Remove `Bank Name Sent`.
3. Select **Device Type** from the Data pane.

The slicer now contains the different devices used to make the transactions.

---

# 11. Slicer 5 — Gender

The fifth slicer will represent **Gender**.

### Steps

1. Select the fifth slicer.
2. Remove `Bank Name Sent` from the Fields bucket.
3. Select **Gender** from the Data pane.

The slicer now allows users to filter the report based on gender.

---

# 12. Slicer 6 — Age Groups

This is where the newly created **Age Groups** column is used.

### Steps

1. Select the sixth slicer.
2. Remove `Bank Name Sent`.
3. Find the newly created **Age Groups** column.
4. Select/check `Age Groups`.

The slicer will now display the different age categories:

* **A1**
* **A2**
* **A3**

Therefore, the DAX-created calculated column is now being used to provide an age-based filtering option.

---

# 13. Slicer 7 — Merchant Name

The seventh slicer will represent the **merchant** associated with the transaction.

### Steps

1. Select the seventh slicer.
2. Remove `Bank Name Sent`.
3. Select **Merchant Name** from the Data pane.

Opening the slicer's dropdown will now show the different merchant names.

---

# 14. Slicer 8 — Payment Method

The eighth slicer will represent the **payment method** used.

### Steps

1. Select the eighth slicer.
2. Remove `Bank Name Sent` from the Fields bucket.
3. Select **Payment Method**.

The slicer now displays the different payment methods used for the transactions.

---

# 15. Slicer 9 — Purpose

The ninth slicer will represent the **purpose of the payment**.

### Steps

1. Select the ninth slicer.
2. Remove `Bank Name Sent`.
3. Select **Purpose** from the Data pane.

This allows the user to filter transactions according to the purpose for which the payments were made.

---

# 16. Slicer 10 — Transaction Type

The tenth slicer will represent the **type of transaction**.

### Steps

1. Select the tenth slicer.
2. Remove `Bank Name Sent`.
3. Select **Transaction Type**.

The slicer now represents the different types of transactions available in the dataset.

---

# 17. Final Slicer Structure

After making all the changes, the report contains different slicers for different attributes:

| Slicer | Field              |
| -----: | ------------------ |
|      1 | Bank Name Sent     |
|      2 | Bank Name Received |
|      3 | City               |
|      4 | Device Type        |
|      5 | Gender             |
|      6 | Age Groups         |
|      7 | Merchant Name      |
|      8 | Payment Method     |
|      9 | Purpose            |
|     10 | Transaction Type   |

### Key idea

Instead of having ten slicers all based on the same field, each slicer now provides a **different filtering dimension**.

This makes the report considerably more useful and interactive.

---

# 18. Creating a Two-Page Report

The report is intended to contain **two pages**.

The slicer section created so far for Page 1 should also be available on Page 2.

Rather than recreating and formatting all the slicers manually, the existing page can be duplicated.

---

# 19. Duplicating Page 1

### Steps

1. Locate **Page 1** at the bottom of the Power BI window.
2. Right-click on **Page 1**.
3. Select **Duplicate**.

Power BI creates a copy of Page 1.

The duplicate initially has a name similar to:

**Duplicate of Page 1**

---

# 20. Renaming the Duplicated Page

Rename the duplicate to **Page 2**.

### Steps

1. Double-click the duplicated page name.
2. Press **Ctrl + A** to select the existing name.
3. Type:

**Page 2**

4. Press **Enter**.

The report now has:

* **Page 1**
* **Page 2**

Both pages contain the same slicer structure created so far.

---

# 21. Report Page Structure Going Forward

At this point, both report pages contain the different slicers.

The next step will be to add different visuals to these pages.

### Page 1

Page 1 will contain:

* The existing slicers
* A **Line Chart**
* An option that allows the user to switch between:

  * **Line Chart**
  * **Clustered Column Chart**

The method for creating this chart-switching functionality will be discussed in a later session.

### Page 2

Page 2 will contain:

* The existing slicers
* A **Matrix visual**

Therefore, the two pages will eventually serve different visualization purposes.

---

# 22. Complete Process Covered in This Video

The overall workflow demonstrated is:

**Existing Customer Age column**

↓

**Create a calculated column using DAX**

↓

**Create `Age Groups` using nested IF**

↓

**Verify the new column**

↓

**Go to Report View**

↓

**Modify each slicer**

↓

**Remove repeated `Bank Name Sent` fields**

↓

**Assign appropriate fields to each slicer**

↓

**Create meaningful filtering options**

↓

**Duplicate Page 1**

↓

**Rename duplicate as Page 2**

↓

**Prepare the two pages for different visuals**

---

## 23. Important Concepts to Remember

### DAX can create calculated columns

A calculated column can be created directly from the data model using **DAX**, without using Power Query.

### Nested IF

A nested `IF` allows multiple conditions to be evaluated sequentially.

In this example:

```text
Age ≤ 25  → A1
Age ≤ 35  → A2
Otherwise → A3
```

### Slicers should represent different dimensions

Using the same field in every slicer is not useful. Instead, slicers should provide different filtering dimensions such as:

* Bank
* City
* Device
* Gender
* Age group
* Merchant
* Payment method
* Purpose
* Transaction type

### Duplicating a page saves time

When the same basic layout needs to be used on another report page, **Duplicate** can be used instead of manually rebuilding all the visuals and slicers.

### Report design being established

The report is being structured into two pages:

* **Page 1 → Line chart + chart-switching capability**
* **Page 2 → Matrix visual**

The slicer structure is shared between both pages.
