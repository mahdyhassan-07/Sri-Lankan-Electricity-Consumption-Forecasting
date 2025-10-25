# Sri Lankan Household Electricity Consumption Forecasting

This project, developed for the Artificial Intelligence and Machine Learning (IT2011) module at SLIIT, focuses on building a machine learning model to forecast household net energy import using smart meter data.

## 🎯 Project Goal
The primary objective was to develop a reliable regression model to predict NET_IMPORT_kWh, while addressing real-world challenges like data leakage and feature correlation.
The final optimized model uses a LightGBM Regressor.

## 📊 Dataset
The dataset used is the Sri Lankan Residential Electricity Consumption Dataset provided by LIRNEasia, available on Kaggle.
It contains millions of smart meter readings, including voltage, current, energy imports/exports, and timestamps from multiple households.

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

## 🧰 Tech Stack
Languages & Libraries: Python, Pandas, NumPy, Scikit-learn, LightGBM, Matplotlib, Seaborn
Tools: Jupyter Notebook, Google Colab, Kaggle

## 📚 Key Learnings
How to detect and fix data leakage in ML pipelines.
The importance of realistic evaluation — high R² ≠ good model if leakage exists.
Interpreting model behavior through feature importance and domain logic.

## 🏆 Acknowledgment
This project was completed as part of SLIIT’s IT2011 – Artificial Intelligence and Machine Learning module.
Special thanks to LIRNEasia for providing the dataset and to my team for collaboration and support.
