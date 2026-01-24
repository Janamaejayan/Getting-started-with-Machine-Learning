# Machine Learning Exercise 2

This folder contains the materials and datasets for the second exercise in the "Getting started with Machine Learning" series.

## 📊 Supervised Learning: Classification & Model Evaluation

In this repository, we transition from data exploration to building and evaluating predictive models. Using the **Spambase** dataset, we implement a **Bernoulli Naive Bayes** classifier to identify spam emails. This exercise focuses on the complete machine learning pipeline: from data preprocessing and feature scaling to model training and rigorous performance evaluation using metrics like Precision, Recall, and F1-Score.

## Contents

* **Ex-2.ipynb**: The main Jupyter Notebook containing the code and implementation for the exercise.
* **datasets/**: A directory containing the CSV dataset used in the exercise.

## Datasets

The `datasets` folder includes the primary dataset used for training and testing the classification model.
* **spambase_csv_Kaggle.csv**: A dataset containing 4,601 instances with 57 features representing word and character frequencies in emails, labeled as spam (1) or non-spam (0).

## Notebook Summary (Ex-2.ipynb)

The `Ex-2.ipynb` notebook implements a full classification workflow focused on spam detection:

### 1. Data Inspection & Cleaning
* **Initial Analysis**: Loading the dataset and inspecting dimensions (4601 rows x 58 columns).
* **Quality Check**: Verifying that there are no null values across the dataset.
* **Statistical Overview**: Generating descriptive statistics (mean, standard deviation, and range) for the word frequency features.

### 2. Preprocessing & Feature Engineering
* **Feature Scaling**: Using `StandardScaler` to normalize numerical frequency data to ensure model stability.
* **Data Splitting**: Separating the features ($X$) from the target labels ($y$) to prepare for training.

### 3. Model Implementation
* **Bernoulli Naive Bayes**: Implementing the `BernoulliNB` classifier from Scikit-Learn, which is highly effective for binary classification tasks involving text or frequency data.



### 4. Performance Evaluation & Visualization
* **Metric Calculation**: Computing key performance indicators including Accuracy, Precision, Recall, and F1-Score.
* **Confusion Matrix**: Visualizing the breakdown of True Positives, True Negatives, False Positives, and False Negatives.
* **Learning Curves**: Plotting Training Accuracy vs. Validation Accuracy against dataset size to analyze model generalization and potential overfitting.



## Getting Started

1.  Open `Ex-2.ipynb` in a Jupyter Notebook environment (like JupyterLab, Google Colab, or VS Code).
2.  Ensure you have the necessary Python libraries installed:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn
    ```
3.  Follow the instructions and code blocks within the notebook to execute the analysis and evaluate the model.
