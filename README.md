# PS4 Game Analytics & Player-Type Based Recommendation (Bartle Achievers)

This repository contains my final project for the **Istanbul Technical University (ITU) Big Data & Business Analytics Certification Program**.

The project focuses on **PS4 games analytics** using a real-world dataset and explores how game metrics relate to player motivations, specifically the **"Achiever"** player type from Bartle’s taxonomy.

---

## 1. Business Context

The dataset includes PlayStation 4 games and key engagement/performance metrics (scores, completion rates, ratings, time to complete, etc.).  
The goal of this project is to:

- Understand which factors drive **game popularity (rating)**.
- Explore how **trophy/score structure** may appeal to **Achiever-type players**.
- Build simple **predictive and classification models** that could support:
  - Game recommendation,
  - Player segmentation,
  - Long-term engagement and monetization strategies.

---

## 2. Dataset

Source: [Kaggle – PS4 Games Dataset](https://www.kaggle.com/datasets/ww1234/ps4-games)

- **Rows:** 1,584
- **Columns:** 9
- Example fields:
  - `title` – Game name  
  - `score` – Maximum achievable score / trophies  
  - `leaderboard` – Number of players on the leaderboard  
  - `gamers` – Number of registered players  
  - `comp_perc` – Completion percentage  
  - `rating` – Popularity rating  
  - `min_comp_time`, `max_comp_time` – Estimated time to fully complete the game  

No missing values were reported in the original dataset.

---

## 3. Methods & Tools

The original analysis was performed using **KNIME Analytics Platform**, with the following main steps:

1. **Descriptive Analytics & EDA**
   - Summary statistics
   - Histograms and boxplots
   - Correlation analysis and scatter matrices

2. **Feature Understanding**
   - Relationship between `rating` and other variables
   - Relationship between `score`, `leaderboard`, and `comp_perc`

3. **Modeling (Machine Learning)**  
   Three models were built:

   - **Linear Regression**
     - Target: `rating`
     - Goal: Identify which variables best explain game popularity.

   - **Logistic Regression**
     - Target: Player-type related classification (Achiever-focused)
     - Goal: Classify games as more/less suitable for Achiever-type players.

   - **Decision Tree**
     - Same classification task as Logistic Regression
     - Optimized using **Forward Feature Selection**.

4. **Model Evaluation**
   - Regression: MSE, MAE, R²
   - Classification: Accuracy  
   - Cross-validation (K-Fold) used for more robust evaluation.

5. **Player Typology**
   - The project is grounded in **Bartle’s player types** (Achievers, Explorers, Socializers, Killers).
   - The focus is on **Achievers**, who are highly motivated by trophies, progress bars, and completion challenges.

---

## 4. Key Insights (High Level)

- Strong positive correlation between **score** and **leaderboard**:
  - Games with more trophies/scores tend to have more players on the leaderboard.

- Negative relationship between **score** and **completion percentage**:
  - As maximum score / trophies increase, completion percentage tends to decrease.
  - This suggests a trade-off between **depth/complexity** and **full completion**.

- Decision Tree model performed best among the classification models in this setup, making it a practical choice for:
  - Recommending games to Achiever-type players,
  - Identifying segments likely to respond well to achievement-heavy design.

---

## 5. Tech Stack

- **KNIME Analytics Platform**
  - Data import and cleaning  
  - EDA and visualization  
  - Linear Regression, Logistic Regression, Decision Tree  
  - K-Fold Cross Validation  
  - Forward Feature Selection

- **In Progress (Planned / Ongoing):**
  - Rebuilding core parts of this workflow in **Python (pandas, scikit-learn)** as part of:
    - **YÖK Data Analysis School** modules:
      - *Descriptive & Inferential Statistics*
      - *Machine Learning & AI Fundamentals*

---

## 6. Next Steps

- Add a **Python notebook** version of:
  - Basic EDA on the PS4 dataset
  - One regression model (rating prediction)
  - One simple classification model (Achiever-friendly vs non-Achiever-oriented games)

- Extend the recommendation logic to include:
  - Player retention metrics
  - Monetization KPIs (e.g., LTV, ARPDAU) on suitable datasets.

---

## 7. About Me

I am a **Junior Data Analyst** with a background in **Physics, Mathematics, and Education**, transitioning from teaching and EdTech into **product, game, and behavioral analytics**.

- Email: **dekbenli@gmail.com**  
- LinkedIn: [Dalida Dikici](https://www.linkedin.com/in/dalida-dikici/)  
- Location: Kuşadası, Türkiye

