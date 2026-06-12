# 💼 Salary Prediction — Linear Regression

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-orange?logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 📌 Project Overview

This project builds **Linear Regression models** to predict employee salary based on personal and professional attributes such as age, education level, job title, and years of experience. A single-feature model and a multiple-feature model are trained and compared, and the better-performing model is saved for reuse.

---

## 📂 Dataset Description

| Property | Details |
|---|---|
| **Source** | [Salary Prediction for Beginners — Kaggle](https://www.kaggle.com/datasets/rkiattisak/salaly-prediction-for-beginer) |
| **Target** | `Salary` |
| **Missing Values** | A few rows with nulls (dropped) |

### Features

| Feature | Type | Description |
|---|---|---|
| `Age` | Numeric | Age of the employee |
| `Gender` | Categorical | Encoded as binary (Male=1, Female=0) |
| `Education Level` | Categorical | Ordinal encoded (High School → PhD) |
| `Job Title` | Categorical | Label encoded (many unique values) |
| `Years of Experience` | Numeric | Total years of work experience |
| `Salary` | Numeric | **Target** — Annual salary (USD) |

---

## 🛠️ Technologies Used

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, manipulation |
| `numpy` | Numerical operations |
| `matplotlib` & `seaborn` | Data visualization |
| `scikit-learn` | Preprocessing, model training, evaluation |
| `joblib` | Model serialization |

---

## 🤖 Model Used

### Linear Regression — Single Feature vs Multiple Features

Two Linear Regression models were trained and compared:

1. **Single Feature Model** — trained using only `Years of Experience`
2. **Multiple Feature Model** — trained using all available features (including engineered features)

**Pipeline:**
1. Drop rows with missing values
2. Encode categorical features (`Gender`, `Education Level`, `Job Title`)
3. Engineer 3 new features
4. Train/test split (80/20)
5. Standardize features (`StandardScaler`)
6. Train both models and compare

**Engineered Features:**

```
Age_Experience_Ratio = Age / (Years of Experience + 1)
Seniority            = Binned Years of Experience (Junior → Executive)
Edu_Exp_Score        = Education Level × Years of Experience
```

---

## 📊 Evaluation Metrics

| Metric | Description |
|---|---|
| **RMSE** | Root Mean Squared Error — penalizes large errors more heavily |
| **R²** | Proportion of variance explained by the model (1.0 = perfect) |

---

## 📈 Results

| Model | RMSE | R² |
|---|---|---|
| **Single Feature (Years of Experience)** | **$15,551.04** | **0.8991** |
| Multiple Features | $15,744.23 | 0.8966 |

**Key observations:**
- `Years of Experience` alone is a very strong predictor of `Salary`, achieving an R² of ~0.90
- Adding more features (`Age`, `Gender`, `Education Level`, `Job Title`, and engineered features) slightly **reduced** performance — likely due to added noise rather than useful signal
- The **Single Feature Model** was selected as the best model and saved
- Example predictions on test samples were within $68–$19,785 of actual salaries, with no systematic bias

---

## 📁 Project Structure

```
salary-prediction/
│
├── Salary_Predict.ipynb     # Main notebook
├── salary_model.pkl         # Saved best model (single feature)
├── salary_scaler.pkl        # Saved scaler
├── requirements.txt         # Dependencies
└── README.md                # Project documentation
```

---

## 👤 Author

**Kishkaya Gayathri**
Bachelor of Science in Information Technology specialized in Artificial Intelligence
[SLIIT] — [2026]
