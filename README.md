# gcn-molecule-discovery
Multitask GCN pipeline for de novo drug design. Preliminaries target SEGRIM discovery; full pipeline demonstrated on ERα as a GR analogy. Transferable to other nuclear receptor targets. Developed as part of an MSc coursework assignment at Imperial College London.

This repository contains the notebooks accompanying my research proposal for *Artificial Intelligence in Chemistry (Drug Discovery)* 

## Installation
Clone the repository and install dependencies:

git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name
pip install -r requirements.txt


## Repository Contents

### `preliminaries.ipynb`
Proof of concept corresponding to the Preliminaries section of the proposal. Uses GR binding affinity data retrieved directly from ChEMBL (target ID: CHEMBL301).

**Covers:**
- ChEMBL data retrieval and preprocessing (IC50 binding assays, pChEMBL threshold optimisation)
- ECFP4 Morgan fingerprint generation and Random Forest classifier 
- PCA and UMAP chemical space visualisation with known reference compounds (dexamethasone, prednisolone, Compound A, ZK 216348, mapracorat)
- Scaffold-based analogue generation from Compound A with Lipinski and SA score filtering

### `era_segrim_phd_poc.ipynb`
Full proof of concept pipeline demonstrating the methodology described in Aims 1-4 of the proposal. Uses estrogen receptor alpha (ERα, CHEMBL206) as a data-rich substitute for GR, chosen for its well-populated paired agonism/antagonism dataset.

**Covers:**
- ChEMBL data retrieval, RDKit structure standardisation, InChI key deduplication, stereochemical ambiguity flagging 
- Multitask GCN with masked BCE loss across four endpoints simultaneously
- Deep ensemble uncertainty quantification
- Benchmarking: multitask GCN ensemble vs single-task GCN vs Random Forest baseline 
- RDKit atom-by-atom generative design with valence validity enforcement at each step
- Pareto front candidate selection trading ERα activity against off-target risk, with high-uncertainty exclusion 
- ADMET filters: Lipinski Ro5, SA score, TPSA 
- AutoDock Vina docking against ERα (PDB: 1GWR) with estradiol validation


## References
- Bento et al. (2020) An open source chemical structure curation pipeline using RDKit. *J Cheminform*, 12, 51.
- Gilmer et al. (2017) Neural message passing for quantum chemistry. *ICML*, 70, 1263-1272.
- Lakshminarayanan et al. (2017) Simple and scalable predictive uncertainty estimation using deep ensembles. *NeurIPS*, 30.
- Mercado et al. (2021) Graph networks for molecular design. *Machine Learning: Science and Technology*, 2, 025023.
- Sun et al. (2020) Graph convolutional networks for computational drug development and discovery. *Briefings in Bioinformatics*, 21(3), 919-935.

