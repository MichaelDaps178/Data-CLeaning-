# 🧹 Data Cleaning in SQL – Layoffs Dataset

This project is part of the **Data Cleaning in MySQL** tutorial by [Alex the Analyst](https://www.youtube.com/@AlextheAnalyst). The goal was to take a messy dataset containing layoff data and clean it using SQL for further analysis.

---

##  Project Overview

The original dataset contained inconsistent values, missing data, and formatting issues. This project walks through the process of using **MySQL** to clean and prepare the data for analysis.

###  Key Cleaning Steps:
- Removed duplicate rows
- Handled `NULL` and blank values
- Standardized text data (e.g. company names, industry fields)
- Filled missing `industry` values using **self-joins**
- Dropped unused columns
- Created a clean, analysis-ready final table

---

## 🛠 Tools Used
- **SQL**
- **MySQL Workbench**
- Layoffs dataset (CSV or staging table)
-Window Functions (`ROW_NUMBER()`, `PARTITION BY`)
- CTEs (Common Table Expressions)
- JOINS and Self-JOINS
- Data Standardization and Cleaning Techniques
---

## Sample Query Used

Here’s an example of a self-join to fill in missing industries based on matching company names:

```sql
SELECT *
FROM layoffs_staging2 t1
JOIN layoffs_staging2 t2
  ON TRIM(t1.company) = TRIM(t2.company)
WHERE (t1.industry IS NULL OR TRIM(t1.industry) = '')
  AND t2.industry IS NOT NULL AND TRIM(t2.industry) <> ''
