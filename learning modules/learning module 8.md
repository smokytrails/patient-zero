# LEARNING MODULE 8

## 1. Key Terms in Patient Zero
- scenario - specific combination of parameters $\rightarrow$ 567 unique scenarios
- simulation runs - realization of a scenario $\rightarrow$ 100 runs per scenario
- observation - each of the recorded measurements 
    - peak infected population
    - peak day
    - final outbreak size
    - epidemic duration
    - attack rate
- comparison group $\rightarrow$ 81 comparison groups (3 topologies, 3 initial infection percentages, 3 transmission rates, and 3 recovery rates)

## 2. Statistics
- statistical independence - two observations are statistically independent if knowing the outcome of one doesn't change the probability distribution of the other
- experimental unit - smallest unit to which an experimental treatment or condition is independently applied

## 3. Descriptive Statistics & Distributions
- measures of central tendency:
    - mean
    - median
    - mode
- variation:
    - variance 
    
        $s^2 = \Sigma (x_i-x_{avg}) / (n-1)$
    - standard deviation: s = $\sqrt{s^2}$
- quartiles & percentiles:
    - 25th percentile (Q1) - approximately 25% of outcomes fall at or below this value
    - 50th percentile (Q2) - median
    - 75th percentile (Q3)
    - 95th percentile
    - inter quartile range: $IQR = Q_3 - Q_1$
- distribution shapes:
    - symmetric distribution
    - right or left skewed distribution
    - bimodal distribution
- outliers

## 4. Probability & Statistical Uncertainty
- standard deviation - spread of individual observations
- standard error - uncertainty in an estimated mean 

    $SE = s / \sqrt{n}$
- central limit theorem - under suitable conditions, sample means approach a normal sampling distribution
- confidence interval - quantifies uncertainty in estimated outcomes

    $95\% \ CI = x_{avg} \pm 1.96 \cdot SE$
- bootstrapping - resampling observations to estimate sampling uncertainty

## 5. Epidemiological Metrics & Effect Size
- absolute reduction: $\Delta = Y_{baseline} - Y_{vaccinated}$
- percentage reduction: $R = (Y_{baseline} - Y_{vaccinated}) \cdot 100 \ / \ Y_{baseline}$

## 6. Hypothesis Testing
does degree-targeted vaccination reduce outbreak size more than random vaccination at equal coverage?
- $\mu_T \rightarrow$ expected outbreak size under targeted vaccination
- $\mu_R \rightarrow$ expected outbreak size under random vaccination
- hypothesis:
    - $H_0: \mu_T=\mu_R$
    - $H_1: \mu_T<\mu_R$
- methods:
    - welch's t-test - comparing means from independent samples with potentially unequal variances
    - paired t-test - comparing matched differences when pairing is justified
    - bootstrap CI - quantifying uncertainty in effect estimates
    - permutation test - testing differences under an appropriate exchangeability assumption
    - multiple-comparison adjustment - controlling false positives when testing many hypotheses

## 7. Multivariable Analysis & Interpretation
- main effect - average association of one factor with an outcome across the levels of other factors