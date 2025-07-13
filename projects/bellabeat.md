---
layout: default
title: Bellabeat Capstone Project
---

# Bellabeat Capstone Project <a name="the-top"></a>

**Certificate:** Google Data Analytics  
**Tools Used:** Excel, SQL, RStudio  
**Skills Applied:** Data manipulation, statistical analysis, data visualization, critical thinking

---

# 🧭  Navigation

- [Overview](#overview)  
- [Excel Cleaning](#excel-cleaning)  
- [SQL Queries](#sql-queries)  
- [RStudio Analysis](#rstudio-analysis)  
- [Key Insights](#insights)  
- [Recommendations](#recommendations)  
- [Acknowledgements](#Acknowledgements) 

---

# 🔍 Project Overview <a name="overview"></a>

This is the Google Data Analytics capstone project I chose to pursue. This case study analyzes smart device fitness data to uncover insights for Bellabeat — a women’s wellness company.
The goal was to explore how consumers use fitness devices and provide actionable recommendations to Bellabeat’s marketing strategy.  
I myself am very passionate about health and wellness and reaching one's fitness goals and deeply enjoyed working on this subject matter. 
To further explore Bellabeat, the case study prompt or the Kaggle dataset used for this case study, please use the links provided below:

- [Bellabeat Official Website](https://bellabeat.com/)
- <a href="https://github.com/emelynataly77/emelynataly77.github.io/raw/main/projects/bellabeat_case_study.pdf" target="_blank">Case Study PDF</a>
- [FitBit Dataset on Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit)

---

### The Data 

The following `.csv` files were used during data cleaning and analysis:

<div style="display: flex; gap: 40px;">

<ul>
  <li><span style="color:gray;">'dailyActivity_merged.csv'</span></li>
  <li><span style="color:gray;">'dailyCalories_merged.csv'</span></li>
  <li><span style="color:gray;">'dailyIntensities_merged.csv'</span></li>
  <li><span style="color:gray;">'dailySteps_merged.csv'</span></li>
  <li><span style="color:gray;">'heartrate_seconds_merged.csv'</span></li>
  <li><span style="color:gray;">'hourlyCalories_merged.csv'</span></li>
</ul>

<ul>
  <li><span style="color:gray;">'hourlyIntensities_merged.csv'</span></li>
  <li><span style="color:gray;">'hourlySteps_merged.csv'</span></li>
  <li><span style="color:gray;">'minuteCaloriesNarrow_merged.csv'</span></li>
  <li><span style="color:gray;">'minuteCaloriesWide_merged.csv'</span></li>
  <li><span style="color:gray;">'minuteIntensitiesNarrow_merged.csv'</span></li>
  <li><span style="color:gray;">'minuteIntensitiesWide_merged.csv'</span></li>
</ul>

<ul>
  <li><span style="color:gray;">'minuteMETsNarrow_merged.csv'</span></li>
  <li><span style="color:gray;">'minuteSleep_merged.csv'</span></li>
  <li><span style="color:gray;">'minuteStepsNarrow_merged.csv'</span></li>
  <li><span style="color:gray;">'minuteStepsWide_merged.csv'</span></li>
  <li><span style="color:gray;">'sleepDay_merged.csv'</span></li>
  <li><span style="color:gray;">'weightLogInfo_merged.csv'</span></li>
</ul>

</div>

---

# 🧼 Data Cleaning in Excel <a name="excel-cleaning"></a>

- Removed nulls, blanks, and duplicate values
- Converted `datetime` columns for SQL compatibility
- Used `=COUNTA(UNIQUE())` to compare unique IDs across datasets

<img src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/Screenshot%20(69).png" alt="Excel Table Screenshot" width="92%">

<ul>
  <li><span style="color:green;">`hourlyCalories_merged.csv` → `hourlyCalories.csv`</span></li>
  <li><span style="color:green;">`hourlyIntensities_merged.csv` → `hourlyIntensities.csv`</span></li>
  <li><span style="color:green;">`hourlySteps_merged.csv` → `hourlySteps.csv`</span></li>
  <li><span style="color:green;">`sleepDay_merged.csv` → `sleepDay.csv`</span></li>
  <li><span style="color:green;">`dailyActivity_merged.csv` → `dailyActivity.csv`</span></li>
</ul>

<ul>
  <li><span style="color:red;">`dailyCalories_merged.csv`</span></li>
  <li><span style="color:red;">`dailyIntensities_merged.csv`</span></li>
  <li><span style="color:red;">`dailySteps_merged.csv`</span></li>
  <li><span style="color:red;">`heartrate_seconds_merged.csv`</span></li>
  <li><span style="color:red;">`minuteCaloriesNarrow_merged.csv`</span></li>
  <li><span style="color:red;">`minuteCaloriesWide_merged.csv`</span></li>
  <li><span style="color:red;">`minuteIntensitiesNarrow_merged.csv`</span></li>
  <li><span style="color:red;">`minuteIntensitiesWide_merged.csv`</span></li>
  <li><span style="color:red;">`minuteMETsNarrow_merged.csv`</span></li>
  <li><span style="color:red;">`minuteSleep_merged.csv`</span></li>
  <li><span style="color:red;">`minuteStepsNarrow_merged.csv`</span></li>
  <li><span style="color:red;">`minuteStepsWide_merged.csv`</span></li>
  <li><span style="color:red;">`weightLogInfo_merged.csv`</span></li>
</ul>

---

# 🧮 SQL Queries in BigQuery <a name="sql-queries"></a>

### Hourly Data

- <span style="color:gray;">'hourlyCalories.csv'</span>
- <span style="color:gray;">'hourlySteps.csv'</span>
- <span style="color:gray;">'hourlyIntensities.csv'</span>

<details>
<summary>Show SQL Query</summary>

```
sql
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

```
sql
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

```
r
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
