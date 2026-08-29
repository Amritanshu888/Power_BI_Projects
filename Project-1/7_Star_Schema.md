# Power BI Data Modeling — Star Schema

These notes are based directly on the provided lecture transcript. The lecture explains **Star Schema**, why it is used in Power BI, the difference between **Fact and Dimension tables**, and how splitting duplicated data into separate tables can reduce model size and improve report performance. 

---

## 1. What is Star Schema?

A **Star Schema** is a way of organizing different tables in a dataset so that **redundancy/duplication in the data is reduced**. 

The main benefits mentioned in the lecture are:

1. Reduces data redundancy/duplication.
2. Reduces the size of the Power BI data model.
3. Improves report performance.
4. Ultimately enhances the user experience. 

### Basic idea

Instead of keeping all information in one large table, we organize the data into different related tables.

The arrangement generally looks like a **star**, which is why it is called a **Star Schema**. 

---

# 2. Components of a Star Schema

A Star Schema consists primarily of:

* **Fact Table**
* **Dimension Tables**

The lecture represents the structure as:

```text
                 Dimension 1
                      |
                      |
Dimension 2 —— Fact Table —— Dimension 3
                      |
                      |
                 Dimension 4
                      |
                 Dimension 5
```

The **Fact Table** is at the center, while multiple **Dimension Tables** surround it.

Because this arrangement visually resembles a star, it is called a **Star Schema**. 

---

# 3. Fact Table

A **Fact Table** generally contains:

* Transaction data
* Sales data

In other words, the fact table contains the actual business events or transactions that are being analyzed. 

### Example

For a sales dataset, the fact table might contain:

| Order ID | Product | Customer ID |  Sales |
| -------- | ------- | ----------- | -----: |
| 1        | X       | A01         |   ₹700 |
| 2        | Y       | A01         | ₹1,000 |
| 3        | M       | A02         |   ₹800 |
| 4        | X       | A02         |   ₹700 |
| 5        | Y       | A02         | ₹1,700 |

These are transactional records.

---

# 4. Dimension Table

A **Dimension Table** contains information or attributes describing a particular entity.

The lecture emphasizes that dimension tables **do not contain the sales/transaction data**. Instead, they contain information about the data. 

For example, customer information can be kept in a Customer Dimension table:

| Customer ID | Customer Name | Customer Number | Customer Email                    |
| ----------- | ------------- | --------------- | --------------------------------- |
| A01         | Nithin        | 789             | [N@gmail.com](mailto:N@gmail.com) |
| A02         | Raj           | 834             | [R@gmail.com](mailto:R@gmail.com) |

The dimension table provides descriptive information about customers.

---

# 5. Fact Table vs Dimension Table

| Fact Table                             | Dimension Table                                           |
| -------------------------------------- | --------------------------------------------------------- |
| Contains transactions/sales data       | Contains descriptive information                          |
| Generally updated frequently           | Updated less frequently                                   |
| New transactions continuously arrive   | Customer/product information doesn't change as frequently |
| Usually contains many records          | Usually contains fewer records                            |
| Located at the center of a star schema | Surrounds the fact table                                  |

The lecture specifically points out that the **fact table is updated more frequently** because new transactions/sales keep arriving. Dimension tables can also be updated, but generally at a lower frequency. 

---

# 6. Why Do We Need Star Schema?

The main problem being solved is **data duplication/redundancy**.

The lecture uses a sales dataset to demonstrate this.

Initially, imagine that we have **one large table** containing both transaction information and customer information.

---

# 7. Initial Sales Dataset

Suppose our table contains these columns:

* Order ID
* Product
* Customer ID
* Customer Name
* Customer Number
* Customer Email
* Sales

The `Customer ID` identifies the customer who made the purchase. 

Example:

| Order ID | Product | Customer ID | Customer Name | Phone | Email                             |  Sales |
| -------: | ------- | ----------- | ------------- | ----- | --------------------------------- | -----: |
|        1 | X       | A01         | Nithin        | 789   | [N@gmail.com](mailto:N@gmail.com) |   ₹700 |
|        2 | Y       | A01         | Nithin        | 789   | [N@gmail.com](mailto:N@gmail.com) | ₹1,000 |
|        3 | M       | A02         | Raj           | 834   | [R@gmail.com](mailto:R@gmail.com) |   ₹800 |
|        4 | X       | A02         | Raj           | 834   | [R@gmail.com](mailto:R@gmail.com) |   ₹700 |
|        5 | Y       | A02         | Raj           | 834   | [R@gmail.com](mailto:R@gmail.com) | ₹1,700 |

This is the basic example constructed in the lecture. 

---

# 8. Problem: Customer Information Is Repeated

Look at customer **A01**.

A01 made two purchases:

* Order ID 1
* Order ID 2

The following information remains exactly the same:

```text
Customer ID   → A01
Customer Name → Nithin
Phone         → 789
Email         → N@gmail.com
```

Only the transaction-specific information changes:

```text
Order ID
Product
Sales
```

Therefore, customer information is being duplicated. 

---

# 9. Example of Increasing Duplication

Suppose customer **A01** purchases **10 different products through 10 different orders**.

The customer information:

```text
A01
Nithin
789
N@gmail.com
```

would have to be repeated **10 times** in the original table.

The lecture highlights this as redundant data. 

The same problem occurs with customer **A02**.

A02 makes three purchases:

* Order ID 3
* Order ID 4
* Order ID 5

But the following information gets repeated:

```text
A02
Raj
834
R@gmail.com
```

Again, this is redundant/duplicated information. 

---

# 10. Why Is Redundancy a Problem?

If a dataset contains a very large number of transactions and customers, this duplication can become substantial.

For example:

```text
1 customer
   ↓
10 transactions
   ↓
Customer details repeated 10 times
```

With thousands or millions of transactions, customer information can be repeated many times.

This increases the amount of data stored in the Power BI model.

Therefore:

**More duplication → Larger model → Potentially poorer performance**

The objective is therefore to organize the data differently so that unnecessary repetition is reduced. 

---

# 11. Solution — Split the Data Into Two Tables

The lecture then restructures the original table into **two separate tables**.

### Table 1

Stores:

> **Customer details**

### Table 2

Stores:

> **Sales/transaction details**

This is the key step used to reduce redundancy. 

---

# 12. Step 1 — Create the Customer Table

Create a table containing customer information.

The lecture uses these columns:

* Customer ID
* Customer Name
* Customer Number
* Customer Email

Example:

| Customer ID | Customer Name | Customer Number | Customer Email                    |
| ----------- | ------------- | --------------- | --------------------------------- |
| A01         | Nithin        | 789             | [N@gmail.com](mailto:N@gmail.com) |
| A02         | Raj           | 834             | [R@gmail.com](mailto:R@gmail.com) |

Notice what happened:

Instead of storing Nithin's details every time he makes a purchase, we store his information **only once**.

Similarly, Raj's information is stored only once. 

---

# 13. Step 2 — Create the Sales Table

Now create another table containing the transaction information.

The lecture uses:

* Sales
* Order ID
* Product
* Customer ID

Example:

|  Sales | Order ID | Product | Customer ID |
| -----: | -------: | ------- | ----------- |
|   ₹700 |        1 | X       | A01         |
| ₹1,000 |        2 | Y       | A01         |
|   ₹800 |        3 | M       | A02         |
|   ₹700 |        4 | X       | A02         |
| ₹1,700 |        5 | Y       | A02         |

The important addition here is **Customer ID**.

Why?

Because Customer ID will allow the Sales table to connect back to the Customer table. 

---

# 14. Step 3 — Create the Relationship Between the Tables

Now both tables have a common column:

```text
Customer ID
```

### Customer Table

```text
Customer ID
A01
A02
```

### Sales Table

```text
Customer ID
A01
A01
A02
A02
A02
```

Therefore, these two tables can be connected through:

**Customer ID**

The lecture explicitly describes creating a relationship using this common column. 

Conceptually:

```text
Customer Dimension
──────────────────
Customer ID
Customer Name
Customer Number
Customer Email
       |
       | Customer ID
       |
       ↓
Sales Fact
──────────────────
Customer ID
Order ID
Product
Sales
```

---

# 15. Which Table Becomes the Dimension Table?

The table containing customer information becomes the:

## Dimension Table

It contains:

```text
Customer ID
Customer Name
Customer Number
Customer Email
```

The lecture explicitly identifies this first table as the **Dimension Table**. 

---

# 16. Which Table Becomes the Fact Table?

The table containing sales and transaction information becomes the:

## Fact Table

It contains:

```text
Sales
Order ID
Product
Customer ID
```

The lecture identifies this second table as the **Fact Table**. 

---

# 17. What Did We Achieve?

Before restructuring, the customer information was repeated for every transaction.

For example:

```text
A01 | Nithin | 789 | N@gmail.com
A01 | Nithin | 789 | N@gmail.com
```

After restructuring:

### Customer Dimension

```text
A01 | Nithin | 789 | N@gmail.com
```

Only one copy is required.

The Sales table only stores:

```text
A01
A01
```

as references to the customer.

Therefore, we have significantly reduced unnecessary duplication. 

---

# 18. Why This Becomes More Important With Large Data

The example contains only:

* 2 customers
* 5 transactions

But real-world datasets can contain:

* Thousands of customers
* Millions of transactions
* Many products
* Many orders
* Many other attributes

Imagine one customer makes hundreds of purchases.

If all customer information is stored in every transaction row, the same information gets duplicated hundreds of times.

The lecture emphasizes that this example is only a simplified demonstration; in real scenarios there can be a **large number of transactions performed by many customers**. 

---

# 19. Benefits of This Arrangement

By organizing data into fact and dimension tables:

### 1. Less duplication

Customer information is stored once instead of repeatedly.

### 2. Smaller data model

Less redundant data means less data needs to be stored in the Power BI model.

### 3. Better report performance

A smaller model can help improve report performance.

### 4. Better user experience

Improved report performance ultimately provides a better experience for users. 

---

# 20. There Can Be Multiple Dimension Tables

The example only creates **one dimension table** — the Customer table.

However, a real Power BI model can have multiple dimension tables.

For example:

```text
                  Customer
                     |
                     |
Product ─────── Fact Sales ─────── Date
                     |
                     |
                  Geography
```

The lecture emphasizes that there can be **more than one dimension table** and that additional duplicated information can be separated in a similar manner. 

---

# 21. Overall Star Schema Structure

Putting everything together:

```text
                     Customer
                         |
                         |
Product ─────────── Fact Sales ─────────── Date
                         |
                         |
                    Other Dimensions
```

The **Fact Table** sits in the center.

The **Dimension Tables** surround it.

This creates the star-like structure.

---

# 22. End-to-End Process

The lecture's approach can be remembered as the following sequence:

### Step 1 — Identify redundant data

Look for information that is repeated across many transaction records.

Example:

```text
Customer ID
Customer Name
Phone
Email
```

being repeated for every purchase.

### Step 2 — Separate descriptive information

Create a separate table for customer information.

```text
Customer Dimension
```

### Step 3 — Keep transaction information separately

Create a table for:

```text
Sales
Orders
Products purchased
```

### Step 4 — Keep a common key

Keep `Customer ID` in both tables.

### Step 5 — Create a relationship

Connect the two tables using:

```text
Customer ID
```

### Step 6 — Use the model for reporting

Power BI can then use the related fact and dimension tables for report creation and analysis.

This overall organization is the Star Schema approach described in the lecture. 

---

# 23. Important Terminology

| Term                   | Meaning                                                 |
| ---------------------- | ------------------------------------------------------- |
| **Star Schema**        | A way of organizing data into fact and dimension tables |
| **Fact Table**         | Contains transaction/sales data                         |
| **Dimension Table**    | Contains descriptive information about entities         |
| **Redundancy**         | Unnecessary repetition of the same information          |
| **Customer ID**        | Common key used to relate customer and sales data       |
| **Model Size**         | Amount of data stored in the Power BI model             |
| **Report Performance** | How efficiently the Power BI report works               |

---

# 24. Key Example to Remember

### Before Star Schema

One large table:

```text
Order ID
Product
Customer ID
Customer Name
Customer Number
Customer Email
Sales
```

Problem:

```text
Customer details
       ↓
Repeated for every transaction
       ↓
Redundancy
       ↓
Larger model
```

### After Star Schema

**Customer Dimension**

```text
Customer ID
Customer Name
Customer Number
Customer Email
```

**Sales Fact**

```text
Order ID
Product
Customer ID
Sales
```

Connected using:

```text
Customer ID
```

Result:

```text
Less redundancy
      ↓
Smaller model
      ↓
Better performance
      ↓
Better user experience
```

---

# 25. Most Important Points for Revision

* **Star Schema** is a method of organizing tables to reduce redundancy/duplication.
* Reducing redundancy helps reduce the **Power BI model size**.
* A smaller model can improve **report performance** and user experience.
* Star Schema consists of **Fact Tables and Dimension Tables**.
* The **Fact Table** generally contains sales/transaction data.
* The **Dimension Table** contains descriptive information.
* Fact tables are generally updated more frequently because new transactions keep arriving.
* Dimension tables can also change, but generally less frequently.
* Storing customer details alongside every transaction creates unnecessary duplication.
* To solve this, separate customer information into a **Customer Dimension**.
* Keep transaction information in a **Sales Fact**.
* Keep the common `Customer ID` in both tables.
* Create a relationship between the two tables using `Customer ID`.
* The customer table becomes the **Dimension Table**.
* The sales/transaction table becomes the **Fact Table**.
* A real model can contain **multiple dimension tables**.
* The final arrangement of fact and dimension tables forms the **Star Schema** used for Power BI reporting. 
