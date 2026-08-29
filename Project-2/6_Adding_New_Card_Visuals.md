# Detailed Notes — Formatting Slicers & Creating Card Visuals in Power BI

## 1. Objective of This Lecture

In the previous lecture, we created the basic report layout with:

* Dark theme
* Policy Number slicer
* Claim Number slicer
* Customer ID slicer
* Company name text box

In this lecture, two major things are covered:

1. **Formatting the existing slicers**
2. **Creating and formatting Card New visuals** to display:

   * Total Premium Amount
   * Total Coverage Amount
   * Total Claim Amount

The lecture also demonstrates how these card values dynamically respond to slicer selections.

---

# 2. Format the Existing Slicers

There are three slicers on the report page:

* Policy Number
* Claim Number
* Customer ID

The instructor wants to apply formatting to all of them.

---

## 3. Select All Three Slicers

Instead of formatting each slicer individually, all three are selected together.

### Steps

1. Click the first slicer.
2. Hold **Ctrl**.
3. Click the second slicer.
4. Continue holding **Ctrl** and click the third slicer.

Now all three slicers are selected.

This allows common formatting changes to be applied to multiple slicers at once.

---

# 4. Format the Slicer Header

With all three slicers selected:

1. Click **Format Your Visual**.
2. Locate **Slicer header**.
3. Change the font style.

The instructor chooses:

> **Trebuchet MS**

This changes the font used for the slicer headers.

---

# 5. Understand Slicer Header vs Slicer Values

A slicer has different textual elements.

### Slicer Header

The header represents the field name, such as:

* Policy Number
* Claim Number
* Customer ID

### Slicer Values

When you open a slicer, the available values are displayed.

For example, the Customer ID slicer can display customer IDs.

Similarly:

* Claim Number slicer → claim numbers
* Policy Number slicer → policy numbers

The instructor wants to change the font of these values as well.

---

# 6. Format Slicer Values

### Steps

1. Keep the slicers selected.
2. Go to the formatting options.
3. Locate the formatting option for the **values**.
4. Change the font.

The instructor changes the font to:

> **Proportions**

This changes the appearance of the values displayed inside the slicers.

### Important

The exact visual appearance changes when the dropdown is opened because the available IDs/values become visible.

---

# 7. Create Card Visuals

The next objective is to display important numerical metrics on the report page.

Three card visuals will be created:

1. **Premium Amount**
2. **Coverage Amount**
3. **Claim Amount**

These cards will provide summary values.

---

# 8. Add the First Card New Visual

### Steps

1. Click on a **blank area of the report canvas**.
2. Select:

> **Card New**

3. Power BI creates a blank card visual.
4. Move the card to the desired position.

---

# 9. Add Premium Amount to the Card

The first card will display:

> **Total Premium Amount**

### Steps

1. Select the newly created Card visual.
2. In the **Data** pane, locate:

   > **Premium Amount**
3. Check/select **Premium Amount**.

Power BI aggregates the column and displays the result on the card.

By default, Power BI displays something similar to:

> **Sum of Premium Amount**

This represents the total premium amount.

---

# 10. Change Card Shape

The instructor wants the card to have rounded corners.

### Steps

1. Select the card.
2. Click **Format Your Visual**.
3. Go to the **Cards** formatting section.
4. Locate the **Shape** option.
5. Change:

> Rectangle

to:

> **Rounded Rectangle**

The card now has rounded corners.

---

# 11. Resize the Card

The card can be resized according to the report layout.

### Steps

1. Select the card.
2. Drag the edges/corners.
3. Adjust its width and height.
4. Position it appropriately on the report canvas.

---

# 12. Rename the Card's Displayed Field

By default, Power BI displays:

> **Sum of Premium Amount**

The instructor wants a cleaner label:

> **Premium Amount**

### Steps

1. Locate the field inside the card's **Data/Fields bucket**.
2. It will be shown as something similar to:

   > Sum of Premium Amount
3. Double-click the field name.
4. Change it to:

> **Premium Amount**

5. Press **Enter**.

Now the card displays the cleaner label instead of "Sum of Premium Amount."

---

# 13. Reduce the Card Value Font Size

The numerical value displayed on the card is initially relatively large.

The instructor reduces its size.

### Steps

1. Select the card.
2. Click **Format Your Visual**.
3. Locate:

> **Callout values**

4. Find the font-size setting.
5. Change it to approximately:

> **25**

This makes the card value smaller and more balanced.

---

# 14. Center Align the Card Value

The instructor also changes the horizontal alignment.

### Steps

1. Select the card.
2. Go to the relevant formatting section.
3. Locate **Horizontal alignment**.
4. Select:

> **Center**

Now the value is centered within the card.

---

# 15. Further Resize the Premium Card

The instructor adjusts the size of the card further to make it fit nicely with the report layout.

The exact dimensions are not important.

The goal is:

> Create a visually balanced and consistently sized card.

---

# 16. Duplicate the Premium Card

Instead of creating the other cards from scratch, the instructor duplicates the existing card.

### Steps

1. Select the Premium Amount card.
2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

4. Move the newly created card to the desired position.

This preserves the existing formatting.

---

# 17. Create the Coverage Amount Card

The second card should represent:

> **Total Coverage Amount**

The duplicated card currently contains Premium Amount.

We need to replace that field.

### Steps

1. Select the second card.
2. Remove/uncheck:

> **Premium Amount**

3. Select/check:

> **Coverage Amount**

The card now displays the total coverage amount.

---

# 18. Rename "Sum of Coverage Amount"

By default, Power BI may display:

> **Sum of Coverage Amount**

The instructor wants:

> **Coverage Amount**

### Steps

1. Locate the `Sum of Coverage Amount` field in the card's data bucket.
2. Double-click the field name.
3. Change it to:

> **Coverage Amount**

4. Press **Enter**.

The card now has the desired label.

---

# 19. Create the Claim Amount Card

A third card is required to display:

> **Total Claim Amount**

Again, the instructor duplicates an existing card.

### Steps

1. Select the Coverage Amount card.
2. Press:

```text
Ctrl + C
Ctrl + V
```

3. Move the newly created card to the right side.

---

# 20. Change the Third Card to Claim Amount

The newly duplicated card currently represents Coverage Amount.

### Steps

1. Select the third card.
2. Remove/uncheck:

> **Coverage Amount**

3. Select/check:

> **Claim Amount**

The card now displays the total claim amount.

---

# 21. Rename "Sum of Claim Amount"

Power BI may display:

> **Sum of Claim Amount**

The instructor changes this to:

> **Claim Amount**

### Steps

1. Double-click the field name in the data bucket.
2. Replace the existing name with:

> **Claim Amount**

3. Press **Enter**.

Now the third card has a clean label.

---

# 22. Final Card Visuals

The report now has three cards:

| Card                | Represents            |
| ------------------- | --------------------- |
| **Premium Amount**  | Total premium amount  |
| **Coverage Amount** | Total coverage amount |
| **Claim Amount**    | Total claim amount    |

These cards summarize important financial values from the insurance dataset.

---

# 23. Important Concept — Cards Are Aggregating the Data

The fields being used are numerical columns:

* Premium Amount
* Coverage Amount
* Claim Amount

Power BI automatically applies an aggregation, in this case:

> **SUM**

Therefore, the card displays the total value of the selected field.

Conceptually:

```text id="2c4f7q"
Premium Amount Card
        ↓
SUM(Premium Amount)
        ↓
Total Premium Amount
```

Similarly:

```text id="h8v4wj"
Coverage Amount Card
        ↓
SUM(Coverage Amount)
        ↓
Total Coverage Amount
```

and:

```text id="p0y4av"
Claim Amount Card
        ↓
SUM(Claim Amount)
        ↓
Total Claim Amount
```

---

# 24. Dynamic Interaction Between Slicers and Cards

One of the most important demonstrations in this lecture is that the cards respond to slicer selections.

The slicers act as filters on the report.

When a user selects a specific policy, customer, or claim, the card values are recalculated based on that selection.

---

# 25. Example — Selecting a Policy

The instructor opens the Policy Number slicer and selects a policy such as:

> **P1055**

After selecting the policy, all three cards are filtered.

The cards now show values corresponding to that selected policy.

The instructor observes approximately:

* Premium received = **51.44**
* Total coverage = **92.06K**
* Claim amount = **1.01K**

The important point is not the specific numbers, but that:

> **The card values dynamically change according to the slicer selection.**

---

# 26. Example — Selecting a Claim Number

The instructor then selects a specific claim number, approximately:

> **C300**

The card values change again.

For that selection, the instructor observes approximately:

* Premium Amount = **690.52**
* Coverage Amount = **87.94**
* Claim Amount = **1.96**

This demonstrates that the Claim Number slicer filters the card visuals.

---

# 27. Example — Selecting a Customer ID

The instructor then selects:

> **C101**

from the Customer ID slicer.

The cards update again.

The instructor observes approximately:

* Premium Amount = **26.09**
* Coverage Amount = **65.0**
* Claim Amount = **0**

This indicates that no claim amount was paid/recorded for the selected customer in that filtered context.

---

# 28. Understanding the Dynamic Filtering

The overall interaction can be understood as:

```text
Slicer Selection
       ↓
Filter Context
       ↓
Underlying Insurance Data
       ↓
SUM(Premium Amount)
SUM(Coverage Amount)
SUM(Claim Amount)
       ↓
Card Visuals Update
```

Therefore, the cards are **not static numbers**.

They dynamically represent the aggregated values for the current filter context.

---

# 29. Reposition the Slicers

After testing the interactions, the instructor adjusts the slicer positions.

### Steps

1. Select the slicers.
2. Move them slightly downward.
3. Adjust their positions according to the report layout.
4. Make sure the cards and slicers are visually aligned.

The goal is to make the report look cleaner and more organized.

---

# 30. Final Layout at This Stage

The report now contains:

### Header

> **Prism Insurance Private Limited**

### Slicers

* Policy Number
* Claim Number
* Customer ID

### Cards

* Premium Amount
* Coverage Amount
* Claim Amount

### Theme

> Dark theme

A simplified structure:

```text id="5m8u7q"
┌──────────────────────────────────────────────────────────┐
│          PRISM INSURANCE PRIVATE LIMITED                 │
│                                                          │
│ [Policy Number ▼] [Claim Number ▼] [Customer ID ▼]      │
│                                                          │
│ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐      │
│ │   PREMIUM    │ │   COVERAGE   │ │    CLAIM     │      │
│ │    AMOUNT    │ │    AMOUNT    │ │    AMOUNT    │      │
│ │    Total     │ │    Total     │ │    Total     │      │
│ └──────────────┘ └──────────────┘ └──────────────┘      │
│                                                          │
│                More visuals to be added                 │
└──────────────────────────────────────────────────────────┘
```

---

# 31. Important Power BI Formatting Techniques Learned

### Selecting multiple visuals

Hold:

> **Ctrl + Click**

This allows common formatting changes to be applied to multiple selected visuals.

### Duplicate a visual

```text
Ctrl + C
Ctrl + V
```

Useful for creating consistently formatted cards/slicers.

### Change slicer formatting

> **Format Your Visual → Slicer settings**

### Change card shape

> **Format Your Visual → Cards → Shape → Rounded Rectangle**

### Change card number size

> **Format Your Visual → Callout values → Font size**

### Center the card value

> **Horizontal alignment → Center**

### Rename automatically generated aggregation labels

Change:

> `Sum of Premium Amount`

to:

> `Premium Amount`

and similarly for other fields.

---

# 32. Key Concepts to Remember

### 1. Slicers provide interactive filtering

Users can select:

* Policy
* Claim
* Customer

and the report responds accordingly.

### 2. Card visuals show summarized KPIs

The three cards show:

* Total Premium
* Total Coverage
* Total Claim

### 3. Card values are dynamic

The values change according to the current filter context.

### 4. Power BI automatically aggregates numerical columns

When a numerical column is added to a card, Power BI generally applies:

> **SUM**

unless the aggregation is changed.

### 5. Formatting improves readability

The instructor formats:

* Slicer headers
* Slicer values
* Card shape
* Card labels
* Card value size
* Card alignment

### 6. Reusing visuals saves time

Copying and pasting an existing card preserves its formatting, after which only the field needs to be changed.

---

# 33. Quick Revision Checklist

Before moving to the next lecture, the report should have:

* [x] Dark theme applied
* [x] Policy Number slicer
* [x] Claim Number slicer
* [x] Customer ID slicer
* [x] Slicer header font formatted
* [x] Slicer value font formatted
* [x] Premium Amount card
* [x] Coverage Amount card
* [x] Claim Amount card
* [x] Card shapes changed to rounded rectangles
* [x] Card labels cleaned up
* [x] Card values resized
* [x] Card values center-aligned
* [x] Slicer-card interaction tested
* [x] Visual positions adjusted

The next stage of the project will involve **adding more visuals to the report page** and building out the insurance analysis further.
