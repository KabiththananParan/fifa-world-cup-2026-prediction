# Challenge Analysis

## Problem Statement

-> predict the total number of goals each team will score during the FIFA World Cup 2026.
-> predict the stage at which each team will finish the tournament (Group Stage, Round of 32, Round of 16, Quarter-finals, Semi-finals, Runner-up, or Champion).

## Target

1. Total no of goals 

- Number of goals scored by a team during FIFA World Cup 2026

2. Stage of the team

- Group Stage (group)
- Round of 32 (roundof32)
- Round of 16 (roundof16)
- Quarter-finals (qf)
- Semi-finals (sf)
- Runner-up (runnerup)
- Champion (champion)

## Evaluation Metrics

1. Goals prediction metric (60%) - The Goals prediction task will be evaluated using Root Mean Squared Error (RMSE) between the predicted and actual number of goals scored by each team during the FIFA World Cup 2026. Lower RMSE values indicate better performance.

- Regression problem
- Metric: RMSE
- Lower is better

2. Stage prediction metric (40%) - The Stage Reached prediction task will be evaluated using F1 Score.
Higher F1 scores indicate better performance.

- Multi-class Classification problem
- Metric: F1 Score
- Higher is better

Overall Score = 0.60 × RMSE(Goals) + 0.40 × F1(Stage)

## Allowed Data

FIFA Men's World Cup tournaments from the Fjelstul World Cup Database

## Constraints

10 submissions per day
70 submissions for this challenge

## Initial Ideas

- Historical goals scored
- Historical goals conceded
- Number of World Cup appearances
- Best tournament finish
- Average tournament finish
- Recent World Cup performance
- Goal difference trends
- Team experience
- Historical knockout-stage performance