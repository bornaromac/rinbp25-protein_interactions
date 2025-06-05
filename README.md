# GCN-based prediction of HIV-1 and human protein-protein interactions

This repository contains code and data preprocessing steps for training a graph convolutional network (GCN) to predict potential interactions between HIV-1 and human proteins. The model integrates topological node features (centrality scores) into the graph structure to improve link prediction accuracy.

## Objectives

- To model the HIV-1 – human protein-protein interaction network using a graph-based approach.
- To evaluate how graph centrality features contribute to prediction performance.
- To apply and compare balanced and unbalanced sampling strategies for negative interaction edges.
- To assess model performance via hyperparameter optimization.

## Project structure

- `PPI.ipynb` — main Jupyter Notebook with full data pipeline and model training
- `data/` — folder to store raw and filtered PPI data (not included, user must download from BioGRID)
- `requirements.txt` — list of Python dependencies
- `README.md` — this file

## Dependencies

Install dependencies via:

```bash
pip install -r requirements.txt
```

Required packages include:
- `torch`, `torch_geometric`
- `networkx`, `pandas`, `numpy`, `scipy`
- `scikit-learn`, `matplotlib`

Tested in Google Colab (CUDA GPU available).

## How to run

1. Download the BioGRID dataset (version 4.4.243) manually from [BioGRID](https://thebiogrid.org/) and place it in the `data/` directory.
2. Open `PPI.ipynb` in Jupyter or Google Colab.
3. Follow the cells sequentially to:
   - Preprocess the dataset
   - Build the graph
   - Compute node features (centrality measures)
   - Assign node labels (HIV-1 or human)
   - Train and evaluate the GCN model
4. Optional: Run hyperparameter tuning block at the end for optimal configuration.

## Results

- Final model achieved:
  - **Test AUC:** 0.8788
  - **Average precision:** 0.8567
- Including centrality-based node features improved performance compared to the structural-only model.
- Balanced negative sampling improved generalization.
- Grid search tuning across 18 configurations led to ~10% improvement in AUC over the baseline.

## Notes

- All code is self-contained and documented with inline comments.
- This notebook was written with reproducibility and transparency in mind.
- Node features are based on topological properties such as degree, betweenness, and eigenvector centrality.
- Negative edge sampling is stratified to include both HIV-1 and non-HIV-1 nodes.

## Contact

For questions or feedback, please contact: [bromac@pmfst.hr]
