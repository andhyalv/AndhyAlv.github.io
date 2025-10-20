# Examining NBA Player Performance for the 2024-2025 Season.
![IMG](images/NBA.jpg "NBA Logo")

### Introduction
After the 2024-2025 National Basketball Association season concluded, I thought that it would be interesting to take a deeper look at player and team performance throughout the season. Understanding the trends of player and team performance will be helpful for teams to learn what is important to winning games. Through the analysis, I aim to provide key insights into difference makers in the NBA. Positions in the NBA can be broken down into 5 roles at the most basic level. Point Gaurds (PG), Shooting Gaurds (SG), Small Forwards (SF), Power Forwards (PF) and Centers (C). These terms will be referred to in the analysis. 

### What will you learn
a) The 3 point percentage per position among NBA teams.

b) The highest scoring players in the NBA are comprised of guards, whether it be point guards or shooting guards.

c) The distribution of age among all teams in the NBA.

d) The distribution of assists per position and player.


### Dataset and tools
The dataset was taken from [Basketball Reference](https://www.basketball-reference.com/leagues/NBA_2025_totals.html) for the 2024-2025 season. The data was converted into a csv file and imported into Tableau for easier visualizations. 
The full visualization can be found [here on Tableau](https://public.tableau.com/app/profile/andhy.alvarez/viz/NBAAnalysis2024-2025Season/NBAAnalysis?publish=yes)

### Data Analysis

#### a) 3pt % Among NBA Teams, broken down by position.
In order to create the visual in Tableau, I entered the position field on the x-axis and the team field on the y-axis. I learned that with this dataset, a player could be a part of multiple teams, which has its own label. Players getting multiple labels for their team creates the issue of double dipping, or their stats being counted twice. Therefore, I had to filter out the multi team label. Another issue that arised is with taking the % at face value. Player shot % measured as shots attempted vs made within their own position class can be skewed by haing too small of a sample size. To account for this, I used a formula that takes the sum of the 3 point shots made for a specific player, and divides it by the sum of the 3 point shots attempted for the team.
Picture of the table.

#### b) The relationship between player scoring, assists and total rebounds.
In order to examine the relationship, I charted points on the x-axis, and assists on the y-axis. To showcase the full relationship by including rebounds, I input the rebound data as a function of plot point size. So, the larger the point, the more rebounds a player grabbed. Player positions are differentiated based on color of the bubble.

The chart tells us that Point gaurds tend to be the higher scoring players, along with more assists. This tracks with the intuition that point gaurds tend to have the ball more throughout the game, and are responsible for distributing the basketball to their teammates.
Centers and power forwards tend to have the larger bubbles, indicating that they get more rebounds. This also tracks with the intuition that larger sized players end up with more rebounds.
Nikola Jokic is a significant outlier from these trends, as he is a leading player in points, assists and rebounds as a center.  

#### c) The distribution of player age among all teams in the NBA.
To visualize the distribution of player age in the NBA, we used a stacked bar chart to compare age groups. The chart shows us the distribution of player scoring based on the age group of players on a team. I kinda hate stacked bar charts. Maybe we can visualize this betterrrrr.
#### d) The distribution of assists per position and player.
In order to visualize the distribution of assists per position and player, we used a tree map. Player positions are distinguished by color, and the size of each box represents the number of assists a player had. Again maybe we can use a different visualization. The treemap shows that point guards hold the highest portion of assists among players, followed by shooting gaurds. 

### Conclusion

### Call to Action
If you were interested in discussing the dataset further or have feedback on the analysis, feel free to message me on [LinkedIn!](https://www.linkedin.com/in/andhyalvarez/)








