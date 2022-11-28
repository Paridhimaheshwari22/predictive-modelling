# predictive-modelling
BenCare Customer Loyalty Assignment- Objective

Bencare Insurance has collected customer data and wants to understand the important factors that influence their customer loyalty. We were asked to build a predictive model  that fulfills the following requirements- (a) has high R-square, (b)  few Predictors, (c) is robust and not biased by violations, and (d) includes important interaction and quadratic terms.
Usage Instructions
Change the data files directory paths, including the BenCare Data Description.xlsx and BenCare_2022_ASN10.csv to get the prediction results. Then change the output directory into your preferred location. The programming output will output the prediction results.

Background

The variable definitions are provided in the BenCare Data Description.xlsx, containing both main and control variables. We have created required data frames, added categorical descriptors of dummy variables for age, and created dummy variables for age, sex, education. We examined the data, performed initial transformations, and dropped unneeded variables like the location and CaseID.

Methodology

We estimated close to 40 models, first using ordinary least square linear regression, and understanding the interaction of control variables with the main effects model but later dropped this approach after running into a significant number of outlier observations. We then continued estimating with robust regression models and built a base main effects model without interactions and got an adjusted R squared value of 0.8035, after performing log transformations in our attempt to normalize the left skew we observed to the dependent variable and many of the independent variables. We also performed the linearity, normality, homoscedasticity, and independence tests and found the data to be not normally distributed. Given the lack of normality of the residuals, we continued to utilize a robust linear regression algorithm. We then continued with identifying the significant interactions between independent variables. After several iterations, we identified the significant interactions and included them with the main effects model to estimate a robust model  that had adjusted R square close to 0.86. However, we found severe multicollinearity between interactions and main effects that we were unable to mitigate using either centered values or standardized values for the main effects. We also tried removing the outliers’ observations to estimate a better robust regression model, but this approach failed, as we repeatedly removed several observations with each iteration. So instead, we decided not to include any interactions in the model despite the improvements in the adjusted R-squared value  and decided to only use the previously estimated robust regression main effects model.

Result

Log-transformed Robust regression main effects model  without interactions used following variables- log_loyalty, log_reputa, log_value, log_satis, age_cat_25_34, age_cat_35-44, age_cat_45-54, age_cat_55+, edu_cat_Graduate, edu_cat_Some College, edu_cat_High School . It yielded an Adjusted R squared value of 0.8035. Severe multicollinearity was found in log_value at 11.32, log_satis at 7.23 and log_ctrust at 8.86. The Shapiro-Wilk test for Normality failed with W= 0.856, p-value = 3.883e-16. However, we utilized a robust linear algorithm to address the lack of normality. The Durbin-Watson test of independence passed  with DW= 2.0356, p-value = 0.8098.
Regression Equation: log_loyalty = -0.1628 + 0.1601*log_reputa + 0.4653*log_value + 0.1645*log_satis - 0.0473*age_cat_25_34 - 0.0343*age_cat_35-44 - 0.0416*age_cat_45-54 – 0.0075*age_cat_55 - 0.0705*edu_cat_Graduate – 0.0012*edu_cat_Some College – 0.0233* edu_cat_High School + 0.2166
