# DataSet Analysis

## Row Definition

Each row represents a team's participation in a specific FIFA World Cup tournament.

Examples:

- Argentina in 1930
- Brazil in 1930
- France in 1930

Targets:

1. total_goals
2. stage_reached

## Column Analysis

| Column | Meaning | Type | Feature/Target | Initial Decision |
|----------|----------|----------|----------|----------|
| ID | Unique identifier for a team in a specific World Cup tournament (e.g., WC-1930_ARG) | Categorical | Feature | Drop for modeling, keep for joins/reference |
| team_id | Unique identifier for a team | Categorical | Feature | Potentially useful for joins, not directly for modeling |
| country | Team/Country name (Argentina, Brazil, France, etc.) | Categorical | Feature | Keep |
| team_code | FIFA country code (ARG, BRA, FRA, etc.) | Categorical | Feature | Keep (or use instead of country) |
| confederation_name | Football confederation of the team (UEFA, CONMEBOL, AFC, CAF, CONCACAF, OFC) | Categorical | Feature | Keep |
| region_name | Geographic region of the team | Categorical | Feature | Keep |
| tournament_id | Unique identifier for a World Cup tournament | Categorical | Feature | Possibly drop later; useful for joins |
| tournament_name | World Cup tournament name | Categorical | Feature | Likely redundant with year |
| year | Tournament year | Numerical | Feature | Keep |
| matches_played | Number of matches played in the tournament | Numerical | Feature | Investigate carefully (possible leakage risk) |
| total_goals | Total goals scored by the team in that tournament | Numerical | Target (Regression) | Target |
| stage_reached | Furthest stage reached by the team | Categorical | Target (Classification) | Target |

### Strong Candidate Features

country
team_code
confederation_name
region_name
year

### Likely Redundant Columns

ID
team_id
tournament_id
tournament_name

## External Database Files

### High Priority Investigation

- teams.csv
- matches.csv
- goals.csv
- team_appearances.csv
- tournament_standings.csv
- group_standings.csv

### Purpose

These files are most likely to contain information useful for predicting:

1. total_goals
2. stage_reached

Potential information:

- Historical team performance
- Goals scored and conceded
- Match results
- Tournament progression
- Group-stage performance
- Team experience across World Cups

### teams.csv

Purpose:

- Team metadata lookup table

Potentially Useful Columns:

- team_id
- team_name
- team_code
- region_name
- confederation_name
- confederation_code

Potential Drops:

- key_id
- mens_team
- womens_team
- federation_name
- wikipedia links

Potential Features:

- Confederation
- Region
- Team identity

### team_appearances.csv

Purpose:

- Historical team performance at match level.

Row Definition:

- One row represents one team's appearance in one World Cup match.

Key Columns:

- goals_for
- goals_against
- goal_differential
- result
- win
- lose
- draw
- stage_name

Potential Features:

- Historical win rate
- Historical draw rate
- Historical loss rate
- Average goals scored
- Average goals conceded
- Average goal difference
- Knockout-stage performance

### goals.csv

Purpose:

- Historical goal-level event data.

Row Definition:

- One row represents one goal scored during a World Cup match.

Important Columns:

- team_id
- team_name
- minute_regulation
- minute_stoppage
- match_period
- own_goal
- penalty

Potential Features:

- Goals per match
- Goals by tournament
- Goals by stage
- Penalty goal percentage
- Knockout-stage scoring rate
- Group-stage scoring rate

Priority:

- Medium to High

### tournament_standings.csv

Purpose:

- Historical final rankings for teams in FIFA World Cup tournaments.

Row Definition:

- One row represents a team's final tournament position.

Important Columns:

- tournament_id
- position
- team_id
- team_name
- team_code

Potential Features:

- Best historical finish
- Average finish
- Champion count
- Runner-up count
- Top 4 appearances
- Top 8 appearances

Priority:

- Very High

### group_standings.csv

Purpose:

- Historical group-stage performance data.

Row Definition:

- One row represents a team's final standing in a World Cup group.

Important Columns:

- position
- played
- wins
- draws
- losses
- goals_for
- goals_against
- goal_difference
- points
- advanced

Potential Features:

- Average group position
- Group qualification rate
- Average group points
- Average group wins
- Average group losses
- Average group goals scored
- Average group goals conceded
- Average goal difference

Priority:

- Very High
