# Machine Learning Exercise 1

This folder contains the materials and datasets for the first exercise in the "Getting started with Machine Learning" series.

## 📊 Learning Machine Learning Fundamentals

In this repository, we will explore the basics of Machine Learning by working hands-on with essential Python libraries such as **NumPy**, **Pandas**, and **Matplotlib**. The focus will be on understanding data through cleaning, manipulation, and visualization techniques, which are critical steps before building any model. By visualizing patterns, trends, and relationships in datasets, we aim to develop strong intuition about the data and how Machine Learning algorithms interpret it. This repo serves as a learning playground for experimenting, practicing, and gradually moving toward more advanced concepts in the field.

## Contents

- **[Ex-1.ipynb](Ex-1.ipynb)**: The main Jupyter Notebook containing the code and implementation for the exercise.
- **[ML Exercise-1.pdf](ML%20Exercise-1.pdf)**: A PDF document detailing the problem statement, instructions, or theoretical background for the exercise.
- **[datasets/](datasets/)**: A directory containing various CSV datasets used in the exercise.

## Datasets

The `datasets` folder includes several CSV files used for analysis. 

**Note regarding the Handwritten Characters Dataset:**
You can download the full "English Handwritten Characters Dataset" using the link below:
[Download English Handwritten Characters Dataset](https://www.kaggle.com/api/v1/datasets/download/dhruvildave/english-handwritten-characters-dataset)

Other datasets included:
- `Iris.csv`: The classic Iris flower dataset.
- `loan_train.csv`: Training data for loan prediction.
- `english.csv`: Metadata for the handwritten characters dataset.
- `diabetes.csv`: Dataset for diabetes prediction.
- `email.csv`: Dataset for spam detection.

## Notebook Summary (Ex-1.ipynb)

The `Ex-1.ipynb` notebook covers Exploratory Data Analysis (EDA) on several distinct datasets:

1.  **Loan Amount Prediction**
    -   **Data Inspection**: Loading `loan_train.csv`, checking shapes, data types, and missing values.
    -   **Statistical Summary**: Generating descriptive statistics for numerical columns.
    -   **Visualization**: Histograms, boxplots, scatter plots, bar charts for categorical features, and a correlation heatmap.

2.  **Iris Dataset Analysis**
    -   **Data Inspection**: Loading `Iris.csv` and reviewing basic statistics.
    -   **Visualization**: Histograms, boxplots grouped by Species, pairplots, and a correlation heatmap.

3.  **Handwritten Character Recognition**
    -   **Data Inspection**: Loading `english.csv` which contains image paths and labels.
    -   **Visualization**: Analyzing label distribution and visualizing sample character images.

4.  **Predicting Diabetes**
    -   **Data Inspection**: Loading `diabetes.csv` to understand health metrics.
    -   **Analysis**: Exploration of features relevant to diabetes diagnosis.

5.  **Classification of Email Spam**
    -   **Data Inspection**: Loading `email.csv` containing email text data.
    -   **Analysis**: Initial exploration for the task of classifying emails as spam or not spam.

## Getting Started

1.  Open `Ex-1.ipynb` in a Jupyter Notebook environment (like JupyterLab, Google Colab, or VS Code).
2.  Ensure you have the necessary Python libraries installed (`pandas`, `numpy`, `matplotlib`, `seaborn`).
3.  Follow the instructions within the notebook to complete the analysis.
