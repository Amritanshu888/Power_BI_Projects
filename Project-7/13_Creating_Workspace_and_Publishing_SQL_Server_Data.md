# Power BI: Creating Separate Workspaces Before SQL Server → MySQL Migration

## 1. Objective of the Session

Before transitioning the Power BI report from **SQL Server** to **MySQL**, we need to protect the existing working version of the report.

The current report uses:

```text
SQL Server → Power BI Report
```

We are going to create **two separate Power BI Service workspaces**:

1. A workspace for the **SQL Server version**
2. A workspace for the **MySQL version**

This provides a safe way to perform the migration without losing the original working report.

---

# 2. Why Create Separate Workspaces?

The existing SQL Server-based report is already working.

When we migrate the report to MySQL, there is a possibility that:

* Data source changes may cause errors.
* DAX calculations could be affected.
* Relationships could behave differently.
* Data refresh may fail.
* Table/column mismatches may occur.
* Additional modifications may be required.

Therefore, we should **not overwrite the existing SQL Server version**.

Instead, maintain a separate copy.

### Safe migration approach

```text
                 Existing Report
                       │
             ┌─────────┴─────────┐
             ↓                   ↓
      SQL Server Version     MySQL Version
             │                   │
             ↓                   ↓
    SQL Server Workspace    MySQL Workspace
```

The SQL Server version acts as a **backup/reference version**.

---

# 3. Power BI Account Requirement

The instructor has already logged into a Power BI account.

If you do not have a Power BI account, the course introduction contains a separate video explaining how to create a **free Power BI account**.

So, before performing these steps, make sure you can access **Power BI Service**.

---

# 4. Create the SQL Server Workspace

The first workspace will contain the report that uses **SQL Server as its data source**.

### Steps

1. Log in to **Power BI Service**.
2. Go to **Workspaces**.
3. Click **New Workspace**.
4. Enter the workspace name:

```text
SQL Server Data Source
```

5. Click **Apply**.

The workspace is now created.

---

# 5. Create the MySQL Workspace

Next, create another workspace specifically for the report that will eventually use MySQL.

### Steps

1. Go to **Workspaces** again.
2. Click **New Workspace**.
3. Enter:

```text
MySQL Database Data Source
```

4. Click **Apply**.
5. Wait for the workspace to be created.

Now there are two separate workspaces.

---

# 6. Verify Both Workspaces

Click **Workspaces** again.

You should now see:

```text
Workspaces
│
├── SQL Server Data Source
│
└── MySQL Database Data Source
```

### Purpose of each workspace

| Workspace                      | Purpose                                           |
| ------------------------------ | ------------------------------------------------- |
| **SQL Server Data Source**     | Store the existing report connected to SQL Server |
| **MySQL Database Data Source** | Store the migrated report connected to MySQL      |

---

# 7. Return to the Power BI Home Page

After creating the workspaces:

1. Click **Home**.
2. Open the existing Power BI report.

This is the report that was created using **SQL Server as the data source**.

---

# 8. Publish the Existing SQL Server Report

The first thing we want to do is publish the existing SQL Server-based report to the **SQL Server Data Source** workspace.

This creates a copy of the report in Power BI Service.

### Why publish it first?

Because if something goes wrong during the migration, we still have the original SQL Server version available.

Think of it as creating a backup before making a major change.

---

# 9. Publish the Report

With the SQL Server-based report open in **Power BI Desktop**:

1. Go to the **Home** tab.
2. Click **Publish**.

Power BI will ask you where you want to publish the report.

---

# 10. Select the SQL Server Workspace

From the list of available workspaces, select:

```text
SQL Server Data Source
```

Then click:

**Select**

Power BI will publish the report to that workspace.

---

# 11. Local PBIX File

The lecture also points out that the `.pbix` file can be retained locally.

For example, the report file is referred to as:

```text
prod Power BI Report.pbix
```

The important idea is that you should retain the local Power BI file as well.

Therefore, you effectively have:

```text
Local Machine
    ↓
Power BI .PBIX file

Power BI Service
    ↓
SQL Server Data Source workspace
```

This gives you an additional backup/reference point.

---

# 12. Recommended Backup Structure

Before beginning the migration, you can think of the setup as:

```text
LOCAL
│
└── prod Power BI Report.pbix
        │
        │ SQL Server data source
        ↓
POWER BI SERVICE
│
└── SQL Server Data Source
        │
        └── Published SQL Server Report
```

Later, the MySQL version will be maintained separately.

---

# 13. Why This Is Important in Real Projects

Changing a report's data source is an important operation.

Suppose you directly modify the only copy of your report:

```text
SQL Server Report
       ↓
Change to MySQL
       ↓
❌ Error
```

You could potentially have difficulty returning to the previous working state.

Instead:

```text
Original SQL Server Report
       ↓
       ├──────────────→ SQL Server Workspace
       │                 (Safe/Reference Copy)
       │
       └──────────────→ MySQL Migration
                         ↓
                     Testing
```

This is a much safer approach.

---

# 14. Migration Strategy

The overall migration process is therefore:

### Phase 1 — Protect the existing report

```text
SQL Server Report
       ↓
Publish to SQL Server Data Source Workspace
```

### Phase 2 — Prepare MySQL

Already covered in previous sessions:

```text
Create MySQL prod database
        ↓
Import inventory data
        ↓
Clean/transform data
        ↓
Import Products table
        ↓
Create New_Table
```

### Phase 3 — Migrate Power BI

Next, the report will be connected to MySQL instead of SQL Server.

```text
SQL Server
    ↓
Power BI Report
```

becomes:

```text
MySQL
   ↓
Power BI Report
```

### Phase 4 — Test

The MySQL version will be checked to ensure:

* Data loads correctly
* DAX measures work
* Visuals work
* Numbers are correct
* Refresh works
* No broken references exist

---

# 15. Two-Workspace Architecture

The final intended structure is:

```text
                 POWER BI SERVICE
                       │
              ┌────────┴────────┐
              │                 │
              ↓                 ↓
    SQL Server Data       MySQL Database
       Source                 Data Source
       Workspace              Workspace
          │                      │
          ↓                      ↓
   SQL Server Report       MySQL Report
          │                      │
          ↓                      ↓
   SQL Server DB             MySQL DB
```

This provides a clean separation between the two versions.

---

# 16. Important Distinction: Workspace vs Data Source

A **workspace** is not the database itself.

For example:

```text
SQL Server Data Source
```

is simply the name of a Power BI workspace.

The actual data source is:

```text
Microsoft SQL Server
```

Similarly:

```text
MySQL Database Data Source
```

is a Power BI workspace, while the actual data source is:

```text
MySQL
```

So:

| Item                                 | Meaning                                             |
| ------------------------------------ | --------------------------------------------------- |
| SQL Server Data Source workspace     | Power BI Service location for the SQL Server report |
| MySQL Database Data Source workspace | Power BI Service location for the MySQL report      |
| SQL Server                           | Actual database/data source                         |
| MySQL                                | Actual database/data source                         |

---

# 17. Key Takeaways

### 1. Always protect the working report before migration

Create a backup/reference copy before changing the data source.

### 2. Use separate workspaces

For this project:

```text
SQL Server Data Source
MySQL Database Data Source
```

### 3. Publish the existing SQL Server report first

Use:

**Power BI Desktop → Home → Publish → SQL Server Data Source → Select**

### 4. Keep the `.PBIX` file

The local Power BI `.pbix` file should also be retained as another reference/backup.

### 5. Don't overwrite the SQL Server version

The SQL Server version should remain available in case the MySQL migration encounters problems.

---

# 18. Quick Revision

```text
1. Log in to Power BI Service
          ↓
2. Workspaces → New Workspace
          ↓
3. Create "SQL Server Data Source"
          ↓
4. Create "MySQL Database Data Source"
          ↓
5. Open existing SQL Server Power BI report
          ↓
6. Home → Publish
          ↓
7. Select "SQL Server Data Source"
          ↓
8. Publish the report
          ↓
9. Keep the local .PBIX file
          ↓
10. Proceed with SQL Server → MySQL migration
```

## Final Concept

> **Before migrating a Power BI report from one data source to another, create a safe copy of the existing working report in a separate workspace. In this project, the SQL Server version is preserved in the `SQL Server Data Source` workspace, while the migrated MySQL version will be handled separately in the `MySQL Database Data Source` workspace.**
