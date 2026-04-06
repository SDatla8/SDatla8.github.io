---
name: Building Inventory Analysis
tools: [Python, Altair, Vega-Lite]
image: assets/pngs/building.png
description: This project explores historical trends in building square footage using interactive visualizations.
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

# Building Square Footage Statistics Over Time

The first plot is a line chart showing the building square footage statistics over time. This visualization is intended to show the trends of the building inventory. Using a log scale allows for small and large values to be visible and prevents large buildings from taking over the visualization.

<vegachart schema-url="{{ site.baseurl }}/HW5/plot1.json" style="width: 100%"></vegachart>

# Interactive Building Statistics

The second plot is the same as the first but with interactivity.

The dropdown selection was added to allow users to choose which statistic to highlight. The dropdown is covering the statistic field and enables dynamic interaction in our plots. When the statistic is selected, the corresponding line is highlighted using color. All the other lines are faded so you can easily visualize the target. This interaction makes it easier to focus on a specific statistics while still having the rest of the data present.

<vegachart schema-url="{{ site.baseurl }}/HW5/plot2.json" style="width: 100%"></vegachart>

## Design Choices & Data Transformations

**Design Choices:**
For both plots, I used temporal encoding for the Year Acquired (x-axis) and quantitative encoding for the Stats Value (y-axis). I used a nominal encoding for the Statistic field to color the lines. I chose a log scale for the y-axis to better visualize the range of values.

**Data Transformations:**
The dataset is grouped by Year Acquired and summary statistics of square footage. This gave values such as the min, median, mean, and max building sizes for every year. The dataframe was then reshaped using the melt function as shown in class. This transformation created two columns, two different statistic types. This structure was ideal for Altair to draw multiple lines using a singular encoding.

## Search The Data & Methods

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/sdatla8/sdatla8.github.io/blob/main/python_notebooks/analysis.ipynb" text="The Analysis" %}
</div>
