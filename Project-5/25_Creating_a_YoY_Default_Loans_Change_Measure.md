# Power BI — Year-on-Year Default Loans Change Measure

## 1. Objective of the Session

In this session, the focus is on creating another **DAX measure** for the **Financial Risk Matrix** report page.

In the previous session, a measure was created for:

> **Year-on-Year Loan Amount Change**

In this session, a similar measure is created for:

> **Year-on-Year Default Loans Change**

The purpose is to determine how the **number of default loans changes from one year to the next**, expressed as a percentage. The measure will be stored in **Measures Table 3**. 

---

# 2. Remove Unnecessary Column from Measures Table 3

The first task is to clean up **Measures Table 3**.

The transcript states that **Column 1** is no longer required.

### Steps

1. Locate **Measures Table 3** in the Data/Fields pane.
2. Find **Column 1**.
3. Click the **three dots (`...`)** next to the column/table as appropriate.
4. Select **Delete from model**.
5. Wait for Power BI to complete the deletion.

The unnecessary Column 1 is now removed from the model.

---

# 3. Collapse the Loan Default Table

After removing Column 1:

1. Collapse the **Loan Default** table in the Data pane.
2. This keeps the Fields pane organized and makes it easier to work with Measures Table 3.

---

# 4. Create a New Measure

Since this measure is also intended for the third report page, it is stored in **Measures Table 3**.

### Steps

1. Right-click **Measures Table 3**.
2. Select **New Measure**.
3. Wait for the formula bar to open.
4. Expand/click the formula bar.
5. Name the measure:

> **Year on Year Default Loans Change**

The instructor repeats the name while entering it. 

---

# 5. Basic Formula for YoY Default Loans Change

The measure follows the same general year-on-year formula discussed previously:

$$
\text{YoY Change}
=
\frac{\text{Current Value} - \text{Previous Value}}
{\text{Previous Value}}
$$

For this particular measure:

* **Current Value** = Current year's number of default loans
* **Previous Value** = Previous year's number of default loans

Therefore:

$$
\text{YoY Default Loans Change}
=
\frac{
\text{Current Default Loans}
-
\text{Previous Default Loans}
}{
\text{Previous Default Loans}
}
$$

The result is subsequently multiplied by **100** to express it as a percentage. 

---

# 6. Use the DIVIDE Function

The instructor again uses the `DIVIDE()` function.

The general structure is:

```DAX id="l0k8tr"
DIVIDE(
    Numerator,
    Denominator,
    Alternate Result
)
```

For this measure:

### Numerator

```text
Current Default Loans − Previous Default Loans
```

### Denominator

```text
Previous Default Loans
```

### Alternate Result

```text
0
```

The alternate result is used when the denominator is zero. 

---

# 7. Calculate the Current Number of Default Loans

To calculate the current number of default loans, the instructor uses:

* `CALCULATE()`
* `COUNTROWS()`
* `FILTER()`

The logic is:

> Filter the Loan Default table to rows where the Default column is `TRUE`, and count those rows.

Conceptually:

```DAX id="1whvqu"
CALCULATE(
    COUNTROWS(
        FILTER(
            'Loan Default',
            'Loan Default'[Default] = TRUE()
        )
    ),
    'Loan Default'[Year] = YEAR(MAX('Loan Default'[Date]))
)
```

The important part is that only rows where:

> **Default = TRUE**

are counted. 

---

# 8. Understanding COUNTROWS + FILTER

The calculation works in two stages.

### `FILTER()`

The `FILTER()` function examines the **Loan Default** table.

The condition is:

```DAX id="c3l2uk"
'Loan Default'[Default] = TRUE()
```

Therefore, only defaulted loans are retained.

### `COUNTROWS()`

After filtering the table, `COUNTROWS()` counts how many rows remain.

So conceptually:

```text
Loan Default Table
        ↓
Filter Default = TRUE
        ↓
Only default-loan records
        ↓
COUNTROWS()
        ↓
Number of default loans
```

This gives the number of default loans for the specified year.

---

# 9. Apply the Current-Year Filter

The current year's value is determined using the **Year** column that was previously created in the Loan Default table.

The instructor uses the logic:

```DAX id="6k3r1x"
'Loan Default'[Year]
    = YEAR(MAX('Loan Default'[Date]))
```

### Meaning

1. `MAX(Date)` finds the maximum/latest available date.
2. `YEAR()` extracts its year.
3. The Loan Default `Year` column is filtered to that year.
4. The number of rows where `Default = TRUE` is counted.

So the calculation represents:

> **Number of default loans in the current/latest year.** 

---

# 10. Calculate the Previous Year's Default Loans

The denominator must contain the **previous year's default-loan count**.

The instructor again uses:

* `CALCULATE()`
* `COUNTROWS()`
* `FILTER()`

The basic logic is:

```DAX id="8k7j1w"
CALCULATE(
    COUNTROWS(
        FILTER(
            'Loan Default',
            'Loan Default'[Default] = TRUE()
        )
    ),
    'Loan Default'[Year] =
        YEAR(MAX('Loan Default'[Date])) - 1
)
```

### Important point

The same condition is used:

```DAX id="t6y2fg"
'Loan Default'[Default] = TRUE()
```

But the year is changed to:

```DAX id="u4x7va"
YEAR(MAX('Loan Default'[Date])) - 1
```

Therefore, this calculation gives the number of default loans for the **previous year**. 

---

# 11. Why `-1` Is Used

The previous year's value is required for YoY calculation.

If the current year is:

> 2016

then the previous year is:

> 2015

Therefore:

$$
Previous\ Year = Current\ Year - 1
$$

The DAX implements this as:

```DAX id="4z6bqk"
YEAR(MAX('Loan Default'[Date])) - 1
```

This is used as the filter condition for the denominator. 

---

# 12. Set the Alternate Result to Zero

After creating the previous-year calculation, the instructor specifies the alternate result for `DIVIDE()`.

### Value

> **0**

So if the previous year's number of default loans is zero, the calculation returns zero rather than attempting an invalid division by zero.

The structure is:

```DAX id="b1q0cg"
DIVIDE(
    Numerator,
    PreviousYearValue,
    0
)
```

The `0` is therefore the **alternate result**, not the actual previous-year value. 

---

# 13. Complete the Numerator

At this point, the measure contains:

* Current-year default loans
* Previous-year default loans

However, the numerator is still incomplete.

The numerator must be:

$$
Current - Previous
$$

### Steps

1. Go to the current-value expression.
2. Place the cursor before the appropriate line containing the previous-value expression.
3. Enter:

```text
-
```

4. Move to the next line using **Shift + Enter**.
5. Copy the previously created previous-year expression.
6. Paste it after the minus sign.

The numerator now becomes:

```text
Current Default Loans
-
Previous Default Loans
```

The denominator remains:

```text
Previous Default Loans
```

This completes the YoY formula. 

---

# 14. Convert the Result to Percentage

The `DIVIDE()` function initially returns a ratio.

For example:

```text
0.15
```

represents a 15% change.

To represent the result directly as a percentage value, the instructor multiplies the complete `DIVIDE()` calculation by **100**.

### Steps

1. Go to the end of the `DIVIDE()` calculation.
2. Write:

```DAX id="2r8m9a"
* 100
```

3. Press **Enter** after completing the measure.

So conceptually:

```DAX id="q8t3la"
DIVIDE(
    CurrentDefaultLoans - PreviousDefaultLoans,
    PreviousDefaultLoans,
    0
) * 100
```

The result is now expressed in percentage terms. 

---

# 15. Full DAX Measure

Combining all the steps from the lecture, the intended measure can be represented as:

```DAX id="w0m5v7"
Year on Year Default Loans Change =
DIVIDE(
    CALCULATE(
        COUNTROWS(
            FILTER(
                'Loan Default',
                'Loan Default'[Default] = TRUE()
            )
        ),
        'Loan Default'[Year] =
            YEAR(MAX('Loan Default'[Date]))
    )
    -
    CALCULATE(
        COUNTROWS(
            FILTER(
                'Loan Default',
                'Loan Default'[Default] = TRUE()
            )
        ),
        'Loan Default'[Year] =
            YEAR(MAX('Loan Default'[Date])) - 1
    ),
    CALCULATE(
        COUNTROWS(
            FILTER(
                'Loan Default',
                'Loan Default'[Default] = TRUE()
            )
        ),
        'Loan Default'[Year] =
            YEAR(MAX('Loan Default'[Date])) - 1
    ),
    0
) * 100
```

### Important structure to remember

```text
DIVIDE(
    Current Default Loans - Previous Default Loans,
    Previous Default Loans,
    0
) × 100
```

This is the core logic demonstrated in the lecture. 

---

# 16. Create the Measure

Once the formula is complete:

1. Press **Enter**.
2. Power BI processes the DAX expression.
3. Wait for the measure to be created.
4. The measure appears under **Measures Table 3**.

The instructor notes that Power BI may take some time to respond while processing the measure. 

---

# 17. Use the Existing Line Chart

The instructor then uses an existing line chart on the report page to visualize the newly created measure.

The previous session had placed:

> **Year-on-Year Loan Amount Change**

on the line chart.

That measure is now removed and replaced with the new measure.

### Steps

1. Click the existing **line chart**.
2. Locate the existing:
   **Year-on-Year Loan Amount Change**
3. Remove/uncheck that measure.
4. Locate:
   **Year-on-Year Default Loans Change**
5. Select/check it.

The line chart now displays the year-on-year change in **default loans** instead of loan amount. 

---

# 18. Interpretation of the Chart

The chart displays the percentage change in the number of default loans across years.

The instructor points out that **2013** is the minimum/earliest year available in the dataset.

There is no prior year available for 2013.

Therefore, a previous-year value cannot be calculated for 2013.

Because the `DIVIDE()` function has an alternate result of **0**, the chart displays:

> **0**

for 2013. 

---

# 19. Subsequent Years

For all subsequent years, a previous year is available.

Therefore, the measure can calculate the year-on-year change.

For example:

```text
2013 → No prior year → 0

2014 → Compared with 2013

2015 → Compared with 2014

2016 → Compared with 2015

...
```

The resulting values are expressed as percentages.

The instructor notes that although the changes are not very large, there is still some variation that can be observed on the chart. 

---

# 20. Example of How the Measure Works

Suppose the number of default loans is:

| Year | Default Loans |
| ---- | ------------: |
| 2013 |        10,000 |
| 2014 |        11,000 |
| 2015 |        10,500 |

### 2013

There is no 2012 data.

Therefore:

```text
YoY Change = 0
```

because the alternate result is 0.

### 2014

$$
\frac{11,000-10,000}{10,000}\times100
$$

$$
=10\%
$$

### 2015

$$
\frac{10,500-11,000}{11,000}\times100
$$

$$
\approx -4.55\%
$$

So the chart can show both:

* Positive percentage → number of defaults increased
* Negative percentage → number of defaults decreased
* Zero → no change or alternate result, depending on context

---

# 21. Difference Between the Previous and Current Measures

The previous session calculated:

> **Year-on-Year Loan Amount Change**

This session calculates:

> **Year-on-Year Default Loans Change**

The main difference is **what is being measured**.

### Previous measure

Uses:

```text
SUM(Loan Amount)
```

Therefore, it measures changes in the **total loan amount**.

### Current measure

Uses:

```text
COUNTROWS(
    FILTER(... Default = TRUE)
)
```

Therefore, it measures changes in the **number of default loans**.

---

# 22. DAX Functions Used

## `CALCULATE()`

Used to evaluate the number of default loans under a specific year filter.

---

## `COUNTROWS()`

Counts the number of rows remaining after filtering.

---

## `FILTER()`

Filters the Loan Default table so that only defaulted loans remain.

The key condition is:

```DAX id="3g9qkd"
'Loan Default'[Default] = TRUE()
```

---

## `MAX()`

Finds the maximum/latest available date.

---

## `YEAR()`

Extracts the year from the maximum date.

---

## `DIVIDE()`

Divides the difference between current and previous values by the previous value and provides a safe alternate result if the denominator is zero.

---

# 23. Key Concept — Current vs Previous

The instructor explicitly explains the three major components of the formula.

### Current value

```text
Number of default loans in current year
```

### Previous value

```text
Number of default loans in previous year
```

### YoY calculation

```text
(Current − Previous) / Previous
```

### Percentage

```text
(Current − Previous) / Previous × 100
```

### Zero denominator handling

```text
If Previous = 0 → return 0
```

This structure should be remembered because it is reusable for calculating year-on-year changes for many different metrics. 

---

# 24. Visual Result

The existing line chart now represents:

### Chart Type

**Line Chart**

### Measure

**Year-on-Year Default Loans Change**

### Time dimension

**Year**

### Metric

**Percentage change in number of default loans**

The chart shows the year-by-year change in default loans. 

---

# 25. Formatting Is Deferred

The instructor does **not** fully format the chart in this session.

Formatting such as:

* Font style
* Visual appearance
* Other chart formatting

will be discussed in an upcoming session.

The main objective of this session was the **creation of the DAX measure** and its initial representation on the line chart. 

---

# 26. Complete Workflow

```text
Measures Table 3
        ↓
Delete unnecessary Column 1
        ↓
Collapse Loan Default table
        ↓
Right-click Measures Table 3
        ↓
New Measure
        ↓
Name:
Year on Year Default Loans Change
        ↓
Use DIVIDE()
        ↓
Calculate CURRENT default loans
        ↓
CALCULATE()
        ↓
COUNTROWS()
        ↓
FILTER()
        ↓
Default = TRUE
        ↓
Year = YEAR(MAX(Date))
        ↓
Calculate PREVIOUS default loans
        ↓
CALCULATE()
        ↓
COUNTROWS()
        ↓
FILTER()
        ↓
Default = TRUE
        ↓
Year = YEAR(MAX(Date)) - 1
        ↓
Numerator:
Current − Previous
        ↓
Denominator:
Previous
        ↓
Alternate Result:
0
        ↓
Multiply entire DIVIDE calculation by 100
        ↓
Press Enter
        ↓
Measure created
        ↓
Select existing Line Chart
        ↓
Remove Year-on-Year Loan Amount Change
        ↓
Select Year-on-Year Default Loans Change
        ↓
View year-by-year percentage changes
        ↓
2013 = 0 because no prior year
```

---

# 27. Quick Revision Notes

### Measure

**Year on Year Default Loans Change**

### Formula

$$
\boxed{
\frac{Current\ Default\ Loans-Previous\ Default\ Loans}
{Previous\ Default\ Loans}
\times100
}
$$

### Current default loans

```text
COUNTROWS
    ↓
FILTER Loan Default
    ↓
Default = TRUE
    ↓
Year = Current Year
```

### Previous default loans

```text
COUNTROWS
    ↓
FILTER Loan Default
    ↓
Default = TRUE
    ↓
Year = Current Year − 1
```

### Error handling

If previous-year value/denominator is zero:

> Return **0**

### Visualization

**Line Chart**

### First year

**2013 → 0**, because there is no prior year available.

### Other years

Each year is compared against the immediately preceding year.

### Formatting

Detailed chart formatting is postponed to a future session. 
