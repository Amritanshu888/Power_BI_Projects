# Detailed Notes: Changing Date Data Types Using Locale in Power Query

## 1. Purpose of the Session

The session continues **data cleaning/data type transformation in Power Query Editor**.

The main focus is on correctly changing the data types of the remaining **date columns**, especially:

* **DOB (Date of Birth)**
* **Open Date**

The instructor emphasizes that even if directly changing a column to `Date` works with the current dataset, it may cause errors when **new data is added in the future**. Therefore, using **Data Type → Using Locale** is a safer and more reliable approach.

---

# 2. Why Use "Using Locale" for Date Columns?

Date values can be written in different formats depending on the **locale/country**.

For example:

* `MM/DD/YYYY` → commonly used in the **United States**
* `DD/MM/YYYY` → commonly used in India and many other countries

If Power BI/Power Query interprets the date using the wrong format, it can produce:

* Incorrect dates
* Conversion errors
* Blank/null values
* Data refresh problems when future data has a different format

### Key idea

Instead of simply selecting:

> **Data Type → Date**

use:

> **Data Type → Using Locale → Date → English (United States)**

This explicitly tells Power Query **how the date should be interpreted**.

---

# 3. Revisiting the Other Columns

The instructor opens the **Power Query Editor** again to review the remaining columns.

The earlier session had already dealt with the **Transaction Date** column.

For Transaction Date, the data type was changed using **Using Locale**.

Now the same approach is applied to the other date columns.

---

# 4. Phone Number Column

The instructor also mentions the **Phone Number** column.

Previously, the phone number column was changed to:

> **Whole Number**

The instructor notices that the corresponding transformation step may have accidentally been deleted.

However, this is not a major issue because the transformation can simply be applied again.

### Step

Select the **Phone Number** column and set its data type to:

> **Whole Number**

### Important point

The instructor says:

> "This change probably I mistakenly deleted a step."

But there is no problem because Power Query allows the transformation to be reapplied.

---

# 5. Changing the DOB Column Data Type

The next important column is:

> **DOB**

DOB = **Date of Birth**

The instructor wants to make sure this column is converted to a proper date using the correct locale.

## Steps

### Step 1: Locate the DOB column

Scroll horizontally to the right in Power Query Editor until the **DOB** column is visible.

### Step 2: Open the data type menu

Click the **data type icon/drop-down** associated with the DOB column.

### Step 3: Select "Using Locale"

Choose:

> **Using Locale**

This opens the locale configuration dialog.

### Step 4: Select the data type

Set the data type to:

> **Date**

### Step 5: Select the locale

Change the locale to:

> **English (United States)**

So the final configuration is:

**Data Type:** Date
**Locale:** English (United States)

### Step 6: Click OK

Click:

> **OK**

Power Query will now interpret the DOB values according to the selected US date format.

---

# 6. Changing the Open Date Column

Another date column in the dataset is:

> **Open Date**

This column needs to be treated in the same way as DOB.

## Steps

### Step 1: Locate Open Date

Find the **Open Date** column in Power Query Editor.

### Step 2: Open the data type menu

Click the data type icon/drop-down for **Open Date**.

### Step 3: Select "Using Locale"

Choose:

> **Using Locale**

### Step 4: Set data type

Select:

> **Date**

### Step 5: Set locale

Choose:

> **English (United States)**

### Step 6: Click OK

Click:

> **OK**

The Open Date column is now explicitly converted to a date using the US locale.

---

# 7. Why the Instructor Does This Even Though There Are No Current Errors

An important point from the lecture is that **the current data may not produce an error**, but future data might.

Previously, the instructor had directly changed certain columns to the `Date` type.

That worked because the current values happened to be interpreted correctly.

However:

> **Future data could potentially have values that Power Query cannot interpret correctly.**

Therefore, explicitly specifying the locale makes the transformation more robust.

### Example

Suppose a date is:

`04/05/2025`

Depending on the locale, this could mean:

* **April 5, 2025** → MM/DD/YYYY
* **May 4, 2025** → DD/MM/YYYY

By specifying **English (United States)**, Power Query knows that the first number represents the month.

---

# 8. Close & Apply

Once the necessary transformations are completed, the instructor closes Power Query and loads the changes into the Power BI model.

## Steps

In Power Query Editor:

1. Verify the transformations.
2. Click:

   > **Close & Apply**
3. Power BI begins applying the transformations.
4. The data is loaded into the Power BI data model.

### Important

The loading process may take some time, particularly when there is a larger dataset.

---

# 9. Checking for Errors During Data Load

After clicking **Close & Apply**, Power BI processes the transformations.

The instructor waits to see whether any errors occur.

If the transformations create problems during loading, Power BI would indicate that errors were encountered.

In this case:

> **No errors were thrown.**

Therefore, the transformations were successfully applied.

---

# 10. Verify the Open Date Column in Table View

After the data loads, the instructor goes to:

> **Table View**

This allows the transformed data to be inspected directly.

The instructor checks the **Open Date** column.

The values now appear as dates, using a format similar to:

> **MM/DD/YYYY**

The exact display format is not the main concern at this point.

The important thing is that Power BI recognizes the values as **dates** rather than text.

---

# 11. Verify the DOB Column

The instructor also checks the **DOB** column.

The DOB column contains:

* Date values
* Some blank values

For example, conceptually:

| DOB        |
| ---------- |
| 05/12/1990 |
| 10/25/1988 |
| Blank      |
| 03/17/1995 |

The presence of blanks is not necessarily an error.

### Important distinction

A blank DOB value does **not** mean that the entire column has a data type problem.

If the available values are correctly recognized as dates and some records simply have no DOB information, those blanks can remain.

---

# 12. Transaction Date Column

The instructor also confirms that the **Transaction Date** column has been handled similarly.

It is already configured as a date using the appropriate locale.

The Transaction Date values are therefore recognized as dates.

---

# 13. Date Display Format vs. Data Type

This is an important concept from the lecture.

The instructor mentions that the date format displayed in the table can be changed, but for now they will **leave it as it is**.

There are two separate concepts:

### Data Type

Determines what the value **actually is**.

For example:

> Date

### Display Format

Determines **how the value is shown** to the user.

For example:

`09/11/2026`

or

`11-Sep-2026`

or

`September 11, 2026`

These are different representations of the same date.

### Key takeaway

> **Changing the display format does not necessarily change the underlying data type.**

The lecture is primarily concerned with ensuring that the columns have the correct **Date data type**.

---

# 14. Checking the Date Format in Report View

After checking the table, the instructor moves to:

> **Report View**

The instructor clicks the relevant drop-down and observes that the dates are displayed in the format currently configured by Power BI.

The instructor does **not** change the format at this point.

The current display is acceptable for the purpose of the lecture.

---

# 15. Overall Workflow

The complete workflow covered in this session can be summarized as:

**Open Power Query Editor**

↓

**Review remaining columns**

↓

**Phone Number → Whole Number**

↓

**DOB → Using Locale → Date → English (United States)**

↓

**Open Date → Using Locale → Date → English (United States)**

↓

**Click Close & Apply**

↓

**Wait for data to load**

↓

**Check for errors**

↓

**No errors → Open Table View**

↓

**Verify Open Date**

↓

**Verify DOB**

↓

**Verify Transaction Date**

↓

**Go to Report View**

↓

**Begin report creation in the upcoming sessions**

---

# 16. Key Concepts / Keywords

### **Power Query Editor**

Used for importing, cleaning, transforming, and preparing data before it is loaded into the Power BI model.

### **Data Type**

Defines what kind of data a column contains, such as:

* Text
* Whole Number
* Decimal Number
* Date
* Date/Time
* True/False

### **Using Locale**

Allows Power Query to interpret values according to a specific country's/regional formatting rules.

### **Locale**

A regional setting that determines conventions such as:

* Date format
* Number format
* Decimal separators
* Currency conventions

### **English (United States)**

The locale selected in this lecture for interpreting the date columns.

### **Close & Apply**

Applies the Power Query transformations and loads the transformed data into the Power BI data model.

### **Table View**

Used to inspect the actual rows and columns of the loaded data.

### **Report View**

Used to create reports, charts, visualizations, slicers, and dashboards.

---

# 17. Important Exam/Interview Takeaways

### 1. Why use Using Locale?

Because simply changing a column to `Date` may work for the current dataset but can potentially fail when future data contains values that require different date interpretation.

### 2. What was the locale used?

> **English (United States)**

### 3. What data type was selected?

> **Date**

### 4. Which date columns were specifically changed?

* **DOB**
* **Open Date**

Transaction Date had already been handled using the same approach.

### 5. What happened to Phone Number?

It was set to:

> **Whole Number**

The instructor noted that this transformation step had accidentally been deleted and therefore reapplied it.

### 6. Were there any errors after applying the transformations?

> **No errors.**

### 7. Were there blanks in DOB?

> **Yes.**

But the blanks did not prevent the column from being treated as a date column.

### 8. Did the instructor change the date display format?

> **No.**

The existing display format was left as it was for now.

### 9. What happens after Power Query transformations?

The data is loaded into the **Power BI data model**, after which it can be inspected in Table View and used for report creation.

---

## Final Summary

The main lesson of this session is:

> **For date columns, don't rely only on directly changing the data type to Date. When date formatting depends on regional conventions, use "Using Locale" and explicitly specify the correct locale.**

In this session:

**DOB → Date → English (United States)**
**Open Date → Date → English (United States)**
**Transaction Date → already handled similarly**
**Phone Number → Whole Number**

After applying these transformations, the instructor used **Close & Apply**, confirmed that **no errors occurred**, verified the results in **Table View**, and then moved to **Report View**. The next sessions will begin the **report creation** process.

Available next action: Create a downloadable DOCX file here in this chat containing the editable prose above
