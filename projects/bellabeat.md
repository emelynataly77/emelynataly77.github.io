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
# load packages needed for analysis
install.packages
library(tidyverse)
library(lubridate)
library(qwraps2)
# import hourly_merged dataset
hourly_df <- read_csv("hourly_merged.csv")
</code></pre>

</details>

Again I quickly checked if the data was uploaded accurately using the code below. 
<br>


Successful Upload check:

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# Preview the data
head(hourly_df)
# A tibble: 6 x 10
          Id activity_hour       Calories step_total total_intensity average_intensity activityDate time
       &lt;dbl&gt; &lt;dttm&gt;                 &lt;dbl&gt;      &lt;dbl&gt;           &lt;dbl&gt;             &lt;dbl&gt; &lt;date&gt;       &lt;dttm&gt;
1 7086361926 2016-04-23 01:00:00       68          0               1            0.0167 2016-04-23   2025-07-15 01:00:00
2 7086361926 2016-04-23 01:00:00       68          0               1            0.0167 2016-04-23   2025-07-15 01:00:00
3 7086361926 2016-04-23 01:00:00       68          0               1            0.0167 2016-04-23   2025-07-15 01:00:00
4 7086361926 2016-04-23 01:00:00       68          0               2            0.0333 2016-04-23   2025-07-15 01:00:00
5 7086361926 2016-04-23 01:00:00       68          0               2            0.0333 2016-04-23   2025-07-15 01:00:00
6 7086361926 2016-04-23 01:00:00       68          0               2            0.0333 2016-04-23   2025-07-15 01:00:00
# ℹ 2 more variables: DayOfWeek &lt;chr&gt;, TimeOfDay &lt;fct&gt;

# Check the structure of the data
str(hourly_df)
spc_tbl_ [15,393,213 x 10] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
 $ Id               : num [1:15393213] 7.09e+09 7.09e+09 7.09e+09 ...
 $ activity_hour    : POSIXct[1:15393213], format: "2016-04-23 01:00:00" ...
 $ Calories         : num [1:15393213] 68 68 68 ...
 $ step_total       : num [1:15393213] 0 0 0 ...
 $ total_intensity  : num [1:15393213] 1 1 1 ...
 $ average_intensity: num [1:15393213] 0.0167 0.0167 ...
 $ activityDate     : Date[1:15393213], format: "2016-04-23" ...
 $ time             : POSIXct[1:15393213], format: "2025-07-15 01:00:00" ...
 $ DayOfWeek        : chr [1:15393213] "Saturday" "Saturday" ...
 $ TimeOfDay        : Factor w/ 4 levels "Night","Morning",..: 1 1 1 ...
 - attr(*, "spec")=
  .. cols(
  ..   Id = col_double(),
  ..   activity_hour = col_datetime(format = ""),
  ..   Calories = col_double(),
  ..   step_total = col_double(),
  ..   total_intensity = col_double(),
  ..   average_intensity = col_double()
  .. )
 - attr(*, "problems")=&lt;externalptr&gt;

# Check the dimensions
dim(hourly_df)
[1] 15393213       10
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
	
cor.test(hourly_df$step_total, hourly_df$Calories, method = "pearson")

	Pearson's product-moment correlation

data:  hourly_df$step_total and hourly_df$Calories
t = 5498.6, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.8138534 0.8141904
sample estimates:
     cor 
0.814022
</code></pre>

</details>


Shockingly, there didnt seem to be any substantial linear correlation between intensity and steps taken or intensity and calories burned. Since we split the data into time of day I wanted to also check at which points of the day individuals were being more or less active. I would assume participants would be more active during the morning or evening times considering, work schedules and common physical activity timeslots. However, this assumption dos not account for the weekends.  I wrote up the following two code blocks to analyze time of day activity throught the week (SUN-SAT).

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# Filter data for "Morning" time period and select relevant columns
morninghr <- hourly_df %>%
  filter(TimeOfDay == "Morning") %>%
  select(step_total, total_intensity, Calories)

# View summary statistics for the morning activity
summary(morninghr)
   step_total     total_intensity     Calories    
 Min.   :   0.0   Min.   :  0.00   Min.   : 42.0  
 1st Qu.:   0.0   1st Qu.:  0.00   1st Qu.: 68.0  
 Median : 104.0   Median :  3.00   Median : 84.0  
 Mean   : 374.8   Mean   : 12.06   Mean   :101.7  
 3rd Qu.: 467.0   3rd Qu.: 16.00   3rd Qu.:117.0  
 Max.   :8976.0   Max.   :180.00   Max.   :544.0
  
# Filter data for "Afternoon" time period and select relevant columns
afternoonhr <- hourly_df %>%
+ filter(hourly_df$TimeOfDay == "Afternoon") %>%
+ select(c(step_total, total_intensity, Calories))

# View summary statistics for the afternoon activity
summary(afternoonhr)
   step_total      total_intensity     Calories    
 Min.   :    0.0   Min.   :  0.00   Min.   : 42.0  
 1st Qu.:   37.0   1st Qu.:  0.00   1st Qu.: 77.0  
 Median :  259.0   Median :  3.00   Median : 96.0  
 Mean   :  519.6   Mean   : 12.06   Mean   :115.9  
 3rd Qu.:  620.0   3rd Qu.: 16.00   3rd Qu.:131.0  
 Max.   :10554.0   Max.   :180.00   Max.   :948.0  

# Filter data for "Evening" time period and select relevant columns  
Eveninghr <- hourly_df %>%
+ filter(hourly_df$TimeOfDay == "Evening") %>%
+ select(c(step_total, total_intensity, Calories))
  
# View summary statistics for the evening activity
summary(eveninghr)
   step_total     total_intensity     Calories    
 Min.   :   0.0   Min.   :  0.00   Min.   : 42.0  
 1st Qu.:   0.0   1st Qu.:  0.00   1st Qu.: 69.0  
 Median : 114.0   Median :  3.00   Median : 86.0  
 Mean   : 370.9   Mean   : 12.06   Mean   :102.1  
 3rd Qu.: 398.0   3rd Qu.: 16.00   3rd Qu.:113.0  
 Max.   :8586.0   Max.   :180.00   Max.   :834.0   

# Filter data for "Night" time period and select relevant columns  
nighthr <- hourly_df %>%
+ filter(hourly_df$TimeOfDay == "Night") %>% 
+ select(c(step_total, total_intensity, Calories))

# View summary statistics for the night activity
summary(nighthr)
   step_total      total_intensity     Calories     
 Min.   :   0.00   Min.   :  0.00   Min.   : 42.00  
 1st Qu.:   0.00   1st Qu.:  0.00   1st Qu.: 56.00  
 Median :   0.00   Median :  3.00   Median : 68.00  
 Mean   :  21.28   Mean   : 12.06   Mean   : 71.68  
 3rd Qu.:   0.00   3rd Qu.: 16.00   3rd Qu.: 83.00  
 Max.   :2844.00   Max.   :180.00   Max.   :669.00   
</code></pre>

</details>

We can see by looking at the summaries that Night has a really low step count(~21) compared to the oter times of day. This makes sense as most people are asleep during the "Night" time-frame. 
Moreover, let go ahead and calculate only for the average stps and calories as thats how we will tell more or less how activity levels based on time of day. 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
#create morning list
morninghr_list <- 
+ list(
+ list("Total_Steps_Avg" = ~mean(morninghr$step_total)),
+ list("Calories_Avg" = ~ mean(morninghr$Calories))
+ )
#creasete morning summary list and view summary
morninghr_sum <- summary_table(morninghr, morninghr_list)
print.default(morninghr_sum)
                          morninghr (N = 3,886,786)
[1,] "\\bf{}"             "~"                      
[2,] "~~ Total_Steps_Avg" "374.758472938825"       
[3,] "\\bf{}"             "~"                      
[4,] "~~ Calories_Avg"    "101.664592287818"       
attr(,"class")
[1] "qwraps2_summary_table" "qwraps2_qable"        
attr(,"qable_args")
attr(,"qable_args")$rtitle
[1] ""

attr(,"qable_args")$rgroup
[1] 1 1

attr(,"qable_args")$rnames
[1] "Total_Steps_Avg" "Calories_Avg"   

attr(,"qable_args")$cnames
[1] ""                          "morninghr (N = 3,886,786)"

attr(,"qable_args")$markup
[1] "latex"

attr(,"qable_args")$kable_args
list()
	
#create afternoon list 
afternoonhr_list <-
+ list(
+ list("Total_Steps_Avg" = ~ mean(afternoonhr$step_total)),
+ list("Calories_Avg" = ~ mean(afternoonhr$Calories))
+ )
	
#create summary table for afternoon and view summary
afternoonhr_sum <- summary_table(afternoonhr, afternoonhr_list)
print.default(afternoonhr_sum)
                          afternoonhr (N = 3,825,364)
[1,] "\\bf{}"             "~"                        
[2,] "~~ Total_Steps_Avg" "519.599624506321"         
[3,] "\\bf{}"             "~"                        
[4,] "~~ Calories_Avg"    "115.866206457738"         
attr(,"class")
[1] "qwraps2_summary_table" "qwraps2_qable"        
attr(,"qable_args")
attr(,"qable_args")$rtitle
[1] ""

attr(,"qable_args")$rgroup
[1] 1 1

attr(,"qable_args")$rnames
[1] "Total_Steps_Avg" "Calories_Avg"   

attr(,"qable_args")$cnames
[1] ""                            "afternoonhr (N = 3,825,364)"

attr(,"qable_args")$markup
[1] "latex"

attr(,"qable_args")$kable_args
list()

#create evening lsit
eveninghr_list <- 
+ list(
+ list("Total_Steps_Avg" = ~ mean(eveninghr$step_total)),
+ 
+ list("Calories_Avg" = ~ mean(eveninghr$Calories))
+ )

#create summary for evening list and view summary
 eveninghr_sum <- summary_table(eveninghr, eveninghr_list)
print.default(eveninghr_sum)
                          eveninghr (N = 3,784,154)
[1,] "\\bf{}"             "~"                      
[2,] "~~ Total_Steps_Avg" "370.922424933024"       
[3,] "\\bf{}"             "~"                      
[4,] "~~ Calories_Avg"    "102.146365607742"       
attr(,"class")
[1] "qwraps2_summary_table" "qwraps2_qable"        
attr(,"qable_args")
attr(,"qable_args")$rtitle
[1] ""

attr(,"qable_args")$rgroup
[1] 1 1

attr(,"qable_args")$rnames
[1] "Total_Steps_Avg" "Calories_Avg"   

attr(,"qable_args")$cnames
[1] ""                          "eveninghr (N = 3,784,154)"

attr(,"qable_args")$markup
[1] "latex"

attr(,"qable_args")$kable_args
list()

#create summary for ngiht list
 night_list <- 
+ list(
+ list("Total_Steps_Avg" = ~ mean(nighthr$step_total)),
+ list("Calories_Avg" = ~ mean(nighthr$Calories))
+ )

#create summary for night list and view summary 
nighthr_sum <- summary_table(nighthr, night_list)
print.default(nighthr_sum)
                          nighthr (N = 3,246,682)
[1,] "\\bf{}"             "~"                    
[2,] "~~ Total_Steps_Avg" "21.2780518695702"     
[3,] "\\bf{}"             "~"                    
[4,] "~~ Calories_Avg"    "71.6811997602475"     
attr(,"class")
[1] "qwraps2_summary_table" "qwraps2_qable"        
attr(,"qable_args")
attr(,"qable_args")$rtitle
[1] ""

attr(,"qable_args")$rgroup
[1] 1 1

attr(,"qable_args")$rnames
[1] "Total_Steps_Avg" "Calories_Avg"   

attr(,"qable_args")$cnames
[1] ""                        "nighthr (N = 3,246,682)"

attr(,"qable_args")$markup
[1] "latex"

attr(,"qable_args")$kable_args
list()

# comparative list of all of out day by day summaries (only mean of steps and calories)
timeofday_summary1 <- data.frame(
+ TimeOfDay = c("Afternoon", "Morning", "Evening", "Night"),
+ Total_Steps_Avg = c(519.599624506321, 374.758472938824, 370.922424933024, 21.2780518695702),
+ Calories_Avg = c(115.86621, 101.66459, 102.14637, 71.73854))
+)
</code></pre>

</details>

Im going to go ahead and make a bar graph of my findings on top of the chart we just made on RStudio (timeofday_summary1). This will visulaly make clear average calories and steps by day of week and the order they will fall in. 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# visual bar graph for average calories by time time of day
ggplot(timeofday_summary1, aes(x = reorder(TimeOfDay, -Calories_Avg), y = Calories_Avg)) +
+ geom_bar(stat = "identity", fill = "#FF69B4") +
+ labs(title = "Average Calories by Time of Day", x = "", y = "Average Calories")

# visual bar graph for average steps by time of day
ggplot(timeofday_summary1, aes(x = reorder(TimeOfDay, -Total_Steps_Avg), y = Total_Steps_Avg)) +
+ geom_bar(stat = "identity", fill = "pink") +
+ labs(title = "Average Steps by Time of Day", x = "", y = "Average Total Steps") 
</code></pre>

</details>


<div style="display: flex; justify-content: center; gap: 40px; flex-wrap: wrap; text-align: center;">

  <!-- Average Steps -->
  <div>
    <h3 style="color:#333; font-weight:bold;">Average Steps by Time of Day</h3>
    <img src="../projects/Average%20Steps%20by%20Time%20of%20Day.png" alt="Average Steps by Time of Day" width="400">
  </div>

  <!-- Average Calories -->
  <div>
    <h3 style="color:#333; font-weight:bold;">Average Calories by Time of Day</h3>
    <img src="../projects/Average%20Calories%20by%20Time%20of%20Day.png" alt="Average Calories by Time of Day" width="400">
  </div>

</div>




 I was a little surprised to find that most users were significantly more active during the afternoon and not the morning and evening. This could be notworthy as to who bellabeats targer customers could be (people who do not usually work a 9-5?) Moreover, that would of course require more data thtan we currently have. Just somthing to keep in mind for future research/refernce. The evening and morning being relatively the same was unsurprising. The sama ecan be said for nightime being the the time users were the least active. 
 
### Daily/Sleep Data <a id="daily-sleep-data-r"></a>
- <span style="color:gray;">'dailyMerged.csv'</span>

The dataset abover was uploaded into BigQuery. Again i quickly checked if the data was uploaded accurately using the code below
<br>

Import data into Rstudio:

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# import daily_merged dataset
daily_df <- read_csv("daily_merged.csv")
</code></pre>

</details>

Successful Upload check: 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# Preview the data
head(daily_df)

# A tibble: 6 × 14
#        Id     ActivityDate TotalSteps TotalDistance TrackerDistance LoggedActivitiesDistance LongerDistance ShorterDistance
#     &lt;dbl&gt;     &lt;chr&gt;            &lt;dbl&gt;         &lt;dbl&gt;           &lt;dbl&gt;                    &lt;dbl&gt;          &lt;dbl&gt;           &lt;dbl&gt;
# 1 1644430081  4/30/2016        18213         13.2            13.2                         0           3.77            9.46
# 2 2347167796  4/14/2016        10129          6.70            6.70                        0           2.76            3.94
# 3 3977333714  4/16/2016        13459          9.00            9.00                        0           6.03            2.97
# 4 3977333714  4/17/2016        10415          6.97            6.97                        0           3.05            3.92
# 5 3977333714  4/19/2016        12414          8.78            8.78                        0           4.69            3.96
# 6 3977333714  4/20/2016        11658          7.83            7.83                        0           4.55            3.28
# ℹ 6 more variables: HeavyActiveMinutes &lt;dbl&gt;, LightActiveMinutes &lt;dbl&gt;, Calories &lt;dbl&gt;, TotalSleepRecords &lt;dbl&gt;,
#   TotalMinutesAsleep &lt;dbl&gt;, TotalTimeInBed &lt;dbl&gt;

# Check the structure of the data
str(daily_df)

# spc_tbl_ [410 × 14] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
#  $ Id                      : num [1:410] 1.64e+09 2.35e+09 ...
#  $ ActivityDate            : chr [1:410] "4/30/2016" "4/14/2016" ...
#  $ TotalSteps              : num [1:410] 18213 10129 ...
#  $ TotalDistance           : num [1:410] 13.24 6.7 ...
#  $ TrackerDistance         : num [1:410] 13.24 6.7 ...
#  $ LoggedActivitiesDistance: num [1:410] 0 0 ...
#  $ LongerDistance          : num [1:410] 3.77 2.76 ...
#  $ ShorterDistance         : num [1:410] 9.46 3.94 ...
#  $ HeavyActiveMinutes      : num [1:410] 80 49 ...
#  $ LightActiveMinutes      : num [1:410] 1218 911 ...
#  $ Calories                : num [1:410] 3846 2010 ...
#  $ TotalSleepRecords       : num [1:410] 1 1 ...
#  $ TotalMinutesAsleep      : num [1:410] 124 445 ...
#  $ TotalTimeInBed          : num [1:410] 142 489 ...
# - attr(*, "spec")=
#   .. cols(
#   ..   Id = col_double(),
#   ..   ActivityDate = col_character(),
#   ..   TotalSteps = col_double(),
#   ..   TotalDistance = col_double(),
#   ..   TrackerDistance = col_double(),
#   ..   LoggedActivitiesDistance = col_double(),
#   ..   LongerDistance = col_double(),
#   ..   ShorterDistance = col_double(),
#   ..   HeavyActiveMinutes = col_double(),
#   ..   LightActiveMinutes = col_double(),
#   ..   Calories = col_double(),
#   ..   TotalSleepRecords = col_double(),
#   ..   TotalMinutesAsleep = col_double(),
#   ..   TotalTimeInBed = col_double()
#   .. )
# - attr(*, "problems")=&lt;externalptr&gt;

# Check the dimensions
dim(daily_df)
# [1] 410  14
</code></pre>

</details>


<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# Pearson correlation test: total minutes asleep vs heavy active minutes
cor.test(daily_df$TotalMinutesAsleep, daily_df$HeavyActiveMinutes, method = "pearson" )

	Pearson's product-moment correlation

data:  daily_df$TotalMinutesAsleep and daily_df$HeavyActiveMinutes
t = -3.7286, df = 408, p-value = 0.0002197
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.27356474 -0.08619484
sample estimates:
       cor 
-0.1815268 

#Pearson correlation test: total minutes asleep light/non active minutes
cor.test(daily_df$TotalMinutesAsleep, daily_df$LightActiveMinutes, method = "pearson")

	Pearson's product-moment correlation

data:  daily_df$TotalMinutesAsleep and daily_df$LightActiveMinutes
t = -14.644, df = 408, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.6470247 -0.5196501
sample estimates:
       cor 
-0.5869577

# Plot sleep vs light activity
library(ggplot2)

ggplot(data = daily_df, aes(x = TotalMinutesAsleep, y = LightActiveMinutes)) +
  geom_jitter(width = 0.3, height = 0.3, alpha = 0.6, color = "blue") +
  geom_smooth(method = "lm", se = FALSE, color = "darkred") +
  labs(
    x = "Total minutes asleep",
    y = "Light/Non-active minutes",
    title = "Sleep vs. Light/Non Activity Patterns"
  )
</code></pre>

</details>


<div style="text-align: center; margin: 2em auto; max-width: 720px;">
  <h3 style="color:#333; font-weight:bold; margin-bottom: 1em;">Sleep vs Light/Non Activity Patterns</h3>
  <img 
    src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/Sleep%20vs%20LightNon%20Activity%20Patterns.png" 
    alt="Sleep vs Light/Non Activity Patterns" 
    style="
      width: 100%;          /* fills container width */
      height: auto;         /* keeps aspect ratio */
      max-height: 400px;    /* caps height so it won’t stretch tall */
      border-radius: 10px; 
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
      object-fit: contain;  /* keeps image fully visible, no cropping */
      "
  >
</div>








People who sleep more tend to have fewer non-active minutes during the day (a stronger relationship)
They also tend to have slightly fewer active minutes, but this relationship is weak....
The negative correlations suggest more sleep might be associated with more overall movement or less sedentary time, especially the stronger relationship with non-active minutes.
The graph above suggests that people who sleep more may be more active during the day. The low p value (2.2e-16) confirms statistical significance. I wanted to look further into the day by day breakdown of the data between sleep adn non-activity. In the code block below I filter the data for each day of the week and generate summary statistics for the filtered datasets.
Again i want to break the data into time frames and days of the week to grasp when users are getting the most out of device usage or the least usage. Simple summaries of the data could help up pinpoint genreal calculations of the columns. 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# convert the Activity_Date into date format
daily_df$ActivityDate <- as.Date(daily_df$ActivityDate, format = "%m/%d/%Y")
	
# create a weekday column 
daily_df$weekday <- weekdays(daily_df$ActivityDate)
	
# seperate mon data from daily
monday_data <- daily_df %>%
+     filter(weekday == "Monday") %>%
+     select(-c(Id, ActivityDate))
	
# summary of the new seperated mon data
summary(monday_data)
   TotalSteps    TotalDistance    TrackerDistance  LoggedActivitiesDistance LongerDistance 
 Min.   : 1831   Min.   : 1.170   Min.   : 1.170   Min.   :0.0000           Min.   :0.000  
 1st Qu.: 6937   1st Qu.: 4.788   1st Qu.: 4.788   1st Qu.:0.0000           1st Qu.:0.410  
 Median : 9831   Median : 6.815   Median : 6.815   Median :0.0000           Median :1.975  
 Mean   : 9273   Mean   : 6.541   Mean   : 6.536   Mean   :0.3113           Mean   :2.519  
 3rd Qu.:11559   3rd Qu.: 8.265   3rd Qu.: 8.265   3rd Qu.:0.0000           3rd Qu.:3.980  
 Max.   :16520   Max.   :11.050   Max.   :11.050   Max.   :3.1678           Max.   :8.020  
 ShorterDistance HeavyActiveMinutes LightActiveMinutes    Calories    TotalSleepRecords
 Min.   :1.120   Min.   :  0.00     Min.   : 322.0     Min.   :1248   Min.   :1.000    
 1st Qu.:3.045   1st Qu.: 10.25     1st Qu.: 882.5     1st Qu.:1998   1st Qu.:1.000    
 Median :3.930   Median : 44.50     Median : 931.5     Median :2232   Median :1.000    
 Mean   :4.016   Mean   : 49.80     Mean   : 940.8     Mean   :2432   Mean   :1.109    
 3rd Qu.:4.855   3rd Qu.: 77.50     3rd Qu.:1000.0     3rd Qu.:3007   3rd Qu.:1.000    
 Max.   :6.790   Max.   :167.00     Max.   :1278.0     Max.   :4157   Max.   :2.000    
 TotalMinutesAsleep TotalTimeInBed    weekday         
 Min.   : 62.0      Min.   : 65.0   Length:46         
 1st Qu.:368.5      1st Qu.:399.8   Class :character  
 Median :434.0      Median :467.5   Mode  :character  
 Mean   :419.5      Mean   :457.3                     
 3rd Qu.:492.8      3rd Qu.:528.8                     
 Max.   :796.0      Max.   :961.0 

# Calculate average steps, activity, sleep, and calories for Mondays only.
mon_data_summary <- monday_data %>%
+     summarise(
+         Total_Steps_Avg = mean(TotalSteps, na.rm = TRUE),
+         Active_Minutes_Avg = mean(HeavyActiveMinutes, na.rm = TRUE),
+         Sedentary_Minutes_Avg = mean(LightActiveMinutes, na.rm = TRUE),
+         Calories_Avg = mean(Calories, na.rm = TRUE),
+         Total_Hours_Asleep_Avg = mean(TotalMinutesAsleep / 60, na.rm = TRUE))

# view mon data sum
print.default(mon_data_summary)
$Total_Steps_Avg
[1] 9273.217

$Active_Minutes_Avg
[1] 49.80435

$Sedentary_Minutes_Avg
[1] 940.7826

$Calories_Avg
[1] 2431.978

$Total_Hours_Asleep_Avg
[1] 6.991667

attr(,"class")
[1] "tbl_df"     "tbl"        "data.frame"

# seperate tues data from daily 
> tuesday_data <- daily_df %>%
+     filter(weekday == "Tuesday") %>%
+     select(-c(Id, ActivityDate))
	
# summary of the new seperated tues data
summary(tuesday_data)
   TotalSteps    TotalDistance   TrackerDistance LoggedActivitiesDistance LongerDistance  ShorterDistance
 Min.   :  254   Min.   : 0.16   Min.   : 0.16   Min.   :0.0000           Min.   :0.000   Min.   :0.160  
 1st Qu.: 6582   1st Qu.: 4.95   1st Qu.: 4.95   1st Qu.:0.0000           1st Qu.:0.000   1st Qu.:2.580  
 Median : 9648   Median : 6.76   Median : 6.76   Median :0.0000           Median :2.400   Median :3.950  
 Mean   : 9183   Mean   : 6.43   Mean   : 6.43   Mean   :0.1387           Mean   :2.535   Mean   :3.888  
 3rd Qu.:11886   3rd Qu.: 8.39   3rd Qu.: 8.39   3rd Qu.:0.0000           3rd Qu.:4.510   3rd Qu.:5.030  
 Max.   :16358   Max.   :12.85   Max.   :12.85   Max.   :2.2531           Max.   :8.430   Max.   :8.410  
 HeavyActiveMinutes LightActiveMinutes    Calories    TotalSleepRecords TotalMinutesAsleep TotalTimeInBed 
 Min.   :  0.00     Min.   : 754.0     Min.   :1141   Min.   :1.000     Min.   :103.0      Min.   :121.0  
 1st Qu.:  7.00     1st Qu.: 897.0     1st Qu.:2026   1st Qu.:1.000     1st Qu.:342.0      1st Qu.:391.0  
 Median : 43.00     Median : 956.0     Median :2291   Median :1.000     Median :417.0      Median :446.0  
 Mean   : 50.66     Mean   : 956.6     Mean   :2496   Mean   :1.108     Mean   :404.5      Mean   :443.3  
 3rd Qu.: 86.00     3rd Qu.:1014.0     3rd Qu.:2944   3rd Qu.:1.000     3rd Qu.:465.0      3rd Qu.:498.0  
 Max.   :141.00     Max.   :1345.0     Max.   :4092   Max.   :3.000     Max.   :750.0      Max.   :775.0  
   weekday         
 Length:65         
 Class :character  
 Mode  :character  
	
# Calculate average steps, activity, sleep, and calories for Tuesdays only
tues_data_summary <- tuesday_data %>%
+     summarise(
+         Total_Steps_Avg = mean(TotalSteps, na.rm = TRUE),
+         Active_Minutes_Avg = mean(HeavyActiveMinutes, na.rm = TRUE),
+         Sedentary_Minutes_Avg = mean(LightActiveMinutes, na.rm = TRUE),
+         Calories_Avg = mean(Calories, na.rm = TRUE),
+         Total_Hours_Asleep_Avg = mean(TotalMinutesAsleep / 60, na.rm = TRUE))

# view tues data sum
print.default(tues_data_summary)
$Total_Steps_Avg
[1] 9182.692

$Active_Minutes_Avg
[1] 50.66154

$Sedentary_Minutes_Avg
[1] 956.6308

$Calories_Avg
[1] 2496.2

$Total_Hours_Asleep_Avg
[1] 6.742308

attr(,"class")
[1] "tbl_df"     "tbl"        "data.frame"

#seperate wed data from daily
wednesday_data <- daily_df %>%
+ filter(weekday == "Wednesday") %>%
+ select(-c(Id, ActivityDate))
	
#summary of the new seperated wed data
summary(wednesday_data)
   TotalSteps    TotalDistance    TrackerDistance  LoggedActivitiesDistance LongerDistance  ShorterDistance
 Min.   :  356   Min.   : 0.250   Min.   : 0.250   Min.   :0.0000           Min.   :0.000   Min.   :0.250  
 1st Qu.: 5318   1st Qu.: 3.748   1st Qu.: 3.748   1st Qu.:0.0000           1st Qu.:0.000   1st Qu.:2.418  
 Median : 8686   Median : 6.175   Median : 6.175   Median :0.0000           Median :1.805   Median :3.590  
 Mean   : 8023   Mean   : 5.720   Mean   : 5.720   Mean   :0.0951           Mean   :2.062   Mean   :3.652  
 3rd Qu.:10516   3rd Qu.: 7.418   3rd Qu.: 7.418   3rd Qu.:0.0000           3rd Qu.:2.910   3rd Qu.:5.063  
 Max.   :15108   Max.   :12.190   Max.   :12.190   Max.   :2.0921           Max.   :9.810   Max.   :7.110  
 HeavyActiveMinutes LightActiveMinutes    Calories    TotalSleepRecords TotalMinutesAsleep TotalTimeInBed
 Min.   :  0.00     Min.   : 320.0     Min.   :1377   Min.   :1.000     Min.   :152.0      Min.   :260   
 1st Qu.:  0.00     1st Qu.: 878.5     1st Qu.:1789   1st Qu.:1.000     1st Qu.:392.0      1st Qu.:425   
 Median : 33.50     Median : 924.5     Median :2207   Median :1.000     Median :444.5      Median :469   
 Mean   : 38.08     Mean   : 922.4     Mean   :2378   Mean   :1.152     Mean   :434.7      Mean   :470   
 3rd Qu.: 58.50     3rd Qu.: 977.8     3rd Qu.:2942   3rd Qu.:1.000     3rd Qu.:477.0      3rd Qu.:525   
 Max.   :130.00     Max.   :1138.0     Max.   :4079   Max.   :3.000     Max.   :658.0      Max.   :679   
   weekday         
 Length:66         
 Class :character  
 Mode  :character  

#Calculate average steps, activity, sleep and calories for wednesday only
wed_data_summary <- wednesday_data %>%
+     summarise(
+         Total_Steps_Avg = mean(TotalSteps, na.rm = TRUE),
+         Active_Minutes_Avg = mean(HeavyActiveMinutes, na.rm = TRUE),
+         Sedentary_Minutes_Avg = mean(LightActiveMinutes, na.rm = TRUE),
+         Calories_Avg = mean(Calories, na.rm = TRUE),
+         Total_Hours_Asleep_Avg = mean(TotalMinutesAsleep / 60, na.rm = TRUE))

# view wednesday data sum 
print.default(wed_data_summary)
$Total_Steps_Avg
[1] 8022.864

$Active_Minutes_Avg
[1] 38.07576

$Sedentary_Minutes_Avg
[1] 922.4242

$Calories_Avg
[1] 2378.242

$Total_Hours_Asleep_Avg
[1] 7.244697

attr(,"class")
[1] "tbl_df"     "tbl"        "data.frame"

# seperate thurs data from daily
thursday_data <- daily_df %>%
+     filter(weekday == "Thursday") %>%
+     select(-c(Id, ActivityDate))

# summary of the new seperated thurs data 
summary(thursday_data)
   TotalSteps    TotalDistance    TrackerDistance  LoggedActivitiesDistance LongerDistance  ShorterDistance
 Min.   :   17   Min.   : 0.010   Min.   : 0.010   Min.   :0.0000           Min.   :0.000   Min.   :0.010  
 1st Qu.: 4363   1st Qu.: 2.925   1st Qu.: 2.925   1st Qu.:0.0000           1st Qu.:0.000   1st Qu.:2.652  
 Median : 8752   Median : 6.355   Median : 6.355   Median :0.0000           Median :1.360   Median :3.610  
 Mean   : 8184   Mean   : 5.773   Mean   : 5.745   Mean   :0.1694           Mean   :1.912   Mean   :3.699  
 3rd Qu.:10971   3rd Qu.: 7.735   3rd Qu.: 7.735   3rd Qu.:0.0000           3rd Qu.:3.072   3rd Qu.:4.827  
 Max.   :19542   Max.   :15.010   Max.   :15.010   Max.   :4.0817           Max.   :7.720   Max.   :7.700  
 HeavyActiveMinutes LightActiveMinutes    Calories    TotalSleepRecords TotalMinutesAsleep TotalTimeInBed 
 Min.   :  0.00     Min.   :   2.0     Min.   : 257   Min.   :1.000     Min.   : 59.0      Min.   : 65.0  
 1st Qu.:  0.00     1st Qu.: 873.0     1st Qu.:1788   1st Qu.:1.000     1st Qu.:377.2      1st Qu.:416.0  
 Median : 23.00     Median : 951.5     Median :2168   Median :1.000     Median :423.5      Median :457.0  
 Mean   : 38.72     Mean   : 901.3     Mean   :2307   Mean   :1.031     Mean   :401.3      Mean   :434.9  
 3rd Qu.: 66.25     3rd Qu.: 993.2     3rd Qu.:2868   3rd Qu.:1.000     3rd Qu.:467.2      3rd Qu.:492.8  
 Max.   :184.00     Max.   :1299.0     Max.   :4900   Max.   :2.000     Max.   :545.0      Max.   :568.0  
   weekday         
 Length:64         
 Class :character  
 Mode  :character 

# calculate average steps, activity, sleep, and calories for thursdays only
thurs_data_summary <- thursday_data %>%
+     summarise(
+         Total_Steps_Avg = mean(TotalSteps, na.rm = TRUE),
+         Active_Minutes_Avg = mean(HeavyActiveMinutes, na.rm = TRUE),
+         Sedentary_Minutes_Avg = mean(LightActiveMinutes, na.rm = TRUE),
+         Calories_Avg = mean(Calories, na.rm = TRUE),
+         Total_Hours_Asleep_Avg = mean(TotalMinutesAsleep / 60, na.rm = TRUE))

# view thurs data sum 
print.default(thurs_data_summary)
$Total_Steps_Avg
[1] 8183.516

$Active_Minutes_Avg
[1] 38.71875

$Sedentary_Minutes_Avg
[1] 901.3125

$Calories_Avg
[1] 2306.672

$Total_Hours_Asleep_Avg
[1] 6.688281

attr(,"class")
[1] "tbl_df"     "tbl"        "data.frame"

# seperate fri data from daily
friday_data <- daily_df %>%
+     filter(weekday == "Friday") %>%
+     select(-c(Id, ActivityDate))

# summary of the new seperated fri data 
summary(friday_data)
   TotalSteps    TotalDistance    TrackerDistance  LoggedActivitiesDistance LongerDistance  ShorterDistance
 Min.   :   42   Min.   : 0.030   Min.   : 0.030   Min.   :0.00000          Min.   :0.000   Min.   :0.03   
 1st Qu.: 5563   1st Qu.: 3.680   1st Qu.: 3.680   1st Qu.:0.00000          1st Qu.:0.000   1st Qu.:2.67   
 Median : 8198   Median : 5.630   Median : 5.630   Median :0.00000          Median :0.880   Median :3.77   
 Mean   : 7901   Mean   : 5.512   Mean   : 5.512   Mean   :0.07341          Mean   :1.722   Mean   :3.78   
 3rd Qu.:10465   3rd Qu.: 7.110   3rd Qu.: 7.110   3rd Qu.:0.00000          3rd Qu.:3.150   3rd Qu.:4.91   
 Max.   :16556   Max.   :11.470   Max.   :11.470   Max.   :2.09215          Max.   :6.140   Max.   :7.24   
 HeavyActiveMinutes LightActiveMinutes    Calories    TotalSleepRecords TotalMinutesAsleep TotalTimeInBed 
 Min.   :  0.00     Min.   :   6.0     Min.   : 403   Min.   :1.00      Min.   : 82.0      Min.   : 85.0  
 1st Qu.:  0.00     1st Qu.: 899.0     1st Qu.:1850   1st Qu.:1.00      1st Qu.:355.0      1st Qu.:386.0  
 Median : 21.00     Median : 987.0     Median :2196   Median :1.00      Median :405.0      Median :448.0  
 Mean   : 35.74     Mean   : 965.8     Mean   :2330   Mean   :1.07      Mean   :405.4      Mean   :445.1  
 3rd Qu.: 61.00     3rd Qu.:1032.0     3rd Qu.:2846   3rd Qu.:1.00      3rd Qu.:465.0      3rd Qu.:510.0  
 Max.   :169.00     Max.   :1332.0     Max.   :4044   Max.   :2.00      Max.   :658.0      Max.   :961.0  
   weekday         
 Length:57         
 Class :character  
 Mode  :character   

# calculate average steps, activity, sleep, and calories for fridays only
fri_data_summary <- friday_data %>%
+     summarise(
+         Total_Steps_Avg = mean(TotalSteps, na.rm = TRUE),
+         Active_Minutes_Avg = mean(HeavyActiveMinutes, na.rm = TRUE),
+         Sedentary_Minutes_Avg = mean(LightActiveMinutes, na.rm = TRUE),
+         Calories_Avg = mean(Calories, na.rm = TRUE),
+         Total_Hours_Asleep_Avg = mean(TotalMinutesAsleep / 60, na.rm = TRUE))

# view fri data sum 
print.default(fri_data_summary)
$Total_Steps_Avg
[1] 7901.404

$Active_Minutes_Avg
[1] 35.73684

$Sedentary_Minutes_Avg
[1] 965.7719

$Calories_Avg
[1] 2329.649

$Total_Hours_Asleep_Avg
[1] 6.757018

attr(,"class")
[1] "tbl_df"     "tbl"        "data.frame"

# seperate sat data from daily
saturday_data <- daily_df %>%
+     filter(weekday == "Saturday") %>%
+     select(-c(Id, ActivityDate))

# summary of the new seperated sat data 
 summary(saturday_data)
   TotalSteps    TotalDistance    TrackerDistance  LoggedActivitiesDistance LongerDistance   ShorterDistance
 Min.   : 1202   Min.   : 0.780   Min.   : 0.780   Min.   :0                Min.   : 0.000   Min.   :0.590  
 1st Qu.: 5079   1st Qu.: 3.420   1st Qu.: 3.420   1st Qu.:0                1st Qu.: 0.000   1st Qu.:2.730  
 Median :10144   Median : 7.710   Median : 7.710   Median :0                Median : 2.010   Median :3.770  
 Mean   : 9871   Mean   : 7.016   Mean   : 7.016   Mean   :0                Mean   : 2.747   Mean   :4.266  
 3rd Qu.:13238   3rd Qu.: 9.240   3rd Qu.: 9.240   3rd Qu.:0                3rd Qu.: 4.160   3rd Qu.:5.330  
 Max.   :22770   Max.   :17.540   Max.   :17.540   Max.   :0                Max.   :13.320   Max.   :9.480  
 HeavyActiveMinutes LightActiveMinutes    Calories    TotalSleepRecords TotalMinutesAsleep TotalTimeInBed 
 Min.   :  0.00     Min.   : 402.0     Min.   :1373   Min.   :1.000     Min.   : 61.0      Min.   : 69.0  
 1st Qu.:  0.00     1st Qu.: 850.0     1st Qu.:1863   1st Qu.:1.000     1st Qu.:340.0      1st Qu.:382.0  
 Median : 44.00     Median : 911.0     Median :2363   Median :1.000     Median :426.0      Median :470.0  
 Mean   : 50.28     Mean   : 927.2     Mean   :2507   Mean   :1.193     Mean   :419.1      Mean   :459.8  
 3rd Qu.: 80.00     3rd Qu.: 998.0     3rd Qu.:3073   3rd Qu.:1.000     3rd Qu.:507.0      3rd Qu.:539.0  
 Max.   :252.00     Max.   :1371.0     Max.   :4501   Max.   :2.000     Max.   :775.0      Max.   :961.0  
   weekday         
 Length:57         
 Class :character  
 Mode  :character  

# calculate average steps, activity, sleep, and calories for saturdays only
sat_data_summary <- saturday_data %>%
+     summarise(
+         Total_Steps_Avg = mean(TotalSteps, na.rm = TRUE),
+         Active_Minutes_Avg = mean(HeavyActiveMinutes, na.rm = TRUE),
+         Sedentary_Minutes_Avg = mean(LightActiveMinutes, na.rm = TRUE),
+         Calories_Avg = mean(Calories, na.rm = TRUE),
+         Total_Hours_Asleep_Avg = mean(TotalMinutesAsleep / 60, na.rm = TRUE))

# view sat data sum 
print.default(sat_data_summary)
$Total_Steps_Avg
[1] 9871.123

$Active_Minutes_Avg
[1] 50.2807

$Sedentary_Minutes_Avg
[1] 927.2105

$Calories_Avg
[1] 2506.895

$Total_Hours_Asleep_Avg
[1] 6.984503

attr(,"class")
[1] "tbl_df"     "tbl"        "data.frame"







# seperate sun data from daily
sunday_data <- daily_df %>%
+     filter(weekday == "Sunday") %>%
+     select(-c(Id, ActivityDate))

# summary of the new seperated sun data 
summary(sunday_data)
   TotalSteps    TotalDistance    TrackerDistance  LoggedActivitiesDistance LongerDistance   ShorterDistance
 Min.   :  655   Min.   : 0.430   Min.   : 0.430   Min.   :0                Min.   : 0.000   Min.   :0.430  
 1st Qu.: 3688   1st Qu.: 2.600   1st Qu.: 2.600   1st Qu.:0                1st Qu.: 0.000   1st Qu.:2.260  
 Median : 6543   Median : 4.330   Median : 4.330   Median :0                Median : 0.000   Median :3.230  
 Mean   : 7298   Mean   : 5.185   Mean   : 5.185   Mean   :0                Mean   : 1.893   Mean   :3.289  
 3rd Qu.:10334   3rd Qu.: 7.020   3rd Qu.: 7.020   3rd Qu.:0                3rd Qu.: 3.520   3rd Qu.:4.035  
 Max.   :17298   Max.   :14.380   Max.   :14.380   Max.   :0                Max.   :11.150   Max.   :6.730  
 HeavyActiveMinutes LightActiveMinutes    Calories    TotalSleepRecords TotalMinutesAsleep TotalTimeInBed 
 Min.   :  0.00     Min.   : 566.0     Min.   :1214   Min.   :1.000     Min.   : 58.0      Min.   : 61.0  
 1st Qu.:  0.00     1st Qu.: 758.5     1st Qu.:1698   1st Qu.:1.000     1st Qu.:380.0      1st Qu.:436.0  
 Median :  0.00     Median : 868.0     Median :2027   Median :1.000     Median :481.0      Median :527.0  
 Mean   : 38.91     Mean   : 887.7     Mean   :2277   Mean   :1.182     Mean   :452.7      Mean   :503.5  
 3rd Qu.: 58.50     3rd Qu.: 945.5     3rd Qu.:2676   3rd Qu.:1.000     3rd Qu.:550.5      3rd Qu.:602.5  
 Max.   :275.00     Max.   :1379.0     Max.   :4552   Max.   :3.000     Max.   :700.0      Max.   :961.0  
   weekday         
 Length:55         
 Class :character  
 Mode  :character   

# calculate average steps, activity, sleep, and calories for sundays only
sun_data_summary <- sunday_data %>%
+     summarise(
+         Total_Steps_Avg = mean(TotalSteps, na.rm = TRUE),
+         Active_Minutes_Avg = mean(HeavyActiveMinutes, na.rm = TRUE),
+         Sedentary_Minutes_Avg = mean(LightActiveMinutes, na.rm = TRUE),
+         Calories_Avg = mean(Calories, na.rm = TRUE),
+         Total_Hours_Asleep_Avg = mean(TotalMinutesAsleep / 60, na.rm = TRUE))

# view sun data sum 
print.default(sun_data_summary)
$Total_Steps_Avg
[1] 7297.855

$Active_Minutes_Avg
[1] 38.90909

$Sedentary_Minutes_Avg
[1] 887.6727

$Calories_Avg
[1] 2276.6

$Total_Hours_Asleep_Avg
[1] 7.545758

attr(,"class")
[1] "tbl_df"     "tbl"        "data.frame"

</code></pre>

</details>

I used the following coded blocks to generate respetive graphs representing my results of the stat summaries. 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# merge daily sums into single data frame
weekday_sum <- rbind(mon_data_summary, tues_data_summary, wed_data_summary, thurs_data_summary, fri_data_summary, sat_data_summary, sun_data_summary)


# assign weekday names to the rows
rownames(weekday_sum) <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday")


</code></pre>

</details>

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
#sorting weekly averages by metric 
sort(weekday_sum[[1]], decreasing = TRUE)
[1] 9871.123 9273.217 9182.692 8183.516 8022.864 7901.404 7297.855
sort(weekday_sum[[2]], decreasing = TRUE)
[1] 50.66154 50.28070 49.80435 38.90909 38.71875 38.07576 35.73684
sort(weekday_sum[[3]], decreasing = TRUE)
[1] 965.7719 956.6308 940.7826 927.2105 922.4242 901.3125 887.6727
sort(weekday_sum[[4]], decreasing = TRUE)
[1] 2506.895 2496.200 2431.978 2378.242 2329.649 2306.672 2276.600
sort(weekday_sum[[5]], decreasing = TRUE)
[1] 7.545758 7.244697 6.991667 6.984503 6.757018 6.742308 6.688281
</code></pre>

</details>

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# average calories by weekday
> ggplot(data = weekday_sum, 
+        aes(x = reorder(as.character(row.names(weekday_sum)), -Calories_Avg), 
+            y = Calories_Avg)) +
+     geom_bar(stat = "identity", fill = "purple") +
+     labs(title = "Average Calories by Weekday", 
+          x = "Weekday", 
+          y = "Avg Calories") +
+     theme(axis.text.x = element_text(angle = 45, hjust = 1))
# average active minutes by weekday
ggplot(data = weekday_sum, 
+           aes(x = reorder(as.character(row.names(weekday_sum)), -Active_Minutes_Avg), 
+               y = Active_Minutes_Avg)) +
+       geom_bar(stat = "identity", fill = "red") +
+       labs(title = "Average Active Minutes by Weekday", 
+             x = "Weekday", 
+             y = "Avg Active Minutes") +
+     theme(axis.text.x = element_text(angle = 45, hjust = 1))

#average sedentary minutes by weekday
ggplot(data = weekday_sum, 
+            aes(x = reorder(as.character(row.names(weekday_sum)), -Sedentary_Minutes_Avg), 
+             y = Sedentary_Minutes_Avg)) +
+      geom_bar(stat = "identity", fill = "green") +
+          labs(title = "Average Sedentary Minutes by Weekday", 
+             x = "Weekday", 
+             y = "Avg Sedentary Minutes") +
+     theme(axis.text.x = element_text(angle = 45, hjust = 1))

# average hours asleep by weekday
ggplot(data = weekday_sum, 
+              aes(x = reorder(as.character(row.names(weekday_sum)), -Total_Hours_Asleep_Avg), 
+               y = Total_Hours_Asleep_Avg)) +
+         geom_bar(stat = "identity", fill = "blue") +
+         labs(title = "Average Hours of Sleep by Weekday", 
+             x = "Weekday", 
+             y = "Avg Hours of Sleep") +
+       theme(axis.text.x = element_text(angle = 45, hjust = 1))
	
# average steps by weekday
 ggplot(data = weekday_sum, 
+              aes(x = reorder(as.character(row.names(weekday_sum)), -Total_Steps_Avg), 
+                   y = Total_Steps_Avg)) +
+          geom_bar(stat = "identity", fill = "orange") +
+          labs(title = "Average Steps by Weekday", 
+               x = "Weekday", 
+               y = "Avg Steps") +
+    theme(axis.text.x = element_text(angle = 45, hjust = 1))	
</code></pre>

</details>

	
<!-- Grid layout for graphs -->
<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 30px; justify-items: center; max-width: 1000px; margin: 0 auto;">

  <!-- Row 1 -->
  <div style="text-align: center; width: 300px;">
    <h4>Average Calories by Weekday</h4>
    <img 
      src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20calories%20final.png" 
      alt="Average Calories" 
      style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: white; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>

  <div style="text-align: center; width: 300px;">
    <h4>Average Active Minutes by Weekday</h4>
    <img 
      src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20active%20minutes.png" 
      alt="Average Active Minutes" 
      style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: white; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>

  <div style="text-align: center; width: 300px;">
    <h4>Average Sedentary Minutes by Weekday</h4>
    <img 
      src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/Avg%20sedentary%20minutes.png" 
      alt="Average Sedentary Minutes" 
      style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: white; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>

  <!-- Row 2 (empty cell to center 2 images) -->
  <div></div>

  <div style="text-align: center; width: 300px;">
    <h4>Average Hours of Sleep by Weekday</h4>
    <img 
      src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20hours%20of%20sleep%20by%20weekday.png" 
      alt="Average Sleep" 
      style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: white; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>

  <div style="text-align: center; width: 300px;">
    <h4>Average Steps by Weekday</h4>
    <img 
      src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20steps%20by%20weekday.png" 
      alt="Average Steps" 
      style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: white; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>

</div>







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
