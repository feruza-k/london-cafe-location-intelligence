# Notebooks

Run these in order. Notebooks 02–05 can also be run independently using the processed datasets in `data/`.

| Notebook | Task | Description |
|----------|------|-------------|
| `01_data_collection_eda.ipynb` | Setup | Data loading, merging, cleaning, and exploratory analysis across 4,835 LSOAs |
| `02_clustering_kmeans_dbscan.ipynb` | Task 1 | K-Means and DBSCAN clustering as exploratory analysis of location groupings |
| `03_ahp_success_prediction.ipynb` | Task 1 | AHP pairwise comparison, weight calculation, consistency check, and success scoring |
| `04_rent_price_prediction.ipynb` | Task 2 | Semi-supervised rent prediction using RandomForestRegressor with hyperparameter tuning |
| `05_comparative_analysis.ipynb` | Task 3 | Predicted vs actual rent evaluation and final location rankings |

All notebooks were developed in **Google Colab** (Python 3.10). To run locally, install dependencies first:

```bash
pip install -r requirements.txt
```

Note: Notebook 01 requires the raw source files listed in `data/README.md`, most of which are not included in this repository. Notebooks 02–05 only need the three CSV files in `data/`.
