# Power BI Lecture Notes — Scheduling Refresh

This lecture explains how to configure **Scheduled Refresh** for a Power BI semantic model after the report has been published to Power BI Service.

The main workflow is:

**Power BI Service → Workspace → Semantic Model → Gateway/Cloud Connections → Data Source Credentials → Schedule Refresh**

---

# 1. Why Do We Need Scheduled Refresh?

In the previous lecture, the report was published from **Power BI Desktop** to **Power BI Service**.

Now the objective is to ensure that the data in the published report is periodically refreshed.

The idea demonstrated in this lecture is:

> If the data source changes, scheduled refresh allows those changes to be reflected in the Power BI dataset/semantic model and therefore in the report.

The instructor plans to test this by:

1. Recording the current values in the report.
2. Making changes to the underlying data source.
3. Waiting for the scheduled refresh.
4. Opening the report again.
5. Checking whether the changed values are reflected.

---

# 2. Open the Power BI Account

The instructor begins by accessing the Power BI account.

### Steps

1. Go to Power BI Service.
2. At the top-right, click the account/profile area.
3. Select **View account**.
4. Wait for the account page to load.
5. Return to the **Home** tab.

The account being used is the same account that was used to publish the report.

---

# 3. Open the Workspace

Previously, two locations were used:

* **My Workspace**
* **Test Power BI Project Two**

For this demonstration, the instructor opens:

### **Test Power BI Project Two**

### Steps

1. Click **Home**.
2. Click **Workspaces**.
3. Open **Test Power BI Project Two**.

Inside the workspace, the instructor can see two important items/icons.

---

# 4. Report vs. Semantic Model

Inside the workspace, there are two different types of objects visible:

### 1. Report

This represents the actual Power BI report containing the report pages and visuals.

### 2. Semantic Model

The second object is labelled **Semantic model**.

The semantic model is the data/model behind the report.

For configuring refresh, the important object is the **semantic model**, rather than the report itself.

---

# 5. Open Scheduled Refresh

To configure refresh:

1. Locate the **Semantic model**.
2. Look toward the right-hand side.
3. Find the **Schedule refresh** option.
4. Click **Schedule refresh**.

This opens the refresh configuration page.

---

# 6. Initial Problem: Gateway Is Required

Initially, the instructor notices that options related to:

* **Data source credentials**
* **Refresh**

cannot be properly configured.

The reason is that a gateway has not yet been configured.

The lecture shows an expanded section called:

### **Gateway and cloud connections**

When expanded, Power BI indicates that there are **no data gateways** available.

Therefore, the next step is to install and configure a gateway.

---

# 7. Install the Data Gateway

Power BI provides an option:

### **Install now**

The instructor clicks this option.

The gateway installation file is downloaded.

The downloaded file is referred to in the lecture as:

**On-premises data gateway**

The downloaded installer is then opened.

---

# 8. Power BI Data Gateway

The lecture introduces two gateway modes:

1. **Standard mode**
2. **Personal mode**

For this demonstration, the instructor uses:

### **Personal Mode**

The instructor explains that personal mode is recommended for **single users** in this context.

So the lecture specifically demonstrates:

> **Personal Mode Data Gateway**

rather than Standard Mode.

---

# 9. Install the Personal Mode Gateway

After opening the downloaded gateway installer:

1. Start the installation.
2. Accept the **terms of use**.
3. Click **Install**.
4. Wait for the installation to complete.

The installation may take some time.

---

# 10. Sign In to the Gateway

After installation, the gateway asks for the email address associated with the Power BI account.

### Steps

1. Enter the same email address used for Power BI.
2. Click **Sign in**.
3. If prompted, select **Use another account** if necessary.
4. Enter the Power BI account email address again.
5. Click **Next**.
6. Enter the password.
7. Click **Sign in**.

---

# 11. Verify Gateway Status

After successfully signing in, the gateway indicates:

### **Gateway is online and ready to be used**

This is an important checkpoint.

It means:

* The gateway installation was successful.
* The gateway is online.
* Power BI can use the gateway for the refresh configuration.

The instructor then clicks elsewhere and returns to the Power BI Service page.

---

# 12. Refresh the Power BI Service Page

After installing and configuring the gateway:

1. Return to the Power BI Service.
2. Refresh the page.
3. Return to the semantic model's refresh settings.

The gateway should now be available.

---

# 13. Configure Data Source Credentials

After refreshing the page, the instructor sees an issue under **Data Source Credentials**:

> **Failed to test the connection to your data source**

Therefore, the credentials need to be configured.

### Steps

1. Go to **Data Source Credentials**.
2. Click **Edit Credentials**.
3. Select the appropriate authentication method.

In the demonstration, the instructor chooses:

### **Windows without impersonation**

4. Click **Sign in**.

This configures the credentials required to connect to the data source.

---

# 14. Enable Scheduled Refresh

After configuring the credentials, the **Refresh** setting becomes available.

Initially, refresh is shown as:

### **Off**

The instructor changes this to:

### **On**

This enables scheduled refresh for the semantic model.

---

# 15. Configure the Time Zone

Power BI allows you to specify the time zone in which the scheduled refresh should occur.

The lecture shows the time zone:

### **UTC +05:30 — Chennai, Kolkata, Mumbai, New Delhi**

This corresponds to the time zone being used in the demonstration.

### Steps

1. Open the time-zone selection.
2. Select the appropriate time zone.
3. The instructor selects:
   **Chennai, Kolkata, Mumbai, New Delhi — UTC+05:30**

You can select another time zone according to your requirements.

---

# 16. Configure Refresh Frequency

Power BI also allows you to specify how frequently the data should be refreshed.

The instructor wants the report to refresh:

### **Daily**

So the refresh frequency is configured as **Daily**.

The available frequency and timing options can be configured according to the requirements.

---

# 17. Configure the Refresh Time

After selecting the frequency and time zone, a specific refresh time can be configured.

The instructor initially discusses selecting a time approximately 15–20 minutes into the future so that the refresh can be observed during the demonstration.

The final example uses approximately:

### **4:30 AM**

The purpose is not the specific time itself, but to schedule a refresh time that allows the instructor to later check whether the refresh actually occurred.

### Steps

1. Select the refresh frequency.
2. Select the time zone.
3. Select the desired refresh time.
4. Click **Apply**.

---

# 18. Scheduled Refresh Is Now Configured

After clicking **Apply**, the semantic model has a scheduled refresh configuration.

The basic configuration is:

| Setting                 | Demonstration                 |
| ----------------------- | ----------------------------- |
| Gateway                 | Personal Mode                 |
| Gateway Status          | Online                        |
| Data Source Credentials | Configured                    |
| Authentication          | Windows without impersonation |
| Refresh                 | On                            |
| Frequency               | Daily                         |
| Time Zone               | UTC+05:30                     |
| Example Refresh Time    | 4:30 AM                       |

---

# 19. Test Whether Scheduled Refresh Works

The instructor now wants to test the configuration.

The testing strategy is important.

### Current state

First, record some values from the existing report.

The instructor returns to the workspace where the report is stored.

### Steps

1. Click **Home**.
2. Click **Workspaces**.
3. Open the workspace containing the report.
4. Open the report.
5. Observe and record some current values.

These values will act as the **baseline** for comparison.

---

# 20. Record the Current Report Values

The instructor chooses **Premium Amount** as the main value for comparison.

The current Premium Amount is approximately:

### **5.97 million**

The instructor also observes the gender distribution:

* **Female customers = 5,000**
* **Male customers = 5,000**

Total:

### **10,000 customers**

These values are recorded so that they can later be compared against the report after the scheduled refresh.

---

# 21. Make Changes to the Data Source

The next step, according to the testing plan, is to make some changes to the underlying data source.

The idea is:

**Original Data**

→ Record current report values

→ **Modify Data Source**

→ Scheduled Refresh

→ **Updated Semantic Model**

→ **Updated Report**

The instructor will then return to the report after the scheduled refresh and check whether the changes are reflected.

---

# 22. What Are We Actually Testing?

The purpose of the experiment is to verify that:

> Changes made in the underlying data source are reflected in Power BI after the scheduled refresh runs.

For example:

### Before refresh

Premium Amount:

**5.97 million**

Female:

**5,000**

Male:

**5,000**

↓

### Change data source

Modify/add data.

↓

### Scheduled refresh runs

Power BI refreshes the semantic model.

↓

### After refresh

Open the report again and compare the values.

If the changed values appear, the scheduled refresh is working.

---

# 23. Complete Scheduled Refresh Workflow

The entire process from the lecture can be remembered as:

**Power BI Service**

↓

**Open Workspace**

↓

**Open Semantic Model**

↓

**Schedule Refresh**

↓

**Gateway and Cloud Connections**

↓

No gateway available

↓

**Install Now**

↓

**Download On-premises Data Gateway**

↓

**Install Personal Mode**

↓

**Accept Terms**

↓

**Install**

↓

**Sign in with Power BI account**

↓

**Gateway Online**

↓

**Refresh Power BI Service**

↓

**Edit Data Source Credentials**

↓

Select:

**Windows without impersonation**

↓

**Sign in**

↓

Turn:

**Refresh → On**

↓

Select:

**Time Zone**

↓

Select:

**Daily**

↓

Select:

**Refresh Time**

↓

**Apply**

↓

**Record Current Report Values**

↓

**Modify Data Source**

↓

Wait for scheduled refresh

↓

**Open Report Again**

↓

**Compare Old vs. New Values**

---

# 24. Important Concepts to Remember

## Gateway

A gateway provides the connection between Power BI Service and the relevant data source when a gateway is required.

In this lecture, the instructor installs the **On-premises Data Gateway**.

---

## Personal Mode

The lecture demonstrates **Personal Mode**.

It is presented as suitable for a **single user** in this context.

The lecture also mentions that another mode exists:

* Standard Mode
* Personal Mode

But only Personal Mode is demonstrated.

---

## Semantic Model

The **semantic model** is the data/model object associated with the report.

The scheduled refresh configuration is accessed through the semantic model.

Therefore, don't look for the refresh configuration by simply opening the report.

The workflow is:

**Workspace → Semantic Model → Schedule Refresh**

---

## Data Source Credentials

The credentials allow Power BI to establish the required connection to the data source.

In the demonstration, the credentials initially fail to test.

The instructor resolves this by:

**Edit Credentials → Windows without impersonation → Sign in**

---

## Scheduled Refresh

Scheduled refresh automatically refreshes the semantic model according to the configured schedule.

The instructor configures:

* Refresh = **On**
* Frequency = **Daily**
* Time zone = **UTC+05:30**
* A specific refresh time

---

# 25. Key Difference: Report vs. Semantic Model

This is an important distinction from the lecture.

### Report

Contains:

* Visuals
* Charts
* Slicers
* Report pages
* Interactive report experience

### Semantic Model

Contains the underlying model/data that the report uses.

### For scheduled refresh

You configure refresh on the:

**Semantic Model**

not directly on the report.

---

# 26. Key Takeaways for Revision

### Why scheduled refresh?

To make sure changes in the underlying data source are reflected in the Power BI report.

### Where do you configure it?

**Workspace → Semantic Model → Schedule Refresh**

### What is needed before scheduling refresh?

A properly configured **gateway** when the data source requires one.

### Which gateway is demonstrated?

**On-premises Data Gateway — Personal Mode**

### What must be configured?

1. Gateway
2. Data source credentials
3. Refresh = On
4. Refresh frequency
5. Time zone
6. Refresh time

### Demonstration settings

**Frequency:** Daily
**Time zone:** UTC+05:30 — Chennai, Kolkata, Mumbai, New Delhi
**Example refresh time:** 4:30 AM

### How is it tested?

1. Record current report values.
2. Change the data source.
3. Wait for scheduled refresh.
4. Open the report again.
5. Compare the values.

The lecture ends at the point where the instructor has recorded the current values and is preparing to make changes to the data source to verify that scheduled refresh works.
