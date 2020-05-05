# Predicting the price of a Lego Set with linear regression

![Lego](https://www.lego.com/cdn/cs/set/assets/blt43d71bdb7a2ee793/pick-a-brick-banner-background-large.jpg?width=1320&height=200&dpr=1)


## Overview
Using a linear regression model, can we help predict the price of a lego set based on specific variables?

## Process followed

### Librairies used
* pandas
* statsmodels
* scipy.stats
* matplotlib.pyplot

### Steps
* Dataset imported from : 
* Data cleaning: 
  * Deleting 8 columns
  * Deleting ~2000 empty rows
  * Reducing the number of themes
  * Replacing "Year" by "Age" to avoid time series
  * Creating dummies for non-numerical columns
  * Checking if the dataset has duplicates - does not have any
  * Convert numerical columns to be normally distributed using the boxcox method:
  
  * Identifying outliers:
  
  
 * Regression analysis:
 Dropping 9 more variables with the first analysis based on high pvalues
 
 
 * Checking the 5 assumptions for linear regression:
 
1. Multicollinearity
Dropping 5 more columns, we checked the assumptions.

2. Linearity
The assumption is verified

3. Autocorrelation
The Durbin-Watson test shows a positive autocorrelation with a coefficient of 1.11

4. Homoscedasticity
The assumption is potentially not verified as the variance is increasing

5. Exogeneity of residuals
The assumption is not verified as the residuals don't follow a normal law according to the Anderson-Darling test (pvalue < 0.05)

## Results
The final linear regression model has a high pvalue, however the 5 assumptions are not verified. 

The model equation: 
ln(y)= -0.21+1.8*Outliers_pieces+ β1*Themes+β2*Packagings+β3*Availability+0.68*Number_pieces

