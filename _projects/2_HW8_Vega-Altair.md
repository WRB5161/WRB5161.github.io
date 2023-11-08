---
name: Visualizing Student-Teacher ratio with spending and whether its Urban
tools: [Python, HTML, vega-lite, altair]
image: assets/pngs/HW8_Chart1.png
description: This combo visualization is for HW8 of IS 445
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# Let's look the individual charts

The following two charts depict the school spending as it relates to student teacher ratio and how that is broken down between Urban vs non-Urban schools If we take a look at both charts individually we can see some interesting characteristics and trends. Let's look at the first graph.

## Chart 1: Heatmap

<vegachart schema-url="{{ site.baseurl }}/assets/json/HW8_Chart1.json" style="width: 100%"></vegachart>

This heatmap shows us a 10x10 heatmap. I decided on bins of 10 for each axis as I enjoy the uniformity and ease that comes from looking at a 10x10, instead of say 10x6. The other axis included in this was color, which I merely have following the count of observations per box of the heatmap. If you decide to click around, you can see that we do hav an intractive box we can highlight certain ranges in the X and Y direction. Now on its own, this doesn't provide any immedeiate information, however it will become useful when we introduce our second chart. Also to note, the 'School_spending' is an interesting variable for our Y axis. It was reported as an integer, and not in $ spent which is interesting for something referring to money being spent. However this doesn't detract from us being able to differentiate between clearly higher spending schools versus the lower spending. Again, this will be easier if we can see our second chart, so let's take a look at it.

## Chart 2: Bar

<vegachart schema-url="{{ site.baseurl }}/assets/json/HW8_Chart2.json" style="width: 100%"></vegachart>

This second chart has no interaction within itself, however when we combine it with our first chart it will provide us a breakdown of Urban vs non-Urban schools within our selection on the heatmap. This chart is simple in nature, however, it took some work on the analysis side of things. The initial dataframe reports urban as a '1' or a '0', and I decided mapping this to a 'Y' indicating it is Urban, and 'N' to indicate it is non-Urban. I think this is really interesting to see as there are some surprising trends that can be seen when looking at specific ranges from our first chart. Before we look at the combined chart, let's see what a snippet of our dataset looked like before we transformed it into our visualizations.

## Here is a snippet of the dataset

This data comes from [the is445 dataset collection](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/mobility.csv), however it is not one I had analyzed prior to this. Here is a snippet of our dataset with only the relevant columns showing.

<img src="/assets/pngs/HW8_dataset.png">

Now that we can see some of the raw data, let's see the final thing!

# Final Viz

<vegachart schema-url="{{ site.baseurl }}/assets/json/HW8_Chart3.json" style="width: 100%"></vegachart>

Our final chart! As you can see when you drag your mouse around, we can now see the breakdown of Urban versus non-Urban for different spending ranges and student-teacher ratios. I think this is pretty interesting to think about. It is hard to draw many  concrete conclusions from this, but I think this type of dashboard would be useful for  people who want to dig deeper into these trends. I hope you enjoyed!


<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/mobility.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://raw.githubusercontent.com/WRB5161/WRB5161.github.io/main/python_notebooks/HW8_Plots.ipynb" text="The Program" %}
</div>

