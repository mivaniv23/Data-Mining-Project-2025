# 🎾 Tennis Match Winner Prediction

This project uses **PyCaret** to predict tennis match winners using player statistics, rankings, and betting odds. The goal is to evaluate different machine learning models and select the most accurate one for classifying the winning player from historical ATP data.

---

## 📊 Dataset Overview

The dataset includes ATP singles match data. The `Winner` column represents the actual match winner.

**Top 20 Most Frequent Winners:**

| Player         | Wins |
|----------------|------|
| Federer R.     | 1151 |
| Djokovic N.    | 1032 |
| Nadal R.       | 1007 |
| Ferrer D.      | 677  |
| Murray A.      | 670  |
| ...            | ...  |
| Dimitrov G.    | 439  |

---

## ⚙️ Models Compared

| Model                  | Accuracy | AUC    | F1 Score |
|------------------------|----------|--------|----------|
| 🎯 Random Forest       | **0.3271** | **0.8461** | 0.3254   |
| 🌲 Decision Tree        | 0.3160   | 0.6391 | 0.3156   |
| 🧠 Naive Bayes          | 0.1703   | 0.7414 | 0.1365   |
| ➕ Logistic Regression  | 0.1201   | 0.0000 | 0.0758   |

> ✅ **Random Forest Classifier** achieved the best overall performance.

---

## 🧪 Final Model Evaluation

### Random Forest (cross-validation):
| Metric     | Score  |
|------------|--------|
| Accuracy   | **0.3218** |
| AUC        | 0.8459 |
| F1 Score   | 0.3221 |
| Recall     | 0.3218 |

Sample predictions:

| Winner       | Predicted | Confidence |
|--------------|-----------|------------|
| Youzhny M.   | Lopez F.  | 26%        |
| Hewitt L.    | Roddick A.| 70%        |
| Djokovic N.  | Djokovic N.| 90%       |

---

## 🔧 Hyperparameter Tuning

Tuned models were tested, but **original Random Forest** performed better.

| Metric     | Before Tuning | After Tuning |
|------------|----------------|---------------|
| Accuracy   | 0.3271         | **0.7647** *(overfitting likely due to data leak or leakage in setup)* |
| AUC        | 0.8461         | 0.9739        |
| F1 Score   | 0.3254         | 0.7628        |

> 📌 *Note: Although tuning boosted metrics, PyCaret automatically reverted to the better-performing original model.*

---

## 📌 Key Insights

- **Feature Importance:** PyCaret heavily favored `player_1` and `player_2` as features, but analysis shows that **Rank, Points, and Betting Odds** have stronger predictive power.
- **Class Imbalance:** Players like Federer, Djokovic, and Nadal dominate the dataset, which could bias predictions.
- **Model Generalization:** Accuracy was limited (~32%) due to the high number of unique target classes (many different players).

---

## 💡 What I Learned

This project taught me how to:
- Use PyCaret for classification workflows.
- Compare models and tune hyperparameters.
- Evaluate results and investigate why some features dominate.
- Understand the limits of accuracy when predicting from many possible classes.

Future improvements might include:
- Framing the problem as "Who will win between these two players?" instead of multiclass classification.
- Using engineered features like recent win streak, surface preference, or player fatigue.

---

