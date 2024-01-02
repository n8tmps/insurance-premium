# Health Insurance Premium Analysis

This project explores health insurance premium charges using regression models, specifically Box-Cox and Gamma Regression, implemented in R and SAS. The goal is to understand the factors influencing premium variations and identify an effective model for the given dataset.

## Dataset Information

The dataset was obtained from Kaggle, a popular platform for data scientists, containing 1338 rows of data with 7 variables:

- Age
- Sex (male/female)
- BMI
- Number of children
- Smoker (yes/no)
- Region (southeast, southwest, northeast, northwest)
- Insurance charges

The original dataset did not contain any missing or undefined values. For this analysis, the dataset was truncated to the first 100 observations. The response variable chosen was insurance charges, with the other variables serving as predictors.

## Regression Models

Both Box-Cox and Gamma Regression models were applied to model the insurance premium charges.

### Box-Cox Regression

The Box-Cox Regression initially attempted to transform the response variable to achieve normality. However, after applying a square root transformation with an optimal lambda of 0.25, the transformed response remained non-normally distributed.

### Gamma Regression

The Gamma Regression, on the other hand, proved to be a better fit for the data. Significant predictors at the 5% level included age, BMI, smoking status, and region northwest. The fitted model demonstrated a good fit, with a deviance test p-value close to zero.

### Fitted Model

The fitted model for the Gamma Regression is expressed as:

\hat{E}(\text{charges}) = \exp(-0.2226 + 0.0345 \times \text{age} + 0.1195 \times \text{male} + 0.0173 \times \text{BMI} + 0.0520 \times \text{children} + 1.6938 \times \text{smoker} + 0.0093 \times \text{northeast} + 0.2674 \times \text{northwest} + 0.0782 \times \text{southwest})

### Predictor Interpretation

The interpretation for significant predictors is as follows:

- As age increases by one year, the estimated mean premiums increase by 3.51%.
- An increase of one BMI point corresponds to a 1.745% increase in estimated mean premiums.
- Smokers have estimated mean premiums 5.44% higher than nonsmokers.
- People living in the northwest have estimated mean premiums 1.3066% of those living in the southeast.

## Conclusion

The Gamma Regression proved effective in modeling health insurance premium charges, capturing the inherent right-skewness of the dataset. This analysis provided insights into risk underwriting in health insurance, showcasing the interplay of various attributes on insurance premiums. In the future, the regression analysis skills gained from this project can be applied to other financial metrics, such as claim amounts.
