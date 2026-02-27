# Competition Overview — March ML Mania 2026

## What is it?

Kaggle March ML Mania is the 12th annual NCAA tournament prediction competition on Kaggle. It's one of the largest and most popular sports prediction contests, with a **$50,000 prize pool** and thousands of participants worldwide.

Your community is running it as an async hackathon — anyone can participate, at any skill level, on their own schedule.

## What you're predicting

Before the tournament begins, you submit a CSV with **probability predictions for every possible game matchup** in both the Men's and Women's NCAA tournaments. For every pair of teams that could theoretically play each other, you predict the probability that Team A beats Team B.

This means you're not just predicting the bracket — you're predicting confidence levels for thousands of possible games, most of which will never happen.

## The scoring metric: Brier Score

The competition uses the **Brier Score** (not log loss). The formula is:

```
Brier Score = (predicted_probability − actual_outcome)²
```

- **actual_outcome** is 1 if the team you're predicting wins, 0 if they lose
- **lower is better**
- Random guessing (50% on everything) = **~0.250**
- Using seed win rates historically = **~0.220–0.230**
- Good community submission = **~0.190–0.210**
- Top 10% = **~0.160–0.175**

**Why does calibration matter?** If you say a team wins with 90% confidence and they lose, you get penalized heavily: (0.90 − 0.0)² = 0.81. The Brier Score rewards honest uncertainty. It's better to say 60% and be right than to say 90% and be wrong.

### Plain-English example

You predict Team A wins with 70% confidence (probability = 0.7).
- If Team A **wins**: score = (0.7 − 1.0)² = **0.09** ✅ good
- If Team A **loses**: score = (0.7 − 0.0)² = **0.49** ❌ ouch

A perfectly calibrated predictor scores near 0. Random guessing scores 0.250.

## Stage 1 vs. Stage 2

**Stage 1** — Predictions due before the tournament starts
- You predict probabilities for ALL possible matchups (even ones that won't happen)
- This tests your ability to estimate team strength across the full field

**Stage 2** — Opens after the bracket is officially announced
- You re-submit predictions for only the actual scheduled games
- Your Stage 1 score and Stage 2 score are combined for the final leaderboard

## The data you'll work with

All data is available for free on Kaggle once you join the competition:

| File | What's in it |
|------|-------------|
| `MTeams.csv` / `WTeams.csv` | Team IDs and names |
| `MSeasons.csv` / `WSeasons.csv` | Season metadata |
| `MRegularSeasonResults.csv` | Every regular season game result |
| `MTourneyResults.csv` | Historical NCAA tournament results |
| `MNCAATourneySeeds.csv` | Seeds for each team each year |
| `MNCAATourneySlots.csv` | Bracket slot structure |
| `SampleSubmission.csv` | Exact format needed for submission |

**Key insight:** The data goes back many years. More historical data = better calibrated probabilities. Seed numbers alone are surprisingly predictive — a #1 seed has beaten a #16 seed in all but a handful of tournament games.

## Submission format

Your submission is a CSV with two columns:
- `ID` — in the format `Season_Team1ID_Team2ID` (lower team ID always goes first)
- `Pred` — your probability that Team 1 wins (a number between 0.001 and 0.999)

Example:
```
ID,Pred
2026_1101_1102,0.72
2026_1101_1103,0.45
...
```

The sample submission file on Kaggle shows you exactly what format is needed.

## Resources

- [Competition page](https://www.kaggle.com/competitions/march-machine-learning-mania-2026)
- [Kaggle Notebooks Docs](https://www.kaggle.com/docs/notebooks)
- [Kaggle API Guide](https://www.kaggle.com/docs/api)
- [Public notebooks from previous years](https://www.kaggle.com/competitions/march-machine-learning-mania-2026/code)
