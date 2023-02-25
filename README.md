# League-of-Legends-Pro-Data-Analysis


## Does Team Side Affect Gameplay Outcomes?
I will be doing analysis on League of Legends Pro Game Data from 2022. <br> 
In League of Legends you play on either the Red side or the Blue side. While these sides are intended to be perfectly balanced, there are a few ways in which the map and camera orientation can affect gameplay. I intend to analyze whether or not there are visible effects on outcomes such as:
- Winrate
- Objective control
- Gold accumulation
- XP accumulation

## Data Cleaning Process

This data set had many irrelevant columns so I first selected only relevant columns to my analysis. These columns consisted of data concerning what team secured each objective first, team gold and xp differences at different points in the game, and total game time. <br>

The data also consisted of both team data and player data. My analysis focused on team outcomes such as winrate and objective control so I chose to filter out player data. <br>

The dataset stored boolean data as floats of 1.0 and 0.0 so I converted relevant columns to boolean data. There was also match time data which I chose to convert from seconds to minutes to better understand in data in relation to the game. <br>

 I also found that there were more False values than True values for the won games column meaning there were a few matches that ended in draws or some other issue. The data was organized by gameid so I had to group by gameid and find all instances where the won games didnt sum to 1. I then removed all rows where gameid groups didnt sum to 1. 

## Exploratory Data Analysis

### Univariate Analysis
I chose to analyze three main things in my univariate analysis:
- Game length distribution
- Gold diffs at 10 and 15 minute marks
- XP diffs at 10 and 15 minute marks <br>

#### Game length distribution:

I chose to visualize the distribution of game lengths in order to better understand what objectives were available in the average game since certain objectives only spawn later into the game such as baron at 20 minutes and elder at 35. 

<iframe src="assets/gamelength.html" width=800 height=600 frameBorder=0></iframe>

The smallest game length observed was 15.55 minutes while the longest was 59.61 minutes

#### Gold and XP diffs at 10 and 15 minutes:

I chose to analyze the distribution of gold and xp diffs at the 10 and 15 minute marks to see how much of an impact early gold and xp leads had on later gold and xp leads. This was relevant to my broader question because the team side you are on has a larger impact on the game while still in laning phase (0 - 10/15 minutes typically).

##### Gold Diff at 10 minutes
<iframe src="assets/gd10.html" width=600 height=600 frameBorder=0></iframe>

##### Gold Diff at 15 minutes
<iframe src="assets/gd15.html" width=400 height=400 frameBorder=0></iframe>

##### XP Diff at 10 minutes
<iframe src="assets/xpd10plot.html" width=200 height=200 frameBorder=0></iframe>

##### XP Diff at 15 minutes
<iframe src="assets/xpd15plot.html" width=100 height=100 frameBorder=0></iframe>



### Bivariate Analysis

For my bivariate analysis I wanted to finally look into whether or not there were visible differences in outcomes based on team side. <br>
In order to do so I chose to look at initial objective control and winrate by team color. This means I would be looking at:
- Winrate by team side
- First team to take dragon by team side
- First team to take rift herald by team side
- First team to take baron by team side


### Interesting Aggregates

To easily show the affects of team side across these metrics I chose to groupby team side and find the mean values. This left me with winrate percentages by side, initial objective control rates by side, and mean gold and xp diffs by side at different points in the game.








