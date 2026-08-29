# Power BI — Sharing Reports Through Apps

This session explains how to **create and share a Power BI App** so that other colleagues/users can access a published Power BI report.

It also demonstrates:

* Editing a report directly in **Power BI Service**
* Saving changes made in Power BI Service
* Creating a **new workspace**
* Publishing a Power BI Desktop report to that workspace
* Understanding why the **Create app** option is available in one workspace but not another
* Creating a Power BI App
* Adding a report to the app
* Configuring an audience
* Publishing the app
* Sharing the generated app link
* Opening and viewing the published app
* Configuring app branding such as colors and logo

---

# 1. Objective of the Session

The main objective is to understand:

> **How to share Power BI reports through Apps.**

The overall concept is:

**Power BI Desktop report**

→ **Publish to Power BI Service**

→ **Workspace**

→ **Create App**

→ **Add report/content**

→ **Configure audience**

→ **Publish App**

→ **Share App link**

This provides a convenient way to distribute reports to other users.

---

# 2. Initial Issue — Ribbon Color Has Changed

At the beginning of the session, the instructor notices an issue with an existing visual.

The chart is:

> **Top Five Brands by Highest Average Sales Price**

The instructor observes that the **ribbon color has changed** for some reason.

The objective is to correct this formatting directly in **Power BI Service**.

---

# 3. Edit the Report in Power BI Service

The instructor wants to demonstrate that reports can be edited directly in Power BI Service.

### Steps

1. Click:

   **Edit**

2. Select the particular visual whose ribbon color needs to be corrected.

3. Open:

   **Format a visual**

This is similar to formatting a visual in Power BI Desktop.

---

# 4. Change the Ribbon Color

The instructor navigates to the ribbon formatting settings.

### Steps

1. Expand:

   **Ribbons**

2. Scroll down.

3. Click:

   **Colors**

4. Click:

   **More colors**

The instructor wants to use the same color that was used elsewhere in the report.

---

# 5. Copy the Color from Excel

The report's color reference is maintained in an Excel sheet.

### Steps

1. Open the Excel sheet.

2. Locate the previously used visual color.

3. The color is referred to as:

   **Visual Light**

4. Copy the color.

5. Return to **Power BI Service**.

6. Paste/select the copied color in the color picker.

The ribbon color is now corrected.

---

# 6. Important — Save Changes in Power BI Service

The instructor emphasizes an important point:

> **Always save changes made in Power BI Service.**

If you make formatting or report changes in Power BI Service and do not save them, those changes may not be retained.

### Steps

1. Click:

   **File**

2. Select:

   **Save**

Power BI confirms that the report has been saved.

A notification appears confirming the save operation.

The instructor then clears the notification.

---

# 7. Why Create a New Workspace?

The instructor then navigates to:

> **Workspaces**

The original report had been published to:

> **My workspace**

However, the instructor observes that there is **no option at the top to create an App** from this workspace.

This leads to an important demonstration:

> What happens if we create a new workspace and publish the same report to that workspace?

The instructor wants to show that the new workspace provides the option to create a Power BI App.

---

# 8. Create a New Workspace

### Steps

1. Click:

   **Workspaces**

2. Click:

   **New Workspace**

3. Enter the workspace name:

   **Azure Power BI project**

### Description

The instructor does **not** enter a description.

The description is optional.

### Image

The instructor also does **not** upload an image for the workspace.

4. Click:

   **Apply**

A new workspace is created.

---

# 9. Verify the New Workspace

After creating the workspace, the instructor opens:

> **Azure Power BI project**

The important observation is that this workspace now provides an option to:

> **Create app**

This is the workspace that will be used for the remainder of the demonstration.

---

# 10. Publish the Report Again from Power BI Desktop

The instructor now returns to the Power BI Desktop report.

The same report created during the earlier sessions is open in Power BI Desktop.

The goal is to publish this report to the newly created workspace:

> **Azure Power BI project**

### Steps

1. Open the report in **Power BI Desktop**.

2. Click:

   **Publish**

3. Power BI may ask whether you want to save changes.

4. Select:

   **Yes / Save changes**

5. Power BI displays the available workspaces.

6. Select:

   **Azure Power BI project**

7. Double-click/select the workspace.

8. Confirm the selection.

The report is now published to the new workspace.

---

# 11. Open the Published Report in Power BI Service

After publishing, Power BI provides an option/link to open the published report.

### Steps

1. Click:

   **Open Azure Power BI report .pbix in Power BI**

2. Click the provided link.

Power BI Service opens.

The instructor waits for the report to load.

---

# 12. Verify the Report Pages

Once the report loads, the instructor verifies that the report contains the two pages created earlier.

### Page 1

> **Brands**

### Page 2

> **Details**

The instructor clicks between:

**Brands → Details → Brands**

to confirm that both pages are available.

---

# 13. Verify the Workspace Contents

The instructor then returns to the workspace.

### Steps

1. Click:

   **Workspaces**

2. Select:

   **Azure Power BI project**

Inside the workspace, the instructor observes both:

* The **Report**
* The **Semantic model**

The workspace therefore contains the report and its associated semantic model.

---

# 14. Create the Power BI App

Now that the report has been published to the appropriate workspace, the instructor creates an App.

### Steps

1. In the **Azure Power BI project** workspace, click:

   **Create app**

This starts the Power BI App creation process.

---

# 15. Configure the App Name

The first configuration is the App name.

The instructor enters:

> **Azure PBI app**

So the application will be named:

**Azure PBI app**

---

# 16. Add an App Description

A description can also be added to explain the purpose of the application.

The instructor enters a description similar to:

> **This report helps to analyze men's wear data.**

The description provides users with context about what the app/report is designed to analyze.

---

# 17. Upload an App Image

The instructor then demonstrates that an image can be associated with the app.

### Steps

1. Click:

   **Upload**

2. Choose an image from:

   **Downloads**

3. Select the required image.

The image can be used for app branding.

---

# 18. Add Content to the App

The next step is to specify what content should be included in the app.

### Steps

1. On the right-hand side, click:

   **Add Content**

2. Click **Add Content** again if required to open the content-selection interface.

The instructor sees the report that was previously published to the workspace.

3. Select/check the checkbox for the report.
4. Click:

   **Add**

The report is now included as content in the Power BI App.

---

# 19. Configure the App Audience

After adding the report, the instructor proceeds to the audience configuration.

### Steps

1. Click:

   **Next**

2. Go to:

   **Add Audience**

The audience determines who will be able to access the app.

For this demonstration, the instructor selects:

> **Entire organization**

This means the app is configured to be accessible to the organization as a whole, subject to the organization's Power BI permissions/licensing and access configuration.

3. Click:

   **Publish App**

---

# 20. Publish the Power BI App

Power BI may take some time to publish the app.

### Steps

1. Click:

   **Publish**

2. Wait for the publishing process to complete.

Once publishing is complete, Power BI provides a **link** to the app.

---

# 21. Share the App Link

The instructor explains that the generated link can be shared with the concerned users.

The workflow is:

**Create App**

→ **Publish App**

→ **Get App Link**

→ **Share Link**

Users who have the necessary access can use the link to open the app and access the report.

The instructor specifically notes that the link can be copied and shared with others.

---

# 22. Open the App

To demonstrate how the final application looks, the instructor uses:

> **Go to app**

### Steps

1. Click:

   **Go to app**

2. Wait for the app to load.

The published application opens.

---

# 23. Viewing the App

The instructor demonstrates the app's final appearance.

The app contains the report pages.

### Brands Page

The user can view:

> **Brands**

### Details Page

The user can also view:

> **Details**

Therefore, the app provides access to the report content that was added during the app configuration.

---

# 24. App Branding — Color

The instructor explains that the color displayed on the left-hand side/top area of the app can be changed.

This color can be configured while creating the app.

In this demonstration:

> The default color is retained.

However, organizations can customize the app's appearance according to their branding requirements.

---

# 25. App Logo

The instructor also explains that an organization can provide a logo for the app.

This is useful in professional/enterprise environments because managers or organizations may expect reports and apps to follow company branding.

For example, an organization could configure:

* Company logo
* Company colors
* Appropriate app name
* Description

This gives the Power BI App a more professional appearance.

---

# 26. Overall Power BI App Architecture

The complete process demonstrated can be visualized as:

```text
Power BI Desktop
       │
       │ Publish
       ▼
Power BI Service Workspace
       │
       ├── Report
       │
       └── Semantic Model
       │
       │ Create App
       ▼
Power BI App
       │
       ├── App Name
       ├── Description
       ├── Logo/Image
       ├── Report Content
       └── Audience
       │
       │ Publish
       ▼
      App Link
       │
       ▼
   End Users
```

---

# 27. Why Use a Power BI App?

A Power BI App provides a structured way to distribute report content to users.

Instead of giving users access to the underlying workspace and asking them to navigate through individual reports, an organization can package selected content into an app.

The general idea is:

> **Workspace = Development/content management area**

> **App = Consumer-facing distribution mechanism**

This provides a cleaner experience for report consumers.

---

# 28. Important Difference — Workspace vs App

### Workspace

The workspace is where the report and semantic model are managed.

In this example:

> **Azure Power BI project**

contains:

* Report
* Semantic model

The workspace is also where the instructor gets the option:

> **Create app**

---

### App

The app is the packaged experience that is distributed to users.

In this example:

> **Azure PBI app**

The app contains the selected report content and is configured for an audience.

---

# 29. Why the Workspace Matters

One of the key demonstrations in this session is the difference between the original workspace and the newly created workspace.

Initially:

> **My workspace**

was used to publish the report.

The instructor did not see the expected option for creating the app there.

Then a new workspace was created:

> **Azure Power BI project**

The same report was published to that workspace.

The instructor could then see:

> **Create app**

This demonstrates the importance of using an appropriate workspace when building a report distribution workflow.

---

# 30. Complete Step-by-Step Workflow

## Part A — Correct Existing Visual

1. Open report in Power BI Service.
2. Click **Edit**.
3. Select the visual.
4. Click **Format a visual**.
5. Expand **Ribbons**.
6. Scroll down.
7. Click **Colors**.
8. Click **More colors**.
9. Open Excel.
10. Locate the **Visual Light** color.
11. Copy the color.
12. Return to Power BI Service.
13. Paste/select the color.
14. Verify the ribbon color.
15. Click **File → Save**.
16. Clear the save notification.

---

# 31. Part B — Create Workspace

1. Click **Workspaces**.

2. Click **New Workspace**.

3. Enter:

   **Azure Power BI project**

4. Leave the description blank.

5. Don't upload a workspace image.

6. Click **Apply**.

7. Verify that the workspace has been created.

8. Confirm that **Create app** is available.

---

# 32. Part C — Publish Report to New Workspace

1. Open Power BI Desktop.

2. Open the existing report.

3. Click **Publish**.

4. Save changes if prompted.

5. Select:

   **Azure Power BI project**

6. Select the workspace.

7. Wait for publishing to complete.

8. Click the option/link to open the report in Power BI Service.

9. Wait for the report to load.

10. Verify:

    * Brands page
    * Details page

---

# 33. Part D — Verify Workspace

1. Click **Workspaces**.
2. Select **Azure Power BI project**.
3. Verify that the workspace contains:

   * Report
   * Semantic model
4. Click **Create app**.

---

# 34. Part E — Configure the App

### App name

Enter:

> **Azure PBI app**

### Description

Enter a description explaining that:

> The report helps analyze men's wear data.

### Image

1. Click **Upload**.
2. Select an image from **Downloads**.

### Content

1. Click **Add Content**.
2. Select the report.
3. Check the report.
4. Click **Add**.

### Audience

1. Click **Next**.

2. Select **Add Audience**.

3. Select:

   **Entire organization**

4. Click **Publish App**.

---

# 35. Part F — Publish and Share

1. Click **Publish**.
2. Wait for the app to be published.
3. Power BI generates an app link.
4. Copy the link.
5. Share the link with the intended users.

Users with the required access can use the link to open the app.

---

# 36. Part G — View the Published App

1. Click:

   **Go to app**

2. Wait for the app to load.

3. Verify the **Brands** page.

4. Verify the **Details** page.

5. Review the app's overall appearance.

---

# 37. Important Settings/Options Mentioned

| Feature              | Purpose                               |
| -------------------- | ------------------------------------- |
| **Edit**             | Modify the report in Power BI Service |
| **Format a visual**  | Change visual formatting              |
| **Ribbons → Colors** | Change ribbon colors                  |
| **More colors**      | Select a custom color                 |
| **File → Save**      | Save changes made in Power BI Service |
| **Workspaces**       | Manage Power BI content               |
| **New Workspace**    | Create a workspace                    |
| **Create app**       | Start creating a Power BI App         |
| **Add Content**      | Select reports/content for the app    |
| **Add Audience**     | Define who can access the app         |
| **Publish App**      | Publish the configured app            |
| **Go to app**        | Open/view the published app           |
| **Upload**           | Add an image/logo for branding        |

---

# 38. Key Concepts to Remember

### 1. Report vs App

A **report** is the analytical content created in Power BI Desktop and published to Power BI Service.

An **app** packages selected content from a workspace for distribution to users.

---

### 2. Workspace Is the Source of App Content

The report is first published to a workspace.

Then the app is created from that workspace.

So:

> **Report → Workspace → App → Users**

---

### 3. Save Service Changes

If you edit a report directly in Power BI Service, remember to:

> **File → Save**

The instructor specifically emphasizes this.

---

### 4. App Audience

During app creation, you need to specify who can access the app.

In the demonstration:

> **Entire organization**

was selected.

In a real project, the audience/access configuration should be aligned with the organization's security and distribution requirements.

---

### 5. App Branding

Power BI Apps can be customized with branding elements such as:

* App name
* Description
* Image/logo
* App color

This can be particularly useful when delivering reports to managers, clients, or organizational users.

---

# 39. Interview Perspective

This session introduces a useful Power BI interview concept:

### Question: How do you share a Power BI report with business users?

A good high-level answer is:

> "I would publish the Power BI report from Power BI Desktop to an appropriate workspace in Power BI Service. From that workspace, I can create a Power BI App, add the required reports/content, configure the intended audience, publish the app, and share the generated app link with authorized users."

### Another common question:

**What is the difference between a workspace and an app?**

Answer:

> A workspace is primarily used to manage and collaborate on Power BI content such as reports and semantic models, while an app provides a packaged, consumer-friendly way to distribute selected content from a workspace to a defined audience.

---

# 40. Final Takeaway

The main lesson of this session is:

> **Don't just publish a report—when you need to distribute it to business users in a structured way, you can create a Power BI App from the workspace and share the app with the intended audience.**

The complete process is:

**Power BI Desktop**
↓
**Publish report**
↓
**Azure Power BI project workspace**
↓
**Report + Semantic Model**
↓
**Create App**
↓
**Azure PBI app**
↓
**Add report/content**
↓
**Configure audience**
↓
**Publish App**
↓
**Generate app link**
↓
**Share with users**
↓
**Users access Brands & Details pages through the app**
