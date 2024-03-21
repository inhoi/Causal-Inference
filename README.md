# Causal-Inference

- Causal Inference: It is the process of drawing a conclusion about a causal connection based on the conditions of the occurrence of an effect. It aims to identify whether a change in one variable would lead to a change in another variable.

## Causation vs. Correlation

- Correlation: It indicates that there is a statistical relationship between two variables, but it doesn’t imply causation. For example, the provision of tablets in schools and improved academic performance may correlate, but other factors like socioeconomic status could be at play.
  
## Potential Outcomes and Average Treatment Effect

- Potential Outcomes Framework: This approach considers every possible outcome that could result from a particular treatment or action for an individual.

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

## Bias and the Importance of Randomization

Bias: This arises when the treatment and control groups differ in ways other than the treatment before the intervention.
Randomization: It helps to neutralize bias by ensuring all other variables are equally distributed across treatment and control groups.

## Challenges When Randomisation Is Not Feasible

Randomised Experiments: These are often considered the gold standard for causal inference because they control for both observed and unobserved confounding variables by random assignment.
Observational Studies and Assignment Mechanisms: When randomization isn’t possible, understanding the mechanism by which treatments are assigned is critical for causal inference. This helps to comprehend how the data we observe has been generated.
