<img src="health.jpg">
<body>
	<header>
		<h1> Health Insurance Premium Analysis </h1>
	</header>
<body>

<div class="section">
	<p>
This project explores health insurance premium charges using regression models, specifically Box-Cox and Gamma Regression, implemented in R and SAS. The goal is to understand the factors influencing premium variations and identify an effective model for the given dataset.
	</p>
</div>
<div class="section">
	<h2>Background</h2>
	<p>
		An insurance premium is the amount of money an individual or business pays for an insurance policy. Insurance premiums are paid for policies that cover healthcare, auto, home, or life insurance. When an individual signs up for an insurance policy, the insurer will charge a premium. The price of the premium depends on a variety of factors including: the type of coverage, age, area in which you live, any claims filed in the past, and moral hazard and adverse selection. Insurers use the premiums paid to them by their customers and policyholders to cover liabilities associated with the policies they underwrite. Some insurers invest in the premium to generate higher returns, which helps maintain competitive prices within the market. In addition to an insurance plan’s premium, total health care costs also include the deductible, copayment/coinsurance amounts, along with health and drug services. A deductible is how much the individual spends for covered health services prior to the insurance company paying anything. Copayments and coinsurance are payments you make to your health care provider each time an individual gets care. Analytics is a vital component of the insurance industry because it allows for interpretation that drives business. These methods of analytics often emphasize data-mining tools and
statistical inference.
	</p>
</div>

<div class="section">
	<h2>Dataset Information</h2>
	<p> The dataset was obtained from <a href="https://www.kaggle.com/datasets/mirichoi0218/insurance">Kaggle</a>, a popular platform for data scientists, containing 1338 rows of data with 7 variables:
</div>
<ul>
	<li><b>Age</b>: Age of primary beneficiary
	<li><b>Sex</b>: insurance contractor gender: female or male
	<li><b>BMI</b>: Body mass index
	<li><b>Children</b>: Number of children covered by health insurance / Number of dependents
	<li><b>Smoker</b>: (yes/no)
	<li><b>Region</b>: The beneficiary's residential area in the US (southeast, southwest, northeast, northwest)
	<li><b>Charges</b>: Individual medical costs billed by health insurance
</ul>
The original dataset did not contain any missing or undefined values. For this analysis, the dataset was truncated to the first 100 observations. The response variable chosen was insurance charges, with the other variables serving as predictors.
	</p>

<div class="section">
	<h2>Analysis</h2>
	<p>
		After plotting the individual medical costs billed by health insurance, the distribution appears to not be normally distributed as supported by the histogram and the normality tests. Many statistical methods assume that the residuals of the data are normally distributed. Right-skewed data can violate these assumptions, leading to incorrect inferences and results.
	</p>
<img src="charges.jpg" />

| Statistic | Value        |
|-----------|--------------|
| W         | 0.81469      |
| p-value   | < 2.2e-16    |

</div>
<div class="section">
	<h2>Regression Models</h2>
	<p>
Both Box-Cox and Gamma Regression models were applied to model the insurance premium charges.
	</p>
</div>

### Box-Cox Power Transformation

If the density of the response variable $y$ is right-skewed, a transformation may be applied to $y$ to make its density appear more normally shaped. This transformation is referred to as *Box-Cox power transformation*. The transformed variable, denoted here by $\tilde{y}$, has the form:

<img src="https://latex.codecogs.com/svg.image?\;\tilde{y}=\begin{cases}\frac{y^\lambda-1}{\lambda},&\text{if}\lambda\neq&space;0,\\\ln&space;y,&\text{if}\lambda=0.\end{cases}\;" />

The fitted mean for the Box-Cox transformed response is:

<img src="https://latex.codecogs.com/svg.image?\;\mathbb{E}(\tilde{y})=\mathbb{E}\left(\frac{y}{\lambda-1}\lambda\right)=\beta_0&plus;\beta_1&space;x_1&plus;\cdots&plus;\beta_k&space;x_k\;" />

The Box-Cox Regression was initially used to transform the response variable to achieve normality. However, after applying a square root transformation with an optimal lambda of 0.25, the transformed response remained non-normally distributed. When the assumption of normality is violated, the results from statistical analysis and modeling can be inaccurate, leading to incorrect conclusions.

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
