# Student Lifestyle — Data Dictionary

## Columns

| Field                           | Type    | Description                                          | Min   | Max   | Average   | Distinct | Notes |
|---------------------------------|---------|------------------------------------------------------|-------|-------|-----------|----------|-------|
| Student_ID                      | Int64   | Unique identifier for each student record            | 1     | 1000  | 500.5     | 1000     | Identifier only, not used for analysis |
| Study_Hours_Per_Day             | Number  | Hours spent studying per day                         | 5     | 10    | 7.4613    | 51       | Continuous numeric |
| Extracurricular_Hours_Per_Day   | Number  | Hours spent in extracurricular activities per day    | 0     | 4     | 2.0241    | 41       | Continuous numeric |
| Sleep_Hours_Per_Day             | Number  | Hours slept per day                                  | 5     | 10    | 7.5115    | 51       | Continuous numeric |
| Social_Hours_Per_Day            | Number  | Hours spent socializing per day                      | 0     | 6     | 2.67179   | 61       | Continuous numeric |
| Physical_Activity_Hours_Per_Day | Number  | Hours spent on physical activity/exercise per day    | 0     | 13    | 4.3313    | 112      | Continuous numeric (possible outliers >10h) |
| GPA                             | Number  | Academic performance score (0–4 scale)              | 2.24  | 4     | 3.11735   | 143      | Target variable |
| Stress_Level                    | Text    | Derived stress category (Low / Moderate / High)      | N/A   | N/A   | N/A       | 3        | Categories: Low, Moderate, High |

---
