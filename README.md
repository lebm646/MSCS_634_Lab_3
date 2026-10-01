# MSCS 634 Lab 3: K-Means and K-Medoids Clustering

**Student:** Minh Le  
**University:** University of the Cumberlands  
**Course:** 2026 Fall - Advanced Big Data and Data Mining (MSCS-634-M50) - Full Term

## Purpose

This lab compares K-Means and K-Medoids clustering on the Wine dataset included with scikit-learn. The workflow explores the dataset, standardizes all 13 numeric features with z-score normalization, fits three clusters with each method, evaluates the assignments, and visualizes the results in a two-dimensional PCA projection.

## Repository contents

- `Minh_Le_Lab_3_Clustering.ipynb` - completed and executed Jupyter Notebook containing the analysis, code, outputs, metrics, visualization, and conclusions.
- `README.md` - summary of the lab, results, and implementation decisions.

## Methods

- **Dataset:** scikit-learn Wine dataset (178 samples, 13 features, 3 known classes)
- **Preprocessing:** `StandardScaler` z-score normalization
- **K-Means:** `k = 3`, 20 initializations, fixed random seed of 42
- **K-Medoids:** alternating assignment/medoid-update implementation, 50 random starts, fixed random seed of 42
- **Evaluation:** Silhouette Score and Adjusted Rand Index (ARI), both calculated using all 13 standardized features
- **Visualization:** PCA projection to two dimensions; PCA is used only for plotting, not for model fitting or metric calculation

## Results

| Algorithm | Silhouette Score | Adjusted Rand Index |
|---|---:|---:|
| K-Means | 0.2849 | 0.8975 |
| K-Medoids | 0.2676 | 0.7411 |

K-Means produced the better result for this dataset. Its higher Silhouette Score indicates slightly more cohesive and separated clusters, while its substantially higher ARI shows closer agreement with the known wine classes. The PCA plots show a similar broad three-group structure for both methods, but their representative points and some assignments near cluster boundaries differ.

K-Means represents a cluster with an arithmetic centroid and tends to work well for compact, roughly spherical numeric clusters. K-Medoids represents a cluster with an actual observed wine sample. It is useful when robustness to extreme values, interpretable representatives, or custom dissimilarities are important, although it is more computationally expensive.

## Challenges and decisions

- The original features use different scales, so standardization was necessary before any distance-based clustering.
- K-Medoids is not included in the core scikit-learn clustering module. A self-contained implementation was used so the notebook does not depend on the optional `scikit-learn-extra` package.
- Cluster identifiers are arbitrary. ARI was selected because it compares partitions without requiring cluster labels to match the numeric class labels.
- A two-dimensional chart cannot preserve all relationships in the 13-dimensional data. Therefore, all metrics were computed in the complete standardized feature space, and PCA was limited to visualization.
- Fixed random seeds and multiple initializations were used to make the results reproducible and reduce sensitivity to poor starting points.

## Running the notebook

1. Use Python 3.10 or newer.
2. Install the required packages:

   ```bash
   pip install numpy pandas matplotlib scikit-learn jupyter
   ```

3. Open `Minh_Le_Lab_3_Clustering.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
4. Run all cells from top to bottom.

The submitted notebook already contains the executed outputs and the side-by-side cluster visualization.
