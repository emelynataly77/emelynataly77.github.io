---
title: Bellabeat Capstone – Full Analysis
layout: default
---

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

## Data Files

The following CSV files were used during data cleaning and analysis:

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
  
---

# 🧼 Data Cleaning in Excel <a name="excel-cleaning"></a>

I began with raw .csv files from the FitBit Fitness Tracker dataset. 

I completed basic cleaning including: 
  
- Removed null and duplicate values   
- Converted `datetime` columns for compatibility into SQL 
- Used =COUNTA(UNIQUE()) function to compare user ID counts across datasets

The table below represents the a summary of the cleaning completed on Excel: 

TABLE HERE/screenshot

<li><span style="color:gray;">`dailyActivity_merged.csv` → ">`dailyActivity.csv`  
<li><span style="color:gray;">`sleepDay_merged.csv` → ">`sleepDay.csv`  
<li><span style="color:gray;">`hourlyCalories_merged.csv` → ">`hourlyCalories.csv`  
<li><span style="color:gray;">`hourlyIntensities_merged.csv` → ">`hourlyIntensities.csv`  
<li><span style="color:gray;">`hourlySteps_merged.csv` → ">`hourlySteps.csv`

I decided that the data was too intolerabel to continue processing on Excel other than the basic cleaning mentioned above. So I decided to move over to the BigQueary platform and continue analyzing the necessary data. Nonetheless, Excel was extremely helpful in providing the first step in cleaning the data. Overall, Excel provided a quick and straightforward way to clean the data during the early stages of processing. 

NOTE: Moving forward I will be processing the data by grouping similiar datasets by datatype (e.g., daily, hourly) to help keep things organized and simple. 

NOTE: After cleaning the proper data on excel the files were saved without the unnecessary "merged" title. For example 'dailyCalories_merged' was changed to 'dailyCalories' and so on. 

---

# 🧮 SQL Queries in BigQuery <a name="sql-queries"></a>

The dataets I decided to upload into BigQuery were: 

-Insert file name here
  give example why this was included 

I checked whether a smooth upload was successful using the a few quick queries: 

The new merged daily file: "" can now be uploaded into RStudio to further analyze the data. 
NOTE: I named this file 'dailyMerged.csv' I kept the 'merged' wordage here because that is more representative of the data (which we merged) 

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
