# Power BI Project — Connecting SQL Server, Transforming Data & Creating the Report Template

## 1. Session Overview

In the previous session, a **new combined table** was created in the SQL Server test environment by joining:

* `products`
* `test_environment_inventory_data_set`

The joined data was stored in:

```text
new_table
```

In this session, the instructor moves from **SQL Server to Power BI Desktop** and prepares the report for the upcoming DAX/KPI work.

The session covers:

1. Opening Power BI Desktop.
2. Removing previously stored SQL Server permissions.
3. Connecting Power BI to SQL Server.
4. Using `test_env` as the database.
5. Using **Import** connectivity mode.
6. Loading `new_table` using a SQL query.
7. Handling the encrypted-connection warning.
8. Opening the Power Query Editor.
9. Correcting and validating data types.
10. Correcting the Order Date data type.
11. Understanding regional date settings.
12. Applying the Power Query transformations.
13. Loading 99 records into the Power BI model.
14. Renaming the query.
15. Creating the Page 1 report background/template.
16. Creating the Page 2 report background/template.
17. Setting wallpaper colors.
18. Saving the Power BI report.
19. Preparing for the next session, where DAX measures and KPIs will be created.

---

# 2. Starting Power BI Desktop

The instructor first opens:

> **Power BI Desktop**

The application may take some time to load.

Once Power BI Desktop opens, the initial intention is to connect to:

> **Microsoft SQL Server**

because SQL Server is being used as the data source for the test environment.

---

# 3. Clearing Existing SQL Server Data Source Permissions

Before connecting again, the instructor performs an important step.

Since the instructor had previously connected to SQL Server, Power BI may already have stored credentials/permissions for that data source.

Therefore, the instructor clears the existing permissions first.

### Steps

In Power BI Desktop:

1. Go to **Home**.
2. Select **Transform Data**.
3. Open **Data Source Settings**.
4. Locate the existing SQL Server data source.
5. Select the relevant permissions.
6. Click **Clear Permissions**.

The instructor removes permissions associated with the SQL Server/test environment connection.

### Why do this?

This ensures that Power BI establishes the connection again using the intended credentials/settings instead of relying on an old stored connection.

---

# 4. Connecting Power BI to SQL Server

After clearing the old permissions:

Go to:

> **Get Data → SQL Server**

Click:

> **SQL Server**

This opens the SQL Server connection dialog.

---

# 5. Getting the SQL Server Name

The instructor opens:

> **SQL Server Management Studio (SSMS)**

and opens the Database Engine connection information.

The server name is copied from SSMS.

For the instructor's system, the server name is the local machine/server name.

### Steps

```text
SSMS
 ↓
Database Engine
 ↓
Copy Server Name
 ↓
Power BI
 ↓
SQL Server connector
 ↓
Paste Server Name
```

---

# 6. Providing the Database Name

The database created earlier was:

```text
test_env
```

Therefore, in the Power BI SQL Server connection dialog:

### Server

Enter the SQL Server server name.

### Database

Enter:

```text
test_env
```

---

# 7. Selecting Connectivity Mode

The instructor chooses:

> **Import**

So the connection is configured as:

```text
SQL Server
    ↓
Power BI
    ↓
Import
    ↓
Data loaded into Power BI model
```

### Import Mode

With Import mode, the data is brought into Power BI's internal model.

This is different from DirectQuery, where Power BI generally queries the source database when the report is used.

For this project, the instructor chooses:

> **Import connectivity mode**

---

# 8. Using a SQL Statement to Retrieve the Data

Instead of importing all tables separately, the instructor uses the combined table that was created in SQL Server.

The table is:

```text
new_table
```

The SQL query is:

```sql id="f2z1vq"
SELECT *
FROM new_table;
```

This table already contains the data obtained by joining the Products and Inventory tables.

---

# 9. Why Use `new_table`?

Recall the previous session.

The two tables were:

```text id="p1j7yx"
Products
```

and:

```text id="w9yd8g"
Test Environment Inventory Data Set
```

They were joined using:

```text id="p89j4a"
Product ID
```

The result was stored in:

```text id="6k1c5j"
new_table
```

Therefore, Power BI can simply retrieve:

```sql id="5v2xq0"
SELECT *
FROM new_table;
```

instead of independently importing and joining the original tables.

---

# 10. Connecting Using Windows Authentication

After entering the server/database details, Power BI asks for authentication.

The instructor chooses:

> **Windows**

and selects:

> **Use my current credentials**

Then clicks:

> **Connect**

---

# 11. Encrypted Connection Warning

Power BI displays a warning indicating that it is unable to connect using an encrypted connection.

It provides the option to access the data source using an **unencrypted connection**.

The instructor accepts this because this is the local/test environment setup being used for the project.

Click:

> **OK**

to continue.

### Important

This is a connection/security configuration detail specific to the instructor's setup. In a real organizational environment, whether an unencrypted connection is acceptable depends on the organization's security requirements.

---

# 12. Open Power Query Editor

The instructor chooses:

> **Transform Data**

This opens the:

> **Power Query Editor**

This is where the imported data can be examined and transformed before being loaded into the Power BI data model.

---

# 13. Why Check the Data Again in Power Query?

The data had already been inspected in SQL Server.

However, once the data enters Power BI, it is important to verify:

* Data types
* Date formats
* Numeric columns
* Text columns
* Any unexpected values
* Transformation requirements

The instructor therefore goes through the data types before using it for reporting.

---

# 14. Order Date Data Type Issue

The first column discussed is:

> **Order Date**

The instructor notices that Power Query has interpreted the column as:

> **Date/Time**

However, the column contains only dates.

There is no requirement for a time component.

Therefore, the data type should be:

> **Date**

instead of:

> **Date/Time**

---

# 15. Changing Order Date from Date/Time to Date

### Steps

1. Select the **Order Date** column.
2. Click the **Data Type** icon/dropdown at the top.
3. Select:

> **Date**

Power Query changes the column's data type.

---

# 16. Date Format Issue — SQL Server vs Power BI

The instructor previously noticed that the date format displayed in SQL Server was not the expected format.

However, after bringing the data into Power BI, the date is displayed in the desired format.

The instructor refers to the expected format as:

```text
DD/MM/YYYY
```

For example:

```text
28/08/2026
```

The exact display format depends on the regional settings.

---

# 17. Regional Settings and Date Formats

Date interpretation/display can depend on the **regional settings** of the system.

The instructor explains that if the date format isn't correct according to your region, you can modify the regional settings through the Windows Control Panel.

### Steps demonstrated

1. Search for:

> **Control Panel**

2. Open Control Panel.
3. Go to:

> **Clock and Region**

The instructor's regional setting is based on:

> **English (India)**

Therefore, dates are interpreted/displayed in the expected day-month-year format.

---

# 18. Why Regional Settings Matter

Different regions use different date conventions.

For example:

### India / UK-style

```text
DD/MM/YYYY
```

Example:

```text
28/08/2026
```

### US-style

```text
MM/DD/YYYY
```

Example:

```text
08/28/2026
```

Therefore, when working with date data, regional settings can affect how dates are interpreted and displayed.

---

# 19. Changing Regional Settings

If your expected date format is different:

```text
Control Panel
     ↓
Clock and Region
     ↓
Regional settings
     ↓
Select required region
     ↓
Apply
     ↓
OK
```

The instructor keeps:

> **English (India)**

because it is suitable for the desired date format.

---

# 20. Data Types of All Columns

The instructor then checks each remaining column.

The final data types should be:

| Column       | Data Type          |
| ------------ | ------------------ |
| Order Date   | **Date**           |
| Product ID   | **Whole Number**   |
| Availability | **Whole Number**   |
| Demand       | **Whole Number**   |
| Product Name | **Text**           |
| Unit Price   | **Decimal Number** |

Let's understand each one.

---

# 21. Product ID → Whole Number

The Product ID is numeric.

Therefore, its Power Query data type is changed/confirmed as:

> **Whole Number**

### Steps

1. Select `Product ID`.
2. Click the data type icon.
3. Select:

> **Whole Number**

---

# 22. Availability → Whole Number

Availability represents a number of units.

For example:

```text
100
200
50
```

These values do not require decimal places.

Therefore:

> **Availability → Whole Number**

---

# 23. Demand → Whole Number

Demand also represents the number of units demanded.

Therefore:

> **Demand → Whole Number**

---

# 24. Product Name → Text

Product Name contains textual information.

For example:

```text
Product A
Product B
Product C
```

Therefore:

> **Product Name → Text**

---

# 25. Unit Price → Decimal Number

Unit Price represents a monetary/price value.

It can contain decimal values.

Therefore:

> **Unit Price → Decimal Number**

The instructor notes that this data type is already appropriate.

---

# 26. Final Data Type Structure

After correcting the data types, the table should look conceptually like:

```text id="eyxxjn"
Demand / Availability Data
│
├── Order Date       → Date
├── Product ID       → Whole Number
├── Availability     → Whole Number
├── Demand           → Whole Number
├── Product Name     → Text
└── Unit Price       → Decimal Number
```

This is an important structure to remember before beginning the reporting/DAX work.

---

# 27. Applying the Power Query Changes

Once the transformations are complete:

Go to:

> **Home → Close & Apply**

Click:

> **Close & Apply**

Power BI now:

1. Applies the Power Query transformations.
2. Loads the transformed data.
3. Adds the data to the Power BI model.
4. Returns to the Power BI report view.

---

# 28. Data Successfully Loaded

Power BI confirms that:

> **99 records** have been loaded into the model.

This matches the number of records present in the inventory dataset.

This provides a useful validation:

```text
SQL Server records = 99
Power BI records   = 99
```

Therefore, no records were unexpectedly lost during this stage.

---

# 29. Renaming the Query

The imported query is initially named:

> **Query1**

The instructor wants to give it a more meaningful name.

The query is renamed to:

> **Demand/Availability Data**

This makes the model easier to understand.

### Steps

1. Find the query in the data/model pane.
2. Double-click the query name.
3. Rename it to:

```text
Demand/Availability Data
```

The instructor mentions the naming around:

> **Demand/Availability Data**

The exact naming convention can be adapted, but the important point is to use a meaningful name rather than leaving the default `Query1`.

---

# 30. Why Meaningful Query/Table Names Matter

Instead of:

```text
Query1
```

a meaningful name such as:

```text
Demand/Availability Data
```

makes the Power BI model easier to understand.

This becomes especially useful when the model contains:

* Multiple tables
* Multiple queries
* Many measures
* Relationships
* Calculations

---

# 31. Preparing the Report Page

After loading and transforming the data, the instructor begins preparing the report layout.

The report will have:

> **Two pages**

The KPI requirements were discussed in the earlier session.

---

# 32. Page 1 KPI Requirements

Page 1 will eventually contain:

1. **Average Demand per Day**
2. **Average Availability per Day**
3. **Total Supply Shortage**

The instructor therefore creates a background/template suitable for these KPIs.

---

# 33. Adding a Background Image to Page 1

The instructor has already created a background image using:

> **Canva**

This image is provided as a resource so students can use the same design.

### Steps

On Page 1:

1. Open the report page formatting options.
2. Select:

> **Format your report page**

3. Find:

> **Canvas Background**

4. Click:

> **Browse Image**

5. Navigate to the location where the background image is stored.

The instructor navigates to a folder on the Desktop associated with the Power BI project.

6. Select the Page 1 background image.

---

# 34. Setting Background Transparency

After selecting the image, the instructor changes:

> **Transparency → 0%**

This makes the background image fully visible.

---

# 35. Changing Image Fit

The image initially has a default fit setting.

The instructor changes:

> **Image Fit → Fit**

This makes the background image fit appropriately within the report canvas.

---

# 36. Page 1 Template

After applying the background, Page 1 now has a predefined report design.

The instructor refers to this as the template that will eventually be used to represent the KPIs.

Conceptually:

```text id="5d7tgo"
PAGE 1
─────────────────────────────────

     Average Demand per Day

     Average Availability per Day

     Total Supply Shortage

─────────────────────────────────
```

At this stage, the visuals/KPIs haven't yet been created.

The background is simply preparing the design.

---

# 37. Changing the Wallpaper Color

The instructor also changes the report wallpaper.

### Steps

1. Expand the visualization/formatting pane.
2. Select:

> **Wallpaper**

3. Change the wallpaper color to:

> **Black**

This creates the intended overall theme.

---

# 38. Page 2 Background

The instructor has also created another background image for:

> **Page 2**

A separate background is used because Page 2 has different KPIs.

---

# 39. Creating Page 2

Click:

> **+**

to add a new report page.

This creates:

> **Page 2**

---

# 40. Adding Page 2 Background Image

Again:

1. Open the page formatting options.
2. Go to:

> **Canvas Background**

3. Click:

> **Browse Image**

4. Select the Page 2 background image.
5. Change:

> **Image Fit → Fit**

6. Set:

> **Transparency → 0%**

---

# 41. Page 2 KPI Requirements

Page 2 will eventually contain:

1. **Total Profit**
2. **Total Loss**
3. **Average Daily Loss**

The theme/design is similar to Page 1, but the KPI labels are different.

Conceptually:

```text id="g4mdn8"
PAGE 2
─────────────────────────────────

          Total Profit

           Total Loss

       Average Daily Loss

─────────────────────────────────
```

Again, these are currently just the report templates/backgrounds.

The actual KPI calculations and visuals will be created in the next sessions.

---

# 42. Page 2 Wallpaper

The instructor also changes the wallpaper for Page 2.

### Steps

1. Expand the wallpaper settings.
2. Change the wallpaper color.
3. Select:

> **Black**

This gives both pages a consistent overall theme.

---

# 43. Report Design

At the end of this session, the report has:

### Page 1

Background/template for:

* Average Demand per Day
* Average Availability per Day
* Total Supply Shortage

### Page 2

Background/template for:

* Total Profit
* Total Loss
* Average Daily Loss

The theme is consistent across both pages.

---

# 44. Saving the Power BI Report

The instructor now saves the Power BI report.

The report is given a name similar to:

> **prod Power BI report**

The instructor deliberately uses a production-oriented name because the eventual goal is to shift the report from the test environment to the production environment.

However:

> **At this stage, the report is still using test environment data.**

This is an important distinction.

---

# 45. Saving the File

The instructor chooses the save option and navigates to:

> **Projects with Power BI**

The report is saved with a name similar to:

```text
prod Power BI
```

The exact filename is less important than understanding that this is the Power BI report being developed for the project.

---

# 46. Important Clarification — "prod" Name Does Not Mean Production Data Yet

Although the file is named something like:

```text
prod Power BI
```

the current report is **not actually connected to production data yet**.

At this point:

```text
Power BI Report
       ↓
SQL Server
       ↓
test_env
       ↓
new_table
```

The production transition will happen later.

---

# 47. Why Build the Report Against Test Data First?

The project follows a real-world development pattern:

```text id="e1whhs"
TEST ENVIRONMENT
      ↓
Build Report
      ↓
Create DAX
      ↓
Create KPIs
      ↓
Validate Results
      ↓
Production
```

The instructor will eventually demonstrate how the report can be shifted from the test environment to production.

---

# 48. Full Session Workflow

The entire session can be summarized as:

```text id="sp5oxr"
SQL Server
    ↓
test_env
    ↓
new_table
    ↓
Power BI Desktop
    ↓
Get Data
    ↓
SQL Server
    ↓
Enter Server Name
    ↓
Database = test_env
    ↓
Import Mode
    ↓
SELECT * FROM new_table
    ↓
Windows Authentication
    ↓
Connect
    ↓
Transform Data
    ↓
Power Query Editor
    ↓
Validate Data Types
    ↓
Order Date → Date
    ↓
Product ID → Whole Number
    ↓
Availability → Whole Number
    ↓
Demand → Whole Number
    ↓
Product Name → Text
    ↓
Unit Price → Decimal
    ↓
Close & Apply
    ↓
99 records loaded
    ↓
Rename Query
    ↓
Create Page 1 Template
    ↓
Create Page 2 Template
    ↓
Save Power BI Report
```

---

# 49. Key Data-Source Architecture

At this stage, the project architecture is:

```text id="t1aqf5"
              SQL SERVER
                  │
                  ↓
               test_env
                  │
                  ↓
              new_table
                  │
                  │ SELECT *
                  ↓
             POWER BI
                  │
          ┌───────┴───────┐
          ↓               ↓
       Page 1           Page 2
          │               │
       KPIs            KPIs
```

---

# 50. Important Concepts Learned

## 1. Data Source Settings

Used to manage stored permissions for existing connections.

Path:

```text id="q6a8j1"
Transform Data
      ↓
Data Source Settings
```

---

## 2. SQL Server Connector

Used to connect Power BI Desktop to Microsoft SQL Server.

Path:

```text id="2r9zv3"
Get Data
   ↓
SQL Server
```

---

## 3. Import Connectivity Mode

The instructor chooses:

> **Import**

This means the data is loaded into the Power BI model.

---

## 4. SQL Query

The instructor retrieves the combined table using:

```sql id="9q8g1q"
SELECT *
FROM new_table;
```

---

## 5. Power Query Editor

Used to transform and validate the data before loading it into the Power BI model.

---

## 6. Data Types

Correct data types are critical for Power BI calculations.

Final types:

```text id="zj6oqh"
Order Date       → Date
Product ID       → Whole Number
Availability     → Whole Number
Demand           → Whole Number
Product Name     → Text
Unit Price       → Decimal Number
```

---

# 51. Why Data Types Matter for the Upcoming DAX

This preparation is particularly important because the next session will involve DAX calculations.

For example:

### Date

`Order Date` must be a proper date field for calculations involving:

* Daily analysis
* Time-based calculations
* Date filtering

### Numeric columns

`Demand`, `Availability`, and `Product ID` need appropriate numeric types so they can be used correctly in calculations.

### Unit Price

`Unit Price` needs a numeric/decimal type because it will contribute to financial calculations such as profit/loss.

---

# 52. Validation Checklist

Before moving to the next session, verify the following.

### SQL Server

* [ ] `test_env` database exists.
* [ ] `new_table` exists.
* [ ] `new_table` contains the combined data.
* [ ] `new_table` contains 99 records.

### Power BI Connection

* [ ] SQL Server connection works.
* [ ] Database is `test_env`.
* [ ] Import mode is selected.
* [ ] Windows authentication/current credentials are used.
* [ ] `new_table` is successfully imported.

### Power Query

* [ ] Order Date = Date.
* [ ] Product ID = Whole Number.
* [ ] Availability = Whole Number.
* [ ] Demand = Whole Number.
* [ ] Product Name = Text.
* [ ] Unit Price = Decimal Number.
* [ ] Changes are applied.

### Power BI Model

* [ ] 99 records loaded.
* [ ] Query renamed meaningfully.
* [ ] Page 1 background added.
* [ ] Page 2 background added.
* [ ] Wallpaper set appropriately.
* [ ] Report saved.

---

# 53. Important Numbers to Remember

The key validation number in this session is:

> **99 records loaded into the Power BI model.**

This should match the SQL Server `new_table`.

So:

```text
SQL Server new_table = 99 records
Power BI model       = 99 records
```

---

# 54. What's Coming Next?

The instructor concludes that the next session will focus on the **DAX portion**.

The next stage will involve:

```text
Data Loaded
     ↓
DAX Measures
     ↓
KPI Calculations
     ↓
Visuals
     ↓
Report Insights
```

The KPIs to be created are:

### Page 1

* Average Demand per Day
* Average Availability per Day
* Total Supply Shortage

### Page 2

* Total Profit
* Total Loss
* Average Daily Loss

---

# ⭐ Final Takeaway

This session represents the transition from **SQL Server data preparation → Power BI report development**.

The most important workflow to remember is:

```text
SQL Server Test Environment
          ↓
       new_table
          ↓
   Power BI SQL Connector
          ↓
        Import
          ↓
    Power Query Editor
          ↓
    Fix Data Types
          ↓
     Close & Apply
          ↓
    99 Records Loaded
          ↓
   Prepare Report Pages
          ↓
      Page 1 + Page 2
          ↓
      Save Report
          ↓
   Next → DAX & KPIs
```

The key practical lesson is that **before creating DAX measures, the source data should be properly connected, validated, and assigned appropriate data types**. Once this foundation is ready, the next step is to build the actual business calculations and visuals.
