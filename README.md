# SaaS-Retention-Rescue
￼# 🛑 SaaS Retention & Churn Analysis: The R$257K Investigation

## 📖 Executive Summary
This project is an end-to-end data investigation into a SaaS company's customer churn crisis. Faced with a 31.89% overall churn rate, I utilized Python, SQL, and Machine Learning to dissect the customer lifecycle, isolate a massive "2024 Cohort Crisis," and uncover a fatal combination of factors driving customers away. 

By moving beyond simple reporting to forensic root-cause analysis, I quantified the financial damage and built a predictive model that achieved **91.5% accuracy** in identifying at-risk customers before they leave. This project proves the value of data analytics not just as a coding exercise, but as a strategic business tool to save revenue.

## 🛠️ Tech Stack & Deep Technical Application
*   **Data Wrangling & Feature Engineering (Pandas/NumPy):** Handled missing values, corrected data types (string to datetime), and engineered critical business features like `tenure_group`, `age_group`, and `signup_year` using custom binning techniques (`pd.cut`).
*   **Business Logic & Aggregation (SQL via `pysqldf`):** Leveraged SQL CTEs, Window Functions (`ROW_NUMBER`), and `CASE` statements directly on Pandas DataFrames to perform complex cohort analyses and segmentations.
*   **Statistical Validation (SciPy):** Conducted Independent T-Tests to mathematically prove that operational friction (support tickets) was statistically linked to churn, ruling out random chance.
*   **Machine Learning (Scikit-Learn):** Built a Logistic Regression model using `class_weight='balanced'` to handle imbalanced data. Standardized features using `StandardScaler` and extracted "Feature Importance" (coefficients) to translate ML predictions into actionable business insights.
*   **Executive Dashboarding (Plotly):** Designed a highly interactive, dark-mode 4x4 grid dashboard summarizing 16 distinct visualizations, allowing stakeholders to trace the entire story from KPIs to root cause.

---

## 🧭 The Deep-Dive Analysis Journey (STARR Method)

### 1. SITUATION (The Business Context)
The company had a stable acquisition engine, bringing in roughly 5,000 new customers annually. However, leadership lacked visibility into their retention health. They needed to understand why 1 in 3 customers were leaving, and more importantly, what operational changes could stop the bleeding.

### 2. TASK (The Goal)
To move beyond descriptive statistics and perform a forensic root-cause analysis. The goals were:
1.  Build a robust, clean dataset from raw, messy CSVs.
2.  Systematically test demographic and behavioral hypotheses.
3.  Identify the specific "Danger Zone" in the customer lifecycle.
4.  Build a predictive model to output an actionable "Danger List" for the Customer Success team.
5.  Quantify the financial impact of the findings (Lost MRR & LTV).

### 3. ACTION (The Tracing Sequence)
This was not a linear process. I built a tracing sequence where every insight prompted the next question, methodically eliminating noise to find the signal.

**Phase 1: The Demographics Trap (Ruling out the noise)**
I started by testing the "usual suspects": Age, Gender, and Region. I binned ages into cohorts (18-25, 26-35, etc.) and calculated churn rates. The result was a **highly homogenized user base**. Demographics were a dead end. However, testing Income Level revealed a slight signal: Low-income customers churned at 34.1% vs. 27.5% for high-income, pointing toward potential price sensitivity.

**Phase 2: The 2024 Cohort Crisis (Finding the anomaly)**
I extracted the signup year to perform a cohort analysis. This exposed a massive anomaly. While the 2022 and 2023 cohorts churned at ~22.8%, the **2024 cohort was churning at 49.7%**. I had found the crisis.

**Phase 3: The "Double Whammy" (Root Cause Discovery)**
I drilled into the 2024 cohort. I discovered a fatal combination: **69.5%** of them were on Monthly contracts (vs. Yearly), and they were logging an average of 3.46 support tickets. When I isolated these two factors together, the result was catastrophic: **Customers on Monthly contracts with 3+ support tickets churned at 76.7%.**

**Phase 4: Statistical & Predictive Rigor**
To prove this wasn't a fluke, I ran a T-Test. The difference in support ticket volume between churned and retained users was statistically significant (p-value = 0.0000). I then trained a Logistic Regression model. Using `class_weight='balanced'` and `StandardScaler`, the model achieved a **91.5% accuracy rate** and successfully identified **90% of actual churners** (862 out of 957).

### 4. RESULT (The Findings)
The analysis delivered undeniable truths:
*   **The Financial Leak:** The company is losing **R$ 257,661.96** in MRR monthly. The average Customer Lifetime Value (LTV) is R$ 185.18.
*   **The 6-Month Danger Zone:** 55% of all churn happens within the first 3-6 months of a customer's lifecycle.
*   **The ML "Smoking Guns":** The Logistic Regression Feature Importance chart proved the top 3 predictors of churn are:
    1.  Days Since Last Login (Recency)
    2.  Number of Support Tickets (Operational friction)
    3.  Tenure (Newer accounts are at higher risk)

### 5. RECOMMENDATION (The Strategic Business Plan)
Based on the data, I didn't just provide insights; I provided a strategic playbook.

**1. Launch a "First 90 Days" Onboarding SWAT Team**
*   *The Data:* 55% of churn happens in the first 6 months.
*   *The Fix:* Automatically flag any new customer who logs 2+ support tickets in their first 90 days. A dedicated agent must call them immediately. Resolving their issue builds trust and prevents them from entering the "Danger Zone."

**2. Shift Acquisition Strategy to Annual Plans**
*   *The Data:* Monthly contracts are the primary driver of the 2024 crisis.
*   *The Fix:* Marketing must aggressively push annual plans with a 2-month discount. For existing monthly subscribers, offer an upgrade incentive. Annual contracts create psychological and financial commitment, structurally reducing churn.

**3. Deploy the "Danger List" Predictive Intervention**
*   *The Data:* The ML model identifies 90% of future churners.
*   *The Fix:* Feed the model's daily top 15 highest-risk customers to the Customer Success team. Provide them with a script to call these specific users, address their open tickets, and offer a loyalty incentive. Saving just 10% of this list protects millions in LTV.

---

## 📊 The Executive Dashboard
I synthesized 16 visualizations into a single interactive, dark-mode dashboard. This dashboard is designed for a CEO or VP of Customer Success to instantly grasp the KPIs, the demographic null results, the cohort crisis, the root causes, and the ML predictions.

**[Click here to view the Interactive Dashboard](saas_churn_executive_dashboard.html)** 
*(Note: Download the HTML file from this repository and open it in your browser to interact with the charts).*

**Dashboard Preview:**
`![Executive Dashboard](images/dashboard_preview.png)`

## 📂 Repository Structure
*   `analysis.ipynb` - Full Python, SQL, and Machine Learning pipeline (Data Cleaning -> EDA -> SQL Aggregations -> ML -> Visualization).
*   `saas_churn_executive_dashboard.html` - Interactive dark-mode executive dashboard.
*   `images/` - Screenshots of all key visualizations.
*   `README.md` - Project documentation.
￼
