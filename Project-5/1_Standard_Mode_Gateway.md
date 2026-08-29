# Data Flows as a Data Source in Power BI — Detailed Notes

## 1. Introduction to Data Flows

**Data Flow** is an advanced concept in Power BI that can be used as a **data source** for a Power BI project.

The overall objective of this session is to:

* Use a **Data Flow as a data source** in Power BI.
* Set up the required **On-premises Data Gateway**.
* Understand how to install and configure the gateway.
* Prepare the environment for establishing a connection between the data source and the Power BI Data Flow.

### Why is this important?

Data Flows are an important advanced Power BI topic and can be asked about in **Power BI interviews**.

Having practical experience with a project that uses a Data Flow as a data source can be useful when explaining your project experience during interviews.

---

# 2. Prerequisites

Before working with Data Flows, the following are required:

1. **Power BI Desktop**
2. **Power BI account**
3. A Power BI workspace
4. **On-premises Data Gateway — Standard Mode**

The instructor uses a **free Power BI account/trial account** for this project.

> The lecture mentions a 60-day free trial for the Power BI account.

If you do not know how to create the account or install Power BI Desktop, refer to the introductory section of the course.

---

# 3. Sign in to Power BI Desktop

First, open **Power BI Desktop**.

On the right-hand side of the Power BI Desktop home screen, there is a **Sign in** option.

### Steps

1. Open **Power BI Desktop**.
2. Look at the top-right corner.
3. Click **Sign in**.
4. Enter the credentials associated with your Power BI account.
5. Sign in successfully.

If you are already signed in, Power BI will display:

* Your account name
* Your email address

### Changing the signed-in account

If you want to sign in using a different account:

1. Click the current account/profile option.
2. Select the option to sign in with another user/account.
3. Enter the required credentials.
4. Sign in.

---

# 4. Open the Power BI Account

Once signed in:

1. Go to the **Home** tab.
2. Click **View Account** if required.
3. Power BI will open the Power BI account in the browser.

If Power BI asks for credentials, use the same credentials that were used while creating the free Power BI account.

---

# 5. Create a New Workspace

The next step is to create a workspace that will be used for the Data Flow project.

### Steps

1. Go to the **Home** tab.
2. Click **Workspaces**.
3. Select **New Workspace**.
4. Enter a suitable workspace name.

In the lecture, the workspace is named:

**Data Flow**

5. Enter the workspace name.
6. Click **Apply**.

Power BI may take some time to create the workspace.

After creation, the **Data Flow** workspace becomes available.

### Important

The workspace will be used later when creating and working with the Data Flow.

---

# 6. Why Do We Need a Gateway?

The next requirement is the **Data Gateway**.

A gateway is required to establish connectivity between Power BI services and certain data sources, particularly when the data source is located in an environment that Power BI Service cannot directly access.

For this particular project, the instructor uses a:

> **Standard Mode Data Gateway**

---

# 7. Download the Data Gateway

Power BI provides two gateway modes:

1. **Standard Mode**
2. **Personal Mode**

### Standard Mode Gateway

The Standard Mode gateway is recommended when:

* Working in a team
* Working with enterprise scenarios
* Sharing gateway connectivity
* Working with Data Flows

For this project, the **Standard Mode Gateway is required**.

### Personal Mode Gateway

The lecture mentions that Personal Mode was already discussed in an earlier project, including:

* Downloading the Personal Mode Gateway
* Installing it
* Configuring it

However, **Personal Mode is not used in this project**.

---

# 8. Steps to Download Standard Mode Gateway

From the Power BI environment:

1. Go to the **Home** tab.
2. Look toward the top-right area.
3. Click **Download**.
4. Select **Data Gateway**.

You will then see two options:

* Standard Mode
* Personal Mode

Select:

**Standard Mode**

5. Click **Download Standard Mode**.
6. Wait for the gateway installer to download.

The downloaded installer will be used to install the gateway on the computer.

---

# 9. Install the Standard Mode Gateway

Once the download is complete:

1. Open the downloaded file's location.
2. Locate the gateway installer.
3. Double-click the gateway installation file.

The installation wizard will open.

### Installation steps

#### Step 1 — Select installation path

The installer will ask you to select the installation location/path.

Choose the appropriate path.

#### Step 2 — Accept terms

Read and accept:

* Terms of Use
* Privacy Statement

Then click:

**Install**

Windows may ask for administrator permission.

Click:

**Yes**

The installation process will begin.

The installation may take some time.

Additional permission prompts may appear during installation.

Click **Yes** when required.

---

# 10. Sign in to the Gateway

After installation, the gateway configuration process begins.

You need to sign in using the **same Power BI account credentials**.

### Steps

1. Enter the email/account used for the Power BI account.
2. Click **Sign in**.
3. Select the appropriate account.
4. Enter the password.
5. Click **Sign in**.

### Authentication / Approval

Depending on the account configuration, an additional approval/authentication screen may appear.

For example, the instructor has an **Authenticator app** activated, so an additional request approval message appears.

This may not appear for every user.

If your account does not have additional authentication enabled, you may be able to proceed directly after signing in.

---

# 11. Register a New Gateway

After successfully signing in, the gateway configuration screen appears.

You need to register the gateway on the current computer.

Select:

**Register a new gateway on this computer**

Then click:

**Next**

---

# 12. Give the Gateway a Name

The gateway needs a unique/suitable name.

In the lecture, the gateway is named:

**DF1**

where:

* **DF** → Data Flow
* **1** → Gateway number

So:

**DF1 = Data Flow 1**

You can use another suitable name depending on your project/environment.

---

# 13. Create a Recovery Key

The next important step is configuring the **Recovery Key**.

The gateway requires a recovery key during registration.

In the lecture, the instructor uses:

**123456789**

and then confirms the same key again.

### Steps

1. Enter a recovery key.
2. Confirm the recovery key.
3. Click **Configure**.

### Important practical point

The recovery key is an important security credential for the gateway. In a real production environment, you should **not use an easily guessable key such as `123456789`**.

Instead, use a strong, securely stored recovery key according to your organization's security policy.

The simple number sequence was only used in the lecture demonstration.

---

# 14. Gateway Configuration

After clicking **Configure**, Power BI begins configuring the gateway.

This may take some time.

Wait for the configuration process to finish.

Once successful, Power BI displays a message similar to:

> **Gateway DF1 is online and ready to be used.**

This confirms that:

* The gateway installation was successful.
* The gateway was successfully registered.
* The gateway is online.
* Power BI can use the gateway for the required connectivity.

---

# 15. Complete Flow of the Setup

The entire process can be remembered as:

**Power BI Desktop**
↓
**Sign in to Power BI account**
↓
**Create Workspace**
↓
**Workspace: Data Flow**
↓
**Download Data Gateway**
↓
**Select Standard Mode**
↓
**Install Gateway**
↓
**Sign in with Power BI credentials**
↓
**Register a new gateway**
↓
**Give gateway a name — DF1**
↓
**Create & confirm Recovery Key**
↓
**Configure**
↓
**Gateway becomes Online**

---

# 16. Standard Mode vs Personal Mode

| Feature               | Standard Mode             | Personal Mode    |
| --------------------- | ------------------------- | ---------------- |
| Intended use          | Team/enterprise scenarios | Individual users |
| Team sharing          | Suitable                  | Limited          |
| Data Flow project     | **Used in this project**  | Not used         |
| Gateway management    | Centralized               | Personal         |
| Recommended for teams | **Yes**                   | No               |

### Key interview point

If asked:

**Which gateway mode would you use when working with a team and Data Flows?**

Answer:

> **Standard Mode Gateway**, because it is designed for shared/enterprise scenarios and is the appropriate gateway mode for this Data Flow setup.

---

# 17. Important Points to Remember

### Data Flow

* Data Flow is an advanced Power BI concept.
* It can be used as a **data source** for Power BI projects.
* It is useful for data preparation/transformation scenarios.
* Practical experience with Data Flows can be useful in Power BI interviews.

### Workspace

* A workspace is created in Power BI Service.
* The lecture creates a workspace named **Data Flow**.
* This workspace will be used for the Data Flow project.

### Gateway

* The project requires a **Data Gateway**.
* Two gateway modes are available:

  * Standard Mode
  * Personal Mode
* **Standard Mode** is used for this project.
* Standard Mode is preferred for team/enterprise scenarios.

### Gateway Registration

During registration, you need to:

1. Sign in.
2. Register a new gateway.
3. Give the gateway a name.
4. Provide a recovery key.
5. Confirm the recovery key.
6. Configure the gateway.

### Successful Setup

The final confirmation is that the gateway is:

**Online and ready to be used.**

---

# 18. Interview Questions from This Session

### Q1. What is a Data Flow in Power BI?

A Data Flow is a cloud-based data preparation capability in the Power BI/Fabric ecosystem that allows data to be ingested and transformed before being consumed by downstream analytics tools such as Power BI.

### Q2. Why is a gateway required?

A gateway provides connectivity between Power BI services and data sources that require gateway-based access, particularly when the source isn't directly accessible from the Power BI service.

### Q3. What are the two gateway modes?

* Standard Mode
* Personal Mode

### Q4. Which gateway mode is used in this project?

**Standard Mode Gateway.**

### Q5. Why use Standard Mode instead of Personal Mode?

Standard Mode is appropriate for **team and enterprise scenarios** because the gateway can be centrally managed and shared.

### Q6. What information is required while registering a gateway?

You need:

* Power BI account credentials
* Gateway name
* Recovery key
* Recovery key confirmation

### Q7. How do you verify that the gateway was configured successfully?

After configuration, Power BI displays a message indicating that the gateway is **online and ready to be used**.

### Q8. What workspace was created in this lecture?

A workspace named:

**Data Flow**

was created.

---

## 19. What Has Been Completed in This Session?

At the end of this lecture, the following setup has been completed:

* ✅ Power BI Desktop account signed in
* ✅ Power BI workspace created
* ✅ Workspace named **Data Flow**
* ✅ Standard Mode Data Gateway downloaded
* ✅ Gateway installed
* ✅ Gateway account signed in
* ✅ Gateway registered on the computer
* ✅ Gateway named **DF1**
* ✅ Recovery key configured
* ✅ Gateway successfully configured
* ✅ Gateway status confirmed as **Online**

### What comes next?

The gateway is now ready. The **next session will focus on establishing the remaining connections and creating/configuring the Data Flow**.
