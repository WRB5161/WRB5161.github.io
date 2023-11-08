---
name: Visualizing Student-Teacher ratio with spending and whether its Urban
tools: [Python, HTML, vega-lite]
image: assets/pngs/HW8_Chart1.png
description: This combo visualization is for HW8 of IS 445
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---


# Here is a snippet of the dataset

This data comes from [the is445 dataset collection](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/mobility.csv) that we have not gotten to use yet. Here is a snippet our dataset with only the relevant columns showing.

<img id="dataset snippet" schema-url="{{ site.baseurl }}/assets/pngs/HW8_dataset.png">



## Final Viz

The following two charts depict the school spending as it relates to student teacher ratio and how that is broken down between Urban vs non-Urban schools

<vegachart schema-url="{{ site.baseurl }}/assets/json/HW8_Chart3.json" style="width: 100%"></vegachart>


<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/mobility.csv" text="The Data" %}
</div>


