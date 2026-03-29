# Machine Learning Exercise 9  

This folder contains the materials and datasets for the ninth exercise in the "Getting started with Machine Learning" series.  

## 🎯 Unsupervised Learning: Clustering Analysis on Human Activity Recognition  

In this repository, we focus on **unsupervised clustering algorithms** to analyze the UCI Human Activity Recognition (HAR) dataset. The experiment compares three powerful clustering techniques—**K-Means**, **DBSCAN**, and **Hierarchical Agglomerative Clustering (HAC)**—to discover patterns in smartphone sensor data representing six human activities. The analysis emphasizes optimal cluster selection, dimensionality reduction visualization, and comprehensive evaluation using both internal and external metrics.

## Dataset

**UCI HAR (Human Activity Recognition) Dataset**  
🔗 [UCI Machine Learning Repository - HAR Using Smartphones](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones)

- **10,299 samples** (7,352 training + 2,947 test)
- **561 numerical features** derived from smartphone accelerometer and gyroscope sensors
- **6 activity classes**:
  - WALKING (1,722 samples)
  - WALKING_UPSTAIRS (1,544 samples)
  - WALKING_DOWNSTAIRS (1,406 samples)
  - SITTING (1,777 samples)
  - STANDING (1,906 samples)
  - LAYING (1,944 samples)

**Features**: Time-domain and frequency-domain signals from Samsung Galaxy S II sensors (50 Hz sampling rate)
- Body acceleration, gravity acceleration, jerk signals
- Magnitude calculations and FFT transformations
- Statistical measures: mean, std, max, min, energy, etc.

**Data Quality**: No missing values, all features standardized

## Contents  

* **Ex-9.ipynb**: The main Jupyter Notebook containing clustering algorithm implementations and analysis.  
* **dataset/**: Directory containing the UCI HAR dataset files (`X_train.txt`, `X_test.txt`, `y_train.txt`, `y_test.txt`, `features.txt`, `activity_labels.txt`).  
* **ML Exercise - 9.pdf**: The report documenting the experiments and results.  

## Notebook Summary (Ex-9.ipynb)  

The `Ex-9.ipynb` notebook demonstrates a complete workflow for unsupervised clustering analysis:

### 1. Data Loading & Exploration  
* **Dataset Loading**: Reading training and test sets, combining into full dataset.  
* **Label Mapping**: Converting activity codes to activity names.  
* **Data Inspection**: Examining shape (10,299 × 561), data types, missing values.  
* **Activity Distribution**: Visualizing sample counts per activity class.

### 2. Data Preprocessing  
* **Feature Standardization**: Applying StandardScaler to normalize all 561 features (zero mean, unit variance).  
* **Data Sampling**: Using 20% sample for hyperparameter search, full dataset for final evaluation.

### 3. Dimensionality Reduction for Visualization  
* **PCA (Principal Component Analysis)**: Reducing to 2D for visualization.  
* **t-SNE (t-Distributed Stochastic Neighbor Embedding)**: Reducing to 2D using PCA-50D as input for computational efficiency.  
* **True Labels Visualization**: Scatter plots showing original activity structure.

### 4. Clustering Algorithms Implemented  

#### **K-Means Clustering**
* **Optimal k Selection**:
  - Elbow method (k vs. Within-Cluster Sum of Squares)
  - Silhouette analysis (k from 2 to 8)
  - **Best k**: 6 (matches the 6 activity classes)
* **Configuration**: k-means++ initialization, 10 runs, random_state=42

#### **DBSCAN (Density-Based Clustering)**
* **Parameter Tuning**: k-distance graph for eps estimation
* **Configuration**: eps=30, minPts=10
* **Result**: Single dominant cluster + 50 noise points (poor performance on this dataset)

#### **Hierarchical Agglomerative Clustering (HAC)**
* **Dendrogram Analysis**: Ward linkage method
* **Configuration**: n_clusters=6, linkage='ward'
* **Visualization**: Truncated dendrogram (30 clusters)

### 5. Evaluation & Performance Analysis  

**Internal Metrics (No Ground Truth Required):**
* **Silhouette Score**: Cluster cohesion and separation (-1 to 1, higher is better)
* **Davies-Bouldin Index**: Cluster similarity measure (lower is better)
* **Calinski-Harabasz Index**: Between-to-within cluster dispersion ratio (higher is better)

**External Metrics (Using Ground Truth Labels):**
* **Adjusted Rand Index (ARI)**: Agreement with true labels (-1 to 1, higher is better)
* **Normalized Mutual Information (NMI)**: Mutual dependence measure (0 to 1, higher is better)

**Visualizations:**
* Activity distribution bar chart
* Elbow curve and silhouette score analysis
* k-distance graph for DBSCAN tuning
* Hierarchical clustering dendrogram
* PCA and t-SNE cluster visualizations for all algorithms
* Comparative bar plots for all evaluation metrics

### 6. Results Summary

#### **K-Means Hyperparameter Optimization**

| k | WCSS (Inertia) | Silhouette Score |
|---|----------------|------------------|
| 2 | 940,338.75 | 0.3945 |
| 3 | 839,955.35 | 0.3139 |
| 4 | 797,965.60 | 0.1501 |
| 5 | 761,293.51 | 0.1386 |
| **6** ✅ | **736,950.81** | **0.1248** |
| 7 | 718,981.15 | 0.0900 |
| 8 | 703,021.71 | 0.0902 |

**Optimal k = 6** (matches ground truth activity count)

#### **Algorithm Performance Comparison**

| Algorithm | Silhouette ↑ | Davies-Bouldin ↓ | Calinski-Harabasz ↑ | ARI ↑ | NMI ↑ |
|-----------|-------------|------------------|---------------------|-------|-------|
| **K-Means** | 0.1096 | **2.3836** 🥇 | **2556.54** 🥇 | 0.4196 | 0.5593 |
| **HAC (Ward)** | **0.1139** 🥇 | 2.4820 | 2349.67 | **0.4599** 🥇 | **0.6015** 🥇 |
| **DBSCAN** | N/A* | N/A* | N/A* | 0.0006 | 0.0076 |

*DBSCAN: Internal metrics undefined due to single-cluster result (1 cluster + 50 noise points)

#### **Key Findings**

**✅ Best Overall Performance: Hierarchical Agglomerative Clustering (HAC)**
- **Highest Silhouette Score** (0.1139): Best cluster cohesion
- **Highest ARI** (0.4599): Best agreement with true activity labels
- **Highest NMI** (0.6015): Captures 60% of information about true activities

**✅ K-Means: Strong Alternative**
- **Best Davies-Bouldin Index** (2.3836): Better cluster separation
- **Best Calinski-Harabasz** (2556.54): Better-defined clusters
- Computationally efficient and scalable

**⚠️ DBSCAN: Poor Performance**
- Unsuitable for this high-dimensional, non-spherical activity data
- Created single dominant cluster (10,249 points) + minimal noise (50 points)
- Nearly zero agreement with true labels (ARI: 0.0006, NMI: 0.0076)

**📊 Interpretation:**
- Low-to-moderate silhouette scores (0.11) indicate overlapping activity patterns in feature space
- HAC with Ward linkage best recovers true activity structure
- Activities don't form perfectly separated spherical clusters, suggesting feature space complexity

## Getting Started  

1. Open `Ex-9.ipynb` in a Jupyter Notebook environment (such as JupyterLab, Google Colab, or VS Code).  

2. Ensure the required Python libraries are installed:  

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn scipy
   ```

3. The dataset is already included in the `dataset/` directory.

4. Run the notebook cells sequentially to:
   - Load and explore the UCI HAR dataset
   - Visualize activity distribution and true label structure
   - Standardize features for clustering
   - Perform K-Means with elbow method and silhouette analysis
   - Apply DBSCAN with k-distance graph tuning
   - Build Hierarchical Agglomerative Clustering with dendrogram
   - Compare all algorithms using 5 evaluation metrics
   - Visualize clusters in 2D using PCA and t-SNE

## Key Learnings

* **Algorithm Selection**: HAC (Ward linkage) outperformed K-Means and DBSCAN for recovering true activity structure in high-dimensional sensor data.
* **Optimal Clusters**: Elbow method and domain knowledge (6 activities) converged on k=6 as optimal.
* **DBSCAN Limitations**: Density-based clustering struggled with high-dimensional, non-uniform density distribution in activity recognition features.
* **Evaluation Metrics**: External metrics (ARI, NMI) showed moderate agreement (40-60%) between clusters and true activities, indicating overlapping activity patterns.
* **Dimensionality Reduction**: PCA and t-SNE visualizations revealed multi-modal structure but confirmed cluster overlap.
* **Ward Linkage**: Minimizing within-cluster variance proved most effective for sensor-based activity data.
* **Feature Complexity**: 561 sensor-derived features capture nuanced activity patterns but don't perfectly separate into spherical clusters.

## Technologies Used

* **Python 3.x**
* **scikit-learn**: For clustering algorithms (KMeans, DBSCAN, AgglomerativeClustering), PCA, and evaluation metrics
* **NumPy & Pandas**: For data manipulation and preprocessing
* **Matplotlib & Seaborn**: For elbow curves, dendrograms, cluster visualizations, and metric comparisons
* **scipy**: For hierarchical clustering dendrogram and linkage calculations

---

📚 This exercise is part of the "Getting started with Machine Learning" series, focusing on unsupervised learning techniques and comprehensive clustering evaluation on real-world sensor-based activity recognition data.
