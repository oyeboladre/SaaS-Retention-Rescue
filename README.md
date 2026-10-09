# SaaS-Retention-Rescue
Uncovering a R$257K monthly churn leak in a 15,000 customer SaaS dataset. An end-to-end analysis using SQL, Python, and Machine Learning to drive retention strategy.
# 🛑 SaaS Retention & Churn Analysis: Finding the R$257K Leak

## 📖 Executive Summary
SaaS companies live and die by their retention rates. This project analyzes a dataset of 15,000 SaaS customers to diagnose a severe retention issue. By combining SQL-style aggregations, statistical testing, and Machine Learning, I identified a critical "2024 Cohort Crisis" and a specific operational failure driving almost 77% of churn in at-risk segments. 

The analysis concludes with specific, data-backed strategic recommendations to save the company an estimated R$ 257,000 in lost Monthly Recurring Revenue (MRR).

## 🛠️ Tech Stack & Skills
*   Data Wrangling: Python (Pandas, NumPy)
*   Business Analytics: Cohort Analysis, Lifecycle Binning, Customer Profiling
*   Statistical Validation: SciPy (T-Test for statistical significance)
*   Machine Learning: Scikit-Learn (Logistic Regression, Confusion Matrix, Feature Importance)
*   Visualization: Plotly (Dark-mode Executive Dashboard)

---

## 🧭 The Analysis Journey (STARR Method)

### 1. SITUATION (The Business Context)
The company acquired roughly 5,000 new customers annually between 2022 and 2024. On the surface, acquisition was healthy. However, the overall churn rate sat at a troubling 31.89%, resulting in significant revenue leakage. The business needed to know: *Who is leaving, why are they leaving, and how can we intervene before they hit the "Cancel" button?*

### 2. TASK (The Goal)
The objective was to move beyond simple reporting and act as a business detective. I needed to:
1. Isolate demographic vs. behavioral drivers of churn.
2. Identify the "Danger Zone" in the customer lifecycle.
3. Build a predictive model to identify at-risk customers *before* they leave.
4. Provide actionable, financially quantified recommendations to the executive team.

### 3. ACTION (The Tracing Sequence)
I approached the data systematically, ruling out noise before identifying the signal.

*   Ruling out Demographics: I tested Age, Gender, and Region. The data revealed a highly homogenized user base. Demographics were not driving churn. However, Income Level showed a slight signal (Low-income churn: 34.1% vs. High-income: 27.5%), suggesting price sensitivity.
*   The Cohort Discovery: Grouping customers by signup year exposed a massive anomaly. The 2024 cohort was churning at 49.7%, double the rate of 2022 (22.6%) and 2023 (22.9%).
*   The "Double Whammy": Drilling into the 2024 cohort, I found the smoking gun. A massive 69.5% of this cohort signed up for Monthly contracts (vs. Yearly), and they were logging an average of 3.46 support tickets. The intersection of these two factors—**Monthly Contract + 3+ Support Tickets—resulted in a staggering 76.7% churn rate.**
*   Statistical Proof: A T-Test confirmed that the difference in support ticket volume between churned and retained customers was highly statistically significant (p < 0.05). This was not random luck.
*   Predictive Modeling: I trained a Logistic Regression model to predict churn probability for all active customers. The model achieved 91.5% accuracy and a 90% Recall rate, successfully identifying 862 out of 957 actual churners.

### 4. RESULT (The Findings)
The analysis generated hard financial and operational truths:
*   Financial Impact: The company is losing R$ 257,661.96 in MRR monthly. The average Customer Lifetime Value (LTV) is R$ 185.18.
*   The 6-Month Danger Zone: 55% of all churn happens within the first 3-6 months of a customer's lifecycle.
*   Feature Importance: The Machine Learning model proved the top 3 predictors of churn are: 
    1. Days Since Last Login
    2. Number of Support Tickets
    3. Tenure (The younger the account, the higher the risk).

### 5. RECOMMENDATION (The Business Strategy)
Based on the data, I provided three high-impact recommendations to the executive team:

1. Implement a "First 90 Days" Onboarding SWAT Team
*   *The Data:* 55% of churn happens in the first 6 months.
*   *The Fix:* Automatically flag any new customer who logs 2+ support tickets within their first 90 days.
*   A dedicated Customer Success agent must reach out personally to resolve their issue. Saving these accounts prevents them from entering the "Danger Zone."

2. Shift Acquisition Strategy to Annual Plans
*   *The Data:* Monthly contracts are the primary driver of the 2024 crisis.
*   *The Fix:* Marketing should aggressively push annual plans with a 2-month discount. For existing monthly subscribers, offer an upgrade incentive. Annual contracts inherently reduce churn because they create a psychological and financial commitment.

3. Deploy the "Danger List" Predictive Intervention
*   *The Data:* The ML model identifies 90% of future churners.
*   *The Fix:* Feed the model's daily top 15 highest-risk customers directly to the Customer Success team. Provide them with a script to call these specific users, address their open tickets, and offer a loyalty incentive. We don't need to save everyone; saving just 10% of this list protects millions in LTV.

---

## 📊 Interactive Dashboard
The full interactive dashboard is saved as a standalone HTML file. 
[Click here to view the Executive Dashboard](cA dedicated Customer Success agent must reach out personally to resolve their issue. Saving these accounts prevents them from entering the "Danger Zone."

2. Shift Acquisition Strategy to Annual Plans
*   *The Data:* Monthly contracts are the primary driver of the 2024 crisis.
*   *The Fix:* Marketing should aggressively push annual plans with a 2-month discount. For existing monthly subscribers, offer an upgrade incentive. Annual contracts inherently reduce churn because they create a psychological and financial commitment.

3. Deploy the "Danger List" Predictive Intervention
*   *The Data:* The ML model identifies 90% of future churners.
*   *The Fix:* Feed the model's daily top 15 highest-risk customers directly to the Customer Success team. Provide them with a script to call these specific users, address their open tickets, and offer a loyalty incentive. We don't need to save everyone; saving just 10% of this list protects millions in LTV.

---

## 📊 Interactive Dashboard
The full interactive dashboard is saved as a standalone HTML file. 
[Click here to view the Executive Dashboard](saas_churn_executive_dashboard.html)
*(Note: You can download the HTML file from this repository and open it locally in any web browser).*

Dashboard Preview:![Dashboard Screenshot](images/dashboard_preview.png)

## 📂 Repository Structure
*   analysis.ipynb - Full Python, SQL, and Machine Learning pipeline.
*   saas_churn_executive_dashboard.html - Interactive dark-mode dashboard.
*   images/ - Screenshots of key visualizations.
*   README.md - Project documentation.l)
*(Note: You can download the HTML file from this repository and open it locally in any web browser).*
