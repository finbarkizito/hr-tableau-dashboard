# Strategic Workforce Analytics & HR Performance Dashboard

## 🚀 Executive Summary
Designed a dual-view business intelligence solution enabling Human Resources stakeholders to monitor workforce dynamics, retention trends, and compensation equity across **8,950+ employee records**. By integrating high-level strategic KPIs with granular employee details in **Tableau**, the dashboard accelerates identification of turnover risks, gender pay gaps, and performance correlations—reducing time-to-insight for workforce planning.

---

## 💼 Business Problem
The HR department lacked a consolidated, decision-ready view of workforce data and relied on fragmented reports to answer critical organisational questions. Leadership faced uncertainty around:

- **Retention Health:** Are we losing talent at an accelerating rate, and which departments experience the highest churn?
- **Compensation Equity:** Do salary disparities exist between genders across education levels?
- **Demographic Risk:** Is the workforce aging, and is there over-reliance on HQ-based talent versus regional branches?
- **Performance Drivers:** Is there a measurable relationship between education level and employee performance?

---

## 🛠️ Methodology & Skills Demonstrated

**Tools:** Tableau Public · Python (Faker) · Figma  

### Analytical Approach

- **Data Engineering & Preparation**
  - Generated a robust synthetic HR dataset using **Python (Faker)** to simulate realistic hire dates, termination logic, salaries, and performance ratings.
  - Validated data types and built hierarchical relationships (Department → Job Title).

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


