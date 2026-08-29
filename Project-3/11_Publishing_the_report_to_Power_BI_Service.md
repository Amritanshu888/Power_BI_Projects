# Detailed Notes: Publishing a Power BI Report to Power BI Service

## 1. Objective of the Lecture

In this lecture, the focus is on **publishing a Power BI report created in Power BI Desktop to Power BI Service**.

The lecture also explains an important difference between **using bookmarks in Power BI Desktop** and **using bookmarks after the report has been published to Power BI Service**.

### Key objectives

* Sign in to Power BI.
* Publish the report from **Power BI Desktop** to **Power BI Service**.
* Publish the report to **My workspace**.
* Open the published report in Power BI Service.
* Understand how bookmarks are selected in Power BI Service.
* Understand the difference between bookmark interaction in Desktop and Service.

---

# 2. Sign In to Power BI

Before publishing the report, the user must be signed in to a Power BI account.

### Current state

The Power BI Desktop application is **not signed in**.

### Steps to sign in

1. Open the **Home** tab in Power BI Desktop.
2. Click **Sign in**.
3. Enter the email address associated with the Power BI account.
4. Click **Continue/Next**.
5. Enter the account password.
6. Complete the sign-in process.
7. If Power BI presents an option such as **Ask later**, select it if appropriate.

> **Note:** The instructor mentions that a new account was created for this purpose and refers learners to previous lectures for instructions on creating a free Power BI account.

### Result

After successful authentication, Power BI Desktop shows that the user is signed in.

---

# 3. Publishing the Report to Power BI Service

Once signed in, the report can be published online.

### Steps

1. Go to the **Home** tab in Power BI Desktop.
2. Click **Publish**.
3. Power BI will ask where the report should be published.
4. Select **My workspace**.
5. Click **Select**.

Power BI then begins publishing the report.

### What happens during publishing?

Power BI uploads the report from **Power BI Desktop** to the selected workspace in **Power BI Service**.

The publishing process may take some time.

Once publishing is complete, Power BI provides a link that can be used to open the report in Power BI Service.

---

# 4. Opening the Published Report in Power BI Service

After the report has been published:

1. Click the link provided by Power BI.
2. This opens the report in **Power BI Service** through a web browser.
3. If prompted to choose an account, select/use the account to which the report was published.
4. Sign in if necessary.

The published report will now be available online.

---

# 5. Using Bookmarks in Power BI Desktop vs. Power BI Service

A major point of this lecture is the difference in how bookmarks are activated in:

* **Power BI Desktop**
* **Power BI Service**

The report contains bookmarks that allow the user to switch between different chart views.

For example:

* **Line Chart**
* **Column Chart**

These bookmarks provide users with the ability to change the visualization without creating separate report pages.

---

# 6. Selecting Bookmarks in Power BI Desktop

In Power BI Desktop, when using bookmark buttons, the instructor explains that you need to use:

**Ctrl + Click**

### Example

Suppose there are two bookmark buttons:

* Line Chart
* Column Chart

To activate a bookmark in Power BI Desktop:

1. Hold down the **Ctrl** key.
2. Click the bookmark/button.

Without holding Ctrl, the button is essentially selected rather than activated.

### Example workflow

If the current view is a column chart and you want to switch to a line chart:

**Ctrl + Click → Line Chart bookmark**

The report view changes to the line chart.

---

# 7. Selecting Bookmarks in Power BI Service

After publishing the report to Power BI Service, the interaction is different.

You **do not need to press Ctrl**.

You can activate the bookmark with a normal single click.

### Steps

1. Open the published report in Power BI Service.
2. Locate the bookmark buttons.
3. Simply click the desired bookmark.
4. The report view changes immediately.

### Example

If the report currently displays a column chart:

**Click "Line Chart" → Line chart view appears**

Then:

**Click "Column Chart" → Column chart view appears**

No Ctrl key is required.

---

# 8. Why This Difference Matters

This is an important practical distinction when developing and testing Power BI reports.

| Environment          | How to activate bookmark |
| -------------------- | ------------------------ |
| **Power BI Desktop** | **Ctrl + Click**         |
| **Power BI Service** | **Single Click**         |

### Important takeaway

The **Ctrl + Click requirement is specific to the Power BI Desktop editing environment**.

Once the report is published and viewed in Power BI Service, the report behaves more like a finished interactive report, so users can simply click the bookmark buttons.

---

# 9. Example of the Bookmark Interaction

The report contains two possible chart views:

### Bookmark 1: Line Chart

When the **Line Chart** bookmark is selected:

* The report displays the line chart.
* The view changes according to the bookmark configuration.

### Bookmark 2: Column Chart

When the **Column Chart** bookmark is selected:

* The report displays the column chart.
* The view changes back to the column-chart configuration.

Therefore, bookmarks can be used to provide users with an easy way to switch between different visualizations.

---

# 10. Complete Publishing Workflow

The overall workflow demonstrated in the lecture is:

### In Power BI Desktop

**Step 1:** Open the report.

**Step 2:** Sign in to Power BI.

**Step 3:** Go to **Home**.

**Step 4:** Click **Publish**.

**Step 5:** Select **My workspace**.

**Step 6:** Click **Select**.

**Step 7:** Wait for the report to be published.

### In Power BI Service

**Step 8:** Open the link to the published report.

**Step 9:** Sign in with the appropriate account if required.

**Step 10:** Open the published report.

**Step 11:** Test the bookmarks.

**Step 12:** Click the bookmark buttons normally to switch between views.

---

# 11. Important Concepts to Remember

### Power BI Desktop

Power BI Desktop is primarily the environment where the report is **created and edited**.

When testing bookmark buttons in Desktop, use:

> **Ctrl + Click**

### Power BI Service

Power BI Service is the online environment where the published report can be **viewed and interacted with**.

When using bookmarks in the Service:

> **Simply click the bookmark**

### My Workspace

**My workspace** is the personal workspace used in this demonstration to publish the report.

---

# 12. Key Takeaways

* A Power BI report created in Desktop can be published to **Power BI Service**.
* You must be **signed in** before publishing.
* The publishing process can be started from **Home → Publish**.
* The report can be published to **My workspace**.
* After publishing, the report can be opened using the link provided by Power BI.
* Bookmarks can be used to switch between different report views, such as a **line chart and column chart**.
* In **Power BI Desktop**, bookmark buttons require **Ctrl + Click** during editing/testing.
* In **Power BI Service**, bookmarks can be activated with a **normal single click**.
* Publishing the report makes it available in the Power BI Service for online interaction.
