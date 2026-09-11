# Power BI — Publishing the Report to Power BI Service

## 1. Objective of the Session

The objective of this session is to learn **how to publish a completed Power BI report from Power BI Desktop to Power BI Service**.

The overall flow is:

**Power BI Desktop → Save the report → Publish → Select Workspace → Sign in to Power BI Service → Complete authentication → View the published report**

> **Prerequisite:** You need a **Power BI account** before publishing the report. The instructor recommends referring to the earlier lecture that explains how to create a free Power BI account.

---

# 2. Prerequisite — Power BI Account

Before starting this session, make sure you have created a **free Power BI account**.

The instructor mentions that a previous lecture in the Power BI section explains:

* How to create a free Power BI account
* How to set up the account required for Power BI Service

This account will be used to sign in to **Power BI Service** and access the published report.

---

# 3. Publishing the Power BI Report

Once the report has been completely created in **Power BI Desktop**, it can be published to Power BI Service.

### Step 1 — Click Publish

In Power BI Desktop:

1. Open the completed Power BI report.
2. Go to the **Publish** option.
3. Click **Publish**.

Power BI will begin the process of publishing the report.

---

# 4. Save the Power BI Report

Before publishing, Power BI may ask you to save the report.

### Step 2 — Save the Report

When the save dialog appears:

1. Give the report a name.
2. In the lecture, the instructor names the report:

**`Power BI one`**

3. Click **Save**.

The report may take some time to save.

### Important

The `.pbix` file is the Power BI Desktop version of the report.

Publishing it makes the report available in **Power BI Service**, where it can be accessed through a web browser.

---

# 5. Select the Workspace

After saving, Power BI asks where the report should be published.

A Power BI report can be published to an appropriate **workspace**.

In this lecture, the instructor chooses:

### **My Workspace**

### Step 3 — Select My Workspace

1. The workspace selection window appears.
2. Locate **My Workspace**.
3. Double-click **My Workspace**.

Power BI then begins publishing the report.

> **Note:** Publishing may take some time depending on the report and connection.

---

# 6. Wait for the Publishing Process

After selecting the workspace:

* Power BI uploads the report.
* The report is published to Power BI Service.
* This process may take some time.

Once publishing is completed, Power BI provides a **link** that can be used to open the report in Power BI Service.

---

# 7. Open the Published Report

### Step 4 — Click the Link

After the report has been published:

1. Click the link provided by Power BI.
2. The browser will open Power BI Service.
3. You may need to sign in.

---

# 8. Sign in to Power BI Service

The instructor enters the organizational Microsoft account used for Power BI.

The account shown in the lecture is an organizational Microsoft account.

### Step 5 — Enter Your Account

Enter your Power BI/Microsoft account email address.

Then:

1. Click **Next**.
2. Enter your password.
3. Click **Sign in**.

---

# 9. Multi-Factor Authentication / Authenticator App

The instructor has **Microsoft Authenticator** activated on the account.

Therefore, after entering the password, an additional authentication step appears.

Power BI/Microsoft displays a **verification code/number**.

### Step 6 — Verify Using Authenticator

The instructor:

1. Checks the Microsoft Authenticator app on the mobile phone.
2. Enters/confirms the displayed code.
3. Completes the authentication process.

### If Authenticator Is Not Activated

The instructor specifically mentions that this is **not a problem**.

If you have not activated the Authenticator app, you may have a different authentication flow depending on your account/security settings.

The important point is that you must successfully complete Microsoft's sign-in verification.

---

# 10. Stay Signed In

After authentication, Microsoft displays a prompt asking whether you want to stay signed in.

The instructor chooses:

**Yes**

There is also an option:

**Don't show this message again**

The instructor selects that option and then clicks **Yes**.

### Step 7 — Stay Signed In

You can therefore:

1. Select **Don't show this message again** if desired.
2. Click **Yes**.

Power BI Service will then open.

---

# 11. View the Published Report in Power BI Service

After successful authentication, the published report becomes available in **Power BI Service**.

The instructor waits for the report to load.

The report that was created in Power BI Desktop can now be viewed online.

---

# 12. Verify the First Report Page

The instructor clicks on the **first page** of the report.

The first page contains all the visuals that were created earlier in the project.

This confirms that the report has been successfully published.

---

# 13. Verify the Second Report Page

The instructor then clicks on the **second page**.

The second page is also displayed correctly.

Therefore, both report pages that were created in Power BI Desktop are available in Power BI Service.

### Important Concept

Publishing the report transfers the Power BI report from:

**Power BI Desktop**

to

**Power BI Service**

while preserving the report pages and visuals.

---

# 14. Complete Publishing Workflow

The complete process demonstrated in the lecture is:

```text
Create Power BI Report
        ↓
Complete all report pages and visuals
        ↓
Click Publish
        ↓
Save the report
        ↓
Give the report a name
        ↓
Select Workspace
        ↓
Choose My Workspace
        ↓
Wait for publishing
        ↓
Click the generated link
        ↓
Power BI Service opens
        ↓
Enter Microsoft/Power BI account
        ↓
Click Next
        ↓
Enter Password
        ↓
Click Sign in
        ↓
Complete Authenticator/MFA verification
        ↓
Click Yes to stay signed in
        ↓
Power BI Service opens
        ↓
Verify Page 1
        ↓
Verify Page 2
```

---

# 15. Power BI Desktop vs Power BI Service

This session demonstrates an important distinction.

| Power BI Desktop       | Power BI Service                        |
| ---------------------- | --------------------------------------- |
| Used to create reports | Used to access published reports        |
| Desktop application    | Web/cloud-based service                 |
| Create visuals         | View/share/access reports               |
| Create DAX measures    | Consume published report                |
| Transform/model data   | Access reports online                   |
| Build report pages     | View report pages online                |
| Save `.pbix` file      | Published report available in workspace |

### Simple Understanding

Think of it as:

**Power BI Desktop = Build the report**

**Power BI Service = Publish, access and work with the report online**

---

# 16. What Is a Workspace?

A **workspace** is a location in Power BI Service where Power BI content can be stored and managed.

In this lecture, the instructor uses:

### **My Workspace**

This is the personal workspace associated with the user's Power BI account.

The publishing process therefore becomes:

**Power BI Desktop → My Workspace → Power BI Service**

---

# 17. Authentication Flow

The lecture also demonstrates that publishing/accessing Power BI Service may involve multiple authentication steps.

The flow shown is:

1. Enter Microsoft account email.
2. Click **Next**.
3. Enter password.
4. Click **Sign in**.
5. Complete Microsoft Authenticator verification.
6. Choose whether to stay signed in.
7. Power BI Service opens.

### Important

The exact authentication screen can differ depending on the organization's Microsoft account and security settings.

---

# 18. Important Concepts Learned

### 1. Publishing

**Publishing** means taking a report created in Power BI Desktop and making it available in Power BI Service.

---

### 2. Workspace

A **workspace** is the destination where the report is published.

In this lecture:

**My Workspace**

was selected.

---

### 3. Power BI Service

Power BI Service is the online/cloud environment where published Power BI reports can be accessed.

---

### 4. Microsoft Account

A valid Power BI/Microsoft account is required to access Power BI Service.

---

### 5. Multi-Factor Authentication

If MFA/Authenticator is enabled, an additional verification step is required during sign-in.

---

### 6. Report Pages Are Published Together

The report created in Power BI Desktop contained multiple pages.

After publishing, the instructor verifies:

* **Page 1**
* **Page 2**

Both are available in Power BI Service.

---

# 19. Quick Revision

### How to Publish a Power BI Report

1. Open the completed report in **Power BI Desktop**.
2. Click **Publish**.
3. Save the report.
4. Give the report a name.
5. Select the destination workspace.
6. Choose **My Workspace**.
7. Wait for the publishing process to complete.
8. Click the generated link.
9. Sign in to your Microsoft/Power BI account.
10. Enter your password.
11. Complete MFA/Authenticator verification if enabled.
12. Choose **Yes** on the stay-signed-in prompt.
13. Power BI Service opens.
14. Verify that all report pages are available.

---

# 20. Key Takeaway

> **Power BI Desktop is where we build the report, while Power BI Service is where we publish and access that report online.**

For this project, the final workflow was:

**Build report in Power BI Desktop → Publish → My Workspace → Sign in → Open Power BI Service → Verify report pages**

---

## 21. Transition to the Next Project

The instructor concludes this project and introduces the **second Power BI project**.

The next project will:

* Use a **different dataset**
* Again make use of **Perplexity**
* Follow a similar AI-assisted approach to developing the Power BI project
* Introduce **new Power BI concepts/features**
* Build on what was learned in the current project

So this lecture effectively marks the completion of the **first Power BI project**, including its publication to Power BI Service.
