# Power BI Customer Feedback Analysis — Word Cloud, Bar Chart, Table & Publishing

## 1. Overview

In the previous session, customer feedback data was imported from an **Excel workbook** and analyzed using **Text Analytics**.

Two important columns were added to the customer feedback dataset:

1. **Score Sentiment**
2. **Good/Improvement**

### Score Sentiment

This column converts textual feedback into a numerical sentiment score between **0 and 1**.

A higher score indicates comparatively better/more positive feedback, while a lower score indicates feedback that may require improvement.

### Good/Improvement

This is a conditional column used to classify feedback into categories:

| Score Sentiment | Category          |
| --------------: | ----------------- |
|        `>= 0.8` | Excellent         |
|        `>= 0.6` | Good              |
|         `< 0.6` | Needs Improvement |

In this session, these columns are used to create different visuals and analyze the customer feedback.

---

# 2. Create a New Report Page

The first step is to create a separate report page for the customer feedback analysis.

### Steps

1. Open the Power BI report in **Power BI Desktop**.
2. At the bottom of the report canvas, click the **`+` (plus) icon**.
3. A new blank report page is created.

This page will be used to represent customer feedback insights.

---

# 3. Word Cloud Visual

The first visual created on this page is a **Word Cloud**.

A word cloud is useful for identifying the words that occur most frequently in a text dataset.

### Important concept

In a word cloud:

> **The more frequently a word occurs, the larger that word is represented.**

For example, if the word **"very"** occurs 34 times, it will appear larger than words that occur fewer times.

---

# 4. Default vs Custom Visuals

Power BI provides many visuals by default in the **Visualizations** pane.

However, Power BI also allows you to import additional/custom visuals.

These visuals can be obtained from:

* **Microsoft AppSource**
* Power BI marketplace/custom visual marketplace

The Word Cloud used in this example is **not one of the default visuals**, so it needs to be imported.

---

# 5. Import the Word Cloud Visual

### Steps

1. In Power BI Desktop, locate the Visualizations pane.
2. Click:

**Get More Visuals**

Power BI opens the marketplace/AppSource area.

3. Search for:

**Word Cloud**

4. Locate the Word Cloud visual that is being used in the lecture.
5. Select it.
6. Click:

**Add**

Power BI displays a confirmation message indicating that:

> The visual was successfully imported into the report.

7. Click **OK**.

The Word Cloud visual is now available in the report's visualization options.

---

# 6. Add the Word Cloud to the Report

### Steps

1. Select the newly imported **Word Cloud** visual.
2. Power BI adds a blank Word Cloud to the report canvas.
3. Resize it according to the requirement.

The Word Cloud is now ready to be configured.

---

# 7. Configure the Word Cloud

The Word Cloud needs two pieces of information:

1. The actual text/words to analyze.
2. The number of times those words occur.

The **Feedback** column is used for both purposes.

---

## 8. Add Feedback to Category

### Steps

1. Select the Word Cloud visual.
2. Expand the **Sheet 1** dataset in the Data pane.
3. Locate the **Feedback** column.
4. Drag and drop **Feedback** into the:

**Category** bucket.

The category tells the Word Cloud which text/words it needs to analyze.

---

# 9. Add Feedback to Values

Now we need to tell Power BI how frequently each word occurs.

### Steps

1. Again select the **Feedback** column.
2. Drag and drop it into:

**Values**

3. Open the dropdown associated with the field.
4. Select:

**Count**

This tells Power BI to count the occurrences.

So the Word Cloud is essentially using:

**Category → Feedback**

**Values → Count of Feedback**

---

# 10. Understanding the Word Cloud

Once configured, the Word Cloud displays words based on their frequency.

For example:

* Word A → 34 occurrences → larger
* Word B → 15 occurrences → smaller
* Word C → 8 occurrences → smaller

The exact size depends on how frequently the word occurs.

---

# 11. Format the Word Cloud

The Word Cloud is then formatted to improve its appearance.

### Turn off text rotation

1. Select the Word Cloud.
2. Click:

**Format a visual**

3. Locate the **Rotate Text** setting.
4. Turn it:

**Off**

This keeps the words from being displayed in different orientations.

---

# 12. Remove the Visual Title

The title is not required for this Word Cloud.

### Steps

1. Go to:

**Format a visual → General**

2. Find **Title**.
3. Turn the title:

**Off**

---

# 13. Add a Border to the Word Cloud

A border is added around the Word Cloud.

### Steps

1. Select the Word Cloud.
2. Open the formatting options.
3. Go to:

**Effects**

4. Locate the **Border** option.
5. Enable the border.
6. Set the border color to:

**White**

This gives the visual a defined boundary.

---

# 14. Word Cloud Tooltip

When you hover over a word in the Word Cloud, Power BI displays information about that word.

For example, hovering over a word can show:

* The word itself
* The number of times the word occurs in the Feedback column

This makes it easy to understand why certain words appear larger than others.

---

# 15. Example: Word "Very"

Suppose the word:

**very**

appears **34 times** in the feedback.

Because it has a relatively high frequency, it is displayed using a larger font size than words that occur fewer times.

Therefore:

> **Frequency ↑ → Word Size ↑**

---

# 16. Create a Stacked Bar Chart

The next requirement is to show the number of customers who provided different categories of feedback.

The categories are:

* Excellent
* Good
* Needs Improvement

A **Stacked Bar Chart** is used for this purpose.

---

# 17. Add the Stacked Bar Chart

### Steps

1. Click on a blank area of the report canvas.
2. Select:

**Stacked Bar Chart**

3. Power BI creates a blank bar chart.
4. Resize the chart.
5. Position it appropriately on the report page.

---

# 18. Configure the Bar Chart

The bar chart needs:

* Feedback category
* Customer count

### Add Good/Improvement

1. Locate the **Good/Improvement** column.
2. Drag it into the:

**Y-axis** bucket.

This gives us the categories:

* Excellent
* Good
* Needs Improvement

---

### Add Customer Name

1. Locate the **Customer Name** field.
2. Drag it into the appropriate value/X-axis bucket.
3. Power BI calculates the count of customers.

The resulting visual represents:

> **Count of Customers by Feedback Category**

---

# 19. Format the Bar Chart

Now the bar chart is formatted.

Select the bar chart and click:

**Format a visual**

---

## 20. Format the Y-Axis

The Y-axis contains the feedback categories.

The axis title is not required.

### Steps

1. Go to:

**Y-axis**
2. Locate **Title**.
3. Turn it:

**Off**

---

# 21. Format the X-Axis

The X-axis represents the numerical count.

In the lecture, the numerical values and title on the horizontal axis are removed.

### Steps

1. Expand:

**X-axis**
2. Turn off the **values**.
3. Turn off the **title**.
4. Turn off **gridlines**.

Since the values will later be displayed directly on the bars through data labels, the X-axis values are unnecessary.

---

# 22. Change Bar Color

The bars are formatted using green.

### Steps

1. Go to the bar formatting options.
2. Expand:

**Bars**
3. Locate **Colors**.
4. Change the bar color to:

**Green**

---

# 23. Resize the Bar Chart

After formatting:

* Resize the bar chart as required.
* Position it appropriately on the report page.

---

# 24. Change the Chart Title

The automatically generated title is changed to something more meaningful.

The new title is:

> **Count of Customers by Feedback**

### Steps

1. Select the chart.
2. Go to:

**General → Title**
3. Change the title text to:

**Count of Customers by Feedback**

---

# 25. Format the Chart Title

The title is further customized.

Possible formatting applied in the lecture includes:

* Font style changes
* **Bold**
* *Italic*
* Underline
* Center alignment

This is done to improve the appearance of the chart title.

---

# 26. Add a Border to the Bar Chart

A border is also added to the bar chart.

### Steps

1. Select the bar chart.
2. Go to:

**General → Effects**
3. Expand the visual border options.
4. Enable the border.
5. Set the border color to:

**White**

---

# 27. Format Y-Axis Values

The feedback categories displayed along the Y-axis are also formatted.

### Steps

1. Go to the visual formatting options.
2. Open:

**Y-axis**
3. Locate the values/categories.
4. Change the font style.
5. Make the text **bold**.
6. Increase the font size slightly.

This improves readability.

---

# 28. Enable Data Labels

Since the numerical values were removed from the X-axis, the actual counts need to be displayed directly on the bars.

### Steps

1. Select the bar chart.
2. Open:

**Data labels**
3. Turn **Data labels**:

**On**

Now the count appears directly on the corresponding bar.

---

# 29. Format Data Labels

The data labels are also formatted.

### Steps

1. Expand the **Data labels** section.
2. Expand the values/options.
3. Change the font style.
4. Make the labels **bold**.
5. Increase their size slightly.

This makes the customer counts easier to read.

---

# 30. Final Bar Chart

The resulting chart represents:

> **Count of Customers by Feedback**

It allows us to quickly see how many customers belong to each feedback category:

* Excellent
* Good
* Needs Improvement

---

# 31. Create a Table Visual

The third visual added to the report page is a **Table**.

The requirement is to show detailed customer feedback information.

The table should contain:

1. Customer Name
2. Sentiment Score
3. Exact Feedback

---

# 32. Add the Table Visual

### Steps

1. Click on a blank area of the canvas.
2. Select:

**Table**

3. Power BI creates a blank table.
4. Resize it appropriately.

---

# 33. Add Customer Name

### Steps

1. Locate **Customer Name** in the Data pane.
2. Drag it into the:

**Columns** bucket.

The table now displays customer names.

---

# 34. Add Sentiment Score

Next, add the sentiment score.

### Steps

1. Locate:

**Score Sentiment**
2. Drag it into the:

**Columns** bucket.

---

# 35. Important: Disable Summarization

Because **Score Sentiment** is a numerical field, Power BI may automatically summarize it.

For example, Power BI might automatically show:

> **Sum of Score Sentiment**

But this is **not what we want**.

We want to display the individual sentiment score for each customer.

### Steps

1. Click the dropdown associated with **Score Sentiment** in the table field.
2. Select:

**Don't Summarize**

Now Power BI displays the actual sentiment score for each individual record.

### Important Power BI concept

> By default, Power BI generally summarizes numerical fields when they are added to visuals.

Therefore, when you want to display individual numerical values, you may need to choose:

**Don't Summarize**

---

# 36. Add the Feedback Column

Finally, add the actual customer feedback.

### Steps

1. Locate the **Feedback** column.
2. Drag it into the:

**Columns** bucket.

The table now contains:

| Customer Name | Score Sentiment | Feedback        |
| ------------- | --------------: | --------------- |
| Customer 1    |            0.91 | Actual feedback |
| Customer 2    |            0.73 | Actual feedback |
| Customer 3    |            0.42 | Actual feedback |

The actual values depend on the dataset.

---

# 37. Interaction Between Word Cloud and Other Visuals

One of the most important concepts demonstrated in this session is **visual interaction/filtering**.

The Word Cloud can be used to filter the other visuals on the page.

For example, clicking a word in the Word Cloud causes the other visuals to update based on that selected word.

---

# 38. Example: Select the Word "Available"

Suppose the word:

**available**

is displayed in the Word Cloud.

If you click **available**:

* The table is filtered.
* The bar chart is filtered.
* Only feedback containing the selected word is displayed/relevant.

The lecture mentions that **available** appears twice in two sentences.

Therefore, selecting the word filters the other visuals to the corresponding feedback records.

---

# 39. Clear the Word Cloud Selection

If you click the selected word again, the selection is removed.

The report returns to its original/unfiltered state.

So:

**Click word → Apply filter**

**Click selected word again → Remove selection**

---

# 40. Example: Select "Satisfied"

The word **satisfied** appears much more frequently.

The lecture mentions that it appears:

> **15 times**

Because of its high frequency, it is represented with a larger word size.

When you click **satisfied**:

* The table is filtered.
* The bar chart is filtered.
* The corresponding feedback records are displayed.

---

# 41. Analyze the "Satisfied" Selection

The filtered results show the feedback associated with the word **satisfied**.

The lecture notes that among the 15 occurrences:

* **12** correspond to Excellent feedback.
* **1** corresponds to Needs Improvement.
* **2** correspond to Good feedback.

Therefore, the Word Cloud isn't merely showing frequently used words—it can also act as an interactive way to explore the underlying feedback.

---

# 42. Example: Select "Good"

Now select the word:

**good**

The lecture notes that this word appears in **8 feedback sentences**.

After clicking **good**:

* The table displays the corresponding feedback.
* The sentiment score is shown.
* Customer names are shown.
* The bar chart is filtered.
* Other visuals respond to the selection.

This demonstrates how Power BI visuals can interact dynamically with each other.

---

# 43. Add a Border to the Table

The table is also formatted with a border.

### Steps

1. Select the table visual.
2. Go to:

**General → Effects → Visual Border**
3. Enable the border.
4. Change the border color to:

**White**

This gives the table a defined visual boundary.

---

# 44. Important Concept: Cross-Filtering

The interaction between the Word Cloud, bar chart, and table is an example of Power BI's interactive filtering behavior.

Conceptually:

**Select Word Cloud Word**

↓

**Power BI applies selection/filter context**

↓

**Bar Chart updates**

*

**Table updates**

*

**Word Cloud may update based on the selected context**

This makes the report interactive rather than simply displaying static charts.

---

# 45. Publishing the Updated Report

After creating the new report page and visuals, the updated report needs to be published to Power BI Service.

### Steps

1. Click:

**Publish**

2. Power BI may ask:

> Do you want to save changes?

3. Select:

**Yes**

4. Select the workspace:

**Test Power BI Project Two**

5. Click/select the workspace to publish.

---

# 46. Replacing the Existing Report

Because the report has already been published previously, Power BI indicates that an existing report/dashboard with the same name will be replaced.

Since changes have been made:

**Select → Replace**

Power BI publishes the updated version.

The publishing process may take some time.

---

# 47. Open the Published Report

After publishing, Power BI provides a link to the report.

### Steps

1. Click the provided link.
2. The Power BI report opens in Power BI Service.
3. If authentication is required:

   * Enter the Power BI account email address.
   * Enter the password.
   * Sign in.

The lecture uses a Power BI account created earlier in the course.

---

# 48. Verify the Third Report Page

After opening the report in Power BI Service, navigate to the newly created:

> **Third report page**

This page contains the customer feedback analysis visuals.

The visuals created include:

* Word Cloud
* Bar Chart
* Table

---

# 49. Test the Word Cloud in Power BI Service

The same interactive behavior that was observed in Power BI Desktop should work in Power BI Service.

For example:

### Select "bird"

Click the word **bird**.

The report gets filtered based on that word.

The table displays the relevant feedback records.

---

### Select "policy"

Click:

**policy**

The table displays the feedback/sentences where the word is used.

---

### Select "process"

Click:

**process**

The corresponding feedback information is displayed.

---

### Select "excellent"

Click:

**excellent**

The page gets filtered according to the relevant feedback/category context.

Other words and visuals also respond to the selection.

This demonstrates that the report's interactive behavior is retained after publishing to Power BI Service.

---

# 50. Custom Visuals and AppSource

An important additional concept from the lecture is the use of **custom visuals**.

The Word Cloud was not available among the default Power BI visuals.

Therefore, it was imported from **AppSource/marketplace**.

### Important point

When importing custom visuals from AppSource/marketplace:

> **You should be signed into your Power BI account.**

In the lecture, the user was already signed in, which allowed the visual to be imported successfully.

---

# 51. Complete Visual Creation Workflow

The complete process can be remembered as:

### Step 1 — Create Page

**`+` → New Blank Page**

↓

### Step 2 — Import Custom Visual

**Get More Visuals → Search Word Cloud → Select → Add → OK**

↓

### Step 3 — Configure Word Cloud

**Feedback → Category**

**Feedback → Values → Count**

↓

### Step 4 — Format Word Cloud

* Rotate Text → Off
* Title → Off
* Border → On
* Border Color → White

↓

### Step 5 — Create Bar Chart

**Blank Canvas → Stacked Bar Chart**

↓

**Good/Improvement → Y-axis**

**Customer Name → Value/X-axis → Count**

↓

### Step 6 — Format Bar Chart

* Y-axis title → Off
* X-axis values → Off
* X-axis title → Off
* Gridlines → Off
* Bars → Green
* Title → `Count of Customers by Feedback`
* Title formatting → Bold/Italic/Underline/Center as required
* Border → On
* Border color → White
* Y-axis labels → Bold/larger
* Data labels → On
* Data labels → Bold/larger

↓

### Step 7 — Create Table

**Table Visual**

↓

**Customer Name → Columns**

**Score Sentiment → Columns**

**Score Sentiment → Don't Summarize**

**Feedback → Columns**

↓

### Step 8 — Format Table

**General → Effects → Visual Border → White**

↓

### Step 9 — Test Interactions

Click words in Word Cloud.

↓

Observe filtering in:

* Bar chart
* Table
* Other relevant visuals

↓

### Step 10 — Publish

**Publish → Save Changes → Test Power BI Project Two → Replace**

↓

Open the report in Power BI Service and verify the visuals.

---

# 52. Important Power BI Concepts Learned

## Custom Visuals

Power BI allows users to extend the default visualization library using visuals from **AppSource/marketplace**.

---

## Word Cloud

Useful for analyzing the frequency of words in text data.

**Higher frequency → Larger word**

---

## Count Aggregation

Used to determine how many times a value/word occurs.

In the Word Cloud:

**Feedback → Values → Count**

---

## Don't Summarize

Used when you want Power BI to display individual numerical values rather than aggregate them.

For the sentiment score:

**Score Sentiment → Don't Summarize**

instead of:

**Sum of Score Sentiment**

---

## Visual Interactions

Selecting one visual can filter/highlight other visuals on the same report page.

In this example:

**Word Cloud selection → Bar Chart + Table filtering**

---

## Publishing

After changes are made to a report:

**Publish → Select Workspace → Replace existing report**

if an existing report with the same name is already present.

---

# 53. Final Report Page Structure

The new third page essentially contains three complementary visuals:

### 1. Word Cloud

Shows:

> **Which words are used most frequently in customer feedback?**

### 2. Bar Chart

Shows:

> **How many customers gave Excellent, Good, or Needs Improvement feedback?**

### 3. Table

Shows:

> **Who gave the feedback, what their sentiment score was, and what exact feedback they provided?**

Together, these provide:

**Text Frequency + Sentiment Category + Detailed Feedback**

---

# 54. Key Takeaways

* A new report page was created for **customer feedback analysis**.
* A **Word Cloud** was imported as a custom visual from AppSource/marketplace.
* Custom visuals can be added using **Get More Visuals**.
* The user should be signed into their Power BI account when importing custom visuals.
* **Feedback** was added to the Word Cloud's Category bucket.
* **Feedback** was also added to Values and changed to **Count**.
* Frequently occurring words appear **larger** in the Word Cloud.
* A **Stacked Bar Chart** was created to show customer counts by feedback category.
* **Good/Improvement** was used for the category.
* **Customer Name** was used to calculate the count.
* The bar chart was formatted with a title, border, labels, and other visual formatting.
* A **Table** was created containing:

  * Customer Name
  * Score Sentiment
  * Feedback
* **Score Sentiment** was set to **Don't Summarize** so individual sentiment scores are displayed.
* Selecting a word in the Word Cloud dynamically filters the other visuals.
* This interaction was tested with words such as **available, satisfied, good, bird, policy, process, and excellent**.
* The completed report was published to **Power BI Service**.
* Since an existing report was already present, **Replace** was selected during publishing.
* The published report was then tested in Power BI Service to verify that the interactive filtering continued to work.
