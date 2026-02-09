# Predicting SaaS Subscription via User Activation

### Executive Summary 
The goal of this analysis was to identify the specific product milestones or events that drive activation and predicts engagement. By quantifying the impact of early user behavior, I provided the sales and product teams with a data-driven framework for lead prioritization.

### Methodology

- Data Modeling & Schema Design: Transformed 600K+ raw event logs into a user-level schema. This involved defining unique user entities, mapping event-to-user relationships, and creating snapshot tables to capture temporal behavior.

- Feature Engineering: Derived high-signal predictors from the structured data, including cumulative engagement metrics, time-to-first-action durations, and binary flags for critical onboarding milestones.

- Statistical Modeling: Built a Logistic Regression model (AUC ~0.82) to calculate the probability of conversion.

- Validation: Used Variance Inflation Factor (VIF) to check for multicollinearity, ensuring that each coefficient accurately represented a distinct business lever.


### Key Findings
Early momentum matters most:
- Setting up an integration within 14 days (+0.76) and booking a second meeting within the first week (+0.54) are clear winners for activation.
- High meeting volume in the first 30 days (**meetings_in_30d**) is the strongest overall signal (**+0.93**)

### Business Questions Answered
1. What separates activated users from drop-offs?  
   → Fast first meeting + early integration = clear winners

2. Which early actions predict long-term engagement & subscription?  
   → Booking momentum (second/third meetings) and quick integrations are the biggest levers

### Tech Stack & Approach
- Feature engineering on 1M+ events (days to meetings, % active weeks, integration speed, renewals, etc.)  
- Logistic regression (AUC ~0.82) with multicollinearity checks (VIF)  
- Correlation matrix + coefficient interpretation  
- Python • pandas • scikit-learn • statsmodels • seaborn

### Results Summary
| Predictor                     | Coefficient | Interpretation                              |
|-------------------------------|-------------|---------------------------------------------|
| first_meeting_within_7d       | -0.17       | Slightly negative (possible collinearity?)  |
| second_meeting_within_7d      | +0.54       | Strong early momentum signal                |
| three_meetings_30d            | -0.90       | Likely collinear with total meetings        |
| integration_within_14d        | +0.76       | Fast integration = big subscription lift    |
| meetings_in_30d               | +0.93       | Highest overall predictor                   |




Feel free to fork / run / improve!
