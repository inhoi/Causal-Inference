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

- Good Control Variables --> These are variables that predict the outcome variable but not the treatment variable. Including good control variables in the model helps explain variability in the outcome variable, thereby increasing the model's accuracy. 

- Variables to Be Cautious With --> Variables that only affect the treatment variable should be added to the model with caution. Including such variables can reduce the variability of the treatment variable, making it harder to detect its causal effect. 

- Selection Bias --> Occurs when controlling for common effects or variables in the causal path from the treatment variable to the outcome variable. To avoid selection bias, do not control for variables that are between the treatment and outcome variables or are common effects of both. 

- Bad COP --> A specific case of selection bias that can occur even in randomized experiments. It involves modeling the probability of a non-zero outcome in the first stage and the value of the outcome given it is non-zero in the second stage. To correctly estimate the effect of the treatment variable, both zero and non-zero outcomes should be considered together.

## Chapter 8 : Instrumental Variables

- Instrumental Variables (IV) --> Variables that are correlated with the treatment variable but only affect the outcome variable through the treatment variable. For example, when measuring the effect of education on wages, the quarter of birth can be used as an instrumental variable to address the bias caused by omitted variables like individual ability.

- Two-Stage Least Squares (2SLS) --> A method to estimate causal effects using instrumental variables. The first stage predicts the treatment variable using the instrumental variable, and the second stage uses this predicted treatment variable to predict the outcome variable.

- Weak Instruments --> When the correlation between the instrumental variable and the treatment variable is weak, 2SLS estimates can become unstable, leading to large standard errors and potentially inaccurate estimates of the true parameter values.

- Consistency and Bias in 2SLS --> While 2SLS is consistent, meaning that it approaches the true parameter value as the sample size increases, it can still be biased, especially in finite samples. The use of multiple instrumental variables can make 2SLS estimates closer to ordinary least squares (OLS) estimates.

## Chapter 9 : Non Compliance and LATE

- Instrumental Variables (IV) as a Causal Chain --> IVs are viewed as causing the treatment, which in turn causes the outcome. This perspective helps in understanding the causal effects estimated using IVs.

- Compliance and Local Average Treatment Effect (LATE) --> The concept of compliance is important in IV estimation. LATE refers to the average treatment effect for the subgroup of 'compliers'—individuals whose treatment status is influenced by the instrumental variable.

- Key Assumptions for IV Estimation
 1. Independence Assumption: The instrumental variable is as good as randomly assigned.
 2. Exclusion Restriction: The potential outcomes of the treatment are the same across different IV groups.
 3.  First Stage Assumption: The instrumental variable has an impact on the treatment.

## Chapter 10 : Matching

- Subclassification Estimator --> Similar to regression analysis, it divides data into subgroups based on the values of X and calculates the average difference between treatment and control groups within each subgroup. These average differences are then combined to estimate the ATE for the entire dataset.

- Matching --> Another method to control for confounding variables. It pairs each unit in the treatment group with a similar unit in the control group and compares them to reduce the impact of confounding variables. The matching estimator calculates the difference between each pair and averages these differences to estimate the ATE.

- Bias in Matching Estimates --> There is a risk of bias if the matched pairs are not perfectly similar, i.e., if there are still differences in confounding variables between the matched treatment and control units. To reduce this bias, bias correction can be performed on the differences between matched pairs.

- Curse of Dimensionality --> Affects both matching and subclassification estimators. As the number of variables increases, it becomes harder to find similar pairs, leading to increased distances between matched pairs and potential bias. Additionally, with more variables, the number of subgroups increases exponentially, leading to sparsity in the data and a lack of data in some subgroups.

## Chapter 11 : Propensity Score

- Propensity Score --> A statistical technique used to reduce bias in estimating treatment effects in observational data. The propensity score represents the probability of an individual receiving treatment (e.g., participating in a program, taking a medication) and helps balance baseline characteristics between treatment and control groups.

- Challenges in Using Propensity Scores

 1) Variable Selection --> If important variables are not included in the propensity score model, the estimated effect can be biased. For instance, if students' motivation for learning or teachers' instructional styles influence seminar participation and academic achievement but are omitted, the propensity scores may not achieve complete balance.
    
 3) Extreme Propensity Scores --> If there are students with very low or high probabilities of seminar participation, the weights for these extreme cases can become very large, increasing the variance of the estimates.

## Chapter 12 : Doubly Robust Estimation

- Doubly Robust Estimation --> A method combining linear regression and propensity score techniques to estimate causal effects. The key advantage is that the estimation remains valid if either the propensity score model or the outcome model is correctly specified, offering robustness against model misspecification.

- Propensity Score Estimation --> Initially, a logistic regression model is used to estimate the propensity scores, which represent the probability of receiving a specific treatment (e.g., attending a seminar). This model calculates the probability of seminar attendance for each student, considering characteristics such as their expectations of success and school environment.

- Conditional Expectation Estimation --> Next, a linear regression model predicts each student's academic achievement, taking into account their characteristics and seminar attendance.

- Causal Effect Estimation --> Finally, the propensity scores and conditional expectation models are combined to estimate the causal effect. The crucial aspect here is that the estimation can be valid even if only one of the models (propensity score or conditional expectation) is accurate. For instance, even if the propensity score model is not perfect, the causal effect can still be estimated accurately if the conditional expectation model is correct.
