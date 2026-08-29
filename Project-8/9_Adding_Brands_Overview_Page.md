# Power BI Reporting – Creating the First Report Page: Available Brands

## 1. Objective of the Session

This session begins the **reporting phase** of the Power BI project.

The goal is to create the **first report page** that provides the user with an overview of the different **brands available in the dataset**.

The page will contain:

* A custom background image
* Customized canvas dimensions
* A customized wallpaper color
* A **Multi-row Card** visual showing available brands
* Formatting such as font size, font color, borders, shadow, and title
* The Filters pane hidden to provide a cleaner report layout

---

# 2. Start the Reporting Phase

After completing the data-cleaning and DAX calculations:

1. Return to **Power BI Desktop**.
2. Begin working in the **Report View**.
3. Create/configure the first report page.

The first page is intended as an **overview page**, rather than a page containing detailed analysis.

---

# 3. Add a Background Image to the Report Page

The first step is to add an image as the background of the report page.

### Steps

1. Open/expand the **Visualizations pane**.
2. Select the **Report Page** settings under the canvas/background settings.
3. Locate the option to add/search for an image.
4. Click **Browse**.
5. Navigate to:

**Desktop → Projects with Power BI**

6. Locate the required background image.
7. Double-click the image to select it.
8. Wait for the image to load.

The selected image becomes the background for the report page.

---

# 4. Set Background Transparency

After adding the image, the instructor changes its transparency.

### Steps

1. Locate the **Transparency** setting.
2. Set:

**Transparency = 0%**

This makes the background image fully visible.

However, the report still does not appear correctly because the canvas dimensions do not match the image.

Therefore, the canvas settings need to be adjusted.

---

# 5. Customize Canvas Settings

The next step is to change the size of the report canvas so that it fits the selected background image.

### Steps

1. Open **Canvas Settings**.
2. Locate **Type**.
3. Change the type to:

**Custom**

4. Set the canvas dimensions to the values used in the lecture:

* **Height:** `4563456`
* **Width:** `6912`

After changing these dimensions, the background should fit the report layout better.

> **Note:** These unusually large dimensions are the values stated in the transcript. If Power BI imposes a maximum-size restriction in your version, use the largest valid dimensions that preserve the intended aspect ratio.

---

# 6. Change the Wallpaper Color

The instructor also customizes the wallpaper color around the report canvas.

### Steps

1. In the formatting/settings area, select **Wallpaper**.
2. Open the color selector.
3. Click **More Colors**.
4. Enter the color code:

```text
808038D
```

The wallpaper color is therefore customized instead of using the default Power BI color.

---

# 7. Change Canvas Background Image Fit

The background image's fit setting is also adjusted.

### Steps

1. Select the **Canvas Background** settings.
2. Locate the **Image Fit** option.
3. Change it from:

**Normal**

to:

**Fit**

This helps the image fit the available canvas area more appropriately.

---

# 8. Hide the Filters Pane

The instructor does not want the Filters pane visible because it takes up unnecessary space on the report page.

### Steps

1. Go to the **View** tab.
2. Locate the **Filters** option.
3. Click it to turn the Filters pane off.

The Filters pane disappears, providing a cleaner report canvas.

---

# 9. Understand the Purpose of the First Report Page

The first page is designed to show the **different brands available in the dataset**.

The instructor first checks the data in **Table View**.

In the table, the first column contains the various brands.

The requirement is to present these brands visually so that a report user can quickly understand:

> **Which brands are available in the dataset?**

A **Multi-row Card** is selected for this purpose.

---

# 10. Rename the Report Page

The default page name is **Page 1**.

It should be renamed to something meaningful.

### Steps

1. At the bottom of the Power BI report canvas, locate **Page 1**.
2. Double-click the page name.
3. Rename it to:

**Brands**

The page now has a meaningful name that represents its purpose.

---

# 11. Add a Multi-row Card Visual

The instructor uses a **Multi-row Card** to display the available brands.

### Steps

1. Expand the **Visualizations pane**.
2. Select **Multi-row Card**.
3. A blank Multi-row Card is created on the canvas.
4. Drag the visual to the desired position, toward the right-hand side.
5. Resize the card as required.

The Multi-row Card will eventually display the different brand names.

---

# 12. Add Brand to the Multi-row Card

Now populate the visual with the Brand field.

### Steps

1. Select the **Multi-row Card**.
2. Expand the **Data pane** if necessary.
3. Locate the **Brand** column.
4. Click/drag **Brand** into the Multi-row Card visual.

Power BI displays the different brands available in the dataset.

Because there may be many brands, the user can scroll through the Multi-row Card to see all available values.

---

# 13. Increase the Brand Font Size

Initially, the brand names appear too small.

The instructor increases the font size significantly.

### Steps

1. Keep the Multi-row Card selected.
2. Open **Format your visual**.
3. Go to the **Cards** section.
4. Locate the font/text size setting.
5. The default size is approximately:

**12**

6. Increase it to:

**60**

The brand names become much larger.

The instructor then adjusts it slightly and chooses:

**55**

This provides a better visual balance.

### Final font size used

**55**

---

# 14. Change the Brand Text Color

The instructor changes the brand text from blue to white.

### Steps

1. With the Multi-row Card selected, open **Format your visual**.
2. Go to **Cards**.
3. Locate the text/color setting.
4. Change the text color from blue to:

**White**

This makes the text work better with the chosen background.

---

# 15. Remove the Card Background

The instructor does not want a separate background behind the Multi-row Card.

### Steps

1. Select the Multi-row Card.
2. Open **Format your visual**.
3. Go to:

**General → Effects**

4. Locate **Background**.
5. Turn the background **Off**.

The card now blends into the report page background.

---

# 16. Add a Border to the Card

The instructor then adds an outline/border around the Multi-row Card.

### Steps

1. Keep the Multi-row Card selected.
2. Go to:

**Format your visual → Visual → Cards → Style**

3. Locate the border/outline options.
4. You can configure the borders for:

   * Top
   * Bottom
   * Left
   * Right
5. Enable the required borders.
6. Change the border color to:

**White**

The white border helps separate the card from the background.

---

# 17. Adjust Outline Weight

The border's thickness can also be controlled.

### Steps

1. Under the card's style/border settings, locate **Outline Weight**.
2. Adjust the weight as required.

The instructor keeps the outline relatively light/thin rather than using a very heavy border.

---

# 18. Accent Bar

The formatting options also include an **Accent Bar**.

The instructor keeps the Accent Bar enabled/available as part of the card formatting.

This can be used to provide an additional visual element to the card.

---

# 19. Change the Font Style

The instructor further customizes the font.

### Steps

1. In the card formatting options, locate **Font**.
2. Choose a font style of your preference.
3. The instructor chooses to use an **italic** text style.
4. The text is not kept bold.

So the final brand text uses an italic-style appearance rather than bold text.

---

# 20. Scrolling Through the Brands

Because there are multiple brands, not all of them may fit simultaneously inside the card.

The user can therefore:

> **Scroll down inside the Multi-row Card**

to see the remaining brands.

This makes the visual useful for presenting a long list of available brands without taking up excessive space.

---

# 21. Add a Shadow to the Multi-row Card

The instructor then adds a shadow around the card to make it visually stand out.

### Steps

1. Select the Multi-row Card.
2. Open **Format your visual**.
3. Go to:

**General → Effects**

4. Enable/configure **Shadow**.
5. A shadow is initially displayed in black.
6. Click the **Shadow** color option.
7. Change the shadow color from black to:

**White**

This creates a lighter visual effect that matches the overall design.

---

# 22. Add a Title to the Multi-row Card

The instructor adds a heading to make the purpose of the visual immediately clear.

### Steps

1. Select the Multi-row Card.
2. Open **Format your visual**.
3. Go to:

**General → Title**

4. Turn the **Title** option **On**.
5. Open the Title settings.
6. Enter the title:

**Available Brands**

This tells the user exactly what the visual represents.

---

# 23. Format the Title

The title is also customized.

### Font Size

Increase the title font size to:

**60**

### Font Style

The instructor chooses a bold style for the title.

### Text Color

Change the title text color to:

**White**

### Alignment

The instructor sets the title alignment to:

**Right**

Therefore, the title appears as a large, bold, white, right-aligned heading.

---

# 24. Add a Border Around the Entire Visual

In addition to the internal card border, the instructor also demonstrates how to add a border around the entire visual.

### Steps

1. Select the Multi-row Card.
2. Open:

**Format your visual → General → Effects**

3. Locate **Border**.
4. Turn the border **On**.
5. Change the border color to:

**White**

This provides a clear outer boundary around the visual.

---

# 25. Final Appearance of the First Report Page

The completed page contains:

### Background

* Custom background image
* Transparency = 0%
* Custom canvas dimensions
* Image Fit = Fit
* Custom wallpaper color

### Report Page

* Page name: **Brands**
* Filters pane hidden

### Multi-row Card

* Displays **Brand**
* Large brand text
* Font size approximately **55**
* White text
* No card background
* White borders
* Light outline
* Accent bar retained
* Italic brand text
* White shadow
* Title: **Available Brands**
* Title font size: **60**
* Bold title
* White title
* Right-aligned title
* Outer border enabled

---

# 26. Formatting Settings Summary

| Element            | Setting          |
| ------------------ | ---------------- |
| Page Name          | Brands           |
| Background         | Custom image     |
| Transparency       | 0%               |
| Canvas Type        | Custom           |
| Canvas Height      | 4563456*         |
| Canvas Width       | 6912*            |
| Wallpaper Color    | `808038D`*       |
| Image Fit          | Fit              |
| Filters Pane       | Off              |
| Visual             | Multi-row Card   |
| Field              | Brand            |
| Brand Font Size    | 55               |
| Brand Text Color   | White            |
| Card Background    | Off              |
| Card Border        | White            |
| Outline            | Light/thin       |
| Accent Bar         | Retained         |
| Brand Font Style   | Italic           |
| Shadow             | On               |
| Shadow Color       | White            |
| Visual Title       | Available Brands |
| Title Font Size    | 60               |
| Title Font Style   | Bold             |
| Title Color        | White            |
| Title Alignment    | Right            |
| Outer Border       | On               |
| Outer Border Color | White            |

*These values are transcribed from the lecture. The very large canvas dimensions/color code should be verified against the instructor's actual project if reproducing it exactly.

---

# 27. Why a Multi-row Card Is Used

A Multi-row Card is useful here because the requirement is simply to display a **list of available brands**.

Instead of creating a complicated chart, the Multi-row Card provides a straightforward way for the user to read the available brand names.

The user can scroll through the card if there are more brands than can fit vertically.

---

# 28. Report Design Principle Demonstrated

This lecture also demonstrates an important Power BI report-design principle:

> **The visual should be formatted according to the overall report theme.**

The instructor consistently uses:

* White text
* White borders
* White shadow
* Custom background
* Large fonts

This creates visual consistency between the background and the report content.

At the same time, unnecessary elements such as the Filters pane and card background are removed to keep the page clean.

---

# 29. Complete Step-by-Step Workflow

```text
Start Reporting
      ↓
Return to Power BI Report View
      ↓
Configure Report Page
      ↓
Add Background Image
      ↓
Set Transparency = 0%
      ↓
Canvas Settings
      ↓
Type = Custom
      ↓
Set Canvas Height & Width
      ↓
Customize Wallpaper Color
      ↓
Canvas Background → Image Fit = Fit
      ↓
View → Hide Filters Pane
      ↓
Rename Page 1 → Brands
      ↓
Add Multi-row Card
      ↓
Add Brand field
      ↓
Increase Brand Font Size
      ↓
Change Brand Text Color → White
      ↓
Turn Card Background Off
      ↓
Configure Border
      ↓
Configure Accent Bar
      ↓
Change Brand Font Style → Italic
      ↓
Add White Shadow
      ↓
Add Title → Available Brands
      ↓
Title Size = 60
      ↓
Title = Bold + White
      ↓
Title Alignment = Right
      ↓
Add Outer Border
      ↓
First Report Page Completed
```

# 30. Key Takeaways

1. **Report design starts after data preparation is complete.**
2. A custom image can be used as a **report page background**.
3. **Canvas Settings → Custom** allows you to control the report dimensions.
4. **Image Fit → Fit** helps the background image fit the canvas.
5. The **Filters pane** can be hidden from the View tab when it isn't required.
6. Rename report pages descriptively instead of keeping names such as `Page 1`.
7. A **Multi-row Card** can be used to display a list of categorical values such as brands.
8. The **Format your visual** pane provides extensive control over:

   * Font
   * Font size
   * Text color
   * Background
   * Borders
   * Shadow
   * Title
   * Alignment
9. Temporary/default formatting should be adjusted to match the report's overall theme.
10. The first page is intended as an **overview of the brands available in the dataset** and serves as the starting point for the remaining report pages.
