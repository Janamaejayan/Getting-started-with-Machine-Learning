# Machine Learning Exercise 7  

This folder contains the materials and datasets for the seventh exercise in the "Getting started with Machine Learning" series.  

## 🎯 Advanced Ensemble Learning: Bagging, Boosting & Stacking for Medical Diagnosis  

In this repository, we focus on **advanced ensemble learning techniques** to classify breast cancer diagnoses as **Malignant (M)** or **Benign (B)**. The experiment compares four powerful ensemble methods—**Bagging**, **AdaBoost**, **Gradient Boosting**, and **Stacking**—demonstrating how combining multiple models can achieve superior performance in critical healthcare classification tasks. The analysis emphasizes ROC-AUC comparison and confusion matrix evaluation to identify the optimal ensemble approach.

## Dataset

**Wisconsin Diagnostic Breast Cancer (WDBC) Dataset**  
🔗 [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+(Diagnostic))

- **569 samples** with 30 numeric features
- **2 classes**: Malignant (M) and Benign (B)
- **Features**: Three groups of measurements computed from digitized images of fine needle aspirate (FNA)
  - **Mean Features** (10): radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension
  - **Standard Error Features** (10): SE measurements for each characteristic
  - **Worst Features** (10): Worst/largest values for each characteristic
- **Data Format**: CSV with 32 columns (ID + 30 features + diagnosis)

## Contents  

* **dataset/**: Directory containing the WDBC dataset (`wdbc.data`) used for training and testing.  
* **images/**: Visualizations including correlation matrices, confusion matrices, and ROC curves.  
* **ML Exercise - 7.pdf**: The report documenting the experiments and results.  

## Exercise Overview

This exercise demonstrates a comprehensive comparison of four ensemble learning techniques:

### 1. Data Preprocessing  
* **Feature-Target Separation**: Extracting 30 numeric features and diagnosis labels.  
* **Data Encoding**: Converting diagnosis labels (M → 1, B → 0).  
* **Feature Correlation Analysis**: Examining multicollinearity through correlation heatmap.  
* **Train–Test Split**: Dividing the data for model training and evaluation.  
* **Feature Scaling**: Normalizing features for optimal ensemble performance.

### 2. Ensemble Models Implemented  

#### **Bagging (Bootstrap Aggregating)**
* Reduces variance by training multiple base estimators on random subsets
* Combines predictions through averaging or voting
* Creates diverse models through bootstrap sampling

#### **AdaBoost (Adaptive Boosting)**
* Sequential ensemble that adjusts weights of misclassified instances
* Focuses subsequent learners on difficult samples
* Iteratively improves performance on hard-to-classify cases

#### **Gradient Boosting**
* Builds ensemble sequentially, each model correcting previous errors
* Uses gradient descent to minimize loss function
* Optimizes predictions through additive modeling

#### **Stacking (Stacked Generalization)**
* Meta-learning approach combining multiple base learners
* Base models' predictions feed into a meta-learner
* Leverages strengths of diverse algorithms

### 3. Evaluation & Performance Analysis  

**Metrics Used:**
* **Accuracy**: Overall classification correctness
* **Confusion Matrix**: True Positives, True Negatives, False Positives, False Negatives
* **ROC-AUC Score**: Area Under the Receiver Operating Characteristic Curve
* **Sensitivity (Recall)**: True Positive Rate
* **Specificity**: True Negative Rate

**Visualizations:**
* **Feature Correlation Matrix**: Heatmap showing relationships among 30 features
* **Confusion Matrices**: Individual matrices for each ensemble method
* **ROC Curves**: Comparative analysis of all four models

### 4. Results Summary

#### **Test Set Performance (All Models)**

All ensemble methods achieved identical confusion matrix results:

| Metric | Value |
|--------|-------|
| True Negatives (TN) | 72 |
| False Positives (FP) | 0 |
| False Negatives (FN) | 3 |
| True Positives (TP) | 39 |
| **Test Accuracy** | **97.37%** |
| **Sensitivity (Recall)** | **92.86%** |
| **Specificity** | **100%** |
| **False Positive Rate** | **0%** |

#### **ROC-AUC Scores Comparison** ⭐

| Model | AUC Score | Rank |
|-------|-----------|------|
| **Gradient Boosting** | **0.998** | 🥇 **Best** |
| **Bagging** | **0.992** | 🥈 |
| **AdaBoost** | **0.991** | 🥉 |
| **Stacking** | **0.979** | 4th |

#### **Key Findings**

✅ **Perfect Specificity**: All models achieved 100% specificity (zero false positives), meaning no benign cases were misclassified as malignant.

✅ **High Sensitivity**: 92.86% sensitivity across all models, with only 3 malignant cases misclassified as benign.

✅ **Superior AUC**: Gradient Boosting achieved the highest AUC score (0.998), indicating best discriminative ability.

✅ **Consistent Performance**: All ensemble methods demonstrated exceptional and nearly identical classification accuracy (97.37%).

✅ **Medical Reliability**: Zero false positives is critical in medical diagnosis to avoid unnecessary patient anxiety and invasive procedures.

## Getting Started  

1. Open the Jupyter Notebook in your preferred environment (JupyterLab, Google Colab, or VS Code).  

2. Ensure the required Python libraries are installed:  

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

3. The dataset is already included in the `dataset/` directory.

4. Run the notebook cells sequentially to:
   - Load and explore the WDBC dataset
   - Analyze feature correlations
   - Preprocess and split the data
   - Build and train Bagging classifier
   - Build and train AdaBoost classifier
   - Build and train Gradient Boosting classifier
   - Build and train Stacking classifier
   - Evaluate all models with confusion matrices and ROC curves
   - Compare ensemble performance

## Key Learnings

* **Gradient Boosting Excellence**: Achieved the highest AUC (0.998), demonstrating superior discriminative performance for medical diagnosis.
* **Ensemble Consistency**: All four methods achieved identical confusion matrices, showing robust classification boundaries.
* **Zero False Positives**: Critical achievement in medical applications—no healthy patients misdiagnosed as having cancer.
* **Boosting vs Bagging**: Sequential boosting methods (Gradient Boosting, AdaBoost) slightly outperformed bagging in AUC scores.
* **Stacking Trade-offs**: Despite combining multiple algorithms, stacking had the lowest AUC (0.979), suggesting potential overfitting or meta-learner limitations.
* **Feature Correlations**: Strong correlations among radius, perimeter, and area measurements suggest redundancy opportunities for dimensionality reduction.

## Technologies Used

* **Python 3.x**
* **scikit-learn**: For ensemble methods (BaggingClassifier, AdaBoostClassifier, GradientBoostingClassifier, StackingClassifier)
* **NumPy & Pandas**: For data manipulation and preprocessing
* **Matplotlib & Seaborn**: For correlation heatmaps, confusion matrices, and ROC curve visualizations

---

📚 This exercise is part of the "Getting started with Machine Learning" series, focusing on advanced ensemble learning techniques and their critical applications in healthcare classification systems.
