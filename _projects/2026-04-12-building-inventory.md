---
name: Building Inventory Agency & Usage Analysis
tools: [Python, Altair, Vega-Lite]
image: assets/pngs/building.png
description: This project explores building distribution across agencies and usage types using interactive Altair visualizations.
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

# Building Count by Agency and Status

The first plot is a horizontal bar chart showing the distribution of building statuses across different Illinois government agencies. It's meant to highlight which agencies manage the largest portfolios and where those properties currently stand. I used a horizontal orientation so the long agency names stay readable without overlapping.

<vegachart schema-url="{{ site.baseurl }}/assets/json/hw6-1.json" style="width: 100%"></vegachart>

# Interactive Building Usage Heatmap

The second plot is a heatmap exploring the relationship between building usage and current status.

Color encodes the density of buildings within each category. I added panning and zooming so users can navigate the wide range of usage labels without the chart getting cramped. Tooltips show exact building counts on hover, which makes it easy to dig into specific cells without cluttering the view.

<vegachart schema-url="{{ site.baseurl }}/assets/json/hw6-2.json" style="width: 100%"></vegachart>

## Design Choices & Data Transformations

**Design Choices:**
For the first plot, I used nominal encoding for both Agency Name (y-axis) and Building Status (color), with a selection parameter bound to the legend so users can highlight a specific status across all agencies. For the second plot, I used `mark_rect` with a "purples" color scheme — quantitative encoding for the building count and nominal encoding for usage and status categories.

**Data Transformations:**
Invalid "0" entries in Year Constructed and Square Footage were replaced with `np.nan`. Since the dataset is large, I passed the data URL directly into the Altair chart rather than loading it locally, which keeps the visualizations lightweight and avoids row-limit errors. No grouping or reshaping was needed since Altair handles the count aggregations natively.

**Comparison to Homework #5:**
In Homework #5, I analyzed the Building Inventory dataset using Year Acquired and Square Footage to create line plots of descriptive statistics. Here, I switched entirely to Agency Name, Usage Description, and Bldg Status with bar charts and heatmaps, so there's no overlap in variables or visual form between the two assignments.

## Search The Data & Methods

Below are the links to the data source and the analysis notebook.

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/yourusername/yourusername.github.io/blob/main/python_notebooks/analysis.ipynb" text="The Analysis" %}
</div>