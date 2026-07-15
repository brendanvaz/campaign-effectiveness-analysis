# Campaign Effectiveness Analysis

Analysis of whether a major loyalty campaign in the Dunnhumby "Complete 
Journey" dataset drove incremental customer spend, using SQL (DuckDB) and 
Python.

## Question
Did households exposed to a large-scale loyalty campaign show a real 
increase in spend during the campaign period — and was this caused by the 
campaign, or by broader spending trends and pre-existing differences between 
customer groups?

## Method
* Compared each household's spend before vs. during the campaign (paired t-test)
* Built a control group of households not exposed to any overlapping campaign, to isolate the campaign's effect from general spending trends
* Identified selection bias: campaign households had 3.6x higher baseline spend than the control group, meaning the two groups were not directly comparable
* Corrected for this by restricting both groups to a shared baseline spend range (£100–£300) and re-running the comparison on this matched subset
* Confirmed the finding with a linear regression across the full dataset, controlling for baseline spend mathematically instead of manual matching (see `campaign_regression_analysis.ipynb`)

## Key finding
In the initial unmatched comparison, both campaign and control groups showed 
significant spend increases — making it unclear whether the campaign itself 
was responsible. After matching both groups on baseline spend, the campaign 
group still showed a significant increase (+£51.79, p<0.001), while the 
matched control group showed no significant change (+£5.46, p=0.52). A 
follow-up regression across the full dataset confirmed this — campaign 
exposure predicted a significant £38.77 increase in spend, holding baseline 
spend constant. Two independent methods converge on the same conclusion: 
Campaign 18 drove real incremental spend. See the notebooks for full analysis 
and discussion of limitations.

## Files
* `campaign_effectiveness_analysis.ipynb` — main analysis: naive comparison, control group, and baseline-matched correction
* `campaign_regression_analysis.ipynb` — regression extension, confirming the matched result across the full dataset

## Tools
SQL (DuckDB), Python (pandas, scipy, statsmodels), Jupyter Notebook

## Data
[Dunnhumby - The Complete Journey](https://www.kaggle.com/datasets/frtgnn/dunnhumby-the-complete-journey)
