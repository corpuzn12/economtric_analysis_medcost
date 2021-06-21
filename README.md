# economtric_analysis_medcost
A rudimental Econometric analysis of medical cost using R. This project was a graded coursework for [ECON 620:](https://catalog.usfca.edu/preview_course_nopop.php?catoid=22&coid=186578)

Markdown Version: https://rpubs.com/corpuzn12/783138

## Data Set Introduction 
The data set was sourced from Kaggle: <https://www.kaggle.com/mirichoi0218/insurance>
The dataset has 6 columns: 
<ul>
<li>age=  patient age in years</li>
<li>sex=  biological sex of the patient</li>
<li>Bmi=  body mass index measured in kg/m^2. BMI is a measure of body fat where bmi > 25 is considered overweight , bmi> 30 is considered obese and bmi > 35  is extremely obese</li>
<li>children= number of children  </li>
<li>charges= medical cost in dollars </li> 
</ul>
For our purposes, the variables sex and smoker were coverted to binary variables where:
<ul>
<li>sex_code= value is 1 when if patient is female; 0 otherwise </li>
<li>smoker_code= value is 1 when if patient has smoking history ; 0 otherwise</li> 
</ul>

<p>This dataset does not have any missing values and contains 1,338 unique patient entries.We are not going to include the number of children in any of our analysis. Without a formal literature review, we suspect that bmi, smoking history and gender might be relevant indicators for medical cost.  It should be noted that the dataset does not contain any data on diagnosis types and therefore any conclusions that we derive from this data set is bound to be very general.</p> 

## Analysis
**Fixed Functional Form**
<ul>
<li>Dependent Variable= log(charges)</li>
<li>Independent Variables = age , bmi, smkr and bmi_smkr </li>
<li>Dummy variable= smkr </li>
  <li>Interaction variable = bmi_smkr</li>
</ul>
<p>Now, we are using log on the variable 'charges' in order to fix the positive skew in 'charges'. The semi-log form also helps us provide a better interpretation by referring to the changes in terms of percentages as opposed to the raw dollar values which can be large. The same Null hypothesis and Alternative hypothesis are used.</p> 

**log(charges) = B0 + B1age + B2bmi + B3 smkr + B4 bmi_smkr + u**

H0: B2 =B3 = 0

H1: B2= B3 not equal to 0

We used Robust Standard errors to address the heteroskedasticity in our data set.

## Conclusion
<p> The regression results and the results of the coefficient show that the standard errors for all  variables decreased in part due to our scaling efforts with ‘charges’.  Overall, the intercept, age and the interaction variable bmi_smkr are significant at 99 % significance level while bmi and smkr failed to be significant at 95 % significance level. Hence, we are not able to reject our stated null hypothesis.  An R^2 score of ~ 76% indicates that this model is decent but not the best. The model resulted in the following interpretations:

When all variables are 0, then the log of charges is about 14.72 which is significant at 99% significance level.

One unit increase in age results in 7% increase in charges which is significant at 99% significance level. 

One unit increase in bmi results in .2% increase in charges. This result is not significant  even at 95% significance level. 

Smoking history results in 41% increase in charges but this result is not significant even at 95% significance level. 

However, the change in the marginal effect of smoking history on charges due to 1 unit increase in bmi causes an increase of ~ 9% in charges and this result is significant at 99% significance level.Overall, these interpretations might not be accurate given the low R^2 score of our model. 

Hence, for this specific set of patients, smoking history and high bmi are only significant cost drivers when both factors are present in the patient’s health record with age being the second cost driver for this set of patients.  

