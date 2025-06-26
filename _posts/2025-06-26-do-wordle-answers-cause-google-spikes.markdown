---
layout: post
title:  "Do Wordle Answers Cause Google Spikes?"
date:   2025-06-26 15:45:00 +0530
categories: data
---

A simple word game - guess a 5-letter word in six tries. [Wordle](https://www.nytimes.com/games/wordle/index.html), created by Josh Wardle, quietly turned into a daily habit for thousands of people — so much so that the New York Times ended up buying it for at least a million dollars.

Like many others, I got into the habit of looking up the meaning of the day’s word — especially when it wasn’t something I’d normally use. At some point, I wondered: if this is my instinct, surely others are doing the same?

That led to a small hypothesis, and eventually, a full dataset exploration.
![Wordle](/assets/images/wordle.png)

{% raw %}
<script type="text/javascript" src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script type="text/javascript" id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
{% endraw %}

## 🧠 Hypothesis

> *Each Wordle word generates a noticeable spike in Google searches on the day it appears — especially if the word is uncommon.*

If this is happening at scale, we should be able to observe it using publicly available data.

## 🔍 What Data We Used

To explore this, I gathered data for each Wordle day including:

- Date
- Wordle Answer  
  *(Source: [YourDictionary](https://wordfinder.yourdictionary.com/wordle/answers/), from June 2021 – June 2025)*
- Commonality of the word
- Google search trends for that word


We defined commonality using two metrics:

1. **Wordfreq** (Python library) – Based on books, websites, etc.
2. **SUBTLEX** (Subtitle-based frequency dataset) – Reflects more spoken-word usage

### Word Commonality
We used the following formula to normalize commonality:

$$
\text{commonality} = \frac{\log(1 + \text{word_frequency})}{\log(1 + \text{max_frequency})}
$$

The max frequency for commanality using `wordfreq` is based on the word “the”, considered one of the most common words in English.


<details>
<summary><strong>Show commonality generation code</strong></summary>
<pre>
{% highlight python %}
import math
import pandas as pd
from wordfreq import word_frequency

# Source: https://www.ugent.be/pp/experimentele-psychologie/en/research/documents/subtlexus (Zipped text version)
_SUBTLEX_SOURCE_PATH = './data/SUBTLEXus.tsv'

def subtlex_commonality(word: str, source_dataset: str = './data/SUBTLEXus.tsv', log_scale: bool = True) -> float:
    word = word.lower()
    subtlex_df = pd.read_csv(source_dataset, sep='\t')
    row = subtlex_df[subtlex_df['Word'].str.lower() == word]

    if row.empty:
        return 0.0  # Word not found
    
    freq = float(row.iloc[0]['SUBTLWF'])
    max_freq = subtlex_df['SUBTLWF'].max()

    if freq == 0 or max_freq == 0:
        return 0.0
    
    if log_scale:
        score = math.log1p(freq) / math.log1p(max_freq)
    else:
        score = freq / max_freq

    return round(score, 4)


def wordfreq_commonality(word: str, lang: str = 'en', wordlist: str = 'best', log_scale: bool = True) -> float:
    """
    Returns a commonness score between 0 and 1 based on wordfreq.
    
    Parameters:
    - word: the input word to evaluate
    - lang: language code (e.g., 'en' for English)
    - wordlist: 'best', 'large', 'small' — which corpus group to use
    - log_scale: whether to apply log scaling to frequency
    
    Returns:
    - A float between 0 (rare) and 1 (very common)
    """
    freq = word_frequency(word.lower(), lang, wordlist=wordlist)

    if freq == 0:
        return 0.0

    if log_scale:
        # Use log1p to normalize and smooth
        max_freq = word_frequency('the', lang, wordlist=wordlist)  # Approx. highest
        score = math.log1p(freq) / math.log1p(max_freq)
    else:
        # Just scale linearly to "the"
        max_freq = word_frequency('the', lang, wordlist=wordlist)
        score = freq / max_freq

    return round(score, 4)

def append_word_commonality(source_dataset: str, fn: callable) -> None:
    """
    Appends the commoness indicator column for each word of the CSV file.

    Parameters:
    - source_dataset: Path to the dataset to read.
    - fn: Function to use for finding the word commoness
    """
    df = pd.read_csv(source_dataset)
    df['word'] = df['word'].str.lower()
    df[fn.__name__] = df['word'].apply(fn)
    df.to_csv(source_dataset, index=False)
    

if __name__ == '__main__':
    print("Starting execution...")
    source_file = './data/raw_data.csv'
    append_word_commonality(source_dataset=source_file, fn=wordfreq_commonality)
    append_word_commonality(source_dataset=source_file, fn=subtlex_commonality)
    print("Finished execution...")

{% endhighlight %}
</pre>
</details>
<br>

In this post, unless otherwise noted, we use the **SUBTLEX-based commonality score** (since I found this to be a better representation).

### Google Search Trends
For each word, we queried Google Trends and captured:

1. Global search volume on the Wordle day
2. Global average for the previous 200 days
3. Search volume (on Wordle day) in the “Language Resources” category
4. 200-day average in the same category

<details>
<summary><strong>Show trend generation code</strong></summary>
<pre>
{% highlight python %}
import pandas as pd
from functools import partial
from pytrends.request import TrendReq
from datetime import datetime, timedelta

# Locally would have to update _get_data method's parameter `method_whitelist` to `allowed_methods`
# to work with newer versions of urllib3
pytrends = TrendReq(hl='en-US', tz=360, retries=2, backoff_factor=0.2)

def get_trends_usage(word: str, target_date: str, category: int = 0) -> tuple[int, float]:
    """
    Returns (usage_on_date, avg_prior_200_days) for a given word and date.
    
    Parameters:
    - word: search term
    - target_date: 'YYYY-MM-DD' format
    
    Returns:
    - Tuple: (value_on_day, avg_of_200_days_before)
    """
    date_obj = datetime.strptime(target_date, '%Y-%m-%d')
    start_date = (date_obj - timedelta(days=200)).strftime('%Y-%m-%d')
    end_date = (date_obj + timedelta(days=1)).strftime('%Y-%m-%d')  # include target day

    # Format: 'YYYY-MM-DD YYYY-MM-DD'
    timeframe = f"{start_date} {end_date}"
    print(f"Searching for trend of {word} in time range: {timeframe}")
    
    try:
        pytrends.build_payload([word], cat=category, timeframe=timeframe, geo='', gprop='')
        df = pytrends.interest_over_time()
        if df.empty:
            return (None, None)
        
        df = df.reset_index()
        df['date'] = df['date'].dt.date  # strip time

        value_on_day = df.loc[df['date'] == date_obj.date(), word]
        avg_before = df.loc[df['date'] < date_obj.date(), word].mean()

        print(f"Found values for {word}: value_on_day = {int(value_on_day.values[0])}, avg_200_days: {round(avg_before, 2)}")

        return (
            int(value_on_day.values[0]) if not value_on_day.empty else None,
            round(avg_before, 2)
        )
    
    except Exception as e:
        print(f"Error for {word} on {target_date}: {e}")
        return (None, None)

def safe_trends_request(row, col1, col2, category):
    """
    Even if we run multiple times, we want to ensure we trigger only for those words where we are missing the datapoints. 
    """
    # Skip if both values already exist and are not NaN
    if pd.notna(row.get(col1)) and pd.notna(row.get(col2)):
        # print(f"Skipping for current one! {row.get('word')}")
        return pd.Series([row[col1], row[col2]])
    
    return pd.Series(get_trends_usage(row['word'], row['date'], category=category))

def append_word_trend(source_dataset: str) -> None:
    df = pd.read_csv(source_dataset)
    # Ensure columns exist
    if 'trend_day_language' not in df.columns:
        df['trend_day_language'] = None
    if 'trend_avg_200_language' not in df.columns:
        df['trend_avg_200_language'] = None
    
    df['word'] = df['word'].str.lower()

    results = df.apply(partial(safe_trends_request, col1="trend_day_language", col2="trend_avg_200_language", category=108), axis=1)
    df[['trend_day_language', 'trend_avg_200_language']] = results

    df.to_csv(source_dataset, index=False)

def append_global_word_trend(source_dataset: str) -> None:
    df = pd.read_csv(source_dataset)
    # Ensure columns exist
    if 'trend_day_global' not in df.columns:
        df['trend_day_global'] = None
    if 'trend_avg_200_global' not in df.columns:
        df['trend_avg_200_global'] = None
    
    df['word'] = df['word'].str.lower()

    results = df.apply(partial(safe_trends_request, col1="trend_day_global", col2="trend_avg_200_global", category=0), axis=1)
    df[['trend_day_global', 'trend_avg_200_global']] = results

    df.to_csv(source_dataset, index=False)

if __name__ == '__main__':
    source_dataset = './data/raw_data.csv'
    append_word_trend(source_dataset=source_dataset)
    append_global_word_trend(source_dataset=source_dataset)

{% endhighlight %}
</pre>
</details>

## 📈 Observations
We looked at how search interest on the Wordle day deviated from historical averages, and how this correlated with word commonality.

### 1. Wordle Day vs 200-Day Avg (Language Category)
We plotted this as a *barbell* chart, sorted by commonality.

* Gray bars: Positive spike
* Red bars: Negative spike

**What stood out:**

* The more common words had little deviation — some even declined slightly. (red bars)

![Wordle Category Barbell Chart - Common Words](/assets/images/wordle_category_barbell_chart_common_words.png)
* The less common a word, the larger the spike.
Words like “waltz” or “droop” showed huge increases (up to 100 on the trend scale).

![Wordle Category Barbell Chart - Uncommon Words](/assets/images/wordle_category_barbell_chart_uncommon_words.png)

* Overall, the hypothesis holds — though the correlation is stronger in the lower half (less common words).


### 2. All-Categories Trend Comparison

This was similar to the previous view but covered all search categories, not just “Language Resources”.

* The same pattern held.
* Common words again showed muted or no change.
* Rare words stood out clearly with search spikes.

This makes sense — common words are likely searched across many contexts, so Wordle adds only a small blip.

### 3. Word Cloud Visualization
We created a word cloud where:

$$ Size = Relative\ spike\ on\ Wordle\ day $$

$$ Color = commonality $$ 

$$ (bluer = rare,\ green/yellow = common) $$

![Wordle Word Cloud](/assets/images/wordle_word_cloud.png)

This clearly showed that **rarer words not only spiked more, but dominated the visualization**.

### 4. Bubble Plot: Commonness vs Spike
For this chart:

$$ X-axis = Commonality $$

$$ Y-axis = Spike\ magnitude $$

$$ Bubble\ size/color = Commonness\ (larger/greener = more common) $$

![Wordle Bubble Plot](/assets/images/wordle_bubble_plot.png)

We excluded words with negative deviations here for clarity.

The trend was visible: **the rarer the word, the stronger the reaction.**

## 🔎 So, What Does This All Mean?

This small experiment seems to confirm a quiet behavioral pattern:

> Many of us look up unfamiliar Wordle words — enough that it leaves a measurable trace on global search data.

Wordle nudges people to learn new words. And it turns out, I’m not the only one using it that way.

## 📊 Explore the Dashboard
Feel free to explore the interactive [Tableau dashboard](https://public.tableau.com/views/Wordle-GoogleTrends/Dashboard1?:language=en-GB&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) below.
{% raw %}
<div class="tableauPlaceholder" id="viz1750938268806" style="position: relative;">
    <noscript>
        <a href="#"><img alt="Dashboard 1 " src="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Wo&#47;Wordle-GoogleTrends&#47;Dashboard1&#47;1_rss.png" style="border: none;" /></a>
    </noscript>
    <object class="tableauViz" style="display: none;">
        <param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" /> <param name="embed_code_version" value="3" /> <param name="site_root" value="" /><param name="name" value="Wordle-GoogleTrends&#47;Dashboard1" />
        <param name="tabs" value="no" /><param name="toolbar" value="yes" /><param name="static_image" value="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Wo&#47;Wordle-GoogleTrends&#47;Dashboard1&#47;1.png" />
        <param name="animate_transition" value="yes" /><param name="display_static_image" value="yes" /><param name="display_spinner" value="yes" /><param name="display_overlay" value="yes" /><param name="display_count" value="yes" />
        <param name="language" value="en-GB" /><param name="filter" value="publish=yes" />
    </object>
</div>
<script type="text/javascript">
    var divElement = document.getElementById("viz1750938268806");
    var vizElement = divElement.getElementsByTagName("object")[0];
    if (divElement.offsetWidth > 800) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else if (divElement.offsetWidth > 500) {
        vizElement.style.width = "100%";
        vizElement.style.height = divElement.offsetWidth * 0.75 + "px";
    } else {
        vizElement.style.width = "100%";
        vizElement.style.height = "1177px";
    }
    var scriptElement = document.createElement("script");
    scriptElement.src = "https://public.tableau.com/javascripts/api/viz_v1.js";
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>
{% endraw %}

### 📁 Dataset: [🔗 View on Kaggle](https://www.kaggle.com/datasets/kambojankush/wordle-answer-search-trends-dataset-20212025)