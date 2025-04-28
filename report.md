---
layout: wide_default
---        


## 10K Sentiment and Returns

Edgard J. Cuadra

_Abstract and Methodology_

To refer to any of the files/folder resort to the following github repository: [10-k Sentiment Repository](https://github.com/edgardjcuadra/asgn-05-edgardjcuadra)


In this report, we explore the 10k files for the S&P500 firms in order to determine their sentiment and explore the correlation between the 10k's and the returns on the stock a period after the companies file their documents. Using python, we first load two dictionaries with positive and negative words, along with a master dictionary that includes a classification for positive and negative words. After looping through these documents, we extract the words into a list and a data frame. After looking at the master dictionary, we defined different sentiment variables to include in our analysis. These variables include:
    1. bad news
    2. good news
    3. neutral words
    4. mildly positive words
    5. words that describe catastrophic events
    6. words that describe a turning point
These classifications are made using the rating for each of the words in order to classify them in levels of good, bad, or neutral.

Additionally, we made several context topics to use a ```NEAR_Regex``` (_a function that finds clusters of specific words_) function to determine if these topics signal something positive or negative. The topics include the following:
    1. bankruptcy risk - includes words like: "bankruptcy, insolvency, default..." among others
    2. growth initiatives - includes words like: "expansion, acquisition, growth, scaling..."
    3. legal exposure - includes words like: "lawsuit, litigacion, penalty..."
    4. economic risk - includes words like: "volatility, instability, fluctuation..."
    5. recovery path - includes words like: "recovery, rebound, turnaround..."

Finally, we scraped ```.html``` versions of the 10-k files, looping through each and identifying the found sets for the sentiment and topic variables. 
While this is executing, we keep track of the ratio of sentiment associated words to the length of the document and the proximity counts of topic related words that signify a nuisance. 

After calculating the sentiment scores, we then proceeded to use a returns document and merged this to our sentiment data. 

To finish off, we created three different data frames, all which contain aggregated returns for each firm t days after the 10k filling date, and we performed a correlation analysis to determine the relationship between our sentiment variables and the returns t days after the 10k is filed.

**A few key points about correlation ahead of result analysis:**


1. It only speaks to linear association, not causation or "which drives which."
    - A positive correlation simply means that when one variable is above its mean, the other tends to also be above its mean (and vice-versa).
    - It does not tell you that changes in a sentiment variable cause changes in the stock returns.
2. The sign tells you the direction of the relationship, but not the causal direction.
    - A positive sign means they move together, and a negative sign means they move in opposite directions.
3. Magniture -> strength of linear fit.
    - Correlation Coefficients run from -1 (perfect inverse) through 0 (no linear relationship) to +1 (perfect direct)
    - E.g. An r of 0.89 (correlation) is very high: it implies a very tight, roughly straight-line clustering of points. In fact, a squared r, assuming r = 0.89, r<sup>2</sup> = 0.79 means that about 79% of the variablity in one variable would be "explained" by a simple linear regression on the other.


## Findings

**Sentiment Variable Correlations Across Different Time Windows**

<p align = "center">
    <img src="images/output7.png" alt = "My Image" width = auto height = auto/>
</p>

<p align = "center" style = "font-style: italic">
For this analysis, we observed the returns from the day of the 10-k filing, 0 to 2 days after the filing, and from 3 to 10 days after the finding, along with their correlation to the sentiment analysis.
As we can observe, there are 10 different variables wich represent the analysis variable performed.
</p>

This table shows a heatmap fo rthe highest correlations between the dates and variables. The definition of the growth initiative variable shows to have the highest correlation with returns with a significant correlation of ```0.89``` on the day of 10-k filing. This is followed by "recovery path proximity", "economic risk proximity", and "bankruptcy risk proximity".

---
**Top Correlations on Filing Day Returns**

<p align = "center">
    <img src="images/output4.png" alt = "My Image" width = auto height = auto/>
</p>

<p align = "center" style = "font-style: italic">
This figure shows the highest sentiment variable and return correlation for the filing date returns.
</p>

In this graph, we can see the most significant correlation for the individual sentiment variable on the x axis and filing date return on the y axis.
An important observation from this figure is the slope of the graphs, which can yield insight into return movements for the filing date based on the sentiment variable analyzed.

---
**Top Correlations on Day Zero to Two Days After Filing**
<p align = "center">
    <img src="images/output5.png" alt = "My Image" width = auto height = auto/>
</p>

<p align = "center" style = "font-style: italic">
This figure shows the highest correlations for sentiment scores and day 0 - 2 after 10-k filing returns.
</p>

Similar to the previous figure, this figure shows the correlation for individual sentiment variables on the x axis and days 0 - 2 returns on the y axis. 
For this return time window, economic risk proximity yields the highest correlation with returns, tailed by growth initiatives proximity, and recovery path proximity.The wider time frame in this image provides insight to the movement of returns based on sentiment scores for these variables. 

---
**Top Correlations on Day Three to Ten Days After Filing**
<p align = "center">
    <img src="images/output6.png" alt = "My Image" width = auto height = auto/>
</p>

<p align = "center" style = "font-style: italic">
This figure shows the highest correlation scores between sentiment variables and returns 3 - 10 days after the 10-k filing date.
</p>

This figure shows that on the longer-run, overall sentiment has a higher correlation with returns in comparison to specific topic based measures.

