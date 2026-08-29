# Power BI End-to-End Project — Electro Hub: Project Introduction & Requirements

## 1. Project Overview

This lecture marks the beginning of the **first end-to-end Power BI project**.

The project is based on a fictional company called **Electro Hub**. The objective is to act as a **Data Analyst / Power BI Developer** and create a Power BI report that answers a set of business questions provided by the management.

### Your role

You are assumed to be working at Electro Hub as either:

* **Data Analyst**, or
* **Power BI Developer**

The management has provided a dataset and expects you to build a Power BI report that can answer specific business questions.

The report will eventually be used to support **business decision-making**.

---

# 2. Company Background — Electro Hub

**Electro Hub** is a company that operates a physical/offline store.

Customers visit the store and purchase different types of products.

The products sold by Electro Hub belong to different **product categories/product lines**.

### Product Categories

The company sells products belonging to the following categories:

1. **Electronics**
2. **Footwear**
3. **Clothing**
4. **Home Appliances**
5. **Accessories**
6. **Kitchenware**
7. **Bags**
8. **Personal Care**

> The exact products belonging to these categories will become clearer when the dataset and its individual tables are discussed in later lectures.

---

# 3. Overall Business Objective

The main objective of this project is to create an interactive **Power BI report/dashboard** that allows management to analyze:

* Sales
* Profit
* Quantity sold
* Discounts
* Net sales
* Orders
* Products
* Cities/geography
* Time-based sales trends

The report should not simply display data. It should help management **understand business performance and make decisions**.

---

# 4. Business Questions / Requirements

The report must answer **8 major requirements**.

---

## Requirement 1 — Top 5 and Bottom 5 Products

The report should identify the:

* **Top 5 products**
* **Bottom 5 products**

based on three different metrics:

### A. Sales

Identify:

* Top 5 products by sales
* Bottom 5 products by sales

### B. Profit

Identify:

* Top 5 products by profit
* Bottom 5 products by profit

### C. Quantity Sold

Identify:

* Top 5 products by quantity sold
* Bottom 5 products by quantity sold

### Example

Suppose Product A, B, C, D and E generate the highest sales.

The report should be able to display these as the **Top 5 products by Sales**.

Similarly, the five products having the lowest sales should be displayed as the **Bottom 5 products by Sales**.

The same analysis should be possible for:

* Profit
* Quantity sold

### Important concept

This requirement involves **ranking products** based on different numerical measures.

Eventually, Power BI can be used to create visuals showing these rankings.

---

# 5. Requirement 2 — Sales Trend Over Time

The report should show **how sales change over time**.

The analysis needs to be available at different time granularities:

* **Daily**
* **Monthly**
* **Quarterly**
* **Annually**

### Business question

> How does the sales trend vary over time?

For example, management should be able to understand:

* How much sales happened on a particular day?
* How sales changed month-by-month?
* How sales changed quarter-by-quarter?
* How sales changed year-by-year?

### Expected analysis

The report should allow the user to analyze the progression of sales across different periods.

A typical Power BI implementation could use a **time-series visual**, where the user can drill down through:

**Year → Quarter → Month → Day**

---

# 6. Requirement 3 — Relationship Between Sales and Profit

The report must show the **relationship between Sales and Profit**.

### Business question

> When sales increase, does profit also increase?

The analysis should help determine:

* Whether higher sales lead to higher profit
* Whether lower sales lead to lower profit
* Whether there are situations where sales increase but profit does not
* Whether there is a general relationship between sales and profit

### Example

Suppose:

|   Sales | Profit |
| ------: | -----: |
| ₹10,000 | ₹2,000 |
| ₹20,000 | ₹4,000 |
| ₹30,000 | ₹6,000 |

The report should help visualize whether a similar relationship exists in the actual dataset.

A suitable visualization for this type of analysis could be a **scatter plot**, although the exact visual will be decided during the implementation lectures.

---

# 7. Requirement 4 — Compare Two User-Selected Periods

The report should allow the user to select **two different periods/dates** and compare their performance.

The comparison should include:

* Sales
* Profit
* Quantity Sold

### Example

Suppose the user wants to compare:

**1 January 2022**

against

**1 January 2023**

The user should be able to select both dates/periods and see the corresponding:

* Sales
* Profit
* Quantity sold

### Key requirement

The comparison should be **dynamic**.

In other words, the user should not be restricted to one predefined comparison.

The user should be able to choose the two periods they want to compare.

This will likely require Power BI features such as:

* Date selection
* Slicers
* Measures
* Time-intelligence/comparison logic

The exact implementation will be covered in later lectures.

---

# 8. Requirement 5 — Average Discount by Discount Category

The report must contain a visual showing the:

> **Average discount offered for each discount category**

Different types of discounts may be offered to customers.

For example, discounts could be associated with:

* Festivals
* New Year
* Weekends
* Other promotional categories

The dataset will contain a **discount category** and a corresponding discount value.

### Required analysis

For every discount category, calculate:

**Average Discount**

### Example

| Discount Category | Average Discount |
| ----------------- | ---------------: |
| Festival          |              15% |
| New Year          |              20% |
| Weekend           |              10% |

The actual values will come from the dataset.

### Important distinction

The requirement is specifically asking for the **average discount**, not the total discount.

---

# 9. Requirement 6 — Total Number of Orders

The report must display the:

> **Total Number of Orders**

This is described as a relatively simple requirement.

A suitable Power BI implementation would typically involve a **Card visual** displaying the total number of orders.

For example:

**Total Orders: 12,450**

The actual value will depend on the dataset.

---

# 10. Requirement 7 — Detailed Order-Level Analysis with Filters

The report must allow users to see information for **individual orders**.

The available order-level information should include fields/measures such as:

* Sales
* Profit
* Discount
* Net Sales
* Other available fields/grains in the dataset

### Filtering requirement

Users should be able to use **visual filters** to filter the data.

For example, users may want to filter the report based on different fields and then examine:

* Sales
* Profit
* Discount
* Net Sales
* Other available attributes

### Key objective

The report should be interactive rather than static.

A user should be able to apply filters and dynamically see the corresponding data.

---

# 11. Requirement 8 — Sales by City

The final requirement is to show **sales geographically/by city**.

### Business question

> How much sales is generated by different cities?

The report should display:

**City → Sales**

### Example

| City      | Sales |
| --------- | ----: |
| Delhi     |    ₹X |
| Mumbai    |    ₹Y |
| Bengaluru |    ₹Z |

The actual cities and sales values will come from the dataset.

This analysis is useful for understanding **geographical sales performance**.

A suitable visualization could potentially be:

* Map
* Filled map
* Bar chart
* Column chart

depending on the data and implementation discussed later.

---

# 12. Complete Project Requirements at a Glance

| # | Requirement          | What the report should show                                               |
| - | -------------------- | ------------------------------------------------------------------------- |
| 1 | Top/Bottom Products  | Top 5 & Bottom 5 by Sales, Profit and Quantity Sold                       |
| 2 | Sales Trend          | Daily, Monthly, Quarterly and Annual sales trends                         |
| 3 | Sales vs Profit      | Relationship between Sales and Profit                                     |
| 4 | Period Comparison    | Compare Sales, Profit and Quantity Sold between two user-selected periods |
| 5 | Discount Analysis    | Average discount for each discount category                               |
| 6 | Total Orders         | Total number of orders                                                    |
| 7 | Order-Level Analysis | Sales, Profit, Discount, Net Sales and other fields with filters          |
| 8 | City Analysis        | Sales by different cities                                                 |

---

# 13. Why Are We Building This Report?

The Power BI report is not just for visualization.

The ultimate goal is to help **management make business decisions**.

### Example from the lecture

Suppose the report identifies the **five best-selling products**.

Management can then ask:

> Why are customers preferring these products?

Based on that information, management might decide to:

* Promote these products
* Offer discounts
* Increase marketing
* Increase inventory
* Focus promotional campaigns on these products

### Example decision-making flow

**Power BI Report**

↓

**Identify top-selling products**

↓

**Understand customer preferences**

↓

**Management analyzes opportunities**

↓

**Offer discounts/promotions**

↓

**Potentially increase sales**

This demonstrates the real purpose of business intelligence: **turning raw data into actionable business insights.**

---

# 14. Project Workflow

The lecture establishes the overall roadmap for the project.

### Step 1 — Understand the company

Understand Electro Hub and its business.

### Step 2 — Understand the dataset

The dataset will be provided.

Later lectures will explain:

* Tables
* Columns
* Data
* Product information
* Other available fields

### Step 3 — Import and work with the data in Power BI

The dataset will be brought into Power BI and analyzed.

### Step 4 — Build the required calculations

Create the required:

* Measures
* Calculations
* Rankings
* Comparisons
* Aggregations

### Step 5 — Create visuals

Build visuals capable of answering the eight business requirements.

### Step 6 — Add interactivity

Add things such as:

* Filters
* Slicers
* User selections
* Dynamic comparisons

### Step 7 — Validate the report

At the end of the project, return to the original list of requirements and verify:

> **Can the completed Power BI report answer every question?**

This is an important validation step.

---

# 15. Important Power BI Concepts Introduced

Although this lecture is primarily about project requirements, it introduces several concepts that will become important later.

### 1. Measures/metrics

The project repeatedly uses numerical business metrics such as:

* Sales
* Profit
* Quantity Sold
* Discount
* Net Sales
* Orders

### 2. Ranking

The Top 5/Bottom 5 requirement introduces the concept of **ranking products**.

### 3. Time-series analysis

Sales need to be analyzed at:

**Day → Month → Quarter → Year**

### 4. Relationships between measures

Sales and Profit need to be analyzed together.

### 5. Dynamic filtering

Users need to interact with the report and filter the data.

### 6. Period comparison

Two user-selected periods need to be compared dynamically.

### 7. Geographic analysis

Sales need to be analyzed by city.

---

# 16. Key Takeaways for Revision

* The project company is **Electro Hub**.
* Electro Hub operates a physical/offline store.
* Customers purchase products belonging to different product categories.
* The eight major product categories are:

  * Electronics
  * Footwear
  * Clothing
  * Home Appliances
  * Accessories
  * Kitchenware
  * Bags
  * Personal Care
* The project simulates the role of a **Data Analyst / Power BI Developer**.
* The Power BI report must answer **8 business requirements**.
* Top and Bottom 5 products must be analyzed by:

  * Sales
  * Profit
  * Quantity Sold
* Sales trends must be analyzed:

  * Daily
  * Monthly
  * Quarterly
  * Annually
* The report must show the relationship between **Sales and Profit**.
* Users must be able to compare **two selected periods** using:

  * Sales
  * Profit
  * Quantity Sold
* Average discount must be shown for every **discount category**.
* Total number of orders must be displayed.
* Users must be able to filter order-level information.
* Sales must be analyzed by **city**.
* The report's ultimate purpose is to support **business decisions**, not merely display data.
* At the end of the project, every original business requirement should be checked against the completed report to ensure that **all requirements have been satisfied**.
