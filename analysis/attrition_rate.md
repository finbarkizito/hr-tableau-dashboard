# 📉 Attrition Rate Analysis — Methodology & Logic

## Overview

This project implements a **yearly attrition (turnover) analysis** using HR employee-level data spanning **2020–2024**.  
The objective is to calculate attrition rates in a way that is **statistically sound, comparable year-on-year, and decision-relevant**, rather than relying on naïve headcount snapshots.

The analysis follows industry-standard HR analytics principles, focusing on **population at risk over time**, not simple leaver counts.

---

## Data Fields Used

The dataset contains one row per employee with the following relevant fields:

- `EmployeeID`
- `HireDate`
- `TerminationDate` (null if employee is active)
- `Department`
- `JobLevel`
- `Gender`, `Age`, etc.

All calculations are derived from these fields without external assumptions.

---

## Analysis Window Design

### Why a Year-Based Approach Was Used

Attrition is inherently a **time-based metric**.  
To ensure consistency and comparability, the analysis is performed on a **full calendar-year basis** rather than arbitrary date ranges.

A **single Year parameter** is used as the source of truth for the analysis window.  
This avoids partial-year distortion and ensures each attrition rate is calculated over an equivalent exposure period.

---

## Parameter Configuration

### Analysis Year (Parameter)

- **Name:** `Analysis Year`
- **Type:** Integer
- **Allowed Values:**  
  `2020, 2021, 2022, 2023, 2024`

This parameter allows the user to select the year of interest while keeping all calculations internally consistent.

---

## Derived Date Boundaries

From the selected `Analysis Year`, fixed start and end dates are generated.

### Year Start Date

```tableau
MAKEDATE([Analysis Year], 1, 1)
```

## Year End Date

```tableau
MAKEDATE([Analysis Year], 12, 31)
```
These derived dates prevent user error and ensure that all calculations align to the same annual window.

---

### Attrition Calculation 
Attrition is calculated using the **population-at-risk approach**, which consists of four core components:

1. Leavers during the year  
2. Opening headcount  
3. Closing headcount  
4. Average headcount (denominator)  

---

### Leavers During the Year

Employees are classified as leavers if their termination date falls within the selected year.

```tableau
IF NOT ISNULL([TerminationDate])  
AND [TerminationDate] >= [Year Start Date]  
AND [TerminationDate] <= [Year End Date]  
THEN 1  
ELSE 0  
END
```

### Opening Headcount (Start of Year)

Opening headcount represents employees who were active on **1 January** of the analysis year.

```tableau
IF [HireDate] <= [Year Start Date]  
AND (  
    ISNULL([TerminationDate])  
    OR [TerminationDate] > [Year Start Date]  
)  
THEN 1  
ELSE 0  
END
```

