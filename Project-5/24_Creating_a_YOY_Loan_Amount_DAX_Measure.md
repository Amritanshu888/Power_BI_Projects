# Power BI Notes — Creating the Third Report Page & Year-on-Year Loan Amount Change

These notes are based directly on the provided lecture transcript. I’ve preserved the instructor’s terminology, sequence, DAX logic, and practical steps, including the corrections and validation/explanation given during the lecture. 

---

## 1. Creating the Third Report Page

The session begins with creating the **third page**, which is the **last page of the report**.

### Remove the Existing Data Validation Table

The table visual currently present on the report was created earlier for **data validation**. Since it is no longer required:

1. Select the **table visual**.
2. Press the **Delete** key.
3. The table visual is removed from the report.

The table was only used temporarily for validating data and is not required in the final report. 

---

## 2. Create the Third Page

After removing the validation table, create a new report page.

### Steps

1. Click the **`+` icon** at the bottom of the report.
2. A new report page is created.
3. Double-click the new page name, initially shown as **Page 1**.
4. Rename it to:

> **Financial Risk Matrix**

This will be the third and final page of the report. 

---

# 3. Copy the Existing Shape to the New Page

The instructor wants the new page to have the same visual/header design as the previous page.

### Steps

1. Go to the **second report page**.
2. Select the shape at the top of the page.
3. Press:

   * `Ctrl + C`
4. Move to the newly created **third page**.
5. Press:

   * `Ctrl + V`

The shape is now copied to the third page. 

---

## 4. Change the Text Inside the Shape

The copied shape needs to contain the name of the new page.

### Steps

1. Select the copied shape.
2. Open **Format Shape**.
3. Go to:

   * **Styles**
   * **Text**
   * **Text Box**
4. The text inside the shape can be edited from here.

The instructor already has **Financial Risk Matrix** written as the page name.

To copy the page name:

1. Select the page name.
2. Press `Ctrl + A`.
3. Press `Ctrl + C`.
4. Click inside the text box of the copied shape.
5. Select the existing text.
6. Press `Ctrl + V`.
7. Press **Enter**.

The shape now displays:

> **Financial Risk Matrix** 

---

# 5. Planned Visuals for the Financial Risk Matrix Page

The instructor mentions that this page will eventually contain:

* **Ribbon visual**
* **Line charts**
* **Decomposition Tree**

However, this particular session focuses primarily on **creating the measure for Year-on-Year Loan Amount Change**.

The other visuals/measures will be discussed in subsequent sessions. 

---

# 6. Objective of the Measure

The main topic of this session is creating a measure to calculate:

> **Year-on-Year Loan Amount Change**

Before writing the DAX, the instructor explains the general formula for calculating year-on-year (YoY) change. 

---

# 7. General Formula for Year-on-Year Change

The general formula explained in the lecture is:

$$
\text{YoY Change}
=
\frac{\text{Current Value} - \text{Previous Value}}
{\text{Previous Value}}
$$

In words:

> **Current Value − Previous Value, divided by Previous Value**

### Example

If:

* Current year value = 120
* Previous year value = 100

Then:

$$
\frac{120-100}{100}=0.20
$$

So the YoY change is:

> **0.20**, or **20%**

The instructor points out that the basic formula produces a **fraction/ratio**.

To express it as a percentage, multiply the result by **100**:

$$
0.20 \times 100 = 20\%
$$

This formula is applicable generally to year-on-year changes for different quantities. 

---

# 8. Create a Separate Measures Table

Because this is the **third report page**, the instructor creates a separate measures table specifically for measures used on this page.

### Steps

1. Expand the **Data pane**.
2. Go to the **Home** tab.
3. Click **Enter Data**.
4. Create a new table.
5. Name the table:

> **Measures Table 3**

6. Click **Load**.
7. Wait for the table to appear in the Data pane.

This provides a separate location for storing the measures used on the third page. 

---

# 9. Create the New Measure

Once **Measures Table 3** has been created:

1. Right-click the measures table.
2. Select **New Measure**.
3. Expand the formula bar.

The measure will be used to calculate the year-on-year change in loan amount. 

---

# 10. Use the DIVIDE Function

The instructor chooses the DAX `DIVIDE()` function for calculating the ratio.

The general structure being used is:

```DAX
DIVIDE(
    Numerator,
    Denominator,
    Alternate Result
)
```

### Three components

#### Numerator

The numerator will be:

> **Current Value − Previous Value**

#### Denominator

The denominator will be:

> **Previous Value**

#### Alternate Result

If the denominator is zero, division by zero would be invalid.

Therefore, the instructor specifies:

> **0**

as the alternate result. 

---

# 11. Calculate the Current Year's Loan Amount

The current value is calculated using:

* `CALCULATE()`
* `SUM()`

The logic is to calculate the **sum of Loan Amount** for the current year.

Conceptually:

```DAX
CALCULATE(
    SUM('Loan Default'[Loan Amount]),
    'Loan Default'[Year] = MAX('Loan Default'[Date])
)
```

The transcript explains that the **Loan Default** table contains:

* `Loan Amount`
* `Year`
* `Date`

The `Year` column had been created earlier in the report using DAX. 

---

# 12. Understanding the Current Value Expression

The instructor explains that the expression currently highlighted in blue represents the:

> **Current Value**

At this stage, only the current value has been written.

The numerator still needs to become:

> **Current Value − Previous Value**

So the previous year's value must be calculated separately and then subtracted from the current value. 

---

# 13. Calculate the Previous Year's Loan Amount

The denominator needs to contain the **previous year's loan amount**.

Again, `CALCULATE()` and `SUM()` are used.

The basic structure is:

```DAX
CALCULATE(
    SUM('Loan Default'[Loan Amount]),
    'Loan Default'[Year] = MAX('Loan Default'[Date]) - 1
)
```

### Why subtract 1?

The current year is determined from the maximum available date/year.

To obtain the previous year:

$$
\text{Previous Year} = \text{Current Year} - 1
$$

Therefore, the year filter is set to:

> **Year = MAX(Date) − 1**

This retrieves the loan amount corresponding to the previous year. 

---

# 14. Why the Year Column Is Used

The instructor specifically mentions that the **Year** column was created earlier.

It did not originally exist in the Loan Default table.

It was created using DAX.

Now that column is being reused in the current measure to filter the data according to year. 

---

# 15. Complete YoY Calculation Logic

The measure ultimately follows this structure:

$$
\frac{\text{Current Loan Amount} - \text{Previous Loan Amount}}
{\text{Previous Loan Amount}}
$$

The `DIVIDE()` function handles the calculation safely.

Conceptually:

```DAX
DIVIDE(
    Current Value - Previous Value,
    Previous Value,
    0
)
```

The final `0` means:

> If the previous year's value is zero, return 0 instead of producing a divide-by-zero error.

The instructor explicitly adds this alternate result. 

---

# 16. Final Measure Logic

The lecture builds the measure step-by-step. In consolidated form, the intended DAX logic is:

```DAX
Year on Year Loan Amount Change =
DIVIDE(
    CALCULATE(
        SUM('Loan Default'[Loan Amount]),
        'Loan Default'[Year] = YEAR(MAX('Loan Default'[Date]))
    )
    -
    CALCULATE(
        SUM('Loan Default'[Loan Amount]),
        'Loan Default'[Year] = YEAR(MAX('Loan Default'[Date])) - 1
    ),
    CALCULATE(
        SUM('Loan Default'[Loan Amount]),
        'Loan Default'[Year] = YEAR(MAX('Loan Default'[Date])) - 1
    ),
    0
)
```

**Important:** The transcript's spoken DAX construction around `MAX(Date)`/`YEAR()` is somewhat abbreviated, but the intended calculation is clearly current-year loan amount minus previous-year loan amount, divided by previous-year loan amount, with `0` as the alternate result.  

---

# 17. Create the Measure

Once the complete expression has been entered:

1. Press **Enter**.
2. Power BI processes the DAX.
3. Wait for the calculation to finish.
4. The **Year-on-Year Loan Amount Change** measure is created successfully.

The instructor then proceeds to visualize the measure. 

---

# 18. Create a Line Chart to View the Measure

The instructor creates a line chart to get an idea of how the measure behaves.

### Steps

1. Collapse the formula bar.
2. Click on a **blank area** of the report canvas.
3. Select the **Line Chart** visual.
4. Place the chart on the page.
5. Select the newly created:

> **Year-on-Year Loan Amount Change**

measure.

6. Expand the **Loan Default** table.
7. Select the **Year** column.
8. Add/drag **Year** to the **X-axis**.

The line chart will now show the year-on-year loan amount change across the available years. 

---

# 19. Convert the Ratio into a Percentage

Initially, the measure returns a **ratio**.

For example:

```text
0.10
```

represents a 10% change.

To display the result directly as a percentage value, the instructor multiplies the `DIVIDE()` result by **100**.

### Steps

1. Select the **Year-on-Year Loan Amount Change** measure.
2. Expand/edit the DAX formula.
3. Multiply the `DIVIDE()` calculation by:

```text
100
```

4. Press **Enter**.
5. Collapse the formula bar.

Now the values are displayed in percentage terms. 

---

# 20. Display Data Labels

The instructor then discusses displaying the values directly on the chart.

### Steps

1. Select the line chart.
2. Open **Format Your Visual**.
3. Locate **Data Labels**.
4. Enable/configure the data labels as required.

This allows the different year-on-year values to be visible on the chart. 

---

# 21. Increase Decimal Places

The values are relatively small, so showing only a couple of decimal places may not provide enough precision.

The instructor therefore increases the number of decimal places.

### Steps

1. Select the **Year-on-Year Loan Amount Change** measure.
2. Locate the decimal-place setting.
3. Initially, it may show **Auto**.
4. Increase the number of decimal places.
5. The instructor sets it to:

> **5 decimal places**

The setting can be directly changed to `5` and confirmed by pressing **Enter**. 

---

# 22. Understanding the First Year's Value

The instructor explains an important point about the first year shown in the chart.

The dataset's earliest available year is:

> **2013**

There is no year before 2013 in the dataset.

But the YoY calculation requires a previous year's value.

For 2013, that would theoretically require:

> **2012**

Since 2012 doesn't exist in the dataset, the previous-year value cannot be calculated.

However, the `DIVIDE()` function was given an alternate result of:

> **0**

Therefore, the YoY change for **2013** appears as:

> **0**

This is intentional and is a direct consequence of the alternate result supplied to `DIVIDE()`. 

---

# 23. Understanding the Subsequent Years

Starting from **2014**, a previous year exists.

Therefore:

### 2014

2014 is compared against:

> **2013**

### 2015

2015 is compared against:

> **2014**

### 2016

2016 is compared against:

> **2015**

And so on.

So the chart represents consecutive year-over-year comparisons. 

---

# 24. Conceptual Example

Suppose the loan amounts are:

| Year | Loan Amount |
| ---- | ----------: |
| 2013 |        ₹100 |
| 2014 |        ₹120 |
| 2015 |         ₹90 |

Then:

### 2013

No 2012 data exists.

Therefore:

**YoY = 0**

### 2014

$$
\frac{120-100}{100}\times100
=20\%
$$

### 2015

$$
\frac{90-120}{120}\times100
=-25\%
$$

So the line chart would show the year-by-year change in loan amount.

---

# 25. Important DAX Functions Used

## `DIVIDE()`

Used to safely divide one value by another.

Structure:

```DAX
DIVIDE(
    Numerator,
    Denominator,
    AlternateResult
)
```

In this lecture:

* Numerator = Current Loan Amount − Previous Loan Amount
* Denominator = Previous Loan Amount
* Alternate result = 0

---

## `CALCULATE()`

Used to evaluate the loan amount under a specified year filter.

It allows the calculation to switch between:

* Current year
* Previous year

---

## `SUM()`

Used to calculate the total **Loan Amount**.

```DAX
SUM('Loan Default'[Loan Amount])
```

---

## `MAX()`

Used to identify the maximum/most recent available date.

The year associated with that date is then used to identify the current year and previous year.

---

## `YEAR()`

Used to extract the year component from the date.

Conceptually:

```DAX
YEAR(MAX('Loan Default'[Date]))
```

This provides the year corresponding to the maximum available date.

---

# 26. Key Concept — YoY Formula

The most important formula from this lecture is:

$$
\boxed{
YoY =
\frac{Current - Previous}{Previous}
}
$$

For percentage representation:

$$
\boxed{
YoY\% =
\frac{Current - Previous}{Previous}
\times100
}
$$

Remember:

> **Current − Previous** goes in the numerator.

> **Previous** goes in the denominator.

> **0** is supplied as the alternate result when the denominator is zero.

---

# 27. Why `DIVIDE()` Is Preferred Here

Instead of performing a direct division, the lecture uses `DIVIDE()` because the denominator can potentially be zero.

For example:

```DAX
Current - Previous / Previous
```

can result in an invalid division when `Previous = 0`.

Using:

```DAX
DIVIDE(Current - Previous, Previous, 0)
```

allows Power BI to return **0** when the denominator is zero.

This is particularly relevant for the first available year, where there is no previous year's data.

---

# 28. Final Report Page Progress

At the end of this session, the **Financial Risk Matrix** page has been created and the first major measure for the page has been developed.

### Page

**Financial Risk Matrix**

### Measure

**Year-on-Year Loan Amount Change**

### Visualization used for initial inspection

**Line Chart**

### X-axis

**Year**

### Y-axis

**Year-on-Year Loan Amount Change**

### Percentage conversion

The result is multiplied by **100**.

### Decimal precision

Set to **5 decimal places**.

### First year

2013 → **0**, because no previous-year data exists.

### Subsequent years

Each year is compared with the immediately preceding year. 

---

# 29. Complete Step-by-Step Workflow

```text
Create third report page
        ↓
Remove temporary data-validation table
        ↓
Rename page → Financial Risk Matrix
        ↓
Copy header shape from second page
        ↓
Paste shape onto third page
        ↓
Change shape text → Financial Risk Matrix
        ↓
Plan page visuals
(Ribbon + Line Charts + Decomposition Tree)
        ↓
Create Measures Table 3
        ↓
Right-click Measures Table 3
        ↓
New Measure
        ↓
Define Year-on-Year Loan Amount Change
        ↓
Current Value = Current Year's Loan Amount
        ↓
Previous Value = Previous Year's Loan Amount
        ↓
Numerator = Current − Previous
        ↓
Denominator = Previous
        ↓
Alternate result = 0
        ↓
Use DIVIDE()
        ↓
Create measure
        ↓
Create Line Chart
        ↓
Add Year → X-axis
        ↓
Add YoY Loan Amount Change → Y-axis
        ↓
Multiply result by 100
        ↓
Enable Data Labels
        ↓
Increase decimal places
        ↓
Set decimal places to 5
        ↓
Interpret results
        ↓
2013 = 0 because no 2012 data
        ↓
2014 compares with 2013
2015 compares with 2014
2016 compares with 2015
...
```

---

## 30. Key Takeaways

1. The **third and final report page** is named **Financial Risk Matrix**.

2. A separate **Measures Table 3** is created to store measures for this page.

3. The major measure created in this session is **Year-on-Year Loan Amount Change**.

4. The general YoY formula is:

   **(Current − Previous) / Previous**

5. `DIVIDE()` is used to safely handle division.

6. The alternate result is set to **0**.

7. `CALCULATE()` and `SUM()` are used to calculate the loan amount for the required year.

8. The **Year** column created earlier is reused in the measure.

9. The previous year is obtained by subtracting **1** from the current year.

10. The measure initially produces a ratio.

11. Multiplying by **100** converts it into a percentage representation.

12. A line chart is used to visualize the YoY change by year.

13. The **Year** field goes on the X-axis.

14. The YoY measure goes on the Y-axis.

15. Data labels can be enabled to display values directly.

16. Decimal places are increased to **5** because the values are small.

17. The first available year, **2013**, displays **0** because there is no previous year in the dataset.

18. From 2014 onward, each year is compared with its immediately preceding year.

19. The instructor notes that a more visually appealing chart will be created in a subsequent session, along with additional measures for the Financial Risk Matrix page. 
