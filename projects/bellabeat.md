---
layout: default
title: Bellabeat Capstone Project
---

<link rel="stylesheet" href="/assets/css/code.css">
<link rel="stylesheet" href="/assets/css/syntax.css">

# Bellabeat Capstone Project <a name="the-top"></a>

**Certificate:** Google Data Analytics  
**Tools Used:** Excel, SQL, RStudio  
**Skills Applied:** Data manipulation, statistical analysis, data visualization, critical thinking

---

# 🧭 Navigation

- [Overview](#overview)  
- [Excel Cleaning](#excel-cleaning)  
- [SQL Queries](#sql-queries)  
- [RStudio Analysis](#rstudio-analysis)  
- [Key Insights](#insights)  
- [Recommendations](#recommendations)
- [Acknowledgements](#Acknowledgements) 

---

# 🔍 Project Overview <a name="overview"></a>

This is the Google Data Analytics capstone project I chose to persue. This case study analyzes smart device fitness data to uncover insights for Bellabeat — a women’s wellness company.
The goal was to explore how consumers use fitness devices and provide actionable recommendations to Bellabeat’s marketing strategy. 
I myself am very passionate about heath and wellness and reaching ones fitness goals and deeply enjoyed working on this subject matter. 
To further explore Bellabeat, the case study prompt or the Kaggle dataset used for this case study, please use the links provided below:

- [Bellabeat Official Website](https://bellabeat.com/)
- <a href="https://github.com/emelynataly77/emelynataly77.github.io/raw/main/projects/bellabeat_case_study.pdf" target="_blank">Case Study PDF</a>
- [FitBit Dataset on Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit)

---

### The Data 

The following .csv files were used during data cleaning and analysis:

<div style="display: flex; gap: 40px;">

  <ul style="list-style-type: disc;">
    <li><span style="color:gray;">'dailyActivity_merged.csv'</span></li>
    <li><span style="color:gray;">'dailyCalories_merged.csv'</span></li>
    <li><span style="color:gray;">'dailyIntensities_merged.csv'</span></li>
    <li><span style="color:gray;">'dailySteps_merged.csv'</span></li>
    <li><span style="color:gray;">'heartrate_seconds_merged.csv'</span></li>
    <li><span style="color:gray;">'hourlyCalories_merged.csv'</span></li>
  </ul>

  <ul style="list-style-type: disc;">
    <li><span style="color:gray;">'hourlyIntensities_merged.csv'</span></li>
    <li><span style="color:gray;">'hourlySteps_merged.csv'</span></li>
    <li><span style="color:gray;">'minuteCaloriesNarrow_merged.csv'</span></li>
    <li><span style="color:gray;">'minuteCaloriesWide_merged.csv'</span></li>
    <li><span style="color:gray;">'minuteIntensitiesNarrow_merged.csv'</span></li>
    <li><span style="color:gray;">'minuteIntensitiesWide_merged.csv'</span></li>
  </ul>

  <ul style="list-style-type: disc;">
    <li><span style="color:gray;">'minuteMETsNarrow_merged.csv'</span></li>
    <li><span style="color:gray;">'minuteSleep_merged.csv'</span></li>
    <li><span style="color:gray;">'minuteStepsNarrow_merged.csv'</span></li>
    <li><span style="color:gray;">'minuteStepsWide_merged.csv'</span></li>
    <li><span style="color:gray;">'sleepDay_merged.csv'</span></li>
    <li><span style="color:gray;">'weightLogInfo_merged.csv'</span></li>
  </ul>

</div>


After doing som research on the data ive learned that the data was collected in 2016 and represents 33 indivduals who decided to participate in having the data anlyzed. 2016 is not very recent, health data from previous years can be useful but for the purpose of planningmarketing strategies for a current market it seems more likely the company should use data that represents their current customer clientail. Moreover, there are no identities associated with the participants as everything has been left anonoymous. The data itself is not very reliable or consistent. Futhermore, many of the participants did not log data for many days, many datasets lack the 33 participants analyzed in this case study. Additionally, the way in which the participants were chosen is not shared meaning we do not know if these participants were chosen randomly, whether they were part a more active customer group, or whther they were part of a lesser active group. Because of the lack of consistent information and no information on thebackground of many of the participants the data seems to be unreliable. 

It is unknown how the data itself was collected. However, the data originated from a third party. Lastly, I owuld like to make it clear that this data was provided by th authors of the capstone project and the dataset itself was downloaded from a Kaggle user, any other information on how this user obained the data is not made clear. In my opinion the data quality is not great alas, I will continue to process and analyze, for the purpose of completing the case study. Onward!

  
  
---

# 🧼 Data Cleaning in Excel <a name="excel-cleaning"></a>

I began with raw .csv files from the FitBit Fitness Tracker dataset. 

I completed basic cleaning including: 
  
- Removed nulls, blanks, and duplicate values   
- Converted `datetime` columns for compatibility into SQL 
- Used =COUNTA(UNIQUE()) function to compare user ID counts across datasets

The table below represents a summary of the cleaning completed on Excel: 





<img src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/Screenshot%20(69).png" alt="Excel Table Screenshot" width="92%">






Many datasets were too large to process on excel and even too large to properly process on either Rstudio and BigQuery.  Additionally, there were a few datasets that were too inconsistent and incomplete to accurately deduct any type of analysis. Also, there were a ferw datasets that contained repetitive data and overlapped with other existing datasets. For example, dailyCalories_merged, dailyIntensities_merged adn dailySteps_merged overlapped with dailyActivity_merged which included all the information on those three files and then some. Therefore those three were dropped and only dailyActivity_merged would continue to be analyzed. Any datasets that met the criteria describes above were dropped from further exploration (red). Datasets that were eligible for proper processing were uplodaed into BigQueary and further processed





<ul>
  <!-- ✅ Green merged & renamed files -->
  <li><span style="color:green;">`hourlyCalories_merged.csv` → `hourlyCalories.csv`</span></li>
  <li><span style="color:green;">`hourlyIntensities_merged.csv` → `hourlyIntensities.csv`</span></li>
  <li><span style="color:green;">`hourlySteps_merged.csv` → `hourlySteps.csv`</span></li>
  <li><span style="color:green;">`sleepDay_merged.csv` → `sleepDay.csv`</span></li>
  <li><span style="color:green;">`dailyActivity_merged.csv` → `dailyActivity.csv`</span></li>
</ul>

<ul>
  <!-- ❌ Red unused or unrenamed files -->
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










 After cleaning the proper data on excel, the files were saved without the unnecessary "merged" title. For example 'dailyCalories_merged' was changed to 'dailyCalories' and so on.
I decided that the data was too intolerabel to continue processing on Excel other than the basic cleaning mentioned above. So I decided to move over to the BigQueary platform and continue analyzing the necessary data. Overall, Excel provided a quick and straightforward way to clean the data during the early stages of processing. 


NOTE: Moving forward I will be processing the data by grouping similiar datasets by their datatype (e.g., daily/sleep, hourly) to help keep things organized and straightforward. 

---


# 🧮 SQL Queries in BigQuery <a name="sql-queries"></a>


### Hourly Data

<li><span style="color:gray;">'hourlyCalories.csv'</span></li>
<li><span style="color:gray;">'hourlySteps.csv'</span></li>
<li><span style="color:gray;">'hourlyIntensities.csv'</span></li>
  

The hourly datasets above were uploaded into BigQuery. I checked if a smooth upload was successful by using the a few quick queries: 

---

Sucessful Upload Check 


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

The resulting data file: <span style="color:gray;">'hourlyMerged.csv'</span> can now be uploaded into RStudio to be further processed. 

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged). 

### Daily/Sleep Data

<li><span style="color:gray;">'dailyActivity.csv'</span></li>
<li><span style="color:gray;">'dailyCalories.csv'</span></li>
<li><span style="color:gray;">'dailyIntensities.csv'</span></li>
<li><span style="color:gray;">'dailySteps.csv'</span></li>
<li><span style="color:gray;">'sleepDay.csv'</span></li>

The daily datasets abover were uploaded into BigQuery. Again i quickly checked if the data was uploaded accurately using the code below: 

 
---

Successful upload check


  <details>
  <summary>Show SQL Query</summary>

```sql
-- Example SQL query for Daily/Sleep data check
SELECT *
FROM `bellabeat-case-study.Fitabase.dailyActivity`
WHERE TotalSteps IS NOT NULL;

SELECT *
FROM `bellabeat-case-study.Fitabase.sleepDay`
WHERE TotalMinutesAsleep IS NOT NULL;
```

</details>

---


The resulting data file: <span style="color:gray;">'daily_Merged.csv'</span> can now be uploaded into RStudio to be further processed. 

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged). 

## 🖥️ RStudio Analysis <a name="rstudio-analysis"></a>
This section covers the data cleaning, analysis, and visualization done in RStudio for the Bellabeat project.

### Hourly Data <a name="rstudio-hourly-data"></a>
Analysis of calories and steps by hour...

<details>
<summary>Show R Code</summary>

```r

hourlyMerged1$activityDate <- as.Date(hourlyMerged1$activityDate, format="%Y-%m-%d")
```

</details>


### Daily/Sleep Data

Exploration of daily activity and sleep patterns...

<details>
<summary>Show R Code</summary>

```r

dailyActivity1 <- dailyActivity %>%
  select(Id, ActivityDate, TotalSteps, TotalDistance, Calories)


sleepDay_clean <- sleepDay %>%
  select(Id, SleepDay, TotalSleepRecords, TotalMinutesAsleep, TotalTimeInBed)
```

</details>
