# Power BI Reports vs Dashboards — Detailed Notes

## 1. Introduction

Power BI provides two important ways to present and analyze data:

1. **Power BI Reports**
2. **Power BI Dashboards**

Although both are used to represent insights and business information, they are different in terms of where they are created, their structure, and their purpose.

---

# 2. Power BI Reports

A **Power BI report** can be created in:

* **Power BI Desktop**
* **Power BI Service**

In the lecture example, the report was:

1. Created in **Power BI Desktop**.
2. Published to **Power BI Service**.

### Important characteristic

A report can contain:

* A **single page**, or
* **Multiple pages**

For example, a report could contain:

* Page 1 → Sales Analysis
* Page 2 → Profit Analysis
* Page 3 → Customer Analysis
* Page 4 → Product Analysis

Therefore:

> **A report can consist of one or multiple pages.**

---

# 3. Power BI Dashboards

A **Power BI dashboard** can be created in:

> **Power BI Service only**

Unlike reports, dashboards have only **one page**.

Therefore:

> **A dashboard is a single-page canvas containing important visualizations/tiles.**

A dashboard can bring together important visuals from different report pages.

---

# 4. Reports vs Dashboards — Quick Comparison

| Feature                                        | Report                 | Dashboard            |
| ---------------------------------------------- | ---------------------- | -------------------- |
| Created in Power BI Desktop                    | ✅ Yes                  | ❌ No                 |
| Created in Power BI Service                    | ✅ Yes                  | ✅ Yes                |
| Number of pages                                | One or multiple        | **Single page only** |
| Purpose                                        | Detailed analysis      | High-level overview  |
| Can contain visuals from multiple report pages | N/A                    | ✅ Yes                |
| Best for                                       | Detailed investigation | At-a-glance insights |

### Easy way to remember

**Report → Detailed Analysis**

**Dashboard → Important Information at a Glance**

---

# 5. Opening the Report in Power BI Service

The lecture demonstrates dashboard creation using an existing report.

The report was already created in Power BI Desktop and published to Power BI Service.

### Steps

1. Open **Power BI Service**.
2. At the top-right, click the account/profile option.
3. Click **View account** if required.
4. Navigate to **Workspaces**.
5. Open:

**Test Power BI Project Two**

6. Locate the published report.
7. Open the report.

The report in the example contains **two pages**.

---

# 6. Example Dashboard Requirement

Suppose the report contains:

### Page 1

Several card visuals, such as:

* Total Premium
* Another important KPI
* Claim Amount

### Page 2

A **table visual** containing additional important information.

The requirement is to create a dashboard containing:

* The first card visual from Page 1
* The second card visual from Page 1
* The Claim Amount card from Page 1
* The table visual from Page 2

This demonstrates one of the major advantages of dashboards:

> You can bring important visuals from different report pages onto a single dashboard.

---

# 7. Creating a Dashboard from Report Visuals

## Step 1: Go to Page 1

Open the first page of the report.

Locate the first card visual.

---

## Step 2: Pin the First Visual

Hover your mouse over the first card visual.

From the visual options:

**Click → Pin visual**

Power BI will ask where you want to pin the visual.

Select:

**New dashboard**

Give the dashboard a name.

In the lecture, the dashboard is named:

**Insurance**

Then pin the visual.

---

# 8. Pin the Second Card Visual

Now repeat the same process for the second card visual.

### Steps

1. Hover over the second card visual.
2. Click **Pin visual**.
3. Select:

**Existing dashboard**

4. Select the dashboard:

**Insurance**
5. Pin the visual.

The second visual is now added to the same dashboard.

---

# 9. Pin the Claim Amount Visual

Repeat the process for the Claim Amount card visual.

### Steps

1. Hover over the Claim Amount visual.
2. Click **Pin visual**.
3. Select **Existing dashboard**.
4. Select **Insurance**.
5. Pin the visual.

Now the dashboard contains three visuals from Page 1.

---

# 10. Pin a Visual from Another Report Page

Now go to:

**Page 2**

Locate the table visual that you want to include in the dashboard.

### Steps

1. Hover over the table visual.
2. Click **Pin visual**.
3. Select **Existing dashboard**.
4. Select:

**Insurance**
5. Pin the visual.

Now the dashboard contains:

* 3 card visuals from Page 1
* 1 table visual from Page 2

---

# 11. Viewing the Dashboard

After pinning the visuals:

1. Navigate to the **Insurance** dashboard.
2. You will see the four visuals displayed as separate **tiles**.

A dashboard is therefore composed of different tiles, where each tile represents a pinned visual/insight.

### In this example

The dashboard contains **four tiles**:

1. Card visual 1
2. Card visual 2
3. Claim Amount card
4. Table visual

---

# 12. Resizing Dashboard Tiles

The tiles on a dashboard are not fixed in size.

You can adjust them according to your requirements.

For example:

* Resize the first card.
* Resize the second card.
* Resize the third card.
* Resize the table.
* Increase the table's width/height if more information needs to be displayed.

### General process

Select/hover over the tile and use the available resizing controls to change its dimensions.

---

# 13. Repositioning Dashboard Tiles

You can also change the **position** of dashboard tiles.

For example, you can:

* Move one card to the top.
* Place another card next to it.
* Move the Claim Amount card somewhere else.
* Place the table below the cards.
* Arrange the tiles according to the importance of the information.

The objective is to create a dashboard layout that is easy to understand.

---

# 14. Why Do We Create Dashboards?

The primary purpose of a dashboard is to provide **important information at a glance**.

A user should be able to open the dashboard and quickly understand the most important business information without going through multiple report pages.

For example, management might immediately want to know:

* Revenue
* Profit
* Sales
* Quantity
* Claims
* Customer count
* Important KPIs

Instead of analyzing an entire report, they can look at the dashboard for a quick overview.

---

# 15. Dashboard vs Detailed Report Analysis

This is one of the most important concepts from the lecture.

### Dashboard

Used when the user wants to know:

> **"What is happening with the business right now?"**

It provides a quick, high-level overview.

### Report

Used when the user wants to know:

> **"Why is this happening?"**

It provides detailed analysis and allows the user to investigate the underlying information.

### Simple relationship

**Dashboard → Overview**

↓

**Report → Detailed Analysis**

---

# 16. Example: Business Owner and Regional Sales

Consider a practical business scenario.

You are a **Data Analyst**, and you have created a Power BI report for a business owner.

The report contains **four pages**:

1. East Region
2. West Region
3. North Region
4. South Region

Each page contains detailed information about the respective region.

The report may contain:

* Business activities
* KPIs
* Metrics
* Sales information
* Profitability information
* Product information
* Customer information
* Discount information
* Promotion information

---

# 17. Business Owner's Requirement

The business owner wakes up in the morning and wants to quickly understand the:

> **Overall health of the business**

He does not initially want to go through all four report pages.

Instead, he wants to know something simple:

> What is the net profit generated by each region?

---

# 18. Creating a Dashboard for the Business Owner

As the Data Analyst, you would create a dashboard containing the most important KPI:

**Net Profit**

You can take the relevant Net Profit visuals from the different report pages and place them on one dashboard.

The dashboard might show:

| Region | Net Profit |
| ------ | ---------: |
| East   |     Profit |
| West   |     Profit |
| North  |       Loss |
| South  |     Profit |

The business owner can immediately identify the overall situation.

---

# 19. Dashboard Helps Identify Problems Quickly

Suppose the business owner notices:

* East → Profit
* West → Profit
* South → Profit
* **North → Loss**

The dashboard immediately highlights that something is wrong with the North region.

Now the business owner wants to investigate:

> **Why is the North region making a loss?**

This is where the **report** becomes important.

---

# 20. Using the Report for Detailed Investigation

The business owner can go back to the detailed report and investigate questions such as:

### Product Analysis

* Which products were sold?
* Which products caused the loss?
* Are certain products generating negative margins?

### Customer Analysis

* Which customers were involved?
* Which customers contributed to the loss?

### Discount Analysis

* Were high discounts provided?
* Did excessive discount percentages reduce profitability?

### Promotion Analysis

* Which promotions were running?
* Did a particular promotion negatively affect profitability?

### Other Business Factors

The user can investigate the detailed information available across the report pages.

---

# 21. The Dashboard-to-Report Workflow

The scenario can be represented as:

**Open Dashboard**

↓

**Check Overall Business Health**

↓

**Identify an Issue**

↓

Example:

**North Region → Loss**

↓

**Open Detailed Report**

↓

**Investigate Products**

↓

**Investigate Customers**

↓

**Investigate Discounts**

↓

**Investigate Promotions**

↓

**Identify the Cause of the Loss**

This is a very common way in which dashboards and reports complement each other.

---

# 22. Reports Can Have Many Pages

A Power BI report does not have to contain only two or four pages.

A report can potentially contain:

* 20 pages
* 30 pages
* 50 pages
* Or many more pages depending on the reporting requirement.

As the number of pages increases, it becomes difficult for a business user to immediately identify the most important information.

This is another reason dashboards are useful.

---

# 23. Dashboard as a Summary of a Large Report

Suppose a report has **50 pages**.

Each page contains detailed analysis.

Instead of expecting the business owner to go through all 50 pages every morning, you can create a dashboard containing the most important:

* KPIs
* Metrics
* Business indicators
* Summary visuals

The dashboard becomes a **single-page summary of the most important information**.

The detailed report remains available whenever deeper analysis is required.

---

# 24. Sharing a Dashboard

Power BI Service also allows you to share a dashboard with colleagues.

To share the dashboard:

1. Open the dashboard.
2. Click **Share**.
3. Enter the email address of the colleague/user.
4. Configure the appropriate access options.
5. Click **Grant access**.

---

# 25. Dashboard Sharing Options

When sharing a dashboard, Power BI provides different options depending on what you want the recipient to do.

For example, you may want users to:

* Simply view/share the dashboard.
* Build content using the data associated with the dashboard.
* Receive access without necessarily sending an email notification.

The appropriate options can be selected according to the organization's requirements.

---

# 26. Important Point About Dashboard Sharing

When sharing a dashboard, you need to consider **what level of access the recipient should receive**.

You should not automatically give every user the ability to build or modify content if they only need to consume the dashboard.

Therefore, access should be granted according to the user's requirements and responsibilities.

---

# 27. Key Differences — Detailed Comparison

| Aspect                | Power BI Report                    | Power BI Dashboard                              |
| --------------------- | ---------------------------------- | ----------------------------------------------- |
| Creation              | Desktop + Service                  | Service only                                    |
| Pages                 | Single or multiple                 | Single page                                     |
| Main purpose          | Detailed analysis                  | High-level overview                             |
| Visual source         | Report visuals                     | Can contain pinned visuals                      |
| Multiple report pages | Can have multiple pages itself     | Can combine visuals from different report pages |
| Best suited for       | Analysis and investigation         | Monitoring important KPIs                       |
| Information level     | Detailed                           | Summary                                         |
| Business use          | Find/analyze details               | Understand situation quickly                    |
| Example               | Regional/product/customer analysis | Overall profit/sales KPI summary                |

---

# 28. Important Terminology

### Report

A collection of visualizations that can contain one or multiple pages and is used for detailed data analysis.

### Dashboard

A single-page collection of important visuals/tiles in Power BI Service used primarily for monitoring and high-level analysis.

### Tile

A visual element displayed on a Power BI dashboard.

When a report visual is pinned to a dashboard, it appears as a **tile**.

### Pin Visual

The action used to place a visual from a report onto a dashboard.

---

# 29. Practical Dashboard Creation Steps

Remember this workflow:

### Create Dashboard

**Power BI Service**

↓

**Open Workspace**

↓

**Open Report**

↓

**Open Report Page**

↓

**Hover over Visual**

↓

**Pin Visual**

↓

For the first visual:

**New Dashboard → Give Dashboard Name → Pin**

↓

For additional visuals:

**Pin Visual → Existing Dashboard → Select Dashboard → Pin**

↓

Repeat from other report pages

↓

**Open Dashboard**

↓

**Arrange Tiles**

↓

**Resize Tiles**

↓

**Reposition Tiles**

↓

**Share Dashboard if required**

---

# 30. Important Points to Remember

* **Reports can be created in Power BI Desktop and Power BI Service.**
* **Dashboards can be created only in Power BI Service.**
* A report can have **one or multiple pages**.
* A dashboard contains **only one page**.
* Dashboard visuals are displayed as **tiles**.
* You can pin visuals from different report pages to the same dashboard.
* A dashboard is primarily intended to provide **important information at a glance**.
* A report provides **detailed analysis**.
* If a dashboard highlights a problem, the user can go to the report to investigate the reason behind it.
* Dashboards are especially useful when a report has a large number of pages.
* Important KPIs and metrics from many report pages can be brought together on one dashboard.
* Dashboard tiles can be **resized and repositioned**.
* Dashboards can be **shared with colleagues** using the Share option.
* When sharing, access permissions should be configured according to what the recipient needs to do.

---

# 31. Easy Way to Remember

### **REPORT = Explore**

Use a report when you want to:

* Explore data
* Analyze details
* Investigate problems
* Understand why something happened

### **DASHBOARD = Monitor**

Use a dashboard when you want to:

* Monitor KPIs
* Get a quick overview
* Identify problems quickly
* Understand the overall health of the business

### Final Concept

> **Dashboard tells you WHAT is happening; the Report helps you understand WHY it is happening.**
