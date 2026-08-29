# Power BI — Creating Bottom 5 Brands by Average Profit Percentage & Publishing the Report

This session covers the **final visual** for the report page and then demonstrates how to **publish the completed Power BI report to Power BI Service**.

The major topics covered are:

1. Formatting the data labels of the previous chart
2. Creating a **Pie Chart** for the Bottom 5 Brands
3. Configuring **Brand** and **Profit Percentage**
4. Changing aggregations from **Sum → Average**
5. Applying a **Bottom N filter**
6. Using **Format Painter**
7. Formatting pie-chart detail labels
8. Removing the filter pane from the report view
9. Changing the chart title
10. Reviewing the two report pages
11. Publishing the `.pbix` report to Power BI Service
12. Opening and editing the published report

---

# 1. Modify the Data Label Color of the Previous Chart

Before creating the final visual, the instructor makes a small formatting change to the chart created in the previous session.

### Objective

Change the **data label color** so that it matches the color/theme being used in the report.

### Steps

1. Click the chart created in the previous session.

2. Open the **Visualizations** pane.

3. Click:

   **Format your visual**

4. Scroll down.

5. Expand:

   **Data labels**

6. Scroll further down.

7. Under **Values**, locate the **Color** option.

8. Click **More colors**.

The instructor then gets the required color from an Excel sheet.

### Getting the color from Excel

1. Open the Excel sheet containing the report's color/theme references.
2. Go to the **Color Visual** slide/section.
3. Copy the required color.
4. Return to Power BI Desktop.
5. Paste/select the copied color in the color selector.

This ensures that the data labels use the desired report color.

### Save the change

Press:

**Ctrl + S**

---

# 2. Create the Final Visual — Bottom 5 Brands

The final visual that needs to be added to the report is:

> **Bottom 5 Brands by Average Profit Percentage**

Another way of describing the requirement is:

> **Bottom 5 Brands by Lowest Average Profit Percentage**

This visual will show the brands having the **lowest average profit percentage**.

---

# 3. Add a Pie Chart

The instructor chooses a **Pie Chart** to represent the Bottom 5 brands.

### Steps

1. Click on a **blank area of the report canvas**.
2. In the Visualizations pane, select:

   **Pie Chart**

Power BI creates a blank pie chart.

3. Resize the pie chart according to the available space on the report page.

---

# 4. Add Brand to the Pie Chart

The first field required is **Brand**.

### Steps

1. Expand the **Data pane**.
2. Locate the **Brand** field.
3. Double-click **Brand** or drag and drop it into:

   **Legend**

The different brands will now form the categories/slices of the pie chart.

---

# 5. Add Profit Percentage to Values

Next, Profit Percentage needs to be used as the numerical value of each slice.

### Steps

1. Locate **Profit Percentage** in the Data pane.
2. Double-click it or drag and drop it into:

   **Values**

### Default aggregation

Power BI will initially use:

> **Sum of Profit Percentage**

But this is not the required calculation.

The requirement is:

> **Average Profit Percentage**

---

# 6. Change Profit Percentage from Sum to Average

### Steps

1. Click the dropdown next to **Profit Percentage** under the Values bucket.
2. Change the aggregation from:

**Sum → Average**

The pie chart now represents:

> **Average Profit Percentage by Brand**

---

# 7. Add Brand to Visual-Level Filters

Now we need to display only the **bottom five brands**.

### Steps

1. Expand the **Filters pane**.
2. From the Data pane, find **Brand**.
3. Double-click Brand or drag and drop it into:

   **Filters on this visual**

This creates a visual-level Brand filter.

---

# 8. Change Basic Filtering to Top N / Bottom N

The instructor now changes the filtering method.

### Steps

Under the Brand filter:

1. Click:

   **Basic filtering**

2. Change it to:

   **Top N**

Although Power BI labels the filtering category as **Top N**, it allows us to choose whether we want the **Top** or **Bottom** values.

3. Change:

   **Top → Bottom**

This is important because our requirement is to find the brands with the **lowest average profit percentage**.

4. Enter:

   **5**

Therefore, the filter becomes:

> **Bottom 5**

---

# 9. Add Profit Percentage to "By Value"

The Bottom N filter needs a measure based on which Power BI can determine the lowest five brands.

Therefore, **Profit Percentage** is added to the **By value** bucket.

### Steps

1. From the Data pane, select **Profit Percentage**.
2. Drag and drop it into:

   **By value**

### Default aggregation

Again, Power BI initially chooses:

> **Sum of Profit Percentage**

But we need:

> **Average Profit Percentage**

---

# 10. Change By Value from Sum to Average

### Steps

1. Click the dropdown next to Profit Percentage under **By value**.
2. Change:

**Sum → Average**

Now the Bottom N filter is based on **Average Profit Percentage**.

### Final filter configuration

The configuration is effectively:

| Setting      | Value             |
| ------------ | ----------------- |
| Filter field | Brand             |
| Filter type  | Top N             |
| Direction    | Bottom            |
| N            | 5                 |
| By value     | Profit Percentage |
| Aggregation  | Average           |

3. Click:

   **Apply filter**

Power BI now displays only the **five brands with the lowest average profit percentage**.

---

# 11. Understand the Logic of the Bottom 5 Filter

The chart is not simply showing five randomly selected brands.

The process is:

**Brand**

→ Calculate **Average Profit Percentage**

→ Rank all brands

→ Select the **5 lowest**

→ Display those five brands in the pie chart.

Therefore, the visual answers:

> **Which five brands have the lowest average profit percentage?**

---

# 12. Use Format Painter to Copy Formatting

The instructor now wants the newly created pie chart to have formatting consistent with another visual.

Instead of manually repeating all formatting settings, **Format Painter** is used.

### Steps

1. Collapse:

   * Filters pane
   * Visualizations pane
   * Data pane

2. Click the **first bar chart** that was created.

3. Go to the:

   **Home** tab.

4. Click:

   **Format Painter**

5. Now click the newly created **pie chart/circle graph**.

Power BI copies the formatting from the first bar chart to the pie chart.

### Why use Format Painter?

Format Painter helps maintain a consistent report design without manually configuring every formatting property.

It can copy things such as visual formatting/theme-related properties from one visual to another.

---

# 13. Further Format the Pie Chart

If additional formatting is required, select the pie chart.

### Steps

1. Click the pie chart.

2. Expand the **Visualizations** pane.

3. Click:

   **Format your visual**

4. Locate:

   **Data labels**

---

# 14. Configure Detail Labels

The instructor observes that not all desired information is currently being displayed in the pie-chart labels.

Under the data-label settings, locate:

> **Label contents**

The instructor changes the label contents so that all details are shown.

### Steps

1. Under **Label contents**, click:

   **All detail labels**

This allows all available detail information to be represented in the data labels.

---

# 15. Turn Legends Off

Because the required information is already being represented through the detailed labels, the separate legend is not required.

### Steps

1. Locate the **Legend** setting.
2. Change it to:

   **Off**

This removes the separate legend from the visual.

---

# 16. Remove the Filter Pane from the Report View

The instructor then cleans up the report interface.

### Steps

1. Collapse the Visualizations pane.

2. Go to the:

   **View** tab.

3. The **Filters pane** is not required in the visible report layout.

4. Remove/hide the Filters pane from the report view.

This gives the report a cleaner presentation when it is being viewed.

---

# 17. Reduce the Pie Chart Data Label Size

Before finalizing the report, the instructor notices that the data labels are somewhat large.

### Steps

1. Select the pie chart.

2. Expand the **Visualizations** pane.

3. Click:

   **Format your visual**

4. Go to:

   **Detail labels**

5. Under **Values**, locate the label size.

The current size is:

> **55**

Reduce it to:

> **45**

The instructor then decides that a slightly larger size looks better and changes it to:

> **48**

So the final selected size is approximately **48**.

---

# 18. Change the Pie Chart Title

The instructor initially forgets to change the title and then corrects it.

### Steps

1. Select the pie chart.

2. Open:

   **Format your visual**

3. Go to:

   **General → Title**

4. Change the title to:

> **Bottom Five Brands by Average Profit Percentage**

This provides a clear description of what the visual represents.

---

# 19. Finalize the Visual

After changing the title:

1. Collapse the **Title** section.
2. Collapse the **Visualizations pane**.
3. Click on a blank area of the canvas.

The visual is now finalized.

---

# 20. Review the Complete Report

The instructor then reviews the complete Power BI report.

The report consists of:

> **Two pages**

### Page 1 — Brands

Click on the first page:

> **Brands**

This is the first report page created during the project.

It contains the various brand-related visuals created throughout the sessions.

---

### Page 2 — Details

Click on:

> **Details page**

This is the second report page created as part of the report.

The instructor confirms that both pages are present and part of the final report.

---

# 21. Publishing the Report to Power BI Service

After completing the report, the instructor explains that it can now be published to **Power BI Service**.

### Important prerequisite

Before publishing, you should be:

> **Signed in to your Power BI account**

This is required to publish the `.pbix` report to Power BI Service.

---

# 22. Important Note About AppSource Visuals

The instructor also highlights an important point from the previous projects:

> When using visuals from **AppSource**, you must be signed in to your Power BI account.

So if you are working with custom/AppSource visuals, make sure your Power BI account is properly signed in.

---

# 23. Publish the Power BI Report

### Steps

1. Go to the:

   **Home** tab.

2. Click:

   **Publish**

Power BI may ask you to save changes.

3. Select:

   **Save changes**

The publishing process will begin.

Depending on the report and connection, publishing may take some time.

---

# 24. Select the Workspace

After choosing Publish, Power BI asks where the report should be published.

The instructor chooses:

> **My workspace**

### Steps

1. Select:

   **My workspace**

2. Click:

   **Select**

The `.pbix` Power BI report is now published to Power BI Service.

---

# 25. What Does Publishing Mean?

The instructor explains that publishing essentially means:

> Publishing your Power BI `.pbix` report to Power BI Service.

The report created in **Power BI Desktop** is uploaded to the selected workspace in **Power BI Service**.

In this case:

**Power BI Desktop**

↓

**Publish**

↓

**My Workspace**

↓

**Power BI Service**

---

# 26. Open the Published Report in Power BI Service

After publishing, the instructor opens the report in Power BI Service.

### Steps

1. Open the published Power BI report.
2. Wait for Power BI Service to load the report.

The report appears in Power BI Service with its two pages.

---

# 27. View the Report Pages in Power BI Service

The instructor confirms that the published report contains the same two pages.

The page navigation can be expanded/collapsed as required.

### Page structure

The report contains:

1. **Brands**
2. **Details page**

The instructor expands the page navigation to view the pages and then collapses it again.

---

# 28. Edit the Published Report

Power BI Service also provides an option to make changes to the report.

If you need to modify the published report:

1. Click:

   **Edit**

2. Make the required changes.

This allows you to modify the report in Power BI Service where supported.

---

# 29. Complete Process — End-to-End

The complete workflow demonstrated in this session can be summarized as:

### Part 1 — Modify Previous Visual

**Select previous chart**

→ Visualizations

→ Format your visual

→ Data labels

→ Values

→ Color

→ More colors

→ Copy desired color from Excel

→ Apply color

→ `Ctrl + S`

---

### Part 2 — Create Bottom 5 Pie Chart

**Blank canvas**

→ Pie Chart

→ Add **Brand → Legend**

→ Add **Profit Percentage → Values**

→ Change **Sum → Average**

→ Add **Brand → Filters on this visual**

→ Basic filtering → Top N

→ Top → **Bottom**

→ Enter **5**

→ Add **Profit Percentage → By value**

→ Change **Sum → Average**

→ **Apply filter**

---

### Part 3 — Format the Pie Chart

**Select pie chart**

→ Format your visual

→ Data labels

→ Label contents → **All detail labels**

→ Legend → **Off**

→ Detail labels → Values

→ Change size:

**55 → 45 → 48**

→ General

→ Title

→ **Bottom Five Brands by Average Profit Percentage**

---

### Part 4 — Apply Existing Formatting

**Select first bar chart**

→ Home

→ **Format Painter**

→ Click pie chart

This transfers the formatting from the bar chart to the pie chart.

---

### Part 5 — Clean the Report

Collapse panes

→ View

→ Remove/hide Filters pane

→ Review **Brands** page

→ Review **Details** page

---

### Part 6 — Publish

**Home**

→ **Publish**

→ Save changes if prompted

→ **My workspace**

→ **Select**

→ Wait for publishing

→ Open report in Power BI Service

→ Review two pages

→ Use **Edit** if changes are required

---

# 30. Key Power BI Concepts from This Session

## 30.1 Bottom N Filtering

The key concept in this session is **Bottom N filtering**.

If you want the lowest-performing categories, you can use:

**Filters on this visual → Top N → Bottom → N**

For example:

* Bottom 5 brands by average profit
* Bottom 10 products by sales
* Bottom 3 regions by revenue

---

## 30.2 Top N vs Bottom N

The same Top N filter interface can be used for both directions.

### Top 5

Select:

**Top → 5**

This gives the five highest values.

### Bottom 5

Select:

**Bottom → 5**

This gives the five lowest values.

In this session, we use:

> **Bottom → 5**

because the requirement is to find the brands with the lowest average profit percentage.

---

# 31. Why Profit Percentage Is Added Twice

Just like the previous Top 5 visual, **Profit Percentage is used in two different places**.

### Values

Used to determine what the pie-chart slices represent.

> **Average Profit Percentage**

### By value

Used by the Bottom N filter to determine which five brands should be selected.

> **Average Profit Percentage**

Both need to use **Average**, otherwise the visual and ranking could be based on different calculations.

---

# 32. Format Painter — Important Concept

**Format Painter** is particularly useful when you have multiple visuals that should have a consistent design.

Instead of manually configuring:

* Fonts
* Labels
* Titles
* Background-related formatting
* Other visual formatting

you can copy formatting from an existing visual.

### Workflow

**Source visual**

→ Format Painter

→ **Target visual**

In this session:

**First bar chart**

→ Format Painter

→ **Bottom 5 pie chart**

---

# 33. Power BI Desktop vs Power BI Service

This session also establishes the distinction between the two environments.

| Power BI Desktop             | Power BI Service                           |
| ---------------------------- | ------------------------------------------ |
| Used to create reports       | Used to access published reports           |
| Used for data modeling       | Used for sharing/collaboration             |
| Used for DAX development     | Used for online report consumption         |
| Used to design visuals       | Reports can be viewed online               |
| `.pbix` file is created here | Published report is available here         |
| Can publish reports          | Can edit published reports where supported |

The workflow is:

> **Develop in Power BI Desktop → Publish → Power BI Service**

---

# 34. Final Report Structure

After completing this session, the report contains **two pages**:

### Page 1 — Brands

Contains the brand-focused analysis and visuals, including the previously created visuals such as:

* Top-performing brand analysis
* Top 5 brands
* Bottom 5 brands
* Other brand-related visuals created in earlier sessions

### Page 2 — Details

Contains the detailed analysis created during the earlier sessions.

---

# 35. Important Takeaways

* Use a **Pie Chart** when you want to represent category contributions as slices.
* Add **Brand** to **Legend** to create the categories.
* Add **Profit Percentage** to **Values** to determine the numerical values.
* Always verify Power BI's automatically selected aggregation.
* Change **Sum → Average** when the business requirement is average profit percentage.
* Use **Top N → Bottom → 5** to identify the five lowest-performing brands.
* Add the ranking metric to **By value**.
* Click **Apply filter** after configuring the Bottom N filter.
* **Format Painter** helps maintain consistent formatting between visuals.
* Use **All detail labels** when more information needs to be displayed directly on a pie chart.
* Turn **Legend Off** when the labels already provide the necessary category information.
* Adjust label size for readability; in this example, it was changed from **55 → 45 → 48**.
* Give every visual a meaningful title.
* Save the report using **Ctrl + S**.
* Before publishing, ensure that you are **signed in to your Power BI account**.
* AppSource visuals also require you to be signed in.
* Use **Home → Publish** to publish the `.pbix` report.
* Select the desired workspace, such as **My workspace**.
* After publishing, open the report in **Power BI Service**.
* The published report retains its report pages.
* Use **Edit** in Power BI Service when you need to make supported modifications.

### Most important business logic

The two complementary visuals created across these sessions are:

**Top 5 Brands by Average Profit Percentage**
→ identifies the brands with the **highest average profit percentage**

**Bottom 5 Brands by Average Profit Percentage**
→ identifies the brands with the **lowest average profit percentage**

Together, they provide a quick view of the best- and worst-performing brands based on average profitability.
