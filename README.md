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
![Capture](https://user-images.githubusercontent.com/94072359/164874324-345aadb3-67ef-4b59-9361-714c440a4fe8.PNG)

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

