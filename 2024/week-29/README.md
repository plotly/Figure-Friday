# The English Women's Football (EWF) Database

The English Women's Football (EWF) Database is an open database of matches played in the top tiers of women's football in England. It covers all matches played since the 2011 season for the highest division (the Women's Super League) and since the 2014 season for the second-highest division (the Women's Championship).

## A brief recent history of professional women's football in England

With the first season held in 2011, the Women's Super League replaced the FA Women's Premier League National Division as the highest division in England. A second division was introduced for this new structure in 2014 which meant teams could be promoted and relegated.

Since the competition's start, all games in a season were played in a single year (a summer league). This changed from the 2017-2018 season, when games were played across two years (a winter league) to align with the traditional English football calendar. For this change to take place, a shortened series of games was played in 2017 (known as the Spring Series). This is included in the database for completeness, under the 2017-2017 season.

As the 2019-2020 season was cut short due to the Covid pandemic, the final standings in each league were based on a points-per-game average.

Due to repeated changes in the structure of women's football in England, promoted and relegated teams have not always been those that finished top and bottom of their division, respectively. For example, Doncaster Rovers Belles (`T-011-T`) placed first in the 2017-2018 tier 2 division but were ultimately relegated to tier 3 because they withdrew from the league for financial reasons. There has been a more consistent approach since the 2021-2022 season, with 12 teams in each division. Due to Reading Women (`T-023-T`) withdrawing from tier 2 at the end of the 2023-2024 season and playing in tier 5 in the 2024-2025 season, there will be 11 teams in tier 2 in 2024-2025.

## Using the data

The database contains three datasets:

* `ewf_matches` contains all matches that have been played and has one observation per match per season.
* `ewf_appearances` contains all appearances by a team and has one observation per team per match per season.
* `ewf_standings` contains all end-of-the-season division tables and has one observation per team per season.

Each dataset is provided as a CSV file in the `data` folder. These can be accessed by either cloning this GitHub repository or by downloading a copy by clicking 'Code' and then 'Download Zip' at the top of this page.

All three datasets will be updated with the latest information at the end of each season.

If you notice an error in the data or have any requests/feedback, please add it [here](https://github.com/probjects/ewf-database/issues).

The English Women's Football (EWF) Database is licensed under <a href="https://creativecommons.org/licenses/by-sa/4.0/" target="_blank">CC BY-SA 4.0</a>. This means that you can distribute, modify, and use all or part of the database for commercial or non-commercial purposes as long as (1) you provide proper attribution and (2) any new works you produce based on this database also carry the CC-BY-SA 4.0 license.

Please cite the database as:
> The English Women's Football (EWF) Database, May 2024, https://github.com/probjects/ewf-database.

Inspiration has been taken from the <a href="https://github.com/jfjelstul/englishfootball" target="_blank">Fjelstul English Football Database</a>, a similarly structured dataset that covers men's professional football since 1888.

## Analysis of the data

If you have used any of this data in your own work, please [let me know](https://github.com/probjects/ewf-database/issues) and it will be showcased here.

## Description of the data

The data in the English Women's Football (EWF) Database has been collected from multiple online sources and has been cross-referenced to confirm its accuracy. Information in the database is also cross-referenced with itself to ensure consistency. For example, that a team's `goals_for` at the end of the season in `ewf_standings` is equal to the number of goals they have scored across all games played in `ewf_matches`.

Each team has been given a unique ID in the format of `T-###-T`. This is to enable the tracking of team performance across multiple seasons, as most teams have changed their name over time. For example, Arsenal Ladies became Arsenal Women before the start of the 2017-2018 season, but the same ID is used for them throughout the database (`T-001-T`). The name of the team in each dataset is the name of the team at the time. Any generic terms such as 'Football Club' or 'F.C.' have been removed. Reference to 'Women' or 'Ladies' is included in the team name, where applicable, to indicate changes that have occurred. However, most teams do not explicitly reference 'Women' or 'Ladies' in their name unless it is to distinguish between the male and female teams.

### Data dictionary

#### ewf_matches

| Field      | Description |
| ----------- | ----------- |
| season_id | The unique ID for the season. Has the format `S-####-####-#-S`, where the first number is the year in which the season started, the second number is the year in which the season ended, and the third number is the tier.|
| season | The year(s) that the season started and ended. Has the format `####-####`, where the first number is the year in which the season started and the second number is the year in which the season ended.|
| tier | The division's tier in English football. Possible values are `1` or `2`.|
| division | The division name in English football.|
| match_id | The unique ID for the match. Has the format `M-####-####-#-###-M`, where the first number is the year in which the season started, the second number is the year in which the season ended, the third number is the tier, and the fourth number is a counter that is assigned to the data when sorted by the match's date, then by the name of the home team, and then by the name of the away team.|
| match_name| The name of the match, where the name of the home team and the name of the away team is separated by ' vs '.|
| date| The date of the match, in ``dd/mm/yyyy`` format.|
| attendance| The total crowd attendance at the match. Note that this information is not available for some matches.|
| home_team_id| The unique ID for the home team. Has the format `T-###-T`.|
| home_team_name| The name of the home team at the match.|
| away_team_id| The unique ID for the away team. Has the format `T-###-T`.|
| away_team_name| The name of the away team at the match.|
| score| The score of the match. Has the format `# -- #`, where the first number is the score of the home team and the second number is the score of the away team.|
| home_team_score| The score of the home team.|
| away_team_score| The score of the away team.|
| home_team_score_margin| The score margin for the home team, equal to home_team_score minus away_team_score.|
| away_team_score_margin| The score margin for the away team, equal to away_team_score minus home_team_score.|
| home_team_win| Whether the home team won the match. Possible values are `1` if the home team won the match and `0` otherwise.|
| away_team_win| Whether the away team won the match. Possible values are `1` if the away team won the match and `0` otherwise.|
| draw| Whether the match ended in a draw. Possible values are `1` if the match ended in a draw and `0` otherwise.|
| result| The result of the match. Possible values are `Home team win`, `Away team win`, and `Draw`.|
| note| A description of any mitigating circumstances. For example, if the match was not played and the win was instead awarded to the home or away team.|

#### ewf_appearances

| Field      | Description |
| ----------- | ----------- |
| season_id | The unique ID for the season. Has the format `S-####-####-#-S`, where the first number is the year in which the season started, the second number is the year in which the season ended, and the third number is the tier.|
| season | The year(s) that the season started and ended. Has the format `####-####`, where the first number is the year in which the season started and the second number is the year in which the season ended.|
| tier | The division's tier in English football. Possible values are `1` or `2`.|
| division | The division name in English football.|
| match_id | The unique ID for the match. Has the format `M-####-####-#-###-M`, where the first number is the year in which the season started, the second number is the year in which the season ended, the third number is the tier, and the fourth number is a counter that is assigned to the data when sorted by the match's date, then by the name of the home team, and then by the name of the away team. References `match_id` in the `ewf_matches` dataset.|
| match_name| The name of the match, where the name of the home team and the name of the away team is separated by ' vs '.|
| date| The date of the match, in ``dd/mm/yyyy`` format.|
| attendance| The total crowd attendance at the match. Note that this information is not available for some matches.|
| team_id| The unique ID for the team. Has the format `T-###-T`.|
| team_name| The name of the team at the match.|
| opponent_id| The unique ID for the team’s opponent. Has the format `T-###-T`.|
| opponent_name| The name of the team’s opponent at the match.|
| score| The score of the match. Has the format `# -- #`, where the first number is the score of the home team and the second number is the score of the away team.|
| home_team| Whether the team was the home team. Possible value are `1` if the team was the home team and `0` otherwise.|
| away_team| Whether the team was the away team. Possible value are `1` if the team was the away team and `0` otherwise.|
| goals_for| The number of goals scored by the team.|
| goals_against| The number of goals scored against the team.|
| goal_difference| The number of goals scored by the team minus the number of goals scored against the team.|
| result| The result of the match. Possible values are `Win`, `Loss`, and `Draw`.|
| win| Whether the team won the match. The possible values are `1` if the team won the match and `0` otherwise.|
| loss| Whether the team lost the match. The possible values are `1` if the team lost the match and `0` otherwise.|
| draw| Whether the match ended in a draw. The possible values are `1` if the match ended in a draw and `0` otherwise.|
| note| A description of any mitigating circumstances. For example, if the match was not played and the win was instead awarded to the home or away team.|
| points| The number of points the team earned from the match. A team earns `0` points for a loss, `1` point for a draw, or `3` points for a win.|

#### ewf_standings

| Field      | Description |
| ----------- | ----------- |
| season_id | The unique ID for the season. Has the format `S-####-####-#-S`, where the first number is the year in which the season started, the second number is the year in which the season ended, and the third number is the tier.|
| season | The year(s) that the season started and ended. Has the format `####-####`, where the first number is the year in which the season started and the second number is the year in which the season ended.|
| tier | The division's tier in English football. Possible values are `1` or `2`.|
| division | The division name in English football.|
| position | The team's final position in the season.|
| team_id| The unique ID for the team. Has the format `T-###-T`.|
| team_name| The name of the team during the season.|
| played| The number of matches that the team played.|
| wins| The number of matches that the team won.|
| draws| The number of matches that the team drew.|
| losses| The number of matches that the team lost.|
| goals_for| The number of goals scored by the team.|
| goals_against| The number of goals scored against the team.|
| goal_difference| The number of goals scored by the team minus the number of goals scored against the team.|
| points| The number of points that the team earned over the whole season (after applying `point_adjustment`).|
| point_adjustment| The number of points that were deducted by the league due to violations of rules or added by the league due to forfeits.|
| season_outcome| The outcome for the team following the season. This variable is included to track the movement of teams across seasons more easily. Possible values are `Club folded`, `No change` for when the team remains in their current tier, `Promoted to tier 1` for when the team moves into tier 1 from a lower tier, `Relegated to tier 2` for when the team moves into tier 2 from a higher tier, and `Relegated to tier 3` for when the team moves into tier 3 from a higher tier, and `Relegated to tier 5` for when the team moves into tier 5 from a higher tier.|