# Solar Power Generation Prediction

This project predicts **AC Power output** from solar plants using machine learning. It leverages inverter-level generation data and plant-level weather sensor data collected from **two solar plants in India** over 34 days.  
Dataset : https://www.kaggle.com/datasets/anikannal/solar-power-generation-data

The pipeline handles **data cleaning, feature engineering, model training, evaluation, and real-time forecasting**.

---

## Dataset
- **Plant 1 & 2 Generation Data**: Power generation at inverter-level.  
- **Plant 1 & 2 Weather Data**: Plant-level weather readings.  

**Key features include**:  
- `DC_POWER`, `AC_POWER`, `DAILY_YIELD`, `TOTAL_YIELD`  
- `AMBIENT_TEMPERATURE`, `MODULE_TEMPERATURE`, `IRRADIATION`  

---

##  Workflow

### 1. Data Preprocessing
- Merge **generation data** with **weather sensor data**.  
- Handle missing values with forward-fill.  
- Convert timestamps and extract time-based features.  

### 2. Feature Engineering
- **Rolling features**: 1-hour mean/std, 3-hour irradiation max.  
- **Lag features**: Previous interval values for DC power & irradiation.  
- **Daily cumulative yield**.  
- **Interaction terms**: Irradiation × Temperature.  
- **Efficiency metric**: DC Power / Irradiation.  

### 3. Model Training
- Models compared:
  - Linear Regression  
  - Decision Tree  
  - Random Forest  
  - Gradient Boosting  
  - KNN  
  - Neural Network (MLP)  

- Data split: **70% train, 15% validation, 15% test**.  
- Preprocessing: **Imputation + Standard Scaling**.  
- Metrics: **R² score** and **RMSE**.  

### 4. Model Evaluation
- Best model selected based on validation R².  
- Comparison plots:  
  - Actual vs Predicted scatter  
  - Time series prediction  
  - Residual analysis  

### 5. Deployment
- Save artifacts: `best_model.pkl`, `scaler.pkl`, `imputer.pkl`, `feature_cols.pkl`.  
- Real-time prediction supported via a **history buffer** for lag/rolling features.  
- Future forecasting with batch inputs.  

---

## Results
- The best-performing model (e.g., **Random Forest**) achieved strong predictive accuracy on unseen data.  
- Validation plots confirm good alignment between predicted and actual AC power.  

---

## The Predictions
- Realtime AC power
- Forcasting AC power few hours ahead
---
