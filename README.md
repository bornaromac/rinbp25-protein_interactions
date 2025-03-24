# Protein-Protein Interaction Modeling using DGraph Community Edition

## Overview
This project aims to model **protein-protein interactions (PPI)** using **DGraph Community Edition**. The goal is to enable researchers to efficiently **query complex biochemical pathways** and identify key proteins involved in biological processes.

## Features
### 1. **Data Ingestion**
- Import PPI datasets from publicly available sources (e.g., **STRING, BioGRID, IntAct**).
- Preprocess and structure data for DGraph compatibility.

### 2. **Graph Schema Design**
- **Nodes:** Proteins, Genes, Biological Pathways.
- **Edges:** Interaction types (binding, inhibition, activation), Confidence scores, Functional annotations.

### 3. **Query & Analysis Capabilities**
- Find **direct and indirect** interactions between proteins.
- Identify proteins **central to pathways** (e.g., via PageRank, Betweenness Centrality).
- Predict potential interactions using **graph-based machine learning**.

### 4. **Visualization & API**
- Interactive web-based visualization of PPI networks.
- API endpoints for **querying interactions programmatically**.

## Technology Stack
- **Database:** DGraph Community Edition
- **Programming Language:** Python (GraphQL, DGraph API)
- **Data Processing:** Pandas, NetworkX
- **Visualization:** Cytoscape.js, D3.js

## Dataset Sources
- [STRING Database](https://string-db.org/)
- [BioGRID](https://thebiogrid.org/)
- [IntAct](https://www.ebi.ac.uk/intact/)

## Installation & Setup
1. **Clone the Repository**
   ```bash
   git clone https://github.com/yourusername/ppi-dgraph.git
   cd ppi-dgraph
   ```

2. **Set Up DGraph**
   Follow the official [DGraph installation guide](https://dgraph.io/docs/get-started/).
   ```bash
   docker-compose up -d
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Load Data into DGraph**
   ```bash
   python data_ingestion.py
   ```

5. **Run API Server**
   ```bash
   python app.py
   ```

## Usage
- Use the API endpoints to query protein interactions.
- Explore the network visualization tool.

## Expected Outcomes
- A fully functional **graph database** for querying protein interactions.
- An API to facilitate automated data retrieval and analysis.
- A visualization tool for exploring biochemical pathways.

## Next Steps
- Define the **exact dataset structure** for ingestion.
- Implement **DGraph schema and queries**.
- Develop API and visualization dashboard.

