---
layout: default
title: Chess Stats Visualization
---

# Chess Stats Visualization on Tableau

<!-- Full dashboard preview image -->
<div style="text-align: center; margin-bottom: 30px;">
  <img src="../assets/img/Dashboard.png" alt="Full Dashboard Preview" style="max-width: 90%; width: 900px; height: auto; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
</div>


This project explores trends in chess openings using a Kaggle dataset of thousands of online games. The dashboard, built in Tableau Public, highlights player win rates, draw percentages, and performance ratings across various chess openings. It helps answer questions like which openings are most successful, which color tends to win, and how player strength affects outcomes.

---
## 🔹 Treemap: Top 15 Most Successful Openings

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Tree.png" style="flex: 1 1 500px; max-width: 100%; border-radius: 10px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);" alt="Common Openings Treemap">

  <div style="flex: 1 1 400px;">
    <p>
      This bar chart displays the top 15 most successful chess openings ranked by player win percentage. It reveals that openings such as the Queen’s Gambit and Sicilian Defense are highly successful for the color they favor. These insights help players choose openings with the best statistical performance.
    </p>
  </div>
</div>

## 🔹 Bar Chart: Top 15 Most Successful Openings

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Bar.png" style="flex: 1 1 500px; max-width: 100%; border-radius: 10px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);" alt="Top Openings Bar Chart">

  <div style="flex: 1 1 400px;">
    <p>
      This bar chart displays the top 15 most successful chess openings ranked by player win percentage. It reveals that openings such as the Queen’s Gambit and Sicilian Defense are highly successful for the color they favor. These insights help players choose openings with the best statistical performance.
    </p>
  </div>
</div>


---

## 🔹 Pie Chart: Game Outcome Distribution

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Pie.png" style="flex: 1 1 500px; max-width: 100%; border-radius: 10px;" alt="Pie Chart of Outcomes">
  <div style="flex: 1 1 400px;">
    <p>
      The pie chart breaks down overall game outcomes across the dataset: wins by White, wins by Black, and draws. It shows that White holds a slight statistical advantage, while draws account for a significant portion of games, especially in balanced or defensive openings.
    </p>
  </div>
</div>

---

## 🔹 Scatter Plot: Player Performance by Opening

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Scatter.png" style="flex: 1 1 500px; max-width: 100%; border-radius: 10px;" alt="Scatter Plot of Ratings">
  <div style="flex: 1 1 400px;">
    <p>
      This scatter plot visualizes the average performance rating of players who used each opening. Higher-rated players tend to use more positional or balanced openings. It also highlights which openings are favored among elite versus casual players.
    </p>
  </div>
</div>

---

## 🔗 View the Full Interactive Dashboard

Click below to explore the full dashboard on Tableau Public:

[➡️ View on Tableau Public](https://public.tableau.com/views/ChessStats_17544059915240/Dashboard1)

