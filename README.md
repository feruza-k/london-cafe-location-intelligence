# Location Intelligence for Café Site Selection in London

**MSc Big Data & Business Intelligence — University of Greenwich (2024)**  
*Predicting café success potential and commercial rent prices across London's 4,835 Lower Super Output Areas*

---

## Overview

London's café industry is growing fast — the UK coffee shop market was valued at around £4.5 billion in 2023, with roughly 6% annual growth since 2018. Yet despite this, up to **74% of independent cafés fail within their first five years**, and poor location choice is consistently identified as one of the leading causes.

The traditional approach to site selection relies on intuition, experience, or basic market research. This leaves entrepreneurs — particularly first-time café owners — without the tools to properly evaluate the financial and commercial risk of a location before committing to a lease.

This project addresses that gap. It builds a **data-driven location intelligence framework** specifically designed for café site selection in London, combining two things that are usually treated separately:

- **Success potential** — how likely is a café to thrive at a given location based on its demographic, economic, and competitive environment?
- **Rent affordability** — what should commercial rent actually cost there, and is the asking price fair?

By integrating both into a single framework, the goal is to help entrepreneurs identify locations that are not just promising on paper, but financially viable in practice.

### Approach

The research is structured across three tasks:

**Task 1 — Predicting Café Success Potential**  
London is divided into 4,835 Lower Super Output Areas (LSOAs) — small geographic units that capture meaningful neighbourhood-level variation in income, transport access, demographics, and competition. Rather than treating the whole city as one market, this granular approach reflects the reality that conditions can change significantly street by street.

Two unsupervised clustering methods (K-Means and DBSCAN) were explored first to identify natural groupings of LSOAs. While useful for exploratory analysis, neither produced results interpretable enough to act on directly. The **Analytic Hierarchy Process (AHP)** was selected as the final method — a structured multi-criteria decision-making technique that assigns evidence-based weights to each success factor and produces a transparent, explainable score for every LSOA.

**Task 2 — Predicting Commercial Rent Prices**  
Commercial rent data is notoriously hard to obtain at scale. Only 347 labelled rent records (with postcodes) were available — covering less than 8% of London's LSOAs. To address this, a **semi-supervised learning approach** was used: a Random Forest Regressor was trained on the labelled records, used to generate predictions for the remaining LSOAs, and then retrained on the expanded dataset. This pseudo-labelling technique allowed rent predictions to be generated across the entire city despite the sparse training data.

**Task 3 — Comparative Analysis**  
With success scores and rent predictions in place for every LSOA, the final step integrates them. Predicted rents are compared against 20 manually collected actual market rents to validate the model. Locations are then ranked to surface the "sweet spot" — areas where **success potential is high and actual rent falls below the predicted market rate**, meaning the location is undervalued relative to its fundamentals.

---

## Key Results

| Task | Method | Result |
|------|--------|--------|
| Café Success Prediction | Analytic Hierarchy Process (AHP) | Consistency Ratio = 0.069 ✅ |
| Rent Price Prediction | Random Forest Regressor | R² = **0.953**, MAE = **1.08 GBP/sq ft** |
| Baseline Comparison | Linear Regression | R² = 0.619, MAE = 9.56 GBP/sq ft |
| Model Significance | ANOVA | p = 0.022 ✅ |

The two strongest predictors of café success were **public transport accessibility** (weight: 16.9%) and **median house prices** (weight: 13.3%), consistent with existing literature on retail location theory. Central and inner London LSOAs dominated the "Very High Success" category, while outer boroughs generally scored lower — though notable exceptions exist where lower rents create strong value opportunities.

The Random Forest Regressor significantly outperformed Linear Regression on rent prediction, with ANOVA confirming the difference is statistically significant rather than due to chance.

---

## Repository Structure

```
├── README.md
├── requirements.txt
│
├── notebooks/
│   ├── README.md
│   ├── 01_data_collection_eda.ipynb
│   ├── 02_clustering_kmeans_dbscan.ipynb
│   ├── 03_ahp_success_prediction.ipynb
│   ├── 04_rent_price_prediction.ipynb
│   └── 05_comparative_analysis.ipynb
│
├── data/
│   ├── README.md
│   ├── LSOA_Statistics.csv
│   ├── lsoa_success_levels.csv
│   └── Predicted_Success.csv
│
└── visualisations/
    ├── london_cafe_success_map.html
    ├── london_predicted_rent_map.html
    └── london_cafe_success_rent_map.html
```

---

## Interactive Maps

Open any of these HTML files in your browser — no installation needed:

| Map | Description |
|-----|-------------|
| [Café Success Levels](visualisations/london_cafe_success_map.html) | AHP-weighted success scores across all LSOAs |
| [Predicted Rent Prices](visualisations/london_predicted_rent_map.html) | RF-predicted commercial rent per sq ft by LSOA |
| [Success + Rent Combined](visualisations/london_cafe_success_rent_map.html) | Composite view for site selection decisions |

Click any LSOA polygon to see its name, success level, AHP score, and predicted rent.

---

## Tech Stack

```
pandas · numpy · scikit-learn · geopandas · folium · matplotlib · seaborn
```

Built and run in **Google Colab** (Python 3.10).  
Data collected via **Apify** (Google Maps Extractor, TripAdvisor Scraper) and open government sources.

---

## How to Run

```bash
git clone https://github.com/feruza-k/london-cafe-location-intelligence
cd london-cafe-location-intelligence
pip install -r requirements.txt
jupyter notebook notebooks/
```

Notebooks 02–05 can be run independently using the processed datasets in `data/`. You do not need to re-run notebook 01 to reproduce the analysis.

---

## Limitations & Future Work

- No direct foot traffic data available at LSOA level — amenity count used as proxy
- Some features date to 2014 (PTAL) and 2011 (employment rate); more recent data would improve accuracy
- Rent training data is sparse (347 records); a larger labelled dataset would strengthen the model
- The framework is calibrated to London but the methodology could be adapted to other cities or retail sectors
- Real-time data (live foot traffic, social media sentiment) is a clear next step

---

## About

**Author:** Feruza Kachkinbayeva  
**Supervisor:** Dr. Sanyaade Olufemi Adekoya  
**Institution:** University of Greenwich — MSc Big Data & Business Intelligence  
**Submitted:** September 2024

Connect on [LinkedIn](https://www.linkedin.com/in/feruza-kachkinbayeva) <!-- update with your actual URL -->
