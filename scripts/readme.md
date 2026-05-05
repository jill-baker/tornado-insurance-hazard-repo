## Project Overview
This project examines whether tornado hazard in the United States is shifting from the traditional Great Plains Tornado Alley toward the Southeast's Dixie Alley region over time, and whether counties predicted to exhibit elevated tornado hazard in the following year also have greater present-day insurance exposure based on population, housing units and median home value. 
The hypothesis is that tornado hazard is shifting from the Tornado Alley region toward Dixie Alley due to increasing tornado frequency and severity in the Southeast over time. It is predicted that counties located in Dixie Alley will be more likely classified as high tornado hazard in the following year compared to Tornado Alley and will exhibit a higher present-day insurance exposure.

## Research Questions
1.	Is tornado hazard in the United States shifting geographically from Tornado Alley to Dixie Alley over time?
2.	Are counties with elevated tornado hazard associated with higher insurance exposure?

## Hypothesis and Prediction
The hypothesis is that tornado hazard is shifting from the Tornado Alley region toward Dixie Alley due to increasing tornado frequency and severity in the Southeast over time. It is predicted that counties located in Dixie Alley will be more likely classified as high tornado hazard in the following year compared to Tornado Alley and will exhibit a higher present-day insurance exposure. 

## Data Sources (located under raw-data-sets)
- NOAA Severe Weather Database Files (All U.S. Tornadoes 1950-2024)
   1950-2024_all_tornadoes.csv
- U.S. Census ACS 2024 (utilized via tidycensus in R)
    acs_county_population_2024.csv
    acs_county_housing_units_2024.csv
    acs_county_median_value_2024.csv

## Requirements for Code
- RStudio Version 2024.12.1+563
- Packages Used: ggplot2, dplyr, tidycensus, PRROC, randomForest

## Required Packages 
- library(ggplot2)
- library(dplyr)
- library(tidymodels)
- library(tidyr)
- library(stringr)
- library(tidycensus)
- library(e1071)
- library(reshape2)
- library(caret)
- library(PRROC)
- library(randomForest)
- library(glmnet)
- library(xgboost)

## Project Structure
- /scripts
  Includes full pipeline

## How to Run
- Clone repo
- Open R project




## Target Variable
- A binary classification predicting high tornado hazard next year-
- Created using a composite hazard score:
  Tornado count
  Average intensity
  Maximum intensity
  Strong tornado count
  Log-transformed property loss
- Standardized using z-scores
- Threshold:
  Originally 25% (75th percentile0
  Adjusted to 35% (65th percentile) to prioritize recall and reduce missed high-risk counties
- Binary classification of 1 = high-risk and 0 = not high-risk.

## Modeling Approach 
- Logistic Regression (baseline)
- random forest
- XGBoost (final selected model)

## Evaluation Metrics
- Recall: Primary method of priotitization to identify high-risk counties
- PR-AUC

## Validation
- Time-based train/test split
  Train: 1979-2014
  Test: 2015-2024
- Cross-Validation
  Stratified k-fold: k=5
  repeated k-fold: k=5, repeats=3
- Hyperparameter Tuning
  Randomized Search

## Results
- XGBoost performed the most balanced
  High Recall: 91%
  Highest PR-AUC: 0.71
  Strong balance between false positives and false negatives
- Support geographic shift in tornado hazard from Tornado Alley towards Dixie Alley
- Dixie Alley
  Lower average population and median house value
  Meaningful insurance exposure with higher proportion of top 25% median home value

## Limitations
- Assumes independence despite spatial and temporal dependencies
- Missing data (unknown observations) that may introduce bias
- Insruance exposure not actual insurance claims
- Does not account for climate change

## Future Work
- Incorporating spatial modeling
- Include insurance claims data
- Include climate trend data

## Testing, Validation & Reproducibility
This code has been self-tested to ensure successful reproducibility. Code was executed using RStudio using all packages and libraries listed above. It has not been user-tested on a separate machine due to lack of availability, however, all necessary compenents are documented for assistance with reproducibility. 
