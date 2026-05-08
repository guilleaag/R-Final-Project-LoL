# League of Legends Match Dataset Analysis
**Author:** Guillermo Arcila  
**Date:** May 2026  
**Tool:** R / R Markdown

---

## Overview

This project analyzes a publicly available League of Legends match dataset sourced from Kaggle. The goal is to use R to explore player performance, identify patterns across roles and champions, and test whether certain in-game metrics (like damage dealt) are statistically linked to winning.

---

## Dataset

- **Source:** Kaggle — League of Legends Match Dataset
- **File:** `league_data.csv`
- **Content:** Individual player match records including kills, deaths, assists, gold earned, damage dealt, role, champion, and match outcome.

---

## Project Structure

Final-Project.Rmd       # Main R Markdown analysis file
league_data.csv         # Raw dataset
README.md               # This file
gold_damage_chart.png   # Visualization 1
win_loss_chart.png      # Visualization 2
role_pie_chart.png      # Visualization 3
damage_type_chart.png   # Visualization 4

---

## Data Cleaning

The raw dataset was cleaned by:
- Filtering to only `CLASSIC` game mode matches
- Removing duplicate rows
- Removing rows with missing `win` values
- Removing players with `Invalid` position
- Dropping the `game_version` column
- Filling missing summoner names with generated placeholders
- Converting `win` to logical, creating `win_numeric`, `game_duration_min`, and `kda` columns

---

## Data Manipulation

Key manipulations performed using `dplyr`:
- **Grouped summaries** by role: win rate, kills, deaths, assists, damage, gold
- **Filtering** by win/loss to compare KDA across outcomes
- **Mutating** to create new variables (KDA, win numeric, game duration in minutes)
- **Arranging** results by win rate and KDA
- **Selecting** relevant columns for analysis

---

## Statistical Analysis

### Descriptive Statistics
- Average game duration: **28.44 minutes**
- Average games played per day: **408.11**
- Longest game and shortest game duration calculated
- Average KDA computed per role for both winners and losers

### Hypothesis Test (t-test)
- **Null Hypothesis:** Winning and losing players deal the same average damage.
- **Alternative Hypothesis:** Winning and losing players deal different average damage.
- **Result:** The p-value was less than 0.05, so the null hypothesis was rejected. Winning players deal significantly more damage on average.

### Linear Regression
- **Model:** `gold_earned ~ total_damage_dealt_to_champions`
- **Result:** Strong positive relationship. R-squared ≈ 0.72, meaning ~72% of variation in gold earned is explained by champion damage. The relationshi
