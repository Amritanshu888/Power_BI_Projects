# Power BI End-to-End Project — Electro Hub

## Lecture 2: Dataset Import, Power BI Views & Power Query Introduction

This lecture focuses on **bringing the Electro Hub dataset into Power BI Desktop** and getting familiar with the initial data preparation workflow.

The key idea is:

> **Before creating any report, you must first understand, clean, prepare, and structure the data.**

---

# 1. Starting Power BI Desktop

The first step is to open **Power BI Desktop**.

### Steps

1. Open **Power BI Desktop**.
2. Wait for Power BI Desktop to load.
3. Select **Blank Report**.

At this stage, signing in is **not required** for this project.

---

# 2. Understanding the Power BI Desktop Report View

After opening the blank report, you are initially taken to the **Report View**.

On the left side of Power BI Desktop, there is a navigation pane containing different views.

If you hover over the first option, Power BI displays:

> **Report view**

This is the main area where reports and visualizations will eventually be created.

---

# 3. Important Panes in Report View

On the right-hand side, Power BI Desktop provides three important panes:

### 1. Filters Pane

Used for applying filters to the report and visuals.

### 2. Visualizations Pane

Used to:

* Create visuals
* Select different visualization types
* Configure visual properties

### 3. Data Pane

Used to view the tables, columns, and other data elements available in the Power BI model.

These panes will be discussed in greater detail while building the actual Electro Hub report.

---

# 4. Data Pane Before Loading Data

Initially, the **Data pane is empty**.

### Why?

Because no data has been loaded into the Power BI model yet.

Therefore, Power BI has no:

* Tables
* Columns
* Fields

to display.

This leads to the first major step of any Power BI project:

> **Bring the data into Power BI Desktop.**

---

# 5. Importing the Electro Hub Dataset

The Electro Hub dataset is stored in an **Excel workbook**.

Power BI supports a large number of data sources, including Excel and many other sources. Other data sources will be discussed in future projects.

For this project, however:

> **Excel Workbook = Data Source**

---

## Step-by-Step: Get Data from Excel

### Step 1 — Open Get Data

From the Power BI Desktop ribbon:

**Home → Get Data**

Click **Get Data**.

### Step 2 — Select Excel

Since the source is an Excel workbook, select:

**Excel Workbook**

### Step 3 — Select the dataset

Locate the Excel workbook containing the Electro Hub data.

Double-click the workbook.

Power BI may take some time to load and display a preview of the workbook.

---

# 6. Tables Available in the Dataset

After selecting the Excel workbook, Power BI displays the available tables/sheets.

The dataset contains **four tables**:

| # | Table           | Type/Role           |
| - | --------------- | ------------------- |
| 1 | `dim customers` | Customer Dimension  |
| 2 | `dim product`   | Product Dimension   |
| 3 | `dim promotion` | Promotion Dimension |
| 4 | `sheet three`   | Fact Table          |

At this point, all four are part of the Electro Hub dataset and will be used for reporting.

### Important

All four tables need to be selected because they collectively form the dataset required for the project.

---

# 7. Load vs Transform Data

After selecting the required tables, Power BI provides two important options at the bottom:

1. **Load**
2. **Transform Data**

Understanding the difference between these two options is extremely important.

---

## Option 1 — Load

Choose **Load** when you want to directly bring the selected data into the Power BI model.

### Workflow

**Excel → Power BI Model**

No additional transformation is performed before loading.

---

## Option 2 — Transform Data

Choose **Transform Data** when you want to modify or prepare the data before loading it into the model.

Selecting this option opens the:

> **Power Query Editor**

Power Query can be used to perform data transformation and cleaning operations.

### Examples of transformations

You may:

* Rename queries
* Remove null values
* Remove blank values
* Change data types
* Remove unnecessary columns
* Clean data
* Restructure data
* Perform other transformations

### Workflow

**Excel → Power Query Editor → Transform/Clean → Power BI Model**

---

# 8. What Was Done in This Project?

For the Electro Hub project, the instructor wants to initially load the data without performing transformations.

Therefore:

### Steps

1. Select all four tables.
2. Click **Load**.
3. Wait for Power BI to load the data.

After loading, the four tables become available in the **Data pane**.

---

# 9. Tables After Loading

Once the data is loaded, the Data pane contains:

* `dim customers`
* `dim product`
* `dim promotion`
* `sheet three`

These are now part of the Power BI data model.

However, the instructor points out that simply loading the data is **not enough**.

Before creating an accurate report, you need to understand the data properly.

---

# 10. Why Understanding the Data Is Important

A key principle from this lecture is:

> **The better you understand your data, the easier it becomes to create an accurate report.**

You shouldn't immediately start creating charts after importing data.

Instead, you should first understand:

* What tables are available?
* What does each table represent?
* What columns are available?
* What type of data does each column contain?
* Is the data clean?
* Are there unnecessary columns?
* Are there missing values?
* Are the data types correct?
* Is the data structured appropriately for reporting?

This process prepares the dataset for the reporting stage.

---

# 11. Opening Power Query Editor

After loading the data, the instructor opens **Power Query Editor**.

### Steps

From Power BI Desktop:

**Home → Transform Data**

Click **Transform Data**.

This opens the **Power Query Editor**.

---

# 12. Understanding Power Query Editor

Power Query Editor is the environment used for:

* Cleaning data
* Transforming data
* Preparing data
* Structuring data

before it is used for reporting.

The instructor emphasizes that Power Query is an important part of the overall Power BI workflow.

---

# 13. Viewing Different Tables in Power Query

Inside Power Query Editor, the different queries/tables appear on the **left-hand side**.

Initially, `dim customers` is selected.

If you click:

### `dim customers`

You see the customer table.

### `dim product`

You see the product table.

### `dim promotion`

You see the promotion table.

### `sheet three`

You see the fourth table containing the transactional/fact data.

The instructor refreshes the data before continuing.

---

# 14. Renaming a Query

The instructor demonstrates how to rename a query.

The fourth table is currently named:

> `sheet three`

This isn't a meaningful name for a fact table, so it is renamed to:

> **Fact Table**

### Steps

1. Go to the **left-hand query/navigation pane** in Power Query Editor.
2. Locate `sheet three`.
3. Double-click `sheet three`.
4. Rename it to **Fact Table**.
5. Press Enter.

### Result

Before:

`sheet three`

After:

`Fact Table`

### Why rename it?

Meaningful names make the data model easier to understand and work with.

Instead of having a generic Excel sheet name, the table now clearly indicates that it represents the **fact/transactional data**.

---

# 15. Applied Steps in Power Query

One of the most important concepts introduced in this lecture is:

> **Applied Steps**

On the right-hand side of Power Query Editor, there is a section called:

### Applied Steps

Power Query records the transformations/operations performed on the data as individual steps.

This allows you to:

* Track transformations
* Review what has been done
* Modify transformations
* Undo transformations

---

# 16. Example — Removing a Column

The instructor demonstrates Applied Steps using the **Fact Table**.

Suppose we don't want the:

> `Net Sales`

column.

### Steps

1. Select the **Fact Table**.
2. Locate the `Net Sales` column.
3. Right-click the column.
4. Select **Remove**.

The `Net Sales` column disappears.

At the same time, Power Query adds a new step under **Applied Steps**.

The new step is:

> **Removed Columns**

This shows that Power Query has recorded the column-removal operation.

---

# 17. Undoing a Transformation

The instructor then demonstrates how to undo the previous transformation.

Suppose we realize that we actually **do need the Net Sales column**.

### Steps

1. Go to the **Applied Steps** section on the right.
2. Locate the `Removed Columns` step.
3. Click the **X/cross icon** next to that step.

The transformation is removed.

As a result:

> The `Net Sales` column appears again.

---

# 18. Why Applied Steps Are Important

Applied Steps provide a transformation history.

For example:

**Original Data**

↓

**Rename Query**

↓

**Remove Column**

↓

**Change Data Type**

↓

**Remove Null Values**

↓

**Other Transformations**

Each operation can appear as an individual step.

This makes the transformation process:

* Trackable
* Transparent
* Easier to modify
* Easier to debug

It is particularly useful when you need to undo a transformation.

---

# 19. Understanding the Columns

On the left/main data area of Power Query, you can see the different columns belonging to the currently selected table.

The instructor points out that these columns need to be understood before moving forward.

For the project, the next stage will involve examining:

* The different tables
* Their columns
* The nature of the data
* Cleaning requirements
* Preparation requirements
* Structure of the data

---

# 20. Power BI Report Development Workflow

The lecture introduces an important overall workflow for Power BI projects.

The basic process is:

### Step 1 — Bring the Data

Import the data into Power BI Desktop.

**Source → Power BI**

For this project:

**Excel → Power BI**

---

### Step 2 — Transform, Clean and Prepare the Data

After importing the data, inspect and prepare it.

This includes:

* Cleaning
* Transforming
* Preparing
* Structuring

The goal is to make the data suitable for reporting.

---

### Step 3 — Build the Report

Once the data is properly prepared, it can be used to create:

* Measures
* Visuals
* Charts
* Filters
* Slicers
* Dashboards
* Business insights

The actual report-building phase will come later in the project.

---

# 21. Why Data Preparation Comes Before Report Creation

Raw data is not always immediately suitable for reporting.

For example, data might contain:

* Incorrect data types
* Blank values
* Null values
* Unnecessary columns
* Poorly named tables
* Poorly structured data

Therefore, you first need to transform the data into a form that is appropriate for reporting.

### Conceptual flow

**Raw Data**

↓

**Clean**

↓

**Transform**

↓

**Prepare**

↓

**Structure**

↓

**Reporting-Ready Data**

↓

**Power BI Report**

---

# 22. Practical Steps Covered in This Lecture — Quick Reference

### Open Power BI

**Power BI Desktop → Blank Report**

### Import data

**Home → Get Data → Excel Workbook**

### Select dataset

Select all four:

* `dim customers`
* `dim product`
* `dim promotion`
* `sheet three`

### Load data

Click:

**Load**

### Open Power Query

**Home → Transform Data**

### Rename `sheet three`

**Left Query Pane → Double-click `sheet three` → Rename to `Fact Table`**

### Remove a column

**Select column → Right-click → Remove**

### Undo transformation

**Applied Steps → Click X beside the unwanted step**

---

# 23. Important Concepts to Remember

### Power BI Desktop

The primary desktop application used to build the Power BI report.

### Report View

The view where reports and visualizations are created.

### Data Pane

Displays the tables and fields available in the model.

### Filters Pane

Used to apply filtering to reports and visuals.

### Visualizations Pane

Used to create and configure visuals.

### Get Data

Used to connect Power BI to a data source.

### Excel Workbook

The data source used for this Electro Hub project.

### Power Query Editor

The environment used to clean, transform, prepare, and structure data.

### Query

A table/query loaded into Power Query.

### Applied Steps

A sequential record of transformations performed on a query.

### Fact Table

The fourth dataset table was renamed from `sheet three` to **Fact Table** because it represents the transactional/fact data.

---

# 24. Key Takeaways

* The Electro Hub project uses an **Excel workbook** as its data source.
* The dataset contains **four tables**:

  * `dim customers`
  * `dim product`
  * `dim promotion`
  * `Fact Table`
* Initially, the data pane is empty because no data has been loaded.
* The general method to import data is:
  **Home → Get Data → Select Data Source**
* **Load** directly imports data into the Power BI model.
* **Transform Data** opens Power Query Editor for data preparation.
* Power Query should be used to **clean, transform, prepare, and structure data**.
* The fourth table was renamed from `sheet three` to **Fact Table**.
* Power Query records transformations under **Applied Steps**.
* Applied Steps can be used to track and undo transformations.
* Data understanding and preparation should happen **before report creation**.
* The overall Power BI workflow introduced here is:

**Bring Data → Clean/Transform → Prepare/Structure → Build Report → Analyze/Report Insights**

This lecture establishes the foundation for the next stage: **understanding and preparing each Electro Hub table and its columns in detail.**
