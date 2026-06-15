# Feature Engineering Pipeline

## Objective

Create a reusable feature engineering pipeline that transforms historical FIFA World Cup data into team-level features for predicting:

1. Total goals scored during FIFA World Cup 2026 (`total_goals`)
2. Tournament stage reached (`stage_reached`)

---

# Pipeline Overview

Raw Historical Data

* teams.csv
* team_appearances.csv
* tournament_standings.csv
* group_standings.csv
* goals.csv

↓

Feature Generation

↓

Master Feature Table

↓

Train/Test Dataset Creation

↓

Model Training

↓

Predictions

---

# Data Flow

teams.csv
│
├── Team Identity Features
│
team_appearances.csv
│
├── Historical Performance Features
│
tournament_standings.csv
│
├── Tournament Success Features
│
group_standings.csv
│
├── Group Stage Features
│
goals.csv
│
├── Goal Scoring Features
│
▼

master_features.csv

▼

Train.csv + master_features.csv
│
▼

train_features.csv

▼

Test.csv + master_features.csv
│
▼

test_features.csv

---

# Step 1: Team Identity Features

Input:

* teams.csv

Purpose:

Generate metadata about each team.

Output:

team_identity_features.csv

Features:

* team_id
* team_name
* team_code
* confederation_name
* confederation_code
* region_name

Expected Usage:

Provide categorical information describing each team.

---

# Step 2: Historical Performance Features

Input:

* team_appearances.csv

Purpose:

Measure historical team strength.

Output:

historical_performance_features.csv

Features:

* total_matches_played
* total_wins
* total_draws
* total_losses

Derived Features:

* historical_win_rate
* historical_draw_rate
* historical_loss_rate

Goal Features:

* total_goals_scored
* total_goals_conceded
* avg_goals_scored
* avg_goals_conceded
* avg_goal_difference

Expected Usage:

Capture long-term team performance.

---

# Step 3: Tournament Success Features

Input:

* tournament_standings.csv

Purpose:

Measure historical World Cup success.

Output:

tournament_success_features.csv

Features:

* best_finish
* avg_finish

Achievement Features:

* champion_count
* runnerup_count
* top4_count
* top8_count

Experience Features:

* total_tournaments_played

Expected Usage:

Capture historical tournament pedigree.

---

# Step 4: Group Stage Features

Input:

* group_standings.csv

Purpose:

Measure historical group-stage performance.

Output:

group_stage_features.csv

Features:

* avg_group_position
* avg_group_points
* avg_group_wins
* avg_group_draws
* avg_group_losses

Goal Features:

* avg_group_goals_for
* avg_group_goals_against
* avg_group_goal_difference

Qualification Features:

* group_qualification_rate

Expected Usage:

Capture consistency in reaching knockout stages.

---

# Step 5: Goal Scoring Features

Input:

* goals.csv

Purpose:

Measure historical scoring patterns.

Output:

goal_scoring_features.csv

Features:

* total_goals
* goals_per_match
* group_stage_goals
* knockout_stage_goals

Advanced Features:

* penalty_goal_percentage
* own_goal_percentage

Expected Usage:

Capture offensive tendencies.

---

# Step 6: Master Feature Generation

Inputs:

* team_identity_features.csv
* historical_performance_features.csv
* tournament_success_features.csv
* group_stage_features.csv
* goal_scoring_features.csv

Output:

master_features.csv

Purpose:

Create one feature table containing all engineered features for each team.

Expected Structure:

One row per team.

Example:

Brazil
Argentina
France
Germany

etc.

---

# Step 7: Training Dataset Builder

Inputs:

* Train.csv
* master_features.csv

Output:

train_features.csv

Purpose:

Attach engineered features to the competition training data.

Result:

Ready for model training.

---

# Step 8: Test Dataset Builder

Inputs:

* Test.csv
* master_features.csv

Output:

test_features.csv

Purpose:

Attach engineered features to the competition test data.

Result:

Ready for prediction.

---

# Expected Outputs

Generated Files

data/processed/

* team_identity_features.csv
* historical_performance_features.csv
* tournament_success_features.csv
* group_stage_features.csv
* goal_scoring_features.csv
* master_features.csv
* train_features.csv
* test_features.csv

---

# Version 1 Feature Set

Initial Feature Categories

1. Team Identity Features
2. Historical Performance Features
3. Tournament Success Features
4. Group Stage Features
5. Goal Scoring Features

Estimated Feature Count:

15–30 features

Purpose:

Establish a strong baseline before experimenting with advanced feature engineering.

---

# Guiding Principle

Focus on:

* Historical team quality
* Historical scoring ability
* Historical tournament success
* Historical group-stage performance

Avoid:

* Player-level features
* Referee features
* Stadium features
* Manager features

until a strong baseline has been established.
