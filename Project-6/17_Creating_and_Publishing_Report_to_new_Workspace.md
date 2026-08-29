# Power BI – Creating a New Workspace and Publishing a Report to It

## 1. Objective of the Session

In the previous session, the report was published to **My Workspace**.

This session explains how to:

1. Create a **new workspace** in Power BI Service.
2. Handle the requirement for **free trial/capacity activation** if applicable.
3. Publish a Power BI Desktop report to the newly created workspace.
4. Open and verify the published report.
5. Understand the difference between **My Workspace** and another workspace.
6. Understand that a workspace can contain both a **Report** and its associated **Semantic Model**.

---

# 2. Why Create Another Workspace?

Previously, the report was published to:

> **My Workspace**

However, in real-world projects, you may want to organize reports into different workspaces.

For example:

```text
My Workspace
    ↓
Personal reports/projects

Housing Project Workspace
    ↓
Housing-related reports
```

Power BI allows you to create additional workspaces and publish reports to them, provided you have the required permissions/capabilities.

---

# 3. Requirement – Ability to Create a Workspace

Before creating a new workspace, you need to have the necessary workspace-creation capability available in your Power BI environment/account.

The instructor points out that if you have **recently created your Power BI account**, you might not immediately see all the required options.

For example, the instructor mentions **Admin Monitoring** and possible **free trial activation**.

### Important point

If Power BI asks you to **activate a free trial**, you should activate it as instructed in the course.

After activation, you may need to **wait for some time** before the required workspace functionality becomes available.

So the general sequence is:

```text
Create/Activate Account
        ↓
Activate Free Trial if required
        ↓
Wait for activation
        ↓
Workspace creation becomes available
```

---

# 4. Open the Workspaces Section

Once the required functionality is available:

### Steps

1. Go to **Power BI Service**.
2. Click **Workspaces**.
3. Look for the option:

**Create a workspace / New Workspace**

The instructor selects the option to create a new workspace.

---

# 5. Create a New Workspace

### Steps

1. Click **New Workspace**.
2. Power BI opens the workspace creation interface.
3. Enter a name for the workspace.

The instructor names the workspace:

> **Housing Project**

Other details are optional in this demonstration, so they are left unchanged.

4. Click **Apply**.

Power BI then creates the new workspace.

---

# 6. Verify the New Workspace

After creating the workspace, the instructor returns to the Home section.

### Steps

1. Click the **Home** tab.
2. Click **Workspaces**.
3. Locate the newly created workspace.

You should now see:

> **Housing Project**

This confirms that the workspace was successfully created.

---

# 7. Open the Power BI Desktop Report

Next, the instructor wants to publish the previously created Housing report.

### Steps

1. Open the **Power BI report** that was created in Power BI Desktop.
2. Make sure you are already **signed in** to your Power BI account.
3. Go to the **Home** tab.
4. Click **Publish**.

---

# 8. Select the Workspace for Publishing

Unlike the previous session, where the report was directly published to **My Workspace**, Power BI now displays multiple workspace options.

The publish window contains the workspaces to which you have access.

The instructor wants to publish the report to:

> **Housing Project**

### Steps

1. Find **Housing Project** in the list.
2. Double-click/select it.

Power BI will now publish the report to the **Housing Project workspace** instead of My Workspace.

---

# 9. Publishing the Report

The report is then uploaded to the selected workspace.

The report being published is referred to as:

> **Housing Copy.pbix**

Power BI may take some time to complete the publishing operation.

Once publishing finishes, the report becomes available in the **Housing Project** workspace.

---

# 10. Open the Published Report

After publishing, Power BI provides an option to open the report.

The lecture refers to the option:

> **Open Housing Copy.pbix**

### Steps

1. Click **Open Housing Copy.pbix**.
2. Wait for Power BI Service to load the report.
3. The report opens in the browser.

The instructor verifies that the report is displayed correctly.

---

# 11. Verify the Report Pages

The Housing report currently contains **two pages**.

Therefore, after opening the report in Power BI Service, both report pages should be available.

Conceptually:

```text
Housing Copy Report
│
├── Page 1
└── Page 2
```

---

# 12. Verify the Housing Project Workspace

The instructor then goes back to the workspace list.

### Steps

1. Click **Workspaces**.
2. Select **Housing Project**.

Inside the workspace, you can see the published content.

The Housing report is now available inside this workspace.

---

# 13. Report and Semantic Model

An important concept demonstrated in this session is that when you publish a Power BI report, you generally see two related items in the workspace:

1. **Report**
2. **Semantic Model**

The instructor points out that the workspace contains both the report and its associated semantic model.

Conceptually:

```text
Housing Project Workspace
│
├── Housing Copy
│   └── Report
│
└── Housing Copy
    └── Semantic Model
```

The semantic model contains the underlying data/model that the report uses.

---

# 14. Compare Housing Project with My Workspace

The instructor then compares the newly created **Housing Project** workspace with **My Workspace**.

### My Workspace

When opening:

**Workspaces → My Workspace**

you can see all the reports/projects that were previously published there.

The instructor had previously published several projects to My Workspace, so it contains multiple reports and their associated semantic models.

Conceptually:

```text
My Workspace
│
├── Project 1
│   ├── Report
│   └── Semantic Model
│
├── Project 2
│   ├── Report
│   └── Semantic Model
│
└── Project 3
    ├── Report
    └── Semantic Model
```

---

## Housing Project Workspace

The newly created **Housing Project** workspace contains only the Housing report that was just published.

Therefore:

```text
Housing Project
│
└── Housing Report
    ├── Report
    └── Semantic Model
```

The difference is simply that **My Workspace contains the previously published projects**, whereas **Housing Project currently contains the newly published Housing report**.

---

# 15. My Workspace vs Other Workspaces

A key concept from the session is understanding the difference between publishing to **My Workspace** and publishing to another workspace.

| My Workspace                            | Other Workspace                                             |
| --------------------------------------- | ----------------------------------------------------------- |
| Personal workspace                      | Separate workspace                                          |
| Reports can be published here           | Reports can be published here                               |
| Used for your own content               | Useful for organizing project/team content                  |
| Previously created reports appear here  | Only content published/added to that workspace appears here |
| Can contain reports and semantic models | Can contain reports and semantic models                     |

---

# 16. Complete Process

The entire process demonstrated in this session is:

```text
Power BI Service
       ↓
Workspaces
       ↓
New Workspace
       ↓
Name = Housing Project
       ↓
Apply
       ↓
Workspace Created
       ↓
Open Power BI Desktop Report
       ↓
Home → Publish
       ↓
Select Housing Project
       ↓
Publish
       ↓
Report Successfully Published
       ↓
Open Housing Copy.pbix
       ↓
Verify 2 Report Pages
       ↓
Workspaces → Housing Project
       ↓
Verify Report + Semantic Model
```

---

# 17. Important Notes About Free Trial/Activation

The lecture emphasizes this because newly created Power BI accounts may not immediately have all the capabilities demonstrated.

If the workspace creation option or required functionality is not available:

1. Check whether Power BI asks you to **activate a free trial**.
2. Activate the trial if required.
3. Wait for the activation to complete.
4. Return to the Workspaces section.
5. Try creating the workspace again.

The instructor specifically notes that **activation may take some time**, so don't assume the feature is unavailable simply because it doesn't appear immediately after account creation.

---

# 18. Key Takeaways

### 1. You don't have to publish everything to My Workspace

You can publish reports to other workspaces that you have access to.

### 2. Create a workspace first

The basic process is:

**Workspaces → New Workspace → Name → Apply**

### 3. Workspace names can be project-specific

In this example:

**Housing Project**

was created specifically for the Housing report.

### 4. Select the destination while publishing

When publishing from Power BI Desktop:

**Home → Publish → Select Workspace**

Choose the desired workspace instead of automatically selecting My Workspace.

### 5. Reports and semantic models are both visible

Publishing a report results in the workspace containing the **report** along with its associated **semantic model**.

### 6. Workspaces help organize projects

Instead of keeping every report in My Workspace, separate workspaces can be created for different projects or teams.

---

# 19. Final Concept

The main difference between the previous and current sessions is the **publishing destination**.

### Previous session

```text
Power BI Desktop
       ↓
Publish
       ↓
My Workspace
```

### Current session

```text
Power BI Desktop
       ↓
Publish
       ↓
Housing Project Workspace
```

So the key lesson is:

> **Power BI reports can be published not only to My Workspace but also to other workspaces that you create or have access to.**

This provides a better way to organize Power BI content by **project, team, department, or business purpose**.
