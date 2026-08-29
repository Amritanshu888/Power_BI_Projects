# Inventory Management Project with Power BI & Copilot — Detailed Notes

## 1. Project Overview

This project focuses on building an **Inventory Management dashboard using Microsoft Power BI**, with **Copilot in Microsoft Fabric** enabled.

The main objective is to understand how **AI/Copilot can assist in building a Power BI dashboard from scratch**, rather than following the traditional manual data analytics workflow.

### Technologies/Tools Used

* **Microsoft Power BI** — for creating the dashboard and reports.
* **Microsoft Fabric** — to enable and use Copilot capabilities.
* **Azure Portal** — to create the Fabric capacity required for Copilot.
* **Python/other data-cleaning tools** — discussed as part of the traditional approach, but **not used in this particular project**.
* **Zoho/Google Workspace + custom domain** — mentioned as possible ways to create an organizational email/account.

---

# 2. Traditional Data Analytics / BI Workflow

Normally, when working on a Power BI or data analytics project, the workflow looks something like this:

### Step 1 — Obtain the Data

Start with the raw dataset.

### Step 2 — Data Cleaning

The raw data usually needs to be cleaned before analysis.

Possible approaches include:

* Python
* Database-level data cleaning
* Excel
* Power BI's built-in data transformation capabilities
* Other ETL/data-cleaning tools

For a **portfolio project**, the instructor recommends using the different technology stacks that you have learned.

For example:

> Raw Data → Python Data Cleaning → Clean Dataset

### Step 3 — Exploratory Data Analysis (EDA)

Once the data has been cleaned, perform **EDA** to understand:

* The structure of the data
* Important patterns
* Trends
* Relationships
* Important metrics
* Potential KPIs
* Business problems/opportunities

EDA can also be performed using multiple tools.

### Step 4 — Identify Important KPIs

After understanding the data, determine:

* Which KPIs are important?
* Which metrics should appear on the dashboard?
* What information is useful to business users?
* What insights should decision-makers be able to obtain?

### Step 5 — Build the Dashboard

Finally, use the insights and identified KPIs to create the Power BI dashboard.

### Traditional Workflow Summary

**Raw Data → Data Cleaning → EDA → KPI Identification → Dashboard → Business Insights**

---

# 3. Approach Used in This Project

This project intentionally **skips the traditional Python-based data-cleaning and EDA workflow**.

Instead, the focus is on **leveraging AI to automate/report-assist the dashboard-building process**.

The idea is that AI can:

1. Understand the dataset.
2. Understand relationships within the data.
3. Analyze the available information.
4. Suggest relevant reports/visualizations.
5. Help generate reports automatically.

Therefore, the project is primarily focused on:

> **Automated reporting using Power BI + Microsoft Fabric Copilot**

### Alternative Approaches

If you don't want to use Copilot, you can:

* Follow the traditional approach without AI.
* Use AI tools for EDA.
* Use tools such as ChatGPT or Grok for analysis/vibe coding.

However, **this particular project concentrates mainly on automated reporting directly inside Power BI using Copilot**.

---

# 4. Understanding the Inventory Management Use Case

## What is Inventory Management?

Inventory management is a **systematic approach to sourcing, storing, and selling inventory**.

### What is Inventory?

Inventory can include:

* Raw materials
* Components
* Finished goods/products

Inventory management is particularly important in:

* Retail
* Manufacturing
* Other businesses that maintain physical stock

---

# 5. Why Inventory Management Is Important

For a business, it is important to have:

> **The right stock, at the right time, in the right quantity, and at the right cost.**

Poor inventory management can result in:

* Excess stock
* Stock shortages
* Increased costs
* Inventory losses
* Poor customer experience
* Reduced profitability

Therefore, an inventory management dashboard can help businesses monitor and optimize their inventory.

---

# 6. Objective of the Power BI Dashboard

The dashboard created in this project should provide a comprehensive view of inventory and sales performance.

It should help users analyze **products based on Cost of Goods Sold (COGS)** and gain a better understanding of overall product performance.

### Major objectives include:

### A. Product Analysis

Users should be able to analyze products based on:

* Cost of Goods Sold
* Sales/revenue-related information
* Product performance

### B. Inventory Visibility

The dashboard should provide visibility into inventory so that users can:

* Effectively manage stock
* Maintain optimal inventory levels
* Optimize inventory turnover
* Monitor inventory in real time

### C. Performance Analysis

The dashboard should help identify:

* High-performing indicators
* Low-performing indicators
* High-performing products/categories
* Low-performing products/categories

This allows business leaders to make better decisions.

### D. Loss Control

Insights from the dashboard can help leaders:

* Identify potential losses
* Control inventory-related losses
* Improve operational efficiency
* Increase profitability

---

# 7. Multi-Page Dashboard Concept

The final Power BI solution may contain **multiple report pages**.

A multi-page dashboard can provide a **bird's-eye view** of different aspects of the business.

Possible areas include:

* Categories
* Orders
* Out-of-stock levels
* In-hand inventory levels

These can potentially be analyzed across different time periods, such as:

* Days
* Months
* Quarters
* Years

The dashboard can therefore provide both:

**High-level business overview + detailed inventory analysis**

---

# 8. Dataset Used in the Project

The project uses a dataset containing **two sheets**.

The two sheets are:

1. **Sales Data**
2. **Inventory Stock Control**

---

# 9. Sheet 1 — Sales Data

The first sheet contains transactional sales information.

It includes details related to customer orders and sales transactions.

### Important columns mentioned in the lecture

* Customer Name
* Customer Type
* Customer Order details
* Order Date
* Product Code
* Order Quantity
* Unit Price
* Revenue
* Cost
* Other transactional information

### Purpose

The sales data can be used to understand:

* Customer orders
* Product sales
* Quantity sold
* Revenue
* Costs
* Product-level performance
* COGS-related analysis

---

# 10. Sheet 2 — Inventory Stock Control

The second sheet focuses on **inventory management and procurement planning**.

It contains information related to inventory and stock control.

### Columns mentioned include:

* Date of Last Order
* Item Name
* Vendor
* Stock
* Stock Location
* Other inventory-related fields

### Purpose

This data can be used to understand:

* Current inventory
* Stock availability
* Vendors
* Procurement requirements
* Stock locations
* Inventory management

---

# 11. First Step — Enable Copilot

The first practical step of the project is to **enable Copilot**.

The instructor assumes that you already have an **organizational account**.

---

# 12. Why an Organizational Account Is Required

According to the lecture, simply having a normal:

* Gmail account
* Outlook/personal email account

is not sufficient for the Azure Portal/Fabric setup being demonstrated.

The project therefore assumes that you have an **organization account**.

The instructor specifically mentions needing an organizational account to log into:

**Portal.azure.com**

---

# 13. Creating an Organizational Account Using a Custom Domain

The instructor describes one legitimate approach to creating an organizational account.

### Basic idea

Purchase a domain and then create an email address associated with that domain.

For example:

> `yourname.com`

Then create an email ID using that domain.

---

## Step 1 — Purchase a Domain

Domain providers mentioned in the lecture include:

* GoDaddy
* Hostinger

The instructor recommends trying to use **your own name** for the domain rather than randomly choosing a domain.

For example:

> If your name is XYZ, try looking for a domain based on your name.

The lecture demonstrates that an inexpensive domain may sometimes be available.

> **Important:** The exact domain pricing shown in the lecture is an example and can change over time.

---

## Step 2 — Create an Email ID

Once you own the domain, create an email address associated with that domain.

The instructor mentions services such as:

* Zoho
* Google Workspace (referred to as Google Suite in the lecture)

For example, conceptually:

> `name@yourdomain.com`

This becomes the organizational email/account used for the Azure/Fabric setup.

### Scope of the Lecture

The instructor explicitly says that **creating the organization account itself is outside the scope of this video**.

So the expectation is:

> **Before following the next steps, have your organizational account ready.**

---

# 14. Important Note About Account Creation

The instructor mentions that there are legitimate and illegitimate ways people may attempt to create organizational accounts.

The lecture focuses only on the **legitimate method using a domain and organizational email**.

The illegal methods are explicitly not discussed.

---

# 15. Log in to Azure Portal

Once the organizational account is ready:

### Step 1

Go to:

**Portal.azure.com**

### Step 2

Log in using the organizational account.

### Step 3

Search for:

**Azure Fabric**

The objective is to access the Fabric-related resources/capacity setup.

---

# 16. Create a Fabric Capacity

After accessing the Fabric-related area, create a **new capacity**.

The lecture demonstrates creating an Azure/Fabric capacity.

### Information required

The instructor shows fields such as:

* Azure Subscription
* Resource Group
* Capacity Name

---

## Step 1 — Select Azure Subscription

Choose the appropriate Azure subscription.

The lecture uses an Azure subscription as the starting point.

---

## Step 2 — Select/Create Resource Group

Choose or create a resource group.

In the demonstration, the instructor tries names such as:

* `test`
* `test new`

The exact name is not important.

The important point is to provide a valid resource group.

---

## Step 3 — Enter Capacity Name

Provide a name for the Fabric capacity.

For example:

> `test new`

Again, the exact name can be different.

---

# 17. Select F2 Capacity

One of the important steps in the demonstration is selecting the **F2 capacity**.

### Why?

The instructor specifically recommends:

> **Change the capacity to F2.**

This is done to avoid unnecessarily high costs while practicing.

### Practical Reminder

When working with Azure/Fabric resources, always pay attention to the selected capacity/SKU because it affects billing.

---

# 18. Azure Free Credits / Billing Warning

The instructor explains that when creating an Azure account for the first time and adding a credit card, Azure may provide promotional credits.

The lecture refers to approximately **₹20,000 worth of credits** as an example.

These credits can be used for practicing.

### Very Important

The instructor emphasizes:

> **Delete the Fabric capacity once the project is finished.**

Otherwise, the capacity can continue consuming Azure resources and potentially result in additional charges after available credits/promotions are exhausted.

### Best Practice

After completing the project:

**Stop/delete the capacity/resource as appropriate.**

Do not leave paid resources running unnecessarily.

---

# 19. Review and Create the Capacity

After selecting the appropriate capacity:

### Step 1

Select:

**Review + Create**

### Step 2

Review the configuration.

### Step 3

Accept the relevant terms/conditions if prompted.

### Step 4

Click:

**Create**

The Fabric capacity will then be provisioned.

---

# 20. Open Microsoft Fabric

Once the Fabric capacity has been created, go to the Microsoft Fabric web application.

The lecture refers to:

**app.fabric.microsoft.com**

Authenticate using the **same organizational user ID**.

The goal is to access the Fabric environment associated with the newly created capacity.

---

# 21. Enable Copilot in Fabric

Once inside Microsoft Fabric:

### Step 1

Open the relevant **Settings/Admin Portal** area.

### Step 2

Search for:

**Copilot**

### Step 3

Review the Copilot settings/options.

### Step 4

Enable the required Copilot options.

The instructor mentions enabling **all the relevant Copilot options** available in the environment.

> In the instructor's environment, Copilot is already enabled because it is used for other projects.

Therefore, the demonstration does not involve turning it on from scratch.

---

# 22. Enable Copilot in Power BI

Enabling Copilot in Fabric is not the only step.

You also need to check the settings in **Power BI**.

### Step 1

Open the Power BI application/web portal.

The lecture refers to:

**app.powerbi.com**

### Step 2

Go to the relevant settings/admin configuration.

### Step 3

Search for:

**Copilot**

### Step 4

If Copilot is disabled, enable the relevant settings.

Again, the instructor's environment already has Copilot activated.

---

# 23. Overall Setup Flow

The entire setup demonstrated in the lecture can be remembered as:

**Organizational Account**
↓
**Azure Portal**
↓
**Create Fabric Capacity**
↓
**Select F2 Capacity**
↓
**Review + Create**
↓
**Open Microsoft Fabric**
↓
**Enable Copilot**
↓
**Open Power BI**
↓
**Enable/Verify Copilot**
↓
**Start the Inventory Management Project**

---

# 24. Important Project Assumptions

Before starting the actual dashboard-building exercise, you should have:

* An organizational account
* Access to Azure
* An Azure subscription
* Required Azure/Fabric permissions
* A Fabric capacity
* F2 capacity selected for the demonstration
* Copilot enabled in Fabric
* Copilot enabled/available in Power BI
* The inventory management dataset

---

# 25. Business Requirements — Quick Revision

The dashboard should ultimately help answer questions around:

### Sales

* What products are being sold?
* How much revenue is being generated?
* What are the associated costs?
* What is the COGS?

### Inventory

* How much stock is available?
* Which items are out of stock?
* What inventory is currently in hand?
* Where is stock located?
* When was an item last ordered?
* Which vendors are involved?

### Performance

* Which products/categories are performing well?
* Which products/categories are performing poorly?
* What are the high-performance indicators?
* What are the low-performance indicators?

### Time Analysis

Information should potentially be analyzed by:

* Day
* Month
* Quarter
* Year

### Management Decision-Making

The dashboard should ultimately help leaders:

* Manage inventory effectively
* Maintain optimal stock
* Optimize inventory turnover
* Control losses
* Identify performance issues
* Make informed decisions
* Improve profitability

---

# 26. Traditional Approach vs. This Project

| Traditional BI Project              | This Project                                          |
| ----------------------------------- | ----------------------------------------------------- |
| Collect raw data                    | Collect dataset                                       |
| Clean data using Python/other tools | Skip traditional cleaning/EDA workflow                |
| Perform EDA                         | Leverage AI capabilities                              |
| Identify KPIs manually              | Copilot can assist with understanding/report creation |
| Design dashboard                    | Use Power BI + Copilot                                |
| Build visuals manually              | Focus on automated/AI-assisted reporting              |
| Generate insights                   | Use AI-assisted analysis                              |

### Key Idea

The purpose isn't to say that traditional data analytics is unnecessary.

Rather, this project is specifically designed to demonstrate:

> **How AI/Copilot can automate and accelerate the reporting/dashboard-building process in Power BI.**

---

# 27. Important Points to Remember

1. **Inventory management** deals with sourcing, storing, and selling inventory.
2. Inventory can consist of **raw materials, components, and finished goods**.
3. The project primarily targets **inventory/sales analysis for business decision-making**.
4. The dataset contains **two sheets**:

   * Sales Data
   * Inventory Stock Control
5. Sales data contains customer/order/product/revenue/cost information.
6. Inventory data contains stock/procurement/vendor/location information.
7. The project deliberately skips the traditional Python EDA workflow.
8. **Microsoft Fabric Copilot** is the primary AI capability being explored.
9. An **organizational account** is assumed to be available.
10. Azure Portal is used to create the Fabric capacity.
11. The lecture demonstrates selecting **F2 capacity**.
12. Be careful with Azure billing and **remove the capacity after completing the project**.
13. Copilot needs to be enabled/configured in **Fabric**.
14. Copilot availability/settings should also be checked in **Power BI**.
15. Once the setup is complete, the next stage is to open Power BI and start building the inventory management project.

---

## 28. One-Line Project Architecture

**Inventory/Sales Dataset → Microsoft Fabric + Copilot → Power BI → AI-Assisted Dashboard → Inventory & Business Insights → Better Decisions & Profitability**
