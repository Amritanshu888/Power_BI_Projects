# Power BI – Publishing a Report to Power BI Service

## 1. Objective of the Session

The objective of this session is to **publish the Power BI report created in Power BI Desktop to Power BI Service**.

The overall process is:

1. Sign in to a Power BI account.
2. Open the **Publish** option in Power BI Desktop.
3. Select the destination workspace.
4. Publish the `.pbix` report.
5. Open the published report in Power BI Service.
6. Verify that the report has been published successfully.

---

# 2. Requirement – Power BI Account

Before publishing a report, you need to be **signed in to a Power BI account**.

The instructor mentions that if you don't already have an account, you should refer to the **Introduction section of the course**, where the process of creating a free account is explained.

### Important

The account created during that process will be used to:

* Sign in to Power BI Desktop.
* Publish reports.
* Access the reports in Power BI Service.

---

# 3. Check Whether You Are Signed In

In **Power BI Desktop**, look at the **top-right corner** of the application.

You will see the account/sign-in option there.

### If you are already signed in

Clicking the account option will show an option such as:

**Sign out**

This confirms that you are currently signed in.

### If you are not signed in

You will be given the option to **Sign in**.

---

# 4. Sign In to Power BI

If you haven't signed in yet:

1. Go to the **top-right corner** of Power BI Desktop.
2. Click the **Sign in** option.
3. Enter the credentials associated with your Power BI account.
4. Complete the sign-in process.

Once successfully signed in, you can proceed with publishing the report.

---

# 5. Publish the Report

Once you are signed in, you can publish the report.

### Steps

1. Go to the **Home** tab in Power BI Desktop.
2. Click **Publish**.

The publish option is available from the Home ribbon.

---

# 6. Save Changes Before Publishing

When the Publish operation is initiated, Power BI may ask whether you want to save changes.

The instructor selects:

**Yes**

So, if prompted:

> Save the changes before proceeding with publishing.

Power BI may take some time to process the report.

---

# 7. Select the Destination Workspace

After clicking Publish, Power BI asks where you want to publish the report.

A list of available workspaces will appear.

In this lecture, the instructor chooses:

**My Workspace**

### Steps

1. Select **My Workspace**.
2. Click **Select**.

The report will then be uploaded/published to that workspace.

---

# 8. Report Being Published

Power BI starts publishing the `.pbix` file.

The lecture refers to the report as:

**Housing Copy.pbix**

The publishing process may take some time depending on the report and connection.

Once completed, Power BI displays a confirmation indicating that the report has been successfully published.

---

# 9. Open the Report in Power BI Service

After successful publishing, Power BI provides an option to open the report in **Power BI Service**.

### Steps

1. After the publishing confirmation appears, click the option to **Open the report in Power BI**.
2. Power BI Service opens in the browser.
3. The published report can now be viewed online.

This demonstrates the connection between:

```text
Power BI Desktop
       ↓
     Publish
       ↓
Power BI Service
```

---

# 10. Verify the Published Report

After opening Power BI Service, the instructor verifies the report.

The report contains **two pages** at this stage.

The instructor mentions that additional pages could potentially be added later.

So the current report structure is:

```text
Housing Report
│
├── Page 1
│
└── Page 2
```

The exact visuals on each page were created in the previous sessions.

---

# 11. Other Reports Published to the Same Power BI Account

The instructor then goes to the **Home** section and demonstrates that other reports have also been published to the same Power BI account.

This shows that Power BI Service can contain multiple reports/projects.

Examples shown in the lecture include:

### Cricket Data Analysis

A report associated with a project involving:

* Cricket data analysis
* Web scraping

This demonstrates another Power BI project that was previously published.

---

### SharePoint and Power BI Report

Another report shown is related to a project where:

**SharePoint was used as the data source.**

This demonstrates that Power BI reports can be built using different data sources and then published to Power BI Service.

---

### Mobile Data Analysis

The instructor also shows a **Mobile Data Analysis** report.

This is another previously published report available in the Power BI account.

---

# 12. Multiple Reports in Power BI Service

The key point demonstrated here is that once reports are published, they become available within the Power BI environment associated with your account/workspace.

For example:

```text
My Workspace
│
├── Housing Report
├── Cricket Data Analysis
├── SharePoint / Power BI Report
└── Mobile Data Analysis
```

The exact list depends on the reports that you have previously published.

---

# 13. Power BI Desktop vs Power BI Service

This session also demonstrates the basic workflow between the two environments.

### Power BI Desktop

Used primarily for:

* Connecting to data
* Data transformation
* Data modeling
* Creating DAX calculations
* Creating reports and visuals
* Designing report pages

### Power BI Service

Used for:

* Hosting published reports
* Viewing reports online
* Sharing reports
* Managing reports/workspaces
* Working with reports after publishing

The basic workflow is:

```text
Build Report in Power BI Desktop
             ↓
        Sign in
             ↓
          Publish
             ↓
      Select Workspace
             ↓
     Power BI Service
             ↓
       View Report
```

---

# 14. Complete Publishing Procedure

Here is the complete process from beginning to end:

### Step 1 – Open the report

Open the `.pbix` report in **Power BI Desktop**.

### Step 2 – Sign in

Go to the **top-right corner** and make sure you are signed in.

If not:

**Sign in → Enter Power BI account credentials**

### Step 3 – Go to Home

Click:

**Home**

### Step 4 – Publish

Click:

**Publish**

### Step 5 – Save Changes

If Power BI asks whether to save changes:

**Click Yes**

### Step 6 – Select Workspace

Choose:

**My Workspace**

### Step 7 – Confirm

Click:

**Select**

### Step 8 – Wait

Allow Power BI some time to upload/publish the `.pbix` file.

### Step 9 – Confirmation

Once publishing is complete, Power BI displays a success message.

### Step 10 – Open in Power BI Service

Click:

**Open in Power BI**

The report opens in Power BI Service.

---

# 15. Important Points to Remember

### Account is required

You need a Power BI account to publish your report to Power BI Service.

### Sign-in is done from Power BI Desktop

Use the account option in the **top-right corner** of Power BI Desktop.

### Publishing starts from Home

The main sequence is:

**Home → Publish**

### Workspace must be selected

You need to choose a destination workspace.

In this lecture:

**My Workspace → Select**

### `.pbix` file is published

The Power BI Desktop report file is uploaded to Power BI Service.

### Reports can be opened online

After publishing, use the provided **Open in Power BI** option to view the report in Power BI Service.

### Multiple projects can be published

The instructor demonstrates that the same Power BI account can contain reports from multiple projects, such as:

* Housing analysis
* Cricket data analysis
* SharePoint-based analysis
* Mobile data analysis

---

# 16. Key Takeaway

The main learning from this session is the **Power BI publishing workflow**:

```text
Create Report
     ↓
Power BI Desktop
     ↓
Sign in to Power BI Account
     ↓
Home → Publish
     ↓
Save Changes
     ↓
Select My Workspace
     ↓
Select
     ↓
Report Published
     ↓
Open in Power BI
     ↓
Power BI Service
```

So, after completing the report development in **Power BI Desktop**, you can publish the `.pbix` file to a workspace in **Power BI Service** and access the report online.
