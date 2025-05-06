---
layout: post
title:  "Numbers Don't Lie"
date:   2025-05-05 21:45:00 +0530
categories: books, data
---

**Status**: In Progress
**Last Updated**: 2025-05-06

While reading [*Numbers Don’t Lie*](https://www.goodreads.com/book/show/50705179-numbers-don-t-lie) by [*Vaclav Smil*](https://www.goodreads.com/author/show/5003.Vaclav_Smil), I found it packed with fascinating data and insights that highlight how the world really works. However, I noticed a gap: many of the global statistics don’t include country-specific numbers for India.

So, to add a local perspective, I’m trying to compile India relevant data points for selected topics covered in the book, in an ongoing effort to help contextualize the insights.

---

## 1. What Happens When We Have Fewer Children?

**Total Fertility Rate (TFR)** – The number of children born per woman during her lifetime.
> The replacement level of fertility is that which maintains a population at a stable level. It is about **2.1**.
> If the national rates remain close to the replacement ( > 1.7), then there is a good chance of possible future rebounds. Once they slip below 1.5, such reversals appear increasingly unlikely.

Below is an interactive chart comparing TFR across countries over time.

{% raw %}
<div class='tableauPlaceholder' id='viz1746508966288' style='position: relative'>
   <noscript><a href='#'><img alt='TFR ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;To&#47;TotalFertilityData&#47;TFRDashboard&#47;1_rss.png' style='border: none' /></a></noscript>
   <object class='tableauViz'  style='display:none;'>
      <param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' />
      <param name='embed_code_version' value='3' />
      <param name='site_root' value='' />
      <param name='name' value='TotalFertilityData&#47;TFRDashboard' />
      <param name='tabs' value='no' />
      <param name='toolbar' value='yes' />
      <param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;To&#47;TotalFertilityData&#47;TFRDashboard&#47;1.png' />
      <param name='animate_transition' value='yes' />
      <param name='display_static_image' value='yes' />
      <param name='display_spinner' value='yes' />
      <param name='display_overlay' value='yes' />
      <param name='display_count' value='yes' />
      <param name='language' value='en-GB' />
   </object>
</div>
<script type='text/javascript'>
    var divElement = document.getElementById('viz1746508966288');
    var vizElement = divElement.getElementsByTagName('object')[0];
    if ( divElement.offsetWidth > 800 ) { 
        vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';
    } 
    else if ( divElement.offsetWidth > 500 ) { 
        vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';
    } 
    else { 
    vizElement.style.width='100%';vizElement.style.height='727px';
    }
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
{% endraw %}

**🗂 Sources:**
* [World Bank Indicator – Fertility Rate](https://datacatalog.worldbank.org/indicator/b199835d-eece-eb11-bacc-000d3a596ff0/Fertility-rate--total--births-per-woman-)
* [Health, Nutrition, and Population Statistics Dataset](https://datacatalog.worldbank.org/search/dataset/0037652/Health-Nutrition-and-Population-Statistics)

## 2. The best indicator for quality of life?

**Infant Mortality Rate (IMR)** – The number of deaths during the first year of life that takes place per 1,000 live births.
> Infant mortality is such a powerful indicator because low rates are impossible to achieve without having a combination of several critical conditions that define good quality of life – good healthcare in general; adequate and sanitary living conditions; and access to social support for disadvantaged families.

IMR Rate for India in 2023 is approximately equivalend to that of United States in **1960**, i.e there's approximately 6 decades of gap in timespan.

Below is an interactive chart comparing IMR across countries over time.

{% raw %}
<div class="tableauPlaceholder" id="viz1746524178027" style="position: relative;">
    <noscript>
        <a href="#"><img alt=" " src="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;To&#47;TotalFertilityData&#47;IMRDashboard&#47;1_rss.png" style="border: none;" /></a>
    </noscript>
    <object class="tableauViz" style="display: none;">
        <param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" /> <param name="embed_code_version" value="3" /> <param name="site_root" value="" /><param name="name" value="TotalFertilityData&#47;IMRDashboard" />
        <param name="tabs" value="yes" /><param name="toolbar" value="yes" /><param name="static_image" value="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;To&#47;TotalFertilityData&#47;IMRDashboard&#47;1.png" />
        <param name="animate_transition" value="yes" /><param name="display_static_image" value="yes" /><param name="display_spinner" value="yes" /><param name="display_overlay" value="yes" /><param name="display_count" value="yes" />
        <param name="language" value="en-GB" /><param name="filter" value="publish=yes" />
    </object>
</div>
<script type="text/javascript">
    var divElement = document.getElementById("viz1746524178027");
    var vizElement = divElement.getElementsByTagName("object")[0];
    if (divElement.offsetWidth > 800) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else if (divElement.offsetWidth > 500) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else {
        vizElement.style.width = "100%";
        vizElement.style.minHeight = "750px";
        vizElement.style.maxHeight = divElement.offsetWidth * 1.77 + "px";
    }
    var scriptElement = document.createElement("script");
    scriptElement.src = "https://public.tableau.com/javascripts/api/viz_v1.js";
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
{% endraw %}

**🗂 Sources:**
* [World Band Indicator - Mortality Rate, infant (per 1,000 live births](https://data.worldbank.org/indicator/SP.DYN.IMRT.IN)
