# 🎓 Student Performance Predictor using Machine Learning

This project predicts **Math scores** of students based on demographic and academic features using a **Lasso Regression model**, implemented in **Google Colab**.

---

## 📌 Project Overview

- 🧠 **Model Used**: Lasso Regression (`alpha = 0.1`)
- ⚙️ **Pipeline**: Includes preprocessing with `OneHotEncoder`, `OrdinalEncoder`, and `StandardScaler`
- 📊 **Performance**:
  - R² Score: **0.8810**
  - RMSE: **5.3818**
  - MAE: **4.1592**
  - Cross-Validated R²: **0.8666**
- 🗂️ **Platform**: Google Colab Notebook

---

## 📁 Dataset

- **Name**: [StudentsPerformance.csv](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)
- **Size**: 1000 rows × 8 columns
- **Target Variable**: `math score`

---

## 🔍 Features Used

- Gender
- Race/Ethnicity
- Parental level of education
- Lunch type
- Test preparation course
- Reading score
- Writing score

---

## 🧪 Machine Learning Flow

1. **Exploratory Data Analysis (EDA)** with `matplotlib` and `seaborn`
2. **Statistical Testing** with ANOVA for feature impact
3. **Preprocessing**:
   - One-hot encode categorical features
   - Ordinal encode education level
   - Standardize numerical features
4. **Model Training & Evaluation**:
   - Train/Test Split (80/20)
   - Pipeline with Lasso Regression
   - Evaluation: MAE, RMSE, R², Cross-Val R²
5. **Prediction**:
   - Save and load the model with `joblib`
   - Accept new user input for prediction

---

## 📈 Evaluation Metrics (Lasso)

| Metric         | Value   |
|----------------|---------|
| R² Score       | **0.8810** |
| Cross-Val R²   | **0.8666** |
| RMSE           | **5.3818** |
| MAE            | **4.1592** |
| MSE            | **28.9638** |

---

## 🚀 Example Prediction

```python
new_data = {
    'gender': ['female'],
    'race/ethnicity': ['group B'],
    'parental level of education': ["bachelor's degree"],
    'lunch': ['standard'],
    'test preparation course': ['completed'],
    'reading score': [88],
    'writing score': [86]
}

# ➤ Predicted Math Score:
#    ➝ 76.13
