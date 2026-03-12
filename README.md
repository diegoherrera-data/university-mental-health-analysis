# University Mental Health Analysis: Depression & Anxiety Patterns

## Project Overview
This project explores the relationship between anxiety and depression in university students through data analysis. The main objective is to measure prevalence rates, compare groups by gender, and identify high-risk populations within a sample of **101 students**.

Understanding these correlations helps educational institutions identify vulnerable groups and design better mental health support programs.

---

## Dashboard Preview
![Mental Health Dashboard](mental_health_dashboard.png) 
*Note: Ensure the file name in the repository matches exactly to display the image.*

---

## Key Findings (Executive Summary)
Based on the statistical analysis of the dataset:
* **Prevalence:** The overall depression rate is **34.65%**, while anxiety prevalence stands at **33.7%**.
* **Critical Correlation:** Students with anxiety show a depression rate of **0.53**, more than double the rate of those without anxiety (**0.25**).
* **Gender Gap:** Female students report a higher depression rate (**0.39**) compared to male students (**0.23**).
* **Professional Help:** Only **15.6%** of the students have sought professional treatment.

---

## Tools Used
- **Excel & Power Query:** Data cleaning, normalization, and categorical standardization.
- **SQL:** Data exploration, relational filtering, and advanced metric calculation.
- **Power BI:** Data modeling and interactive visualization.

---

## Analytical Process

### 🧹 1. Data Cleaning & Normalization (Power Query)
- **Categorical Consistency:** Unified variations in the 'Year of Study' column (e.g., converting "year 1" to "Year 1") to ensure accurate grouping.
- **Text Standardization:** Cleaned and standardized 'Course' names to prevent category fragmentation.
- **Data Integrity:** Applied 'Trim' functions to remove trailing spaces and handled missing values to maintain a consistent sample of 101 records.

### 2. Exploratory Data Analysis (EDA)
- Used SQL to calculate prevalence rates and segment the population by gender and anxiety status to find correlations.

### 3. Data Visualization
- Developed an interactive Power BI dashboard using dynamic filters for **Gender** and **Anxiety Status** to highlight risk segments.

---

## SQL Analysis
I developed specific queries to extract mental health indicators and validate the co-occurrence of symptoms:

```sql
-- 1. Overall Depression Rate
SELECT 
    SUM(CASE WHEN Depression = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*) AS depression_rate
FROM mental_health;

-- 2. Depression Rate Segmented by Anxiety Status
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
To explore the dashboard interactively, download the .pbix file and open it using Microsoft Power BI Desktop.

---

## 🚀 Conclusion & Business Insights
The analysis reveals that **anxiety is a powerful predictor of depression** in the student population. Identifying students with high anxiety levels could allow universities to prioritize early mental health interventions. Furthermore, the identified gender gap suggests that support programs should be tailored to address the specific needs of different demographic groups.

---

## 📄 Repository Files
- `student_mental_health_clean.csv`: Cleaned and standardized dataset used for the analysis.
- `mental_health_dashboard.pbix`: Full Power BI project file.
- `mental_health_dashboard.png`: High-resolution dashboard screenshot.
