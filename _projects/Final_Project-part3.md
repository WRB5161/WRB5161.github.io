---
name: Solar Installations in Bloomington, IN
tools: [Python, HTML, vega-lite, altair, pandas, geopandas]
image: assets/pngs/FP3_solarpanel.png
description: This article goes into the details of solar production at various installations owned by the City of Bloomington Indiana.
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
  - vl-convert-python
---

<div class="center">
Author: William Bechtel
</div>

# Let's Look At The Data!

This data comes from [Indiana.gov](https://catalog.data.gov/dataset/solar-data-f09f3). They provide the dataset in multiple formats, however I used it as a csv

<img src="/assets/pngs/FP3_Data1.png">

This dataset contains 12 variables for each observation, including the index which is 'site_id'. Each observation/row of the dataset represents the solar production aggregates for that given date. The variables for each site include the address, name of the site, latitude and longitude of the site, and the department that owns/operates the facility. For the solar measurements there are a number of variables: watt_min and watt_max for that given date, the watt_avg which is a cumulative average production rate, and the watt_hours and watt_hours_expected represent the amount of energy that is expected to be generated and the actual amount that was generate. All of these values are in Watt's (and Wh) and not the more common kW (and kWh). This was a bit confusing at first but it's not too hard when looking at graphics to be able to understand relational details.

<div class="center">
Onto our figures!
</div>

## Figure 1: The First Bar Chart

<vegachart schema-url="{{ site.baseurl }}/assets/json/FP3_bars5.json" style="width: 100%"></vegachart>

On our first bar chart you will notice a few things a few things, and the first is that the scale of the Y-axis is unusual. For this data we needed to use a 'symlog' scale as two of the sites in Bloomington are significantly larger, and thus throw off the proportions of the bar chart when they're included with a linear scale. That's to say, without a 'symlog' scale, if we used a linear scale instead, our bar chart looks like the one below, not too useful. The final thing you will notice about our lovely bar chart is the opacity of each bar, which is grouped based on the number of days in which the site produced any energy (defined as the watt_hours being greater than 0). 

<vegachart schema-url="{{ site.baseurl }}/assets/json/FP3_bars4.json" style="width: 100%"></vegachart>


## Figure 2: The Map

<vegachart schema-url="{{ site.baseurl }}/assets/json/FP3_solar_map2.json" style="width: 100%"></vegachart>

Our map is crucial in understanding where these sites are located and how they compare to one another. This map has the shape and color mapped to the department that operates the facility, and the size is now represented by the count of days that was used for the bar chart opacity. As you hover over a point you can also see the name of the site for a better understanding of where certain sites are located. The other notable feature of the map is the background layer. I'm using a geojson file collected from [Indianamap.org](https://www.indianamap.org/datasets/INMap::road-centerlines-of-indiana-current/explore?location=39.169713%2C-86.520274%2C12.91) which contains the road center lines of Indiana as line geometry. Using a filtered version of this allowed me to produce a nice background map of Bloomington roads that makes the orientation and location of each site around the city more clear.


## Figure 3: The Other Bar

<vegachart schema-url="{{ site.baseurl }}/assets/json/FP3_bars3.json" style="width: 100%"></vegachart>

This bar chart is different than the one from before, but still quite useful. It displays the sites across the x-axis and the y-axis is the average number of watts produced per day by that site across its lifespan since 1/1/2018. The color dictates which department the facility is operated by, and helps us see that park/rec centers are apparently really good places to add solar installations. This also shows us that there are also a lot of sites really seem to lack substantial production values, and it makes me question the economic viability of some of those sites. Let's check out our final figure.


## Figure 4: The Scatter

<vegachart schema-url="{{ site.baseurl }}/assets/json/FP3_scatter1.json" style="width: 100%"></vegachart>

Finally, this scatter plot is quite neat, as each point represents observations from one day for one site. Each site is represented by its own color and in the adjacent legend, you are able to click on an individual site to then see the scatter plot filtered down to that site's data entries. Each entry is comprised of its average_watt_hours along the x-axis, it's watt_hours_produced along the y-axis, and if you hover on a map point, you can see the date that was from. I find this to be a really neat figure that is useful for getting specific details about a site's energy production. In combination with the other figures, you can learn a good deal about each site individually, and how it compares to others.


<!-- these are written in a combo of html and liquid --> 

<div class="left">
{% include elements/button.html link="https://catalog.data.gov/dataset/solar-data-f09f3/resource/bfbaeff4-d099-41a2-867c-f593ccb1a4a3" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://us.prairielearn.com/pl/workspace/1384174/container/lab/tree/Workbook1.ipynb" text="The Analysis" %}
</div>

