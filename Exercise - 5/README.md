# Machine Learning Exercise 5  

This folder contains the materials and datasets for the fifth exercise in the "Getting started with Machine Learning" series.  

## 🧠 Deep Learning: Neural Networks for Handwritten Character Recognition  

In this repository, we focus on **neural network architectures** to recognize handwritten English characters using **Single Layer Perceptron (SLP)** and **Multilayer Perceptron (MLP)** models. The experiment demonstrates how network depth, activation functions, optimizers, and hyperparameter tuning influence classification performance in a 62-class recognition task. Different MLP configurations are compared to study the impact of architecture design, and cross-validation is used to find optimal hyperparameters.

## Dataset

**English Handwritten Characters Dataset**  
🔗 [Kaggle Dataset Link](https://www.kaggle.com/datasets/dhruvildave/english-handwritten-characters-dataset)

- **3,410 samples** of handwritten character images
- **62 classes** (alphanumeric and special characters)
- **Image format**: 32×48 pixel grayscale images (flattened to 3,072 features)
- **Train/Test split**: 80/20 (2,728 train / 682 test samples)

## Contents  

* **Ex-5.ipynb**: The main Jupyter Notebook containing the implementation of SLP and MLP neural network models.  
* **datasets/**: A directory containing the English handwritten characters dataset used for training and testing.  
* **ML Exercise - 5.pdf**: The report documenting the experiments and results.  

## Notebook Summary (Ex-5.ipynb)  

The `Ex-5.ipynb` notebook demonstrates a complete workflow for building and analyzing neural network classifiers:

### 1. Data Preprocessing  
* **Image Loading**: Reading grayscale images using OpenCV.  
* **Image Resizing**: Standardizing images to 64×48 pixels.  
* **Normalization**: Scaling pixel values to [0,1] range.  
* **Feature Extraction**: Flattening images into feature vectors.  
* **Train–Test Split**: Dividing the data into 80% training and 20% testing sets.  
* **Feature Scaling**: Standardizing features using `StandardScaler`.

### 2. Models Implemented  
* **Single Layer Perceptron (SLP)**: Custom implementation using One-vs-Rest (OvR) strategy for multi-class classification.  
* **Baseline MLP Models**: Three different configurations with varying architectures, activations, and optimizers.  
* **Tuned MLP**: Optimized model using GridSearchCV with cross-validation.

### 3. Hyperparameter Tuning  
* **GridSearchCV**: Systematic exploration of parameter combinations for MLP.  
* **Parameters Tuned**:
  - Hidden layer sizes: [(128,), (256,128)]
  - Activation functions: ['relu', 'tanh']
  - Solvers: ['adam', 'sgd']
  - Learning rates: [0.001, 0.01]
  - Batch sizes: [32, 64]
* **Cross-Validation**: Applying 2-fold cross-validation to assess stability and robustness.

### 4. Evaluation & Performance Analysis  
* **Metrics**: Measuring Accuracy, Precision, Recall, and F1-score (both Macro and Weighted averages).  
* **Confusion Matrices**: Visualizing classification errors for SLP and MLP models across all 62 classes.  
* **ROC Curves & AUC**: Computing One-vs-Rest ROC curves for each class with micro and macro averaging.  
* **Classification Reports**: Detailed per-class performance breakdown.  
* **Model Comparison**: Analyzing the impact of architecture depth and hyperparameter choices.

### 5. Results Summary

| Model | Architecture | Train Acc | Test Acc | Macro F1 |
|-------|-------------|-----------|----------|----------|
| SLP (OvR) | Single Layer | - | 14.8% | 0.120 |
| MLP Model 1 | (128,) | 94.21% | 38.12% | - |
| MLP Model 2 | (256, 128) | 83.65% | 35.63% | - |
| MLP Model 3 | (512, 256, 128) | 92.82% | 31.67% | - |
| **Tuned MLP** | **(128,)** | **94.21%** | **38.12%** | **0.380** |

The tuned MLP with a single hidden layer (128 units), ReLU activation, and SGD optimizer achieved the best generalization performance with early stopping after 32 epochs.

## Getting Started  

1. Open `Ex-5.ipynb` in a Jupyter Notebook environment (such as JupyterLab, Google Colab, or VS Code).  

2. Ensure the required Python libraries are installed:  

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn opencv-python
   ```

3. Download the dataset from the [Kaggle link](https://www.kaggle.com/datasets/dhruvildave/english-handwritten-characters-dataset) and place it in the `datasets/` directory.

4. Run the notebook cells sequentially to:
   - Load and preprocess the handwritten character images
   - Train the Single Layer Perceptron (SLP) model
   - Build and evaluate baseline MLP configurations
   - Perform hyperparameter tuning using GridSearchCV
   - Analyze results through confusion matrices and ROC curves

## Key Learnings

* **SLP Limitations**: Single layer perceptrons struggle with complex multi-class problems (14.8% accuracy).
* **Architecture Depth**: Deeper networks don't always generalize better; the single hidden layer model outperformed deeper architectures.
* **Overfitting**: Large gap between train and test accuracy indicates overfitting challenges in character recognition.
* **Optimizer Choice**: SGD with appropriate learning rate performed better than Adam for this task.
* **Early Stopping**: Convergence in 32 epochs (out of 800 max) demonstrates the importance of monitoring training progress.

## Technologies Used

* **Python 3.x**
* **scikit-learn**: For MLP implementation, hyperparameter tuning, and evaluation metrics
* **OpenCV**: For image loading and preprocessing
* **NumPy & Pandas**: For data manipulation
* **Matplotlib & Seaborn**: For visualization of confusion matrices and ROC curves

---

📚 This exercise is part of the "Getting started with Machine Learning" series, focusing on deep learning fundamentals and neural network design principles.
