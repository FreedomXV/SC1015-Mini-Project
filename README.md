# Tracking Covid Cases in US Counties
### Group Project for SC1015: Introduction to Data Science and Artificial Intelligence

## About
This Data Science focused project aims to model the spread of Covid-19 cases around US [Counties](https://en.wikipedia.org/wiki/County_(United_States))

### Contributors
Zaki

Shiqiang

Ming Wei

## Data Sets
This project used data from the following data sets:

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

### Healthcare Access EDA
In this folder you can find the Jupyter Notebook where we performed EDA for Healthcare Access for the following predictor variables:
- Total population without healthcare access
- Civilian noninstitutionalized population with Health Coverage
- Percent of Population with No Health Insurance Coverage

Using the results, we deemed **Total population without healthcare access** and **Percent of Population with No Health Insurance Coverage** to be statistically significant.

### Occupation EDA
In this folder you can find the Jupyter Notebook where we performed EDA for Occupation for the following predictor variables:
- Total - Civilian employed population 16 years and over
- Percentage of Healthcare related workers
- Total Healthcare-related workers	

To our surprise, our results showed that none of these factors were statistically significant to our desired response variable, and we made the choice to omit these variables from our final model.

### Population EDA
In this folder you can find the Jupyter Noteboook where we performed EDA for Population for the following predictor variables:
- Average Household Size
- Total Population
- Population Density (people per square kilometer)

From this study, we found that all three of these demographic factors, **Average Household Size**, **Total Population** and **Population Density** are statistically significant in predicting the response variable, and included all three in the final model.

### Poverty EDA
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

### Predictor Variables
The following predictor variables were used to build the model:
- Percent of Population with No Health Insurance Coverage
- Average Household Size
- Total Population
- Population Density (people per square kilometer)

As a note, we dropped **Total population without healthcare access** as a predictor variable, since we included **Total Population**. Our team felt having both predictors included would not accurately represent the data as **Total population without healthcare access** is heavily influenced by **Total Population** as well.

### Multivariate Exploratory Data Analysis
In the folders you can find the Jupyter Notebook where we performed various multivariate analysis on the predictor variables against response variables to build our models. The models used can be found above in the *Machine Learning* section.
 
## Regression Analysis
## Population EDA
We used regression analysis with **Confirmed** case count as our response variable and **Average Household Size**, **Total Population** and **Population Density** as our predictor variables. We randomly split the datasets into 80:20 datasets, with *train* containing 80% of the dataset while *test* containing 20% of it. Before that, we first remove the outliers from the dataset to better improve the accuracy of our models. Then, we use linear regression to train our *train* dataset which will be then used to predict our *test* dataset. After that, we will measure the goodness of fit of our model using Explained Variance (R ^ 2) and Mean Squared Error. 

## Healthcare EDA
The same is done on the ***Healthcare Demographics*** with predictor variable **Percentage of Population without Healthcare Insurance**.

We then made use of a variety of machine learning models to try to model our data to accurately predict **Confirmed** cases based on the predictor variables that we have previously chosen. The machine learning models that we have used besides Linear Regression are Decision Tree Regressor, from Sci-Kit; Gradient Boosting, of which we used three different kinds of models from Sci-Kit, lightGBM, and XGBoost, and finally Random Forest, from XGBoost.
