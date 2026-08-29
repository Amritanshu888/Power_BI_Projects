# Power BI Data Flow — Schedule Refresh

## 1. Objective of the Session

This session explains how to configure **Schedule Refresh for a Data Flow** in Power BI.

### Business requirement

Suppose the Data Flow is created using **Microsoft SQL Server** as the data source.

The source data in SQL Server may get updated over time. Since Power BI reports are going to use the Data Flow as their source, the Data Flow also needs to be updated regularly.

There are two ways to update it:

1. **Manual Refresh**
2. **Scheduled Refresh**

The session focuses on **Scheduled Refresh**.

---

# 2. Manual Refresh vs Scheduled Refresh vs Incremental Refresh

There are three refresh concepts discussed in the lecture.

### Manual Refresh

You manually trigger the refresh whenever you want.

```text
SQL Server
    ↓
Manual Refresh
    ↓
Entire Data Flow Updated
```

### Scheduled Refresh

You configure Power BI to automatically refresh the Data Flow at predefined times.

```text
SQL Server
    ↓
Scheduled Refresh
    ↓
Entire Data Flow Updated
```

Therefore, both **manual refresh and scheduled refresh refresh the entire data**.

---

## Incremental Refresh

Incremental refresh works differently.

Instead of refreshing the entire dataset/data every time, **only a specified portion of the data is refreshed** based on the conditions/time period you configure.

For example, you might configure the system to refresh only recent data.

```text
Existing Data
├── Older Data → Remains unchanged
└── Recent Data → Refreshed
```

### Why use incremental refresh?

If incremental refresh is applicable to your scenario, it is generally recommended because:

* Less data needs to be refreshed.
* Refresh takes less time.
* It reduces the refresh workload.
* It can improve overall report performance because refresh operations are faster.

### Key distinction

| Refresh Type        | Data Refreshed                  |
| ------------------- | ------------------------------- |
| Manual Refresh      | Entire data                     |
| Scheduled Refresh   | Entire data                     |
| Incremental Refresh | Only configured portion of data |

> **Interview point:** Be prepared to explain the difference between **Scheduled Refresh and Incremental Refresh**.

---

# 3. Opening the Data Flow

The lecture starts from the **Power BI Service**.

### Steps

1. Log in to your **Power BI account**.
2. Click **Workspaces**.
3. Navigate to the relevant workspace.
4. Click on **Data Flow**.

You are now ready to configure the Data Flow's refresh settings.

---

# 4. Opening Schedule Refresh

### Steps

1. Open the Data Flow.
2. Click **Schedule Refresh**.

You will see information about the currently configured refresh.

For example, the lecture initially shows a message similar to:

> Next refresh is scheduled to happen on Sunday, March 16, 2025 at 6:30.

The displayed time is based on the configured time zone, which in this example is **Indian Standard Time (IST)**.

Since a refresh had already been configured, the existing schedule is displayed.

---

# 5. Check Data Source Credentials

Before configuring the schedule, check the **Data Source Credentials** section.

### Steps

1. Expand **Data Source Credentials**.
2. Verify whether credentials/access are required.
3. In the lecture example, the administrator has already granted access.
4. Therefore, credentials are **not required** for this particular setup.

So this section can be left as it is.

---

# 6. Configure the Refresh Schedule

Now expand the **Refresh** section.

The first thing you need to configure is the **Time Zone**.

---

## Step 1 — Select Time Zone

Select the appropriate time zone according to your region.

In the lecture, the selected time zone is:

```text
(UTC+05:30) Chennai, Kolkata, Mumbai, New Delhi
```

This corresponds to **Indian Standard Time (IST)**.

### Important

Choose the time zone according to where you want the refresh schedule to be interpreted.

---

# 7. Enable Scheduled Refresh

After selecting the time zone:

1. Locate the **scheduled refresh toggle**.
2. Switch it **ON**.

This enables automatic refresh of the Data Flow.

---

# 8. Select Refresh Frequency

Power BI allows you to specify how frequently the refresh should occur.

The lecture discusses options such as:

* **Daily**
* **Weekly**

### Weekly refresh

If you select **Weekly**, you can also specify the **days** on which the refresh should happen.

For example:

```text
Monday
Wednesday
Friday
```

You can choose the required days according to your business requirement.

---

# 9. Configure a Daily Refresh

In this example, the instructor wants the Data Flow to refresh **daily**.

### Steps

1. Select **Daily** as the refresh frequency.
2. Select the required refresh time.
3. The lecture sets the time to:

```text
5:30 AM
```

Therefore, the Data Flow will be scheduled to refresh every day at **5:30 AM IST**.

---

# 10. Configure Refresh Failure Notifications

Another useful option is notification when the scheduled refresh fails.

There may be situations where a refresh cannot be completed successfully.

For example:

```text
SQL Server
    ↓
Scheduled Refresh
    ↓
Refresh Failure
```

In such a situation, Power BI can send a notification to the relevant people.

---

## Data Flow Owner

By default, you can select the **Data Flow Owner** to receive the refresh failure notification.

In the lecture, the instructor selects:

```text
Data Flow Owner
```

---

## Additional Contacts

You can also configure notifications for other people.

### Steps

1. Select the option to include additional contacts for refresh failure notifications.
2. Enter their **email addresses**.
3. These contacts will also receive notifications if the refresh fails.

In this example, the instructor does **not** add additional contacts and keeps only the **Data Flow Owner** selected.

---

# 11. Apply the Schedule

Once all settings have been configured:

1. Verify the time zone.
2. Verify the refresh frequency.
3. Verify the refresh time.
4. Verify the notification settings.
5. Click **Apply**.

The scheduled refresh configuration is now saved.

---

# 12. Verify the Next Refresh

After applying the settings, refresh/reload the page.

### Steps

1. Refresh the Power BI page.
2. Check the **Next Refresh** message.

The lecture demonstrates that the scheduled time has changed.

Initially it was:

```text
6:30 AM
```

After changing the schedule:

```text
5:30 AM
```

The message now indicates that the next refresh will happen at the newly configured time.

### Why verify?

This confirms that the new schedule has actually been applied.

---

# 13. Checking Refresh History

The lecture then demonstrates how to verify previous Data Flow refreshes.

### Steps

1. Go back to **Workspaces**.
2. Open the relevant **Data Flow**.
3. Click the **three-dot (...) menu**.
4. Select **Refresh History**.

This allows you to see previous refresh operations.

---

# 14. Understanding Refresh History

The Refresh History shows information about when the Data Flow was previously updated/refreshed.

In the lecture example:

* The Data Flow was last updated on **14 March 2025**.
* The current time was **16 March 2025, approximately 5:20 AM**.
* The next scheduled refresh was at **5:30 AM**.

Therefore, the instructor expected another refresh to occur in approximately **10 minutes**.

The plan was to wait and then check the Refresh History again to verify that the scheduled refresh had executed successfully.

---

# 15. How to Verify That Scheduled Refresh Worked

The verification process demonstrated in the lecture is:

```text
Configure Schedule Refresh
        ↓
Click Apply
        ↓
Refresh/Reload Power BI page
        ↓
Verify "Next Refresh"
        ↓
Wait until scheduled time
        ↓
Open Data Flow
        ↓
Three dots (...)
        ↓
Refresh History
        ↓
Verify new refresh entry
```

This is important because simply configuring a schedule does not mean you should assume it worked—you can verify the execution through **Refresh History**.

---

# 16. Complete Configuration Flow

For quick revision:

```text
Login to Power BI
       ↓
Workspaces
       ↓
Open Data Flow
       ↓
Schedule Refresh
       ↓
Check Data Source Credentials
       ↓
Expand Refresh
       ↓
Select Time Zone
       ↓
Enable Schedule Refresh
       ↓
Choose Frequency
       ↓
Daily / Weekly
       ↓
Select Refresh Time
       ↓
Configure Failure Notifications
       ↓
Select Data Flow Owner
       ↓
Optionally add other contacts
       ↓
Click Apply
       ↓
Refresh Page
       ↓
Verify Next Refresh
       ↓
Check Refresh History after execution
```

---

# 17. Important Interview Concepts

This topic is specifically highlighted as an **important interview question**.

### Question 1: What is Scheduled Refresh?

Scheduled Refresh automatically refreshes the Data Flow at predefined intervals/times so that changes in the source data are reflected in the Data Flow.

---

### Question 2: What happens during a scheduled refresh?

The Data Flow is refreshed according to the configured schedule, and in the context discussed in this lecture, the **entire data** is refreshed.

```text
Updated Source
      ↓
Scheduled Refresh
      ↓
Entire Data Flow Refreshed
      ↓
Reports using the Data Flow
      ↓
Updated Data
```

---

### Question 3: What is Incremental Refresh?

Incremental Refresh refreshes **only a specified portion of the data** instead of refreshing the complete data every time.

---

### Question 4: Scheduled Refresh vs Incremental Refresh

| Feature          | Scheduled Refresh                                      | Incremental Refresh                                            |
| ---------------- | ------------------------------------------------------ | -------------------------------------------------------------- |
| Refresh approach | Entire data                                            | Only configured portion                                        |
| Refresh time     | Can be higher for large data                           | Generally lower                                                |
| Suitable for     | Smaller/moderate data or when full refresh is required | Large datasets where only recent/changed data needs refreshing |
| Performance      | Can require more resources                             | Can reduce refresh workload                                    |
| Configuration    | Schedule/frequency/time                                | Requires defining the incremental portion/time period          |

### Interview-ready answer

> **Scheduled refresh refreshes the entire data according to a predefined schedule, whereas incremental refresh refreshes only a specified portion of the data. Incremental refresh is generally preferred for large datasets when applicable because it reduces the amount of data processed and can significantly reduce refresh time.**

---

# 18. Key Takeaways

* **Manual Refresh** and **Scheduled Refresh** refresh the entire data in the scenario discussed.
* **Scheduled Refresh** automates the refresh process.
* Always configure the appropriate **time zone**.
* Refresh frequency can be **Daily** or **Weekly**.
* Weekly schedules allow you to select specific days.
* You can configure a specific **refresh time**.
* You can enable **refresh failure notifications**.
* The **Data Flow Owner** can receive failure notifications.
* Additional contacts can also be added through their email addresses.
* Click **Apply** to save the schedule.
* Verify the configured schedule using the **Next Refresh** message.
* Use **Refresh History** to verify whether the refresh actually executed.
* **Incremental Refresh** refreshes only a selected/configured portion of data and can reduce refresh time.
* The difference between **Scheduled Refresh and Incremental Refresh** is an important interview topic.
