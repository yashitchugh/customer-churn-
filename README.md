# 🚀 MISSION CONTROL: Telco Churn Predictor (Production-Grade ML)

> **TUTOR'S NOTE:** Welcome aboard! You are not just building a project; you are building the exact muscle memory required of a Senior Machine Learning Engineer.
>
> This repository is your personal command center. Do not rush—focus on mastery, clean code, and understanding **why** every line is written.

---

# 🧭 The North Star

## 🎯 Goal

Deliver an end-to-end, interpretable **Customer Churn Prediction Web Application** deployed live on the web.

### Why this matters

Tabular classification models power **90% of business AI**.

Mastering:

- Data Wrangling
- Machine Learning Pipelines
- Hyperparameter Tuning
- Model Explainability (SHAP)
- Deployment

...will put you ahead of **95% of candidates** who only build toy Jupyter notebooks.

---

# 📊 PROGRESS DASHBOARD

Update your progress at the start of every session.

- [ ] **Phase 0:** Setup & Environment *(Est. 1–2 Hours)*
- [ ] **Phase 1:** Data Wrangling & EDA *(Est. 4–6 Hours)*
- [ ] **Phase 2:** Preprocessing & Anti-Leakage Pipeline *(Est. 3–4 Hours)*
- [ ] **Phase 3:** XGBoost Modeling & Optuna Tuning *(Est. 5–7 Hours)*
- [ ] **Phase 4:** Model Interpretability (SHAP) *(Est. 2–3 Hours)*
- [ ] **Phase 5:** Streamlit App & Cloud Deployment *(Est. 4–6 Hours)*
- [ ] **Phase 6:** Deep Learning Comparison (ANN) *(Est. 2–3 Hours)*

---

# 🚨 CURRENT ACTIVE PHASE

> **TUTOR DIRECTION:** Start here right now. Complete each item sequentially. Do **not** move to the next phase until every checkbox is completed.

---

# 🟢 Phase 0: The Arsenal (Environment Setup)

**⏱ Estimated Time:** 1–2 Hours

**🎯 Focus:** Build a clean, reproducible development environment.

## 📝 Action Checklist

### [ ] 0.1 Create an isolated Conda environment

```bash
conda create -n ml_course python=3.10 -y
conda activate ml_course
```

### [ ] 0.2 Install project dependencies

```bash
pip install numpy pandas matplotlib seaborn scikit-learn xgboost shap joblib streamlit optuna tensorflow missingno jupyter
```

### [ ] 0.3 Create project structure

```bash
mkdir data notebooks models src
```

### [ ] 0.4 Download Dataset

- Download the **IBM Telco Customer Churn Dataset** from Kaggle.
- Place it inside the **data/** folder.

### [ ] 0.5 Commit Setup

```bash
git add .
git commit -m "Phase 0 Complete: Environment & Repository Structure Setup"
```

---

> 💡 **TUTOR WISDOM**
>
> Isolating your environment early prevents dependency conflicts later.
>
> Treat Git commits like automatic save points in a video game.

---

# 🔵 Phase 1: The Deep Dive (Data Wrangling & EDA)

**⏱ Estimated Time:** 4–6 Hours

**🎯 Focus:** Understand the dataset, clean defects, and extract business insights.

## 📝 Action Checklist

### [ ] 1.1 Launch Jupyter

```bash
jupyter notebook
```

Create:

```
notebooks/01_EDA.ipynb
```

---

### [ ] 1.2 Load Dataset

Inspect using:

```python
.info()
.describe()
.shape
```

---

### [ ] 1.3 Fix Data Defects

- Convert **TotalCharges** to float.
- Fill missing values using the median.

---

### [ ] 1.4 Create Core Visualizations

#### Plot 1

Correlation Heatmap

#### Plot 2

Bar Chart

**Churn % by Contract Type**

#### Plot 3

Boxplot

MonthlyCharges vs Churn

#### Plot 4

KDE / Histogram

Tenure segmented by Churn

#### Plot 5

Pairplot

Key Numerical Features

---

### [ ] 1.5 Notebook Summary

Write a **3-sentence** summary explaining why customers churn.

---

## 🏆 Milestone Gate

Can you explain to a non-technical person why:

- Short-tenure customers
- Month-to-month contracts

have the highest churn?

If yes, proceed.

---

# 🟣 Phase 2: The Fortress (Anti-Leakage Pipelines)

**⏱ Estimated Time:** 3–4 Hours

**🎯 Focus:** Build preprocessing pipelines that eliminate data leakage.

---

## 📝 Action Checklist

### [ ] 2.1 Create

```
notebooks/02_Pipeline.ipynb
```

---

### [ ] 2.2 Split Data

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42,
    stratify=y
)
```

---

### [ ] 2.3 Build ColumnTransformer

### Numerical Pipeline

```
SimpleImputer(strategy="median")
        ↓
StandardScaler()
```

### Categorical Pipeline

```
SimpleImputer(strategy="most_frequent")
        ↓
OneHotEncoder(handle_unknown="ignore")
```

---

### [ ] 2.4 Assemble Pipeline

Use

```python
Pipeline()
```

Then execute

```python
fit_transform(X_train)
```

---

### [ ] 2.5 Test Holdout Data

Run

```python
transform(X_test)
```

Ensure **zero errors**.

---

## 🧠 Mastery Checkpoint

Never call:

```python
fit()
```

or

```python
fit_transform()
```

on test data.

Only call:

```python
transform()
```

---

# 🟠 Phase 3: Heavy Lifting (XGBoost + Optuna)

**⏱ Estimated Time:** 5–7 Hours

**🎯 Focus:** Train powerful models and optimize them.

---

## 📝 Action Checklist

### [ ] 3.1 Create

```
notebooks/03_Modeling.ipynb
```

---

### [ ] 3.2 Train Baselines

- DummyClassifier
- Logistic Regression

---

### [ ] 3.3 Train XGBoost

Integrate

```python
XGBClassifier
```

inside the Scikit-Learn Pipeline.

---

### [ ] 3.4 Hyperparameter Tuning

Use Optuna.

Tune:

- max_depth
- learning_rate
- n_estimators
- subsample

Run

```
100 Trials
```

---

### [ ] 3.5 Retrain Final Model

Use

```python
study.best_params_
```

---

### [ ] 3.6 Evaluation

Generate:

- Confusion Matrix
- ROC Curve

---

### [ ] 3.7 Target

Achieve

```
F1 Score > 0.65
```

If recall is poor:

Adjust

```python
scale_pos_weight
```

---

# 🔴 Phase 4: The "Why" (Interpretability with SHAP)

**⏱ Estimated Time:** 2–3 Hours

**🎯 Focus:** Explain model predictions.

---

## 📝 Action Checklist

### [ ] 4.1 Create

```
notebooks/04_SHAP.ipynb
```

---

### [ ] 4.2 Extract Model

Retrieve the trained XGBoost estimator.

---

### [ ] 4.3 Create Explainer

```python
shap.TreeExplainer()
```

Use a

```
100 sample
```

subset of training data.

---

### [ ] 4.4 Export Plots

Generate

- SHAP Beeswarm Plot
- SHAP Feature Importance Plot

---

### [ ] 4.5 Executive Summary

Write a 3-sentence business interpretation.

---

# 🟡 Phase 5: Streamlit Deployment

**⏱ Estimated Time:** 4–6 Hours

**🎯 Focus:** Build a production-ready web application.

---

## 📝 Action Checklist

### [ ] 5.1 Save Pipeline

```python
joblib.dump(
    pipeline,
    "models/churn_pipeline.joblib"
)
```

---

### [ ] 5.2 Create

```
app.py
```

Include

- Sliders
- Dropdowns
- Raw Feature Inputs

---

### [ ] 5.3 Prediction Flow

```
User Input
      ↓
Pipeline
      ↓
Prediction
      ↓
Probability
```

Display

- 🟢 Low Risk
- 🔴 High Risk

---

### [ ] 5.4 Local Testing

```bash
streamlit run app.py
```

---

### [ ] 5.5 Deployment

- Push to GitHub
- Deploy on Streamlit Community Cloud

---

# ⚪ Phase 6: Deep Learning Comparison (Bonus)

**⏱ Estimated Time:** 2–3 Hours

**🎯 Focus:** Compare ANN vs XGBoost.

---

## 📝 Action Checklist

### [ ] 6.1 Create

```
notebooks/05_DeepLearning.ipynb
```

---

### [ ] 6.2 Build ANN

Architecture

```
Dense
↓
Dropout
↓
Dense
↓
Dropout
↓
Dense(Output)
```

---

### [ ] 6.3 Benchmark

Compare

- F1 Score
- Training Speed
- Deployment Complexity

---

### [ ] 6.4 Conclusion

Explain why tree-based models often outperform deep learning on tabular datasets.

---

# 🧠 MASTERY FLASHCARDS

## fit()

Learns parameters from training data.

Examples

- Mean
- Standard Deviation
- Categories

---

## transform()

Uses learned parameters on unseen data.

---

## fit_transform()

Performs both operations together.

**Never fit on test data.**

---

## Precision

"When the model predicts churn,

how often is it correct?"

---

## Recall

"Out of all customers who churned,

how many did we successfully identify?"

---

## Pipeline Serialization

Save the **entire pipeline**, not just the model.

Reason:

Raw Streamlit inputs must undergo the exact same preprocessing before prediction.

---

# 🐞 DEBUG & ERROR LOG

| Date | Phase | Error Encountered | Resolution |
|------|------|-------------------|------------|
| YYYY-MM-DD | P2 | Unseen category error in test data | Added `handle_unknown="ignore"` to `OneHotEncoder` |

---

# 🔥 TUTOR'S FINAL WORDS

> **"Code isn't written in a single sitting; it's built brick by brick."**
>
> Focus on completing **one phase at a time**.
>
> When bugs appear—and they will—remember that reading stack traces and fixing errors is where real learning happens.
>
> **You've got this. 🚀**
