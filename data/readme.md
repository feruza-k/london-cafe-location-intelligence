# Data

This folder contains the processed datasets used across notebooks 02–05.

## Files

| File | Description | Used in |
|------|-------------|---------|
| `LSOA_Statistics.csv` | Unified dataset — 4,835 LSOAs × 16 features covering demographics, transport accessibility, competition, amenities, crime, and house prices | Notebooks 02, 03, 04 |
| `lsoa_success_levels.csv` | Task 1 output — AHP weighted scores and success tier (Low / Medium / High / Very High) per LSOA | Notebook 05 |
| `Predicted_Success.csv` | Task 2 output — predicted commercial rent per sq ft merged with success levels per LSOA | Notebook 05 |

## What is not included

The following raw source files are not in this repository:

- **Scraped data** (Google Maps, TripAdvisor via Apify) — redistribution conflicts with terms of service
- **Commercial rent listings** (PropertyLink, OnTheMarket) — manually collected, not for redistribution
- **London postcodes CSV** — too large for GitHub; download from [Doogal](https://www.doogal.co.uk/london_postcodes)
- **Crime data** — download from [Metropolitan Police / London Data Store](https://data.london.gov.uk/dataset/recorded_crime_summary)

If you want to reproduce notebook 01 (data collection) from scratch, see the source links above and in the thesis for the full list of datasets used.

## Key features in LSOA_Statistics.csv

| Feature | Source | Year |
|---------|--------|------|
| LSOA Code, Name, Postcode | Doogal | 2024 |
| Average Income | Doogal | 2024 |
| Index of Multiple Deprivation | Doogal | 2024 |
| Distance to Station | Doogal | 2024 |
| Population | ONS | 2015 |
| Average Age | ONS (calculated) | 2015 |
| Median Household Income | data.gov.uk | 2015 |
| PT Accessibility Levels | London Data Store | 2014 |
| Employment Rate | London Data Store | 2011 |
| Median House Price | ONS HPSSA Dataset 46 | 2023 |
| Competitors (café count) | Apify / Google Maps | 2024 |
| Café Score (avg rating) | Apify / Google Maps | 2024 |
| Amenities count | Apify / Google Maps + TripAdvisor | 2024 |
| Crime Rate per 1,000 | Metropolitan Police | 2023–24 |
