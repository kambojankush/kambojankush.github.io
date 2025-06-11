---
layout: post
title:  "Numbers Don't Lie"
date:   2025-05-21 21:45:00 +0530
categories: books
---

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
* [World Band Indicator - Mortality Rate, infant (per 1,000 live births)](https://data.worldbank.org/indicator/SP.DYN.IMRT.IN)

## 3. Pandemic - Sometimes Numbers Do Lie

Numbers can be fudged when checks are absent—or more subtly, they can be misrepresented. This kind of misrepresentation is more common than we think. During the COVID-19 pandemic, several countries either underreported data or exploited loopholes in reporting systems to downplay the actual impact.

Let’s take the case of India. It is widely acknowledged that the official numbers significantly understate the true scale of the crisis. But how does such underreporting happen?

To begin with, many COVID-19 cases were never recorded. At the peak of the pandemic, the healthcare system was overwhelmed. Limited testing capacity, combined with the prevalence of asymptomatic or mildly symptomatic cases, meant a large portion of infections simply went undetected. Deaths, too, were very frequently misclassified. Instead of COVID-19, secondary causes like cardiac arrest or respiratory failure were often listed—even though these were direct consequences of the virus.

Officially, India reported around 5.3 lakh COVID-related deaths. However, a broader demographic view tells a very different story. If we look at India’s Crude Death Rate—the number of deaths per 1,000 people per year—and compare total annual deaths, 2021 stands out sharply.

Based on historical trends, India should have recorded around 92 to 93 lakh deaths in 2021. Instead, estimates put the total at approximately 1.3 crore—a spike of nearly **40** lakh deaths. This excess mortality far exceeds the official COVID death toll and offers a more realistic measure of the pandemic’s impact. Even conservatively, the actual toll appears to be **8 times** the reported figure. And if anecdotal and ground-level evidence is any guide, the real number could have been closer to 20 times—though hard data to confirm that scale is unfortunately lacking.

To put this in perspective: India’s death rate in 2021 mirrored levels last seen in 1997, more than **2 decades ago**. Under normal demographic projections, such a high number of deaths wouldn’t have been expected until **2043**, by which time India’s population is projected to reach about 168 crore.

So yes, sometimes numbers do lie—or at least, they hide more than they reveal. But by zooming out, cross-referencing data, and contextualizing statistics with broader indicators, we can arrive at something much closer to the truth.

{% raw %}
<div class="tableauPlaceholder" id="viz1746637025597" style="position: relative;">
    <noscript>
        <a href="#"><img alt="Dashboard 1 " src="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Co&#47;CovidDatawDemographicData&#47;Dashboard1&#47;1_rss.png" style="border: none;" /></a>
    </noscript>
    <object class="tableauViz" style="display: none;">
        <param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" /> <param name="embed_code_version" value="3" /> <param name="site_root" value="" /><param name="name" value="CovidDatawDemographicData&#47;Dashboard1" />
        <param name="tabs" value="no" /><param name="toolbar" value="yes" /><param name="static_image" value="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Co&#47;CovidDatawDemographicData&#47;Dashboard1&#47;1.png" />
        <param name="animate_transition" value="yes" /><param name="display_static_image" value="yes" /><param name="display_spinner" value="yes" /><param name="display_overlay" value="yes" /><param name="display_count" value="yes" />
        <param name="language" value="en-GB" />
    </object>
</div>
<script type="text/javascript">
    var divElement = document.getElementById("viz1746637025597");
    var vizElement = divElement.getElementsByTagName("object")[0];
    if (divElement.offsetWidth > 800) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else if (divElement.offsetWidth > 500) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else {
        vizElement.style.width = "100%";
        vizElement.style.height = "977px";
    }
    var scriptElement = document.createElement("script");
    scriptElement.src = "https://public.tableau.com/javascripts/api/viz_v1.js";
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
{% endraw %}

**🗂 Sources:**
* [WHO COVID-19 Dashboard Data](https://data.who.int/dashboards/covid19/data?n=o)
* [World Population Prospects](https://population.un.org/wpp/downloads?folder=Standard%20Projections&group=Most%20used)

## 4. Is life expectancy finally topping out?

{% raw %}
<div class="tableauPlaceholder" id="viz1747202972251" style="position: relative;">
    <noscript>
        <a href="#"><img alt="Life Expectancy Dashboard " src="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;LI&#47;LIfeExpectancy_17470426457230&#47;LifeExpectancyDashboard&#47;1_rss.png" style="border: none;" /></a>
    </noscript>
    <object class="tableauViz" style="display: none;">
        <param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" /> <param name="embed_code_version" value="3" /> <param name="site_root" value="" />
        <param name="name" value="LIfeExpectancy_17470426457230&#47;LifeExpectancyDashboard" /><param name="tabs" value="no" /><param name="toolbar" value="yes" />
        <param name="static_image" value="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;LI&#47;LIfeExpectancy_17470426457230&#47;LifeExpectancyDashboard&#47;1.png" /> <param name="animate_transition" value="yes" />
        <param name="display_static_image" value="yes" /><param name="display_spinner" value="yes" /><param name="display_overlay" value="yes" /><param name="display_count" value="yes" /><param name="language" value="en-GB" />
    </object>
</div>
<script type="text/javascript">
    var divElement = document.getElementById("viz1747202972251");
    var vizElement = divElement.getElementsByTagName("object")[0];
    if (divElement.offsetWidth > 800) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else if (divElement.offsetWidth > 500) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else {
        vizElement.style.width = "100%";
        vizElement.style.height = "727px";
    }
    var scriptElement = document.createElement("script");
    scriptElement.src = "https://public.tableau.com/javascripts/api/viz_v1.js";
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
{% endraw %}

**🗂 Sources:**
* [World Bank: Life expectancy at birth, total (years)](https://datacatalog.worldbank.org/indicator/6fc20d68-bace-eb11-bacc-000d3a3b9510/Life-expectancy-at-birth--total--years-)


## 5. How happy are people?

Distribution of happiness score based on various parameters.

* **Happiness Score** is the national average response to the question of life evaluations. The English
wording of the question is “Please imagine a ladder, with steps numbered from
0 at the bottom to 10 at the top. The top of the ladder represents the best
possible life for you and the bottom of the ladder represents the worst possible
life for you. On which step of the ladder would you say you personally feel you
stand at this time?”

* The statistics of **GDP per capita** in purchasing power parity (PPP)

* **Healthy Life Expectancy (HLE)** at birth are based on
the data extracted from the World Health Organization’s (WHO) Global Health
World Happiness Report 2025 Observatory data repository.

* **Social support** (or having someone to count on in times of trouble) is the national
average of the binary responses (either 0 or 1) to the GWP question “If you
were in trouble, do you have relatives or friends you can count on to help you
whenever you need them, or not?”

* **Freedom to make life choices** is the national average of responses to the GWP
question “Are you satisfied or dissatisfied with your freedom to choose what
you do with your life?”

* **Generosity** is the residual of regressing national average of response to the GWP
question “Have you donated money to a charity in the past month?” on GDP
per capita.

* **Coruption Perception** measure is the national average of the survey responses to two questions in the GWP: “Is corruption widespread throughout
the government or not” and “Is corruption widespread within businesses or
not?” The overall perception is just the average of the two 0-or-1 responses.

* **Dystopia residual** is "the Dystopia Happiness Score(1.85) + the Residual value or the unexplained value for each country"

{% raw %}
<div class="tableauPlaceholder" id="viz1747209126612" style="position: relative;">
    <noscript>
        <a href="#"><img alt="Dashboard " src="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Wo&#47;WorldHappinessReport_17472090930350&#47;Dashboard&#47;1_rss.png" style="border: none;" /></a>
    </noscript>
    <object class="tableauViz" style="display: none;">
        <param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" /> <param name="embed_code_version" value="3" /> <param name="site_root" value="" /><param name="name" value="WorldHappinessReport_17472090930350&#47;Dashboard" />
        <param name="tabs" value="no" /><param name="toolbar" value="yes" />
        <param name="static_image" value="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Wo&#47;WorldHappinessReport_17472090930350&#47;Dashboard&#47;1.png" /> <param name="animate_transition" value="yes" />
        <param name="display_static_image" value="yes" /><param name="display_spinner" value="yes" /><param name="display_overlay" value="yes" /><param name="display_count" value="yes" /><param name="language" value="en-GB" />
        <param name="filter" value="publish=yes" />
    </object>
</div>
<script type="text/javascript">
    var divElement = document.getElementById("viz1747209126612");
    var vizElement = divElement.getElementsByTagName("object")[0];
    if (divElement.offsetWidth > 800) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else if (divElement.offsetWidth > 500) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else {
        vizElement.style.width = "100%";
        vizElement.style.height = "827px";
    }
    var scriptElement = document.createElement("script");
    scriptElement.src = "https://public.tableau.com/javascripts/api/viz_v1.js";
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
{% endraw %}

**🗂 Sources:**
* [World Happiness Report](https://worldhappiness.report/data-sharing/)

