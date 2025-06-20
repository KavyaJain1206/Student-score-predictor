# Student Score Predictor

This project builds **individual machine learning models** to predict **student performance scores** — specifically:

- `math score`
- `reading score`
- `writing score`

Each target is modeled **separately** using a range of regression algorithms, with **Optuna-based hyperparameter tuning**, and the best-performing models are saved.

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

##  Project Structure

```bash
Student-score-predictor/
│
├── models/
│   ├── math_score_model.pkl
│   ├── reading_score_model.pkl
│   └── writing_score_model.pkl
│
├── data/
│   └── StudentsPerformance.csv
│
├── notebooks/
│   └── student_score_pipeline.ipynb
│
├── outputs/
│   ├── all_models_results.csv
│   └── best_models_summary.csv
│
├── README.md
├── requirements.txt
└── create_virtualenv.md

```
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
