---
layout: default
title: Chess Stats Visualization
---

# Chess Stats Visualization on Tableau
--- 

Hello fellow chess fanatic! This project explores trends in chess openings using a [Kaggle](https://www.kaggle.com/datasets/alexandrelemercier/all-chess-openings) dataset of thousands of online games. The dataset was uploaded by the user: Alexandre Le Mercier, and updated a year ago. The dashboard, built in Tableau Public, highlights player win rates, draw percentages, and performance ratings across various chess openings. It helps answer questions like which openings are most successful, which color tends to win, and how player strength affects outcomes.

The data cosists of the following fields: 
- **Opening**: The name of the chess opening or defense variation.
- **Colour**: The side (White or Black) that the opening is more favorable towards.
- **Num Games**: The total number of games played with this opening.
- **ECO**: The Encyclopaedia of Chess Openings classification code.
- **Last Played**: The date of the latest game in the dataset utilizing this opening.
- **Perf Rating**: The average performance rating of players who have played this opening.
- **Avg Player**: The overall average rating of players in the dataset.
- **Player Win** %: The win rate for players using the opening.
- **Draw %**: The percentage of games that ended in a draw.
- **Opponent Win %**: The win rate against players using the opening.
- **Moves**: A sequence of the initial moves in standard chess notation.
- **Moves_list**: A comprehensive list of all moves made in the opening sequence.
- **Move1w to Move4b**: Detailed opening moves for both White and Black, up to the 4th move
- **White_win%, Black_win%**: The win percentages for White and Black.
- **White_odds**: The odds ratio favoring White based on win rates.
- **White_Wins, Black_Wins**: The total number of wins by White and Black.


<!-- Full dashboard preview image -->
<div style="text-align: center; margin-bottom: 30px;">
  <a href="https://public.tableau.com/views/ChessStats_17544059915240/Dashboard1" target="_blank">
    <img src="../assets/img/Dashboard.png" alt="Full Dashboard Preview" style="max-width: 90%; width: 900px; height: auto; border-radius: 10px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </a>
  <p style="font-size: 0.9em; color: #666;">Click the dashboard preview to view it interactively on Tableau Public</p>
</div>

## 🔹 Treemap: The 15 Most Used Openings

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Tree.png" style="flex: 1 1 700px; max-width: 100%; border-radius: 10px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);" alt="Common Openings Treemap">


  <div style="flex: 1 1 400px;">
    <p>
      This treemap highlights the top 15 most popular chess openings from the dataset. The color gradient represents success rates based on player win percentages, with deeper green indicating lower win rates, deeper blue indicating higher success, and white sitting in the middle of the green-to-blue scale. The interactive viz displays each opening along with the total number of games it appears in and its average player win percentage.

What’s immediately clear from the data is that popularity doesn’t always equal success. For example, the most commonly played opening is the Sicilian Defense, Closed Variation, appearing in 32,617 games. However, it has a relatively low average win rate of just 32.17%. On the other hand, the Sicilian Defense, Nyezhmetdinov-Rossolimo Attack shows up in only 17,184 games, yet has the highest win rate at 41.80%.

So while certain openings are widely used, that doesn’t necessarily make them the most effective, sometimes the best moves are the ones less played. Keep in mind that this viz did not take player skill level into account. 
    </p>
  </div>
</div>

## 🔹 Bar Chart: Top 15 Most Successful Openings

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Bar.png" style="flex: 1 1 500px; max-width: 100%; border-radius: 10px; box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);" alt="Top Openings Bar Chart">

  <div style="flex: 1 1 400px;">
    <p>
   So, what are the most successful chess openings according to this dataset? The bar chart showcases the top 15 most successful openings, ranked by average player win percentage. This means we're not looking at how often an opening is used, just how effective it is when it is used (by either White or Black). 

Interestingly, the top 15 most successful openings don’t overlap with the top 15 most common ones. That tells us something important: just because an opening is popular doesn’t necessarily mean it is effective. 

There’s also a classic debate in the chess world, does White have a natural advantage just by moving first? To explore that, each bar in the chart is color-coded: gray if White tends to win more with that opening, and black if Black is more likely to win.

According to the data, the Italian Game, Two Knights Defense, Fried Liver Attack is the most successful opening, with a 77.60% average win rate, favoring White. It’s not the most played on the list though. The most played is the Scotch Game, General, which shows up in 3,697 games, but has a lower overall win rate.

Most of the bars in the chart favor White, so does that mean White really has the advantage according to the data? Let’s take a closer look.

NOTE: draws are included in the interactive viz, shown as percentages, since not every game ends with a win for either side.

    </p>
  </div>
</div>


## 🔹 Pie Chart: Game Outcome Distribution

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Pie.png" style="flex: 1 1 500px; max-width: 100%; border-radius: 10px;" alt="Pie Chart of Outcomes">
  <div style="flex: 1 1 400px;">
    <p>
   The pie chart breaks down the overall outcomes of games in the dataset: wins by White, wins by Black, and draws. While White has the highest win rate between the two sides, draws actually make up the largest portion of game results. This suggests that White might have a slight edge over Black, but it’s not overwhelming. Of course, we haven’t factored in player skill yet, so let’s dig deeper into the data. 
    </p>
  </div>
</div>


## 🔹 Scatter Plot: Color Performance by Opening

<div style="display: flex; flex-wrap: wrap; gap: 20px; align-items: flex-start;">
  <img src="../assets/img/Scatter.png" style="flex: 1 1 500px; max-width: 100%; border-radius: 10px;" alt="Scatter Plot of Ratings">
  <div style="flex: 1 1 400px;">
    <p>
This scatter plot compares White and Black win percentages across different openings, using only games played by higher-rated players (avg rating between 2200 and 2400). By filtering out lower-level games and limiting the chart to openings with at least 400 games, we’re focusing on data that’s a little bit more reliable and relevant. 
      
Each point represents a chess opening. The size of the point shows how many games it was used in, and the color reflects the draw rate. There's a horizontal line showing the average White win rate, points below the line tend to favor White, while those above the line lean more toward Black.

What this chart shows is that even at higher skill levels, many openings still lean in favor of White, with more points falling below the diagonal or to the right of center. That adds some weight to the idea that White might have a slight edge. That said, there are also a few openings where Black holds their ground or even outperforms White, but this happens rarely.
Overall, White does seem to have a slight edge in the outcomes of the games included in this dataset.
    </p>
  </div>
</div>

## 🧠 Conclusion

Overall, this project highlights some trends in chess strategy. I personally, love chess and enjoy digging into datasets like these to help gain insights on the game and data tactics. While some openings are clearly more popular, that doesn’t always translate to higher success rates. In fact, less common openings sometimes outperform the usual favorites. The analysis also suggests that White tends to have a slight edge, amongst different skill levels, though the margin isn't super significant. By combining win rates, draw percentages, and player skill levels, this dataset provides a valuable look at how opening choices impact game outcomes. So maybe look into learning more niche openings and gravitate to playing white. Good luck on your next game!

## 🔗 View the Full Interactive Dashboard

Click below to explore the full dashboard on Tableau Public:

[➡️ View on Tableau Public](https://public.tableau.com/views/ChessStats_17544059915240/Dashboard1)

