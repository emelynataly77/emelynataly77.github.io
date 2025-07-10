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

## The Data 

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






Many datasets were too large to process on excel. Additionally, there were a few datasets that lacked too much information to be helpful or provide much insights. Also, there were datasets that contained repetitive data and overlapped with other existing datasets. Those datasets were dropped from further exploration. 


## Data Files

The following CSV files were used during data cleaning and analysis:

<div style="white-space: nowrap;">

  <!-- ✅ Used Files -->
  <ul style="display: inline-block; vertical-align: top; width: 45%; margin-right: 5%;">
    <li><span style="color:green;">`dailyActivity_merged.csv` → `dailyActivity.csv`</span></li>
    <li><span style="color:green;">`sleepDay_merged.csv` → `sleepDay.csv`</span></li>
    <li><span style="color:green;">`hourlyCalories_merged.csv` → `hourlyCalories.csv`</span></li>
    <li><span style="color:green;">`hourlyIntensities_merged.csv` → `hourlyIntensities.csv`</span></li>
    <li><span style="color:green;">`hourlySteps_merged.csv` → `hourlySteps.csv`</span></li>
  </ul>

  <!-- ❌ Unused Files -->
  <ul style="display: inline-block; vertical-align: top; width: 45%;">
    <li><span style="color:red;">'dailyCalories_merged.csv'</span></li>
    <li><span style="color:red;">'dailyIntensities_merged.csv'</span></li>
    <li><span style="color:red;">'dailySteps_merged.csv'</span></li>
    <li><span style="color:red;">'heartrate_seconds_merged.csv'</span></li>
    <li><span style="color:red;">'minuteCaloriesNarrow_merged.csv'</span></li>
    <li><span style="color:red;">'minuteCaloriesWide_merged.csv'</span></li>
    <li><span style="color:red;">'minuteIntensitiesNarrow_merged.csv'</span></li>
    <li><span style="color:red;">'minuteIntensitiesWide_merged.csv'</span></li>
    <li><span style="color:red;">'minuteMETsNarrow_merged.csv'</span></li>
    <li><span style="color:red;">'minuteSleep_merged.csv'</span></li>
    <li><span style="color:red;">'minuteStepsNarrow_merged.csv'</span></li>
    <li><span style="color:red;">'minuteStepsWide_merged.csv'</span></li>
    <li><span style="color:red;">'weightLogInfo_merged.csv'</span></li>
  </ul>

</div>



 After cleaning the proper data on excel the files were saved without the unnecessary "merged" title. For example 'dailyCalories_merged' was changed to 'dailyCalories' and so on.
I decided that the data was too intolerabel to continue processing on Excel other than the basic cleaning mentioned above. So I decided to move over to the BigQueary platform and continue analyzing the necessary data. Overall, Excel provided a quick and straightforward way to clean the data during the early stages of processing. 

NOTE: Moving forward I will be processing the data by grouping similiar datasets by datatype (e.g., daily, hourly) to help keep things organized and simple. 

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
