# Machine Learning Exercise 3

This folder contains the materials and datasets for the third exercise in the "Getting started with Machine Learning" series.

## 📈 Supervised Learning: Regression & Regularization

In this repository, we explore advanced regression techniques to predict continuous values. Using a housing/real estate dataset, we implement and compare multiple regression models, focusing on how regularization techniques like **Ridge**, **Lasso**, and **Elastic Net** help prevent overfitting and handle feature selection. This exercise emphasizes the importance of data pipelines, including automated imputation for missing values and encoding for categorical data.

## Contents

* **Ex-3.ipynb**: The main Jupyter Notebook containing the implementation of the regression pipeline and model comparison.
* **dataset/**: A directory containing the datasets used for training and testing the regression models.
* **ML Exercise - 3.pdf**: It contains the report for the experiments performed.

## Notebook Summary (Ex-3.ipynb)

The `Ex-3.ipynb` notebook demonstrates a robust workflow for building and tuning regression models:

### 1. Data Preprocessing Pipeline
* **Handling Missing Values**: Using `SimpleImputer` to handle gaps in numerical and categorical data.
* **Feature Transformation**: Implementing a `ColumnTransformer` to apply `StandardScaler` to numerical features and `OneHotEncoder` to categorical variables.
* **Pipelines**: Organizing the workflow into Scikit-Learn `Pipeline` objects for reproducible and clean code.

### 2. Regression Models Implemented
* **Linear Regression**: Establishing a baseline model for prediction.
* **Ridge Regression (L2)**: Applying L2 regularization to manage multicollinearity.
* **Lasso Regression (L1)**: Utilizing L1 regularization for automated feature selection by shrinking less important coefficients to zero.
* **Elastic Net**: Combining both L1 and L2 penalties for a more flexible regularized model.

### 3. Hyperparameter Tuning
* **GridSearchCV**: Systematically searching for the optimal `alpha` and `l1_ratio` values to maximize model performance.
* **Cross-Validation**: Using k-fold cross-validation to ensure the model generalizes well to unseen data.

### 4. Evaluation & Performance Analysis
* **Metrics**: Evaluating models using Mean Absolute Error (MAE), Mean Squared Error (MSE), and R-squared ($R^2$) scores.
* **Coefficient Analysis**: Visualizing and comparing the weights assigned to features across different models (Linear vs. Ridge vs. Lasso).
* **Execution Time**: Monitoring the computational efficiency of different algorithms.

## Getting Started

1.  Open `Ex-3.ipynb` in a Jupyter Notebook environment (like JupyterLab, Google Colab, or VS Code).
2.  Ensure you have the necessary Python libraries installed:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn
    ```
3.  Follow the structured cells within the notebook to execute the data processing, model training, and performance comparison.