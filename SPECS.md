# Project specifications

## Project title

Prediction of HIV-1 and human protein-protein interactions using graph convolutional networks

## System environment

* **Runtime environment**: Google Colab (recommended)
* **Python version**: 3.10+
* **Hardware requirements**:

  * Recommended: GPU (CUDA enabled)
  * Minimum: 8 GB RAM, 2-core CPU
* **Frameworks and libraries**:

  * PyTorch
  * PyTorch Geometric
  * NetworkX
  * Pandas, NumPy, Scikit-learn
  * Matplotlib, SciPy
  * Requests (for Dgraph integration)

## Dataset

* **Source**: BioGRID v4.4.243
* **Download date**: March 28, 2025
* **Original size**: 2,752,018 interactions, 37 features
* **Filtered size**: 2,555 interactions (HIV-1 and human only)
* **Final graph**: 1,430 connected protein nodes

## Model architecture

* **Type**: Graph convolutional network (GCN)
* **Layers**: 2-layer GCN with ReLU activation
* **Loss function**: Binary cross-entropy
* **Optimizer**: Adam
* **Learning rate**: 0.01 (tunable)
* **Weight decay**: 5e-4
* **Epochs**: 200
* **Negative sampling**: Balanced strategy (HIV-1 and host node pairs)

## Evaluation metrics

* Area Under ROC Curve (AUC)
* Average Precision (AP)

## Experiments overview

* Inclusion vs. exclusion of centrality-based node features
* Comparison of original vs. balanced (negative sampled) training data
* Grid search over:

  * Learning rate: \[0.01, 0.005, 0.001]
  * Hidden layer size: \[32, 64, 128]
  * Dropout rate: \[0.3, 0.5]

## Best performance

* **Test AUC**: 0.8788
* **Average precision**: 0.8567
* **Improvement over baseline**: +10% AUC

## Integration with Dgraph

* Filtered graph exported from NetworkX into Dgraph Cloud
* Schema includes `name`, `interacts_with`, and type `Protein`
* Dgraph used for interactive querying of:

  * Direct and indirect interactors
  * Shortest paths between viral and host proteins
  * High-degree hubs and shared targets
* Queries executed in Google Colab or via Ratel/API Explorer

## Reproducibility

* All code contained in `PPI.ipynb` and `DGraph.ipynb`
* Preprocessing steps documented and executable in sequence
* Mutations and schema for Dgraph exported as `.json`
* All library versions pinned in `requirements.txt`
