# Machine Learning Exercise 4  

This folder contains the materials and datasets for the fourth exercise in the "Getting started with Machine Learning" series.  

## 📧 Binary Classification: Logistic Regression & Support Vector Machines  

In this repository, we focus on binary classification techniques to detect spam emails using **Logistic Regression** and **Support Vector Machines (SVM)**. The experiment emphasizes how feature scaling, kernel selection, and hyperparameter tuning influence classification performance. Different SVM kernels are compared to study linear and nonlinear decision boundaries, and cross-validation is used to evaluate generalization ability.

## Contents  

* **Ex-4.ipynb**: The main Jupyter Notebook containing the implementation of Logistic Regression and SVM models.  
* **dataset/**: A directory containing the email dataset used for training and testing.  
* **ML Exercise - 4.pdf**: The report documenting the experiments and results.  

## Notebook Summary (Ex-4.ipynb)  

The `Ex-4.ipynb` notebook demonstrates a complete workflow for building and analyzing binary classifiers:

### 1. Data Preprocessing  
* **Handling Missing Values**: Checking and addressing incomplete records in the dataset.  
* **Feature Scaling**: Standardizing numerical attributes using `StandardScaler`.  
* **Train–Validation–Test Split**: Dividing the data to support tuning and unbiased evaluation.

### 2. Models Implemented  
* **Baseline Logistic Regression**: Establishing reference performance.  
* **Tuned Logistic Regression**: Improving results through regularization and hyperparameter search.  
* **Support Vector Machines**: Training models with linear, polynomial, RBF, and sigmoid kernels.

### 3. Hyperparameter Tuning  
* **RandomizedSearchCV**: Efficiently exploring parameter combinations for both Logistic Regression and SVM.  
* **Cross-Validation**: Applying 5-fold cross-validation to assess stability and robustness.

### 4. Evaluation & Performance Analysis  
* **Metrics**: Measuring Accuracy, Precision, Recall, and F1-score.  
* **Confusion Matrices**: Visualizing classification errors for each model.  
* **ROC Curves & AUC**: Comparing discriminative ability across classifiers and kernels.  
* **Learning Curves**: Studying bias–variance characteristics as training size increases.  
* **Execution Time**: Tracking computational efficiency of different models.

## Getting Started  

1. Open `Ex-4.ipynb` in a Jupyter Notebook environment (such as JupyterLab, Google Colab, or VS Code).  

2. Ensure the required Python libraries are installed:  

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
