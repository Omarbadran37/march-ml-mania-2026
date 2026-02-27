# Participant Paths — A, B, and C

There are three paths through this competition. Pick the one that fits where you are right now — you can always do more later.

---

## Path A — The Basketball Fan (Beginner)

**Best for:** Sports fans, bracket fillers, anyone who watches college basketball. You know which teams are overseeded, who has a tough first-round draw, and which conferences have been dominating lately. That knowledge is real signal for predictions.

**Your workflow:** Entirely in plain English. You describe what you want, your AI tool does it, you share results in Slack. Use AI to turn your intuition into data — no coding required. A well-researched paragraph on why a specific team is overseeded is a real, valuable contribution — no notebook required.

**Tools:** Cowork (desktop app) or any AI chat tool in your browser.

**What you'll produce:** Written analysis, charts and tables your AI generates, qualitative team breakdowns. You can even upload CSVs to your AI tool and ask it to analyze them directly.

### Path A — Getting Started Steps

1. Download the Kaggle data files (join the competition, go to Data tab, download)
2. Open Cowork or your AI tool of choice
3. Upload the CSV files directly into the chat
4. Paste Prompt 1 below and start exploring
5. Ask your AI to explain anything you don't understand
6. Screenshot or copy any charts/tables it makes and share in #march-ml-mania

### Path A — Prompts

**Prompt 1 — Understand the data:**
```
I've uploaded the NCAA tournament data from Kaggle. Can you look at the files and give me a plain-English summary of what's in each one? I want to understand: how many years of data there are, what teams are included, and what kind of information I can use to predict tournament winners.
```

**Prompt 2 — Explore seed performance:**
```
Using the tournament results data, can you analyze how often each seed number (1 through 16) wins their first-round game? Show me the win percentages as a table and tell me which seeds are most reliable and which ones are most likely to cause upsets.
```

**Prompt 3 — Tell me a story:**
```
Looking at the last 10 years of NCAA tournament data, which teams have been consistently overseeded or underseeded? Which conferences produce the most first-round upsets? Give me 3–5 interesting findings I could write about.
```

**Prompt 4 — Make predictions:**
```
Based on the historical win rates for each seed matchup, can you create a simple prediction: for every possible first-round game, what probability would you give the higher seed of winning? Explain the Brier Score in basketball terms so I understand what a good score looks like — use specific examples like "if you say Duke wins with 80% confidence and they win, your score for that game is X."
```

**Prompt 5 — Write it up:**
```
Help me write a 200-word post for our Slack channel summarizing what I found. Include one surprising insight about tournament seeding and what I learned about the Brier Score. Keep it conversational, not technical.
```

---

## Path B — The Data Explorer (Intermediate)

**Best for:** Spreadsheet users, SQL folks, analysts, anyone comfortable with data even if not ML.

**Best for:** Comfortable reading data and asking questions of it. You don't need to know how a model works — you just describe what you want and your AI writes the code. You review the output and decide if it makes sense.

**Your workflow:** Use Cowork or an AI coding agent to explore the data, generate Python code, and build a submission. You don't write code from scratch — you describe the goal and iterate on what your AI produces.

**Tools:** Cowork with a script-first workflow, or any AI coding agent.

### Path B — Getting Started Steps

1. Download the Kaggle data files and put them in a folder
2. Ask Cowork to explore the data (Prompts 1–2 below) — this orients both you and your AI
3. Ask your AI to generate a seed-based baseline submission (Prompt 3)
4. Review the output file — does it look like what you expected?
5. Submit to Kaggle, get your Brier Score (~0.210–0.230 is expected for seed baseline)
6. Iterate: submit to Kaggle, note your score, ask your AI what could improve it
7. See the Prediction Strategies reference for upgrade ideas

### Path B — Prompts

**Prompt 1 — Orient yourself:**
```
I have Kaggle March ML Mania data in this folder. Can you look at all the CSV files and give me a summary of each one? Tell me: what years are covered, what columns are in each file, and which files I'll need to make tournament predictions.
```

**Prompt 2 — Find patterns:**
```
Using the tournament seeds and results files, can you analyze: (1) win rate by seed number in round 1, (2) win rate by seed in round 2, and (3) the biggest upsets in the last 10 years by seed differential? Show me the results as tables.
```

**Prompt 3 — Build a baseline submission:**
```
Using historical seed matchup win rates from MTourneyResults.csv and MNCAATourneySeeds.csv, build a submission file. For every possible 2026 game matchup (from the SampleSubmission.csv), predict the probability the lower-numbered team ID wins based on average historical win rates for that seed vs. seed matchup. Output a CSV in the exact format Kaggle expects: columns ID and Pred.
```

**Prompt 4 — Improve it:**
```
My current Brier Score is [X]. The submission uses historical seed win rates. What are the top 3 improvements I could make without writing a complex ML model? For each one, estimate how much it might improve my Brier Score and write the code.
```

**Prompt 5 — Check your work:**
```
Look at the submission file we created. Are there any rows where the probability is outside [0.001, 0.999]? Are there any missing matchups? Does the format exactly match what Kaggle expects?
```

---

## Path C — The Model Builder (Advanced)

**Best for:** Engineers, data scientists, Python or R coders who want to go deep. You want to actually build something — feature engineering, model training, calibration, ensemble blending. Use an AI coding agent as your co-pilot to move faster and explore ideas you might not have tried alone.

**Your workflow:** Iterative model development. Use an AI coding agent to generate code you review and modify — not just run blindly. The prompts below take you from raw data to a competitive submission, then give you clear upgrade paths.

**Tools:** AI coding agent (terminal) or Cowork with a script-first workflow.

### Path C — Getting Started Steps

1. Set up a project folder with your Kaggle CSVs and launch your AI coding agent in that directory
2. Run Prompts 1–2 to explore the data
3. Build a baseline model (Prompt 3)
4. Get your first submission on the leaderboard
5. Iterate on features and models using Prompts 4–6
6. Add probability calibration — this alone can drop your Brier Score significantly
7. See `prediction_strategies.md` for the full model upgrade ladder

### Path C — Prompts

**Prompt 1 — Set up and explore:**
```
I have Kaggle March ML Mania 2026 data in this folder. Set up a Python analysis environment, load the key CSV files (MTeams, MSeasons, MRegularSeasonResults, MTourneyResults, MNCAATourneySeeds), and give me an exploratory data analysis. Show me: data shapes, date ranges, missing values, and 5 interesting statistical patterns in historical tournament performance.
```

**Prompt 2 — Feature engineering:**
```
Using the regular season and tournament data, create a feature engineering pipeline that builds team-level features for the 2026 season. Include: win/loss record, average point differential, strength of schedule (based on opponents' records), seed number, and any other features you think are predictive. Create one row per team.
```

**Prompt 3 — Build a baseline:**
```
Using the features we built, train a logistic regression model to predict tournament game outcomes. Use historical tournament games as training data (with the home team feature engineered as the difference between teams' stats). Evaluate with cross-validation and report the Brier Score on holdout data. Output a submission CSV.
```

**Prompt 4 — Compare and improve:**
```
Compare the new Brier Score from the logistic regression against the seed-baseline. What features have the highest coefficients? Based on the model, which teams are most over/undervalued by their seeds in 2026? Suggest 3 specific feature improvements.
```

**Prompt 5 — Upgrade to gradient boosting:**
```
Replace the logistic regression with an XGBoost model. Use the same features plus any new ones you suggest. Tune hyperparameters with cross-validation. Report Brier Score on holdout data compared to the logistic regression baseline.
```

**Prompt 6 — Calibrate and submit:**
```
Apply Platt scaling (or isotonic regression) to calibrate the XGBoost probability outputs. Show me a reliability diagram (calibration curve) before and after calibration. Report the improvement in Brier Score. Then generate the final submission CSV for Kaggle.
```

**Path C Tip:** The single biggest lever beyond features is **probability calibration** — uncalibrated models get punished heavily by the Brier Score. See `prediction_strategies.md` for the full prediction ladder including ensemble methods.
