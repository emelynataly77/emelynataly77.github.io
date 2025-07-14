---
layout: default
title: Bellabeat Capstone Project
permalink: /bellabeat.html
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
- [Key Insights](#key-insights)
- [Acknowledgements](#acknowledgements)
  
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

# 🧹 Data Cleaning in Excel <a name="excel-cleaning"></a>

I began with raw .csv files from the FitBit Fitness Tracker dataset. 

<br>
I completed basic cleaning including: 
  
- Removed nulls, blanks, and duplicate values   
- Converted `datetime` columns for compatibility into SQL 
- Used =COUNTA(UNIQUE()) function to compare user ID counts across datasets

<br>

The table below represents a summary of the cleaning completed on Excel: 





<img src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/Screenshot%20(69).png" alt="Excel Table Screenshot" width="92%"> 



<br>


Many datasets were too large to process on excel and even too large to properly process on either Rstudio and BigQuery.  Additionally, there were a few datasets that were too inconsistent and incomplete to accurately deduct any type of analysis. Also, there were a ferw datasets that contained repetitive data and overlapped with other existing datasets. For example, dailyCalories_merged, dailyIntensities_merged adn dailySteps_merged overlapped with dailyActivity_merged which included all the information on those three files and then some. Therefore those three were dropped and only dailyActivity_merged would continue to be analyzed. Any datasets that met the criteria describes above were dropped from further exploration (red). Datasets that were eligible for proper processing were uplodaed into BigQueary and further processed

<div style="display: flex; justify-content: space-between; gap: 40px;">

  <!-- Green Section -->
  <div style="flex: 1;">
    <h4 style="color:green;"><span style="color:green;">✔️</span> Renamed Files</h4>
    <ul>
      <li><span style="color:gray;">`hourlyCalories_merged.csv` → `hourlyCalories.csv`</span></li>
      <li><span style="color:gray;">`hourlyIntensities_merged.csv` → `hourlyIntensities.csv`</span></li>
      <li><span style="color:gray;">`hourlySteps_merged.csv` → `hourlySteps.csv`</span></li>
      <li><span style="color:gray;">`sleepDay_merged.csv` → `sleepDay.csv`</span></li>
      <li><span style="color:gray;">`dailyActivity_merged.csv` → `dailyActivity.csv`</span></li>
      <li><span style="color:gray;">`dailyCalories_merged.csv` → `dailyCalories.csv`</span></li>
      <li><span style="color:gray;">`dailyIntensities_merged.csv` → `dailyIntensities.csv`</span></li>
      <li><span style="color:gray;">`dailySteps_merged.csv` → `dailySteps.csv`</span></li>
    </ul>
  </div>

  <!-- Red Section -->
  <div style="flex: 1;">
    <h4 style="color:red;">❌ Removed Files</h4>
    <ul>
      <li><span style="color:gray;">`minuteCaloriesNarrow.csv`</span></li>
      <li><span style="color:gray;">`minuteCaloriesWide.csv`</span></li>
      <li><span style="color:gray;">`minuteIntensitiesNarrow.csv`</span></li>
      <li><span style="color:gray;">`minuteIntensitiesWide.csv`</span></li>
      <li><span style="color:gray;">`minuteMETsNarrow.csv`</span></li>
      <li><span style="color:gray;">`minuteSleep.csv`</span></li>
      <li><span style="color:gray;">`minuteStepsNarrow.csv`</span></li>
      <li><span style="color:gray;">`dailyIntensities_merged.csv`</span></li>
      <li><span style="color:gray;">`dailyCalories_merged.csv`</span></li>
    </ul>
  </div>

</div>















 After cleaning the proper data on excel, the files were saved without the unnecessary "merged" title. For example 'dailyCalories_merged' was changed to 'dailyCalories' and so on.
I decided that the data was too intolerabel to continue processing on Excel other than the basic cleaning mentioned above. So I decided to move over to the BigQueary platform and continue analyzing the necessary data. Overall, Excel provided a quick and straightforward way to clean the data during the early stages of processing. 


NOTE: Moving forward I will be processing the data by grouping similiar datasets by their datatype (e.g., daily/sleep, hourly) to help keep things organized and straightforward. 

---


# 🧮 SQL Queries in BigQuery <a name="sql-queries"></a>


### Hourly Data

- <span style="color:gray;">'hourlyCalories.csv'</span>
- <span style="color:gray;">'hourlySteps.csv'</span>
- <span style="color:gray;">'hourlyIntensities.csv'</span>
  

The hourly datasets above were uploaded into BigQuery. I checked if a smooth upload was successful by using a few quick queries
<br>

---

Successful Upload Check: 


<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
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
</code></pre>

</details>

<br> 
Next, I decided to combine the three hourly datasets mentioned above becasus they had overlapping data and create one dataset that contained all the necessary information.
<br>


I used the following query to merge the hourly datasets:

<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
-- Merge hourly data files using left join
SELECT A.Id, A.ActivityHour AS activity_hour, A.Calories, C.StepTotal AS step_total, I.TotalIntensity AS total_intensity, I.AverageIntensity AS average_intensity,
FROM `capstone-case-study-460717.Fitness_Tracker_Data.hourlycalories` A
LEFT JOIN `capstone-case-study-460717.Fitness_Tracker_Data.hourlysteps` C
ON
A.Id=C.Id
AND A.ActivityHour=C.ActivityHour
LEFT JOIN `capstone-case-study-460717.Fitness_Tracker_Data.hourlyintensities` I
ON
A.Id=I.Id
AND A.ActivityHour=C.ActivityHour
</code></pre>

</details>

<br>

The resulting data file: <span style="color:gray;">'hourlyMerged.csv'</span> can now be uploaded into RStudio to be further processed. 

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged). 

### Daily/Sleep Data


- <span style="color:gray;">'dailyActivity.csv'</span>
- <span style="color:gray;">'dailyCalories.csv'</span>
- <span style="color:gray;">'dailyIntensities.csv'</span>
- <span style="color:gray;">'dailySteps.csv'</span>
- <span style="color:gray;">'sleepDay.csv'</span>

The daily datasets abover were uploaded into BigQuery. Again i quickly checked if the data was uploaded accurately using the code below
<br>

 
---

Successful upload check:


<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
-- Remove NULLs from calories and steps
SELECT *
FROM `bellabeat-case-study.Fitabase.hourlyCalories`
WHERE Calories IS NOT NULL;

SELECT *
FROM `bellabeat-case-study.Fitabase.hourlySteps`
WHERE StepTotal IS NOT NULL;

-- Join hourly calories and steps
SELECT A.Id, A.ActivityHour AS activity_hour, A.Calories, C.StepTotal AS step_total, I.TotalIntensity AS total_intensity, I.AverageIntensity AS average_intensity,
FROM `capstone-case-study-460717.Fitness_Tracker_Data.hourlycalories` A
LEFT JOIN `capstone-case-study-460717.Fitness_Tracker_Data.hourlysteps` C
ON
A.Id=C.Id
AND A.ActivityHour=C.ActivityHour
LEFT JOIN `capstone-case-study-460717.Fitness_Tracker_Data.hourlyintensities` I
ON
A.Id=I.Id
AND A.ActivityHour=C.ActivityHour
</code></pre>

</details>

<br> 
Next, I decided to combine the three hourly datasets mentioed above becasue they had overlapping data and create one dataset that contained all the necessary information.

I used the following query to merge the daily/sleep datasets:

<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
-- Merge daily/sleep datasets using inner join
SELECT
  activity.Id,
  ActivityDate,
  TotalSteps,
  TotalDistance,
  TrackerDistance,
  LoggedActivitiesDistance,
  (VeryActiveDistance + ModeratelyActiveDistance) AS LongerDistance,
  (LightActiveDistance + SedentaryActiveDistance) AS ShorterDistance,
  (VeryActiveMinutes + FairlyActiveMinutes) AS HeavyActiveMinutes,
  (LightlyActiveMinutes + SedentaryMinutes) AS LightActiveMinutes,
  Calories,
  sleep.TotalSleepRecords,
  sleep.TotalMinutesAsleep,
  sleep.TotalTimeInBed
FROM `bellabeat-461300.fittracker.daily_activity` AS activity
INNER JOIN `bellabeat-461300.fittracker.sleep_day` AS sleep
  ON activity.Id = sleep.Id
  AND activity.ActivityDATE = sleep.SleepDay;

</code></pre>

</details>

<br>

After merging the daily data files i peeked at the correlation coefficients  (r) on excel between the data, i found that sleep and non-active minutes had a somehwat negative correlation (-0.5869588). Suggesting, sleep has a somewhat stronger effect on if an individual will be active the following day. 
The resulting merged data file: <span style="color:gray;">'dailyMerged.csv'</span> can now be uploaded into RStudio to be further processed. 

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged). 

# 🖥️ RStudio Analysis <a name="rstudio-analysis"></a>
This section covers the data cleaning, analysis, and visualization done in RStudio for the Bellabeat project.

### Hourly Data <a name="rstudio-hourly-data"></a>
- <span style="color:gray;">'hourlyMerged.csv'</span>

The dataset abover was uploaded into BigQuery. Again i quickly checked if the data was uploaded accurately using the code below
<br>

Successful Upload check: 
<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
library(tidyverse)

# Load data
hourly_df <- read_csv("SQL hourly_merged.csv")

# View column names
colnames(hourly_df)

# Check participant counts
n_distinct(hourly_df$Id)   # Number of unique participants in hourly data
</code></pre>

</details>

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

### Daily/Sleep Data
- <span style="color:gray;">'dailyMerged.csv'</span>

The dataset abover was uploaded into BigQuery. Again i quickly checked if the data was uploaded accurately using the code below
<br>

Successful Upload check: 
<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
library(tidyverse)

# Load data
daily_df  <- read_csv("SQL daily_merged.csv")

# View column names
colnames(hourly_df)

# Check participant counts
n_distinct(hourly_df$Id)   # Number of unique participants in hourly data
</code></pre>

</details>

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# Pearson correlation tests
cor.test(daily_df$TotalMinutesAsleep, daily_df$HeavyActiveMinutes, method = "pearson")
cor.test(daily_df$TotalMinutesAsleep, daily_df$LightActiveMinutes, method = "pearson")

# Plot sleep vs light activity
library(ggplot2)

ggplot(data = daily_df, aes(x = TotalMinutesAsleep, y = LightActiveMinutes)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE, col = "blue") +
  labs(
    y = "Light/Non‑active minutes",
    x = "Total minutes asleep"
  ) +
  ggtitle("Relationship Between Sleep and Light/Non Activity")

</code></pre>

</details>

INSERT GGPLOT GRAPH 
The graph above suggests that people who sleep more may be more active during the day. The low p value (2.2e-16) confirms statistical significance. I wanted to look further into the day by day breakdown of the data between sleep adn non-activity. In the code block below I filter the data for each day of the week and generate summary statistics for the filtered datasets.

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

I used the following coded blocks to generate respetive graphs representing my results of the stat summaries. 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

INSERT AVERAGE STEPS BY WEEKDAY GRAPH

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

INSERT AVERAGE ACTIVE MINUTES BY WEEKDAY GRAPH

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

INSERT AVERAGE SEDENTARY MINUTES BY WEEKDAY GRAPH

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

INSERT AVERAGE CALORIES BY WEEKDAY GRAPH

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

INSERT AVERAGE HOURS OF SLEEP BY WEEDAY GRAPH

Looking at the graohs it becomes more clear that the beginning of the work week (mon/tues) tend to be higher on all the generated graphs along wiht saturday. Fridays tend to be the lowest on most of the graphs suggesting a more relaxed Fiday in terms of the data. 

# 💡 Key Insights
- <span style="color:gray;">'INSIGHT 1'</span>
- <span style="color:gray;">'INSIGHT 2'</span>
- <span style="color:gray;">'INSIGHT 3'</span>

---

### Proposal
I believe that bellbeat copany....insert proposal ideas an reasoning here

# 🤝 Acknowledgements
I would like to thank Ed Garcia for his guidance on RStudio 
  https://www.kaggle.com/code/edgarcia1/bellabeat-case-study-analysis-and-visualizations 
I would like to thank Tom Leary for his guidance on grouping data by datatype
  https://tomleary.net/projects/capstone/ 
