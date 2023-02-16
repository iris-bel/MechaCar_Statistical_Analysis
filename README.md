# MechaCar Statistical Analysis

## Overview of Project

The purpose of this analysis is to review the production data of the MechaCar model to provide insights that might help the manufacturing team improve this specific prototype. 

## Linear Regression to Predict MPG

### Output of linear regression

Call
lm(formula = mpg ~ vehicle_length + vehicle_weight + spoiler_angle + 
    ground_clearance + AWD, data = MechaCar_mpg)

Residuals:
     Min       1Q   Median       3Q      Max 
-19.4701  -4.4994  -0.0692   5.4433  18.5849 

Coefficients:
                   Estimate Std. Error t value Pr(>|t|)    
(Intercept)      -1.040e+02  1.585e+01  -6.559 5.08e-08 ***
vehicle_length    6.267e+00  6.553e-01   9.563 2.60e-12 ***
vehicle_weight    1.245e-03  6.890e-04   1.807   0.0776 .  
spoiler_angle     6.877e-02  6.653e-02   1.034   0.3069    
ground_clearance  3.546e+00  5.412e-01   6.551 5.21e-08 ***
AWD              -3.411e+00  2.535e+00  -1.346   0.1852    

Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 8.774 on 44 degrees of freedom
Multiple R-squared:  0.7149,	Adjusted R-squared:  0.6825 
F-statistic: 22.07 on 5 and 44 DF,  p-value: 5.35e-11

### Analysis

Based on this linear regression, vehicle length and ground clearance all provide a non-random amount amount of variance to the mpg values in the dataset. They have a significant impact on mpg. However, the fact that the intercept is statistically significant means that there are other variables contibuting to mpg variation that have not been accounted for in this model.

We can state that there is sufficient evidence to reject our null hypthesis and that the slope of our linear model is not zero because the p-value of this analysis is 5.35e-11 which is much smaller than the assumed significance level of 0.05%.

The r -squared value of our linear regression model is 0.71 which means that roughly 71% of all mpg predictions will be correct when using this linear model. Nevertheless, the missing significant variables suggests overfitting, in which case the model might predict 71% of mpg predictions in this dataset but not in others.  

## Summary Statistics on Suspension Coils

### Output of Summary Statistics


### Analysis

As seen in the table above, the current manufacturing data for ALL lots does meet the design specification that the variance of the suspension coils must not exceed 100 PSI. However, this information is a bit misleading. When we look at the summary data we see that Lots 1 and 2 have a much lower variance in PSI (as low as 1 PSI). However, variance in Lot 3 is 170 PSI which far exceeds the variance allowed by the specification. 

## T-Tests on Suspension Coils

### Output of T-Tests

Summary Sample t-test

data:  suspension_coil$PSI
t = -1.8931, df = 149, p-value = 0.06028
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1497.507 1500.053
sample estimates:
mean of x 
  1498.78 

Lot 1 Sample t-test

data:  Lot1$PSI
t = 0, df = 49, p-value = 1
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1499.719 1500.281
sample estimates:
mean of x 
     1500 

Lot 2 Sample t-test

data:  Lot2$PSI
t = 0.51745, df = 49, p-value = 0.6072
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1499.423 1500.977
sample estimates:
mean of x 
   1500.2 

Lot 3 Sample t-test

data:  Lot3$PSI
t = -2.0916, df = 49, p-value = 0.04168
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1492.431 1499.849
sample estimates:
mean of x 
  1496.14 

### Analysis

The t-tests above reveal results that follow a similar pattern laid out by the summary statistics in the previous section. Based on the p value of 0.06, the t-test performed on the full sample does not provide evidence that the PSI of this sample group is statistically different from the population mean of 1,500, although it gets close to the statistically significant 0.05% threshold. 

Lots 1 and 2 have high p values, 1 and 0.6 respectively, revealing that they do not vary statistically from the population mean. Lot 3, however, has a p value of 0.04 which is less than our assumed significance level of 0.05% suggesting that this sample is statistically different from the population mean based on our significance criteria. Lot 3 seems to act as an outlier that skewed the p value for the t-test performed on the total sample population. 

## Study Design: MechaCar vs. Competition

The recent concerns over gas prices have made the customers at CarsRUs increasingly vigilant about checking their future car's fuel efficiency (both in the city and on the highway). In order to test the MechaCar's fuel efficiency compared to that of competitor brands, we will need a data set that shows the MechaCar's mpg both in the city and on the highway and similar data sets for the competing brands we are analyzing. When running our statistical tests, our null hypothesis would be that there is no statistical difference between the MechaCar's mpg performance and that of a competing brand. Our alternative hypothesis will be that the MechaCar will perform better (or worse, hopefully not...) than the competing brand in a statistically significant way.

From there we can perform a series of two sample t-tests. For instance, we can compare the MechaCar's overall mpg (including city and highway data) to the competitor's overall mpg, and then compare the MechaCar city mpg to competitor city mpg, the MechaCar highway mpg to competitor highway mpg, and so on.
