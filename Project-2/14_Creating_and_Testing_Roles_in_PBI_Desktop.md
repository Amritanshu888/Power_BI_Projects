# Row-Level Security (RLS) in Power BI — Detailed Notes

## 1. What is Row-Level Security?

**Row-Level Security (RLS)** is a Power BI feature used to restrict the data that different users can see based on predefined rules.

### Example business scenario

Suppose you are working for an **insurance company** and there are different managers responsible for different policy types:

| Manager   | Policy Type They Handle |
| --------- | ----------------------- |
| Manager 1 | Travel                  |
| Manager 2 | Health                  |
| Manager 3 | Auto                    |
| Manager 4 | Life                    |
| Manager 5 | Home                    |

The requirement is:

> Each manager should see only the insights/data relevant to their policy type.

For example:

* Travel manager → should see only **Travel** data.
* Health manager → should see only **Health** data.
* Auto manager → should see only **Auto** data.
* Life manager → should see only **Life** data.
* Home manager → should see only **Home** data.

This requirement can be implemented using **Row-Level Security (RLS)**.

---

# 2. RLS Implementation Process

RLS can be implemented in **two major stages**:

### Step 1 — Create roles in Power BI Desktop

In Power BI Desktop, you:

1. Create the required roles.
2. Define filtering conditions for each role.
3. Test the roles using **View as**.

### Step 2 — Validate roles in Power BI Service

After publishing the report to Power BI Service:

1. The roles created in Power BI Desktop are available in the service.
2. You can validate/configure them there.
3. This allows you to ensure that users receive only the data they are supposed to see.

> **Important:** The lecture focuses on creating and testing the roles in Power BI Desktop. Validation in Power BI Service is discussed in the next session.

---

# 3. Example: Creating RLS Roles

For demonstration, two roles are created:

1. **Travel Role**
2. **Health Role**

The goal is:

* Travel Role → display only records where `Policy Type = Travel`
* Health Role → display only records where `Policy Type = Health`

---

# 4. Create the Travel Role

### Step 1: Open Manage Roles

In **Power BI Desktop**:

1. Go to the **Modeling** tab.
2. Click **Manage Roles**.

This opens the role management window.

---

### Step 2: Create a new role

Inside the Manage Roles window:

1. Click **New**.
2. A role named **Untitled** will appear.
3. Double-click the role name.
4. Rename it to:

**Travel Role**

---

### Step 3: Select the table

Under **Select tables**:

1. Select the table containing the insurance data.
2. In the lecture, this table is referred to as the **Insurance Data** table.

---

### Step 4: Create the filter

Under **Filter data**:

1. Click **New**.
2. Select the required column.
3. Select the **Policy Type** column.
4. Set the condition so that:

`Policy Type = Travel`

In other words, the role should filter the insurance data to only those rows where the policy type is **Travel**.

---

### Step 5: Save the role

After configuring the filter:

1. Check/enable the filter condition.
2. Click **Save**.

Power BI displays a message indicating that the **role changes were successfully applied**.

The Travel Role is now created.

---

# 5. Create the Health Role

Now create another role for Health policies.

### Step 1: Create another role

In the **Manage Roles** window:

1. Click **New**.
2. Select the **Untitled** role.
3. Rename it to:

**Health Role**

---

### Step 2: Select the table

Select the **Insurance Data** table.

---

### Step 3: Create the filter

Under **Filter data**:

1. Click **New**.
2. Select the **Policy Type** column.
3. Set the value/condition to:

`Policy Type = Health`

This means the Health Role will only be able to see rows where the policy type is **Health**.

---

### Step 4: Save

Click **Save**.

Power BI again displays the message indicating that the **role changes were successfully applied**.

Now two roles have been created:

* **Travel Role**
* **Health Role**

---

# 6. Close Manage Roles

Once both roles have been created:

1. Click **Close**.

You can now test whether the roles are working correctly.

---

# 7. Testing RLS in Power BI Desktop

Power BI provides the **View as** functionality to test the roles that you have created.

This is important because before publishing the report, you should verify that the RLS filters are actually working.

---

## 8. Test the Travel Role

### Step 1: Open View as

In Power BI Desktop:

1. Go to the relevant security/modeling area.
2. Click **View as**.

You will see the roles that have been created.

---

### Step 2: Select Travel Role

Select:

**Travel Role**

Then click **OK**.

Power BI will now display the report as though the current user belongs to the **Travel Role**.

---

### Step 3: Verify the report

Look at the visuals in the report.

For example, the lecture has a bar chart showing:

**Premium Amount by Policy Type**

After applying the Travel Role:

* Only **Travel** data is displayed.
* Other policy types are filtered out.

This confirms that the Travel Role is working correctly.

---

# 9. Stop Viewing the Role

After testing:

1. Click **Stop viewing**.

This removes the simulated role and returns the report to its normal view.

---

# 10. Test the Health Role

Now test the second role.

### Step 1

Click:

**View as**

### Step 2

Select:

**Health Role**

### Step 3

Click:

**OK**

The report will now be displayed as though the user belongs to the Health Role.

---

### Step 4: Verify the results

All the insights/visuals on the report page should now be filtered according to:

`Policy Type = Health`

For example, the policy-type visual should display only **Health** data.

This confirms that the Health Role is also working correctly.

---

### Step 5

After testing:

**Click → Stop viewing**

---

# 11. RLS Flow in Power BI Desktop

The complete Desktop process can be remembered as:

**Modeling → Manage Roles → New Role → Select Table → Filter Data → Save → Close → View as → Select Role → OK → Verify → Stop viewing**

---

# 12. Publishing the RLS Report to Power BI Service

After creating and testing the roles, the report needs to be published to **Power BI Service**.

### Step 1: Go to Home

Click the:

**Home** tab.

### Step 2: Publish

Click:

**Publish**

Power BI may ask:

> Do you want to save changes?

Select:

**Yes**

Then save the report.

---

### Step 3: Select the workspace

Power BI asks you where you want to publish the report.

In the lecture, the selected workspace is:

**Test Power BI Project Two**

Select the workspace.

Power BI then publishes the report to the selected workspace.

---

# 13. Handling an Existing Report

If a report with the **same name already exists** in the workspace, Power BI displays a confirmation asking whether you want to replace it.

Since changes were made to the report, select:

**Replace**

Power BI will replace the existing report with the updated version containing the newly created RLS roles.

---

# 14. Successful Publication

After the publishing process completes, the updated report is available in Power BI Service.

The next step is to validate the roles in **Power BI Service**.

> The lecture ends here. The actual validation/configuration of these roles in Power BI Service is covered in the next session.

---

# 15. Important Concepts to Remember

### Row-Level Security

RLS restricts the **rows of data** that a user can access based on a role/filter.

### Role

A role defines **which subset of data a particular user/group should be able to see**.

Example:

`Travel Role → Policy Type = Travel`

`Health Role → Policy Type = Health`

### Manage Roles

Used in **Power BI Desktop** to:

* Create roles
* Define filtering conditions
* Modify roles
* Manage RLS rules

### View as

Used to **test RLS roles in Power BI Desktop**.

It allows you to simulate what the report looks like for a particular role.

### Publish

After testing the roles, publish the report to **Power BI Service**, where the roles can subsequently be validated and assigned/configured.

---

# 16. Complete Example

Suppose the Insurance Data table contains:

| Customer | Policy Type | Premium |
| -------- | ----------- | ------: |
| C001     | Travel      |     500 |
| C002     | Health      |     800 |
| C003     | Auto        |     600 |
| C004     | Travel      |     700 |
| C005     | Health      |     900 |

If we create:

**Travel Role**

`Policy Type = Travel`

The Travel Role will see:

| Customer | Policy Type | Premium |
| -------- | ----------- | ------: |
| C001     | Travel      |     500 |
| C004     | Travel      |     700 |

If we create:

**Health Role**

`Policy Type = Health`

The Health Role will see:

| Customer | Policy Type | Premium |
| -------- | ----------- | ------: |
| C002     | Health      |     800 |
| C005     | Health      |     900 |

The Auto records will not be visible to either of these roles.

---

# 17. Key Takeaways

* **RLS = Row-Level Security.**
* It is used when different users need access to **different subsets of data**.
* In this example, different insurance managers are responsible for different policy types.
* RLS ensures that each manager sees only the data relevant to their responsibility.
* Roles are created in **Power BI Desktop → Modeling → Manage Roles**.
* Each role gets a filtering condition.
* Example:

  * Travel Role → `Policy Type = Travel`
  * Health Role → `Policy Type = Health`
* Roles can be tested in Power BI Desktop using **View as**.
* **Stop viewing** returns the report to its normal state.
* After testing, the report can be published to **Power BI Service**.
* If an existing report with the same name is present, choose **Replace** to publish the updated report.
* The next step is to **validate/configure the roles in Power BI Service**.
