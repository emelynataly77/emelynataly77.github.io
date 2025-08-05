---
layout: default
title: Chess Stats Visualization
---

# Chess Stats Visualization on Tableau

![Full Dashboard](../assets/images/dashboard_preview.png){: style="width: 100%; height: auto;" }

This project explores trends in chess openings using a Kaggle dataset of thousands of online games. The dashboard was created in Tableau Public and highlights win rates, draw percentages, and performance metrics for different opening strategies. It allows us to understand which openings are most successful, and how game outcomes differ by color and player rating.

---

## 🔹 Opening Win Rates

<div style="display: flex; gap: 20px; align-items: flex-start;">
  <img src="../assets/images/opening_win_rates.png" style="width: 50%; border-radius: 10px;" alt="Opening Win Rates">
  <p style="width: 50%;">
    This bar chart displays the top 15 chess openings ranked by player win percentage. Openings such as the Queen’s Gambit and Sicilian Defense show a strong tendency for White or Black to gain an advantage. The visualization highlights which strategies offer the best chance of success.
  </p>
</div>

---

## 🔹 Draw vs Win/Loss Breakdown

<div style="display: flex; gap: 20px; align-items: flex-start;">
  <img src="../assets/images/draw_distribution.png" style="width: 50%; border-radius: 10px;" alt="Draw Distribution">
  <p style="width: 50%;">
    This stacked bar chart shows the distribution of game outcomes—wins, losses, and draws—for each opening. Some openings, like the Petroff Defense, are highly draw-prone, while others lead to more decisive outcomes. This helps identify conservative vs aggressive strategies.
  </p>
</div>

---

## 🔹 Performance by Opening

<div style="display: flex; gap: 20px; align-items: flex-start;">
  <img src="../assets/images/rating_vs_opening.png" style="width: 50%; border-radius: 10px;" alt="Performance by Opening">
  <p style="width: 50%;">
    This scatter plot shows the average performance rating of players using each opening. We can observe that stronger players often use balanced or positional openings, while more casual players may favor aggressive lines.
  </p>
</div>

---

## 🔗 View the Full Dashboard

Click below to explore the interactive Tableau dashboard:

[➡️ View on Tableau Public](https://public.tableau.com/views/ChessStats_17544059915240/Dashboard1)
