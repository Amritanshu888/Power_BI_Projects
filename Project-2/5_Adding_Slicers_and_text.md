# Detailed Notes — Power BI Report Formatting, Theme & Slicers

## 1. Purpose of This Lecture

In the previous lecture, we covered **data profiling**.

In this lecture, we move back to the **Report View** and begin the actual report-building process.

The main activities covered are:

* Applying a dark theme to the report
* Creating slicers
* Changing slicer style
* Creating multiple slicers efficiently using copy/paste
* Adding slicers for Policy Number, Claim Number, and Customer ID
* Adding the insurance company's name using a text box
* Formatting and positioning the text box
* Preparing the report page for adding more visuals

---

# 2. Return to Report View

Since the data profiling was performed inside **Power Query Editor**, the instructor first applies the changes and returns to the report.

### Steps

1. Go to the **Home** tab.
2. Click:

> **Close & Apply**

This closes Power Query Editor and takes you back to **Power BI Report View**.

---

# 3. Apply a Dark Theme

The instructor wants the project to use a **dark-colored theme**.

### Steps

1. Go to the **View** tab.
2. Locate the **Themes** section.
3. Power BI displays several default themes.
4. Select the desired **dark theme**.

After selecting it:

> The background/theme of the report changes to a dark color.

This dark theme will be used throughout the project.

### Important

The theme provides a consistent visual appearance for the report.

---

# 4. Add the First Slicer

The first visual added to the report is a:

> **Slicer**

A slicer allows report users to interactively filter the report based on a particular field.

### Steps

1. Click the **Slicer** visual from the Visualizations pane.
2. A blank slicer appears on the report canvas.
3. Resize the slicer as required.

---

# 5. Create a Policy Number Slicer

The first slicer will be used to display the available:

> **Policy Numbers**

### Steps

1. Select the blank slicer.
2. From the **Data** pane, locate **Policy Number**.
3. Check the box next to **Policy Number**.

Power BI adds Policy Number to the slicer.

The slicer now displays the different policy numbers available in the dataset.

---

# 6. Change Slicer Style from List to Dropdown

By default, the slicer is displayed as a vertical list.

The instructor changes it to a **dropdown** style to make the report more compact.

### Steps

1. Select the Policy Number slicer.
2. Open **Format Your Visual**.
3. Locate **Slicer settings**.
4. Find the **Style** option.
5. Change:

> **Vertical List**

to:

> **Dropdown**

The slicer now appears as a dropdown selector.

### Why use a dropdown?

Policy Number can contain many values. Displaying every policy number vertically would consume a lot of report space.

A dropdown provides a more compact interface.

---

# 7. Reposition and Resize the Slicer

After changing the style:

1. Move the slicer to the desired location.
2. Resize it as required.
3. Place it neatly on the report canvas.

The instructor positions the slicer toward the upper portion of the report.

---

# 8. Create Additional Slicers

The instructor wants to add two additional slicers.

The required slicers will represent:

1. **Policy Number**
2. **Claim Number**
3. **Customer ID**

Instead of creating every slicer from scratch, the instructor duplicates the existing slicer.

---

# 9. Duplicate the Slicer Using Copy/Paste

The existing slicer is copied and pasted.

### Keyboard shortcuts

```text id="5f2z6n"
Ctrl + C
Ctrl + V
```

### Steps

1. Select the existing slicer.
2. Press **Ctrl + C**.
3. Press **Ctrl + V**.
4. A duplicate slicer is created.
5. Move the duplicated slicer to the desired position.

This is faster than creating a completely new slicer and formatting it again.

---

# 10. Change the Second Slicer to Claim Number

The duplicated slicer initially contains **Policy Number**.

The instructor changes its field to:

> **Claim Number**

### Steps

1. Select the second slicer.
2. In the **Fields** bucket, locate **Policy Number**.
3. Remove **Policy Number**.
4. From the Data pane, select/check **Claim Number**.
5. Add Claim Number to the slicer's field.

The second slicer now displays the available claim numbers.

---

# 11. Create the Third Slicer

The instructor creates another slicer by duplicating the Claim Number slicer.

### Steps

1. Select the Claim Number slicer.
2. Press:

```text id="5y7r4v"
Ctrl + C
```

3. Press:

```text id="nd4vgy"
Ctrl + V
```

4. Move the newly created slicer to the desired location.

Now there are three slicers on the report page.

---

# 12. Change the Third Slicer to Customer ID

The third slicer currently contains:

> Claim Number

The instructor changes it to:

> **Customer ID**

### Steps

1. Select the third slicer.
2. Remove **Claim Number** from the Fields bucket.
3. Locate **Customer ID** in the Data pane.
4. Drag and drop **Customer ID** into the slicer's Fields bucket.

Alternatively, the instructor mentions selecting/double-clicking the Customer ID field and dragging it into the field bucket.

The third slicer now represents customer IDs.

---

# 13. Final Slicers Added

At this point, the report contains three slicers:

| Slicer        | Purpose                       |
| ------------- | ----------------------------- |
| Policy Number | Filter the report by policy   |
| Claim Number  | Filter the report by claim    |
| Customer ID   | Filter the report by customer |

These slicers will later allow users to interactively filter the report.

---

# 14. Reposition the Slicers

The instructor adjusts the position of all three slicers.

### Steps

1. Select each slicer.
2. Drag it to the desired position.
3. Resize if necessary.
4. Arrange the three slicers neatly on the report page.

The goal is to create a clean report layout.

---

# 15. Add the Company Name

The instructor wants to display the company name prominently on the report.

The company name used in the example is:

> **Prism Insurance Private Limited**

A **Text Box** is used for this purpose.

---

# 16. Insert a Text Box

### Steps

1. Go to the **Insert** tab.
2. Click:

> **Text Box**

3. A text box appears on the report canvas.
4. Enter:

> **Prism Insurance Private Limited**

The text box can then be resized and positioned.

---

# 17. Increase Text Size

The instructor increases the font size to make the company name more prominent.

### Steps

1. Select the text inside the text box.
2. Press:

```text id="z18l4r"
Ctrl + A
```

to select the text.
3. Change the font size.
4. The instructor uses approximately:

> **44**

The company name becomes much larger and more visible.

---

# 18. Resize and Position the Text Box

After increasing the font size:

1. Resize the text box so that the entire company name fits.
2. Move it to the desired location.
3. Drag and drop it into position.

The instructor places it as part of the report header area.

---

# 19. Format the Company Name

The text box can be further formatted.

With the text selected, you can change:

* Font style
* Bold
* Italic
* Font size
* Other available text formatting options

### Steps demonstrated

1. Select the text.
2. Press **Ctrl + A**.
3. Choose **Bold** if desired.
4. Choose **Italic** if desired.
5. Select a different **font style** from the font dropdown.

The instructor chooses a different font style to improve the appearance.

---

# 20. Reposition the Text Box

After formatting:

1. Adjust the position of the text box.
2. Move it to the appropriate location on the report.
3. Make sure it aligns well with the slicers and other visuals.

This contributes to a cleaner report layout.

---

# 21. Current Report Page Structure

At this stage, the report page contains:

```text id="1kkl5t"
┌───────────────────────────────────────────────┐
│       Prism Insurance Private Limited        │
│                                               │
│  [Policy Number ▼] [Claim Number ▼] [Customer│
│                                             ▼]│
│                                               │
│                                               │
│             Report Visuals                    │
│             to be added                       │
│                                               │
└───────────────────────────────────────────────┘
```

The exact positioning may differ, but the key elements introduced are:

* Dark theme
* Company name
* Policy Number slicer
* Claim Number slicer
* Customer ID slicer

---

# 22. Why Slicers Are Important

Slicers provide **interactive filtering**.

For example, if the user selects a particular:

> Customer ID

the other report visuals can respond to that selection.

Similarly, users can select:

* A policy
* A claim
* A customer

This makes the report interactive rather than static.

---

# 23. Why Copy/Paste Is Useful

Instead of repeatedly creating slicers from scratch, the instructor uses:

```text id="r3t1ut"
Ctrl + C
Ctrl + V
```

This is useful because the duplicated visual retains much of the original formatting.

You only need to:

1. Duplicate the visual.
2. Change the field.
3. Reposition it.

This saves time and maintains consistent formatting across visuals.

---

# 24. Important Power BI Actions Demonstrated

| Action               | How                                          |
| -------------------- | -------------------------------------------- |
| Add slicer           | Select Slicer visual                         |
| Add field to slicer  | Select/check or drag field                   |
| Change slicer style  | Format Your Visual → Slicer settings → Style |
| Make slicer dropdown | Change Vertical List → Dropdown              |
| Copy visual          | `Ctrl + C`                                   |
| Paste visual         | `Ctrl + V`                                   |
| Add text box         | Insert → Text Box                            |
| Select all text      | `Ctrl + A`                                   |
| Change font size     | Font size option                             |
| Change font style    | Font dropdown                                |
| Bold text            | Bold formatting                              |
| Italic text          | Italic formatting                            |
| Move visual          | Drag and drop                                |
| Resize visual        | Drag visual handles                          |

---

# 25. Key Takeaways

### Theme

* Go to **View → Themes**.
* Select the desired **dark theme**.
* The project uses the dark theme for its report design.

### Slicers

Three slicers are created:

1. **Policy Number**
2. **Claim Number**
3. **Customer ID**

The slicers are changed from:

> Vertical List → Dropdown

### Text Box

A text box is added containing:

> **Prism Insurance Private Limited**

It is:

* Resized
* Enlarged to approximately font size **44**
* Formatted
* Given a different font style
* Positioned appropriately on the report page

### Overall Goal

The lecture begins establishing the **visual layout and user-interaction controls** for the insurance Power BI report. More report visuals will be added in the following lectures.
