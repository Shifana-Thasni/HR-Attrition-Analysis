HR Attrition Analysis: Predicting & Preventing Employee Turnover
A data-driven retention strategy project combining Excel and Python to identify why employees leave, predict individual flight risk, and quantify the financial cost of attrition.

Business Questions
Which employee demographic segments show the highest attrition rates compared to the overall workforce average?
Which satisfaction metric has the strongest relationship with an employee's decision to leave?
Does monetary compensation reduce attrition risk consistently, or does its effect plateau at higher salary levels?
Does time without promotion or a long commute increase attrition risk?
What combination of factors most commonly appears among employees who left?
Can we build a predictive model to estimate the likelihood of an individual employee leaving?
What is attrition actually costing the company in estimated replacement costs?
If the company reduced overtime, how much could projected attrition be reduced, and is that intervention worth the cost saved?
Based on risk scores and cost estimates, which employees or segments should be prioritized for retention efforts?
Key Findings
Overtime is the strongest predictor of attrition. Employees working overtime leave at 30.5%, nearly 3x the rate of those who don't (10.4%).
Sales carries both the highest attrition rate (20.6%) and the highest total replacement cost ($6.2M) among all departments.
New employees (0–2 years tenure) are ~4x more likely to leave than tenured staff (29.8% vs. 8.1% for 11+ years).
Attrition has cost the company an estimated $12.0M historically, with a further $14.8M currently at risk based on the model's High-risk employee segment.
A 10% reduction in overtime alone could save an estimated $425K.
Tools & Methods
Excel

Data cleaning and validation (duplicate/missing-value checks, stray-row detection)
XLOOKUP-based label tables and department/risk-tier benchmark lookups
15+ PivotTables and PivotCharts across demographic, satisfaction, tenure, and financial dimensions
Custom cost-of-attrition formulas (job-level-weighted replacement cost multipliers)
A live what-if scenario modeling projected savings from overtime reduction
Python (Jupyter / pandas / scikit-learn)

Logistic regression model trained on 9 features (income, satisfaction scores, distance, tenure, promotion history, overtime, age)
Addressed class imbalance (only ~16% of employees left) using class-weighted logistic regression, prioritizing recall over raw accuracy
Generated individual attrition-probability scores for every employee, exported back into Excel via XLOOKUP to build a Low/Medium/High risk tier
Model Performance
Model	Accuracy	Recall (employees who left)
Initial (unbalanced)	86%	8%
Final (class-balanced)	72%	46%
The unbalanced model looked more accurate but caught almost none of the employees who actually left. The final model trades some accuracy for a model that is actually useful for proactive retention.

Repository Contents
├── HR_Attrition_Workbook.xlsx      # Full Excel analysis (cleaning, pivot tables, cost model, what-if scenario)
├── attrition_model.ipynb           # Python notebook: logistic regression model & risk scoring
├── attrition_risk_scores.csv       # Exported per-employee attrition probability scores
├── HR_Attrition_Analysis.pptx      # Final report deck (Pyramid Principles structure)
└── README.md
Recommendations
Risk Tier	Key Drivers	Recommended Action
High	Overtime, low tenure, low work-life balance, concentrated in Sales	Immediate 1:1 retention conversations; review overtime load; prioritize Sales department cases
Medium	Moderate satisfaction and tenure signals	Proactive check-ins; monitor satisfaction trends; watch for overtime creep
Low	Stable tenure, no overtime, higher satisfaction	Standard engagement; no urgent action needed
Dataset
IBM HR Analytics Employee Attrition & Performance (1,470 employees, 35 features)

Author
Shifana Thasni GitHub
