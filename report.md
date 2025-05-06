---
layout: wide_default
---        

## 10K Sentiment and Returns

Edgard J. Cuadra

_Abstract and Methodology_

To access any of the files or folders referenced in this report, please refer to the following GitHub repository: [10-k Sentiment Repository](https://github.com/edgardjcuadra/asgn-05-edgardjcuadra)

In this report, we analyze 10-K filings for S&P 500 firms to assess sentiment and examine its correlation with stock returns following the filing dates. Using Python, we first load two dictionaries of positive and negative words, along with a master dictionary that classifies word sentiment. We then iterate through the documents, extracting relevant words into lists and data frames. Based on the master dictionary, we define several sentiment variables for analysis, including:

1. Bad news  
2. Good news  
3. Neutral words  
4. Mildly positive words  
5. Words describing catastrophic events  
6. Words describing turning points  

These classifications are derived from each word’s sentiment rating, grouping them into positive, negative, or neutral categories.

Additionally, we develop topic specific indicators using a `NEAR_Regex` function—designed to identify clusters of context-specific words, to detect whether certain themes are associated with positive or negative implications. The identified topics include:

1. **Bankruptcy risk** – e.g., "bankruptcy", "insolvency", "default"  
2. **Growth initiatives** – e.g., "expansion", "acquisition", "growth", "scaling"  
3. **Legal exposure** – e.g., "lawsuit", "litigation", "penalty"  
4. **Economic risk** – e.g., "volatility", "instability", "fluctuation"  
5. **Recovery path** – e.g., "recovery", "rebound", "turnaround"  

We scrape the `.html` versions of the 10-K filings, iterating through each to identify sentiment and topic indicators. During this process, we track the ratio of sentiment related words to the document length, as well as the frequency and proximity of topic-specific keywords indicating potential risks or opportunities.

After calculating sentiment scores, we merge the sentiment dataset with a file containing stock return data.

To conclude the analysis, we construct three data frames that aggregate returns for each firm at various intervals following their 10-K filing date. We then perform a correlation analysis to explore the relationship between our sentiment variables and these post-filing returns.

**A few important notes about correlation before interpreting the results:**

1. Correlation describes **linear association**, not **causation** or directionality.
    - A positive correlation means that when one variable is above its mean, the other tends to be above its mean as well (and vice versa).
    - It does **not** imply that changes in sentiment cause changes in stock returns.

2. The **sign** of the correlation indicates direction, not causality.
    - A positive value means the variables move together; a negative value means they move in opposite directions.

3. **Magnitude** indicates the strength of the linear relationship.
    - Correlation coefficients range from -1 (perfect negative correlation), to 0 (no correlation), to +1 (perfect positive correlation).
    - For example, a correlation of 0.89 is very high, indicating a strong linear association. If r = 0.89, then r² = 0.79, suggesting that approximately 79% of the variability in one variable can be explained by a simple linear model using the other.

## Findings

**Sentiment Variable Correlations Across Different Time Windows**

<p align="center">
    <img src="images/output7.png" alt="Correlation Heatmap" width=auto height=auto />
</p>

<p align="center" style="font-style: italic">
This heatmap presents return correlations from the day of the 10-K filing, 0–2 days post-filing, and 3–10 days post-filing, relative to sentiment variables. 
There are 10 distinct sentiment metrics represented.
</p>

This table highlights the highest correlations across sentiment variables and post-filing return periods. The **Growth Initiatives** variable shows the strongest correlation with returns on the day of filing, with a coefficient of `0.89`. This is followed by **Recovery Path Proximity**, **Economic Risk Proximity**, and **Bankruptcy Risk Proximity**.

---

**Top Correlations on Filing Day Returns**

<p align="center">
    <img src="images/output4.png" alt="Filing Day Correlations" width=auto height=auto />
</p>

<p align="center" style="font-style: italic">
This figure displays the sentiment variables with the highest correlations to returns on the day the 10-K was filed.
</p>

The graph visualizes individual sentiment variables (x-axis) against same-day returns (y-axis). One key insight is the slope of the trend lines, which may provide predictive value on how certain sentiment indicators align with immediate market reactions.

---

**Top Correlations from Day 0 to Day 2 After Filing**

<p align="center">
    <img src="images/output5.png" alt="Day 0–2 Correlations" width=auto height=auto />
</p>

<p align="center" style="font-style: italic">
This figure presents the strongest correlations between sentiment variables and stock returns over the 0–2 day window post-filing.
</p>

As with the prior figure, sentiment variables are on the x-axis and corresponding returns on the y-axis. In this window, **Economic Risk Proximity** has the highest correlation, followed by **Growth Initiatives Proximity** and **Recovery Path Proximity**. This broader time frame captures delayed investor reactions to specific disclosures in the filings.

---

**Top Correlations from Day 3 to Day 10 After Filing**

<p align="center">
    <img src="images/output6.png" alt="Day 3–10 Correlations" width=auto height=auto />
</p>

<p align="center" style="font-style: italic">
This figure highlights the top correlations between sentiment measures and returns 3–10 days after the 10-K filing.
</p>

This longer-term view reveals that **overall sentiment**, as opposed to topic-specific variables—, xhibits stronger correlations with stock performance. This may suggest that the broader tone of the filing has a sustained influence on investor expectations and market valuation.
