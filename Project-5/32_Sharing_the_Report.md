# Power BI Service — Sharing Reports with Other Users

## 1. Objective of the Session

This session explains how to **share Power BI reports with colleagues or other team members** through Power BI Service.

The main topics covered are:

* How to access the **Share** option.
* How to share a report with people in your organization.
* Power BI license requirements for sharing/viewing.
* Organization/domain restrictions when entering email addresses.
* How the recipient receives access to the report.

---

# 2. Sharing a Report in Power BI Service

Once a report has been published to **Power BI Service**, you can share it with other users.

### Steps

1. Open the relevant **Power BI workspace**.
2. Locate the report you want to share.
3. Hover your mouse over the area near the report.
4. You will see a small **Share** icon.
5. Click the **Share** option.

This opens the report-sharing interface.

---

# 3. Select the Sharing Option

Power BI provides an option similar to:

> **People in your organization with a link can view and share**

The instructor selects this option.

This is intended for sharing the report with people within the same organization.

---

# 4. Enter the Recipient's Email Address

After selecting the appropriate sharing option:

1. Enter the **email address** of the person with whom you want to share the report.
2. Power BI checks the email address/domain.
3. If the user satisfies the necessary requirements, you can proceed with sharing.
4. Click **Send** to share the report.

The recipient will receive an email containing access information/link to the report.

---

# 5. Power BI License Requirement

An important point highlighted in the lecture is that simply receiving a report link does not necessarily mean that someone can access the report.

The users need the **appropriate Power BI licensing/access configuration**.

According to the lecture, when accessing reports online:

* The person **sharing** the report needs the appropriate Power BI license.
* The person **viewing** the report also needs the appropriate Power BI license.

So conceptually:

```text
Person A
(Sharing Report)
       │
       │ Appropriate Power BI License
       ↓
Power BI Report
       ↑
       │ Appropriate Power BI License
       │
Person B
(Viewing Report)
```

> **Important:** Exact licensing requirements can depend on the organization's Power BI/Fabric capacity and license setup, so in real-world environments the workspace capacity and user licenses also need to be considered.

---

# 6. Organization Email Domain

The lecture demonstrates an important restriction when sharing with users within an organization.

Suppose a company uses the domain:

```text
@inscib.com
```

For example:

```text
giant@inscib.com
```

If the colleague you want to share the report with also has an email address using the same organizational domain:

```text
colleague@inscib.com
```

then Power BI can recognize that the person belongs to the same organization.

---

# 7. What Happens with an External Email Address?

The instructor enters a **personal email address** instead of an organizational email address.

Power BI then displays an error indicating that:

> One or more email addresses are outside your organization.

### Why does this happen?

The personal email address has a different domain from the organization's domain.

For example:

```text
Your organization:
employee@company.com

Personal email:
someone@gmail.com
```

The domains are different:

```text
company.com ≠ gmail.com
```

Therefore, Power BI identifies the recipient as being **outside the organization**.

---

# 8. Same Domain vs Different Domain

### Same organizational domain

Example:

```text
User 1 → employee1@company.com
User 2 → employee2@company.com
```

Both use:

```text
@company.com
```

Power BI can recognize them as users belonging to the same organization, subject to the organization's sharing policies and access configuration.

---

### Different/external domain

Example:

```text
User 1 → employee@company.com
User 2 → person@gmail.com
```

The second email address is outside the organization's domain.

Power BI therefore displays a warning/error about the email address being outside the organization.

---

# 9. Recipient Access

Once you enter an eligible user's email address and successfully share the report:

1. The recipient receives an **email notification**.
2. The email contains a **link to the Power BI report**.
3. The recipient can click the link.
4. They can access the report provided they have the required license/access permissions.

Conceptually:

```text
Report Owner
     │
     │ Share
     ↓
Recipient Email
     │
     ↓
Email Notification
     │
     ↓
Report Link
     │
     ↓
Recipient Signs In
     │
     ↓
Power BI License + Permissions Checked
     │
     ↓
Report Accessible
```

---

# 10. Complete Procedure

### To share a Power BI report:

```text
Power BI Service
      ↓
Open Workspace
      ↓
Locate Report
      ↓
Hover over Report
      ↓
Click Share
      ↓
Select:
"People in your organization with a link
can view and share"
      ↓
Enter Email Address
      ↓
Power BI Checks Recipient
      ↓
Verify License/Access
      ↓
Click Send
      ↓
Recipient Gets Email
      ↓
Recipient Uses Report Link
      ↓
Report Can Be Viewed
```

---

# 11. Important Error to Remember

### Error/Warning

If you enter an email address belonging to an external domain, Power BI can show a message indicating that:

```text
One or more email addresses are outside your organization.
```

### Example

```text
Organization:
employee@company.com

External:
employee@gmail.com
```

Power BI recognizes `gmail.com` as outside the organization's domain.

---

# 12. Important Interview Points

### Q1. How do you share a Power BI report?

**Answer:**

Open the report in Power BI Service → hover over the report → click **Share** → select the appropriate sharing option → enter the recipient's email address → send the report link.

---

### Q2. Can you share a report with anyone using any email address?

Not necessarily.

The ability to share with external users depends on the organization's **sharing policies, permissions, licensing, and tenant configuration**.

The lecture demonstrates that selecting the organizational sharing option and entering an external/personal email can result in an error.

---

### Q3. What happens after sharing a report?

The recipient receives an **email containing a link** to the report and can access it if they have the necessary Power BI license and permissions.

---

### Q4. Why did the personal email address produce an error?

Because the selected sharing option is for **people within the organization**, while the personal email address belongs to an external domain.

---

# 13. Quick Revision

| Topic            | Key Point                                              |
| ---------------- | ------------------------------------------------------ |
| Share report     | Use the **Share** icon near the report                 |
| Sharing option   | People in your organization can view/share             |
| Recipient        | Enter their email address                              |
| License          | Appropriate licensing/access is required               |
| Same domain      | Recognized as organizational user, subject to policies |
| External domain  | May trigger an outside-organization warning            |
| Notification     | Recipient receives an email                            |
| Access           | Recipient uses the provided report link                |
| External sharing | Depends on organization's policies/configuration       |

### Core takeaway

> **Power BI Service allows you to share published reports with other users. You select the Share option, provide the recipient's email address, and send the report link. The recipient must have the appropriate access/licensing, and organizational sharing policies determine whether internal or external users can access the report.**
