# Student Score Predictor

This project builds **individual machine learning models** to predict **student performance scores** — specifically:

- `math score`
- `reading score`
- `writing score`

Each target is modeled **separately** using a range of regression algorithms, with **Optuna-based hyperparameter tuning**, and the best-performing models are saved.

---
## Dataset Used: StudentsPerformance.csv

This dataset contains exam scores and demographic data for high school students. It is used to analyze how various factors influence student performance in three core subjects:

- Math
- Reading
- Writing

Each row represents a single student.

---

## Source

- **Original Dataset**: [Kaggle - Students Performance in Exams](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams)
- **File Name**: `StudentsPerformance.csv`

---

## Columns and Description

| Column                    | Description |
|---------------------------|-------------|
| `gender`                  | Student gender (male/female) |
| `race/ethnicity`          | Group classification (A–E) |
| `parental level of education` | Highest level of education achieved by parent |
| `lunch`                   | Type of lunch received (standard or free/reduced) |
| `test preparation course` | Whether the student completed a test prep course |
| `math score`              | Score in math exam (0–100) |
| `reading score`           | Score in reading exam (0–100) |
| `writing score`           | Score in writing exam (0–100) |

---

## Usage in This Project

This dataset is used to:

- Predict individual subject scores (Math, Reading, Writing) based on personal and academic attributes.
- Train separate ML models for each score.
- Analyze correlations between demographic features and academic outcomes.

---

##  Features

- Load and preprocess CSV dataset
- Basic exploratory data analysis (EDA)
- Encoding of categorical features using One-Hot Encoding
- Feature scaling using `StandardScaler`
- Split dataset into training and testing sets
- Use Optuna for hyperparameter tuning on multiple regression models:
  - Lasso
  - Ridge
  - Decision Tree
  - Random Forest
  - SVR
  - Gradient Boosting
  - XGBoost
- Evaluate models using multiple metrics:
  - R² Score
  - Cross-Validation R²
  - RMSE, MAE, MSE, Max Error
- Save:
  - Best models for each target variable using `joblib`
  - CSV files for all model performances
  - CSV file for best-performing models

---
# Installation Guide for Student Score Predictor

This guide will help you set up the environment for running the **Student Score Predictor** project on your local machine or cloud environment.

---

## Step 1: Clone the GitHub Repository

Make sure you have `git` installed. Then, run:
```bash
git clone https://github.com/KavyaJain1206/Student-score-predictor.git
cd Student-score-predictor
```
---

## Step 2: Create a Virtual Environment (Optional but Recommended)

**Using Python's built-in venv:**

**For Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**For macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```
---

## Step 3: Install Dependencies

Use the provided `requirements.txt` to install all necessary libraries:
```bash
pip install -r requirements.txt
```
This installs the following key packages:

- pandas  
- numpy  
- scikit-learn  
- xgboost  
- optuna  
- joblib  
- matplotlib  
- seaborn  
- notebook  

---

## Step 4: Run the Jupyter Notebook

Launch the notebook interface:

```bash
jupyter notebook
```
Open `student_score_pipeline.ipynb`

---

## Step 5 (Optional): Run with Google Colab

If you prefer using Google Colab:

1. **Upload all necessary files:** notebook, dataset, and `requirements.txt` (if needed).
2. **Run the notebook in the Colab environment.**
3. **Install missing packages in the first notebook cell if necessary:**
```bash
!pip install optuna xgboost joblib matplotlib seaborn
```
---

- Results and configurations are stored in:
- `all_models_results.csv`: All model trials and metrics
- `saved_best_models_info.csv`: Only the best models and their details

---

## Prediction Pipeline

Each saved model includes:
- StandardScaler
- Trained ML model
- Encoding steps matched to training

To load and predict from a saved model:

```python
import pandas as pd
import joblib

# --- Load model ---
pipeline = joblib.load("best_saved_models/math_score_Lasso.pkl")

# --- Prepare input ---
input_data = pd.DataFrame([{
  'gender': 'female',
  'race/ethnicity': 'group B',
  'lunch': 'standard',
  'test preparation course': 'completed',
  'parental level of education': "bachelor's degree",
  'reading score': 75,
  'writing score': 72
}])

# Apply same ordinal encoding and one-hot encoding as in training
# (Refer to the prediction script for full preprocessing steps)

# --- Predict ---
predicted_score = pipeline.predict(input_encoded)[0]
print(f"Predicted Math Score: {predicted_score:.2f}")

