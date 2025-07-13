---
layout: default
title: Bellabeat Capstone Project
---

# Bellabeat Capstone Project <a name="the-top"></a>

**Certificate:** Google Data Analytics  
**Tools Used:** Excel, SQL, RStudio  
**Skills Applied:** Data manipulation, statistical analysis, data visualization, critical thinking

---

# 🌝 Navigation

- [Overview](#overview)  
- [Excel Cleaning](#excel-cleaning)  
- [SQL Queries](#sql-queries)  
- [RStudio Analysis](#rstudio-analysis)  
- [Key Insights](#insights)  
- [Recommendations](#recommendations)
- [Acknowledgements](#Acknowledgements) 

---

# 🔍 Project Overview <a name="overview"></a>

This is the Google Data Analytics capstone project I chose to pursue...

---

# 🧼 Data Cleaning in Excel <a name="excel-cleaning"></a>

<!-- Cleaned section retained for brevity -->

---

# 🧲 SQL Queries in BigQuery <a name="sql-queries"></a>

### Hourly Data

- <span style="color:gray;">'hourlyCalories.csv'</span>
- <span style="color:gray;">'hourlySteps.csv'</span>
- <span style="color:gray;">'hourlyIntensities.csv'</span>

<details>
<summary>Show SQL Query</summary>

```sql
-- Remove NULLs from calories and steps
SELECT *
FROM `bellabeat-case-study.Fitabase.hourlyCalories`
WHERE Calories IS NOT NULL;

SELECT *
FROM `bellabeat-case-study.Fitabase.hourlySteps`
WHERE StepTotal IS NOT NULL;

-- Join hourly calories and steps
SELECT *
FROM `bellabeat-case-study.Fitabase.hourlyCalories` AS calories
JOIN `bellabeat-case-study.Fitabase.hourlySteps` AS steps
  ON calories.Id = steps.Id AND calories.ActivityHour = steps.ActivityHour;
```

</details>

---

### Daily/Sleep Data

- <span style="color:gray;">'dailyActivity.csv'</span>
- <span style="color:gray;">'dailyCalories.csv'</span>
- <span style="color:gray;">'dailyIntensities.csv'</span>
- <span style="color:gray;">'dailySteps.csv'</span>
- <span style="color:gray;">'sleepDay.csv'</span>

<details>
<summary>Show SQL Query</summary>

```sql
-- Remove NULLs from daily and sleep
SELECT *
FROM `bellabeat-case-study.Fitabase.dailyActivity`
WHERE TotalSteps IS NOT NULL;

SELECT *
FROM `bellabeat-case-study.Fitabase.sleepDay`
WHERE TotalMinutesAsleep IS NOT NULL;
```

</details>

---

## 💻 RStudio Analysis <a name="rstudio-analysis"></a>

### Hourly Data <a name="rstudio-hourly-data"></a>

<details>
<summary>Show R Code</summary>

```r
hourlyMerged1$activityDate <- as.Date(hourlyMerged1$activityDate, format="%Y-%m-%d")
```

</details>

### Daily/Sleep Data

<details>
<summary>Show R Code</summary>

```r
dailyActivity1 <- dailyActivity %>%
  select(Id, ActivityDate, TotalSteps, TotalDistance, Calories)

sleepDay_clean <- sleepDay %>%
  select(Id, SleepDay, TotalSleepRecords, TotalMinutesAsleep, TotalTimeInBed)
```

</details>

