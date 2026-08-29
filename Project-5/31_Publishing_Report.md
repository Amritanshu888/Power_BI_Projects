# Power BI — Publishing a Report to Power BI Service & Setting Up Report Refresh

## 1. Objective of the Session

This session covers two major tasks:

1. **Publishing a Power BI Desktop report to Power BI Service**
2. **Configuring refresh for the published report/semantic model**

The important concept is that refreshing the **Data Flow** alone is not enough. If the report is built using that Data Flow, the **report's semantic model must also be refreshed** so that the report displays the latest data and insights.

---

# 2. Publishing a Power BI Desktop Report

The report used in the lecture was created in **Power BI Desktop**.

Before publishing it, you need to make sure that you are **signed in to your Power BI account**.

---

## 3. Sign in to Power BI

### Why sign-in is required

You need to be authenticated with your Power BI account to publish the report to Power BI Service.

If you are not signed in and click **Publish**, Power BI will ask you to provide your Power BI credentials.

### Steps

1. Open the report in **Power BI Desktop**.
2. Look at the top-right corner.
3. Click **Sign in**.
4. Enter your Power BI account credentials.
5. Complete the sign-in process.

### If you don't have an account

The lecture refers to an earlier course video covering how to create a **free Power BI account**.

---

# 4. Publish the Report

Once you are signed in:

### Steps

1. Go to the **Home** tab.
2. Click **Publish**.
3. Power BI may ask whether you want to save changes.
4. Select **Yes/Save Changes** as appropriate.
5. Power BI will ask you to select a destination/workspace.
6. Select the workspace created for the project.

In the lecture, the workspace is:

```text id="3nq5uk"
Data Flow
```

7. Double-click/select the workspace.
8. Power BI begins publishing the report.

The publishing process may take some time.

---

# 5. Open the Published Report

After publishing, the instructor opens the report in Power BI Service.

The report is referred to as:

```text id="2ftx5a"
Loan default copy
```

with the `.pbix` report originating from Power BI Desktop.

### Steps

1. Click **Open** after publishing.
2. Power BI Service opens the published report.
3. Wait for the report to load.
4. The different report pages created in Power BI Desktop will be available in Power BI Service.

The instructor verifies that all the previously created pages are visible.

---

# 6. Understanding What Gets Published

When you publish a Power BI Desktop report to Power BI Service, you will see two important components in the workspace.

### 1. Report

The first component is the **Report**.

It can be identified by the **Report icon/symbol**.

The report contains things such as:

* Report pages
* Visualizations
* Charts
* Slicers
* Other report-level presentation elements

### 2. Semantic Model

The second component is the **Semantic Model**.

The semantic model contains the underlying data/model that powers the report.

Conceptually:

```text id="7vmt8p"
Power BI Desktop
       │
       │ Publish
       ↓
Power BI Service Workspace
       │
       ├── Report
       │
       └── Semantic Model
```

---

# 7. Important Data Flow → Semantic Model → Report Relationship

This is one of the most important concepts from this lecture.

The project uses a **Data Flow** as the source for the report.

Therefore, there is effectively a refresh chain:

```text id="1c7lhy"
Source Database
(SQL Server)
       ↓
Data Flow
       ↓
Semantic Model
       ↓
Report
```

For example:

1. SQL Server gets new/updated data.
2. The Data Flow is refreshed.
3. The semantic model needs to retrieve the updated data.
4. The report then displays the latest insights.

### Important

> Refreshing the Data Flow does **not automatically mean that the report/semantic model has been refreshed**.

Therefore, you need to configure refresh for the report's semantic model as well.

---

# 8. Refreshing the Published Report

Once the report is published, you can refresh its underlying semantic model.

There are two approaches discussed:

### Manual Refresh

You can manually trigger the refresh.

### Scheduled Refresh

You can configure a schedule so that the semantic model automatically refreshes at predefined times.

---

# 9. Manual Refresh of the Semantic Model

Suppose the Data Flow has already been refreshed and contains the latest data.

You can manually refresh the semantic model.

### Steps

1. Go to the relevant **Workspace**.
2. Locate the **Semantic Model**.
3. Click the **Refresh** option.
4. The refresh operation begins.

This is similar to manually refreshing the Data Flow.

---

# 10. Refresh Error Encountered in the Lecture

When the instructor initially tries to configure the refresh, Power BI displays an error:

> Schedule refresh has been disabled. Please try again later or contact support.

The instructor also observes that the previous refresh had failed.

The failure occurred because there was a problem with the **connection to the data source**.

---

# 11. Checking Refresh Details

To investigate the failure:

1. Open the refresh/schedule refresh settings.
2. Observe that the **last refresh failed**.
3. Click **Details**.
4. Scroll down to inspect the error information.

The important error shown is related to the data source connection:

> Failed to test the connection to your data source.

Therefore, the data source connection/credentials need to be updated.

---

# 12. Updating Data Source Credentials

To fix the connection issue:

### Steps

1. Locate the data source credentials section.
2. Click **Edit credentials**.
3. Select the available **Authentication Method**.
4. In the lecture, only one authentication option is available, so that option is selected.
5. Configure the **Privacy Level**.

The instructor chooses:

```text id="e3jz5u"
Privacy Level = None
```

6. Click **Sign in**.
7. Select the Power BI account being used for the project.
8. Complete authentication.

After this, the data source credentials are updated.

The lecture displays a message indicating that the **Power Platform Data Flows data source has been updated**.

---

# 13. Why Credentials Were Updated

The earlier refresh failed because Power BI could not successfully establish a connection to the data source.

Therefore:

```text id="5u3v2p"
Refresh Failed
      ↓
Check Details
      ↓
Data Source Connection Failed
      ↓
Edit Credentials
      ↓
Authenticate
      ↓
Credentials Updated
      ↓
Try Refresh Again
```

This is an important troubleshooting workflow when a Power BI Service refresh fails.

---

# 14. Setting Up Scheduled Refresh for the Report

After updating the credentials, the instructor configures a **scheduled refresh** for the semantic model.

The important point is that the report should be refreshed **after the Data Flow has been refreshed**.

---

# 15. Refresh Order

Suppose the Data Flow is scheduled to refresh at:

```text id="m8a6h7"
5:30 AM
```

The semantic model should be refreshed **afterward**.

Why?

Because the Data Flow needs time to obtain and process the latest source data first.

Conceptually:

```text id="j1x6eg"
5:30 AM
   ↓
Data Flow Refresh
   ↓
Data Flow gets latest data
   ↓
Wait for Data Flow refresh to complete
   ↓
7:00 AM
   ↓
Semantic Model Refresh
   ↓
Report gets latest data
```

The instructor chooses approximately **1.5 hours after the Data Flow refresh** to give the Data Flow sufficient time to complete.

---

# 16. Configure the Report Refresh Schedule

### Steps

1. Open the **Semantic Model**.
2. Select **Schedule Refresh**.
3. Choose an appropriate **Time Zone**.
4. Turn the scheduled refresh **ON**.
5. Select the refresh frequency.

In the lecture:

```text id="1v5kik"
Frequency = Daily
```

6. Select a suitable refresh time.

The Data Flow was scheduled for approximately:

```text id="1v6m4a"
5:30 AM
```

The semantic model/report refresh is scheduled for:

```text id="e5c4ay"
7:00 AM
```

This provides approximately **1.5 hours** between the Data Flow refresh and the semantic model refresh.

---

# 17. Why Schedule the Report After the Data Flow?

This sequencing is extremely important.

If the semantic model refreshes **before** the Data Flow has finished updating, the semantic model may retrieve old data.

### Incorrect sequence

```text id="wq8j54"
7:00 AM → Semantic Model Refresh
5:30 AM → Data Flow Refresh
```

This would be problematic because the order is reversed.

### Correct sequence

```text id="5c3qfq"
5:30 AM → Data Flow Refresh
       ↓
Data Flow updated
       ↓
7:00 AM → Semantic Model Refresh
       ↓
Report updated
```

The time gap gives the Data Flow enough time to complete.

---

# 18. Refresh Failure Notifications

The schedule configuration also contains an option to send a **refresh failure notification**.

In the lecture, the selected recipient is:

```text id="2e8i1p"
Semantic Model Owner
```

### Additional contacts

If other people need to receive failure notifications:

1. Select the option for additional contacts.
2. Enter their email addresses.
3. They will also receive notifications when the refresh fails.

For this example, only the **Semantic Model Owner** is selected.

---

# 19. Apply the Schedule

Once the configuration is complete:

1. Verify the time zone.
2. Verify that scheduled refresh is **ON**.
3. Verify frequency = **Daily**.
4. Verify the selected refresh time.
5. Verify failure notification settings.
6. Click **Apply**.

The configuration is then updated successfully.

---

# 20. Verify the Next Scheduled Refresh

After applying the schedule, scroll back up or refresh the page.

The instructor observes:

* The previous refresh had failed.
* The **Next Refresh** is now scheduled for **17 March at 7:00 AM**.

This confirms that the schedule has been configured.

The previous failure message is expected to disappear once a subsequent refresh succeeds.

---

# 21. Manually Test the Refresh

After updating the credentials, the instructor also demonstrates a manual refresh.

### Steps

1. Go to **Workspaces**.
2. Open the **Data Flow** workspace.
3. Locate the **Semantic Model**.
4. Click **Refresh**.
5. The refresh begins.

The interface displays:

```text id="q82u4n"
Refresh in progress
```

This confirms that the manual refresh has started successfully after correcting the credentials.

---

# 22. Checking Refresh History

Power BI provides **Refresh History** to investigate previous refresh attempts.

### Steps

1. Locate the Semantic Model.
2. Click the **three dots (...)**.
3. Select **Refresh History**.

The history shows previous refresh operations.

In the lecture, two different outcomes can be seen:

### Earlier refresh

```text id="g7y5pr"
Status = Failed
```

This was the refresh that failed because of the data source connection/credential issue.

### Later manual refresh

```text id="lqk4ds"
Type = On demand
Status = Completed
```

This refresh was manually triggered after the credentials were updated and completed successfully.

---

# 23. Complete Refresh Architecture

The entire project refresh flow can be understood as:

```text
             SQL Server
                 │
                 │ Source Data Updated
                 ↓
             Data Flow
                 │
                 │ Scheduled Refresh
                 ↓
       Latest Data Available
                 │
                 │
                 ↓
          Semantic Model
                 │
                 │ Scheduled Refresh
                 ↓
              Report
                 │
                 ↓
       Latest Insights
```

The key is to coordinate the schedules.

---

# 24. Full Practical Workflow

```text
Power BI Desktop
      ↓
Sign in to Power BI account
      ↓
Home → Publish
      ↓
Select Workspace
      ↓
Publish Report
      ↓
Open Report in Power BI Service
      ↓
Workspace
      ↓
Report + Semantic Model
      ↓
Configure Data Flow Refresh
      ↓
Data Flow refreshes first
      ↓
Configure Semantic Model Schedule Refresh
      ↓
Schedule it AFTER Data Flow
      ↓
Configure failure notifications
      ↓
Apply
      ↓
Verify Next Refresh
      ↓
Use Refresh History to monitor execution
```

---

# 25. Important Difference: Data Flow Refresh vs Report/Semantic Model Refresh

| Component          | Purpose                                          |
| ------------------ | ------------------------------------------------ |
| **Data Flow**      | Retrieves/processes updated data from the source |
| **Semantic Model** | Loads/updates the data used by the report        |
| **Report**         | Presents the data through visuals and insights   |

Therefore:

```text id="r0z0dw"
Data Flow Refresh
        ≠
Semantic Model Refresh
```

Both need to be appropriately configured.

---

# 26. Troubleshooting Refresh Failures

The lecture demonstrates an important troubleshooting approach.

### Problem

Refresh fails.

### Step 1 — Check Refresh History

```text id="a6h8c0"
Three dots (...)
      ↓
Refresh History
```

Determine whether the refresh failed.

### Step 2 — Check Details

Open the details of the failed refresh.

### Step 3 — Identify the Cause

In this case:

```text id="w7yqti"
Failed to test connection to data source
```

### Step 4 — Edit Credentials

```text id="qv3w9d"
Edit Credentials
      ↓
Authentication Method
      ↓
Privacy Level
      ↓
Sign In
```

### Step 5 — Retry Refresh

After updating credentials, manually refresh again.

### Step 6 — Verify

Check Refresh History.

Expected result:

```text id="l2l9ra"
Status = Completed
Type = On demand
```

---

# 27. Key Interview Questions

## Q1. What happens when you publish a Power BI Desktop report?

The report is published to a selected Power BI Service workspace, where you can see the **Report** and its associated **Semantic Model**.

---

## Q2. Is refreshing the Data Flow enough to update the report?

**No.**

The Data Flow needs to be refreshed first, and the semantic model consuming that Data Flow should also be refreshed so that the report can display the latest data.

---

## Q3. Why should the semantic model refresh happen after the Data Flow refresh?

Because the Data Flow needs to contain the latest data before the semantic model retrieves it.

Correct sequence:

```text
Source
 ↓
Data Flow Refresh
 ↓
Semantic Model Refresh
 ↓
Report
```

---

## Q4. How do you troubleshoot a failed Power BI Service refresh?

A typical process is:

```text
Refresh History
      ↓
Check failed refresh
      ↓
Open Details
      ↓
Identify error
      ↓
Edit Credentials
      ↓
Authenticate
      ↓
Retry Refresh
      ↓
Check Refresh History
```

---

## Q5. What is "On demand" in Refresh History?

**On demand** indicates that the refresh was manually triggered rather than being executed automatically according to the scheduled refresh.

---

# 28. Quick Revision Notes

### Publishing

```text
Power BI Desktop
→ Sign In
→ Home
→ Publish
→ Select Workspace
→ Publish
→ Open in Power BI Service
```

### Power BI Service components

```text
Workspace
├── Report
└── Semantic Model
```

### Refresh sequence

```text
SQL Server
→ Data Flow
→ Semantic Model
→ Report
```

### Example schedule

```text
Data Flow       → 5:30 AM
       ↓
    Wait ~1.5 hours
       ↓
Semantic Model  → 7:00 AM
```

### Refresh troubleshooting

```text
Failed Refresh
→ Details
→ Connection/Credentials Issue
→ Edit Credentials
→ Sign In
→ Manual Refresh
→ Refresh History
→ Completed
```

### Core takeaway

> **Always coordinate the Data Flow and Semantic Model refresh schedules. The Data Flow should refresh first, and the semantic model should refresh afterward so that the published report reflects the latest source data.**
