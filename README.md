# League-of-Legends-Pro-Data-Analysis


## Does Team Side Affect Gameplay Outcomes?
I will be doing analysis on League of Legends Pro Game Data from 2022. <br> 
In League of Legends you play on either the Red side or the Blue side. While these sides are intended to be perfectly balanced, there are a few ways in which the map and camera orientation can affect gameplay. I intend to analyze whether or not there are visible effects on outcomes such as:
- Winrate
- Objective control
- Gold accumulation
- XP accumulation

## Data Cleaning Process

This data set had many irrelevant columns so I first selected only relevant columns to my analysis. The data also consisted of both team data and player data. My analysis focused on team outcomes such as winrate and objective control so I chose to filter out player data. The dataset stored boolean data as floats of 1.0 and 0.0 so I converted relevant columns to boolean data. There was also match time data which I chose to convert from seconds to minutes to better understand in data in relation to the game. I also found that there were more False values than True values for the won games column meaning there were a few matches that were draws or some other issue. The data was organized by gameid so I had to group by gameid and find all instances where the won games didnt sum to 1. I then removed all rows where gameid groups didnt sum to 1.

## Exploratory Data Analysis

<iframe src="assets/gamelength.html" width=800 height=600 frameBorder=0></iframe>






