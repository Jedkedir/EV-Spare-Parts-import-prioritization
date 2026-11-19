# EV Spare-Parts Import Prioritization (Ethiopia Market)

A data-driven import prioritization model designed to help an Ethiopian EV spare-parts importer select a high-turnover **Top starter SKU portfolio** from public marketplace and catalog evidence.

## Project Structure
* **`01_raw_data/raw_parts_data.csv`** — Unedited 30-row dataset (3 EV models × 10 spare-part categories).
* **`01_raw_data/source_log.csv`** — Audit log of all 14 data sources with URLs, collection dates, and notes.
* **`02_cleaned_data/cleaned_parts_data.csv`** — Standardized dataset with missing-value flags (`N/A` preserved) and USD currency normalization.
* **`03_code/EV_Spare_Parts_Prioritization.ipynb`** — Reproducible Python/Colab analysis notebook (cleaning, scoring, sensitivity analysis, and charting).
* **`04_scores/scored_parts_ranking.csv`** — Full 30-SKU ranked output with factor sub-scores and total priority scores.
* **`04_scores/top10_priority_chart.png`** — Horizontal bar chart of the Top 10 priority spare parts.

## Methodology & Scoring Formula
Three high-visibility EVs were selected using five Ethiopian online marketplaces (`Adey Market`, `Jiji Ethiopia`, `Afromekina`, `Mekina.net`, `Gezat Electric`) as a relative market-visibility proxy: **BYD Seagull**, **Volkswagen ID.4**, and **Changan Benben E-Star**.

Each part is scored on a `0–100` scale using five weighted criteria:
$$\text{Priority Score} = 0.30(\text{Demand}) + 0.25(\text{Visibility}) + 0.20(\text{Scarcity}) + 0.15(\text{Practicality}) + 0.10(\text{Confidence})$$

## Key Limitations
* **Visibility vs. Registrations:** Local classifieds counts reflect relative online visibility (including duplicate broker listings), not official Ethiopian vehicle registrations.
* **NHTSA Coverage:** US safety/complaint data (`SRC-09`) applies only to the `Volkswagen ID.4` and is `N/A` for China-spec `BYD Seagull` and `Changan Benben E-Star`.
* **B2B Pricing & Landed Costs:** Four quote-required parts lack public unit prices, and international freight and Ethiopian customs duties require supplier CIF proforma quotes before ordering.

## How to Run
Open `03_code/EV_Spare_Parts_Prioritization.ipynb` in Google Colab or run it locally in Python 3 (`01_raw_data/raw_parts_data.csv` is detected automatically).
