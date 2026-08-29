# Power BI Inventory Management Project — Detailed Notes

## Part 2: Building the Dashboard with Copilot

This lecture continues from the point where the **Microsoft Fabric capacity has already been created** and demonstrates how to use **Power BI Desktop + Copilot** to build an inventory management report with minimal manual work.

---

# 1. Open Power BI Desktop and Sign In

Once the Fabric capacity is ready:

1. Open **Power BI Desktop**.
2. Sign in using the same organizational/account credentials that were used for the Fabric setup.
3. In the lecture, the instructor signs in using the **SAP Analytics account**.
4. After signing in, create a **Blank Report**.

### Important

Copilot availability depends on the required Copilot settings being enabled in both:

* Microsoft Fabric
* Power BI

If Copilot has been disabled, the Copilot option may still appear in Power BI, but it will be **disabled/unavailable for clicking**.

---

# 2. Create a Workspace in Microsoft Fabric

When Copilot is opened for the first time, it asks you to select a **workspace**.

The instructor initially cannot see any workspace because no workspace was created after creating the Fabric capacity.

Therefore, a workspace needs to be created.

### Steps

1. Open **Microsoft Fabric**.
2. Go to **Workspaces**.
3. Select **Create a workspace** / **New workspace**.
4. Give the workspace a name.

The instructor uses:

> `Fabric Test New`

5. Open the advanced settings/options if required.
6. The workspace initially appears to be in **Pro mode**.
7. Select the appropriate Fabric capacity.
8. Choose the previously created capacity:

> `Test New`

9. Click **Apply**.

The workspace is now associated with the Fabric capacity.

---

# 3. Configure the Copilot Workspace in Power BI

Return to Power BI Desktop.

1. Click **Copilot**.
2. The newly created workspace should now be available.
3. Select:

> `Fabric Test New`

4. Configure/select the workspace.
5. Click **OK**.

Copilot is now ready to work with the report.

At this stage, Copilot is essentially waiting for the dataset/report data.

---

# 4. Import the Inventory Management Dataset

The instructor uses an **Excel workbook** for this project.

However, the lecture points out that the choice of data source is up to you.

You could potentially connect Power BI to:

* Excel
* A database
* Other supported data sources

### Excel Import Steps

1. In Power BI Desktop, select **Excel Workbook**.
2. Navigate to the folder containing the dataset.
3. Select the **Inventory Management** Excel file.
4. Power BI displays a preview/selection window.
5. Multiple sheets are available.
6. Select the required sheets.
7. Select both relevant sheets.
8. Click **Load**.

The dataset contains the sales/inventory information discussed in the previous lecture.

---

# 5. Key Idea — Let Copilot Work With the Data

Once the data has been loaded, the main objective is to leverage Copilot.

The instructor emphasizes that the purpose of this project is to demonstrate how much of the dashboard creation can be automated with AI.

Instead of manually creating every:

* Measure
* Chart
* Page
* Visual
* Summary

you can describe what you want using **natural-language prompts**.

---

# 6. Creating Measures — Traditional DAX vs Copilot

The lecture first demonstrates that you can still use your own **domain knowledge and DAX skills**.

For example, suppose the dataset contains:

> `Cost per Item`

and you want to calculate total cost/value.

You could manually create a DAX measure.

### Example

Conceptually:

```DAX
Total Value Aggregated =
SUM('Inventory Stock Control'[Total Value])
```

The exact table/column names depend on the dataset.

---

# 7. Creating a Measure Manually

The instructor demonstrates the basic process.

Suppose you want a measure for total value.

### Steps

1. Go to the table containing the relevant field.
2. Select **New Measure**.
3. Write the DAX expression.
4. Use `SUM()` to aggregate the required column.
5. Click the checkmark/tick to create the measure.
6. Add the measure to a visual such as a **Card**.

For example:

> `Total Value Aggregated = SUM(Total Value)`

The resulting value can then be displayed in a card.

---

# 8. Using Copilot to Write DAX

Instead of manually writing the DAX expression, Copilot can assist with generating DAX.

### Process

1. Open the DAX-related/Copilot functionality.
2. Describe what you want in natural language.

For example:

> **"I want to find Total Value Aggregated."**

3. Copilot analyzes the available model.
4. It identifies the relevant field.
5. It generates the appropriate DAX expression.

The instructor demonstrates that Copilot can identify the appropriate table/field and generate the `SUM()` calculation.

### Important Concept

Copilot can therefore assist with:

> **Natural-language requirement → DAX expression**

This can be especially useful when you know **what you want to calculate** but aren't completely sure about the exact DAX syntax.

---

# 9. DAX Query View

The lecture also demonstrates **DAX Query View**, described as a newer Power BI feature.

DAX Query View allows you to:

* Write DAX queries
* Execute DAX
* View query output
* Use Copilot to assist with DAX
* Experiment with calculations

If you want to keep a query, you can save/store it.

If you want to execute it:

1. Write the DAX query.
2. Run the query.
3. View the output directly on the screen.

### Key Takeaway

With Copilot + DAX Query View, many DAX-related tasks can be assisted or automated.

---

# 10. Generate a Report Page Using Copilot

Now the main dashboard-building process begins.

Instead of manually deciding what each page should contain, ask Copilot for suggestions.

The instructor uses a prompt similar to:

> **"Suggest me some content for a new report page."**

Copilot generates a suggested report outline.

---

# 11. Copilot's Suggested Report Structure

Copilot suggests multiple potential pages.

The instructor finds that the suggestions are very similar to what a BI professional would traditionally design manually.

Potential pages include:

1. **Inventory Overview**
2. **Sales Performance / Sales Overview**
3. **Inventory Insights**
4. **Customer Insights**
5. **Vendor Performance / Inventory-related analysis**

### Important Observation

Copilot can use the context of the data to suggest meaningful report pages.

This is one of the major benefits demonstrated in the project.

---

# 12. Create an Inventory Overview Page Using a Default Prompt

The instructor first selects the suggested **Inventory Overview** option.

Copilot generates a prompt similar to:

> **"Create a page to display an overview of the current inventory status including stock quantities, total value and reorder levels."**

### Process

1. Select **Inventory Overview**.
2. Review the automatically generated prompt.
3. Select **Create a page**.
4. Copilot analyzes the dataset.
5. Copilot generates the report page and its visuals.

The page is automatically populated.

---

# 13. Create a Custom Report Page Using Your Own Prompt

The instructor then demonstrates a more important feature:

> **Writing your own detailed prompt.**

Instead of accepting Copilot's suggested prompt, you can specify exactly what you want.

For example, the instructor requests a page containing:

### Charts

* Total revenue by date → **Line chart**
* Total quantity sold by warehouse → **Pie chart**
* Profit margins per day
* Total revenue by item name
* Average units sold per month by item name

### Cards/KPIs

The instructor also asks for cards showing:

* Total Revenue
* Total Profit
* Profit Margin
* Average Sales per Day
* Total Quantity Sold
* Total Customers

---

# 14. Why Detailed Prompts Matter

This demonstrates an important principle:

> **Prompt engineering is important when using Copilot.**

The more clearly you specify:

* What you want
* Which metric you need
* Which dimension to use
* What chart type to use
* Which filters/slicers are needed
* How the visual should behave

the better Copilot can understand your requirement.

### General Pattern

Instead of:

> "Create a sales page."

Prefer something like:

> "Create a sales overview page showing total revenue by date in a line chart, quantity sold by warehouse in a pie chart, and cards for total revenue, total profit, profit margin, total quantity sold, and total customers."

---

# 15. Copilot-Generated Sales Overview

Copilot successfully creates a page containing several requested metrics.

The instructor observes metrics such as:

* Total Revenue
* Average Order Quantity
* Sum of Order Quantity
* Total Profit-related information

The instructor considers the generated page quite successful.

### Important

Copilot may not implement **every single requested item exactly as specified**.

Therefore:

> AI-generated reports still need human review and adjustment.

---

# 16. Rename the Page

After generating the page, the instructor realizes that the page is actually more appropriate as a **Sales Overview** rather than an Inventory Overview.

The page is therefore renamed:

> **Sales Overview**

This highlights another important point:

**Copilot can create the initial report, but the user remains responsible for organizing and refining it.**

---

# 17. Create the Inventory Overview Page

The instructor then creates a dedicated inventory page using domain knowledge.

The requested page should show:

### Inventory Information

* Current inventory status
* Stock quantities
* Total inventory value
* Reorder levels

### KPI Cards

The instructor requests metrics such as:

* Inventory Value
* Reorder Products
* Decommissioned Products
* Inventory Restocking Costs
* Total Vendors

---

# 18. Copilot Generates Inventory Visuals

Copilot generates the requested inventory page.

The instructor observes that Copilot has done a good job overall.

However, there is one major design issue:

> **Many of the visuals are bar charts.**

The instructor doesn't want the entire dashboard to consist of bar charts.

This demonstrates that Copilot's output should be treated as a **starting point**, not necessarily the final polished dashboard.

---

# 19. Editing a Copilot-Generated Page

Copilot can also be used to **modify an existing page**.

For example, the instructor asks:

> Edit the inventory overview page.

Then specifies that:

> The "Total Value by Item" chart should be replaced with "Inventory Value by Warehouse" and displayed as a pie chart.

Copilot processes the request and refreshes the page.

### Key Learning

Copilot can assist with both:

* **Creating pages**
* **Editing existing pages**

---

# 20. Vendor Performance Page

The instructor creates another page focused on **Vendor Performance / Vendor Analysis**.

A suggested prompt is:

> **"Create a page to evaluate vendor performance, including cost per item."**

Copilot generates the page.

---

# 21. Adding a Vendor Slicer

The instructor then asks Copilot to modify the vendor page.

Request:

> **"Add a slicer for vendor on the left side of the page."**

The slicer is generated/recognized, but Copilot does not position it exactly as requested.

The instructor observes that it appears at the **top** rather than the left.

### Lesson

Copilot can understand the functional requirement but may not always execute **precise layout/positioning instructions** correctly.

Therefore, manual editing may still be necessary.

---

# 22. Changing Visual Types

The instructor notices that the generated page contains too many bar charts.

A possible prompt is:

> **"Change the graph types because everything has a bar chart."**

Another possible instruction is:

> **"Limit the number of bar charts on this page to one or two."**

### Important Lesson

When a Copilot-generated dashboard doesn't have the desired visual variety, provide more explicit instructions.

However, Copilot may not always be able to perform every formatting/layout modification automatically.

---

# 23. Azure Maps Issue

One of the generated visuals is a **map**, but the map does not work.

The instructor suspects that **Azure Maps** may be disabled.

This leads to an exploration of how Azure Maps can be enabled.

---

# 24. Checking Power BI Settings for Azure Maps

The instructor explores Power BI settings.

A possible path discussed is:

**File → Options and settings → Options → Preview features**

The instructor looks for:

> **Azure Maps Visual**

The exact location can vary depending on the Power BI version and whether the feature is still classified as a preview feature.

### Important

The lecture demonstrates troubleshooting rather than reaching a definitive configuration.

The instructor eventually decides not to spend more time on the map and instead replaces the problematic visual.

---

# 25. Replace the Map With Another Visual

Since the map isn't working, the instructor asks Copilot to replace/change the visual.

This illustrates a practical principle:

> If an AI-generated visual depends on a feature that isn't available, replace it with a supported visual.

---

# 26. Limiting a Visual to Top 5 Vendors

Copilot is unable to perform a particular request to limit the chart to the **top five vendors**.

The instructor therefore demonstrates doing it manually.

Suppose the visual contains:

> Count of Stock Location

You can use the visual's filter functionality.

### Manual Top-N Filtering

1. Select the visual.
2. Open the **Filters** pane.
3. Select the relevant field/measure.
4. Change the filter type to **Top N**.
5. Set the number to:

> **5**

6. Choose the appropriate measure for ranking.
7. Click **Apply filter**.

This produces a visual showing only the top five results.

### Key Lesson

Not every task should be expected to be automated.

A strong Power BI user should know when to:

* Use Copilot
* Use DAX
* Use Power BI's native features
* Manually configure a visual

---

# 27. Customer Insights Page

The instructor then creates another page for:

> **Customer Insights**

This becomes one of the pages in the final report.

The report therefore contains multiple analytical perspectives, including:

* Sales
* Inventory
* Vendors
* Customers

---

# 28. Attempt to Create a Home Page With Copilot

The instructor tries to use Copilot to create a **home page**.

The requested home page should contain:

* A background image
* Four buttons
* Navigation to:

  1. Sales Overview
  2. Inventory Overview
  3. Vendor Performance
  4. Customer Insights

The instructor tries prompts such as:

> **"Create a home page with a background image and four buttons to navigate to these pages."**

Copilot is unable to create the interactive navigation buttons as requested.

### Lesson

Copilot has limitations when dealing with:

* Interactive buttons
* Page navigation
* Precise layout
* Complex formatting

---

# 29. Manually Create the Home Page

Since Copilot cannot create the interactive navigation page, the instructor creates it manually.

### Step 1 — Create a New Blank Page

Create a new page to serve as the:

> **Home Page**

### Step 2 — Add Buttons

Use Power BI's:

* Buttons
* Shapes
* Other interactive elements

to create navigation controls.

The instructor creates four buttons.

---

# 30. Configure Page Navigation Buttons

Each button should navigate to a different report page.

### Example Navigation

| Button    | Destination        |
| --------- | ------------------ |
| Sales     | Sales Overview     |
| Inventory | Inventory Overview |
| Vendor    | Vendor Performance |
| Customer  | Customer Insights  |

### Steps

1. Insert a button.
2. Select the button.
3. Open the **Format** pane.
4. Locate **Action**.
5. Turn on/configure the action.
6. Set the action type to:

> **Page Navigation**

7. Select the destination page.
8. Repeat for the other buttons.

---

# 31. Test Page Navigation

The instructor verifies that the buttons work.

Each button correctly navigates to its intended page.

This demonstrates that Power BI's native page-navigation functionality can easily fill gaps left by Copilot.

---

# 32. Add Text to Buttons

You can add labels to the buttons.

Possible approaches include:

### Method 1

Add text directly to the button.

### Method 2

Create a **Text Box** above/on top of the button.

The instructor mentions that there are multiple ways to achieve this and demonstrates the general concept.

---

# 33. Add a Background Image

The home page can also be visually enhanced by adding a background image.

This is optional and mainly intended to improve the dashboard's appearance.

The instructor deliberately doesn't spend much time on aesthetic formatting because the primary purpose of the project is demonstrating **Copilot functionality**, not detailed dashboard design.

---

# 34. Publish the Power BI Report

Once the report is ready, publish it.

### Steps

1. Save the report.
2. Give it a name such as:

> **Inventory Management Dashboard**

3. Go to the **Home** page.
4. Select **Publish**.
5. Select the target workspace:

> **Test New / Fabric Test New**

6. Start publishing.
7. Wait for the publishing process to complete.

The report should appear in the Fabric workspace.

---

# 35. Refresh Microsoft Fabric

After publishing:

1. Go back to **Microsoft Fabric**.
2. Refresh the Fabric workspace.
3. The newly published report should now be visible.

---

# 36. Important Capacity/Copilot Dependency

The instructor emphasizes that the report's Copilot-related functionality depends on the configured environment.

If you turn off:

* The Fabric capacity
* Copilot

then the associated Copilot functionality/details may no longer be available.

### Important Practical Reminder

Don't leave the Fabric capacity running unnecessarily after completing your practice.

---

# 37. Add a Narrative Using Copilot

One additional feature demonstrated is the **Narrative** capability.

The instructor initially forgets to add this and then creates it.

A narrative can provide a textual summary of the report/data.

### Steps

1. Go to the report.
2. Add/select the **Narrative** functionality.
3. Select the relevant report content/pages.
4. Ask Copilot to create/update the narrative.
5. Wait while Copilot analyzes the selected content.
6. The generated narrative appears on the report.

Because the instructor selected multiple pages, the narrative takes some time to generate.

---

# 38. Narrative as a Summary

The generated narrative can be used as a kind of:

> **Dashboard Summary**

The instructor creates a visual/text label called:

> **Summary**

and places it near the narrative.

The background of the narrative visual can also be modified.

### Example Formatting

1. Select the narrative.
2. Go to formatting/effects.
3. Turn off the background if desired.
4. Adjust the surrounding design.

---

# 39. Narrative Can Be Scoped to Specific Pages

The instructor initially creates a narrative using the entire report.

However, you don't necessarily need to use all pages.

For example, you can create/update a narrative specifically for:

> **Customer Insights**

This means you can control the context used to generate the summary.

---

# 40. Add Back Buttons

The instructor later realizes that the report should have **Back buttons**.

These can be added manually.

### General Process

1. Insert a button.
2. Choose a suitable back-arrow/button style.
3. Configure its action.
4. Set the destination appropriately.
5. Repeat for the relevant pages.

Back buttons can be added to pages such as:

* Inventory Overview
* Vendor Performance
* Customer Insights
* Other report pages

This improves report navigation.

---

# 41. "Ask a Question" / Natural Language Feature

Another feature mentioned near the end is the ability to **ask natural-language questions about the data**.

The instructor clarifies that this is an AI/natural-language feature, although it isn't necessarily the same thing as Copilot.

Users can ask questions such as:

> **"How many vendors do we have?"**

or:

> **"What is the customer type count?"**

Power BI can then attempt to interpret the question and return an appropriate result/visual.

### Key Idea

This provides a natural-language interface for querying the data without manually building the visual first.

---

# 42. Final Dashboard Structure

The final project contains multiple pages.

A possible structure based on the lecture is:

### 1. Home Page

Contains navigation buttons to other pages.

### 2. Sales Overview

Potentially contains:

* Revenue trends
* Quantity sold
* Profit
* Profit margin
* Customer metrics
* Product-level sales analysis

### 3. Inventory Overview

Potentially contains:

* Stock quantity
* Inventory value
* Reorder products
* Decommissioned products
* Restocking costs
* Vendors
* Inventory by warehouse

### 4. Vendor Performance

Potentially contains:

* Vendor performance
* Cost per item
* Stock/location information
* Vendor slicer
* Top vendor analysis

### 5. Customer Insights

Provides customer-related analysis.

### 6. Narrative/Summary

Provides AI-generated textual insights/summaries.

---

# 43. What Copilot Was Able to Do

The project demonstrates that Copilot can assist with:

### Report Planning

* Suggest report pages
* Suggest relevant analytical sections

### Report Creation

* Create new report pages
* Generate visuals
* Add metrics
* Create charts
* Create cards

### DAX

* Generate DAX expressions
* Assist with measures
* Assist with DAX queries

### Editing

* Modify existing report pages
* Replace visual types
* Modify requested visuals

### Narrative

* Generate textual summaries of report information

### Natural Language

* Help users ask questions about their data

---

# 44. What Copilot Could Not Do Reliably

The lecture also demonstrates several limitations.

Copilot may struggle with:

* Precise visual positioning
* Complex page layout
* Creating interactive navigation buttons
* Controlling the exact number/type of charts
* Applying some Top-N filtering requirements
* Certain map/Azure Maps configurations
* Detailed formatting
* Making every requested change exactly as specified

Therefore:

> **Copilot is an assistant, not a complete replacement for Power BI expertise.**

---

# 45. Importance of Prompt Engineering

One of the biggest lessons from this project is:

> **Prompt engineering is extremely important when working with Copilot.**

A vague prompt provides less context.

For example:

> ❌ "Create an inventory page."

is less useful than:

> ✅ "Create an inventory overview page displaying current stock quantities, total inventory value, reorder levels, inventory restocking costs, total vendors, and decommissioned products. Use cards for the KPI metrics and appropriate charts for the remaining analysis."

---

# 46. Give Copilot Context

When writing prompts, clearly specify:

### What

What do you want?

> Inventory overview

### Which Metrics

What should be measured?

> Revenue, profit, inventory value, quantity sold

### Which Dimensions

What should the metrics be broken down by?

> Date, warehouse, vendor, item name

### Which Visual

What type of chart should be used?

> Line chart, pie chart, card, etc.

### Filters

What slicers should be included?

> Vendor slicer

### Layout

Where should something appear?

> Left side, top, etc.

The more relevant context you provide, the more likely Copilot is to produce the desired result.

---

# 47. Human Expertise Is Still Important

The instructor makes an important observation.

Traditionally, BI professionals use their:

* Domain knowledge
* Business understanding
* Data knowledge
* Visualization knowledge
* DAX skills

to build dashboards.

Copilot can automate a large portion of this work, but **human judgment is still required**.

You still need to:

* Validate metrics
* Check calculations
* Review charts
* Fix incorrect visuals
* Improve layout
* Apply filters
* Correct formatting
* Ensure business relevance
* Test navigation
* Review AI-generated insights

---

# 48. AI + Power BI Workflow

The project demonstrates a hybrid workflow:

**Load Data**
↓
**Connect Power BI to Dataset**
↓
**Copilot Understands Data**
↓
**Ask Copilot for Report Suggestions**
↓
**Generate Report Pages**
↓
**Generate DAX / Measures When Needed**
↓
**Modify Pages Using Prompts**
↓
**Manually Fix Anything Copilot Cannot Do**
↓
**Add Navigation & Formatting**
↓
**Add AI Narrative**
↓
**Test Report**
↓
**Publish to Fabric**
↓
**Review Final Dashboard**

---

# 49. Important Practical Workflow to Follow

When doing this project yourself, a good sequence is:

### Phase 1 — Setup

1. Ensure organizational account is available.
2. Ensure Fabric capacity is created.
3. Ensure Copilot is enabled.
4. Open Power BI Desktop.
5. Sign in.

### Phase 2 — Workspace

6. Create a Fabric workspace.
7. Assign the correct Fabric capacity.
8. Select the workspace in Copilot.

### Phase 3 — Data

9. Connect the Inventory Management Excel file.
10. Load the required sheets.
11. Verify that the tables/fields are available.

### Phase 4 — AI-Assisted Analysis

12. Ask Copilot for suggested report pages.
13. Review its suggestions.
14. Create the Sales Overview.
15. Create the Inventory Overview.
16. Create Vendor Performance.
17. Create Customer Insights.

### Phase 5 — Refinement

18. Ask Copilot to modify visuals.
19. Change chart types.
20. Add/modify slicers.
21. Manually perform Top-N filters where necessary.
22. Fix unsupported visuals such as problematic maps.
23. Adjust formatting manually.

### Phase 6 — Navigation

24. Create a Home page.
25. Add navigation buttons.
26. Configure Page Navigation actions.
27. Add text labels.
28. Add a background image if desired.
29. Add Back buttons to report pages.

### Phase 7 — AI Summary

30. Add a Copilot Narrative.
31. Generate the report summary.
32. Adjust its formatting.
33. Scope the narrative to relevant pages if required.

### Phase 8 — Finalization

34. Test all visuals.
35. Test slicers.
36. Test navigation buttons.
37. Verify metrics.
38. Save the report.
39. Publish it to the Fabric workspace.
40. Refresh Fabric and verify the published report.
41. After finishing the project, turn off/delete the capacity as appropriate to avoid unnecessary costs.

---

# 50. Key Takeaways for Revision

### Copilot

* Can generate report pages.
* Can suggest dashboard structures.
* Can create visuals based on natural-language prompts.
* Can modify existing pages.
* Can generate DAX.
* Can assist with DAX Query View.
* Can generate narratives.
* Can assist with natural-language questions.

### Power BI

* Still provides all the manual controls required to refine the report.
* Can be used when Copilot cannot complete a task.
* Supports manual filters, page navigation, buttons, formatting, etc.

### Prompt Engineering

* Clear prompts produce better results.
* Include metrics, dimensions, chart types, filters and requirements.
* Don't expect every instruction to be followed perfectly.

### Human + AI

The best approach demonstrated by the project is:

> **Use Copilot for speed and automation, and use your Power BI/domain expertise for validation, correction, and final design.**

### Final Principle

**Don't try to automate 100% of the dashboard.**

Instead:

> **Let Copilot handle repetitive/complex initial work → review the output → manually refine what is necessary → publish a business-ready dashboard.**
