# Customer Churn Analysis Pipeline

[![Python](https://img.shields.io/badge/python-v3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.68+-00a393.svg)](https://fastapi.tiangolo.com/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange.svg)](https://scikit-learn.org/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

A comprehensive data science pipeline for analyzing and predicting customer churn using machine learning techniques. This project demonstrates end-to-end MLOps practices with feature engineering, model training, evaluation, and deployment via FastAPI.

## Features

- 🔍 Comprehensive exploratory data analysis (EDA)
- ⚙️ Advanced feature engineering and preprocessing
- 🤖 Multiple ML model implementations (Logistic Regression, Random Forest, XGBoost)
- 📊 Model performance evaluation and comparison
- 🚀 REST API deployment with FastAPI
- 📈 Interactive visualizations and insights
- 🔧 Configurable hyperparameter tuning
- 📋 Automated model validation and testing

## Installation

### Prerequisites

- Python 3.8+
- pip or conda package manager

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/test-student-customer-churn-analysis.git
cd test-student-customer-churn-analysis
```

2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Install the package in development mode:
```bash
pip install -e .
```

## Usage

### Data Processing and Model Training

1. **Run the complete pipeline:**
```bash
python src/main.py
```

2. **Train models individually:**
```bash
# Train specific model
python src/models/train_model.py --model logistic_regression

# With custom parameters
python src/models/train_model.py --model random_forest --n_estimators 200
```

3. **Generate analysis reports:**
```bash
python src/analysis/eda.py
python src/visualization/plots.py
```

### API Deployment

1. **Start the FastAPI server:**
```bash
uvicorn src.api.main:app --reload --host 0.0.0.0 --port 8000
```

2. **Make predictions via API:**
```bash
curl -X POST "http://localhost:8000/predict" \
     -H "Content-Type: application/json" \
     -d '{
       "tenure": 12,
       "monthly_charges": 70.5,
       "total_charges": 1200.0,
       "contract": "Month-to-month",
       "payment_method": "Electronic check"
     }'
```

3. **Access interactive API documentation:**
   - Swagger UI: `http://localhost:8000/docs`
   - ReDoc: `http://localhost:8000/redoc`

### Jupyter Notebook Analysis

```bash
jupyter notebook notebooks/
```

## Architecture

```
test-student-customer-churn-analysis/
│
├── data/
│   ├── raw/                    # Original datasets
│   ├── processed/              # Cleaned and engineered features
│   └── external/               # Third-party data sources
│
├── src/
│   ├── api/
│   │   ├── main.py            # FastAPI application
│   │   ├── models.py          # Pydantic data models
│   │   └── endpoints/         # API route handlers
│   │
│   ├── data/
│   │   ├── ingestion.py       # Data loading utilities
│   │   ├── preprocessing.py   # Data cleaning pipeline
│   │   └── feature_engineering.py
│   │
│   ├── models/
│   │   ├── base_model.py      # Abstract model interface
│   │   ├── train_model.py     # Model training pipeline
│   │   ├── predict_model.py   # Inference utilities
│   │   └── evaluation.py     # Model metrics and validation
│   │
│   ├── analysis/
│   │   ├── eda.py            # Exploratory data analysis
│   │   └── statistical_tests.py
│   │
│   └── visualization/
│       ├── plots.py          # Chart generation
│       └── dashboard.py      # Interactive dashboards
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_development.ipynb
│   └── 04_model_evaluation.ipynb
│
├── tests/
│   ├── test_data_processing.py
│   ├── test_models.py
│   └── test_api.py
│
├── models/                    # Trained model artifacts
├── reports/                   # Analysis reports and figures
├── config/                    # Configuration files
├── requirements.txt
├── setup.py
└── README.md
```

## Model Performance

| Model | Accuracy | Precision | Recall | F1-Score | AUC-ROC |
|-------|----------|-----------|--------|----------|---------|
| Logistic Regression | 0.82 | 0.78 | 0.75 | 0.76 | 0.85 |
| Random Forest | 0.86 | 0.82 | 0.79 | 0.80 | 0.91 |
| XGBoost | 0.87 |