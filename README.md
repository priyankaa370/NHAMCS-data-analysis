# Emergency Room Wait Time Analysis (NHAMCS)
## Project Overview

This project analyzes real-world emergency department data from the National Hospital Ambulatory Medical Care Survey (NHAMCS) to investigate factors influencing patient wait times before being seen by a healthcare provider.

Emergency room wait times are a critical operational and public health concern. National averages suggest ER patients wait over 2 hours to see a provider, significantly longer than primary care settings. Understanding what drives this delay is essential for improving healthcare equity and operational efficiency.

This project combines statistical hypothesis testing and machine learning to explore:

- Whether racial demographics influence ER wait times

- Whether holiday seasons impact wait duration

- Which clinical and operational features most strongly predict wait time

## Data Source

Data obtained from:

National Hospital Ambulatory Medical Care Survey (NHAMCS)
Conducted by the National Center for Health Statistics (NCHS)

The dataset represents nationally sampled emergency department visits across the United States.

## Research Questions

- Do wait times differ significantly across racial groups?

- Are wait times longer during holiday periods?

- Which features most strongly predict emergency room wait time?

## Methodology
1. Statistical Analysis – Independent T-Tests

      Independent two-sample t-tests were performed to compare mean wait times between:
      
      - White vs Black patients
      
      - White vs Other racial groups
      
      - Black vs Other racial groups
      
      - Holiday vs Non-holiday visits
      
      The t-test evaluates whether observed mean differences are statistically significant under the null hypothesis of equal group means.

2. Machine Learning – Random Forest Regressor

      A Random Forest Regressor was trained to predict patient wait time using demographic, clinical, hospital, and operational features.
      
      **Model**: Random Forest Regressor
      
      **Evaluation metric**: R² on test set
      
      **Test performance**: 19.2% variance explained
      
      Feature importance was extracted to identify the strongest predictors.

## Key Findings
Racial Differences in Wait Times

### White vs Black:

- t-statistic: -9.4639

- p-value: 3.23e-21

**Result: Statistically significant difference**

### White vs Other:

- t-statistic: -3.1013

- p-value: 0.00193

**Result: Statistically significant difference**

### Black vs Other:

- t-statistic: 1.0567

- p-value: 0.2907

**Result: No significant difference**


**Interpretation:**

- Statistically significant differences exist between White patients and minority groups. 
- Minority groups experienced longer wait times on average. 
- However, no significant difference was found between Black patients and other non-White groups.

This suggests structural disparities that warrant deeper multivariate investigation.

### Holiday vs Non-Holiday Analysis:

- t-statistic: 1.4913

- p-value: 0.1359

**Result: No statistically significant difference.**

Wait times do not meaningfully vary between holiday and non-holiday periods.

## Top Predictive Features (Random Forest)

**Most Important Categorical Features:**
- ARRTIME (Arrival Time)

- DIAG13D 

- RX1CAT1

- DIAG1

- DIAG23D

**Most Important Numerical Features:**

- LOV (Length of Visit)

- PATCODE

- DIAG1R

- PULSE

- AGE

## Insights:

- Time of arrival is one of the strongest predictors, indicating operational congestion patterns.

- Clinical variables (diagnosis codes, pulse, age) influence prioritization through triage.

- Hospital-level identifiers also contribute to variation, suggesting institutional differences in workflow or capacity.

## Technical Stack

- Python

- Pandas

- NumPy

- Scikit-learn

- SciPy

- Matplotlib / Seaborn

## Limitations

- Observational dataset; causality cannot be inferred

- Potential confounders not fully controlled

- Model explains 19.2% of variance, indicating unobserved operational complexity

- No causal inference or multilevel modeling performed

## Future Improvements

- Multivariate regression controlling for triage severity and hospital fixed effects

- Gradient boosting models (XGBoost, LightGBM)

- SHAP analysis for interpretable feature contributions

- Hospital-level clustering analysis

- Fairness metrics and bias quantification

## Conclusion

This project demonstrates how statistical testing and machine learning can be applied to real healthcare data to uncover disparities and operational drivers of emergency department wait times.

The findings highlight measurable racial disparities and identify key operational and clinical factors influencing patient flow in U.S. emergency departments.
