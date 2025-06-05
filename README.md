# NFL Fan Sentiment Tracker

## Introduction

This project uses HTTPX and Parsel to scrape through all of the post-game threads of every NFL team subreddit during the 2024-25 season. Each comment is run through [VADER (Valence Aware Dictionary and sEntiment Reasoner)](https://github.com/cjhutto/vaderSentiment) and classified as positive, neutral, or negative. The percentage of positive comments is then assigned to the corresponding post-game thread to quantify fan sentiment.

This fan sentiment is analyzed alongside other values such as:
- Final game result (win/loss)
- Score differential (victory margin)
- Opponent team
- Week of the season

The goal is to identify trends in how fans react to different types of wins and losses, such as blowouts, close games, or upsets.


---

## Results

>  **For more in-depth results and analysis, please refer to the included PDF file in the repository.**

- **Win Margin & Sentiment Correlation:** There is a strong correlation between game outcomes and fan sentiment — especially with larger margins of victory generating more positive reactions.
- **Home Advantage Influence:** Slight correlation observed between playing at home and positive fan sentiment, even in close games.
- **Expectation vs. Outcome:** Some games defy typical trends — for example, wins with low sentiment or losses with high sentiment. These cases are usually driven by fan expectations (e.g. underperformance despite a win, or moral victories in a hard-fought loss) or external factors such as key injuries or controversial calls.

![image](https://github.com/user-attachments/assets/8a0dbebb-6979-4dfa-b3f6-6919fb007336)
![image](https://github.com/user-attachments/assets/c5f46a79-c1ad-46d3-9c30-2e6737153a05)
![image](https://github.com/user-attachments/assets/3a1dcfbd-a83e-4efc-857b-7a5f51a3360e)


---

## 🛠️ How to Use

First, install the necessary libraries.

1. **`FetchandBuildData.ipynb`**  
   This notebook performs the following:
   - Reads the input file: `NFL 2024-25 Subreddit - Sheet1.csv`.
   - Scrapes each Reddit post URL to extract comments and calculates the **positive sentiment ratio** using [VADER](https://github.com/cjhutto/vaderSentiment).
   - Stores the intermediate results in `team_week_sentiment_long.csv`.

   >  **Note:** Due to rate limits, scraping might occasionally fail. Simply rerun the notebook — it will pick up where it left off and continue updating the CSV.

   - Finally, it merges all available data into a single file: `NFL 2024-25 Full.csv`.  
   - You can also use this notebook to inspect sentiment results for individual post URLs.

2. **`DataAnalysis.ipynb`**  
   This notebook loads `NFL 2024-25 Full.csv` and:
   - Encodes and processes relevant columns for analysis.
   - Performs exploratory analysis on sentiment trends, correlations with wins, margins, home/away games, etc.
