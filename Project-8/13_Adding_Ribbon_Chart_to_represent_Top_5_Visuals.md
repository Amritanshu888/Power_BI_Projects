# Steps: Create a Ribbon Chart for Top 5 Brands by Number of Varieties

## 1. Copy the Existing Bar Chart

1. Select the existing **bar chart**.
2. Press **Ctrl + C**.
3. Press **Ctrl + V**.
4. Move the copied chart to the desired position.
5. Resize it as required.

---

## 2. Remove the Existing Visual-Level Filter

Since the copied chart inherits the filters from the original chart:

1. Select the copied chart.
2. Open the **Filters pane**.
3. Remove the existing **visual-level filter** from this copied chart.

---

## 3. Remove the Existing Fields

Open the **Visualizations pane**.

From the copied chart, remove the fields that belonged to the previous visualization:

* Remove **Brand** from the **Y-axis**.
* Remove **Average Discount Percentage** from the **X-axis**.

Now the chart is ready for the new configuration.

---

# 4. Add Brand to the Axis

For a Ribbon Chart, **Brand** will be the category being ranked.

1. Open the **Data pane**.
2. Find **Brand**.
3. Drag **Brand** into the **X-axis** bucket.

> **Important:** Unlike the previous bar chart, the Ribbon Chart uses a category axis differently. For this analysis, Brand should be used as the categorical axis.

---

# 5. Add Title and Count Varieties

Now we need to calculate the number of varieties for each brand.

1. Find the **Title** column in the Data pane.
2. Drag **Title** into the **Y-axis** bucket.
3. Click the dropdown beside **Title**.
4. Change the aggregation from **Count** to:

**Distinct count**

So the configuration is approximately:

| Bucket | Field                  |
| ------ | ---------------------- |
| X-axis | Brand                  |
| Y-axis | Title → Distinct Count |

This gives you the **number of unique varieties/titles for each brand**.

---

# 6. Apply a Top 5 Filter

Now we only want the five brands with the highest number of varieties.

1. Select the Ribbon Chart.
2. Open the **Filters pane**.
3. From the Data pane, drag **Brand** into:

**Filters on this visual**

4. Click the filter type currently showing **Basic filtering**.
5. Change it to **Top N / Top**.
6. Enter:

**Top 5**

---

# 7. Tell Power BI What "Top 5" Means

The Top 5 needs to be determined according to the **distinct count of Title**.

1. In the Top N filter, locate the **By value** / **Add data fields here** section.
2. Drag **Title** into that section.
3. Open the dropdown for Title.
4. Select:

**Distinct count**

5. Click:

**Apply filter**

Now Power BI will show only:

> **The 5 brands having the highest number of distinct varieties/titles.**

---

# 8. Convert the Visual to a Ribbon Chart

Once the fields and Top 5 filter are configured:

1. Select the chart.
2. Go to the **Visualizations pane**.
3. Select **Ribbon Chart**.

Power BI will convert the visual into a Ribbon Chart.

---

# 9. Understand What the Ribbon Chart Shows

The Ribbon Chart is particularly useful for showing **ranking**.

In this case:

* **Brand** → categories being compared.
* **Distinct Count of Title** → number of varieties.
* The ribbon/ranking arrangement shows how the brands compare against one another.

Because you've filtered the visual to Top 5, only the five highest-ranking brands will be displayed.

---

# 10. Change the Chart Title

Give the visual a meaningful title.

1. Select the Ribbon Chart.
2. Open **Format Your Visual**.
3. Go to **General**.
4. Expand **Title**.
5. Turn the title on if required.
6. Enter:

> **Top 5 Brands by Highest Number of Varieties**

You could also use the shorter:

> **Top 5 Brands by Number of Varieties**

The second title is cleaner and usually preferable.

---

# 11. Format the Data Labels

To make the number of varieties visible:

1. Select the Ribbon Chart.
2. Open **Format Your Visual**.
3. Find **Data labels**.
4. Turn them **On**.

If available in your Power BI version, adjust the label settings so that the distinct-count values are clearly visible.

---

# 12. Format the Legend

Depending on how Power BI displays the Ribbon Chart, you may have a **Legend** option.

You can:

1. Open **Format Your Visual**.
2. Select **Legend**.
3. Adjust its position if necessary.

For example:

* Top
* Bottom
* Left
* Right

If the legend doesn't add useful information, you can turn it **Off**.

---

# 13. Adjust the Ribbon Chart Appearance

You can further format the visual according to the report layout.

Check options such as:

* **Data labels**
* **Legend**
* **X-axis**
* **Y-axis**
* **Gridlines**
* **Title**
* **Spacing**
* **Visual size**

Resize the chart on the canvas so that it fits neatly with your other visuals.

---

# 14. Final Configuration

Your Ribbon Chart should essentially have the following configuration:

### Fields

**X-axis:**

> Brand

**Y-axis:**

> Title → Distinct Count

### Visual-level filter

**Brand:**

> Top 5

**By value:**

> Title → Distinct Count

### Title

> **Top 5 Brands by Number of Varieties**

---

# Complete Workflow

**Copy existing bar chart**

↓

**Ctrl+C → Ctrl+V**

↓

**Remove existing visual-level filter**

↓

**Remove Brand from previous axis**

↓

**Remove Average Discount Percentage**

↓

**Add Brand → X-axis**

↓

**Add Title → Y-axis**

↓

**Change Title → Distinct Count**

↓

**Add Brand → Filters on this visual**

↓

**Change Basic filtering → Top**

↓

**Select Top 5**

↓

**Add Title → By value**

↓

**Change Title → Distinct Count**

↓

**Click Apply filter**

↓

**Change visualization → Ribbon Chart**

↓

**Format data labels**

↓

**Format legend**

↓

**Change title**

↓

**Resize/adjust chart**

---

### One important difference from the Donut Chart

For the **donut chart**, you were essentially showing the **composition of the top 5 brands**.

For the **Ribbon Chart**, the key purpose is to show the **ranking of those brands based on their number of varieties**.

So the core calculation remains:

> **Brand → Top 5 → based on Distinct Count of Title**

but the **Ribbon Chart emphasizes ranking**, making it a useful alternative visual for the same insight.
