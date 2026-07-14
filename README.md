# Campaign Effectiveness Analysis

Analysis of whether a major loyalty campaign in the Dunnhumby "Complete 
Journey" dataset drove incremental customer spend, using SQL (DuckDB) and 
Python.

## Question
Did households exposed to a large-scale loyalty campaign show a statistically 
significant increase in spend during the campaign period — and was this 
specific to the campaign, or part of a broader trend?

## Method
- Compared each household's spend before vs. during the campaign (paired t-test)
- Built a control group of households not exposed to any overlapping campaign, 
  to isolate the campaign's effect from general spending trends
- Identified and addressed selection bias in the campaign-targeted population

## Key finding
Both campaign and control groups showed statistically significant spend 
increases over the period, and campaign households had a 3.6x higher baseline 
spend than the control group — indicating the campaign was targeted at 
already high-value customers, not a random sample. This makes it difficult to 
attribute the spend increase to the campaign alone. See the notebook for full 
analysis and discussion of this limitation.

## Tools
SQL (DuckDB), Python (pandas, scipy), Jupyter Notebook

## Data
[Dunnhumby - The Complete Journey](https://www.kaggle.com/datasets/frtgnn/dunnhumby-the-complete-journey)
