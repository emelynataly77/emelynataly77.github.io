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

- [Project Overview](#project-overview)  
- [Excel Cleaning](#excel-cleaning)  
- [SQL Queries](#sql-queries)  
- [RStudio Analysis](#rstudio-analysis)  
- [Key Insights](#key-insights)
- [Acknowledgements](#acknowledgements)
  
---

# 🔍 Project Overview <a id="project-overview"></a>

This is the Google Data Analytics capstone project I chose to persue. This case study analyzes smart device fitness data to uncover insights for Bellabeat — a women’s wellness company.
The goal was to explore how consumers use fitness devices and provide actionable recommendations to Bellabeat’s marketing strategy. 
I myself am very passionate about heath and wellness and reaching ones fitness goals and deeply enjoyed working on this subject matter. 
To further explore Bellabeat, the case study prompt or the Kaggle dataset used for this case study, please use the links provided below:

- [Bellabeat Official Website](https://bellabeat.com/)
- <a href="https://github.com/emelynataly77/emelynataly77.github.io/raw/main/projects/bellabeat_case_study.pdf" target="_blank">Case Study PDF</a>
- [FitBit Dataset on Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit)

---

### The Data <a id="the-data"></a>

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

# 🧹 Excel Cleaning <a id="excel-cleaning"></a>

I began with raw .csv files from the FitBit Fitness Tracker dataset. 
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
      <li><span style="color:gray;">'weightLogInfo_merged.csv'</span></li>
    </ul>
  </div>

</div>















 After cleaning the proper data on excel, the files were saved without the unnecessary "merged" title. For example 'dailyCalories_merged' was changed to 'dailyCalories' and so on.
I decided that the data was too intolerabel to continue processing on Excel other than the basic cleaning mentioned above. So I decided to move over to the BigQueary platform and continue analyzing the necessary data. Overall, Excel provided a quick and straightforward way to clean the data during the early stages of processing. 


NOTE: Moving forward I will be processing the data by grouping similiar datasets by their datatype (e.g., daily/sleep, hourly) to help keep things organized and straightforward. 

---


# 🧮 SQL Queries in BigQuery <a id="sql-queries"></a>

### Hourly Data <a id="hourly-data-sql"></a>

- <span style="color:gray;">'hourlyCalories.csv'</span>
- <span style="color:gray;">'hourlySteps.csv'</span>
- <span style="color:gray;">'hourlyIntensities.csv'</span>
  

The hourly datasets above were uploaded into BigQuery. I checked if a smooth upload was successful by using a few quick queries
<br>



Successful Upload Check: 

<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
-- Row count
SELECT COUNT (*) as row_count
FROM `bellabeat-461300.fittracker.hourly_calories` 
--Check for NULL values in columns
SELECT
  COUNTIF(Id IS NULL) AS id_nulls,
  COUNTIF(ActivityHour IS NULL) AS activity_hour_nulls,
  COUNTIF(Calories IS NULL) AS calories_nulls
FROM `bellabeat-461300.fittracker.hourly_calories`;
-- Preview Data
SELECT *
FROM `bellabeat-461300.fittracker.hourly_calories` LIMIT 10;
</code></pre>

</details>



<br> 
I completed the above three querires for all of the hourly data sets after uploading. After I felt comfprtable that the data was ploaded correctly I decided to combine the three hourly datasets. The hourly datasets contained overlapping data that was repetiative and unncescesary. I combined them into one data set so that they owuld beocme easier to handle and analyze later on. 
<br>



I used the following query to merge the hourly datasets:

<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
-- Merge hourly calories, steps, and intensities datasets using LEFT JOIN on Id and ActivityHour
SELECT A.Id, A.ActivityHour AS activity_hour, A.Calories, C.StepTotal AS step_total, I.TotalIntensity AS total_intensity, I.AverageIntensity AS average_intensity,
FROM `bellabeat-461300.fittracker.hourly_calories` A
LEFT JOIN `bellabeat-461300.fittracker.hourly_steps` C
ON
A.Id=C.Id
AND A.ActivityHour=C.ActivityHour
LEFT JOIN `bellabeat-461300.fittracker.hourly_intensities` I
ON
A.Id=I.Id
AND A.ActivityHour=C.ActivityHour
</code></pre>

</details>



<br>
The resulting data file: <span style="color:gray;">'hourlyMerged.csv'</span> can now be uploaded into RStudio to be further processed. 

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged). 


### Daily/Sleep Data <a id="daily-sleep-data-sql"></a>

- <span style="color:gray;">'dailyActivity.csv'</span>
- <span style="color:gray;">'dailyCalories.csv'</span>
- <span style="color:gray;">'dailyIntensities.csv'</span>
- <span style="color:gray;">'dailySteps.csv'</span>
- <span style="color:gray;">'sleepDay.csv'</span>


The daily datasets abover were uploaded into BigQuery. Again i quickly checked if the data was uploaded accurately using a few wuick queries.
<br>


 
Successful upload check:

<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
-- Row count
SELECT COUNT (*) as row_count
FROM `bellabeat-461300.fittracker.sleep_day` 
--Check for NULL values in columns
SELECT
  COUNTIF(Id IS NULL) AS id_nulls,
  COUNTIF(SleepDay IS NULL) AS sleep_day_nulls,
  COUNTIF(TotalSleepRecords IS NULL) AS total_sleep_records_nulls,
  COUNTIF(TotalMinutesAsleep IS NULL) AS total_minutes_asleep_nulls,
  COUNTIF(TotalTimeInBed IS NULL) AS total_time_in_bed_nulls
FROM `bellabeat-461300.fittracker.sleep_day`;
-- Preview Data
SELECT *
FROM `bellabeat-461300.fittracker.sleep_day` LIMIT 10;
</code></pre>

</details>



<br> 
I completed the above querys for the dailyactivity dataset as well. Next, I decided to combine the dailyactivity and sleepday datasets as they had some correspondonding data. It was also cleaner to just develop two datasets (hourly and daily/sleep) so sleepday was also added to the daily dataset. 
<br>



I used the following query to merge the dailyactivity sleepday datasets:

<details>
<summary>Show SQL Query</summary>

<pre><code class="language-sql">
-- Join daily activity and sleep datasets using INNER JOIN on Id and matching date fields
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
The resulting merged data file: <span style="color:gray;">'dailyMerged.csv'</span> can now be uploaded into RStudio to be further processed. 

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged). 

# 🖥️ RStudio Analysis <a id="rstudio-analysis"></a>
This section covers the data cleaning, analysis, and visualization done in RStudio for the Bellabeat project.

### Hourly Data <a id="hourly-data-r"></a>
- <span style="color:gray;">'hourlyMerged.csv'</span>

First I loaded the packages that I will be needing for the hourly and daily data analysis in RStudio. I will be using tidyverse and lubridate. Next, I uploaded both my hourly_merged datasets. 

Load packages and merged data into RStudio

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
#load packages needed for analysis
library(tidyverse)
library(lubridate)
#import hourly_merged dataset
hourly_df<- read_csv("hourly_merged.csv")
</code></pre>

</details>

Again I quickly checked if the data was uploaded accurately using the code below. 
<br>

Successful Upload check: 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
#Preview the data
head(hourly_df)
# A tibble: 6 × 10
          Id activity_hour       Calories step_total total_intensity average_intensity activityDate time               
      # <dbl> <dttm>                 <dbl>      <dbl>           <dbl>             <dbl> <date>       <dttm>             
1 7086361926 2016-04-23 01:00:00       68          0               1            0.0167 2016-04-23   2025-07-15 01:00:00
2 7086361926 2016-04-23 01:00:00       68          0               1            0.0167 2016-04-23   2025-07-15 01:00:00
3 7086361926 2016-04-23 01:00:00       68          0               1            0.0167 2016-04-23   2025-07-15 01:00:00
4 7086361926 2016-04-23 01:00:00       68          0               2            0.0333 2016-04-23   2025-07-15 01:00:00
5 7086361926 2016-04-23 01:00:00       68          0               2            0.0333 2016-04-23   2025-07-15 01:00:00
6 7086361926 2016-04-23 01:00:00       68          0               2            0.0333 2016-04-23   2025-07-15 01:00:00
# ℹ 2 more variables: DayOfWeek <chr>, TimeOfDay <fct>
</code></pre>

</details>
  
After confirming the file was uploaded correctly, I began analyzing the data from both a day-of-the-week and time-of-day perspective. To do this, I first split the `activity_hour column` (which contains combined date and time values) into two separate columns: `activityDate` for the date and `time` for the time. I then converted the `activityDate` column into proper Date format and used it to create a new weekday column that indicates the day of the week. Similarly, I converted the time column and used it to categorize each entry into time-of-day segments—Night, Morning, Afternoon, and Evening—based on the hour of the activity. You can see the following code below.

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
#split data and assigned metrics
hourly_df$activityDate <- str_split_fixed(hourly_df$activity_hour, " ", n = 2)[, 1]
hourly_df$time <- str_split_fixed(hourly_df$activity_hour, " ", n = 2)[, 2]
hourly_df$activityDate <- as.Date(hourly_df$activityDate, format="%Y-%m-%d")
hourly_df$DayOfWeek <- format(as.Date(hourly_df$activityDate), "%A")
breaks <- hour(hms("00:00:00", "05:59:59", "11:59:59", "17:59:59", "23:59:59"))
labels <- c("Night", "Morning", "Afternoon", "Evening")
hourly_df$time  <- as.POSIXct(hourly_df$time, format = "%H:%M:%S")
hourly_df$TimeOfDay <- cut(x =  hour(hourly_df$time), breaks = breaks, labels = labels, include.lowest=TRUE)
  
#check for na values after pushing metrics and splitting data
colSums(is.na(hourly_df))
               Id     activity_hour          Calories        step_total   total_intensity 
                0                 0                 0                 0                 0 
average_intensity      activityDate              time         DayOfWeek         TimeOfDay 
                0                 0            650227                 0            650227  
</code></pre>

</details>

I went ahead and also performed a correlation test (similar to what we did in the daily/sleep data). I just wanted to grasp possible relationships amongst the data. 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
cor.test(hourly_df$average_intensity, hourly_df$Calories, method = "pearson")

   Pearson's product-moment correlation
data:  hourly_df$average_intensity and hourly_df$Calories
t = 147.75, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
0.03713366 0.03813135
sample estimates:
cor = 0.03763252

cor.test(hourly_df$total_intensity, hourly_df$Calories, method = "pearson")

   Pearson's product-moment correlation
data:  hourly_df$total_intensity and hourly_df$Calories
t = 147.75, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
0.03713366 0.03813136
sample estimates:
cor = 0.03763252

cor.test(hourly_df$total_intensity, hourly_df$step_total, method = "pearson")

   Pearson's product-moment correlation
data:  hourly_df$total_intensity and hourly_df$step_total
t = 170.87, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
0.04301144 0.04400866
sample estimates:
cor = 0.04351006

cor.test(hourly_df$average_intensity, hourly_df$step_total, method = "pearson")

   Pearson's product-moment correlation
data:  hourly_df$average_intensity and hourly_df$step_total
t = 170.87, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
0.04301144 0.04400866
sample estimates:
cor = 0.04351006
</code></pre>

</details>


Shockingly, there didnt seem to be any substantial correlation between intensity and steps taken or intensity and calories burned. Since we split the data into time of day I wanted to also check at which points of the day individuals were being more or less active. I would assume participants would be more active during the morning or evening times considering, work schedules and common physical activity timeslots. However, this assumption dos not account for the weekends.  I wrote up the following two code blocks to analyze time of day activity throught the week (SUN-SAT).

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# Filter data for "Morning" time period and select relevant columns
morninghr <- hourly_df1 %>%
  filter(TimeOfDay == "Morning") %>%
  select(step_total, total_intensity, calories)

# View summary statistics for the morning activity
summary(morninghr)
   step_total     total_intensity     Calories    
 Min.   :   0.0   Min.   :  0.00   Min.   : 42.0  
 1st Qu.:   0.0   1st Qu.:  0.00   1st Qu.: 68.0  
 Median : 104.0   Median :  3.00   Median : 84.0  
 Mean   : 374.8   Mean   : 12.06   Mean   :101.7  
 3rd Qu.: 467.0   3rd Qu.: 16.00   3rd Qu.:117.0  
 Max.   :8976.0   Max.   :180.00   Max.   :544.0
</code></pre>

</details>

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

The charts below represent my findings 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
INSERT CODE
</code></pre>

</details>

INSERT AVERAGE STEPS BY TIME OF DAY 
INSERT AVERAGE CALORIES BY TIME OF DAY 

 I was a little surprised to find that most users were significantly more active during the afternoon and not the morning and evening. This could be notworthy as to who bellabeats targer customers could be (people who do not usually work a 9-5?) Moreover, that would of course require more data thtan we currently have. Just somthing to keep in mind for future research/refernce. The evening and morning being relatively the same was unsurprising. The sama ecan be said for nightime being the the time users were the least active. 
 
### Daily/Sleep Data <a id="daily-sleep-data-r"></a>
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

# 💡 Key Insights <a id="key-insights"></a>
- Early on during the data research phase I discovered gaps and inconsitensies that point to flawed or inadequate data recording/gathering. Meaning, bellabeat needs to work on properly gathering reliable/substantial data from their users. Or they need to find a way to push their customers into logging data more consistently. 
- There are specific days of the week in which customers are less likely to be more active. Users are more active during the week. excluding friday which is the least active reported day. 
- Encourage other aspects of health more readily such as, weight and nutritional intake through the fitbit.
- Users are more active during the week
- Step counts are generally lower than the recommneded average, encourage walking or set walking goals
- Sleep is below average recom?


---

### Proposal <a id="proposal"></a>
(make it easier to log make more comfy desigh)
 Implement design improvments that encourage other aspects of health more readily such as, weight and nutritional intake.

#  🤝 Acknowledgements <a id="acknowledgements"></a>

I would like to thank Ed Garcia for his guidance on RStudio 
  https://www.kaggle.com/code/edgarcia1/bellabeat-case-study-analysis-and-visualizations 
I would like to thank Tom Leary for his guidance on grouping data by datatype
  https://tomleary.net/projects/capstone/ 
