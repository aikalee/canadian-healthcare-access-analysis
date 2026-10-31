Canadian Specialist Wait-Time Analysis

## Overview

This project analyzes provincial differences in specialist wait-time outcomes in Canada, with a particular focus on British Columbia. Using Statistics Canada survey data, the analysis compares prolonged specialist wait times with patient-reported outcomes to examine whether conventional wait-time measures adequately reflect patients’ experiences.

The analysis was conducted using PostgreSQL and SQL for data querying and aggregation, and Python (pandas and matplotlib) for statistical analysis and visualization.

## Research Questions

1. How does British Columbia perform relative to other Canadian provinces across specialist wait-time indicators?
2. How are prolonged specialist wait times, reported life impact, and patient dissatisfaction related across Canadian provinces?

## Data

The analysis uses Statistics Canada survey estimates on access to specialist care and wait-time experiences.

The dataset contains provincial estimates stratified by demographic groups and includes both estimated population counts and percentages for indicators such as:

* total population reporting a specialist wait time;
* wait times of six months or longer;
* reported impact of wait times on patients’ lives; and
* dissatisfaction with specialist wait times.

The analysis focuses on the 10 Canadian provinces and excludes the national aggregate when calculating provincial rankings and comparisons.

## Methodology

Data querying and aggregation

The data was loaded into PostgreSQL and queried using SQL. Common table expressions (CTEs), filtering, aggregation, and joins were used to construct province-level measures from the survey data.

Where subgroup estimates were provided, population counts were aggregated to calculate province-level rates rather than taking unweighted averages of subgroup percentages.

Denominator validation

Before calculating patient-reported outcome rates, the denominator implied by each indicator’s reported population count and percentage was compared with the reported total specialist wait-time population.

Across all geographies, the inferred denominators differed from the reported total wait-time population by only 0.07%–0.31%, supporting the use of the total specialist wait-time population as the denominator. Small discrepancies are consistent with rounding in the published estimates.

## Provincial benchmarking

British Columbia was compared with the other Canadian provinces using three measures:

* proportion waiting six months or longer;
* proportion reporting that wait time affected their life; and
* proportion dissatisfied or very dissatisfied with wait time.

Provincial rankings were used to describe BC’s relative position without imposing arbitrary thresholds for “good” or “poor” performance.

## Correlation analysis

Pearson correlations were calculated across the 10 provinces to explore relationships among prolonged wait times, reported life impact, and dissatisfaction.

Because the analysis contains only 10 provincial observations and uses aggregate survey estimates, correlations are treated as exploratory descriptive relationships, not causal evidence.

## Key Findings

1. British Columbia performs relatively well on prolonged waits but poorly on patient-reported outcomes

British Columbia had the second-lowest proportion of patients waiting six months or longer, at approximately 18.8%.

However, patient-reported outcomes showed a different pattern:

* BC had the second-highest rate of reported life impact, at approximately 67.7%.
* BC had the third-highest dissatisfaction rate, at approximately 33.4%.

This indicates a notable discrepancy between the prevalence of very long waits and patients’ reported experiences in British Columbia.

2. The six-month wait threshold was not strongly associated with patient-reported outcomes

Across provinces, the proportion waiting six months or longer was:

* essentially uncorrelated with reported life impact (r = -0.05); and
* weakly negatively correlated with dissatisfaction (r = -0.29).

In contrast, reported life impact and dissatisfaction were strongly positively correlated (r = 0.72).

These results suggest that the prevalence of waits lasting six months or longer, when considered alone, may not adequately capture patients’ experience of specialist wait times. Measures of patient-reported impact may provide additional information that is not reflected by this duration threshold.

## Limitations

This analysis has several important limitations:

* Aggregate data: The dataset contains provincial survey estimates rather than individual patient-level observations. Relationships observed at the provincial level should therefore not be interpreted as individual-level relationships.
* Small number of observations: Cross-provincial correlations are based on only 10 provinces and should be interpreted as exploratory.
* No causal inference: Correlation does not establish that wait duration causes changes in life impact or dissatisfaction.
* Limited wait-time measure: The six-month-or-longer indicator represents only one threshold in the wait-time distribution. A weak relationship with this indicator does not imply that wait duration itself is unimportant.
* Survey and rounding uncertainty: Published counts and percentages are rounded survey estimates, resulting in small discrepancies when denominators are reconstructed.
* Unobserved factors: Differences in patient experience may reflect factors not captured in this analysis, such as type or urgency of specialist care, expectations, health status, or other characteristics of healthcare delivery.

## Tools

* PostgreSQL / SQL — data querying, filtering, aggregation, CTEs, and joins
* Python
* pandas — data manipulation and statistical analysis
* matplotlib — data visualization

## Summary

The analysis demonstrates that provincial performance on a single prolonged-wait threshold does not necessarily align with patient-reported experience. British Columbia illustrates this distinction particularly clearly: despite having a relatively low proportion of specialist waits lasting six months or longer, it reported comparatively high levels of life impact and dissatisfaction.

The findings highlight the value of examining multiple complementary healthcare indicators rather than relying on a single wait-time threshold when assessing patient experience.
