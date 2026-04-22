# Project Code 
This file includes any code for this project. 

## Project Overview
This project examines whether tornado hazard in the United States is shifting from the traditional Great Plains Tornado Alley toward the Southeast's Dixie Alley region over time, and whether counties predicted to exhibit elevated tornado hazard in the following year also have greater present-day insurance exposure based on population, housing units and median home value. 
The hypothesis is that tornado hazard is shifting from the Tornado Alley region toward Dixie Alley due to increasing tornado frequency and severity in the Southeast over time. It is predicted that counties located in Dixie Alley will be more likely classified as high tornado hazard in the following year compared to Tornado Alley and will exhibit a higher present-day insurance exposure.

## Data Sources (located under raw-data-sets)
- NOAA Severe Weather Database Files (All U.S. Tornadoes 1950-2024)
- U.S. Census ACS 2024 (utilized via tidycensus in R)

## Requirements for Code
- RStudio Version 2024.12.1+563
- Packages Used: ggplot2, dplyr, tidycensus, PRROC, randomForest
- Libraries: ggplot2, dplyr, tidyr, stringr, tidycensus, e1071, reshape2, caret, PRROC, randomForest, glmnet, xgboost

## Target Variable
- Utilized a composite hazard score. This used Z-scores for target variable's hazard variables to allow standardization then create a composite hazard score with an average of all standardized variables: tornado_count_county_year, average_intensity_county, max_intensity_county, strong_tornado_count, log_property_loss 
- Defining the hazard cutoff for binary classification: This was originally set at 75%, however, it was adjusted to 65% to allow for better performance (aka the top 35% of county-years will be classified as high-risk). Binary classification of 1 = high-risk and 0 = not high-risk.

## Testing, Validation & Reproducibility
This code has been self-tested to ensure successful reproducibility. Code was executed using RStudio using all packages and libraries listed above. It has not been user-tested on a separate machine due to lack of availability, however, all necessary compenents are documented for assistance with reproducibility. 
