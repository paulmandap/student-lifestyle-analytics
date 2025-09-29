# Student Lifestyle Analytics — EDA (Exploratory Data Analysis)
_Last updated: 2025-09-28_

## 0) Context
**Objective:** Explore the Student Lifestyle dataset to understand how study, sleep, and other lifestyle habits relate to **GPA**. This is part of the CRISP-DM workflow, covering **Data Understanding** outputs and insights.

---

## 1) Dataset Overview
- **Rows:** 2,000
- **Columns:** 8
- **Target:** GPA (0–4 scale)
- **Predictors:** Study Hours, Sleep Hours, Social Hours, Extracurricular Hours, Physical Activity Hours, Stress Level

---

## 2) Summary Statistics

| Variable                        | Mean   | Std Dev | Min  | 25%  | 50%  | 75%  | Max  |
|---------------------------------|--------|---------|------|------|------|------|------|
| Study_Hours_Per_Day             | 7.48   | 1.42    | 5.00 | 6.3  | 7.4  | 8.7  | 10.0 |
| Sleep_Hours_Per_Day             | 7.50   | 1.46    | 5.00 | 6.2  | 7.5  | 8.8  | 10.0 |
| Social_Hours_Per_Day            | 2.70   | 1.69    | 0.00 | 1.2  | 2.6  | 4.1  | 6.0  |
| Extracurricular_Hours_Per_Day   | 1.99   | 1.16    | 0.00 | 1.0  | 2.0  | 3.0  | 4.0  |
| Physical_Activity_Hours_Per_Day | 4.33   | 2.51    | 0.00 | 2.4  | 4.1  | 6.1  | 13.0 |
| GPA                             | 3.12   | 0.30    | 2.24 | 2.9  | 3.11 | 3.33 | 4.0  |

**Stress Level distribution (%):**
- High: 51.45%  
- Moderate: 33.70%  
- Low: 14.85%  

---

## 3) Distributions & Outliers

- **Study Hours:** Normal-like distribution, most between 6–9h/day.  
- **Sleep Hours:** Centered at ~7–8h/day, balanced distribution.  
- **Social Hours:** Right-skewed, many at 0–3h/day, tail up to 6h.  
- **Extracurricular Hours:** Most between 1–3h, max 4h.  
- **Physical Activity:** Peak around 3–5h/day; outliers up to 13h (likely unrealistic).  
- **GPA:** Centered near 3.1, bell-shaped distribution with some clustering near 4.0.  

**Boxplots confirmed:** Outliers exist mainly in Physical Activity (>10h) and a few low GPAs (~2.2).

---

## 4) Correlations

From the correlation heatmap (Pearson):  
- **Study Hours & GPA:** **+0.73** → strong positive correlation.  
- **Sleep Hours & GPA:** near zero (–0.004) → surprisingly little effect.  
- **Social Hours & GPA:** –0.09 → weak negative.  
- **Extracurricular & GPA:** –0.03 → almost no effect.  
- **Physical Activity & GPA:** –0.34 → moderate negative correlation.  

⚠️ Interpretation: Unexpected **negative correlation** for Physical Activity may be due to outliers or confounding effects. Needs cautious interpretation.

---

## 5) Group Comparisons

### 5.1 GPA by Stress Level
- **High stress** group has the **highest median GPA** (~3.3).  
- **Low stress** group has the **lowest median GPA** (~2.8).  
- Counterintuitive: possibly reflects that more academically driven students report higher stress but also higher GPAs.  

### 5.2 GPA Quartiles (Top vs Bottom)
| Quartile      | Study Hours | Sleep Hours | Social Hours | Extracurricular | Physical Activity | GPA   |
|---------------|-------------|-------------|--------------|-----------------|------------------|-------|
| Q1 (Lowest)   | 6.14        | 7.62        | 2.86         | 2.01            | 5.37             | 2.74  |
| Q2            | 7.04        | 7.42        | 2.87         | 2.08            | 4.59             | 3.02  |
| Q3            | 7.93        | 7.36        | 2.59         | 1.92            | 4.20             | 3.22  |
| Q4 (Highest)  | 8.88        | 7.60        | 2.49         | 1.95            | 3.09             | 3.51  |

**Patterns:**  
- Higher GPA quartiles study **more hours** (Q4 ~8.9h vs Q1 ~6.1h).  
- Sleep is fairly stable (~7.4–7.6h across quartiles).  
- Higher GPA quartiles socialize slightly less.  
- Physical activity tends to **decrease** as GPA increases.  

---

## 6) Key Insights

1. **Study hours** are the **strongest driver** of GPA (r = +0.73).  
2. **Sleep** has no strong direct correlation with GPA, but consistently ~7–8h across quartiles suggests an optimal baseline.  
3. **Social hours** and **extracurricular hours** have weak or negligible effect on GPA.  
4. **Physical activity** shows a negative correlation with GPA; but outliers (>10h) and confounding may distort this. Moderate activity may still be healthy.  
5. **Stress level vs GPA:** “High stress” students show higher GPA, suggesting stress may be linked to academic drive. Needs careful narrative framing.  

---

## 7) Data Quality Decisions

- **Cap Physical Activity Hours** at ~10h/day to remove unrealistic outliers.  
- Re-confirm “Stress Level” categories are consistent (Low/Moderate/High).  
- Validate that no totals (study + sleep + others) exceed 24h/day (sanity check).  
- Maintain both raw and cleaned versions of the dataset.  

---

## 8) Outputs for Next Steps
- Clean dataset saved: `data/interim/student_lifestyle_clean.csv`.  
- These EDA insights will guide:  
  - **Feature engineering** (Step 3).  
  - **Dashboard visuals** (Power BI).  
  - **Modeling** (optional regression to predict GPA).  

---
