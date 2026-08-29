# Power BI Lecture Notes — Testing Scheduled Refresh & Republishing Report Changes

This lecture covers **two important concepts**:

1. **Verifying that Scheduled Refresh is working correctly**
2. **Understanding the difference between data-source changes and report-design changes**, and when you need to republish the report.

---

# 1. Verify That Scheduled Refresh Is Working

In the previous lecture, Scheduled Refresh was configured for the report.

Now the objective is to verify whether the scheduled refresh actually worked.

The instructor had previously scheduled the refresh for approximately **4:30 AM**.

At the time of this test, it is approximately **4:40 AM**, so the instructor checks whether the updated data has appeared in the Power BI report.

---

# 2. Open the Power BI Account

### Steps

1. Open **Power BI Service**.
2. Click the account name at the top-right.
3. Click **View account**.
4. Go to the **Home** tab.

---

# 3. Open the Workspace

The report was published to:

### **Test Power BI Project Two**

### Steps

1. Click **Home**.
2. Click **Workspaces**.
3. Open **Test Power BI Project Two**.
4. Open the report that was published to this workspace.

---

# 4. Verify the Updated Data

The instructor had previously made changes to the underlying dataset.

Specifically:

> **Four new records were added in the backend Microsoft SQL Server database.**

Because Scheduled Refresh was configured, these changes should now be reflected in Power BI.

The instructor observes that the report has changed.

### Female count

Previously:

**5,000**

After refresh:

**5,001**

### Male count

Previously:

**5,000**

After refresh:

**5,003**

Therefore, the total customer count has increased as a result of the four new records.

### Premium Amount

Previously:

**5.97 million**

After refresh:

**5.98 million**

These changes demonstrate that the scheduled refresh successfully retrieved the updated data from the underlying SQL Server data source.

---

# 5. Why Did the Data Change?

The important sequence is:

```text
Microsoft SQL Server
        ↓
4 new records added
        ↓
Scheduled Refresh runs
        ↓
Power BI Semantic Model refreshes
        ↓
Power BI Report reflects updated data
```

The instructor had configured the scheduled refresh for approximately **4:30 AM**.

At approximately **4:40 AM**, the report is checked.

The updated values are now visible.

Therefore:

> **Scheduled Refresh is working successfully.**

---

# 6. Check Refresh History

Power BI also provides a way to verify whether refreshes succeeded or failed.

This is useful because simply seeing updated data isn't the only way to verify refresh status.

### Steps

1. Go to **Workspaces**.
2. Open **Test Power BI Project Two**.
3. Locate the **Semantic Model**.
4. Open the **Schedule Refresh** settings.
5. Check the refresh information/history.

The lecture shows a refresh entry similar to:

### Last Refresh

**Succeeded**

with a timestamp around:

**14/07/2024 4:30:42 AM**

And the next scheduled refresh is shown as:

**15/07/2024 4:30 AM**

The exact dates/times are part of the demonstration; the important concept is that Power BI records the status and timing of refreshes.

---

# 7. Refresh History

The refresh history allows you to determine:

* When the last refresh occurred.
* Whether it succeeded.
* When the next refresh is scheduled.
* Whether previous refreshes failed.

Therefore, if your data isn't updating as expected, **Refresh History** is an important place to investigate.

---

# 8. Refresh Failures

The lecture specifically points out that refresh history can also help identify:

### Refresh failures

If a scheduled refresh fails, you can check the refresh history to identify that failure.

So the basic troubleshooting flow is:

```text
Data not updated?
       ↓
Check Semantic Model
       ↓
Check Schedule Refresh
       ↓
Check Refresh History
       ↓
Check whether refresh succeeded/failed
```

---

# 9. Important: Scheduled Refresh vs. Report Changes

The lecture then moves to another very important concept.

The instructor previously added a **second page** to the Power BI report while demonstrating **Drill Through** functionality.

So the Power BI Desktop report now contains:

* Page 1
* Page 2

However, when the instructor opens the report in Power BI Service, only **one page** is visible.

This creates an important question:

> Why isn't the second page visible in Power BI Service?

---

# 10. Reason: The Report Was Not Republished

The reason is:

> The report was modified in **Power BI Desktop**, but it was **not published again** after the modification.

This is a very important distinction.

The instructor had added the second page locally in Power BI Desktop.

But Power BI Service was still displaying the **previously published version**.

Therefore:

### Power BI Desktop

Contains:

**Page 1 + Page 2**

### Power BI Service

Still contains:

**Page 1 only**

because the updated report had not been republished.

---

# 11. When Do You Need to Republish?

If you make changes to the **report itself** in Power BI Desktop, you need to publish the updated report again to Power BI Service.

Examples of report changes include:

* Adding a new report page
* Adding a visual
* Removing a visual
* Changing report design
* Changing formatting
* Modifying report layout
* Adding drill-through functionality

In this example:

> A second page was added to the report.

Therefore, the report needs to be republished.

---

# 12. Open the Report in Power BI Desktop

The instructor returns to Power BI Desktop.

The local report now contains:

### Page 1

Original report page.

### Page 2

New page added for **Drill Through** functionality.

The instructor wants both pages to appear in Power BI Service.

---

# 13. Republish the Updated Report

### Steps

1. Open the updated report in **Power BI Desktop**.
2. Click **Publish**.
3. Select the appropriate workspace:
   **Test Power BI Project Two**
4. Click **Select**.
5. Power BI detects that a report with the same name already exists in the workspace.

Power BI asks whether you want to replace the existing report.

---

# 14. Replace the Existing Report

Since the local report contains the latest changes, select:

### **Yes / Replace**

The old published version will be replaced by the newer version.

Power BI then takes some time to publish the updated report.

---

# 15. Verify the Republished Report

After publishing:

1. Open the report from the Power BI Service workspace.
2. Wait for it to load.
3. Look at the page navigation on the left.

Now the report contains:

### Page 1

Original report page.

### Page 2

The newly added drill-through/detail page.

Therefore, the second page is now visible in Power BI Service.

---

# 16. Why Did the Second Page Appear Now?

Because the updated Power BI Desktop file was republished.

The sequence is:

```text
Power BI Desktop
       │
       │ Add Page 2
       ↓
Updated Report
       │
       │ Publish
       ↓
Power BI Service
       │
       ↓
Updated Report
Page 1 + Page 2
```

Before republishing:

```text
Power BI Desktop → Page 1 + Page 2

Power BI Service → Page 1
```

After republishing:

```text
Power BI Desktop → Page 1 + Page 2

Power BI Service → Page 1 + Page 2
```

---

# 17. Critical Difference: Report Changes vs. Data Changes

This is probably the **most important concept of this lecture**.

There are two different types of changes.

---

## A. Changes to the Report

Examples:

* Adding a new page
* Adding a visual
* Changing visual formatting
* Changing report layout
* Adding drill-through functionality

For these changes:

### You need to **publish the report again**.

Flow:

**Power BI Desktop → Make Report Changes → Publish Again → Power BI Service**

---

## B. Changes to the Data Source

Examples:

* New records added
* Existing data modified
* Data source receives new transactions

For these changes:

### You need **Scheduled Refresh**.

You don't need to manually redesign and republish the report just because new data has arrived.

Flow:

**Data Source → Scheduled Refresh → Semantic Model Updated → Report Shows Updated Data**

---

# 18. Side-by-Side Comparison

| Change        | Example                 | What is required? |
| ------------- | ----------------------- | ----------------- |
| Report change | Add a new page          | Publish again     |
| Report change | Add a new visual        | Publish again     |
| Report change | Change report layout    | Publish again     |
| Report change | Add Drill Through       | Publish again     |
| Data change   | Add new records         | Scheduled Refresh |
| Data change   | Modify source data      | Scheduled Refresh |
| Data change   | New transactions arrive | Scheduled Refresh |

### Easy way to remember:

> **Changed the report → Republish**

> **Changed the data → Refresh**

---

# 19. Scheduled Refresh Does NOT Publish Report Design Changes

This is an important distinction.

Suppose you:

1. Add a new page in Power BI Desktop.
2. Add a new visual.
3. Save the PBIX.
4. Do not publish it.

Even if Scheduled Refresh runs successfully in Power BI Service:

**The new page/visual will NOT automatically appear in the service.**

Why?

Because Scheduled Refresh refreshes the **data**, not the unpublished report design.

You must publish the updated report.

---

# 20. Example From This Lecture

### Situation 1 — New SQL records

Four records were added to Microsoft SQL Server.

Scheduled Refresh runs.

Result:

* Female count changes from 5,000 → 5,001.
* Male count changes from 5,000 → 5,003.
* Premium amount changes from 5.97M → 5.98M.

**No manual republishing was required for these data changes.**

---

### Situation 2 — New Report Page

A second page was added to Power BI Desktop for Drill Through.

The report wasn't republished.

Result:

**Power BI Service still showed only Page 1.**

After publishing again:

**Power BI Service showed Page 1 + Page 2.**

---

# 21. Overall Power BI Deployment Flow

The lecture effectively demonstrates the following complete lifecycle:

```text
             POWER BI DESKTOP
                    │
          Build / Modify Report
                    │
                    ▼
                 PUBLISH
                    │
                    ▼
             POWER BI SERVICE
                    │
                    ▼
               WORKSPACE
                    │
          ┌─────────┴─────────┐
          │                   │
          ▼                   ▼
       REPORT          SEMANTIC MODEL
          │                   │
          │                   │
    Report changes       Data changes
          │                   │
          ▼                   ▼
      REPUBLISH        SCHEDULED REFRESH
                              │
                              ▼
                       Updated Data
```

---

# 22. Key Takeaways

### Scheduled Refresh

Used to automatically update the **data** in the Power BI semantic model when the underlying data source changes.

### Refresh History

Used to check:

* Last refresh
* Refresh status
* Next scheduled refresh
* Refresh failures

### Republish

Required when the **report itself** has been changed in Power BI Desktop.

### Example

Adding a new page:

**Power BI Desktop → Add Page → Publish Again**

### Data source update

Adding records to SQL Server:

**SQL Server → Scheduled Refresh → Updated Power BI Data**

---

# 23. Final Revision Notes

Remember these two rules:

> **REPORT CHANGED → PUBLISH AGAIN**

> **DATA CHANGED → SCHEDULED REFRESH**

And if you want to verify whether scheduled refresh worked:

**Workspace → Semantic Model → Schedule Refresh → Refresh History**

The lecture concludes by noting that the last few sessions covered **Drill Through Filters** and **Scheduled Refresh**, and the next sessions will move on to other Power BI functionalities.
