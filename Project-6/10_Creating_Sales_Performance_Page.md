# Power BI – Measures Table & Sales Performance Page Setup

## 1. Session Overview

This session covers **two main tasks**:

1. Moving existing DAX measures from the **Housing** table into a dedicated **Measures Table**.
2. Creating and formatting the **second report page**, named **Sales Performance**.

The first part focuses on a Power BI modeling best practice: **keeping measures in a separate table**.

The second part prepares the canvas for the next set of visuals by adding:

* A background image
* A rectangle/header shape
* A page title

---

# Part 1 – Creating a Dedicated Measures Table

## 2. Why Create a Separate Measures Table?

The instructor emphasizes that it is a **good practice to create a separate table for measures**.

In a real-world Power BI project, you may have:

* Many tables
* A large number of columns
* Dozens or hundreds of DAX measures

If measures are stored inside different business/data tables, it can become difficult to find the required measure.

For example, the Housing table may contain:

```text
Housing
├── Date
├── House ID
├── House Type
├── Sales Type
├── Purchase Price
├── Region
├── ...
├── Year-on-Year Sales Growth       ← Measure
├── Median Sales Price Change       ← Measure
├── Units Sold in Latest Year...    ← Measure
└── Last 12 Month Sales             ← Measure
```

A separate Measures table provides a cleaner structure:

```text
Housing
├── Date
├── House ID
├── House Type
├── Sales Type
├── Purchase Price
└── ...

Measures Table
├── Year-on-Year Sales Growth
├── Median Sales Price Change
├── Units Sold in Latest Year...
└── Last 12 Month Sales
```

### Main benefit

It becomes much easier to:

> **Search for, organize, and manage measures.**

---

# 3. Creating the Measures Table

### Steps

1. Go to the **Home** tab.
2. Click:

> **Enter Data**

3. A new table window will appear.
4. Name the table:

```text id="q0j6r1"
Measures table
```

5. Click:

> **Load**

Power BI creates the new Measures table.

---

# 4. Identifying Measures in the Housing Table

After creating the Measures table, expand the **Housing** table in the Data/Fields pane.

You will see the existing measures.

The instructor identifies them using the **calculator icon**.

The calculator icon indicates that the item is a:

> **Measure**

rather than a regular column.

The measures created in the previous sessions include:

* Median Sales Price Change
* Units Sold in Latest Year and Quarter
* Year-on-Year Sales Growth
* Last 12 Month Sales

---

# 5. Changing the Home Table of a Measure

Power BI allows you to specify the **Home Table** of a measure.

The instructor moves each measure from the Housing table to the newly created Measures table.

### General process

1. Click a measure.
2. Go to:

> **Measure tools**

3. Locate:

> **Home table**

4. Change it from:

> Housing

to:

> Measures table

This does **not** change the DAX calculation.

It only changes where the measure is organized/displayed in the model.

---

# 6. Moving Median Sales Price Change

The first measure moved is:

> **Median Sales Price Change**

### Steps

1. Click **Median Sales Price Change**.
2. Go to **Measure tools**.
3. Find **Home table**.
4. Change:

```text id="ux2x8s"
Housing
```

to:

```text id="0q8z6y"
Measures table
```

The measure now appears under the Measures table.

---

# 7. Moving Units Sold Measure

Next, the instructor moves:

> **Units Sold in Latest Year and Quarter**

### Steps

1. Select the measure.
2. Open **Measure tools**.
3. Find **Home table**.
4. Change the Home table from:

```text id="3cv7j4"
Housing
```

to:

```text id="c2j8s6"
Measures table
```

---

# 8. Moving Year-on-Year Sales Growth

The next measure is:

> **Year-on-Year Sales Growth**

### Steps

1. Select the measure.
2. Open **Measure tools**.
3. Change **Home table**:

```text id="n9p5x3"
Housing → Measures table
```

The measure is now organized under the dedicated Measures table.

---

# 9. Moving Last 12 Month Sales

The previously created:

> **Last 12 Month Sales**

measure should also belong to the Measures table.

The same process is followed:

```text id="w0f8g5"
Select Measure
     ↓
Measure tools
     ↓
Home table
     ↓
Measures table
```

---

# 10. Why This Is Useful in Real Projects

The instructor highlights an important practical scenario.

In a real-time project, you could have:

```text id="k1h5j7"
Table 1
Table 2
Table 3
Table 4
Table 5
...
```

and each table could potentially have many measures.

Trying to remember which table contains a particular measure can become confusing.

A dedicated Measures table provides a central location:

```text id="7lq3r8"
                 Measures Table
                       │
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
   KPI Measures    Growth Measures   Other Measures
```

Therefore:

> **Keeping measures in a separate table is a recommended organization practice for larger Power BI models.**

---

# 11. Removing the Unnecessary Column

When the Measures table was created using **Enter Data**, Power BI created a default column:

> **Column 1**

The instructor does not need this column because the table is intended to act as a container for measures.

### Steps

1. Locate **Column 1** under the Measures table.
2. Right-click it.
3. Remove/delete the column.

The Measures table can now simply serve as the location for the measures.

---

# Part 2 – Creating the Second Report Page

## 12. Creating a New Page

After organizing the measures, the instructor begins setting up the second report page.

### Steps

1. At the bottom of the Power BI report, click the:

> **+ (Plus) icon**

2. Power BI creates a new blank report page.

---

# 13. Renaming the New Page

The newly created page is renamed:

> **Sales Performance**

### Steps

1. Locate the new page tab.
2. Rename the page.
3. Enter:

```text id="1g4n7b"
Sales Performance
```

The report now has a second page dedicated to sales performance analysis.

---

# Part 3 – Adding a Background Image

## 14. Adding the Canvas Background

The instructor wants to use a background image to improve the appearance of the Sales Performance page.

### Steps

1. Click on the report page/canvas.
2. Open the formatting options for the page.
3. Go to:

> **Canvas Background**

4. Click:

> **Browse**

5. Select the **second image** provided with the course/resources.
6. Double-click the image.

The image is now assigned as the canvas background.

---

# 15. Changing Background Transparency

Initially, the image may not be visible because the transparency is set to a high value.

The instructor changes:

> **Transparency → 0%**

### Result

The background image becomes fully visible.

Conceptually:

```text
Transparency = 100%
        ↓
Image effectively invisible

Transparency = 0%
        ↓
Image fully visible
```

The instructor notes that the required images are provided in the resources.

---

# Part 4 – Adding the Page Header

## 16. Inserting a Rectangle Shape

The instructor wants a header/banner at the top of the Sales Performance page.

### Steps

1. Go to:

> **Insert**

2. Select:

> **Shapes**

3. Choose:

> **Rectangle**

A rectangle appears on the canvas.

---

# 17. Resizing the Rectangle

The rectangle is resized so that it can function as a header.

The instructor adjusts its dimensions and places it at the **top of the report page**.

Conceptually:

```text
┌─────────────────────────────────────────────┐
│              SALES PERFORMANCE              │
└─────────────────────────────────────────────┘

              Report Content
```

---

# 18. Formatting the Rectangle

After inserting the rectangle, its appearance is customized.

### Steps

1. Select the rectangle.
2. Open its:

> **Style**

3. Turn:

> **Border → Off**

4. Choose a suitable fill/background color.

The instructor emphasizes that the exact color is not mandatory.

You can:

> **Choose any color of your preference.**

The colors shown in the lecture are simply examples.

---

# Part 5 – Adding "Sales Performance" Text

## 19. Turning Text On

The rectangle is also used as the header containing the page title.

### Steps

1. Select the rectangle.
2. Open:

> **Style**

3. Turn:

> **Text → On**

This allows text to be entered inside the shape.

---

# 20. Entering the Page Title

The title entered is:

> **Sales Performance**

### Steps

Enter:

```text id="5zq7c2"
Sales Performance
```

inside the rectangle.

---

# 21. Formatting the Title

The instructor then formats the title to make it prominent.

### Font size

The font size is increased to:

> **44**

### Other formatting

The instructor demonstrates changing:

* Font style
* Font color
* Font weight
* Italic
* Underline

The title is made visually prominent using combinations such as:

> **Bold + Italic + Underline**

The exact font/color can be changed according to your preference.

---

# 22. Final Page Header

The top of the Sales Performance page now contains a styled header:

```text id="h0m7x4"
┌─────────────────────────────────────────────────┐
│                                                 │
│              Sales Performance                 │
│                                                 │
└─────────────────────────────────────────────────┘
```

The background image is positioned behind the report content.

---

# 23. Why the Formatting Is Done This Way

The instructor is essentially establishing a consistent report design:

### Background

Provides a visual theme.

### Rectangle

Creates a clear header area.

### Title

Makes the purpose of the page immediately understandable.

This design will serve as the foundation for the visuals that will be added in subsequent sessions.

---

# 24. Current Report Structure

At the end of this session, the report has at least two pages.

### Page 1

> **House Market Overview**

Contains the visuals developed in previous sessions, including:

* Year-on-Year Sales Growth by Sales Type
* Offer Price vs Purchase Price
* Median Sales Price Change by Region
* Units Sold in Latest Year and Quarter
* 12 Month Sales

---

### Page 2

> **Sales Performance**

Currently contains:

* Background image
* Top rectangle/header
* **Sales Performance** title

The actual sales performance visuals will be added in the **upcoming sessions**.

---

# 25. Measures Table – Final Structure

After moving the measures, the model is conceptually organized like this:

```text
Housing
│
├── Date
├── House ID
├── House Type
├── Sales Type
├── Purchase Price
├── SQM
├── Region
├── ...
│
└── Data Columns

Measures table
│
├── Median Sales Price Change
├── Units Sold in Latest Year and Quarter
├── Year-on-Year Sales Growth
└── Last 12 Month Sales
```

This makes it much easier to identify measures.

---

# 26. Important Power BI Concept – Home Table

### What is the Home Table?

The **Home Table** determines where a measure is displayed/organized in the Fields/Data pane.

For example:

```text id="4t1v8e"
Measure:
Year-on-Year Sales Growth

Home Table:
Housing
```

can be changed to:

```text id="i6d2p9"
Measure:
Year-on-Year Sales Growth

Home Table:
Measures table
```

### Important

Changing the Home Table:

> **does not change the DAX formula or calculation.**

It primarily changes the organizational location of the measure.

---

# 27. Complete Workflow

```text id="9i6s4m"
Home
 ↓
Enter Data
 ↓
Create "Measures table"
 ↓
Load
 ↓
Expand Housing
 ↓
Identify measures using calculator icon
 ↓
Select each measure
 ↓
Measure tools
 ↓
Home table
 ↓
Change Housing → Measures table
 ↓
Repeat for all measures
 ↓
Delete unnecessary Column 1
 ↓
Click + to create new report page
 ↓
Rename page
 ↓
Sales Performance
 ↓
Format page
 ↓
Canvas Background
 ↓
Browse
 ↓
Select second image
 ↓
Set Transparency = 0%
 ↓
Insert
 ↓
Shapes
 ↓
Rectangle
 ↓
Resize and position at top
 ↓
Style
 ↓
Border = Off
 ↓
Choose fill color
 ↓
Text = On
 ↓
Enter "Sales Performance"
 ↓
Font Size ≈ 44
 ↓
Format font/color/style
```

---

# 28. Quick Revision Table

| Task                      | Action                                 |
| ------------------------- | -------------------------------------- |
| Create Measures table     | Home → Enter Data                      |
| Table name                | Measures table                         |
| Load table                | Click Load                             |
| Identify measures         | Calculator icon                        |
| Change measure location   | Measure tools → Home table             |
| Old Home table            | Housing                                |
| New Home table            | Measures table                         |
| Remove unnecessary column | Delete Column 1                        |
| Create second page        | Click `+`                              |
| Page name                 | Sales Performance                      |
| Add background            | Format Page → Canvas Background        |
| Background image          | Second resource image                  |
| Background transparency   | 0%                                     |
| Add header                | Insert → Shapes → Rectangle            |
| Rectangle border          | Off                                    |
| Rectangle text            | On                                     |
| Header text               | Sales Performance                      |
| Font size                 | 44                                     |
| Additional formatting     | Font/style/color/bold/italic/underline |

---

# 29. Key Takeaways

1. **Create a dedicated Measures table** when a Power BI project contains many measures.
2. The **calculator icon** identifies measures in the Fields/Data pane.
3. Use **Measure tools → Home table** to move a measure from one table to another.
4. Moving a measure to another Home Table **does not change its DAX calculation**.
5. Delete unnecessary **Column 1** from the Measures table.
6. Create a second report page using the **+ icon**.
7. Rename it **Sales Performance**.
8. Add a background through **Format Page → Canvas Background → Browse**.
9. Set background **Transparency to 0%** to make the image fully visible.
10. Use **Insert → Shapes → Rectangle** to create a page header.
11. Turn the rectangle's **Border Off**.
12. Turn **Text On** and enter **Sales Performance**.
13. Increase the title size to approximately **44** and format it according to the desired design.
14. This session primarily **prepares the Sales Performance page**; the actual analytical visuals will be created in the following sessions.
