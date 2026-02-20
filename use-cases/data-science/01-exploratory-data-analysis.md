# Use Case: Exploratory Data Analysis

## Objective

Ask the AI tool to perform a complete EDA on an unfamiliar dataset. Tests the tool's ability to understand data, generate meaningful insights, produce quality visualizations, and work with pandas/notebook workflows.

## The Task

Perform a thorough EDA on a public dataset. Suggested options (pick one, use the same for both tools):

- **Titanic dataset**: `seaborn.load_dataset('titanic')` or [Kaggle](https://www.kaggle.com/c/titanic)
- **NYC Taxi data**: [TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page) (use a small sample)
- **Your own dataset**: Any CSV you have on hand that the tool hasn't seen before

### What the EDA Should Cover

1. **Data overview**: Shape, dtypes, missing values, basic statistics
2. **Data quality assessment**: Duplicates, outliers, inconsistencies
3. **Univariate analysis**: Distribution of key variables
4. **Bivariate analysis**: Relationships between variables
5. **Key insights**: 3-5 non-obvious findings from the data
6. **Visualizations**: At least 5 well-formatted charts

## Acceptance Criteria

- [ ] Data is loaded and basic info is displayed (shape, types, nulls)
- [ ] Missing values are identified and a strategy is discussed
- [ ] At least 5 visualizations are produced (histograms, scatter, correlation, etc.)
- [ ] Visualizations have titles, labels, and appropriate formatting
- [ ] Non-obvious insights are identified (not just "column X has 10% nulls")
- [ ] Code runs end-to-end without errors

## Suggested Prompt

> "Perform a thorough exploratory data analysis on this dataset. I want to understand the data quality, distributions, relationships between variables, and any interesting patterns. Generate visualizations for key findings."

## What to Observe

- Does it ask about the data or dive in? (Both can be valid)
- How well does it handle missing values — does it just count them or suggest strategies?
- Are the visualizations insightful or generic?
- Does it find genuinely interesting patterns or just describe obvious things?
- How well does it work with Jupyter notebooks vs. scripts?
- Does it use appropriate chart types for the data (e.g., not a pie chart for 50 categories)?
- Does it format charts properly (labels, titles, color schemes)?
