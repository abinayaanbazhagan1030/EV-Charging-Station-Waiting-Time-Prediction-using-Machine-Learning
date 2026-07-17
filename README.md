# EV-Charging-Station-Waiting-Time-Prediction-using-Machine-Learning
This project predicts EV charging station waiting times using data analysis and machine learning. It covers EDA, outlier handling, and correlation analysis, then compares Linear Regression, Ridge Regression (GridSearchCV tuned), and Random Forest Regressor models, evaluated using R² and MSE.
# EV Charging Station Waiting Time Prediction

## 📌 Overview
Electric Vehicle (EV) adoption is growing rapidly, and with it comes increasing pressure on charging infrastructure. Long or unpredictable waiting times at charging stations are a major pain point for EV owners and a planning challenge for station operators.

This project uses data analysis and machine learning to **predict waiting times at EV charging stations** based on operational and environmental factors such as charger availability, charging type, vehicle type, weather, traffic, and time of day. The insights and models produced can help operators optimize charger allocation and help drivers plan their charging visits more efficiently.

## 🎯 Objective
- Analyze the key factors that influence EV charging station waiting times
- Handle outliers and prepare the data for modeling
- Build and compare multiple regression models to predict waiting time
- Identify the best-performing model based on evaluation metrics

## 📂 Dataset
**File:** `ev_charging_dataset_with_added_parameters.xlsx`

| Column | Description |
|---|---|
| Station_ID | Unique identifier for the charging station (dropped before modeling) |
| Date | Date of the record (dropped before modeling) |
| Charging_Type | Fast or Normal charging |
| Available_Chargers | Number of chargers available at the station |
| Vehicle_Type | Type of EV (e.g., car, bike, bus) |
| City | Location of the charging station |
| Time_Slot | Time period of charging session |
| Weather | Weather conditions during the session |
| Holiday | Whether the day was a holiday |
| Traffic_Level | Traffic conditions near the station |
| **Waiting_Time** | Target variable — time (in minutes) a user waited to charge |

## 🛠️ Tech Stack
- **Language:** Python
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn
- **Environment:** Jupyter Notebook / Google Colab

## 🔄 Project Workflow

### 1. Import Libraries
Load pandas, numpy, matplotlib, seaborn, and scikit-learn.

### 2. Load Dataset
Read the Excel dataset into a pandas DataFrame.

### 3. Exploratory Data Analysis (EDA)
- Check dataset shape and structure (`.info()`)
- Generate summary statistics (`.describe()`)
- Check for missing values (`.isnull().sum()`)

### 4. Data Visualization
- **Boxplot** of `Waiting_Time` to identify outliers
- **Countplot** of `Vehicle_Type` distribution
- **Bar plots** comparing `Charging_Type` and `Available_Chargers` against `Waiting_Time`

### 5. Data Preprocessing
- Cap extreme outliers in `Waiting_Time` (values above 500 capped at 500) to reduce their skewing effect on the model
- Encode `Charging_Type` numerically (Fast = 1, Normal = 0)
- Drop non-predictive columns (`Station_ID`, `Date`)
- One-hot encode categorical features: `City`, `Time_Slot`, `Vehicle_Type`, `Weather`, `Holiday`, `Traffic_Level`

### 6. Correlation Analysis
Generate a correlation matrix and heatmap to visualize relationships between numeric features and identify which variables most influence waiting time.

### 7. Train-Test Split
Split the dataset into training (80%) and testing (20%) sets using `train_test_split`.

### 8. Model Building & Evaluation
Three regression models are trained and compared:

| Model | Description |
|---|---|
| **Linear Regression** | Baseline model capturing linear relationships |
| **Ridge Regression** | Regularized linear model; alpha tuned via GridSearchCV |
| **Random Forest Regressor** | Ensemble model tuned via GridSearchCV (n_estimators, max_depth, criterion) to capture non-linear patterns |

Each model is evaluated using:
- **R² Score** — proportion of variance in waiting time explained by the model
- **Mean Squared Error (MSE)** — average squared difference between predicted and actual waiting times

### 9. Results
A comparison DataFrame of actual vs. predicted waiting times is generated for the final model to visually assess prediction accuracy.

## 📊 Results Summary
*(Fill in with your final output values after running the notebook)*

| Model | R² Score | MSE |
|---|---|---|
| Linear Regression | 0.69 | 0.4353 |
| Ridge Regression | 0.69 | 0.4353 |
| Random Forest Regressor | 0.99 | 10.78 |

## 🚀 How to Run
1. Clone/download this repository.
2. Install the required dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
   ```
3. Place `ev_charging_dataset_with_added_parameters.xlsx` in the project directory (update the file path in the notebook if not using Google Colab's default `/content/` path).
4. Open the notebook and run all cells sequentially.

## 📁 Project Structure
```
├── ev_charging.ipynb                                   # Main analysis notebook
├── ev_charging_dataset_with_added_parameters.xlsx       # Dataset
└── README.md                                            # Project documentation
```

## 🔮 Future Improvements
- Experiment with Gradient Boosting / XGBoost for potentially stronger performance
- Analyze feature importance from the Random Forest model to identify top waiting-time drivers
- Use k-fold cross-validation instead of a single train/test split for more robust evaluation
- Deploy the best model as a simple web app or API for real-time waiting time prediction
- Incorporate real-time data (live traffic, live charger status) for dynamic predictions

## 👤 Author
Abinaya — B.Tech Computer Science Engineering student

