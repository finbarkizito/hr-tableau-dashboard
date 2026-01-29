# Workforce Analytics & HR Performance Dashboard

## Summary
Designed a dual-view business intelligence solution enabling Human Resources stakeholders to monitor workforce dynamics, retention trends, and compensation equity across **8,950+ employee records**. By integrating strategic KPIs with granular employee details in **Tableau**, from this, we cam identify turnover risks, gender pay gaps, and performance correlations which redues time-to-insight for workforce planning.

🔗 **Interactive Dashboard:**  
[View the live Tableau Public dashboard](https://public.tableau.com/app/profile/finbar.kizito/viz/HRdashboard_17697193047110/HRISummary)

---

## Business Problem
The HR department lacked a consolidated, decision-ready view of workforce data and relied on fragmented reports to answer critical organisational questions. Leadership faced uncertainty around:

- **Retention Health:** Are we losing talent at an accelerating rate, and which departments experience the highest churn?
- **Compensation Equity:** Do salary disparities exist between genders across education levels?
- **Demographic Risk:** Is the workforce aging, and is there over-reliance on HQ-based talent versus regional branches?
- **Performance Drivers:** Is there a measurable relationship between education level and employee performance?

---

## Methodology & Skills Demonstrated

**Tools:** Tableau Public · Python (Faker) · Figma  

### Analytical Approach

- **Data Engineering & Preparation**
  - Generated a robust synthetic HR dataset using **Python (Faker)** to simulate realistic hire dates, termination logic, salaries, and performance ratings.
  - From this, data tyes were validated and heirarchical relatonships (Department → Job Title).

- **KPI Logic & Calculations**
  - Classified **Active vs. Terminated** employees using `IF/THEN` logic with `ISNULL` checks on termination dates.
  - Computed **Employee Age** and **Tenure** dynamically using `DATEDIFF` relative to the current date.
  - Created **Age Bands** and **Salary Bins** to support segmentation analysis.

- **Advanced Tableau Techniques**
  - **Gap Analysis (Dual-Axis):** Visualised gender pay differentials using layered bar and reference mark techniques.
  - **Correlation Analysis:** Used scatter plots and heat maps to evaluate relationships between education, salary, and performance.
  - **Viz-in-Tooltip:** Embedded secondary charts in tooltips to enable drill-down without disrupting dashboard context.

- **Dashboard Architecture & UX**
  - Designed a **two-layer navigation system** (Executive Summary vs. Employee Detail) using parameter actions and navigation buttons.
  - Implemented a high-fidelity background layout designed in **Figma** to improve visual hierarchy and user adoption.

---

## Results & Key Insights

- **Workforce Concentration:** The organisation is heavily centralised, with a disproportionate share of employees based at the New York HQ—posing scalability and resilience risks.
- **Compensation Disparities:**
  - At **Bachelor’s degree level**, male employees earn higher average salaries than female peers.
  - At **PhD level**, the trend reverses, with female employees earning approximately **25% more** on average.
- **Performance Correlation:** Higher education levels strongly correlate with stronger performance ratings; PhD holders cluster in “Excellent,” while High School graduates show higher “Needs Improvement” rates.
- **Managerial Demographics:** HR Managers are significantly younger on average, while Finance Managers represent the highest-paid and oldest cohort.

---

## Business Recommendations

1. **Pay Equity Audit:** Conduct a focused compensation review for Bachelor’s-degree roles to address identified gender pay gaps and reduce legal and reputational exposure.
2. **Talent Distribution Strategy:** Reduce dependency on HQ-based talent by incentivising hiring and retention in regional branches.
3. **Targeted Upskilling:** Introduce development programmes for employees with High School education levels to improve performance outcomes.
4. **Retention Intervention:** Use the detailed employee view to flag high-performing staff with tenure >5 years for proactive retention discussions.

---

## Limitations & Next Steps

- **Synthetic Data:** Insights are derived from Python-generated data; patterns reflect realistic logic but not real organisational behaviour.
- **Live Integration:** Future iterations should connect to an HRIS API (e.g. Workday, BambooHR) for real-time reporting.
- **Attrition Tracking:** Churn rate analysis requires historical snapshots; a future enhancement would involve warehouse-style snapshot tables to enable month-over-month attrition tracking.

---
