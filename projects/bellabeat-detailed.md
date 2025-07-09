---
title: Bellabeat Capstone – Full Analysis
layout: default
---
# 📊 Bellabeat Capstone – Full Project Analysis

**Certificate:** Google Data Analytics Capstone  
**Tools Used:** Excel, SQL (BigQuery), RStudio  
**Skills Applied:** Data cleaning, transformation, SQL querying, statistical analysis, data visualization

---

## 📝 Project Prompt

Analyze smart device usage data to help Bellabeat, a high-tech wellness company for women, gain insights into how users use their smart devices and how that can guide marketing strategy.

**Project Goal:** Provide actionable recommendations for how Bellabeat can improve its product and user engagement.

---

## 🧼 Step 1: Data Cleaning in Excel

Before any analysis, I manually inspected the raw `.csv` files in Excel to:

- Remove rows with null/NA values
- Standardize column names and formats (e.g., `snake_case`)
- Convert date/time columns into consistent formats
- Filter out duplicate or irrelevant entries

This allowed for clean and structured input when importing into SQL.

---

## 🧮 Step 2: SQL Queries in BigQuery

I imported the cleaned data into BigQuery to run aggregation and filtering queries. Below are example code snippets:

```sql
-- Total steps by day
SELECT activityDate, SUM(TotalSteps) AS total_steps
FROM daily_activity
GROUP BY activityDate
ORDER BY activityDate;

-- Average calories by user
SELECT Id, AVG(Calories) AS avg_calories
FROM daily_activity
GROUP BY Id;
