# Causal-Inference

## Chapter 1 : Introduction To Causality

- Importance --> Essential for understanding the 'why' and 'how' in data science, beyond just predictions.

- Fundamental Problem --> We can't observe both potential outcomes for the same unit, leading to the need for latent outcomes and comparability of groups. 

- Estimating Causal Effects --> The goal is to eliminate bias and estimate the pure treatment effect to understand causality. 
  
##### Potential Outcomes and Average Treatment Effect

$Y_{i}$  the observed outcome variable for unit i.

$$ T_i=\begin{cases}
1 \ \text{if unit i received the treatment}\\
0 \ \text{otherwise}\\
\end{cases} $$

$Y_{0i}$  is the potential outcome for unit i without the treatment.

$Y_{1i}$  is the potential outcome for the same unit i with the treatment.

- ITE (Individual Treatment Effect)
 $Y_{1i} - Y_{0i}$

- ATE (Average Treatment Effect) : This is the average effect of a treatment across a population, as we can't observe the individual effects directly.  $ATE = E[Y_1 - Y_0]$

- ATT (average Treatement effect on the treated
$ATT = E[Y_1 - Y_0 | T=1]$

##### Bias

$$ E[Y|T=1] - E[Y|T=0] = \underbrace{E[Y_1 - Y_0|T=1]} + \underbrace{\{ E[Y_0|T=1] - E[Y_0|T=0] \}} $$

## Chapter 2 : Randomised Experiments

- Bias Elimination --> RCTs ensure comparability between treatment and control groups, eliminating bias and allowing for causal inference.

- Random Assignment --> Subjects are randomly assigned to treatment or control groups, ensuring that any differences are due to the treatment effect. 

- Limitations --> While RCTs are the gold standard, they may not always be feasible due to cost, ethical concerns, or practicality.

- Value --> Despite limitations, RCTs are invaluable for establishing causality when feasible.

$(Y_0, Y_1) \perp T$

## Chapter 3 : Stats Review: The Most Dangerous Equation

- Standard Error and Confidence Intervals: Standard error measures the accuracy of the sample mean, and confidence intervals provide a range where the true population mean is likely to fall.

$\hat{\sigma} = \sqrt{\frac{1}{N-1}\sum_{i=1}^N (x_{i}-\bar{x})^2}$

 As sample size increases, confidence intervals become narrower, standard error is inversely proportional to the square root of sample size.

- Hypothesis Testing: We use hypothesis testing to determine if the observed difference between groups is statistically significant.

1 -  Set a null hypothesis (H0) and evaluated the possibility of rejecting it.

2 -  In our case, we tested the null hypothesis that there's no difference in academic achievement between online and face-to-face classes.

3 -  The z-statistic measures how extreme the observed difference is.

4 -  The p-value indicates the probability of obtaining the observed results if the null hypothesis is true.

5 -  A smaller p-value strengthens the case against the null hypothesis.

- p-Value: The p-value indicates the probability of observing the results (or more extreme) under the null hypothesis. A low p-value suggests rejecting the null hypothesis. 

## Chapter 4 : Graphical Causal Models

1. Confounding
- Occurs when a common cause affects both treatment and outcome
- Example: Intelligence affecting both education level and income

2. Selection Bias
- Occurs from the data selection process for analysis
- Example: Pre-existing differences between treated and untreated groups in a study

4. Conver Contraol for Mediators
- Happens when controlling too much for variables that mediate treatment effects
- Example: Overcontrolling for job type in the relationship between education and income



![image](https://github.com/inhoi/Causal-Inference/assets/76868046/b1d4babc-c9e8-4fa9-87a7-166f388d0543)
![image](https://github.com/inhoi/Causal-Inference/assets/76868046/696c9b2c-8a2b-47fa-9547-619e89e4779f)

## Chapter 5 : The Unreasonable Effectiveness of Linear Regression

- Regression Analysis --> A statistical method to analyze the relationship between two variables, such as education duration and wages.
  
- A/B Testing and Confidence Intervals -->Regression analysis can be used to perform A/B testing and calculate confidence intervals, helping to determine if differences between groups are statistically significant.
  
- Conditional Expectation --> The expected outcome given a specific condition, analyzed through linear approximation in regression analysis.
  
- Multivariate Regression Analysis --> Allows simultaneous analysis of the impact of multiple independent variables on a dependent variable.
  
- Omitted Variable Bias --> The distortion in regression analysis results due to omitted variables. It's important to control for omitted variables and consider confounding variables.

## Chapter 6 : Grouped and Dummy Regression

- Weighted Linear Regression --> Not all data points have equal importance in linear regression. Larger sample sizes should be given more weight due to lower variance. 

- Dummy Regression Analysis --> A non-parametric model that doesn't assume a functional form for how treatment affects the outcome. It allows independent estimation of the impact of each category of a variable.

- Regression with All Dummy Variables --> When all variables are dummies, the model calculates the average wages for each category. This model is very flexible but can lose statistical significance with too many categories. 

## Chapter 7 : Beyond Confounders
