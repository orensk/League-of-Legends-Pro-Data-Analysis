# League-of-Legends-Pro-Data-Analysis
<iframe src="assets/Summoner's_Rift_Update_Map.webp" width=600 height=400 frameBorder=0></iframe>


## Does Team Side Affect Gameplay Outcomes?
_This analysis was done on League of Legends Pro Game Data from 2022._ <br> 

In League of Legends the two teams play on either the Red side or the Blue side of the map. <br>
While these sides are intended to be perfectly balanced, there are a few ways in which the map-structure and camera orientation can affect gameplay differently for each side. In pro matches teams are allowed to choose between red or blue side. Throughout the history of the game, teams have favored blue side over red. This could either be due to the pick ban order for the given side or due to the sides affecting gameplay outcomes. <br>

I intend to analyze whether or not there are visible effects on gameplay outcomes such as:
- Winrate
- Objective control
- Gold accumulation
- XP accumulation

## Data Cleaning Process

#### Data Introduction:
- Structure: 149,232 rows × 123 columns
- Relevant Columns: 'gamelength' (Game Time in Seconds), 'result' (Win/Loss), 'firstbaron' (Took/Lost First Baron), 'barons' (Number of Barons Taken by Team), 'firstblood' (Took/Lost First Blood), 'firstdragon' (Took/Lost First Dagon), 'dragons' (Number of Dragons Taken by Team), 'firstherald' (Took/Lost First Rift Herald), 'firsttower' (Took/Lost First Tower), 'golddiffat10' (Gold Diff vs Other Team at 10 Minutes), 'xpdiffat10' (XP Diff vs Other Team at 10 Minutes), 'golddiffat15' (Gold Diff vs Other Team at 15 Minutes), 'xpdiffat15' (XP Diff vs Other Team at 15 Minutes), 'gameid' (ID for given game), 'side' (Red/Blue team side)

#### The Initial Data:


| gameid                | datacompleteness   |   url | league   |   year | split   |   playoffs | date                |   game |   patch |   participantid | side   | position   | playername   | playerid                                  | teamname                 | teamid                                  | champion   | ban1   | ban2    | ban3   | ban4   | ban5   |   gamelength |   result |   kills |   deaths |   assists |   teamkills |   teamdeaths |   doublekills |   triplekills |   quadrakills |   pentakills |   firstblood |   firstbloodkill |   firstbloodassist |   firstbloodvictim |   team kpm |   ckpm |   firstdragon |   dragons |   opp_dragons |   elementaldrakes |   opp_elementaldrakes |   infernals |   mountains |   clouds |   oceans |   chemtechs |   hextechs |   dragons (type unknown) |   elders |   opp_elders |   firstherald |   heralds |   opp_heralds |   firstbaron |   barons |   opp_barons |   firsttower |   towers |   opp_towers |   firstmidtower |   firsttothreetowers |   turretplates |   opp_turretplates |   inhibitors |   opp_inhibitors |   damagetochampions |     dpm |   damageshare |   damagetakenperminute |   damagemitigatedperminute |   wardsplaced |    wpm |   wardskilled |   wcpm |   controlwardsbought |   visionscore |   vspm |   totalgold |   earnedgold |   earned gpm |   earnedgoldshare |   goldspent |   gspd |   total cs |   minionkills |   monsterkills |   monsterkillsownjungle |   monsterkillsenemyjungle |   cspm |   goldat10 |   xpat10 |   csat10 |   opp_goldat10 |   opp_xpat10 |   opp_csat10 |   golddiffat10 |   xpdiffat10 |   csdiffat10 |   killsat10 |   assistsat10 |   deathsat10 |   opp_killsat10 |   opp_assistsat10 |   opp_deathsat10 |   goldat15 |   xpat15 |   csat15 |   opp_goldat15 |   opp_xpat15 |   opp_csat15 |   golddiffat15 |   xpdiffat15 |   csdiffat15 |   killsat15 |   assistsat15 |   deathsat15 |   opp_killsat15 |   opp_assistsat15 |   opp_deathsat15 |
|:----------------------|:-------------------|------:|:---------|-------:|:--------|-----------:|:--------------------|-------:|--------:|----------------:|:-------|:-----------|:-------------|:------------------------------------------|:-------------------------|:----------------------------------------|:-----------|:-------|:--------|:-------|:-------|:-------|-------------:|---------:|--------:|---------:|----------:|------------:|-------------:|--------------:|--------------:|--------------:|-------------:|-------------:|-----------------:|-------------------:|-------------------:|-----------:|-------:|--------------:|----------:|--------------:|------------------:|----------------------:|------------:|------------:|---------:|---------:|------------:|-----------:|-------------------------:|---------:|-------------:|--------------:|----------:|--------------:|-------------:|---------:|-------------:|-------------:|---------:|-------------:|----------------:|---------------------:|---------------:|-------------------:|-------------:|-----------------:|--------------------:|--------:|--------------:|-----------------------:|---------------------------:|--------------:|-------:|--------------:|-------:|---------------------:|--------------:|-------:|------------:|-------------:|-------------:|------------------:|------------:|-------:|-----------:|--------------:|---------------:|------------------------:|--------------------------:|-------:|-----------:|---------:|---------:|---------------:|-------------:|-------------:|---------------:|-------------:|-------------:|------------:|--------------:|-------------:|----------------:|------------------:|-----------------:|-----------:|---------:|---------:|---------------:|-------------:|-------------:|---------------:|-------------:|-------------:|------------:|--------------:|-------------:|----------------:|------------------:|-----------------:|
| ESPORTSTMNT01_2690210 | complete           |   nan | LCK CL   |   2022 | Spring  |          0 | 2022-01-10 07:44:08 |      1 |   12.01 |               1 | Blue   | top        | Soboro       | oe:player:38e0af7278d6769d0c81d7c4b47ac1e | Fredit BRION Challengers | oe:team:68911b3329146587617ab2973106e23 | Renekton   | Karma  | Caitlyn | Syndra | Thresh | Lulu   |         1713 |        0 |       2 |        3 |         2 |           9 |           19 |             0 |             0 |             0 |            0 |            0 |                0 |                  0 |                  0 |     0.3152 | 0.9807 |           nan |       nan |           nan |               nan |                   nan |         nan |         nan |      nan |      nan |         nan |        nan |                      nan |      nan |          nan |           nan |       nan |           nan |          nan |        0 |            0 |          nan |      nan |          nan |             nan |                  nan |            nan |                nan |            0 |                0 |               15768 | 552.294 |     0.278784  |               1072.4   |                    777.793 |             8 | 0.2802 |             6 | 0.2102 |                    5 |            26 | 0.9107 |       10934 |         7164 |      250.928 |          0.253859 |       10275 |    nan |        231 |           220 |             11 |                     nan |                       nan | 8.0911 |       3228 |     4909 |       89 |           3176 |         4953 |           81 |             52 |          -44 |            8 |           0 |             0 |            0 |               0 |                 0 |                0 |       5025 |     7560 |      135 |           4634 |         7215 |          121 |            391 |          345 |           14 |           0 |             1 |            0 |               0 |                 1 |                0 |
| ESPORTSTMNT01_2690210 | complete           |   nan | LCK CL   |   2022 | Spring  |          0 | 2022-01-10 07:44:08 |      1 |   12.01 |               2 | Blue   | jng        | Raptor       | oe:player:637ed20b1e41be1c51bd1a4cb211357 | Fredit BRION Challengers | oe:team:68911b3329146587617ab2973106e23 | Xin Zhao   | Karma  | Caitlyn | Syndra | Thresh | Lulu   |         1713 |        0 |       2 |        5 |         6 |           9 |           19 |             0 |             0 |             0 |            0 |            1 |                0 |                  1 |                  0 |     0.3152 | 0.9807 |           nan |       nan |           nan |               nan |                   nan |         nan |         nan |      nan |      nan |         nan |        nan |                      nan |      nan |          nan |           nan |       nan |           nan |          nan |        0 |            0 |          nan |      nan |          nan |             nan |                  nan |            nan |                nan |            0 |                1 |               11765 | 412.084 |     0.208009  |                944.273 |                    650.158 |             6 | 0.2102 |            18 | 0.6305 |                    6 |            48 | 1.6813 |        9138 |         5368 |      188.021 |          0.19022  |        8750 |    nan |        148 |            33 |            115 |                     nan |                       nan | 5.1839 |       3429 |     3484 |       58 |           2944 |         3052 |           63 |            485 |          432 |           -5 |           1 |             2 |            0 |               0 |                 0 |                1 |       5366 |     5320 |       89 |           4825 |         5595 |          100 |            541 |         -275 |          -11 |           2 |             3 |            2 |               0 |                 5 |                1 |
| ESPORTSTMNT01_2690210 | complete           |   nan | LCK CL   |   2022 | Spring  |          0 | 2022-01-10 07:44:08 |      1 |   12.01 |               3 | Blue   | mid        | Feisty       | oe:player:d1ae0e2f9f3ac1e0e0cdcb86504ca77 | Fredit BRION Challengers | oe:team:68911b3329146587617ab2973106e23 | LeBlanc    | Karma  | Caitlyn | Syndra | Thresh | Lulu   |         1713 |        0 |       2 |        2 |         3 |           9 |           19 |             0 |             0 |             0 |            0 |            0 |                0 |                  0 |                  0 |     0.3152 | 0.9807 |           nan |       nan |           nan |               nan |                   nan |         nan |         nan |      nan |      nan |         nan |        nan |                      nan |      nan |          nan |           nan |       nan |           nan |          nan |        0 |            0 |          nan |      nan |          nan |             nan |                  nan |            nan |                nan |            0 |                0 |               14258 | 499.405 |     0.252086  |                581.646 |                    227.776 |            19 | 0.6655 |             7 | 0.2452 |                    7 |            29 | 1.0158 |        9715 |         5945 |      208.231 |          0.210665 |        8725 |    nan |        193 |           177 |             16 |                     nan |                       nan | 6.7601 |       3283 |     4556 |       81 |           3121 |         4485 |           81 |            162 |           71 |            0 |           0 |             1 |            0 |               0 |                 0 |                1 |       5118 |     6942 |      120 |           5593 |         6789 |          119 |           -475 |          153 |            1 |           0 |             3 |            0 |               3 |                 3 |                2 |
| ESPORTSTMNT01_2690210 | complete           |   nan | LCK CL   |   2022 | Spring  |          0 | 2022-01-10 07:44:08 |      1 |   12.01 |               4 | Blue   | bot        | Gamin        | oe:player:998b3e49b01ecc41eacc392477a98cf | Fredit BRION Challengers | oe:team:68911b3329146587617ab2973106e23 | Samira     | Karma  | Caitlyn | Syndra | Thresh | Lulu   |         1713 |        0 |       2 |        4 |         2 |           9 |           19 |             0 |             0 |             0 |            0 |            1 |                0 |                  1 |                  0 |     0.3152 | 0.9807 |           nan |       nan |           nan |               nan |                   nan |         nan |         nan |      nan |      nan |         nan |        nan |                      nan |      nan |          nan |           nan |       nan |           nan |          nan |        0 |            0 |          nan |      nan |          nan |             nan |                  nan |            nan |                nan |            0 |                0 |               11106 | 389.002 |     0.196358  |                463.853 |                    218.879 |            12 | 0.4203 |             6 | 0.2102 |                    4 |            25 | 0.8757 |       10605 |         6835 |      239.405 |          0.242201 |       10425 |    nan |        226 |           208 |             18 |                     nan |                       nan | 7.9159 |       3600 |     3103 |       78 |           3304 |         2838 |           90 |            296 |          265 |          -12 |           1 |             1 |            0 |               0 |                 0 |                0 |       5461 |     4591 |      115 |           6254 |         5934 |          149 |           -793 |        -1343 |          -34 |           2 |             1 |            2 |               3 |                 3 |                0 |
| ESPORTSTMNT01_2690210 | complete           |   nan | LCK CL   |   2022 | Spring  |          0 | 2022-01-10 07:44:08 |      1 |   12.01 |               5 | Blue   | sup        | Loopy        | oe:player:e9741b3a238723ea6380ef2113fae63 | Fredit BRION Challengers | oe:team:68911b3329146587617ab2973106e23 | Leona      | Karma  | Caitlyn | Syndra | Thresh | Lulu   |         1713 |        0 |       1 |        5 |         6 |           9 |           19 |             0 |             0 |             0 |            0 |            1 |                1 |                  0 |                  0 |     0.3152 | 0.9807 |           nan |       nan |           nan |               nan |                   nan |         nan |         nan |      nan |      nan |         nan |        nan |                      nan |      nan |          nan |           nan |       nan |           nan |          nan |        0 |            0 |          nan |      nan |          nan |             nan |                  nan |            nan |                nan |            0 |                0 |                3663 | 128.301 |     0.0647631 |                475.026 |                    490.123 |            29 | 1.0158 |            14 | 0.4904 |                   11 |            69 | 2.4168 |        6678 |         2908 |      101.856 |          0.103054 |        6395 |    nan |         42 |            42 |              0 |                     nan |                       nan | 1.4711 |       2678 |     2161 |       16 |           2150 |         2748 |           15 |            528 |         -587 |            1 |           1 |             1 |            0 |               0 |                 0 |                1 |       3836 |     3588 |       28 |           3393 |         4085 |           21 |            443 |         -497 |            7 |           1 |             2 |            2 |               0 |                 6 |                2 |


This data set had many irrelevant columns so I first selected only relevant columns to my analysis. These columns consisted of data concerning what team secured each objective first, team gold and xp differences at different points in the game, and total game time. <br>

The data also consisted of both team data and player data. My analysis focused on team outcomes such as winrate and objective control so I chose to filter out player data. Using player data would have led to each data point being repeated 5 times for each team.<br>

The dataset stored boolean data as floats of 1.0 and 0.0 so I converted relevant columns to boolean data. There was also match time data which I chose to convert from seconds to minutes to better understand in data in relation to the game. <br>

I also found that there were more False values than True values for the won games column meaning there were a few matches that ended in draws or some other issue. The data was organized by gameid so I had to group by gameid and find all instances where the won games didnt sum to 1. I then removed all rows where gameid groups didnt sum to 1. <br>

There were also games where no barons/heralds/dragons were taken leading to two False values for the 'firstx' columns. I chose not to filter these games out at this point because they had otherwise valid and valuable data for my analysis. Instead I later filter out these games for specific parts of my analysis such as first baron.

#### Cleaned Data:


|   gamelength |   result | firstbaron   |   barons | firstblood   | firstdragon   |   dragons | firstherald   | firsttower   |   golddiffat10 |   xpdiffat10 |   golddiffat15 |   xpdiffat15 | gameid                | side   |
|-------------:|---------:|:-------------|---------:|:-------------|:--------------|----------:|:--------------|:-------------|---------------:|-------------:|---------------:|-------------:|:----------------------|:-------|
|      28.55   |        False | False        |        0 | True         | False         |         1 | True          | True         |           1523 |          137 |            107 |        -1617 | ESPORTSTMNT01_2690210 | Blue   |
|      28.55   |        True | False        |        0 | False        | True          |         3 | False         | False        |          -1523 |         -137 |           -107 |         1617 | ESPORTSTMNT01_2690210 | Red    |
|      35.2333 |        False | False        |        0 | False        | False         |         1 | True          | False        |          -1619 |        -1586 |          -1763 |         -906 | ESPORTSTMNT01_2690219 | Blue   |
|      35.2333 |        True | True         |        2 | True         | True          |         4 | False         | True         |           1619 |         1586 |           1763 |          906 | ESPORTSTMNT01_2690219 | Red    |
|      32.8667 |        True | True         |        1 | False        | True          |         4 | False         | True         |           -103 |          813 |           1191 |         2298 | ESPORTSTMNT01_2690227 | Blue   |


## Exploratory Data Analysis

### Univariate Analysis
I chose to analyze three main things in my univariate analysis:
- Game length distribution
- Gold diffs at 10 and 15 minute marks
- XP diffs at 10 and 15 minute marks <br>

#### Game length distribution:

I chose to visualize the distribution of game lengths in order to better understand what objectives were available in the average game since certain objectives only spawn later into the game such as baron at 20 minutes and elder at 35. 

<iframe src="assets/gamelength.html" width=600 height=400 frameBorder=0></iframe>

Most games took around 25 - 35 minutes to complete with the most frequent being 30 minutes. The shortest game length observed was 15.55 minutes while the longest was 59.61 minutes. 

#### Gold and XP diffs at 10 and 15 minutes:

I chose to analyze the distribution of gold and xp diffs at the 10 and 15 minute marks to see how much of an impact early gold and xp leads had on later gold and xp leads. This was relevant to my broader question because the team side you are on has a larger impact on the game while still in laning phase (0 - 10/15 minutes typically).

##### Gold Diff at 10 minutes
<iframe src="assets/gd10.html" width=600 height=400 frameBorder=0></iframe>

##### Gold Diff at 15 minutes
<iframe src="assets/gd15.html" width=600 height=400 frameBorder=0></iframe>

##### XP Diff at 10 minutes
<iframe src="assets/xpd10plot.html" width=600 height=400 frameBorder=0></iframe>

##### XP Diff at 15 minutes
<iframe src="assets/xpd15plot.html" width=600 height=400 frameBorder=0></iframe>

Observing these plots it seems that the distribution remains similar but grows in value from the 10 minute to 15 minute mark. I would think that this means early leads tend to grow with time rather than even out. This is possibly important if we find that team side has a stronger impact on the early game.

### Bivariate Analysis

For my bivariate analysis I wanted to finally look into whether or not there were visible differences in outcomes based on team side. <br>
In order to do so I chose to look at initial objective control and winrate by team color. This means I would be looking at:
- Winrate by team side
- First team to take dragon by team side
- First team to take rift herald by team side
- First team to take baron by team side

###### _these values were filtered for games in which the respective objective was taken_

##### Winrate By Side
<iframe src="assets/results.html" width=600 height=400 frameBorder=0></iframe>

Blue side has a favorable winrate of 52.28% compared to Red's 47.71%

##### First Dragon Rate by side
<iframe src="assets/fdragon.html" width=600 height=400 frameBorder=0></iframe>

Red side favorably takes first dragon 59.42% of the time compared to Blue's 40.57%

##### First Rift Herald Rate by side
<iframe src="assets/fherald.html" width=600 height=400 frameBorder=0></iframe>

Blue side favorably takes first herald 57.84% of the time compared to Red's 42.15%

##### First Baron Rate by side
<iframe src="assets/fbaron.html" width=600 height=400 frameBorder=0></iframe>

Blue side takes first baron 50.43% of the time compared to Red's 49.56%

##### Takeaways:
It seems that winrate is slighty favored to blue side, first early objectives (dragon spawns at 5 mins and herald at 8 mins) are heavily skewed to favor opposite sides, and first baron (spawns mid game at 20 minutes) is mostly fair.

### Interesting Aggregates

To show the effects of team side across these metrics I chose to groupby team side and find the mean values. This left me with winrate percentages by side, initial objective control rates by side, and mean gold and xp diffs by side at different points in the game.


###### _these values were not filtered for games in which the respective objective was taken. refer to bivariate analysis for more accurate 'firstx' data_


| side   |   result |   firstbaron |   barons |   firstblood |   firstdragon |   dragons |   firstherald |   firsttower |   golddiffat10 |   xpdiffat10 |   golddiffat15 |   xpdiffat15 |
|:-------|---------:|-------------:|---------:|-------------:|--------------:|----------:|--------------:|-------------:|---------------:|-------------:|---------------:|-------------:|
| Blue   | 0.522845 |     0.477909 | 0.668676 |     0.504192 |      0.405652 |   2.13848 |      0.578238 |      0.54244 |        86.7126 |      23.6677 |         248.29 |     -4.70626 |
| Red    | 0.477155 |     0.469713 | 0.681865 |     0.494395 |      0.594159 |   2.35309 |      0.421479 |      0.45756 |       -86.7126 |     -23.6677 |        -248.29 |      4.70626 |


We can see at a baseline that Blue side has a favorable winrate of 52.28% compared to Red's 47.71% <br>

More interestingly, when we compare the sides and the early game objectives we see a strong relation between first herald going to Blue Side and first dragon going to Red side. <br>

Blue side takes first herald 57.84% of the time while Red side takes first dragon 59.42% of the time. <br>

With my knowledge of the game, I would assume that this is due to the placement of the 'tribrush' for the bot and top lanes. <br>
<iframe src="assets/Trisbush_1st2015.webp" width=600 height=400 frameBorder=0></iframe>
<br>
On Red side the tribrush is placed unfavorably for the top lane. <br>
On Blue side the tribrush is placed unfavorably for the bot lane. 

<br>
This placement means that these lanes will be more easily/effectively ganked by the jungler through their tribrush and therefore lose the lane. 

<br>
For example: Red side Bot lane has a favorable tribrush that appears behind the enemy laners. The Red jungler can path through this for an easier gank onto the Blue bot laners. This allows red side to more easily win the bot lane and therfore control dragon, the bot sided objective, with help from the winning bot lane.

<br>
This sidedness doesn't appear, however, when we look at the midgame objective, Baron. We saw in the bivariate analysis, that Blue side takes first baron 50.43% of the time compared to Red's 49.56%. Baron replaces Rift Herald at the 20 minute mark, spawning in the top side of the map. Seeing the previous data where Blue controls Rift Herald 57.84% of the time, I would think that there would be a more apparent disparity between Red and Blue first baron control. It seems however that objective control by side diminishes as game length progresses, and this would make sense with how games typically play out. Usually by the 20 minute mark when Baron spawns, teams have transitioned from 'laning phase' to being grouped to contest objectives/towers. Grouping would even out the map control allowing teams to more evenly contest objectives.

<br>
Looking at total objective control we can see that Red side actually has a slight lead in both total Dragons and total Barons. Red side on average gets 2.35 dragons while Blue gets 2.13. Red side on average gets 0.68 Barons while Blue gets 0.66. I'm unsure of what could contribute to Red taking slightly more total Dragons and Barons. It could be random chance or true advantage, I will have to see in the future.

<br>
Apart from objective control, we can see that Blue side, on average, has a favorable gold lead at the 10 minute mark which grows into the 15 minute mark. As for XP, Blue side on average starts with an XP lead at the 10 minute mark but this lead diminishes into a slight lead for Red on average at the 15 minute mark. It should be noted that the average Gold Diff values are a much more significant amount than the average XP values.


## Missingness Analysis

### NMAR Analysis:

There are many columns in this data set so NMAR is largely weakened because these columns offer explanations for the missingness of the values. Most columns can be explained by seeing how different leagues collect data, looking at the datacompleteness column, looking to the game timer to see if it was possible for an even to even happen, looking at position (player vs team), etc. 

### Missingness Dependency

#### Missing By Design:

<iframe src="assets/team_md_plot.html" width=600 height=400 frameBorder=0></iframe>

I found that many columns' missingess were impacted by whether or not the position was describing a whole team or an individual player. I chose to demonstrate missing by design by looking at playername and playerid when the position column was set to team or not. All values for playername and playerid were missing when position was set to team.

#### Perumtation Testing for Other Missingness:



## Hypothesis Testing

### Method
My data consisted of 1 year containing 10,615 pro games. I chose to simulate 1 million 'years' of 10,615 games assuming balanced 50/50 distribution of win/firstobjective rate since the sides are intended to be perfectly balanced for gameplay. This allows me to see the odds of the observed number of wins/firstobjectives happening under a perfectly balanced game.
<br>


#### Null Hypothesis 1: Team Side Does Not Affect Winrate Outcomes
#### Alt Hypothesis: Team Side Does Affect Winrate Outcomes
#### Test Statistic: The Number of Wins, by Side.
##### Observed Red and Blue Win Counts Over 10,615 Games vs Wincount Distribution Assuming Equal Winrate
<iframe src="assets/wrfighyp.html" width=600 height=400 frameBorder=0></iframe>

We can see that the observed values for each side fall far outside the distribution expected with balanced odds. Blue side wins far more than expected and red side wins far less than expected. With pvalues very close to 0 (1e-06 and 2e-06 respectively) we can safely reject the null hypothesis, at a significance level of 0.01, that team side does not affect winrates. It is very likely that team side affects winrate.

#### Null Hypothesis 2: Team Side Does Not Affect Initial Dragon Take Rates
#### Alt Hypothesis: Team Side Does Affect Initial Dragon Take Rates
#### Test Statistic: The Number of First Dragons Taken, by Side.
##### Observed Red and Blue Initial Dragon Counts Over 10,615 Games vs Initial Dragon Distribution Assuming Equal Rate
<iframe src="assets/fdragonfighyp.html" width=600 height=400 frameBorder=0></iframe>


We can see that the observed values for each side fall far outside the distribution expected with balanced odds. Red side takes first dragon far more than expected and blue side takes dragon far less than expected. With pvalues very close to 0 (0.000) we can safely reject the null hypothesis, at a significance level of 0.01, that team side does not affect initial dragon rates. It is very likely that team side affects ability to take first Rift Herald.

#### Null Hypothesis 3: Team Side Does Not Affect Initial Rift Herald Take Rates
#### Alt Hypothesis: Team Side Does Affect Initial Rift Herald Take Rates
#### Test Statistic: The Number of First Rift Heralds Taken, by Side.
##### Observed Red and Blue Initial Herald Counts Over 10,615 Games vs Initial Herald Distribution Assuming Equal Rate
<iframe src="assets/fheraldfighyp.html" width=600 height=400 frameBorder=0></iframe>

We can see that the observed values for each side fall far outside the distribution expected with balanced odds. Blue side takes first herald far more than expected and red side takes herald far less than expected. With pvalues very close to 0 (0.000) we can safely reject the null hypothesis, at a significance level of 0.01, that team side does not affect initial herald rates. It is very likely that team side affects ability to take first Rift Herald.



