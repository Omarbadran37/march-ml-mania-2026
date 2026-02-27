# Kaggle Setup Guide

Two ways to run your Kaggle notebook. Both work — choose based on your comfort level.

---

## Option 1 — Browser Notebook (Beginner-friendly)

No installation required. Everything runs in your browser.

1. Go to [kaggle.com/competitions/march-machine-learning-mania-2026](https://www.kaggle.com/competitions/march-machine-learning-mania-2026)
2. Click **Data** tab → Download the CSV files to your computer
3. Click **Code** tab → **New Notebook**
4. In the notebook, add the competition data: **+ Add Data** → search for "March ML Mania 2026"
5. Write or paste your code in the notebook cells
6. Click **Run All** (or Shift+Enter cell by cell)
7. When ready to submit: **Save Version** → **Save & Run All** → go to **Output** tab → **Submit to Competition**

**Tip:** The competition has starter notebooks in the Code tab — look for "Starter Notebook" to see a working example.

---

## Option 2 — Kaggle API (for AI coding agent workflow)

The Kaggle API lets you push notebooks from your computer to Kaggle's cloud and run them remotely — all from the command line or from within your AI coding agent. This is useful when you're iterating quickly and want to keep your code in a local folder.

### One-time setup

**Step 1 — Get your API token:**
Go to [kaggle.com](https://www.kaggle.com) → Account → API section → **Create New API Token**. This downloads `kaggle.json`.

**Step 2 — Place your token:**
Move `kaggle.json` to `~/.kaggle/kaggle.json` (create the `.kaggle` folder if it doesn't exist). On Mac/Linux:
```bash
mkdir -p ~/.kaggle
mv ~/Downloads/kaggle.json ~/.kaggle/kaggle.json
chmod 600 ~/.kaggle/kaggle.json
```

**Step 3 — Install the Kaggle package:**
Run this once in your terminal. If you're using an AI coding agent, just tell it: "Install the kaggle Python package."
```bash
pip install kaggle
```

### Download the competition data

```bash
kaggle competitions download -c march-machine-learning-mania-2026
unzip march-machine-learning-mania-2026.zip -d ./data
```

### Push and run a notebook

Create a `kernel-metadata.json` file in your project folder:
```json
{
  "id": "yourusername/march-ml-mania-2026",
  "title": "March ML Mania 2026",
  "code_file": "notebook.ipynb",
  "language": "python",
  "kernel_type": "notebook",
  "is_private": true,
  "enable_gpu": false,
  "enable_internet": false,
  "dataset_sources": [],
  "competition_sources": ["march-machine-learning-mania-2026"],
  "kernel_sources": []
}
```

Then use these three commands:

| Command | What it does |
|---------|-------------|
| `kaggle kernels push -p .` | Upload and run your notebook on Kaggle |
| `kaggle kernels status yourusername/march-ml-mania-2026` | Check if it's still running |
| `kaggle kernels output yourusername/march-ml-mania-2026 -p ./output` | Download the output files |

### Using an AI coding agent to automate this

If you're using an AI coding agent, you can skip the terminal commands entirely and just describe what you want in plain English. Your coding agent handles the Kaggle API calls for you.

**Prompt for full automation:**
```
I want to automate my Kaggle workflow. Set up the kaggle Python package, download the March ML Mania 2026 competition data, create a kernel-metadata.json for my notebook, push it to Kaggle, check its status until it finishes, and download the output. My Kaggle username is [your_username]. Walk me through each step.
```

**Prompt to push after changes:**
```
I've updated my notebook.ipynb with new features. Push it to Kaggle using the API, wait for it to finish, download the output, and show me the submission file's first 10 rows and probability distribution.
```

**Prompt to check status:**
```
Check the status of my Kaggle kernel [yourusername/march-ml-mania-2026] and let me know when it's done running. Once it's complete, download the output files.
```

**Prompt to submit:**
```
My submission.csv is ready. Submit it to the March ML Mania 2026 competition using the Kaggle API and tell me my score.
```

---

## Which option should I use?

| | Option 1 (Browser) | Option 2 (API) |
|--|---------------------|----------------|
| **Setup time** | 0 minutes | 15–30 minutes |
| **Best for** | Beginners, one-off exploration | Iterating quickly, Path C |
| **Requires** | Just a Kaggle account | Kaggle account + API token |
| **AI coding agent friendly** | Less so | Yes — great pairing |
| **Result** | Same submission | Same submission |

Both options produce the same result — a submission file on the Kaggle leaderboard.

---

## Useful links

- [Kaggle Notebooks Documentation](https://www.kaggle.com/docs/notebooks)
- [Kaggle API Documentation](https://www.kaggle.com/docs/api)
- [Competition page](https://www.kaggle.com/competitions/march-machine-learning-mania-2026)
- [Starter notebooks (community)](https://www.kaggle.com/competitions/march-machine-learning-mania-2026/code)
