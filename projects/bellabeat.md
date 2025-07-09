---
title: Bellabeat Capstone – Full Analysis
layout: default
---

# Bellabeat Capstone Project <a name="the-top"></a>

**Certificate:** Google Data Analytics  
**Tools Used:** Excel, SQL (BigQuery), RStudio  
**Skills Applied:** Data wrangling, SQL querying, statistical analysis, data visualization

---

## 🧭 Navigation

- [Overview](#overview)  
- [Excel Cleaning](#excel-cleaning)  
- [SQL Queries](#sql-queries)  
- [RStudio Analysis](#rstudio-analysis)  
- [Key Insights](#insights)  
- [Recommendations](#recommendations)  
- [📁 Files & Code](#files)

---

## 🔍 Project Overview <a name="overview"></a>

This capstone project for the Google Data Analytics Certificate analyzes smart device fitness data to uncover insights for Bellabeat — a women’s wellness company.

The goal was to explore how consumers use fitness devices and provide actionable recommendations to Bellabeat’s marketing strategy.

---

## 🧼 Data Cleaning in Excel <a name="excel-cleaning"></a>

I began with raw `.csv` files from the FitBit Fitness Tracker dataset. In Excel, I:

- Removed null and duplicate values  
- Renamed columns to consistent `snake_case` format  
- Converted `datetime` columns for compatibility  
- Manually inspected entries for anomalies

This prepared the data for SQL processing.

---

## 🧮 SQL Queries in BigQuery <a name="sql-queries"></a>

The cleaned Excel data was uploaded to BigQuery for querying. Example queries below:

```sql
-- Total steps per user per day
SELECT Id, activityDate, SUM(TotalSteps) AS daily_steps
FROM daily_activity
GROUP BY Id, activityDate
ORDER BY activityDate;

-- Average calories burned
SELECT Id, AVG(Calories) AS avg_calories
FROM daily_activity
GROUP BY Id;
