---

# 🧮 SQL Queries in BigQuery <a name="sql-queries"></a>

### Hourly Data

- <span style="color:gray;">'hourlyCalories.csv'</span>  
- <span style="color:gray;">'hourlySteps.csv'</span>  
- <span style="color:gray;">'hourlyIntensities.csv'</span>  

The hourly datasets above were uploaded into BigQuery. I checked if a smooth upload was successful by using a few quick queries:

---

Successful Upload Check

<details>
<summary>Show SQL Query</summary>

{% highlight sql %}
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
{% endhighlight %}

</details>

---

The resulting data file: <span style="color:gray;">'hourlyMerged.csv'</span> can now be uploaded into RStudio to be further processed.

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged).

### Daily/Sleep Data

- <span style="color:gray;">'dailyActivity.csv'</span>  
- <span style="color:gray;">'dailyCalories.csv'</span>  
- <span style="color:gray;">'dailyIntensities.csv'</span>  
- <span style="color:gray;">'dailySteps.csv'</span>  
- <span style="color:gray;">'sleepDay.csv'</span>  

The daily datasets above were uploaded into BigQuery. Again, I quickly checked if the data was uploaded accurately using the code below:

---

Successful Upload Check

<details>
<summary>Show SQL Query</summary>

{% highlight sql %}
-- Remove NULLs from daily and sleep
SELECT *
FROM `bellabeat-case-study.Fitabase.dailyActivity`
WHERE TotalSteps IS NOT NULL;

SELECT *
FROM `bellabeat-case-study.Fitabase.sleepDay`
WHERE TotalMinutesAsleep IS NOT NULL;
{% endhighlight %}

</details>

---

The resulting data file: <span style="color:gray;">'daily_Merged.csv'</span> can now be uploaded into RStudio to be further processed.

NOTE: I reintroduced the 'merged' wordage here because that is more representative of the data (which we merged).

# 🖥️ RStudio Analysis <a name="rstudio-analysis"></a>

This section covers the data cleaning, analysis, and visualization done in RStudio for the Bellabeat project.

### Hourly Data <a name="rstudio-hourly-data"></a>

Analysis of calories and steps by hour...

<details>
<summary>Show R Code</summary>

{% highlight r %}
hourlyMerged1$activityDate <- as.Date(hourlyMerged1$activityDate, format="%Y-%m-%d")
{% endhighlight %}

</details>

### Daily/Sleep Data

Exploration of daily activity and sleep patterns...

<details>
<summary>Show R Code</summary>

{% highlight r %}
dailyActivity1 <- dailyActivity %>%
  select(Id, ActivityDate, TotalSteps, TotalDistance, Calories)

sleepDay_clean <- sleepDay %>%
  select(Id, SleepDay, TotalSleepRecords, TotalMinutesAsleep, TotalTimeInBed)
{% endhighlight %}

</details>

