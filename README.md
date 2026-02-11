# 🧬 Tuberculosis 4-Gene Signature Discovery Pipeline

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX) <!-- update upon publication -->

Complete reproducible workflow accompanying the manuscript:

> **"Identification and validation of a four-gene transcriptomic signature for active tuberculosis triage using hybrid machine learning"**  
> *Authors et al., 2026*

This pipeline identifies a minimal 4-gene diagnostic signature (*TAP2, SORT1, WARS, ANKRD22*) for active tuberculosis (TB) from whole‑blood transcriptomic data. It combines rigorous statistical testing, hybrid feature selection, nested cross‑validation, and external validation with bootstrap confidence intervals.

---

## 🔧 Requirements

- Python 3.8 or higher
- Install dependencies:

```bash
pip install -r requirements.txt

📁 Repository Structure

tb-4gene-signature-pipeline/
│
├── tb_4gene_pipeline.py          # Main executable pipeline (run this)
├── requirements.txt              # Python dependencies
├── README.md                     # This file
├── LICENSE                       # MIT license
├── .gitignore                    # Files to ignore
│
├── data/                         # GEO datasets (downloaded automatically)
├── results/                      # Output tables and metrics
├── figures/                      # Generated plots (.png)
└── models/                       # Saved trained models (.pkl)

🚀 Usage
Run the complete pipeline with one command:
python tb_4gene_pipeline.py

The script will automatically:

Download training (GSE19439) and validation (GSE19444) datasets from GEO.

Preprocess: RMA (already in GEO), ComBat batch correction, arsinh transformation, RobustScaler.

Differential expression: Volcano plots (pairwise t‑test + FDR), multi‑group ANOVA + Tukey HSD.

Sensitivity analysis: ANOVA thresholds p < 0.001, 0.01, 0.05.

Hybrid feature selection: Correlation filtering → Boruta‑XGBoost → LASSO.

Nested cross‑validation: 5‑fold outer, 3‑fold inner (feature selection + hyperparameter tuning).

Final model: Voting Classifier (XGBoost, Random Forest, SVM, Gradient Boosting) trained on full training set.

Evaluation: Internal test set + external validation (GSE19444).

Confidence intervals: 1,000 bootstrap resamples for AUC, sensitivity, specificity, accuracy, F1‑score.

Functional enrichment: GO, KEGG, Reactome via g:Profiler.

Visualisations: Volcano plots, box plots, heatmaps, feature importance, model comparison, confusion matrices.

All outputs are saved to results/, figures/, and models/.

📊 Outputs
File	Description
results/final_genes.txt	Four selected genes (TAP2, SORT1, WARS, ANKRD22)
results/external_validation_metrics.csv	Performance metrics with 95% CIs
results/enrichment_results.csv	GO/KEGG/Reactome enrichment
figures/volcano_*.png	Volcano plots for pairwise comparisons
figures/boxplot_*.png	Box plots for each gene (validation cohort)
figures/heatmap.png	Hierarchical clustering heatmap
figures/feature_importance.png	LASSO coefficient bar plot
figures/model_comparison.png	Bar chart comparing 6 classifiers
figures/confusion_matrix_*.png	Confusion matrices
models/voting_classifier.pkl	Trained Voting Classifier
models/robust_scaler.pkl	Fitted RobustScaler

🔬 Reproducibility
All random seeds are fixed (random_state=42). The pipeline is fully deterministic and will reproduce the exact results reported in the manuscript.

📖 Citation
If you use this code or the signature in your work, please cite:
[Author names], "Identification and validation of a four-gene transcriptomic signature 
for active tuberculosis triage using hybrid machine learning", Journal, 2026.

⚖️ License
This project is licensed under the MIT License – see the LICENSE file for details.

🙏 Acknowledgements
We thank the Gene Expression Omnibus (GEO) for providing public datasets GSE19439 and GSE19444.

🧪 How to Test the Pipeline

After installing dependencies, simply run:
python tb_4gene_pipeline.py
The first run will download the datasets (may take a few minutes). Subsequent runs will use cached files.

❓ Questions / Issues
If you encounter any problems, please open an issue on GitHub.

---

## ✅ What’s Included in This README?

| Section | Purpose |
|---------|---------|
| **Title + Badges** | Professional look; license, Python version, DOI placeholder |
| **Description** | Summarises the study and the pipeline |
| **Requirements** | Quick setup instructions |
| **Repository Structure** | Visual map of files and folders |
| **Usage** | One‑line command + step‑by‑step explanation |
| **Outputs** | Table of all generated files |
| **Reproducibility** | Statement about fixed random seeds |
| **Citation** | How to credit your work |
| **License** | MIT open‑source license |
| **Acknowledgements** | Credit to GEO |
| **Testing** | Repeats the run command |
| **Issues** | Link for help |

---

