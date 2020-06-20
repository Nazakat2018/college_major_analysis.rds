# college_major_analysis.rds
1. We are conducting research on the ways that people use data analysis and data science tools. Your participation in this non-graded and completely optional peer assessment will be part of that research. We will not collect any personally identifiable information about you for the purposes of this research and only aggregated totals of responses to questions will be reported. The potential risks to you are small. The potential benefits to the community of data scientists, developers, and professors are very high – we will be able to figure out which methods work and which methods do not. This exercise is 100% optional and will not have any influence whatsoever on your grade in the class. Thanks for considering helping us learn about data science!

Jeff + Roger + Brian

It has been widely noted that there is a relationship between x1 and y. We are interested in studying the magnitude of this relationship and reporting results to the president of the company. Using the data available at



Use a linear regression model to investigate this relationship.

Would you be confident telling the company president that there is a meaningful relationship between x1 and y?

No
2. Report the estimated coefficient for x1 from your model to 6 significant digits.

4.03520
Explanation:
3. Report the 95% confidence interval for the coefficient for x1 from your model. Use 6 significant digits for both the lower and upper bounds. Report it in the format:

(Lower Bound, Upper Bound)
3.915693 4.154714
Explanation:
4. Report the p-value associated with the coefficient for x1 from your model to 6 significant digits. Use scientific notation.

9.061134e-249
Explanation:
5. Copy and paste the code that you used for your analysis, including any exploratory analysis.

****
Explanation:

data <- read.csv("opt.csv")
head(data)
##           y       x1       x2       x3
## 1  852.3656 181.2064 62.46470 150.9062
## 2 1013.0280 205.5093 74.78887 163.0869
## 3  891.4585 174.9311 50.66267 154.9904
## 4 1236.8196 247.8584 96.39904 193.3458
## 5  863.6771 209.8852 29.46853 154.1846
## 6  727.6746 175.3859 23.12800 139.2999
fit_x1 <- lm(y~x1,data=data)
fit_all <- lm(y~., data=data)
summary(fit_x1)
## 
## Call:
## lm(formula = y ~ x1, data = data)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -164.572  -48.630   -1.861   49.181  170.498 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept) 90.77375   19.33019   4.696 3.44e-06 ***
## x1           4.13185    0.09524  43.383  < 2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 64.59 on 498 degrees of freedom
## Multiple R-squared:  0.7908, Adjusted R-squared:  0.7903 
## F-statistic:  1882 on 1 and 498 DF,  p-value: < 2.2e-16
summary(fit_all)
## 
## Call:
## lm(formula = y ~ ., data = data)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -133.59  -27.18    0.05   28.48  148.47 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept) 13.14843   20.17481   0.652   0.5149    
## x1           4.03520    0.06083  66.339   <2e-16 ***
## x2           2.13295    0.07899  27.003   <2e-16 ***
## x3          -0.15383    0.08836  -1.741   0.0823 .  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 41.17 on 496 degrees of freedom
## Multiple R-squared:  0.9153, Adjusted R-squared:  0.9148 
## F-statistic:  1787 on 3 and 496 DF,  p-value: < 2.2e-16
summary(fit_all)$coef
##               Estimate  Std. Error   t value      Pr(>|t|)
## (Intercept) 13.1484281 20.17481007  0.651725  5.148805e-01
## x1           4.0352037  0.06082712 66.338895 9.061134e-249
## x2           2.1329532  0.07898888 27.003209  1.873017e-99
## x3          -0.1538264  0.08836054 -1.740895  8.232202e-02
summary(fit_all)$coef[2]+c(-1,1)*qt(.975,496)*summary(fit_all)$coef[6]
## [1] 3.915693 4.154714
