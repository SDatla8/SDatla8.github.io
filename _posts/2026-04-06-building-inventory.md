---
layout: post
title: "Building Inventory Analysis"
---

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<div id="vis1"></div>
<div id="vis2"></div>

The first plot is a line chart showing the building square footage statistics over time. This visualization is intended to show the trends of the building inventory. Using a log scale allows for small and large values to be visible and prevents large buildings from taking over the visualization.

The second plot is the same as the first but with interactivity.

**Design Choices:**
For both plots, I used temporal encoding for the Year Acquired (x-axis) and quantitative encoding for the Stats Value (y-axis). I used a nominal encoding for the Statistic field to color the lines. I chose a log scale for the y-axis to better visualize the range of values.

**Data Transformations:**
The dataset is grouped by Year Acquired and summary statistics of square footage. This gave values such as the min, median, mean, and max building sizes for every year. The dataframe was then reshaped using the melt function as shown in class. This transformation created two columns, two different statistic types. This structure was ideal for Altair to draw multiple lines using a singular encoding.

**Interactivity:**
The dropdown selection was added to allow users to choose which statistic to highlight. The dropdown is covering the statistic field and enables dynamic interaction in our plots. When the statistic is selected, the corresponding line is highlighted using color. All the other lines are faded so you can easily visualize the target. This interaction makes it easier to focus on a specific statistics while still having the rest of the data present.

---

<div class="left">
<a href="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv">
    <button type="button" class="btn btn-primary">The Data</button>
</a>
<a href="https://github.com/sdatla8/sdatla8.github.io/blob/main/HW5/analysis.ipynb">
    <button type="button" class="btn btn-primary">The Analysis</button>
</a>
</div>

<script type="text/javascript">
  // Pointing to your HW5 folder
  var spec1 = "{{ site.baseurl }}/HW5/plot1.json";
  var spec2 = "{{ site.baseurl }}/HW5/plot2.json";
  
  vegaEmbed('#vis1', spec1).catch(console.error);
  vegaEmbed('#vis2', spec2).catch(console.error);
</script>