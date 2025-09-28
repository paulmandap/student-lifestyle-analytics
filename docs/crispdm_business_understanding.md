# Student Lifestyle & GPA Analysis (CRISP-DM)

## 1. Problem Statement
I want to identify which lifestyle habits (study, sleep, extracurriculars, socializing, physical activity) are associated with higher GPA, and translate those findings into simple, testable recommendations.

## 2. Objectives (Analyst-focused)
- Quantify relationships between lifestyle factors and GPA.  
- Detect potential diminishing returns (e.g., too much study or too little sleep).  
- Compare stress levels vs GPA and find patterns among top-GPA students.  
- **Produce**: a Power BI dashboard + an auto-generated PDF report summarizing insights and recommendations.  

## 3. Key Questions
- **Q1**: Which factors are most strongly correlated with GPA?  
- **Q2**: What study-sleep balance is associated with the best outcomes?  
- **Q3**: How does derived stress level relate to GPA?  
- **Q4**: What habits differentiate the top GPA quartile from the bottom?  
- **Q5**: What is the estimated GPA impact of +1 hour sleep or +1 hour study (holding others constant)?  

## 4. KPIs & Definitions
- **GPA (target)** — numeric 0–4 (assumption; confirm from data).  
- **StudyHours, SleepHours, SocialHours, PhysicalHours, ExtracurricularHours** — numeric 0–? (confirm typical ranges).  
- **StressLevel** — derived score (dataset description).  
- **Balanced Lifestyle Index (engineered later)**: (Study + Sleep + Physical + Social)/24.  
- **Efficiency Ratio (engineered later)**: StudyHours / SleepHours (sanity-checked).  

## 5. Hypotheses (to test)
- **H1**: Sleep 7–8 hours is positively associated with GPA.  
- **H2**: Very high study hours with low sleep shows lower GPA (diminishing returns).  
- **H3**: Higher stress level → lower GPA.  
- **H4**: Moderate physical activity → small positive association with GPA.  

## 6. Scope / Constraints
- **Scope**: Descriptive analytics + simple predictive modeling (linear/logistic).  
- **Out of scope**: causal claims; longitudinal interventions.  
- **Constraints**: single snapshot dataset; derived stress may embed assumptions.  

## 7. Success Criteria
Clear, interpretable visuals in Power BI.  
PDF report stating top 3 drivers, 2–3 practical recommendations.  
(Optional) Simple model with readable coefficients and metric (R²/MAE or Accuracy/F1).  

## 8. Risks & Mitigations
- Collinearity between lifestyle variables → check VIF / correlations, prefer interpretable models.  
- Outliers (e.g., 20h study/day) → cap at reasonable bounds.  
- Imbalanced categories → show confidence bands/describe uncertainty.  

## 9. Deliverables
- Power BI .pbix + dashboard screenshots.  
- Auto-generated PDF report.  
- Repository with notebook, cleaned data, and this CRISP-DM doc.  
