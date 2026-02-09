# User Activation Model

**Logistic Regression** | Key Behaviors for Subscription

Analyzed user events from a leading scheduling SaaS platform to uncover what drives activation, engagement, and subscriptions.

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
| first_meeting_within_7d       | -0.17       | Slightly negative (possible collinearity?)   |
| second_meeting_within_7d      | +0.54       | Strong early momentum signal                |
| three_meetings_30d            | -0.90       | Likely collinear with total meetings        |
| integration_within_14d        | +0.76       | Fast integration = big subscription lift    |
| meetings_in_30d               | +0.93       | Highest overall predictor                   |




Feel free to fork / run / improve!
