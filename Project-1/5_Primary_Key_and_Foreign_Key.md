# Power BI Data Modeling — Primary Key & Foreign Key

## 1. Why these concepts are important

When creating a **Power BI report**, especially during the **data modeling** phase, you will often work with multiple tables.

These tables need to be connected to each other so that Power BI can understand how data in one table relates to data in another.

Two fundamental concepts used for this are:

1. **Primary Key**
2. **Foreign Key**

These concepts are the foundation for creating **relationships between tables** in a Power BI data model.

---

# 2. Primary Key

### Definition

A **primary key** is an attribute (column) or a group of attributes (multiple columns) that can be used to **uniquely identify every record in a table**.

A primary key must contain:

* **Unique values**
* **Non-null values**

In simple terms:

> Every row should have a unique primary-key value, and that value cannot be blank/null.

---

## 3. Example of a Primary Key

Suppose we have a table called **Table 1**.

| ID | Name   | Course |
| -: | ------ | ------ |
|  1 | Nithin | A      |
|  2 | Rajat  | B      |
|  3 | Nithin | NULL   |
|  4 | Raj    | A      |

### Step 1: Check the ID column

The `ID` values are:

* 1
* 2
* 3
* 4

Every value is unique.

There are also **no NULL values**.

Therefore:

**ID → Primary Key**

---

## 4. Why Name cannot be the Primary Key

Look at the `Name` column:

| ID | Name   |
| -: | ------ |
|  1 | Nithin |
|  2 | Rajat  |
|  3 | Nithin |
|  4 | Raj    |

`Nithin` appears twice.

Therefore, `Name` cannot uniquely identify a record.

### Important point

Even if a column currently appears to contain unique values, you need to consider whether duplicate values could exist when more records are added.

Therefore:

**Name ≠ Primary Key**

---

# 5. Why Course cannot be the Primary Key

Look at the `Course` column:

| ID | Course |
| -: | ------ |
|  1 | A      |
|  2 | B      |
|  3 | NULL   |
|  4 | A      |

There are two problems:

### Problem 1: Duplicate values

Course `A` appears multiple times.

Multiple students can obviously be enrolled in the same course.

### Problem 2: NULL value

The course for ID 3 is NULL.

A primary key cannot contain NULL values.

Therefore:

**Course ≠ Primary Key**

---

# 6. Primary Key — Key Characteristics

Remember these characteristics:

| Characteristic                  | Primary Key |
| ------------------------------- | ----------- |
| Uniquely identifies a record    | ✅           |
| Duplicate values allowed        | ❌           |
| NULL values allowed             | ❌           |
| Can be a single column          | ✅           |
| Can consist of multiple columns | ✅           |

A primary key can therefore be thought of as the **unique identifier of a row**.

---

# 7. Foreign Key

Now consider that we have **multiple tables** in our dataset.

These tables can be related to each other using common attributes.

A **foreign key** is an attribute or group of attributes in one table that refers to a key in another table, typically the primary key of that related table.

Unlike a primary key, a foreign key:

* **Can contain duplicate values**
* **Can contain NULL values**

This is important because one record in the first table can have **multiple related records** in the second table.

---

# 8. Example of a Foreign Key

We already have **Table 1**:

### Table 1

| ID | Name   | Course |
| -: | ------ | ------ |
|  1 | Nithin | A      |
|  2 | Rajat  | B      |
|  3 | Nithin | NULL   |
|  4 | Raj    | A      |

Here:

**ID = Primary Key**

Now let's create **Table 2**.

| ID | Subject | Marks |
| -: | ------- | ----: |
|  1 | Math    |    98 |
|  1 | English |    78 |
|  2 | Math    |    97 |
|  2 | English |    89 |
|  3 | Hindi   |    94 |

---

# 9. Identifying the Foreign Key

Look at the `ID` column in Table 2:

```text
1
1
2
2
3
```

Here:

* ID 1 occurs twice
* ID 2 occurs twice
* ID 3 occurs once

Therefore, the ID column **contains duplicate values**.

That's perfectly valid for a foreign key.

So:

**Table 2 → ID = Foreign Key**

The `ID` in Table 2 refers back to the `ID` in Table 1.

---

# 10. Understanding the Relationship

Consider ID = 1.

### Table 1

| ID | Name   | Course |
| -: | ------ | ------ |
|  1 | Nithin | A      |

This tells us:

> Student 1 is Nithin and is enrolled in Course A.

Now look at Table 2:

| ID | Subject | Marks |
| -: | ------- | ----: |
|  1 | Math    |    98 |
|  1 | English |    78 |

This tells us:

> Student 1 has 98 marks in Math and 78 marks in English.

Therefore, the `ID` allows us to connect the information in the two tables.

---

# 11. Primary Key vs Foreign Key

This is one of the most important comparisons to remember.

| Feature                | Primary Key                  | Foreign Key                           |
| ---------------------- | ---------------------------- | ------------------------------------- |
| Purpose                | Uniquely identifies a record | Connects to a record in another table |
| Duplicate values       | ❌ Not allowed                | ✅ Allowed                             |
| NULL values            | ❌ Not allowed                | ✅ Can be allowed                      |
| Uniqueness required    | ✅ Yes                        | ❌ No                                  |
| Used for relationships | ✅                            | ✅                                     |
| Example                | Table 1 → ID                 | Table 2 → ID                          |

### Easy way to remember

**Primary Key = Who is this record?**

**Foreign Key = Which record does this belong to/relate to?**

---

# 12. Relationship Between Table 1 and Table 2

The relationship can be represented conceptually as:

```text
Table 1                         Table 2
─────────                       ─────────
ID          ←──────────────→    ID
Name                            Subject
Course                          Marks
```

Here:

```text
Table 1.ID = Primary Key
Table 2.ID = Foreign Key
```

Therefore:

**Table 1 and Table 2 are related through the ID column.**

---

# 13. One-to-Many Relationship

The example also demonstrates an important relationship pattern.

In Table 1:

```text
ID = 1
```

appears **once**.

But in Table 2:

```text
ID = 1
```

appears **multiple times**.

Similarly:

```text
Table 1        Table 2

ID = 1    →    ID = 1, ID = 1
ID = 2    →    ID = 2, ID = 2
ID = 3    →    ID = 3
```

This represents a **one-to-many relationship**:

> One record in Table 1 can be associated with multiple records in Table 2.

For example:

**One student → Multiple subject/marks records**

---

# 14. How this is used in Power BI

When you build a Power BI data model, you may have tables such as:

```text
Customer Table
        ↓
Sales Table
        ↓
Product Table
        ↓
Date Table
```

Each table can contain keys that allow Power BI to establish relationships.

For example:

```text
Customer
────────────
CustomerID  ← Primary Key
Name
City

        │
        │ relationship
        ↓

Sales
────────────
CustomerID  ← Foreign Key
OrderID
Sales
Quantity
```

Here:

* `Customer[CustomerID]` is the **primary/unique side**
* `Sales[CustomerID]` is the **foreign/many side**

This relationship allows Power BI to analyze sales based on customer attributes.

---

# 15. Important Takeaways

### Primary Key

A primary key:

* Uniquely identifies each record.
* Must contain unique values.
* Cannot contain NULL values.
* Can be a single attribute or a group of attributes.
* Represents the unique side of a relationship.

### Foreign Key

A foreign key:

* References a key in another table.
* Can contain duplicate values.
* Can contain NULL values.
* Is used to establish relationships between tables.
* Usually represents the "many" side of a relationship.

---

## 16. Core Example to Remember

### Table 1

| ID | Name   | Course |
| -: | ------ | ------ |
|  1 | Nithin | A      |
|  2 | Rajat  | B      |
|  3 | Nithin | NULL   |
|  4 | Raj    | A      |

**Primary Key → `ID`**

### Table 2

| ID | Subject | Marks |
| -: | ------- | ----: |
|  1 | Math    |    98 |
|  1 | English |    78 |
|  2 | Math    |    97 |
|  2 | English |    89 |
|  3 | Hindi   |    94 |

**Foreign Key → `ID`**

Therefore:

```text
Table 1.ID (Primary Key)
          │
          │
          ↓
Table 2.ID (Foreign Key)
```

The **primary key–foreign key concept is fundamental to creating relationships between tables**, and these relationships will be used extensively when building the Power BI data model and eventually creating reports.
