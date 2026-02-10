# Workforce Analytics & HR Performance Dashboard

## Summary
Designed a dual-view business intelligence solution enabling Human Resources stakeholders to monitor workforce dynamics, retention trends, and compensation equity across **8,950+ employee records**. By integrating strategic KPIs with granular employee details in **Tableau**, from this, we can identify turnover risks, gender pay gaps, and performance correlations which redues time-to-insight for workforce planning.

🔗 **Interactive Dashboard:**  
[View the live Tableau Public dashboard](https://public.tableau.com/app/profile/finbar.kizito/viz/HRdashboard_17697193047110/HRISummary)

---

## Business Problem
The HR department lacked a consolidated, decision-ready view of workforce data and relied on fragmented reports to answer critical organisational questions. Leadership faced uncertainty around:

- **Retention Health:** Are we losing talent at an accelerating rate, and which departments experience the highest churn?
- **Compensation Equity:** Do salary disparities exist between genders across education levels?
- **Demographic Risk:** Is our workforce aging and at what rate, and is there over-reliance on HQ-based talent versus regional branches?
- **Performance Drivers:** Is there a measurable relationship between education level and employee performance?

---

## Methodology & Skills Demonstrated

**Tools:** Tableau Public · Python · Figma  

### Analytical Approach

- **Data Engineering & Preparation**
  - Generated an HR dataset using **Python** to simulate realistic hire dates, termination logic, salaries, and performance ratings.
  - From this, data tyes were validated and heirarchical relatonships (Department → Job Title).

- **KPI Logic & Calculations**
  - Classified **Active vs. Terminated** employees using `IF/THEN` logic with `ISNULL` checks on termination dates.
  - Computed **Employee Age** and **Tenure** dynamically using `DATEDIFF` relative to the current date.
  - Created **Age Bands** and **Salary Bins** to support segmentation analysis.

- **Advanced Tableau Techniques**
  - **Gap Analysis (Dual-Axis):** Visualised gender pay differentials using layered bar and reference mark techniques.
  - **Correlation Analysis:** Used scatter plots and heat maps to evaluate relationships between education, salary, and performance.
  - **Viz-in-Tooltip:** Embedded secondary charts in tooltips to enable the drill-down without disrupting dashboard context.

- **Dashboard Architecture & UX**
  - Designed a **two-layer navigation system** (Executive Summary vs. Employee Detail) using parameter actions and navigation buttons.
  - Implemented a high-fidelity background layout designed in **Figma** to improve visual hierarchy and user adoption.

---

## Insights

### Workforce Compensation & Capability Overview
This analysis consolidates multiple employee-focused dashboards to assess how compensation aligns with experience, education, and performance across the organisation. The objective is to move beyond descriptive reporting and identify structural strengths, governance watchpoints, and decision-relevant implications for workforce strategy.

---

### Compensation Scales with Experience, with Targeted Market Exceptions
Analysis of **salary versus age** shows a clear upward relationship between experience and compensation, indicating a coherent progression framework. Senior and managerial roles are appropriately concentrated in higher salary bands, while a subset of younger employees earn above-average pay, reflecting market pricing for specialist or high-impact roles.

**Implications**  
This pattern suggests a balanced compensation strategy that combines tenure-based progression with selective pay premiums for scarce skills. Such a structure supports competitiveness in tight labour markets without undermining internal pay coherence.

**Watchpoint:**  
More experienced employees earning below the company average represent a potential retention and engagement risk if progression pathways are unclear or constrained. This group warrants targeted monitoring rather than broad compensation restructuring.

---

### Education Delivers Consistent Returns Without Systemic Gender Distortion
Average salary increases consistently from **High School → Bachelor → Master → PhD**, indicating disciplined returns to education. Gender-based differences are minimal at entry level, widen modestly at Bachelor level, and narrow or disappear at higher qualifications, with PhD-level compensation appearing fully aligned.

**So what:**  
Compensation at higher qualification levels is primarily driven by skill scarcity and role criticality rather than gender. The absence of widening gaps at senior or specialist levels suggests no evidence of systemic gender bias in pay-setting.

**Watchpoint:**  
Bachelor-level variation merits deeper, role-normalised review to confirm whether differences reflect role mix and progression patterns rather than emerging structural misalignment.

---

### Performance Improves with Education but Plateaus at Higher Levels
Performance ratings improve materially from lower to mid education levels, with fewer low-performance outcomes among Bachelor and Master-qualified employees. At Master and PhD levels, performance distributions stabilise, indicating diminishing marginal returns from additional qualifications.

**So what:**  
Education strengthens baseline capability, but long-term performance differentiation is driven more by role fit, execution, and scope of responsibility than by credentials alone. This reinforces the importance of development, leadership, and role design at senior levels.

---

### Executive Takeaway
The organisation demonstrates a **coherent and defensible people strategy**. Compensation generally aligns with experience and education, selectively rewards high-value skills, and shows no indication of systemic gender imbalance at senior levels. Identified risks are localised—mid-career pay compression and early-career progression clarity—supporting targeted intervention rather than wholesale reform.

---

## Business Recommendations

1. **Pay Equity Audit:** Conduct a focused compensation review for Bachelor’s-degree roles to address identified gender pay gaps and reduce legal and reputational exposure (Could this be due to hours worked?).
2. **Talent Distribution Strategy:** Reduce dependency on HQ-based talent by incentivising hiring and retention in regional branches.
3. **Targeted Upskilling:** Introduce development programmes for employees with High School levels of education to improve performance outcomes.
4. **Retention Intervention:** Use the detailed employee view to flag high-performing staff with tenure >5 years for proactive retention discussions.

---

## Limitations & Next Steps

- **Live Integration:** Future iterations should connect to an HRIS API (e.g. Workday, BambooHR) for real-time reporting.
- **Attrition Tracking:** Churn rate analysis requires historical snapshots; a future enhancement would involve warehouse-style snapshot tables to enable month-over-month attrition tracking.

---
