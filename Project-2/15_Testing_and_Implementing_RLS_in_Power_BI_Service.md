# Power BI Row-Level Security (RLS) — Validating Roles in Power BI Service

## 1. Overview

In the previous session, we created **Row-Level Security (RLS) roles in Power BI Desktop**.

The roles created were:

* **Health Role**
* **Travel Role**

In this session, we learn how to:

1. Validate/test those roles in **Power BI Service**.
2. Assign users to specific RLS roles using their **email addresses**.
3. Understand how users see filtered data after logging into Power BI.
4. Review the role of **Power BI Gateway** when working with data sources such as Microsoft SQL Server.

---

# 2. Opening the Report in Power BI Service

The first step is to open the published Power BI report in **Power BI Service**.

### Steps

1. Click the link to open the Power BI report.
2. The report opens in **Power BI Service**.
3. It may take some time for the report to load.

The report being opened is the same report that was previously created in Power BI Desktop and published to the service.

---

# 3. Navigate to the Workspace

Once the report opens:

1. Go to the **Home** tab.
2. Navigate to:

**Workspaces → Test Power BI Project Two**

Inside this workspace, you will find the relevant Power BI items, including the **semantic model** associated with the report.

---

# 4. Open Security Settings

To manage and test the RLS roles:

1. Locate the **semantic model**.
2. Click the **three ellipses (`...`)** next to the semantic model.
3. Select:

**Security**

The Security page displays the roles that were created earlier in Power BI Desktop.

In this example, two roles are visible:

* **Health Role**
* **Travel Role**

---

# 5. Test the Health Role

Suppose we want to verify whether the **Health Role** is working correctly.

### Steps

1. Locate **Health Role**.
2. Click the **three ellipses (`...`)** next to Health Role.
3. Select:

**Test as role**

Power BI may take some time to open the report in the role-testing mode.

Once it loads, you will see a message indicating that you are:

**Viewing as Health Role**

---

# 6. Verify the Health Role

Now inspect the report.

For example, the report contains a **bar chart** displaying different policy categories.

Normally, the chart contains multiple policy types.

However, because we are currently viewing the report as **Health Role**, only Health-related data should be displayed.

### Result

The entire report is filtered according to the RLS condition:

**Policy Type = Health**

Therefore:

* Health data → visible
* Other policy types → filtered out

This confirms that the **Health Role is working correctly**.

---

# 7. Change the Role Being Tested

Power BI Service also allows you to switch between the available roles while testing.

For example, instead of Health Role, we can test the **Travel Role**.

### Steps

1. Use the role-selection option available in the testing interface.
2. Change the selected role from:

**Health Role → Travel Role**

3. Click:

**Apply**

Power BI will reload/apply the report using the Travel Role.

---

# 8. Verify the Travel Role

After applying the Travel Role:

* The entire report becomes filtered according to the Travel role.
* The policy-type visual now shows **Travel** data.
* Data belonging to other policy types is filtered out.

Therefore, the condition is effectively:

**Policy Type = Travel**

This confirms that the Travel RLS role is also working correctly in Power BI Service.

---

# 9. Stop Role Testing / Return to the Report

After testing the roles:

1. Go back to the report.
2. Click **Back**.

This takes you back to the normal report/service interface.

---

# 10. Assigning Users to RLS Roles

Testing the roles is only one part of RLS.

The next important step is to specify **which users should belong to each role**.

For example, suppose the person responsible for Health policies has a particular email address.

We want that person to automatically see only the data allowed by the **Health Role**.

---

# 11. Assign a User to the Health Role

In the Security section:

1. Locate **Health Role**.
2. Select the Health Role.
3. Enter the **email address of the person** who should have access to this role.
4. Click **Save**.

The email address identifies the user who should be associated with the Health Role.

### Example

Conceptually:

**Health Role → [user@example.com](mailto:user@example.com)**

That user will then receive the filtering defined for the Health Role.

---

# 12. Assign a User to the Travel Role

The same process can be followed for the Travel Role.

### Steps

1. Select **Travel Role**.
2. Enter the relevant person's **email address**.
3. Click **Save**.

Conceptually:

**Travel Role → [user@example.com](mailto:user@example.com)**

The person assigned to this role will see only the data permitted by the Travel Role.

---

# 13. How RLS Works for the End User

Once the users have been assigned to their respective roles, the process works as follows:

**User → Logs into Power BI → Power BI identifies the user → User's assigned RLS role is applied → Data is filtered → User sees only relevant data**

For example:

### Health manager

**Health Manager → Health Role → Policy Type = Health**

The user sees Health-related data only.

### Travel manager

**Travel Manager → Travel Role → Policy Type = Travel**

The user sees Travel-related data only.

---

# 14. Why Row-Level Security Is Important

RLS is particularly important when a report contains information that should **not be visible to everyone**.

Organizations may have:

* Sensitive business information
* Department-specific information
* Manager-specific information
* Regional information
* Customer-specific information
* Financial information
* Confidential insights

It may not be appropriate to provide all employees with access to all of this information.

RLS allows the organization to control **which portion of the data each user can see**.

---

# 15. Example of RLS in an Organization

Consider the insurance company example:

| Role        | Filter                 | User sees   |
| ----------- | ---------------------- | ----------- |
| Health Role | `Policy Type = Health` | Health data |
| Travel Role | `Policy Type = Travel` | Travel data |
| Auto Role   | `Policy Type = Auto`   | Auto data   |
| Life Role   | `Policy Type = Life`   | Life data   |
| Home Role   | `Policy Type = Home`   | Home data   |

Each manager can therefore access the insights relevant to their responsibility without necessarily seeing data belonging to other policy categories.

---

# 16. RLS and User Credentials

The lecture emphasizes that the user's **email ID/Power BI identity** is used to associate the user with a particular role.

When the user logs into Power BI using their credentials:

1. Power BI identifies the user.
2. Power BI determines the role associated with that user.
3. The RLS filter associated with that role is applied.
4. The user sees only the relevant data.

So, conceptually:

**User credentials → Assigned role → RLS filter → Filtered report**

---

# 17. Important Distinction: Testing vs Assigning Users

There are two separate activities in Power BI Service.

### Testing

**Test as role**

Used by the report developer/administrator to verify that the role works correctly.

Example:

> Test as Health Role → verify that only Health data appears.

### Assigning users

Used to associate actual users with a role.

Example:

> Health Role → Add user's email address → Save.

Testing ensures that the rule works.

User assignment ensures that the **actual person** receives the appropriate filtering.

---

# 18. Power BI Gateway — Connection With the Earlier Topic

The lecture also revisits an earlier topic: **Power BI Gateway**.

Previously, Microsoft SQL Server was used as a data source.

Since SQL Server in that setup was an external/on-premises data source, a **Power BI Gateway** was configured.

---

# 19. What Is a Power BI Gateway?

A Power BI Gateway acts as a connection/bridge between a data source and Power BI Service.

Conceptually:

**Data Source → Gateway → Power BI Service**

For example:

**Microsoft SQL Server → Power BI Gateway → Power BI Service**

The gateway allows Power BI Service to communicate with the underlying data source and retrieve updated data when required.

---

# 20. Why Was Gateway Required for SQL Server?

In the example from the course:

1. Microsoft SQL Server was used as the data source.
2. The SQL Server environment required a gateway for Power BI Service connectivity.
3. The gateway was therefore:

   * Downloaded
   * Installed
   * Configured

The gateway acts as a **gate/bridge between the data source and the Power BI cloud service**.

This enables Power BI Service to obtain updated data and consequently provide updated reports/dashboards.

---

# 21. Gateway Is Not Required for Every Data Source

An important point from the lecture is:

> **A gateway is not required for every data source.**

Whether a gateway is required depends on the type/location/configuration of the data source and how Power BI Service connects to it.

In the course example, the gateway was specifically used for **Microsoft SQL Server**.

---

# 22. Gateway and Data Refresh

The gateway is particularly relevant when Power BI Service needs to access data from a source that it cannot directly reach from the cloud.

The overall concept is:

**SQL Server → Gateway → Power BI Service → Updated Report/Dashboard**

The gateway facilitates communication so that Power BI Service can retrieve the latest available data from the source.

This is related to the earlier discussion about **scheduled refresh**.

---

# 23. Complete RLS Workflow

The complete process covered across the two RLS sessions can be summarized as:

### Power BI Desktop

**Modeling → Manage Roles**

↓

Create roles:

* Health Role
* Travel Role

↓

Define filters:

* Health Role → `Policy Type = Health`
* Travel Role → `Policy Type = Travel`

↓

**Save**

↓

**View as**

↓

Test each role

↓

**Stop viewing**

↓

### Publish

**Home → Publish → Select Workspace → Replace existing report if required**

↓

### Power BI Service

**Workspace → Semantic Model → `...` → Security**

↓

View available roles

↓

**Test as role**

↓

Verify filtered data

↓

Assign users using their **email addresses**

↓

**Save**

↓

Users log into Power BI

↓

Power BI applies their assigned RLS role

↓

Users see only the relevant data.

---

# 24. Key Points for Interviews/Exams

### What is RLS?

**Row-Level Security is a Power BI security feature that restricts the rows of data visible to users based on roles and filtering rules.**

### Where are RLS roles created?

**Power BI Desktop → Modeling → Manage Roles**

### How do you test an RLS role in Desktop?

Use:

**View as**

### How do you test an RLS role in Power BI Service?

Go to:

**Workspace → Semantic Model → `...` → Security → `...` next to role → Test as role**

### How do you assign a user to an RLS role?

Select the role, provide the user's **email address**, and save.

### What happens when the user logs in?

Power BI identifies the user and applies the RLS role assigned to that user, so the user sees only the relevant filtered data.

### Is a gateway required for every data source?

**No.** Gateway requirements depend on the data source and connectivity setup.

### Why was a gateway used for SQL Server in this course?

It acts as a bridge between the SQL Server data source and Power BI Service, allowing Power BI Service to access updated data.

---

# 25. Quick Revision

**RLS = Restrict data based on user/role**

**Desktop:**

`Modeling → Manage Roles → Create Role → Add Filter → Save → View as → Test`

**Service:**

`Workspace → Semantic Model → Security → Test as role`

**User assignment:**

`Select Role → Enter Email Address → Save`

**User experience:**

`Login → Role Identified → RLS Applied → Relevant Data Only`

**Gateway:**

`Data Source → Gateway → Power BI Service`

And remember: **RLS controls what data a user can see, while the gateway facilitates connectivity between Power BI Service and certain data sources.**
