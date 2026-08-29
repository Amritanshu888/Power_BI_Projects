# Power BI Data Modeling — Creating Relationships & Implementing Star Schema

These notes cover the complete lecture, including the **practical steps in Power BI Model View**, relationship settings, cardinality, cross-filter direction, active relationships, primary/foreign keys, matching data types, and the final Star Schema structure.

---

# 1. Purpose of the Lecture

This lecture focuses on the **data model used for Power BI reporting**.

Before this lecture, the following concepts were already covered:

* Data transformation
* Primary key
* Foreign key
* Star schema
* Cardinality
* Dimension tables

The purpose now is to actually apply these concepts in a Power BI model. 

---

# 2. Opening the Model View

The first practical step is to open **Model View** in Power BI.

### Steps

1. Open the Power BI report.
2. Go to the **Model View**.
3. Collapse the **Properties** and **Data** sections to make the model easier to work with.

In the model, the following tables are present:

* **Dimension Promotion**
* **Customer Dimension**
* **Fact Table**
* **Product Dimension**

The fact table already has relationships with some dimension tables. 

---

# 3. Removing Existing Relationships

Before creating the relationships manually, the lecture removes the existing relationships.

### Steps

For each existing relationship:

1. Right-click on the relationship line.
2. Select **Delete**.
3. Repeat the process for the other existing relationship.

After deleting them, the model contains:

* 1 Fact Table
* 3 Dimension Tables

The three dimension tables are:

1. Customer Dimension
2. Promotion Dimension
3. Product Dimension 

---

# 4. Arrange the Tables

The lecture then arranges the tables visually in Model View.

The **Fact Table** is kept in the center, with the dimension tables positioned around it.

This arrangement is useful because it makes the Star Schema visually clear.

Conceptually:

```text
                 Customer Dimension
                         |
                         |
Product Dimension — Fact Table — Promotion Dimension
```

The exact visual positioning is not what creates the relationship; it simply makes the model easier to understand.

---

# 5. Creating the Customer–Fact Relationship

The first relationship created is between:

* **Customer Dimension**
* **Fact Table**

The common column is:

**Customer ID**

Both tables contain a `Customer ID` column. 

---

## Practical Steps

### Step 1

In the **Customer Dimension** table:

* Locate `Customer ID`.

### Step 2

Double-click/select the `Customer ID` column and drag it onto the `Customer ID` column in the **Fact Table**.

### Step 3

Power BI opens the **relationship dialog box**.

The `Customer ID` column is automatically selected on both sides because it is the column being used to create the relationship. 

---

# 6. Customer–Fact Cardinality

The relationship dialog shows:

**Cardinality = One-to-Many (1:N)**

Why?

Because:

* In the **Customer Dimension**, one customer ID occurs once.
* In the **Fact Table**, the same customer ID can occur multiple times because one customer can make multiple transactions.

For example:

```text
Customer Dimension       Fact Table

A01                      A01
                         A01
                         A01
                         A01
```

Therefore:

```text
Customer Dimension  1 ───────── N  Fact Table
```

The dimension table is on the **one side**, and the fact table is on the **many side**. 

---

# 7. Cross-Filter Direction

Another important setting in the relationship dialog is:

**Cross filter direction**

The lecture selects:

**Single**

### What does Single mean?

With Single cross-filter direction:

```text
Customer Dimension
        ↓
     Fact Table
```

The **Customer Dimension can filter the Fact Table**.

But:

```text
Fact Table
    ✕
    ↓
Customer Dimension
```

The Fact Table **cannot filter the Customer Dimension**.

This is an important concept that will become clearer when creating visuals and reports. 

---

# 8. Active Relationship

The relationship dialog also contains:

**Make this relationship active**

The checkbox is selected.

An important rule mentioned in the lecture is:

> Between any two given tables, only one active relationship can exist at a given time.

So when creating this relationship, the **active relationship** checkbox is enabled. 

---

# 9. Save the Relationship

After checking the required settings:

### Steps

1. Verify the columns.
2. Verify **Cardinality = One-to-Many**.
3. Verify **Cross filter direction = Single**.
4. Ensure **Make this relationship active** is checked.
5. Click **Save**.

Power BI then creates the relationship between:

**Customer Dimension → Fact Table** 

---

# 10. Understanding the Relationship Symbols

After the relationship is created, Power BI displays symbols on the relationship line.

You will see:

```text
Customer Dimension       Fact Table

      1  ───────────────  *
```

Where:

* `1` represents the **one side**
* `*` represents the **many side**

Therefore:

```text
Customer Dimension 1 ───── * Fact Table
```

The arrow indicates the direction in which filtering works.

Since the dimension table filters the fact table, the direction is:

```text
Customer Dimension → Fact Table
```

The lecture also points out that the asterisk appears near the fact table because the fact table is on the many side. 

---

# 11. Creating the Promotion–Fact Relationship

The next relationship is between:

* **Promotion Dimension**
* **Fact Table**

The common column is:

**Promotion ID**

Both tables contain `Promotion ID`. 

---

## Practical Steps

1. Locate `Promotion ID` in the **Promotion Dimension**.
2. Drag it onto `Promotion ID` in the **Fact Table**.
3. Power BI opens the relationship dialog.
4. Verify that `Promotion ID` is selected on both sides.
5. Set/verify **Cardinality = One-to-Many**.
6. Keep the **Promotion Dimension** on the one side.
7. Keep the **Fact Table** on the many side.
8. Set **Cross filter direction = Single**.
9. Ensure the relationship is active if required.
10. Click **Save**. 

---

# 12. Why Promotion Is One-to-Many

The relationship follows the same logic as Customer → Fact.

One promotion can be associated with multiple records in the fact table.

Therefore:

```text
Promotion Dimension  1 ───── * Fact Table
```

The filter direction is:

```text
Promotion Dimension
        ↓
   Fact Table
```

The Fact Table does not filter the Promotion Dimension under the **Single** filter direction. 

---

# 13. Creating the Product–Fact Relationship

The third relationship is between:

* **Product Dimension**
* **Fact Table**

The common column is:

**Product ID**

Both tables contain `Product ID`. 

---

## Practical Steps

1. Locate `Product ID` in the Product Dimension table.
2. Drag it onto `Product ID` in the Fact Table.
3. Power BI opens the relationship dialog.
4. Verify `Product ID` is selected in both tables.
5. Set/verify **Cardinality = One-to-Many**.
6. Product Dimension is the **one side**.
7. Fact Table is the **many side**.
8. Set **Cross filter direction = Single**.
9. Check **Make this relationship active**.
10. Click **Save**. 

---

# 14. Active vs Inactive Relationships

The lecture briefly introduces **inactive relationships**.

For the relationships created in this example, the relationships are made **active**.

The instructor mentions that inactive relationships will be discussed later in the same project. 

### Important distinction

**Active relationship:**

* Used by Power BI as the active/default relationship between the tables.

**Inactive relationship:**

* Exists in the model but isn't the active relationship being used by default.

The detailed handling of inactive relationships is outside this lecture.

---

# 15. Primary Key and Foreign Key in This Model

Now the lecture connects the relationship concepts back to **primary keys and foreign keys**.

---

## Product ID

In the **Product Dimension**:

```text
Product ID = Primary Key
```

In the **Fact Table**:

```text
Product ID = Foreign Key
```

Therefore:

```text
Product Dimension
Product ID (PK)
       |
       | 1:N
       ↓
Fact Table
Product ID (FK)
```



---

## Customer ID

In the **Customer Dimension**:

```text
Customer ID = Primary Key
```

In the **Fact Table**:

```text
Customer ID = Foreign Key
```

Therefore:

```text
Customer Dimension
Customer ID (PK)
       |
       | 1:N
       ↓
Fact Table
Customer ID (FK)
```



---

## Promotion ID

In the **Promotion Dimension**:

```text
Promotion ID = Primary Key
```

In the **Fact Table**:

```text
Promotion ID = Foreign Key
```

The transcript has a wording slip at this point, saying "product ID" while describing the fact-side key for promotion; based on the immediately preceding discussion and relationship creation, the intended fact-side key is **Promotion ID**. 

---

# 16. Overall Relationship Pattern

Every dimension table is connected to the fact table through its respective key.

```text
Customer Dimension
Customer ID (PK)
        |
        | 1 : N
        ↓
      Fact Table
Customer ID (FK)


Promotion Dimension
Promotion ID (PK)
        |
        | 1 : N
        ↓
      Fact Table
Promotion ID (FK)


Product Dimension
Product ID (PK)
        |
        | 1 : N
        ↓
      Fact Table
Product ID (FK)
```

Thus, every dimension–fact pair uses a **one-to-many relationship** based on the corresponding primary key and foreign key. 

---

# 17. Important: Data Types Must Match

The lecture then introduces another very important modeling rule:

> **The columns used to create a relationship between two tables should have the same data type.**

For example, if we are connecting:

```text
Customer Dimension[Customer ID]
          ↕
Fact Table[Customer ID]
```

both `Customer ID` columns should have the same data type. 

---

# 18. Checking Data Types in Power Query

The lecture demonstrates how to verify this.

### Step 1 — Open Power Query Editor

In Power BI:

**Home → Transform Data**

Clicking **Transform Data** opens the Power Query Editor. 

---

### Step 2 — Check Customer Dimension

Select the **Customer Dimension** table.

Locate:

**Customer ID**

The lecture observes that its data type is:

**Text**

---

### Step 3 — Check Fact Table

Select the **Fact Table**.

Locate:

**Customer ID**

The lecture observes that its data type is also:

**Text**. 

Therefore:

```text
Customer Dimension[Customer ID] → Text
Fact Table[Customer ID]         → Text
```

The data types match.

---

# 19. Why Matching Data Types Is Important

If the columns used for a relationship don't have compatible/same data types, you may not be able to create the **correct relationship** between the fact and dimension tables.

Therefore, before creating relationships:

1. Check the relationship columns.
2. Check their data types.
3. Make sure they match.
4. Then create the relationship. 

This is why data preparation and transformation are extremely important before modeling.

---

# 20. Importance of Data Preparation

The instructor emphasizes that data needs to be:

* Cleaned
* Prepared
* Structured

before it is used for:

* Data modeling
* Reporting

The reasoning is:

```text
Raw Data
   ↓
Clean Data
   ↓
Properly Structured Data
   ↓
Data Model
   ↓
Power BI Report
   ↓
Accurate Insights
```

If the data isn't properly prepared, creating accurate relationships and producing correct report insights becomes difficult. 

---

# 21. Power Query as the "Heart" of Power BI

The lecture refers to **Power Query as the heart of Power BI** because it allows you to perform different types of data transformations.

These transformations help prepare the data so that the final report can represent the correct insights.

Therefore, when creating Power BI reports, you should pay attention to both:

### 1. Data Preparation

Cleaning and transforming the source data.

### 2. Data Modeling

Creating appropriate tables and relationships.

Both are necessary for producing accurate reports. 

---

# 22. Returning to Model View

After checking the data types, the lecture returns to the model.

### Step

Click:

**Close & Apply**

This closes/applies the Power Query changes and returns to the Power BI model/report environment.

The lecture then views the model again. 

---

# 23. Final Star Schema

The final model represents a **Star Schema**.

It contains:

### Dimension Tables

1. **Product Dimension**
2. **Promotion Dimension**
3. **Customer Dimension**

### Fact Table

4. **Fact Table**

The Fact Table contains the sales/transaction data.

The three dimension tables are connected to it through relationships. 

Conceptually:

```text
                       Customer Dimension
                              |
                              |
                              | 1:N
                              ↓
Product Dimension ─────── Fact Table ─────── Promotion Dimension
       1:N                     ↑                    1:N
                               |
                               |
```

A cleaner representation:

```text
                    Customer Dimension
                            |
                            | 1 : N
                            ↓
Product Dimension ───→ Fact Table ←─── Promotion Dimension
      1 : N                                  1 : N
```

The arrangement forms the characteristic **star shape**.

---

# 24. Filter Direction in the Final Model

Each relationship has a **single cross-filter direction**.

Therefore, the general pattern is:

```text
Dimension
    ↓
Fact
```

For example:

```text
Customer Dimension
        ↓
     Fact Table
```

```text
Product Dimension
        ↓
     Fact Table
```

```text
Promotion Dimension
        ↓
     Fact Table
```

The arrows displayed in Model View indicate the direction in which filtering works. The lecture says this concept will be explored more deeply while building reports and using visuals. 

---

# 25. Complete Model Summary

The final model can be summarized as:

| Dimension           | Relationship Column | Fact Column       | Cardinality | Filter Direction |
| ------------------- | ------------------- | ----------------- | ----------- | ---------------- |
| Customer Dimension  | Customer ID (PK)    | Customer ID (FK)  | 1:N         | Dimension → Fact |
| Product Dimension   | Product ID (PK)     | Product ID (FK)   | 1:N         | Dimension → Fact |
| Promotion Dimension | Promotion ID (PK)   | Promotion ID (FK) | 1:N         | Dimension → Fact |

All three relationships created in this lecture are **active**.

---

# 26. Relationship Creation Checklist

When creating a relationship between a dimension and fact table, follow this sequence:

* [ ] Identify the common column.
* [ ] Confirm that the dimension-side column is the primary/unique key.
* [ ] Confirm that the fact-side column is the foreign key.
* [ ] Check that both columns have the same data type.
* [ ] Drag the dimension key onto the corresponding fact key.
* [ ] Verify the selected columns in the relationship dialog.
* [ ] Set **Cardinality = One-to-Many**.
* [ ] Set **Cross filter direction = Single**.
* [ ] Check **Make this relationship active** when you want it active.
* [ ] Click **Save**.
* [ ] Verify the `1` and `*` symbols in Model View.
* [ ] Verify the arrow/filter direction.

---

# 27. Important Concepts to Memorize

### Star Schema

A model consisting of a central fact table surrounded by dimension tables.

### Fact Table

Contains transaction/sales data.

### Dimension Table

Contains descriptive information such as:

* Customer details
* Product details
* Promotion details

### Primary Key

Unique key on the dimension side.

Examples:

```text
Customer Dimension → Customer ID
Product Dimension  → Product ID
Promotion Dimension → Promotion ID
```

### Foreign Key

Corresponding key in the fact table.

Examples:

```text
Fact → Customer ID
Fact → Product ID
Fact → Promotion ID
```

### Cardinality

For these dimension-to-fact relationships:

**1 : N (One-to-Many)**

### Cross Filter Direction

**Single**

Meaning:

**Dimension → Fact**

### Active Relationship

The relationship is actively used by Power BI.

Only **one active relationship can exist between a given pair of tables at a time**.

### Matching Data Types

The columns used to establish a relationship should have the **same data type**.

---

# 28. Complete Learning Flow From This Lecture

The entire practical process can be remembered as:

```text
Data Preparation
      ↓
Clean & Transform Data
      ↓
Identify Fact & Dimension Tables
      ↓
Identify Primary & Foreign Keys
      ↓
Check Data Types
      ↓
Open Model View
      ↓
Create Relationships
      ↓
Set Cardinality = 1:N
      ↓
Set Cross Filter = Single
      ↓
Make Relationship Active
      ↓
Save
      ↓
Verify 1 and * Symbols
      ↓
Final Star Schema
      ↓
Create Power BI Reports
```

The key lesson is that **data preparation and data modeling are foundational to accurate Power BI reporting**. Once the data is properly cleaned, structured, divided into fact/dimension tables, and connected through appropriate relationships, the model can be used to build reports and visuals with reliable insights. 
