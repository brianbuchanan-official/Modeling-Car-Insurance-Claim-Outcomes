```markdown
# Modeling Car Insurance Claim Outcomes

## Executive Summary
This project builds an interpretable Logistic Regression model to predict the likelihood that an auto insurance policyholder will file a claim. Using underwriting-relevant features such as driving history, vehicle attributes, and exposure measures, the model achieves strong discriminatory power (ROC-AUC ≈ 0.89). Policyholders are segmented into risk tiers, with the highest-risk decile exhibiting a 92% observed claim rate versus 13% in the lowest tier. The results demonstrate clear applications for underwriting review, pricing adjustments, and loss ratio improvement.

---

## Business Problem
Auto insurers must accurately assess claim risk at the policy level to price coverage appropriately, control loss exposure, and avoid adverse selection. Traditional rule-based underwriting can miss complex risk interactions, leading to underpriced high-risk policies or unnecessary friction for low-risk customers.

**Objective:**  
Predict whether a policyholder will file a claim during the policy period and translate model outputs into actionable underwriting risk tiers.

---

## KPIs

### Model Performance
- Confusion Matrix  
- Precision  
- Recall (Sensitivity)  
- F1 Score  
- ROC-AUC  

### Insurance / Business KPIs
- Claim Rate by Risk Tier  
- Lift vs Random Selection  
- False Negative Rate (missed high-risk exposure)  
- False Positive Rate (customer friction risk)  

---

## Data & Method

### Dataset
- Public auto insurance dataset sourced from Kaggle  
- ~10,000 policies with a binary claim outcome (`OUTCOME`)  
- Mix of driver behavior, vehicle characteristics, and exposure variables  

### Methodology
1. Data cleaning and preprocessing  
2. One-hot encoding of categorical variables  
3. Stratified train/test split to preserve claim rate  
4. Median imputation for missing numeric fields  
5. Feature scaling for continuous variables  
6. Logistic Regression modeling for interpretability  
7. Threshold-independent evaluation using ROC-AUC  
8. Risk tier segmentation based on predicted claim probability  

---

## Findings

### Model Performance
- **ROC-AUC:** 0.888  
- **Precision:** 74%  
- **Recall:** 72%  
- **Accuracy:** 83% (contextual only)  

The model effectively ranks policyholders by risk, capturing the majority of claimants while limiting excessive false positives.

### Risk Segmentation
| Risk Tier | Observed Claim Rate |
|----------|--------------------|
| Low Risk | 12.7% |
| Medium Risk | 66.0% |
| High Risk | 92.0% |

High-risk policies are nearly **3× more likely** to file a claim than the portfolio average, demonstrating strong lift and underwriting value.

---

## Recommendations

### High Risk (Top 10%)
- Underwriting review  
- Higher deductibles or premium surcharges  
- Coverage restrictions or additional documentation  

### Medium Risk (Next 20%)
- Moderate pricing adjustments  
- Increased monitoring  

### Low Risk (Bottom 70%)
- Preferred pricing  
- Retention-focused offers  
- Straight-through processing  

Applying these actions can materially improve loss ratio performance and pricing fairness.

---

## Next Steps
- Incorporate claim severity modeling (loss amount)  
- Optimize thresholds using expected loss cost  
- Add geographic risk banding  
- Deploy preprocessing and model as a production pipeline  
- Build an interactive dashboard for underwriting teams  

---

## Visualizations

All figures are stored in:

```

reports/figures/

```

- `roc_curve.png` — ROC Curve showing ranking performance  
- `confusion_matrix.png` — Classification trade-offs  
- `claim_rate_by_risk_tier.png` — Business-critical risk segmentation  
- `predicted_probability_distribution.png` — Probability spread and separation  

### Example Figures
![ROC Curve](reports/figures/roc_curve.png)
![Claim Rate by Risk Tier](reports/figures/claim_rate_by_risk_tier.png)

---

## Repository Structure

```

Car_Insurance_Claim_Outcomes/
├─ data/
│  └─ raw/
│     └─ car_insurance_claims.csv
├─ notebooks/
│  └─ 01_data_load_and_eda.ipynb
├─ reports/
│  └─ figures/
│     ├─ roc_curve.png
│     ├─ confusion_matrix.png
│     ├─ claim_rate_by_risk_tier.png
│     └─ predicted_probability_distribution.png
├─ models/
├─ src/
└─ README.md

```

---

## Tools Used
- Python (pandas, numpy)  
- scikit-learn  
- matplotlib & seaborn  
- Jupyter Notebook  

---

## Author
**Brian Buchanan**  
Finance & Data Analytics | Insurance Risk Modeling
```
