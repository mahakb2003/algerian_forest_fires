# algerian_forest_fires

This project applies machine learning to predict forest fires in Algeria using meteorological and fire weather index (FWI) data. It includes exploratory data analysis (EDA), feature engineering, model building, and deployment using Flask.

## 📌 Project Objective

To build a predictive model that classifies whether a forest fire occurred (`fire`) or not (`not fire`) based on environmental factors like temperature, humidity, wind speed, and FWI indices.


## 📁 Dataset

- **Source:** Algerian Forest Fires Dataset
- **Total Records:** 246
- **Features:**

| Feature         | Description                     |
|-----------------|---------------------------------|
| day, month, year| Date of observation             |
| Temperature     | Ambient temperature in Celsius  |
| RH              | Relative humidity (%)           |
| Ws              | Wind speed (km/h)               |
| Rain            | Rainfall (mm)                   |
| FFMC, DMC, DC   | Fire Weather Indices            |
| ISI, BUI, FWI   | Fire behavior indices           |
| Classes         | Target: `fire` or `not fire`    |

---

## 🔍 Exploratory Data Analysis (EDA)

- Checked for nulls and duplicates
- Converted categorical columns
- Visualized feature distributions and correlation matrix
- Separated dataset by region (Bejaia & Sidi Bel-abbes) if needed

---

## ⚙️ Feature Engineering

- Date columns converted to datetime
- Label encoding for target variable
- Feature scaling using **StandardScaler**

---

## 🤖 Model Building

- Implemented and compared the following regression models:
  - **Ridge Regression**
  - **Lasso Regression**
  - **ElasticNet Regression**
  
- Used **cross-validation (CV)** to ensure the models are robust and not overfitting:
  - Applied 5-fold cross-validation on all models using `cross_val_score`
  - Evaluated average performance across folds

- Evaluation metrics used:
  - **R² Score** (Coefficient of Determination)
  - **MAE** (Mean Absolute Error)
  - **MSE** (Mean Squared Error)
  - **RMSE** (Root Mean Squared Error)

- **Ridge Regression** performed the best in terms of both accuracy and stability during cross-validation

- The final Ridge model and its corresponding scaler were serialized using `pickle` and used in the deployed Flask application.


---

## 🚀 Deployment

- Developed a **Flask web application**
- Users can input values for Temperature, RH, and Wind Speed
- Model and scaler are loaded using `pickle`
  - Files used: `ridge.pkl`, `scaler.pkl`
- Returns predicted output on test data

---

## 🗃️ Folder Structure

algerian_forest_fires/
│
├── data/ # Dataset CSV files
│ └── Algerian_forest_fires_dataset.csv
│
├── notebooks/ # EDA and model training
│ └── EDA_and_Model.ipynb
│
├── models/ # Saved models
│ └── ridge.pkl
│ └── scaler.pkl
│
├── templates/ # HTML templates for Flask app
│ └── index.html
│ └── home.html
│
├── src/ # Scripts (if needed)
│ └── train.py
│ └── utils.py
│
├── app.py # Flask web app
├── requirements.txt # Dependencies
└── README.md # Project documentation

---

## 💻 Installation & Usage


# Install dependencies
pip install -r requirements.txt

# Run the Flask app
python application.py
