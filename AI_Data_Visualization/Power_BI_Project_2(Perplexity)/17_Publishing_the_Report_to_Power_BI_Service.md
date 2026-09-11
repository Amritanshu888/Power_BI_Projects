# Detailed Notes: Publishing a Power BI Report to Power BI Service

This session explains how to **publish a Power BI Desktop report to Power BI Service**, open the published report online, and understand how **cross-filtering/interactions** work between visuals.

---

# 1. Objective of the Session

The main objective is to:

> **Publish the Power BI report created in Power BI Desktop to Power BI Service.**

The report that has been created contains **two report pages** with multiple charts and visualizations.

After publishing, the report can be opened and viewed in **Power BI Service**.

---

# 2. Prerequisite: Sign in to Power BI

Before publishing the report, you need to be signed into your Power BI account.

The instructor has already signed into the account.

### If you don't have a Power BI account

The instructor mentions that users who don't know how to create a free Power BI account should refer to the **Introduction section of the Power BI course**, where a separate video explains how to create a free account.

So, before publishing:

> **Power BI account + signed-in Power BI Desktop account are required.**

---

# 3. Save the Power BI Report Before Publishing

Before publishing, the report needs to be saved.

### Steps

1. Open the completed report in **Power BI Desktop**.
2. Go to the:

> **Home** tab

3. Click:

> **Publish**

However, before the publishing process can proceed, Power BI requires the report to be saved.

So the instructor clicks:

> **Save**

---

# 4. Give the Report a Name

Power BI asks for a name for the report/file.

The instructor names the report:

> **Power BI Banking**

The resulting Power BI Desktop file is:

> **Power BI Banking.pbix**

### Important

A `.pbix` file is the standard **Power BI Desktop report file format**.

---

# 5. Save the Report

After entering the report name:

1. Enter:

> **Power BI Banking**

2. Click:

> **Save**

3. Wait while Power BI saves the report.

The instructor mentions that this may take some time.

---

# 6. Publish the Report

Once the report has been saved, the instructor proceeds with publishing.

### Steps

1. Go to the **Home** tab.
2. Click:

> **Publish**

Power BI will ask where the report should be published.

---

# 7. Select a Workspace

Power BI Service organizes content using **workspaces**.

The instructor has several workspaces already created.

You may have fewer workspaces depending on your account.

For this demonstration, the instructor chooses:

> **My Workspace**

### Steps

1. Locate **My Workspace**.
2. Double-click/select it.
3. Wait while Power BI uploads the report.

The publishing process may take some time.

---

# 8. Report Successfully Published

After the publishing process finishes, Power BI provides an option to open the published report.

The instructor selects:

> **Open Power BI Banking.pbix**

The report then opens in **Power BI Service**.

### Important distinction

There are two environments involved:

**Power BI Desktop**

→ Used to create and develop the report.

**Power BI Service**

→ Used to publish, view, share, and work with the report online.

---

# 9. Report in Power BI Service

After opening the report in Power BI Service, the instructor confirms that the report has been successfully published.

The published report contains:

> **Two report pages**

---

# 10. First Report Page

The first page contains the visuals created earlier in the project.

The instructor demonstrates that the visuals are interactive.

### Example

If you click on a particular value in one visual:

> The other visuals on the page get filtered accordingly.

For example:

```text
Select value in Visual A
          ↓
Power BI applies filter
          ↓
Visual B changes
Visual C changes
Visual D changes
```

This is known as **cross-filtering / visual interaction**.

---

# 11. Interactive Filtering

The instructor clicks on values within the visuals to demonstrate the interaction.

When a value is selected:

> The other charts on the report page respond to that selection.

This allows users to perform interactive analysis without manually changing filters.

For example, if a user selects a particular account type, other visuals can update to show information relevant to that selection.

---

# 12. Second Report Page

The instructor then navigates to:

> **Page 2**

The same interactive behavior can be observed.

When values in certain charts are selected:

> Other charts respond and become filtered according to the selection.

This demonstrates that the report is not simply a collection of static charts.

Instead, the visuals are **connected through the underlying data model and DAX calculations**.

---

# 13. Important Exception: Monthly Transaction Balance by Month

At the end of the session, the instructor notices something important.

When selecting values in other visuals:

> **Monthly Transaction Balance by Month**

does **not get filtered**.

This is intentional and is related to the DAX measure used for that visual.

---

# 14. Why Is the Monthly Transaction Balance Chart Not Filtering?

The instructor explains that the reason is the type of DAX calculation used.

The measure uses the:

> **ALL except function**

The transcript refers to this as an **ALL except function**.

The important idea is that the DAX calculation is designed to **ignore certain filters**.

Therefore, when other visual elements are selected, the monthly transaction balance visual does not respond in the same way as the other charts.

---

# 15. Understanding the Filter Behavior

Normally:

```text
User selects a value
        ↓
Filter is applied
        ↓
Visual recalculates
        ↓
Chart changes
```

But when a DAX measure deliberately removes/ignores certain filters:

```text
User selects a value
        ↓
Filter is generated
        ↓
DAX measure ignores specified filter context
        ↓
Chart remains unchanged
```

This is why the **Monthly Transaction Balance by Month** chart does not get filtered by the selections demonstrated in the session.

---

# 16. Key DAX Concept: Filter Context

This session demonstrates an important Power BI/DAX concept:

> **Filter context**

A visual normally evaluates its measure based on the filters currently applied to it.

These filters can come from:

* Slicers
* Other visuals
* Page filters
* Report filters
* User selections
* Relationships between tables

However, DAX functions that modify filter context can change this behavior.

---

# 17. ALL and Filter Removal

The instructor specifically attributes the behavior to the DAX expression using an **ALL-related function**.

The important takeaway is:

> **ALL can remove filters from a table or column when evaluating a DAX expression.**

This can cause a measure to continue showing values based on a broader dataset rather than responding normally to selections.

The exact behavior depends on the complete DAX formula and where `ALL` is applied.

---

# 18. Publishing Workflow — Complete Steps

The complete publishing process demonstrated in the lecture is:

```text
Create Power BI Report
        ↓
Complete all report pages and visuals
        ↓
Sign in to Power BI account
        ↓
Power BI Desktop → Home
        ↓
Click Publish
        ↓
Save the report
        ↓
Give report a name
        ↓
Power BI Banking
        ↓
Save
        ↓
Choose Workspace
        ↓
My Workspace
        ↓
Wait for publishing
        ↓
Open Power BI Banking
        ↓
Report opens in Power BI Service
```

---

# 19. Power BI Desktop vs Power BI Service

This session is also useful for understanding the difference between the two.

| Power BI Desktop           | Power BI Service                        |
| -------------------------- | --------------------------------------- |
| Desktop application        | Cloud-based service                     |
| Used to create reports     | Used to access published reports        |
| Create visuals             | View/interact with published visuals    |
| Create DAX calculations    | Work with published content             |
| Transform/model data       | Share and collaborate on reports        |
| `.pbix` report development | Online report consumption/collaboration |

### Simple way to remember

> **Power BI Desktop = Build**

> **Power BI Service = Publish, access, share, and collaborate**

---

# 20. Important Terms

### **Publish**

Uploads a Power BI Desktop report to Power BI Service.

### **Workspace**

A container in Power BI Service where reports, semantic models/datasets, and other Power BI content can be organized.

### **My Workspace**

A personal workspace available to the user for their own Power BI content.

### **PBIX**

The file format used by Power BI Desktop.

Example:

> `Power BI Banking.pbix`

### **Cross-filtering**

Selecting data in one visual causes other related visuals to update based on the selection.

### **Filter Context**

The set of filters that determine what data a DAX measure evaluates.

### **ALL**

A DAX function that can remove filters from specified tables or columns when calculating a measure.

---

# 21. Key Takeaways

* Before publishing, make sure you are **signed into Power BI**.
* Save the Power BI report before publishing.
* The instructor names the report **Power BI Banking**.
* The report is saved as a `.pbix` file.
* Go to **Home → Publish** to publish the report.
* Select the desired **workspace**.
* The instructor publishes to **My Workspace**.
* After publishing, choose the option to **Open Power BI Banking**.
* The report opens in **Power BI Service**.
* The published report contains **two pages**.
* Power BI visuals are interactive: selecting one visual can filter other visuals.
* This behavior is called **cross-filtering/visual interaction**.
* The **Monthly Transaction Balance by Month** visual does not respond to certain selections because its DAX measure uses an **ALL-related filter-removal calculation**.
* This demonstrates how **DAX can control filter context**.
* The next sessions will move on to other important Power BI topics.
