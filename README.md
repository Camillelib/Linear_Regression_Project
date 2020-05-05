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
<b>1. Data collection</b>
<p>Dataset imported from : https://github.com/seankross/lego/tree/master/data-tidy</p>

<b>2. Data cleaning:</b>
 * Deleting 8 columns
 * Deleting ~2000 empty rows  
 * Reducing the number of themes
 * Replacing "Year" by "Age" to avoid time series
 * Creating dummies for non-numerical columns
 * Checking if the dataset has duplicates - does not have any
  
 * Convert numerical columns to be normally distributed using the boxcox method:
  
  Distribution in the dataset:
  ![Distribution](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Distribution_1.png?raw=true)
  
  Both are lognormally distributed. 
  
  Distribution after using the boxcox method with a lambda 0:
  ![Distribution_transformed](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Distribution_2.png?raw=true)
  
 * Identifying outliers:

 ![Outliers](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Outliers.png?raw=true)
 Solution: creating 2 new columns identifying outliers
  
<b>3. Regression analysis: </b>
 Dropping 9 more variables with the first analysis based on high pvalues
 
<b> 4. Checking the 5 assumptions for linear regression </b>
 
1. Multicollinearity

![Multicollineraity](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Correlations.png?raw=true)
 
Dropping 5 more columns, we checked the assumption.

2. Linearity

![Linearity](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Linearity.png?raw=true)

The assumption is verified

3. Autocorrelation

<p>The Durbin-Watson test shows a positive autocorrelation with a coefficient of 1.11</p>

4. Homoscedasticity

![Homoscedasticity](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Homoskedasticity.png?raw=true)

The assumption is potentially not verified.

5. Exogeneity of residuals

![Exogeneity](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Residuals.png?raw=true)

The assumption is not verified as the residuals don't follow a normal law according to the Anderson-Darling test (pvalue < 0.05)

## Results
The final linear regression model has a high R², however the 5 assumptions are not verified. 

The model equation: 
ln(y)= -0.21+1.8xOutliers_pieces+ β1xThemes+β2xPackagings+β3xAvailability+0.68xNumber_pieces

Result of the OLS model:
![Results](https://github.com/Camillelib/Linear_Regression_Project/blob/master/Output/Results.png?raw=true)
  

## Conclusion
The model can be used to explain the current prices of these lego sets however is not yet usable for predictions as all assumptions are not checked.

