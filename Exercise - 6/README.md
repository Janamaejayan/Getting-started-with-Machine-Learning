# Machine Learning Exercise 6  

This folder contains the materials and datasets for the sixth exercise in the "Getting started with Machine Learning" series.  

## 🌳 Ensemble Learning: Decision Trees & Random Forests for Breast Cancer Diagnosis  

In this repository, we focus on **tree-based ensemble methods** to classify breast cancer diagnoses as **Malignant (M)** or **Benign (B)**. The experiment demonstrates how Decision Trees and Random Forests handle medical classification tasks, emphasizing hyperparameter tuning through GridSearchCV and cross-validation. The comparison highlights the benefits of ensemble methods in improving accuracy and reducing overfitting for critical healthcare applications.

## Dataset

**Wisconsin Diagnostic Breast Cancer (WDBC) Dataset**  
🔗 [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+(Diagnostic))

- **569 samples** with 30 numeric features
- **2 classes**: Malignant (212 samples) and Benign (357 samples)
- **Features**: Characteristics computed from digitized images of fine needle aspirate (FNA) of breast mass
  - Mean measurements (10 features)
  - Standard error measurements (10 features)
  - Worst/largest measurements (10 features)
- **Train/Test split**: 80/20 (455 train / 114 test samples)

## Contents  

* **Ex-6.ipynb**: The main Jupyter Notebook containing the implementation of Decision Tree and Random Forest classifiers.  
* **dataset/**: A directory containing the WDBC dataset used for training and testing.  
* **ML Exercise - 6.pdf**: The report documenting the experiments and results.  

## Notebook Summary (Ex-6.ipynb)  

The `Ex-6.ipynb` notebook demonstrates a complete workflow for building and analyzing tree-based ensemble classifiers:

### 1. Data Loading & Exploration  
* **Dataset Loading**: Reading the WDBC dataset with proper column naming.  
* **Data Inspection**: Examining dataset shape (569 samples, 32 columns).  
* **Class Distribution**: Analyzing the balance between Malignant and Benign samples.

### 2. Data Preprocessing  
* **Target Encoding**: Converting diagnosis labels (M → 1, B → 0).  
* **Feature-Target Separation**: Splitting the dataset into features (X) and target variable (y).  
* **Train–Test Split**: Dividing the data into 80% training and 20% testing sets with random_state=42.

### 3. Models Implemented  
* **Decision Tree Classifier**: Single tree model with hyperparameter optimization.  
* **Random Forest Classifier**: Ensemble of decision trees with bagging and feature randomness.

### 4. Hyperparameter Tuning  
* **GridSearchCV**: Systematic search over parameter combinations with 5-fold cross-validation.  
* **Decision Tree Parameters Tuned**:
  - Criterion: ['gini', 'entropy']
  - Max depth: [None, 3, 5, 10]
  - Min samples split: [2, 5, 10]
  - Min samples leaf: [1, 2, 4]
* **Random Forest Parameters Tuned**:
  - Number of estimators: [50, 100, 200]
  - Max depth: [None, 5, 10]
  - Max features: ['sqrt', 'log2']
  - Bootstrap: [True, False]

### 5. Evaluation & Performance Analysis  
* **Metrics**: Measuring Accuracy, Precision, Recall, and F1-score for both classes.  
* **Confusion Matrices**: Visualizing true positives, true negatives, false positives, and false negatives.  
* **ROC Curves & AUC**: Comparing discriminative ability of Decision Tree vs Random Forest.  
* **Cross-Validation**: Applying 5-fold cross-validation to assess model stability and generalization.  
* **Classification Reports**: Detailed per-class performance breakdown.

### 6. Results Summary

#### **Decision Tree Classifier**
- **Best Parameters**: criterion='entropy', max_depth=None, min_samples_leaf=1, min_samples_split=10
- **Test Accuracy**: 94.74%
- **Cross-Validation Accuracy**: 94.28%
- **Average CV Score**: 91.73%

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Benign (0) | 0.96 | 0.96 | 0.96 | 71 |
| Malignant (1) | 0.93 | 0.93 | 0.93 | 43 |
| **Weighted Avg** | **0.95** | **0.95** | **0.95** | **114** |

#### **Random Forest Classifier** ⭐
- **Best Parameters**: n_estimators=50, max_depth=None, max_features='sqrt', bootstrap=False
- **Test Accuracy**: 96.49% (Better than Decision Tree)
- **Cross-Validation Accuracy**: 96.48% (Better than Decision Tree)
- **Average CV Score**: 95.61%

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Benign (0) | 0.96 | 0.99 | 0.97 | 71 |
| Malignant (1) | 0.98 | 0.93 | 0.95 | 43 |
| **Weighted Avg** | **0.96** | **0.96** | **0.96** | **114** |

#### **Model Comparison**

| Metric | Decision Tree | Random Forest |
|--------|---------------|---------------|
| Test Accuracy | 94.74% | **96.49%** ⭐ |
| CV Accuracy | 94.28% | **96.48%** ⭐ |
| Average CV Score | 91.73% | **95.61%** ⭐ |
| Benign Recall | 96% | **99%** ⭐ |
| Malignant Recall | 93% | 93% |

**Conclusion**: Random Forest outperforms Decision Tree with higher accuracy and better recall on benign cases, making it more suitable for this medical classification task where minimizing false negatives is critical.

## Getting Started  

1. Open `Ex-6.ipynb` in a Jupyter Notebook environment (such as JupyterLab, Google Colab, or VS Code).  

2. Ensure the required Python libraries are installed:  

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```

3. The dataset is already included in the `dataset/` directory.

4. Run the notebook cells sequentially to:
   - Load and explore the WDBC dataset
   - Preprocess and split the data
   - Build and tune Decision Tree classifier using GridSearchCV
   - Build and tune Random Forest classifier using GridSearchCV
   - Evaluate both models with cross-validation
   - Compare results through confusion matrices and ROC curves

## Key Learnings

* **Ensemble Superiority**: Random Forests achieved 96.49% accuracy vs 94.74% for Decision Trees by reducing overfitting through ensemble averaging.
* **Hyperparameter Tuning**: GridSearchCV with 5-fold cross-validation identified optimal parameters for both models.
* **Medical Classification**: High recall for benign cases (99%) is crucial in medical diagnostics to minimize false positives.
* **Cross-Validation Consistency**: Both models showed consistent performance across folds, indicating robust generalization.
* **Tree Depth**: Unrestricted tree depth (max_depth=None) performed best when combined with appropriate split constraints.
* **Bootstrap Effect**: Random Forest without bootstrap (bootstrap=False) performed better, suggesting feature randomness alone was sufficient.

## Technologies Used

* **Python 3.x**
* **scikit-learn**: For Decision Tree, Random Forest, GridSearchCV, and evaluation metrics
* **NumPy & Pandas**: For data manipulation and preprocessing
* **Matplotlib & Seaborn**: For visualization of confusion matrices and ROC curves

---

📚 This exercise is part of the "Getting started with Machine Learning" series, focusing on tree-based ensemble methods and their application in critical healthcare classification tasks.
