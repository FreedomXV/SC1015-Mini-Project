# Analysing Covid-19 Cases in US Counties
### Group Project for SC1015: Introduction to Data Science and Artificial Intelligence

## About
This Data Science focused project aims to model the spread of Covid-19 cases around US [Counties](https://en.wikipedia.org/wiki/County_(United_States))

### Contributors
Zaki | Shiqiang | Ming Wei

## Datasets
This project used data from the following [datasets](https://github.com/FreedomXV/SC1015-Mini-Project/tree/main/Foundation%20Datasets):

From Kaggle:
- [Covid-19 Dataset](https://www.kaggle.com/datasets/imdevskp/corona-virus-report?select=usa_county_wise.csv)

From the US Census Bureau:
- [Average Household Size and Population Density - County](https://covid19.census.gov/datasets/USCensus::average-household-size-and-population-density-county/about)
- [Health Insurance Coverage - Counties](https://covid19.census.gov/datasets/USCensus::health-insurance-coverage-counties-2015-2019/about)
- [Income and Benefits - Counties](https://covid19.census.gov/datasets/USCensus::income-and-benefits-counties-2015-2019/about)
- [Occupation by Sex - Counties](https://covid19.census.gov/datasets/USCensus::occupation-by-sex-counties-2015-2019/about)
- [Population and Poverty Status - Counties](https://covid19.census.gov/datasets/USCensus::population-and-poverty-status-counties-2015-2019/about)

## Problem Definition
How can we predict the severity of Covid-19 outbreaks in US [Counties](https://en.wikipedia.org/wiki/County_(United_States)), based on its demographic and geographic factors?

The final goal of this project is to extract relevant geographic and demographic factors which we can used to build a multivariate model that can predict the potential severity of outbreaks similar to Covid-19

### Univariate Distribution of Cases
Here is what the distribution of confirmed cases looks like, which is our response variable:
![response](https://user-images.githubusercontent.com/94072359/164878282-ffe76b13-7507-4fb2-93cc-5e824c5376d4.png)




## Data Cleaning
Cleaning the data sets consisted of merging all 6 data sets, and extracting the relevant columns, which we used as our predictor variables. We first tested each variable in a bivariate analysis in a smaller environment. Through this process, we selected what would be the most relevant factors that we would eventually include in our final multivariate model.

## Exploratory Data Analysis (EDA)
First, we conducted smaller EDAs on the focused demographic factors, which can be explored in their respective folders.

### [Healthcare Access EDA](https://github.com/FreedomXV/SC1015-Mini-Project/tree/main/Healthcare%20Access%20EDA):
In this folder you can find the Jupyter Notebook where we performed EDA for Healthcare Access for the following predictor variables:
- Total population without healthcare access
- Civilian noninstitutionalized population with Health Coverage
- Percent of Population with No Health Insurance Coverage

Using the results, we deemed **Total population without healthcare access** and **Percent of Population with No Health Insurance Coverage** to be statistically significant.

### [Occupation EDA](https://github.com/FreedomXV/SC1015-Mini-Project/tree/main/Occupation%20EDA):
In this folder you can find the Jupyter Notebook where we performed EDA for Occupation for the following predictor variables:
- Total - Civilian employed population 16 years and over
- Percentage of Healthcare related workers
- Total Healthcare-related workers	

To our surprise, our results showed that none of these factors were statistically significant to our desired response variable, and we made the choice to omit these variables from our final model.

### [Population EDA](https://github.com/FreedomXV/SC1015-Mini-Project/tree/main/Population%20EDA):
In this folder you can find the Jupyter Noteboook where we performed EDA for Population for the following predictor variables:
- Average Household Size
- Total Population
- Population Density (people per square kilometer)

From this study, we found that all three of these demographic factors, **Average Household Size**, **Total Population** and **Population Density** are statistically significant in predicting the response variable, and included all three in the final model.

### [Poverty EDA](https://github.com/FreedomXV/SC1015-Mini-Project/tree/main/Poverty%20EDA):
In this folder you can find the Jupyter Notebook where we performed EDA for Poverty for the following predictor variables:
- Households: Income Below Poverty Level (%)

Observing the results, we found this predictor to be insignificant, and did not include this in the final model.

## Machine Learning
### Models Used
Our team used a variety of models, making use of the SciKit-Learn, LightGBM and XGBoost libraries.
- Linear Regression
- Decision Tree Regressor
- Gradient Boosting
- Random Forest

### Linear Regression for Exploration
Univariate and Multivariate Linear Regression models for variables of similar demographic aspect (i.e population, healthcare access) were done in the respective EDA folders mentioned above for exploratory purposes to help us better understand our predictor variables.

### [Multivariate ML Models](https://github.com/FreedomXV/SC1015-Mini-Project/tree/main/Multivariate%20Machine%20Learning)
This folder contains all machine learning results obtained from the models used above.

#### The following response variables were used to build the models:
- Total confirmed cases up till 20th July 2020
- Case Incidence (Number of confirmed cases per 100000 population)

#### The following predictor variables were used to build the models:
- Percent of Population with No Health Insurance Coverage
- Average Household Size
- Total Population (only for models against confirmed case count)
- Population Density (people per square kilometer)
- Percentage of Households in Poverty (only for models against case incidence)

The models with response variable confirmed cases was used for the presentation as it consistently outperformed models with response variable case incidence. Poverty rate was used in models with case incidence as a stronger linear relationship existed between the two.

Separate models with and without outliers were built. Hyperparameter tuning via gridsearchcv was done on the best performing model without outliers which was XGBoost Random Forest.

## Individual Contribution
Zaki: Slides Content, Script, Presentation, Video editing, EDA, ML <br/>
Shiqiang: Slides Content, Script, Presentation, EDA, ML <br/>
Ming Wei: Slides Content, Slides Design, Script, Presentation, EDA

## References
- https://towardsdatascience.com/how-to-improve-the-accuracy-of-a-regression-model-3517accf8604
- https://lightgbm.readthedocs.io/en/latest/
- https://xgboost.readthedocs.io/en/stable/python/python_api.html
- https://xgboost.readthedocs.io/en/stable/parameter.html#parameters-for-tree-booster
- https://xgboost.readthedocs.io/en/stable/parameter.html#parameters-for-tree-booster
- https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.GradientBoostingRegressor.html
- https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/
- https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html
