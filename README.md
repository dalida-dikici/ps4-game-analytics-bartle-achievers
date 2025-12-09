# PS4 Game Analytics & Player-Type Based Recommendation

This repository contains a game analytics project completed as the final project of the **Big Data & Business Analytics** certificate program at Istanbul Technical University (İTÜ).

The project focuses on understanding **player behavior and game popularity** using a real-world PlayStation 4 games dataset and building **predictive and classification models** to support game recommendation scenarios.

---

## 🎯 Project Objectives

- Analyze a PS4 games dataset from the [TrueTrophies](https://truetrophies.com/) website (via Kaggle).
- Understand which features drive **game ratings** and **popularity**.
- Classify games based on their suitability for **"Achiever" player type** (Bartle’s taxonomy).
- Compare different models and translate the results into **business-oriented recommendations** (player retention, personalized game suggestions).

---

## 📊 Dataset

- **Source:** [Kaggle – PS4 Games Dataset](https://www.kaggle.com/datasets/ww1234/ps4-games)
- **Size:** 1,584 rows, 9 columns  
- **Context:** PS4 games collected from the TrueTrophies website  
- **Examples of features:**
  - `rating` – overall game rating
  - `score` – trophy/achievement score
  - `comp-perc` – completion percentage
  - `leaderboard` – ranking-related metrics
  - Various trophy-related statistics

> **Note:** The raw dataset is not redistributed in this repository due to licensing.  
> You can download it directly from Kaggle using the link above.

---

## 🔍 Methods & Workflow

The analysis was performed using **KNIME Analytics Platform** with a customer/behavioral analytics perspective.

### 1. Exploratory Data Analysis (EDA)

- Loaded the CSV dataset into KNIME.
- Verified **missing values** (none in this dataset).
- Generated basic **descriptive statistics** (`mean`, `median`, `std`, histograms).
- Used:
  - `Statistics` node for summary stats
  - `Linear Correlation` to inspect relationships between variables
  - `Scatter Matrix` to visualize pairwise relationships
  - `Box Plot` (focused on `rating` distribution)

Key insight:  
- Positive correlation between **`score`** and **`leaderboard`**  
- Negative correlation between **`score`** and **`comp-perc`**  
  → As players collect more trophies, the completion rate tends to drop.

### 2. Problem Definition

The project is framed around:

- **Game popularity modeling** (via `rating`)
- **Player-type–based game recommendation**, focusing on the **Achiever** type from **Bartle’s player taxonomy**.

Using literature on player types and motivation, the project connects data patterns with:

- Achievers (motivated by trophies/progression)
- Other player types (Explorers, Socializers, Killers – considered for future work)

---

## 🤖 Models

Three main models were built and compared.

### 1️⃣ Linear Regression – Predicting Game Rating

- **Target:** `rating`
- **Goal:** Find which features best explain game rating.
- **Process:**
  - Train–test split (e.g. ~76% training, ~24% test)
  - Used KNIME’s `Linear Regression Learner` and `Linear Regression Predictor`.
- **Evaluation Metrics:**
  - Mean Squared Error (MSE)
  - Mean Absolute Error (MAE)
  - R² (coefficient of determination)

### 2️⃣ Logistic Regression – Classifying “Achiever-Friendly” Games

- **Target:** Newly engineered categorical variable representing **Achiever suitability**.
- **Feature Engineering:**
  - `Rule Engine` used to transform the `score` variable into a categorical `Bartle Player`–like label based on histogram and thresholds.
- **Learning Process:**
  - **K-Fold Cross Validation** (k=5) for more robust performance estimation.
  - **Forward Feature Selection** meta-node to find the best subset of features.
- **Output:**
  - A probabilistic classification of whether a game is likely to appeal to Achiever-type players.

### 3️⃣ Decision Tree – Achiever Classification (Best Performing Model)

- Same target as Logistic Regression (Achiever vs. Non-Achiever).
- Used:
  - `Partitioning` (e.g. 80% train / 20% test)
  - Decision Tree learner node in KNIME.
- **Result:**  
  - Achieved the best **classification performance** among the three models.
  - Offered interpretable rules (e.g. threshold-based splits on score and completion metrics).

---

## 📏 Model Evaluation

Models were compared using:

- **Regression:** MSE, MAE, R²  
- **Classification:** Accuracy and validation performance

> Overall, the **Decision Tree classifier** delivered the strongest performance for the Achiever classification task, while Linear Regression provided interpretable insights into rating drivers.

---

## 💡 Business & Analytics Insights

From a **customer / player analytics** perspective:

- Games with high trophy scores but low completion rates may be particularly attractive to **Achievers**, who are motivated by collecting difficult trophies.
- A rule-based or ML-based recommendation system can:
  - Suggest Achiever-friendly games to players with matching behavior patterns,
  - Re-target players in segments where the model predicts a high probability of interest.

**Long-term possibilities:**

- Building a **popularity-based recommendation system** using predicted ratings.
- Expanding player segmentation beyond Achievers and incorporating other Bartle types.
- Integrating behavioral logs or time-based activity data if available.

---

## 🛠 Tech Stack

- **Tools:** KNIME Analytics Platform  
- **Techniques:**
  - Exploratory Data Analysis (EDA)
  - Linear Regression
  - Logistic Regression
  - Decision Trees
  - K-Fold Cross Validation
  - Forward Feature Selection
- **Domain:** Game analytics, customer analytics, player behavior, recommendation logic

---

## 📂 Repository Structure (Planned)

```text
ps4-game-analytics-bartle-achievers/
├── README.md
├── presentation/
│   └── ITU_BigData_PS4_Game_Analytics_DalidaDikici.pdf
├── data/
│   └── README_DATA.md  # Notes + Kaggle link
├── notebooks/          # (optional) Jupyter notebooks for future work
└── knime/              # (optional) KNIME workflow file (.knwf)

