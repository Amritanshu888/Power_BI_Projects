# Power BI Lecture Notes — Publishing a Report to Power BI Service

This lecture explains how to **publish a Power BI Desktop report to Power BI Service**, how to select a workspace, how to create a new workspace, how to republish a report to that workspace, and how to share the report with other users. It also introduces **scheduled refresh**, which is covered in the next lecture.

---

# 1. Power BI Desktop vs. Power BI Service

The report has currently been created in **Power BI Desktop**.

The next step is to publish this report to **Power BI Service**, which the lecture refers to as the **second element of Power BI**.

### Basic flow

**Power BI Desktop**

→ Create/report development

→ **Publish**

→ **Power BI Service**

→ Share/access/manage the report

---

# 2. Requirement: Power BI Account

Before publishing a report, you need a **Power BI account**.

The instructor mentions that a separate video was created explaining how to create a **free Power BI account**.

Therefore, if you don't already have an account:

1. Create the Power BI account.
2. Sign in using that account.
3. Return to Power BI Desktop.
4. Follow the publishing process.

The account used in the demonstration is an **organizational/work or school account**. 

---

# 3. Sign In to Power BI Desktop

At the top-right of Power BI Desktop, the instructor initially sees:

**Sign in**

This indicates that Power BI Desktop is not currently signed in.

### Steps

1. Open the Power BI report in **Power BI Desktop**.
2. Look at the **top-right corner**.
3. Click **Sign in** if required.
4. When prompted, provide the work/school or organizational Power BI account.
5. Enter the password.
6. Complete the sign-in process.

The demonstration uses an organizational account created specifically for Power BI. 

---

# 4. Publish the Report to Power BI Service

Once signed in:

### Steps

1. In Power BI Desktop, click **Publish**.
2. Power BI asks you to choose the destination/workspace.
3. Select the appropriate workspace.

Initially, the instructor has not created any custom workspace, so Power BI provides:

### **My Workspace**

as the available destination.

The report is therefore published to **My Workspace** initially.

---

# 5. What Is a Workspace?

A **workspace** is essentially a container where Power BI content is stored.

According to the lecture, a workspace contains things such as:

* Reports
* Dashboards
* Datasets

Therefore, conceptually:

**Workspace = Container for Power BI content**

For the initial demonstration, because no additional workspace has been created, the report is published to **My Workspace**. 

---

# 6. Publish to "My Workspace"

### Steps

1. Click **Publish** in Power BI Desktop.
2. Select **My Workspace**.
3. Click **Select**.
4. Power BI starts publishing the report.
5. Wait for the publishing process to complete.

After publishing, Power BI provides a link similar to:

**Open [report name] in Power BI**

The instructor's report is named something similar to **PBIX PBI 2**.

Clicking this link opens the report in **Power BI Service**. 

---

# 7. Open the Published Report in Power BI Service

After clicking the provided link:

1. The browser opens.
2. Power BI Service loads.
3. Sign in if required.
4. Provide the Power BI account password.
5. The published report becomes available.

The lecture demonstrates that the report appears in Power BI Service essentially as it was created in Power BI Desktop. 

---

# 8. Verify That Report Interactivity Works

An important point demonstrated in the lecture is that the published report remains **interactive**.

For example, the report contains slicers.

### Selecting a slicer value

If you select a value from a slicer:

* The report gets filtered.
* The other visuals respond to the selection.
* The filtering behavior works similarly to Power BI Desktop.

### Selecting multiple slicer values

To select multiple values:

1. Hold the **Ctrl** key.
2. Select additional values.

This allows multiple slicer selections.

The instructor demonstrates that the entire report responds to these selections. 

---

# 9. Example: Customer Gender Filter

The lecture provides an example involving customer gender.

Suppose there are **10,000 total customers**.

The instructor demonstrates approximately:

* **5,000 Female**
* **5,000 Male**

When a gender is selected from the slicer, the entire report gets filtered accordingly.

This confirms that the interactive filtering behavior from Power BI Desktop has been retained after publishing to Power BI Service. 

---

# 10. Filtering Through Other Visuals

Filtering isn't restricted to slicers.

The instructor also demonstrates selecting a category from a **ribbon chart**.

When a category is selected:

> The entire report gets filtered accordingly.

Therefore, the published report continues to support interactive filtering between visuals.

This means the report behaves similarly in Power BI Service to how it behaved in Power BI Desktop. 

---

# 11. Sharing a Report

After publishing a report to Power BI Service, you may want to share it with:

* Colleagues
* Other people
* People within your organization

The lecture explains that the report should first be **published to Power BI Service**, after which it can be shared with other users. 

---

# 12. How to Share the Report

In Power BI Service, the report provides a **Share** option.

### Steps

1. Open the report.
2. Click **Share**.
3. Enter the **email address** or other identifying information of the person/colleague.
4. Configure what the recipient is allowed to do.
5. Click **Send**.

The recipient receives a link through email and can access the report according to the permissions you've provided. 

---

# 13. Configure Sharing Permissions

Power BI allows you to control what recipients can do with the report.

The instructor gives an example of selecting an option similar to:

### "People in your organization with the link"

and allowing them to:

* **View**
* **Share**

Therefore, sharing is not simply about giving someone access; you can also configure their permissions. 

---

# 14. Creating a New Workspace

The first report was published to **My Workspace**.

The instructor now demonstrates how to create a separate/custom workspace.

### Steps

1. Go to the **Home** tab in Power BI Service.
2. Click **Workspaces**.
3. Click **New Workspace**.
4. Enter a workspace name.

The demonstration uses a name similar to:

### **Test Power BI Project Two**

5. Click **Apply**.
6. Wait while Power BI creates the workspace.



---

# 15. Workspace Customization

When creating a workspace, Power BI provides additional configuration options.

The lecture mentions that you can:

### Add a workspace image

You can upload an image for the workspace.

### Add a description

You can also provide a description explaining what the workspace is used for.

These are optional workspace customization/configuration elements mentioned in the demonstration. 

---

# 16. Verify the New Workspace

After creating the workspace:

1. Go back to the **Home** tab.
2. Click **Workspaces**.
3. You should now see:

   * **My Workspace**
   * The newly created custom workspace.

In the demonstration, the newly created workspace is the test/project workspace. 

---

# 17. Publish the Report to the New Workspace

Now the instructor returns to **Power BI Desktop**.

The objective is to publish the same report to the newly created workspace instead of My Workspace.

### Steps

1. Open the Power BI file in **Power BI Desktop**.
2. Click **Publish**.
3. If prompted, save changes.
4. Power BI now displays the available workspaces.
5. Select the newly created workspace.
6. Click **Select**.
7. Wait while Power BI publishes the report. 

---

# 18. Open the Report From the New Workspace

After publishing:

1. Power BI provides the report link.
2. Click the link.
3. Wait for the report to load.
4. The report now exists inside the **newly created workspace**.

So instead of:

**My Workspace → Report**

the structure is now:

**Test Project Workspace → Report**



---

# 19. Sharing Reports From the New Workspace

Reports published to the custom workspace can also be shared.

The process remains similar:

1. Open the report.
2. Click **Share**.
3. Enter the person's email address/name.
4. Configure permissions.
5. Send the invitation/link.

However, there is an important consideration:

> The person with whom you are sharing the report should have the appropriate rights to access the workspace.

Therefore, **workspace access/permissions matter when sharing content**. 

---

# 20. Different Levels of Permissions

The lecture emphasizes that the recipient's capabilities depend on the permissions you give them.

Depending on the permissions, users may be able to:

* View the report
* Share the report
* Build content using the associated data
* Potentially edit content when appropriate permissions are provided

Therefore:

> **The permissions you assign determine what the recipient can do with the report.**



---

# 21. Allow Recipients to Share the Report

The sharing settings contain an option similar to:

### "Allow recipients to share the report"

If this is enabled:

* The recipient can view the report.
* The recipient can also share the report with others, subject to the applicable permissions.

---

# 22. Allow Recipients to Build Content With the Data

Another important sharing option demonstrated is:

### "Allow recipients to build content with the data associated with the report"

If this option is enabled:

1. The recipient can access the report.
2. They can use the associated data.
3. They can build **new content** based on that data.

The instructor demonstrates checking this option and then clicking **Apply**. 

### Key distinction

**View/Share permission**

→ User can view and potentially share the report.

**Build permission**

→ User can also create new content based on the associated data.

This is an important concept when managing Power BI content access.

---

# 23. Complete Publishing Workflow

The complete process demonstrated can be remembered as:

### Step 1 — Create Report

Build the report in:

**Power BI Desktop**

↓

### Step 2 — Sign In

Sign in using your Power BI organizational/work/school account.

↓

### Step 3 — Publish

Click:

**Publish**

↓

### Step 4 — Select Workspace

Choose:

**My Workspace**

or a custom workspace.

↓

### Step 5 — Publish

Click:

**Select**

and wait for the report to publish.

↓

### Step 6 — Open in Power BI Service

Click the generated:

**Open report in Power BI**

link.

↓

### Step 7 — Verify

Check that:

* Visuals load.
* Slicers work.
* Cross-filtering works.
* Report interactions work.

↓

### Step 8 — Share

Click:

**Share**

↓

### Step 9 — Add Recipients

Enter their email/name.

↓

### Step 10 — Configure Permissions

Choose whether recipients can:

* View
* Share
* Build content using the data

↓

### Step 11 — Send

Click:

**Send**

---

# 24. My Workspace vs. Custom Workspace

A key distinction from this lecture:

| My Workspace                                       | Custom Workspace                                |
| -------------------------------------------------- | ----------------------------------------------- |
| Available by default                               | Created by the user                             |
| Personal/default destination in this demonstration | Can be specifically created for a project       |
| Used for the initial publishing demonstration      | Used to organize the project report             |
| No custom workspace creation required              | Requires creating and configuring the workspace |

The instructor initially publishes to **My Workspace**, then creates a separate project workspace and republishes the report there. 

---

# 25. Important Concepts

### Power BI Service

The cloud/service component where Power BI reports can be published, accessed, and shared.

### Workspace

A container for Power BI content such as:

* Reports
* Dashboards
* Datasets

### Publish

Moves the report developed in **Power BI Desktop** into a selected **Power BI Service workspace**.

### Share

Allows other users to access the published report according to the permissions assigned.

### Permissions

Determine what recipients can do with the shared content.

### Build Permission

Allows recipients to build new content using the data associated with the report.

---

# 26. Why Do We Need Scheduled Refresh?

The lecture ends by introducing the next topic: **Scheduled Refresh**.

The reason scheduled refresh is required is that the underlying dataset may change over time.

For example:

**Data source**

→ New data arrives

→ Existing data is modified

→ Power BI dataset needs to receive those changes

→ Report/dashboard should reflect the updated information

Therefore, we need a mechanism to periodically refresh the dataset so that the report reflects changes in the underlying data source.

The next lecture will discuss **scheduling refresh**. 

---

# Quick Revision

### Publishing

**Power BI Desktop → Publish → Select Workspace → Publish → Open in Power BI Service**

### Initial workspace

**My Workspace**

### Custom workspace

**Home → Workspaces → New Workspace → Name → Apply**

### Publish to custom workspace

**Power BI Desktop → Publish → Select custom workspace → Select**

### Sharing

**Open Report → Share → Enter recipient → Configure permissions → Send**

### Important permissions

* **View** → Can view the report.
* **Share** → Can share the report.
* **Build content** → Can create new content using the associated data.

### Main concept

> **Power BI Desktop is where the report is developed; Power BI Service is where the published report can be hosted, accessed, and shared.**

### Next topic

**Scheduled Refresh** — keeping the Power BI dataset/report synchronized with changes in the underlying data source.
