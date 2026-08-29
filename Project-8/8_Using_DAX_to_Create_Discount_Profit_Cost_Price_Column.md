# Power BI – Adding Additional Columns Using DAX

## 1. Objective of the Session

In this session, additional columns are created in **Power BI using DAX (Data Analysis Expressions)**.

The columns created are:

1. **Discount Percentage**
2. **Profit Percentage**
3. **Cost Price**

The session builds on the previous data-cleaning work where the following columns were prepared:

* **Sales Price**
* **Mark Price**
* **Title**
* **Brand**

The final objective is to prepare the dataset so that it is ready for **reporting and visualization**.

---

# 2. Apply the Power Query Changes

The previous session involved cleaning the data in Power Query.

Now those changes need to be applied.

### Steps

1. In **Power Query Editor**, click **Close & Apply**.
2. Power BI applies all the transformations performed in Power Query.
3. Power BI takes you back to the **Report View** in Power BI Desktop.

---

# 3. Check the Data in Model View

After applying the changes, the instructor checks the table and its data.

### Steps

1. Click **Model View** from the left-hand navigation.
2. Locate the table being used, which in the lecture is the **T Shirt** table.
3. Then click **Table/Data View** to inspect the actual data.
4. It may take some time for the data to load.

The table now contains the cleaned price-related columns, including:

* Mark Price
* Sales Price
* Title
* Brand

---

# 4. Rename the Sales Price Column

The instructor notices that the Sales Price column has an incorrect/inconsistent name and renames it.

### Steps

1. Locate the Sales Price column.
2. Double-click the column name.
3. Rename it to:

**Sales Price**

This makes the column name clear and consistent.

---

# 5. Create the Discount Percentage Column

The first additional calculated column created using DAX is:

> **Discount Percentage**

This column calculates the discount given on each product.

---

## 5.1 Discount Percentage Formula

The formula is based on:

**Discount = Mark Price − Sales Price**

Then:

**Discount Percentage = ((Mark Price − Sales Price) / Mark Price) × 100**

### Mathematical representation

$$
Discount\ Percentage =
\frac{Mark\ Price-Sales\ Price}{Mark\ Price}\times100
$$

### Example

Suppose:

* Mark Price = ₹1,000
* Sales Price = ₹800

Then:

$$
Discount = 1000-800=200
$$

$$
Discount\ Percentage =
\frac{200}{1000}\times100=20\%
$$

Therefore, the discount is **20%**.

---

# 6. Create Discount Percentage Using DAX

The instructor creates this as a **calculated column**.

### Steps

1. On the right-hand side, locate the **Data pane**.
2. Right-click the **T Shirt** table.
3. Select **New Column**.
4. Power BI opens the **DAX formula bar**.
5. Expand the formula bar if required so that the formula is easier to write.
6. Name the column:

**Discount Percentage**

7. Enter the DAX formula.

The formula used is conceptually:

```DAX
Discount Percentage =
DIVIDE(
    'T Shirt'[Mark Price] - 'T Shirt'[Sales Price],
    'T Shirt'[Mark Price]
) * 100
```

The lecture describes the formula as:

```text
DIVIDE(
    Mark Price - Sales Price,
    Mark Price
) × 100
```

8. Press **Enter**.

Power BI creates the new **Discount Percentage** column.

---

# 7. Understanding the DAX DIVIDE Function

The formula uses the DAX:

**DIVIDE()**

The general syntax is:

```DAX
DIVIDE(<numerator>, <denominator>)
```

In this case:

### Numerator

```text
Mark Price - Sales Price
```

This calculates the actual discount amount.

### Denominator

```text
Mark Price
```

This converts the discount amount into a proportion of the original/marked price.

Finally:

```text
× 100
```

converts the proportion into a percentage value.

---

# 8. Result of Discount Percentage Column

After pressing Enter, the new column appears in the table.

For example:

| Mark Price | Sales Price | Discount Percentage |
| ---------: | ----------: | ------------------: |
|       1000 |         800 |                  20 |
|        500 |         400 |                  20 |
|       2000 |        1500 |                  25 |

The exact values depend on the dataset.

---

# 9. Create the Profit Percentage Column

Next, the instructor wants to determine the **Cost Price**.

However, the dataset does not contain the Cost Price directly.

The available information includes:

* Mark Price
* Sales Price
* Discount Percentage

But there is no:

> **Cost Price**

There is also no:

> **Profit Percentage**

Therefore, the instructor makes an assumption about the profit percentage.

---

# 10. Assumption for Profit Percentage

The lecture assumes that the profit percentage is somewhere between:

> **2% and 17%**

Since actual profit percentage values are not available in the dataset, they are generated using the DAX **RANDBETWEEN()** function.

### Assumption

```text
Minimum Profit Percentage = 2%
Maximum Profit Percentage = 17%
```

This means each product will receive a randomly generated integer profit percentage between **2 and 17**.

---

# 11. Create Profit Percentage Column Using RANDBETWEEN

### Steps

1. Right-click the **T Shirt** table in the Data pane.
2. Select **New Column**.
3. Expand the DAX formula bar if required.
4. Name the column:

**Profit Percentage**

5. Use the `RANDBETWEEN()` function.

Formula:

```DAX
Profit Percentage =
RANDBETWEEN(2, 17)
```

6. Press **Enter**.

Power BI creates the Profit Percentage calculated column.

---

# 12. Understanding RANDBETWEEN()

The DAX function:

```DAX
RANDBETWEEN(bottom, top)
```

returns a random integer between the specified minimum and maximum values.

Here:

```DAX
RANDBETWEEN(2, 17)
```

means:

> Generate a random integer from 2 through 17.

Possible values include:

```text
2, 3, 4, 5, ... 16, 17
```

Therefore, every row receives a profit percentage value within the assumed range.

### Important

This is an **assumption for the project**, not actual business data.

The lecture is essentially creating simulated profit percentages because the actual profit percentage isn't available.

---

# 13. Verify the Profit Percentage Column

After pressing Enter:

1. Collapse the formula bar if necessary.
2. Click the **Profit Percentage** column.
3. Inspect the generated values.

You will now see profit percentage values populated in the column.

For example:

| Product   | Profit Percentage |
| --------- | ----------------: |
| Product A |                 8 |
| Product B |                15 |
| Product C |                 4 |
| Product D |                11 |

The exact values can vary because they are generated using `RANDBETWEEN()`.

---

# 14. Calculate Cost Price

Now that the Profit Percentage is available, the instructor can calculate the **Cost Price**.

The formula used is:

$$
Cost\ Price =
\frac{100\times Sales\ Price}
{100+Profit\ Percentage}
$$

This formula is derived from the relationship between selling price, cost price, and profit percentage.

---

# 15. Understanding the Cost Price Formula

Profit percentage is generally calculated as:

$$
Profit\ Percentage =
\frac{Selling\ Price-Cost\ Price}
{Cost\ Price}\times100
$$

Rearranging the equation gives:

$$
Selling\ Price =
Cost\ Price\times
\left(1+\frac{Profit\ Percentage}{100}\right)
$$

Therefore:

$$
Cost\ Price =
\frac{Selling\ Price}
{1+\frac{Profit\ Percentage}{100}}
$$

Multiplying numerator and denominator by 100:

$$
Cost\ Price =
\frac{100\times Selling\ Price}
{100+Profit\ Percentage}
$$

The lecture uses **Sales Price as the selling price**.

Therefore:

```text
Cost Price =
(100 × Sales Price)
÷
(100 + Profit Percentage)
```

---

# 16. Example of Cost Price Calculation

Suppose:

* Sales Price = ₹1,000
* Profit Percentage = 10%

Then:

$$
Cost\ Price =
\frac{100\times1000}{100+10}
$$

$$
Cost\ Price =
\frac{100000}{110}
$$

$$
Cost\ Price \approx ₹909.09
$$

The selling price is therefore ₹1,000, representing approximately a 10% profit over the cost price.

---

# 17. Create Cost Price Using DAX

### Steps

1. Right-click the **T Shirt** table in the Data pane.
2. Click **New Column**.
3. Expand the DAX formula bar.
4. Name the column:

**Cost Price**

5. Use the `DIVIDE()` function.

The DAX is conceptually:

```DAX
Cost Price =
DIVIDE(
    100 * 'T Shirt'[Sales Price],
    100 + 'T Shirt'[Profit Percentage]
)
```

6. Press **Enter**.

Power BI creates the Cost Price column.

---

# 18. Understanding the Cost Price DAX Formula

The formula consists of two parts.

### Numerator

```text
100 × Sales Price
```

This represents the top part of the cost-price equation.

### Denominator

```text
100 + Profit Percentage
```

This accounts for the assumed profit percentage.

### Complete calculation

```text
Cost Price =
(100 × Sales Price)
/
(100 + Profit Percentage)
```

The DAX `DIVIDE()` function performs the division.

---

# 19. Final Columns Created

At the end of the session, the dataset contains the required price-related information.

### Existing/Cleaned Columns

* Sales Price
* Mark Price

### Newly Created DAX Columns

* Discount Percentage
* Profit Percentage
* Cost Price

Other product information includes:

* Title
* Brand

---

# 20. Overall Transformation Process

The complete workflow from the previous session through this session is:

```text
Raw/Uncleaned Data
       ↓
Clean data in Power Query
       ↓
Handle missing Original Price
       ↓
Create Mark Price
       ↓
Remove unnecessary helper columns
       ↓
Apply Power Query changes
       ↓
Return to Power BI Desktop
       ↓
Create Discount Percentage using DAX
       ↓
Create Profit Percentage using RANDBETWEEN()
       ↓
Create Cost Price using DAX
       ↓
Dataset ready for reporting
```

---

# 21. Important DAX Formulas from the Session

## Discount Percentage

```DAX
Discount Percentage =
DIVIDE(
    'T Shirt'[Mark Price] - 'T Shirt'[Sales Price],
    'T Shirt'[Mark Price]
) * 100
```

### Logic

```text
(Mark Price − Sales Price)
-------------------------------- × 100
         Mark Price
```

---

## Profit Percentage

```DAX
Profit Percentage =
RANDBETWEEN(2, 17)
```

### Logic

Generate a random integer:

```text
2 ≤ Profit Percentage ≤ 17
```

This is an assumed/simulated value because the original dataset does not provide profit percentage.

---

## Cost Price

```DAX
Cost Price =
DIVIDE(
    100 * 'T Shirt'[Sales Price],
    100 + 'T Shirt'[Profit Percentage]
)
```

### Logic

```text
              100 × Sales Price
Cost Price = ----------------------
             100 + Profit Percentage
```

---

# 22. Why Calculated Columns Are Used Here

The instructor uses **New Column** to create these values because the calculation needs to be performed for each individual product/row.

For example, every product can have:

* Its own Mark Price
* Its own Sales Price
* Its own Discount Percentage
* Its own Profit Percentage
* Its own Cost Price

Therefore, these are row-level calculations and are appropriate for **calculated columns**.

---

# 23. Important Concept: Data Preparation Before Reporting

The lecture follows an important Power BI workflow:

### Stage 1 – Data Cleaning

Power Query was used to:

* Remove/filter invalid values.
* Handle missing Original Price.
* Create Mark Price.
* Set appropriate data types.
* Remove unnecessary helper columns.

### Stage 2 – Data Enrichment

DAX is then used to add additional analytical information:

* Discount Percentage
* Profit Percentage
* Cost Price

### Stage 3 – Reporting

Once these columns are ready, the dataset can be used to create:

* Charts
* Tables
* KPIs
* Slicers
* Other report visuals

Therefore:

> **Power Query → Clean/Transform data → DAX → Add analytical calculations → Reporting**

---

# 24. Important Notes About RANDBETWEEN

The `RANDBETWEEN()` function is being used here to **simulate missing business information**.

The actual dataset does not contain the profit percentage, so the lecture assumes a range of 2–17%.

This means the resulting Cost Price is also based on this assumption.

Therefore:

> **The Cost Price is an estimated/calculated value, not an actual cost price obtained from the source data.**

This distinction is important when interpreting the final report.

---

# 25. Final Understanding

Initially, the dataset had limited price information:

```text
Sales Price
Mark Price
```

After data cleaning and DAX calculations, it becomes more useful for analysis:

```text
Mark Price
Sales Price
Discount Percentage
Profit Percentage
Cost Price
```

These additional columns provide information that can later be used to analyze:

* Product discounts
* Product profitability
* Pricing
* Cost vs. selling price
* Brand-level pricing
* Product-level performance

---

# Quick Revision

### Apply Power Query changes

**Close & Apply → Return to Power BI Desktop**

### Create a calculated column

**Data pane → Right-click T Shirt table → New Column → Enter DAX → Enter**

### Discount %

```DAX
Discount Percentage =
DIVIDE(
    [Mark Price] - [Sales Price],
    [Mark Price]
) * 100
```

### Profit %

```DAX
Profit Percentage =
RANDBETWEEN(2, 17)
```

### Cost Price

```DAX
Cost Price =
DIVIDE(
    100 * [Sales Price],
    100 + [Profit Percentage]
)
```

### Final result

```text
Clean Data
    ↓
Mark Price + Sales Price
    ↓
Discount Percentage
    ↓
Profit Percentage
    ↓
Cost Price
    ↓
Ready for Reporting
```

## Key Takeaway

The major lesson from this session is how to **extend a cleaned Power BI dataset using DAX calculated columns**. The lecture first calculates discount percentage from Mark Price and Sales Price, then assumes a profit percentage between 2% and 17% using `RANDBETWEEN()`, and finally uses that profit percentage with Sales Price to calculate Cost Price. The resulting dataset is considered ready for building the report.
