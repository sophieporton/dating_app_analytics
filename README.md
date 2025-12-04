# Dating App A/B Test Analysis

## Project Overview
This project analyzes the results of an A/B test conducted for a dating application. The goal was to evaluate three different user interface variants (A, B, and C) to determine which drives the highest conversion rate and revenue, and whether there is a statistically significant difference in the time it takes for a user to convert.

## Tech Stack
* **Language:** Python 3
* **Data Manipulation:** Pandas, NumPy
* **Database:** SQLite3
* **Visualization:** Matplotlib, Seaborn
* **Statistics & Machine Learning:** Scipy, Statsmodels, Scikit-learn

## Data Structure
The analysis utilizes three primary datasets:
1.  **`impressions.csv`**: User ad impressions and activity logs.
2.  **`transactions.csv`**: Records of payments/conversions (revenue).
3.  **`user_experiment_variants.csv`**: Mapping of users to their assigned test variant (A, B, or C).

## Methodology

### 1. ETL & Data Wrangling
* Ingested raw CSV data into a local **SQLite database** to perform SQL-based joins and filtering.
* Created a master table `conversion_rate` merging user assignments with transaction timestamps.
* engineered features such as `sec_diff` (time taken from entering the test to purchasing) and a binary `converted` flag.

### 2. Exploratory Data Analysis (EDA)
* Analyzed the distribution of users across variants.
* Visualized temporal patterns (Day of Week, Hour of Day) to identify peak usage times.
* Plotted revenue distribution by variant.

### 3. Statistical Analysis
* **Chi-Square Test:** Used to determine if the difference in conversion rates between groups was statistically significant.
* **Power Analysis:** Conducted using `statsmodels` to assess the statistical power of the test given the sample size and effect size.
* **Normality Tests:** Applied Shapiro-Wilk and Kruskal-Wallis tests to check the distribution of time-to-conversion data.

### 4. Modeling
* **Logistic Regression:** Built to quantify the odds of conversion based on the variant.
* **Linear Regression:** Used to predict the time (in seconds) taken to convert based on the assigned variant.

## Key Findings
* **Revenue:** Variant B generated the highest total revenue (£2,948.82), followed by A and C.
* **Conversion Rate:** Variant B showed a slightly higher conversion rate (approx. 5.8%) compared to A (5.0%) and C (4.6%).
* **Statistical Significance:** The Chi-square test yielded a p-value of ~0.24, indicating that the differences in conversion rates are likely due to chance rather than the variants themselves.
* **Time to Convert:** Linear regression suggested Variant C users might convert faster, though the R-squared value was low, indicating other factors drive conversion speed.

## Conclusion
While Variant B performed best numerically in terms of revenue and conversion percentage, statistical tests suggest the results are not significant at the 95% confidence level. Further testing or a larger sample size may be required to draw concrete conclusions.