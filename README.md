# Seasonal Agriculture Performance Analysis

VOIS AICTE Batch 1 (2026–2027) — Major Project
Prepared by: Muthumenen M — B.Tech (Artificial Intelligence and Data Science), Dhanalakshmi Srinivasan University

## Project Overview

This project analyzes 4,000 farm-level agricultural records across three cropping seasons
(Kharif, Rabi, Zaid), 8 Indian states, 8 crops, and 4 irrigation methods, to identify how
agricultural performance — yield, production, profitability, water efficiency, and disease/pest
risk — varies across seasons, and to develop evidence-based conclusions and recommendations for
seasonal agricultural planning.

## Objectives

- Explore, clean, and prepare the dataset for analysis.
- Determine how agricultural performance varies across seasons.
- Investigate relationships between environmental conditions and outcomes.
- Compare performance across crops, states, and irrigation methods within seasons.
- Apply appropriate statistical tests (alpha = 0.05) and visualizations.
- Produce evidence-based conclusions and data-driven recommendations.

## Dataset

- **File:** `seasonal_agriculture_performance_dataset.xlsx`
- **Records:** 4,000 farm-level rows, 28 columns (5 categorical, 23 numeric)
- **Covers:** location, crop, season, environmental conditions, resource usage, yield/production,
  and economic outcomes (revenue, cost, profit)

## Tools / Libraries

Python 3, pandas, numpy, scipy, scikit-learn, matplotlib, seaborn, openpyxl, Jupyter
(see `requirements.txt` for versions).

## Project Structure

```
├── Seasonal_Agriculture_Performance_Analysis.ipynb   # Main deliverable — full analysis notebook
├── Seasonal_Agriculture_Performance_Analysis_Report.docx  # Word report
├── Seasonal_Agriculture_Performance_Analysis_Report.pdf   # PDF version of the report
├── data/
│   └── seasonal_agriculture_performance_cleaned.xlsx  # Cleaned dataset
├── figures/                                           # All chart images (used in notebook + report)
├── requirements.txt
└── README.md
```

## Installation

```bash
pip install -r requirements.txt
```

## How to Run the Notebook

1. Place `seasonal_agriculture_performance_dataset.xlsx` at
   `/mnt/user-data/uploads/seasonal_agriculture_performance_dataset.xlsx`, or edit the
   `DATA_PATH` variable in the "Load Dataset" cell to point to your local copy.
2. Open `Seasonal_Agriculture_Performance_Analysis.ipynb` in Jupyter.
3. Run all cells top to bottom (`Kernel -> Restart & Run All`). The notebook is self-contained,
   sets a random seed for reproducibility, and will re-generate every table, statistic, and
   chart directly from the raw dataset — nothing is hard-coded.
4. Running the cleaning section will also write the cleaned dataset to
   `data/seasonal_agriculture_performance_cleaned.xlsx`.

## Major Findings

- **Kharif** (the monsoon season) has the highest average rainfall, yield (5.63 t/ha), and
  average profit (₹178,915), but also the highest average disease/pest risk (54.5%) — a genuine
  trade-off rather than one season being best on every metric.
- **Zaid** is the weakest season economically: average profit is negative (−₹24,805) and 64% of
  its farm records operate at a loss.
- **Crop choice, not season, is the dominant driver of yield and profit.** A regression of yield
  on rainfall, soil moisture, fertilizer, seed quality, and temperature (excluding Sugarcane)
  explains only R² = 0.031 of yield variation.
- **Sugarcane** is both the highest-yielding and most profitable crop per hectare
  (₹97,170/ha average profit); **Wheat** is the least profitable (−₹15,969/ha average).
- Season shows a statistically significant effect on yield, profit, water efficiency, and
  disease/pest risk (Kruskal-Wallis, all p < 0.05), but is **not** significantly associated with
  which crops or irrigation methods are used in that season (chi-square, both p > 0.05).
- Irrigation method is significantly associated with water efficiency (p < 0.001); **Rainfed**
  and **Drip** irrigation show the highest average water efficiency in this dataset.
- Extreme yield values (up to ~101 t/ha) were investigated and found to be legitimate —
  essentially all belong to Sugarcane, a crop that genuinely yields far more per hectare than
  grains or pulses — so they were retained rather than deleted.

## Conclusions

Seasonal differences in agricultural performance are real and statistically measurable, but
modest relative to the differences driven by crop selection. Seasonal planning is most useful
when applied per crop rather than as a single blanket recommendation, and disease/pest
monitoring, irrigation choice, and cost review should be targeted at the specific season-crop
combinations identified in the analysis rather than applied uniformly.

## Limitations

- Observational data — relationships found are associations, not proven causal effects.
- The State–District field does not form a true geographic hierarchy in this dataset; regional
  analysis is therefore reported at the State level only.
- A single snapshot per farm per season; no multi-year comparison is possible.
- See the notebook's "Limitations" section for the full list.
