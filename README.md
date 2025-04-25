![image](https://github.com/user-attachments/assets/74e7255e-c5c7-4b2c-a960-7964f8d78957)# 

Audit-Volume-Bias-in-Stack-Ranking---Case-Study
This case study explores bias in a performance evaluation framework used by large-scale e-commerce operations, focusing on how quality metrics unfairly penalize employees handling fewer audit tasks within a normalized KPI-based ranking system.

📂 Dataset Summary

Rows: 20 employees

Key Columns:

Audits Sent Back + Shadow Audited

Audit Reverts + Shadow Audits

Disputes Against

Quality (%)

Productivity (%)

Time Utilization (%)

Final Q Score, Final P Score, Final T Score

Final T (Total Score)

## 📐 KPI Weights (as per Amazon's model)

| **KPI**                  | **Weight (%)** |
|--------------------------|----------------|
| **Quality (%)**          | 55             |
| **Productivity (%)**     | 35             |
| **Time Utilization (%)** | 10             |


📌 Formula Used for Quality Calculation:

Quality (%) = [1 - ((Audit Reverts + Disputes Against) / (Audits Sent Back + Disputes Resolved))] × 100

This formula is highly sensitive when the audit count is very low, often leading to extremely low Quality % even with minimal errors.

🔬 Hypothesis Testing

We tested the following:

Group A: Low audit volume (< 5 audits)

Group B: High audit volume (>= 5 audits)


### 📊 t-test Results

| **Metric**         | **T-statistic** | **P-value** | **Significance?**         |
|--------------------|----------------:|------------:|----------------------------|
| Final Q Score      | -27.0571        | 0.0090      | ✅ **Significant**         |
| Final P Score      | -2.8580         | 0.0108      | ✅ **Significant**         |
| Final T Score      | -0.6338         | 0.6197      | ❌ Not significant         |
| Final T (Total)    | -23.0554        | 0.0000      | ✅ **Highly Significant**  |


🔍 Interpretation

Quality Score (Final Q Score) is highly biased by audit volume.

Productivity Score also shows a notable difference.

Time Utilization is consistent and fair.

Overall Final T (Total Score) is biased because of over-weighted Quality component.

📊 Visualizations

Generated boxplots comparing score distributions for:

Final Q Score

Final P Score

Final T Score

Final T (Total)

These visually support the t-test results, showing significantly lower scores for low audit volume employees.

✅ Conclusion

Employees with low audit volume face systematic unfairness in stack ranking due to the way Quality Score is calculated.

⚠️ Quality % is unreliable at low volume, and severely reduces total score.

🧪 Our statistical test and visualization confirm this bias.

📌 Recommendation:

Use a minimum threshold for audit volume before calculating Quality.

Rebalance weightings across KPIs.

Consider confidence intervals or variance normalization.

💼 About the Author

This project is part of a transition journey from Quality Specialist to Data Engineer / Data Analyst, applying real-world business problems and statistical analysis to build job-readiness.

🛠️ Tech Stack

Python (Pandas, NumPy, Seaborn, Matplotlib, SciPy)

Google Colab

Excel for dataset preparation

📁 Files

Stack_Rank_Calc.xlsx — anonymized dataset used for analysis

stack_rank_analysis.ipynb — full Jupyter notebook (code + plots)

⭐ GitHub Tags

#dataanalysis #hypothesistesting #businesscase #stackranking #biasdetection #amazon #qualityscore
