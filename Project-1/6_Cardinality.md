# Power BI Data Modeling — Foreign Key Constraints & Cardinality

This lecture continues the discussion of **Primary Key and Foreign Key** and introduces an important concept used while creating relationships between tables in Power BI: **Cardinality**.

---

# 1. Recap: Primary Key and Foreign Key

In the previous lecture, we had two tables:

* **Table 1**
* **Table 2**

They were connected through the `ID` column.

### Table 1

The `ID` column was the **Primary Key**.

Example values:

```text
1
2
3
4
```

### Table 2

The `ID` column was the **Foreign Key**.

Example values:

```text
1
2
3
```

Therefore:

```text
Table 1.ID  → Primary Key
Table 2.ID  → Foreign Key
```

The two tables are related using these columns.

---

# 2. Important Foreign Key Rule — Subset Rule

One important point to remember is:

> **The values contained in the foreign key should be a subset of the values contained in the primary key.**

Suppose the primary key contains:

```text
Primary Key:
1
2
3
4
```

Then the foreign key can contain:

```text
1
2
3
```

It can also contain:

```text
1
2
3
4
```

because `4` exists in the primary key.

It can even contain duplicate values:

```text
1
1
2
2
3
4
```

because foreign keys are allowed to contain duplicates.

---

## 3. What Cannot Be Added to the Foreign Key?

Suppose the primary key contains:

```text
1
2
3
4
```

You **cannot** add:

```text
5
```

to the foreign key because `5` does not exist in the primary-key column.

Similarly, you cannot add:

```text
7
```

because `7` doesn't exist in the primary key.

### Correct

```text
Primary Key: 1 2 3 4

Foreign Key: 1 2 3 4
```

### Incorrect

```text
Primary Key: 1 2 3 4

Foreign Key: 1 2 3 5
                         ↑
                    Invalid
```

because `5` does not exist in the primary key.

---

# 4. Why Is This Important?

This rule ensures that the relationship between the two tables makes sense.

For example:

```text
Student Table
ID
1
2
3
4
```

If a marks table contains:

```text
Student ID
1
2
3
5
```

there is no student with `ID = 5` in the Student table.

Therefore, the relationship cannot properly identify which student the record belongs to.

---

# 5. Introduction to Cardinality

The next important concept is **Cardinality**.

### Definition

Cardinality describes **how records in one table are related to records in another table**.

Two tables can have different types of relationships depending on how frequently values occur in the columns used to establish the relationship.

The lecture discusses these main types:

1. **One-to-One (1:1)**
2. **One-to-Many (1:N)**
3. **Many-to-One (N:1)**
4. **Many-to-Many (N:N)**

These relationships are extremely important when building a **Power BI data model**.

---

# 6. One-to-One Relationship (1:1)

Let's take two tables.

### Table 1

| C1 | C2 |
| -- | -- |
| 1  | A  |
| 2  | B  |
| 3  | C  |

### Table 2

| C1 | C3 |
| -- | -- |
| 1  | X  |
| 2  | Y  |
| 3  | Z  |

The two tables are related using the `C1` column.

```text
Table 1.C1
    ↕
Table 2.C1
```

Now examine the values.

### Table 1

```text
1 → occurs once
2 → occurs once
3 → occurs once
```

### Table 2

```text
1 → occurs once
2 → occurs once
3 → occurs once
```

Therefore:

> Every value in Table 1 occurs exactly once in Table 2, and every value in Table 2 occurs exactly once in Table 1.

This is called a:

## One-to-One (1:1) Relationship

Conceptually:

```text
Table 1             Table 2

1  ───────────────  1
2  ───────────────  2
3  ───────────────  3
```

Each record on one side corresponds to exactly one record on the other side.

---

# 7. One-to-Many Relationship (1:N)

Now consider another example.

### Table 1

| C1 | C2 |
| -- | -- |
| 1  | A  |
| 2  | B  |
| 3  | C  |

### Table 2

| C1 | C3 |
| -- | -- |
| 1  | X  |
| 1  | Y  |
| 2  | M  |
| 3  | N  |
| 3  | T  |
| 3  | P  |

Again, the relationship is based on:

```text
Table 1.C1 ↔ Table 2.C1
```

Now examine the occurrences.

### Value 1

Table 1:

```text
1 → once
```

Table 2:

```text
1 → twice
```

### Value 2

Table 1:

```text
2 → once
```

Table 2:

```text
2 → once
```

That's fine because the value can occur once or multiple times on the second side.

### Value 3

Table 1:

```text
3 → once
```

Table 2:

```text
3 → three times
```

Therefore, a single value in Table 1 can correspond to **one or more records in Table 2**.

This is a:

# One-to-Many (1:N) Relationship

```text
Table 1              Table 2

1 ───────────────→   1
                     1

2 ───────────────→   2

3 ───────────────→   3
                     3
                     3
```

The important point is:

> **One record on the Table 1 side can be associated with multiple records on the Table 2 side.**

---

# 8. Understanding the "One" and "Many" Sides

In the above example:

```text
Table 1 → One side
Table 2 → Many side
```

So we say:

**Table 1 → Table 2 = One-to-Many**

or:

**1 : N**

where:

* `1` = one
* `N` = many

For example:

```text
One Student → Many Marks Records
```

A student may have:

```text
Student ID = 1

Math       98
English    78
Hindi      94
Science    88
```

The student exists once in the Student table, but can have multiple records in a marks/transactions table.

---

# 9. Many-to-Many Relationship (N:N)

Now consider another situation.

### Table 1

| C1 | C2 |
| -- | -- |
| 1  | A  |
| 1  | B  |
| 1  | C  |
| 2  | D  |
| 2  | E  |

### Table 2

| C1 | C3 |
| -- | -- |
| 1  | X  |
| 1  | N  |
| 1  | P  |
| 2  | M  |
| 2  | X  |
| 3  | N  |
| 3  | X  |

The two tables are related using `C1`.

Now observe the values.

### Value 1

In Table 1:

```text
1 → occurs multiple times
```

In Table 2:

```text
1 → occurs multiple times
```

So:

```text
Many records ↔ Many records
```

### Value 2

In Table 1:

```text
2 → occurs multiple times
```

In Table 2:

```text
2 → occurs multiple times
```

Again:

```text
Many ↔ Many
```

### Value 3

It may occur multiple times on the relevant side as well.

Therefore, multiple records in Table 1 can correspond to multiple records in Table 2.

This is called:

# Many-to-Many (N:N) Relationship

Conceptually:

```text
Table 1                    Table 2

1 ────────────────→        1
1 ────────────────→        1
1 ────────────────→        1

2 ────────────────→        2
2 ────────────────→        2

...                        ...
```

The key idea is:

> **Many records on one side can be related to many records on the other side.**

---

# 10. Reverse of One-to-Many = Many-to-One

The lecture then takes the one-to-many example and **reverses the direction**.

Consider:

### Table 1

| C1 | C2 |
| -- | -- |
| 1  | A  |
| 1  | B  |
| 1  | C  |
| 2  | D  |
| 2  | E  |

Here:

* `1` occurs multiple times.
* `2` occurs multiple times.

### Table 2

| C1 | C3 |
| -- | -- |
| 1  | T  |
| 2  | X  |

Here:

* `1` occurs once.
* `2` occurs once.

---

# 11. Analyze the Relationship

For value `1`:

```text
Table 1 → 1 occurs multiple times
Table 2 → 1 occurs once
```

For value `2`:

```text
Table 1 → 2 occurs multiple times
Table 2 → 2 occurs once
```

Therefore:

```text
Table 1 → Many side
Table 2 → One side
```

So, when describing the relationship **from Table 2 to Table 1**, it is:

# One-to-Many

```text
Table 2 (One)
      │
      ↓
Table 1 (Many)
```

But if you describe it from **Table 1 to Table 2**, it is:

# Many-to-One

```text
Table 1 (Many)
      │
      ↓
Table 2 (One)
```

This distinction is important.

---

# 12. All Cardinalities at a Glance

| Cardinality | Meaning                                     |
| ----------- | ------------------------------------------- |
| **1:1**     | One record relates to exactly one record    |
| **1:N**     | One record relates to multiple records      |
| **N:1**     | Multiple records relate to one record       |
| **N:N**     | Multiple records relate to multiple records |

---

# 13. Visual Summary

### One-to-One

```text
Table 1                 Table 2

1 ──────────────────── 1
2 ──────────────────── 2
3 ──────────────────── 3
```

**One ↔ One**

---

### One-to-Many

```text
Table 1                 Table 2

1 ──────────────────── 1
                        1

2 ──────────────────── 2

3 ──────────────────── 3
                        3
                        3
```

**One → Many**

---

### Many-to-One

```text
Table 1                 Table 2

1 ──────────────────── 1
1
1

2 ──────────────────── 2
2
```

**Many → One**

---

### Many-to-Many

```text
Table 1                 Table 2

1 ──────────────────── 1
1 ──────────────────── 1
1 ──────────────────── 1

2 ──────────────────── 2
2 ──────────────────── 2
```

**Many ↔ Many**

---

# 14. Cardinality in Power BI

When you create a relationship between two tables in **Power BI**, you need to specify the appropriate cardinality based on how the data is structured.

For example, suppose you have:

### Customer Table

| CustomerID | CustomerName |
| ---------- | ------------ |
| 1          | A            |
| 2          | B            |
| 3          | C            |

`CustomerID` is unique.

### Sales Table

| CustomerID | Sales |
| ---------: | ----: |
|          1 |   100 |
|          1 |   200 |
|          2 |   300 |
|          3 |   150 |

Here:

```text
Customer.CustomerID
        │
        │ 1 : N
        ↓
Sales.CustomerID
```

One customer can have multiple sales records.

Therefore:

**Customer → Sales = One-to-Many**

This is one of the most common relationship patterns you'll encounter in Power BI data models.

---

# 15. How to Decide Cardinality

When creating a relationship, follow this thought process:

### Step 1 — Identify the columns used for the relationship

For example:

```text
Table 1.C1
Table 2.C1
```

### Step 2 — Check whether the value is unique in each table

Ask:

> Does each value occur only once?

### Step 3 — Determine the side with unique values

If the values are unique in Table 1 but repeated in Table 2:

```text
Table 1 = One
Table 2 = Many
```

Therefore:

```text
1 : N
```

### Step 4 — If both sides are unique

```text
Table 1 = One
Table 2 = One
```

Therefore:

```text
1 : 1
```

### Step 5 — If both sides contain duplicates

```text
Table 1 = Many
Table 2 = Many
```

Therefore:

```text
N : N
```

---

# 16. Important Concept: Direction Matters

The same two tables can be described differently depending on which direction you're talking about.

For example:

```text
Table 1 = Many
Table 2 = One
```

From **Table 1 → Table 2**:

**Many-to-One (N:1)**

From **Table 2 → Table 1**:

**One-to-Many (1:N)**

So always identify **which table is on the "one" side and which table is on the "many" side**.

---

# 17. Key Points to Remember for Exams/Interviews

### Primary Key

* Unique.
* Non-null.
* Identifies a record uniquely.

### Foreign Key

* References a key in another table.
* Can contain duplicates.
* Can contain NULL values.
* Its values should correspond to values available in the referenced key.

### Cardinality

Cardinality describes how records in two related tables correspond to each other.

The four important types are:

```text
1. One-to-One       (1:1)
2. One-to-Many      (1:N)
3. Many-to-One      (N:1)
4. Many-to-Many     (N:N)
```

### Most common Power BI scenario

A typical Power BI model often has:

```text
Dimension Table          Fact Table
     (One)                  (Many)
       │                       │
       └────── 1 : N ──────────┘
```

For example:

```text
Customer
CustomerID
    │
    │ 1 : N
    ↓
Sales
CustomerID
```

One customer can have many sales transactions.

---

# 18. Final Mental Model

Keep this simple rule in mind:

> **Look at how many times the same key value occurs on each side.**

| Table 1        | Table 2        | Relationship |
| -------------- | -------------- | ------------ |
| Once           | Once           | **1:1**      |
| Once           | Multiple times | **1:N**      |
| Multiple times | Once           | **N:1**      |
| Multiple times | Multiple times | **N:N**      |

And remember the foreign-key rule:

> **Foreign-key values should correspond to values available in the referenced primary/unique key.**

These cardinalities will become important when you start **creating relationships in the Power BI data model**, because the correct cardinality determines how Power BI understands and propagates relationships between your tables.
