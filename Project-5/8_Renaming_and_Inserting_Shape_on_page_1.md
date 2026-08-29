# Power BI — KPI Preparation, Page Formatting & Report Setup

## 1. Session Overview

This session marks the beginning of the **reporting and KPI preparation phase** of the Loan Default Power BI project.

In the previous sessions, we covered:

* Loan Default dataset overview
* Column definitions
* Data types
* Data profiling
* Data quality checking
* Power Query

Now we move toward:

* Creating **KPIs**
* Creating **DAX measures**
* Creating **DAX calculated columns**
* Preparing the report page
* Formatting the report page
* Later representing KPIs using appropriate visuals/charts

The DAX measures and columns created in this stage will ultimately be used while building the Power BI report.

---

# 2. Move to Report View

Since the data preparation was completed in Power Query, the instructor now moves to the report-building interface.

### Steps

In **Power BI Desktop**:

1. Go to **Report View**.
2. This is where the report page and visuals will be created.

The report page currently has the default name:

> **Page 1**

---

# 3. Rename the Report Page

The first formatting task is to give the report page a meaningful name.

Instead of keeping the default:

> `Page 1`

the instructor renames it to:

> **Loan Default Overview**

### Steps

1. Look at the bottom-left area of Power BI Desktop where the report pages are displayed.
2. Locate **Page 1**.
3. **Double-click** on `Page 1`.
4. Press:

**Ctrl + A**

5. Enter the new name:

> `Loan Default Overview`

6. Press **Enter**.

### Why rename report pages?

Meaningful page names make reports easier to navigate and understand, especially when a report contains multiple pages.

For example:

```text
Page 1
Page 2
Page 3
```

is less descriptive than:

```text
Loan Default Overview
Customer Analysis
Loan Analysis
Risk Analysis
```

---

# 4. Insert a Shape

The instructor then begins formatting the report page by adding a shape.

Shapes can be used to create:

* Headers
* Background elements
* Section titles
* Containers
* Decorative elements
* KPI areas

### Steps

Go to:

**Insert → Shapes**

Power BI provides multiple shapes that can be inserted into the report canvas.

The instructor chooses:

> **Rounded Tab Top Right**

---

# 5. Resize the Shape

After inserting the shape, it appears on the report canvas.

The instructor then resizes it so that it can function as a header/banner at the top of the page.

### Steps

1. Select the inserted shape.
2. Use its resize handles.
3. Adjust its width and height.
4. Position it near the **top of the report page**.

The purpose is to create a visually appealing header area.

---

# 6. Format the Shape

Power BI allows the inserted shape to be customized using the **Format pane**.

The instructor opens:

> **Format Shape**

This allows different properties of the shape to be modified.

---

# 7. Change the Border

Under the formatting options, the instructor goes to:

> **Styles**

and changes the border setting.

### Steps

1. Open the **Format Shape** pane.
2. Go to **Styles**.
3. Locate the **Border** option.
4. Turn the border:

> **Off**

This removes the visible border around the shape.

---

# 8. Change the Fill Color

The shape's fill color can also be customized.

Under the style settings, the instructor selects a different:

> **Fill Color**

You can choose any suitable color according to the design of the report.

The instructor mentions that the exact color can be changed later if required.

### Important

The color chosen at this stage is not necessarily the final design.

The objective is simply to format the header/shape appropriately.

---

# 9. Enable Text on the Shape

The shape can also contain text.

The instructor enables the text option.

### Steps

Under the shape's:

> **Style**

settings:

1. Locate **Text**.
2. Change it to:

> **On**

Once enabled, text can be entered inside the shape.

---

# 10. Add Header Text

The instructor enters the following text:

> **Loan Default Overview**

This matches the name of the report page.

The shape therefore acts as a **header/title** for the report.

Conceptually:

```text
┌───────────────────────────────────────────────┐
│             Loan Default Overview             │
└───────────────────────────────────────────────┘
```

---

# 11. Format the Header Text

The text inside the shape can also be formatted.

The instructor mentions that you can change:

* Font style
* Font size
* Text formatting
* Boldness

### Font Style

Under the text formatting settings, select the desired font.

You can choose any font according to your report design.

### Font Size

The text size can be adjusted according to the available space.

### Bold

The text can also be made bold.

The instructor chooses to keep the text:

> **Bold**

This makes the report title more prominent.

---

# 12. Result of the Formatting

At this point, the report page has:

### Page name

> **Loan Default Overview**

### Header shape

A rounded-tab style shape positioned at the top of the report.

### Header text

> **Loan Default Overview**

### Formatting

* Border: Off
* Fill color: Customized
* Text: On
* Font: Customizable
* Font size: Customizable
* Bold: Enabled according to preference

---

# 13. Why This Formatting Is Useful

Although this may look like only a visual/design step, report formatting is important in Power BI.

A good report should not only provide correct analysis but should also be:

* Easy to understand
* Visually organized
* Easy to navigate
* Professionally designed
* Clear to business users

For example, a bank official looking at the report should immediately understand that the page represents:

> **Loan Default Overview**

rather than having to figure out what the page is about.

---

# 14. Upcoming KPI and DAX Work

The main purpose of this stage is not just formatting.

The instructor indicates that the next sessions will focus on creating:

### DAX Measures

Measures will be used to calculate important business metrics/KPIs dynamically.

Examples of KPIs could include:

* Total Loans
* Total Loan Amount
* Defaulted Loans
* Default Rate
* Average Credit Score
* Average Loan Amount

The exact KPIs will be created in the upcoming sessions.

---

### DAX Calculated Columns

Calculated columns may also be created where row-level calculations are required.

The distinction to remember is:

**Calculated Column**

```text
Calculated for each row
↓
Stored in the model
```

**Measure**

```text
Calculated dynamically
↓
Based on filter/context
↓
Primarily used in visuals/KPIs
```

The instructor will discuss the actual columns and measures required for this project in the next sessions.

---

# 15. KPIs and Visual Representation

After creating the required DAX measures/columns, they will be used to create visuals.

The instructor specifically mentions:

> **Representing KPIs using charts/visuals**

This means the report will eventually convert the calculated metrics into visual elements that can be easily interpreted by users.

For example:

```text
Raw Data
   ↓
DAX Measures / Columns
   ↓
KPIs
   ↓
Power BI Visuals
   ↓
Business Insights
   ↓
Loan Decision Making
```

---

# 16. Important Steps to Remember

### Rename the page

```text
Double-click Page 1
        ↓
Ctrl + A
        ↓
Type "Loan Default Overview"
        ↓
Enter
```

### Add a shape

```text
Insert
  ↓
Shapes
  ↓
Rounded Tab Top Right
```

### Format the shape

```text
Format Shape
      ↓
Styles
      ↓
Border → Off
      ↓
Fill Color → Choose suitable color
      ↓
Text → On
```

### Add title

```text
Text → Loan Default Overview
```

### Format title

Customize:

```text
Font Style
Font Size
Bold
```

---

# 17. Key Takeaways

> **1. The reporting phase starts after data preparation and validation.**

> **2. Report pages should be given meaningful names instead of leaving them as Page 1, Page 2, etc.**

> **3. The page is renamed to `Loan Default Overview`.**

> **4. Shapes can be used to create professional report headers and sections.**

> **5. The instructor uses `Insert → Shapes → Rounded Tab Top Right`.**

> **6. The shape is resized and positioned at the top of the report page.**

> **7. The shape border is turned off.**

> **8. A suitable fill color can be selected.**

> **9. Text is enabled inside the shape.**

> **10. The text `Loan Default Overview` is added.**

> **11. Font style, font size, and bold formatting can be customized.**

> **12. The upcoming sessions will focus on DAX measures, DAX calculated columns, KPIs, and their visual representation.**

### Overall flow of the project so far

```text
Data Source
     ↓
SQL Server
     ↓
Data Flow
     ↓
Power BI Desktop
     ↓
Power Query
     ↓
Data Profiling & Data Type Validation
     ↓
Close & Apply
     ↓
Report View
     ↓
Report Page Formatting
     ↓
DAX Measures & Calculated Columns
     ↓
KPIs
     ↓
Visualizations
     ↓
Loan Default Analysis
```
