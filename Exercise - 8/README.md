# Machine Learning Exercise 8  

This folder contains the materials and datasets for the eighth exercise in the "Getting started with Machine Learning" series.  

## 📊 Dimensionality Reduction: Principal Component Analysis (PCA) for Model Optimization  

In this repository, we focus on **dimensionality reduction using Principal Component Analysis (PCA)** to improve model performance and computational efficiency. The experiment compares regression and classification models with and without PCA preprocessing, demonstrating how reducing feature dimensions from 11 to 7 (while retaining 95% variance) impacts model accuracy and generalization. Multiple algorithms are evaluated including **Linear Regression**, **Random Forest**, **Logistic Regression**, and **Support Vector Machines (SVM)**.

## Dataset

**Student Academic Performance Dataset**  
📁 Synthetic educational dataset generated for dimensionality reduction analysis

- **1,000 samples** with 11 numeric features
- **Dual-task dataset**: Supports both regression and classification
- **Features (11 independent variables)**:
  - Math, Physics, Chemistry, Biology scores
  - Total_Science, Average_Science
  - English, Computer_Science
  - Sports_Score, Attendance_Percentage
  - Random_Noise_Feature (intentionally noisy)

- **Target Variables**:
  - **Regression**: Final_Score_Regression (continuous)
  - **Classification**: Performance_Level_Classification (3 classes)
    - Classes: High (202), Medium (545), Low (253)

- **Data Quality**: No missing values, fully complete dataset

## Contents  

* **Ex-8.ipynb**: The main Jupyter Notebook containing PCA implementation and model comparisons.  
* **dataset/**: Directory containing the student performance dataset (`Dataset.csv`).  
* **ML Exercise - 8.pdf**: The report documenting the experiments and results.  

## Notebook Summary (Ex-8.ipynb)  

The `Ex-8.ipynb` notebook demonstrates a complete workflow for dimensionality reduction and model comparison:

### 1. Data Loading & Exploration  
* **Dataset Loading**: Reading the student performance dataset.  
* **Data Inspection**: Examining shape (1,000 × 13), data types, and basic statistics.  
* **Missing Values Check**: Verifying data completeness.  
* **Class Distribution**: Analyzing target variable balance.

### 2. Data Preprocessing  
* **Feature-Target Separation**: Splitting features from regression and classification targets.  
* **Label Encoding**: Converting categorical Performance_Level to numeric.  
* **Feature Standardization**: Applying StandardScaler to normalize all features.  
* **Train–Test Split**: Creating validation sets for model evaluation.

### 3. Principal Component Analysis (PCA)  
* **Variance Threshold**: Configured to retain 95% of total variance.  
* **Optimal Components**: Automatically determined **7 components** (from 11 features).  
* **Actual Variance Retained**: **95.90%** with 36% dimensionality reduction.  
* **Component Analysis**: Visualizing individual and cumulative explained variance.

### 4. Models Implemented  

#### **Regression Models:**
* **Linear Regression**: Baseline model with no hyperparameters
* **Random Forest Regressor**: Ensemble method with hyperparameter tuning
  - Tuned parameters: n_estimators [50, 100, 200], max_depth [None, 5, 10]
  - Best parameters: n_estimators=200, max_depth=5

#### **Classification Models:**
* **Logistic Regression**: Linear classifier with regularization tuning
  - Tuned parameter: C [0.01, 0.1, 1, 10]
  - Best parameter: C=0.1 (strong regularization)
* **Support Vector Machine (SVM)**: Non-linear classifier with kernel optimization
  - Tuned parameters: kernel ['linear', 'rbf'], C [0.1, 1, 10], gamma ['scale', 'auto']
  - Best parameters: kernel='rbf', C=1, gamma='auto'

### 5. Hyperparameter Tuning  
* **GridSearchCV**: Systematic parameter search with cross-validation.  
* **5-Fold Cross-Validation**: Stratified splits for robust performance assessment.  
* **Scoring Metrics**: R² for regression, Accuracy for classification.

### 6. Evaluation & Performance Analysis  

**Metrics Used:**
* **Regression**: Mean Squared Error (MSE), R² Score
* **Classification**: Accuracy, F1-Score (weighted)

**Visualizations:**
* **Scree Plot**: Individual component variance contribution
* **Cumulative Variance Plot**: Shows 95% threshold and optimal 7 components
* **Model Comparison Charts**: MSE, R², Accuracy, and F1-Score comparisons (PCA vs. No PCA)

### 7. Results Summary

#### **Regression Performance (5-Fold CV Averages)**

| Model | Configuration | MSE | R² Score |
|-------|--------------|-----|----------|
| Linear Regression | No PCA | 26.2338 | **0.7479** 🥇 |
| Linear Regression | With PCA (7 components) | 26.2766 | 0.7476 |
| Random Forest | No PCA | 28.7219 | 0.7241 |
| Random Forest | With PCA (7 components) | **27.8283** | 0.7328 ✅ |

**Key Findings:**
- **Best Model**: Linear Regression without PCA (R² = 0.7479)
- **PCA Impact**: Random Forest improved with PCA (MSE reduced by 0.89, R² increased by 0.87%)
- Linear Regression performance nearly identical with/without PCA

#### **Classification Performance (5-Fold CV Averages)**

| Model | Configuration | Accuracy | F1-Score (Weighted) |
|-------|--------------|----------|---------------------|
| Logistic Regression | No PCA | 0.7380 | 0.7350 |
| Logistic Regression | With PCA (7 components) | **0.7440** 🥇 | **0.7411** ✅ |
| SVM | No PCA | 0.7420 | 0.7354 |
| SVM | With PCA (7 components) | 0.7320 | 0.7251 |

**Key Findings:**
- **Best Model**: Logistic Regression with PCA (Accuracy = 74.40%)
- **PCA Impact**: Beneficial for Logistic Regression (+0.6% accuracy), detrimental for SVM (-1.0% accuracy)
- Algorithm-dependent effectiveness of dimensionality reduction

#### **PCA Impact Summary**

| Model Type | PCA Effect | Performance Change |
|------------|------------|-------------------|
| Linear Regression | Minimal | ≈ 0% (nearly identical) |
| Random Forest | ✅ **Improved** | MSE ↓ 3.1%, R² ↑ 1.2% |
| Logistic Regression | ✅ **Improved** | Accuracy ↑ 0.8%, F1 ↑ 0.8% |
| SVM | ⚠️ **Degraded** | Accuracy ↓ 1.3%, F1 ↓ 1.4% |

## Getting Started  

1. Open `Ex-8.ipynb` in a Jupyter Notebook environment (such as JupyterLab, Google Colab, or VS Code).  

2. Ensure the required Python libraries are installed:  

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

3. The dataset is already included in the `dataset/` directory.

4. Run the notebook cells sequentially to:
   - Load and explore the student performance dataset
   - Standardize features and encode targets
   - Apply PCA with 95% variance retention
   - Train Linear Regression and Random Forest regressors
   - Train Logistic Regression and SVM classifiers
   - Compare all models with and without PCA preprocessing
   - Visualize component variance and performance comparisons

## Key Learnings

* **Dimensionality Reduction Efficiency**: PCA reduced features from 11 to 7 (36% reduction) while retaining 95.90% variance.
* **Algorithm-Dependent Benefits**: PCA improved ensemble methods (Random Forest) and linear classifiers (Logistic Regression) but degraded SVM performance.
* **Linear Models Resilience**: Linear Regression showed minimal sensitivity to PCA, maintaining nearly identical performance.
* **Computational Advantages**: 36% feature reduction translates to faster training and prediction times with minimal accuracy loss.
* **Variance Threshold**: 95% retention effectively balances information preservation and dimensionality reduction.
* **Hyperparameter Optimization**: GridSearchCV identified optimal configurations (RF: n_estimators=200, depth=5; LR: C=0.1; SVM: rbf kernel, C=1).
* **Cross-Validation Consistency**: 5-fold CV provided stable performance estimates across all models.

## Technologies Used

* **Python 3.x**
* **scikit-learn**: For PCA, regression/classification models, GridSearchCV, and evaluation metrics
* **NumPy & Pandas**: For data manipulation and preprocessing
* **Matplotlib & Seaborn**: For scree plots, cumulative variance visualization, and performance comparison charts

---

📚 This exercise is part of the "Getting started with Machine Learning" series, focusing on dimensionality reduction techniques and their impact on model performance across regression and classification tasks.
