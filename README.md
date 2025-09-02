# Seeds Clustering Analysis

This project performs unsupervised clustering on a dataset of wheat seeds using **K-Means** and **Hierarchical Clustering**. It compares **data-driven clustering** with the **known ground truth** (3 wheat varieties) using PCA and multiple evaluation metrics.

---

## Dataset Overview

- **Source**: UCI Machine Learning Repository  
- **Samples**: 210  
- **Features**: 7 numerical features + 1 label (used for evaluation)  
- **Classes**: 3 (Kama, Rosa, Canadian)  
- **Description**: Measurements of kernel geometry from wheat grains captured using soft X-ray imaging.

Dataset file: `Seeds Dataset.txt`

---

## Project Objectives

- Explore relationships between features and visualize distributions.
- Apply **Principal Component Analysis (PCA)** for dimensionality reduction.
- Determine the optimal number of clusters using:
  - **Silhouette Score**
  - **Davies-Bouldin Index**
  - **Calinski-Harabasz Score**
  - **Elbow Method**
  - **Dendrogram (Hierarchical Clustering)**
- Compare clustering results with known classes using **Adjusted Rand Index (ARI)**.

---

## Clustering Strategy

Although most **internal validation metrics** (Silhouette, Davies-Bouldin, etc.) suggested **K=2**, the dataset is known to have **3 wheat varieties**. So both scenarios were analyzed:

| Cluster Count | Rationale                                 |
|---------------|--------------------------------------------|
| **K=2**        | Optimal according to unsupervised metrics |
| **K=3**        | Ground truth from dataset description     |

---

## Techniques Used

- **Data preprocessing** and feature standardization
- **PCA** for variance preservation and visualization (3 components explained 98.67%)
- **K-Means** clustering
- **Agglomerative (Hierarchical)** clustering
- Cluster evaluation:
  - Silhouette Score
  - Davies-Bouldin Index
  - Calinski-Harabasz Index
  - Adjusted Rand Index (external)

---

## Clustering Evaluation Summary

Both clustering algorithms were evaluated using **Adjusted Rand Index (ARI)**, comparing predicted labels to true classes.

| Model         | ARI Score | Interpretation         |
|---------------|-----------|------------------------|
| K-Means       | 0.7850    | 78.50% Similarity      |
| Hierarchical  | 0.7844    | 78.44% Similarity      |

**K-Means slightly outperformed Hierarchical**, and is preferred due to:
- Higher ARI
- Better scalability
- Simpler tuning

> Final clustering visualizations were made for both **K=2** and **K=3** to represent both perspectives.

---

## PCA Results

| Component(s)         | Cumulative Variance Explained |
|----------------------|-------------------------------|
| PC1                  | 71.87%                        |
| PC1 + PC2            | 88.98%                        |
| PC1 + PC2 + PC3      | 98.67%                        |

> Dimensionality was reduced to 3 principal components while retaining nearly all data variance.

---

## Visualizations

- Feature scatter plots and correlation heatmaps
- Scree plot and PCA loadings heatmap
- Elbow method, silhouette, DB, CH metrics
- Dendrogram with optimal cut
- Clustering projections on PCA components (K=2 and K=3)
