# Power BI — Formatting and Creating Visuals for the Financial Risk Matrix

## 1. Objective of the Session

In the previous sessions, two DAX measures were created:

1. **Year-on-Year Loan Amount Change**
2. **Year-on-Year Default Loans Change**

In this session, the focus is on **creating and formatting the visuals** that will represent these two measures on the **Financial Risk Matrix** page.

The session mainly covers:

* Reusing formatting from an existing visual
* Creating a second line chart
* Assigning the two YoY measures to the two charts
* Changing line colors
* Adjusting transparency
* Removing vertical gridlines
* Applying consistent formatting across report pages

---

# 2. Existing Line Chart

The Financial Risk Matrix page already contains one line chart.

The instructor first resizes the existing chart to make better use of the available space.

### Steps

1. Select the existing line chart.
2. Resize it as required.
3. Position it appropriately on the page.

The chart will eventually be one of the two line charts on the page.

---

# 3. Copy Formatting from the Second Report Page

Instead of manually formatting the chart from scratch, the instructor reuses the formatting from a line chart that already exists on the **second report page**.

This is done using **Format Painter**.

### Steps

1. Go to the **second report page**.
2. Select one of the existing line charts.
3. Click **Format Painter**.
4. Move to the **third page**, i.e. the **Financial Risk Matrix** page.
5. Click the line chart on the third page.

The formatting from the second-page line chart is transferred to the third-page chart.

### Key Concept — Format Painter

**Format Painter** allows you to copy the formatting of one Power BI visual and apply it to another visual.

This avoids manually repeating formatting settings.

---

# 4. Create the Second Line Chart

The Financial Risk Matrix page requires two line charts.

The first line chart is already present.

### Steps

1. Select the formatted line chart.
2. Press:

```text
Ctrl + C
```

3. Press:

```text
Ctrl + V
```

4. A copy of the line chart is created.
5. Move the copied chart to the **right-hand side** of the first chart.
6. Increase/adjust the size of the charts as required.

The page now contains two line charts positioned next to each other.

---

# 5. First Line Chart — Year-on-Year Loan Amount Change

The first line chart initially contains the:

> **Year-on-Year Default Loans Change**

measure.

However, the instructor wants this chart to represent the **loan amount change**.

### Steps

1. Select the **first line chart**.
2. Locate the existing:

> **Year-on-Year Default Loans Change**

measure.

3. Remove/uncheck it.
4. Select/check:

> **Year-on-Year Loan Amount Change**

The first chart now represents:

> **Year-on-Year Loan Amount Change by Year**

### Final configuration

**Measure:**

> Year-on-Year Loan Amount Change

**Category/Axis:**

> Year

**Chart title:**

> Year-on-Year Loan Amount Change by Year

The instructor confirms that this heading is appropriate.

---

# 6. Second Line Chart — Year-on-Year Default Loans Change

The second line chart retains the other measure.

It represents:

> **Year-on-Year Default Loans Change by Year**

So the two charts now have different purposes.

### Chart 1

> **Year-on-Year Loan Amount Change by Year**

### Chart 2

> **Year-on-Year Default Loans Change by Year**

This allows the report user to compare the year-over-year change in:

* Loan amounts
* Number of default loans

---

# 7. Format the First Line Chart

The instructor then starts formatting the two charts individually.

For the first chart:

> **Year-on-Year Loan Amount Change**

the line color needs to be changed.

### Steps

1. Select the first line chart.
2. Click:

**Format Your Visual**

3. Locate the **Lines** section.
4. Scroll down to **Colors**.
5. Click the color selector.
6. Select **More Colors**.
7. Enter the specified color code:

> **#46B1C9**

8. Press **Enter**.

The line in the first chart now uses the specified color.

---

# 8. Adjust Transparency of the First Chart

The instructor also changes the transparency of the first chart's line.

### Steps

1. Continue in the formatting options for the first chart.
2. Locate the **Transparency** setting.
3. Increase/set the transparency to:

> **44**

This makes the line slightly more transparent.

---

# 9. Format the Second Line Chart

The second chart represents:

> **Year-on-Year Default Loans Change**

Its line should have a different color from the first chart.

### Steps

1. Select the second line chart.
2. Click:

**Format Your Visual**

3. Go to:

**Lines**

4. Scroll down to the **Colors** section.
5. Click the color selector.
6. Click **More Colors**.
7. Enter:

> **#BCC1BA**

8. Press **Enter**.

The second chart now uses the specified color.

---

# 10. Color Assignment Summary

The two charts use different colors to visually distinguish the two metrics.

| Visual            | Measure                           | Color     |
| ----------------- | --------------------------------- | --------- |
| First Line Chart  | Year-on-Year Loan Amount Change   | `#46B1C9` |
| Second Line Chart | Year-on-Year Default Loans Change | `#BCC1BA` |

For the first chart, the instructor also sets transparency to:

> **44**

---

# 11. Remove Gridlines

The instructor does not want gridlines to appear on these charts.

Although the existing gridlines are light-colored, they are still visible.

Therefore, they are removed to make the visuals cleaner.

---

# 12. Remove Vertical Gridlines from First Chart

### Steps

1. Select the first line chart.
2. Expand the **Visualization** pane if necessary.
3. Click **Format Your Visual**.
4. Locate:

> **Gridlines**

5. Find the **Vertical Gridline** option.
6. Change it to:

> **Off**

The vertical gridlines are now removed from the first chart.

---

# 13. Remove Vertical Gridlines from Second Chart

The same formatting needs to be applied to the second line chart.

### Steps

1. Select the second line chart.
2. Open **Format Your Visual**.
3. Locate **Gridlines**.
4. Find **Vertical Gridline**.
5. Set it to:

> **Off**

Both line charts now have their vertical gridlines removed.

---

# 14. Check the Second Report Page

The instructor also checks the second report page to ensure that the same gridline formatting is consistent.

### Steps

1. Navigate to the **second report page**.
2. Select the relevant visual/chart.
3. Open **Format Your Visual**.
4. Go to **Gridlines**.
5. Check the vertical gridline setting.

In this case, the instructor observes that the other charts on the second page **already do not have gridlines**.

Therefore, no additional changes are required there.

---

# 15. Final Financial Risk Matrix Page

After completing the formatting, the third page — **Financial Risk Matrix** — contains the two required line charts.

### Visual 1

**Year-on-Year Loan Amount Change by Year**

* Represents changes in loan amount across years.
* Line color: `#46B1C9`
* Transparency: 44
* Vertical gridlines: Off

### Visual 2

**Year-on-Year Default Loans Change by Year**

* Represents changes in default loans across years.
* Line color: `#BCC1BA`
* Vertical gridlines: Off

---

# 16. Why Format Painter Was Used

A key technique demonstrated in this session is **Format Painter**.

Instead of manually reproducing formatting settings from another chart:

```text
Existing formatted visual
          ↓
    Format Painter
          ↓
Target visual
```

This copies the visual's formatting and helps maintain consistency across the report.

This is particularly useful when several report pages should follow the same visual design.

---

# 17. Important Formatting Workflow

The formatting process can be remembered as:

```text
Go to second report page
        ↓
Select existing line chart
        ↓
Click Format Painter
        ↓
Go to Financial Risk Matrix page
        ↓
Click target line chart
        ↓
Formatting copied
        ↓
Copy line chart
Ctrl + C → Ctrl + V
        ↓
Place second chart on right
        ↓
Chart 1:
Remove Default Loans Change
        ↓
Add Loan Amount Change
        ↓
Chart 2:
Keep Default Loans Change
        ↓
Format Chart 1
Color → #46B1C9
Transparency → 44
        ↓
Format Chart 2
Color → #BCC1BA
        ↓
Remove Vertical Gridlines
        ↓
Apply to both charts
```

---

# 18. Final Comparison of the Two Visuals

| Property           | Line Chart 1                   | Line Chart 2                          |
| ------------------ | ------------------------------ | ------------------------------------- |
| Metric             | YoY Loan Amount Change         | YoY Default Loans Change              |
| Time dimension     | Year                           | Year                                  |
| Title              | YoY Loan Amount Change by Year | YoY Default Loans Change by Year      |
| Line color         | `#46B1C9`                      | `#BCC1BA`                             |
| Transparency       | 44                             | Not specifically stated in transcript |
| Vertical gridlines | Off                            | Off                                   |

---

# 19. Key Takeaways

### Visual Creation

* An existing line chart was resized and reused.
* **Format Painter** was used to copy formatting from the second page.
* The formatted chart was duplicated using `Ctrl + C` and `Ctrl + V`.
* The second chart was positioned on the right side.

### Measures Used

The two previously created measures are:

1. **Year-on-Year Loan Amount Change**
2. **Year-on-Year Default Loans Change**

### Chart 1

Represents:

> **Year-on-Year Loan Amount Change by Year**

### Chart 2

Represents:

> **Year-on-Year Default Loans Change by Year**

### Formatting

* First chart color: **#46B1C9**
* First chart transparency: **44**
* Second chart color: **#BCC1BA**
* Vertical gridlines: **Off** for both charts.

### Report Design

The instructor emphasizes keeping the visuals clean by removing unnecessary gridlines and maintaining consistent formatting across pages.

---

# 20. Session Outcome

At the end of this session, the **Financial Risk Matrix** page has two formatted line charts:

```text
┌─────────────────────────────┐  ┌─────────────────────────────┐
│ YoY Loan Amount Change      │  │ YoY Default Loans Change    │
│             ╱───╲           │  │        ╱╲                   │
│       ╱─────╯     ╲          │  │   ────╯  ╲────              │
│                             │  │                             │
│        By Year              │  │        By Year              │
└─────────────────────────────┘  └─────────────────────────────┘
```

The remaining visuals and additional formatting for the **Financial Risk Matrix** page will be covered in the subsequent sessions.
