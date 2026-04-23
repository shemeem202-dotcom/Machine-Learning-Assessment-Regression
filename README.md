# Machine-Learning-Assessment-Regression

House Price Prediction using Regression Algorithms
A machine learning project that predicts residential house prices using the King County House Sales dataset (Kaggle). Three regression models are trained, evaluated, and compared — Linear Regression, Decision Tree, and Random Forest.

* Project Overview
ItemDetailsDatasetKing County House Sales (kc_house_data.csv)SourceKaggleTarget Variableprice (house sale price in USD)Dataset Size21,613 rows × 21 columnsTask TypeSupervised Regression

* Objective
To build and compare multiple regression models that accurately predict house prices based on features such as living area, number of bedrooms, grade, and location.

* Project Structure
*  House_price_prediction.ipynb   # Main Jupyter Notebook
*  kc_house_data.csv              # Dataset (download from Kaggle)
*  boxplots.png                   # Generated EDA visualization
*  README.md                      # Project documentation

* Tech Stack
LibraryPurposepandasData loading and manipulationnumpyNumerical operationsmatplotlib / seabornData visualizationscikit-learnModel building, scaling, and evaluation

Getting Started
Prerequisites
Make sure you have Python 3.7+ installed, then install the required packages:
bashpip install numpy pandas matplotlib seaborn scikit-learn
Running the Notebook

Download the dataset from Kaggle and place kc_house_data.csv in the project directory.
Launch Jupyter Notebook:

bash   jupyter notebook House_price_prediction.ipynb

Run all cells in order (Kernel → Restart & Run All).


* Data Preprocessing
The following preprocessing steps were applied before model training:

Dropped irrelevant columns: id (unique identifier) and date (not directly useful for price)
No missing values — the dataset was clean with zero null entries
Outlier removal using the IQR method (3× IQR threshold) on the price column
Feature scaling using StandardScaler (for Linear Regression compatibility)
Train/Test split: 80% training, 20% testing (random_state=42)


 * Models
1. Linear Regression
Fits a hyperplane through the data by minimizing squared prediction errors. Used as the baseline model — suitable because several features (e.g., sqft_living, grade) show a roughly linear relationship with price.
2. Decision Tree Regressor
Recursively splits data using feature thresholds to reduce prediction error. Captures non-linear relationships without requiring feature scaling and naturally handles feature interactions.
3. Random Forest Regressor  Best Model
An ensemble of many Decision Trees, each trained on a random data/feature subset. Final prediction is the average across all trees, reducing overfitting and improving generalization.

* Results
ModelMAERMSER² ScoreLinear Regression~$130,000~$175,000~0.68Decision Tree~$100,000~$145,000~0.78Random Forest~$80,000~$118,000~0.86

Random Forest achieves the highest R² score and the lowest error — making it the best-performing model on this dataset.


* Key Insights

Most important features for predicting house price:

sqft_living — total living area
grade — construction and design quality
lat — latitude (location)
sqft_above — above-ground square footage


Location + size together are the strongest combined predictors of house price.
Random Forest outperforms simpler models by capturing complex, non-linear feature interactions that cannot be expressed by a straight line.


* Visualizations
The notebook generates:

Boxplot Analysis — Price distribution by number of bedrooms and house grade
Model Evaluation Table — MAE, MSE, RMSE, and R² for all three models
