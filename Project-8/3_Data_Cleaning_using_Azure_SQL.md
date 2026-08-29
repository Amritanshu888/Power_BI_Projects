# Data Cleaning Using SQL and Azure — Detailed Notes

## 1. Objective of the Session

This session focuses on **cleaning data using SQL in Azure**.

The specific problem being addressed is the presence of **question marks (`?`)** in two columns:

1. **Original Price**
2. **Sales Price**

The objective is to remove/replace these question marks with blank values so that the data becomes cleaner before it is eventually connected to **Power BI**.

---

# 2. Problem in the Data

The instructor begins with the existing Azure SQL table and observes that both price columns contain question marks.

```text
Original Price     → contains ?
Sales Price        → contains ?
```

The goal is:

```text
Question mark (?) → Blank
```

The instructor plans to use an **UPDATE statement** along with:

* `REPLACE()`
* `TRIM()`
* `CAST()`

The same cleaning operation is then performed separately for both columns.

---

# 3. SQL Functions Used

Three SQL functions/operators are involved in the cleaning process.

### `UPDATE`

Used to modify existing records in the table.

General structure:

```sql
UPDATE table_name
SET column_name = ...
WHERE condition;
```

---

### `REPLACE()`

Used to replace a particular value/string with another value.

In this case:

```text
? → blank
```

Conceptually:

```sql
REPLACE(column_name, '?', '')
```

---

### `TRIM()`

Used to remove unwanted spaces from the resulting value.

The instructor wants to **replace the question mark first and then trim the resulting value**.

Conceptually:

```sql
TRIM(REPLACE(...))
```

---

### `CAST()`

The price columns were previously stored as **text**, so the instructor casts the column to `VARCHAR(MAX)` before applying the replacement operation.

Conceptually:

```sql
CAST(original_price AS VARCHAR(MAX))
```

---

# 4. Cleaning the Original Price Column

The first column being cleaned is:

**Original Price**

The instructor constructs an `UPDATE` statement.

The basic logic is:

```text
UPDATE table
       ↓
SET Original Price =
       ↓
TRIM(
       ↓
REPLACE(
       ↓
CAST(Original Price AS VARCHAR(MAX)),
       ↓
'?',
       ↓
''
)
)
WHERE Original Price contains '?'
```

The important sequence is:

**CAST → REPLACE → TRIM**

---

# 5. Step-by-Step SQL Logic for Original Price

### Step 1 — Update the Table

Start with:

```sql
UPDATE table_name
```

where `table_name` is the actual table containing the men's T-shirt data.

---

### Step 2 — Specify the Column

The instructor selects the **Original Price** column.

Conceptually:

```sql
SET OriginalPrice = ...
```

---

### Step 3 — Cast the Column

Because the column has a text data type, the instructor uses:

```sql
CAST(OriginalPrice AS VARCHAR(MAX))
```

This converts the value to `VARCHAR(MAX)` for the replacement operation.

---

### Step 4 — Replace the Question Mark

The `REPLACE()` function is then applied.

The logic is:

```sql
REPLACE(
    CAST(OriginalPrice AS VARCHAR(MAX)),
    '?',
    ''
)
```

Here:

* First argument = Original Price
* Second argument = value to search for (`?`)
* Third argument = replacement value (blank)

So:

```text
? → ''
```

---

### Step 5 — Trim the Result

The instructor then applies `TRIM()` around the replacement operation:

```sql
TRIM(
    REPLACE(
        CAST(OriginalPrice AS VARCHAR(MAX)),
        '?',
        ''
    )
)
```

This cleans up any unnecessary surrounding spaces.

---

### Step 6 — Specify the WHERE Condition

The instructor specifies that the update should apply where the **Original Price** contains the question mark.

Conceptually:

```sql
WHERE OriginalPrice = '?'
```

The transcript describes this as applying the update to the rows where the Original Price column has the question mark.

---

# 6. Execute the Original Price Update

After creating the UPDATE statement:

1. Select the UPDATE statement.
2. Click **Run/Execute**.
3. Wait for the query to complete.

The instructor receives:

**1294 records impacted**

This means the update affected 1,294 records according to the execution result. 

---

# 7. Verify the Original Price Column

After updating the data, the instructor verifies the result using a SELECT query.

The instructor runs a:

```sql
SELECT TOP 1000 ...
```

query against the table.

### Steps

1. Select the SELECT statement.
2. Execute/run it.
3. Inspect the results.
4. Check the **Original Price** column.

The instructor observes that the question mark is no longer visible in the **Original Price** column.

Therefore, the replacement was successful.

---

# 8. Clean the Sales Price Column

After successfully cleaning **Original Price**, the instructor performs the same operation on:

**Sales Price**

Rather than writing the entire statement from scratch, the instructor **copies the existing UPDATE code** and modifies the column references.

This is an important practical shortcut demonstrated in the lecture.

---

# 9. Modify the Query for Sales Price

The existing query for Original Price is copied.

Then the instructor replaces the references to **Original Price** with **Sales Price**.

This needs to be done in the relevant places in the query.

Conceptually:

```text
Original Price
      ↓
Sales Price
```

The replacement operation therefore becomes:

```sql
TRIM(
    REPLACE(
        CAST(SalesPrice AS VARCHAR(MAX)),
        '?',
        ''
    )
)
```

And the `WHERE` condition is also changed to refer to the **Sales Price** column.

---

# 10. Execute the Sales Price Update

Once the modified UPDATE statement is ready:

1. Select the UPDATE statement.
2. Execute it.
3. Wait for the query to finish.

The instructor receives:

**1428 records impacted**

So the update affected 1,428 records for the Sales Price column.

---

# 11. Verify Both Price Columns

The instructor then runs the SELECT statement again.

### Steps

1. Select the previously written SELECT statement.
2. Execute/run it.
3. Inspect the resulting data.
4. Check both:

   * Original Price
   * Sales Price

The instructor confirms that the data is now cleaner in both columns.

### Result

```text
Original Price → question marks removed
Sales Price    → question marks removed
```

Thus, the data-cleaning operation has been successfully completed for both price columns.

---

# 12. Complete SQL Cleaning Logic

The important logic demonstrated in the lecture can be summarized as:

### Original Price

```sql
UPDATE table_name
SET OriginalPrice =
    TRIM(
        REPLACE(
            CAST(OriginalPrice AS VARCHAR(MAX)),
            '?',
            ''
        )
    )
WHERE OriginalPrice = '?';
```

### Sales Price

The same logic is applied to the Sales Price column:

```sql
UPDATE table_name
SET SalesPrice =
    TRIM(
        REPLACE(
            CAST(SalesPrice AS VARCHAR(MAX)),
            '?',
            ''
        )
    )
WHERE SalesPrice = '?';
```

> **Note:** The transcript does not provide the exact table name or exact spelling of the column identifiers in the final SQL statement, so the above uses descriptive placeholders. The important thing to retain from the lecture is the demonstrated sequence: `UPDATE` → `CAST` → `REPLACE` → `TRIM` → `WHERE`.

---

# 13. What Each Part of the Query Does

| SQL component               | Purpose                                   |
| --------------------------- | ----------------------------------------- |
| `UPDATE`                    | Modifies existing records                 |
| `SET`                       | Specifies the column/value to modify      |
| `CAST(... AS VARCHAR(MAX))` | Treats the text value as `VARCHAR(MAX)`   |
| `REPLACE()`                 | Replaces `?` with a blank value           |
| `TRIM()`                    | Removes unnecessary surrounding spaces    |
| `WHERE`                     | Limits the update to the relevant records |
| `SELECT TOP 1000`           | Used to inspect/verify the cleaned data   |

---

# 14. Data Cleaning Workflow

The practical workflow used in the lecture is:

```text
Existing Azure SQL Data
          ↓
Identify problem
          ↓
? present in Original Price
? present in Sales Price
          ↓
Create UPDATE statement
          ↓
CAST column AS VARCHAR(MAX)
          ↓
REPLACE ? with blank
          ↓
TRIM the result
          ↓
Apply WHERE condition
          ↓
Execute UPDATE
          ↓
Check number of records impacted
          ↓
Run SELECT TOP 1000
          ↓
Verify Original Price
          ↓
Repeat for Sales Price
          ↓
Run SELECT again
          ↓
Verify both columns
          ↓
Clean data available
```

---

# 15. Record Counts From the Demonstration

The lecture provides two important execution results:

| Column cleaned | Records impacted |
| -------------- | ---------------: |
| Original Price |        **1,294** |
| Sales Price    |        **1,428** |

These numbers represent the records affected by the respective UPDATE statements in the instructor's demonstration.

---

# 16. Important Practical Steps to Remember

### For the first column

1. Identify the problematic column.
2. Write an `UPDATE` statement.
3. Set the column equal to the cleaned value.
4. `CAST` the column as `VARCHAR(MAX)`.
5. Use `REPLACE()` to replace `?` with blank.
6. Apply `TRIM()`.
7. Add the appropriate `WHERE` condition.
8. Execute the query.
9. Check the number of affected records.
10. Run a SELECT query to verify the result.

### For the second column

1. Copy the first UPDATE statement.
2. Replace the **Original Price** references with **Sales Price**.
3. Execute the new UPDATE statement.
4. Check the number of affected records.
5. Run the SELECT query again.
6. Verify that both columns are clean.

---

# 17. Key Learning: Reusing SQL Code

An important practical technique demonstrated here is **reusing an existing SQL query**.

Instead of creating a completely new query for Sales Price:

```text
Original Price UPDATE query
            ↓
          Copy
            ↓
Replace Original Price
            ↓
With Sales Price
            ↓
Execute
```

This saves time and reduces the chance of rewriting the entire query incorrectly.

---

# 18. Why Data Cleaning Is Being Done Before Power BI

The instructor is preparing the data before establishing the connection with **Power BI**.

The sequence is:

```text
Azure SQL Database
       ↓
Data Cleaning using SQL
       ↓
Clean Data
       ↓
Connect to Power BI
       ↓
Create Power BI Report
```

The purpose is to make sure that the data being brought into Power BI is cleaner and more usable.

---

# 19. Final Outcome of This Session

At the end of the session:

* The **Original Price** column has been cleaned.
* The **Sales Price** column has been cleaned.
* The question marks have been removed/replaced with blank values.
* The instructor verifies the cleaned data using a SELECT query.
* The data is now ready for the next stage of the project.

The instructor concludes by saying that the **next session will discuss establishing the connection with Power BI**.

So the next major step is:

**Azure SQL Database → Power BI connection**.
