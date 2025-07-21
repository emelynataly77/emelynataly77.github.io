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

This is the Google Data Analytics Capstone Project, focused on analyzing smart device fitness data to uncover insights for Bellabeat — a women’s wellness company. The goal was to explore how consumers use fitness devices and provide actionable recommendations to Bellabeat’s marketing strategy.
I myself am very passionate about heath and wellness and reaching ones fitness goals and really enjoyed working on this project. 
To further explore Bellabeat, the case study prompt or the Kaggle dataset used for this case study, please use the links provided below:

- [Bellabeat Official Website](https://bellabeat.com/)
- <a href="https://github.com/emelynataly77/emelynataly77.github.io/raw/main/projects/bellabeat case study.pdf" target="_blank">Case Study PDF</a>
- [FitBit Dataset on Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit)

---
### Stakeholders
- **Urška Sršen**: Bellabeat’s cofounder and Chief Creative Officer
- **Sando Mur**: Bellabeat’s cofounder; key member of the Bellabeat executive team

### Bellabeat Products
- **Bellabeat app:** The app provides users with health data related to their activity, sleep, stress, menstrual cycle, and mindfulness habits. The Bellabeat app connects to their line of smart wellness products.
- **Leaf:** A Wellness tracker that can be worn as a bracelet, necklace, or clip. The Leaf tracker connects to the Bellabeat app to track activity, sleep, and stress.
- **Time:** A Wellness watch that combines the timeless look of a classic timepiece with smart technology to track user activity, sleep, and stress. The Time watch connects to the Bellabeat app to provide you with insights into your daily wellness.
- **Spring:** A water bottle that tracks daily water intake using smart technology to ensure that you are appropriately hydrated throughout the day. The Spring bottle connects to the Bellabeat app to track your hydration levels.
- **Bellabeat membership:** A subscription-based membership program for users. Membership gives users 24/7 access to fully personalized guidance on nutrition, activity, sleep, health and beauty, and mindfulness based on their lifestyle and goals.

### The Data <a id="the-data"></a>

The FitBit Fitness Tracker dataset, provided by Kaggle user Mobius, serves as the basis for this case study. It includes the 18 .csv files that I will use for procsessing, cleaning and analyzing. 

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

After doing some research on the data, I found that it was collected in 2016 and includes data from 33 Bellabeat users who voluntarily agreed to share their information for analysis. Although historical health data can provide helpful insights, using data from 2016 might not be the best way to guide marketing strategies for today’s consumers. It would seem more effective to analyze data that accurately reflects Bellabeat's current customer base. Additionally, all of the data has been anonymized, and it remains unclear how these users were selected. We don't know if these users represent a randomly selected group or if they met some other criteria. The lack of available information, combined with the small sample size, makes it hard to determine how representative and reliable the data actually is. The data is also inconsistent — many datasets include fewer than 33 users, and entire days of data are absent. The data itself is sourced from a third party and made available on Kaggle by the user Mobius. Overall, the data quality could use some improvement. That said, I will continue with the analysis for the sake of this case study — onward!

---

# 🧹 Excel Cleaning <a id="excel-cleaning"></a>

I began with 18 raw .csv files from the FitBit Fitness Tracker dataset. 
I completed basic data cleaning including: 
  
- Removing nulls, blanks, and duplicate values   
- Converting datetime columns for compatibility into SQL/R 
- Using =COUNTA(UNIQUE()) function to compare user ID counts across datasets 

The table below represents a summary of the cleaning completed on Excel: 



<img src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/Screenshot%20(69).png" alt="Excel Table Screenshot" width="92%"> 



<br>

Many of the original datasets were too large to be processed efficiently using Excel, RStudio, or even BigQuery. In addition, several datasets were too inconsistent or incomplete to support any meaningful analysis. Some also contained repetitive or overlapping information. For instance, dailyCalories_merged, dailyIntensities_merged, and dailySteps_merged all overlapped with dailyActivity_merged, which already included the same data and more. As a result, those files were removed, and only dailyActivity_merged was kept for further analysis.

Any datasets that were incomplete, redundant, or too large to process were excluded from further exploration (as shown on the right). The remaining datasets (listed on the left) were uploaded into BigQuery for continued analysis.

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

After completing the initial cleaning in Excel—such as removing nulls and duplicates—the files were renamed to drop the unnecessary 'merged' label (e.g., 'dailyCalories_merged' became 'dailyCalories,' as shown above). While Excel worked well for early-stage cleanup, the data soon became too large and difficult to manage efficiently. So, I moved everything over to BigQuery, where working with the datasets was much more manageable.


NOTE: Moving forward I will be processing the data by grouping similiar datasets by their datatype (e.g., daily/sleep, hourly) to help keep things organized and straightforward. 

---


# 🧮 SQL Queries in BigQuery <a id="sql-queries"></a>

### Hourly Data <a id="hourly-data-sql"></a>

- <span style="color:gray;">'hourlyCalories.csv'</span>
- <span style="color:gray;">'hourlySteps.csv'</span>
- <span style="color:gray;">'hourlyIntensities.csv'</span>
  

After uploading the hourly datasets to BigQuery, I ran a few quick queries to ensure the data had been imported correctly. 
<br>



Upload Check: 

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
After running the three queries on each of the hourly datasets, I was confident everything uploaded correctly. Because the datasets shared some common data (like ID and activity hour) but each also contained different information (such as calories, steps, and intensities), I combined them into one comprehensive hourly dataset.
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

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data now (which we just merged). 


### Daily/Sleep Data <a id="daily-sleep-data-sql"></a>

- <span style="color:gray;">'dailyActivity.csv'</span>
- <span style="color:gray;">'dailyCalories.csv'</span>
- <span style="color:gray;">'dailyIntensities.csv'</span>
- <span style="color:gray;">'dailySteps.csv'</span>
- <span style="color:gray;">'sleepDay.csv'</span>


The daily and sleep datasets above were uploaded into BigQuery. Once again, I ran a few quik checks to ensure everything was imported correctly. 
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
I ran the same set of queries on the dailyActivity dataset as well.  Next, I decided to combine the dailyactivity and sleepday datasets as they had some correspondonding data. Bringing the two datasets together also made things simpler, letting me focus on just two main datasets: hourly and daily/sleep. 
<br>



Merging dailyactivity and sleepday datasets:

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

First I loaded the packages that I will be needing for the hourly and daily data analysis in RStudio. Next, I uploaded my hourlyMerged dataset. 

Load packages and hourly dataset:

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# load packages needed for analysis
install.packages
library(tidyverse)
library(lubridate)
library(qwraps2)
# import hourlyMerged dataset, rename (df=dataframe)
hourly_df <- read_csv("hourlyMerged.csv")
</code></pre>

</details>

Same as before, I ran a quick check using the code below to make sure the data improted properly. 
<br>


Upload check:

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

  
After confirming the file uploaded correctly, I decided to analyze the data by both day of the week and time of day. This allowed me to examine user activity across a Monday–Sunday timeframe and throughout different parts of the day. To do this, I first split the activity_hour column—which contains both date and time values—into two separate columns: activityDate for the date and time for the time. I then converted the activityDate column into a proper date format and used it to create a new column indicating the day of the week. Similarly, I converted the time column and categorized each entry into one of four time-of-day segments—Night, Morning, Afternoon, and Evening—based on the activity hour. You can see the following code below.

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

I went ahead and also performed a correlation test. I just wanted to see any potential relationships amongst the data. This could help identify how different variables of data might be connected. 

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
#Pearson correlation test: average_intensity vs Calories
with(hourly_df, cor.test(average_intensity, Calories, method = "pearson"))

	Pearson's product-moment correlation

data:  average_intensity and Calories
t = 147.75, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.03713366 0.03813135
sample estimates:
       cor 
0.03763252 

#Pearson corelation test: total_intensity vs Calories
with(hourly_df, cor.test(total_intensity, Calories, method = "pearson"))

	Pearson's product-moment correlation

data:  total_intensity and Calories
t = 147.75, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.03713366 0.03813136
sample estimates:
       cor 
0.03763252 

#Pearson correlation test: total_intensity vs step_total
with(hourly_df, cor.test(total_intensity, step_total, method = "pearson"))

	Pearson's product-moment correlation

data:  total_intensity and step_total
t = 170.87, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.04301144 0.04400866
sample estimates:
       cor 
0.04351006 

#Pearson correlation test: average_intensity vs step_total
with(hourly_df, cor.test(average_intensity, step_total, method = "pearson"))

	Pearson's product-moment correlation

data:  average_intensity and step_total
t = 170.87, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.04301144 0.04400866
sample estimates:
       cor 
0.04351006 

#Pearson correlation test: step _total vs Calories
with(hourly_df, cor.test(step_total, Calories, method = "pearson"))

	Pearson's product-moment correlation

data:  step_total and Calories
t = 5498.6, df = 15393211, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 0.8138534 0.8141904
sample estimates:
     cor 
0.814022 
</code></pre>

</details>


Interestingly, there didn’t appear to be any strong or meaningful linear correlation between intensity and steps taken, or between intensity and calories burned. On the other hand, the number of steps has a strong positive linear correlation with calories burned. This makes sense, as generally the more steps you take the more calories you're likely to burn. Since the dataset was already grouped by time of day, I wanted to take a closer look at when participants were most or least active. I first assumed that activity levels would peak in the morning and evening—times because that usually aligns with common workout windows. But that assumption might not represent weekends, when people's schedules tend to vary. To take a closer look, I used the next two code blocks to check out activity levels at different times of day, from Sunday through Saturday.

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

Looking at the summaries, it's clear that step counts are lower at night, ~21 steps on average—which makes sense since most peopole are asleep during that time. To get a better idea of activity levels throughout the day, I decided to focus on calculating the average steps and calories burned by time of day.

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

#create summary for night list
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

# comparative list of all of the day by day summaries (only mean of steps and calories)
timeofday_summary1 <- data.frame(
+ TimeOfDay = c("Afternoon", "Morning", "Evening", "Night"),
+ Total_Steps_Avg = c(519.599624506321, 374.758472938824, 370.922424933024, 21.2780518695702),
+ Calories_Avg = c(115.86621, 101.66459, 102.14637, 71.73854))
+)
</code></pre>

</details>

The following code creates a bar graph that represents the average calories burned and steps taken each day of the week, based on the findings above. It helps visualize how both calories and steps vary across different times of the day. 

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
    <img 
      src="../projects/Average%20Steps%20by%20Time%20of%20Day.png" 
      alt="Average Steps by Time of Day" 
      width="360" 
      style="border-radius: 12px;">
  </div>

  <!-- Average Calories -->
  <div>
    <h3 style="color:#333; font-weight:bold;">Average Calories by Time of Day</h3>
    <img 
      src="../projects/Average%20Calories%20by%20Time%20of%20Day.png" 
      alt="Average Calories by Time of Day" 
      width="360" 
      style="border-radius: 12px;">
  </div>

</div>


I was a bit surprised to find that most users were significantly more active in the afternoon, rather than in the morning or evening. This could be a sign of Bellabeat’s target audience—possibly individuals who don’t follow a typical 9-to-5 schedule or who have more physically demanding jobs. Of course, drawing solid conclusions would require more data than we currently have access to, but it’s something worth considering for future research. It wasn’t surprising to see that activity levels in the morning and evening were relatively the same. As expected, nighttime was when users were the least active.

### Daily/Sleep Data <a id="daily-sleep-data-r"></a>
- <span style="color:gray;">'dailyMerged.csv'</span>

I uploaded my dailyMerged dataset into RStudio and checked the data imported correctly. 
<br>

Upload check: 
<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# import dailyMerged dataset, rename (df = dataframe)
daily_df <- read_csv("dailyMerged.csv")
</code></pre>

</details>

Upload check: 

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

First, I analyzed how frequently users engaged with their smart devices (though the specific device types remain unknown). My goal was to understand how many Bellabeat users were consistently using their devices versus those who hardly used them. This could give a better sense of how engaged users are overall.

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# assign usage type
user_usage <- daily_df%>%
+    count(Id) %>% 
+     mutate(user_type = case_when(
+      n >= 1 & n <= 10 ~ "sparse",
+              n >= 11 & n <= 20 ~ "modest",
+            n >= 21 & n <= 31 ~ "frequent"
+  ))
# assign usage percentage
user_usage_percent <- user_usage %>%
+     count(user_type) %>%
+     mutate(
+         total_percent = n / sum(n),
+         labels = scales::percent(total_percent),
+         user_type = factor(user_type, levels = c("frequent", "modest", "sparse"))
+ )
#check results
print(user_usage_percent)
# A tibble: 3 × 4
  user_type     n total_percent labels
  <fct>     <int>         <dbl> <chr> 
1 frequent     12         0.5   50%   
2 modest        3         0.125 12%   
3 sparse        9         0.375 38% 
#create ggplot donut chart
ggplot(user_usage_percent, aes(x = 2, y = total_percent, fill = user_type)) +
  geom_bar(stat = "identity", width = 1, color = "white") +
  coord_polar("y") +
  xlim(0.5, 2.5) +
  scale_fill_manual(values = c("frequent" = "#2a9d8f", 
                               "modest" = "#70c1b3", 
                               "sparse" = "#b2dfdb")) +
  geom_text(aes(label = scales::percent(total_percent)), 
            position = position_stack(vjust = 0.5), 
            color = "white", size = 4) +
  theme_void() +
  labs(title = "Smart Device Usage Frequency") +
  theme(
    plot.title = element_text(hjust = 0.5),
    legend.position = "bottom",
    legend.title = element_blank()
  )

</code></pre>

</details>


I ran another correlation test—similar to the one I used with the hourly dataset—to explore the relationship between sleep and activity levels.

<details>
<summary>Show R Code</summary>

<pre><code class="language-r">
# Pearson correlation test: total minutes asleep vs heavy active minutes
with(daily_df, cor.test(TotalMinutesAsleep, HeavyActiveMinutes, method = "pearson"))

	Pearson's product-moment correlation

data:  TotalMinutesAsleep and HeavyActiveMinutes
t = -3.7286, df = 408, p-value = 0.0002197
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.27356474 -0.08619484
sample estimates:
       cor 
-0.1815268 

#Pearson correlation test: total minutes asleep vs light/non active minutes
with(daily_df, cor.test(TotalMinutesAsleep, LightActiveMinutes, method = "pearson"))

	Pearson's product-moment correlation

data:  TotalMinutesAsleep and LightActiveMinutes
t = -14.644, df = 408, p-value < 2.2e-16
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.6470247 -0.5196501
sample estimates:
       cor 
-0.5869577

# Pearson correlation test: total minutes asleep vs calories
with(daily_df, cor.test(TotalMinutesAsleep, Calories, method = "pearson"))

	Pearson's product-moment correlation

data:  TotalMinutesAsleep and Calories
t = -0.64061, df = 408, p-value = 0.5221
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
 -0.12815287  0.06534893
sample estimates:
        cor 
-0.03169899 

# Plot sleep vs light/non activity
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

The results show that people who sleep more tend to have fewer light/non-active minutes during the day—a moderately strong relationship. There’s also a slight decrease in active minutes with more sleep, but that correlation is much weaker. Overall, the negative correlations suggest that more sleep may be linked to less sedentary time. The graph above supports this, indicating that individuals who get more sleep may also be more active overall.

To dig deeper into the data, I broke it down by day of the week to compare sleep and light/non-active minutes across different days. In the code block below, I filtered the data by weekday and generated summary stats for each group. This helps show when users are getting the most—or least—engagement with their smart device. These summaries show how sleep and activity levels change throughout the week.



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
as.data.frame (mon_data_summary)
  Total_Steps_Avg Active_Minutes_Avg Sedentary_Minutes_Avg Calories_Avg Total_Hours_Asleep_Avg
1        9273.217           49.80435              940.7826     2431.978               6.991667

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
as.data.frame(tues_data_summary)
  Total_Steps_Avg Active_Minutes_Avg Sedentary_Minutes_Avg Calories_Avg Total_Hours_Asleep_Avg
1        9182.692           50.66154              956.6308       2496.2               6.742308

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
as.data.frame (wed_data_summary)
  Total_Steps_Avg Active_Minutes_Avg Sedentary_Minutes_Avg Calories_Avg Total_Hours_Asleep_Avg
1        8022.864           38.07576              922.4242     2378.242               7.244697

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
as.data.frame (thurs_data_summary)
  Total_Steps_Avg Active_Minutes_Avg Sedentary_Minutes_Avg Calories_Avg Total_Hours_Asleep_Avg
1        8183.516           38.71875              901.3125     2306.672               6.688281

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
as.data.frame (fri_data_summary)
  Total_Steps_Avg Active_Minutes_Avg Sedentary_Minutes_Avg Calories_Avg Total_Hours_Asleep_Avg
1        7901.404           35.73684              965.7719     2329.649               6.757018

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
as.data.frame (sat_data_summary)
  Total_Steps_Avg Active_Minutes_Avg Sedentary_Minutes_Avg Calories_Avg Total_Hours_Asleep_Avg
1        9871.123            50.2807              927.2105     2506.895               6.984503

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
as.data.frame (sun_data_summary)
  Total_Steps_Avg Active_Minutes_Avg Sedentary_Minutes_Avg Calories_Avg Total_Hours_Asleep_Avg
1        7297.855           38.90909              887.6727       2276.6               7.545758

</code></pre>

</details>

I used the following code blocks to generate graphs that represent the results of the stat summaries.


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


<!-- Wrapper to center everything as a unit -->
<div style="display: flex; flex-direction: column; align-items: center; margin: 0 auto;">

  <!-- Top Row: 3 Images -->
  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 30px; justify-items: center; max-width: 1100px;">
    <div style="text-align: center; width: 340px;">
      <h4>Avg Calories by Weekday</h4>
      <img 
        src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20calories%20final.png" 
        alt="Avg Calories" 
        style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: #fff; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    </div>

    <div style="text-align: center; width: 340px;">
      <h4>Avg Active Minutes by Weekday</h4>
      <img 
        src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20active%20minutes.png" 
        alt="Avg Active Minutes" 
        style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: #fff; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    </div>

    <div style="text-align: center; width: 340px;">
      <h4>Avg Sedentary Minutes by Weekday</h4>
      <img 
        src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/Avg%20sedentary%20minutes.png" 
        alt="Avg Sedentary Minutes" 
        style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: #fff; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    </div>
  </div>

  <!-- Spacer -->
  <div style="height: 40px;"></div>

  <!-- Bottom Row: 2 Images -->
  <div style="display: flex; justify-content: center; gap: 30px; flex-wrap: wrap;">
    <div style="text-align: center; width: 340px;">
      <h4>Avg Hours of Sleep by Weekday</h4>
      <img 
        src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20hours%20of%20sleep%20by%20weekday.png" 
        alt="Avg Hours of Sleep" 
        style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: #fff; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    </div>

    <div style="text-align: center; width: 340px;">
      <h4>Avg Steps by Weekday</h4>
      <img 
        src="https://raw.githubusercontent.com/emelynataly77/emelynataly77.github.io/main/projects/avg%20steps%20by%20weekday.png" 
        alt="Avg Steps" 
        style="width: 100%; aspect-ratio: 4 / 3; object-fit: contain; background: #fff; padding: 10px; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    </div>
  </div>

</div>


Looking at the graphs, it becomes clear that the start of the workweek—Monday and Tuesday—along with Saturday, tend to be higher across most of the graphs. In contrast, Fridays consistently show lower values, suggesting that user activity tends to slow down as the week wraps up.



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
