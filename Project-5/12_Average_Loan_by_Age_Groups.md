# Power BI — Average Loan Amount by Age Group

## 1. Objective

In this session, the goal is to add a new visual to the report page that represents:

> **Average Loan Amount by Age Group**

However, the dataset currently contains an **Age** column but does not contain an **Age Group** column. Therefore, the first step is to create an Age Group column using **DAX**.

---

# 2. Check the Available Age Range

Before creating age groups, determine the minimum and maximum ages available in the dataset.

### Find the minimum age

1. Go to **Table View**.
2. Select the **Loan Default** table.
3. Locate the **Age** column.
4. Click the dropdown on the Age column.
5. Sort the column in **Ascending order**.
6. The minimum age available is **18 years**.

### Find the maximum age

1. Click the dropdown on the **Age** column again.
2. Sort it in **Descending order**.
3. The maximum age available is **69 years**.

Therefore, the dataset contains ages from approximately **18 to 69 years**.

---

# 3. Create the Age Group Column

Since Age Group is not available in the dataset, create a calculated column using DAX.

### Steps

1. In the **Data/Fields pane**, right-click the **Loan Default** table.
2. Select **New column**.
3. The DAX formula bar will appear.
4. Expand the formula bar if required.
5. Name the new column:

**Age groups**

6. Use a **nested IF function** to categorize the ages.

### Age Group Logic

| Age Condition  | Age Group         |
| -------------- | ----------------- |
| Age ≤ 19       | Teen              |
| Age ≤ 39       | Adults            |
| Age ≤ 59       | Middle Age Adults |
| Remaining ages | Senior Citizens   |

The important point is that the conditions are evaluated **sequentially**.

For example:

* First, Power BI checks whether Age ≤ 19.
* If not, it checks whether Age ≤ 39.
* If not, it checks whether Age ≤ 59.
* Anything remaining is classified as Senior Citizens.

### DAX

```DAX
Age groups =
IF(
    'Loan Default'[Age] <= 19,
    "Teen",
    IF(
        'Loan Default'[Age] <= 39,
        "Adults",
        IF(
            'Loan Default'[Age] <= 59,
            "Middle Age Adults",
            "Senior Citizens"
        )
    )
)
```

### Understanding the nested IF

The structure is essentially:

```text
IF Age <= 19
    → Teen

ELSE IF Age <= 39
    → Adults

ELSE IF Age <= 59
    → Middle Age Adults

ELSE
    → Senior Citizens
```

So, for example:

* Age 18 → Teen
* Age 19 → Teen
* Age 20 → Adults
* Age 39 → Adults
* Age 40 → Middle Age Adults
* Age 59 → Middle Age Adults
* Age 60 → Senior Citizens
* Age 69 → Senior Citizens

7. Press **Enter** to create the column.
8. Power BI may take some time to apply the changes.

---

# 4. Verify the Age Group Column

After creating the column:

1. Click the **blank area on the report canvas** if necessary.
2. Collapse the formula bar.
3. Return to **Table View**.
4. Scroll to the right side of the table.
5. Locate the newly created **Age groups** column.
6. Click its dropdown.

You should see the age-group categories:

* **Teen**
* **Adults**
* **Middle Age Adults**
* **Senior Citizens**

### Important

The Age Group column is a **calculated column**, because a value needs to be assigned to each individual row based on that row's Age.

---

# 5. Remove the Temporary Table Visual

The lecture also removes the table visual that was created in the previous session for data validation.

1. Return to **Report View**.
2. Select the temporary table visual.
3. Delete/remove it from the canvas.

---

# 6. Create the Average Loan by Age Group Measure

Now that the Age groups column exists, create a measure to calculate the average loan amount for each age group.

### Steps

1. In **Report View**, locate the **Measures Table**.
2. Right-click **Measures Table 1**.
3. Select **New Measure**.
4. Expand the formula bar.
5. Name the measure:

**Average Loan by Age Group**

6. Create the measure using `AVERAGEX`, `VALUES`, and `AVERAGE`.

### DAX

```DAX
Average Loan by Age Group =
AVERAGEX(
    VALUES('Loan Default'[Age groups]),
    AVERAGE('Loan Default'[Loan Amount])
)
```

---

# 7. Understand the Measure

The measure uses three important functions:

### `VALUES()`

```DAX
VALUES('Loan Default'[Age groups])
```

`VALUES()` returns a table containing the **distinct Age Group values**.

Conceptually, it produces something like:

```text
Teen
Adults
Middle Age Adults
Senior Citizens
```

### `AVERAGE()`

```DAX
AVERAGE('Loan Default'[Loan Amount])
```

This calculates the average loan amount.

### `AVERAGEX()`

`AVERAGEX()` iterates over the table returned by `VALUES()`.

Therefore, the calculation works conceptually like this:

```text
For each distinct Age Group:
    Calculate the average Loan Amount
```

So the result can be represented as:

| Age Group         |                    Average Loan Amount |
| ----------------- | -------------------------------------: |
| Teen              |             Average for Teen borrowers |
| Adults            |            Average for Adult borrowers |
| Middle Age Adults | Average for Middle Age Adult borrowers |
| Senior Citizens   |   Average for Senior Citizen borrowers |

The key idea is that **`VALUES()` provides the distinct age groups, while `AVERAGEX()` evaluates the average loan amount for each of those groups.**

---

# 8. Create the Line Chart

Now represent the average loan amount by age group visually.

### Steps

1. Click on a **blank area of the report canvas**.
2. Select a **Line Chart** from the Visualizations pane.
3. The lecture creates the chart by copying an existing line chart:

   * Select the existing line chart.
   * Press **Ctrl + C**.
   * Press **Ctrl + V**.
4. Move the newly created line chart to the **right-hand side** of the report page.
5. Increase its size as required.

---

# 9. Configure the Line Chart

The copied line chart initially contains fields from the previous visual.

Remove:

* **Employment Type** from the **X-axis** bucket.
* **Default Rate** from the **Y-axis** bucket.

Then add the fields required for the new visual.

### X-axis

Add:

**Age groups**

from the **Loan Default** table.

### Y-axis

Add:

**Average Loan by Age Group**

from the Measures table.

You can add the measure by checking the box next to it in the Data/Fields pane.

The resulting chart will show the **average loan amount for each Age Group category**.

---

# 10. Format the Line Color

The lecture then customizes the appearance of the chart.

### Steps

1. Select the line chart.
2. Open **Format visual**.
3. Expand the relevant **Lines/Colors** formatting options.
4. Open the color selector.
5. Select **More colors**.
6. Enter the color value specified in the lecture:

**B1B** (as stated in the transcript).

7. Press **Enter**.

This changes the color of the line.

---

# 11. Change the Interpolation Type

The line chart's interpolation can also be modified.

### Steps

1. Select the line chart.
2. Open its formatting options.
3. Locate the **Interpolation** setting.
4. Change it from **Step** to **Smooth**.

This produces a smoother-looking line chart.

### Smooth Type

The lecture also demonstrates that the smooth/interpolation type can be changed.

For example:

* **Monotone**
* **Cardinal**

The lecture changes the type to **Cardinal** as an example, while also noting that **Monotone** can be retained if preferred.

---

# 12. Change the Chart Title

The default chart title should be replaced with a meaningful title.

### Steps

1. Select the line chart.
2. Open **Format visual**.
3. Go to **General**.
4. Expand **Title**.
5. Edit the title.
6. Enter:

**Average Loan Amount by Age Group**

The final chart should clearly communicate that it displays the average loan amount for each age group.

---

# 13. Final Result

The completed visual represents:

> **Average Loan Amount by Age Group**

The overall workflow is:

```text
Age column
     ↓
Determine minimum & maximum age
     ↓
Create Age groups calculated column
     ↓
18–19   → Teen
20–39   → Adults
40–59   → Middle Age Adults
60+     → Senior Citizens
     ↓
Create "Average Loan by Age Group" measure
     ↓
AVERAGEX + VALUES + AVERAGE
     ↓
Create Line Chart
     ↓
Age groups → X-axis
Average Loan by Age Group → Y-axis
     ↓
Format line/color/interpolation
     ↓
Title: Average Loan Amount by Age Group
```

---

## Key Concepts to Remember

### 1. Calculated Column vs Measure

**Age groups** is a **calculated column** because every row needs to be classified according to its Age.

**Average Loan by Age Group** is a **measure** because it performs an aggregation that can dynamically respond to the visual's filter context.

### 2. Nested IF in DAX

A nested `IF()` can be used when multiple conditions need to be evaluated sequentially.

```DAX
IF(condition1, result1,
    IF(condition2, result2,
        IF(condition3, result3,
            default_result
        )
    )
)
```

### 3. `VALUES()` + `AVERAGEX()`

This combination is useful when you want to iterate through distinct categories and calculate an expression for each category.

```DAX
AVERAGEX(
    VALUES(Category),
    Expression
)
```

In this lecture:

```DAX
AVERAGEX(
    VALUES('Loan Default'[Age groups]),
    AVERAGE('Loan Default'[Loan Amount])
)
```

means:

> **For every distinct age group, calculate the average loan amount.**

### 4. Age Group Boundaries

Because the conditions are checked from top to bottom, the boundaries are:

* **18–19:** Teen
* **20–39:** Adults
* **40–59:** Middle Age Adults
* **60–69:** Senior Citizens

The next session will cover **data validation for this chart** and then proceed to creating another chart.
