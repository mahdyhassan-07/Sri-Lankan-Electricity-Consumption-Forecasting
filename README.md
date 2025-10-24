# Sri Lankan Household Electricity Consumption Forecasting

This project, developed for the Artificial Intelligence and Machine Learning (IT2011) module at SLIIT, focuses on building a machine learning model to forecast household net energy import based on smart meter data.

## 🎯 Project Goal
The primary objective was to develop a reliable regression model to predict `NET_IMPORT_kWh` while navigating real-world data challenges like data leakage. The final model uses a LightGBM Regressor.

## 📊 Dataset
The project utilizes the [Sri Lankan Residential Electricity Consumption dataset](https://www.kaggle.com/datasets/lirneasia/sri-lankan-residential-electricity-consumption) from Kaggle, provided by LIRNEasia.

## 🛠️ Methodology

1.  **Data Preprocessing**: The initial pipeline involved handling missing values, creating time-based features (year, month, hour), and scaling numerical features.
2.  **Data Leakage Detection**: Initial models achieved near-perfect R² scores (~0.99), indicating a data leakage problem. The feature importance plot revealed that the model was using direct components of the target variable.
3.  **Leakage Mitigation**: All direct and proxy features related to energy import/export were systematically removed to create a realistic forecasting model.
4.  **Model Training & Tuning**: A LightGBM Regressor was trained on the corrected feature set. `n_estimators` was tuned from 100 to 300 to improve performance.

## 📈 Results
After correcting for data leakage and tuning the model, the final LightGBM Regressor achieved the following performance on the test set:

- **R-squared ($R^2$)**: 0.8448
- **Mean Absolute Error (MAE)**: 2231.32 kWh

The final feature importance plot confirms that the model uses logical predictors like `PHASE_A_CURRENT`, `hour`, and `month`.

## 🚀 How to Run
1.  Clone this repository.
2.  Download the dataset from the Kaggle link above and place the CSV files in a `data/raw/` folder.
3.  Run the preprocessing notebook: `notebooks/Preprocessed pipeline.ipynb`.
4.  Run the model training notebook: `notebooks/Mahdy_LIGHTGBM_NETFIXED_FINAL.ipynb`.

## 🧑‍💻 My Role
Developed and tuned the LightGBM Regressor, and was responsible for identifying and resolving the critical data leakage issue that affected the initial models.
