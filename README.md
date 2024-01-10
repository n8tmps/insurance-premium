<img src="insurance.jpg" width="300" height="350">
<body>
	<header>
		<h1> Health Insurance Premium Analysis </h1>
	</header>
<body>

<div class="section">
	<p>
This project explores health insurance premium charges using regression models, specifically Box-Cox and Gamma Regression, implemented in R and SAS. The goal is to understand the factors influencing premium variations and identify an effective model for the given dataset.

</div>

<div class="section">
	<h2>Dataset Information</h2>
	<p> The dataset was obtained from Kaggle, a popular platform for data scientists, containing 1338 rows of data with 7 variables:
</div>
<ul>
	<li>Age
	<li>Sex (male/female)
	<li>BMI
	<li>Number of children
	<li>Smoker (yes/no)
	<li>Region (southeast, southwest, northeast, northwest)
	<li>Insurance charges
</ul>
	<p>
The original dataset did not contain any missing or undefined values. For this analysis, the dataset was truncated to the first 100 observations. The response variable chosen was insurance charges, with the other variables serving as predictors.

<div class="section">
	<h2>Regression Models</h2>
	<p>
Both Box-Cox and Gamma Regression models were applied to model the insurance premium charges.
	</p>
</div>

<div class="section">
	<h3>Box-Cox Regression</h3>

The Box-Cox Regression initially attempted to transform the response variable to achieve normality. However, after applying a square root transformation with an optimal lambda of 0.25, the transformed response remained non-normally distributed.
</div>

<div class="section">
	<h3>Gamma Regression</h3>
The Gamma Regression, on the other hand, proved to be a better fit for the data. Significant predictors at the 5% level included age, BMI, smoking status, and region northwest. The fitted model demonstrated a good fit, with a deviance test p-value close to zero.
</div>

<div class="section">
	<h2>Predictor Interpretation</h2>

The interpretation for significant predictors is as follows:

<ul>
	<li>As age increases by one year, the estimated mean premiums increase by 3.51%.
	<li>An increase of one BMI point corresponds to a 1.745% increase in estimated mean premiums.
	<li>Smokers have estimated mean premiums 5.44% higher than nonsmokers.
	<li>People living in the northwest have estimated mean premiums 1.3066% of those living in the southeast.
</div>

<div class="section">
	<h2>Conclusion</h2>

The Gamma Regression proved effective in modeling health insurance premium charges, capturing the inherent right-skewness of the dataset. This analysis provided insights into risk underwriting in health insurance, showcasing the interplay of various attributes on insurance premiums.
