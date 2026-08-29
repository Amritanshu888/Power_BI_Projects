# Power BI – Report Page 2: Details Page & Scroller Visual

## 1. Objective of the Session

In the previous session, the **first report page** was created to provide an overview of the available brands.

In this session, the focus is on creating the **second report page**, named **Details**.

The main tasks are:

* Create a second report page.
* Rename it to **Details**.
* Customize the canvas size.
* Add a background image.
* Customize the wallpaper color.
* Hide the Filters pane.
* Import a **Scroller** visual from AppSource.
* Display the company/brand information using the scroller.
* Add custom text to the scroller.
* Customize its font, background, border, shadow, and scrolling speed.
* Make the background image fit the entire canvas.

---

# 2. Create the Second Report Page

To create a new page:

1. Go to the bottom of the Power BI report.
2. Click the **+ (Plus)** icon.
3. Power BI creates a new report page.

The new page is initially named something like:

> **Page 1**

---

# 3. Rename the Page

The new page is intended to contain detailed information, so it should be renamed.

### Steps

1. Double-click the newly created page name.
2. Rename it to:

**Details**

The report now has:

* First page → **Brands**
* Second page → **Details**

---

# 4. Configure the Canvas Settings

The instructor now customizes the size of the Details page.

### Steps

1. Expand the **Visualizations** pane.
2. Locate **Canvas Settings**.
3. Click **Canvas Settings**.
4. The default Type is:

**16:9**

5. Click the **Type** dropdown.
6. Change it to:

**Custom**

7. Set the dimensions to:

* **Height:** `3456`
* **Width:** `6912`

The custom canvas dimensions are now configured.

---

# 5. Add a Background Image

The Details page will also use a custom background image.

### Steps

1. Collapse **Canvas Settings**.
2. Open **Canvas Background**.
3. Locate the option to add an image.
4. Click **Browse**.
5. Select the image named/used for **Page 2**.

The instructor mentions that this image will be provided in the **resource section** of the course.

> The lecture also notes that the other resources used in the lectures are available in the resource section.

---

# 6. Set Background Transparency

After adding the image:

1. Locate the **Transparency** setting.
2. Set it to:

**0%**

This makes the background image fully visible.

---

# 7. Customize the Wallpaper Color

The wallpaper surrounding the report canvas is also customized.

### Steps

1. Collapse **Canvas Background**.
2. Expand **Wallpaper**.
3. Click **Color**.
4. Click **More Colors**.
5. Enter the color code:

```text id="e5l1g3"
182849
```

This becomes the wallpaper color for the Details page.

---

# 8. Hide the Filters Pane

The Filters pane is not required for the current page.

### Steps

1. Go to the **View** tab.
2. Click **Filters**.
3. This hides/removes the Filters pane from the report workspace.

This provides more space for designing the report.

---

# 9. Requirement: Add a Company/Brand Scroller

The instructor now wants to add a **scrolling text visual** near the top of the report.

The purpose is to display the company/brand information for which the report is being created.

The scroller will act as a dynamic header/banner.

For example, the scroller can display:

> **Inside BI Solutions Private Limited**

The important point is that this is not a standard Power BI visual available by default.

Therefore, the visual must be imported from **Power BI AppSource**.

---

# 10. Open Get More Visuals

### Steps

1. Expand the **Visualizations** pane.
2. Click **Add Data to Your Visual** / the option for adding visuals.
3. Click the **three dots (...)** in the Visualizations pane.
4. Select:

**Get more visuals**

This opens the additional visual marketplace/AppSource area.

---

# 11. Search for the Scroller Visual

The instructor searches for a **Scroller** visual because it is not available among the default Power BI visuals.

### Steps

1. In the additional visuals/AppSource window, search for:

**Scroller**

2. Locate the appropriate scroller visual.
3. Select the first relevant scroller visual shown in the lecture.
4. Click **Add**.
5. Wait while Power BI imports the visual.
6. Once successfully imported, click **OK**.

The Scroller visual is now available in the Visualizations pane.

---

# 12. Add the Scroller to the Page

After importing the visual:

1. Locate the newly added **Scroller** icon in the Visualizations pane.
2. Click the Scroller visual.
3. Power BI creates a blank Scroller on the Details page.
4. Resize it as necessary.
5. Position it near the top of the report page.

The scroller will serve as a dynamic scrolling company-information banner.

---

# 13. Add Brand to the Scroller

The instructor wants to use information from the dataset in the scroller.

### Steps

1. Select the Scroller.
2. Expand the **Data pane**.
3. Expand the **T Shirt** table.
4. Select/drag the **Brand** field into the Scroller.

The brand information is now associated with the scrolling visual.

---

# 14. Add Custom Text

The Scroller also allows custom text to be displayed.

The instructor enters:

> **Inside BI Solutions Private Limited**

This is the company information that will be displayed through the scrolling visual.

The exact text in the lecture is:

**Inside BI Solutions Private Limited**

---

# 15. Enable Auto Size Font

The instructor wants the text to automatically adjust its font size to fit the available space.

### Steps

1. Select the Scroller.
2. Open **Format your visual**.
3. Locate the relevant text/font settings.
4. Find:

**Auto Size Font**

5. Turn it **On**.

This allows the scroller to automatically size its text appropriately.

---

# 16. Turn Off the Scroller Title

The instructor does not want a separate title displayed above the scroller.

### Steps

1. Select the Scroller.
2. Go to:

**General → Title**

3. Turn the **Title** option:

**Off**

This leaves only the scrolling content without an additional visual title.

---

# 17. Remove the Visual Background

The instructor also wants the scroller itself to blend into the report design rather than having a separate background.

### Steps

1. Select the Scroller.
2. Go to:

**General → Effects**

3. Locate **Background**.
4. Turn the background:

**Off**

---

# 18. Customize the Scroller Background Color

Although the general visual background is turned off, the Scroller's own visual formatting contains another background color option.

The instructor changes this to match the wallpaper.

### Steps

1. Select the Scroller.
2. Open **Format your visual**.
3. Go to the **Visual** formatting options.
4. Locate **Background Color**.
5. Click the color selector.
6. Select **More Colors**.
7. Use the same wallpaper color:

```text id="zqhj6c"
182849
```

This makes the Scroller visually consistent with the page's wallpaper.

---

# 19. Adjust the Scroller Scroll Speed

The Scroller's movement speed can be customized.

### Steps

1. Select the Scroller.
2. Open **Format your visual**.
3. Locate the **Scroller** settings.
4. Find the **Scroll Speed** option.
5. Adjust the value according to the desired speed.

The instructor gives an example of setting the speed to:

**5**

A higher scroll speed makes the company name move faster.

---

# 20. Scroller as a Dynamic Header

The instructor explains that in earlier projects, a **static shape** was generally used at the top of the report to display headings or other information.

However, a Scroller can be used instead.

### Traditional approach

```text
Static Shape
      ↓
Heading/Text
```

### Approach used here

```text
Scroller Visual
      ↓
Scrolling Company Information
```

This gives the report a more dynamic appearance.

---

# 21. Add a Border to the Scroller

The instructor then demonstrates how to add a border around the Scroller.

### Steps

1. Select the Scroller.
2. Open:

**Format your visual → General → Effects**

3. Locate **Border**.
4. Turn the border:

**On**

5. Click the border **Color**.
6. Click **More Colors**.
7. Select the desired custom color from the provided Excel color reference.

The instructor mentions using a color copied from an **Excel sheet** containing the project's color codes.

---

# 22. Using an Excel Sheet for Color Codes

The lecture repeatedly refers to an Excel sheet containing color codes.

The workflow is:

1. Open the Excel sheet.
2. Locate the required color code.
3. Copy the code.
4. Return to Power BI Desktop.
5. Open the appropriate color selector.
6. Paste the color code.
7. Apply it.

This allows consistent colors to be used throughout the report.

---

# 23. Add a Shadow to the Scroller

A shadow is also added to improve the appearance of the visual.

### Steps

1. Select the Scroller.
2. Open:

**Format your visual → General → Effects**

3. Locate **Shadow**.
4. Turn Shadow **On**.
5. Click the shadow color.
6. The default color is black.
7. Change it to the same/custom color selected from the Excel color reference.

---

# 24. Configure Shadow Position

The shadow's position can also be customized.

The available settings allow you to decide where the shadow appears, such as:

* Outside
* Inside
* Bottom
* Right

The instructor leaves the settings at their current/default configuration.

The important point is that Power BI provides control over the shadow position.

---

# 25. Make the Background Image Fit the Canvas

The instructor notices that the background image can be improved further by changing its image-fit setting.

### Steps

1. Click on a blank area of the report canvas.
2. Make sure the **report page** itself is selected rather than the Scroller.
3. Open **Format your report page**.
4. Go to:

**Canvas Background**

5. Locate **Image Fit**.
6. Change:

**Normal → Fit**

The background image now fits the entire report canvas more appropriately.

---

# 26. Final Details Page Structure

The page now contains the basic foundation for the Details report page:

```text
┌─────────────────────────────────────────────┐
│                                             │
│     Scrolling Company Information           │
│     Inside BI Solutions Private Limited     │
│                                             │
│                                             │
│                                             │
│              Details Page                  │
│                                             │
│          Other visuals will be added        │
│          in upcoming sessions               │
│                                             │
└─────────────────────────────────────────────┘
```

The remaining report visuals will be added in subsequent sessions.

---

# 27. Formatting Summary

| Element                 | Setting                             |
| ----------------------- | ----------------------------------- |
| Page Name               | Details                             |
| Canvas Type             | Custom                              |
| Canvas Height           | 3456                                |
| Canvas Width            | 6912                                |
| Background              | Page 2 image                        |
| Background Transparency | 0%                                  |
| Wallpaper Color         | `182849`                            |
| Filters Pane            | Hidden                              |
| Additional Visual       | Scroller                            |
| Scroller Source         | Power BI AppSource                  |
| Data Field              | Brand                               |
| Custom Text             | Inside BI Solutions Private Limited |
| Auto Size Font          | On                                  |
| Visual Title            | Off                                 |
| General Background      | Off                                 |
| Visual Background Color | `182849`                            |
| Scroll Speed            | Example: 5                          |
| Border                  | On                                  |
| Border Color            | Custom color from Excel reference   |
| Shadow                  | On                                  |
| Shadow Color            | Custom color from Excel reference   |
| Shadow Position         | Default/current settings            |
| Background Image Fit    | Fit                                 |

---

# 28. Complete Step-by-Step Workflow

```text
Create New Page
      ↓
Rename Page → Details
      ↓
Open Visualizations
      ↓
Canvas Settings
      ↓
Type → Custom
      ↓
Height = 3456
Width = 6912
      ↓
Canvas Background
      ↓
Browse → Select Page 2 Image
      ↓
Transparency = 0%
      ↓
Wallpaper
      ↓
Color → More Colors
      ↓
Enter 182849
      ↓
View → Filters → Hide
      ↓
Get More Visuals (...)
      ↓
Search → Scroller
      ↓
Select Scroller
      ↓
Add
      ↓
OK
      ↓
Add Scroller to Canvas
      ↓
Add Brand Data
      ↓
Enter Custom Text
"Inside BI Solutions Private Limited"
      ↓
Auto Size Font → On
      ↓
General → Title → Off
      ↓
General → Effects → Background → Off
      ↓
Visual → Background Color → 182849
      ↓
Adjust Scroll Speed
      ↓
General → Effects → Border → On
      ↓
Customize Border Color
      ↓
General → Effects → Shadow → On
      ↓
Customize Shadow Color
      ↓
Select Blank Canvas
      ↓
Format Report Page
      ↓
Canvas Background
      ↓
Image Fit → Fit
      ↓
Details Page Foundation Completed
```

# 29. Important Concepts to Remember

### Power BI AppSource Visuals

Not every visual is available by default in Power BI.

Additional visuals can be imported using:

**Visualizations → (...) → Get more visuals**

The Scroller used in this lecture is an example of an **AppSource/custom visual**.

---

### Scroller vs. Static Shape

A normal shape can be used for a static heading.

A Scroller can be used when you want text/information to move dynamically across the report.

This can make the report header more interactive and visually appealing.

---

### General vs. Visual Formatting

The lecture demonstrates that Power BI may provide formatting controls at different levels.

For example:

**General → Effects**

* Background
* Border
* Shadow

while the visual-specific **Visual** settings can contain additional options such as:

* Background color
* Scrolling behavior
* Font settings

Understanding this distinction helps when a formatting option isn't found immediately.

---

### Page Background vs. Wallpaper

These are different:

**Canvas Background**

* Controls the background of the report canvas.
* Can contain an image.

**Wallpaper**

* Controls the area surrounding the report canvas.
* Can have its own color.

Both can therefore be customized separately.

---

# 30. Key Takeaway

The major focus of this session is learning how to **create and format a second Power BI report page and use an AppSource Scroller visual as a dynamic company-information header**.

The workflow is:

> **Create Details page → Customize canvas → Add background → Customize wallpaper → Hide Filters → Import Scroller → Add Brand data/custom text → Format Scroller → Add border/shadow → Fit background image**

This establishes the basic layout of the **Details** page. The next sessions will build additional analytical visuals on top of this formatted page.
