# Power BI Project — Data Sources, Real-Time Scenarios & Dataset Understanding

## 1. Session Overview

This session introduces the **overall scenario of the Power BI project** before getting into the actual dataset and KPI creation.

The instructor first explains:

* Which data sources will be used.
* Why both SQL Server and MySQL are required.
* How a Power BI developer may need to move a report from a **test environment to a production environment**.
* How to handle a migration from **Microsoft SQL Server to MySQL**.
* The structure and meaning of the project's dataset.
* The KPIs that will eventually be created in the Power BI report.
* The software/tools required for the project.

---

# 2. Data Sources Used in the Project

Two database systems will be used as data sources:

1. **Microsoft SQL Server**
2. **MySQL Database**

The project deliberately uses both because the course wants to demonstrate scenarios that commonly occur in real-world Power BI development.

### Data-source flow

```text
Microsoft SQL Server
        +
MySQL Database
        ↓
     Power BI
        ↓
Power BI Report
```

---

# 3. Scenario 1 — Moving a Power BI Report from Test to Production

One of the major scenarios covered in this project is the movement of a Power BI report between different environments.

### Typical real-world situation

Suppose an organization has:

```text
TEST Environment
```

and

```text
PRODUCTION Environment
```

As a Power BI developer, you may initially build and test your report using data available in the **test environment**.

Once the report has been developed and validated, you may need to move it to the **production environment**.

### Typical workflow

```text
Test Environment
       ↓
Develop Power BI Report
       ↓
Test / Validate Report
       ↓
Move to Production
       ↓
Production Environment
```

---

## Why is this important?

In real-world projects, developers generally **do not directly develop against production data**.

Instead, development and testing are commonly performed against a test/development environment.

Once the report is ready, it is transitioned to production.

The course therefore demonstrates how this transition can be handled in Power BI.

---

# 4. Scenario 2 — Migrating from SQL Server to MySQL

Another important real-world scenario covered by the project is **changing the database technology used as the data source**.

For example, imagine that:

### Initially

The organization uses:

```text
Microsoft SQL Server
       ↓
Power BI Reports
```

Later, the organization decides to migrate to:

```text
MySQL
       ↓
Power BI Reports
```

As a Power BI developer or Data Analyst, you may be responsible for transitioning the existing reports to the new data source.

---

# 5. Why SQL Server → MySQL Migration Requires Care

Although both SQL Server and MySQL use SQL, their SQL syntax and database-specific features are **not always identical**.

Therefore, simply replacing one data source with another may not always be sufficient.

You need to carefully verify:

* SQL queries
* Table names
* Column names
* Data types
* Functions
* Calculations
* Filters
* Joins
* Result sets
* Overall report numbers

### Main objective

After migration:

> **The report should continue to provide the same accurate and appropriate insights as before.**

Conceptually:

```text
Before Migration

SQL Server
    ↓
Power BI
    ↓
Correct KPIs
    ↓
Correct Insights


After Migration

MySQL
    ↓
Power BI
    ↓
Correct KPIs
    ↓
Same / Expected Insights
```

The important point is that changing the underlying database should **not unintentionally change the business results**.

---

# 6. Role of a Power BI Developer / Data Analyst

During such a migration, the developer needs to ensure that the report continues to work correctly.

Important responsibilities include:

### 1. Transition the data source

Move from:

```text
SQL Server → MySQL
```

### 2. Handle syntax differences

Check whether SQL statements/functions used in the existing solution work correctly in MySQL.

### 3. Validate results

Compare the old and new results.

For example:

```text
SQL Server Result
       ↓
   KPI = 10,000

        VS

MySQL Result
       ↓
   KPI = 10,000
```

If the values differ, investigate why.

### 4. Preserve report accuracy

The final Power BI report must display:

* Correct numbers
* Correct insights
* Correct KPIs
* Appropriate results

---

# 7. Purpose of Including These Scenarios in the Project

The instructor emphasizes that these scenarios are included because they represent situations that a person may encounter while working as:

* **Data Analyst**
* **Power BI Developer**

The objective is therefore not merely to learn how to build a Power BI report.

The project is designed to provide exposure to **real-world Power BI development scenarios**.

The major scenarios are:

```text
Scenario 1
Test → Production


Scenario 2
SQL Server → MySQL
```

---

# 8. Understanding the Dataset

After discussing the scenarios, the instructor moves to the actual dataset.

The test environment contains a table referred to as the:

> **D&A table**

Here:

* **D = Demand**
* **A = Availability**

So the table represents:

> **Demand and Availability**

---

# 9. Demand & Availability Table

The table contains **four columns**.

The columns represent information about:

1. Order Date
2. Product ID
3. Availability
4. Demand

Let's understand each one.

---

# 10. Column 1 — Order Date

The **Order Date** represents the date on which a particular product was ordered.

For example:

| Order Date  |
| ----------- |
| 01-Jan-2026 |
| 02-Jan-2026 |
| 03-Jan-2026 |

Each date represents a particular day associated with an order.

---

# 11. Column 2 — Product ID

The **Product ID** identifies the product associated with the order.

For example:

| Product ID |
| ---------- |
| P101       |
| P102       |
| P103       |

The Product ID allows us to identify which product the demand and availability information belongs to.

---

# 12. Column 3 — Availability

The **Availability** column tells us:

> **The number of units of a particular product available in the store on a given date.**

For example:

| Order Date | Product ID | Availability |
| ---------- | ---------- | -----------: |
| 01-Jan     | P101       |          100 |

This means that on the given date, **100 units** of product P101 were available in the store.

---

# 13. Column 4 — Demand

The **Demand** column represents:

> **The total demand for the given product on a particular date.**

For example:

| Order Date | Product ID | Demand |
| ---------- | ---------- | -----: |
| 01-Jan     | P101       |     80 |

This means that customers demanded **80 units** of product P101 on that date.

---

# 14. Relationship Between Demand and Availability

The most important concept in this dataset is the comparison between:

```text
Demand
   VS
Availability
```

There are three possible situations.

---

## Case 1 — Availability = Demand

Example:

```text
Availability = 100
Demand       = 100
```

In this case:

> The entire customer demand can be fulfilled.

There is no shortage.

### Interpretation

```text
Demand       = 100
Availability = 100
Shortage     = 0
```

---

# 15. Case 2 — Availability > Demand

Example:

```text
Availability = 150
Demand       = 100
```

There are more units available than customers demand.

Therefore:

> The entire demand can be fulfilled.

There is no demand shortage.

The remaining inventory is:

```text
Availability - Demand
= 150 - 100
= 50 units
```

So:

```text
Demand       = 100
Availability = 150
Surplus      = 50
```

---

# 16. Case 3 — Demand > Availability

This is the important/problematic situation.

Example:

```text
Demand       = 150
Availability = 100
```

Customers want:

```text
150 units
```

but only:

```text
100 units
```

are available.

Therefore, the store cannot fulfill the entire demand.

The shortage is:

```text
Demand - Availability
= 150 - 100
= 50 units
```

### Interpretation

```text
Demand       = 150
Availability = 100
Shortage     = 50
```

This is concerning from a business perspective because the company/store is unable to fulfill customer requirements because the product is unavailable in sufficient quantity.

---

# 17. Business Logic of Demand vs Availability

The basic business logic can be summarized as:

| Condition             | Meaning                      | Demand Fulfilled? |
| --------------------- | ---------------------------- | ----------------- |
| Availability = Demand | Exactly enough inventory     | Yes               |
| Availability > Demand | More inventory than required | Yes               |
| Demand > Availability | Insufficient inventory       | **No**            |

A useful way to visualize this is:

```text
              Compare
          Demand vs Availability
                  │
        ┌─────────┴─────────┐
        ↓                   ↓
 Availability >= Demand   Demand > Availability
        ↓                   ↓
   Demand fulfilled       Shortage
                            ↓
                     Customer requirement
                      cannot be fulfilled
```

---

# 18. Why Demand and Availability Matter for the Report

The business wants to understand how effectively it is meeting customer demand.

Therefore, the Power BI report will contain KPIs related to:

* Demand
* Availability
* Supply shortage
* Loss
* Profit

These KPIs can help the business understand the impact of inventory availability on sales and profitability.

---

# 19. Products Table

Apart from the Demand & Availability table, another table is available:

> **Products table**

The Products table contains information about the products.

It contains **three columns**.

---

# 20. Column 1 — Product ID

The first column contains the:

> **Product ID**

This ID uniquely identifies a particular product.

For example:

| Product ID |
| ---------- |
| P101       |
| P102       |
| P103       |

The Product ID is particularly important because it can be used to associate product information with the Demand & Availability table.

---

# 21. Column 2 — Product Name

The second column contains:

> **Product Name**

This provides the actual name of the product.

Example:

| Product ID | Product Name |
| ---------- | ------------ |
| P101       | Product A    |
| P102       | Product B    |

---

# 22. Column 3 — Unit Price

The third column contains:

> **Unit Price**

This represents the price associated with one unit of the product.

For example:

| Product ID | Product Name | Unit Price |
| ---------- | ------------ | ---------: |
| P101       | Product A    |       ₹100 |
| P102       | Product B    |       ₹150 |

The Unit Price becomes important later when calculating financial metrics such as **profit and loss**.

---

# 23. Products Table Structure

The Products table can therefore be represented as:

```text
Products
│
├── Product ID
├── Product Name
└── Unit Price
```

The important relationship is:

```text
D&A Table
    │
    │ Product ID
    ↓
Products Table
```

The Product ID provides the common product identifier between the datasets.

---

# 24. Power BI Report Requirements

The project requires creating a **two-page Power BI report**.

There are different KPIs that need to be represented on the two pages.

---

# 25. Page 1 KPIs

The **first page** should represent three KPIs.

### KPI 1 — Average Demand per Day

This KPI should show the:

> **Average demand per day**

It helps understand the typical daily demand level.

---

### KPI 2 — Average Availability per Day

This KPI should show:

> **Average availability per day**

It helps understand the typical number of units available on a daily basis.

---

### KPI 3 — Total Supply Shortage

This KPI represents:

> **Total supply shortage**

This is particularly important because it captures situations where:

```text
Demand > Availability
```

The shortage essentially represents the amount of demand that could not be fulfilled because there wasn't enough product available.

---

## Page 1 Summary

```text
PAGE 1
──────────────────────────────
Average Demand per Day

Average Availability per Day

Total Supply Shortage
──────────────────────────────
```

---

# 26. Page 2 KPIs

The **second page** should contain three additional KPIs.

### KPI 1 — Total Loss

Represents the total loss associated with the business scenario.

The exact calculation will be discussed in the upcoming sessions.

---

### KPI 2 — Total Profit

Represents the overall profit.

The Products table's **Unit Price** and the Demand/Availability information will be relevant when calculating financial metrics.

---

### KPI 3 — Average Daily Loss

Represents:

> **Average loss per day**

This helps the business understand the typical daily financial impact.

---

## Page 2 Summary

```text
PAGE 2
──────────────────────────────
Total Loss

Total Profit

Average Daily Loss
──────────────────────────────
```

---

# 27. Overall Dataset Structure

The project essentially works with two main tables.

### Table 1 — Demand & Availability

```text
D&A
│
├── Order Date
├── Product ID
├── Availability
└── Demand
```

### Table 2 — Products

```text
Products
│
├── Product ID
├── Product Name
└── Unit Price
```

---

# 28. Conceptual Data Model

The two tables can conceptually be connected through `Product ID`.

```text
          PRODUCTS
┌────────────────────────┐
│ Product ID              │
│ Product Name            │
│ Unit Price               │
└───────────┬────────────┘
            │
       Product ID
            │
            ↓
┌────────────────────────┐
│ D&A                     │
│ Order Date              │
│ Product ID              │
│ Availability             │
│ Demand                   │
└────────────────────────┘
```

This relationship will become important when building the Power BI data model.

---

# 29. Business Scenario in One Example

Suppose we have:

| Date  | Product | Availability | Demand |
| ----- | ------- | -----------: | -----: |
| Day 1 | P101    |          100 |     80 |
| Day 2 | P101    |          100 |    100 |
| Day 3 | P101    |          100 |    130 |

### Day 1

```text
Availability = 100
Demand       = 80
```

Demand is fully satisfied, with 20 units remaining.

### Day 2

```text
Availability = 100
Demand       = 100
```

Demand is exactly satisfied.

### Day 3

```text
Availability = 100
Demand       = 130
```

Demand exceeds availability.

Therefore:

```text
Shortage = 130 - 100
         = 30 units
```

The third day contributes to the **supply shortage**.

This type of business logic will ultimately be reflected in the Power BI KPIs.

---

# 30. Software Required for the Project

The instructor emphasizes that two database tools will be required.

### 1. MySQL Workbench

This was covered in the previous session.

It will be used to work with the **MySQL database**.

```text
MySQL Database
      ↕
MySQL Workbench
```

---

### 2. SQL Server Management Studio (SSMS)

The project will also use **Microsoft SQL Server**.

Therefore, you need:

> **SQL Server Management Studio (SSMS)**

to work with the SQL Server database.

```text
SQL Server
     ↕
SSMS
```

---

# 31. If SQL Server Is Not Installed

The instructor explains that if you already know how to download and install SQL Server, you can set it up yourself.

If you don't know how to install it:

* There is another project in the course that uses **Microsoft SQL Server as the data source**.
* That section contains a video explaining how to download and install SQL Server.
* You can refer to that video to complete the SQL Server setup.

---

# 32. MySQL Installation in This Project

For MySQL, the instructor says that the current project itself contains the relevant video for:

> **Downloading and installing MySQL Workbench.**

Therefore, both tools will be used throughout the project:

```text
SQL Server + SSMS
        +
MySQL + MySQL Workbench
        ↓
      Power BI
```

---

# 33. End-to-End Project Flow

The overall project can now be understood as follows:

```text
                    PROJECT
                       │
          ┌────────────┴────────────┐
          ↓                         ↓
   SQL Server                    MySQL
      │                             │
      ↓                             ↓
     SSMS                    MySQL Workbench
          │                         │
          └────────────┬────────────┘
                       ↓
                    Power BI
                       ↓
                Build the Report
                       ↓
             Test Environment
                       ↓
                 Validate Results
                       ↓
              Production Environment
```

The project also demonstrates the migration scenario:

```text
SQL Server
    ↓
Existing Power BI Report
    ↓
Organization migrates database
    ↓
MySQL
    ↓
Transition Power BI Report
    ↓
Validate Results
```

---

# 34. Important Points to Remember

### Data Sources

The project uses:

* **Microsoft SQL Server**
* **MySQL**

---

### Real-World Scenario 1

Power BI report needs to be moved:

**Test → Production**

---

### Real-World Scenario 2

Data source needs to be migrated:

**SQL Server → MySQL**

---

### Migration Challenge

SQL Server and MySQL may have differences in SQL syntax and functionality.

Therefore, after migration, you must validate the report carefully.

---

### D&A Table

D&A stands for:

**Demand & Availability**

Contains:

* Order Date
* Product ID
* Availability
* Demand

---

### Products Table

Contains:

* Product ID
* Product Name
* Unit Price

---

### Important Business Rule

```text
Availability >= Demand
        ↓
Demand fulfilled


Demand > Availability
        ↓
Demand not completely fulfilled
        ↓
Supply shortage
```

---

# 35. KPI Requirements — Quick Revision

## Page 1

| KPI                              | Purpose                                                        |
| -------------------------------- | -------------------------------------------------------------- |
| **Average Demand per Day**       | Understand average daily customer demand                       |
| **Average Availability per Day** | Understand average daily product availability                  |
| **Total Supply Shortage**        | Measure unfulfilled demand caused by insufficient availability |

## Page 2

| KPI                    | Purpose                                |
| ---------------------- | -------------------------------------- |
| **Total Loss**         | Measure overall loss                   |
| **Total Profit**       | Measure overall profit                 |
| **Average Daily Loss** | Measure average financial loss per day |

---

# 36. What Will Be Done in Upcoming Sessions?

The current session is primarily an **introduction and dataset-understanding session**.

The instructor indicates that the detailed discussion/calculation of the KPIs will happen in upcoming sessions.

The project will eventually cover:

1. Understanding the dataset.
2. Working with SQL Server.
3. Working with MySQL.
4. Creating the Power BI report.
5. Calculating the required KPIs.
6. Handling the **test → production** scenario.
7. Handling the **SQL Server → MySQL** transition.
8. Validating that the migrated report continues to produce correct results.

---

## ⭐ Final Mental Model

The most important thing to understand from this lecture is that this isn't simply a **"build a Power BI dashboard"** project.

It is designed around a **real-world data analytics workflow**:

```text
                    BUSINESS DATA
                         │
             ┌───────────┴───────────┐
             ↓                       ↓
        SQL Server                 MySQL
             │                       │
             └───────────┬───────────┘
                         ↓
                       Power BI
                         ↓
                  Test Environment
                         ↓
                 Build + Validate
                         ↓
                 Production Report
```

And the business problem revolves around:

```text
Demand vs Availability
         ↓
Can customer demand be fulfilled?
         ↓
If not → Supply Shortage
         ↓
Impact on Loss / Profit
         ↓
Power BI KPIs & Report
```

**Core takeaway:** The project teaches both **Power BI reporting** and the kind of **data-source/environment transition scenarios** a Power BI Developer or Data Analyst may encounter in a real organization.
