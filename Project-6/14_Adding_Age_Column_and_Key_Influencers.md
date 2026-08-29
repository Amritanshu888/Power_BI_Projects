# Power BI – Key Influencers Visual & Creating Property Age Column

## 1. Objective of the Session

In this session, the focus is on:

1. Creating a **new calculated column** called **Age** because it is not directly available in the dataset.
2. Calculating the age of a property using:

   * **Purchase Date**
   * **Year Built**
3. Viewing and validating the newly created column.
4. Adding a **Key Influencers visual** to the report page.
5. Analyzing the relationship between **Purchase Price** and **Age**.
6. Changing the summarization of Age from **Sum** to **Don't summarize**.
7. Formatting the Key Influencers visual.
8. Adding a border to the visual.
9. Using **Format Painter** to apply formatting from another visual.

---

# 2. Creating the Age Column

The dataset already contains:

* `Purchase Date`
* `Year Built`

However, it does **not** contain the age of the property.

Therefore, we need to create a new calculated column.

### Logic

The age of the property can be calculated as:

**Age = Year of Purchase Date − Year Built**

For example:

* Purchase Date = 2020
* Year Built = 2005

Then:

**Age = 2020 − 2005 = 15 years**

---

# 3. Steps to Create the Age Column

### Step 1 – Select the Housing Table

In the **Fields/Data pane**:

1. Locate the **Housing** table.
2. Right-click on the Housing table.

### Step 2 – Create a New Column

Select:

**New column**

Power BI will open the formula bar where you can enter the DAX expression.

### Step 3 – Create the Age Calculation

The basic DAX logic used in the lecture is:

```DAX
Age =
ABS(
    YEAR('Housing'[Purchase Date]) -
    'Housing'[Year Built]
)
```

### Explanation

#### `YEAR()`

```DAX
YEAR('Housing'[Purchase Date])
```

Extracts the **year** from the Purchase Date.

For example:

```text
Purchase Date = 15/06/2020
YEAR(Purchase Date) = 2020
```

#### Subtraction

```DAX
YEAR(Purchase Date) - Year Built
```

calculates how many years have passed since the property was built.

#### `ABS()`

The lecture also mentions considering the **absolute value**.

```DAX
ABS(...)
```

returns the positive magnitude of the difference.

For example:

```text
ABS(2020 - 2005) = 15
ABS(2005 - 2020) = 15
```

### Step 4 – Press Enter

After entering the formula:

**Press Enter**

Power BI creates the calculated column.

---

# 4. Verify the Newly Created Column

The instructor then checks whether the column was created correctly.

### Steps

1. Go to **Table View**.
2. Select the **Housing** table.
3. Scroll toward the end/right side of the table.
4. You should see the newly created **Age** column.

The column contains different numerical values representing the **age of the property**.

### Important

The Age column represents:

> **The age of the house/property at the time it was purchased.**

---

# 5. Why Create the Age Column?

The instructor wants to analyze whether the **age of a property has an impact on its purchase price**.

Therefore, the two important fields for the next analysis are:

* **Purchase Price** → the value being analyzed
* **Age** → the factor potentially influencing Purchase Price

This makes the **Key Influencers visual** appropriate for the analysis.

---

# 6. Add the Key Influencers Visual

Now we move back to the report.

### Steps

1. Go to **Report View**.
2. Click on a **blank area of the report canvas**.
3. From the Visualizations pane, select **Key Influencers**.
4. Power BI creates the Key Influencers visual.
5. Resize and position the visual appropriately on the report page.

---

# 7. Configure the Key Influencers Visual

The Key Influencers visual generally has two important areas:

* **Analyze**
* **Explain by**

In this example, we want to analyze **Purchase Price** based on **Age**.

---

## Step 1 – Add Purchase Price to Analyze

1. Locate **Purchase Price**.
2. Drag and drop **Purchase Price** into the **Analyze** field.

This tells Power BI:

> Analyze the Purchase Price and identify factors that influence it.

---

## Step 2 – Add Age to Explain By

1. Locate the newly created **Age** column.
2. Drag and drop **Age** into **Explain by**.

Now the visual is configured as:

```text
Analyze
   ↓
Purchase Price

Explain by
   ↓
Age
```

Power BI will run the analysis and attempt to identify how **Age** is related to **Purchase Price**.

---

# 8. Understanding the Key Influencers Results

After the analysis finishes, Power BI displays insights about the relationship between the two fields.

The lecture gives an example where Power BI identifies different age ranges and explains how they are associated with changes in purchase price.

For example, the visual may indicate that when **Age is within a certain range**, the average Purchase Price is higher by a particular amount.

The lecture mentions an example where:

> When the sum of Age is between **2 and 16**, the average Purchase Price increases by approximately **502.9K**.

Similarly, it gives an example of a decrease:

> When the sum of Age is between **16 and 45**, the average Purchase Price decreases by approximately **512.6K**.

### Important interpretation

The Key Influencers visual is trying to answer:

> **How is Purchase Price related to Age?**

It identifies patterns where certain age ranges are associated with higher or lower purchase prices.

---

# 9. Problem: Age Is Being Summarized as Sum

The instructor notices an important issue.

Power BI is initially treating **Age** as a numeric field and therefore may automatically apply a summarization such as:

**Sum of Age**

This is not ideal for this analysis.

Why?

Because **Age represents the age of an individual property**. We generally want to analyze the age itself or age ranges, rather than the **total/sum of ages across properties**.

Therefore, the summarization should be changed.

---

# 10. Change Age to "Don't Summarize"

The lecture recommends changing the Age field from **Sum** to **Don't summarize**.

### Steps

1. Select the **Age** field used in the Key Influencers visual.
2. Open its field/summarization dropdown.
3. Change:

**Sum → Don't summarize**

This prevents Power BI from adding together the ages.

### Why this is better

Instead of asking:

> "What happens when the **sum of property ages** falls within a certain range?"

we want the analysis to work with the **actual Age values/property ages**.

This gives a more meaningful interpretation of the relationship between:

**Property Age ↔ Purchase Price**

---

# 11. Analyze the Updated Results

After changing the summarization to **Don't summarize**, the Key Influencers visual provides a more useful analysis.

The lecture gives the example:

> When Age is between **16 and 45**, the average Purchase Price decreases by approximately **512.6K**.

The exact numbers are dependent on the dataset and the Power BI analysis.

The important concept is that the Key Influencers visual identifies **age ranges associated with increases or decreases in Purchase Price**.

---

# 12. Formatting the Key Influencers Visual

After configuring the analysis, the instructor formats the visual to match the report's overall appearance.

### Steps

1. Select the **Key Influencers visual**.
2. Click **Format Visual**.

---

# 13. Change Chart/Data Colors

Within the formatting options, go to the relevant **Charts** section.

You can select the **data color** according to your report theme.

### Steps

```text
Key Influencers
      ↓
Format Visual
      ↓
Charts
      ↓
Data Color
      ↓
Choose desired color
```

The instructor chooses a color of their choice.

---

# 14. Formatting Bubble Visual Colors

The instructor also explores the **Bubble** visual formatting.

### Steps

1. Go to the Bubble-related formatting options.
2. Open **Visual colors**.
3. Adjust the colors if required.
4. The instructor checks the **secondary color** option.

However, the instructor decides to **keep the secondary color as gray** rather than changing it.

So this setting is left unchanged.

---

# 15. Change Background Color

The background of the Key Influencers visual can also be customized.

### Steps

1. Select the Key Influencers visual.
2. Open **Format Visual**.
3. Locate the **Background** option.
4. Choose a different background color if desired.

The instructor chooses a different color as part of the formatting demonstration.

---

# 16. Use Format Painter

The instructor then uses an existing **Sales by Region** chart as a formatting reference.

### Steps

1. Select the **Sales by Region** chart.
2. Click **Format Painter**.
3. Click the **Key Influencers visual**.

This applies the formatting of the Sales by Region chart to the Key Influencers visual.

### If You Prefer the Previous Colors

The instructor notes that the previously used colors may look better.

In that case:

**Press `Ctrl + Z`**

to undo the formatting change.

The instructor ultimately prefers the previous appearance.

---

# 17. Add a Border to the Key Influencers Visual

The lecture also demonstrates how to add a border around the visual.

### Steps

1. Select the **Key Influencers visual**.
2. Click **Format Visual**.
3. Go to **General**.
4. Open **Effects**.
5. Locate **Border**.
6. Change the border setting to **1**.

This adds a visible border around the Key Influencers visual.

---

# 18. Final Key Influencers Configuration

The completed visual can be summarized as:

| Component        | Configuration                     |
| ---------------- | --------------------------------- |
| Visual           | Key Influencers                   |
| Analyze          | Purchase Price                    |
| Explain by       | Age                               |
| Age              | Don't summarize                   |
| Data/Chart color | Customized                        |
| Secondary color  | Kept gray                         |
| Background       | Customized                        |
| Border           | Enabled / set to 1                |
| Formatting       | Format Painter optionally applied |

---

# 19. Important DAX Concept – Calculated Column vs Measure

This session also reinforces an important Power BI distinction.

Here, **Age** is created as a **calculated column**, not a measure.

### Why?

Age is a property-level attribute.

Each house/property has its own age:

```text
House 1 → Age = 10
House 2 → Age = 25
House 3 → Age = 5
House 4 → Age = 40
```

Therefore, we need a value stored/evaluated for each row.

A calculated column is appropriate.

The logic is:

```text
Purchase Date
      ↓
Extract Year
      ↓
Subtract Year Built
      ↓
Absolute Value
      ↓
Age
```

---

# 20. Key Influencers – Core Concept

The **Key Influencers** visual is useful when you want to understand:

> **Which factors are associated with increases or decreases in a particular metric?**

In this session:

```text
Metric being analyzed
        ↓
   Purchase Price
        ↑
        │
   Explain by
        ↑
       Age
```

Power BI examines the available data and identifies patterns in Age that are associated with changes in Purchase Price.

---

# 21. Important Observations from the Session

### 1. Create missing attributes when required

Even though the dataset doesn't directly contain **Age**, we can derive it using existing columns.

### 2. Purchase Date is converted to a year

We don't need the complete purchase date for this calculation. We extract its year using:

```DAX
YEAR(Purchase Date)
```

### 3. Age is calculated using Year Built

```text
Age = Purchase Year − Year Built
```

### 4. `ABS()` can be used

The instructor recommends considering the absolute value to ensure the resulting age is positive.

### 5. Verify calculated columns

After creating a calculated column, use **Table View** to inspect the resulting values.

### 6. Key Influencers can identify relationships

It helps identify how one variable is associated with changes in another.

### 7. Be careful with automatic summarization

Power BI may automatically summarize numeric columns as **Sum**.

For an attribute such as Age, this may not be meaningful.

Therefore, use:

**Don't summarize**

when appropriate.

### 8. Visual formatting matters

The lecture demonstrates:

* Data colors
* Bubble/visual colors
* Secondary colors
* Background
* Format Painter
* Undo using `Ctrl + Z`
* Border

---

# 22. Complete Workflow

```text
Housing Table
      ↓
Right-click Housing
      ↓
New Column
      ↓
Calculate Age
      ↓
YEAR(Purchase Date) - Year Built
      ↓
ABS()
      ↓
Press Enter
      ↓
Check Column in Table View
      ↓
Go to Report View
      ↓
Insert Key Influencers Visual
      ↓
Analyze → Purchase Price
      ↓
Explain by → Age
      ↓
Power BI runs analysis
      ↓
Check identified relationships
      ↓
Change Age → Don't summarize
      ↓
Review improved analysis
      ↓
Format Visual
      ↓
Customize Colors
      ↓
Customize Background
      ↓
Optional Format Painter
      ↓
General → Effects → Border → 1
```

## Final takeaway

The main lesson is that **Power BI's Key Influencers visual can be used to discover factors associated with changes in a target metric**. In this example, we first derived a meaningful **Age** attribute from `Purchase Date` and `Year Built`, and then used **Purchase Price** as the metric to analyze and **Age** as the explanatory factor.
