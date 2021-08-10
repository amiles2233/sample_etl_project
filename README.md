# Example ETL Project Repo

UCSD Data Visualization Course

## Data Sources 

The data for this project came from a [Kaggle dataset](https://www.kaggle.com/gyejr95/league-of-legendslol-ranked-games-2020-ver1) on League of Legends Ranked games that occurred in 2020.

## Cleaning and Joining Process

I have a mix of challenger level and game level datasets. For the `challenger_match` data, I aggregate up by the `gameId` column to get the number of challengers by game.

With the game level datasets, there is `match_data` which provides overall match features like Game Mode, Game Type etc. Most of my work there is just restricting the dataset down to the columns of interest.

 Both the `match_winner` and `match_loser` data have columns containing info about whether the winning or losing team had a first kill, a first tower, etc. and the raw number of those features as well. I chose to re-code the `first` columns as integers rather than booleans because it is easier to get averages from 1s and 0s, and it is more robust for my excel users out there.

All of the datasets have a `gameId` column, which I used to join them all together.

## Final Destination

After all the data was joined together, I placed it in a local PostgreSQL database.