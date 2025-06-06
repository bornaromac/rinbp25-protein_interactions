# GCN-based prediction of HIV-1 and human protein-protein interactions

This repository contains code and data preprocessing steps for training a graph convolutional network (GCN) to predict potential interactions between HIV-1 and human proteins. The model integrates topological node features (centrality scores) into the graph structure to improve link prediction accuracy.

## Objectives

* To model the HIV-1 – human protein-protein interaction network using a graph-based approach.
* To evaluate how graph centrality features contribute to prediction performance.
* To apply and compare balanced and unbalanced sampling strategies for negative interaction edges.
* To assess model performance via hyperparameter optimization.
* To explore and query the interaction network using the Dgraph graph database.

## Project structure

* `PPI.ipynb` — main Jupyter Notebook with full data pipeline and model training
* `data/` — folder to store raw and filtered PPI data (not included, user must download from BioGRID)
* `requirements.txt` — list of Python dependencies
* `README.md` — this file
* `DGraph.ipynb` — notebook for exporting graph data to Dgraph and executing queries

## Dependencies

Install dependencies via:

```bash
pip install -r requirements.txt
```

Required packages include:

* `torch`, `torch_geometric`
* `networkx`, `pandas`, `numpy`, `scipy`
* `scikit-learn`, `matplotlib`
* `requests` (for communication with Dgraph)

Tested in Google Colab (CUDA GPU available).

## How to run

1. Download the BioGRID dataset (version 4.4.243) manually from [BioGRID](https://thebiogrid.org/) and place it in the `data/` directory.
2. Open `PPI.ipynb` in Jupyter or Google Colab.
3. Follow the cells sequentially to:

   * Preprocess the dataset
   * Build the graph
   * Compute node features (centrality measures)
   * Assign node labels (HIV-1 or human)
   * Train and evaluate the GCN model
4. Optional: Run hyperparameter tuning block at the end for optimal configuration.
5. Open `DGraph.ipynb` to:

   * Export filtered graph data (nodes and edges) to a Dgraph Cloud instance
   * Post the schema and mutations using DQL
   * Perform live queries via Google Colab or Dgraph Ratel/API Explorer

## Results

* Final model achieved:

  * **Test AUC:** 0.8788
  * **Average precision:** 0.8567
* Including centrality-based node features improved performance compared to the structural-only model.
* Balanced negative sampling improved generalization.
* Grid search tuning across 18 configurations led to \~10% improvement in AUC over the baseline.

## Integration with Dgraph

As part of exploratory and presentation steps, the filtered HIV-1/human protein-protein interaction (PPI) graph is exported to a Dgraph Cloud instance. Dgraph is a native graph database that supports efficient traversal, pattern matching, and query execution using DQL (Dgraph Query Language). Through this integration, it is possible to:

* Explore direct and indirect interactions of proteins such as "tat"
* Analyze shortest paths between viral and human proteins (e.g., `shortest(from: ..., to: ...)`)
* Identify high-degree hubs and shared interactors
* Run expressive queries in Ratel or Colab for scientific insights or database course demonstrations

Dgraph was chosen because it natively supports graph data structures, reverse edges, full-text search, and scalable performance, making it a suitable choice for querying biological networks.

## Notes

* All code is self-contained and documented with inline comments.
* This notebook was written with reproducibility and transparency in mind.
* Node features are based on topological properties such as degree, betweenness, and eigenvector centrality.
* Negative edge sampling is stratified to include both HIV-1 and non-HIV-1 nodes.

## Contact

For questions or feedback, please contact: \[[bromac@pmfst.hr](mailto:bromac@pmfst.hr)]
