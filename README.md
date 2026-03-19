# University Mental Health: Depression & Anxiety Patterns

## Project Overview
This project explores the relationship between anxiety and depression in university students through quantitative data analysis. Using a sample of **101 students**, the objective was to measure prevalence rates, identify high-risk demographic segments, and establish the statistical correlation between different mental health conditions.

This analysis provides evidence-based insights to help educational institutions design targeted mental health support programs and early intervention strategies.

---

## Dashboard Preview
![Mental Health Dashboard](mental_health_dashboard.png)  
*(Interactive visualization of mental health indicators, gender gaps, and treatment rates).*

---

## Tech Stack
* **Excel & Power Query:** Data cleaning, normalization, and categorical standardization.
* **SQL:** Data exploration, relational filtering, and advanced metric calculation (Prevalence rates).
* **Power BI:** Data modeling, DAX measures, and interactive reporting.

---

## Key Findings (Executive Summary)
* **Prevalence Rates:** The overall depression rate is **34.65%**, while anxiety prevalence stands at **33.7%**.
* **The "Co-occurrence" Factor:** Students with anxiety show a depression rate of **0.53**, more than double the rate of those without anxiety (**0.25**).
* **Gender Disparity:** Female students report a significantly higher depression rate (**0.39**) compared to male students (**0.23**).
* **Treatment Gap:** Only **15.6%** of students in the sample have sought professional help, indicating a significant barrier to access.

---

## Analytical Process: Data Cleaning
Mental health datasets are often categorical and "noisy". I used **Power Query** to ensure data integrity:
* **Normalization:** Unified 'Year of Study' variations (e.g., converting "year 1" to "Year 1") for accurate grouping.
* **Standardization:** Cleaned 'Course' names to prevent category fragmentation during visualization.
* **Integrity Checks:** Applied 'Trim' functions to remove trailing spaces and handled missing values to maintain a consistent sample of 101 records.

---

## SQL Analysis
I developed specific queries to transform qualitative responses into quantitative indicators and validate symptom co-occurrence:

```sql
-- 1. Overall Depression Rate
SELECT 
    SUM(CASE WHEN Depression = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS depression_rate
FROM mental_health;

-- 2. Depression Rate Segmented by Anxiety Status (Correlation Check)
SELECT 
    Anxiety, 
    COUNT(*) AS total_students,
    SUM(CASE WHEN Depression = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS depression_rate
FROM mental_health
GROUP BY Anxiety;

-- 3. Mental Health Gender Gap Analysis
SELECT 
    Gender, 
    SUM(CASE WHEN Depression = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS depression_rate
FROM mental_health
GROUP BY Gender
ORDER BY depression_rate DESC;
## Repository Files
- `student_mental_health_clean.csv`: Cleaned and standardized dataset used for the analysis.
- `mental_health_dashboard.pbix`: Full Power BI project file.
- `mental_health_dashboard.png`: High-resolution dashboard screenshot.
```

---

## 🚀 Institutional Insights & Recommendations

1. **Early Intervention:** The analysis confirms that **anxiety is a powerful predictor of depression**. Universities should prioritize students reporting high anxiety for early psychological screening.
2. **Tailored Support:** The identified **gender gap** suggests that mental health awareness campaigns should be tailored to address the specific stressors and help-seeking behaviors of different demographic groups.
3. **Closing the Treatment Gap:** With only **15.6%** of students seeking help, there is a clear need to reduce stigma and increase the visibility of available campus counseling services.
4. **Academic Integration:** Since mental health directly impacts performance, these insights should be used by academic advisors to identify "at-risk" students during peak stress periods (finals/midterms).

---

## 📁 Repository Files
- `student_mental_health_clean.csv`: Cleaned and standardized dataset.
- `mental_health_dashboard.pbix`: Full Power BI project file.
- `mental_health_dashboard.png`: High-resolution dashboard preview.

---

### 📝 Analyst's Note:
As a Psychology student and Data Analyst, this project represents my ability to apply **evidence-based decision-making** to human behavior. I focused on the "Anxiety-Depression" correlation to show how data can pinpoint exactly where resources are most needed.
