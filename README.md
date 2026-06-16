# HR Employee Retention — Business Analytics

A People-Analytics study of what drives employee attrition in a 14,999-person company. Written for an HR audience — EDA-first, modelling, every chart paired with a plain-English takeaway.

---

## Notebook

**`HR_Retention_Analysis.ipynb`** — the single deliverable. Runs end-to-end.

---

## Dataset

[HR Analytics and Job Prediction Dataset](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction) — 14,999 employees × 10 columns.

`satisfaction_level`, `last_evaluation`, `number_project`, `average_montly_hours`, `time_spend_company`, `work_accident`, `left` (target), `promotion_last_5years`, `department`, `salary`.

---

## Headline findings

- **23.8% of employees leave** — high for a white-collar firm (healthy range is 10–15%).
- **Attrition is company-wide**, not a department problem (rates are 19–28% across all 10 departments).
- **Two distinct leaver personas** that need different interventions:
  - *Burned-out / unhappy* — the majority (low satisfaction, modest workload).
  - *High-performer* — smaller but expensive slice (high evaluation, high hours, often 3–5 years tenure, no recent promotion).
- **The strongest controllable drivers**: low salary band, the 3–5 year promotion cliff, and workload extremes (≤2 or ≥6 projects).
- **The workload curve is a U**: under-used *and* over-loaded people both leave; 3–5 projects is the safe zone.

---

## Modelling

The model is a **risk-score generator for HRBPs**.

| Model | Accuracy | Precision | Recall | ROC-AUC | Purpose |
|---|---|---|---|---|---|
| Logistic Regression | ~0.90 | 0.80 | 0.79 | 0.94 | Interpretable driver analysis + per-employee risk score |
| Random Forest | ~0.99 | 0.99 | 0.97 | 0.99 | Sanity check on which signals matter |

A per-employee `risk_score` is bucketed into **Low / Watch / High** bands, capturing ~6× more leavers per employee in the High band than in the Low — a usable shortlist for retention conversations.

---

## Recommended HR interventions

1. Compensation review for the low-salary band.
2. Promotion-transparency conversation at the 3–5 year mark.
3. Workload audit — reassign people at the U-curve edges.
4. Two-track retention: stay-interviews for the burned-out, market-pay + fast-track promotion for the high-performers.
5. Quarterly risk-score refresh against live HRIS data.

The full "what to do" *and* "what not to do" list is in §13–14 of the notebook.

---

## How to run

```bash
pip install -r requirements.txt
jupyter notebook "HR_Retention_Analysis.ipynb"
```

The dataset `HR_Dataset.csv` must sit next to the notebook.

---

## Libraries

`pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.
