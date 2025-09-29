# Student Lifestyle Analytics — Step 3: Data Preparation & Feature Engineering
_Last updated: 2025-09-29_

## 0) Context
This document records all data cleaning, preparation, and feature engineering steps applied to the **Student Lifestyle Dataset**.  
The purpose is to ensure a high-quality dataset suitable for analysis, visualization (Power BI), and optional modeling.

---

## 1) Objectives
- Clean the dataset by removing outliers and enforcing sanity rules.  
- Encode categorical variables into usable formats.  
- Engineer new features to capture lifestyle patterns more effectively.  
- Produce a **final processed dataset** for analysis and visualization.

---

## 2) Cleaning Decisions

### 2.1 Outlier Handling
- **Physical Activity Hours:** Values above **10 hours/day** were capped to 10.  
  - Rationale: >10 hours/day of physical activity is unrealistic and skews analysis.  
- **Total Hours Constraint:** Rows where the sum of all activity hours exceeded **24 hours/day** were removed.  
  - Result: Dataset reduced from ~2000 to **1766 rows**.

### 2.2 Missing Values
- Checked with `.isna().sum()`.  
- **Result:** No missing values in the final dataset.

### 2.3 Data Types
- All time-based fields (`Study_Hours_Per_Day`, `Sleep_Hours_Per_Day`, etc.) confirmed as numeric (float).  
- GPA retained as float (0–4 scale).  
- Stress Level converted from text to dummy variables.

---

## 3) Categorical Encoding
- **Stress_Level** (Low, Moderate, High):  
  - Encoded into two dummy variables:  
    - `Stress_Level_Moderate` (1 if Moderate, else 0)  
    - `Stress_Level_High` (1 if High, else 0)  
  - `Stress_Level_Low` is the baseline and was dropped to avoid multicollinearity.

---

## 4) Feature Engineering
The following new variables were created to support richer analysis:

1. **Total_Hours**  
   - Definition: Sum of study, sleep, social, extracurricular, and physical hours.  
   - Purpose: Ensure realistic daily totals and enable workload comparisons.

2. **Study_Sleep_Ratio**  
   - Definition: `Study_Hours_Per_Day / Sleep_Hours_Per_Day`.  
   - Purpose: Measures balance between study and rest.

3. **Active_Hours**  
   - Definition: `Study + Physical Activity + Extracurricular + Social`.  
   - Purpose: Captures overall time spent in “active” (non-sleep) pursuits.

4. **GPA_Quartile**  
   - Definition: Quartile categorization of GPA into Q1 (Lowest) → Q4 (Highest).  
   - Purpose: Enables group comparisons of lifestyle patterns across performance levels.

---

## 5) Validation Checks
- **Row Count:** 1766 (after filtering invalid rows).  
- **No missing values:** Verified.  
- **Totals ≤24h:** Confirmed after filtering.  
- **No negative values:** Confirmed.  
- **Stress encoding:** Dummy variables consistent with original categories.

---

## 6) Final Dataset Overview
- **Shape:** 1766 rows × 13 columns  
- **Columns:**
  - `Student_ID`  
  - `Study_Hours_Per_Day`  
  - `Extracurricular_Hours_Per_Day`  
  - `Sleep_Hours_Per_Day`  
  - `Social_Hours_Per_Day`  
  - `Physical_Activity_Hours_Per_Day`  
  - `GPA`  
  - `GPA_Quartile`  
  - `Total_Hours`  
  - `Stress_Level_Moderate`  
  - `Stress_Level_High`  
  - `Study_Sleep_Ratio`  
  - `Active_Hours`  

---

## 7) Outputs
- Final cleaned dataset saved as:  
  `data/processed/student_lifestyle_final.csv`  
- To be used in:  
  - Step 4 (Analysis & Visualization in Power BI + Python)  
  - Step 5 (Optional modeling)  

---
