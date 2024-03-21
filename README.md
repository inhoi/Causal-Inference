# Causal-Inference

- Causal Inference: It is the process of drawing a conclusion about a causal connection based on the conditions of the occurrence of an effect. It aims to identify whether a change in one variable would lead to a change in another variable.

## Causation vs. Correlation

- Correlation: It indicates that there is a statistical relationship between two variables, but it doesn’t imply causation. For example, the provision of tablets in schools and improved academic performance may correlate, but other factors like socioeconomic status could be at play.
  
## Potential Outcomes and Average Treatment Effect

- Potential Outcomes : This approach considers every possible outcome that could result from a particular treatment or action for an individual. 

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

- Bias: This arises when the treatment and control groups differ in ways other than the treatment before the intervention.

$$ E[Y|T=1] - E[Y|T=0] = \underbrace{E[Y_1 - Y_0|T=1]} + \underbrace{\{ E[Y_0|T=1] - E[Y_0|T=0] \}} $$

Association becomes causation only when bias is absent. We can say that bias is not present when, other than the treatment received, the target and control groups are equivalent or similar. In other words, if the groups are alike in all respects except for the intervention, the association can be considered causal.

$E[Y_0|T=0]=E[Y_0|T=1]$

## Randomization

- Randomised Experiments: Distribute individuals randomly into the treatment group and the control group. This random allocation ensures that the two groups are comparable, which allows for the assessment of the causal effect of the treatment.

$(Y_0, Y_1) \perp T$

- Observational Studies and Assignment Mechanisms: When randomization isn’t possible, understanding the mechanism by which treatments are assigned is critical for causal inference. This helps to comprehend how the data we observe has been generated.
